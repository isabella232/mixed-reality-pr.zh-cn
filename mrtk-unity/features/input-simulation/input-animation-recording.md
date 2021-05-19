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
# <a name="input-animation-recording"></a><span data-ttu-id="14b5a-104">输入动画录制</span><span class="sxs-lookup"><span data-stu-id="14b5a-104">Input animation recording</span></span>

<span data-ttu-id="14b5a-105">MRTK 具有记录系统，可通过该系统将头部移动和手部跟踪数据存储在动画文件中。</span><span class="sxs-lookup"><span data-stu-id="14b5a-105">MRTK features an recording system by which head movement and hand tracking data can be stored in animation files.</span></span> <span data-ttu-id="14b5a-106">然后，可以使用输入模拟系统 播放 [录制的数据](input-simulation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="14b5a-106">The recorded data can then be played back using the [input simulation system](input-simulation-service.md).</span></span>

<span data-ttu-id="14b5a-107">记录输入是多种情况下的有用工具：</span><span class="sxs-lookup"><span data-stu-id="14b5a-107">Recording input is a useful tool in a variety of situations:</span></span>

* <span data-ttu-id="14b5a-108">为交互、操作、求解器等创建自动测试。为这些测试创建控制器和手部移动可能很耗时。</span><span class="sxs-lookup"><span data-stu-id="14b5a-108">Creating automated tests for interaction, manipulations, solvers, etc. Creating the movement of controllers and hands for these tests can be time consuming.</span></span> <span data-ttu-id="14b5a-109">直接记录输入可以加快处理速度并提供实际数据。</span><span class="sxs-lookup"><span data-stu-id="14b5a-109">Recording input directly can speed up the process and provide real-world data.</span></span>
* <span data-ttu-id="14b5a-110">通过动画教授 UX 元素的使用。</span><span class="sxs-lookup"><span data-stu-id="14b5a-110">Teaching the use of UX elements through animations.</span></span>
  <span data-ttu-id="14b5a-111">向用户展示如何与按钮和其他对象交互可以平滑学习曲线。</span><span class="sxs-lookup"><span data-stu-id="14b5a-111">Showing users how to interact with buttons and other objects can smooth the learning curve.</span></span>
* <span data-ttu-id="14b5a-112">调试在常规使用过程中可能会遇到的意外行为。</span><span class="sxs-lookup"><span data-stu-id="14b5a-112">Debugging unexpected behavior that may be encountered during regular use.</span></span>
  <span data-ttu-id="14b5a-113">录制系统支持"滚动缓冲区"概念，该概念允许在后台记录最近的输入。</span><span class="sxs-lookup"><span data-stu-id="14b5a-113">The recording system supports a "rolling buffer" concept that allows recording recent input in the background.</span></span>
  <span data-ttu-id="14b5a-114">请参阅 [输入记录服务](#input-recording-service)。</span><span class="sxs-lookup"><span data-stu-id="14b5a-114">See [Input Recording Service](#input-recording-service).</span></span>

## <a name="recording-and-playback-services"></a><span data-ttu-id="14b5a-115">录制和播放服务</span><span class="sxs-lookup"><span data-stu-id="14b5a-115">Recording and playback services</span></span>

<span data-ttu-id="14b5a-116">提供了两个输入系统服务来分别记录和播放输入。</span><span class="sxs-lookup"><span data-stu-id="14b5a-116">Two input system services are provided to record and play back input respectively.</span></span>

### <a name="input-recording-service"></a><span data-ttu-id="14b5a-117">输入记录服务</span><span class="sxs-lookup"><span data-stu-id="14b5a-117">Input recording service</span></span>

<span data-ttu-id="14b5a-118">[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 从主相机转换和主动手部控制器接收数据，并存储在内部缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="14b5a-118">[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) takes data from the main camera transform and active hand controllers and stores it in an internal buffer.</span></span> <span data-ttu-id="14b5a-119">在请求时，此数据随后序列化为二进制文件，供存储和稍后重播。</span><span class="sxs-lookup"><span data-stu-id="14b5a-119">When requested this data is then serialized into binary files for storage and later replay.</span></span>

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="录制输入动画" width="80%" alt="Recording diagram" class="center" />
</a>

<span data-ttu-id="14b5a-121">若要开始记录输入，请调用 [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) 函数。</span><span class="sxs-lookup"><span data-stu-id="14b5a-121">To start recording input call the [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) function.</span></span> <span data-ttu-id="14b5a-122">[`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) 将暂停 (，但不放弃到目前为止记录的数据，如果需要，请使用 [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput)) 。</span><span class="sxs-lookup"><span data-stu-id="14b5a-122">[`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) will pause recording (but not discard the data recorded so far, use [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) to do this if needed).</span></span>

<span data-ttu-id="14b5a-123">默认情况下，录制缓冲区的大小限制为30秒。</span><span class="sxs-lookup"><span data-stu-id="14b5a-123">By default the size of the recording buffer is limited to 30 seconds.</span></span> <span data-ttu-id="14b5a-124">这允许记录服务在后台保持记录不会积累太多数据，然后在需要时保存最后30秒。</span><span class="sxs-lookup"><span data-stu-id="14b5a-124">This allows the recording service to keep recording in the background without accumulating too much data, and then save the last 30 seconds when required.</span></span> <span data-ttu-id="14b5a-125">可以使用属性更改时间间隔 [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) ，也可以使用选项来限制记录 [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) 。</span><span class="sxs-lookup"><span data-stu-id="14b5a-125">The time interval can be changed using the [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) property, or recording can be unlimited using the [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) option.</span></span>

<span data-ttu-id="14b5a-126">可以使用 [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) 函数将记录缓冲区中的数据保存到二进制文件中。</span><span class="sxs-lookup"><span data-stu-id="14b5a-126">The data in the recording buffer can be saved in a binary file using the [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) function.</span></span>

<span data-ttu-id="14b5a-127">有关二进制文件格式的详细信息，请参阅 [输入动画文件格式规范](input-animation-file-format.md)。</span><span class="sxs-lookup"><span data-stu-id="14b5a-127">For details on the binary file format see [Input Animation File Format Specification](input-animation-file-format.md).</span></span>

### <a name="input-playback-service"></a><span data-ttu-id="14b5a-128">输入播放服务</span><span class="sxs-lookup"><span data-stu-id="14b5a-128">Input playback service</span></span>

<span data-ttu-id="14b5a-129">[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) 读取包含输入动画数据的二进制文件，然后通过 [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) 应用此数据，重新创建记录的移动。</span><span class="sxs-lookup"><span data-stu-id="14b5a-129">[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) reads a binary file with input animation data and then applies this data through the [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) to recreate the recorded movements.</span></span>

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="播放输入动画" width="80%" alt="Play Back diagram" class="center" />
</a>

<span data-ttu-id="14b5a-131">若要开始播放输入动画，应该使用 [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) 函数从文件中加载它。</span><span class="sxs-lookup"><span data-stu-id="14b5a-131">To start playing back input animation it should be loaded from a file using the [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) function.</span></span>

<span data-ttu-id="14b5a-132">调用 " [播放](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)"、" [暂停](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)" 或 " [停止](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) " 以控制动画播放。</span><span class="sxs-lookup"><span data-stu-id="14b5a-132">Call [Play](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), [Pause](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), or [Stop](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) to control the animation playback.</span></span>

<span data-ttu-id="14b5a-133">当前动画时间还可以与 [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 属性直接控制。</span><span class="sxs-lookup"><span data-stu-id="14b5a-133">The current animation time can also be controlled directly with the [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) property.</span></span>

> [!WARNING]
> <span data-ttu-id="14b5a-134">操作场景时，循环或直接循环输入动画或设置 [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 可能会产生意外的结果！</span><span class="sxs-lookup"><span data-stu-id="14b5a-134">Looping or resetting input animation or setting [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) directly by scrubbing the timeline may yield unexpected results when manipulating the scene!</span></span> <span data-ttu-id="14b5a-135">仅记录输入变动，任何其他更改（例如移动对象或翻转交换机）都不会重置。</span><span class="sxs-lookup"><span data-stu-id="14b5a-135">Only the input movements are recorded, any additional changes such as moving objects or flipping switches will not be reset.</span></span> <span data-ttu-id="14b5a-136">如果进行了不可逆的更改，请确保重新加载场景。</span><span class="sxs-lookup"><span data-stu-id="14b5a-136">Make sure to reload the scene if irreversible changes have been made.</span></span>

### <a name="editor-tools-for-recording-and-playing-input-animation"></a><span data-ttu-id="14b5a-137">用于记录和播放输入动画的编辑器工具</span><span class="sxs-lookup"><span data-stu-id="14b5a-137">Editor tools for recording and playing input animation</span></span>

<span data-ttu-id="14b5a-138">Unity 编辑器中存在大量用于记录和检查输入动画的工具。</span><span class="sxs-lookup"><span data-stu-id="14b5a-138">A number of tools exist in the Unity editor for recording and examining input animation.</span></span> <span data-ttu-id="14b5a-139">可以在 " [输入模拟工具" 窗口](input-simulation-service.md#input-simulation-tools-window)中访问这些工具，该窗口可以从 _混合现实工具包打开 > 实用程序 > 输入模拟_ 菜单。</span><span class="sxs-lookup"><span data-stu-id="14b5a-139">These tools can be accessed in the [input simulation tools window](input-simulation-service.md#input-simulation-tools-window), which can be opened from the _Mixed Reality Toolkit > Utilities > Input Simulation_ menu.</span></span>

> [!NOTE]
> <span data-ttu-id="14b5a-140">输入记录和播放仅在播放模式下工作。</span><span class="sxs-lookup"><span data-stu-id="14b5a-140">Input recording and playback only works during play mode.</span></span>

<span data-ttu-id="14b5a-141">输入记录窗口有两种模式：</span><span class="sxs-lookup"><span data-stu-id="14b5a-141">The input recording window has two modes:</span></span>

* <span data-ttu-id="14b5a-142">_记录_ 在播放模式下录制输入并将其保存到动画文件中。</span><span class="sxs-lookup"><span data-stu-id="14b5a-142">_Recording_ for recording input during play mode and saving it to animation files.</span></span>

  <span data-ttu-id="14b5a-143">切换录制按钮时，启用 [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 以记录输入。</span><span class="sxs-lookup"><span data-stu-id="14b5a-143">When toggling on the recording button the [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) is enabled to record input.</span></span>
  <span data-ttu-id="14b5a-144">切换录制按钮时，将显示文件保存选择，并且录制的输入动画将保存到所选目标。</span><span class="sxs-lookup"><span data-stu-id="14b5a-144">When toggling off the recording button a file save selection is shown and the recorded input animation is saved to the selected destination.</span></span>

  <span data-ttu-id="14b5a-145">在此模式下，还可以更改缓冲区时间限制。</span><span class="sxs-lookup"><span data-stu-id="14b5a-145">The buffer time limit can also be changed in this mode.</span></span>

* <span data-ttu-id="14b5a-146">_播放_ 以加载动画文件，然后通过输入模拟系统重新创建输入。</span><span class="sxs-lookup"><span data-stu-id="14b5a-146">_Playback_ for loading animation files and then recreating input through the input simulation system.</span></span>

  <span data-ttu-id="14b5a-147">必须先在此模式下加载动画。</span><span class="sxs-lookup"><span data-stu-id="14b5a-147">An animation must be loaded in this mode first.</span></span> <span data-ttu-id="14b5a-148">在录制模式下记录输入后，将自动加载生成的动画。</span><span class="sxs-lookup"><span data-stu-id="14b5a-148">After recording input in recording mode the resulting animation is automatically loaded.</span></span> <span data-ttu-id="14b5a-149">或者，单击"加载"按钮以选择现有的动画文件。</span><span class="sxs-lookup"><span data-stu-id="14b5a-149">Alternatively click the "Load" button to select an existing animation file.</span></span>

  <span data-ttu-id="14b5a-150">从左到右的时间控制按钮为：</span><span class="sxs-lookup"><span data-stu-id="14b5a-150">The time control buttons from left to right are:</span></span>

  * <span data-ttu-id="14b5a-151">_将_ 播放时间重置为动画的开始。</span><span class="sxs-lookup"><span data-stu-id="14b5a-151">_Reset_ the playback time to the start of the animation.</span></span>
  * <span data-ttu-id="14b5a-152">_在_ 一段时间持续播放动画。</span><span class="sxs-lookup"><span data-stu-id="14b5a-152">_Play_ animation continuously over time.</span></span>
  * <span data-ttu-id="14b5a-153">_向前_ 单步执行一次步骤。</span><span class="sxs-lookup"><span data-stu-id="14b5a-153">_Step_ forward one time step.</span></span>

  <span data-ttu-id="14b5a-154">滑块还可用于清理动画时间线。</span><span class="sxs-lookup"><span data-stu-id="14b5a-154">The slider can also be used to scrub through the animation timeline.</span></span>

> [!WARNING]
> <span data-ttu-id="14b5a-155">操作场景时，循环或重置输入动画或清理时间线可能会导致意外结果！</span><span class="sxs-lookup"><span data-stu-id="14b5a-155">Looping or resetting input animation or scrubbing the timeline may yield unexpected results when manipulating the scene!</span></span> <span data-ttu-id="14b5a-156">仅记录输入移动，不会重置任何其他更改，例如移动对象或翻转开关。</span><span class="sxs-lookup"><span data-stu-id="14b5a-156">Only the input movements are recorded, any additional changes such as moving objects or flipping switches will not be reset.</span></span> <span data-ttu-id="14b5a-157">如果进行了不可逆的更改，请确保重新加载场景。</span><span class="sxs-lookup"><span data-stu-id="14b5a-157">Make sure to reload the scene if irreversible changes have been made.</span></span>
