---
title: Unity 中的混合现实原生对象
description: 了解如何使用 XR 命名空间在 Unity 中访问基础全息本机对象。
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: unity， 混合现实， 本机， xrdevice， spatialcoordinatesystem， holographicframe， holographiccamera， ispatialcoordinatesystem， iholographicframe， iholographiccamera， getnativeptr， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: 63ee9c33a972cb918f141df3b4c1608a561b96dc5c37910deb77b089f7be69b8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208395"
---
# <a name="mixed-reality-native-interop-in-unity"></a>Unity 中的混合现实本机互操作

每个混合现实应用在开始接收相机数据和渲染帧之前，都会获得一个[HolographicSpace。](../native/getting-a-holographicspace.md) 在 Unity 中，引擎会处理这些步骤，处理全息对象，并在其呈现循环中内部更新。

但是，在高级方案中，可能需要访问基础本机对象，例如 <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> 和当前的 <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>。

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>取消引用本机指针

从上述方法之一 (MRTK) ，使用以下代码片段将它们封送 `IntPtr` 到托管对象。

如果使用[Microsoft.Windows。MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)，可以使用 方法从本机指针构造 `FromNativePtr()` 托管对象：

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

否则， `Marshal.GetObjectForIUnknown()` 请使用 并强制转换到想要的类型：

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a>在坐标系统之间转换

Unity 使用左手坐标系，而Windows感知 API 使用右手坐标系。 若要在两个约定之间转换，可以使用以下帮助程序：

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
> 更改通过 HolographicFrameNativeData 接收的本机对象的状态可能会导致不可预知的行为和呈现项目，尤其是在 Unity 也导致同一状态时。  例如，不应调用 HolographicFrame.UpdateCurrentPrediction，否则 Unity 使用该帧呈现的姿势预测将与 Windows 期望的姿势不同步，这将降低全息影像[的稳定性。](../platform-capabilities-and-apis/hologram-stability.md)

如果需要访问本机接口进行呈现或调试，请使用本机插件或 C# 代码中 HolographicFrameNativeData 的数据。

以下示例演示了如何使用 HolographicFrameNativeData 通过 XR SDK 扩展获取当前帧对光子时间的预测。

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
