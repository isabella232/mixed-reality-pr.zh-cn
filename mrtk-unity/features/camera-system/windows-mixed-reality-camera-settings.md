---
title: Windows Mixed Reality 照相机设置
description: 在 MRTK Windows Mixed Reality相机的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 相机，
ms.openlocfilehash: 94e00f47dc565af0824ef6acf5c08a9e99d4529f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145167"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="aef9d-104">Windows Mixed Reality相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="aef9d-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="aef9d-105">Windows Mixed Reality相机设置提供程序确定运行应用程序的设备类型，并基于显示器的透明或不透明 (应用相应的) 。</span><span class="sxs-lookup"><span data-stu-id="aef9d-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="aef9d-106">启用Windows Mixed Reality设置提供程序</span><span class="sxs-lookup"><span data-stu-id="aef9d-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="aef9d-107">以下步骤将预先使用 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="aef9d-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="aef9d-108">其他服务注册机构所需的步骤可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="aef9d-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="aef9d-109">选择场景层次结构中的 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="aef9d-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="aef9d-111">将"检查器"面板导航到"相机系统"部分，然后展开" **相机设置提供程序"** 部分。</span><span class="sxs-lookup"><span data-stu-id="aef9d-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展开设置提供程序](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="aef9d-113">单击 **"添加相机设置提供程序"，** 然后展开新 **添加的"新建相机设置"** 条目。</span><span class="sxs-lookup"><span data-stu-id="aef9d-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展开新设置提供程序](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="aef9d-115">选择Windows Mixed Reality设置提供程序</span><span class="sxs-lookup"><span data-stu-id="aef9d-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![选择Windows Mixed Reality设置提供程序](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="aef9d-117">使用 Microsoft Mixed Reality Toolkit 默认配置文件时，Windows Mixed Reality相机设置提供程序已启用并配置。</span><span class="sxs-lookup"><span data-stu-id="aef9d-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="aef9d-118">配置Windows Mixed Reality设置提供程序</span><span class="sxs-lookup"><span data-stu-id="aef9d-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="aef9d-119">Windows Mixed Reality相机设置还支持配置文件。</span><span class="sxs-lookup"><span data-stu-id="aef9d-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="aef9d-120">此配置文件提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="aef9d-120">This profile provides the following options:</span></span>

![Windows Mixed Reality相机设置配置](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="aef9d-122">从照片/视频摄像机呈现混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="aef9d-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="aef9d-123">在 HoloLens 2 上使用此设置，你可以在混合现实捕获中启用全息图对齐。</span><span class="sxs-lookup"><span data-stu-id="aef9d-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="aef9d-124">如果已启用，则在采用混合现实捕获照片或视频时，平台将为应用提供附加的 HolographicCamera。</span><span class="sxs-lookup"><span data-stu-id="aef9d-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="aef9d-125">此 HolographicCamera 提供与照片/视频摄像机位置对应的视图矩阵，并使用视图的 "照片/视频相机" 字段提供投影矩阵。</span><span class="sxs-lookup"><span data-stu-id="aef9d-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="aef9d-126">这将确保全息影像（如手写网格）在视频输出中保持明显对齐。</span><span class="sxs-lookup"><span data-stu-id="aef9d-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="aef9d-127">HoloLens 2 reprojection 方法</span><span class="sxs-lookup"><span data-stu-id="aef9d-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="aef9d-128">为 HoloLens 2 reprojection 设置初始方法。</span><span class="sxs-lookup"><span data-stu-id="aef9d-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="aef9d-129">默认的建议是使用深度 reprojection，因为场景的所有部分都将基于用户与用户之间的距离进行单独的稳定。</span><span class="sxs-lookup"><span data-stu-id="aef9d-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="aef9d-130">如果全息影像仍显示不稳定，请尝试确保所有对象已正确地将其深度提交到深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="aef9d-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="aef9d-131">这有时是着色器设置。</span><span class="sxs-lookup"><span data-stu-id="aef9d-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="aef9d-132">如果深度看上去正确并仍存在不稳定，请尝试 autoplanar 稳定性，它使用深度缓冲区来计算稳定平面。</span><span class="sxs-lookup"><span data-stu-id="aef9d-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="aef9d-133">如果某个应用无法为这些选项中的任何一个提供足够的深度数据可供使用，则将平面 reprojection 作为回退提供。</span><span class="sxs-lookup"><span data-stu-id="aef9d-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="aef9d-134">此方法将基于通过 [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)提供的应用提供的焦点数据。</span><span class="sxs-lookup"><span data-stu-id="aef9d-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="aef9d-135">若要在运行时更新 reprojection 方法，请访问， `WindowsMixedRealityReprojectionUpdater` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="aef9d-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="aef9d-136">这只需更新一次，并为所有后续帧重复使用该值。</span><span class="sxs-lookup"><span data-stu-id="aef9d-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="aef9d-137">如果此方法将会频繁更新，则建议缓存的结果， `EnsureComponent` 而不是经常调用它。</span><span class="sxs-lookup"><span data-stu-id="aef9d-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="aef9d-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aef9d-138">See also</span></span>

- [<span data-ttu-id="aef9d-139">照相机系统概述</span><span class="sxs-lookup"><span data-stu-id="aef9d-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="aef9d-140">创建照相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="aef9d-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="aef9d-141">通过 PV 相机呈现混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="aef9d-141">Rendering Mixed Reality Capture from the PV camera</span></span>](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="aef9d-142">全息 reprojection</span><span class="sxs-lookup"><span data-stu-id="aef9d-142">Holographic reprojection</span></span>](/windows/mixed-reality/hologram-stability#reprojection)