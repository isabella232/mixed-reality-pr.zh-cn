---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475068"
---
# <a name="mrtk"></a>[<span data-ttu-id="9af2e-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="9af2e-101">MRTK</span></span>](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a><span data-ttu-id="9af2e-102">WindowsMixedRealityUtilities</span><span class="sxs-lookup"><span data-stu-id="9af2e-102">WindowsMixedRealityUtilities</span></span>

<span data-ttu-id="9af2e-103">**命名空间：** *MixedReality. WindowsMixedReality*</span><span class="sxs-lookup"><span data-stu-id="9af2e-103">**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*</span></span><br>
<span data-ttu-id="9af2e-104">**类型：** *WindowsMixedRealityUtilities*</span><span class="sxs-lookup"><span data-stu-id="9af2e-104">**Type:** *WindowsMixedRealityUtilities*</span></span>

<span data-ttu-id="9af2e-105">MRTK 通过 **WindowsMixedRealityUtilities** 类在旧式 WSA 和 XR SDK 中提供已封送的类型。</span><span class="sxs-lookup"><span data-stu-id="9af2e-105">MRTK provides already-marshalled types across both legacy WSA and XR SDK through the **WindowsMixedRealityUtilities** class.</span></span>

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[<span data-ttu-id="9af2e-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="9af2e-106">XR SDK</span></span>](#tab/xr)

## <a name="windowsmrenvironment"></a><span data-ttu-id="9af2e-107">WindowsMREnvironment</span><span class="sxs-lookup"><span data-stu-id="9af2e-107">WindowsMREnvironment</span></span>

<span data-ttu-id="9af2e-108">**命名空间：** *UnityEngine. XR. WindowsMR*</span><span class="sxs-lookup"><span data-stu-id="9af2e-108">**Namespace:** *UnityEngine.XR.WindowsMR*</span></span><br>
<span data-ttu-id="9af2e-109">**类型：** *WindowsMREnvironment*</span><span class="sxs-lookup"><span data-stu-id="9af2e-109">**Type:** *WindowsMREnvironment*</span></span>

<span data-ttu-id="9af2e-110">Static **WindowsMREnvironment** 类提供对多个本机指针的访问。</span><span class="sxs-lookup"><span data-stu-id="9af2e-110">The static **WindowsMREnvironment** class provides access to several native pointers.</span></span>

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="9af2e-111">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="9af2e-111">Legacy WSA</span></span>](#tab/wsa)

## <a name="xrdevice"></a><span data-ttu-id="9af2e-112">XRDevice</span><span class="sxs-lookup"><span data-stu-id="9af2e-112">XRDevice</span></span>

<span data-ttu-id="9af2e-113">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="9af2e-113">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="9af2e-114">**类型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="9af2e-114">**Type:** *XRDevice*</span></span>

<span data-ttu-id="9af2e-115"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a>类型允许使用 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法获取对基础本机对象的访问权限。</span><span class="sxs-lookup"><span data-stu-id="9af2e-115">The <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="9af2e-116">不同平台之间的 GetNativePtr 返回内容有所不同。</span><span class="sxs-lookup"><span data-stu-id="9af2e-116">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="9af2e-117">在针对 Windows Mixed Reality 的通用 Windows 平台上，GetNativePtr 将返回一个指针 (IntPtr) 到以下结构：</span><span class="sxs-lookup"><span data-stu-id="9af2e-117">On the Universal Windows Platform when targeting Windows Mixed Reality, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span>

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

<span data-ttu-id="9af2e-118">可以使用 Marshal.ptrtostructure 方法将其转换为 HolographicFrameNativeData：</span><span class="sxs-lookup"><span data-stu-id="9af2e-118">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

<span data-ttu-id="9af2e-119">***IHolographicCameraPtr** 是一个作为 unmanagedtype.bool 进行封送的 IntPtr 数组，其长度等于 MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="9af2e-119">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span>
