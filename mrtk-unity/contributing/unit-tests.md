---
title: UnitTests
description: 检查 MRTK 可靠性的 UnitTests。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， UnitTest，
ms.openlocfilehash: 51a485ff258ceafb8841ff1b86e715b1623f3255
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489237"
---
# <a name="writing-and-running-tests-in-mrtk"></a><span data-ttu-id="6b5a2-104">在 MRTK 中编写和运行测试</span><span class="sxs-lookup"><span data-stu-id="6b5a2-104">Writing and running tests in MRTK</span></span>

<span data-ttu-id="6b5a2-105">为了确保 MRTK 可靠，MRTK 提供了一组测试，以确保对代码的更改不会回归现有行为。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-105">To ensure MRTK is reliable, MRTK has a set of tests to ensure that changes to the code does not regress existing behavior.</span></span> <span data-ttu-id="6b5a2-106">在 MRTK 等大型代码库中拥有良好的测试覆盖率对于稳定性和在进行更改时具有置信度至关重要。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-106">Having good test coverage in a big codebase like MRTK is crucial for stability and having confidence when making changes.</span></span>

<span data-ttu-id="6b5a2-107">MRTK 使用 [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 使用 [NUnit](https://nunit.org/)的 Unity 集成。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-107">MRTK uses the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) which uses a Unity integration of [NUnit](https://nunit.org/).</span></span> <span data-ttu-id="6b5a2-108">本指南将提供一个起点，了解如何向 MRTK 添加测试。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-108">This guide will provide a starting point on how to add tests to MRTK.</span></span> <span data-ttu-id="6b5a2-109">它将不会解释[Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html)[和 NUnit，](https://nunit.org/)可在提供的链接中查找。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-109">It will not explain the [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) and [NUnit](https://nunit.org/) which can be looked up in the links provided.</span></span>

<span data-ttu-id="6b5a2-110">在提交拉取请求之前，请确保：</span><span class="sxs-lookup"><span data-stu-id="6b5a2-110">Before submitting a pull request, make sure to:</span></span>

1. <span data-ttu-id="6b5a2-111">在本地运行测试，使更改不会回归现有行为 (如果任何测试失败，将不允许完成拉) 。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-111">Run the tests locally so your changes don't regress existing behavior (completing PRs won't be allowed if any tests fail).</span></span>

1. <span data-ttu-id="6b5a2-112">如果修复 bug，请编写测试来测试修复，并确保将来的代码修改不会再次中断它。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-112">If fixing a bug, write a test to test the fix and ensure that future code modifications won't break it again.</span></span>

1. <span data-ttu-id="6b5a2-113">如果编写功能，请编写新测试以防止即将进行的代码更改中断此功能。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-113">If writing a feature, write new tests to prevent upcoming code changes breaking this feature.</span></span>

<span data-ttu-id="6b5a2-114">目前，playmode 测试将在 Unity 2018.4 中运行，并且可能会在其他版本的 Unity 中失败</span><span class="sxs-lookup"><span data-stu-id="6b5a2-114">Currently playmode tests are meant to be run in Unity 2018.4 and may fail in other versions of Unity</span></span>

## <a name="running-tests"></a><span data-ttu-id="6b5a2-115">运行测试</span><span class="sxs-lookup"><span data-stu-id="6b5a2-115">Running tests</span></span>

### <a name="unity-editor"></a><span data-ttu-id="6b5a2-116">Unity 编辑器</span><span class="sxs-lookup"><span data-stu-id="6b5a2-116">Unity editor</span></span>

<span data-ttu-id="6b5a2-117">Unity [Test Runner"](https://docs.unity3d.com/Manual/testing-editortestsrunner.html)窗口常规"Test Runner，将显示所有可用的  >    >  MRTK 播放和编辑模式测试。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-117">The [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) can be found under **Window** > **General** > **Test Runner** and will show all available MRTK play and edit mode tests.</span></span>

### <a name="command-line"></a><span data-ttu-id="6b5a2-118">命令行</span><span class="sxs-lookup"><span data-stu-id="6b5a2-118">Command line</span></span>

<span data-ttu-id="6b5a2-119">测试也可由位于 的 [Powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) 脚本运行 `Scripts\test\run_playmode_tests.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-119">Tests can also be run by a [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) script located at `Scripts\test\run_playmode_tests.ps1`.</span></span> <span data-ttu-id="6b5a2-120">这将运行 playmode 测试，与在 github/CI (一样运行，) 输出结果。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-120">This will run the playmode tests exactly as they are executed on github / CI (see below), and print results.</span></span> <span data-ttu-id="6b5a2-121">下面是一些如何运行脚本的示例</span><span class="sxs-lookup"><span data-stu-id="6b5a2-121">Here are some examples of how to run the script</span></span>

<span data-ttu-id="6b5a2-122">对位于 H：\mrtk.dev 的项目运行测试，使用 Unity 2018.4 (例如 Unity 2018.4.26f1) </span><span class="sxs-lookup"><span data-stu-id="6b5a2-122">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4 (for example Unity 2018.4.26f1)</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

<span data-ttu-id="6b5a2-123">使用 Unity 2018.4 对位于 H：\mrtk.dev 的项目运行测试，将结果输出到 C：\playmode_test_out</span><span class="sxs-lookup"><span data-stu-id="6b5a2-123">Run the tests on the project located at H:\mrtk.dev, with Unity 2018.4, output results to C:\playmode_test_out</span></span>

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

<span data-ttu-id="6b5a2-124">也可通过脚本多次运行 playmode `run_repeat_tests.ps1` 测试。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-124">It's also possible to run the playmode tests multiple times via the `run_repeat_tests.ps1` script.</span></span> <span data-ttu-id="6b5a2-125">可以使用在中使用的所有参数 `run_playmode_tests.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-125">All parameters used in `run_playmode_tests.ps1` may be used.</span></span>

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a><span data-ttu-id="6b5a2-126">拉取请求验证</span><span class="sxs-lookup"><span data-stu-id="6b5a2-126">Pull request validation</span></span>

<span data-ttu-id="6b5a2-127">MRTK 的 CI 将在所有配置中生成 MRTK，并运行所有编辑和播放模式测试。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-127">MRTK's CI will build MRTK in all configurations and run all edit and play mode tests.</span></span> <span data-ttu-id="6b5a2-128">如果用户拥有足够的权限，则可以通过在 github PR 上发布注释来触发 CI `/azp run mrtk_pr` 。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-128">CI can be triggered by posting a comment on the github PR `/azp run mrtk_pr` if the user has sufficient rights.</span></span> <span data-ttu-id="6b5a2-129">可以在 PR 的 "检查" 选项卡中查看 CI 运行。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-129">CI runs can be seen in the 'checks' tab of the PR.</span></span>

<span data-ttu-id="6b5a2-130">只有在成功通过所有测试后，才能将 PR 合并到 main。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-130">Only after all of the tests have passed successfully can the PR be merged into main.</span></span>

### <a name="stress-tests--bulk-tests"></a><span data-ttu-id="6b5a2-131">压力测试/批量测试</span><span class="sxs-lookup"><span data-stu-id="6b5a2-131">Stress tests / bulk tests</span></span>

<span data-ttu-id="6b5a2-132">有时，测试仅会失败，这可能会使调试更加沮丧。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-132">Sometimes tests will only fail occasionally which can be frustrating to debug.</span></span>

<span data-ttu-id="6b5a2-133">若要在本地运行多个测试，请修改按测试脚本。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-133">To have multiple test runs locally, modify the according test scripts.</span></span> <span data-ttu-id="6b5a2-134">以下 python 脚本应该使此方案更方便。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-134">The following python script should make this scenario more convenient.</span></span>

<span data-ttu-id="6b5a2-135">运行 python 脚本的先决条件是 [安装了 python](https://www.python.org/downloads/)3.x。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-135">Prerequisite for running the python script is having [Python 3.X installed](https://www.python.org/downloads/).</span></span>

<span data-ttu-id="6b5a2-136">对于需要多次执行的单个测试：</span><span class="sxs-lookup"><span data-stu-id="6b5a2-136">For a single test that needs to be executed multiple times:</span></span>

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="6b5a2-137">在建议的命令行中运行以下命令 ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core)) </span><span class="sxs-lookup"><span data-stu-id="6b5a2-137">Run the following from a command line ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core) is recommended)</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

<span data-ttu-id="6b5a2-138">将输出复制并粘贴到测试文件中。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-138">Copy and paste the output into your test file.</span></span> <span data-ttu-id="6b5a2-139">下面的脚本用于按顺序运行多个测试：</span><span class="sxs-lookup"><span data-stu-id="6b5a2-139">The following script is for running multiple tests in sequence:</span></span>

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

<span data-ttu-id="6b5a2-140">新的测试文件现在应包含</span><span class="sxs-lookup"><span data-stu-id="6b5a2-140">The new test file should now contain</span></span>

```c#
[UnityTest]
public IEnumerator A1MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A2MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A3MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator A4MyTest0(){ yield return MyTest();}
[UnityTest]
public IEnumerator MyTest() {...}
```

<span data-ttu-id="6b5a2-141">打开测试运行程序并观察现在可以重复调用的新测试。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-141">Open the test runner and observe the new tests that can now be called repeatedly.</span></span>

## <a name="writing-tests"></a><span data-ttu-id="6b5a2-142">编写测试</span><span class="sxs-lookup"><span data-stu-id="6b5a2-142">Writing tests</span></span>

<span data-ttu-id="6b5a2-143">可以为新代码添加两种类型的测试</span><span class="sxs-lookup"><span data-stu-id="6b5a2-143">There are two types of tests that can be added for new code</span></span>

* <span data-ttu-id="6b5a2-144">播放模式测试</span><span class="sxs-lookup"><span data-stu-id="6b5a2-144">Play mode tests</span></span>
* <span data-ttu-id="6b5a2-145">编辑模式测试</span><span class="sxs-lookup"><span data-stu-id="6b5a2-145">Edit mode tests</span></span>

### <a name="play-mode-tests"></a><span data-ttu-id="6b5a2-146">播放模式测试</span><span class="sxs-lookup"><span data-stu-id="6b5a2-146">Play mode tests</span></span>

<span data-ttu-id="6b5a2-147">MRTK 播放模式测试能够测试新功能如何响应不同的输入源，例如手或眼睛。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-147">MRTK play mode tests have the ability to test how your new feature responds to different input sources such as hands or eyes.</span></span>

<span data-ttu-id="6b5a2-148">新的播放模式测试可以继承 [BasePlayModeTests，](xref:Microsoft.MixedReality.Toolkit.Tests) 或者可以使用以下框架。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-148">New play mode tests can inherit [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) or the skeleton below can be used.</span></span>

<span data-ttu-id="6b5a2-149">创建新的播放模式测试：</span><span class="sxs-lookup"><span data-stu-id="6b5a2-149">To create a new play mode test:</span></span>

* <span data-ttu-id="6b5a2-150">导航到 PlayModeTests >"MRTK >测试>资产"</span><span class="sxs-lookup"><span data-stu-id="6b5a2-150">Navigate to Assets > MRTK > Tests > PlayModeTests</span></span>
* <span data-ttu-id="6b5a2-151">右键单击"创建>测试> C# 测试脚本</span><span class="sxs-lookup"><span data-stu-id="6b5a2-151">Right click, Create > Testing > C# Test Script</span></span>
* <span data-ttu-id="6b5a2-152">将默认模板替换为以下框架</span><span class="sxs-lookup"><span data-stu-id="6b5a2-152">Replace the default template with the skeleton below</span></span>

```c#
#if !WINDOWS_UWP
// When the .NET scripting backend is enabled and C# projects are built
// The assembly that this file is part of is still built for the player,
// even though the assembly itself is marked as a test assembly (this is not
// expected because test assemblies should not be included in player builds).
// Because the .NET backend is deprecated in 2018 and removed in 2019 and this
// issue will likely persist for 2018, this issue is worked around by wrapping all
// play mode tests in this check.

using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using NUnit.Framework;
using System;
using System.Collections;
using System.Linq;
using UnityEngine;
using UnityEngine.TestTools;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class ExamplePlayModeTests
    {
        // This method is called once before we enter play mode and execute any of the tests
        // do any kind of setup here that can't be done in playmode
        public void Setup()
        {
            // eg installing unity packages is only possible in edit mode
            // so if a test requires TextMeshPro we will need to check for the package before entering play mode
            PlayModeTestUtilities.InstallTextMeshProEssentials();
        }

        // Do common setup for each of your tests here - this will be called for each individual test after entering playmode
        // Note that this uses UnitySetUp instead of [SetUp] because the init function needs to await a frame passing
        // to ensure that the MRTK system has had the chance to fully set up before the test runs.
        [UnitySetUp]
        public IEnumerator Init()
        {
            // in most play mode test cases you would want to at least create an MRTK GameObject using the default profile
            TestUtilities.InitializeMixedRealityToolkit(true);
            yield return null;
        }

        // Destroy the scene - this method is called after each test listed below has completed
        // Note that this uses UnityTearDown instead of [TearDown] because the init function needs to await a frame passing
        // to ensure that the MRTK system has fully torn down before the next test setup->run cycle starts.
        [UnityTearDown]
        public IEnumerator TearDown()
        {
            PlayModeTestUtilities.TearDown();
            yield return null;
        }

        #region Tests

        /// <summary>
        /// Skeleton for a new MRTK play mode test.
        /// </summary>
        [UnityTest]
        public IEnumerator TestMyFeature()
        {
            // ----------------------------------------------------------
            // EXAMPLE PLAY MODE TEST METHODS
            // ----------------------------------------------------------
            // Getting the input system
            // var inputSystem = PlayModeTestUtilities.GetInputSystem();

            // Creating a new test hand for input
            // var rightHand = new TestHand(Handedness.Right);
            // yield return rightHand.Show(new Vector3(0, 0, 0.5f));

            // Moving the new test hand
            // We are doing a yield return here because moving the hand to a new position
            // requires multiple frames to complete the action.
            // yield return rightHand.MoveTo(new Vector3(0, 0, 2.0f));

            // Getting a specific pointer from the hand
            // var linePointer = PointerUtils.GetPointer<LinePointer>(Handedness.Right);
            // Assert.IsNotNull(linePointer);
            // ---------------------------------------------------------

            // Your new test here
            yield return null;
        }
        #endregion
    }
}
#endif
```

### <a name="edit-mode-tests"></a><span data-ttu-id="6b5a2-153">编辑模式测试</span><span class="sxs-lookup"><span data-stu-id="6b5a2-153">Edit mode tests</span></span>

<span data-ttu-id="6b5a2-154">编辑模式测试在 Unity 的编辑模式下执行，并可以在混合现实工具包存储库的 **MRTK**  >  **测试**  >  **EditModeTests** 文件夹下添加。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-154">Edit mode tests are executed in Unity's edit mode and can be added under the **MRTK** > **Tests** > **EditModeTests** folder in the Mixed Reality Toolkit repo.</span></span>
<span data-ttu-id="6b5a2-155">若要创建新测试，可以使用以下模板：</span><span class="sxs-lookup"><span data-stu-id="6b5a2-155">To create a new test the following template can be used:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.

using NUnit.Framework;

namespace Microsoft.MixedReality.Toolkit.Tests
{
    class EditModeExampleTest
    {
        [Test]
        /// the name of this method will be used as test name in the unity test runner
        public void TestEditModeExampleFeature()
        {

        }
    }
}
```

### <a name="test-naming-conventions"></a><span data-ttu-id="6b5a2-156">测试命名约定</span><span class="sxs-lookup"><span data-stu-id="6b5a2-156">Test naming conventions</span></span>

<span data-ttu-id="6b5a2-157">通常，应该根据测试的类或测试的方案对测试进行命名。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-157">Tests should generally be named based on the class they are testing, or the scenario that they are testing.</span></span>
<span data-ttu-id="6b5a2-158">例如，给定一个要测试的类：</span><span class="sxs-lookup"><span data-stu-id="6b5a2-158">For example, given a to-be-tested class:</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

<span data-ttu-id="6b5a2-159">考虑为测试命名</span><span class="sxs-lookup"><span data-stu-id="6b5a2-159">Consider naming the test</span></span>

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

<span data-ttu-id="6b5a2-160">请考虑将测试放置在文件夹层次结构中，该层次结构类似于其相应的非测试文件。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-160">Consider placing the test in a folder hierarchy that is similar to its corresponding non-test file.</span></span>
<span data-ttu-id="6b5a2-161">例如：</span><span class="sxs-lookup"><span data-stu-id="6b5a2-161">For example:</span></span>

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

<span data-ttu-id="6b5a2-162">这是为了确保在此类测试类存在时，有一种明显的方式来查找每个类的相应测试类。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-162">This is to ensure that there's a clear an obvious way of finding each class's corresponding test class, if such a test class exists.</span></span>

<span data-ttu-id="6b5a2-163">基于方案的测试的位置定义较少 - 例如，如果测试练习整个输入系统，请考虑在相应的编辑模式或播放模式测试文件夹中将输入系统放入"InputSystem"文件夹。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-163">Placement of scenario based tests is less defined - if the test exercises the overall input system, for example, consider putting it into an "InputSystem" folder in the corresponding edit mode or play mode test folder.</span></span>

### <a name="test-script-icons"></a><span data-ttu-id="6b5a2-164">测试脚本图标</span><span class="sxs-lookup"><span data-stu-id="6b5a2-164">Test script icons</span></span>

<span data-ttu-id="6b5a2-165">添加新测试时，请修改脚本，使 MRTK 图标正确。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-165">When adding a new test, please modify the script to have the correct MRTK icon.</span></span> <span data-ttu-id="6b5a2-166">有一个简单的 MRTK 工具可以这样做：</span><span class="sxs-lookup"><span data-stu-id="6b5a2-166">There's an easy MRTK tool to do so:</span></span>

1. <span data-ttu-id="6b5a2-167">中转到混合现实工具包菜单项</span><span class="sxs-lookup"><span data-stu-id="6b5a2-167">Go go the Mixed Reality Toolkit menu item</span></span>
1. <span data-ttu-id="6b5a2-168">依次单击 "实用程序"、"更新" 和图标</span><span class="sxs-lookup"><span data-stu-id="6b5a2-168">Click on Utilities, then Update, then Icons</span></span>
1. <span data-ttu-id="6b5a2-169">单击 "测试"，更新程序将自动运行，更新所有缺少图标的测试脚本</span><span class="sxs-lookup"><span data-stu-id="6b5a2-169">Click on Tests, and the updater will run automatically, updating any test scripts missing their icons</span></span>

### <a name="mrtk-utility-methods"></a><span data-ttu-id="6b5a2-170">MRTK 实用工具方法</span><span class="sxs-lookup"><span data-stu-id="6b5a2-170">MRTK Utility methods</span></span>

<span data-ttu-id="6b5a2-171">本部分介绍了编写 MRTK 的测试时使用的一些常用代码片段/方法。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-171">This section shows some of the commonly used code snippets / methods when writing tests for MRTK.</span></span>

<span data-ttu-id="6b5a2-172">有两个实用工具类可帮助设置 MRTK 和测试与 MRTK 中的组件的交互</span><span class="sxs-lookup"><span data-stu-id="6b5a2-172">There are two Utility classes that help with setting up MRTK and testing interactions with components in MRTK</span></span>

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

<span data-ttu-id="6b5a2-173">TestUtilities 提供以下方法来设置 MRTK 场景和 Gameobject：</span><span class="sxs-lookup"><span data-stu-id="6b5a2-173">TestUtilities provide the following methods to set up your MRTK scene and GameObjects:</span></span>

```c#
/// creates the mrtk GameObject and sets the default profile if passed param is true
TestUtilities.InitializeMixedRealityToolkit()

/// creates an empty scene prior to adding the mrtk GameObject to it
TestUtilities.InitializeMixedRealityToolkitAndCreateScenes();

/// sets the initial playspace transform and camera position
TestUtilities.InitializePlayspace();

/// destroys previously created mrtk GameObject and playspace
TestUtilities.ShutdownMixedRealityToolkit();
```

<span data-ttu-id="6b5a2-174">请参阅和的 API 文档 [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) ，以 [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) 获取这些 util 类的更多方法，因为它们是定期扩展的，而新的测试则添加到 MRTK 中。</span><span class="sxs-lookup"><span data-stu-id="6b5a2-174">Please refer to the API docs of [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) and [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) for further methods of these util classes as they're extended on a regular basis while new tests get added to MRTK.</span></span>