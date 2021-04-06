---
title: 使用眼动跟踪
description: 本课程介绍如何将混合现实应用中的眼动跟踪与混合现实工具包 (MRTK) 结合使用。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 眼动跟踪
ms.localizationpriority: high
ms.openlocfilehash: bf7bd266eb471193979c588d97d14dd37aed175e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982873"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="cae82-104">8.使用眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="cae82-104">8. Using eye-tracking</span></span>

<span data-ttu-id="cae82-105">在本教程中，你将了解如何为 HoloLens 2 启用眼动跟踪，以及在用户查看对象时如何将眼动跟踪添加到对象以触发操作。</span><span class="sxs-lookup"><span data-stu-id="cae82-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="cae82-106">如果你也要将此项目部署到 HoloLens（第一代），请注意，只有 HoloLens 2 支持眼动跟踪。</span><span class="sxs-lookup"><span data-stu-id="cae82-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="cae82-107">目标</span><span class="sxs-lookup"><span data-stu-id="cae82-107">Objectives</span></span>

* <span data-ttu-id="cae82-108">了解如何为 HoleLens 2 启用眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="cae82-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="cae82-109">了解如何使用眼动跟踪触发操作</span><span class="sxs-lookup"><span data-stu-id="cae82-109">Learn how to use eye-tracking to trigger action</span></span>

[!INCLUDE[](includes/ensuring-eye-gaze-capabality.md)]

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="cae82-110">在凝视提供者中启用基于眼睛的凝视</span><span class="sxs-lookup"><span data-stu-id="cae82-110">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="cae82-111">在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：</span><span class="sxs-lookup"><span data-stu-id="cae82-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="cae82-112">克隆 DefaultHoloLens2InputSystemProfile 并为其指定合适的名称，例如 GettingStarted_HoloLens2InputSystemProfile</span><span class="sxs-lookup"><span data-stu-id="cae82-112">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="cae82-113">展开“指针”部分</span><span class="sxs-lookup"><span data-stu-id="cae82-113">Expand the **Pointers** section</span></span>
* <span data-ttu-id="cae82-114">克隆 DefaultMixedRealityPointerProfile 并为其指定合适的名称，例如 GettingStarted_MixedRealityPointerProfile</span><span class="sxs-lookup"><span data-stu-id="cae82-114">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="cae82-115">找到“凝视设置”部分，并选中“是否启用了眼动跟踪”复选框 </span><span class="sxs-lookup"><span data-stu-id="cae82-115">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![应用了新创建的配置文件并启用了眼动跟踪的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="cae82-117">有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="cae82-117">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="cae82-118">为 Unity 编辑器启用模拟的眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="cae82-118">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="cae82-119">在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡，然后执行以下操作 ：</span><span class="sxs-lookup"><span data-stu-id="cae82-119">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="cae82-120">展开“输入数据提供者” > “输入模拟服务”部分 </span><span class="sxs-lookup"><span data-stu-id="cae82-120">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="cae82-121">克隆 DefaultMixedRealityInputSimulationProfile 并为其指定合适的名称，例如 GettingStarted_MixedRealityInputSimulationProfile</span><span class="sxs-lookup"><span data-stu-id="cae82-121">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="cae82-122">找到“眼睛凝视模拟”，并将“默认眼睛凝视模拟模式”设置为“摄像头前轴”  </span><span class="sxs-lookup"><span data-stu-id="cae82-122">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![选中了 TextMeshPro 对象的 Unity](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="cae82-124">将眼动跟踪添加到对象</span><span class="sxs-lookup"><span data-stu-id="cae82-124">Adding eye-tracking to objects</span></span>

<span data-ttu-id="cae82-125">在“层次结构”窗口中，展开“RoverExplorer” > “Buttons”，然后选择全部三个子按钮对象：</span><span class="sxs-lookup"><span data-stu-id="cae82-125">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![已选中 Button 对象的 Unity](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="cae82-127">在三个 Button 对象仍处于选中状态时，在“检查器”窗口中使用“添加组件”按钮将 EyeTrackingTarget 组件添加到所有选定对象 ：</span><span class="sxs-lookup"><span data-stu-id="cae82-127">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![选中了 TextMeshPro 对象并添加了组件的 Unity](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="cae82-129">在“层次结构”窗口中，展开“RoverExplorer” > “Buttons” > “Hints” > “SeeItSayItLabel” > “TextMeshPro”</span><span class="sxs-lookup"><span data-stu-id="cae82-129">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="cae82-130">在“层次结构”窗口中，选择“Hints”按钮对象，然后按以下方式配置“EyeTrackingTarget”组件： </span><span class="sxs-lookup"><span data-stu-id="cae82-130">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="cae82-131">在“On Look At Start ()”事件部分</span><span class="sxs-lookup"><span data-stu-id="cae82-131">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="cae82-132">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="cae82-132">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="cae82-133">将“Hints”按钮中的“TextMeshPro”对象分配给“None (Object)”字段  </span><span class="sxs-lookup"><span data-stu-id="cae82-133">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="cae82-134">在“无函数”下拉列表中选择“TextMeshPro” > “float fontSize”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="cae82-134">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="cae82-135">将参数设置为 0.06，以将 0.04 的当前字号增加 50%</span><span class="sxs-lookup"><span data-stu-id="cae82-135">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="cae82-136">在“On Look Away ()”事件部分</span><span class="sxs-lookup"><span data-stu-id="cae82-136">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="cae82-137">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="cae82-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="cae82-138">将“Hints”按钮中的“TextMeshPro”对象分配给“None (Object)”字段  </span><span class="sxs-lookup"><span data-stu-id="cae82-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="cae82-139">在“无函数”下拉列表中选择“TextMeshPro” > “float fontSize”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="cae82-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="cae82-140">将参数设置为 0.04 以将字号重置为 0.04</span><span class="sxs-lookup"><span data-stu-id="cae82-140">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![选中了“提示 TextMeshPro 对象”并配置了 EyeTrackingTarget 组件的 Unity](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="cae82-142">对“Explode”和“Reset”按钮对象重复此步骤，为剩余按钮配置眼动跟踪。  </span><span class="sxs-lookup"><span data-stu-id="cae82-142">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="cae82-143">如果你现在进入游戏模式，然后按住鼠标右键，同时移动鼠标，直到凝视命中的某个按钮出现，你将看到文本字号增加了 50%，而鼠标移走时字号将重置回其原始大小：</span><span class="sxs-lookup"><span data-stu-id="cae82-143">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![视线对准眼动跟踪目标“分解”按钮标签的 Unity“播放”模式分屏视图](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="cae82-145">祝贺</span><span class="sxs-lookup"><span data-stu-id="cae82-145">Congratulations</span></span>

<span data-ttu-id="cae82-146">在本教程中，你了解了如何为 HoloLens 2 启用眼动跟踪，以及在用户查看对象时如何将眼动跟踪添加到对象以触发操作。</span><span class="sxs-lookup"><span data-stu-id="cae82-146">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cae82-147">下一教程：9.使用语音命令</span><span class="sxs-lookup"><span data-stu-id="cae82-147">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
