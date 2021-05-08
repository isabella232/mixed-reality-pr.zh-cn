---
title: MRTK-Unity 开发人员文档
description: 了解适用于 Unity 的混合现实工具包。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK
ms.openlocfilehash: cb8b95cf9e563e8a277fa0d4b253639a763f5ad5
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489297"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>混合现实工具包指的是什么

![混合现实工具包](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

MRTK-Unity 是由 Microsoft 驱动的项目，它提供了一系列组件和功能来加速 Unity 中的跨平台 MR 应用开发。 以下是它的一些功能：

* 为空间交互和 UI 提供跨平台输入系统和构建基块。
* 通过编辑器内模拟实现快速原型制作，让你能够立即看到变化。
* 作为可扩展的框架运行，使开发人员能够交换出核心组件。
* 支持一系列广泛的平台：

| 平台 | 支持的设备 |
|---|---|
| OpenXR（Unity 2020.2 或更高版本） | Microsoft HoloLens 2 <br> Windows Mixed Reality 头戴显示设备 |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Windows Mixed Reality 头戴显示设备  |
| Oculus（Unity 2019.3 或更高版本） | Oculus Quest |
| OpenVR |  Windows Mixed Reality 头戴显示设备 <br> HTC Vive <br> Oculus Rift |
| Ultraleap 手部跟踪 | Ultraleap Leap 运动控制器 |
| 移动型 | iOS 和 Android |

## <a name="getting-started-with-mrtk"></a>MRTK 入门

如果你不熟悉 Unity 中的 MRTK 或混合现实开发，我们建议在设备或模拟器上安装并浏览 MRTK 示例中心示例应用程序。 

> [!div class="nextstepaction"]
> [下载 MRTK 示例中心应用](running-examples-hub.md)

在熟悉混合现实和 MRTK 的内容后，请安装所需的工具，并遵循初级级别 HoloLens 2 教程系列操作。

> [!div class="nextstepaction"]
> [安装工具](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [HoloLens 2 教程系列](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

想要查看后台正在执行的情况？
> [!div class="nextstepaction"]
> [在 GitHub 上了解 MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a>文档

| [![发行说明](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)<br/>[发行说明](release-notes/mrtk-26-release-notes.md)| [![MRTK 概述](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)<br/>[MRTK 概述](architecture/overview.md)|[![API 参考](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)<br/>[API 参考](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a>生成状态

| 分支 | CI 状态 | 文档状态 |
|---|---|---|
| `main` |[![CI 状态](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![文档状态](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="feature-areas"></a>功能区域

:::row:::
    :::column:::
       [![输入系统](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)<br>
        **[输入系统](features/input/overview.md)**<br>
    :::column-end:::
    :::column:::
        [![手部跟踪 (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)<br>
        **[手部跟踪 <br> (HoloLens 2)](features/input/hand-tracking.md)**<br>
    :::column-end:::
    :::column:::
        [![眼动跟踪 (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)<br>
        **[眼动跟踪 <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**<br>
    :::column-end:::
    :::column:::
        [![配置文件](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)<br>
        **[配置文件](configuration/mixed-reality-configuration-guide.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![手部跟踪 (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)<br>
        **[手部跟踪 <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**<br>
    :::column-end:::
    :::column:::
        [![UI 控件](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)<br>
        **[UI 控件](#ux-building-blocks)**<br>
    :::column-end:::
    :::column:::
        [![求解器](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)<br>
        **[求解器](features/ux-building-blocks/solvers/solver.md)**<br>
    :::column-end:::
    :::column:::
        [![多场景管理器](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[多场景<br/>管理器](features/scene-system/scene-system-getting-started.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![空间感知](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)<br>
        **[空间<br/>感知](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![诊断工具](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[诊断<br/>工具](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![MRTK 标准着色器视图](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)<br>
        **[MRTK 标准着色器示例视图](features/rendering/mrtk-standard-shader.md?q=shader)**<br>
    :::column-end:::
    :::column:::
        [![语音与听写](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[语音](features/input/speech.md)<br/> & [听写](features/input/dictation.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![边界系统](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)<br>
        **[边界<br/>系统](features/boundary/boundary-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![编辑器内模拟](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[编辑器内<br/>模拟](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![实验性功能](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)<br>
        **[实验性<br/>功能](contributing/experimental-features.md)**<br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a>UX 构建基块

:::row:::
    :::column:::
       [![按钮](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) [按钮](features/ux-building-blocks/button.md)<br>
        一种支持各种输入方法（包括 HoloLens 2 关节式手部）的按钮控件
    :::column-end:::
    :::column:::
        [![边界控制](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) [边界控制](features/ux-building-blocks/bounds-control.md)<br>
        用于模拟 3D 空间中的对象的标准 UI
    :::column-end:::
    :::column:::
        [![对象操控器](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) [对象操控器](features/ux-building-blocks/object-manipulator.md)<br>
        用于通过单手或双手操控对象的脚本
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![场记板](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) [场记板](features/ux-building-blocks/slate.md)<br>
        支持通过关节式手部输入进行滚动的 2D 样式平面
    :::column-end:::
    :::column:::
        [![系统键盘](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) [系统键盘](features/ux-building-blocks/system-keyboard.md)<br>
        用于在 Unity 中使用系统键盘的示例脚本
    :::column-end:::
    :::column:::
        [![可交互](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) [可交互](features/ux-building-blocks/interactable.md)<br>
        用于使对象可与可视状态和主题支持进行交互的脚本
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![求解器](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) [求解器](features/ux-building-blocks/solvers/solver.md)<br>
        各种对象定位行为，例如尾随、跟随人体、常量视图大小和表面磁性
    :::column-end:::
    :::column:::
        [![对象集合](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) [对象集合](features/ux-building-blocks/object-collection.md)<br>
        用于在三维形状中布设一组对象的脚本
    :::column-end:::
    :::column:::
        [![工具提示](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) [工具提示](features/ux-building-blocks/tooltip.md)<br>
        具有灵活定位点/透视系统的注释 UI，可用于标记运动控制器和对象
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![滑块](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) [滑块](features/ux-building-blocks/sliders.md)<br>
        用于调整支持直接手部跟踪交互的值的滑块 UI
    :::column-end:::
    :::column:::
        [![MRTK 标准着色器](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) [MRTK 标准着色器](features/rendering/mrtk-standard-shader.md)<br>
        MRTK 的标准着色器支持各种 Fluent 设计元素并提供高性能
    :::column-end:::
    :::column:::
        [![手动菜单](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) [手动菜单](features/ux-building-blocks/hand-menu.md)<br>
        使用手部约束求解器实现快速访问的手部锁定 UI
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![应用栏](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) [应用栏](features/ux-building-blocks/app-bar.md)<br>
        用于边界控制的手动激活的 UI
    :::column-end:::
    :::column:::
        [![指针](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[指针](features/input/pointers.md)**<br>
        了解各种类型的指针
    :::column-end:::
    :::column:::
        [![指尖可视化](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) [指尖可视化](features/ux-building-blocks/fingertip-visualization.md)<br>
        指尖上的视觉可供性，可提高直接交互的置信度
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![追踪菜单](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) [追踪菜单](features/ux-building-blocks/near-menu.md)<br>
        用于追踪交互的浮动菜单 UI
    :::column-end:::
    :::column:::
        [![空间感知入门](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) [空间感知视图](features/spatial-awareness/spatial-awareness-getting-started.md)<br>
        让全息对象与物理环境进行交互
    :::column-end:::
    :::column:::
        [![语音命令](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) [语音命令](features/input/speech.md)<br>
        用于集成语音输入的脚本和示例
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![进度指示器](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) [进度指示器](features/ux-building-blocks/progress-indicator.md)<br>
        用于传达数据进度或操作的可视指示器
    :::column-end:::
    :::column:::
        [![对话框](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) [对话框](features/ux-building-blocks/dialog.md)<br>
        用于请求用户确认或认可的 UI
    :::column-end:::
    :::column:::
        [![手部指导](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) [手部指导](features/ux-building-blocks/hand-coach.md)<br>
        在未告知手势时帮助引导用户的组件
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![手部物理服务](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) [手部物理服务 [实验性]](features/experimental/hand-physics-service.md)<br>
        通过手部物理服务，可实现刚体碰撞事件和与关节式手部的交互
    :::column-end:::
    :::column:::
        [![滚动集合](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) [滚动集合](features/ux-building-blocks/scrolling-object-collection.md)<br>
        本机滚动 3D 对象的一个对象集合
    :::column-end:::
    :::column:::
        [![停靠](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) [停靠 [实验性]](features/experimental/dock.md)<br>
        通过停靠功能，可将对象移入和移出预定位置
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![眼动跟踪：目标选择](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) [眼动跟踪：目标选择](features/input/eye-tracking/eye-tracking-target-selection.md)<br>
        将眼睛、语音和手部输入组合起来，以快速轻松地在场景中选择全息影像
    :::column-end:::
    :::column:::
        [![眼动跟踪：导航](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) [眼动跟踪：导航](features/input/eye-tracking/eye-tracking-navigation.md)<br>
        了解如何根据要查看的内容自动滚动文本或流畅地放大到聚焦内容
    :::column-end:::
    :::column:::
        [![眼动跟踪：热图](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) [眼动跟踪：热图](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)<br>
        记录、加载和直观显示用户已在你的应用中查找的内容的示例
    :::column-end:::
:::row-end:::

## <a name="tools"></a>工具

|  [![优化窗口](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [优化窗口](features/tools/optimize-window.md) | [![依赖关系窗口](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [依赖关系窗口](features/tools/dependency-window.md) | ![“生成”窗口](features/images/MRTK_Icon_BuildWindow.png) “生成”窗口 | [![输入记录](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [输入记录](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| 自动配置混合现实项目来优化性能 | 分析资产之间的依赖关系并确定未使用的资产 |  为混合现实应用程序配置和执行端到端生成进程 | 在编辑器中记录和播放头部移动和手部跟踪数据 |

## <a name="example-scenes"></a>示例场景

在 [此示例场景](features/example-scenes/hand-interaction-examples.md)中，了解 MRTK 各种类型的交互和 UI 控件。

[![示例场景 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>MRTK 示例中心

通过 MRTK 示例中心，可在 MRTK 中尝试各种示例场景。
可在 [MR 功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)中选择“混合现实工具包示例”包，为 HoloLens (x86)、HoloLens 2 (ARM) 和 Windows Mixed Reality 沉浸式头戴显示设备 (x64) 下载预生成的应用包。 请务必[使用 Windows 设备门户在 HoloLens（第一代）上安装应用](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)。 在 HoloLens 2 上，可通过 Microsoft Store 应用下载和安装 [MRTK 示例中心](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)。

请查看[示例中心 README 页面](features/example-scenes/example-hub.md)，详细了解如何使用 MRTK 的场景系统和场景过渡服务创建多场景中心。

[![示例场景中心](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>使用 MRTK 创建的示例应用

| [![元素周期表](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![星系探索者](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)| [![“表面”示例应用](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [元素周期表](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)是一款开源示例应用，它演示了如何使用 MRTK 的输入系统和构建基块打造适合 HoloLens 和沉浸式头戴显示设备的应用体验。 阅读迁移案例：[使用 MRTK v2 将“元素周期表”应用引入 HoloLens 2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[星系探索者](https://github.com/Microsoft/GalaxyExplorer)是一款开源示例应用，它最初是 2016 年 3 月作为 HoloLens 的“分享你的创意”活动的一部分开发出来的。 而借助 MRTK v2，“星系探索者”应用已经过更新，具有适合 HoloLens 2 的新功能。 阅读文章：[创建适合 HoloLens 2 的“星系探索者”应用](/windows/mixed-reality/galaxy-explorer-update) |[表面](https://github.com/microsoft/MRDL_Unity_Surfaces)是一款适合 HoloLens 2 的开源示例应用，它探讨了我们可如何使用视觉、音频和含义清晰的手部跟踪来创建触觉。 若要了解详细设计和开发案例，请查看混合现实开发日活动的研讨会：[从“表面”应用中学到的知识](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>来自 2020 年混合现实开发日活动的研讨会视频

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| 查看教程了解如何从头开始创建简单的 MRTK 应用。 了解交互概念和 MRTK 的多平台功能。 | 深入了解 MRTK 的 UX 构建基块，它们可帮助你构建精美的混合现实体验。 | 介绍 MRTK 内部和外部的性能工具以及概述 MRTK 标准着色器。 |

若要查看更多研讨会视频，请查看[混合现实开发日](/windows/mixed-reality/mr-dev-days-sessions)。

## <a name="engage-with-the-community"></a>与社区互动

* 在 [Slack](https://holodevelopers.slack.com/) 上加入有关 MRTK 的对话。 可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。

* 在 [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) 上就 MRTK 的使用提问并附上 MRTK 标记。

* 如果发现 MRTK 代码中有内容已损坏，请搜索[已知问题](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)或提出[新问题](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)。

* 若要就如何向 MRTK 贡献内容提问，请转到 Stack 上的 [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) 频道。

此项目采用了 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。
有关详细信息，请参阅[行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)，如有任何其他问题或评论，请联系 [opencode@microsoft.com](mailto:opencode@microsoft.com)。

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>混合现实开发人员中心的有用资源

| ![发现](features/images/mrdevcenter/icon-discover.png) [发现](/windows/mixed-reality/)| ![设计](features/images/mrdevcenter/icon-design.png) [设计](/windows/mixed-reality/design)| ![开发](features/images/mrdevcenter/icon-develop.png) [开发](/windows/mixed-reality/development)| ![分发)](features/images/mrdevcenter/icon-distribute.png) [分发](/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| 了解如何打造适合 HoloLens 和沉浸式头戴显示设备 (VR) 的混合现实体验。          | 获取设计指南。 构建用户界面。 了解交互和输入。     | 获取开发指南。 了解相关技术。 了解相关科学。       | 让应用做好供他人使用的准备，并考虑创建 3D 启动器。 |

## <a name="useful-resources-on-azure"></a>Azure 上的有用资源

| ![空间定位点](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [空间定位点](/azure/spatial-anchors/)| ![语音服务](features/images/mrdevcenter/icon-azurespeechservices.png) [语音服务](/azure/cognitive-services/speech-service/)| ![视觉服务](features/images/mrdevcenter/icon-azurevisionservices.png) [视觉服务](/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| 空间定位点是一项跨平台的服务；借助它，你可使用一段时间内在各设备中位置不变的对象来创建混合现实体验。| 发现 Azure 支持的语音功能（例如语音转文本、说话人识别或语音翻译）并将其集成到应用程序中。| 使用视觉服务（例如计算机视觉、人脸检测、情感识别或视频索引器）标识和分析图像或视频内容。 |

## <a name="how-to-contribute"></a>如何参与

可[参与](contributing/contributing.md)页面了解可如何向 MRTK 贡献内容。

## <a name="getting-help"></a>获取帮助

如果遇到 MRTK 导致的问题，或者对如何执行某些操作存在疑问，下面几项资源可提供帮助：

* 若要报告 bug，请在 GitHub 存储库上[提问](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose)。
* 如有一文，请在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 上进行联系，或在 Slack 上的 [mixed-reality-toolkit 频道](https://holodevelopers.slack.com/messages/C2H4HT858)中联系。 可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。