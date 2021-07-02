---
title: 输入动画录音
description: 有关 MRTK 中的输入动画录音系统的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 6bdb764c5905352b9aec7c1512a73e727b60573a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176943"
---
# <a name="input-animation-recording"></a>输入动画录音

MRTK 具有一个记录系统，通过该系统可以将 head 移动和手跟踪数据存储在动画文件中。 然后，可以使用 [输入模拟系统](input-simulation-service.md)播放记录的数据。

在各种情况下，录制输入是一项有用的工具：

* 为交互、操作、solvers 等创建自动测试。为这些测试创建控制器和指针的移动可能非常耗时。 直接记录输入可加快处理速度并提供实际数据。
* 通过动画教授 UX 元素的使用。
  向用户显示如何与按钮和其他对象进行交互会使学习曲线平滑。
* 调试在正常使用过程中可能遇到的意外行为。
  记录系统支持 "滚动缓冲" 概念，允许在后台记录最近的输入。
  请参阅 [输入记录服务](#input-recording-service)。

## <a name="recording-and-playback-services"></a>录制和播放服务

提供两个输入系统服务分别用于记录和播放输入。

### <a name="input-recording-service"></a>输入记录服务

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 从主相机转换和活动手型控制器获取数据，并将其存储在内部缓冲区中。 在请求时，会将此数据序列化为二进制文件以供存储并在以后重播。

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="录制输入动画" width="80%" alt="Recording diagram" class="center" />
</a>

若要开始记录输入，请调用 [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) 函数。 [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) 将暂停录制 (但不放弃目前记录的数据， [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) 如果需要) ，请使用执行此操作。

默认情况下，录制缓冲区的大小限制为30秒。 这允许记录服务在后台保持记录不会积累太多数据，然后在需要时保存最后30秒。 可以使用属性更改时间间隔 [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) ，也可以使用选项来限制记录 [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) 。

可以使用 [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) 函数将记录缓冲区中的数据保存到二进制文件中。

有关二进制文件格式的详细信息，请参阅 [输入动画文件格式规范](input-animation-file-format.md)。

### <a name="input-playback-service"></a>输入播放服务

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) 读取包含输入动画数据的二进制文件，然后通过 [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) 应用此数据，重新创建记录的移动。

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="播放输入动画" width="80%" alt="Play Back diagram" class="center" />
</a>

若要开始播放输入动画，应该使用 [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) 函数从文件中加载它。

调用 " [播放](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)"、" [暂停](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)" 或 " [停止](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) " 以控制动画播放。

当前动画时间还可以与 [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 属性直接控制。

> [!WARNING]
> 操作场景时，循环或直接循环输入动画或设置 [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 可能会产生意外的结果！ 仅记录输入变动，任何其他更改（例如移动对象或翻转交换机）都不会重置。 如果进行了不可逆的更改，请确保重新加载场景。

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>用于记录和播放输入动画的编辑器工具

Unity 编辑器中存在大量用于记录和检查输入动画的工具。 可以在 "[输入模拟工具" 窗口](input-simulation-service.md#input-simulation-tools-window)中访问这些工具，该窗口可以从 _混合现实 Toolkit > 实用工具 > 输入模拟_ 菜单中打开。

> [!NOTE]
> 输入记录和播放仅在播放模式下工作。

输入记录窗口有两种模式：

* _记录_ 在播放模式下录制输入并将其保存到动画文件中。

  当在 "录制" 按钮上切换时， [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 会启用来记录输入。
  当关闭 "录制" 按钮时，将显示一个文件保存选择，并将录制的输入动画保存到所选目标。

  还可以在此模式下更改缓冲区时间限制。

* _播放_ 以便加载动画文件，然后通过输入模拟系统重新创建输入。

  必须先在此模式下加载动画。 在记录模式下记录输入后，将自动加载生成的动画。 或者单击 "加载" 按钮以选择现有的动画文件。

  从左到右的时间控制按钮如下：

  * 将播放时间 _重置_ 为动画的开始时间。
  * 随着时间的推移连续 _播放_ 动画。
  * _单步执行_ 一次。

  滑块还可用于擦除动画时间线。

> [!WARNING]
> 在操作场景时循环或重置输入动画或擦除时间线可能会产生意外的结果！ 仅记录输入变动，任何其他更改（例如移动对象或翻转交换机）都不会重置。 如果进行了不可逆的更改，请确保重新加载场景。
