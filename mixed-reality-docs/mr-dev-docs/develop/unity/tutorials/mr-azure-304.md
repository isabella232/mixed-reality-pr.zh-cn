---
title: HoloLens（第一代）和 Azure 304 - 人脸识别
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure， 混合现实， 学院， unity， 教程， api， 人脸识别， hololens， 沉浸式， vr， Windows 10， Visual Studio
ms.openlocfilehash: 2547b61669884c524fdd605240322dc9d568039b5a202d0a411317b0e83bd547
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219442"
---
# <a name="hololens-1st-gen-and-azure-304-face-recognition"></a>HoloLens (第一代) Azure 304：人脸识别

<br>

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来将发布一系列新的教程，演示如何针对 HoloLens 2。  发布这些教程时，此通知将更新为指向这些教程的链接。

<br>

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

本课程将学习如何通过 Microsoft 人脸 API 使用 Azure 认知服务 向混合现实应用程序添加人脸识别功能。

*Azure 人脸 API* 是一项 Microsoft 服务，它为开发人员提供最先进的人脸算法，所有这些算法都位于云中。 人脸 *API* 有两个主要功能：使用属性进行人脸检测和人脸识别。 这样，开发人员只需为人脸设置一组组，然后稍后将查询图像发送到服务，以确定人脸所属的人员。 有关详细信息，请访问 Azure [人脸识别页](https://azure.microsoft.com/services/cognitive-services/face/)。

完成本课程后，你将拥有一个混合现实HoloLens应用程序，它将能够执行以下操作：

1. 使用 **板载** 相机和相机，使用点击手势HoloLens图像。 
2. 将捕获的图像发送到 Azure *人脸 API* 服务。
3. 接收人脸 API *算法* 的结果。
4. 使用简单的用户界面显示匹配人员的名称。

这将指导如何将人脸 API 服务的结果获取到基于 Unity 的混合现实应用程序中。

在应用程序中，由你决定如何将结果与设计集成。 本课程旨在教授如何将 Azure 服务与 Unity Project。 你的工作是利用从本课程中获得的知识来增强混合现实应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 304：人脸识别</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 虽然本课程主要重点介绍HoloLens，但也可以将本课程中学习到Windows Mixed Reality VR (头戴显示) 应用。 由于沉浸 (VR) 头戴显示设备没有可访问相机，因此需要将外部相机连接到电脑。 在学习本课程时，你将看到有关可能需要使用的任何更改来支持沉浸式 VR (头戴显示设备) 说明。

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
- 连接到电脑摄像头的相机 (沉浸式头戴显示设备开发) 
- 用于 Azure 设置和人脸 API 检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

1.  为了避免在生成此项目时遇到问题，强烈建议在根文件夹或近根文件夹中创建本教程中提到的项目 (长文件夹路径可能会导致生成时) 。
2.  设置并测试HoloLens。 如果需要支持设置[HoloLens，请确保访问HoloLens设置一文](/hololens/hololens-setup)。 
3.  在开始开发新的 HoloLens App (时，建议执行校准和传感器优化 (有时可以帮助为每个用户应用执行) 。 

有关校准的帮助，请遵循[以下链接，HoloLens校准一文](/hololens/hololens-calibration#hololens-2)。

有关传感器优化的帮助，请遵循此[链接，HoloLens传感器优化一文](/hololens/hololens-updates)。

## <a name="chapter-1---the-azure-portal"></a>第 1 章 - Azure 门户

若要在 Azure 中使用人脸 *API* 服务，需要将服务的实例配置为可供应用程序使用。

1.  首先，登录到 Azure [门户](https://portal.azure.com)。 

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室环境中遵循本教程，请询问讲师或其中一位讲师，以帮助设置新帐户。

2.  登录后，单击左上角的"新建"，搜索"*人脸 API"，* 然后 **按 Enter**。 

    ![搜索人脸 API](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 在较 **新的** 门户中，"新建"一词可能已被替换为"创建资源"。

3.  新页面将提供人脸 *API 服务* 的说明。 在此提示的左下角， **选择"创建** "按钮，创建与此服务的关联。

    ![人脸 API 信息](images/AzureLabs-Lab4-02.png)

4.  单击"创建" **后**：

    1. 插入此服务实例的所需名称。

    2. 选择一个订阅。

    3. 选择适合你的定价层，如果这是首次创建人脸 *API* 服务， (F0) 免费层。

    4. 选择一 **个资源组** 或创建一个新资源组。 资源组提供了一种方法来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将与单个项目关联的所有 Azure 服务 (例如，这些实验室) 位于公共资源组) 。 

        > 若要详细了解 Azure 资源组，请访问 [资源组一文](/azure/azure-resource-manager/resource-group-portal)。

    5. 稍后使用的 UWP 应用 **Person Maker** 需要使用"美国西部"作为位置。

    6. 还需要确认你已了解适用于此服务的条款和条件。

    7. 选择" **创建"*。**

        ![创建人脸 API 服务](images/AzureLabs-Lab4-03.png)

5.  单击"创建 **"*** 后，必须等待服务创建完成，这可能需要一分钟。

6.  创建服务实例后，门户中会显示一条通知。

    ![服务创建通知](images/AzureLabs-Lab4-04.png)

7.  单击通知以浏览新的服务实例。

    ![转到资源通知](images/AzureLabs-Lab4-05.png)

8.  准备就绪后，单击通知 **中的"转到资源** "按钮，浏览新的服务实例。

    ![访问人脸 API 密钥](images/AzureLabs-Lab4-06.png)

9.  在本教程中，应用程序需要调用服务，这通过使用服务的订阅"密钥"完成。 在 *人脸 API 服务的* "快速入门" *页* 中，第一个点是数字 1，即 *"抓取密钥"。*

10. 在"服务"页上，选择蓝色"密钥"超链接 (（如果在"快速启动"页) 上），或者选择左侧服务导航菜单中的"密钥"链接 (（由"密钥"图标) 表示）以显示密钥。 

    > [!NOTE] 
    > 请记下其中一个密钥并保护它，因为稍后需要它。

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>第 2 章 - 使用"Person Maker"UWP 应用程序

请确保下载名为 Person Maker 的预创建 UWP [应用程序](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)。 此应用不是本课程的最终产品，只是一个可帮助你创建 Azure 条目的工具，下一个项目将依赖它。

**Person Maker** 允许创建与人员以及人员组关联的 Azure 条目。 应用程序会以格式放置所有所需信息，稍后人脸API 可以使用该格式，以便识别已添加的人脸。 

> [重要] **Person Maker** 使用一些基本限制来帮助确保不超过免费订阅层 每分钟的服务 **调用数**。 发生限制时，顶部的绿色文本将更改为红色，并更新为"ACTIVE";如果是这种情况，只需等待应用程序 (等待应用程序继续访问人脸服务，在可以再次使用人脸服务时更新为"in-ACTIVE") 。

此应用程序使用 *Microsoft.ProjectOxford.Face* 库，这允许你充分利用人脸 API。 此库以包包NuGet提供。 有关此内容以及类似的详细信息，API [请确保访问 API 参考文章](/azure/cognitive-services/face/apireference)。

> [!NOTE] 
> 这些只是所需步骤，有关如何执行这些操作的说明会进一步介绍文档。 **Person Maker** 应用将允许你：
>
> - 创建 *人员组*，该组由多个要与该组关联的人员组成。 使用 Azure 帐户可以托管多个人员组。
>
> - 创建 *Person*，它是人员组的成员。 每个人都有一些 *与之* 关联的人脸图像。
>
> -  将 *人脸图像* 分配给 *人员*，以允许 Azure 人脸 API 服务通过相应的人脸 识别 *人员*。
>
> -  *训练* *Azure 人脸 API 服务*。

请注意，若要训练此应用以识别人员，需要 10 (10) 要添加到人员组的每一个人的照片。 Windows 10 Cam 应用可帮助你实现这些操作。 必须确保每张照片都清晰 (避免模糊、模糊或离主题) 太远，使照片采用 jpg 或 png 文件格式，且图像文件大小不大于 **4 MB，** 且不能小于 **1 KB。**

> [!NOTE]
> 如果按照本教程操作，请不要使用自己的人脸进行训练，因为当你打开HoloLens时，无法查看自己。 使用同事或同事的人脸。

运行 **Person Maker：**

1.  打开 **PersonMaker** 文件夹，然后双击 *PersonMaker 解决方案*，使用 *Visual Studio。*

2.  打开 *PersonMaker 解决方案* 后，请确保：

    1. "*解决方案配置*"设置为"调试 **"。**

    2. 解决方案 *平台* 设置为 **x86**

    3. 目标 *平台* 是 **本地计算机**。

    4.  可能还需要在 *"还原NuGet* 包 (解决方案 *"，* 然后选择"还原NuGet **包**) 。

3.  单击 *"本地计算机* "，应用程序将启动。 请注意，在较小的屏幕上，所有内容可能不可见，但你可以进一步向下滚动以查看它。

    ![person maker 用户界面](images/AzureLabs-Lab4-07.png)

4.  从 **Azure 中的** 人脸 *API* 服务插入应具有的 Azure 身份验证密钥。

5.  插入：

    1. 要分配给人员组的 *ID。*  ID 必须小写，无空格。 请记下此 ID，因为稍后在 Unity 项目中需要此 ID。
    2. 要 *分配给* 人员组名称 *的名称 (具有* 空格) 。


6.  按 **"创建人员组"** 按钮。 按钮下方应会显示一条确认消息。

> [!NOTE]
> 如果出现错误"拒绝访问"，请检查为 Azure 服务设置的位置。 如上所述，此应用专为"美国西部"设计。

> [!IMPORTANT]
> 你会注意到，还可以单击"提取已知组"按钮：如果已创建人员组，并且想要使用该组，则此按钮适用于 ，而不是创建新的组。 请注意，如果单击 *"使用* 已知组创建人员组"，也会提取组。

7.  插入 *要* 创建 *的人* 的名称。

    1. 单击" **创建人员"** 按钮。

    2. 按钮下方应会显示一条确认消息。

    3. 如果要删除之前创建的人，可以将名称写入文本框，然后按" **删除人员"**

8.  请确保你知道要添加到组 (10) 10 张照片的位置。

9.  按 **"创建并打开** 文件夹"，Windows资源管理器打开与人员关联的文件夹。 在 文件夹中 (10) 10 个图像。 这些必须采用 *JPG* 或 *PNG* 文件格式。

10. 单击"**提交到 Azure"。** 计数器会显示提交状态，完成后后跟消息。

11. 计数器完成后，显示确认消息后，单击" **训练** "以训练服务。

完成该过程后，即可进入 Unity。

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章 - 设置 Unity 项目

下面是使用混合现实进行开发的典型设置，因此，是其他项目的良好模板。

1.  打开 *Unity，* 然后单击"新建 **"。** 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab4-08.png)

2.  现在需要提供 Unity Project名称。 插入 **MR_FaceRecognition**。 确保项目类型设置为 **3D**。 将" **位置** "设置为适合你记住 (，越靠近根目录越好) 。 然后单击"创建 **项目"。**

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab4-09.png)

3.  打开 Unity 后，值得检查 **默认脚本编辑器** 是否设置为 **Visual Studio。** 转到"**编辑>首选项"，** 然后在新窗口中导航到"**外部工具"。** 将 **"外部脚本编辑器"****更改为 Visual Studio 2017。** 关闭 **"首选项"** 窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab4-10.png)

4.  接下来，单击 **"切换>"设置"，** 转到"文件"Windows"平台"，将平台切换到"**通用平台**"。

    ![生成设置窗口，将平台切换到 UWP。](images/AzureLabs-Lab4-11.png)

5.  转到"**文件>生成设置** 并确保：

    1. **目标设备****设置为"HoloLens**

        > 对于沉浸式头戴显示设备，将 **"目标设备"设置为***"任何设备"。*

    2. **生成类型** 设置为 **D3D**
    3. **SDK** 设置为"最新 **安装"**
    4. **Visual Studio版本** 设置为"最新 **安装"**
    5. **"生成和运行** "设置为" **本地计算机"**
    6. 保存场景并将其添加到生成。 

        1. 为此，选择"**添加打开的场景"。** 将显示保存窗口。

            ![单击"添加打开的场景"按钮](images/AzureLabs-Lab4-12.png)

        2. 选择"**新建文件夹"** 按钮以创建新文件夹，将其命名为 **"场景"。**

            ![创建新脚本文件夹](images/AzureLabs-Lab4-13.png)

        3. 打开新创建的 **"场景**"文件夹，然后在"文件名 **：** 文本"字段中，键入 **FaceRecScene，** 然后按"**保存"。**

            ![为新场景命名。](images/AzureLabs-Lab4-14.png)

    7. 目前，"*生成设置中的* 其余设置应保留为默认值。

6. 在"*生成设置* 窗口中，单击"播放器设置按钮，这将在 *检查* 器所在的空间中打开相关面板。 

    ![打开播放器设置。](images/AzureLabs-Lab4-15.png)

7. 在此面板中，需要验证一些设置：

    1. 在"**其他设置** 选项卡中：

        1. **脚本运行时****版本****应为实验性**（A0.NET 4.6 等效) 。 更改此选项将触发重启编辑器。
        2. **脚本后端应为** **.NET**
        3. **API 兼容性级别** 应为 **.NET 4.6**

            ![更新其他设置。](images/AzureLabs-Lab4-16.png)
      
    2. 在"**发布设置** 选项卡中的"**功能"下**，选中：

        - **InternetClient**
        - **网络摄像头**

            ![更新发布设置。](images/AzureLabs-Lab4-17.png)

    3. 在面板的下方，在"发布 设置) "下找到的 **"XR** 设置 ("中，勾选"支持虚拟现实"，确保Windows Mixed Reality **SDK。** 

        ![更新 X R 设置。](images/AzureLabs-Lab4-18.png)

8.  返回到生成 *设置，Unity* **C#** 项目不再灰暗;勾选此 旁边的复选框。 
9.  关闭“生成设置”窗口。
10. 保存场景和Project (**文件>保存场景/文件>保存项目**) 。

## <a name="chapter-4---main-camera-setup"></a>第 4 章 - 主相机设置

> [!IMPORTANT]
> 如果要跳过本课程 *的 Unity 设置* 组件，并直接继续编写代码，请随意下载此 [.unitypackage，](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)并作为自定义包将其导入 [项目中](https://docs.unity3d.com/Manual/AssetPackages.html)。 请注意，此包还包括 *导入 Newtonsoft DLL，* 如第 [5 章中介绍](#chapter-5--import-the-newtonsoftjson-library)。 导入此 后，可以从第 [6 章 继续](#chapter-6---create-the-faceanalysis-class)。

1.  在"*层次结构面板"* 中，选择 **"主相机"。**

2.  选择后，你将能够在检查器面板 中查看主相机 *的所有组件*。 

    1. Camera **对象必须** 命名为 **Main Camera， (** 拼写！) 

    2. 主相机 **标记** 必须设置为 **MainCamera， (** 拼写！) 

    3. 确保" **转换位置"** 设置为 **0、0、0**

    4. 将 **"清除标志"****设置为纯色**

    5. 将" **相机组件的背景** 色"设置为 **"黑色，Alpha 0" (十六进制代码：#00000000)**

        ![设置相机组件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>第 5 章 – 导入 Newtonsoft.Json 库

> [!IMPORTANT]
> 如果在上一章中导入了".unitypackage"，可以跳过本章。 [](#chapter-4---main-camera-setup)

若要帮助反序列化接收并发送到机器人服务的对象，需要下载Newtonsoft.Js *文件* 。 你将在此 Unity 包文件中找到已使用正确的 Unity 文件夹结构 [组织的兼容版本](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)。 

导入库：

1.  下载 Unity 包。
2.  单击"**资产****"，"导入包"** 和 **"自定义包"。**

    ![导入Newtonsoft.Js打开](images/AzureLabs-Lab4-20.png)

3.  查找已下载的 Unity 包，然后单击"打开"。
4.  确保已勾选包的所有组件，然后单击"导入 **"。**

    ![导入Newtonsoft.Js的导入](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>第 6 章 - 创建 FaceAnalysis 类

FaceAnalysis 类的目的是托管与 Azure 人脸识别服务通信所需的方法。 

- 向服务发送捕获图像后，它会分析该图像并识别其中人脸，并确定其中是否有人脸属于已知人员。 
- 如果找到已知人员，此类将在场景中以 UI 文本显示其名称。

创建 *FaceAnalysis* 类：

 1. 右键单击 *位于"资产*"面板中的"资产Project，然后单击"创建 **文件夹**  >  **"。** 调用文件夹 **Scripts**。 

    ![创建 FaceAnalysis 类。](images/AzureLabs-Lab4-22.png)

2.  双击刚刚创建的文件夹，打开它。 
3.  右键单击文件夹内，然后单击"创建  >  **C# 脚本"。** 调用脚本 *FaceAnalysis*。 
4.  双击新的 *FaceAnalysis* 脚本，使用 Visual Studio 2017 打开它。
5.  在 *FaceAnalysis* 类上方输入以下命名空间：

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  现在需要添加用于反反初始化的所有 对象。 这些对象 **需要添加到***FaceAnalysis* 脚本脚本 (括号下) 。 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. "*启动 ()**和更新 ()* 方法不会使用，因此立即删除它们。 

8.  在 *FaceAnalysis* 类中，添加以下变量：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > 将 **密钥和** **personGroupId** 替换为服务密钥以及之前创建的组的 ID。

9.  添加 *"唤醒 ()* 方法，该方法初始化 类，将 *ImageCapture* 类添加到主相机并调用 Label 创建方法：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. 添加 *CreateLabel ()* 方法，该方法创建 *Label* 对象以显示分析结果：

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. 添加 *DetectFacesFromImage ()* *GetImageAsByteArray ()* 方法。 前者将请求人脸识别服务检测所提交图像中任何可能的人脸，而后者是将捕获的图像转换为字节数组所必需的：

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. 添加 *IdentifyFaces ()* 方法，该方法请求人脸识别服务识别以前在提交的图像中检测到的任何已知人脸。 请求将返回已标识的人的 ID，而不是姓名：

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. 添加 *GetPerson ()* 方法。 通过提供人员 ID，此方法随后请求人脸识别服务返回已标识人员的姓名：

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  请记得 **在** 返回到 Unity 编辑器之前保存更改。
15.  在 Unity 编辑器中，将 FaceAnalysis 脚本从 Project 面板中的 Scripts 文件夹拖动到"层次结构"面板 *中的 Main* Camera 对象。 新的脚本组件将添加到主相机。 

![将 FaceAnalysis 放在主相机上](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>第 7 章 - 创建 ImageCapture 类

*ImageCapture* 类的目的是托管与 *Azure* 人脸识别服务通信所需的方法，以分析要捕获的图像，识别图像中的人脸，并确定该图像是否属于已知人员。 如果找到已知人员，此类将在场景中以 UI 文本显示其名称。

创建 *ImageCapture* 类：
 
1.  右键单击之前 **创建的"脚本**"文件夹，然后单击"**创建**"，**然后单击"C# 脚本"。** 调用脚本 *ImageCapture*。 
2.  双击新的 *ImageCapture* 脚本，使用 Visual Studio 2017 打开它。
3.  在 ImageCapture 类上方输入以下命名空间：

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  在 *ImageCapture* 类中，添加以下变量：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  添加 *"唤醒 () "* 和"启动 () 初始化类所需的方法，并允许HoloLens捕获用户的手势：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  添加 *TapHandler ()* 用户执行点击手势 *时调用它* ：

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  添加 *ExecuteImageCaptureAndAnalysis ()* 方法，该方法将开始映像捕获过程：

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  添加在照片捕获过程完成时调用的处理程序：

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. 请记得 **在** 返回到 Unity 编辑器之前保存更改。

## <a name="chapter-8---building-the-solution"></a>第 8 章 - 生成解决方案

若要对应用程序执行全面测试，需要将应用程序旁加载到HoloLens。

在这样做之前，请确保：

-   第 3 章中提到的所有设置均正确设置。 
-   脚本 *FaceAnalysis* 附加到 Main Camera 对象。 
-   已在 *FaceAnalysis* 脚本中设置身份验证密钥和组 ID。 

此时，你已准备好生成解决方案。 生成解决方案后，即可部署应用程序。

开始生成过程：

1.  单击"文件""保存"，保存当前场景。
2.  转到"文件"，设置，单击"添加打开场景"。
3.  请确保勾选"Unity C# 项目"。

    ![部署 Visual Studio 解决方案](images/AzureLabs-Lab4-24.png)

4.  按"生成"。 执行此操作后，Unity 将启动文件资源管理器窗口，你需要创建该窗口，然后选择要生成应用的文件夹。 现在，在 Unity 项目中创建该文件夹，并调用它"应用"。 然后选择"应用"文件夹后，按"选择文件夹"。 
5.  Unity 将开始生成项目，到"应用"文件夹。 
6.  Unity 完成生成 (可能需要一) ，它会在生成文件资源管理器打开一个窗口。

    ![从部署解决方案Visual Studio](images/AzureLabs-Lab4-25.png)

7.  打开 App 文件夹，然后打开新的 Project 解决方案 (，如上所示，MR_FaceRecognition.sln) 。


## <a name="chapter-9---deploying-your-application"></a>第 9 章 - 部署应用程序

若要在 HoloLens：

1.  需要远程部署HoloLens (IP 地址) ，并确保HoloLens开发人员 **模式**。 若要实现此目的，请执行以下操作：

    1. 一边HoloLens，一边 **打开设置。**
    2. 转到" **网络& Internet > Wi-Fi >高级选项"**
    3. 记下 **IPv4** 地址。
    4. 接下来，导航回 **设置，** 然后导航到 **"更新 & Security > For Developers"** 
    5. 将"开发人员模式"设置为"打开"。

2.  导航到"应用"文件夹 (*新的* Unity) ，然后使用 Visual Studio 打开 *解决方案文件*。
3.  在"解决方案配置"中，选择"**调试"。**
4.  在"解决方案平台"中，选择 **"x86**"**远程计算机"。** 

    ![更改解决方案配置](images/AzureLabs-Lab4-26.png)
 
5.  转到"**生成"菜单** 并单击"部署 **解决方案**"，将应用程序旁加载到HoloLens。
6.  应用现在应显示在应用程序上安装的应用列表中HoloLens，可以启动！

> [!NOTE]
> 若要部署到沉浸式头戴显示设备，将"解决方案平台"设置为"*本地计算机*"，将"配置"设置为"调试"，将 *x86* 设置为 **"平台"。** 然后，使用"生成"菜单，选择"部署解决方案"*部署到本地计算机*。 


## <a name="chapter-10---using-the-application"></a>第 10 章 - 使用应用程序

1.  在HoloLens，启动应用。
2.  查看已注册人脸 *API 的人*。 请确保：

    -  人脸不是太远且清晰可见
    -  环境照明不太暗

3.  使用点击手势捕获人员的照片。
4.  等待应用发送分析请求并接收响应。
5.  如果已成功识别该人员，该人员的姓名将显示为 UI 文本。
6.  可以每隔几秒钟使用点击手势重复捕获过程。

## <a name="your-finished-azure-face-api-application"></a>已完成的 Azure 人脸 API 应用程序

恭喜，你构建了一个混合现实应用，该应用利用 Azure 人脸识别服务来检测图像中的人脸，并识别任何已知人脸。

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习 1

**Azure 人脸 API** 功能强大，可检测单个图像中最多 64 张人脸。 扩展应用程序，以便它可以识别许多其他人中的两个或三张人脸。

### <a name="exercise-2"></a>练习 2

**Azure 人脸 API** 还可以提供各种类型的属性信息。 将其集成到应用程序中。 与情感 API 结合使用时，这可能更 [有趣](https://azure.microsoft.com/services/cognitive-services/emotion/)。