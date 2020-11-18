---
title: Unreal 中的 HoloLens 照片/视频摄像头
description: Unreal 中 HoloLens 照片/视频摄像头使用指南
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 摄像头, PV 摄像头, MRC
ms.openlocfilehash: 6302a64fcde2a16b6ae1cb570215629a3e6ea9e5
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573231"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="e6154-104">Unreal 中的 HoloLens 照片/视频摄像头</span><span class="sxs-lookup"><span data-stu-id="e6154-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="e6154-105">概述</span><span class="sxs-lookup"><span data-stu-id="e6154-105">Overview</span></span>

<span data-ttu-id="e6154-106">HoloLens 具有照片/视频 (PV) 摄像头，可用于混合现实捕获 (MRC)，应用还可以使用它来访问真实的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="e6154-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="e6154-107">全息远程不支持 PV 摄像头，但可使用电脑上附带的网络摄像头来模拟 HoloLens PV 摄像头功能。</span><span class="sxs-lookup"><span data-stu-id="e6154-107">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="e6154-108">从 MRC 的 PV 摄像头渲染</span><span class="sxs-lookup"><span data-stu-id="e6154-108">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="e6154-109">这需要 Unreal Engine 4.25 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e6154-109">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="e6154-110">系统和自定义 MRC 记录器通过将 PV 摄像头与沉浸式应用渲染的全息影像结合在一起，创建混合现实捕获。</span><span class="sxs-lookup"><span data-stu-id="e6154-110">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="e6154-111">默认情况下，混合现实捕获使用右眼的全息影像输出。</span><span class="sxs-lookup"><span data-stu-id="e6154-111">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="e6154-112">如果沉浸式应用选择[从 PV 摄像头进行渲染](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，则会改用它。</span><span class="sxs-lookup"><span data-stu-id="e6154-112">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="e6154-113">这改进了真实世界与 MRC 视频中全息影像之间的映射。</span><span class="sxs-lookup"><span data-stu-id="e6154-113">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="e6154-114">若要选择从 PV 摄像机进行渲染：</span><span class="sxs-lookup"><span data-stu-id="e6154-114">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="e6154-115">调用 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera </span><span class="sxs-lookup"><span data-stu-id="e6154-115">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="e6154-116">使用“尺寸 X”和“尺寸 Y”值设置视频尺寸。 </span><span class="sxs-lookup"><span data-stu-id="e6154-116">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第三人称摄像头](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="e6154-118">然后，Unreal 将处理 MRC 要从 PV 摄像头的角度进行渲染的请求。</span><span class="sxs-lookup"><span data-stu-id="e6154-118">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="e6154-119">仅当触发[混合现实捕获](../../mixed-reality-capture.md)时，才会要求应用从照片/视频摄像头的角度进行渲染。</span><span class="sxs-lookup"><span data-stu-id="e6154-119">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="e6154-120">使用 PV 摄像头</span><span class="sxs-lookup"><span data-stu-id="e6154-120">Using the PV Camera</span></span>

<span data-ttu-id="e6154-121">在游戏中，可以在运行时检索网络摄像头纹理，但需要在编辑器的“编辑 > 项目设置”中启用它：</span><span class="sxs-lookup"><span data-stu-id="e6154-121">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="e6154-122">转到“平台 > HoloLens > 功能”，然后选中“网络摄像头”。 </span><span class="sxs-lookup"><span data-stu-id="e6154-122">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="e6154-123">在运行时通过 StartCameraCapture 函数使用网络摄像头，通过 StopCameraCapture 函数停止录像。 </span><span class="sxs-lookup"><span data-stu-id="e6154-123">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![摄像头开始/停止](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="e6154-125">渲染图像</span><span class="sxs-lookup"><span data-stu-id="e6154-125">Rendering an image</span></span>
<span data-ttu-id="e6154-126">渲染摄像头图像：</span><span class="sxs-lookup"><span data-stu-id="e6154-126">To render the camera image:</span></span>
1. <span data-ttu-id="e6154-127">基于项目中的材料创建动态材料实例，下方的屏幕截图将其命名为“PVCamMat”。</span><span class="sxs-lookup"><span data-stu-id="e6154-127">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="e6154-128">将动态材料实例设置为“材料实例动态对象引用”变量。</span><span class="sxs-lookup"><span data-stu-id="e6154-128">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="e6154-129">设置场景中的对象的材料，它会将摄像头源渲染到这个新的动态材料实例。</span><span class="sxs-lookup"><span data-stu-id="e6154-129">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="e6154-130">启动计时器，用于将摄像头图像与材料绑定。</span><span class="sxs-lookup"><span data-stu-id="e6154-130">Start a timer that will be used to bind the camera image to the material.</span></span>

![摄像头渲染](images/unreal-camera-render.PNG)

4. <span data-ttu-id="e6154-132">为此计时器创建新函数（在本例中为 MaterialTimer），并调用 GetARCameraImage 从网络摄像头获取纹理。 </span><span class="sxs-lookup"><span data-stu-id="e6154-132">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="e6154-133">如果此纹理有效，则将着色器中的纹理参数设置为此图像。</span><span class="sxs-lookup"><span data-stu-id="e6154-133">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="e6154-134">否则，请重新启动材质计时器。</span><span class="sxs-lookup"><span data-stu-id="e6154-134">Otherwise, start the material timer again.</span></span>

![来自网络摄像头的摄像头纹理](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="e6154-136">请确保材料的参数与绑定到颜色条目的 SetTextureParameterValue 中的名称匹配，</span><span class="sxs-lookup"><span data-stu-id="e6154-136">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="e6154-137">否则将无法正确显示摄像头图像。</span><span class="sxs-lookup"><span data-stu-id="e6154-137">Without this, the camera image can't be properly displayed.</span></span>

![摄像头纹理](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="e6154-139">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="e6154-139">Next Development Checkpoint</span></span>

<span data-ttu-id="e6154-140">如果你遵循我们规划的 Unreal 开发检查点历程，则你处于探索混合现实平台功能和 API 的过程之中。</span><span class="sxs-lookup"><span data-stu-id="e6154-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="e6154-141">从这里，你可以进入下一主题：</span><span class="sxs-lookup"><span data-stu-id="e6154-141">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e6154-142">QR 码</span><span class="sxs-lookup"><span data-stu-id="e6154-142">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="e6154-143">或直接跳到在设备或模拟器上部署应用：</span><span class="sxs-lookup"><span data-stu-id="e6154-143">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e6154-144">部署到设备</span><span class="sxs-lookup"><span data-stu-id="e6154-144">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="e6154-145">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#3-platform-capabilities-and-apis)。</span><span class="sxs-lookup"><span data-stu-id="e6154-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6154-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6154-146">See also</span></span>
* [<span data-ttu-id="e6154-147">可定位相机</span><span class="sxs-lookup"><span data-stu-id="e6154-147">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="e6154-148">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="e6154-148">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
