---
title: MRTK 教程 - 2. 初始化项目并部署第一个应用程序
description: 本课程介绍如何配置 Unity 项目以使用混合现实工具包 (MRTK) 以及如何将其部署到 HoloLens 2。
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859526"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2.初始化项目并部署第一个应用程序

## <a name="overview"></a>概述

在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 开发，以及如何导入 MRTK。 你还将演练如何配置和生成基本 Unity 场景，并将其从 Visual Studio 部署到 HoloLens 2。 将其部署到 HoloLens 2 后，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。

## <a name="objectives"></a>目标

* 了解如何配置用于 HoloLens 开发的 Unity。
* 了解如何生成应用并将其部署到 HoloLens。
* 在 HoloLens 2 设备上体验空间映射网格、手部网格和帧率计数器。

## <a name="creating-the-unity-project"></a>创建 Unity 项目

1. 启动“Unity 中心”，选择“项目”选项卡，然后单击“新建”按钮旁边的向下箭头：   

![突出显示“新建”按钮的向下箭头的 Unity 中心](images/mr-learning-base/base-02-section1-step1-1.png)

2. 在下拉菜单中，选择[先决条件](mr-learning-base-01.md#prerequisites)中指定的 Unity 版本：

![选择 Unity 版本](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> 如果 Unity Hub 没有特定的 Unity 版本，可以从 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下载存档</a>启动安装。

3. 在“创建新项目”窗口中，执行以下操作：

    * 确保将“模板”设置为“3D” 。
    * 在“项目名称”框中，为项目输入一个合适的名称（例如“MRTK 教程”）。
    * 单击“位置”旁边的三点按钮，然后导航到要在其中保存项目的文件夹。

> [!CAUTION]
> 在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。 因此，应将 Unity 项目保存到驱动器的根目录附近。

    * 单击“创建”  按钮。 这将创建并启动新的 Unity 项目。

![Unity 中心，已填写其中的“创建新项目”窗口](images/mr-learning-base/base-02-section1-step1-3.png)

状态栏可让你了解最新进度。

![Unity 进度栏可让你了解“创建项目”的最新状态](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>切换生成平台

1. 在菜单栏上，选择“文件” > “生成设置…” 

![Unity“生成设置...”菜单路径](images/mr-learning-base/base-02-section2-step1-1.png)

2. 在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮：  

![选中了 UWP 要从 Standalone 切换平台的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section2-step1-2.png)

3. 等待 Unity 完成平台切换，然后关闭“生成设置”窗口。

## <a name="importing-the-textmeshpro-essential-resources"></a>导入 TextMeshPro 基本资源

MRTK 的 UI 元素需要 TextMeshPro 基本资源。 如果你不打算在项目中使用 MRTK 的 UI 元素，则可以跳过此步骤。

1. 在菜单栏上，选择“窗口” > “TextMeshPro” > “导入 TMP Pro 基本资源”  。

![Unity 导入 TMP 基本资源菜单路径](images/mr-learning-base/base-02-section3-step1-1.png)

2. 在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产  ：

![Unity TMP 基本资源导入窗口](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a>导入混合现实工具包

1. 下载 Unity 自定义包：

    [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. 在菜单栏上，选择“资产” > “导入包” > “自定义包…”  。
3. 在“导入包…”对话框中，导航到刚才下载的包所在的位置，选择该包，然后单击“打开”按钮 。
4. 在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产  。

## <a name="selecting-mrtk-and-project-settings"></a>选择 MRTK 和项目设置

Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。 如果未显示该窗口，请转到“混合现实工具包” > “实用程序” > “配置 Unity 项目”：

![Unity“配置 Unity 项目”菜单路径](images/mr-learning-base/base-02-section5-step1-1.png)

1. 在“MRTK 项目配置器”窗口中，展开“修改配置”部分（如果需要），确保选中所有选项 。

![显示了“修改配置”的 Unity“MRTK 项目配置器”窗口](images/mr-learning-base/base-02-section5-step1-2.png)

2. 要应用设置，请单击“应用”按钮。

![MRTK 中的“应用”按钮](images/mr-learning-base/apply.png)

> [!NOTE]
> 你使用的是 Unity 的内置旧版 XR 而不是新的 XR 插件系统，因为新系统与本系列教程中[推荐的 Unity 和 MRTK 版本](mr-learning-base-01.md#prerequisites)不完全兼容。 如果你看到任何关于即将弃用内置 XR 的警告，可以忽略它们。

> [!TIP]
> 可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：
>
> * 启用旧版 XR：为项目启用 VR。
> * 设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。 若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文档的[单通道实例化渲染](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)部分。
> * 设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。 若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。

3. 在菜单栏上，选择“编辑” > “项目设置…” 。

4. 在“项目设置”窗口中，选择“播放器”，单击“XR 设置”下拉列表，然后选中“支持的虚拟现实”旁边的框   ：

![显示了“支持虚拟现实”的 Unity“XR 设置”](images/mr-learning-base/base-02-section5-step2-2.png)

这会导入 Windows Mixed Reality SDK：

![显示了“Virtual Reality SDK”的 Unity“XR 设置”](images/mr-learning-base/mixed-reality-sdk.png)

Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。 如果未显示该窗口，请选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”，以将其打开  。

5. 在“MRTK 项目配置器”窗口中，单击“音频空间定位器”下拉列表，然后选择“MS HRTF 空间定位器”  。

![显示了“音频空间定位器”选项的“项目设置”](images/mr-learning-base/base-02-section5-step2-3.png)

6. 单击“应用”  按钮。 这将关闭“MRTK 项目配置器”窗口。

    > [!TIP]
    > 可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。 如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。 若要了解有关本主题的详细信息，请参阅空间音频教程。

7. 在“项目设置”窗口中，单击“深度格式”下拉列表，然后选择“16 位深度”：  

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="选中了“16 位深度”的 Unity“XR 设置”。":::

    > [!TIP]
    > 可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。 若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文档的[深度缓冲区共享 (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) 部分。

8. 单击“发布设置”下拉列表，然后在“包名称”框中输入合适的名称（例如“MRTK-Tutorials-Getting-Started”） 。

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="配置了“包名称”的 Unity“发布设置”。":::

    **包名称和产品名称**

    - “包名称”是应用的唯一标识符。 应在部署应用之前创建此标识符，以免覆盖以前安装的应用。
    - “产品名称”是在 HoloLens“开始”菜单中显示的名称。 为了更轻松地在开发期间查找应用，可以在名称前面添加一个下划线，以将其排在顶部。

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="已配置“产品名称”的 Unity“项目设置”。":::

9. 关闭“项目设置”窗口。

## <a name="creating-and-configuring-the-scene"></a>创建和配置场景

1. 在菜单栏中，选择“文件” > “新场景” 。
2. 要将 MRTK 添加到场景，请在菜单栏上选择“混合现实工具包” > “添加到场景并配置…” 。

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity“添加到场景并配置...”菜单路径。":::

3. 在“层次结构”窗口中，确保选中了“MixedRealityToolkit” 。

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="确保已选中“MixedRealityTookit”。":::

4. 在“检查器”窗口的“MixedRealityToolkit”部分中，验证配置文件是否设置为“DefaultMixedRealityToolkitConfigurationProfile”  ：

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="选中了“DefaultMixedRealityTookitConfigurationProfile”的 Unity MixedRealityToolkit 组件。":::

    > [!IMPORTANT]
    > 通常，在针对 HoloLens 进行开发时会使用 DefaultHoloLens2ConfigurationProfile。 但对于本教程，将使用 DefaultMixedRealityToolkitConfigurationProfile。 在下一个教程（[配置 MRTK 配置文件](mr-learning-base-03.md)）中，将改用 DefaultHoloLens2ConfigurationProfile。

5. 在菜单栏上，选择“文件” > “另存为…” 
6. 在“保存场景”对话框中，导航到项目的“场景”文件夹 。 在“文件名”框中，为场景指定一个合适的名称（例如“\_GettingStarted\_”），然后单击“保存”按钮 。

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Unity“保存场景”的“保存”提示窗口。":::

## <a name="building-and-deploying-to-your-hololens-2"></a>生成并部署到 HoloLens 2

> 在生成到设备之前，请确认以下事项：
- 设备处于开发人员模式。
- 设备已与开发计算机配对。 如果没有，则在生成过程中，Visual Studio 中会出现以下对话框：

![输入 PIN 以实现设备配对](images/mr-learning-base/pin-request.png)

 要了解有关这两个步骤的详细信息，请参阅[使用 Visual Studio 进行部署和调试](../../platform-capabilities-and-apis/using-visual-studio.md)。

1. 在菜单栏上，选择“文件” > “生成设置…” 。
2. 在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表中  。

![将当前场景添加“生成中的场景”列表](images/mr-learning-base/base-02-section7-step1-1.png)

3. 单击“**生成**”按钮。

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="单击“生成”按钮。":::

4. 在“生成通用 Windows 平台”对话框中，选择一个合适的位置来存储生成（例如，你可能希望在“MRTK 教程”文件夹中创建一个“生成”文件夹）。 创建一个新文件夹并为其提供一个合适的名称（例如“GettingStarted”），选择该文件夹，然后单击“选择文件夹”按钮启动生成过程。

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="显示生成文件夹的 Unity 生成窗口。":::

    此时会显示一个状态栏，可让你了解最新生成进度。

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Unity 生成过程正在进行中。":::

    > [!TIP]
    > 你还可以部署到 [HoloLens 模拟器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)或创建[应用包](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)用于旁加载。

5. 生成过程完成后，在文件资源管理器中导航到存储生成的位置，然后双击解决方案文件以在 Visual Studio 中打开它：

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="选中了新建的 Visual Studio 解决方案文件的 Windows 资源管理器。":::

    > [!NOTE]
    > 如果 Visual Studio 要求安装新组件，请花一点时间确保拥有[安装工具](../../install-the-tools.md)文档中的所有必备组件。

6. 通过选择“Master”配置或“发布”配置、ARM64 体系结构和“设备”作为目标，配置 Visual Studio for HoloLens   。

    > [!TIP]
    > 如果要部署到 HoloLens（第一代），请选择 x86 体系结构。

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="配置为部署到 HoloLens 2 的 Visual Studio。":::

    > [!NOTE]
    > 对于 HoloLens，通常是针对 ARM 体系结构进行生成。 但是，在 Unity 2019.3 中有一个 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知问题</strong></a>，即在 Visual Studio 中选择 ARM 作为生成体系结构时会导致错误。 建议的解决方法是针对 ARM64 进行生成。 如果该方法不可行，请前往“编辑”>“项目设置”>“播放器”>“其他设置”并禁用“图形作业” 。

    > [!NOTE]
    > 如果目标选项中没有“设备”，则可能需要将 Visual Studio 解决方案的启动项目从 IL2CPP 项目更改为 UWP 项目。 为此，请在“解决方案资源管理器”中右键单击“YourProjectName (通用 Windows)”，然后选择“设为启动项目”。

7. 将 HoloLens 连接到计算机，然后执行以下操作之一：
- 要生成应用，请将其部署到 HoloLens，并在不附加 Visual Studio 调试器的情况下自动启动它，在菜单栏上，选择“调试” > “启动但不调试” 。

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Visual Studio“启动但不调试”的菜单路径。":::

- 要生成应用并将其部署到 HoloLens，但不自动启动该应用，请在菜单栏上选择“生成”>“部署解决方案”。

    > [!NOTE]
    >在应用中，你可能会注意到诊断探查器，可以使用语音命令“切换诊断”来切换其可见性。 我们建议你在开发过程中使探查器在大部分时间都可见，以便了解何时更改应用可能会影响性能。 例如，HoloLens 应用应以 [60 Fps 连续运行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。

## <a name="congratulations"></a>祝贺

现在，你已经部署了第一个 HoloLens 2 应用。 四处浏览一下，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。 此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。 这些只是 MRTK 附带的几个基础功能。 在接下来的教程中，我们将向场景添加内容，以探索 HoloLens 和 MRTK 的各种功能。

> [!div class="nextstepaction"]
> [下一教程：3.配置 MRTK 配置文件](mr-learning-base-03.md)
