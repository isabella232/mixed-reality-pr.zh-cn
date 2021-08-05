---
ms.openlocfilehash: 78296dd4e6667c34926c954774547b21a223c5f4b6635476c51046c7ca22cdc3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208394"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**命名空间***：Microsoft.MixedReality.Toolkit。WindowsMixedReality*<br>
**类型***：WindowsMixedRealityUtilities*

MRTK 通过 **WindowsMixedRealityUtilities** 类跨旧版 WSA 和 XR SDK 提供已封送的类型。

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**命名空间***：UnityEngine.XR.WindowsMR*<br>
**类型***：WindowsMREnvironment*

静态 **WindowsMREnvironment** 类提供对多个本机指针的访问。

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**命名空间***：UnityEngine.XR*<br>
**类型***：XRDevice*

<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a>类型允许使用 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法访问基础本机对象。 GetNativePtr 返回的信息因平台而异。 在面向 Windows 平台Windows Mixed Reality，XRDevice.GetNativePtr 返回指向 (IntPtr) 的指针：

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame
    public IntPtr IHolographicCameraPtr; // Windows::Graphics::Holographic::IHolographicCamera
}
```

可以使用 Marshal.PtrToStructure 方法将其转换为 HolographicFrameNativeData：

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** 是 IntPtr 数组，作为 UnmanagedType.ByValArray 封送，长度等于 MaxNumberOfCameras*
