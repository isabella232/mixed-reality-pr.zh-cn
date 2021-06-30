---
title: Windows Mixed Reality相机设置
description: 在 MRTK Windows Mixed Reality相机设置的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 相机，
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121635"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="74dea-104">Windows Mixed Reality相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="74dea-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="74dea-105">Windows Mixed Reality相机设置提供程序确定运行应用程序的设备类型，并基于显示器的透明或不透明 (应用相应的) 。</span><span class="sxs-lookup"><span data-stu-id="74dea-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="74dea-106">启用Windows Mixed Reality设置提供程序</span><span class="sxs-lookup"><span data-stu-id="74dea-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="74dea-107">以下步骤将预先使用 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="74dea-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="74dea-108">其他服务注册机构所需的步骤可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="74dea-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="74dea-109">选择场景层次结构中的 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="74dea-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="74dea-111">将"检查器"面板导航到"相机系统"部分，然后展开" **相机设置提供程序"** 部分。</span><span class="sxs-lookup"><span data-stu-id="74dea-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展开设置提供程序](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="74dea-113">单击 **"添加相机设置提供程序"，** 然后展开新 **添加的"新建相机设置"** 条目。</span><span class="sxs-lookup"><span data-stu-id="74dea-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展开新设置提供程序](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="74dea-115">选择Windows Mixed Reality设置提供程序</span><span class="sxs-lookup"><span data-stu-id="74dea-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![选择Windows Mixed Reality设置提供程序](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="74dea-117">使用 Microsoft Mixed Reality Toolkit 默认配置文件时，Windows Mixed Reality相机设置提供程序已启用并配置。</span><span class="sxs-lookup"><span data-stu-id="74dea-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="74dea-118">配置Windows Mixed Reality设置提供程序</span><span class="sxs-lookup"><span data-stu-id="74dea-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="74dea-119">Windows Mixed Reality相机设置还支持配置文件。</span><span class="sxs-lookup"><span data-stu-id="74dea-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="74dea-120">此配置文件提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="74dea-120">This profile provides the following options:</span></span>

![Windows Mixed Reality相机设置配置](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="74dea-122">从照片/视频相机渲染混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="74dea-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="74dea-123">使用此设置HoloLens 2，可以在混合现实捕获中启用全息影像对齐。</span><span class="sxs-lookup"><span data-stu-id="74dea-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="74dea-124">如果启用，该平台将在拍摄混合现实捕获照片或视频时向应用提供额外的 HolographicCamera。</span><span class="sxs-lookup"><span data-stu-id="74dea-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="74dea-125">此 HolographicCamera 提供与照片/视频相机位置对应的视图矩阵，并且它使用照片/视频相机视场提供投影矩阵。</span><span class="sxs-lookup"><span data-stu-id="74dea-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="74dea-126">这将确保全息影像（如手部网格）在视频输出中保持可见对齐。</span><span class="sxs-lookup"><span data-stu-id="74dea-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="74dea-127">HoloLens 2重现方法</span><span class="sxs-lookup"><span data-stu-id="74dea-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="74dea-128">设置用于重新HoloLens 2的初始方法。</span><span class="sxs-lookup"><span data-stu-id="74dea-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="74dea-129">默认建议是使用深度重新项目，因为场景的所有部分都将根据它们与用户的距离独立稳定。</span><span class="sxs-lookup"><span data-stu-id="74dea-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="74dea-130">如果全息影像看起来仍不稳定，请尝试确保所有对象已正确将深度提交到深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="74dea-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="74dea-131">这有时是着色器设置。</span><span class="sxs-lookup"><span data-stu-id="74dea-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="74dea-132">如果深度似乎已正确提交，并且不稳定仍然存在，请尝试自动平面稳定，它使用深度缓冲区来计算稳定平面。</span><span class="sxs-lookup"><span data-stu-id="74dea-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="74dea-133">如果应用无法提交足够的深度数据供其中任一选项使用，则平面重新保护作为回退提供。</span><span class="sxs-lookup"><span data-stu-id="74dea-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="74dea-134">此方法将基于应用通过 [SetFocusPointForFrame 提供的焦点数据](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)。</span><span class="sxs-lookup"><span data-stu-id="74dea-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="74dea-135">若要在运行时更新 reprojection 方法，请如下所示 `WindowsMixedRealityReprojectionUpdater` 访问 ：</span><span class="sxs-lookup"><span data-stu-id="74dea-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="74dea-136">只需更新一次，该值将重新用于所有后续帧。</span><span class="sxs-lookup"><span data-stu-id="74dea-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="74dea-137">如果方法将频繁更新，则建议缓存 的结果， `EnsureComponent` 而不是经常调用它。</span><span class="sxs-lookup"><span data-stu-id="74dea-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="74dea-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74dea-138">See also</span></span>

- [<span data-ttu-id="74dea-139">照相机系统概述</span><span class="sxs-lookup"><span data-stu-id="74dea-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="74dea-140">创建相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="74dea-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="74dea-141">从 PV 混合现实捕获渲染图像</span><span class="sxs-lookup"><span data-stu-id="74dea-141">Rendering Mixed Reality Capture from the PV camera</span></span>](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="74dea-142">全息重新投影</span><span class="sxs-lookup"><span data-stu-id="74dea-142">Holographic reprojection</span></span>](/windows/mixed-reality/hologram-stability#reprojection)