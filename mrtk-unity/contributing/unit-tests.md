---
title: 单元测试
description: 用于检查 MRTK 的可靠性的单元测试。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，UnitTest，
ms.openlocfilehash: a915b005a69de1864a5674bbb0363f18d1c74b19
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121345"
---
# <a name="writing-and-running-tests-in-mrtk"></a>在 MRTK 中编写和运行测试

为了确保 MRTK 可靠，MRTK 具有一组测试，可确保代码的更改不会回退现有行为。 大基本代码（如 MRTK）中的良好测试覆盖率对于稳定性至关重要，并在进行更改时具有信心。

MRTK 使用 [Unity 测试运行](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 程序，该程序使用 [NUnit](https://nunit.org/)的 unity 集成。 本指南将提供有关如何将测试添加到 MRTK 的起点。 它不会介绍可在提供的链接中查找的 [Unity 测试运行](https://docs.unity3d.com/Manual/testing-editortestsrunner.html) 程序和 [NUnit](https://nunit.org/) 。

提交拉取请求之前，请确保：

1. 在本地运行测试，使更改不会回退现有的行为 (如果任何测试失败，则不会允许完成 Pr) 。

1. 如果修复了某个 bug，请编写测试来测试该修复程序，并确保以后的代码修改不会再次将其中断。

1. 如果编写了一个功能，请编写新测试以防止即将发生的代码更改破坏此功能。

当前 playmode 测试应在 Unity 2018.4 中运行，并且在其他版本的 Unity 中可能会失败

## <a name="running-tests"></a>运行测试

### <a name="unity-editor"></a>Unity 编辑器

可以在 "**窗口** 常规测试运行程序" 下找到 [Unity 测试运行](https://docs.unity3d.com/Manual/testing-editortestsrunner.html)程序  >    >   ，它将显示所有可用的 MRTK play 和 edit 模式测试。

### <a name="command-line"></a>命令行

还可以通过位于的 [powershell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6) 脚本运行测试 `Scripts\test\run_playmode_tests.ps1` 。 这将完全按 github/CI 上执行 playmode 测试的方式运行这些测试 (参见下面) 和打印结果。 下面是有关如何运行脚本的一些示例

在 H:\mrtk.dev 上的项目上运行测试，并在 Unity 2018.4 (示例 Unity 2018.4.26 f1) 

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe"
```

在 H:\mrtk.dev 上运行包含 Unity 2018.4 的项目测试，并将结果输出到 C：\ playmode_test_out

```ps
.\run_playmode_tests.ps1 H:\mrtk.dev -unityExePath = "C:\Program Files\Unity\Hub\Editor\2018.4.26f1\Editor\Unity.exe" -outFolder "C:\playmode_test_out\"
```

还可以通过脚本多次运行 playmode 测试 `run_repeat_tests.ps1` 。 可以使用在中使用的所有参数 `run_playmode_tests.ps1` 。

```ps
.\run_repeat_tests.ps1 -Times 5
```

### <a name="pull-request-validation"></a>拉取请求验证

MRTK 的 CI 将在所有配置中生成 MRTK，并运行所有编辑和播放模式测试。 如果用户拥有足够的权限，则可以通过在 github PR 上发布注释来触发 CI `/azp run mrtk_pr` 。 可以在 PR 的 "检查" 选项卡中查看 CI 运行。

只有在成功通过所有测试后，才能将 PR 合并到 main。

### <a name="stress-tests--bulk-tests"></a>压力测试/批量测试

有时，测试仅会失败，这可能会使调试更加沮丧。

若要在本地运行多个测试，请修改按测试脚本。 以下 python 脚本应该使此方案更方便。

运行 python 脚本的先决条件是 [安装了 python](https://www.python.org/downloads/)3.x。

对于需要多次执行的单个测试：

```c#
[UnityTest]
public IEnumerator MyTest() {...}
```

在建议的命令行中运行以下命令 ([PowerShell](/powershell/scripting/install/installing-powershell?preserve-view=true&view=powershell-6#powershell-core)) 

```powershell
cd scripts\tests
# Repeat the test 5 times. Default is 100
python .\generate_repeat_tests.py -n 5 -t MyTest
```

将输出复制并粘贴到测试文件中。 下面的脚本用于按顺序运行多个测试：

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

可以为新代码添加两种类型的测试

* 播放模式测试
* 编辑模式测试

### <a name="play-mode-tests"></a>播放模式测试

MRTK play 模式测试能够测试您的新功能对不同输入源（如手或眼睛）的响应方式。

新的播放模式测试可以继承 [BasePlayModeTests](xref:Microsoft.MixedReality.Toolkit.Tests) ，或者可以使用以下主干。

若要创建新的播放模式测试：

* 导航到 "资产" > MRTK "> 测试 > PlayModeTests
* 右键单击，创建 > 测试 > c # 测试脚本
* 将默认模板替换为以下主干

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

编辑模式测试在 Unity 的编辑模式下执行，可以添加到混合现实工具包存储库中的 **MRTK**  >  **测试**  >  **EditModeTests** 文件夹下。
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

通常应根据测试所测试的类或测试的方案来命名测试。
例如，给定一个待测试的类：

```c#
namespace Microsoft.MixedReality.Toolkit.Input
{
    class InterestingInputClass
    {
    }
}
```

考虑命名测试

```c#
namespace Microsoft.MixedReality.Toolkit.Tests.Input
{
    class InterestingInputClassTest
    {
    }
}
```

考虑将测试放在类似于其对应非测试文件的文件夹层次结构中。
例如：

```md
Non-Test: Assets/MRTK/Core/Utilities/InterestingUtilityClass.cs
Test: Assets/MRTK/Tests/EditModeTests/Core/Utilities/InterestingUtilityClassTest.cs
```

这是为了确保有一个明确的方法来查找每个类的相应测试类（如果存在这样的测试类）。

不定义基于方案的测试的位置-如果测试执行整个输入系统，例如，请考虑将其放入相应的编辑模式或播放模式测试文件夹中的 "InputSystem" 文件夹。

### <a name="test-script-icons"></a>测试脚本图标

添加新测试时，请修改脚本以使其具有正确的 MRTK 图标。 有一个简单的 MRTK 工具可以实现此目的：

1. 中转到混合现实工具包菜单项
1. 依次单击 "实用程序"、"更新" 和图标
1. 单击 "测试"，更新程序将自动运行，更新所有缺少图标的测试脚本

### <a name="mrtk-utility-methods"></a>MRTK 实用工具方法

本部分介绍了编写 MRTK 的测试时使用的一些常用代码片段/方法。

有两个实用工具类可帮助设置 MRTK 和测试与 MRTK 中的组件的交互

* [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities)
* [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities)

TestUtilities 提供以下方法来设置 MRTK 场景和 Gameobject：

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

请参阅和的 API 文档 [`TestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.TestUtilities) ，以 [`PlayModeTestUtilities`](xref:Microsoft.MixedReality.Toolkit.Tests.PlayModeTestUtilities) 获取这些 util 类的更多方法，因为它们是定期扩展的，而新的测试则添加到 MRTK 中。