---
title: HoloLens（第一代）和 Azure 310 - 物体检测
description: 完成本课程，了解如何定型和使用机器学习模型来识别相似对象及其在实际中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，自定义视觉对象，对象检测，混合现实，学院，unity，教程，api，hololens，Windows 10，Visual Studio
ms.openlocfilehash: 85a99b676f6765696524bc42adf257b3430c00cc955413b4c299ddb58502cefb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216532"
---
# <a name="hololens-1st-gen-and-azure-310-object-detection"></a>HoloLens (第一代) 和 Azure 310：对象检测

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

在本课程中，你将了解如何在混合现实应用程序中使用 Azure 自定义视觉 "对象检测" 功能来识别所提供的映像中的自定义视觉对象内容及其空间位置。

此服务允许你使用对象图像训练机器学习模型。 然后，您将使用训练的模型来识别类似对象并大致了解其在现实世界中的位置，如 Microsoft HoloLens 的照相机捕获提供，或照相机连接到用于沉浸式 (VR) 耳机的电脑。

![课程结果](images/AzureLabs-Lab310-00.png)

**Azure 自定义视觉中，对象检测** 是一种 Microsoft 服务，它允许开发人员构建自定义映像分类器。 然后，可以将这些分类器用于新的图像，通过在图像本身中提供 **框边界** 来检测该新图像内的对象。 此服务提供简单易用的联机门户来简化此过程。 有关详细信息，请访问以下链接：

* [Azure 自定义视觉页面](/azure/cognitive-services/custom-vision-service/home)
* [限制和配额](/azure/cognitive-services/custom-vision-service/limits-and-quotas)

完成本课程后，你将拥有一个混合现实应用程序，该应用程序将能够执行以下操作：

1. 用户将可以 *注视* 使用 Azure 自定义影像服务、对象检测训练的对象。 
2. 用户将使用 *点击* 手势来捕获所查看内容的图像。
3. 应用会将映像发送到 Azure 自定义影像服务。
4. 此时会显示服务的答复，该服务会将识别结果显示为世界空间文本。 这将通过利用 Microsoft HoloLens 的空间跟踪来实现，这是为了了解识别对象的世界位置，然后使用与在图像中检测到的内容关联的 *标记* 来提供标签文本。

本课程还将介绍如何手动上传图像、创建标记和培训服务，通过在提交的图像中设置 *边界框* 来识别提供的) 示例中 (的不同对象。 

> [!IMPORTANT]
> 创建和使用应用后，开发人员应导航回 Azure 自定义影像服务，并确定该服务所进行的预测，并通过标记缺少的任何内容来确定其是否正确或未 (，并) 调整 *边界框* 。 然后，可以对服务进行重新训练，这会增加识别真实世界对象的可能性。

本课程将介绍如何从 Azure 自定义影像服务、对象检测到基于 Unity 的示例应用程序中获取结果。 您可以将这些概念应用到您可能生成的自定义应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 310：对象检测</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>先决条件

> [!NOTE]
> 本教程专为具有 Unity 和 c # 基本经验的开发人员设计。 请注意，本文档中的先决条件和书面说明表示在) 2018 年7月 (撰写本文时已测试和验证的内容。 你可以随意使用最新的软件（如 [安装工具](../../install-the-tools.md) 一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件：

- 开发 PC
- [启用开发人员模式 Windows 10 Fall Creators Update (或更高版本) ](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [最新的 Windows 10 SDK](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- 已启用开发人员模式[Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details)
- Azure 安装和自定义影像服务检索的 Internet 访问
-  对于希望自定义视觉识别的每个对象) ，需要一系列至少15个 (15) 的图像。 如果需要，可以使用本课程提供的映像， [一系列 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) 。

## <a name="before-you-start"></a>开始之前

1.  若要避免在生成此项目时遇到问题，强烈建议你在根或近乎根文件夹中创建本教程中所述的项目 (长文件夹路径在生成时) 会导致问题。
2.  设置并测试 HoloLens。 如果需要支持设置 HoloLens，请[确保访问 HoloLens 安装程序一文](/hololens/hololens-setup)。 
3.  在开始开发新的 HoloLens 应用程序时，最好执行校准和传感器调整 (有时，它可以帮助为每个用户) 执行这些任务。 

有关校准的帮助信息，请访问[HoloLens 校准文章](/hololens/hololens-calibration#hololens-2)。

有关传感器优化的帮助，请访问[HoloLens 传感器优化文章](/hololens/hololens-updates)。

## <a name="chapter-1---the-custom-vision-portal"></a>第1章-自定义视觉门户

若要使用 **Azure 自定义影像服务**，你将需要配置该应用程序的实例。

1.  导航 [到 **自定义影像服务** 主页](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  单击 **入门**。

    ![](images/AzureLabs-Lab310-01.png)

3.  登录到自定义视觉门户。

    ![](images/AzureLabs-Lab310-02.png)

4.  如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。

5.  首次登录后，系统会提示 " *服务* " 面板。 单击复选框以 *同意条款*。 然后单击 " **我同意**"。

    ![](images/AzureLabs-Lab310-03.png)

6.  如果同意这些条款，你现在已在 " *我的项目* " 部分。 单击 "**新建 Project**"。

    ![](images/AzureLabs-Lab310-04.png)

7.  右侧将显示一个选项卡，该选项卡将提示你为项目指定某些字段。

    1.  插入项目的名称

    2.  为项目插入说明 (**可选**) 

    3.  选择一个 **资源组** ，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议保留与单个项目关联的所有 Azure 服务 (例如，这些课程) 常用资源组) 下。

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > 若要 [阅读有关 Azure 资源组的详细信息，请导航到相关文档](/azure/azure-resource-manager/resource-group-portal)

    4.  **(preview)** 将 **Project 类型** 设置为对象检测。

8.  完成后，单击 " **创建项目**"，将重定向到 "自定义影像服务项目" 页面。


## <a name="chapter-2---training-your-custom-vision-project"></a>第2章-培训自定义视觉项目

在自定义视觉门户中，你的主要目标是训练你的项目以识别图像中的特定对象。

对于你希望应用程序识别的每个对象，你需要至少15个 (15) 映像。 您可以使用本课程附带的图像 ([一系列 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) 。

训练自定义视觉项目：

1.  单击 " **+** **标记**" 旁边的按钮。

    ![](images/AzureLabs-Lab310-06.png)

2.  添加用于将图像与相关联的标记的 **名称** 。 在此示例中，我们将使用 cup 的图像进行识别，因此已为此、 **杯** 命名了标记。 完成后单击 " **保存** "。

    ![](images/AzureLabs-Lab310-07.png)

3.  你将注意到已添加 **标记** (你可能需要重新加载页面以使其) 显示。 

    ![](images/AzureLabs-Lab310-08.png)

4.  单击页中心的 " **添加图像** "。

    ![](images/AzureLabs-Lab310-09.png)

5.  单击 " **浏览本地文件**"，然后浏览到要为一个对象上传的图像，最小为十五 (15) 。

    > [!TIP]
    >  你可以一次选择多个图像来上传。

    ![](images/AzureLabs-Lab310-10.png)

6.  选择要对项目定型的所有映像后，按 **Upload 文件**。 文件将开始上传。 确认上传后，单击 " **完成**"。

    ![](images/AzureLabs-Lab310-11.png)

7.  此时，将上载映像，但不会对其进行标记。

    ![](images/AzureLabs-Lab310-12.png)

8.  若要为图像标记，请使用鼠标。 当你将鼠标指针悬停在图像上时，选择突出显示将帮助你在对象周围自动绘制选定内容。 如果它不准确，可以自行绘制。 为此，请按住鼠标左键并拖动选择区域以包含您的对象。 

    ![](images/AzureLabs-Lab310-13.png) 

9. 在图像中选择对象后，一个小提示会要求你添加 *区域标记*。 选择前面创建的标记 ('Cup'，在以上示例中选择") "，或者如果要添加更多标记，请在 中键入该标记，然后单击 **"+ (+) "** 按钮。

    ![](images/AzureLabs-Lab310-14.png) 

10. 若要标记下一个图像，可以单击边栏选项卡右侧箭头，或单击边栏选项卡右上角的 **X** (关闭标记边栏选项卡) 然后单击下一个图像。 准备好下一个映像后，重复相同的过程。 对已上传的所有图像执行此操作，直到它们全部标记。 

    > [!NOTE]
    >  可以在同一图像中选择多个对象，如下图所示： 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. 标记所有图像后，单击屏幕左侧的标记按钮以显示标记的图像。 

    ![](images/AzureLabs-Lab310-16.png)

12. 现在可以训练服务了。 单击" **训练"** 按钮，将开始第一个训练迭代。

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. 生成后，你将能够看到两个按钮，称为"默认"和"**预测 URL"。** 首先单击 **"默认"，** 然后单击"预测 **URL"。**

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > 从此 提供的终结点设置为任何 *已标记为* 默认迭代的迭代。 因此，如果以后进行新的迭代并更新为默认值，则无需更改代码。

14. 单击"预测 **URL"** 后，打开 *记事本，* 然后复制并粘贴 **URL** (也称为预测终结点 **)** 和服务 **预测** 密钥，以便稍后在代码中需要它时检索它。

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第 3 章 - 设置 Unity 项目

下面是使用混合现实进行开发的典型设置，因此，是其他项目的良好模板。

1.  打开 **Unity，** 然后单击"新建 **"。**

    ![](images/AzureLabs-Lab310-21.png)

2.  现在需要提供 Unity 项目名称。 插入 **CustomVisionObjDetection**。 请确保项目类型设置为 **3D**，并且将"位置"设置为适合你记住 (的位置，越接近根目录) 。 然后单击"创建 **项目"。**

    ![](images/AzureLabs-Lab310-22.png)

3.  打开 Unity 后，值得检查 **默认脚本编辑器** 是否设置为 **Visual Studio。** 转到"**编辑*  >  *首选项"，** 然后从新窗口导航到"**外部工具"。** 将 **"外部脚本编辑器"****更改为Visual Studio。** 关闭 **"首选项"** 窗口。

    ![](images/AzureLabs-Lab310-23.png)

4.  接下来，转到"文件 **>生成设置，** 将"平台"切换到"通用平台 *Windows"，* 然后单击"切换平台 **"** 按钮。

    ![](images/AzureLabs-Lab310-24.png)

5.  在同一 **"生成设置** 窗口中，确保已设置以下内容：

    1.  **目标设备****设置为"HoloLens**        
    2.  **生成类型** 设置为 **D3D**
    3.  **SDK** 设置为"最新 **安装"**
    4.  **Visual Studio版本** 设置为"最新 **安装"**
    5.  **"生成和运行** "设置为" **本地计算机"**            
    6.  目前，"**生成设置中的** 其余设置应保留为默认值。

        ![](images/AzureLabs-Lab310-25.png)

6.  在同一"生成 **设置** 窗口中，单击"播放器设置按钮，这将在检查器所在的空间中 **打开相关面板**。

7. 在此面板中，需要验证一些设置：

    1.  在"**其他设置** 选项卡中：

        1.  **脚本运行时版本** 应为试验版 **(.NET** 4.6 等效) ，这将触发需要重启编辑器。

        2. **脚本后端应为** **.NET**。

        3. **API 兼容级别** 应为 **.NET 4.6。**

            ![](images/AzureLabs-Lab310-26.png)

    2.  在"**发布设置** 选项卡中的"**功能"下**，选中：

        1. **InternetClient**

        2.  **网络摄像头**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  在面板的下方，在"发布 设置) "下面的 **"XR** 设置 ("中，勾选"支持虚拟现实"，Windows Mixed Reality  **SDK。**

        ![](images/AzureLabs-Lab310-29.png)

8.  返回到"**生成设置"** 中 *，Unity C \#* 项目不再灰度：勾选此旁边的复选框。

9.  关闭“生成设置”窗口  。

10. 在编辑器 **中**，单击 **"编辑**  >  **Project 设置**  >  **图形"。**

    ![](images/AzureLabs-Lab310-30.png)

11. 在检查 **器面板中***，设置"* 图形"面板。 向下滚动，直到看到名为 Always **Include 着色器 的数组**。 通过增加一个大小变量来添加槽 (此示例中，该变量为 8，因此我们将其) 。 将在数组的最后一个位置显示一个新槽，如下所示：

    ![](images/AzureLabs-Lab310-31.png)

12. 在槽中，单击槽旁边的小目标圆圈以打开着色器列表。 查找旧版 **着色器/透明/** 漫射着色器，然后双击它。 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>第 4 章 - 导入 CustomVisionObjDetection Unity 包

对于本课程，你将获得名为 **Azure-MR-310.unitypackage 的** Unity 资产包。 

> [提示]Unity 支持的任何对象（包括整个场景）都可以打包到 **.unitypackage** 文件中，并导出/导入到其他项目中。 它是在不同 Unity 项目之间移动资产的最安全且 **最高效的方法**。

可在此处找到需要下载的 [Azure-MR-310 包](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。

1.  在 Unity 仪表板的前面，单击屏幕顶部菜单中的"资产"，然后单击"导入包>**自定义包"。**

    ![](images/AzureLabs-Lab310-33.png)

2.  使用文件选取器选择 **Azure-MR-310.unitypackage** 包，然后单击"打开 **"。** 此时会显示此资产的组件列表。 单击"导入"按钮确认 **导入** 。

    ![](images/AzureLabs-Lab310-34.png)

3.  导入完成后，你会注意到包中的文件夹现已添加到 **"资产** "文件夹。 此类文件夹结构对于 Unity 项目是典型的。

    ![](images/AzureLabs-Lab310-35.png)

    1.  " **材料** "文件夹包含凝视光标 **使用的材料**。 

    2.  **Plugins** 文件夹包含代码用于反初始化服务 Web 响应的 Newtonsoft DLL。 若要允许 Unity 编辑器和 UWP 生成使用和生成库， (2) 文件夹和子文件夹中包含的不同版本，这两个库是必需的。 

    3.  **Prefabs** 文件夹包含场景中包含的预制项。 这些资源类型包括：

        1.  **GazeCursor**，应用程序中使用的游标。 将与 SpatialMapping 预制件一起工作，能够放置在场景中物理对象的顶部。
        2.  **标签**，它是用于显示场景中的对象标记的 UI 对象（如果需要）。
        3.  **SpatialMapping**，它是使应用程序能够使用 创建虚拟地图的对象，Microsoft HoloLens空间跟踪。

    4.  " **场景** "文件夹，当前包含本课程的预建场景。

4.  打开 **"场景**"文件夹，在Project面板中，双击 **ObjDetectionScene，** 加载用于本课程的场景。

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **不包含任何代码**，你将按照本课程中的说明编写代码。

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>第 5 章 - 创建 CustomVisionAnalyser 类。

此时，你已准备好编写一些代码。 你将从 **CustomVisionAnalyser 类** 开始。

> [!NOTE]
> 对 自定义视觉 **服务的** 调用（在如下所示的代码中进行）是使用 **自定义视觉 REST API。** 通过使用此功能，你将了解如何实现和利用此 API (了解如何在你自己的目标上实现) 。 请注意，Microsoft 提供了自定义视觉 **SDK，** 该 SDK 还可用于调用服务。 有关详细信息，请访问 自定义视觉 [SDK 一文](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。

此类负责：

- 加载捕获为字节数组的最新映像。

- 将字节数组发送到 Azure **自定义视觉服务实例** 进行分析。

- 以 JSON 字符串形式接收响应。

- 反化响应，将生成的预测传递给 **SceneOrganiser** 类，该类将处理响应的显示方式。 

若要创建此类，请：

1.  右键单击位于"资产"**面板** 中的"资产 **Project"，** 然后单击"创建 **文件夹**  >  **"。** 调用文件夹 **Scripts**。

    ![](images/AzureLabs-Lab310-37.png)

2.  双击新创建的文件夹，打开它。

3.  右键单击文件夹内，然后单击"**创建**  >  **C 脚本 \# "。** 将脚本命名 **CustomVisionAnalyser。**

4.  双击新的 **CustomVisionAnalyser** 脚本，以使用 **Visual Studio。**

5.  请确保在文件顶部引用了以下命名空间：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  在 **CustomVisionAnalyser** 类中，添加以下变量：

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 请确保将服务 **Prediction-Key** 插入 **predictionKey** 变量，并将 **Prediction-Endpoint** 插入 **predictionEndpoint** 变量。 你之前在第[2 章记事本 14 中](#chapter-2---training-your-custom-vision-project)将这些文件复制到了其中。

7.  现在 **需要 ()** 唤醒代码来初始化 Instance 变量：

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  使用 (下面的静态 **GetImageAsByteArray ()** 方法添加协同例程) ，该方法将获取 **ImageCapture** 类捕获的图像分析结果。

    > [!NOTE]
    > 在 **"分析""映像""** 捕获协同例程"中，需要调用尚未创建的 **SceneOrganiser** 类。 因此，**请保留这些行的注释。**

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. 删除 **"启动 ()****更新 ()** 方法，因为它们不会使用。 

10.  在返回到 Unity **之前**，请务必Visual Studio 中的 **更改**。

> [!IMPORTANT]
> 如前所述，不必担心代码可能看起来有错误，因为很快会提供进一步的类，这将修复这些错误。

## <a name="chapter-6---create-the-customvisionobjects-class"></a>第 6 章 - 创建 CustomVisionObjects 类

现在将创建的类是 **CustomVisionObjects** 类。

此脚本包含其他类用来序列化并反序列化对服务自定义视觉的对象。

若要创建此类，请：

1.  在"脚本 **"文件夹中右** 键单击，然后单击"**创建**  >  **C 脚本 \# "。** 调用脚本 **CustomVisionObjects。**

2.  双击新的 **CustomVisionObjects 脚本**，以使用 **Visual Studio。**

3.  请确保在文件顶部引用了以下命名空间：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  删除 **CustomVisionObjects** () **中的** Start **()** Update () 方法，此类现在应为空。

    > [!WARNING]
    > 必须仔细遵循下一条说明。 如果将新的类声明放在 **CustomVisionObjects** 类中，将在第 [10](#chapter-10---create-the-imagecapture-class)章中收到编译错误，指出 **找不到 AnalysisRootObject** 和 **BoundingBox。**

5.  在 **CustomVisionObjects 类外部添加以下** 类。  **Newtonsoft** 库使用这些对象来序列化并反序列化响应数据：

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  在返回到 Unity **之前**，请务必Visual Studio 中的 **更改**。

## <a name="chapter-7---create-the-spatialmapping-class"></a>第 7 章 - 创建 SpatialMapping 类

此类将在场景中设置空间 **映射碰撞** 体，以便能够检测虚拟对象与真实对象之间的冲突。

若要创建此类，请：

1.  在"脚本 **"文件夹中右** 键单击，然后单击"**创建**  >  **C 脚本 \# "。** 调用脚本 **SpatialMapping。**

2.  双击新的 **SpatialMapping 脚本**，以使用 **Visual Studio。**

3.  请确保在 **SpatialMapping** 类上方引用了以下命名空间：

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  然后，将以下变量添加到 **SpatialMapping** 类中的 Start **()** 方法上方：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  添加 **"唤醒 () "** 和"**启动 () ：**

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  删除 **Update ()** 方法。

7.  在返回到 Unity **之前**，请务必Visual Studio 中的 **更改**。


## <a name="chapter-8---create-the-gazecursor-class"></a>第 8 章 - 创建 GazeCursor 类

此类负责通过使用上一章中创建的 **SpatialMappingCollider，** 在真实空间中的正确位置设置光标。

若要创建此类，请：

1.  在"脚本 **"文件夹中右** 键单击，然后单击"**创建**  >  **C 脚本 \# "。** 调用脚本 **GazeCursor**

2.  双击新的 **GazeCursor** 脚本，以使用 **Visual Studio。**

3.  请确保在 **GazeCursor** 类上方引用了以下命名空间：

    ```csharp
    using UnityEngine;
    ```

4.  然后将以下变量添加到 **GazeCursor** 类中的 Start **()** 方法。 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  使用以下 **()** 更新 Start () 方法：

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  使用 **以下 ()** Update () 方法：

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > 不必担心找不到 **SceneOrganiser** 类的错误，你将在下一章创建它。

7. 在返回到 Unity **之前**，请务必Visual Studio 中的 **更改**。

## <a name="chapter-9---create-the-sceneorganiser-class"></a>第 9 章 - 创建 SceneOrganiser 类

此类将：

-   通过向 *主相机附加* 相应的组件来设置主相机。

-   检测到对象时，它将负责计算它在现实世界中的位置，并在其附近放置一个标记标签，并带有相应的 **标记名称**。    

若要创建此类，请：

1.  在"脚本 **"文件夹中右** 键单击，然后单击"**创建**  >  **C 脚本 \# "。** 将脚本 **"SceneOrganiser"命名**。

2.  双击新的 **SceneOrganiser** 脚本，以使用 **Visual Studio。**

3.  请确保在 **SceneOrganiser** 类上方引用了以下命名空间：

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  然后在 Start () 方法的 **SceneOrganiser** **类中添加以下** 变量：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  删除"**启动 ()****更新 ()** 方法。

6.  在变量下面，添加 **"唤醒 ()** 方法，该方法将初始化 类并设置场景。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  添加 **PlaceAnalysisLabel ()** 方法，该方法将实例化场景中的标签 (此时用户看不到) 。 它还使四边形 (在) 位置不可见，并且与现实世界重叠。 这一点很重要，因为分析后从服务中检索到的框坐标将追溯到此四边形中，以确定现实世界中对象的大致位置。 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  添加 **FinaliseLabel ()** 方法。 它负责：

    *   使用 *具有* 最高置信 *度的预测* 标记设置标签文本。
    *   调用四边形 *对象* 上边界框的计算（以前定位）并放置场景中的标签。
    *   通过使用向边界框 方向的 Raycast 调整标签深度，该边界框应与现实世界中的对象发生冲突。
    * 重置捕获进程以允许用户捕获另一个映像。

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  添加 **CalculateBoundingBoxPosition ()** 方法，该方法承载转换从服务检索到的 *Bounding Box* 坐标，并按比例在四边形上重新创建它们所需的大量计算。

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. 在返回到 Unity **之前**，请务必Visual Studio 中的 **更改**。

    > [!IMPORTANT]
    > 在继续之前，请打开 **CustomVisionAnalyser** 类，在 **"分析""LastImageCaptured" ()** 方法中，取消注释以下行：
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> 不必担心 **ImageCapture** 类"找不到"消息，你将在下一章创建它。


## <a name="chapter-10---create-the-imagecapture-class"></a>第 10 章 - 创建 ImageCapture 类

要创建的下一个类是 **ImageCapture** 类。

此类负责：

*   使用相机捕获图像HoloLens相机，并存储在 *"应用*"文件夹中。
*   处理 *用户的* 点击手势。

若要创建此类，请：

1.  转到之前 **创建的 Scripts** 文件夹。

2.  右键单击文件夹内，然后单击"**创建**  >  **C 脚本 \# "。** 将脚本命名 **ImageCapture**。

3.  双击新的 **ImageCapture** 脚本，以使用 **Visual Studio。**

4.  将文件顶部的命名空间替换为以下内容：

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然后将以下变量添加到 **ImageCapture** 类中的 Start **()** 方法上：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  现在需要 **()****唤醒** () 启动方法的代码：

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  实现一个处理程序，该处理程序将在点击手势出现时调用：

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > 当光标为 **绿色** 时，表示照相机可用于拍摄图像。 当光标为 **红色** 时，表示照相机正忙。

8.  添加应用程序用于启动映像捕获过程并存储映像的方法：

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  添加在捕获照片时以及准备好分析照片时调用的处理程序。 然后将结果传递给 **CustomVisionAnalyser 进行分析** 。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 在返回到 Unity **之前**，请务必Visual Studio 中的 **更改**。

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>第 11 章 - 设置场景中的脚本

现在，你已编写此项目所需的全部代码，现在可以在场景和预制器上设置脚本，使它们能够正常运行。

1.  在 **Unity 编辑器的**"层次结构 **面板"中**，选择 **"主相机"。**
2.  在检查 **器面板中**，选中 **"主** 相机"后，单击 **"添加组件**"，然后搜索 **SceneOrganiser** 脚本并双击以添加它。

    ![](images/AzureLabs-Lab310-38.png)

3.  在 Project 面板中，打开 **Prefabs** 文件夹，将标签预制块拖到刚添加到主相机的 **SceneOrganiser** 脚本中的"标签空引用目标输入区域"中，如下图所示： 

    ![](images/AzureLabs-Lab310-39.png)

4.  在"**层次结构面板"中**，选择主相机 的 **"GazeCursor"****子级**。
5.  在检查 **器面板中**，选中 **"GazeCursor"** 后，单击 **"添加组件**"，然后搜索 **"GazeCursor"** 脚本并双击以添加它。

    ![](images/AzureLabs-Lab310-40.png)

6.  同样，在 **"层次结构面板"** 中，选择主相机 的 **SpatialMapping** **子级**。
7.  在检查 **器面板中**，选中 **"SpatialMapping"** 后，单击 **"添加组件**"，然后搜索 **SpatialMapping 脚本** 并双击以添加它。

    ![](images/AzureLabs-Lab310-41.png)

在运行时 **，SceneOrganiser** 脚本中的代码将添加尚未设置的剩余脚本。

## <a name="chapter-12---before-building"></a>第 12 章 - 生成前

若要对应用程序执行全面测试，需要将应用程序旁加载到Microsoft HoloLens。

在这样做之前，请确保：

-  第 3 章 [中提到的所有](#chapter-3---set-up-the-unity-project) 设置均正确设置。
- 脚本 **SceneOrganiser** 附加到 **主相机** 对象。
- 脚本 **GazeCursor** 附加到 **GazeCursor** 对象。
- 脚本 **SpatialMapping** 附加到 **SpatialMapping** 对象。
- 在第 [5 章](#chapter-5---create-the-customvisionanalyser-class)中，步骤 6：

    - 确保将服务预测 **密钥插入到** **predictionKey** 变量中。
    - 你已将预测 **终结点插入到** **predictionEndpoint** 类中。

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>第 13 章 - 生成 UWP 解决方案并旁加载应用程序

现在，你已准备好将应用程序构建为 UWP 解决方案，你可以将其部署到 Microsoft HoloLens。 开始生成过程：

1.  转到"**文件>生成设置"。**

2.  勾选 **Unity C \# 项目**。

3.  单击"**添加打开的场景"。** 这会将当前打开的场景添加到生成中。

    ![](images/AzureLabs-Lab310-42.png)

4.  单击“生成”。 Unity 将启动 *文件资源管理器* 窗口，你需要创建该窗口，然后选择要生成应用的文件夹。 现在创建该文件夹，并命名"应用 **"。** 然后选择"应用 **"文件夹** 后，单击"**选择文件夹"。**

5.  Unity 将开始将项目生成到 **"应用"** 文件夹。

6.  Unity 完成生成 (可能需要一些时间) ，它会在生成位置打开 **文件资源管理器** 窗口 (检查任务栏，因为它可能不会始终显示在窗口上方，但会通知你新窗口) 。

7.  若要部署到 Microsoft HoloLens，需要该设备的 IP 地址 (远程部署) ，并确保 **它还设置了开发人员** 模式。 若要实现此目的，请执行以下操作：

    1.  一边HoloLens，一边 **打开设置。**

    2.  转到"**网络& Internet**  >  **Wi-Fi**  >  **高级选项"**

    3.  记下 **IPv4** 地址。

    4.  接下来，导航回 **设置，** 然后导航到 **"更新开发人员&**  >  **安全性"**

    5.  在 **上设置开发人员***模式*。

8.  导航到"应用"文件夹 (**新的** Unity) ，然后使用 Visual Studio 打开 **解决方案文件**。

9.  在"解决方案配置"中，选择"**调试"。**

10. 在"解决方案平台"中，选择 **"x86，远程计算机"。** 此时，系统会提示你插入远程设备的 **IP** 地址 (Microsoft HoloLens，在这种情况下，你已) 。

    ![](images/AzureLabs-Lab310-43.png)

11. 转到"**生成"** 菜单并单击"部署 **解决方案**"，将应用程序旁加载到HoloLens。

12. 应用现在应显示在应用程序上安装的应用列表中Microsoft HoloLens，可以启动！

### <a name="to-use-the-application"></a>若要使用应用程序，请执行以下代码：

* 查看一个对象，该对象已使用 Azure 自定义视觉 **服务、对象检测** 进行训练，并使用点击 **手势**。
* 如果成功检测到该对象，则会出现一个带有标记名称的空格标签文本。

> [!IMPORTANT]
> 每次捕获照片并将其发送到服务时，都可以返回到"服务"页，然后使用新捕获的图像重新训练服务。 一开始，可能还需要更正边界框，以更准确并重新训练服务。

> [!NOTE]
> 当 Unity 中的 Microsoft HoloLens 传感器和/或 SpatialTrackingComponent 无法放置相对于实际对象的适当碰撞体时，放置的标签文本可能不会显示在对象附近。 如果情况如此，请尝试在不同的图面上使用该应用程序。

## <a name="your-custom-vision-object-detection-application"></a>你的自定义视觉对象检测应用程序

祝贺你，你构建了一个混合现实应用，该应用利用 Azure 自定义视觉 对象检测 API，该应用可以从图像中识别对象，然后在 3D 空间中提供该对象的大致位置。

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习 1

将 添加到文本标签中，使用半透明多维数据集将真实对象包装在 3D *边界框中*。

### <a name="exercise-2"></a>练习 2

训练 自定义视觉 服务以识别更多对象。

### <a name="exercise-3"></a>练习 3

识别对象时播放声音。

### <a name="exercise-4"></a>练习 4

使用 API 使用应用正在分析的相同图像重新训练服务，使服务更 (预测和训练) 。