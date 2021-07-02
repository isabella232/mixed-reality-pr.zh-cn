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
# <a name="input-animation-recording"></a><span data-ttu-id="bf7be-104">输入动画录音</span><span class="sxs-lookup"><span data-stu-id="bf7be-104">Input animation recording</span></span>

<span data-ttu-id="bf7be-105">MRTK 具有一个记录系统，通过该系统可以将 head 移动和手跟踪数据存储在动画文件中。</span><span class="sxs-lookup"><span data-stu-id="bf7be-105">MRTK features an recording system by which head movement and hand tracking data can be stored in animation files.</span></span> <span data-ttu-id="bf7be-106">然后，可以使用 [输入模拟系统](input-simulation-service.md)播放记录的数据。</span><span class="sxs-lookup"><span data-stu-id="bf7be-106">The recorded data can then be played back using the [input simulation system](input-simulation-service.md).</span></span>

<span data-ttu-id="bf7be-107">在各种情况下，录制输入是一项有用的工具：</span><span class="sxs-lookup"><span data-stu-id="bf7be-107">Recording input is a useful tool in a variety of situations:</span></span>

* <span data-ttu-id="bf7be-108">为交互、操作、solvers 等创建自动测试。为这些测试创建控制器和指针的移动可能非常耗时。</span><span class="sxs-lookup"><span data-stu-id="bf7be-108">Creating automated tests for interaction, manipulations, solvers, etc. Creating the movement of controllers and hands for these tests can be time consuming.</span></span> <span data-ttu-id="bf7be-109">直接记录输入可加快处理速度并提供实际数据。</span><span class="sxs-lookup"><span data-stu-id="bf7be-109">Recording input directly can speed up the process and provide real-world data.</span></span>
* <span data-ttu-id="bf7be-110">通过动画教授 UX 元素的使用。</span><span class="sxs-lookup"><span data-stu-id="bf7be-110">Teaching the use of UX elements through animations.</span></span>
  <span data-ttu-id="bf7be-111">向用户显示如何与按钮和其他对象进行交互会使学习曲线平滑。</span><span class="sxs-lookup"><span data-stu-id="bf7be-111">Showing users how to interact with buttons and other objects can smooth the learning curve.</span></span>
* <span data-ttu-id="bf7be-112">调试在正常使用过程中可能遇到的意外行为。</span><span class="sxs-lookup"><span data-stu-id="bf7be-112">Debugging unexpected behavior that may be encountered during regular use.</span></span>
  <span data-ttu-id="bf7be-113">记录系统支持 "滚动缓冲" 概念，允许在后台记录最近的输入。</span><span class="sxs-lookup"><span data-stu-id="bf7be-113">The recording system supports a "rolling buffer" concept that allows recording recent input in the background.</span></span>
  <span data-ttu-id="bf7be-114">请参阅 [输入记录服务](#input-recording-service)。</span><span class="sxs-lookup"><span data-stu-id="bf7be-114">See [Input Recording Service](#input-recording-service).</span></span>

## <a name="recording-and-playback-services"></a><span data-ttu-id="bf7be-115">录制和播放服务</span><span class="sxs-lookup"><span data-stu-id="bf7be-115">Recording and playback services</span></span>

<span data-ttu-id="bf7be-116">提供两个输入系统服务分别用于记录和播放输入。</span><span class="sxs-lookup"><span data-stu-id="bf7be-116">Two input system services are provided to record and play back input respectively.</span></span>

### <a name="input-recording-service"></a><span data-ttu-id="bf7be-117">输入记录服务</span><span class="sxs-lookup"><span data-stu-id="bf7be-117">Input recording service</span></span>

<span data-ttu-id="bf7be-118">[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 从主相机转换和活动手型控制器获取数据，并将其存储在内部缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="bf7be-118">[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) takes data from the main camera transform and active hand controllers and stores it in an internal buffer.</span></span> <span data-ttu-id="bf7be-119">在请求时，会将此数据序列化为二进制文件以供存储并在以后重播。</span><span class="sxs-lookup"><span data-stu-id="bf7be-119">When requested this data is then serialized into binary files for storage and later replay.</span></span>

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="录制输入动画" width="80%" alt="Recording diagram" class="center" />
</a>

<span data-ttu-id="bf7be-121">若要开始记录输入，请调用 [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) 函数。</span><span class="sxs-lookup"><span data-stu-id="bf7be-121">To start recording input call the [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) function.</span></span> <span data-ttu-id="bf7be-122">[`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) 将暂停录制 (但不放弃目前记录的数据， [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) 如果需要) ，请使用执行此操作。</span><span class="sxs-lookup"><span data-stu-id="bf7be-122">[`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) will pause recording (but not discard the data recorded so far, use [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) to do this if needed).</span></span>

<span data-ttu-id="bf7be-123">默认情况下，录制缓冲区的大小限制为30秒。</span><span class="sxs-lookup"><span data-stu-id="bf7be-123">By default the size of the recording buffer is limited to 30 seconds.</span></span> <span data-ttu-id="bf7be-124">这允许记录服务在后台保持记录不会积累太多数据，然后在需要时保存最后30秒。</span><span class="sxs-lookup"><span data-stu-id="bf7be-124">This allows the recording service to keep recording in the background without accumulating too much data, and then save the last 30 seconds when required.</span></span> <span data-ttu-id="bf7be-125">可以使用属性更改时间间隔 [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) ，也可以使用选项来限制记录 [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) 。</span><span class="sxs-lookup"><span data-stu-id="bf7be-125">The time interval can be changed using the [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) property, or recording can be unlimited using the [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) option.</span></span>

<span data-ttu-id="bf7be-126">可以使用 [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) 函数将记录缓冲区中的数据保存到二进制文件中。</span><span class="sxs-lookup"><span data-stu-id="bf7be-126">The data in the recording buffer can be saved in a binary file using the [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) function.</span></span>

<span data-ttu-id="bf7be-127">有关二进制文件格式的详细信息，请参阅 [输入动画文件格式规范](input-animation-file-format.md)。</span><span class="sxs-lookup"><span data-stu-id="bf7be-127">For details on the binary file format see [Input Animation File Format Specification](input-animation-file-format.md).</span></span>

### <a name="input-playback-service"></a><span data-ttu-id="bf7be-128">输入播放服务</span><span class="sxs-lookup"><span data-stu-id="bf7be-128">Input playback service</span></span>

<span data-ttu-id="bf7be-129">[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) 读取包含输入动画数据的二进制文件，然后通过 [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) 应用此数据，重新创建记录的移动。</span><span class="sxs-lookup"><span data-stu-id="bf7be-129">[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) reads a binary file with input animation data and then applies this data through the [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) to recreate the recorded movements.</span></span>

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="播放输入动画" width="80%" alt="Play Back diagram" class="center" />
</a>

<span data-ttu-id="bf7be-131">若要开始播放输入动画，应该使用 [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) 函数从文件中加载它。</span><span class="sxs-lookup"><span data-stu-id="bf7be-131">To start playing back input animation it should be loaded from a file using the [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) function.</span></span>

<span data-ttu-id="bf7be-132">调用 " [播放](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)"、" [暂停](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)" 或 " [停止](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) " 以控制动画播放。</span><span class="sxs-lookup"><span data-stu-id="bf7be-132">Call [Play](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), [Pause](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), or [Stop](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) to control the animation playback.</span></span>

<span data-ttu-id="bf7be-133">当前动画时间还可以与 [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 属性直接控制。</span><span class="sxs-lookup"><span data-stu-id="bf7be-133">The current animation time can also be controlled directly with the [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) property.</span></span>

> [!WARNING]
> <span data-ttu-id="bf7be-134">操作场景时，循环或直接循环输入动画或设置 [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 可能会产生意外的结果！</span><span class="sxs-lookup"><span data-stu-id="bf7be-134">Looping or resetting input animation or setting [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) directly by scrubbing the timeline may yield unexpected results when manipulating the scene!</span></span> <span data-ttu-id="bf7be-135">仅记录输入变动，任何其他更改（例如移动对象或翻转交换机）都不会重置。</span><span class="sxs-lookup"><span data-stu-id="bf7be-135">Only the input movements are recorded, any additional changes such as moving objects or flipping switches will not be reset.</span></span> <span data-ttu-id="bf7be-136">如果进行了不可逆的更改，请确保重新加载场景。</span><span class="sxs-lookup"><span data-stu-id="bf7be-136">Make sure to reload the scene if irreversible changes have been made.</span></span>

### <a name="editor-tools-for-recording-and-playing-input-animation"></a><span data-ttu-id="bf7be-137">用于记录和播放输入动画的编辑器工具</span><span class="sxs-lookup"><span data-stu-id="bf7be-137">Editor tools for recording and playing input animation</span></span>

<span data-ttu-id="bf7be-138">Unity 编辑器中存在大量用于记录和检查输入动画的工具。</span><span class="sxs-lookup"><span data-stu-id="bf7be-138">A number of tools exist in the Unity editor for recording and examining input animation.</span></span> <span data-ttu-id="bf7be-139">可以在 "[输入模拟工具" 窗口](input-simulation-service.md#input-simulation-tools-window)中访问这些工具，该窗口可以从 _混合现实 Toolkit > 实用工具 > 输入模拟_ 菜单中打开。</span><span class="sxs-lookup"><span data-stu-id="bf7be-139">These tools can be accessed in the [input simulation tools window](input-simulation-service.md#input-simulation-tools-window), which can be opened from the _Mixed Reality Toolkit > Utilities > Input Simulation_ menu.</span></span>

> [!NOTE]
> <span data-ttu-id="bf7be-140">输入记录和播放仅在播放模式下工作。</span><span class="sxs-lookup"><span data-stu-id="bf7be-140">Input recording and playback only works during play mode.</span></span>

<span data-ttu-id="bf7be-141">输入记录窗口有两种模式：</span><span class="sxs-lookup"><span data-stu-id="bf7be-141">The input recording window has two modes:</span></span>

* <span data-ttu-id="bf7be-142">_记录_ 在播放模式下录制输入并将其保存到动画文件中。</span><span class="sxs-lookup"><span data-stu-id="bf7be-142">_Recording_ for recording input during play mode and saving it to animation files.</span></span>

  <span data-ttu-id="bf7be-143">当在 "录制" 按钮上切换时， [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 会启用来记录输入。</span><span class="sxs-lookup"><span data-stu-id="bf7be-143">When toggling on the recording button the [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) is enabled to record input.</span></span>
  <span data-ttu-id="bf7be-144">当关闭 "录制" 按钮时，将显示一个文件保存选择，并将录制的输入动画保存到所选目标。</span><span class="sxs-lookup"><span data-stu-id="bf7be-144">When toggling off the recording button a file save selection is shown and the recorded input animation is saved to the selected destination.</span></span>

  <span data-ttu-id="bf7be-145">还可以在此模式下更改缓冲区时间限制。</span><span class="sxs-lookup"><span data-stu-id="bf7be-145">The buffer time limit can also be changed in this mode.</span></span>

* <span data-ttu-id="bf7be-146">_播放_ 以便加载动画文件，然后通过输入模拟系统重新创建输入。</span><span class="sxs-lookup"><span data-stu-id="bf7be-146">_Playback_ for loading animation files and then recreating input through the input simulation system.</span></span>

  <span data-ttu-id="bf7be-147">必须先在此模式下加载动画。</span><span class="sxs-lookup"><span data-stu-id="bf7be-147">An animation must be loaded in this mode first.</span></span> <span data-ttu-id="bf7be-148">在记录模式下记录输入后，将自动加载生成的动画。</span><span class="sxs-lookup"><span data-stu-id="bf7be-148">After recording input in recording mode the resulting animation is automatically loaded.</span></span> <span data-ttu-id="bf7be-149">或者单击 "加载" 按钮以选择现有的动画文件。</span><span class="sxs-lookup"><span data-stu-id="bf7be-149">Alternatively click the "Load" button to select an existing animation file.</span></span>

  <span data-ttu-id="bf7be-150">从左到右的时间控制按钮如下：</span><span class="sxs-lookup"><span data-stu-id="bf7be-150">The time control buttons from left to right are:</span></span>

  * <span data-ttu-id="bf7be-151">将播放时间 _重置_ 为动画的开始时间。</span><span class="sxs-lookup"><span data-stu-id="bf7be-151">_Reset_ the playback time to the start of the animation.</span></span>
  * <span data-ttu-id="bf7be-152">随着时间的推移连续 _播放_ 动画。</span><span class="sxs-lookup"><span data-stu-id="bf7be-152">_Play_ animation continuously over time.</span></span>
  * <span data-ttu-id="bf7be-153">_单步执行_ 一次。</span><span class="sxs-lookup"><span data-stu-id="bf7be-153">_Step_ forward one time step.</span></span>

  <span data-ttu-id="bf7be-154">滑块还可用于擦除动画时间线。</span><span class="sxs-lookup"><span data-stu-id="bf7be-154">The slider can also be used to scrub through the animation timeline.</span></span>

> [!WARNING]
> <span data-ttu-id="bf7be-155">在操作场景时循环或重置输入动画或擦除时间线可能会产生意外的结果！</span><span class="sxs-lookup"><span data-stu-id="bf7be-155">Looping or resetting input animation or scrubbing the timeline may yield unexpected results when manipulating the scene!</span></span> <span data-ttu-id="bf7be-156">仅记录输入变动，任何其他更改（例如移动对象或翻转交换机）都不会重置。</span><span class="sxs-lookup"><span data-stu-id="bf7be-156">Only the input movements are recorded, any additional changes such as moving objects or flipping switches will not be reset.</span></span> <span data-ttu-id="bf7be-157">如果进行了不可逆的更改，请确保重新加载场景。</span><span class="sxs-lookup"><span data-stu-id="bf7be-157">Make sure to reload the scene if irreversible changes have been made.</span></span>
