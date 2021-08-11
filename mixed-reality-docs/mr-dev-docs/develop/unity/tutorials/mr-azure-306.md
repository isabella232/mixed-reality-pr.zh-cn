---
title: HoloLens（第一代）和 Azure 306 - 流式传输视频
description: 完成本课程以了解如何在混合现实应用程序中实现 Azure 媒体服务。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，媒体服务，流视频，360，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 3f3567c140c3162258475c28c2ef149039e3c40ed418ed2801ac8c40dda00a8f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224134"
---
# <a name="hololens-1st-gen-and-azure-306-streaming-video"></a>HoloLens (第一代) 和 Azure 306：流式处理视频

<br>

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br> 

![最终产品-启动 ](images/AzureLabs-Lab6-00.png)
 ![ 最终产品-启动](images/AzureLabs-Lab6-01.png)

在本课程中，你将了解如何将 Azure 媒体服务连接到 Windows Mixed Reality VR 体验，以允许在沉浸式耳机上播放流式传输360学位视频。 

**Azure 媒体服务** 是提供广播质量的视频流式处理服务的服务的集合，可让用户在当前最常见的移动设备上达到更大的受众。 有关详细信息，请访问[Azure 媒体服务页](https://azure.microsoft.com/services/media-services)。

完成本课程后，你将拥有一个混合现实沉浸式耳机应用程序，该应用程序将能够执行以下操作：

1. 通过 **Azure 媒体服务** 从 **Azure 存储** 检索360度视频。

2. 在 Unity 场景中显示检索到的360度视频。

3. 在两个场景之间导航，具有两个不同的视频。

在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。 本课程旨在向您介绍如何将 Azure 服务与 Unity Project 集成。 您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 306：流式传输视频</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为具有 Unity 和 c # 基本经验的开发人员设计。 请注意，本文档中的先决条件和书面说明表明了编写 (2018) 时测试和验证的内容。 您可以随意使用最新的软件（如 [安装工具一文](../../install-the-tools.md)中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件：

- 与沉浸式 (VR) 耳机开发[Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC
- [启用开发人员模式 Windows 10 Fall Creators Update (或更高版本) ](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017。4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 沉浸式 (VR) 耳机](../../../discover/immersive-headset-hardware-details.md)
- Azure 安装和数据检索的 Internet 访问
- 2 360 的视频学位格式 (你可以 [在此下载页面上](https://www.mettle.com/360vr-master-series-free-360-downloads-page) 找到一些免费版税的视频) 

## <a name="before-you-start"></a>开始之前

1.  若要避免在生成此项目时遇到问题，强烈建议你在根或近乎根文件夹中创建本教程中所述的项目 (长文件夹路径在生成时) 会导致问题。
2.  设置并测试混合现实沉浸式耳机。

    > [!NOTE]
    > 本课程 **不** 需要移动控制器。 如果需要支持设置沉浸式耳机，请单击["如何设置 Windows Mixed Reality 的链接](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)"。

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>第1章-Azure 门户：创建 Azure 存储帐户

若要使用 **Azure 存储服务**，你将需要在 Azure 门户中创建和配置 **存储帐户**。

1.  登录到 [Azure 门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。

2.  登录后，单击左侧菜单中的 "**存储帐户**"。

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-02.png)

3.  在 "**存储帐户**" 选项卡上，单击 "**添加**"。

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-03.png)

4.  在 " **创建存储帐户** " 选项卡中：

    1.  插入帐户的 **名称** ，请注意，此字段仅接受数字和小写字母。

    2.  对于 **部署模型，选择 "** **资源管理器**"。

    3.  对于 "**帐户类型**"，请选择 "**存储 (常规用途 v1)**"。

    4.  对于 " **性能**"，请选择 " **标准"。**

    5.  对于 **复制** ，请选择 **本地冗余存储 (LRS)**。

    6.  使 **安全传输** 保持 **禁用状态**。

    7.  选择一个“订阅”  。

    8.  选择一个 **资源组** ，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。

    9.  如果要创建新的资源组) ，请确定资源组 (的 **位置** 。 此位置理想情况下会在应用程序运行所在的区域中。 某些 Azure 资产仅在特定区域提供。

5.  你将需要确认你已了解应用于此服务的条款和条件。

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-04.png)

6.  单击 " **创建**" 后，需要等待创建服务，这可能需要一分钟时间。

7.  创建服务实例后，门户中将显示一个通知。

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-05.png)

8.  此时，无需访问资源，只需转到下一章即可。

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>第2章-Azure 门户：创建媒体服务

若要使用 Azure 媒体服务，需要将服务实例配置为可用于应用程序 (其中，帐户持有者必须是管理员) 。

1.  在 Azure 门户中，单击左上角的 " **创建资源** "，然后搜索 **Media Service，** 按 **enter**。 当前所需资源的图标为粉红色;单击此，显示新页。

    ![Azure 门户](images/AzureLabs-Lab6-06.png)

2.  新页将提供 **媒体服务** 的说明。 在此提示符的左下方，单击 " **创建** " 按钮以创建与此服务的关联。

    ![Azure 门户](images/AzureLabs-Lab6-07.png)

3.  单击 " **创建** " 后，将显示一个面板，需要在其中提供有关新媒体服务的一些详细信息：

    1.  为此服务实例插入所需的 **帐户名称** 。

    2.  选择一个“订阅”  。

    3. 选择一个 **资源组** ，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议保留与单个项目关联的所有 Azure 服务 (例如，这些实验室) 在常见资源组) 下。 
    
    > 若要了解有关 Azure 资源组的详细信息，请参阅此 [链接，了解如何管理 Azure 资源组](/azure/azure-resource-manager/resource-group-portal)。

    4.  如果要创建新的资源组) ，请确定资源组 (的 **位置** 。 此位置理想情况下会在应用程序运行所在的区域中。 某些 Azure 资产仅在特定区域提供。

    5.  对于 "**存储帐户**" 部分，单击 "**请选择 ...** " 部分，然后单击在上一章中创建的 **存储帐户**。

    6.  还需要确认是否已了解应用于此服务的条款和条件。

    7.  单击“**创建**”。

        ![Azure 门户](images/AzureLabs-Lab6-08.png)

4.  单击 " **创建**" 后，需要等待创建服务，这可能需要一分钟时间。

5.  创建服务实例后，门户中将显示一个通知。

    ![Azure 门户](images/AzureLabs-Lab6-09.png)

6.  单击通知以浏览新服务实例。

    ![Azure 门户](images/AzureLabs-Lab6-10.png)

7.  单击 **通知中的"** 转到资源"按钮，浏览新的服务实例。

8.  在新的"媒体服务"页的左侧面板中，单击"资产"链接，该链接大约位于半角。

9.  在页面左上角的下一页上，单击 **"Upload"。**

    ![Azure 门户](images/AzureLabs-Lab6-11.png)

10. 单击" **文件夹"** 图标浏览文件，然后选择要流式传输的第一个 360 视频。 
    
    > 可以单击此 [链接下载示例视频](https://vimeo.com/214401712)。

    ![Azure 门户](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> 长文件名可能会导致编码器问题：因此，若要确保视频没有问题，请考虑缩短视频文件名的长度。

11. 上传完视频后，进度栏将变成绿色。

    ![Azure 门户](images/AzureLabs-Lab6-13.png)

12. 单击上述文本 **， ("yourservicename - Assets")** 返回到"资产 **"** 页。

13. 你会注意到你的视频已成功上传。 单击该磁贴。

    ![Azure 门户](images/AzureLabs-Lab6-14.png)

14. 重定向到的页面将显示有关视频的详细信息。 若要能够使用视频，需要单击页面左上方的"编码"按钮进行编码。

    ![Azure 门户](images/AzureLabs-Lab6-15.png)

15. 右侧将显示一个新面板，可以在其中为文件设置编码选项。 设置以下属性 (某些属性默认已设置为) ：

    1.  **媒体编码器 *名称Media Encoder Standard***

    2.  **编码预设 *内容自适应多比特率 MP4***

    3.  **作业名称 *Media Encoder Standard处理Video1.mp4***

    4.  **输出媒体资产名称 *Video1.mp4 -- Media Encoder Standard编码***

        ![Azure 门户](images/AzureLabs-Lab6-16.png)

16. 单击“创建”按钮。

17. 你会注意到添加了编码 **作业的栏**，单击该栏，将显示一个面板，并显示"编码进度"。

    ![Azure 门户](images/AzureLabs-Lab6-17.png)

    ![Azure 门户](images/AzureLabs-Lab6-18.png)

18. 等待作业完成。 完成后，请随意关闭面板，面板右上方有"X"。

    ![Azure 门户](images/AzureLabs-Lab6-19.png)

    ![Azure 门户](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > 此时间取决于视频的文件大小。 此过程可能需要很长时间。

19. 创建视频的编码版本后，可以发布该视频，使其可访问。 为此，请单击蓝色链接 **"资产** "返回到"资产"页。

    ![Azure 门户](images/AzureLabs-Lab6-21.png)

20. 你将看到视频以及另一个，即资产 **类型 _多比特率 MP4。_**

    ![Azure 门户](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > 你可能会注意到，新资产与初始视频一起为"未知"，其大小为"0"字节，只需刷新窗口以进行更新。

21. 单击此新资产。

    ![Azure 门户](images/AzureLabs-Lab6-23.png)

22. 你将看到一个与之前使用的面板类似的面板，只是这是一个不同的资产。 单击 **页面** 顶部中心的"发布"按钮。

    ![Azure 门户](images/AzureLabs-Lab6-24.png)

23. 系统将提示将 **定位** 符 （即入口点）设置为"资产"中的文件。 对于方案，请设置以下属性：

    1.  **定位符类型**  > **渐进式**。

    2.  日期和时间 **将** 设置为从当前日期到未来 100 年 (，本例中) 。 保留为""或"更改"以适合。

    > [!NOTE]
    > 有关定位符以及可以选择哪些内容的详细信息，请访问 Azure 媒体服务[文档](/azure/media-services/media-services-concepts)。

24. 在面板底部，单击"添加 **"** 按钮。

    ![Azure 门户](images/AzureLabs-Lab6-25.png)

25. 视频现已发布，可以使用其终结点进行流式传输。 页面的下部是"文件 **"** 部分。 这是视频的不同编码版本。 选择下图中可能 (分辨率为 1920x960) ，然后右侧会显示一个面板。 可在此处找到"下载 **URL"。** 复制 **此终结点** ，因为稍后将在代码中使用它。

    ![Azure 门户](images/AzureLabs-Lab6-26.png)    

    ![Azure 门户](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > 还可以按"播放 **"** 按钮播放视频并进行测试。

26. 现在需要上传将在此实验室中使用的第二个视频。 按照上述步骤操作，为第二个视频重复相同的过程。 确保同时复制第二 **个** 终结点。 使用以下链接 [下载第二个视频](https://vimeo.com/214402865)。

27. 发布这两个视频后，即可进入下一章。

## <a name="chapter-3---setting-up-the-unity-project"></a>第 3 章 - 设置 Unity Project

下面是使用混合现实进行开发的典型设置，因此，是其他项目的良好模板。

1.  打开 **Unity，** 然后单击"新建 **"。** 

    ![Azure 门户](images/AzureLabs-Lab6-28.png)

2.  现在，需要提供 Unity Project，插入 **MR \_ 360VideoStreaming。** 确保项目类型设置为 **3D**。 将"位置"设置为适合你记住 (，越靠近根目录越好) 。 然后单击"创建 **项目"。**

    ![Azure 门户](images/AzureLabs-Lab6-29.png)

3.  打开 Unity 后，值得检查 **默认脚本编辑器** 是否设置为 **Visual Studio。** 转到"**_编辑_*首选项"，*** 然后从新窗口导航到"**外部工具"。** 将 **"外部脚本编辑器"****更改为 Visual Studio 2017。** 关闭 **"首选项"** 窗口。

    ![Azure 门户](images/AzureLabs-Lab6-30.png)

4.  接下来，转到"***文件* 生成 *设置，*** 并单击"切换平台"按钮 **，将** 平台切换到"通用 Windows **平台**"。

5.  另请确保：

    1. **目标设备** 设置为" **任何设备"。**
    
    2.  **生成类型** 设置为 **D3D。**

    3.  **SDK** 设置为"最新 **安装"。**

    4.  **Visual Studio版本** 设置为"最新 **安装"。**

    5.  **"生成和运行** "设置为" **本地计算机"。**

    6.  请不要担心现在设置 **"场景** "，因为稍后会进行设置。

    7.  其余设置现在应保留为默认值。

        ![设置 Unity Project](images/AzureLabs-Lab6-31.png)

6.  在"**生成设置** 窗口中，单击"播放器设置按钮，这将在 **检查** 器所在的空间中打开相关面板。 

7. 在此面板中，需要验证一些设置：

    1.  在"**其他设置** 选项卡中：

        1.  **脚本运行时****版本****应稳定**（A0.NET 3.5 等效) 。

        2. **脚本后端应为** **.NET。**

        3. **API 兼容性级别应为** **.NET 4.6。**

            ![设置 Unity Project](images/AzureLabs-Lab6-32.png)

    2.  在面板的下方，在"发布 设置) "下找到的 **"XR** 设置 ("中，勾选"支持虚拟现实"，确保Windows Mixed Reality **SDK。** 

        ![设置 Unity Project](images/AzureLabs-Lab6-33.png)

    3.  在"**发布设置** 选项卡中的"**功能"下**，选中：

        - **InternetClient**

            ![设置 Unity Project](images/AzureLabs-Lab6-34.png)

8.  进行这些更改后，关闭"**生成设置窗口**。

9.  保存Project **文件**保存Project**。



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>第 4 章 - 导入 InsideOutSphere Unity 包

> [!IMPORTANT]
> 如果要跳过本课程 *的 Unity 设置* 组件，并直接继续编写代码，请随意下载 [此 .unitypackage，](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)将其作为自定义包导入到项目中，然后继续学习 [](https://docs.unity3d.com/Manual/AssetPackages.html)第 **5** 章 。 你仍然需要创建 Unity Project。

对于本课程，需要下载名为 [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)的 Unity 资产包。

如何导入 **unitypackage：**

1.  在 Unity 仪表板的前面，单击屏幕顶部菜单中的"资产"，然后单击"导入包>**自定义包"。**

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-35.png)

2.  使用文件选取器选择 **InsideOutSphere.unitypackage** 包，然后单击"打开 **"。** 此时会显示此资产的组件列表。 单击"导入"确认 **导入**。

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-36.png)

3.  导入完成后，你会注意到，"材料"、"模型"和"预制文件"这三个新文件夹已添加到 **"资产"** 文件夹。  此类文件夹结构对于 Unity 项目是典型的。

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-37.png)

    1.  打开 **Models** 文件夹，会看到 **InsideOutSphere** 模型已导入。

    2.  在 **"材料** "文件夹中，可以找到 **InsideOutSpheres** 材料  *lambert1，* 以及一种名为 *ButtonMaterial* 的材料，由 GazeButton 使用，你很快就会看到它。

    3.  **Prefabs** 文件夹包含 **InsideOutSphere** 预制项，其中包含 **InsideOutSphere** *模型* 和 *GazeButton*。

    4.  **不包含任何代码**，你将按照本课程中的说明编写代码。


4.  在" **层次结构"中**，选择 **"主相机"** 对象，并更新以下组件：

    1.  **转换**

        1.  Position = **X**： 0， **Y**： 0， **Z**： 0。

        2. Rotation = **X**： 0， **Y**： 0， **Z**： 0。

        3. Scale **X**：1， **Y**： 1， **Z**： 1.

    2.  **摄像头**

        1. **清除标志**：纯色。

        2.  **裁剪平面：** 近：0.1，远：6。

            ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-38.png)

5.  导航到 **"Prefab"** 文件夹，然后将 **InsideOutSphere** 预制块拖到"层次结构 **面板"** 中。

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-39.png)

6.  单击"层次结构"旁边的小箭头，展开"层次结构"中的 **InsideOutSphere** 对象。 你将在它 **下面看到一个** 称为 **"GazeButton"的子对象**。 这将用于更改场景，从而更改视频。

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-40.png)

7.  在"检查器"窗口中，单击 **InsideOutSphere** 的"转换"组件，确保已设置以下属性：

    |            |    TRANSFORM - POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    转换 - 旋转   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     转换 - 缩放     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-41.png)

8.  单击 **"GazeButton"** 子对象，并按如下所示 **设置其** "转换"：

    |            |    TRANSFORM - POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    转换 - 旋转   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     转换 - 缩放     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>第 5 章 - 创建 VideoController 类

**VideoController** 类托管两个视频终结点，用于流式传输 Azure 媒体服务中的内容。

若要创建此类，请：

1.  右键单击位于"**资产"** 面板中的"资产 **Project，然后单击**"**创建>文件夹"。** 将 **文件夹命名脚本**。

    ![创建 VideoController 类](images/AzureLabs-Lab6-43.png)

    ![创建 VideoController 类](images/AzureLabs-Lab6-44.png)

2.  双击"脚本 **"** 文件夹以打开它。

3.  右键单击文件夹内，然后单击"**创建> C \# 脚本"。** 将脚本名称 **为 VideoController**。

    ![创建 VideoController 类](images/AzureLabs-Lab6-45.png)

4.  双击新的 **VideoController** 脚本，使用 Visual Studio **2017 打开它。**

    ![创建 VideoController 类](images/AzureLabs-Lab6-46.png)

5.  更新代码文件顶部的命名空间，如下所示：

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  在 **VideoController** 类中输入以下变量，以及 **"唤醒** () 方法：

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  现在，可以在 Azure 媒体服务视频中输入终结点：

    1.  第一个输入 *video1endpoint* 变量。
    
    2.  *video2endpoint 变量中的第二* 个 。

    > [!WARNING]
    > 在 Unity 内部使用 *https* 存在一个已知问题，版本为 2017.4.1f1。 如果视频在播放时出现错误，请尝试改为使用"http"。

8.  接下来， **需要 ()** Start () 方法。 每次用户切换场景时都会触发此方法 (通过查看"凝视"按钮) 切换视频。

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  按照 **Start ()** 方法，插入 **PlayVideo ()** *IEnumerator* 方法，该方法将用于无缝启动视频 (因此) 。

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. 此类所需的最后一个方法是 **ChangeScene ()** 方法，该方法将用于在场景之间交换。

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > **ChangeScene ()** 方法使用一种称为 \# 条件运算符 的便捷 C *功能*。 这允许检查条件，然后根据检查结果返回值，所有这些操作都位于单个语句中。 单击 [此链接可详细了解条件运算符](/dotnet/csharp/language-reference/operators/conditional-operator)。

11. 在返回到 Unity 之前，Visual Studio中的更改。

12. 返回到 Unity 编辑器中，单击 **VideoController** 类 [from]{.underline} 将 **Scripts** 文件夹拖动到"层次结构面板"中的 **Main Camera****对象。**

13. 单击主 **相机并** 查看检查 **器面板**。 你会注意到，在新添加的脚本组件中，有一个空值字段。 这是一个引用字段，它面向代码中的公共变量。

14. 将 **InsideOutSphere** 对象从"层次结构 **面板** "拖动到 **"Sphere"** 槽，如下图所示。

    ![创建 VideoController 类 ](images/AzureLabs-Lab6-47.png)
     ![ 创建 VideoController 类](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>第6章-创建注视类

此类负责创建将从 **主相机** 向前投影的 **Raycast** ，以检测用户正在查看的对象。 在这种情况下， **Raycast** 需要确定用户是否正在查看场景中的 **GazeButton** 对象并触发行为。

若要创建此类：

1.  中转到前面创建的 " **脚本** " 文件夹。

2.  右键单击 " **Project** " 面板中的 "*创建** C \# 脚本"。 将脚本命名为 " **注视**"。

3.  双击新的 * "**注视**" 脚本，用 _ *Visual Studio 2017* 打开它。*

4.  确保以下命名空间位于该脚本的顶部，并删除所有其他命名空间：

    ```csharp
    using UnityEngine;
    ```

5.  然后在 **注视** 类中添加以下变量：

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  现在需要添加 **唤醒 ()** 和 **启动 ()** 方法的代码。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  在 **Update ()** 方法中添加以下代码，以投影 Raycast 并检测目标命中：

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  在返回到 Unity 之前，请将所做的更改保存在 Visual Studio 中。

9.  单击 "脚本" 文件夹中的 " **注视** " 类并将其拖到 " **层次结构** " 面板中的主相机对象。

## <a name="chapter-7---setup-the-two-unity-scenes"></a>第7章-设置两个 Unity 场景

本章的目的是设置两个场景，其中每个都托管要流式传输的视频。 您将复制您已创建的场景，这样您就不需要再次设置它，不过您将编辑新场景，使 *GazeButton* 对象位于不同的位置，并且具有不同的外观。 这是为了说明如何在场景之间进行更改。

1.  为此，请转到 " **文件" > 将场景另存为 ...**"。将显示 "保存" 窗口。 单击 " **新建文件夹** " 按钮。

    ![第7章-设置两个 Unity 场景](images/AzureLabs-Lab6-49.png)

2.  将文件夹命名为 **场景**。

3.  " **保存场景** " 窗口将仍处于打开状态。 打开新创建的 **场景** 文件夹。

4.  在 "文件名 **：** 文本" 字段中，键入 **VideoScene1**，然后按 " **保存**"。

5.  返回 Unity，打开 **场景** 文件夹，然后单击 **VideoScene1** 文件。 使用键盘，并按 **Ctrl + D** 将复制该场景

    > [!TIP]
    > 还可以通过导航到 **编辑 > 重复** 来执行 **重复** 的命令。

6.  Unity 将自动递增场景名称编号，但仍要检查它，以确保它与以前插入的代码匹配。

    >  应该有 **VideoScene1** 和 **VideoScene2**。

7.  对于这两个场景，请参阅 **文件 > 生成设置**。 在 "**生成设置**" 窗口打开的情况下，将场景拖动到 "生成" 部分中的 "**场景**"。

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > 您可以通过按住 **Ctrl** 按钮并单击每个场景，最后拖动两者，从 **场景** 文件夹中选择两个场景。

8.  关闭 "**生成设置**" 窗口，然后双击 " **VideoScene2**"。

9.  在第二个场景打开的情况下，单击 **InsideOutSphere** 的 **GazeButton** 子对象，并按如下所示设置其变换：

    |            |    转换位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1。3         | **Z** 3。6 |

    |            |    转换-旋转   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     转换-缩放     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. 选择 **GazeButton** 子级后，查看 **检查** 器和 **网格筛选器**。 单击 " **网格** 引用" 字段旁边的小目标：

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-51.png)

11. 将显示 " **选择网格** " 弹出窗口。 双击 **资产** 列表中的 **多维数据集** 网格。

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-52.png)

12. **网格筛选器** 将更新，现在为 **多维数据集**。 现在，单击 "**球碰撞** 器" 旁边的 **齿轮** 图标，然后单击 "**删除组件**"，从此对象中删除碰撞器。

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-53.png)

13. 在 **GazeButton** 仍处于选中状态的情况下，单击 **检查器** 底部的 "**添加组件**" 按钮。 在 "搜索" 字段中，键入 **框** 和 **框碰撞** 器将是一个选项，单击此选项可将 **框碰撞** 器添加到 **GazeButton** 对象。

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-54.png)

14. 现在， **GazeButton** 已部分更新，但要看起来不同，但现在你将创建新的 **材料**，使其看起来完全不同，并且更容易识别为不同于第一个场景中的对象的对象。

15. 导航到 " **Project" 面板** 中的 "**材料**" 文件夹。 复制 **ButtonMaterial** 材料 (按  +  键盘上的 Ctrl **D** 或左键单击 **材料**，然后从 "**编辑** 文件" 菜单选项中选择 "**复制**) "。

    ![第7章-设置两个 Unity 场景 ](images/AzureLabs-Lab6-55.png)
     ![ 第7章-设置两个 unity 场景](images/AzureLabs-Lab6-56.png)

16. 选择名为 **ButtonMaterial 1**) 的新 **ButtonMaterial** 材料 (，然后在 **检查器** 中，单击 " **Albedo** 颜色" 窗口。 此时将显示一个弹出窗口，您可以在其中选择其他颜色 (选择) ，然后关闭弹出窗口。 材料将是其自身的实例，并且不同于原始。

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-57.png)

17. 将新 **材料** 拖到 **GazeButton** 子级上，立即完全更新其外观，使其与第一个场景按钮容易区分。

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-58.png)

18. 此时，可以在生成 UWP 项目之前在编辑器中测试项目。

    -  按下 **编辑器** 中的 "**播放**" 按钮，戴上耳机。

        ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-59.png)

19. 查看两个 **GazeButton** 对象，以便在第一个和第二个视频之间切换。

## <a name="chapter-8---build-the-uwp-solution"></a>第8章-构建 UWP 解决方案

确保编辑器没有错误之后，就可以开始生成了。

若要生成：

1.  单击 " **文件" > "保存**"，保存当前场景。

2.  选中名为 " **Unity C \# 项目** (这一点很重要，因为它将允许您在完成生成后编辑类) 。

3.  请参阅 **文件 > 生成设置**，单击 "**生成**"。

4.  系统将提示您选择要在其中生成解决方案的文件夹。

5.  创建一个 **生成** 文件夹，在该文件夹中创建另一个文件夹，其中包含所选的适当名称。

6.  单击新文件夹，然后单击 " **选择文件夹**"，然后选择该文件夹以在该位置开始生成。

    ![第8章-构建 UWP 解决方案 ](images/AzureLabs-Lab6-60.png)
     ![ 第8章-构建 uwp 解决方案](images/AzureLabs-Lab6-61.png)

7.  Unity 完成生成后 (可能需要一些时间) ，它会在生成的位置打开 **文件资源管理器** 窗口。

## <a name="chapter-9---deploy-on-local-machine"></a>第9章-在本地计算机上部署

完成生成后，" **文件资源管理器** " 窗口将出现在生成的位置。 打开名为的文件夹，然后双击该文件夹中的解决方案 ( .sln) 文件，以 Visual Studio 2017 打开解决方案。

唯一要做的事情就是将应用部署到计算机 (或 *本地计算机*) 。

部署到本地计算机：

1.  在 **Visual Studio 2017** 中，打开刚刚创建的解决方案文件。

2.  在 **解决方案平台** 中，选择 " **X86，本地计算机**"。

3.  在 **解决方案配置** 中，选择 " **调试**"。

    ![第9章--在本地计算机上部署](images/AzureLabs-Lab6-62.png)

4.  你现在需要将任何包还原到你的解决方案中。 右键单击 **解决方案**，然后单击 "**还原解决方案 NuGet 包**..."。

    > [!NOTE] 
    > 完成此操作的原因是，需要以 Unity 构建的目标来处理本地计算机引用。

5.  中转到 " **生成" 菜单** ，然后单击 " **部署解决方案** "，将应用程序旁加载到计算机上。 Visual Studio 将首先生成并部署应用程序。

6.  应用现在应显示在已安装的应用列表中，可以启动。

    ![第 9 章 -- 在本地计算机上部署](images/AzureLabs-Lab6-63.png)

运行混合现实应用程序时，你将位于 **在应用中使用的 InsideOutSphere** 模型中。 此球体是视频流式传输到的位置，提供传入视频视频的 360 度视图 (该视频是为此类型的透视视频) 。 如果视频加载需要几秒钟时间，则不要感到意外，因为需要提取并下载视频，以便流式传输到应用中，因此应用会受可用 Internet 速度影响。
准备就绪后，更改场景并打开第二个视频，在红色球体上凝视！ 然后随意返回，使用第二个场景中的蓝色立方体！

## <a name="your-finished-azure-media-service-application"></a>已完成的 Azure 媒体服务应用程序
 
恭喜，你构建了一个混合现实应用，该应用利用 Azure 媒体服务流式传输 360 个视频。

![实验室结果](images/AzureLabs-Lab6-00.png)

![实验室结果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>额外练习

**练习 1**

在本教程中，完全可以使用单个场景来更改视频。 对应用程序进行试验，使其进入单个场景！ 甚至可能向组合中添加另一个视频。

**练习 2**

试验 Azure 和 Unity，并尝试实现应用根据 Internet 连接强度自动选择文件大小不同的视频的能力。