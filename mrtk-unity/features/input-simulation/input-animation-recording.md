---
title: 输入动画录制
description: 有关 MRTK 中的输入动画录制系统的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 81e49178a9f218e5d3be796ec6253ccabe5d44fc
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143912"
---
# <a name="input-animation-recording"></a>输入动画录制

MRTK 具有记录系统，可通过该系统将头部移动和手部跟踪数据存储在动画文件中。 然后，可以使用输入模拟系统 播放 [录制的数据](input-simulation-service.md)。

记录输入是多种情况下的有用工具：

* 为交互、操作、求解器等创建自动测试。为这些测试创建控制器和手部移动可能很耗时。 直接记录输入可以加快处理速度并提供实际数据。
* 通过动画教授 UX 元素的使用。
  向用户展示如何与按钮和其他对象交互可以平滑学习曲线。
* 调试在常规使用过程中可能会遇到的意外行为。
  录制系统支持"滚动缓冲区"概念，该概念允许在后台记录最近的输入。
  请参阅 [输入记录服务](#input-recording-service)。

## <a name="recording-and-playback-services"></a>录制和播放服务

提供了两个输入系统服务来分别记录和播放输入。

### <a name="input-recording-service"></a>输入记录服务

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 从主相机转换和主动手部控制器接收数据，并存储在内部缓冲区中。 在请求时，此数据随后序列化为二进制文件，供存储和稍后重播。

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="录制输入动画" width="80%" alt="Recording diagram" class="center" />
</a>

若要开始记录输入，请调用 [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) 函数。 [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) 将暂停 (，但不放弃到目前为止记录的数据，如果需要，请使用 [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput)) 。

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

Unity 编辑器中存在大量用于记录和检查输入动画的工具。 可以在 " [输入模拟工具" 窗口](input-simulation-service.md#input-simulation-tools-window)中访问这些工具，该窗口可以从 _混合现实工具包打开 > 实用程序 > 输入模拟_ 菜单。

> [!NOTE]
> 输入记录和播放仅在播放模式下工作。

输入记录窗口有两种模式：

* _记录_ 在播放模式下录制输入并将其保存到动画文件中。

  切换录制按钮时，启用 [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 以记录输入。
  切换录制按钮时，将显示文件保存选择，并且录制的输入动画将保存到所选目标。

  在此模式下，还可以更改缓冲区时间限制。

* _播放_ 以加载动画文件，然后通过输入模拟系统重新创建输入。

  必须先在此模式下加载动画。 在录制模式下记录输入后，将自动加载生成的动画。 或者，单击"加载"按钮以选择现有的动画文件。

  从左到右的时间控制按钮为：

  * _将_ 播放时间重置为动画的开始。
  * _在_ 一段时间持续播放动画。
  * _向前_ 单步执行一次步骤。

  滑块还可用于清理动画时间线。

> [!WARNING]
> 操作场景时，循环或重置输入动画或清理时间线可能会导致意外结果！ 仅记录输入移动，不会重置任何其他更改，例如移动对象或翻转开关。 如果进行了不可逆的更改，请确保重新加载场景。
