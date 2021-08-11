---
title: 'HoloLens (第一代) Azure 303 - LUIS (自然) '
description: 完成本课程，了解如何在混合现实应用程序中语言理解 LUIS (Azure) 智能服务。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure， 混合现实， 学院， unity， 教程， api， 语言理解智能服务， luis， hololens， 沉浸式， vr， Windows 10， Visual Studio
ms.openlocfilehash: 443b5f2c186fbbb0a3e979b48ccc20b4c3d3b4f0bd9c93950e27e1f86d610c07
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217962"
---
# <a name="hololens-1st-gen-and-azure-303-natural-language-understanding-luis"></a>HoloLens (第一代) 和 Azure 303：LUIS (自然) 

<br>

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来将发布一系列新的教程，演示如何针对 HoloLens 2。  发布这些教程时，此通知将更新为指向这些教程的链接。

<br>

本课程将学习如何使用 语言理解 API 将 Azure 认知服务 集成到混合现实语言理解应用程序中。

![实验室结果](images/AzureLabs-Lab3-000.png)

*语言理解 (LUIS)* 是一种Microsoft Azure服务，它使应用程序能够使用用户输入来表达含义，例如，通过提取用户可能想要用自己的语言表达的含义。 这是通过机器学习实现的，机器学习了解和了解输入信息，然后可以使用详细、相关的信息进行回复。 有关详细信息，请访问 Azure [语言理解 (LUIS) 页](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。

完成本课程后，你将拥有一个混合现实沉浸式头戴显示设备应用程序，该应用程序能够执行以下操作：

1.  使用附加到沉浸式头戴显示设备麦克风捕获用户输入语音。 
2.  将捕获的听写发送到 LUIS 语言理解 *Azure* (*服务*) 。 
3.  让 LUIS 从发送信息中提取含义，这些信息将进行分析，并尝试确定将发出用户请求的意图。

开发将包括创建一个应用，用户可以使用语音和/或凝视来更改场景中对象的大小和颜色。 不会涵盖运动控制器的使用。

在应用程序中，由你决定如何将结果与设计集成。 本课程旨在教授如何将 Azure 服务与 Unity Project。 你的工作是利用从本课程中获得的知识来增强混合现实应用程序。

准备多次训练 LUIS，第 [12 章中介绍了这一点](#chapter-12--improving-your-luis-service)。 LUIS 训练次数越多，结果就越好。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 和 Azure 303：LUIS (的自然语言) </td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 虽然本课程主要重点介绍Windows Mixed Reality VR () 头戴显示设备，但也可以将本课程中学习到Microsoft HoloLens。 随着课程的进行，你将看到有关支持此课程可能需要采用的任何更改HoloLens。 使用语音HoloLens，你可能会注意到在语音捕获期间有一些回显。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为具有 Unity 和 C# 基本经验的开发人员设计。 另请注意，本文档中的先决条件和书面说明表示截至 2018 年 5 月 2018 年 5 月 (测试和验证的内容) 。 可以随意使用安装工具一文中列出的最新软件，但不应[](../../install-the-tools.md)假定本课程中的信息与下面列出的新软件中的信息完全匹配。

对于本课程，我们建议使用以下硬件和软件：

- 一台开发电脑[，Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 头戴显示设备开发
- [Windows 10 Fall Creators Update (开发人员模式) 或更高版本](../../install-the-tools.md)
- [最新的 Windows 10 SDK](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- 已启用[Windows Mixed Reality开发人员模式 (VR](../../../discover/immersive-headset-hardware-details.md)) 头戴显示设备[Microsoft HoloLens](/hololens/hololens1-hardware)沉浸式设备
- 一组带内置麦克风的耳机 (如果头戴显示设备没有内置麦克风和扬声器，) 
- 用于 Azure 设置和 LUIS 检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

1.  为了避免在生成此项目时遇到问题，强烈建议在根文件夹或近根文件夹中创建本教程中提到的项目 (长文件夹路径可能会导致生成时) 。 
2.  若要允许计算机启用听写，请转到 Windows 设置 > Privacy **> Speech， Inking & Typing，** 然后按按钮"打开语音服务并键入 **建议**"。
3.  本教程中的代码允许你从计算机上设置的默认 **麦克风** 设备进行录制。 请确保将"默认麦克风设备"设置为想要用于捕获语音的设备。
4.  如果头戴显示设备具有内置麦克风，请确保在设备设置中启用"当我戴头戴显示设备时，切换到头戴 *显示* 设备麦克风 *混合现实门户"* 。

    ![设置沉浸式头戴显示设备](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>第 1 章 - 设置 Azure 门户

若要在 Azure *语言理解* 服务，需要将服务的实例配置为可供应用程序使用。

1.  登录到 [Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室环境中遵循本教程，请询问讲师或其中一位讲师，以帮助设置新帐户。

2.  登录后，单击左上角的"新建"，然后搜索 *语言理解，然后单击*  **Enter**。 

    ![创建 LUIS 资源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > 在较 **新的** 门户中，"新建"一词可能已被替换为"创建资源"。
 
3.  右侧新页面将提供服务语言理解说明。 在此页左下角， **选择"创建** "按钮，创建此服务的实例。

    ![LUIS 服务创建 - 法律声明](images/AzureLabs-Lab3-02.png)
 
4.  单击"创建"后：

    1. 为此服务 **实例插入** 所需的名称。
    2. 选择一个“订阅”  。
    3. 选择 **适合你的** 定价层，如果这是首次创建 *LUIS* 服务， (名为 F0) 的免费层。 免费分配应足以满足本课程。
    4. 选择一 **个资源组** 或创建一个新资源组。 资源组提供了一种方法来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将与单个项目关联的所有 Azure 服务 (例如，这些课程) 位于公共资源组) 。 

        > 若要详细了解 Azure 资源组，请访问 [资源组一文](/azure/azure-resource-manager/resource-group-portal)。

    5. 如果要 **创建新的** 资源组组 (，请确定资源组) 。 理想情况下，位置将位于应用程序将运行的区域。 某些 Azure 资产仅在某些区域可用。
    6. 还需要确认你已了解适用于此服务的条款和条件。
    7. 选择“创建”。 

        ![创建 LUIS 服务 - 用户输入](images/AzureLabs-Lab3-03.png)
 
5.  单击"创建 **"** 后，必须等待服务创建完成，这可能需要一分钟。
6.  创建服务实例后，门户中会显示一条通知。 
 
    ![新的 Azure 通知映像](images/AzureLabs-Lab3-04.png)

7.  单击通知以浏览新的服务实例。

    ![成功创建资源通知](images/AzureLabs-Lab3-05.png)
 
8.  单击 **通知中的"** 转到资源"按钮，浏览新的服务实例。 你将被带至新的 LUIS 服务实例。 
 
    ![访问 LUIS 密钥](images/AzureLabs-Lab3-06.png)

9.  在本教程中，应用程序需要调用服务，这通过使用服务的订阅密钥完成。
10. 在 *LUIS API* 服务的"快速启动"页中，导航到第一步"获取密钥"，然后单击"**密钥" (** 也可以单击位于服务导航菜单中的蓝色超链接"密钥"（由密钥图标) 表示）来实现此目的。 这将显示 *服务密钥*。
11. 请复制其中一个显示的密钥，因为稍后在项目中需要此密钥。 
12. 在 *"服务*"语言理解，单击"门户"，重定向到将在 LUIS 应用中用于创建新服务的网页。 

## <a name="chapter-2--the-language-understanding-portal"></a>第 2 章 - 语言理解 门户

本部分将了解如何在 LUIS 门户上创建 LUIS 应用。 

> [!IMPORTANT]
> 请注意，在本章中设置 *实体*、意向和话语只是生成 LUIS服务的第一步：还需要多次重新训练该服务，以便使其更准确。 本课程的最后一章介绍了重新训练服务[](#chapter-12--improving-your-luis-service)，因此请确保完成。

1.  到达 *语言理解* 门户时，可能需要使用与门户相同的凭据登录（如果尚未Azure 门户。 

    ![LUIS 登录页](images/AzureLabs-Lab3-07.png)
 
2.  如果这是你第一次使用 LUIS，则需要向下滚动到 "欢迎" 页的底部，查找并单击 " **创建 LUIS 应用** " 按钮。

    !["创建 LUIS 应用" 页](images/AzureLabs-Lab3-08.png)
 
3.  登录后，单击 **"我的应用** " (如果当前不在该分区中) 。 然后，可以单击 " **创建新应用**"。

    ![LUIS-我的应用图像](images/AzureLabs-Lab3-09.png)
 
4.  为应用程序 *命名*。
5.  如果你的应用程序应了解不同于英语的语言，则应将 *区域性* 更改为适当的语言。
6.  你还可以在此处添加新的 LUIS 应用的 *描述* 。

    ![LUIS-创建新应用](images/AzureLabs-Lab3-10.png)

7.  按下 "**完成**" 后，将进入新 *LUIS* 应用程序的 "*生成*" 页。
8.  此处有几个重要概念需要了解：

    -   *意向*，表示将从用户查询后调用的方法。 *意向* 可以有一个或多个 *实体*。
    -   *实体*，是描述与 *意向* 相关的信息的查询组件。
    -   *最谈话* 是由开发人员提供的查询的示例，LUIS 将使用该查询来训练自身。

如果这些概念并不完全清晰，请不要担心，因为本课程将在本章中进一步阐明它们。

首先创建生成此课程所需的 *实体* 。

9.  在页面左侧，单击 " *实体*"，并单击 " **创建新实体**"。

    ![创建新实体](images/AzureLabs-Lab3-11.png)

10. 调用新的实体 *颜色*，将其类型设置为 " *简单*"，并按 " **完成**"。

    ![创建简单实体-颜色](images/AzureLabs-Lab3-12.png)
 
11. 重复此过程以创建三个 (3) 名更简单的实体：

    -   *降级*
    -   *缩小*
    -   *目标*

结果应如下图所示：

![实体创建的结果](images/AzureLabs-Lab3-13.png)
 
此时，你可以开始创建 *意向*。 

> [!WARNING]
> 请勿删除 " **无** "。

12. 在页面左侧，单击 "选择 **"，然后** 单击 " **创建新意向**"。

    ![创建新意向](images/AzureLabs-Lab3-14.png)

13. 调用新 *意向* **ChangeObjectColor**。

    > [!IMPORTANT]
    > 本课程后面的代码中使用此 *意向* 名称，因此为了获得最佳结果，请完全按所提供的名称使用此名称。

确认名称后，将定向到 "意向" 页。

![LUIS 页](images/AzureLabs-Lab3-15.png)

你会注意到有一个文本框要求你键入5个或更多不同的 *最谈话*。

> [!NOTE]
> LUIS 将所有最谈话都转换为小写。

14. 在顶部文本框中插入以下 *查询文本* (当前包含 *大约5个示例的文本类型 ...* ) ，然后按 **enter**：

```
The color of the cylinder must be red
```

你会注意到，新的 *查询文本* 将显示在下面的列表中。

按照相同的过程，插入以下六个 (6) 最谈话：

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

对于创建的每个查询文本，必须确定 LUIS 将哪些字词作为实体使用。 在此示例中，需要将所有颜色标记为一个 *颜色* 实体，并将所有可能的引用标记为 *目标实体。*

15. 为此，请在第一个查询文本中单击 " *圆柱* "，然后选择 " *目标*"。

    ![标识查询文本目标](images/AzureLabs-Lab3-16.png)
 
16. 现在，在第一个查询文本中单击 " *红色* "，然后选择 " *颜色*"。

    ![标识查询文本实体](images/AzureLabs-Lab3-17.png)
 
17. 标记下一行，其中， *cube* 应为 *目标*， *黑色* 应为一种 *颜色*。 另请注意，我们提供了单词 *"this"*、 *"it"* 和 *"this object"*，因此还提供了非特定目标类型。 

18. 重复上述过程，直到所有最谈话都具有标记的实体。 如果需要帮助，请参阅下图。

    > [!TIP]
    > 选择要标记为实体的单词时：
    > - 只需单击一下即可。
    > - 对于两个或多个单词的集合，请单击 "开始"，然后在集末尾单击。

    > [!NOTE]
    > 您可以使用 " *标记视图* " 切换按钮在 **实体/标记视图** 之间切换！

19. 结果应如下图所示，其中显示了 " **实体/标记" 视图**：

    ![标记 & 实体视图](images/AzureLabs-Lab3-18.png)
  
20. 此时，按页面右上角的 " **训练** " 按钮，并等待其上的小圆形指示器变为绿色。 这表示已成功训练 LUIS 以识别此目的。

    ![训练 LUIS](images/AzureLabs-Lab3-19.png)
 
21. 作为练习，使用实体 *target*、*升迁* 和 *缩小* 创建名为 **ChangeObjectSize** 的新意向。
22. 按照与上一意向相同的过程，插入以下八个 (8) 最谈话 *大小* 更改：

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. 结果应类似于下图所示：

    ![设置 ChangeObjectSize 令牌/实体](images/AzureLabs-Lab3-20.png) 

24. 一旦创建并训练了 **ChangeObjectColor** 和 **ChangeObjectSize**，单击页面顶部的 " **发布** " 按钮。

    ![发布 LUIS 服务](images/AzureLabs-Lab3-21.png)

25. 在 " *发布* " 页上，您将完成并发布 LUIS 应用程序，以便您的代码可以访问它。

    1. 将下拉 " *发布到* " 设置为 " **生产**"。
    2. 将 *时区* 设置为时区。
    3. 选中 " **包括所有预测意向分数**" 框。
    4. 单击 " **发布到生产槽**"。

        ![发布设置](images/AzureLabs-Lab3-22.png)

26. 在 " *资源和密钥*" 部分中：

    1.  在 Azure 门户中选择为服务实例设置的区域。
    2.  你将注意到下面的一个 **Starter_Key** 元素，请将其忽略。
    3.  单击 " **添加密钥** "，并在创建服务实例时插入在 Azure 门户中获取的 *密钥* 。 如果你的 Azure 和 LUIS 门户登录到同一用户，你将向你提供 " *租户名称*"、" *订阅名称*" 和你想要使用的 *密钥* 的下拉菜单， (会与你之前在 Azure 门户中提供的名称相同。

    > [!IMPORTANT] 
    > 在 " *终结点*" 下，获取与所插入的密钥对应的终结点副本，然后在代码中立即使用该副本。
 
## <a name="chapter-3--set-up-the-unity-project"></a>第3章–设置 Unity 项目

下面是使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。

1.  打开 *Unity* ，并单击 " **新建**"。 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab3-24.png)

2.  你现在需要提供 Unity Project 名称，插入 **MR_LUIS**。 请确保 "项目类型" 设置为 " **3d**"。 将位置设置为合适的 **位置** (记住，更接近根目录) 。 然后单击 " **创建项目**"。

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab3-25.png)
 
3.  当 Unity 处于打开状态时，有必要检查默认 **脚本编辑器** 是否设置为 **Visual Studio**。 转到 "编辑 > 首选项"，然后在新窗口中导航到 " **外部工具**"。 将 **外部脚本编辑器** 更改为 **Visual Studio 2017**。 关闭 " **首选项** " 窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab3-26.png)
 
4.  接下来，通过单击 "**切换平台**" 按钮转到 "**文件 > 生成" 设置** 并将平台切换到 "**通用 Windows 平台**"。

    ![构建设置窗口，将平台切换到 UWP。](images/AzureLabs-Lab3-27.png)
 
5.  请参阅 **文件 > 生成设置**，并确保：

    1. **目标设备** 设置为 **任何设备**

        > 对于 Microsoft HoloLens，请将 "**目标设备**" 设置为 " *HoloLens*"。

    2. **生成类型** 设置为 **D3D**
    3. **SDK** 设置为 "**最新安装**"
    4. **Visual Studio版本** 设置为"最新 **安装"**
    5. **"生成和运行** "设置为" **本地计算机"**
    6. 保存场景并将其添加到生成。

        1. 为此，选择"**添加打开的场景"。** 将显示保存窗口。
        
            ![单击"添加打开的场景"按钮](images/AzureLabs-Lab3-28.png)

        2. 为此和任何将来的场景创建新文件夹，然后选择"新建文件夹"按钮，以创建新文件夹，将其命名为 **"场景"。**

            ![创建新脚本文件夹](images/AzureLabs-Lab3-29.png)

        3. 打开新创建的 **"场景**"文件夹，然后在"文件名 *：* 文本"字段中，键入"MR_LuisScene"，**然后** 按"**保存"。**

            ![为新场景命名。](images/AzureLabs-Lab3-30.png)

    7. 目前，"*生成设置中的* 其余设置应保留为默认值。

6. 在"*生成设置* 窗口中，单击"播放器设置按钮，这将在 *检查* 器所在的空间中打开相关面板。 

    ![打开播放器设置。](images/AzureLabs-Lab3-31.png) 
 
7. 在此面板中，需要验证一些设置：

    1. 在"**其他设置** 选项卡中：

        1. **脚本运行时版本****应稳定**（A0.NET 3.5 等效) 。
        2. **脚本后端应为** **.NET**
        3. **API 兼容性级别** 应为 **.NET 4.6**

            ![更新其他设置。](images/AzureLabs-Lab3-32.png)
      
    2. 在"**发布设置** 选项卡中的"**功能"下**，选中：

        1. **InternetClient**
        2. **麦克风**

            ![更新发布设置。](images/AzureLabs-Lab3-33.png)

    3. 在面板的下方，在"发布 设置) "下找到的 **"XR** 设置 ("中，勾选"支持虚拟现实"，确保Windows Mixed Reality **SDK。** 

        ![更新 X R 设置。](images/AzureLabs-Lab3-34.png)

8.  返回到 *"生成设置* _Unity C#_ 项目不再灰度;勾选此 旁边的复选框。 
9.  关闭“生成设置”窗口。
10. 保存场景和Project (**文件>保存场景/文件>保存项目**) 。

## <a name="chapter-4--create-the-scene"></a>第 4 章 - 创建场景

> [!IMPORTANT]
> 如果要跳过本课程 *的 Unity 设置* 组件，并直接继续编写代码，请随意下载 [此 .unitypackage，](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)将其作为自定义包导入到项目中，然后继续学习 [](https://docs.unity3d.com/Manual/AssetPackages.html)第 [5](#chapter-5--create-the-microphonemanager-class)章 。 

1.  右键单击"层次结构面板"的空白区域，在 **"3D 对象**"下添加 **"平面"。**

    ![创建平面。](images/AzureLabs-Lab3-35.png)

2.  请注意，再次右键单击"层次结构"以创建更多对象时，如果仍选择了最后一个对象，则所选对象将是新对象的父级。 避免在层次结构中的空白区域进行此左键单击，然后右键单击。

3.  重复上述过程以添加以下对象：

    1. *Sphere*
    2. *柱状*
    3. *Cube*
    4. *3D 文本*

4.  生成的场景 *层次结构* 应如下图所示：

    ![场景层次结构设置。](images/AzureLabs-Lab3-36.png)
 
5.  左键单击 **"主相机"** 将其选中，查看检查器面板，你将看到"相机"对象及其所有组件。
6.  单击" **检查器面板** "最底部的"添加组件 *"按钮*。

    ![添加音频源](images/AzureLabs-Lab3-37.png)
 
7.  搜索名为"音频 *源"的组件*，如上所示。
8.  此外，请确保主相机的"转换"组件设置为 (0，0，0) ，这可以通过按相机的"转换"组件旁边的齿轮图标并选择"重置 **"完成。**  转换 *组件* 应如下所示：

    1.  *位置* 设置为 **0、0、0。**
    2.  *旋转* 设置为 **0、0、0。**

    > [!NOTE] 
    > 对于Microsoft HoloLens，还需要更改以下各项，这些组件是主相机上的 **Camera** 组件的 **一部分**：
    > - **清除标志：** 纯色。
    > - **背景** "Black， Alpha 0"– 十六进制颜色：#00000000。

9.  左键单击 **"平面"** 将其选中。 在检查 *器面板* 中， *将"转换* "组件设置为以下值：

    |   X 轴    | Y 轴 |   Z 轴    |
    |:-----:|:----------------------:|:-----:|
    | 0     | -1                     | 0     |


10. 左键单击 **"Sphere"** 将其选中。 在检查 *器面板* 中， *将"转换* "组件设置为以下值：

    |   X 轴    | Y 轴 |   Z 轴    |
    |:-----:|:----------------------:|:-----:|
    | 2     | 1                      | 2     |

11. 左键单击 **"柱面"** 将其选中。 在检查 *器面板* 中， *将"转换* "组件设置为以下值：

    |   X 轴    | Y 轴 |   Z 轴    |
    |:-----:|:----------------------:|:-----:|
    | -2    | 1                      | 2     |

12. 左键单击 **"多维数据集"** 将其选中。 在检查 *器面板* 中， *将"转换* "组件设置为以下值：

    |        | 转换 - *位置* |       |  \| |       | 转换 - *旋转* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **是**                   | **Z** |  \| | **X** | **是**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. 左键单击 **"新建文本"** 对象以将其选中。 在检查 *器面板* 中， *将"转换* "组件设置为以下值：

    |       | 转换 - *位置* |       |  \| |       | 转换 - *缩放* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **是**                  | **Z** |  \| | **X** | **是**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. 将 **文本网格** 组件 **中的字** 号更改为 **50。**
15. 将 *文本网格***对象的名称** 更改为 **听写文本**。

    ![创建三维文本对象](images/AzureLabs-Lab3-38.png)
 
16. 层次结构面板结构现在应如下所示：

    ![场景视图中的文本网格](images/AzureLabs-Lab3-38b.png)


17. 最终场景应如下图所示：

    ![场景视图。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>第 5 章 - 创建 MicrophoneManager 类

要创建的第一个脚本是 *MicrophoneManager* 类。 然后，你将创建 *LuisManager、**行为* 类和最后一个 *"* 凝视"类 (现在可随意创建所有这些内容，不过，在到达每个章节) 时，将介绍所有这些内容。

*MicrophoneManager* 类负责：

-   检测连接到头戴显示设备或 (设备（以默认设备为准) ）。
-   捕获语音 (语音) 听写以字符串形式存储。
-   语音暂停后，将听写提交到 *LuisManager* 类。 

若要创建此类，请： 

1.  右键单击 *"Project"，***创建>文件夹"**。 调用文件夹 **Scripts**。 

    ![创建 Scripts 文件夹。](images/AzureLabs-Lab3-40.png)
 
2.  创建 **"脚本"** 文件夹后，双击它以打开。 然后，在此文件夹中，右键单击"创建 **> C# 脚本"。** 将脚本 *"MicrophoneManager"命名*。 

3.  双击 *"MicrophoneManager"，* 使用 *Visual Studio。*
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  然后在 *MicrophoneManager* 类中添加以下变量：

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  现在需要 *()**唤醒 ()* 启动方法的代码。 当 类初始化时，将调用这些 ：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  现在，需要应用用于启动和停止语音捕获的方法，并传递给 *LuisManager* 类，你即将生成该方法。 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  添加 *语音暂停时* 将调用的听写处理程序。 此方法将听写文本传递给 *LuisManager* 类。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > 删除 *Update ()* 方法，因为此类不会使用它。

9.  在返回到 Unity 之前，请确保Visual Studio中的 *更改*。

    > [!NOTE]
    > 此时，你将注意到 Unity 编辑器控制台面板 *中出现一个错误*。 这是因为代码引用将在下一章创建的 *LuisManager* 类。

## <a name="chapter-6--create-the-luismanager-class"></a>第 6 章 - 创建 LUISManager 类

现在可以创建 *LuisManager* 类，该类将调用 Azure LUIS 服务。 

此类的目的是接收 *来自 MicrophoneManager* 类的听写文本，并将其发送到 *Azure 语言理解 API* 进行分析。

此类将反初始化 *JSON* 响应，并调用 *行为类* 的适当方法来触发操作。

若要创建此类，请： 

1.  双击"脚本 **"** 文件夹，打开它。 
2.  在"脚本"文件夹中 **右键** 单击，单击 **"> C# 脚本"。** 将脚本名称 *为 LuisManager*。 
3.  双击该脚本，以使用 Visual Studio。
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  首先，在同一脚本文件的 *LuisManager* 类 (内创建三个类，这三个类位于 Start *()* 方法) 上，表示来自 Azure 的反初始化 JSON 响应。

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  接下来，在 *LuisManager 类中添加以下* 变量：
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  确保现在将 LUIS 终结点放在 (LUIS 门户门户中) 。

8.  现在 *需要 ()* 唤醒方法的代码。 当 类初始化时，将调用此方法：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  现在，需要此应用程序用于将 *从 MicrophoneManager* 类收到的听写发送到 *LUIS* 的方法，然后接收和反反初始化响应。 
10. 确定"意向"和关联的"实体"的值后，这些实体将传递到 *"行为* "类的实例，以触发预期操作。

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. 创建名为 *"分析""ResponseElements" () ，* 该方法将读取生成的 *"处理* "查询并确定"实体"。 确定这些实体后，这些实体将传递到 *行为类* 的实例，以在操作中使用。

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > 删除 *Start ()* Update *()* 方法，因为此类不会使用它们。

12. 在返回到 Unity 之前，请确保Visual Studio中的 *更改*。

> [!NOTE]
> 此时，你会注意到 Unity 编辑器控制台面板 中出现 *几个错误*。 这是因为代码引用将在下一章创建的 *"行为* "类。

## <a name="chapter-7--create-the-behaviours-class"></a>第 7 章 - 创建行为类

*行为类* 使用 *LuisManager* 类提供的 Entities 触发操作。

若要创建此类，请： 

1.  双击"脚本 **"** 文件夹，打开它。 
2.  在"脚本"文件夹中 **右键** 单击，单击 **"> C# 脚本"。** 将脚本 *名称为"行为"。* 
3.  双击该脚本，以使用 *Visual Studio。*
4.  然后在"行为"类中添加 *以下* 变量：

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  添加 *"唤醒 ()* 方法代码。 当 类初始化时，将调用此方法：

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  之前创建的 *LuisManager* (调用以下方法，) 确定哪个对象是查询的目标，然后触发相应的操作。

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  添加 *FindTarget ()* 确定 *哪个 GameObjects* 是当前意向的目标。 如果未在实体中定义显式目标，此方法默认将 *GameObject* 的目标设置为"已禁用"。

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > 删除 *Start ()* Update *()* 方法，因为此类不会使用它们。

8.  在返回到 Unity 之前，请确保Visual Studio中的 *更改*。

## <a name="chapter-8--create-the-gaze-class"></a>第 8 章 - 创建凝视类

完成此应用所需的最后一个类是 *"凝视"* 类。 此类更新对当前处于用户视觉焦点中的 *GameObject* 的引用。

若要创建此类，请： 

1.  双击"脚本 **"** 文件夹，打开它。 
2.  在"脚本"文件夹中 **右键** 单击，单击 **"> C# 脚本"。** 将脚本命名"*凝视"。* 
3.  双击该脚本，以使用 *Visual Studio。*
4.  插入此类的以下代码：

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  在返回到 Unity 之前，请确保Visual Studio中的 *更改*。

## <a name="chapter-9--completing-the-scene-setup"></a>第 9 章 - 完成场景设置

1.  若要完成场景设置，请将创建的每个脚本从"脚本文件夹"拖动到"层次结构面板"中的"主 *相机"对象*。
2.  选择 **主相机** 并查看检查器面板，应能够看到已附加的每个脚本，并且你会注意到每个脚本上都有参数尚未设置。

    ![设置相机参考目标。](images/AzureLabs-Lab3-41.png)

3.  若要正确设置这些参数，请按照以下说明操作：

    1. *MicrophoneManager：*

        - 从" *层次结构面板"* 中，将 **听写文本** 对象拖到" **听写文本"** 参数值框中。

    2. *行为，* 来自 *层次结构面板*：

        - 将 **Sphere 对象** 拖到 *"Sphere* 引用目标"框中。
        - 将" **柱面"** 拖动到 *"柱面* 引用目标"框中。
        - 将" **多维数据集"** 拖到 *"多维数据集引用* 目标"框中。

    3. *注视*：

        - 如果尚未) ，请将 " *注视最大距离* " 设置为 **300** (。 

4.  结果应如下图所示：

    ![当前设置了照相机引用目标。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>第10章–在 Unity 编辑器中测试

测试场景设置是否已正确实现。

请确保：

-   所有脚本都附加到 **相机** 对象上。 
-   *主相机检查器面板* 中的所有字段均已正确分配。

1.  按下 *Unity 编辑器* 中的 "**播放**" 按钮。 应用应在附加的沉浸式耳机中运行。

2.  尝试一些最谈话，例如：

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > 如果在 Unity 控制台中看到有关默认音频设备变化的错误，场景可能无法按预期方式工作。 这是因为混合现实门户使用内置麦克风处理随附的耳机的方式。 如果看到此错误，只需停止场景并再次启动，应按预期方式工作。

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>第11章–构建和旁加载 UWP 解决方案

确保应用程序在 Unity 编辑器中运行后，便可以生成并部署了。

若要生成：

1.  单击 " **文件" > "保存**"，保存当前场景。
2.  请参阅 **文件 > 生成设置**。
3.  勾选称为 **Unity c # 项目** 的框， (在创建 UWP 项目后查看和调试代码非常有用。
4.  单击 " **添加打开的场景**"，然后单击 " **生成**"。

    ![构建设置窗口](images/AzureLabs-Lab3-43.png)

4.  系统将提示您选择要在其中生成解决方案的文件夹。 

5.  创建一个 *生成* 文件夹，在该文件夹中创建另一个文件夹，其中包含所选的适当名称。 
6.  单击 " **选择文件夹** "，在该位置开始生成。
 
    ![创建生成文件夹 ](images/AzureLabs-Lab3-44.png)
     ![ 选择生成文件夹](images/AzureLabs-Lab3-45.png)
 
7.  Unity 完成生成后 (可能需要一些时间) ，它应在生成的位置打开 **文件资源管理器** 窗口。

在本地计算机上部署：

1.  在 *Visual Studio* 中，打开已在 [上一章](#chapter-10--test-in-the-unity-editor)中创建的解决方案文件。
2.  在 **解决方案平台** 中，选择 " **X86**， **本地计算机**"。
3.  在 **解决方案配置** 中，选择 " **调试**"。

    > 对于 Microsoft HoloLens，你可能会发现将其设置为 *远程计算机* 会更容易，因此你不会受限到计算机上。 不过，还需要执行以下操作：
    > - 知道 HoloLens 的 **IP 地址**，可在 *设置 > 网络 & Internet > Wi-Fi 高级选项* 中找到该地址;IPv4 是应使用的地址。 
    > - 确保 **开发人员模式** 已 **打开**;*> 更新开发人员设置 & 安全 >*。

    ![部署应用](images/AzureLabs-Lab3-46.png)
 
4.  请在 " **生成" 菜单** 中，单击 " **部署解决方案** "，将应用程序旁加载到计算机上。
5.  应用现在应显示在已安装的应用列表中，可以启动了！
6.  启动后，应用会提示你授权访问 _麦克风_。 使用 *运动控制器*、 *语音输入* 或 *键盘* 按 **"是"** 按钮。 

## <a name="chapter-12--improving-your-luis-service"></a>第12章-改进 LUIS 服务

>[!IMPORTANT] 
> 本章非常重要，可能需要多次迭代，因为这将有助于提高 LUIS 服务的准确性：请确保完成此操作。

若要改进 LUIS 提供的理解级别，需要捕获新的最谈话，并使用它们重新训练 LUIS 应用。

例如，你可能已经训练了 LUIS 来理解 "增加" 和 "升迁"，但又不希望你的应用程序也知道 "放大" 等词呢？

一旦你使用了应用程序几次，你所说的一切将被 LUIS 收集，并在 LUIS 门户中可用。

1.  请按照以下 [链接](https://www.luis.ai/home)打开门户应用程序，并登录。
2.  用 MS 凭据登录后，单击你的 *应用名称*。
3.  单击页面左侧的 " **查看终结点最谈话** " 按钮。

    ![查看最谈话](images/AzureLabs-Lab3-47.png)
 
4.  将显示一个列表，其中包含已由混合现实应用程序发送到 LUIS 的最谈话。

    ![最谈话列表](images/AzureLabs-Lab3-48.png)
 
你会注意到一些突出显示的 *实体*。 

通过将鼠标悬停在每个突出显示的单词上，你可以查看每个查询文本并确定哪些实体已正确识别，哪些实体出现错误以及哪些实体丢失。

在上面的示例中，发现 "鱼叉式" 一词已突出显示为目标，因此需要更正此错误，这是通过将鼠标悬停在单词上并单击 " **删除标签**" 来完成的。

![检查最谈话 ](images/AzureLabs-Lab3-49.png)
 ![ 删除标签图像](images/AzureLabs-Lab3-50.png)
 
5.  如果找到完全错误的最谈话，可以使用屏幕右侧的 " **删除** " 按钮删除它们。

    ![删除错误的最谈话](images/AzureLabs-Lab3-51.png)

6.  或者，如果您认为 LUIS 已正确解释查询文本，则可以使用 " **添加到对齐意向** " 按钮来验证其理解。

    ![添加到对齐意向](images/AzureLabs-Lab3-52.png)

7.  对所有显示的最谈话进行排序后，请尝试重新加载页面，查看是否有更多的可用功能。
8.  尽可能多地重复此过程以提高应用程序理解。 

**玩得愉快！**

## <a name="your-finished-luis-integrated-application"></a>已完成的 LUIS 集成应用程序

恭喜，你构建了一个使用 Azure 语言理解智能服务的混合现实应用，以了解用户所说的内容，并对该信息采取措施。

![实验室结果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习 1

使用此应用程序时，您可能会注意到，如果注视地面对象并要求更改其颜色，则会这样做。 您可以如何阻止您的应用程序更改地面颜色？

### <a name="exercise-2"></a>练习 2

尝试扩展 LUIS 和应用功能，为场景中的对象添加其他功能;例如，在注视点处创建新的对象，具体取决于用户所显示的内容，然后可以将这些对象和当前场景对象与现有的命令一起使用。