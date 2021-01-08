---
title: MRTK 教程 - 9. 使用语音命令
description: 本课程介绍如何将语音命令与混合现实工具包 (MRTK) 结合使用。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 语音命令, 语音输入
ms.localizationpriority: high
ms.openlocfilehash: 6e008f3e46bc4a22499691e284020321d29a2f23
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613461"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="875d1-105">9.使用语音命令</span><span class="sxs-lookup"><span data-stu-id="875d1-105">9. Using speech commands</span></span>

## <a name="overview"></a><span data-ttu-id="875d1-106">概述</span><span class="sxs-lookup"><span data-stu-id="875d1-106">Overview</span></span>

<span data-ttu-id="875d1-107">本教程将介绍如何创建语音命令，以及如何在全局范围内对其进行控制。</span><span class="sxs-lookup"><span data-stu-id="875d1-107">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="875d1-108">还将介绍如何控制需要用户查看控制语音命令的对象的本地语音命令。</span><span class="sxs-lookup"><span data-stu-id="875d1-108">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="875d1-109">目标</span><span class="sxs-lookup"><span data-stu-id="875d1-109">Objectives</span></span>

* <span data-ttu-id="875d1-110">了解如何创建语音命令</span><span class="sxs-lookup"><span data-stu-id="875d1-110">Learn how to create speech commands</span></span>
* <span data-ttu-id="875d1-111">了解如何在全局和本地控制语音命令</span><span class="sxs-lookup"><span data-stu-id="875d1-111">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="875d1-112">确保启用麦克风功能</span><span class="sxs-lookup"><span data-stu-id="875d1-112">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="875d1-113">在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：</span><span class="sxs-lookup"><span data-stu-id="875d1-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![启用麦克风功能](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="875d1-115">在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings)指令期间，应该已经启用了麦克风功能。</span><span class="sxs-lookup"><span data-stu-id="875d1-115">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="875d1-116">但如果未启用此功能，请确保立即启用。</span><span class="sxs-lookup"><span data-stu-id="875d1-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="875d1-117">创建语音命令</span><span class="sxs-lookup"><span data-stu-id="875d1-117">Creating speech commands</span></span>

<span data-ttu-id="875d1-118">在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：</span><span class="sxs-lookup"><span data-stu-id="875d1-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="875d1-119">展开“语音”部分</span><span class="sxs-lookup"><span data-stu-id="875d1-119">Expand the **Speech** section</span></span>
* <span data-ttu-id="875d1-120">克隆 DefaultMixedRealitySpeechCommandsProfile 并为其指定一个适当的名称，例如 GettingStarted_MixedRealitySpeechCommandsProfile</span><span class="sxs-lookup"><span data-stu-id="875d1-120">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="875d1-121">验证“启动行为”是否设置为“自动启动” </span><span class="sxs-lookup"><span data-stu-id="875d1-121">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![创建语音命令](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="875d1-123">有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="875d1-123">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="875d1-124">在“语音”>“语音命令”部分，单击“+ 添加新的语音命令”按钮四次，以在现有语音命令列表种添加四个新的语音命令，然后在“关键字”字段中输入以下短语  ：</span><span class="sxs-lookup"><span data-stu-id="875d1-124">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="875d1-125">启用指示器</span><span class="sxs-lookup"><span data-stu-id="875d1-125">Enable Indicator</span></span>
* <span data-ttu-id="875d1-126">启用点击放置</span><span class="sxs-lookup"><span data-stu-id="875d1-126">Enable Tap to Place</span></span>
* <span data-ttu-id="875d1-127">启用边界框</span><span class="sxs-lookup"><span data-stu-id="875d1-127">Enable Bounding Box</span></span>
* <span data-ttu-id="875d1-128">禁用边界框</span><span class="sxs-lookup"><span data-stu-id="875d1-128">Disable Bounding Box</span></span>

![添加新语音命令](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="875d1-130">如果计算机没有麦克风，可向语音命令分配一个 KeyCode，以便在按下相应的键时触发它们。</span><span class="sxs-lookup"><span data-stu-id="875d1-130">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="875d1-131">控制语音命令</span><span class="sxs-lookup"><span data-stu-id="875d1-131">Controlling speech commands</span></span>

<span data-ttu-id="875d1-132">在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “功能” > “UX” > “预制件” > “工具提示”文件夹，以查找工具提示预制件      ：</span><span class="sxs-lookup"><span data-stu-id="875d1-132">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![打开工具提示文件夹](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="875d1-134">在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”，将空对象添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="875d1-134">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="875d1-135">将对象命名为 SpeechInputHandler_Global，然后在“检查器”窗口中，使用“添加组件”按钮添加 SpeechInputHandler 组件，并按如下所示对其进行配置  ：</span><span class="sxs-lookup"><span data-stu-id="875d1-135">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="875d1-136">取消选中“需要焦点”复选框，使用户无需查看带有 SpeechInputHandler 组件的对象即可触发语音命令 </span><span class="sxs-lookup"><span data-stu-id="875d1-136">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="875d1-137">从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 </span><span class="sxs-lookup"><span data-stu-id="875d1-137">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![配置语音输入处理程序组件](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="875d1-139">在 SpeechInputHandler 组件上，单击小 + 图标三次，添加三个关键字元素：</span><span class="sxs-lookup"><span data-stu-id="875d1-139">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![向语音输入处理程序添加关键字元素](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="875d1-141">展开“元素 0”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="875d1-141">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="875d1-142">在“关键字”字段中，输入“启用指示器”，以引用在上一部分中创建的“启用指示器”语音命令 </span><span class="sxs-lookup"><span data-stu-id="875d1-142">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="875d1-143">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="875d1-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="875d1-144">从“层次结构”窗口中，向“无(对象)”字段分配 Indicator 对象 </span><span class="sxs-lookup"><span data-stu-id="875d1-144">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="875d1-145">从“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="875d1-145">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="875d1-146">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="875d1-146">Check the argument checkbox, so it is **checked**</span></span>

![配置关键字元素 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="875d1-148">展开“元素 1”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="875d1-148">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="875d1-149">在“关键字”字段中，输入“启用边界框”，以引用在上一部分中创建的“启用边界框”命令 </span><span class="sxs-lookup"><span data-stu-id="875d1-149">In the **Keyword** field, enter **Enable Bounding Box**, to reference the Enable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="875d1-150">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="875d1-150">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="875d1-151">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="875d1-151">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="875d1-152">在“无函数”下拉列表中选择“BoundingBox” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="875d1-152">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="875d1-153">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="875d1-153">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="875d1-154">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="875d1-154">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="875d1-155">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="875d1-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="875d1-156">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="875d1-156">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="875d1-157">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="875d1-157">Check the argument checkbox, so it is **checked**</span></span>

![配置关键字元素 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="875d1-159">展开“元素 2”并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="875d1-159">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="875d1-160">在“关键字”字段中，输入“禁用边界框”，以引用在上一部分中创建的“禁用边界框”命令 </span><span class="sxs-lookup"><span data-stu-id="875d1-160">In the **Keyword** field, enter **Disable Bounding Box**, to reference the Disable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="875d1-161">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="875d1-161">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="875d1-162">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="875d1-162">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="875d1-163">在“无函数”下拉列表中选择“BoundingBox” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="875d1-163">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="875d1-164">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="875d1-164">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="875d1-165">单击小 + 图标以添加另一个事件</span><span class="sxs-lookup"><span data-stu-id="875d1-165">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="875d1-166">从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 </span><span class="sxs-lookup"><span data-stu-id="875d1-166">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="875d1-167">在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="875d1-167">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="875d1-168">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="875d1-168">Verify that the argument checkbox is **unchecked**</span></span>

![配置关键字元素 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="875d1-170">在“层次结构”窗口中依次选择“RoverExplorer”>“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“SpeechInputHandler”组件，并按如下所述配置该组件：  </span><span class="sxs-lookup"><span data-stu-id="875d1-170">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="875d1-171">验证是否已选中“需要焦点”复选框，使用户需要查看带有 SpeechInputHandler 组件的对象才可触发语音命令 </span><span class="sxs-lookup"><span data-stu-id="875d1-171">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="875d1-172">从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 </span><span class="sxs-lookup"><span data-stu-id="875d1-172">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![将语音输入处理程序添加到 Rover Assembly](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="875d1-174">在 SpeechInputHandler 组件上，单击小 + 图标以添加关键字元素，展开新创建的元素，然后按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="875d1-174">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="875d1-175">在“关键字”字段中，输入“启用点击放置”，以引用在上一部分中创建的“启用点击放置”命令 </span><span class="sxs-lookup"><span data-stu-id="875d1-175">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="875d1-176">单击 + 图标以添加事件</span><span class="sxs-lookup"><span data-stu-id="875d1-176">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="875d1-177">从“层次结构”窗口中，将对象本身（即 RoverAssembly 对象）分配给“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="875d1-177">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="875d1-178">在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="875d1-178">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="875d1-179">选中参数复选框，让其处于选中状态</span><span class="sxs-lookup"><span data-stu-id="875d1-179">Check the argument checkbox, so it is **checked**</span></span>

![配置 Rover Assembly 上的语音输入处理程序](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="875d1-181">祝贺</span><span class="sxs-lookup"><span data-stu-id="875d1-181">Congratulations</span></span>

<span data-ttu-id="875d1-182">在本教程中，你学习了如何创建语音命令，以及如何在全局范围内对其进行控制。</span><span class="sxs-lookup"><span data-stu-id="875d1-182">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="875d1-183">还了解了如何控制需要用户查看控制语音命令的对象的本地语音命令。</span><span class="sxs-lookup"><span data-stu-id="875d1-183">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="875d1-184">[入门教程](mr-learning-base-01.md)系列到此也就结束了。</span><span class="sxs-lookup"><span data-stu-id="875d1-184">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="875d1-185">通过这些教程，你成功使用 MRTK 从头构建了一个完整的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="875d1-185">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="875d1-186">接下来的 [Azure 空间定位点](mr-learning-asa-01.md)和[多用户功能教程](mr-learning-sharing-01.md)这两个教程系列将首先介绍如何将 Azure 空间定位点集成到你的项目中，以定位在现实世界中创建的漫游者探测器体验。</span><span class="sxs-lookup"><span data-stu-id="875d1-186">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="875d1-187">然后，将介绍如何将多用户功能添加到你的项目，以实时共享用户和对象的移动情况。</span><span class="sxs-lookup"><span data-stu-id="875d1-187">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="875d1-188">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="875d1-188">Next Development Checkpoint</span></span>

<span data-ttu-id="875d1-189">如果你遵循我们规划的 Unity 开发检查点历程，你的下一项任务就是熟悉混合现实应用的核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="875d1-189">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="875d1-190">基本交互</span><span class="sxs-lookup"><span data-stu-id="875d1-190">Basic interactions</span></span>](../mrtk-101.md)

<span data-ttu-id="875d1-191">你可以随时返回到 [Unity 开发检查点](../unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="875d1-191">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>

