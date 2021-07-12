---
title: 使用语音命令
description: 本课程介绍如何使用混合现实工具包 (MRTK) 在混合现实应用中设置、创建和使用语音命令。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 语音命令, 语音输入
ms.localizationpriority: high
ms.openlocfilehash: 9422c16781af33fa3d68d7f6046e3a86c4b36b44
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403368"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="09973-104">9.使用语音命令</span><span class="sxs-lookup"><span data-stu-id="09973-104">9. Using speech commands</span></span>

<span data-ttu-id="09973-105">本教程将介绍如何创建语音命令，以及如何在全局范围内对其进行控制。</span><span class="sxs-lookup"><span data-stu-id="09973-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="09973-106">还将介绍如何控制需要用户查看控制语音命令的对象的本地语音命令。</span><span class="sxs-lookup"><span data-stu-id="09973-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="09973-107">目标</span><span class="sxs-lookup"><span data-stu-id="09973-107">Objectives</span></span>

* <span data-ttu-id="09973-108">了解如何创建语音命令</span><span class="sxs-lookup"><span data-stu-id="09973-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="09973-109">了解如何在全局和本地控制语音命令</span><span class="sxs-lookup"><span data-stu-id="09973-109">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="09973-110">确保启用麦克风功能</span><span class="sxs-lookup"><span data-stu-id="09973-110">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="09973-111">在 Unity 菜单中，选择“混合现实”>“工具包”>“实用工具”>“为 MRTK 配置项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：</span><span class="sxs-lookup"><span data-stu-id="09973-111">In the Unity menu, select Mixed Reality > Toolkit > Utilities > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![启用麦克风功能](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="09973-113">在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指令期间，应该已经启用了麦克风功能。</span><span class="sxs-lookup"><span data-stu-id="09973-113">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="09973-114">但如果未启用此功能，请确保立即启用。</span><span class="sxs-lookup"><span data-stu-id="09973-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="09973-115">创建语音命令</span><span class="sxs-lookup"><span data-stu-id="09973-115">Creating speech commands</span></span>

<span data-ttu-id="09973-116">在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：</span><span class="sxs-lookup"><span data-stu-id="09973-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="09973-117">展开“语音”部分</span><span class="sxs-lookup"><span data-stu-id="09973-117">Expand the **Speech** section</span></span>
* <span data-ttu-id="09973-118">克隆 DefaultMixedRealitySpeechCommandsProfile 并为其指定一个适当的名称，例如 GettingStarted_MixedRealitySpeechCommandsProfile</span><span class="sxs-lookup"><span data-stu-id="09973-118">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="09973-119">验证“启动行为”是否设置为“自动启动” </span><span class="sxs-lookup"><span data-stu-id="09973-119">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![创建语音命令](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="09973-121">有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="09973-121">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="09973-122">在“语音”>“语音命令”部分，单击“+ 添加新的语音命令”按钮四次，以在现有语音命令列表种添加四个新的语音命令，然后在“关键字”字段中输入以下短语  ：</span><span class="sxs-lookup"><span data-stu-id="09973-122">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="09973-123">启用指示器</span><span class="sxs-lookup"><span data-stu-id="09973-123">Enable Indicator</span></span>
* <span data-ttu-id="09973-124">启用点击放置</span><span class="sxs-lookup"><span data-stu-id="09973-124">Enable Tap to Place</span></span>
* <span data-ttu-id="09973-125">启用边界控制</span><span class="sxs-lookup"><span data-stu-id="09973-125">Enable Bounds Control</span></span>
* <span data-ttu-id="09973-126">禁用边界控制</span><span class="sxs-lookup"><span data-stu-id="09973-126">Disable Bounds Control</span></span>

![添加新语音命令](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="09973-128">如果计算机没有麦克风，可向语音命令分配一个 KeyCode，以便在按下相应的键时触发它们。</span><span class="sxs-lookup"><span data-stu-id="09973-128">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="09973-129">控制语音命令</span><span class="sxs-lookup"><span data-stu-id="09973-129">Controlling speech commands</span></span>

<span data-ttu-id="09973-130">在“项目”窗口中，导航到“包” > “混合现实工具包基础” > “SDK” > “功能” > “UX” > “预制件” > “工具提示”文件夹，以查找工具提示预制件      ：</span><span class="sxs-lookup"><span data-stu-id="09973-130">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![打开工具提示文件夹](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="09973-132">在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”，将空对象添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="09973-132">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="09973-133">将对象命名为 SpeechInputHandler_Global，然后在“检查器”窗口中，使用“添加组件”按钮添加 SpeechInputHandler 组件，并按如下所示对其进行配置  ：</span><span class="sxs-lookup"><span data-stu-id="09973-133">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="09973-134">取消选中“需要焦点”复选框，使用户无需查看带有 SpeechInputHandler 组件的对象即可触发语音命令 </span><span class="sxs-lookup"><span data-stu-id="09973-134">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="09973-135">从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 </span><span class="sxs-lookup"><span data-stu-id="09973-135">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![配置语音输入处理程序组件](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="09973-137">在 SpeechInputHandler 组件上，单击小 + 图标三次，添加三个关键字元素：</span><span class="sxs-lookup"><span data-stu-id="09973-137">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![向语音输入处理程序添加关键字元素](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="09973-139">展开“元素 0”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="09973-139">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="09973-140">在“关键字”字段中，输入“启用指示器”，以引用在上一部分中创建的“启用指示器”语音命令 </span><span class="sxs-lookup"><span data-stu-id="09973-140">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="09973-141">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="09973-141">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="09973-142">从“层次结构”窗口中，向“无(对象)”字段分配 Indicator 对象 </span><span class="sxs-lookup"><span data-stu-id="09973-142">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="09973-143">从“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="09973-143">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="09973-144">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="09973-144">Check the argument checkbox, so it is **checked**</span></span>

![配置关键字元素 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="09973-146">展开“元素 1”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="09973-146">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="09973-147">在“关键字”字段中，输入“启用边界控制”，以引用在上一部分中创建的“启用边界控制”命令 </span><span class="sxs-lookup"><span data-stu-id="09973-147">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="09973-148">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="09973-148">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="09973-149">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="09973-149">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="09973-150">在“无函数”下拉列表中选择“BoundsControl” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="09973-150">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="09973-151">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="09973-151">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="09973-152">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="09973-152">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="09973-153">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="09973-153">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="09973-154">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="09973-154">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="09973-155">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="09973-155">Check the argument checkbox, so it is **checked**</span></span>

![配置关键字元素 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="09973-157">展开“元素 2”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="09973-157">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="09973-158">在“关键字”字段中，输入“禁用边界控制”，以引用在上一部分中创建的“禁用边界控制”命令 </span><span class="sxs-lookup"><span data-stu-id="09973-158">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="09973-159">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="09973-159">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="09973-160">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="09973-160">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="09973-161">在“无函数”下拉列表中选择“BoundsControl” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="09973-161">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="09973-162">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="09973-162">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="09973-163">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="09973-163">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="09973-164">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="09973-164">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="09973-165">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="09973-165">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="09973-166">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="09973-166">Verify that the argument checkbox is **unchecked**</span></span>

![配置关键字元素 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="09973-168">在“层次结构”窗口中依次选择“RoverExplorer”>“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“SpeechInputHandler”组件，并按如下所述配置该组件：  </span><span class="sxs-lookup"><span data-stu-id="09973-168">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="09973-169">验证是否已选中“需要焦点”复选框，使用户需要查看带有 SpeechInputHandler 组件的对象才可触发语音命令 </span><span class="sxs-lookup"><span data-stu-id="09973-169">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="09973-170">从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 </span><span class="sxs-lookup"><span data-stu-id="09973-170">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![将语音输入处理程序添加到 Rover Assembly](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="09973-172">在 SpeechInputHandler 组件上，单击小 + 图标以添加关键字元素，展开新创建的元素，然后按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="09973-172">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="09973-173">在“关键字”字段中，输入“启用点击放置”，以引用在上一部分中创建的“启用点击放置”命令 </span><span class="sxs-lookup"><span data-stu-id="09973-173">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="09973-174">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="09973-174">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="09973-175">从“层次结构”窗口中，将对象本身（即 RoverAssembly 对象）分配给“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="09973-175">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="09973-176">在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="09973-176">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="09973-177">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="09973-177">Check the argument checkbox, so it is **checked**</span></span>

![配置 Rover Assembly 上的语音输入处理程序](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="09973-179">祝贺</span><span class="sxs-lookup"><span data-stu-id="09973-179">Congratulations</span></span>

<span data-ttu-id="09973-180">在本教程中，你学习了如何创建语音命令，以及如何在全局范围内对其进行控制。</span><span class="sxs-lookup"><span data-stu-id="09973-180">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="09973-181">还了解了如何控制需要用户查看控制语音命令的对象的本地语音命令。</span><span class="sxs-lookup"><span data-stu-id="09973-181">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="09973-182">[入门教程](mr-learning-base-01.md)系列到此也就结束了。</span><span class="sxs-lookup"><span data-stu-id="09973-182">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="09973-183">通过这些教程，你成功使用 MRTK 从头构建了一个完整的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="09973-183">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="09973-184">接下来的 [Azure 空间定位点](mr-learning-asa-01.md)和[多用户功能教程](mr-learning-sharing-01.md)这两个教程系列将首先介绍如何将 Azure 空间定位点集成到你的项目中，以定位在现实世界中创建的漫游者探测器体验。</span><span class="sxs-lookup"><span data-stu-id="09973-184">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="09973-185">然后，将介绍如何将多用户功能添加到你的项目，以实时共享用户和对象的移动情况。</span><span class="sxs-lookup"><span data-stu-id="09973-185">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="09973-186">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="09973-186">Next Development Checkpoint</span></span>

<span data-ttu-id="09973-187">如果你遵循我们规划的 Unity 开发检查点历程，你的下一项任务就是熟悉混合现实应用的核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="09973-187">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="09973-188">基本交互</span><span class="sxs-lookup"><span data-stu-id="09973-188">Basic interactions</span></span>](/windows/mixed-reality/mrtk-unity/)

<span data-ttu-id="09973-189">你可以随时返回到 [Unity 开发检查点](../unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="09973-189">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>
