---
title: 空间感知入门
description: 介绍 MRTK 中的空间感知
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 46bb78bc4e2574fd4da14f19edf52624b7b301c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176717"
---
# <a name="spatial-awareness-getting-started"></a><span data-ttu-id="41681-104">空间感知入门</span><span class="sxs-lookup"><span data-stu-id="41681-104">Spatial awareness getting started</span></span>

![空间感知](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="41681-106">空间感知系统在混合现实应用程序中提供真实的环境意识。</span><span class="sxs-lookup"><span data-stu-id="41681-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="41681-107">在 Microsoft HoloLens 上引入时，空间感知提供了一组网格，表示环境的几何图形，这允许全息影像与现实世界之间的引人注目的交互。</span><span class="sxs-lookup"><span data-stu-id="41681-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="41681-108">目前，混合现实Toolkit与最初打包在 HoloToolkit 中的空间理解算法一起提供。</span><span class="sxs-lookup"><span data-stu-id="41681-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="41681-109">空间理解通常涉及转换空间网格数据，以创建简化的和/或分组的网格数据，例如平面、墙、楼层、上限等。</span><span class="sxs-lookup"><span data-stu-id="41681-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="41681-110">入门</span><span class="sxs-lookup"><span data-stu-id="41681-110">Getting started</span></span>

<span data-ttu-id="41681-111">添加对空间感知的支持需要混合现实平台的两个关键Toolkit：空间感知系统和受支持的平台提供程序。</span><span class="sxs-lookup"><span data-stu-id="41681-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="41681-112">[启用](#enable-the-spatial-awareness-system) 空间感知系统</span><span class="sxs-lookup"><span data-stu-id="41681-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="41681-113">[注册](#register-observers) 并 [配置](configuring-spatial-awareness-mesh-observer.md) 一个或多个空间观察器以提供网格数据</span><span class="sxs-lookup"><span data-stu-id="41681-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="41681-114">[生成并](#build-and-deploy) 部署到支持空间感知的平台</span><span class="sxs-lookup"><span data-stu-id="41681-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="41681-115">启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="41681-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="41681-116">空间感知系统由 MixedRealityToolkit 对象管理 (或其他 [服务](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 注册器组件) 。</span><span class="sxs-lookup"><span data-stu-id="41681-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="41681-117">按照以下步骤在 *MixedRealityToolkit* *配置文件* 中启用或禁用空间感知系统。</span><span class="sxs-lookup"><span data-stu-id="41681-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="41681-118">混合现实Toolkit预配置的一些默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="41681-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="41681-119">其中一些默认已启用或禁用空间感知系统。</span><span class="sxs-lookup"><span data-stu-id="41681-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="41681-120">此预配置（尤其是禁用时）的目的是避免计算和呈现网格的视觉开销。</span><span class="sxs-lookup"><span data-stu-id="41681-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="41681-121">配置文件</span><span class="sxs-lookup"><span data-stu-id="41681-121">Profile</span></span> | <span data-ttu-id="41681-122">系统默认启用</span><span class="sxs-lookup"><span data-stu-id="41681-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="41681-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1) </span><span class="sxs-lookup"><span data-stu-id="41681-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="41681-124">错误</span><span class="sxs-lookup"><span data-stu-id="41681-124">False</span></span> |
| <span data-ttu-id="41681-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2) </span><span class="sxs-lookup"><span data-stu-id="41681-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="41681-126">错误</span><span class="sxs-lookup"><span data-stu-id="41681-126">False</span></span> |
| <span data-ttu-id="41681-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) </span><span class="sxs-lookup"><span data-stu-id="41681-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="41681-128">正确</span><span class="sxs-lookup"><span data-stu-id="41681-128">True</span></span> |

1. <span data-ttu-id="41681-129">选择场景层次结构中的 MixedRealityToolkit 对象，以在检查器面板中打开。</span><span class="sxs-lookup"><span data-stu-id="41681-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="41681-131">导航到" *空间感知系统"* 部分，并选中" *启用空间感知系统"*</span><span class="sxs-lookup"><span data-stu-id="41681-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![启用空间感知](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="41681-133">选择所需的空间感知系统实现类型。</span><span class="sxs-lookup"><span data-stu-id="41681-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="41681-134">[`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)是提供的默认值。</span><span class="sxs-lookup"><span data-stu-id="41681-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![选择空间感知系统实现](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="41681-136">注册观察者</span><span class="sxs-lookup"><span data-stu-id="41681-136">Register observers</span></span>

<span data-ttu-id="41681-137">混合现实服务Toolkit数据提供程序服务，通过平台特定的[](../../architecture/systems-extensions-providers.md)数据和实现控制来补充主要服务。</span><span class="sxs-lookup"><span data-stu-id="41681-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="41681-138">例如，混合现实输入系统具有多个数据访问接口，用于[](../input/input-providers.md)从各种特定于平台的 API 获取控制器和其他相关输入信息。</span><span class="sxs-lookup"><span data-stu-id="41681-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="41681-139">空间感知系统类似，数据提供程序为系统提供有关现实世界的网格数据。</span><span class="sxs-lookup"><span data-stu-id="41681-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="41681-140">空间感知配置文件必须至少注册一个空间观察器。</span><span class="sxs-lookup"><span data-stu-id="41681-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="41681-141">空间观察器通常是平台特定的组件，充当提供程序，用于从特定于平台的终结点（即） (网格数据</span><span class="sxs-lookup"><span data-stu-id="41681-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="41681-142">HoloLens) 。</span><span class="sxs-lookup"><span data-stu-id="41681-142">HoloLens).</span></span>

1. <span data-ttu-id="41681-143">打开或展开 *空间感知系统配置文件*</span><span class="sxs-lookup"><span data-stu-id="41681-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![空间感知系统配置文件](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="41681-145">单击" *添加空间观察器"* 按钮</span><span class="sxs-lookup"><span data-stu-id="41681-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="41681-146">选择所需的 *空间观察器实现类型*</span><span class="sxs-lookup"><span data-stu-id="41681-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![选择空间观察器实现](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="41681-148">[根据需要修改观察器上的](configuring-spatial-awareness-mesh-observer.md) 配置属性</span><span class="sxs-lookup"><span data-stu-id="41681-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="41681-149"> (`DefaultMixedRealityToolkitConfigurationProfile` Assets/MRTK/SDK/Profiles) 的用户将为使用 类的 Windows Mixed Reality 平台预配置空间感知 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 系统。</span><span class="sxs-lookup"><span data-stu-id="41681-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="41681-150">生成并部署</span><span class="sxs-lookup"><span data-stu-id="41681-150">Build and deploy</span></span>

<span data-ttu-id="41681-151">使用所需的观察程序配置空间感知系统 () ，可以生成项目并部署到目标平台。</span><span class="sxs-lookup"><span data-stu-id="41681-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41681-152">如果面向 Windows Mixed Reality平台 (例如：HoloLens) ，请确保启用空间感知功能，以便使用设备上的空间感知系统。 [](/windows/mixed-reality/spatial-mapping-in-unity)</span><span class="sxs-lookup"><span data-stu-id="41681-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="41681-153">某些平台（包括 Microsoft HoloLens）为 Unity 中的远程执行提供支持。</span><span class="sxs-lookup"><span data-stu-id="41681-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="41681-154">此功能可实现快速开发和测试，而无需生成和部署步骤。</span><span class="sxs-lookup"><span data-stu-id="41681-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="41681-155">请确保使用在目标硬件和平台上运行的生成和部署的应用程序版本执行最终验收测试。</span><span class="sxs-lookup"><span data-stu-id="41681-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="41681-156">后续步骤</span><span class="sxs-lookup"><span data-stu-id="41681-156">Next steps</span></span>

<span data-ttu-id="41681-157">按照上述过程启用空间感知系统后，可以更详细地配置和控制系统。</span><span class="sxs-lookup"><span data-stu-id="41681-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="41681-158">有关在检查器中配置观察程序的信息：</span><span class="sxs-lookup"><span data-stu-id="41681-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="41681-159">为设备使用情况配置观察程序</span><span class="sxs-lookup"><span data-stu-id="41681-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="41681-160">为编辑器内使用情况配置观察程序</span><span class="sxs-lookup"><span data-stu-id="41681-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="41681-161">有关通过代码控制和扩展观察程序的信息：</span><span class="sxs-lookup"><span data-stu-id="41681-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="41681-162">通过代码配置观察程序</span><span class="sxs-lookup"><span data-stu-id="41681-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="41681-163">创建自定义观察者</span><span class="sxs-lookup"><span data-stu-id="41681-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="41681-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41681-164">See also</span></span>

- [<span data-ttu-id="41681-165">空间感知 API 文档</span><span class="sxs-lookup"><span data-stu-id="41681-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="41681-166">空间映射概述 WMR</span><span class="sxs-lookup"><span data-stu-id="41681-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="41681-167">Unity WMR 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="41681-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)
