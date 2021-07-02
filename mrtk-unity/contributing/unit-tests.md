---
title: 编写和运行测试
description: 单元测试以检查 MRTK 的可靠性。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， UnitTest，
ms.openlocfilehash: c8efb192982a1cb9ca07e91d29a69b11aaffc290
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177111"
---
# <a name="writing-and-running-tests"></a>编写和运行测试

为了确保 MRTK 可靠，MRTK 提供了一组测试，以确保对代码的更改不会回归现有行为。 在 MRTK 等大型代码库中拥有良好的测试覆盖率对于稳定性和在进行更改时具有置信度至关重要。

MRTK 使用 [Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 使用 [NUnit](https://nunit.org/)的 Unity 集成。 本指南将提供一个起点，了解如何向 MRTK 添加测试。 它将不会解释[Unity Test Runner](https://docs.unity3d.com/Manual/testing-editortestsrunner.html)[和 NUnit，](https://nunit.org/)可在提供的链接中查找。

在提交拉取请求之前，请确保：

1. 在本地运行测试，使更改不会回归现有行为 (如果任何测试失败，将不允许完成拉) 。

1. 如果修复 bug，请编写测试来测试修复，并确保将来的代码修改不会再次中断它。

1. 如果编写功能，请编写新测试以防止即将进行的代码更改中断此功能。

目前，playmode 测试将在 Unity 2018.4 中运行，并且可能会在其他版本的 Unity 中失败

## <a name="running-tests"></a>运行测试

### <a name="unity-editor"></a>Unity 编辑器

Unity [Test Runner"](https://docs.unity3d.com/Manual/testing-editortestsrunner.html)窗口常规"Test Runner，将显示所有可用的  >    >  MRTK 播放和编辑模式测试。

### <a name="command-line"></a>命令行

测试也可由位于 的 [Powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) 脚本运行 `Scripts\test\run_playmode_tests.ps1` 。 这将运行 playmode 测试，与在 github/CI (一样运行，) 输出结果。 下面是一些如何运行脚本的示例

对位于 H：\mrtk.dev 的项目运行测试，使用 Unity 2018.4 (例如 Unity 2018.4.26f1) 

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

使用 Unity 2018.4 对位于 H：\mrtk.dev 的项目运行测试，将结果输出到 C：\playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

也可通过脚本多次运行 playmode `run_repeat_tests.ps1` 测试。 中使用的所有参数 `run_playmode_tests.ps1` 都可能会使用。

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>拉取请求验证

MRTK 的 CI 将在所有配置中生成 MRTK，并运行所有编辑和播放模式测试。 如果用户有足够的权限，可以通过在 github PR 上发布注释 `/azp run mrtk_pr` 来触发 CI。 可以在 PR 的"检查"选项卡中查看 CI 运行。

只有在所有测试都成功完成后，PR 才能合并到 main 中。

### <a name="stress-tests--bulk-tests"></a>压力测试/批量测试

有时，测试偶尔会失败，调试可能会让人感到沮丧。

若要在本地运行多个测试，请修改相应的测试脚本。 以下 python 脚本应使此方案更方便。

运行 Python 脚本的先决条件是安装[Python 3.X。](https://www.python.org/downloads/)

对于需要多次执行的单个测试：

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

从命令行运行以下 ([建议使用 PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core)) 

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

将输出复制并粘贴到测试文件中。 以下脚本用于按顺序运行多个测试：

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest MySecondTest
```

新的测试文件现在应包含

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

打开测试运行程序并观察现在可以重复调用的新测试。

## <a name="writing-tests"></a>编写测试

可以针对新代码添加两种类型的测试

* 播放模式测试
* 编辑模式测试

### <a name="play-mode-tests"></a>播放模式测试

MRTK 播放模式测试能够测试新功能如何响应不同的输入源，例如手或眼睛。

新的播放模式测试可以继承 [BasePlayModeTests，](xref:Microsoft.MixedReality.Toolkit.Tests) 或者可以使用以下框架。

创建新的播放模式测试：

* 导航到 PlayModeTests >"MRTK >测试>资产"
* 右键单击"创建>测试> C# 测试脚本
* 将默认模板替换为以下框架

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

### <a name="edit-mode-tests"></a>编辑模式测试

编辑模式测试在 Unity 的编辑模式下执行，并可以在混合现实存储库的 **MRTK**  >  **测试**  >  **EditModeTests** 文件夹下Toolkit添加。
若要创建新测试，可以使用以下模板：

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

### <a name="test-naming-conventions"></a>测试命名约定

通常，应该根据测试的类或测试的方案对测试进行命名。
例如，给定一个要测试的类：

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

考虑为测试命名

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

请考虑将测试放置在文件夹层次结构中，该层次结构类似于其相应的非测试文件。
例如：

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

这是为了确保在此类测试类存在时，有一种明显的方式来查找每个类的相应测试类。

基于方案的测试的位置定义较少 - 例如，如果测试练习整个输入系统，请考虑在相应的编辑模式或播放模式测试文件夹中将输入系统放入"InputSystem"文件夹。

### <a name="test-script-icons"></a>测试脚本图标

添加新测试时，请修改脚本，使 MRTK 图标正确。 有一个简单的 MRTK 工具可以这样做：

1. 转到混合现实Toolkit菜单项
1. 单击"实用工具"，然后单击"更新"，然后单击"图标"
1. 单击"测试"，更新程序将自动运行，更新缺少其图标的任何测试脚本

### <a name="mrtk-utility-methods"></a>MRTK 实用工具方法

本部分介绍编写 MRTK 测试时常用的一些代码片段/方法。

有两个实用工具类可帮助设置 MRTK 并测试与 MRTK 中组件的交互

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities 提供以下方法来设置 MRTK 场景和 GameObjects：

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

请参阅 和 的 API 文档，了解这些 util 类的更多方法，因为它们在将新测试添加到 [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) MRTK 时会定期扩展。
