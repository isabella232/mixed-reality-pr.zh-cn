---
ms.openlocfilehash: c3775dc73f41b822c233d8fc4ec62459e789b89f
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2021
ms.locfileid: "122264009"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**命名空间：** *MixedReality。 Toolkit。WindowsMixedReality*<br>
**类型：** *WindowsMixedRealityUtilities*

MRTK 通过 **WindowsMixedRealityUtilities** 类在旧式 WSA 和 XR SDK 中提供已封送的类型。

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="windows-xr-plugin"></a>[WindowsXR 插件](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**命名空间：** *UnityEngine. XR. WindowsMR*<br>
**类型：** *WindowsMREnvironment*

Static **WindowsMREnvironment** 类提供对多个本机指针的访问。

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**命名空间：** *UnityEngine. XR*<br>
**类型：** *XRDevice*

<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a>类型允许使用 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法获取对基础本机对象的访问权限。 不同平台之间的 GetNativePtr 返回内容有所不同。 在针对 Windows Mixed Reality 的通用 Windows 平台上，XRDevice 会返回 (IntPtr) 的指针到以下结构：

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

可以使用 Marshal.ptrtostructure 方法将其转换为 HolographicFrameNativeData：

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** 是一个作为 unmanagedtype.bool 进行封送的 IntPtr 数组，其长度等于 MaxNumberOfCameras*
