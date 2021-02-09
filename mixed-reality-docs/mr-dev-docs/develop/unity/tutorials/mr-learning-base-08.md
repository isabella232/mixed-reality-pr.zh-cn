---
title: 使用眼动跟踪
description: 本课程介绍如何将混合现实应用中的眼动跟踪与混合现实工具包 (MRTK) 结合使用。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 眼动跟踪
ms.localizationpriority: high
ms.openlocfilehash: e4104dfd0d7b27425217c8cb92fa36c807053081
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590369"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="50a92-104">8.使用眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="50a92-104">8. Using eye-tracking</span></span>

<span data-ttu-id="50a92-105">在本教程中，你将了解如何为 HoloLens 2 启用眼动跟踪，以及在用户查看对象时如何将眼动跟踪添加到对象以触发操作。</span><span class="sxs-lookup"><span data-stu-id="50a92-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="50a92-106">如果你也要将此项目部署到 HoloLens（第一代），请注意，只有 HoloLens 2 支持眼动跟踪。</span><span class="sxs-lookup"><span data-stu-id="50a92-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="50a92-107">目标</span><span class="sxs-lookup"><span data-stu-id="50a92-107">Objectives</span></span>

* <span data-ttu-id="50a92-108">了解如何为 HoleLens 2 启用眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="50a92-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="50a92-109">了解如何使用眼动跟踪触发操作</span><span class="sxs-lookup"><span data-stu-id="50a92-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="50a92-110">确保启用了“眼睛凝视输入”功能</span><span class="sxs-lookup"><span data-stu-id="50a92-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="50a92-111">在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用眼睛凝视输入功能”是否灰显   ：</span><span class="sxs-lookup"><span data-stu-id="50a92-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity“MRTK 项目配置器”窗口](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="50a92-113">当你在本系列教程开头配置 Unity 项目时，[应用 MRTK 项目配置器设置](mr-learning-base-02.md#creating-and-configuring-the-scene)指令期间应该已经启用了眼睛凝视输入功能。</span><span class="sxs-lookup"><span data-stu-id="50a92-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="50a92-114">但如果未启用此功能，请确保立即启用。</span><span class="sxs-lookup"><span data-stu-id="50a92-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="50a92-115">在凝视提供者中启用基于眼睛的凝视</span><span class="sxs-lookup"><span data-stu-id="50a92-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="50a92-116">在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：</span><span class="sxs-lookup"><span data-stu-id="50a92-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="50a92-117">克隆 DefaultHoloLens2InputSystemProfile 并为其指定合适的名称，例如 GettingStarted_HoloLens2InputSystemProfile</span><span class="sxs-lookup"><span data-stu-id="50a92-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="50a92-118">展开“指针”部分</span><span class="sxs-lookup"><span data-stu-id="50a92-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="50a92-119">克隆 DefaultMixedRealityPointerProfile 并为其指定合适的名称，例如 GettingStarted_MixedRealityPointerProfile</span><span class="sxs-lookup"><span data-stu-id="50a92-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="50a92-120">找到“凝视设置”部分，并选中“是否启用了眼动跟踪”复选框 </span><span class="sxs-lookup"><span data-stu-id="50a92-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![应用了新创建的配置文件并启用了眼动跟踪的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="50a92-122">有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="50a92-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="50a92-123">为 Unity 编辑器启用模拟的眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="50a92-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="50a92-124">在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡，然后执行以下操作 ：</span><span class="sxs-lookup"><span data-stu-id="50a92-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="50a92-125">展开“输入数据提供者” > “输入模拟服务”部分 </span><span class="sxs-lookup"><span data-stu-id="50a92-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="50a92-126">克隆 DefaultMixedRealityInputSimulationProfile 并为其指定合适的名称，例如 GettingStarted_MixedRealityInputSimulationProfile</span><span class="sxs-lookup"><span data-stu-id="50a92-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="50a92-127">找到“眼睛凝视模拟”，并将“默认眼睛凝视模拟模式”设置为“摄像头前轴”  </span><span class="sxs-lookup"><span data-stu-id="50a92-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![选中了 TextMeshPro 对象的 Unity](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="50a92-129">将眼动跟踪添加到对象</span><span class="sxs-lookup"><span data-stu-id="50a92-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="50a92-130">在“层次结构”窗口中，展开“RoverExplorer”>“按钮”对象，然后为三个子按钮对象中的每一个对象展开并选择“SeeItSayItLabel”>“TextMeshPro”对象 ：</span><span class="sxs-lookup"><span data-stu-id="50a92-130">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![选中了 TextMeshPro 对象的 Unity](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="50a92-132">当“检查器”窗口中的三个“TextMeshPro”对象仍处于选中状态时，请使用“添加组件”按钮将以下组件添加到所有选定对象：</span><span class="sxs-lookup"><span data-stu-id="50a92-132">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="50a92-133">盒碰撞体组件</span><span class="sxs-lookup"><span data-stu-id="50a92-133">**Box Collider** component</span></span>
* <span data-ttu-id="50a92-134">EyeTrackingTarget 组件</span><span class="sxs-lookup"><span data-stu-id="50a92-134">**EyeTrackingTarget** component</span></span>

![选中了 TextMeshPro 对象并添加了组件的 Unity](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="50a92-136">在“层次结构”窗口中，选择“提示”>“SeeItSayItLabel”>“TextMeshPro”对象，然后按以下方式配置“EyeTrackingTarget”组件  ：</span><span class="sxs-lookup"><span data-stu-id="50a92-136">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="50a92-137">在“On Look At Start ()”事件部分</span><span class="sxs-lookup"><span data-stu-id="50a92-137">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="50a92-138">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="50a92-138">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="50a92-139">将对象本身（即相同的 TextMeshPro 对象）分配给“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="50a92-139">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="50a92-140">在“无函数”下拉列表中选择“TextMeshPro” > “float fontSize”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="50a92-140">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="50a92-141">将参数设置为 0.06，以将 0.04 的当前字号增加 50%</span><span class="sxs-lookup"><span data-stu-id="50a92-141">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="50a92-142">在“On Look Away ()”事件部分</span><span class="sxs-lookup"><span data-stu-id="50a92-142">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="50a92-143">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="50a92-143">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="50a92-144">将对象本身（即相同的 TextMeshPro 对象）分配给“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="50a92-144">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="50a92-145">在“无函数”下拉列表中选择“TextMeshPro” > “float fontSize”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="50a92-145">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="50a92-146">将参数设置为 0.04 以将字号重置为 0.04</span><span class="sxs-lookup"><span data-stu-id="50a92-146">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![选中了“提示 TextMeshPro 对象”并配置了 EyeTrackingTarget 组件的 Unity](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="50a92-148">对“分解”>“SeeItSayItLabel”>“TextMeshPro”对象和“重置”>“SeeItSayItLabel”>“TextMeshPro”对象重复此步骤    。</span><span class="sxs-lookup"><span data-stu-id="50a92-148">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="50a92-149">如果你现在进入游戏模式，然后按住鼠标右键，同时移动鼠标，直到凝视命中的某个标签出现，你将看到字号增加了 50%，而鼠标移走时字号将重置回其原始大小：</span><span class="sxs-lookup"><span data-stu-id="50a92-149">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![视线对准眼动跟踪目标“分解”按钮标签的 Unity“播放”模式分屏视图](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="50a92-151">祝贺</span><span class="sxs-lookup"><span data-stu-id="50a92-151">Congratulations</span></span>

<span data-ttu-id="50a92-152">在本教程中，你了解了如何为 HoloLens 2 启用眼动跟踪，以及在用户查看对象时如何将眼动跟踪添加到对象以触发操作。</span><span class="sxs-lookup"><span data-stu-id="50a92-152">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="50a92-153">下一教程：9.使用语音命令</span><span class="sxs-lookup"><span data-stu-id="50a92-153">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
