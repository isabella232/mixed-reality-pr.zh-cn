---
title: 初始化项目并部署第一个应用程序
description: 本课程介绍如何配置 Unity 项目以使用混合现实工具包 (MRTK) 以及如何将其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 82551257339d41940075ee06a6e6937624b83900
ms.sourcegitcommit: 08503cada8a29a34bcbd9fd955cb23adfe9b60a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99627848"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2.初始化项目并部署第一个应用程序

在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 开发，以及如何导入 MRTK。 你还将演练如何配置和生成基本 Unity 场景，并将其从 Visual Studio 部署到 HoloLens 2。 将其部署到 HoloLens 2 后，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。

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

在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口： 

![Unity“生成设置...”菜单路径](images/mr-learning-base/base-02-section2-step1-1.png)

在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮： 

![选中了 UWP 要从 Standalone 切换平台的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section2-step1-2.png)

等待 Unity 完成平台切换操作：

![Unity 正在切换平台](images/mr-learning-base/base-02-section2-step1-3.png)

当 Unity 完成平台切换后，单击红色 **x** 图标，关闭“生成设置”窗口：

![突出显示了“关闭”图标的 Unity 生成窗口](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>导入 TextMeshPro 基本资源

在 Unity 菜单中，选择“窗口” > “TextMeshPro” > “导入 TMP 基本资源”以打开“导入 Unity 包”窗口  ：

![Unity 导入 TMP 基本资源菜单路径](images/mr-learning-base/base-02-section3-step1-1.png)

在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：

![Unity TMP 基本资源导入窗口](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> MRTK 的 UI 元素需要 TextMeshPro 基本资源。 如果你不打算在项目中使用 MRTK 的 UI 元素，则可以跳过此步骤。

## <a name="importing-the-mixed-reality-toolkit"></a>导入混合现实工具包

若要将“混合现实工具包”导入 Unity 项目中，需要使用[混合现实功能工具](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)，开发人员使用该工具能够发现、更新混合现实功能包并将其添加到 Unity 项目中。 你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。

从 [Microsoft 下载中心](https://aka.ms/MRFeatureTool)下载最新版本的混合现实功能工具，下载完成后，解压缩文件并将其保存到桌面。

> [!NOTE]
> 需先安装 [.NET 5.0 运行时](https://dotnet.microsoft.com/download/dotnet/5.0)，才能运行混合现实功能工具

> [!NOTE]
> 混合现实功能工具目前仅在 Windows 上运行，对于 MacOS，请按照此[过程](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages)下载混合现实工具包并将其导入 unity 项目。

从下载的文件夹中打开可执行文件“MixedRealityFeatureTool”，以启动混合现实功能工具。  

![打开 MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)

打开“MixedRealityFeatureTool”后，单击“开始”以开始使用混合现实功能工具。

![MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-2.png)

功能按类别进行了分组，以便于查找，单击“混合现实工具包”下拉列表，查找与混合现实工具包相关的包。

![MixedRealityFeatureTool 窗口](images/mr-learning-base/base-02-section4-step1-3.png)

勾选“混合现实工具包基础”，并单击其旁边的下拉列表，选择所需的 MRTK 版本，在本教程系列中，请选择“2.5.3”。 然后单击“获取功能”按钮，下载所选的包。

![选择混合现实基础](images/mr-learning-base/base-02-section4-step1-4.png)

“导入功能”窗口中出现了所选包“混合现实工具包基础 2.5.3”及其依赖项包“混合现实工具包标准资产 2.5.3”  。

还需要设置目标 unity 项目的位置以提供“项目路径”，单击项目路径旁边的三个点，在浏览器中浏览到所需项目文件夹，例如“D:\MixedRealityLearning\MRTK Tutorials”。

> [!NOTE]
> 浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。 文件名必须有一个值才能使文件夹被选中。

接下来，单击“验证”按钮以验证所选包，随即显示一个弹出窗口，其中显示消息“未检测到任何验证问题”，单击“确定”以关闭弹出窗口，然后单击“导入”按钮。

![验证混合现实基础](images/mr-learning-base/base-02-section4-step1-5.png)

单击“批准”按钮，将“混合现实工具包”添加到项目中。

![批准混合现实基础](images/mr-learning-base/base-02-section4-step1-6.png)

## <a name="configuring-the-unity-project"></a>配置 Unity 项目

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1.应用 MRTK 项目配置器设置

Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。 如果未显示该窗口，请转到“混合现实工具包” > “实用程序” > “配置 Unity 项目”：

![Unity“配置 Unity 项目”菜单路径](images/mr-learning-base/base-02-section5-step1-1.png)

在“MRTK 项目配置器”窗口中，展开“修改配置”部分，确保勾选所有选项，然后单击“应用”按钮以应用设置 ：

![Unity“MRTK 项目配置器”窗口](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> 可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：

> * 设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。 若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文档的[单通道实例化渲染](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)部分。
> * 设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。 若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。

### <a name="2-configure-additional-project-settings"></a>2.配置其他项目设置

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： 

在“项目设置”窗口中，选择“播放器” > “XR 设置”，勾选“支持虚拟现实”复选框，然后单击 + 图标，选择“Windows Mixed Reality”以添加 Windows Mixed Reality SDK   ：

![选中了“添加 Windows Mixed Reality SDK”的 Unity XR 设置](images/mr-learning-base/base-02-section5-step2-4.png)

Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。 如果未显示该窗口，可从 Unity 菜单手动将其打开，方法是转到“混合现实工具包” > “实用程序” > “配置 Unity 项目”

在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：

![选中了“添加 Windows Mixed Reality SDK”的 Unity XR 设置](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。 如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。 若要了解有关本主题的详细信息，请参阅<a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。

在“项目设置”窗口中，选择“播放器” > “XR 设置”，然后使用“深度格式”下拉列表选“16 位深度”   ：

![Unity 启用 16 深度](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> 可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。 若要了解有关此主题的更多信息，可以参考 MRTK 的<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">性能</a>文档的<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。

在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：

![配置了包名称的 Unity 发布设置](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> “包名称”是应用的唯一标识符。 在部署应用之前应更改此标识符，以免覆盖以前安装的应用。

> [!TIP]
> “产品名称”是在 HoloLens“开始”菜单中显示的名称。 要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。

## <a name="creating-and-configuring-the-scene"></a>创建和配置场景

在 Unity 菜单中，选择“文件” > “新建场景”，以创建新场景 ：

![Unity“新建场景”菜单路径](images/mr-learning-base/base-02-section6-step1-1.png)

在 Unity 菜单中，选择“混合现实工具包” > “添加到场景并配置…”，将 MRTK 添加到当前场景 ：

![Unity“添加到场景并配置...”菜单路径](images/mr-learning-base/base-02-section6-step1-2.png)

仍在“层次结构”窗口中选中 MixedRealityToolkit 对象，在“检查器”窗口中验证 MixedRealityToolkit 配置文件是否已设置为 DefaultMixedRealityToolkitConfigurationProfile  ：

![选中了 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-02-section6-step1-3.png)

在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口： 

![Unity“另存为...”菜单路径](images/mr-learning-base/base-02-section6-step1-4.png)

在“保存场景”窗口中，导航到项目的 **Scenes** 文件夹中，为场景提供一个合适的名称（例如“GettingStarted”），然后单击“保存”按钮以保存场景：

![Unity 保存场景“保存”提示窗口](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>将应用程序构建到 HoloLens 2

### <a name="1-build-the-unity-project"></a>1.生成 Unity 项目

在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口。 

在“生成设置”窗口中单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表，然后单击“生成”按钮以打开“生成通用 Windows 平台”窗口：

![选中了 UWP 的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section7-step1-1.png)

在“生成通用 Windows 平台”窗口中，选择用于存储生成的适当位置（例如 _D:\MixedRealityLearning\Builds_），创建一个新文件夹并为其指定适当的名称（例如 _GettingStarted_），然后单击“选择文件夹”按钮，启动生成过程：

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section7-step1-2.png)

等待 Unity 完成生成过程：

![Unity 正在生成进程](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.生成并部署应用程序

生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。 在文件夹内导航，然后双击解决方案文件，在 Visual Studio 中其打开：

![选中了“新建的 Visual Studio 解决方案”的 Windows 资源管理器](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> 如果 Visual Studio 要求安装新组件，请花一点时间确保拥有[安装工具](../../install-the-tools.md)文档中的所有必备组件。

通过选择“Master”配置或“发布”配置、ARM64 体系结构和“设备”作为目标，配置 Visual Studio for HoloLens   ：

![配置为部署到 HoloLens 2 的 Visual Studio](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> 如果要部署到 HoloLens（第一代），请选择 x86 体系结构。

> [!NOTE]
> 对于 HoloLens，通常是针对 ARM 体系结构进行生成。 但是，在 Unity 2019.3 中有一个 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知问题</strong></a>，即在 Visual Studio 中选择 ARM 作为生成体系结构时会导致错误。 建议的解决方法是针对 ARM64 进行生成。 如果该方法不可行，请前往“编辑”>“项目设置”>“播放器”>“其他设置”并禁用“图形作业” 。

> [!NOTE]
> 如果目标选项中没有“设备”，则可能需要将 Visual Studio 解决方案的启动项目从 IL2CPP 项目更改为 UWP 项目。 在“解决方案资源管理器”中，右键单击“YourProjectName (通用 Windows)”并选择“设为启动项目”。

将 HoloLens 连接到计算机，然后选择“调试” > “启动但不调试”，以生成并部署到你的设备 ：

![Visual Studio“启动(不调试)”菜单路径](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> 在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。 这两个步骤都可以按照[这些说明](../../platform-capabilities-and-apis/using-visual-studio.md)来完成。

> [!TIP]
> 你还可以部署到 [HoloLens 模拟器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)或创建[应用包](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)用于旁加载。

使用“启动但不调试”会自动启动设备上的应用，而不会连接 Visual Studio 调试器。

选择“生成”>“部署解决方案”，在不自动启动应用的情况下将内容部署到设备。

> [!NOTE]
>在应用中，你可能会注意到诊断探查器，可以使用语音命令“切换诊断”来切换其可见性。 我们建议你在开发过程中使探查器在大部分时间都可见，以便了解何时更改应用可能会影响性能。 例如，HoloLens 应用应以 [60 Fps 连续运行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。

## <a name="congratulations"></a>祝贺

现在，你已经部署了第一个 HoloLens 2 应用。 四处浏览一下，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。 这些只是 MRTK 附带的几个基础功能。 在接下来的教程中，我们将向场景添加内容，以探索 HoloLens 和 MRTK 的各种功能。

> [!div class="nextstepaction"]
> [下一教程：3.配置 MRTK 配置文件](mr-learning-base-03.md)
