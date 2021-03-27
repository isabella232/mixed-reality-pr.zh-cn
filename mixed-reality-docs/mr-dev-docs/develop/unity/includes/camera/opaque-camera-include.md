---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636264"
---
# <a name="mrtk"></a>[<span data-ttu-id="daf52-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="daf52-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="daf52-102">MRTK 将基于 [照相机系统配置文件中的配置](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)自动处理特定相机设置。</span><span class="sxs-lookup"><span data-stu-id="daf52-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="daf52-103">**命名空间：** *MixedReality. CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="daf52-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="daf52-104">**类型：** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="daf52-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="daf52-105">若要检查相机的 opaqueness，MixedRealityCamera 系统具有 [ `IsOpaque` 属性](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque)。</span><span class="sxs-lookup"><span data-stu-id="daf52-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="daf52-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="daf52-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="daf52-107">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="daf52-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="daf52-108">**类型：** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="daf52-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="daf52-109">你可以使用脚本代码来确定在运行时，耳机是沉浸式还是全息的，因为在主动运行的[XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)上检查[displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) 。</span><span class="sxs-lookup"><span data-stu-id="daf52-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="daf52-110">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="daf52-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="daf52-111">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="daf52-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="daf52-112">**类型：** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="daf52-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="daf52-113">您可以使用脚本代码，通过检查 [HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)来确定头戴式耳机是沉浸还是全息。</span><span class="sxs-lookup"><span data-stu-id="daf52-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>