---
title: 空间感知
description: 介绍 MRTK 中的空间感知
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 776033dbb4736ccaa44cdb683c4fce284758a51c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144461"
---
# <a name="spatial-awareness"></a><span data-ttu-id="df139-104">空间感知</span><span class="sxs-lookup"><span data-stu-id="df139-104">Spatial Awareness</span></span>

![空间感知](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="df139-106">空间感知系统在混合现实应用程序中提供真实的环境意识。</span><span class="sxs-lookup"><span data-stu-id="df139-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="df139-107">在 Microsoft HoloLens 上引入时，空间感知提供了一个网格集合，表示环境的几何图形，从而允许在全息影像与现实世界之间进行引人注目的交互。</span><span class="sxs-lookup"><span data-stu-id="df139-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="df139-108">目前，混合现实工具包未随最初打包在 HoloToolkit 中的空间理解算法一起提供。</span><span class="sxs-lookup"><span data-stu-id="df139-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="df139-109">空间理解通常涉及转换空间网格数据，以创建简化的和/或分组的网格数据，例如平面、墙、楼层、上限等。</span><span class="sxs-lookup"><span data-stu-id="df139-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="df139-110">入门</span><span class="sxs-lookup"><span data-stu-id="df139-110">Getting started</span></span>

<span data-ttu-id="df139-111">添加对空间感知的支持需要混合现实工具包的两个关键组件：空间感知系统和受支持的平台提供程序。</span><span class="sxs-lookup"><span data-stu-id="df139-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="df139-112">[启用](#enable-the-spatial-awareness-system) 空间感知系统</span><span class="sxs-lookup"><span data-stu-id="df139-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="df139-113">[注册](#register-observers) 并 [配置](configuring-spatial-awareness-mesh-observer.md) 一个或多个空间观察器以提供网格数据</span><span class="sxs-lookup"><span data-stu-id="df139-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="df139-114">[生成并](#build-and-deploy) 部署到支持空间感知的平台</span><span class="sxs-lookup"><span data-stu-id="df139-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="df139-115">启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="df139-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="df139-116">空间感知系统由 MixedRealityToolkit 对象管理 (或其他 [服务](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 注册器组件) 。</span><span class="sxs-lookup"><span data-stu-id="df139-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="df139-117">按照以下步骤在 *MixedRealityToolkit* *配置文件* 中启用或禁用空间感知系统。</span><span class="sxs-lookup"><span data-stu-id="df139-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="df139-118">混合现实工具包附带一些默认预配置的配置文件。</span><span class="sxs-lookup"><span data-stu-id="df139-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="df139-119">其中一些默认已启用或禁用空间感知系统。</span><span class="sxs-lookup"><span data-stu-id="df139-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="df139-120">此预配置（尤其是禁用时）的目的是避免计算和呈现网格的视觉开销。</span><span class="sxs-lookup"><span data-stu-id="df139-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="df139-121">配置文件</span><span class="sxs-lookup"><span data-stu-id="df139-121">Profile</span></span> | <span data-ttu-id="df139-122">系统默认启用</span><span class="sxs-lookup"><span data-stu-id="df139-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="df139-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1) </span><span class="sxs-lookup"><span data-stu-id="df139-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="df139-124">False</span><span class="sxs-lookup"><span data-stu-id="df139-124">False</span></span> |
| <span data-ttu-id="df139-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2) </span><span class="sxs-lookup"><span data-stu-id="df139-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="df139-126">False</span><span class="sxs-lookup"><span data-stu-id="df139-126">False</span></span> |
| <span data-ttu-id="df139-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) </span><span class="sxs-lookup"><span data-stu-id="df139-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="df139-128">True</span><span class="sxs-lookup"><span data-stu-id="df139-128">True</span></span> |

1. <span data-ttu-id="df139-129">选择场景层次结构中的 MixedRealityToolkit 对象，以在检查器面板中打开。</span><span class="sxs-lookup"><span data-stu-id="df139-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![MRTK 配置场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="df139-131">导航到 "*空间感知系统*" 部分，并选中 "*启用空间感知系统*"</span><span class="sxs-lookup"><span data-stu-id="df139-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![启用空间感知](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="df139-133">选择所需的空间感知系统实现类型。</span><span class="sxs-lookup"><span data-stu-id="df139-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="df139-134">[`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)为提供的默认值。</span><span class="sxs-lookup"><span data-stu-id="df139-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![选择空间感知系统实现](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="df139-136">注册观察者</span><span class="sxs-lookup"><span data-stu-id="df139-136">Register observers</span></span>

<span data-ttu-id="df139-137">混合现实工具包中的服务可以拥有使用平台特定的数据和实现控制来补充主要服务的 [数据提供程序服务](../../architecture/systems-extensions-providers.md) 。</span><span class="sxs-lookup"><span data-stu-id="df139-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="df139-138">这种情况的一个示例是混合现实输入系统，它具有 [多个数据提供程序](../input/input-providers.md) ，可从各种特定于平台的 api 获取控制器和其他相关输入信息。</span><span class="sxs-lookup"><span data-stu-id="df139-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="df139-139">空间感知系统类似于数据访问接口为系统提供关于现实世界的网格数据。</span><span class="sxs-lookup"><span data-stu-id="df139-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="df139-140">空间识别配置文件必须至少注册一个空间观察程序。</span><span class="sxs-lookup"><span data-stu-id="df139-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="df139-141">空间观察器通常是特定于平台的组件，用作提供程序，用于从特定于平台的终结点呈现各种类型的网格数据 (即</span><span class="sxs-lookup"><span data-stu-id="df139-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="df139-142">HoloLens) 。</span><span class="sxs-lookup"><span data-stu-id="df139-142">HoloLens).</span></span>

1. <span data-ttu-id="df139-143">打开或展开 *空间感知系统配置文件*</span><span class="sxs-lookup"><span data-stu-id="df139-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![空间感知系统配置文件](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="df139-145">单击 *"添加空间观察器"* 按钮</span><span class="sxs-lookup"><span data-stu-id="df139-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="df139-146">选择所需的 *空间观察程序实现类型*</span><span class="sxs-lookup"><span data-stu-id="df139-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![选择空间观察程序实现](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="df139-148">根据需要[修改观察者的配置属性](configuring-spatial-awareness-mesh-observer.md)</span><span class="sxs-lookup"><span data-stu-id="df139-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="df139-149">`DefaultMixedRealityToolkitConfigurationProfile` (资产/MRTK/SDK/配置文件) 的用户将为使用类的 Windows Mixed Reality 平台预配置空间感知系统 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 。</span><span class="sxs-lookup"><span data-stu-id="df139-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="df139-150">生成并部署</span><span class="sxs-lookup"><span data-stu-id="df139-150">Build and deploy</span></span>

<span data-ttu-id="df139-151">一旦将空间感知系统配置 () 的所需观察程序，就可以生成项目并将其部署到目标平台。</span><span class="sxs-lookup"><span data-stu-id="df139-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df139-152">如果面向 Windows Mixed Reality 平台 (例如： HoloLens) ，请务必确保启用 [空间感知功能](/windows/mixed-reality/spatial-mapping-in-unity) ，以便在设备上使用空间感知系统。</span><span class="sxs-lookup"><span data-stu-id="df139-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="df139-153">某些平台（包括 Microsoft HoloLens）为从 Unity 内的远程执行提供支持。</span><span class="sxs-lookup"><span data-stu-id="df139-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="df139-154">此功能可实现快速开发和测试，而无需执行生成和部署步骤。</span><span class="sxs-lookup"><span data-stu-id="df139-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="df139-155">请确保使用在目标硬件和平台上运行的应用程序的构建和部署版本执行最终的验收测试。</span><span class="sxs-lookup"><span data-stu-id="df139-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="df139-156">后续步骤</span><span class="sxs-lookup"><span data-stu-id="df139-156">Next steps</span></span>

<span data-ttu-id="df139-157">按照上述步骤启用空间感知系统后，可以更详细地配置和控制系统。</span><span class="sxs-lookup"><span data-stu-id="df139-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="df139-158">用于在检查器中配置观察程序的信息：</span><span class="sxs-lookup"><span data-stu-id="df139-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="df139-159">为设备使用配置观察程序</span><span class="sxs-lookup"><span data-stu-id="df139-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="df139-160">为编辑器内使用配置观察器</span><span class="sxs-lookup"><span data-stu-id="df139-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="df139-161">有关通过代码控制和扩展观察程序的信息：</span><span class="sxs-lookup"><span data-stu-id="df139-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="df139-162">通过代码配置观察者</span><span class="sxs-lookup"><span data-stu-id="df139-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="df139-163">创建自定义观察程序</span><span class="sxs-lookup"><span data-stu-id="df139-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="df139-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df139-164">See also</span></span>

- [<span data-ttu-id="df139-165">空间感知 API 文档</span><span class="sxs-lookup"><span data-stu-id="df139-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="df139-166">空间映射概述 WMR</span><span class="sxs-lookup"><span data-stu-id="df139-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="df139-167">Unity WMR 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="df139-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)