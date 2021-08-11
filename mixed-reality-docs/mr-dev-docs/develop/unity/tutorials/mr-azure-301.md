---
title: HoloLens（第一代）和 Azure 301 - 语言翻译
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure 文本翻译 API。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，学院，unity，教程，api，translator 文本，hololens，沉浸，vr，语言翻译，Windows 10，Visual Studio
ms.openlocfilehash: 8eeeab45c6e7d93c1b04afa4db811f220b0c2f9c85400fc93a81ac413164a6b7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115229470"
---
# <a name="hololens-1st-gen-and-azure-301-language-translation"></a>HoloLens (第一代) 和 Azure 301：语言翻译

<br>

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

在本课程中，你将学习如何使用 Azure 认知服务将翻译功能添加到混合现实应用程序，并提供文本翻译 API。

![最终产品](images/AzureLabs-Lab1-00.png)

文本翻译 API 是一项近乎实时的翻译服务。 该服务是基于云的，并且使用 REST API 调用，应用程序可以使用神经计算机翻译技术将文本转换为其他语言。 有关详细信息，请访问[Azure 文本翻译 API 页](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。

完成本课程后，你将拥有一个混合现实应用程序，该应用程序将能够执行以下操作：

1.  用户会说到连接到沉浸式 (VR) 耳机 (或 HoloLens) 内置麦克风的麦克风。
2.  此应用将捕获听写，并将其发送到 Azure 文本翻译 API。
3.  翻译结果将显示在 Unity 场景中的一个简单 UI 组中。

本课程将介绍如何将翻译工具服务的结果获取到基于 Unity 的示例应用程序。 您可以将这些概念应用到您可能生成的自定义应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 301：语言翻译</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要重点介绍 Windows Mixed Reality 沉浸式 (VR) 耳机，您也可以将您在本课程中学到的内容应用到 Microsoft HoloLens。 在本课程中，你将看到有关支持 HoloLens 所需的任何更改的说明。 使用 HoloLens 时，可能会在语音捕获过程中注意到某些回声。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为具有 Unity 和 c # 基本经验的开发人员设计。 请注意，本文档中的先决条件和书面说明表明了编写 (2018) 时测试和验证的内容。 您可以随意使用最新的软件（如 [安装工具](../../install-the-tools.md) 一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件：

- 与沉浸式 (VR) 耳机开发[Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC
- [启用开发人员模式 Windows 10 Fall Creators Update (或更高版本) ](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017。4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- 启用开发人员模式[Windows Mixed Reality 沉浸式 (VR) 耳机](../../../discover/immersive-headset-hardware-details.md)或[Microsoft HoloLens](/hololens/hololens1-hardware)
- 带有内置麦克风的一组耳机 (如果耳机没有内置麦克风和扬声器) 
- Azure 安装和翻译检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

- 若要避免在生成此项目时遇到问题，强烈建议你在根或近乎根文件夹中创建本教程中所述的项目 (长文件夹路径在生成时) 会导致问题。
- 本教程中的代码允许您从连接到您的 PC 的默认麦克风设备进行录制。 请确保将默认麦克风设备设置为计划用于捕获语音的设备。
- 若要允许你的电脑启用听写，请转到 **设置 > 的隐私 > 语音，墨迹书写 & 键入内容**，然后选择 "**打开语音服务并键入建议**" 按钮。
- 如果使用连接到 (或内置的麦克风和耳机来) 耳机，请确保在 **设置 > 混合现实 > 音频和语音** 中启用 "当我戴上耳机时，切换到耳机麦克风" 选项。

   ![混合现实设置](images/AzureLabs-Lab1-00-5.png)

   ![麦克风设置](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> 请注意，如果你要为此实验室开发沉浸式耳机，你可能会遇到音频输出设备问题。 这是由 Unity 中的问题导致的，该问题在 (Unity 2018.2) 的 Unity 的更高版本中已修复。 此问题可防止 Unity 在运行时更改默认音频输出设备。 作为解决方法，请确保已完成上述步骤，并在此问题自行显示时关闭并重新打开编辑器。

## <a name="chapter-1--the-azure-portal"></a>第1章-Azure 门户

若要使用 Azure 翻译工具 API，你将需要配置服务的实例，使其可用于你的应用程序。

1.  登录到  [Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。

2.  登录后，单击左上角的 "**新建**"，搜索 "文本翻译 API"。 选择 **Enter**。

    ![新建资源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 在较新的门户中，可能已将 " **新建** " 一词替换为 " **创建资源**"。

3.  新页将提供 *文本翻译 API* 服务的说明。 在此页的左下角，选择 " **创建** " 按钮以创建与此服务的关联。

    ![创建文本翻译 API 服务](images/AzureLabs-Lab1-03.png)

4.  单击 " **创建**" 后：

    1. 为此服务实例插入所需的 **名称** 。
    2. 选择相应的 **订阅**。
    3. 选择适合于你的 **定价层**，如果这是第一次创建 *文本翻译服务*，则 (名为 F0) 的免费层。
    4. 选择一个 **资源组** ，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议保留与单个项目关联的所有 Azure 服务 (例如，这些实验室) 在常见资源组) 下。

        > 若要了解有关 Azure 资源组的详细信息，请 [访问资源组一文](/azure/azure-resource-manager/resource-group-portal)。

    5. 如果要创建新的资源组) ，请确定资源组 (的 **位置** 。 此位置理想情况下会在应用程序运行所在的区域中。 某些 Azure 资产仅在特定区域提供。
    6. 还需要确认是否已了解应用于此服务的条款和条件。
    7. 选择“创建”。 

        ![选择 "创建" 按钮。](images/AzureLabs-Lab1-04.png)

5.  单击 " **创建**" 后，需要等待创建服务，这可能需要一分钟时间。
6.  创建服务实例后，门户中将显示一个通知。 

    ![Azure 服务创建通知](images/AzureLabs-Lab1-05.png)

7.  单击通知以浏览新服务实例。 

    ![中转到资源弹出。](images/AzureLabs-Lab1-06.png)

8.  单击通知中的 " **中转到资源** " 按钮以浏览新服务实例。 你将转到新的文本翻译 API 服务实例。 

    ![翻译工具文本 API 服务页](images/AzureLabs-Lab1-07.png)

9.  在本教程中，你的应用程序将需要调用你的服务，这是通过使用你的服务的订阅密钥来完成的。 
10. 在你的 *文本翻译* 服务的 "*快速启动*" 页上，导航到第一步，*获取你的密钥*，然后单击 "**密钥**" (你还可以通过单击 "服务" 导航菜单中的 "蓝色" 超链接项（位于 "服务" 导航菜单中，由键图标) 表示）来实现此目的 这会显示你的服务 *密钥*。
11. 复制其中一个所显示的密钥，因为稍后会在项目中使用此密钥。 

## <a name="chapter-2--set-up-the-unity-project"></a>第2章–设置 Unity 项目

设置并测试混合现实沉浸式耳机。

> [!NOTE]
> 本课程不需要移动控制器。 如果需要支持设置沉浸式耳机，请 [遵循以下步骤](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

下面是使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板：

1.  打开 *Unity* ，并单击 " **新建**"。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab1-08.png)

2.  现在需要提供 Unity Project名称。 插入 **MR_Translation**。 确保项目类型设置为 **3D**。 将" *位置* "设置为适合你记住 (，越靠近根目录越好) 。 然后单击"创建 **项目"。**

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab1-09.png)

3.  打开 Unity 后，值得检查 **默认脚本编辑器** 是否设置为 **Visual Studio。** 转到"**编辑>首选项"，** 然后在新窗口中导航到"**外部工具"。** 将 **"外部脚本编辑器"****更改为 Visual Studio 2017。** 关闭 **"首选项"** 窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab1-10.png)

4.  接下来，单击 **"切换>"设置"，** 转到"文件"Windows"平台"，将平台切换到"**通用平台**"。

    ![生成设置窗口，将平台切换到 UWP。](images/AzureLabs-Lab1-11.png)

5.  转到"**文件>生成设置** 并确保：

    1. **目标设备** 设置为"任何 **设备"。**

        > 对于Microsoft HoloLens，将 **"目标设备"** 设置为 *HoloLens。*

    2. **生成类型** 设置为 **D3D**
    3. **SDK** 设置为"最新 **安装"**
    4. **Visual Studio版本** 设置为"最新 **安装"**
    5. **"生成和运行** "设置为" **本地计算机"**
    6. 保存场景并将其添加到生成。

        1. 为此，选择"**添加打开的场景"。** 将显示保存窗口。

            ![单击"添加打开的场景"按钮](images/AzureLabs-Lab1-12.png)

        2. 为此和任何将来的场景创建新文件夹，然后选择"新建文件夹"按钮，以创建新文件夹，将其命名为 **"场景"。**

            ![创建新脚本文件夹](images/AzureLabs-Lab1-13.png)

        3. 打开新创建的 **"场景**"文件夹，然后在"文件名 *：* 文本"字段中，键入"MR_TranslationScene"，**然后** 按"**保存"。**

            ![为新场景命名。](images/AzureLabs-Lab1-14.png)

            > 请注意，必须将 Unity 场景保存在 *Assets* 文件夹中，因为它们必须与 Unity Project。 创建场景文件夹 (和其他类似文件夹) 是构建 Unity 项目的典型方法。

    7. 目前，"*生成设置中的* 其余设置应保留为默认值。

6. 在"*生成设置* 窗口中，单击"播放器设置按钮，这将在 *检查* 器所在的空间中打开相关面板。 

    ![打开播放器设置。](images/AzureLabs-Lab1-15.png)

7. 在此面板中，需要验证一些设置：

    1. 在"**其他设置** 选项卡中：

        1. **脚本运行时版本****应稳定**（A0.NET 3.5 等效) 。
        2. **脚本后端应为** **.NET**
        3. **API 兼容性级别** 应为 **.NET 4.6**

            ![更新其他设置。](images/AzureLabs-Lab1-16.png)
      
    2. 在"**发布设置** 选项卡中的"**功能"下**，选中：

        1. **InternetClient**
        2. **麦克风**

            ![更新发布设置。](images/AzureLabs-Lab1-17.png)

    3. 在面板的下方，在"发布 设置) "下找到的 **"XR** 设置 ("中，勾选"支持虚拟现实"，确保Windows Mixed Reality **SDK。** 

        ![更新 X R 设置。](images/AzureLabs-Lab1-18.png)

8.  返回到生成 **设置，Unity** *C#* 项目不再灰暗;勾选此 旁边的复选框。 
9.  关闭“生成设置”窗口。
10. 保存场景和Project (**文件>保存场景/文件>保存项目**) 。

## <a name="chapter-3--main-camera-setup"></a>第 3 章 - 主相机设置

> [!IMPORTANT]
> 如果要跳过本课程 *的 Unity 设置* 组件，并直接继续编写代码，请随意下载 [此 .unitypackage，](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)将其作为自定义包导入到项目中，然后继续学习 [](https://docs.unity3d.com/Manual/AssetPackages.html)第 [5](#chapter-5--create-the-results-class)章 。 你仍然需要创建 Unity Project。

1.  在 *"层次结构面板*"中，你将找到一个称为"主相机"的对象，一旦"进入"应用程序，此对象表示你的"头部"视点。
2.  在 Unity 仪表板的前面，选择"**主相机 GameObject"。** 你会注意到，检查 (面板通常位于右侧，仪表板) 内将显示 *该 GameObject* 的各种组件，其中 *"* 转换"位于顶部，后跟"相机"和一些其他组件。  需要重置主相机的转换，以便正确定位。
3.  为此，请选择相机的 **"转换**"组件旁边的 *齿轮图标，* 然后选择"重置 **"。** 

    ![重置主相机转换。](images/AzureLabs-Lab1-19.png)
 
4.  转换 *组件* 应如下所示：

    1. 位置 *设置为* **0、0、0**
    2. *旋转* 设置为 **0、0、0**
    3. Scale 设置为 **1、1、1**

        ![相机的转换信息](images/AzureLabs-Lab1-20.png)

5.  接下来，选中 **"主相机"** 对象后，请参阅"检查器面板"最底部的"添加 *组件"按钮*。 
6.  选择该按钮，然后 (搜索字段中键入"音频源"，或导航名为"音频源"的组件的) 部分，然后选择它， (按 Enter 也可以) 。
7.  音频 *源* 组件将添加到 **主相机**，如下所示。

    ![添加音频源组件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > 对于Microsoft HoloLens，还需要更改以下各项，这些组件是主相机上的 **Camera** 组件的 **一部分**：
    > - **清除标志：** 纯色。
    > - **背景** "Black， Alpha 0"– 十六进制颜色：#00000000。

## <a name="chapter-4--setup-debug-canvas"></a>第 4 章 - 设置调试画布

若要显示翻译的输入和输出，需要创建基本 UI。 对于本课程，你将创建一个 Canvas UI 对象，其中有几个"Text"对象用于显示数据。

1.  右键单击"层次结构面板"的空白 *区域*，在 **UI** 下添加 **"画布"。**

    ![添加新的 Canvas UI 对象。](images/AzureLabs-Lab1-22.png)

2.  选中 Canvas 对象后，在"Canvas"组件 (面板中，将) **模式更改为****"世界空间"。** 
3.  接下来，在检查器面板的矩形 *转换中更改以下参数*：

    1. *POS*  -  **X** 0 **Y** 0 **Z** 40
    2. *宽度* - 500
    3. *高度* - 300
    4. *缩放*  - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![更新画布的矩形转换。](images/AzureLabs-Lab1-23.png)
 
4.  右键单击"**层次结构面板**"中的 *"画布"，* 在 **UI** 下添加"面板 **"。** 此 **面板** 将提供将在场景中显示的文本的背景。
5.  右键 **单击"层次结构** 面板"中的 *"面板"，* 在 **UI** 下添加 **文本对象**。 重复相同的过程，直到总共创建了四个 UI 文本对象 (提示：如果选择了第一个"Text"对象，只需按 **"Ctrl"+ "D"** 进行复制，直到总共创建了四个) 。 
6.  对于每个 **文本对象**，请选择它，然后使用以下表在检查器面板 中 *设置参数*。

    1. 对于 *矩形转换* 组件：

        | 名称                   | 转换 - *位置*             | 宽度      | 高度    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. 对于 **"文本 (脚本)** 组件：


        | 名称                   | 文本               | 字号    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | 麦克风状态： | 20           |
        | AzureResponseLabel     | Azure Web 响应 | 20           |
        | DictationLabel         |   刚才说：   | 20           |
        | TranslationResultLabel |    翻译：    | 20           |

        ![输入 UI 标签的相应值。](images/AzureLabs-Lab1-24.png)

    3. 此外，将字体样式加 **粗**。 这会使文本更易于阅读。

        ![粗体字体。](images/AzureLabs-Lab1-25.png)

7.  对于在第 [5](#chapter-5--create-the-results-class)*章* 中创建的每个 UI 文本对象，*创建新的子***UI 文本对象**。 这些子对象将显示应用程序的输出。 通过 *右* 键单击预期的父对象（ (*如 MicrophoneStatusLabel*) ，然后选择 **"UI"，** 然后选择"文本"来创建 **子对象**。
8.  对于其中每个子项，请选择它并使用下表在检查器面板中设置参数。

    1. 对于 **矩形转换** 组件：

        | 名称                  | 转换 - *位置* | 宽度      | 高度    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. 对于 **"文本 (脚本)** 组件：

        | 名称                  | 文本          | 字号    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 接下来，选择每个文本组件的"中心"对齐选项：

    ![对齐文本。](images/AzureLabs-Lab1-26.png)

10. 若要确保子 **UI 文本** 对象易于阅读，请更改其 *颜色*。 为此，单击"颜色" ("旁边的) "黑色 *"图标*。 

    ![输入 UI 文本输出的相应值。](images/AzureLabs-Lab1-27.png)
 
11. 然后，在新的"小颜色" *窗口中，* 将 *"十六进制颜色* "更改为 **：0032EAFF**

    ![将颜色更新为蓝色。](images/AzureLabs-Lab1-28.png)
 
12. 下面是 UI **的外观** 。
    1.  在" *层次结构面板"中*：

        ![在提供的 结构中具有层次结构。](images/AzureLabs-Lab1-29.png)

    2.  在 *场景和**游戏视图中*：

        ![使场景和游戏视图具有相同的结构。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>第 5 章 - 创建 Results 类

需要创建的第一个脚本是 *Results* 类，该类负责提供查看翻译结果的方法。 类存储和显示以下内容： 

- 来自 Azure 的响应结果。
- 麦克风状态。 
- 听写结果 (语音到文本) 。
- 翻译的结果。

若要创建此类，请： 

1.  右键单击 *"Project"，* 然后单击"**创建>文件夹"。** 将 **文件夹命名脚本**。 
 
    ![创建 scripts 文件夹。](images/AzureLabs-Lab1-31.png)

    ![打开 scripts 文件夹。](images/AzureLabs-Lab1-32.png)
 
2.  创建 **Scripts** 文件夹后，双击它以打开它。 然后，在此文件夹中，右键单击并选择"创建 **>"C# 脚本"。** 将 *脚本命名结果*。 

    ![创建第一个脚本。](images/AzureLabs-Lab1-33.png)
 
3.  双击新的"结果 *"* 脚本，使用 **Visual Studio。**
4.  插入以下命名空间：

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  在 类中插入以下变量：

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  然后添加 *"唤醒 ()* 方法，该方法将在类初始化时调用。 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  最后，添加负责将各种结果信息输出到 UI 的方法。 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  在返回到 Unity 之前，请确保Visual Studio中的 *更改*。

## <a name="chapter-6--create-the-microphonemanager-class"></a>第 6 章 - 创建 *MicrophoneManager* 类

要创建的第二个类是 *MicrophoneManager*。

此类负责：

- 检测连接到头戴显示设备或计算机设备的 (默认设备) 。
- 捕获语音 (语音) 听写以字符串形式存储。
- 语音暂停后，将听写提交到 翻译工具 类。
- 托管一个方法，该方法可停止语音捕获（如果需要）。

若要创建此类，请： 
1.  双击"脚本 **"** 文件夹，打开它。 
2.  在"脚本"文件夹中 **右键** 单击，单击 **"> C# 脚本"。** 将脚本 *"MicrophoneManager"命名*。 
3.  双击新脚本，以使用 Visual Studio。
4.  在 *MicrophoneManager* 类的顶部，将命名空间更新为与以下内容相同：

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  然后，在 *MicrophoneManager 类中添加以下* 变量：

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  现在需要添加 *()**唤醒* () 启动方法的代码。 当 类初始化时，将调用这些 ：

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  可以 *删除* *Update ()* 方法，因为此类不会使用它。
8.  现在，需要应用用于启动和停止语音捕获的方法，并传递给翻译工具类（即将生成）。  复制以下代码并将其粘贴到 Start *()* 下。

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > 尽管此应用程序不会使用它，但如果你希望实现在应用程序中停止捕获音频的能力，此处也提供了 *StopCapturingAudio ()* 方法。

9.  现在需要添加一个听写处理程序，该处理程序将在语音停止时调用。 然后，此方法将指定文本传递给 翻译工具 *类。*

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. 在返回到 Unity 之前，请确保Visual Studio中的更改。

> [!WARNING]  
> 此时，你会注意到 Unity 编辑器控制台面板中出现一个错误 ("名称'翻译工具'不存在...") 。 这是因为代码引用了翻译工具类，将在下一章创建该类。

## <a name="chapter-7--call-to-azure-and-translator-service"></a>第 7 章 - 调用 Azure 和翻译器服务

需要创建的最后一个脚本是 *翻译工具* 类。 

此类负责：

-   使用 Azure 对 *应用进行身份验证*，以交换 **身份验证令牌**。
-   使用 **身份验证令牌提交** 从 (*MicrophoneManager* 类收到的文本) 文本。
-   接收转换后的结果，并将其传递给 *结果* 类，以在 UI 中可视化。

若要创建此类，请： 
1.  转到之前 **创建的 Scripts** 文件夹。 
2.  右键单击"Project **面板**，**创建> C# 脚本"。** 调用 脚本 *翻译工具。*
3.  双击新的 翻译工具 *脚本，* 以使用 **Visual Studio。**
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  然后将以下变量添加到 翻译工具 *类中*：

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - 插入到语言枚举的语言 **只是** 示例。 如果需要，可以随意添加更多内容; [API 支持 60 多种语言](/azure/cognitive-services/translator/languages) ， (Klingon) ！
    > - 有一 [个](https://www.microsoft.com/translator/business/languages/)涵盖可用语言的更具交互性的页面，但请注意，只有当站点语言设置为""时，该页面才 (并且 Microsoft 站点可能会重定向到你的本机语言) 。 可以在页面底部更改站点语言，也可以更改 URL。
    > - 上述代码片段中的 **authorizationKey** 值必须是订阅 Azure文本 API 时收到的翻译工具 *密钥*。 第 [1 章中介绍了这一点](#chapter-1--the-azure-portal)。

6.  现在需要添加 *()**唤醒* () 启动方法的代码。 
7.  在这种情况下，代码会使用授权密钥调用 *Azure，**获取令牌*。

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > 令牌将在 10 分钟后过期。 根据应用的情况，可能需要多次进行相同的协同例程调用。

8.  用于获取令牌的协同例程如下所示：

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > 如果编辑 IEnumerator 方法 **GetTokenCoroutine ()** 的名称，则需要更新上述代码中 *的 StartCoroutine* 和 *StopCoroutine* 调用字符串值。 [根据 Unity 文档](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)，若要停止特定的 *协同例程*，需要使用字符串值方法。

9.  接下来，使用 ("支持"流方法添加协同例程) 以获取 *MicrophoneManager* 类收到的文本的翻译。 此代码创建一个查询字符串以发送到 *Azure 翻译工具 文本 API，* 然后使用内部 UnityWebRequest 类通过查询字符串对终结点进行"Get"调用。 然后，使用结果在 Results 对象中设置翻译。 下面的代码演示了实现：

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. 在返回到 Unity 之前，请确保Visual Studio中的 *更改*。

## <a name="chapter-8--configure-the-unity-scene"></a>第 8 章 - 配置 Unity 场景

1.  返回到 Unity 编辑器中，单击"结果"类，并将其从 **"** 脚本"文件夹拖动到"层次结构面板"*中的"主相机"对象*。
2.  单击主 **相机并** 查看检查 *器面板*。 你会注意到，在新添加的 *脚本* 组件中，有四个字段具有空值。 这些是对代码中属性的输出引用。 
3.  将相应的 **"文本** "对象从"层次结构 *面板* "拖动到这四个槽，如下图所示。

    ![使用指定的值更新目标引用。](images/AzureLabs-Lab1-34.png)
  
4.  接下来，单击"翻译工具"类，并将其从 **"** 脚本"文件夹拖动到"层次结构面板"*中的"主相机"对象*。 
5.  然后，单击 *"MicrophoneManager"* 类，并将其从 **"脚本**"文件夹拖动到"层次结构面板 *"中的"主相机"对象*。 
6.  最后，单击主 **相机** 并查看检查 *器面板*。 你会注意到，在拖动的脚本中，有两个下拉框允许你设置语言。
 
    ![确保输入预期的翻译语言。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>第 9 章 - 在混合现实中测试

此时，需要测试场景是否已正确实现。

请确保：

- 第 [1 章中提到的所有](#chapter-1--the-azure-portal) 设置均正确设置。 
- 结果 *、翻译工具* 和 *MicrophoneManager* 脚本将附加到 **Main Camera** 对象。  
- 你已将 *Azure 翻译工具 文本 API* 服务 **密钥** 放置在脚本中的 **authorizationKey** *翻译工具* 中。  
- 主相机检查 *器面板中* 的所有字段都分配正确。
- 运行场景时，麦克风 (，请检查附加的麦克风是默认设备，以及是否已正确设置Windows) 。  [](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)

可以通过在 Unity 编辑器中按"播放 **"** 按钮来测试沉浸式 *头戴显示设备*。
应用应通过附加的沉浸式头戴显示设备正常运行。

> [!WARNING]  
> 如果在 Unity 控制台中看到有关默认音频设备更改的错误，则场景可能无法正常运行。 这是因为混合现实门户为具有麦克风的头戴显示设备处理内置麦克风的方式。 如果看到此错误，只需停止场景并再次启动它，一切应如预期工作。

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>第 10 章 - 在本地计算机上生成 UWP 解决方案和旁加载

此项目的 Unity 部分所需的一切现已完成，因此现在可以从 Unity 生成它。

1.  导航到 **"生成设置：****文件>生成设置...**
2.  在"生成 **设置** 窗口中，单击"生成 **"。**

    ![生成 Unity 场景。](images/AzureLabs-Lab1-36.png)
  
3.  如果尚未选中，请勾选 **"Unity C# 项目"。**
4.  单击“生成”。 Unity 将启动 *文件资源管理器* 窗口，你需要创建该窗口，然后选择要生成应用的文件夹。 现在创建该文件夹，并命名"应用 *"。* 然后选择"*应用"文件夹* 后，按"**选择文件夹"。** 
5.  Unity 将开始将项目生成到 *"应用"* 文件夹。 
6.  Unity 完成生成 (可能需要一些时间) ，它会在生成位置打开 *文件资源管理器* 窗口 (检查任务栏，因为它可能不会始终显示在窗口上方，但会通知你新窗口) 。

## <a name="chapter-11--deploy-your-application"></a>第 11 章 - 部署应用程序

部署应用程序：

1.  导航到"应用"文件夹 (*新的* Unity) ，然后使用 Visual Studio 打开 *解决方案文件*。
2.  在"解决方案配置"中，选择"**调试"。**
3.  在"解决方案平台"中，选择 **"x86，****本地计算机"。** 

    > 对于Microsoft HoloLens，你可能会发现，将此选项设置为"远程计算机"会更容易，这样一来，你将不会与计算机连接。 不过，还需要执行以下操作：
    > - 了解 **虚拟网络的 IP** 地址HoloLens，该地址位于 设置 > Network *& Internet > Wi-Fi >高级选项中*;IPv4 是应该使用的地址。 
    > - 确保 *"开发人员模式"* 为 **"打开";** 在开发人员 *设置 >更新&安全>中。*

    ![从部署解决方案Visual Studio。](images/AzureLabs-Lab1-37.png)
    
 
4.  转到" **生成"菜单** ，然后单击" **部署解决方案** "，将应用程序旁加载到电脑。
5.  应用现在应显示在已安装的应用列表中，并准备好启动。
6.  启动后，应用将提示你授权访问麦克风。 请确保单击"是 **"** 按钮。
7.  现在可以开始翻译了！

## <a name="your-finished-translation-text-api-application"></a>已完成的翻译文本 API 应用程序

恭喜，你构建了一个混合现实应用，该应用利用 Azure 翻译文本 API 将语音转换为翻译的文本。

![最终产品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises&quot;></a>额外练习

### <a name=&quot;exercise-1&quot;></a>练习 1

能否将文本到语音功能添加到应用，以便说出返回的文本？

### <a name=&quot;exercise-2&quot;></a>练习 2

让用户可以在应用本身内将源和输出语言 (&quot;from&quot;和&quot;to") ，因此无需每次更改语言时都重新生成应用。