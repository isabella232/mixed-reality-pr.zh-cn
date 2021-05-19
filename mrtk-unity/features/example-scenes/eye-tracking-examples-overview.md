---
title: 目视跟踪示例概述
description: 用于在 MRTK 中生成 eyetracking 的示例
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，EyeTracking，
ms.openlocfilehash: b5fd3ee35e54c54f2f6b21dc1ce53625c68f65b4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144686"
---
# <a name="eye-tracking-examples"></a>目视跟踪示例

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

### <a name="eye-supported-navigation"></a>[**眼睛支持的导航**](../input/eye-tracking/eye-tracking-navigation.md)

假设你正在阅读有关远程显示器或电子阅读器的一些信息，当你到达所显示文本的末尾时，文本会自动向上滚动以显示更多内容。
或者，如何直接将缩放到你正在查看的什么位置？
以下是本教程中展示的一些有关眼支持导航的示例。
此外，还有一个示例，通过使 3D 全息影像基于当前焦点自动旋转，从而进行免手旋转。

**摘要：** 使用眼睛、语音和手部输入的组合进行滚动、平移、缩放、3D 旋转。

### <a name="eye-supported-positioning"></a>[**眼睛支持的位置**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

本教程演示了一种名为 [Put-That-There](https://youtu.be/CbIn8p4_4CQ) 的输入方案，该场景在 20 世纪 80 年代早期通过 MIT 媒体实验室返回研究，并输入了眼睛、手部和语音。
理念很简单：从眼睛中获益，快速选择和定位目标。
只需查看全息影像并说"_放置此_"，查看要放置它的位置，然后说 _"there！"。_
为了更精确地定位全息影像，可以使用手部、语音或控制器的其他输入。

**摘要：** 使用眼睛、语音和手部输入来定位全息 (*拖放) 。* 使用眼睛 + 手的眼支持滑块。

### <a name="visualization-of-visual-attention"></a>**视觉关注可视化效果**

基于用户外观的数据是一种功能非常强大的工具，用于评估设计的可用性，并确定高效工作流中的问题。
本教程讨论不同的眼动跟踪可视化效果及其如何适应不同的需求。
我们提供了日志记录和加载眼动跟踪数据的基本示例，以及如何可视化这些数据的示例。

**摘要：** 二维注意地图 (上) 热度地图。 录制&重放眼动跟踪数据。

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>设置 MRTK 眼动跟踪示例

### <a name="prerequisites"></a>先决条件

请注意，在设备上使用目视跟踪示例需要使用适用于包的 Appxmanifest.xml 上的 "注视输入" 功能生成的 HoloLens 2 和示例应用包。

若要在设备上使用这些目视跟踪示例，请在 Visual Studio 中生成应用之前确保遵循 [这些步骤](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) 。

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

若要在运行时加载附加场景，必须先将这些场景添加到 _生成设置-在 "生成" 菜单中 > 场景_ 。
根场景在列表中显示为第一个场景，这一点很重要：

![目视跟踪示例的 "生成设置" 场景菜单](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. 在 Unity 编辑器中播放眼睛跟踪示例

将眼睛跟踪场景添加到生成设置并加载 _EyeTrackingDemo-00-RootScene_ 后，最后一步需要检查：是否已启用附加到 _MixedRealityBasicSceneSetup_ GameObject 的 _"OnLoadStartScene"_ 脚本？ 这是为了让根场景知道要首先加载哪个演示场景。

![OnLoad_StartScene 脚本的示例](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

让我们开始吧！ 点击 _"播放"！_
应会看到多个 gem 出现，并且场景菜单位于顶部。

![ET 目标选择场景的示例屏幕截图](../images/eye-tracking/mrtk_et_targetselect.png)

还应注意到游戏视图中心有一个小的半透明圆圈。
这充当模拟 (光标) 的指示器：只需按下鼠标右键并移动鼠标即可更改其位置。 
当光标悬停在 gem 上时，你会注意到它将与当前查看的 gem 的中心对齐。
这是测试在"查看&quot;目标时是否根据预期 _触发事件的一_ 种好方法。
请注意 _，通过鼠标_ 控制进行模拟眼睛凝视是对快速和无意眼动的一种相当差的补充。
但是，它非常适用于测试基本功能，然后再通过将其部署到设备来HoloLens 2设计。
返回到眼动跟踪示例场景：只要查看 gem，就旋转，并且可以通过&quot;查看&quot;它和 ...来销毁它。

- 按 _Enter_ (模拟说&quot;select") 
- 在 _麦克风中说"_ 选择"
- 按 _空格_ 键显示模拟手部输入时，单击鼠标左键以执行模拟收缩

我们将在"眼睛支持的目标选择"教程中更详细地介绍如何实现 [**这些**](../input/eye-tracking/eye-tracking-target-selection.md) 交互。

将光标向上移动到场景中的顶部菜单栏时，你会注意到当前悬停的项将小突出显示。
可以使用上述提交方法之一选择当前突出显示的项，例如 (按 _Enter_) 。
这样，就可以在不同的眼动跟踪示例场景之间切换。

### <a name="4-how-to-test-specific-sub-scenes"></a>4.如何测试特定的子场景

处理特定方案时，你可能不希望每次都浏览场景菜单。
相反，在按下"播放"按钮时，你可能希望直接从当前正在工作的 _场景中_ 启动。
没问题！ 下面是你可以执行的操作：

1. 加载 _根_ 场景
2. 在 _根_ 场景中，禁用 _"OnLoadStartScene"_ 脚本
3. 将下面所述的眼睛跟踪测试场景之一 _拖放_ (或任何其他场景) 到 _层次结构_ 视图中，如下面的屏幕截图中所示。

    ![加法场景示例](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. 按下 _播放_

请注意，加载此子场景的方式不是永久性的：这意味着，如果你将应用部署到 HoloLens 2 设备，则它将仅加载根场景， (假设它出现在) 的生成设置的顶部。
此外，当你与他人共享你的项目时，不会自动加载子场景。

---

现在，你已了解如何让 MRTK 目视跟踪示例场景工作，接下来让我们进一步深入了解如何选择你的眼睛： [目视支持的目标选择](../input/eye-tracking/eye-tracking-target-selection.md)。

---
[返回 "MixedRealityToolkit" 中的眼睛跟踪](../input/eye-tracking/eye-tracking-Main.md)
