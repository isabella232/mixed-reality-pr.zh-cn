---
title: 案例研究 - 跨性能不同的设备缩放 Datascape
description: 此案例研究深入探讨 Microsoft 开发人员如何优化 Datascape 应用，以跨具有一系列性能功能的设备提供引人注目的体验。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式头戴显示设备， 性能优化， VR， 案例研究
ms.openlocfilehash: d1c54f5fbe6843f9bf61af20b611c6aeb22b0704c209bfdb555fe57b95805cf9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195747"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>案例研究 - 跨性能不同的设备缩放 Datascape

Datascape 是一Windows Mixed Reality Microsoft 内部开发的一种应用程序，我们专注于在地形数据上显示天气数据。 应用程序通过将用户与全息数据可视化效果围绕，探索用户在混合现实中发现数据获得的独特见解。

对于 Datascape，我们希望面向具有不同硬件功能的各种平台，包括 Microsoft HoloLens 到 Windows Mixed Reality 沉浸式头戴显示设备，以及从低功率电脑到具有高端 GPU 的最新电脑。 主要挑战是在以高帧速率执行时，在具有完全不同的图形功能的设备上以视觉上引人注目的内容呈现我们的场景。

本案例研究将演练用于创建一些 GPU 密集型系统的过程和技术，描述我们遇到的问题以及如何克服这些问题。

## <a name="transparency-and-overdraw"></a>透明性和过度绘制

我们的主要渲染难以处理透明度，因为透明度在 GPU 上可能很昂贵。

写入深度缓冲区时，可以前后呈现纯色几何图形，阻止丢弃位于该像素后面的任何未来像素。 这可以防止隐藏像素执行像素着色器，显著加快进程。 如果以最佳方式对几何图形进行排序，则屏幕上每个像素将只绘制一次。

透明几何图形需要重新排序，并依赖于将像素着色器的输出与屏幕上的当前像素混合。 这可能会导致屏幕上的每个像素被绘制到每个帧多次，称为过度绘制。

对于HoloLens和主流电脑，屏幕只能填充几次，使透明呈现出现问题。

## <a name="introduction-to-datascape-scene-components"></a>Datascape 场景组件简介

场景中有三个主要组件： **UI、地图** 和 **天气**。 我们一开始知道天气影响需要它可以获得的所有 GPU 时间，因此，我们特意设计 UI 和地形，以减少任何过度绘制。

我们多次修改了 UI，以最大程度地减少它产生的过度绘制量。 对于闪烁按钮和地图概述等组件，我们在更复杂的几何图形方面出错，而不是相互叠加透明美。

对于地图，我们使用自定义着色器来去除标准 Unity 功能（如阴影和复杂照明），将其替换为简单的单一光照模型和自定义光照计算。 这生成了简单的像素着色器，并释放了 GPU 周期。

我们成功地使 UI 和地图都按预算呈现，因为根据硬件，我们不需要对它们进行更改;但是，天气可视化效果（尤其是云渲染）证明更具挑战性！

## <a name="background-on-cloud-data"></a>云数据的背景

我们的云数据从 NOAA 服务器 (下载，并进入三个不同的 2D 层，每个层具有云的顶部和底部高度，以及网格的每个单元的云 https://nomads.ncep.noaa.gov/) 密度。 数据已处理到云信息纹理中，其中每个组件都存储在纹理的红色、绿色和蓝色组件中，便于在 GPU 上访问。

## <a name="geometry-clouds"></a>几何云

若要确保低功率计算机能够呈现云，我们决定从一种使用纯几何图形来最大程度地减少过度绘制的方法开始。

我们首先尝试使用每个顶点的云信息纹理半径生成每个层的实心高度地图网格来生成云，以生成形状。 我们使用几何着色器在云的顶部和底部生成顶点，从而生成纯云形状。 我们使用了纹理中的密度值，以较深的颜色为云着色，使云更密集。

**用于创建顶点的着色器：**

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

我们引入了一个小干扰模式，以基于实际数据获取更多详细信息。 为了生成圆云边缘，当内插半径值达到阈值以丢弃接近零的值时，我们剪切了像素着色器中的像素。

![几何云](images/datascape-geometry-clouds-700px.jpg)

由于云是纯几何图形，因此可以在地形之前呈现它们，以隐藏下方的任何昂贵的地图像素，以进一步提高帧速率。 由于纯几何图形呈现方法，此解决方案在所有图形卡（从 min-spec 到高端图形卡）以及 HoloLens 上运行良好。

## <a name="solid-particle-clouds"></a>纯粒子云

我们现在有一个备份解决方案，它生成了云数据的适当表示形式，但在"wow"因素中有点缺乏，并且没有传达我们希望高端计算机具有的容量。

下一步是创建云，用大约 100，000 个粒子表示云，以生成更自然、更音量的外观。

如果粒子保持实心并按前对后排序，我们仍可从深度缓冲区剔除之前呈现的粒子后的像素中获益，从而减少过度绘制。 此外，使用基于粒子的解决方案，我们可以更改用于面向不同硬件的粒子量。 但是，仍然需要对所有像素进行深度测试，这会增加一些开销。

首先，我们在启动时围绕体验的中心点创建了粒子位置。 我们围绕中心更密集地分布粒子，在距离上分布得更少。 我们预先排序了从中心到背面的所有粒子，以便最靠近的粒子首先呈现。

计算着色器将采样云信息纹理，以将每个粒子定位在正确的高度，并基于密度设置其颜色。

我们使用了 *DrawProcedural* 来呈现每个粒子的四边形，使粒子数据可以一直停留在 GPU 上。

每个粒子同时包含高度和半径。 高度基于从云信息纹理中采样的云数据，半径基于初始分布，计算该分布以存储其最近邻域的水平距离。 四边形会使用此数据按高度倾斜自身，以便当用户水平查看它时，显示高度，当用户从上到下查看它时，将覆盖其相邻区域之间的区域。

![粒子形状](images/particle-shape-700px.png)

**显示分布的着色器代码：**

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

由于我们按前对后对粒子进行排序，并且仍使用纯色样式着色器来剪裁 (而不是混合) 透明像素，因此，此方法可处理意外数量的粒子，即使在低功率计算机上，也可避免代价高昂的过度绘制。

## <a name="transparent-particle-clouds"></a>透明粒子云

纯粒子为云的形状提供了良好的自然感觉，但仍需要一些产品来销售云的波动。 我们决定尝试高端图形卡的自定义解决方案，可在其中引入透明度。

为此，我们只需切换粒子的初始排序顺序，并更改着色器以使用纹理 alpha。

![浮云](images/fluffy-clouds-700px.jpg)

它看起来不错，但被证明对于最困难的计算机来说过于繁重，因为它会导致在屏幕上呈现每个像素数百次！

## <a name="render-off-screen-with-lower-resolution"></a>以较低的分辨率在屏幕外呈现

为了减少云呈现的像素数，我们开始在四分之一分辨率缓冲区中呈现它们 (与屏幕) 相比，在绘制完所有粒子后将最终结果拉伸回屏幕。 这为我们大约加快了 4 倍的速度，但有几个注意事项。

**在屏幕外呈现的代码：**

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

首先，在呈现到屏幕外缓冲区中时，我们丢失了主场景中的所有深度信息，导致在群顶上呈现后的粒子。

其次，拉伸缓冲区还会在云边缘上引入项目，其中分辨率更改明显。 接下来的两个部分将讨论我们如何解决这些问题。

## <a name="particle-depth-buffer"></a>粒子深度缓冲区

为了让粒子与一个世界几何图形共存，其中一个或一个云或对象可以覆盖其后面的粒子，我们使用包含主场景几何图形的深度缓冲区填充了屏幕外缓冲区。 为了生成此类深度缓冲区，我们创建了第二个相机，只呈现场景的纯几何图形和深度。

然后，我们使用云的像素着色器中的新纹理来遮挡像素。 我们使用相同的纹理来计算与云像素后面的几何图形的距离。 通过使用该距离，将其应用于像素的 alpha，我们现在在云接近地形时逐渐消失，从而消除了粒子和地形满足的任何硬剪切。

![与地形混合的云](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>增强边缘

拉伸云看起来几乎与粒子中心的正常大小云相同，或者它们重叠，但在云边缘上显示了一些项目。 否则，在移动相机时，清晰边缘看起来会模糊，并引入别名效果。

我们解决了这一问题，在屏幕外缓冲区上运行一个简单的着色器，以确定在 1 (中发生了) 。 我们将具有较大更改的像素放入新的模具缓冲区， (2) 。 然后，在将屏幕外缓冲区应用回屏幕时，我们使用了模具缓冲区来屏蔽这些高对比度区域，导致云中和周围出现 (3) 。

然后，我们在全屏模式下再次呈现所有粒子，但这一次使用模具缓冲区屏蔽除边缘外的所有内容，从而将最小像素集接触 4 (4) 。 由于已针对粒子创建了命令缓冲区，因此只需再次向新相机呈现它。

![呈现云边缘的进程](images/cloud-steps-1-4-700px.jpg)

最终结果是具有云中成本低的中心部分的边缘。

虽然这比全屏呈现所有粒子要快得多，但针对模具缓冲区测试像素仍有相关的成本，因此，大量过度绘制仍需要付费。

## <a name="culling-particles"></a>剔除粒子

对于风效果，我们在计算着色器中生成了长三角形带，从而在世界上产生许多风。 虽然由于生成的剥离带，风对填充速率的影响并不很大，但它生成了数十万个顶点，导致顶点着色器负载很大。

我们在计算着色器上引入了追加缓冲区，以馈送要绘制的一部分风条。 使用计算着色器中的一些简单视图 frustum culling 逻辑，我们可以确定条带是否位于相机视图之外，并防止将条带添加到推送缓冲区。 这大大减少了条带的数量，在 GPU 上释放了一些所需的周期。

**演示追加缓冲区的代码：**

*计算着色器：*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C# 代码：*

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

我们尝试在云粒子上使用相同的技术，在计算着色器上将其剔除，并仅推送要呈现的可见粒子。 此方法实际上不会在 GPU 上节省太多成本，因为最大的瓶颈是屏幕上呈现的像素量，而不是计算顶点的成本。

此技术的另一个问题在于，追加缓冲区由于计算粒子的并行化性质而按随机顺序填充，导致已排序的粒子未经排序，从而导致闪烁云粒子。

有一些技术可以对推送缓冲区进行排序，但我们从剔除粒子中获得的有限性能提升可能会因其他排序而偏移，因此，我们决定不采用这种优化。

## <a name="adaptive-rendering"></a>自适应渲染

为了确保在呈现条件各不相同（如云视图和清晰视图）的应用上稳定帧速率，我们向应用引入了自适应渲染。

自适应渲染的第一步是测量 GPU。 为此，我们在呈现帧的开头和结尾插入 GPU 命令缓冲区，并捕获左右眼屏幕时间。

通过测量呈现所花费的时间，并比较它与所需的刷新率，我们可以了解放置帧的接近度。

接近删除帧时，我们将调整呈现，使其更快。 调整的一种简单方法就是更改屏幕的视区大小，减少呈现像素。

通过使用 *UnityEngine.XR.XRSettings.renderViewportScale，* 系统收缩目标视区，并自动将结果向上拉伸以适应屏幕。 小比例变化对于世界几何图形来说几乎不明显，比例因子 0.7 需要呈现像素量的一半。

![70% 刻度，一半像素](images/datascape-scaling-700px.jpg)

当我们检测到即将删除帧时，我们会将缩放比例降低一个固定数字，当我们再次以足够快的速度运行时，再增加缩放比例。

虽然我们根据启动时硬件的图形功能决定使用什么云技术，但可以基于 GPU 度量的数据来阻止系统长时间保持低分辨率，但我们没有时间在 Datascape 中探索。

## <a name="final-thoughts"></a>结束语

面向各种硬件具有挑战性，需要进行一些规划。

建议开始面向低功率计算机，以熟悉问题空间，并开发将在所有计算机上运行的备份解决方案。 设计解决方案时，请注意填充速率，因为像素将是最宝贵的资源。 针对透明度的纯几何图形。

使用备份解决方案，可以针对高端计算机开始更复杂的分层，或者可能只是增强备份解决方案的解析。

针对最差情况进行设计，并可能考虑在繁重的情况下使用自适应渲染。

## <a name="about-the-authors"></a>关于作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert 使用</b><br>软件工程师 @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>软件工程师 @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>另请参阅
* [了解混合现实的性能](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity 推荐性能](../develop/unity/performance-recommendations-for-unity.md)

 
