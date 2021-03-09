---
title: Unity 中的混合现实原生对象
description: 了解如何使用 XR 命名空间访问 Unity 中的基础全息本机对象。
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: unity，mixed reality，native，xrdevice，spatialcoordinatesystem，holographicframe，holographiccamera，ispatialcoordinatesystem，iholographicframe，iholographiccamera，getnativeptr，mixed reality 耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475067"
---
# <a name="mixed-reality-native-interop-in-unity"></a>Unity 中的混合现实本机互操作

每个混合现实应用都在开始接收相机数据和渲染帧之前 [获得 HolographicSpace](../native/getting-a-holographicspace.md) 。 在 Unity 中，引擎负责处理这些步骤，处理全息对象和内部更新作为其呈现循环的一部分。

但是，在高级方案中，可能需要访问基础本机对象，例如 <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> 和 current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>。

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>取消封送本机指针

`IntPtr`从上述其中一个方法获取 (不需要 MRTK) ，请使用以下代码段将它们封送到托管对象。

如果你使用的是 [MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)，则可以使用方法从本机指针构造托管对象 `FromNativePtr()` ：

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

否则，请使用 `Marshal.GetObjectForIUnknown()` 并强制转换为所需的类型：

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a>坐标系统之间的转换

Unity 使用左手坐标系，而 Windows 感知 Api 使用右手坐标系。 若要在这两种约定之间进行转换，可以使用以下帮助器：

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(q.X, q.Y, -q.Z, -q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(q.x, q.y, -q.z, -q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a>使用 HolographicFrame 本机数据

> [!NOTE]
> 更改通过 HolographicFrameNativeData 接收的本机对象的状态可能会导致不可预知的行为和呈现项目，特别是当 Unity 也导致相同状态时。  例如，您不应调用 HolographicFrame. UpdateCurrentPrediction，否则 Unity 呈现与该框架的姿势预测将与 Windows 所需的姿势不同步，这将减少全息图的 [稳定性](../platform-capabilities-and-apis/hologram-stability.md)。

如果需要访问本机接口以进行呈现或调试，请在本机插件或 c # 代码中使用 HolographicFrameNativeData 中的数据。

下面是一个示例，说明如何使用 HolographicFrameNativeData 通过 XR SDK 扩展获取当前帧预测的 photon 时间。

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if ENABLE_WINMD_SUPPORT
    IntPtr holographicFramePtr = UnityEngine.XR.WindowsMR.WindowsMREnvironment.CurrentHolographicRenderFrame;

    if (holographicFramePtr != IntPtr.Zero)
    {
        var holographicFrame = Marshal.GetObjectForIUnknown(holographicFramePtr) as Windows.Graphics.Holographic.HolographicFrame;
        frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
        return true;
    }
#endif

    frameDateTime = DateTime.MinValue;
    return false;
}
```

## <a name="see-also"></a>另请参阅

* [将 Windows 命名空间与 Unity 应用配合用于 HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [在 DirectX 中渲染](../native/rendering-in-directx.md)
