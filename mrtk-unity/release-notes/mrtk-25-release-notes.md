---
title: MRTK 2.5 发行说明
description: MRTK 版本 2.5 的发行说明
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity， HoloLens， HoloLens 2， 混合现实， 开发， MRTK，
ms.openlocfilehash: 536a37b56b4c7de9875ce1e1642922bd363fecb1
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562487"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a><span data-ttu-id="fc625-104">Microsoft Mixed Reality Toolkit 2.5 发行说明</span><span class="sxs-lookup"><span data-stu-id="fc625-104">Microsoft Mixed Reality Toolkit 2.5 release notes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc625-105">存在一个已知的编译器问题，该问题会影响使用 ARM64 为 Microsoft HoloLens 2 构建的应用程序。</span><span class="sxs-lookup"><span data-stu-id="fc625-105">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="fc625-106">此问题通过更新 2019 Visual Studio版本 16.8 或更高版本来修复。</span><span class="sxs-lookup"><span data-stu-id="fc625-106">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="fc625-107">如果无法更新Visual Studio，请 `com.microsoft.mixedreality.toolkit.tools` 导入包以应用解决方法。</span><span class="sxs-lookup"><span data-stu-id="fc625-107">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new-in-254"></a><span data-ttu-id="fc625-108">2.5.4 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="fc625-108">What's new in 2.5.4</span></span>

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a><span data-ttu-id="fc625-109">修复了使用 UPM 时 Oculus 集成的 bug</span><span class="sxs-lookup"><span data-stu-id="fc625-109">Fixes a bug with Oculus Integration when using UPM</span></span>

<span data-ttu-id="fc625-110">使用 UPM 时，OculusXRSDKDeviceManagerProfile 在启动时始终将预制项[设置为 None。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160)</span><span class="sxs-lookup"><span data-stu-id="fc625-110">When using UPM, the OculusXRSDKDeviceManagerProfile would always have its [prefabs set to None on startup](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160).</span></span> <span data-ttu-id="fc625-111">此版本将 设备管理器 配置为在启动时指向一组工作预制。</span><span class="sxs-lookup"><span data-stu-id="fc625-111">This release configures the Device Manager to point to a working set of prefabs on startup.</span></span>

### <a name="fixes-an-issue-with-openxr-via-upm"></a><span data-ttu-id="fc625-112">修复了通过 UPM 使用 OpenXR 时的问题</span><span class="sxs-lookup"><span data-stu-id="fc625-112">Fixes an issue with OpenXR via UPM</span></span>

<span data-ttu-id="fc625-113">修复了默认情况下未将 OpenXR 提供程序添加到 link.xml 的问题，该问题会导致新项目在通过 Unity 的 程序包管理器 使用 OpenXR 和 MRTK 时无法在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="fc625-113">Fixes an issue where the OpenXR providers weren't added to the link.xml by default, causing new projects to fail to run on-device when using OpenXR and MRTK via Unity's Package Manager.</span></span> <span data-ttu-id="fc625-114">升级的现有项目仍然需要手动添加。</span><span class="sxs-lookup"><span data-stu-id="fc625-114">Existing projects that are upgraded will still need this added manually.</span></span>

## <a name="whats-new-in-253"></a><span data-ttu-id="fc625-115">2.5.3 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="fc625-115">What's new in 2.5.3</span></span>

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a><span data-ttu-id="fc625-116">修复了 2.5.2 中引入的 Oculus 回归</span><span class="sxs-lookup"><span data-stu-id="fc625-116">Fixes a regression with Oculus introduced in 2.5.2</span></span>

<span data-ttu-id="fc625-117">2.5.2 [集成 Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083)时引入了生成问题。</span><span class="sxs-lookup"><span data-stu-id="fc625-117">2.5.2 introduced [a build issue when integrating the Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083).</span></span> <span data-ttu-id="fc625-118">此版本可还原此问题。</span><span class="sxs-lookup"><span data-stu-id="fc625-118">This release reverts that issue.</span></span>

## <a name="whats-new-in-252"></a><span data-ttu-id="fc625-119">2.5.2 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="fc625-119">What's new in 2.5.2</span></span>

### <a name="add-support-for-openxr"></a><span data-ttu-id="fc625-120">添加对 OpenXR 的支持</span><span class="sxs-lookup"><span data-stu-id="fc625-120">Add support for OpenXR</span></span>

<span data-ttu-id="fc625-121">添加了对 Unity 的 OpenXR 预览包和 Microsoft 的混合现实 OpenXR 包的初始支持。</span><span class="sxs-lookup"><span data-stu-id="fc625-121">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="fc625-122">有关详细信息 [，请参阅 MRTK/XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)入门页 [、Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)论坛文章或 [Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) 文档。</span><span class="sxs-lookup"><span data-stu-id="fc625-122">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](/windows/mixed-reality/develop/unity/openxr-getting-started) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc625-123">Unity 中的 OpenXR 仅在 Unity 2020.3 及更高版本上受支持。</span><span class="sxs-lookup"><span data-stu-id="fc625-123">OpenXR in Unity is only supported on Unity 2020.3 and higher.</span></span>
> <span data-ttu-id="fc625-124">它还仅支持 x64、ARM 和 ARM64 生成。</span><span class="sxs-lookup"><span data-stu-id="fc625-124">It also only supports x64, ARM, and ARM64 builds.</span></span>

### <a name="boundary-visualization-errors-fixed"></a><span data-ttu-id="fc625-125">已修复的边界可视化错误</span><span class="sxs-lookup"><span data-stu-id="fc625-125">Boundary visualization errors fixed</span></span>

<span data-ttu-id="fc625-126">现在，边界可视化效果（如楼层或墙）将正确配置，并在运行时根据边界配置文件可见。</span><span class="sxs-lookup"><span data-stu-id="fc625-126">Boundary visualizations, like the floor or walls, will now be properly configured and visible at runtime according to the boundary profile.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="fc625-127">MSBuild for Unity 支持</span><span class="sxs-lookup"><span data-stu-id="fc625-127">MSBuild for Unity support</span></span>

<span data-ttu-id="fc625-128">从 2.5.2 版开始，已移除对适用于 Unity 的 MSBuild 的支持，以与 Unity 的新包 [指南保持一致](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)。</span><span class="sxs-lookup"><span data-stu-id="fc625-128">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="whats-new-in-251"></a><span data-ttu-id="fc625-129">2.5.1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="fc625-129">What's new in 2.5.1</span></span>

### <a name="package-dependency-errors-fixed"></a><span data-ttu-id="fc625-130">修复了包依赖项错误</span><span class="sxs-lookup"><span data-stu-id="fc625-130">Package dependency errors fixed</span></span>

<span data-ttu-id="fc625-131">此版本修复了不正确的包间文件 (，例如：标准资产中的文件不再错误地引用 Foundation) 。</span><span class="sxs-lookup"><span data-stu-id="fc625-131">This release fixes incorrect inter-package file dependencies (ex: files in Standard Assets no longer incorrectly reference files in Foundation).</span></span> <span data-ttu-id="fc625-132">版本 2.5.1 还添加了对文本网格 Pro 的显式依赖项。</span><span class="sxs-lookup"><span data-stu-id="fc625-132">Version 2.5.1 also adds an explicit dependency on Text Mesh Pro.</span></span>

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a><span data-ttu-id="fc625-133">复制到 Assets/MRTK/Shaders 的标准资产包着色器</span><span class="sxs-lookup"><span data-stu-id="fc625-133">Standard Assets package shaders copied to Assets/MRTK/Shaders</span></span>

<span data-ttu-id="fc625-134">通过 UPM 安装标准资产包时，着色器将复制到 Assets/MRTK/Shaders 文件夹，以便它们不再不可变。</span><span class="sxs-lookup"><span data-stu-id="fc625-134">When the Standard Assets package is installed via UPM, the shaders will be copied to the Assets/MRTK/Shaders folder so that they will no longer be immutable.</span></span> <span data-ttu-id="fc625-135">这解决了在下次加载项目时 (URP) 还原旧行为的着色器的问题。</span><span class="sxs-lookup"><span data-stu-id="fc625-135">This resolves the issue of shaders updated for the Universal Render Pipeline (URP) reverting the legacy behavior the next time the project is loaded.</span></span>

### <a name="fixed-teleport-cursor-sticking-to-hands"></a><span data-ttu-id="fc625-136">修复了远程端口光标卡在手上的问题</span><span class="sxs-lookup"><span data-stu-id="fc625-136">Fixed teleport cursor sticking to hands</span></span>

<span data-ttu-id="fc625-137">此版本修复了 [远程](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) 端口目标光标可以停留在手部视觉对象上的问题。</span><span class="sxs-lookup"><span data-stu-id="fc625-137">This release fixes an [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) where the teleport destination cursor can stick to hand visuals.</span></span>

## <a name="whats-new-in-250"></a><span data-ttu-id="fc625-138">2.5.0 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="fc625-138">What's new in 2.5.0</span></span>

### <a name="unity-package-manager-upm-support"></a><span data-ttu-id="fc625-139">Unity 程序包管理器 (UPM) 支持</span><span class="sxs-lookup"><span data-stu-id="fc625-139">Unity Package Manager (UPM) support</span></span>

<span data-ttu-id="fc625-140">现在可以使用 Unity 工具管理混合现实程序包管理器。</span><span class="sxs-lookup"><span data-stu-id="fc625-140">The Mixed Reality Toolkit can now be managed using the Unity Package Manager.</span></span>

![MRTK Foundation UPM 包](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="fc625-142">导入 MRTK UPM 包需要一些手动步骤。</span><span class="sxs-lookup"><span data-stu-id="fc625-142">There are some manual steps required to import the MRTK UPM packages.</span></span> <span data-ttu-id="fc625-143">有关详细信息， [请查看混合现实工具包和 Unity](../configuration/usingupm.md) 程序包管理器。</span><span class="sxs-lookup"><span data-stu-id="fc625-143">Please review [Mixed Reality Toolkit and Unity Package Manager](../configuration/usingupm.md) for more information.</span></span>

### <a name="oculus-quest-xr-sdk-support"></a><span data-ttu-id="fc625-144">Oculus Quest XR SDK 支持</span><span class="sxs-lookup"><span data-stu-id="fc625-144">Oculus Quest XR SDK support</span></span>

<span data-ttu-id="fc625-145">MRTK 现在支持使用本机 XR SDK 管道运行 Oculus Quest 头戴显示设备与控制器。</span><span class="sxs-lookup"><span data-stu-id="fc625-145">MRTK now supports running Oculus Quest Headsets and Controllers using the native XR SDK pipeline.</span></span> <span data-ttu-id="fc625-146">[Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)包也支持手部跟踪，感谢 Eric [Provencher](https://twitter.com/prvncher)在 MRTK-Quest 上的工作！</span><span class="sxs-lookup"><span data-stu-id="fc625-146">Hand tracking is also supported with the [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) thanks to [Eric Provencher's](https://twitter.com/prvncher) work on MRTK-Quest!</span></span>

<span data-ttu-id="fc625-147">有关如何使用新管道在 Oculus Quest 上部署设备的说明，请参阅 [Oculus Quest 设置指南](../supported-devices/oculus-quest-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="fc625-147">For instructions on how to deploy your device on the Oculus Quest using the new pipeline, see the [Oculus Quest Setup Guide](../supported-devices/oculus-quest-mrtk.md)</span></span>

### <a name="scrolling-object-collection"></a><span data-ttu-id="fc625-148">滚动对象集合</span><span class="sxs-lookup"><span data-stu-id="fc625-148">Scrolling Object Collection</span></span>

<span data-ttu-id="fc625-149">MRTK UX 组件已从实验性功能升级，为布局不同大小的 3D 内容提供了更多自由，并添加了对未附加碰撞体的对象的支持。</span><span class="sxs-lookup"><span data-stu-id="fc625-149">The MRTK UX component has been upgraded from an experimental feature and offers more freedom for layouting 3D content of different sizes with added support for objects that have no colliders attached.</span></span> <span data-ttu-id="fc625-150">还添加了一个禁用内容掩码的新选项，使原型制作更容易。</span><span class="sxs-lookup"><span data-stu-id="fc625-150">A new option for disabling content masking was also added, making prototyping easier.</span></span>

<span data-ttu-id="fc625-151">有关详细信息 [，请参阅滚动](../features/ux-building-blocks/scrolling-object-collection.md) 对象集合。</span><span class="sxs-lookup"><span data-stu-id="fc625-151">See [Scrolling Object Collection](../features/ux-building-blocks/scrolling-object-collection.md) for more information.</span></span>

![滚动对象集合](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a><span data-ttu-id="fc625-153">Teleport 指针动画、处理和声音改进</span><span class="sxs-lookup"><span data-stu-id="fc625-153">Teleport pointer animation, handling, and sound improvements</span></span>

<span data-ttu-id="fc625-154">远程端口指针现在改进了动画和音频反馈。</span><span class="sxs-lookup"><span data-stu-id="fc625-154">The teleport pointer now has improved animations and audio feedback.</span></span> <span data-ttu-id="fc625-155">我们还改进了对远程端口指针的处理，以便它在从指向附近表面转换到远离表面时处理更平滑。</span><span class="sxs-lookup"><span data-stu-id="fc625-155">We also improved the handling of the teleport pointer so it handles smoother when transitioning from pointing at nearby surfaces to farther away surfaces.</span></span>

### <a name="input-simulation-cheat-sheet"></a><span data-ttu-id="fc625-156">输入模拟备忘单</span><span class="sxs-lookup"><span data-stu-id="fc625-156">Input simulation cheat sheet</span></span>

<span data-ttu-id="fc625-157">HandInteractionExamples 场景现在具有可配置的快捷方式，用于显示输入模拟的帮助页</span><span class="sxs-lookup"><span data-stu-id="fc625-157">The HandInteractionExamples scene now has a configurable shortcut to show a help page for input simulation</span></span>

![输入模拟备忘单](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a><span data-ttu-id="fc625-159">使用鼠标进行输入模拟眼睛凝视</span><span class="sxs-lookup"><span data-stu-id="fc625-159">Input simulation eye gaze with mouse</span></span>

<span data-ttu-id="fc625-160">用户现在可以使用鼠标来模拟眼动跟踪。</span><span class="sxs-lookup"><span data-stu-id="fc625-160">Users can now use the Mouse for simulating eye tracking.</span></span> <span data-ttu-id="fc625-161">查看 `Eye Simulation Mode` 输入模拟配置文件中的字段，并设置为"鼠标"。</span><span class="sxs-lookup"><span data-stu-id="fc625-161">See the `Eye Simulation Mode` field in the input simulation profile and set it to Mouse.</span></span> <span data-ttu-id="fc625-162">这将替换上一 `Simulate Eye Position` 个字段。</span><span class="sxs-lookup"><span data-stu-id="fc625-162">This replaces the previous `Simulate Eye Position` field.</span></span>

![眼睛凝视鼠标](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a><span data-ttu-id="fc625-164">编辑器播放模式下的输入模拟运动控制器</span><span class="sxs-lookup"><span data-stu-id="fc625-164">Input simulation motion controller in editor Play Mode</span></span>

<span data-ttu-id="fc625-165">用户现在可以像在编辑器播放模式下一样模拟运动控制器。</span><span class="sxs-lookup"><span data-stu-id="fc625-165">Users can now simulate motion controller just like hands in editor play mode.</span></span> <span data-ttu-id="fc625-166">当前支持触发器、抓取按钮和菜单按钮。</span><span class="sxs-lookup"><span data-stu-id="fc625-166">The trigger, grab and menu buttons are currently supported.</span></span>

### <a name="conical-grab-pointer"></a><span data-ttu-id="fc625-167">圆条抓取指针</span><span class="sxs-lookup"><span data-stu-id="fc625-167">Conical grab pointer</span></span>

<span data-ttu-id="fc625-168">现在可以将抓取指针配置为使用抓取点中的圆锥（而不是球体）查询附近的对象。</span><span class="sxs-lookup"><span data-stu-id="fc625-168">Grab pointers can now be configured to query for nearby objects using a cone from the grab point rather than a sphere.</span></span> <span data-ttu-id="fc625-169">这更类似于默认HoloLens 2接口的行为，该接口使用圆锥查询附近的对象。</span><span class="sxs-lookup"><span data-stu-id="fc625-169">This more closely resembles the behavior from the default HoloLens 2 interface, which queries for nearby objects using a cone.</span></span> <span data-ttu-id="fc625-170">DefaultHoloLens2InputSystemProfile 也进行了调整以使用新的 `ConicalGrabPointer` 。</span><span class="sxs-lookup"><span data-stu-id="fc625-170">The DefaultHoloLens2InputSystemProfile has also been adjusted to use the new `ConicalGrabPointer`.</span></span>

![圆条抓取指针](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a><span data-ttu-id="fc625-172">TestUtilities 包</span><span class="sxs-lookup"><span data-stu-id="fc625-172">TestUtilities package</span></span>

<span data-ttu-id="fc625-173">现在有一个包 (Microsoft.MixedReality.Toolkit.Unity.TestUtilities.2.5.0.unitypackage) ，其中包含 MRTK 用于创建端到端测试的 PlayMode 和 TestMode 测试基础结构。</span><span class="sxs-lookup"><span data-stu-id="fc625-173">There is now a package (Microsoft.MixedReality.Toolkit.Unity.TestUtilities.2.5.0.unitypackage) that contains the PlayMode and TestMode test infrastructure that the MRTK uses to create end-to-end tests.</span></span> <span data-ttu-id="fc625-174">对于 MRTK 团队本身来说，此基础结构非常方便，我们很高兴让使用者使用此基础结构将测试覆盖率添加到自己的项目。</span><span class="sxs-lookup"><span data-stu-id="fc625-174">This infrastructure has been extremely handy for the MRTK team itself, and we're excited to have consumers use this to add test coverage to their own projects.</span></span>

<span data-ttu-id="fc625-175">下面的代码演示如何创建测试手，在特定位置显示它，移动它，然后收缩并打开。</span><span class="sxs-lookup"><span data-stu-id="fc625-175">The following code shows how to create a test hand, show it at a certain location, move it around, and then pinch and open.</span></span>

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

<span data-ttu-id="fc625-176">有关如何使用这些 TestUtilities 编写测试的说明，请参阅有关编写测试 [的此部分](../contributing/unit-tests.md#writing-tests)。</span><span class="sxs-lookup"><span data-stu-id="fc625-176">For instructions on how to write a test using these TestUtilities, see this section on [writing tests](../contributing/unit-tests.md#writing-tests).</span></span>

<span data-ttu-id="fc625-177">有关使用此基础结构的现有测试的示例，请参阅 MRTK 的 [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)。</span><span class="sxs-lookup"><span data-stu-id="fc625-177">For examples of existing tests that use this infrastructure, see MRTK's [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests).</span></span>

### <a name="support-for-the-leap-motion-451-unity-modules"></a><span data-ttu-id="fc625-178">支持 Leap Motion 4.5.1 Unity 模块</span><span class="sxs-lookup"><span data-stu-id="fc625-178">Support for the Leap Motion 4.5.1 Unity Modules</span></span>

<span data-ttu-id="fc625-179">添加了对 Leap Motion Unity 模块版本 4.5.1 的支持，并删除了对 4.4.0 资产的支持。</span><span class="sxs-lookup"><span data-stu-id="fc625-179">Support for the Leap Motion Unity Modules version 4.5.1 has been added and support for the 4.4.0 assets has been removed.</span></span> <span data-ttu-id="fc625-180">Leap Motion Unity 模块的当前支持版本为 4.5.0 和 4.5.1。</span><span class="sxs-lookup"><span data-stu-id="fc625-180">The current supported versions of the Leap Motion Unity Modules are 4.5.0 and 4.5.1.</span></span>

<span data-ttu-id="fc625-181">还有一个有关初始 Leap Motion 集成的附加步骤，请参阅 [How to Configure the Leap Motion Hand Tracking in MRTK（如何在 MRTK](../supported-devices/leap-motion-mrtk.md) 中配置 Leap Motion 手部跟踪）了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="fc625-181">There is also an additional step for initial Leap Motion integration, see [How to Configure the Leap Motion Hand Tracking in MRTK](../supported-devices/leap-motion-mrtk.md) for more information.</span></span>

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a><span data-ttu-id="fc625-182">空间感知网格观察器更好地处理材料自定义</span><span class="sxs-lookup"><span data-stu-id="fc625-182">Spatial Awareness Mesh Observer better handles customization of materials</span></span>

<span data-ttu-id="fc625-183">在此版本中， `Windows Mixed Reality Spatial Mesh Observer` 和 `Generic XR SDK Spatial Mesh Observer` 组件改进了可视材料处理。</span><span class="sxs-lookup"><span data-stu-id="fc625-183">With this release, the `Windows Mixed Reality Spatial Mesh Observer` and the `Generic XR SDK Spatial Mesh Observer` components have improved visual material handling.</span></span> <span data-ttu-id="fc625-184">现在，当观察程序更新网格后，材料将保留，以前，这些网格已重置为配置文件中配置的默认 VisibleMaterial。</span><span class="sxs-lookup"><span data-stu-id="fc625-184">Materials are now preserved when a mesh has been updated by the observer where, previously, they were reset to the default VisibleMaterial as configured in the profile.</span></span>

<span data-ttu-id="fc625-185">这使开发人员能够更改网格材料，并且不会意外覆盖更改。</span><span class="sxs-lookup"><span data-stu-id="fc625-185">This enables developers to alter the mesh material and not have the changes overwritten unexpectedly.</span></span>

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a><span data-ttu-id="fc625-186">Link.xml MixedRealityToolkit.Generated 文件夹中创建</span><span class="sxs-lookup"><span data-stu-id="fc625-186">Link.xml created in the MixedRealityToolkit.Generated folder</span></span>

<span data-ttu-id="fc625-187">随着 Unity 包管理器 MRTK 的引入，MRTK 现在会将文件写入文件夹 `link.xml` `Assets/MixedRealityToolkit.Generated` （如果不存在）。</span><span class="sxs-lookup"><span data-stu-id="fc625-187">With the introduction of Unity Package Manger MRTK, MRTK now writes a `link.xml` file to the `Assets/MixedRealityToolkit.Generated` folder, if none is present.</span></span> <span data-ttu-id="fc625-188">建议将此文件添加到 () `link.xml.meta` 添加到源代码管理。</span><span class="sxs-lookup"><span data-stu-id="fc625-188">It is recommended to add this file (and `link.xml.meta`) be added to source control.</span></span> <span data-ttu-id="fc625-189">Link.xml用于影响 Unity [链接](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) 器托管代码去除功能。</span><span class="sxs-lookup"><span data-stu-id="fc625-189">Link.xml is used to influence the [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) functionality of the Unity linker.</span></span>

<span data-ttu-id="fc625-190">有关 MRTK link.xml文件，请参阅 [MRTK 和托管代码去除一](../updates-deployment/mrtk-and-managed-code-stripping.md) 文。</span><span class="sxs-lookup"><span data-stu-id="fc625-190">More information on the MRTK link.xml file can be found in the [MRTK and managed code stripping](../updates-deployment/mrtk-and-managed-code-stripping.md) article.</span></span>

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a><span data-ttu-id="fc625-191">Unity 2019.3+：MRTK 配置对话框不再尝试启用旧版 XR 支持</span><span class="sxs-lookup"><span data-stu-id="fc625-191">Unity 2019.3+: MRTK configuration dialog no longer attempts to enable legacy XR support</span></span>

<span data-ttu-id="fc625-192">为了避免在使用 Unity 的 XR 平台时出现潜在冲突，从 MRTK 配置对话框中删除了启用旧版 XR 支持的选项。</span><span class="sxs-lookup"><span data-stu-id="fc625-192">To avoid potential conflicts when using Unity's XR Platform, the option to enable legacy XR support has been removed from the MRTK configuration dialog.</span></span> <span data-ttu-id="fc625-193">如果需要，可以启用旧版 XR 支持，在 Unity 2019中，使用"编辑项目设置  >    >
 **播放器**  >  **XR 设置**  >  **""支持虚拟现实"。**</span><span class="sxs-lookup"><span data-stu-id="fc625-193">If desired, legacy XR support can be enabled, in Unity 2019, using **Edit** > **Project Settings** >
**Player** > **XR Settings** > **Virtual Reality Supported**.</span></span>

### <a name="reduction-in-initializeonload-overhead"></a><span data-ttu-id="fc625-194">减少 InitializeOnLoad 开销</span><span class="sxs-lookup"><span data-stu-id="fc625-194">Reduction in InitializeOnLoad overhead</span></span>

<span data-ttu-id="fc625-195">我们一直在努力减少 InitializeOnLoad 处理程序中运行的工作量，这应提高内部循环开发速度。</span><span class="sxs-lookup"><span data-stu-id="fc625-195">We've been doing work to reduce the amount of work that runs in InitializeOnLoad handlers, which should lead to improvements in inner loop development speed.</span></span> <span data-ttu-id="fc625-196">每次编译脚本、进入播放模式之前以及编辑器启动时，都会运行 InitializeOnLoad 处理程序。</span><span class="sxs-lookup"><span data-stu-id="fc625-196">InitializeOnLoad handlers run every time a script is compiled, prior to entering play mode, and also at editor launch.</span></span> <span data-ttu-id="fc625-197">这些处理程序现在以更少的情况运行，从而改进了常规 Unity 响应能力。</span><span class="sxs-lookup"><span data-stu-id="fc625-197">These handlers now run in far fewer cases, resulting in general Unity responsiveness improvements.</span></span>

<span data-ttu-id="fc625-198">在某些情况下，必须做出权衡：</span><span class="sxs-lookup"><span data-stu-id="fc625-198">In some cases there was a tradeoff that had to be made:</span></span>

- <span data-ttu-id="fc625-199">有关 [额外的集成步骤，](../supported-devices/leap-motion-mrtk.md) 请参阅 Leap Motion Hand Tracking Configuration。</span><span class="sxs-lookup"><span data-stu-id="fc625-199">See [Leap Motion Hand Tracking Configuration](../supported-devices/leap-motion-mrtk.md) for the extra integration step.</span></span>
- <span data-ttu-id="fc625-200">对于使用 ARFoundation 的人，现在在其入门步骤中还有一个额外的手动步骤。</span><span class="sxs-lookup"><span data-stu-id="fc625-200">For those who are using ARFoundation, there's now an additional manual step in its getting started steps.</span></span>
  <span data-ttu-id="fc625-201">有关新步骤，请参阅 [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) 。</span><span class="sxs-lookup"><span data-stu-id="fc625-201">See [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) for the new steps.</span></span>
- <span data-ttu-id="fc625-202">对于将在 HoloLens 2 上将使用 [全息远程处理与旧版 XR 管道](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) 的用户，现在可以执行 [手动步骤](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) 。</span><span class="sxs-lookup"><span data-stu-id="fc625-202">For those who will be using [Holographic Remoting with legacy XR pipeline](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) on HoloLens 2, there is now a [manual step](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) to perform.</span></span>

### <a name="bounds-control-graduated"></a><span data-ttu-id="fc625-203">边界控制渐变</span><span class="sxs-lookup"><span data-stu-id="fc625-203">Bounds control graduated</span></span>

![边界控件](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="fc625-205">[边界控制](../features/ux-building-blocks/bounds-control.md) 以实验性为依据，并附带一组新功能和大量 bug 修复。</span><span class="sxs-lookup"><span data-stu-id="fc625-205">[Bounds control](../features/ux-building-blocks/bounds-control.md) graduated out of experimental and comes with a bunch of new features and tons of bug fixes.</span></span>
<span data-ttu-id="fc625-206">下面列出了此更新的要点：</span><span class="sxs-lookup"><span data-stu-id="fc625-206">Here a list of the highlights of this update:</span></span>

- <span data-ttu-id="fc625-207">属性被拆分为多个配置，以便更轻松地设置边界控件</span><span class="sxs-lookup"><span data-stu-id="fc625-207">properties are split into configurations which makes it easier to set up bounds control</span></span>
- <span data-ttu-id="fc625-208">可以通过可编写脚本的对象共享配置</span><span class="sxs-lookup"><span data-stu-id="fc625-208">configurations can be shared through scriptable objects</span></span>
- <span data-ttu-id="fc625-209">每个属性/可脚本属性均可配置运行时</span><span class="sxs-lookup"><span data-stu-id="fc625-209">every property / scriptable property is runtime configurable</span></span>
- <span data-ttu-id="fc625-210">不再在属性更改时重新创建边界控制远程测试机组</span><span class="sxs-lookup"><span data-stu-id="fc625-210">bounds control rig isn't recreated on property changes anymore</span></span>
- <span data-ttu-id="fc625-211">翻译句柄支持</span><span class="sxs-lookup"><span data-stu-id="fc625-211">translation handles support</span></span>
- <span data-ttu-id="fc625-212">通过约束管理器的完全约束支持</span><span class="sxs-lookup"><span data-stu-id="fc625-212">full constraint support through constraint manager</span></span>
- <span data-ttu-id="fc625-213">池中弹性系统集成 (试验性) </span><span class="sxs-lookup"><span data-stu-id="fc625-213">elastics system integration (experimental)</span></span>

<span data-ttu-id="fc625-214">现在已弃用旧的边界框，可以 [使用迁移工具](../features/tools/migration-window.md) 或 [边界框检查器](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control)升级使用范围框的现有游戏对象。</span><span class="sxs-lookup"><span data-stu-id="fc625-214">The old bounding box is now deprecated and existing game objects using bounding box can be [upgraded using the migration tool](../features/tools/migration-window.md) or the [bounding box inspector](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control).</span></span>

### <a name="constraint-manager-component"></a><span data-ttu-id="fc625-215">约束管理器组件</span><span class="sxs-lookup"><span data-stu-id="fc625-215">Constraint manager component</span></span>

<span data-ttu-id="fc625-216">现在，约束控件和对象操控器都可以通过新的 [约束管理器组件](../features/ux-building-blocks/constraint-manager.md)来使用约束。</span><span class="sxs-lookup"><span data-stu-id="fc625-216">Constraints can now be used by both, bounds control and object manipulator via the new [constraint manager component](../features/ux-building-blocks/constraint-manager.md).</span></span> <span data-ttu-id="fc625-217">这两个组件将为每个默认创建一个约束管理器，并自动处理任何附加的约束。</span><span class="sxs-lookup"><span data-stu-id="fc625-217">Both components will create a constraint manager per default and process any attached constraints automatically.</span></span>

<span data-ttu-id="fc625-218">此外，自动行为约束管理器还附带了 "手动" 模式，使用户能够决定应处理哪一个约束。</span><span class="sxs-lookup"><span data-stu-id="fc625-218">Additionally to the automatic behavior constraint manager also comes with a manual mode that lets users decide which constraint should be processed.</span></span>
<span data-ttu-id="fc625-219">出于此原因，我们在属性检查器中显示约束的方式已更改。</span><span class="sxs-lookup"><span data-stu-id="fc625-219">For this reason the way we display constraints in the property inspector changed a bit.</span></span>

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

<span data-ttu-id="fc625-220">应用于组件的约束现在显示为 "约束管理器" 组件中的一个列表，而使用约束管理器的组件 (" [边界控制](../features/ux-building-blocks/bounds-control.md#constraint-system) " 或 " [对象操控](../features/ux-building-blocks/object-manipulator.md#constraint-manager) 器") 现在将显示选定的约束管理器和模式 (自动或手动) 。</span><span class="sxs-lookup"><span data-stu-id="fc625-220">The constraints that are applied to the component are now shown as a list in the constraint manager component whereas the component using the constraint manager (either [bounds control](../features/ux-building-blocks/bounds-control.md#constraint-system) or [object manipulator](../features/ux-building-blocks/object-manipulator.md#constraint-manager)) will now show the selected constraint manager and mode (auto or manual).</span></span>
<span data-ttu-id="fc625-221">有关详细信息，请参阅文档中的 [约束管理器](../features/ux-building-blocks/constraint-manager.md) 部分。</span><span class="sxs-lookup"><span data-stu-id="fc625-221">For more information read the [constraint manager](../features/ux-building-blocks/constraint-manager.md) section in our docs.</span></span>

### <a name="hololens-2-button-material-update"></a><span data-ttu-id="fc625-222">HoloLens 2 按钮材料更新</span><span class="sxs-lookup"><span data-stu-id="fc625-222">HoloLens 2 button material update</span></span>

<span data-ttu-id="fc625-223">更新了 HoloLens 2 按钮的前固定架材料，以删除 MRC 中的黑色颜色。</span><span class="sxs-lookup"><span data-stu-id="fc625-223">Updated HoloLens 2 button's front cage material to remove black color in MRC.</span></span>

![HoloLens 2 按钮材料更新](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a><span data-ttu-id="fc625-225">说明面板更新，可移动示例场景</span><span class="sxs-lookup"><span data-stu-id="fc625-225">Description panel update, movable example scene</span></span>

<span data-ttu-id="fc625-226">更新了说明面板。</span><span class="sxs-lookup"><span data-stu-id="fc625-226">Updated description panel.</span></span> <span data-ttu-id="fc625-227"> (prefab) "新设计" 提供了一个 grabbable 顶栏，用户可在其中调整/移动整个场景。</span><span class="sxs-lookup"><span data-stu-id="fc625-227">(SceneDescriptionPanelRev.prefab) New design provides a grabbable top bar which allows the user to adjust/move the entire scene.</span></span>

![说明面板更新](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a><span data-ttu-id="fc625-229">空间网格可视化-轻按的脉冲</span><span class="sxs-lookup"><span data-stu-id="fc625-229">Spatial mesh visualization - pulse on air-tap</span></span>

<span data-ttu-id="fc625-230">更新了用于匹配 HoloLens 2 的外壳行为的空间网格的脉冲着色器示例。</span><span class="sxs-lookup"><span data-stu-id="fc625-230">Updated pulse shader example for the spatial mesh to match HoloLens 2's shell behavior.</span></span>

![无线点击脉冲](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a><span data-ttu-id="fc625-232">弹性系统 (试验性) </span><span class="sxs-lookup"><span data-stu-id="fc625-232">Elastic system (experimental)</span></span>

![弹性 System2](../features/images/elastics/Elastics_Main.gif)

<span data-ttu-id="fc625-234">MRTK 现在附带了一个 [弹性模拟系统](../features/elastics/elastic-system.md) ，该系统包含各种可扩展和灵活的子类，为四维四元数弹簧、三维量弹簧和简单线性弹簧系统提供绑定。</span><span class="sxs-lookup"><span data-stu-id="fc625-234">MRTK now comes with an [elastic simulation system](../features/elastics/elastic-system.md) that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="fc625-235">目前，支持 [池中弹性 manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 的以下 MRTK 组件可以利用池中弹性功能：</span><span class="sxs-lookup"><span data-stu-id="fc625-235">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="fc625-236">边界控件</span><span class="sxs-lookup"><span data-stu-id="fc625-236">Bounds control</span></span>](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [<span data-ttu-id="fc625-237">对象操控器</span><span class="sxs-lookup"><span data-stu-id="fc625-237">Object manipulator</span></span>](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a><span data-ttu-id="fc625-238">游戏杆 (试验) </span><span class="sxs-lookup"><span data-stu-id="fc625-238">Joystick (experimental)</span></span>

<span data-ttu-id="fc625-239">可以控制大目标对象的游戏杆界面的示例。</span><span class="sxs-lookup"><span data-stu-id="fc625-239">An example of joystick interface that can control a large target object.</span></span>

![操纵杆](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a><span data-ttu-id="fc625-241"> (试验) 颜色选取器</span><span class="sxs-lookup"><span data-stu-id="fc625-241">Color picker (experimental)</span></span>

<span data-ttu-id="fc625-242">一个试验性控件，使您可以轻松地在运行时更改任何对象上的材料颜色。</span><span class="sxs-lookup"><span data-stu-id="fc625-242">An experimental control that makes it easy to change material colors on any object at runtime.</span></span>

![颜色选取器控件的三个不同方法](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![颜色选取器控件的四种不同方法](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a><span data-ttu-id="fc625-245">中断性变更</span><span class="sxs-lookup"><span data-stu-id="fc625-245">Breaking changes</span></span>

### <a name="assembly-definition-files-changes"></a><span data-ttu-id="fc625-246">程序集定义文件更改</span><span class="sxs-lookup"><span data-stu-id="fc625-246">Assembly definition files changes</span></span>

<span data-ttu-id="fc625-247">某些 asmdef 文件已更改，现在仅支持 Unity 2018.4.13 f1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="fc625-247">Some asmdef files are changed and are now only supporting Unity 2018.4.13f1 or later.</span></span> <span data-ttu-id="fc625-248">当在 Unity 的早期版本中更新到 MRTK 2.5 时，将显示编译错误。</span><span class="sxs-lookup"><span data-stu-id="fc625-248">Compilation errors will show up when updating to MRTK 2.5 in earlier versions of Unity.</span></span> <span data-ttu-id="fc625-249">若要解决此情况，可以转到 `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` "项目" 窗口，并删除检查器中缺少的引用。</span><span class="sxs-lookup"><span data-stu-id="fc625-249">This can be fixed by going to `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` in the project window and removing the missing reference in the inspector.</span></span> <span data-ttu-id="fc625-250">用和重复这些 `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` 步骤 `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` 。</span><span class="sxs-lookup"><span data-stu-id="fc625-250">Repeat those steps with `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` and `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef`.</span></span> <span data-ttu-id="fc625-251">请注意，必须使用原始 (替换这三个 asmdef 文件（即，升级到 Unity 2019 时未修改的) ）来还原更改。</span><span class="sxs-lookup"><span data-stu-id="fc625-251">Note you must revert the changes by replacing those three asmdef files with original (i.e. unmodified) ones when upgrading to Unity 2019.</span></span>

### <a name="imixedrealitypointermediator"></a><span data-ttu-id="fc625-252">IMixedRealityPointerMediator</span><span class="sxs-lookup"><span data-stu-id="fc625-252">IMixedRealityPointerMediator</span></span>

<span data-ttu-id="fc625-253">此接口已更新为具有新函数：</span><span class="sxs-lookup"><span data-stu-id="fc625-253">This interface has been updated to have a new function:</span></span>

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

<span data-ttu-id="fc625-254">如果你的自定义指针转存进程不是子类的子类，则需要实现此新函数。</span><span class="sxs-lookup"><span data-stu-id="fc625-254">If you have a custom pointer mediator that doesn't subclass DefaultPointerMediator, you will need to implement this new function.</span></span> <span data-ttu-id="fc625-255">有关添加此问题的原因的更多背景信息，请参阅 [此问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) 。</span><span class="sxs-lookup"><span data-stu-id="fc625-255">See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) for more background on why this was added.</span></span> <span data-ttu-id="fc625-256">这样做是为了确保将指针首选项直接传递到转存进程，而不是根据是否存在采用 IPointerPreferences 的构造函数隐式完成此操作。</span><span class="sxs-lookup"><span data-stu-id="fc625-256">This was added to ensure that pointer preferences would be explicitly passed to the mediator, rather than having it be implicitly done based on the presence of a constructor that took a IPointerPreferences.</span></span>

### <a name="rest--device-portal-api"></a><span data-ttu-id="fc625-257">Rest/设备门户 API</span><span class="sxs-lookup"><span data-stu-id="fc625-257">Rest / Device Portal API</span></span>

<span data-ttu-id="fc625-258">`UseSSL`静态属性已从移动 `Rest` 到 `DevicePortal` 。</span><span class="sxs-lookup"><span data-stu-id="fc625-258">The `UseSSL` static property has been moved from `Rest` to `DevicePortal`.</span></span>

<span data-ttu-id="fc625-259">如果你之前执行此操作 .。。</span><span class="sxs-lookup"><span data-stu-id="fc625-259">If you did this previously...</span></span>

```csharp
Rest.UseSSL = true
```

<span data-ttu-id="fc625-260">立即执行此操作 .。。</span><span class="sxs-lookup"><span data-stu-id="fc625-260">Do this now...</span></span>

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a><span data-ttu-id="fc625-261">Link.xml</span><span class="sxs-lookup"><span data-stu-id="fc625-261">Link.xml</span></span>

<span data-ttu-id="fc625-262">如果某个应用程序以前使用了 MRTK 的 NuGet 分发版，则该 `link.xml` 文件已从基础包中删除。</span><span class="sxs-lookup"><span data-stu-id="fc625-262">If an application was previously using the NuGet distribution of the MRTK, the `link.xml` file has been removed from the Foundation package.</span></span> <span data-ttu-id="fc625-263">若要还原代码保存规则，请在 Unity 中打开项目一次，将在中创建一个默认 `link.xml` 文件 `Assets/MixedRealityToolkit.Generated` 。</span><span class="sxs-lookup"><span data-stu-id="fc625-263">To restore code preservation rules, opening the project in Unity once will create a default `link.xml` file in `Assets/MixedRealityToolkit.Generated`.</span></span> <span data-ttu-id="fc625-264">建议将此文件 (，并 `link.xml.meta` 将) 添加到源代码管理中。</span><span class="sxs-lookup"><span data-stu-id="fc625-264">It is recommended that this file (and `link.xml.meta`) be added to source control.</span></span>

### <a name="transform-constraint-changes"></a><span data-ttu-id="fc625-265">转换约束更改</span><span class="sxs-lookup"><span data-stu-id="fc625-265">Transform Constraint changes</span></span>

<span data-ttu-id="fc625-266">TargetTransform 属性已标记为过时，因为它不被约束系统使用。</span><span class="sxs-lookup"><span data-stu-id="fc625-266">TargetTransform property has been marked as obsolete as it wasn't used by constraint system.</span></span> <span data-ttu-id="fc625-267">约束逻辑基于传递到 Initialize 和 Apply 方法中的转换。</span><span class="sxs-lookup"><span data-stu-id="fc625-267">Constraint logic is based on the transform passed into Initialize and Apply methods.</span></span> <span data-ttu-id="fc625-268">依赖于此属性的派生用户约束可以通过存储约束组件的转换来实现相同的行为，从而在其实现中缓存 TargetTransform。</span><span class="sxs-lookup"><span data-stu-id="fc625-268">Derived user constraints that rely on this property can cache the TargetTransform in their implementation by storing the transform of the constraint component to achieve the same behavior.</span></span>

<span data-ttu-id="fc625-269">存储的初始世界的 `worldPoseOnManipulationStart` 数据类型已从 MixedRealityPose 更改为 MixedRealityTransform，其中包括操作对象的本地缩放值。</span><span class="sxs-lookup"><span data-stu-id="fc625-269">The stored initial world pose `worldPoseOnManipulationStart` data type has been changed from MixedRealityPose to MixedRealityTransform, which includes the local scale value of the manipulated object.</span></span> <span data-ttu-id="fc625-270">进行此更改后，无需再单独缓存任何初始缩放值。</span><span class="sxs-lookup"><span data-stu-id="fc625-270">With this change it's not necessary to separately cache any initial scale values anymore.</span></span>

### <a name="new-property-in-imixedrealitydictationsystem"></a><span data-ttu-id="fc625-271">IMixedRealityDictationSystem 中的新属性</span><span class="sxs-lookup"><span data-stu-id="fc625-271">New property in IMixedRealityDictationSystem</span></span>

<span data-ttu-id="fc625-272">新属性已 `AudioClip` 添加到 IMixedRealityDictationSystem 接口。</span><span class="sxs-lookup"><span data-stu-id="fc625-272">A new property `AudioClip` has been added to the IMixedRealityDictationSystem interface.</span></span> <span data-ttu-id="fc625-273">`AudioClip`使用属性可以访问与当前听写会话关联的音频剪辑。</span><span class="sxs-lookup"><span data-stu-id="fc625-273">The `AudioClip` property enables access to the audio clip associated with the current dictation session.</span></span> <span data-ttu-id="fc625-274">用户必须在实现接口的脚本中实现该属性。</span><span class="sxs-lookup"><span data-stu-id="fc625-274">Users must implement the property in their scripts implementing the interface.</span></span>

### <a name="service-facades-turn-down"></a><span data-ttu-id="fc625-275">服务外观关闭</span><span class="sxs-lookup"><span data-stu-id="fc625-275">Service facades turn down</span></span>

<span data-ttu-id="fc625-276">2.5 中的服务外观正在关闭。</span><span class="sxs-lookup"><span data-stu-id="fc625-276">Services facades are being turned down in 2.5.</span></span> <span data-ttu-id="fc625-277">此功能最初是通过创建) MRTK 的每个服务的虚假的场景 Gameobject 来使配置 MRTK 配置文件的配置变得更简单 (。</span><span class="sxs-lookup"><span data-stu-id="fc625-277">This feature was originally added to make configuration of the MRTK profiles easier (by creating fake in-scene GameObjects that represented each of MRTK's services).</span></span> <span data-ttu-id="fc625-278">在长时间运行的情况下，我们希望避免创建虚假的游戏内对象，并尝试使它们保持同步 (因为数据同步和 "真实" 问题是难以缩放和) 正确的。</span><span class="sxs-lookup"><span data-stu-id="fc625-278">In the long run, we want to avoid creating fake in-game objects and trying to keep them in sync (as data sync and "source of truth" issues are notoriously difficult to scale and get right).</span></span>

<span data-ttu-id="fc625-279">在2.5 中，服务外观处理程序会保持不变，以确保项目升级顺利进行-服务外观处理程序将删除项目中存在的任何外观，以确保在2.5 中打开的场景自动修复。</span><span class="sxs-lookup"><span data-stu-id="fc625-279">In 2.5, the service facade handlers are kept around to ensure that project upgrade goes smoothly - any facades that exist in the project will be deleted by the service facade handler to ensure that scenes opened up in 2.5 get automatically fixed.</span></span>

<span data-ttu-id="fc625-280">未来版本中将删除与服务外观功能关联的剩余代码。</span><span class="sxs-lookup"><span data-stu-id="fc625-280">The remaining code associated with the service facade feature will be removed in a future release.</span></span>

### <a name="addition-of-motion-controller-to-input-simulation-service"></a><span data-ttu-id="fc625-281">向输入模拟服务添加运动控制器</span><span class="sxs-lookup"><span data-stu-id="fc625-281">Addition of motion controller to input simulation service</span></span>

<span data-ttu-id="fc625-282">现在，运动控制器模拟以编辑器播放模式提供，沿现有的手动模拟。</span><span class="sxs-lookup"><span data-stu-id="fc625-282">Motion controller simulation is now offered in editor play mode along side the existing hand simulation.</span></span> <span data-ttu-id="fc625-283">若要启用此更改，许多当前函数/字段/属性现已标记为过时， `InputSimulationService.cs` 并 `MixedRealityInputSimulationProfile.cs` 获得最重要的更改。</span><span class="sxs-lookup"><span data-stu-id="fc625-283">To enable this change, many current functions/fields/properties are now marked obsolete, with `InputSimulationService.cs` and `MixedRealityInputSimulationProfile.cs` getting the most significant changes.</span></span> <span data-ttu-id="fc625-284">相关代码的逻辑和行为很大程度上保持不变，大多数过时的函数等都与将对 "手型" 的引用替换为更通用的术语 "controller" (例如从 `DefaultHandSimulationMode` 到 `DefaultControllerSimulationMode`) 。</span><span class="sxs-lookup"><span data-stu-id="fc625-284">The logic and behavior of relevant code largely remain the same, and the majority of obsoleted functions etc. are related to replacing reference to "hand" to the more generic term "controller" (e.g. from `DefaultHandSimulationMode` to `DefaultControllerSimulationMode`).</span></span> <span data-ttu-id="fc625-285">除了获取新名称外，还会更新某些新函数的返回类型，使其与名称/行为更改相匹配 (例如， `GetControllerDevice` 基于原始源的 `GetHandDevice` 返回 `BaseController` 而不是 `SimulatedHand`) 。</span><span class="sxs-lookup"><span data-stu-id="fc625-285">Besides getting new names, the return type of certain new functions are updated to match the name/behavior change (e.g. `GetControllerDevice` based on the original `GetHandDevice` now returns `BaseController` instead of `SimulatedHand`).</span></span>

<span data-ttu-id="fc625-286">`IInputSimulationService` 现在具有新的属性 `MotionControllerDataLeft` 和 `MotionControllerDataRight` 。</span><span class="sxs-lookup"><span data-stu-id="fc625-286">`IInputSimulationService` now has new properties `MotionControllerDataLeft` and `MotionControllerDataRight`.</span></span> <span data-ttu-id="fc625-287">`MixedRealityInputSimulationProfile` 现在包含用于特定运动控制器按钮的键盘映射的新字段。</span><span class="sxs-lookup"><span data-stu-id="fc625-287">`MixedRealityInputSimulationProfile` now includes new fields for the keyboard mapping of certain motion controller buttons.</span></span>

## <a name="known-issues"></a><span data-ttu-id="fc625-288">已知问题</span><span class="sxs-lookup"><span data-stu-id="fc625-288">Known issues</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="fc625-289">关闭时，CameraCache 可能会创建新的照相机</span><span class="sxs-lookup"><span data-stu-id="fc625-289">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="fc625-290">在某些情况下 (例如，在 Unity 编辑器中使用 LeapMotion 提供程序时) ，CameraCache 可以在关闭时重新创建 MainCamera。</span><span class="sxs-lookup"><span data-stu-id="fc625-290">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="fc625-291">有关详细信息，请参阅 [此问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 。</span><span class="sxs-lookup"><span data-stu-id="fc625-291">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="fc625-292">通过 Unity 包管理器导入示例时的 System.io.filenotfoundexception</span><span class="sxs-lookup"><span data-stu-id="fc625-292">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="fc625-293">根据项目路径的长度，通过 Unity 包管理器导入示例可能会在 Unity 控制台中生成 System.io.filenotfoundexception 消息。</span><span class="sxs-lookup"><span data-stu-id="fc625-293">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="fc625-294">导致这种情况的原因是，"丢失" 文件的路径超过了 MAX_PATH (256) 的字符。</span><span class="sxs-lookup"><span data-stu-id="fc625-294">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="fc625-295">若要解决此问题，请缩短项目路径的长度。</span><span class="sxs-lookup"><span data-stu-id="fc625-295">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="fc625-296">未指定 spatializer。</span><span class="sxs-lookup"><span data-stu-id="fc625-296">No spatializer was specified.</span></span> <span data-ttu-id="fc625-297">应用程序将不支持空间音效</span><span class="sxs-lookup"><span data-stu-id="fc625-297">The application will not support Spatial Sound</span></span>

<span data-ttu-id="fc625-298">如果未配置音频 spatializer，将显示 "未指定任何 spatializer" 警告。</span><span class="sxs-lookup"><span data-stu-id="fc625-298">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="fc625-299">如果未安装 XR 包，则可能会发生这种情况，因为 Unity 包含这些包中的 spatializers。</span><span class="sxs-lookup"><span data-stu-id="fc625-299">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="fc625-300">若要解决此问题，请确保：</span><span class="sxs-lookup"><span data-stu-id="fc625-300">To resolve, please ensure that:</span></span>

- <span data-ttu-id="fc625-301">**窗口**  > **程序包管理器** 已安装一个或多个 XR 包</span><span class="sxs-lookup"><span data-stu-id="fc625-301">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="fc625-302">**混合现实工具包**  > **实用工具**  > **配置 Unity 项目**，并针对音频空间 **化程序进行选择**</span><span class="sxs-lookup"><span data-stu-id="fc625-302">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![选择"音频空间化程序"](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="fc625-304">NullReferenceException：对象引用未设置为实例化 (SceneTransitionService.Ini实例) </span><span class="sxs-lookup"><span data-stu-id="fc625-304">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="fc625-305">在某些情况下，打开 `EyeTrackingDemo-00-RootScene` 可能会导致 SceneTransitionService 类的 Initialize 方法中出现 NullReferenceException。</span><span class="sxs-lookup"><span data-stu-id="fc625-305">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="fc625-306">此错误是由于未设置场景转换服务的配置文件。</span><span class="sxs-lookup"><span data-stu-id="fc625-306">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="fc625-307">若要解决此问题，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="fc625-307">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="fc625-308">导航到 `MixedRealityToolkit` 层次结构中的 对象</span><span class="sxs-lookup"><span data-stu-id="fc625-308">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="fc625-309">在"检查器"窗口中，选择 `Extensions`</span><span class="sxs-lookup"><span data-stu-id="fc625-309">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="fc625-310">如果未展开，则展开 `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="fc625-310">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="fc625-311">将 的值设置为 `Configuration Profile` **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="fc625-311">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![修复场景转换](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="fc625-313">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="fc625-313">Oculus Quest</span></span>

<span data-ttu-id="fc625-314">在面向独立平台 时，当前存在将 [Oculus XR 插件与 一起使用的已知问题](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)。</span><span class="sxs-lookup"><span data-stu-id="fc625-314">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span> <span data-ttu-id="fc625-315">有关更新，请查看 Oculus bug 跟踪器/论坛/发行说明。</span><span class="sxs-lookup"><span data-stu-id="fc625-315">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="fc625-316">此 bug 由以下 3 个错误集表示：</span><span class="sxs-lookup"><span data-stu-id="fc625-316">The bug is signified with this set of 3 errors:</span></span>

![Oculus XR 插件错误](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="fc625-318">UnityUI 和 TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="fc625-318">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="fc625-319">较新版本的 TextMeshPro (1.5.0+ 或 2.1.1+) 存在已知问题，其中下拉列表的默认字号和粗体字体字符间距已更改。</span><span class="sxs-lookup"><span data-stu-id="fc625-319">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![TMP 映像](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="fc625-321">可以通过降级到早期版本的 TextMeshPro 来这样做。</span><span class="sxs-lookup"><span data-stu-id="fc625-321">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="fc625-322">有关详细信息 [，#8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 问题说明。</span><span class="sxs-lookup"><span data-stu-id="fc625-322">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
