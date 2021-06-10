---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748468"
---
# <a name="mrtk"></a>[<span data-ttu-id="622f0-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="622f0-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="622f0-102">MRTK 将基于相机系统配置文件 中的配置自动 [处理特定的相机设置](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)。</span><span class="sxs-lookup"><span data-stu-id="622f0-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="622f0-103">\**命名空间\*\*\*：Microsoft.MixedReality.Toolkit.CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="622f0-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="622f0-104">\**类型\*\*\*：MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="622f0-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="622f0-105">为了检查相机的不透明性，MixedRealityCamera 系统具有 [ `IsOpaque` 属性](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)。</span><span class="sxs-lookup"><span data-stu-id="622f0-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="622f0-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="622f0-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="622f0-107">\**命名空间\*\*\*：UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="622f0-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="622f0-108">\**类型\*\*\*：XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="622f0-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="622f0-109">可以使用脚本代码在运行时通过检查主动运行的[XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)上的[displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html)来确定头戴显示设备是沉浸式还是全息的。</span><span class="sxs-lookup"><span data-stu-id="622f0-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="622f0-110">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="622f0-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="622f0-111">\**命名空间\*\*\*：UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="622f0-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="622f0-112">\**类型\*\*\*：HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="622f0-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="622f0-113">可以使用脚本代码在运行时通过检查 [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)来确定头戴显示设备是沉浸式还是全息。</span><span class="sxs-lookup"><span data-stu-id="622f0-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>