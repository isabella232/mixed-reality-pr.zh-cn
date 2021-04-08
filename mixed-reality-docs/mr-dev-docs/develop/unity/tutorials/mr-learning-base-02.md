---
title: 初始化项目并部署第一个应用程序
description: 本课程介绍如何配置 Unity 项目以使用混合现实工具包 (MRTK) 以及如何将其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 4363d3280036ef2cd93e75233005c00db17eb59b
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088602"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2.初始化项目并部署第一个应用程序

在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">混合现实工具包 (MRTK)</a> 开发，以及如何导入 MRTK。 你还将演练如何配置和生成基本 Unity 场景，并将其从 Visual Studio 部署到 HoloLens 2。 将其部署到 HoloLens 2 后，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a>目标

* 了解如何配置用于 HoloLens 开发的 Unity
* 了解如何生成应用并将其部署到 HoloLens
* 在 HoloLens 2 设备上体验空间映射网格、手部网格和帧率计数器

## <a name="creating-the-unity-project"></a>创建 Unity 项目

启动“Unity 中心”，选择“项目”选项卡，然后单击“新建”按钮旁边的 **向下箭头**：

![突出显示了“新建”按钮的 Unity 中心](images/mr-learning-base/base-02-section1-step1-1.png)

在下拉列表中，选择[先决条件](mr-learning-base-01.md#prerequisites)中指定的 Unity 版本：

![具有新版本选择器下拉菜单的 Unity 中心](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> 如果 Unity Hub 没有特定的 Unity 版本，可以从 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下载存档</a>启动安装。

在“创建新项目”窗口中执行以下操作：

* 确保将“模板”设置为“3D” 
* 输入合适的“项目名称”，例如“MRTK 教程”
* 选择合适的“位置”来存储项目，例如“D:\MixedRealityLearning”
* 单击“创建”按钮，创建并启动新的 Unity 项目

![Unity 中心，其中“新建项目窗口”已填写](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> 在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。 因此，应将 Unity 项目保存到驱动器的根目录附近。

等待 Unity 创建项目：

![Unity 正在新建项目](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>切换生成平台

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a>导入 TextMeshPro 基本资源

在 Unity 菜单中，选择“窗口” > “TextMeshPro” > “导入 TMP 基本资源”以打开“导入 Unity 包”窗口  ：

![Unity 导入 TMP 基本资源菜单路径](images/mr-learning-base/base-02-section3-step1-1.png)

在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：

![Unity TMP 基本资源导入窗口](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> MRTK 的 UI 元素需要 TextMeshPro 基本资源。 如果你不打算在项目中使用 MRTK 的 UI 元素，则可以跳过此步骤。

## <a name="importing-the-mixed-reality-toolkit"></a>导入混合现实工具包

若要将“混合现实工具包”导入 Unity 项目中，需要使用[混合现实功能工具](../welcome-to-mr-feature-tool.md)，开发人员使用该工具能够发现、更新混合现实功能包并将其添加到 Unity 项目中。 你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。

从 [Microsoft 下载中心](https://aka.ms/MRFeatureTool)下载最新版本的混合现实功能工具，下载完成后，解压缩文件并将其保存到桌面。

> [!NOTE]
> 需先安装 [.NET 5.0 运行时](https://dotnet.microsoft.com/download/dotnet/5.0)，才能运行混合现实功能工具

> [!NOTE]
> 混合现实功能工具目前仅在 Windows 上运行，对于 MacOS，请按照此[过程](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages)下载混合现实工具包并将其导入 unity 项目。

从下载的文件夹中打开可执行文件“MixedRealityFeatureTool”，以启动混合现实功能工具。  

![打开 MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a>配置 Unity 项目

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1.应用 MRTK 项目配置器设置

Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。 如果未显示该窗口，请转到“混合现实工具包” > “实用程序” > “配置 Unity 项目”：

![Unity“配置 Unity 项目”菜单路径](images/mr-learning-base/base-02-section5-step1-1.png)

在“MRTK 项目配置器”窗口中，展开“修改配置”部分，确保勾选所有选项，然后单击“应用”按钮以应用设置 ：

![Unity“MRTK 项目配置器”窗口](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> 可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：

> * 设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。 若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文档的[单通道实例化渲染](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)部分。
> * 设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。 若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。

### <a name="2-configure-additional-project-settings"></a>2.配置其他项目设置

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>创建场景并配置 MRTK

在 Unity 菜单中，选择“文件” > “新建场景”，以创建新场景 ：

![Unity“新建场景”菜单路径](images/mr-learning-base/base-02-section6-step1-1.png)

在 Unity 菜单中，选择“混合现实工具包” > “添加到场景并配置…”，将 MRTK 添加到当前场景 ：

![Unity“添加到场景并配置...”菜单路径](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口： 

![Unity“另存为...”菜单路径](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> 可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。 若要了解有关此主题的更多信息，可以参考 MRTK 的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">性能</a>文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。

![Unity 保存场景“保存”提示窗口](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a>导入教程资产

下载以下 Unity 自定义包：

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

若要导入 Unity 自定义包，在 Unity 菜单中选择“资产” > “导入包” > “自定义包...”，打开“导入包...”窗口：  

![导入自定义包](images/mr-learning-base/base-02-section7-step1-1.png)

在“导入包…”窗口中，选择下载的 MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage，然后单击“打开”按钮：

![选择资产包](images/mr-learning-base/base-02-section7-step1-2.png)

在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：

![选择要导入的所有资产](images/mr-learning-base/base-02-section7-step1-3.png)

导入教程资产后，“项目”窗口应如下所示：

![导入资产后的 Unity 项目窗口](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a>配置场景

在“项目”窗口中，导航到“资产”>“MRTK.Tutorials.GettingStarted”>“预制件”文件夹：

在“项目”窗口中，单击“立方体”预制件并将其拖动到“层次结构”窗口中，然后在“检查器”窗口中，按如下所示配置“转换”组件 

* **位置**：X = 0, Y = 0, Z = 0.5
* **旋转**：X = 0, Y = 0, Z = 0
* **缩放**：X = 1，Y = 1，Z = 1

![将立方体添加到场景中](images/mr-learning-base/base-02-section8-step1-1.png)

若要将焦点置于场景中的对象上，可双击“立方体”对象，然后再次放大一些：

若要使用被跟踪的双手与对象进行交互和抓取对象，对象必须具有碰撞体组件，例如盒碰撞体、Object Manipulator（脚本）组件和 NearInteractionGrabbable（脚本）组件。  

在“层次结构”窗口中保持选中“立方体”，在“检查器”窗口中单击“添加组件”按钮，然后搜索并选择“对象操控器”脚本，将对象操控器脚本添加到立方体对象。  

![向立方体添加对象操控器](images/mr-learning-base/base-02-section8-step1-2.png)

重复相同的操作，以向立方体添加 Near Interaction Grabbable 脚本

![向立方体添加 Near Interaction Grabbable](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> 在这种情况下，添加对象操控器（脚本）时，将自动添加约束管理器（脚本），因为对象操控器（脚本）依赖于约束管理器。

> [!NOTE]
> 在本教程中，碰撞体已添加到立方体对象中。 若要详细了解碰撞体，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞体</a>文档。

若要在 Unity 编辑器中测试此情况，可以进入播放模式并按住左 Shift 或空格键来启用控制器，这样即可通过鼠标移动来移动控制器，还可以使用鼠标滚轮将其移动到距离相机更远或更近的位置。  当指针位于立方体上时，按住鼠标右键以移动立方体对象。

![游戏模式](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a>将应用程序构建到 HoloLens 2

### <a name="1-build-the-unity-project"></a>1.生成 Unity 项目

在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口。 

在“生成设置”窗口中单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表，然后单击“生成”按钮以打开“生成通用 Windows 平台”窗口：

![选中了 UWP 的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section9-step1-1.png)

在“生成通用 Windows 平台”窗口中，选择用于存储生成的适当位置（例如 _D:\MixedRealityLearning\Builds_），创建一个新文件夹并为其指定适当的名称（例如 _GettingStarted_），然后单击“选择文件夹”按钮，启动生成过程：

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section9-step1-2.png)

等待 Unity 完成生成过程：

![Unity 正在生成进程](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.生成并部署应用程序

生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。 在文件夹内导航，然后双击解决方案文件，在 Visual Studio 中其打开：

![选中了“新建的 Visual Studio 解决方案”的 Windows 资源管理器](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> 如果 Visual Studio 要求安装新组件，请花一点时间确保拥有[安装工具](../../install-the-tools.md)文档中的所有必备组件。

通过选择“Master”配置或“发布”配置、ARM64 体系结构和“设备”作为目标，配置 Visual Studio for HoloLens   ：

![配置为部署到 HoloLens 2 的 Visual Studio](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> 如果要部署到 HoloLens（第一代），请选择 x86 体系结构。

> [!NOTE]
> 对于 HoloLens，通常是针对 ARM 体系结构进行生成。 但是，在 Unity 2019.3 中有一个 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知问题</strong></a>，即在 Visual Studio 中选择 ARM 作为生成体系结构时会导致错误。 建议的解决方法是针对 ARM64 进行生成。 如果该方法不可行，请前往“编辑”>“项目设置”>“播放器”>“其他设置”并禁用“图形作业” 。

> [!NOTE]
> 如果目标选项中没有“设备”，则可能需要将 Visual Studio 解决方案的启动项目从 IL2CPP 项目更改为 UWP 项目。 在“解决方案资源管理器”中，右键单击“YourProjectName (通用 Windows)”并选择“设为启动项目”。

将 HoloLens 连接到计算机，然后选择“调试” > “启动但不调试”，以生成并部署到你的设备 ：

![Visual Studio“启动(不调试)”菜单路径](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> 在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。 这两个步骤都可以按照[这些说明](../../platform-capabilities-and-apis/using-visual-studio.md)来完成。

> [!TIP]
> 你还可以部署到 [HoloLens 模拟器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)或创建[应用包](/windows/uwp/packaging/packaging-uwp-apps)用于旁加载。

使用“启动但不调试”会自动启动设备上的应用，而不会连接 Visual Studio 调试器。

选择“生成”>“部署解决方案”，在不自动启动应用的情况下将内容部署到设备。

> [!NOTE]
>在应用中，你可能会注意到诊断探查器，可以使用语音命令“切换诊断”来切换其可见性。 我们建议你在开发过程中使探查器在大部分时间都可见，以便了解何时更改应用可能会影响性能。 例如，HoloLens 应用应以 [60 Fps 连续运行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。

## <a name="congratulations"></a>祝贺

现在，你已经部署了第一个 HoloLens 2 应用。 打开应用后，你面前应该会出现一个立方体对象，你应该能够通过移动该对象来与其进行交互；并且当你四处走动时，应该会看到一个空间映射网格，它覆盖了 HoloLens 识别出的表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。 这些只是 MRTK 附带的几个基础功能。 在接下来的教程中，我们将向场景添加内容，以探索 HoloLens 和 MRTK 的各种功能。

> [!div class="nextstepaction"]
> [下一教程：3.配置 MRTK 配置文件](mr-learning-base-03.md)