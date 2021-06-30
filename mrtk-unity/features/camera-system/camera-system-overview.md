---
title: 相机系统概述
description: MRTK 中相机系统的登陆页
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 相机，
ms.openlocfilehash: e3b7caacaa9baa67fd81f6d32f3fd8c9f123e66d
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121285"
---
# <a name="camera-system"></a><span data-ttu-id="970f7-104">相机系统</span><span class="sxs-lookup"><span data-stu-id="970f7-104">Camera system</span></span>

<span data-ttu-id="970f7-105">借助相机系统，Microsoft Mixed Reality Toolkit 可以配置和优化应用程序的相机，以用于混合现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="970f7-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="970f7-106">使用相机系统，可以编写应用程序来支持不透明的 (例如：虚拟现实) 和透明 (，例如 Microsoft HoloLens) 设备，无需编写代码来区分和适应每种类型的显示器。</span><span class="sxs-lookup"><span data-stu-id="970f7-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="970f7-107">启用相机系统</span><span class="sxs-lookup"><span data-stu-id="970f7-107">Enabling the camera system</span></span>

<span data-ttu-id="970f7-108">相机系统由 MixedRealityToolkit 对象 (或其他服务注册器组件) 。</span><span class="sxs-lookup"><span data-stu-id="970f7-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="970f7-109">以下步骤将预先使用 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="970f7-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="970f7-110">其他服务注册机构所需的步骤可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="970f7-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="970f7-111">选择场景层次结构中的 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="970f7-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="970f7-113">将检查器面板导航到相机系统部分，并确保选中" **启用相机系统** "。</span><span class="sxs-lookup"><span data-stu-id="970f7-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![启用相机系统](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="970f7-115">选择相机系统实现。</span><span class="sxs-lookup"><span data-stu-id="970f7-115">Select the camera system implementation.</span></span> <span data-ttu-id="970f7-116">MRTK 提供的默认类实现是 `MixedRealityCameraSystem` 。</span><span class="sxs-lookup"><span data-stu-id="970f7-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![选择相机系统实现](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="970f7-118">选择所需的配置文件</span><span class="sxs-lookup"><span data-stu-id="970f7-118">Select the desired configuration profile</span></span>

    ![选择相机系统配置文件](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="970f7-120">配置相机系统</span><span class="sxs-lookup"><span data-stu-id="970f7-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="970f7-121">设置提供程序</span><span class="sxs-lookup"><span data-stu-id="970f7-121">Settings providers</span></span>

![相机设置提供程序](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="970f7-123">相机设置提供程序启用相机的平台特定配置。</span><span class="sxs-lookup"><span data-stu-id="970f7-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="970f7-124">这些设置可能包括自定义配置步骤和/或组件。</span><span class="sxs-lookup"><span data-stu-id="970f7-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="970f7-125">可以通过单击"添加相机设置提供程序 **"按钮来添加** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="970f7-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="970f7-126">可以通过单击提供程序名称右边的按钮 **-** 来删除它们。</span><span class="sxs-lookup"><span data-stu-id="970f7-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="970f7-127">并非所有平台都需要相机设置提供程序。</span><span class="sxs-lookup"><span data-stu-id="970f7-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="970f7-128">如果没有与运行应用程序的平台兼容的提供程序，Microsoft Mixed Reality Toolkit 将应用基本默认值。</span><span class="sxs-lookup"><span data-stu-id="970f7-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="970f7-129">显示设置</span><span class="sxs-lookup"><span data-stu-id="970f7-129">Display settings</span></span>

![相机显示设置](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="970f7-131">为不透明对象指定显示 (例如：虚拟现实) 和 (显示Microsoft HoloLens) 设置。</span><span class="sxs-lookup"><span data-stu-id="970f7-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="970f7-132">相机是使用这些设置运行时配置的。</span><span class="sxs-lookup"><span data-stu-id="970f7-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="970f7-133">**近剪辑**</span><span class="sxs-lookup"><span data-stu-id="970f7-133">**Near Clip**</span></span>

<span data-ttu-id="970f7-134">近剪贴平面最接近虚拟对象与相机的距离（以米为单位）并且仍可呈现。</span><span class="sxs-lookup"><span data-stu-id="970f7-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="970f7-135">为获得最大的用户舒适感，建议将此值大于零。</span><span class="sxs-lookup"><span data-stu-id="970f7-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="970f7-136">上图包含各种设备上已发现的舒适值。</span><span class="sxs-lookup"><span data-stu-id="970f7-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="970f7-137">**Far Clip**</span><span class="sxs-lookup"><span data-stu-id="970f7-137">**Far Clip**</span></span>

<span data-ttu-id="970f7-138">最远的剪辑平面是虚拟对象可以到达相机且仍可呈现的最远（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="970f7-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="970f7-139">对于透明设备，建议此值相对接近，因为不要过度超过现实世界空间，并破坏应用程序的沉浸式质量。</span><span class="sxs-lookup"><span data-stu-id="970f7-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="970f7-140">**清除标志**</span><span class="sxs-lookup"><span data-stu-id="970f7-140">**Clear Flags**</span></span>

<span data-ttu-id="970f7-141">清除标志值指示绘制显示器时如何清除显示。</span><span class="sxs-lookup"><span data-stu-id="970f7-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="970f7-142">对于虚拟现实体验，此值通常设置为 Skybox。</span><span class="sxs-lookup"><span data-stu-id="970f7-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="970f7-143">对于透明显示，建议将此选项设置为"颜色"。</span><span class="sxs-lookup"><span data-stu-id="970f7-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="970f7-144">**背景色**</span><span class="sxs-lookup"><span data-stu-id="970f7-144">**Background Color**</span></span>

<span data-ttu-id="970f7-145">如果未将清除标志设置为 Skybox，将显示背景色属性。</span><span class="sxs-lookup"><span data-stu-id="970f7-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="970f7-146">**质量设置**</span><span class="sxs-lookup"><span data-stu-id="970f7-146">**Quality Settings**</span></span>

<span data-ttu-id="970f7-147">质量设置值指示 Unity 在呈现场景时应该使用的图形质量。</span><span class="sxs-lookup"><span data-stu-id="970f7-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="970f7-148">质量级别是项目级别设置，并不特定于任何一个相机。</span><span class="sxs-lookup"><span data-stu-id="970f7-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="970f7-149">有关详细信息，请参阅 Unity [文档中的质量](https://docs.unity3d.com/Manual/class-QualitySettings.html) 文章。</span><span class="sxs-lookup"><span data-stu-id="970f7-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="970f7-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="970f7-150">See also</span></span>

- [<span data-ttu-id="970f7-151">相机系统 API 文档</span><span class="sxs-lookup"><span data-stu-id="970f7-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="970f7-152">创建相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="970f7-152">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
