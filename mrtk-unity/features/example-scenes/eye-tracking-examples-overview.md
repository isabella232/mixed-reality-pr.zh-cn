---
title: 目视跟踪示例概述
description: 用于在 MRTK 中生成 eyetracking 的示例
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，EyeTracking，
ms.openlocfilehash: 4cdeaa10725e00ac1a041c3692d64c1bd6488854
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175546"
---
# <a name="eye-tracking-examples-overview"></a>目视跟踪示例概述

本主题介绍了如何在 MRTK 中快速开始使用目视跟踪，方法是在 MRTK 眼跟踪示例 (资产/MRTK/示例/演示/EyeTracking) 上构建。
这些示例可让你体验我们的新神奇输入功能： **目视跟踪**！
此演示包括各种用例，从隐式的基于目视的激活到如何无缝地将有关所查看内容的信息与 **语音** 和 **手写** 输入相关。
这样，用户就可以通过查看目标并说 _"选择"_ 或执行手动手势，在视图中快速轻松地选择和移动全息内容。
演示还包括一个用于目视定向滚动的示例、文本和图像在石板上的平移和缩放。
最后，还提供了一个示例，用于记录和直观显示二维石板上用户的视觉对象。
在下一节中，你将了解 MRTK 目视跟踪示例包 (资产/MRTK/示例/演示/EyeTracking) 中每个不同示例的详细信息，包括：

![目视跟踪场景列表](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

以下部分简要概述了各个目视跟踪演示的幕后内容。
MRTK 目视跟踪演示场景已 [加载添加性地](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)，我们将在下面介绍如何设置。

## <a name="overview-of-the-eye-tracking-demo-samples"></a>目视跟踪演示示例概述

### <a name="eye-supported-target-selection"></a>[**目视支持的目标选择**](../input/eye-tracking/eye-tracking-target-selection.md)

本教程展示了访问眼睛数据以选择目标的便利。
它包括一个微妙但功能强大的反馈示例，可让用户自信地了解目标，而不会带来巨大的作用。
此外，还提供了一个简单的智能通知示例，可在读取后自动消失。

**摘要**：通过眼睛、语音和手写输入的组合来快速轻松地进行目标选择。

### <a name="eye-supported-navigation"></a>[**目视支持的导航**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine 您正在阅读有关远处显示或您的电子读者的某些信息，并且到达显示文本的末尾时，文本会自动向上滚动以显示更多内容。
或者怎样才能直接缩放到你所关注的位置呢？
以下是本教程中有关目视支持的导航的一些示例展示。
此外，还提供了一种无人参与的3D 全息旋转示例，使其根据当前焦点自动旋转。

**摘要**：使用眼睛、声音和手写输入的组合进行滚动、平移、缩放、3d 旋转。

### <a name="eye-supported-positioning"></a>[**目视支持的定位**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

本教程展示了一种名为 "Put" 的输入方案 [-](https://youtu.be/CbIn8p4_4CQ) 在早期的1980年中，可以从 MIT Media Lab 可追溯到 "信息检索"。
思路非常简单：从眼睛中获益，实现快速目标选择和定位。
只需查看一个全息图，说 _"放置此"_，就可以在想要放置它的位置寻找 _"！"_。
为了更精确地定位全息图，你可以使用手中的其他输入、声音或控制器。

**摘要**：使用眼睛、语音和手写输入 (*拖放*) 来定位全息影像。 使用眼睛和双手的眼睛支持的滑块。

### <a name="visualization-of-visual-attention"></a>**视觉对象视觉对象**

基于用户所在位置的数据使极具强大的工具可评估设计的可用性，并识别高效工作流中的问题。
本教程介绍了不同的目视跟踪可视化效果，以及它们如何满足不同的需求。
我们提供了用于记录和加载目视跟踪数据的基本示例，以及如何对其进行可视化的示例。

**摘要**：清单上 (热图) 的二维注意事项。 录制 & 重播目视跟踪数据。

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>设置 MRTK 目视跟踪示例

### <a name="prerequisites"></a>先决条件

请注意，在设备上使用目视跟踪示例需要 HoloLens 2 和使用包的 appxmanifest.xml 上的 "注视输入" 功能生成的示例应用程序包。

若要在设备上使用这些目视跟踪示例，请确保在 Visual Studio 中生成应用之前执行[以下步骤](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2)。

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Load EyeTrackingDemo-00-RootScene

*EyeTrackingDemo-00-RootScene* 是包含所有核心 MRTK 组件) 场景的基本 (_根_。
这是你首先需要加载的场景，你将在其中运行眼睛跟踪演示。
它具有图形场景菜单，可让你轻松地在将 [加载添加性地](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)的不同眼睛跟踪示例之间切换。

![目视跟踪示例中的场景菜单](../images/eye-tracking/mrtk_et_scenemenu.jpg)

根场景包括一些核心组件，这些组件将在添加性地加载的场景（如 MRTK 配置的配置文件和场景相机）之间保持。
_MixedRealityBasicSceneSetup_ (参阅下面的屏幕截图) 包含一个脚本，该脚本将在启动时自动加载引用的场景。
默认情况下，这是 _EyeTrackingDemo-TargetSelection_。  

![OnLoadStartScene 脚本示例](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. 将场景添加到 "生成" 菜单

若要在运行时加载附加场景，必须先将这些场景添加到 "生成" 菜单 _中设置 > "场景_。
根场景在列表中显示为第一个场景，这一点很重要：

![用于眼睛跟踪示例的 "构建设置场景" 菜单](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. 在 Unity 编辑器中播放眼睛跟踪示例

将眼睛跟踪场景添加到生成设置并加载 _EyeTrackingDemo-00-RootScene_ 后，你可能需要检查的最后一件事是：是否已启用附加到 _MixedRealityBasicSceneSetup_ GameObject 的 _"OnLoadStartScene"_ 脚本？ 这是为了让根场景知道要首先加载哪个演示场景。

![OnLoad_StartScene 脚本的示例](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

让我们开始吧！ 点击 _"播放"_！
此时会显示多个宝物，屏幕顶部会显示场景菜单。

![ET 目标选择场景中的示例屏幕截图](../images/eye-tracking/mrtk_et_targetselect.png)

你还应注意到游戏视图中心的小半透明圆圈。
这作为 _模拟眼睛_ (光标) 的指示器：只需按下鼠标 _右键_ ，然后移动鼠标更改其位置。
当光标悬停在 gem 上时，您会注意到它将与当前查看的 gem 的中心对齐。
这是一种很好的方法，可用于测试在目标 _"查找&quot;_ 时是否按预期触发事件。
请注意，通过鼠标控制的 _模拟眼睛_ 看不太太好了我们的快速和意外的眼睛运动。
不过，它非常适合于测试基本功能，然后再通过将其部署到 HoloLens 2 设备来循环访问设计。
返回到我们的眼睛跟踪示例场景：只要查看并可通过 &quot;查看&quot; 来销毁 gem，gem 就会旋转 .。。

- 按 _enter_ (模拟口述 &quot;select" ) 
- 说 _"选择"_ 到麦克风
- 按 _空格键_ 显示模拟手写输入时，请单击鼠标左键以执行模拟的挤压

我们更详细地介绍了如何在 [**目视支持的目标选择**](../input/eye-tracking/eye-tracking-target-selection.md) 教程中实现这些交互。

将光标上移到场景中的顶部菜单栏时，你会注意到当前悬停的项将会有变化。
您可以使用以上所述的提交方法之一来选择当前突出显示的项 (例如，按 _enter_) 。
这样，便可以在不同的目视跟踪示例场景之间切换。

### <a name="4-how-to-test-specific-sub-scenes"></a>4. 如何测试特定的子场景

处理特定方案时，您可能不希望每次都浏览场景菜单。
相反，你可能想要直接从当前正在处理的场景开始，按下 " _播放_ " 按钮。
没问题！ 下面是你可以执行的操作：

1. 加载 _根_ 场景
2. 在 _根_ 场景中，禁用 _"OnLoadStartScene"_ 脚本
3. 将下面所述的眼睛跟踪测试场景之一 _拖放_ (或任何其他场景) 到 _层次结构_ 视图中，如下面的屏幕截图中所示。

    ![加法场景示例](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. 按下 _播放_

请注意，加载这样的子场景不是永久性的：这意味着，如果将应用程序部署到 HoloLens 2 设备，则它将只加载根场景 (，因为它会出现在生成设置) 的顶部。
此外，当你与他人共享你的项目时，不会自动加载子场景。

---

现在，你已了解如何让 MRTK 目视跟踪示例场景工作，接下来让我们进一步深入了解如何选择你的眼睛： [目视支持的目标选择](../input/eye-tracking/eye-tracking-target-selection.md)。

---
[返回 "MixedRealityToolkit" 中的眼睛跟踪](../input/eye-tracking/eye-tracking-Main.md)
