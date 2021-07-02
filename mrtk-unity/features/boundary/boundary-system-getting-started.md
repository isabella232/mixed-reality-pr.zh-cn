---
title: 边界系统概述
description: MRTK 中边界系统的登陆页
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 边界系统，
ms.openlocfilehash: fd70479e5183e9a7557de5c5a532cc87161be017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177085"
---
# <a name="boundary-system-overview"></a><span data-ttu-id="bbd7f-104">边界系统概述</span><span class="sxs-lookup"><span data-stu-id="bbd7f-104">Boundary system overview</span></span>

<span data-ttu-id="bbd7f-105">边界系统支持在混合现实应用程序中可视化虚拟现实边界组件。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="bbd7f-106">边界定义一个区域，用户可以在运动 VR 头戴显示设备时安全地四处移动。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="bbd7f-107">边界是混合现实体验的一个重要组成部分，可帮助用户在接触 VR 头戴显示设备时避免意外的障碍。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="bbd7f-108">许多虚拟现实平台都提供自动显示，例如，当用户或控制器接近边界时，虚拟世界上叠加了白色轮廓。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="bbd7f-109">混合现实Toolkit边界系统扩展了此功能，以便显示跟踪区域、地平面和其他可用于为用户提供附加信息的功能的轮廓。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="bbd7f-110">入门</span><span class="sxs-lookup"><span data-stu-id="bbd7f-110">Getting started</span></span>

<span data-ttu-id="bbd7f-111">添加对边界的支持需要混合现实平台的两个关键Toolkit：边界系统和配置了边界的虚拟现实平台。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="bbd7f-112">[启用](#enable-boundary-system) 边界系统</span><span class="sxs-lookup"><span data-stu-id="bbd7f-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="bbd7f-113">[配置](#configure-boundary-visualization) 边界可视化效果</span><span class="sxs-lookup"><span data-stu-id="bbd7f-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="bbd7f-114">[生成并](#build-and-deploy) 部署到具有已配置边界的 VR 平台</span><span class="sxs-lookup"><span data-stu-id="bbd7f-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="bbd7f-115">启用边界系统</span><span class="sxs-lookup"><span data-stu-id="bbd7f-115">Enable boundary system</span></span>

<span data-ttu-id="bbd7f-116">边界系统由 MixedRealityToolkit 对象对象 (或其他 [服务](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 注册器组件) 。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="bbd7f-117">以下步骤将预先使用 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="bbd7f-118">其他服务注册机构所需的步骤可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="bbd7f-119">选择场景层次结构中的 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="bbd7f-121">将"检查器"面板导航到"边界系统"部分，并选中"启用"</span><span class="sxs-lookup"><span data-stu-id="bbd7f-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![启用边界系统](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="bbd7f-123">选择边界系统实现。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="bbd7f-124">MRTK 提供的默认类实现是 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="bbd7f-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![选择边界系统实现](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="bbd7f-126">所有边界系统实现都必须扩展 [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="bbd7f-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="bbd7f-127">配置边界可视化</span><span class="sxs-lookup"><span data-stu-id="bbd7f-127">Configure boundary visualization</span></span>

<span data-ttu-id="bbd7f-128">[边界系统使用配置文件来](configuring-boundary-visualization.md)指定要显示的边界组件并配置其外观。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![边界可视化选项](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="bbd7f-130">默认配置文件 `DefaultMixedRealityBoundaryVisualizationProfile` （ (Assets/MRTK/SDK/Profiles) ）的用户将预先配置边界系统以显示楼层平面、播放区域以及跟踪区域。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="bbd7f-131">生成并部署</span><span class="sxs-lookup"><span data-stu-id="bbd7f-131">Build and deploy</span></span>

<span data-ttu-id="bbd7f-132">使用所需的可视化选项配置边界系统后，可以将项目部署到目标平台。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="bbd7f-133">Unity 播放模式启用已配置边界的编辑器内可视化。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="bbd7f-134">此功能可实现快速开发和测试，而无需生成和部署步骤。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="bbd7f-135">请确保使用在目标硬件和平台上运行的生成和部署的应用程序版本执行最终验收测试。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="bbd7f-136">通过代码访问边界系统</span><span class="sxs-lookup"><span data-stu-id="bbd7f-136">Accessing boundary system via code</span></span>

<span data-ttu-id="bbd7f-137">如果启用并配置了边界系统，则可以通过 CoreServices 静态帮助程序类访问边界系统。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="bbd7f-138">然后，可以使用引用动态更改边界参数，并访问由系统管理的相关 GameObject。</span><span class="sxs-lookup"><span data-stu-id="bbd7f-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="bbd7f-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbd7f-139">See also</span></span>

- [<span data-ttu-id="bbd7f-140">边界 API 文档</span><span class="sxs-lookup"><span data-stu-id="bbd7f-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="bbd7f-141">配置边界可视化效果</span><span class="sxs-lookup"><span data-stu-id="bbd7f-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
