---
title: 初始化项目并部署第一个应用程序
description: 本课程介绍如何配置 Unity 项目以使用混合现实工具包 (MRTK) 以及如何将其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176022"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2.初始化项目并部署第一个应用程序

在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行混合现实工具包 (MRTK) 开发，以及如何导入 MRTK。 你还将演练如何配置和生成基本 Unity 场景，并将其从 Visual Studio 部署到 HoloLens 2。 将其部署到 HoloLens 2 后，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。

## <a name="objectives"></a>目标

* 了解如何配置用于 HoloLens 开发的 Unity
* 了解如何生成应用并将其部署到 HoloLens
* 在 HoloLens 2 设备上体验空间映射网格、手部网格和帧率计数器

### <a name="steps-overview"></a>步骤概述
:::row:::
    :::column:::
       ![概述步骤 1](images/mr-learning-base/base-02-overview-step1.png) **1. 创建新的 Unity 项目**
    :::column-end:::
    :::column:::
       ![概述步骤 2](images/mr-learning-base/base-02-overview-step2.png) **2. 将 MRTK 导入到项目中**
    :::column-end:::
    :::column:::
       ![概述步骤 3](images/mr-learning-base/base-02-overview-step3.png) **3. 使用 MRTK 配置新场景**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       ![概述步骤 4](images/mr-learning-base/base-02-overview-step4.png) **4. 构建 Unity 项目**
    :::column-end:::
    :::column:::
       ![概述步骤 5](images/mr-learning-base/base-02-overview-step5.png) **5. 构建 UWP 项目**
    :::column-end:::
    :::column:::
       ![概述步骤 6](images/mr-learning-base/base-02-overview-step6.png) **6. 在设备上运行项目**
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a>创建 Unity 项目

启动“Unity 中心”，选择“项目”选项卡，然后单击“新建”按钮旁边的 **向下箭头**：

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

在下拉列表中，选择[先决条件](mr-learning-base-01.md#prerequisites)中指定的 Unity 版本：

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> 如果 Unity Hub 没有特定的 Unity 版本，可以从 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下载存档</a>启动安装。

在“创建新项目”窗口中执行以下操作：

* 确保将“模板”设置为“3D” 
* 输入合适的“项目名称”，例如“MRTK 教程”
* 选择合适的“位置”来存储项目，例如“D:\MixedRealityLearning”
* 单击“创建”按钮，创建并启动新的 Unity 项目

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> 在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。 因此，应将 Unity 项目保存到驱动器的根目录附近。

等待 Unity 创建项目：

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a>切换生成平台

在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口： 

![Unity“生成设置...”菜单路径](images/mr-learning-base/base-02-section2-step1-1.png)

在“生成设置”窗口中选择“通用 Windows 平台”，然后：

1. 将“目标设备”设置为“HoloLens” 
2. 将“体系结构”设置为“ARM 64”  
3. 将“生成类型”设置为“D3D 项目”
4. 将“目标 SDK 版本”设置为“最新安装项” 
5. 将“最低平台版本”设置为 10.0.1024.0 
6. 将“Visual Studio 版本”设置为“最新安装项” 
7. 将“生成和运行位置”设置为“USB 设备” 
8. 将“生成配置”设置为“发布”，因为调试存在已知的性能问题 
9. 单击“切换平台”按钮

![设置了通用 Windows 平台设置的 Unity 生成设置](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

等待 Unity 完成平台切换操作：

![Unity 正在切换平台](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

当 Unity 完成平台切换后，单击 x 图标，关闭“生成设置”窗口。

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a>导入混合现实工具包和配置 Unity 项目

若要将“混合现实工具包”导入 Unity 项目中，需要使用[混合现实功能工具](../welcome-to-mr-feature-tool.md)，开发人员使用该工具能够发现、更新混合现实功能包并将其添加到 Unity 项目中。 你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。

从 [Microsoft 下载中心](https://aka.ms/MRFeatureTool)下载最新版本的混合现实功能工具，下载完成后，解压缩文件并将其保存到桌面。

> [!NOTE]
> 需先安装 [.NET 5.0 运行时](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)，才能运行混合现实功能工具

从下载的文件夹中打开可执行文件“MixedRealityFeatureTool”，以启动混合现实功能工具。  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>创建场景并配置 MRTK

在 Unity 菜单中，选择“文件” > “新建场景”：

![Unity“新建场景”菜单路径](images/mr-learning-base/base-02-section6-step1-1.png)

在“新建场景”窗口中，选择“基本（内置）”并单击“创建”以创建新场景：

![Unity“新建场景”窗口](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> 上面的屏幕截图来自 Unity 版本 2020，如果您使用的是 Unity 2019，那么单击“创建”时，将创建一个新的空白场景。

在 Unity 菜单中，选择“混合现实” > “工具包” > “添加到场景并配置…”，将 MRTK 添加到当前场景  ：

![Unity“添加到场景并配置...”菜单路径](images/mr-learning-base/base-02-section6-step1-2.png)

仍在“层次结构”窗口中选中 MixedRealityToolkit 对象，在“检查器”窗口中验证 MixedRealityToolkit 配置文件是否已设置为 DefaultMixedRealityToolkitConfigurationProfile  ：

![选中了 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-02-section6-step1-3.png)

在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口： 

![Unity“另存为...”菜单路径](images/mr-learning-base/base-02-section6-step1-4.png)

在“资产” > “场景”下，将场景保存在项目中。

![Unity 保存场景“保存”提示窗口](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a>向项目添加手交互

在 Unity 菜单中，选择“GameObject” > “3D 对象” > “立方体”，将立方体对象添加到场景中。

![将立方体添加到场景中](images/mr-learning-base/base-02-section8-step1-1.png)

单击“层次结构”窗口中的“立方体”对象，然后在检查器窗口中按如下所示配置其“转换”组件

* **位置**：X = 0, Y = -0.1, Z = 0.5
* **旋转**：X = 0, Y = 0, Z = 0
* **缩放**：X = 0.1, Y = 0.1, Z = 0.1

1 个 Unity 单位等于 1 米。 我们已将立方体的大小更新到 10x10x10 cm，位于头戴式耳机位置 (0,0,0) 的 50cm 处。 位于眼睛下方 10cm 处，给用户提供舒适的交互体验。 

如果使用默认缩放 (1,1,1)，则立方体将会太大。 如果使用默认位置 (0,0,0)，则该立方体将放在与耳机相同的位置上，你只能在向后移动之后才能看到它。

![调整转换信息](images/mr-learning-base/base-02-section8-step1-1b.png)

若要将焦点置于场景中的对象上，可双击“立方体”对象，然后再次放大一些。 也可以使用 F 键进行缩放并将焦点置于对象上。

要使用跟踪的手进行交互并抓取对象，对象必须具有：
 * 碰撞器组件，如“盒碰撞器”（Unity 的立方体默认已有一个盒碰撞器）
 * “对象操控器(脚本)”组件
 * NearInteractionGrabbable（脚本）组件

MRTK 的 ObjectManipulator 脚本能够让对象变得可移动、可缩放和可旋转，这些操作可通过一只或两只手来实现。 此脚本支持直接操作输入模型，因为此脚本让用户能够直接用手接触全息影像。

在“层次结构”窗口中保持选中“立方体”，在“检查器”窗口中单击“添加组件”按钮，然后搜索并选择“对象操控器”脚本，将对象操控器脚本添加到立方体对象。  

![向立方体添加对象操控器](images/mr-learning-base/base-02-section8-step1-2.PNG)

重复相同的操作，以向立方体添加 Near Interaction Grabbable 脚本

![向立方体添加 Near Interaction Grabbable](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> 在这种情况下，添加对象操控器（脚本）时，将自动添加约束管理器（脚本），因为对象操控器（脚本）依赖于约束管理器。

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a>通过 MRTK 输入模拟在 Unity 编辑器中测试应用程序

借助 MRTK 的输入模拟，你可以在 Unity 编辑器中测试各种类型的交互，而无需生成并部署到设备。 这使你可以在设计和开发过程中快速迭代你的想法。 使用键盘和鼠标组合来控制模拟输入。

单击播放按钮，然后进入播放模式。 按住左 Shift 或空格键来调出控制器（模拟的双手），鼠标移动将移动控制器，还可以使用鼠标滚轮来远离或靠近摄像头。 当指针在立方体上时，按住鼠标左键可抓握立方体对象。

* 按 W、A、S、D、Q、E 键可移动摄像头。
* 在按住鼠标右键的同时移动鼠标可以四处浏览。
* 按空格键（右手）或左 Shift 键（左手）以显示模拟的双手 
* 按 T 或 Y 键以将模拟的双手保持在视野中 
* 若要旋转模拟的手部，请按住 Ctrl 键并移动鼠标

![游戏模式](images/mr-learning-base/base-02-section8-step1-4.gif)


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
