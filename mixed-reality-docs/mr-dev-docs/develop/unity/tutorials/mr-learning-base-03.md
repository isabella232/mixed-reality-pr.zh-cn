---
title: 入门教程 - 3. 配置 MRTK 配置文件
description: 本教程介绍如何配置混合现实工具包 (MRTK) 配置文件。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 空间感知
ms.localizationpriority: high
ms.openlocfilehash: 0a8beb647516ebcb5bc07cb58d0193e8fe71e9fc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "101760013"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="56f18-105">3.配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="56f18-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="56f18-106">概述</span><span class="sxs-lookup"><span data-stu-id="56f18-106">Overview</span></span>

<span data-ttu-id="56f18-107">在本教程中，你将学习如何自定义和配置 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="56f18-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="56f18-108"><a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">MRTK 配置文件</a>是一个嵌套配置文件树，它们构成了应如何初始化 MRTK 系统和功能的配置信息。</span><span class="sxs-lookup"><span data-stu-id="56f18-108">The <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="56f18-109">顶级配置文件（即“配置”配置文件）包含每个主要核心系统的嵌套配置文件。</span><span class="sxs-lookup"><span data-stu-id="56f18-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="56f18-110">每个嵌套的配置文件都设计为配置其对应系统的行为。</span><span class="sxs-lookup"><span data-stu-id="56f18-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="56f18-111">此特定示例将演示如何通过更改空间网格观察程序的设置来隐藏空间感知网格。</span><span class="sxs-lookup"><span data-stu-id="56f18-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="56f18-112">但是，可以按照相同的原则来自定义 MRTK 配置文件中的任何设置或值。</span><span class="sxs-lookup"><span data-stu-id="56f18-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="56f18-113">正如你在[上一教程](mr-learning-base-02.md#congratulations)期间将项目部署到 HoloLens 2 时遇到的一样，<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">空间感知</a>网格是一系列表示环境几何图形的网格。</span><span class="sxs-lookup"><span data-stu-id="56f18-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="56f18-114">这是一种有用的可视化效果，一开始就能看到，但通常也可将它关闭，以避免用它后产生视觉干扰和额外的性能影响。</span><span class="sxs-lookup"><span data-stu-id="56f18-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="56f18-115">目标</span><span class="sxs-lookup"><span data-stu-id="56f18-115">Objectives</span></span>

* <span data-ttu-id="56f18-116">了解如何自定义和配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="56f18-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="56f18-117">隐藏空间感知网格</span><span class="sxs-lookup"><span data-stu-id="56f18-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="56f18-118">更改空间感知显示选项</span><span class="sxs-lookup"><span data-stu-id="56f18-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="56f18-119">隐藏空间感知网格所要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="56f18-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="56f18-120">克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="56f18-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="56f18-121">启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="56f18-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="56f18-122">克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="56f18-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="56f18-123">克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="56f18-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="56f18-124">更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="56f18-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="56f18-125">默认情况下，MRTK 配置文件不可编辑。</span><span class="sxs-lookup"><span data-stu-id="56f18-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="56f18-126">这是一些默认的配置文件模板，必须先克隆它们，然后才能对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="56f18-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="56f18-127">配置文件有多个嵌套层。</span><span class="sxs-lookup"><span data-stu-id="56f18-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="56f18-128">因此，在配置一个或多个设置时，常见的做法是克隆然后编辑多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="56f18-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="56f18-129">1.克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="56f18-129">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="56f18-130">配置配置文件是顶级配置文件。</span><span class="sxs-lookup"><span data-stu-id="56f18-130">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="56f18-131">因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。</span><span class="sxs-lookup"><span data-stu-id="56f18-131">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="56f18-132">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，然后在检查器窗口中将“MixedRealityToolkit”配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”：</span><span class="sxs-lookup"><span data-stu-id="56f18-132">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![选中 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="56f18-134">在仍选中了“MixedRealityToolkit”对象的情况下，在检查器窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="56f18-134">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Unity MixedRealityToolkit 组件的“复制和自定义”按钮](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="56f18-136">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_HoloLens2ConfigurationProfile），然后单击“克隆”按钮，创建“DefaultHololens2ConfigurationProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="56f18-136">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆配置文件”弹出窗口](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="56f18-138">新建的配置配置文件现已分配为场景中的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="56f18-138">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![应用了新创建的自定义 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="56f18-140">在 Unity 菜单中，选择“文件” > “保存”以保存场景。 </span><span class="sxs-lookup"><span data-stu-id="56f18-140">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="56f18-141">在学习整篇教程的过程中，请记得保存自己的工作。</span><span class="sxs-lookup"><span data-stu-id="56f18-141">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="56f18-142">2.启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="56f18-142">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="56f18-143">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，接下来在检查器窗口中，选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：  </span><span class="sxs-lookup"><span data-stu-id="56f18-143">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![启用了空间感知系统的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="56f18-145">在未来的项目中，如果你的应用无需响应环境或与环境交互，则建议关闭空间感知来减少性能成本。</span><span class="sxs-lookup"><span data-stu-id="56f18-145">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="56f18-146">3.克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="56f18-146">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="56f18-147">在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="56f18-147">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![选中“空间感知”选项卡的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="56f18-149">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessSystemProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessSystemProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="56f18-149">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆空间感知系统配置文件”弹出窗口](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="56f18-151">新建的空间感知系统配置文件现已自动分配到你的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="56f18-151">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![应用了新创建的自定义 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="56f18-153">4.克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="56f18-153">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="56f18-154">在仍然选中了“空间感知”选项卡的情况下，展开“Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口：  </span><span class="sxs-lookup"><span data-stu-id="56f18-154">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![已展开“Windows Mixed Reality 空间网格观察程序”部分的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="56f18-156">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessMeshObserverProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="56f18-156">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆空间网格观察程序配置文件”弹出窗口](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="56f18-158">新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：</span><span class="sxs-lookup"><span data-stu-id="56f18-158">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![应用了新创建的自定义 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="56f18-160">5.更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="56f18-160">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="56f18-161">在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下正常运行：  </span><span class="sxs-lookup"><span data-stu-id="56f18-161">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![空间网格观察程序显示选项设置为“遮挡”的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="56f18-163">尽管空间映射网格不可见，但它依然存在且可正常运行。</span><span class="sxs-lookup"><span data-stu-id="56f18-163">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="56f18-164">例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。</span><span class="sxs-lookup"><span data-stu-id="56f18-164">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="56f18-165">你已了解如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="56f18-165">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="56f18-166">可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="56f18-166">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="56f18-167">由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。</span><span class="sxs-lookup"><span data-stu-id="56f18-167">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="56f18-168">若要详细了解 MRTK 配置文件及其体系结构，可参阅 [MRTK 文档门户](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs)中的 [MRTK 配置文件配置指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="56f18-168">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span></span>

## <a name="congratulations"></a><span data-ttu-id="56f18-169">祝贺</span><span class="sxs-lookup"><span data-stu-id="56f18-169">Congratulations</span></span>

<span data-ttu-id="56f18-170">在本教程中，你学习了如何克隆、自定义和配置 MRTK 配置文件和设置。</span><span class="sxs-lookup"><span data-stu-id="56f18-170">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56f18-171">下一教程：4.定位场景中的对象</span><span class="sxs-lookup"><span data-stu-id="56f18-171">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
