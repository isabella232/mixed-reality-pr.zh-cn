---
title: HoloLens（第一代）和 Azure 302 - 计算机视觉
description: 完成本课程，了解如何在混合现实应用程序中使用 Azure 计算机视觉识别提供的图像中的视觉内容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure， 混合现实， 学院， unity， 教程， api， 计算机视觉， hololens， 沉浸式， vr， Windows 10， Visual Studio
ms.openlocfilehash: 5cac40c2613187776ea9ec5ba1268f1422a084d32322e9c4aca6742ed75d05b2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225918"
---
# <a name="hololens-1st-gen-and-azure-302-computer-vision"></a>HoloLens (第一代) 和 Azure 302：计算机视觉

<br>

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来将发布一系列新的教程，演示如何针对 HoloLens 2。  发布这些教程时，此通知将更新为指向这些教程的链接。

<br>

本课程将学习如何在混合现实应用程序中使用 Azure 计算机视觉识别提供的图像中的视觉内容。

识别结果将显示为描述性标记。 无需训练机器学习模型即可使用此服务。 如果实现需要训练机器学习模型，请参阅 MR[和 Azure 302b。](mr-azure-302b.md)

![实验室结果](images/AzureLabs-Lab2-000.png)

Microsoft 计算机视觉是一组 API，旨在向开发人员提供图像处理和分析 (，以及使用高级) 从云返回信息。 开发人员上传图像或图像 URL，Microsoft 计算机视觉 API 算法根据所选用户的输入分析可视内容，然后可以返回信息，包括识别图像的类型和质量、检测人脸 (返回其坐标) 以及标记图像或对图像进行分类。 有关详细信息，请访问 Azure 计算机视觉 [API 页](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。

完成本课程后，你将拥有一个混合现实HoloLens应用程序，它将能够执行以下操作：

1.  使用点击手势，HoloLens相机将捕获图像。
2.  该映像将发送到 Azure 计算机视觉 API 服务。 
3.  识别的对象将列在 Unity 场景中定位的简单 UI 组中。

在应用程序中，由你决定如何将结果与设计集成。 本课程旨在教授如何将 Azure 服务与 Unity 项目集成。 你的工作是利用从本课程中获得的知识来增强混合现实应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 302：计算机视觉</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 虽然本课程主要重点介绍HoloLens，但也可以将本课程中学习到Windows Mixed Reality VR (头戴显示) 应用。 由于沉浸 (VR) 头戴显示设备没有可访问相机，因此需要将外部相机连接到电脑。 在学习本课程时，你将看到有关可能需要使用的任何更改来支持沉浸式 VR (头戴显示设备) 说明。

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为具有 Unity 和 C# 基本经验的开发人员设计。 另请注意，本文档中的先决条件和书面说明表示截至 2018 年 5 月 2018 年 5 月 (测试和验证的内容) 。 可以随意使用安装工具一文中列出的最新软件，但不应[](../../install-the-tools.md)假定本课程中的信息与下面列出的新软件中的信息完全匹配。

对于本课程，我们建议使用以下硬件和软件：

- 一台开发电脑[，Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 头戴显示设备开发
- [Windows 10 Fall Creators Update (开发人员模式) 或更高版本](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- 已启用[Windows Mixed Reality开发人员模式 (VR](../../../discover/immersive-headset-hardware-details.md)) 头戴显示设备[Microsoft HoloLens](/hololens/hololens1-hardware)沉浸式设备
- 连接到电脑摄像头的相机 (沉浸式头戴显示设备开发) 
- Azure 设置和 API 计算机视觉的 Internet 访问

## <a name="before-you-start"></a>开始之前

1.  为了避免在生成此项目时遇到问题，强烈建议在根文件夹或近根文件夹中创建本教程中提到的项目 (长文件夹路径可能会导致生成时) 。
2.  设置并测试HoloLens。 如果需要支持设置[HoloLens，请确保访问HoloLens设置一文](/hololens/hololens-setup)。 
3.  在开始开发新的 HoloLens App (时，建议执行校准和传感器优化 (有时可以帮助为每个用户应用执行) 。 

有关校准的帮助，请遵循[以下链接，HoloLens校准一文](/hololens/hololens-calibration#hololens-2)。

有关传感器优化的帮助，请遵循此[链接，HoloLens传感器优化一文](/hololens/hololens-updates)。

## <a name="chapter-1--the-azure-portal"></a>第 1 章 - Azure 门户

若要在 Azure *计算机视觉 API* 服务，需要将服务的实例配置为可供应用程序使用。

1.  首先，登录到 Azure [门户](https://portal.azure.com)。 

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室环境中遵循本教程，请询问讲师或其中一位讲师，以帮助设置新帐户。

2.  登录后，单击左上角的"新建"，搜索"计算机视觉 *API"，* 然后单击"**输入"。**

    ![在 Azure 中创建新资源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 在较 **新的** 门户中，"新建"一词可能已被替换为"创建资源"。
 
3.  新页面将提供 API 服务 *计算机视觉说明* 。 在此页左下角， **选择"创建** "按钮，创建与此服务的关联。

    ![关于计算机视觉 API 服务](images/AzureLabs-Lab2-01.png)
 
4.  单击"创建" **后**：

    1. 为此服务 **实例插入** 所需的名称。
    2. 选择一个“订阅”  。
    3. 选择 **适合你的** 定价层，如果这是第一次创建 *计算机视觉 API* 服务，则应该 (名为 F0) 的免费层。
    4. 选择一 **个资源组** 或创建一个新资源组。 资源组提供了一种方法来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将与单个项目关联的所有 Azure 服务 (例如，这些实验室) 位于公共资源组) 。 

        > 若要详细了解 Azure 资源组，请访问 [资源组一文](/azure/azure-resource-manager/resource-group-portal)。

    5. 如果要创建新的资源组组 (，请确定资源组) 。 理想情况下，位置将位于应用程序将运行的区域。 某些 Azure 资产仅在某些区域可用。

    6. 还需要确认你已了解适用于此服务的条款和条件。
    7. 单击“创建”。

        ![服务创建信息](images/AzureLabs-Lab2-02.png)

5.  单击"创建 **"** 后，必须等待服务创建完成，这可能需要一分钟。
6.  创建服务实例后，门户中会显示一条通知。

    ![查看新服务的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  单击通知以浏览新的服务实例。 

    ![选择"转到资源"按钮。](images/AzureLabs-Lab2-04.png)
 
8. 单击 **通知中的"** 转到资源"按钮，浏览新的服务实例。 你将被带至新的 计算机视觉 API 服务实例。 

    ![新的 计算机视觉 API 服务映像](images/AzureLabs-Lab2-05.png)
 
9.  在本教程中，应用程序需要调用服务，这通过使用服务的订阅密钥完成。
10. 在 *计算机视觉 API* 服务的"快速启动"页中，导航到第一步"获取密钥"，然后单击"密钥 **" (** 也可以单击位于服务导航菜单中的蓝色超链接"密钥"（由密钥图标) 表示）来实现此目的。 这将显示 *服务密钥*。
11. 请复制其中一个显示的密钥，因为稍后在项目中需要此密钥。 

12. 返回到"快速 *入门"* 页，然后从该页面提取终结点。 请注意，你的代码可能有所不同，具体取决于 (，如果需要，需要在以后对代码) 。 请复制此终结点，供稍后使用：

    ![新的 计算机视觉 API 服务](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > 可以在此处检查各种终结点[。](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa) 

## <a name="chapter-2--set-up-the-unity-project"></a>第 2 章 - 设置 Unity 项目

下面是使用混合现实进行开发的典型设置，因此，是其他项目的良好模板。

1.  打开 *Unity，* 然后单击"新建 **"。** 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab2-06.png)

2.  现在需要提供 Unity Project名称。 插入 **MR_ComputerVision**。 确保项目类型设置为 **3D**。 将" **位置** "设置为适合你记住 (，越靠近根目录越好) 。 然后单击"创建 **项目"。**

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab2-07.png)

3.  打开 Unity 后，值得检查 **默认脚本编辑器** 是否设置为 **Visual Studio。** 转到"**编辑>首选项"，** 然后在新窗口中导航到"**外部工具"。** 将 **"外部脚本编辑器"****更改为 Visual Studio 2017。** 关闭 **"首选项"** 窗口。

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab2-08.png)

4.  接下来，转到"文件>**生成** 设置并选择"**通用平台Windows"，** 然后单击"切换平台"按钮应用选择。 

    ![生成设置窗口，将平台切换到 UWP。](images/AzureLabs-Lab2-10.png)

5.  仍在"文件 **>生成设置** 并确保：

    1. **目标设备****设置为"HoloLens**

        > 对于沉浸式头戴显示设备，将 **"目标设备"设置为***"任何设备"。*

    2. **生成类型** 设置为 **D3D**
    3. **SDK** 设置为"最新 **安装"**
    4. **Visual Studio版本** 设置为"最新 **安装"**
    5. **"生成和运行** "设置为" **本地计算机"**
    6. 保存场景并将其添加到生成。

        1. 为此，选择"**添加打开的场景"。** 将显示保存窗口。
        
            ![单击"添加打开的场景"按钮](images/AzureLabs-Lab2-11.png)

        2. 为此和任何将来的场景创建新文件夹，然后选择"新建文件夹"按钮，以创建新文件夹，将其命名为 **"场景"。**

            ![创建新脚本文件夹](images/AzureLabs-Lab2-12.png)

        3. 打开新创建的 **"场景**"文件夹，然后在"文件名 *：* 文本"字段中，键入"MR_ComputerVisionScene"，然后单击"保存 **"。** 

            ![为新场景命名。](images/AzureLabs-Lab2-13.png)

            > 请注意，必须将 Unity 场景保存在 *Assets* 文件夹中，因为它们必须与 Unity Project。 创建场景文件夹 (和其他类似文件夹) 是构建 Unity 项目的典型方法。

    7. 目前，"*生成设置中的* 其余设置应保留为默认值。

6. 在"*生成设置* 窗口中，单击"播放器设置按钮，这将在 *检查* 器所在的空间中打开相关面板。 

    ![打开播放器设置。](images/AzureLabs-Lab2-14.png)

7. 在此面板中，需要验证一些设置：

    1. 在"**其他设置** 选项卡中：

        1. **脚本运行时版本****应稳定**（A0.NET 3.5 等效) 。
        2. **脚本后端应为** **.NET**
        3. **API 兼容性级别** 应为 **.NET 4.6**

            ![更新其他设置。](images/AzureLabs-Lab2-15.png)
      
    2. 在"**发布设置** 选项卡中的"**功能"下**，选中：

        1. **InternetClient**
        2. **网络摄像头**

            ![更新发布设置。](images/AzureLabs-Lab2-16.png)

    3. 在面板的下方，在"发布 设置) "下找到的 **"XR** 设置 ("中，勾选"支持虚拟现实"，确保Windows Mixed Reality **SDK。** 

        ![更新 X R 设置。](images/AzureLabs-Lab2-17.png)

8.  返回到 *"生成设置* _Unity C#_ 项目不再灰度;勾选此 旁边的复选框。 
9.  关闭“生成设置”窗口。
10. 保存场景和Project (**文件>保存场景/文件>保存项目**) 。

## <a name="chapter-3--main-camera-setup"></a>第 3 章 - 主相机设置

> [!IMPORTANT]
> 如果要跳过本课程 *的 Unity 设置* 组件，并直接继续编写代码，请随意下载 [此 .unitypackage，](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)将其作为自定义包导入到项目中，然后继续学习 [](https://docs.unity3d.com/Manual/AssetPackages.html)第 [5](#chapter-5--create-the-resultslabel-class)章 。

1.  在"*层次结构面板"中*，选择 **"主相机"。** 
2.  选择后，你将能够在检查器面板 中查看主相机 *的所有组件*。 

    1. Camera **对象必须** 命名为 **Main Camera， (** 拼写！) 
    2. 主相机 **标记** 必须设置为 **MainCamera， (** 拼写！) 
    3. 确保" **转换位置"** 设置为 **0、0、0**
    4. 对于 **沉浸式** 头戴 **显示设备** (，将"清除标志"设置为"纯色") 。
    5. 将相机 **组件的背景** 色设置为黑色 **、Alpha 0 (十六** 进制代码：#00000000)  (沉浸式头戴显示设备时忽略) 。

        ![更新相机组件。](images/AzureLabs-Lab2-18.png)
 
3.  接下来，必须创建附加到主相机 的简单"Cursor"对象，这有助于在应用程序运行时定位图像分析输出。 此光标将确定相机焦点的中心点。

创建游标：

1.  在" *层次结构面板"* 中，右键单击主 **相机**。 在 **"3D 对象"下**，单击 **"Sphere"。**

    ![选择"游标对象"。](images/AzureLabs-Lab2-19.png)
 
2.  将 **Sphere** 重命名为 **光标** (双击 Cursor 对象或按"F2"键盘按钮，其中对象已选择) ，并确保它作为主相机 的 **子级。**

3.  在" *层次结构面板"中*，左键单击 **光标**。 选中"光标"后，在检查器面板中调整 *以下变量*：

    1. 将" *转换位置"设置为* **0、0、5**
    2. 将" *缩放"设置为* **0.02、0.02、0.02**

        ![更新转换位置和缩放。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>第 4 章 - 设置标签系统

使用 HoloLens 相机捕获图像后，该图像将发送到 *Azure 计算机视觉 API* 服务实例进行分析。 

该分析结果将是名为 Tags 的已识别对象 **的列表**。 

你将使用"标签 (作为世界空间中 3D 文本) 在拍摄照片的位置显示这些标记。

以下步骤将展示如何设置 **Label** 对象。

1.  右键单击"层次结构面板"中的任意位置 (此时位置并不重要 **，) "3D** 对象"下添加一个 **3D 文本**。 将它命名 **LabelText**。

    ![创建三维文本对象。](images/AzureLabs-Lab2-21.png)
 
2.  在"*层次结构面板"中*，左键单击 **"LabelText"。** 选中 **LabelText** 后，在检查器面板中调整 *以下变量*：

    1. 将 **"位置"** 设置为 **0，0，0**
    2. 将" **缩放"设置为** **0.01、0.01、0.01**
    3. 在组件 **文本网格中**：
    4. 将 Text 内的所有 **文本替换为**"..."        
    5. 将定位 **点设置为****中间中心**
    6. 将" **对齐方式"** 设置为 **"居中"**
    7. 将选项卡 **大小设置为** **4**
    8. 将 **"字号"设置为****"50"**
    9. 将"**颜色"****设置为#FFFFFFFF**

    ![文本组件](images/AzureLabs-Lab2-21-5.png)

3.  将 **LabelText** 从"层次结构 *面板*"拖动到"资产文件夹"中的"Project *面板"* 中。 这会使 **LabelText** 成为预制件，以便可以在代码中实例化它。

    ![创建 LabelText 对象的预制件。](images/AzureLabs-Lab2-22.png)
 
4.  应从"层次结构面板"中删除 **LabelText，** 以便它不显示在打开的场景中。 由于现在是一个预制，你将从 Assets 文件夹对各个实例调用它，因此无需在场景中保留它。 
5.  层次结构面板中的最终 *对象* 结构应如下图所示：

    ![层次结构面板的最终结构。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>第 5 章 - 创建 ResultsLabel 类

需要创建的第一个脚本是 *ResultsLabel* 类，该类负责以下各项： 

- 在适当的世界空间中创建标签，相对于照相机的位置。
- 显示图像 Analysis 中的标记。

若要创建此类： 

1.  右键单击 " *Project" 面板*，然后 **创建 "> 文件夹**"。 命名文件夹 **脚本**。 

    ![创建脚本文件夹。](images/AzureLabs-Lab2-24.png)

2.  在 " **脚本** " 文件夹中，双击以打开。 然后在该文件夹中，右键单击，然后选择 " **创建 >** 然后选择" **c # 脚本**"。 将脚本命名为 *ResultsLabel*。 

3.  双击新的 " *ResultsLabel* " 脚本，用 **Visual Studio** 打开它。

4.  在类中，在 *ResultsLabel* 类中插入以下代码：

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  返回到 *Unity* 之前，请务必在 *Visual Studio* 中保存所做的更改。
7.  返回 *Unity 编辑器*，单击 "**脚本**" 文件夹中的 *ResultsLabel* 类并将其拖到 "*层次结构" 面板* 中的 **主相机** 对象。
8.  单击 **主摄像机** ，查看 *检查器面板*。

你会注意到，从刚才拖到摄像机的脚本中，有两个字段： **Cursor** 和 **Label Prefab**。

9.  将名为 **cursor** 的对象从 " *层次结构" 面板* 拖动到名为 " **cursor**" 的槽中，如下图所示。
10. 将名为 **LabelText** 的对象从 " *Project" 面板* 中的 "*资产" 文件夹* 拖到名为 **Label Prefab** 的槽中，如下图所示。 

    ![在 Unity 中设置引用目标。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>第6章–创建 ImageCapture 类

要创建的下一个类是 *ImageCapture* 类。 此类负责：

-   使用 HoloLens 相机捕获映像，并将其存储在 App 文件夹中。
-   正在捕获用户的点击手势。

若要创建此类： 

1.  中转到前面创建的 " **脚本** " 文件夹。 
2.  右键单击文件夹内部， **创建 > c # 脚本**。 调用脚本 *ImageCapture*。 
3.  双击新的 " *ImageCapture* " 脚本，用 **Visual Studio** 打开它。
4.  将以下命名空间添加到文件顶部：

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  然后将以下变量添加到 *ImageCapture* 类中，并将其置于 *Start ()* 方法之上：

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount** 变量将存储从用户捕获的攻丝手势的数目。 此编号用于捕获的映像的命名。

6.  现在需要添加 *唤醒 ()* 和 *启动 ()* 方法的代码。 当类初始化时，将调用以下内容：

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  实现一个处理程序，该处理程序将在出现分流手势时调用。 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
*TapHandler ()* 方法会递增从用户捕获的点击次数，并使用当前光标位置确定新标签的位置。

然后，此方法会调用 *ExecuteImageCaptureAndAnalysis ()* 方法来开始此应用程序的核心功能。

8.  捕获并存储映像后，将调用以下处理程序。 如果该过程成功，则会将结果传递给 *VisionManager* (您还需要创建) 进行分析。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  然后添加应用程序用于启动映像捕获进程并存储映像的方法。

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> 此时，你会注意到在 *Unity 编辑器控制台面板* 中出现错误。 这是因为代码引用了将在下一章中创建的 *VisionManager* 类。

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>第7章–调用 Azure 和映像分析

需要创建的最后一个脚本是 *VisionManager* 类。 

此类负责：

-   加载作为字节数组捕获的最新映像。
-   将字节数组发送给 *Azure 计算机视觉 API* 服务实例进行分析。
-   接收 JSON 字符串形式的响应。
-   反序列化响应并将生成的标记传递给 *ResultsLabel* 类。
 
若要创建此类：

1.  双击 " **脚本** " 文件夹以将其打开。 
2.  右键单击 " **脚本** " 文件夹中，单击 " **创建 > c # 脚本**"。 将脚本命名为 *VisionManager*。 
3.  双击新脚本，用 Visual Studio 打开它。
4.  在 *VisionManager* 类的顶部，将命名空间更新为与以下相同：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  在脚本顶部 *("* *开始 ()* 方法) *上方，你* 现在需要创建两个 *类*，用于表示从 Azure 反序列化的 JSON 响应：

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > *TagData* 和 *AnalysedObject* 类需要添加 *[system.exception]* 特性，然后才能使用 Unity 库反序列化声明。

6.  在 VisionManager 类中，应添加以下变量：

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > 请确保将 **身份验证密钥** 插入到 **authorizationKey** 变量。 你将在本课程开头注明 **身份验证密钥** ， [第1章](#chapter-1--the-azure-portal)。

    > [!WARNING] 
    > **VisionAnalysisEndpoint** 变量可能不同于在此示例中指定的变量。 " **美国西部** " 严格指为 "美国西部" 区域创建的服务实例。 用 [终结点 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)更新此值;下面是一些可能的示例：
    > - 西欧： `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 东南亚： `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 澳大利亚东部： `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  现在需要添加用于唤醒的代码。 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  接下来，将协同程序 (与其下面的静态流方法) ，它将获取 *ImageCapture* 类捕获的映像的分析结果。 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  返回到 *Unity* 之前，请务必在 *Visual Studio* 中保存所做的更改。
10. 返回 Unity 编辑器，单击 "**脚本**" 文件夹中的 *VisionManager* 和 *ImageCapture* 类，然后将其拖到 *层次结构面板* 中的 **主相机** 对象。 

## <a name="chapter-8--before-building"></a>第8章–生成之前

若要对应用程序进行全面测试，需要将其旁加载到 HoloLens。
在执行此操作之前，请确保：

-   [第2章](#chapter-2--set-up-the-unity-project)中提到的所有设置都已正确设置。 
-   所有脚本都附加到 **相机** 对象上。 
-   *主相机检查器面板* 中的所有字段均已正确分配。
-   请确保将 **身份验证密钥** 插入到 **authorizationKey** 变量。
-   确保你还在 *VisionManager* 脚本中检查了你的终结点，并将其与 *你* 所在 *的* 区域对齐 (本文档默认使用) 。

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>第9章–构建 UWP 解决方案并旁加载应用程序
此项目的 Unity 部分所需的所有内容现在均已完成，因此可以从 Unity 构建它。

1.  导航到 "*生成" 设置*  -  **文件 > 生成设置 ...**
2.  从 "*生成设置*" 窗口中，单击 "**生成**"。

    ![从 Unity 生成应用](images/AzureLabs-Lab2-26.png)

3.  如果尚未这样做，请勾选 **Unity c # 项目**。
4.  单击“生成”。 Unity 将启动 *文件资源管理器* 窗口，在该窗口中，需要创建一个文件夹，然后选择要在其中生成应用的文件夹。 立即创建该文件夹并将其命名为 *应用*。 选择 *应用* 文件夹后，按 " **选择文件夹**"。 
5.  Unity 将开始向 *应用* 文件夹生成项目。 
6.  Unity 完成生成后 (可能需要一些时间) ，它将在你的生成的位置上打开 " *文件资源管理器* " 窗口 (检查任务栏，因为它可能不会始终出现在 windows 上，但会通知你添加了新的窗口) 。

## <a name="chapter-10--deploy-to-hololens"></a>第10章–部署到 HoloLens

若要在 HoloLens 上部署：

1.  你将需要用于远程部署) 的 HoloLens (的 IP 地址，并确保你的 HoloLens 处于 **开发人员模式**。 若要实现此目的，请执行以下操作：

    1. 在戴 HoloLens 的同时，打开 **设置**。
    2. **Wi-Fi > 高级选项中转到网络 & Internet >**
    3. 记下 **IPv4** 地址。
    4. 接下来，向后导航到 **设置**，然后向 **开发人员更新 & 安全 >** 
    5. 设置开发人员模式。

2.  导航到新的 Unity 生成 (*应用* 文件夹) ，然后用 *Visual Studio* 打开解决方案文件。
3.  在解决方案配置中，选择 " **调试**"。
4.  在解决方案平台中，选择 " **x86**， **远程计算机**"。 

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab2-27.png)
 
5.  请在 "**生成" 菜单** 中，单击 "**部署解决方案**"，将应用程序旁加载到 HoloLens。
6.  现在，你的应用程序应出现在你 HoloLens 上已安装的应用程序列表中，可以启动了！

> [!NOTE]
> 若要部署到沉浸式耳机，请将 " **解决方案平台** " 设置为 " *本地计算机*"，并将 **配置** 设置为 " *调试*"，将 " *x86* " 设置为 **平台**。 然后，使用 " **生成" 菜单** 选择 " *部署解决方案*"，将部署到本地计算机。 

## <a name="your-finished-computer-vision-api-application"></a>已完成的计算机视觉 API 应用程序

恭喜，你构建了一个使用 Azure 计算机视觉 API 来识别真实世界对象的混合现实应用，并清楚地显示了所见的内容。

![实验室结果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习 1

正如你在 *VisionManager*) 内使用的 *终结点* 中使用了 *Tags* 参数 (作为出现，扩展应用程序以检测其他信息;查看你可以 [访问的其他参数。](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)

### <a name="exercise-2"></a>练习 2

显示返回的 Azure 数据，其显示方式更多，而且可能会隐藏数字。 如机器人可能对用户讲话。