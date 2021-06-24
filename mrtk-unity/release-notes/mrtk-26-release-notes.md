---
title: MRTK 2.6 发行说明
description: MRTK 版本 2.6 的发行说明
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity， HoloLens， HoloLens 2， 混合现实， 开发， MRTK，
ms.openlocfilehash: c172e5d071bba22626e9c35b2b4318f1ff779335
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562507"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a><span data-ttu-id="df35e-104">Microsoft Mixed Reality Toolkit 2.6 发行说明</span><span class="sxs-lookup"><span data-stu-id="df35e-104">Microsoft Mixed Reality Toolkit 2.6 Release Notes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df35e-105">存在一个已知的编译器问题，该问题会影响使用 ARM64 为 Microsoft HoloLens 2 构建的应用程序。</span><span class="sxs-lookup"><span data-stu-id="df35e-105">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="df35e-106">此问题通过更新 2019 Visual Studio版本 16.8 或更高版本来修复。</span><span class="sxs-lookup"><span data-stu-id="df35e-106">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="df35e-107">如果无法更新Visual Studio，请 `com.microsoft.mixedreality.toolkit.tools` 导入包以应用解决方法。</span><span class="sxs-lookup"><span data-stu-id="df35e-107">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new-in-262"></a><span data-ttu-id="df35e-108">2.6.2 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="df35e-108">What's new in 2.6.2</span></span>

### <a name="corrects-parenting-of-the-spatial-mesh"></a><span data-ttu-id="df35e-109">更正空间网格的父级设置</span><span class="sxs-lookup"><span data-stu-id="df35e-109">Corrects parenting of the spatial mesh</span></span>

<span data-ttu-id="df35e-110">修复了 [在](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) 移动混合现实 Playspace 对象后空间网格未正确定位的问题 (例如：通过远程端口) 。</span><span class="sxs-lookup"><span data-stu-id="df35e-110">Fixes the [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) where spatial meshes were not being properly located after the Mixed Reality Playspace object was moved (ex: via a teleport).</span></span>

## <a name="whats-new-in-261"></a><span data-ttu-id="df35e-111">2.6.1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="df35e-111">What's new in 2.6.1</span></span>

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a><span data-ttu-id="df35e-112">修复了 OpenXR 未在 HoloLens 2/UWP 上运行的问题</span><span class="sxs-lookup"><span data-stu-id="df35e-112">Fixes OpenXR not running on HoloLens 2 / UWP</span></span>

<span data-ttu-id="df35e-113">修复了阻止 MRTK 的 OpenXR 支持在 UWP 上运行的回归。</span><span class="sxs-lookup"><span data-stu-id="df35e-113">Fixes a regression that prevented MRTK's OpenXR support from running on UWP.</span></span>

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a><span data-ttu-id="df35e-114">修复了 Leap Motion ObjectManipulator 不旋转的问题</span><span class="sxs-lookup"><span data-stu-id="df35e-114">Fixes Leap Motion ObjectManipulator not rotating</span></span>

<span data-ttu-id="df35e-115">修复了 ObjectManipulator 脚本未考虑闰运动手旋转的回归。</span><span class="sxs-lookup"><span data-stu-id="df35e-115">Fixes a regression where a Leap Motion hand's rotation was not taken into account by the ObjectManipulator script.</span></span>

### <a name="sample-scene-updates"></a><span data-ttu-id="df35e-116">示例场景更新</span><span class="sxs-lookup"><span data-stu-id="df35e-116">Sample scene updates</span></span>

<span data-ttu-id="df35e-117">更新场景理解示例场景，以正确反映 Unity 插件的已发货状态。</span><span class="sxs-lookup"><span data-stu-id="df35e-117">Updates the scene understanding sample scene to correctly reflect the shipped state of the Unity plugin.</span></span> <span data-ttu-id="df35e-118">此外，将示例更新为不再依赖于正在导入的空间感知示例场景。</span><span class="sxs-lookup"><span data-stu-id="df35e-118">Also updates the sample to no longer have a dependency on the spatial awareness sample scene being imported.</span></span> <span data-ttu-id="df35e-119">在更新到 2.6.1 之前，应删除导入的场景理解和空间感知示例（如果它们存在于项目中）以避免可能出现的冲突。</span><span class="sxs-lookup"><span data-stu-id="df35e-119">Before updating to 2.6.1 you should delete the imported scene understanding and spatial awareness samples if they are present in your project to avoid possible conflicts.</span></span> <span data-ttu-id="df35e-120">如果未删除这些示例，并且确实在控制台中看到了与这些示例相关的冲突，请删除示例 (或文件夹) ，然后 `Assets/Samples/Mixed Reality Toolkit Examples` 重试导入。</span><span class="sxs-lookup"><span data-stu-id="df35e-120">If you did not remove those samples and do see conflicts related to those in the console, please remove both samples (or the `Assets/Samples/Mixed Reality Toolkit Examples` folder) and then try importing again.</span></span>

<span data-ttu-id="df35e-121">更新对话示例场景以正确描述当前对话方案。</span><span class="sxs-lookup"><span data-stu-id="df35e-121">Updates the dialog example scene to correctly describe the current dialog scenarios.</span></span>

## <a name="whats-new-in-260"></a><span data-ttu-id="df35e-122">2.6.0 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="df35e-122">What's new in 2.6.0</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a><span data-ttu-id="df35e-123">添加对 OpenXR 的支持</span><span class="sxs-lookup"><span data-stu-id="df35e-123">Add support for OpenXR</span></span>

<span data-ttu-id="df35e-124">添加了对 Unity 的 OpenXR 预览包和 Microsoft 的混合现实 OpenXR 包的初始支持。</span><span class="sxs-lookup"><span data-stu-id="df35e-124">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="df35e-125">有关详细信息 [，请参阅 MRTK/XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)入门页 [、Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)论坛文章或 [Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) 文档。</span><span class="sxs-lookup"><span data-stu-id="df35e-125">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](/windows/mixed-reality/develop/unity/openxr-getting-started) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df35e-126">Unity 中的 OpenXR 仅在 Unity 2020.2 及更高版本上受支持。</span><span class="sxs-lookup"><span data-stu-id="df35e-126">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="df35e-127">目前，它还仅支持 x64 和 ARM64 生成。</span><span class="sxs-lookup"><span data-stu-id="df35e-127">Currently, it also only supports x64 and ARM64 builds.</span></span>

### <a name="asset-swap-utility"></a><span data-ttu-id="df35e-128">资产交换实用工具</span><span class="sxs-lookup"><span data-stu-id="df35e-128">Asset swap utility</span></span>

<span data-ttu-id="df35e-129">使用新的资产交换实用工具 交换 Unity 场景中 [的多个资产](../features/tools/asset-swap-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="df35e-129">Swap multiple assets in a Unity scene with the new [Asset Swap utility](../features/tools/asset-swap-utility.md).</span></span>

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a><span data-ttu-id="df35e-130">MRTK 现在支持 HP 运动控制器</span><span class="sxs-lookup"><span data-stu-id="df35e-130">HP Motion Controllers now supported with MRTK</span></span>

<span data-ttu-id="df35e-131">HP Reverb G2 的控制器现在本机与 MRTK 一起工作。</span><span class="sxs-lookup"><span data-stu-id="df35e-131">Controllers for the HP Reverb G2 now work natively with MRTK.</span></span>

### <a name="experimental-interactive-element--state-visualizer"></a><span data-ttu-id="df35e-132">实验交互式元素 + 状态可视化工具</span><span class="sxs-lookup"><span data-stu-id="df35e-132">Experimental Interactive Element + State Visualizer</span></span>

<span data-ttu-id="df35e-133">Interactive 元素是 MRTK 输入系统的简化集中入口点。</span><span class="sxs-lookup"><span data-stu-id="df35e-133">Interactive Element is a simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="df35e-134">它包含状态管理方法、事件管理和核心交互状态的状态设置逻辑。</span><span class="sxs-lookup"><span data-stu-id="df35e-134">It contains state management methods, event management and the state setting logic for Core Interaction States.</span></span> <span data-ttu-id="df35e-135">有关详细信息，请参阅 [Interactive 元素文档](../features/experimental/interactive-element.md)。</span><span class="sxs-lookup"><span data-stu-id="df35e-135">For more information see [Interactive Element Documentation](../features/experimental/interactive-element.md).</span></span>

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

<span data-ttu-id="df35e-137">状态可视化工具是依赖于 Interactive 元素的动画组件。</span><span class="sxs-lookup"><span data-stu-id="df35e-137">The State Visualizer is an animation component that depends on Interactive Element.</span></span> <span data-ttu-id="df35e-138">此组件创建动画剪辑、设置关键帧并生成动画器状态机。</span><span class="sxs-lookup"><span data-stu-id="df35e-138">This component creates Animation Clips, sets keyframes and generates an Animator State Machine.</span></span> <span data-ttu-id="df35e-139">有关详细信息，请参阅 [状态可视化工具文档](../features/experimental/interactive-element.md#state-visualizer-experimental)</span><span class="sxs-lookup"><span data-stu-id="df35e-139">For more information see [State Visualizer Documentation](../features/experimental/interactive-element.md#state-visualizer-experimental)</span></span>

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a><span data-ttu-id="df35e-141">所有平台上现在都支持使用远程端口手势进行远程传送</span><span class="sxs-lookup"><span data-stu-id="df35e-141">Teleportation with the teleport gesture now supported on all platforms</span></span>

<span data-ttu-id="df35e-142">用户现在可以使用远程端口手势跨所有平台移动其播放空间。</span><span class="sxs-lookup"><span data-stu-id="df35e-142">Users can now use the teleport gesture to move around their play space across all platforms.</span></span> <span data-ttu-id="df35e-143">若要在具有默认配置的 MR 设备上通过控制器进行远程传送，请使用指纹。</span><span class="sxs-lookup"><span data-stu-id="df35e-143">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="df35e-144">若要使用可表达的手进行远程传送，请用手指朝上手势，同时将索引和滚动块朝外，通过卷起手指完成视区。</span><span class="sxs-lookup"><span data-stu-id="df35e-144">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="df35e-145">若要使用输入模拟进行远程传送，请参阅更新 [后的输入模拟服务文档](../features/input-simulation/input-simulation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="df35e-145">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../features/input-simulation/input-simulation-service.md).</span></span>

![远程端口手势](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a><span data-ttu-id="df35e-147">场景理解现在以实验性空间感知观察器的身份在 MRTK 中提供</span><span class="sxs-lookup"><span data-stu-id="df35e-147">Scene Understanding now available in MRTK as an experimental spatial awareness observer</span></span>

<span data-ttu-id="df35e-148">MRTK 2.6 [中引入了](/windows/mixed-reality/scene-understanding) 对场景理解的实验性支持。</span><span class="sxs-lookup"><span data-stu-id="df35e-148">Experimental support of [Scene Understanding](/windows/mixed-reality/scene-understanding) is introduced in MRTK 2.6.</span></span> <span data-ttu-id="df35e-149">用户可以在基于 MRTK 的项目中HoloLens 2空间感知观察器，将场景理解功能合并到一起。</span><span class="sxs-lookup"><span data-stu-id="df35e-149">Users can incorporate the scene understanding capabilities of HoloLens 2 as a spatial awareness observer in MRTK based projects.</span></span> <span data-ttu-id="df35e-150">有关详细信息， [请阅读场景理解](../features/spatial-awareness/scene-understanding.md) 文档。</span><span class="sxs-lookup"><span data-stu-id="df35e-150">Please read the [Scene Understanding documentation](../features/spatial-awareness/scene-understanding.md) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df35e-151">场景理解仅在 HoloLens 2 Unity 2019.4 及更高版本上受支持。</span><span class="sxs-lookup"><span data-stu-id="df35e-151">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>
>
> <span data-ttu-id="df35e-152">此功能需要场景理解包，该包现在可通过混合现实 [功能工具 获得](https://aka.ms/MRFeatureTool)。</span><span class="sxs-lookup"><span data-stu-id="df35e-152">This feature requires the Scene Understanding package, which is now available via the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>
> <span data-ttu-id="df35e-153">使用混合现实功能工具或通过 UPM 导入时，请在导入实验性 - 场景了解示例之前导入 Demos - SpatialAwareness 示例，因为存在依赖项问题。</span><span class="sxs-lookup"><span data-stu-id="df35e-153">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="df35e-154">有关详细信息 [，请参阅此 GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 问题。</span><span class="sxs-lookup"><span data-stu-id="df35e-154">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

![场景理解](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a><span data-ttu-id="df35e-156">运行时配置文件切换支持</span><span class="sxs-lookup"><span data-stu-id="df35e-156">Runtime profile switching support</span></span>

<span data-ttu-id="df35e-157">MRTK 现在允许在 MRTK 实例初始化之前（即 MRT (K 初始化配置文件开关) 之前）和在配置文件处于活动状态后（即活动配置文件开关) ）之前进行配置文件切换 (。</span><span class="sxs-lookup"><span data-stu-id="df35e-157">MRTK now allows profile switching both before the initialization of the MRTK instance (i.e. Pre MRTK initialization profile switch) and after a profile has been in active use (i.e. Active profile switch).</span></span> <span data-ttu-id="df35e-158">前一个开关可用于基于硬件的功能启用选择组件，而后者可用于在用户输入应用程序的子部分时修改体验。</span><span class="sxs-lookup"><span data-stu-id="df35e-158">The former switch can be used to enable select components based on capabilities of the hardware, while the latter can be used to modify experience as the user enters a subpart of the application.</span></span> <span data-ttu-id="df35e-159">有关详细信息和 [代码示例，请阅读](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) 有关配置文件切换的文档。</span><span class="sxs-lookup"><span data-stu-id="df35e-159">Please read the [documentation on profile switching](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) for more information and code samples.</span></span>

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a><span data-ttu-id="df35e-160">方向指示器和关注从实验阶段中学习的求解器</span><span class="sxs-lookup"><span data-stu-id="df35e-160">Directional indicator and follow solvers graduated from experimental</span></span>

<span data-ttu-id="df35e-161">两个新的求解器已准备好与主线 MRTK 一起使用。</span><span class="sxs-lookup"><span data-stu-id="df35e-161">Two new solvers are ready for use with mainline MRTK.</span></span>

![方向指示器求解器](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a><span data-ttu-id="df35e-163">手部教练从实验阶段中训练</span><span class="sxs-lookup"><span data-stu-id="df35e-163">Hand Coach graduated from experimental</span></span>

<span data-ttu-id="df35e-164">手部指导功能现已准备好与主线 MRTK 一起使用。</span><span class="sxs-lookup"><span data-stu-id="df35e-164">The Hand Coach feature is now ready for use with mainline MRTK.</span></span>

![手部教练示例](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a><span data-ttu-id="df35e-166">从实验性中开始的对话控件</span><span class="sxs-lookup"><span data-stu-id="df35e-166">Dialog controls graduated from experimental</span></span>

<span data-ttu-id="df35e-167">对话框控件现已准备好与主线 MRTK 一起使用。</span><span class="sxs-lookup"><span data-stu-id="df35e-167">Dialog controls are now ready for use with mainline MRTK.</span></span>

![对话框控件](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a><span data-ttu-id="df35e-169">从实验性中培养的脉冲着色器</span><span class="sxs-lookup"><span data-stu-id="df35e-169">Pulse shader graduated from experimental</span></span>

<span data-ttu-id="df35e-170">脉冲着色器脚本从实验阶段开始。</span><span class="sxs-lookup"><span data-stu-id="df35e-170">The Pulse shader scripts have graduated from experimental.</span></span> <span data-ttu-id="df35e-171">有关详细信息，请参阅： [脉冲着色器文档](../features/rendering/pulse-shader.md)</span><span class="sxs-lookup"><span data-stu-id="df35e-171">For more information see: [Pulse Shader Documentation](../features/rendering/pulse-shader.md)</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a><span data-ttu-id="df35e-173">输入录制服务改进</span><span class="sxs-lookup"><span data-stu-id="df35e-173">Input Recording Service improvements</span></span>

<span data-ttu-id="df35e-174">`InputRecordingService` 和 `InputPlaybackService` 现在可以录制和播放眼睛凝视输入。</span><span class="sxs-lookup"><span data-stu-id="df35e-174">`InputRecordingService` and `InputPlaybackService` can now record and play back eye gaze input.</span></span> <span data-ttu-id="df35e-175">录制经过优化，可确保在录制整个录制期间保持一致的帧速率，同时将文件大小和节省时间减少约 50%。</span><span class="sxs-lookup"><span data-stu-id="df35e-175">Recording has been optimized to ensure a consistent framerate throughout the recording period while recording file size and save time are also reduced by about 50%.</span></span> <span data-ttu-id="df35e-176">现在，可以异步执行录制文件的保存和加载。</span><span class="sxs-lookup"><span data-stu-id="df35e-176">Saving and loading of recording files can now be performed asynchronously.</span></span> <span data-ttu-id="df35e-177">请注意，此 MRTK 版本中记录的文件格式已更改，有关新版本 1.1 规范详细信息，请参阅此处。 [](../features/input-simulation/input-animation-file-format.md)</span><span class="sxs-lookup"><span data-stu-id="df35e-177">Note the file format of the recording has changed in this MRTK version, please see [here](../features/input-simulation/input-animation-file-format.md) for more information on the new version 1.1 specifications.</span></span>

### <a name="reading-mode"></a><span data-ttu-id="df35e-178">读取模式</span><span class="sxs-lookup"><span data-stu-id="df35e-178">Reading mode</span></span>

<span data-ttu-id="df35e-179">添加了对读取[模式的支持，HoloLens 2。](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality)</span><span class="sxs-lookup"><span data-stu-id="df35e-179">Added support for [reading mode](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) on HoloLens 2.</span></span> <span data-ttu-id="df35e-180">读取模式可减少系统的视场，但消除了 Unity 输出的缩放。</span><span class="sxs-lookup"><span data-stu-id="df35e-180">Reading mode reduces the system's field of view but eliminates a scaling of Unity's output.</span></span> <span data-ttu-id="df35e-181">Unity 呈现的像素将对应于项目上HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="df35e-181">A pixel rendered by Unity will correspond to a projected pixel on HoloLens 2.</span></span> <span data-ttu-id="df35e-182">应用程序作者应该对多个人员进行测试，以确保这是他们希望在应用中进行权衡。</span><span class="sxs-lookup"><span data-stu-id="df35e-182">Application authors should do tests with multiple individuals to be sure this is a tradeoff they want in their app.</span></span>

![Windows Mixed Reality读取模式](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a><span data-ttu-id="df35e-184">支持 UWP 上的 3D 应用启动器</span><span class="sxs-lookup"><span data-stu-id="df35e-184">Support for 3D app launchers on UWP</span></span>

<span data-ttu-id="df35e-185">添加了为 UWP 设置 [3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 应用启动器的能力。</span><span class="sxs-lookup"><span data-stu-id="df35e-185">Adds the ability to set a [3D app launcher](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for UWP.</span></span> <span data-ttu-id="df35e-186">此设置在"MRTK 生成窗口"和"MRTK 项目设置"下的"生成设置"中公开。</span><span class="sxs-lookup"><span data-stu-id="df35e-186">This setting is exposed both in the MRTK Build Window and the MRTK Project Settings, under Build Settings.</span></span> <span data-ttu-id="df35e-187">在 Unity 中生成期间，它会自动写入项目。</span><span class="sxs-lookup"><span data-stu-id="df35e-187">It's automatically written into the project during the build in Unity.</span></span>

![生成设置](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a><span data-ttu-id="df35e-189">中断性变更</span><span class="sxs-lookup"><span data-stu-id="df35e-189">Breaking changes</span></span>

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a><span data-ttu-id="df35e-190">导入的 GLTF 对象的某些字段现已大写</span><span class="sxs-lookup"><span data-stu-id="df35e-190">Certain fields of imported GLTF objects are now capitalized</span></span>

<span data-ttu-id="df35e-191">由于反序列化相关问题，导入的 GLTF 对象的某些字段现在以大写字母开始。</span><span class="sxs-lookup"><span data-stu-id="df35e-191">Due to deserialization related issues some fields of imported GLTF objects are now starting with capital letters.</span></span> <span data-ttu-id="df35e-192">受影响的字段 (名称中 `ComponentType`) ：、、 `Path` `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` 。</span><span class="sxs-lookup"><span data-stu-id="df35e-192">The affected fields are (in their new names): `ComponentType`, `Path`, `Interpolation`, `Target`, `Type`, `Mode`, `MagFilter`, `MinFilter`, `WrapS`, `WrapT`.</span></span>

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a><span data-ttu-id="df35e-193">输入动画二进制文件具有更新版本 1.1 格式</span><span class="sxs-lookup"><span data-stu-id="df35e-193">Input animation binary file has an updated version 1.1 format</span></span>

<span data-ttu-id="df35e-194">和 使用的输入动画二进制文件现在具有更新的文件格式，以启用对这两个 `InputRecordingService` `InputPlaybackService` 服务的优化。</span><span class="sxs-lookup"><span data-stu-id="df35e-194">Input animation binary file, used by `InputRecordingService` and `InputPlaybackService`, now has an updated file format to enable the optimizations made to those two services.</span></span> <span data-ttu-id="df35e-195">有关 [新版本](../features/input-simulation/input-animation-file-format.md) 1.1 规范的信息，请参阅此处。</span><span class="sxs-lookup"><span data-stu-id="df35e-195">Please see [here](../features/input-simulation/input-animation-file-format.md) for more information on the new version 1.1 specifications.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="df35e-196">MSBuild for Unity 支持</span><span class="sxs-lookup"><span data-stu-id="df35e-196">MSBuild for Unity support</span></span>

<span data-ttu-id="df35e-197">从 2.5.2 版开始，已移除对适用于 Unity 的 MSBuild 的支持，以与 Unity 的新包 [指南保持一致](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)。</span><span class="sxs-lookup"><span data-stu-id="df35e-197">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="known-issues"></a><span data-ttu-id="df35e-198">已知问题</span><span class="sxs-lookup"><span data-stu-id="df35e-198">Known issues</span></span>

### <a name="openxr"></a><span data-ttu-id="df35e-199">OpenXR</span><span class="sxs-lookup"><span data-stu-id="df35e-199">OpenXR</span></span>

<span data-ttu-id="df35e-200">全息远程处理和 OpenXR 当前存在一个已知问题，其中手部无法一致地可用。</span><span class="sxs-lookup"><span data-stu-id="df35e-200">There's currently a known issue with Holographic Remoting and OpenXR, where hand joints aren't consistently available.</span></span>
<span data-ttu-id="df35e-201">此外，眼动跟踪示例场景当前不兼容，尽管眼动跟踪 _确实_ 可以正常工作。</span><span class="sxs-lookup"><span data-stu-id="df35e-201">Additionally, the eye tracking sample scenes aren't currently compatible, though eye tracking _does_ work.</span></span>

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a><span data-ttu-id="df35e-202">某些混合现实工具包标准着色器功能需要 Foundation 包</span><span class="sxs-lookup"><span data-stu-id="df35e-202">Some Mixed Reality Toolkit Standard Shader features require the Foundation package</span></span>

<span data-ttu-id="df35e-203">通过 Unity 程序包管理器 导入时，MRTK 标准着色器实用工具脚本 (例如：HoverLight.cs) 不会与标准资产包中的着色器共存。</span><span class="sxs-lookup"><span data-stu-id="df35e-203">When imported via the Unity Package Manager, the MRTK Standard Shader utilities scripts (ex: HoverLight.cs) are not co-located with the shader in the Standard Assets package.</span></span> <span data-ttu-id="df35e-204">若要访问此功能，应用程序需要导入 Foundation 包。</span><span class="sxs-lookup"><span data-stu-id="df35e-204">To access this functionality, applications will require the Foundation package to be imported.</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="df35e-205">CameraCache 可能在关闭时创建新的相机</span><span class="sxs-lookup"><span data-stu-id="df35e-205">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="df35e-206">在某些情况下 (例如，在 Unity 编辑器) 中使用 LeapMotion 提供程序时，CameraCache 可能会关闭时重新创建 MainCamera。</span><span class="sxs-lookup"><span data-stu-id="df35e-206">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="df35e-207">有关详细信息 [，请参阅](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 此问题。</span><span class="sxs-lookup"><span data-stu-id="df35e-207">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="df35e-208">通过 Unity 代码导入示例时，FileNotFoundException 程序包管理器</span><span class="sxs-lookup"><span data-stu-id="df35e-208">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="df35e-209">根据项目路径的长度，通过 Unity 命令导入示例程序包管理器 Unity 控制台中生成 FileNotFoundException 消息。</span><span class="sxs-lookup"><span data-stu-id="df35e-209">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="df35e-210">原因是"缺少"文件的路径超过 256 个字符MAX_PATH (256 个字符) 。</span><span class="sxs-lookup"><span data-stu-id="df35e-210">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="df35e-211">若要解决此问题，请缩短项目路径的长度。</span><span class="sxs-lookup"><span data-stu-id="df35e-211">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="df35e-212">未指定空间化程序。</span><span class="sxs-lookup"><span data-stu-id="df35e-212">No spatializer was specified.</span></span> <span data-ttu-id="df35e-213">应用程序将不支持空间声音</span><span class="sxs-lookup"><span data-stu-id="df35e-213">The application will not support Spatial Sound</span></span>

<span data-ttu-id="df35e-214">如果未配置音频空间化程序，则会出现"未指定空间化程序"警告。</span><span class="sxs-lookup"><span data-stu-id="df35e-214">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="df35e-215">如果未安装 XR 包，则可能会发生这种情况，因为 Unity 在这些包中包含空间化程序。</span><span class="sxs-lookup"><span data-stu-id="df35e-215">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="df35e-216">若要解决此问题，请确保：</span><span class="sxs-lookup"><span data-stu-id="df35e-216">To resolve, please ensure that:</span></span>

- <span data-ttu-id="df35e-217">**窗口**  > **程序包管理器** 已安装一个或多个 XR 包</span><span class="sxs-lookup"><span data-stu-id="df35e-217">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="df35e-218">**混合现实工具包**  > **实用工具**  > **配置 Unity 项目**，并针对音频空间 **化程序进行选择**</span><span class="sxs-lookup"><span data-stu-id="df35e-218">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![选择"音频空间化程序"](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="df35e-220">NullReferenceException：对象引用未设置为实例化 (SceneTransitionService.Ini实例) </span><span class="sxs-lookup"><span data-stu-id="df35e-220">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="df35e-221">在某些情况下，打开 `EyeTrackingDemo-00-RootScene` 可能会导致 SceneTransitionService 类的 Initialize 方法中出现 NullReferenceException。</span><span class="sxs-lookup"><span data-stu-id="df35e-221">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="df35e-222">此错误是由于未设置场景转换服务的配置文件。</span><span class="sxs-lookup"><span data-stu-id="df35e-222">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="df35e-223">若要解决此问题，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="df35e-223">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="df35e-224">导航到 `MixedRealityToolkit` 层次结构中的 对象</span><span class="sxs-lookup"><span data-stu-id="df35e-224">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="df35e-225">在"检查器"窗口中，选择 `Extensions`</span><span class="sxs-lookup"><span data-stu-id="df35e-225">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="df35e-226">如果未展开，则展开 `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="df35e-226">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="df35e-227">将 的值设置为 `Configuration Profile` **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="df35e-227">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![修复场景转换配置文件](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="df35e-229">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="df35e-229">Oculus Quest</span></span>

<span data-ttu-id="df35e-230">在面向独立平台 时，当前存在将 [Oculus XR 插件与 一起使用的已知问题](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)。</span><span class="sxs-lookup"><span data-stu-id="df35e-230">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span> <span data-ttu-id="df35e-231">有关更新，请查看 Oculus bug 跟踪器/论坛/发行说明。</span><span class="sxs-lookup"><span data-stu-id="df35e-231">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="df35e-232">此 bug 由以下 3 个错误集表示：</span><span class="sxs-lookup"><span data-stu-id="df35e-232">The bug is signified with this set of 3 errors:</span></span>

![Oculus XR 插件错误](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="df35e-234">UnityUI 和 TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="df35e-234">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="df35e-235">较新版本的 TextMeshPro (1.5.0+ 或 2.1.1+) 存在已知问题，其中下拉列表的默认字号和粗体字体字符间距已更改。</span><span class="sxs-lookup"><span data-stu-id="df35e-235">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![TMP 映像](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="df35e-237">可以通过降级到早期版本的 TextMeshPro 来这样做。</span><span class="sxs-lookup"><span data-stu-id="df35e-237">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="df35e-238">有关详细信息 [，#8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 问题说明。</span><span class="sxs-lookup"><span data-stu-id="df35e-238">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
