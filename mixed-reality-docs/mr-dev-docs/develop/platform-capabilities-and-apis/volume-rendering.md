---
title: 立体渲染
description: 了解如何在图像中以不透明度与颜色高效呈现丰富的Windows Mixed Reality。
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: volumetric image， volume rendering， performance， mixed reality
ms.openlocfilehash: 3843f0f4e49a0564b41d834231630d281aa9e874df8d35c4feaa4fe5bba0ed68
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220924"
---
# <a name="volume-rendering"></a>立体渲染

有关医疗 MRI 或工程卷，请参阅 [维基百科上的批量渲染](https://en.wikipedia.org/wiki/Volume_rendering)。 这些"音量图像"包含在整个卷中不透明度、颜色丰富的信息，这些信息无法轻松表示为多边形网格 [等表面](https://en.wikipedia.org/wiki/Polygon_mesh)。

用于提高性能的关键解决方案
1. BAD：Naïve 方法：显示整个卷，通常运行速度过慢
2. 好：剪切平面：只显示卷的单个切片
3. 好：剪切子卷：只显示卷的一些层
4. 好：降低音量渲染分辨率 (请参阅"混合分辨率场景渲染") 

在任何特定帧（即总内存带宽）中，只有一定数量的信息可以从应用程序传输到屏幕。 此外，转换 (或) 呈现所需的任何处理操作或"明暗度"都需要时间。 执行卷呈现时，主要注意事项如下：
* Screen-Width * Screen-Height * Screen-Count * Volume-Layers-on-that-Pixel = Total-Volume-Samples-Per-Frame
* 1028 * 720 * 2 * 256 = 378961920 (100%)  (完全 res 量：样本) 
* 1028 * 720 * 2 * 1 = 1480320 (0.3% 的完整)  (精简切片：每个像素 1 个样本，可顺利) 
* 1028 * 720 * 2 * 10 = 14803200 (3.9% 的完整)  (子卷切片：每个像素 10 个样本，运行相当流畅，看起来是三维) 
* 200 * 200 * 2 * 256 = 20480000 (5%)  (的完全分辨率低于 5%的 res 音量：更少的像素、完整音量、看起来 3d 但有点模糊) 

## <a name="representing-3d-textures"></a>表示三维纹理

在 CPU 上：

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

在 GPU 上：

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>着色和渐变

如何为卷（如 MRI）着色，以用于有用的可视化效果。 主要方法是使用"强度窗口" (最小和最大) ，并且只需缩小该空间以查看黑色和白色强度。 然后，可以将"颜色渐变"应用于该范围内的值，并存储为纹理，以便对强度范围的不同部分使用不同的颜色进行着色：

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

在许多应用程序中，我们在卷中存储原始强度值和"分段索引" (将不同的部分（如外观和）分段;这些细分市场由专家在专用工具中创建) 。 这可与上述方法结合使用，以针对每个段索引设置不同的颜色，甚至不同的颜色渐变：

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>着色器中的卷切片

一个很好的第一步是创建一个"切片平面"，该平面可以移动卷、"切片"以及每个点的扫描值方式。 这假设有一个"VolumeSpace"多维数据集，它表示卷位于世界空间中，该多维数据集可以用作放置点的参考：

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>着色器中的卷跟踪

如何使用 GPU 执行子卷跟踪 (体体深度，然后对数据进行从后到前分层) ：

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>全卷渲染

修改上面的子卷代码后，我们获得：

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>混合分辨率场景渲染

如何以低分辨率呈现场景的一部分，以及如何将部分场景放置到位：
1. 设置两个屏幕外相机，一个摄像头用于跟踪更新每个帧的每个眼睛
2. 设置两个低分辨率渲染 (，即相机渲染到的每个) 200x200
3. 设置在用户前面移动的四边形

每个帧：
1. 以低分辨率绘制每个眼睛的呈现目标 (数据、昂贵的着色器等) 
2. 通常将场景绘制为 (网格、UI 等的全分辨率) 
3. 在用户前面绘制一个四边形，在场景上绘制一个四边形，将低 res 呈现到该场景上
4. 结果：具有低分辨率但高密度卷数据的全分辨率元素的可视化组合
