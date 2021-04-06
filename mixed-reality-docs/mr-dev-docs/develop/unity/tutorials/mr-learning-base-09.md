---
title: 使用语音命令
description: 本课程介绍如何使用混合现实工具包 (MRTK) 在混合现实应用中设置、创建和使用语音命令。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 语音命令, 语音输入
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982923"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="63194-104">9.使用语音命令</span><span class="sxs-lookup"><span data-stu-id="63194-104">9. Using speech commands</span></span>

<span data-ttu-id="63194-105">本教程将介绍如何创建语音命令，以及如何在全局范围内对其进行控制。</span><span class="sxs-lookup"><span data-stu-id="63194-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="63194-106">还将介绍如何控制需要用户查看控制语音命令的对象的本地语音命令。</span><span class="sxs-lookup"><span data-stu-id="63194-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="63194-107">目标</span><span class="sxs-lookup"><span data-stu-id="63194-107">Objectives</span></span>

* <span data-ttu-id="63194-108">了解如何创建语音命令</span><span class="sxs-lookup"><span data-stu-id="63194-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="63194-109">了解如何在全局和本地控制语音命令</span><span class="sxs-lookup"><span data-stu-id="63194-109">Learn how to control speech commands globally and locally</span></span>

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a><span data-ttu-id="63194-110">创建语音命令</span><span class="sxs-lookup"><span data-stu-id="63194-110">Creating speech commands</span></span>

<span data-ttu-id="63194-111">在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：</span><span class="sxs-lookup"><span data-stu-id="63194-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="63194-112">展开“语音”部分</span><span class="sxs-lookup"><span data-stu-id="63194-112">Expand the **Speech** section</span></span>
* <span data-ttu-id="63194-113">克隆 DefaultMixedRealitySpeechCommandsProfile 并为其指定一个适当的名称，例如 GettingStarted_MixedRealitySpeechCommandsProfile</span><span class="sxs-lookup"><span data-stu-id="63194-113">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="63194-114">验证“启动行为”是否设置为“自动启动” </span><span class="sxs-lookup"><span data-stu-id="63194-114">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![创建语音命令](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="63194-116">有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="63194-116">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="63194-117">在“语音”>“语音命令”部分，单击“+ 添加新的语音命令”按钮四次，以在现有语音命令列表种添加四个新的语音命令，然后在“关键字”字段中输入以下短语  ：</span><span class="sxs-lookup"><span data-stu-id="63194-117">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="63194-118">启用指示器</span><span class="sxs-lookup"><span data-stu-id="63194-118">Enable Indicator</span></span>
* <span data-ttu-id="63194-119">启用点击放置</span><span class="sxs-lookup"><span data-stu-id="63194-119">Enable Tap to Place</span></span>
* <span data-ttu-id="63194-120">启用边界控制</span><span class="sxs-lookup"><span data-stu-id="63194-120">Enable Bounds Control</span></span>
* <span data-ttu-id="63194-121">禁用边界控制</span><span class="sxs-lookup"><span data-stu-id="63194-121">Disable Bounds Control</span></span>

![添加新语音命令](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="63194-123">如果计算机没有麦克风，可向语音命令分配一个 KeyCode，以便在按下相应的键时触发它们。</span><span class="sxs-lookup"><span data-stu-id="63194-123">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="63194-124">控制语音命令</span><span class="sxs-lookup"><span data-stu-id="63194-124">Controlling speech commands</span></span>

<span data-ttu-id="63194-125">在“项目”窗口中，导航到“包” > “混合现实工具包基础” > “SDK” > “功能” > “UX” > “预制件” > “工具提示”文件夹，以查找工具提示预制件      ：</span><span class="sxs-lookup"><span data-stu-id="63194-125">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![打开工具提示文件夹](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="63194-127">在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”，将空对象添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="63194-127">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="63194-128">将对象命名为 SpeechInputHandler_Global，然后在“检查器”窗口中，使用“添加组件”按钮添加 SpeechInputHandler 组件，并按如下所示对其进行配置  ：</span><span class="sxs-lookup"><span data-stu-id="63194-128">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="63194-129">取消选中“需要焦点”复选框，使用户无需查看带有 SpeechInputHandler 组件的对象即可触发语音命令 </span><span class="sxs-lookup"><span data-stu-id="63194-129">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="63194-130">从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 </span><span class="sxs-lookup"><span data-stu-id="63194-130">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![配置语音输入处理程序组件](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="63194-132">在 SpeechInputHandler 组件上，单击小 + 图标三次，添加三个关键字元素：</span><span class="sxs-lookup"><span data-stu-id="63194-132">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![向语音输入处理程序添加关键字元素](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="63194-134">展开“元素 0”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="63194-134">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="63194-135">在“关键字”字段中，输入“启用指示器”，以引用在上一部分中创建的“启用指示器”语音命令 </span><span class="sxs-lookup"><span data-stu-id="63194-135">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="63194-136">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="63194-136">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="63194-137">从“层次结构”窗口中，向“无(对象)”字段分配 Indicator 对象 </span><span class="sxs-lookup"><span data-stu-id="63194-137">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="63194-138">从“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="63194-138">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="63194-139">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="63194-139">Check the argument checkbox, so it is **checked**</span></span>

![配置关键字元素 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="63194-141">展开“元素 1”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="63194-141">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="63194-142">在“关键字”字段中，输入“启用边界控制”，以引用在上一部分中创建的“启用边界控制”命令 </span><span class="sxs-lookup"><span data-stu-id="63194-142">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="63194-143">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="63194-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="63194-144">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="63194-144">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="63194-145">在“无函数”下拉列表中选择“BoundsControl” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="63194-145">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="63194-146">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="63194-146">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="63194-147">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="63194-147">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="63194-148">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="63194-148">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="63194-149">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="63194-149">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="63194-150">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="63194-150">Check the argument checkbox, so it is **checked**</span></span>

![配置关键字元素 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="63194-152">展开“元素 2”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="63194-152">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="63194-153">在“关键字”字段中，输入“禁用边界控制”，以引用在上一部分中创建的“禁用边界控制”命令 </span><span class="sxs-lookup"><span data-stu-id="63194-153">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="63194-154">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="63194-154">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="63194-155">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="63194-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="63194-156">在“无函数”下拉列表中选择“BoundsControl” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="63194-156">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="63194-157">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="63194-157">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="63194-158">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="63194-158">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="63194-159">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="63194-159">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="63194-160">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="63194-160">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="63194-161">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="63194-161">Verify that the argument checkbox is **unchecked**</span></span>

![配置关键字元素 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="63194-163">在“层次结构”窗口中依次选择“RoverExplorer”>“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“SpeechInputHandler”组件，并按如下所述配置该组件：  </span><span class="sxs-lookup"><span data-stu-id="63194-163">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="63194-164">验证是否已选中“需要焦点”复选框，使用户需要查看带有 SpeechInputHandler 组件的对象才可触发语音命令 </span><span class="sxs-lookup"><span data-stu-id="63194-164">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="63194-165">从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 </span><span class="sxs-lookup"><span data-stu-id="63194-165">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![将语音输入处理程序添加到 Rover Assembly](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="63194-167">在 SpeechInputHandler 组件上，单击小 + 图标以添加关键字元素，展开新创建的元素，然后按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="63194-167">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="63194-168">在“关键字”字段中，输入“启用点击放置”，以引用在上一部分中创建的“启用点击放置”命令 </span><span class="sxs-lookup"><span data-stu-id="63194-168">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="63194-169">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="63194-169">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="63194-170">从“层次结构”窗口中，将对象本身（即 RoverAssembly 对象）分配给“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="63194-170">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="63194-171">在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="63194-171">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="63194-172">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="63194-172">Check the argument checkbox, so it is **checked**</span></span>

![配置 Rover Assembly 上的语音输入处理程序](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="63194-174">祝贺</span><span class="sxs-lookup"><span data-stu-id="63194-174">Congratulations</span></span>

<span data-ttu-id="63194-175">在本教程中，你学习了如何创建语音命令，以及如何在全局范围内对其进行控制。</span><span class="sxs-lookup"><span data-stu-id="63194-175">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="63194-176">还了解了如何控制需要用户查看控制语音命令的对象的本地语音命令。</span><span class="sxs-lookup"><span data-stu-id="63194-176">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="63194-177">[入门教程](mr-learning-base-01.md)系列到此也就结束了。</span><span class="sxs-lookup"><span data-stu-id="63194-177">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="63194-178">通过这些教程，你成功使用 MRTK 从头构建了一个完整的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="63194-178">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="63194-179">接下来的 [Azure 空间定位点](mr-learning-asa-01.md)和[多用户功能教程](mr-learning-sharing-01.md)这两个教程系列将首先介绍如何将 Azure 空间定位点集成到你的项目中，以定位在现实世界中创建的漫游者探测器体验。</span><span class="sxs-lookup"><span data-stu-id="63194-179">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="63194-180">然后，将介绍如何将多用户功能添加到你的项目，以实时共享用户和对象的移动情况。</span><span class="sxs-lookup"><span data-stu-id="63194-180">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="63194-181">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="63194-181">Next Development Checkpoint</span></span>

<span data-ttu-id="63194-182">如果你遵循我们规划的 Unity 开发检查点历程，你的下一项任务就是熟悉混合现实应用的核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="63194-182">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="63194-183">基本交互</span><span class="sxs-lookup"><span data-stu-id="63194-183">Basic interactions</span></span>](../../../out-of-scope/mrtk-101.md)

<span data-ttu-id="63194-184">你可以随时返回到 [Unity 开发检查点](../unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="63194-184">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>