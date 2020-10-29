---
title: MR 和 Azure 302b-自定义构想
description: 完成本课程，了解如何训练机器学习模型，然后使用训练的模型识别混合现实应用程序内的类似对象。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，自定义视觉，hololens，沉浸，vr
ms.openlocfilehash: 857cdc00daa94db5bb4d4fda1d5adfcf0ba28822
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91678161"
---
# <a name="mr-and-azure-302b-custom-vision"></a>MR 和 Azure 302b：自定义视觉

<br>

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>


在本课程中，你将了解如何在混合现实应用程序中使用 Azure 自定义视觉功能，识别提供的映像中的自定义视觉对象内容。

此服务允许你使用对象图像训练机器学习模型。 然后，你将使用训练的模型来识别类似对象，这些对象由 Microsoft HoloLens 的相机捕获或连接到电脑以便沉浸式 (VR) 耳机提供。

![课程结果](images/AzureLabs-Lab302b-00.png)

Azure 自定义视觉是一种 Microsoft 认知服务，允许开发人员构建自定义映像分类器。 然后，可以将这些分类器与新图像一起使用，以识别或分类该新图像中的对象。 此服务提供简单易用的联机门户来简化流程。 有关详细信息，请访问 [Azure 自定义影像服务页](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。

完成本课程后，你将拥有一个混合现实应用程序，可以在两种模式下工作：

-   **分析模式** ：通过以下方式设置自定义影像服务：上传图像，创建标记，并培训服务，以识别在此情况下鼠标和键盘)  (不同对象。 然后，将创建一个将使用相机捕获图像的 HoloLens 应用，并尝试识别真实环境中的对象。

-   **定型模式** ：将实现在应用中启用 "定型模式" 的代码。 训练模式允许使用 HoloLens 相机捕获图像，将捕获的图像上传到服务，并训练自定义视觉模型。

本课程将介绍如何将自定义影像服务中的结果获取到基于 Unity 的示例应用程序。 您可以将这些概念应用到您可能生成的自定义应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 302b：自定义视觉</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 尽管本课程主要侧重于 HoloLens，但你也可以将本课程中学习的内容应用于 Windows Mixed Reality 沉浸式 (VR) 耳机。 由于沉浸式 (VR) 耳机没有可访问的相机，因此你需要连接到电脑的外置相机。 在本课程中，您将看到有关在支持沉浸式 (VR) 耳机时可能需要执行的任何更改的说明。

## <a name="prerequisites"></a>必备条件

> [!NOTE]
> 本教程专为具有 Unity 和 c # 基本经验的开发人员设计。 请注意，本文档中的先决条件和书面说明表示在) 2018 年7月 (撰写本文时已测试和验证的内容。 你可以随意使用最新的软件（如 [安装工具](../../install-the-tools.md) 一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。

本课程建议采用以下硬件和软件：

- [与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，适用于沉浸式 (VR) 耳机开发
- [Windows 10 秋季创意者更新 (或更高版本启用了开发人员模式) ](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017。4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 沉浸式 (VR) 耳机](../../../discover/immersive-headset-hardware-details.md)或[Microsoft HoloLens](../../../hololens-hardware-details.md) ，启用了开发人员模式
- 连接到电脑的相机 (沉浸式耳机开发) 
- Azure 安装和自定义视觉 API 检索的 Internet 访问
- 一系列至少五个 (5) 映像 (10 (10) 建议) 识别的每个对象。 如果需要，可以使用 [本课程提供的映像 (计算机鼠标和键盘) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。

## <a name="before-you-start"></a>开始之前

1.  若要避免在生成此项目时遇到问题，强烈建议你在根或近乎根文件夹中创建本教程中所述的项目 (长文件夹路径在生成时) 会导致问题。
2.  设置并测试你的 HoloLens。 如果需要支持设置 HoloLens，请 [确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。 
3.  在开始开发新的 HoloLens 应用程序时，最好执行校准和传感器调整 (有时，它可以帮助为每个用户) 执行这些任务。 

有关校准的帮助信息，请单击此链接，了解 [到 HoloLens 校准文章](../../../calibration.md#hololens-2)。

有关传感器优化的帮助，请单击 ["HoloLens 传感器优化" 一文](../../../sensor-tuning.md)。

## <a name="chapter-1---the-custom-vision-service-portal"></a>第1章-自定义影像服务门户

若要在 Azure 中使用 *自定义影像服务* ，你将需要配置服务的实例，使其可用于你的应用程序。

1.  首先， [导航到 *自定义影像服务* 主页](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  单击 " **开始** " 按钮。

    ![自定义影像服务入门](images/AzureLabs-Lab302b-01.png)

3.  登录到 *自定义影像服务* 门户。

    ![登录到门户](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。

4.  首次登录后，系统会提示 " *服务* " 面板。 单击相应的复选框以同意条款。 然后单击 " **我同意** "。

    ![服务条款](images/AzureLabs-Lab302b-03.png)

5.  同意这些条款后，你将会导航到门户的 " *项目* " 部分。 单击 " **新建项目** "。

    ![创建新项目](images/AzureLabs-Lab302b-04.png)

6.  右侧将显示一个选项卡，该选项卡将提示你为项目指定某些字段。

    1.  插入项目的 *名称* 。

    2.   ( *可选* ) 中插入项目的 *描述* 。

    3.  选择一个 *资源组* ，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议保留与单个项目关联的所有 Azure 服务 (例如，这些课程) 常用资源组) 下。

    4. 将 *项目类型* 设置为 **分类**
    
    5. 将 *域* 设置为 " **常规** "。

        ![设置域](images/AzureLabs-Lab302b-05.png)

        > 若要了解有关 Azure 资源组的详细信息，请 [访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。

7.  完成后，单击 " **创建项目** "，你会被重定向到自定义影像服务，"项目" 页。

## <a name="chapter-2---training-your-custom-vision-project"></a>第2章-培训自定义视觉项目

在自定义视觉门户中，你的主要目标是训练你的项目以识别图像中的特定对象。 对于你希望应用程序识别的每个对象，你需要至少5个 (5) 映像，但最好是10个 (10) 。 [您可以使用本课程附带的图像 (计算机鼠标和键盘) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。 

训练自定义影像服务项目：

1.  单击 " **+** 标记" 旁边的按钮 **。**

    ![添加新标记](images/AzureLabs-Lab302b-06.png)

2.  添加要识别的对象的 **名称** 。 单击“保存” 。

    ![添加对象名称并保存](images/AzureLabs-Lab302b-07.png)

3.  你将注意到已添加 **标记** (你可能需要重新加载页面以使其) 显示。 单击新标记旁边的复选框（如果尚未选中）。

    ![启用新标记](images/AzureLabs-Lab302b-08.png)

4.  单击页中心的 " **添加图像** "。

    ![添加图像](images/AzureLabs-Lab302b-09.png)

5.  单击 " **浏览本地文件** "，搜索，然后选择要上传的映像，最小为 5 (5) 。 请记住，这些映像应该包含您正在训练的对象。

    > [!NOTE]
    >  你可以一次选择多个图像来上传。

6.  在选项卡中看到图像后，请在 " **我的标记** " 框中选择相应的标记。

    ![选择标记](images/AzureLabs-Lab302b-10.png)

7.  单击 "上 **传文件** "。 文件将开始上传。 确认上传后，单击 " **完成** "。

    ![上传文件](images/AzureLabs-Lab302b-11.png)

8.  重复相同的过程，创建名为 " **键盘** " 的新 **标记** ，并为其上传适当的照片。 请确保在创建新标记后 **取消选中***鼠标* ，以便显示 " *添加映像* " 窗口。

9.  设置两个标记后，单击 " **训练** "，第一次训练迭代将开始生成。

    ![启用定型迭代](images/AzureLabs-Lab302b-12.png)

10. 构建后，可以看到两个称为 " **创建默认值** " 和 " **预测 URL** " 的按钮。 先单击 " **设为默认值** "，然后单击 " **预测 URL** "。

    ![设置默认 URL 和预测 URL](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > 从此提供的端点 URL 设置为标记为默认值的任何 *迭代* 。 这种情况下，如果您以后生成新的 *迭代* 并将其更新为默认值，则无需更改代码。

11. 单击 " *预测 URL* " 后，打开 " *记事本* "，复制并粘贴该 **url** 和 **预测密钥** ，以便稍后在代码中需要时进行检索。

    ![复制并粘贴 URL 和预测-密钥](images/AzureLabs-Lab302b-14.png)

12. 单击屏幕右上角的 **齿轮** 。

    ![单击 "齿轮" 图标打开 "设置"](images/AzureLabs-Lab302b-15.png)

13. 复制 **定型密钥** ，并将其粘贴到 *记事本* 中供以后使用。

    ![复制定型密钥](images/AzureLabs-Lab302b-16.png)

14. 还应复制 **项目 Id** ，并将其粘贴到 *记事本* 文件中供以后使用。

    ![复制项目 id](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第3章-设置 Unity 项目

下面是用于使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。

1.  打开 *Unity* ，并单击 " **新建** "。

    ![创建新 Unity 项目](images/AzureLabs-Lab302b-17.png)

2.  现在需要提供 Unity 项目名称。 插入 **AzureCustomVision。** 请确保将项目模板设置为 **3d** 。 将位置设置为合适的 **位置** (记住，更接近根目录) 。 然后单击 " **创建项目** "。

    ![配置项目设置](images/AzureLabs-Lab302b-18.png)

3.  当 Unity 处于打开状态时，有必要选中 "默认 **脚本编辑器** " 设置为 " **Visual Studio** "。 转到 " **编辑*  >  *首选项** "，然后在新窗口中导航到 " **外部工具** "。 将 **外部脚本编辑器** 更改为 **Visual Studio 2017** 。 关闭 " **首选项** " 窗口。

    ![配置外部工具](images/AzureLabs-Lab302b-19.png)

4.  接下来，转到 " **文件 > 生成设置** "，选择 " **通用 Windows 平台** "，然后单击 " **切换平台** " 按钮以应用所选内容。

    ![配置生成设置 ](images/AzureLabs-Lab302b-20.png)

5.  尽管仍处于 **文件 > 生成设置** ，但请确保：

    1.  **目标设备** 设置为 **HoloLens**

        > 对于沉浸式耳机，将 " **目标设备** " 设置为 " *任何设备* "。
        
    2.  **生成类型** 设置为 **D3D**
    3.  **SDK** 设置为 " **最新安装** "
    4.  **Visual Studio 版本** 设置为 " **最新安装** "
    5.  " **生成并运行** " 设置为 " **本地计算机** "
    6.  保存场景并将其添加到生成中。 

        1. 通过选择 " **添加打开的场景** " 来执行此操作。 将显示 "保存" 窗口。

            ![将打开的场景添加到生成列表](images/AzureLabs-Lab302b-21.png)

        2. 为此创建新文件夹，并为将来的任何场景创建一个新文件夹，然后选择 " **新建文件夹** " 按钮以创建新文件夹，将其命名为 **场景** 。

            ![创建新的场景文件夹](images/AzureLabs-Lab302b-22.png)

        3. 打开新创建的 **场景** 文件夹，然后在 "文件名 *：* 文本" 字段中，键入 **CustomVisionScene** ，然后单击 " **保存** "。

            ![命名新的场景文件](images/AzureLabs-Lab302b-23.png)

            > 请注意，必须将 Unity 场景保存在 " *资产* " 文件夹中，因为它们必须与 Unity 项目相关联。 创建场景文件夹 (和其他类似文件夹) 是构建 Unity 项目的典型方式。
            
    7.  现在，" *生成设置* " 中的其余设置应保留为默认值。

        ![默认生成设置](images/AzureLabs-Lab302b-24.png)

6.  在 " *生成设置* " 窗口中，单击 " **播放机设置** " 按钮，这会在 *检查器* 所在的空间中打开相关面板。

7. 在此面板中，需要验证几项设置：

    1.  在 " **其他设置** " 选项卡中：

        1.  **脚本运行时版本** 应 **( .net 4.6 等效) 试验** ，这会触发重新启动编辑器的需要。

        2. **脚本编写后端** 应为 **.net**

        3. **API 兼容级别** 应为 **.net 4.6**

        ![设置 API compantiblity](images/AzureLabs-Lab302b-25.png)

    2.  在 " **发布设置** " 选项卡的 " **功能** " 下，检查：

        1. **InternetClient**

        2.  **网络摄像头**

        3. **麦克风**

        ![配置发布设置](images/AzureLabs-Lab302b-26.png)

    3.  在面板中，在 " **XR 设置** " 中， () "发布设置" 下的 " **发布设置** " 下提供了 **支持** ，请确保已添加 **Windows Mixed reality SDK** 。

    ![配置 XR 设置](images/AzureLabs-Lab302b-27.png)

8.  返回 *生成设置* *Unity C \# 项目* 不再灰显; 勾选此的旁边的复选框。

9.  关闭“生成设置”窗口。

10.  保存场景和项目 ( **文件 > 保存场景/文件 > 保存项目** ) 。


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>第4章-导入 Unity 中的 Newtonsoft.json DLL

> [!IMPORTANT]
> 如果你想要跳过本课程的 *Unity 设置* 组件，并继续直接进入代码，欢迎下载此 [302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)，将其作为 [**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入到你的项目，然后继续 [第6章](#chapter-6---create-the-customvisionanalyser-class)。

本课程需要使用 **newtonsoft.json** 库，可将其作为 DLL 添加到资产中。 [可以从此链接下载包含此库](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)的包。
若要将 Newtonsoft.json 库导入项目，请使用本课程附带的 Unity 包。

1.  使用 " **资产*  >  *导入**包*  >  *自定义**包** " 菜单选项将 *unitypackage* 添加到 Unity。

2.  在弹出的 " **导入 Unity 包** " 框中，确保选择 (下的所有内容，包括) 的 **插件** 。

    ![导入所有包项](images/AzureLabs-Lab302b-28.png)

3.  单击 " **导入** " 按钮，将项添加到项目。

4.  在项目视图中，在 " **插件** " 下，单击 " **newtonsoft.json** " 文件夹，然后选择 " *Newtonsoft.Js" 插件* 。

    ![选择 Newtonsoft.json 插件](images/AzureLabs-Lab302b-29.png)

5.  选择 " *Newtonsoft.Json" 插件* 后，请确保 **未选中****任何平台** ，然后确保 **WSAPlayer** 未被 **选中** ，然后单击 " **应用** "。 这只是为了确认已正确配置文件。

    ![配置 Newtonsoft.json 插件](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > 标记这些插件会将它们配置为仅在 Unity 编辑器中使用。 在从 Unity 导出项目后，将使用 WSA 文件夹中的一组不同的组。

6.  接下来，需要在 **newtonsoft.json** 文件夹中打开 **WSA** 文件夹。 你将看到刚才配置的同一文件的副本。 选择该文件，然后在 "检查器" 中，确保
    -   **未选中****任何平台** 
    -   **仅****检查** **WSAPlayer**
    -   不 **检查****进程**

    ![配置 Newtonsoft.json 插件平台设置](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>第5章-照相机设置

1.  在 "层次结构" 面板中，选择 " *摄像机* "。

2.  选择后，你将能够在 " *检查器" 面板* 中看到 *主相机* 的所有组件。

    1.  *照相机* 对象必须命名为 " **主相机** " (记下拼写！ ) 

    2.  必须将主相机 **标记** 设置为 " **MainCamera** "， (记下拼写！ ) 

    3.  请确保将 **转换位置** 设置为 **0，0，0**

    4.  将 " **清除标志** " 设置为 **纯色** (为沉浸式头戴式耳机) 忽略此标志。

    5.  将相机组件的 **背景** 色设置为 **黑色、Alpha 0 (十六进制代码： #00000000)** (为沉浸式耳机) 忽略此颜色。

    ![配置照相机组件属性](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>第6章-创建 CustomVisionAnalyser 类。

此时，您可以编写一些代码。

你将从 *CustomVisionAnalyser* 类开始。

> [!NOTE]
> 在下面显示的代码中对 **自定义影像服务** 所做的调用是使用 **自定义视觉 REST API** 进行的。 通过使用此方法，你将了解如何实现和使用此 API (有助于了解如何实现类似于你自己的) 的内容。 请注意，Microsoft 提供了一个 **自定义影像服务 SDK** ，该 SDK 还可用于对服务进行调用。 有关详细信息，请访问 [自定义影像服务 SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) 文章。

此类负责：

-   加载作为字节数组捕获的最新映像。

-   将字节数组发送给 Azure *自定义影像服务* 实例以进行分析。

-   接收 JSON 字符串形式的响应。

-   反序列化响应并将结果 *预测* 传递给 *SceneOrganiser* 类，这将负责显示响应的方式。

若要创建此类：

1.  右键单击位于 " *项目" 面板* 中的 *资产文件夹* ，然后单击 " **创建 > 文件夹** 。 调用文件夹 **脚本** 。

    ![创建脚本文件夹](images/AzureLabs-Lab302b-33.png)

2.  双击刚创建的文件夹以将其打开。

3.  右键单击文件夹内，然后单击 " **创建**  >  **C \# 脚本** "。 将脚本命名为 *CustomVisionAnalyser* 。

4.  双击新的 *CustomVisionAnalyser* 脚本以通过 **Visual Studio** 打开它。

5.  更新文件顶部的命名空间，以匹配以下内容：

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  在 *CustomVisionAnalyser* 类中，添加以下变量：

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 请确保将 **预测密钥** 插入到 **predictionKey** 变量中，并将 **预测终结点** 插入到 **predictionEndpoint** 变量中。 您在本课程的前面部分将它们复制到 *记事本* 。

7.  现在需要添加用于 **唤醒 ( # B1** 的代码以初始化实例变量：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  删除方法 **开始 ( # B1** 并 **更新 ( # B3** 。

9.  接下来，将协同程序 (与静态 **GetImageAsByteArray ( # B2** 方法一起添加) ，该方法将获得 *ImageCapture* 类捕获的映像的分析结果。

    > [!NOTE]
    > 在 **AnalyseImageCapture** 协同程序中，有一个对你还需要创建的 *SceneOrganiser* 类的调用。 因此，请 **暂时将这些行注释为** 。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  在返回到 **Unity** 之前，请务必保存 **Visual Studio** 中所做的更改。

## <a name="chapter-7---create-the-customvisionobjects-class"></a>第7章-创建 CustomVisionObjects 类

你现在将创建的类是 *CustomVisionObjects* 类。

此脚本包含其他类用于序列化和反序列化对 *自定义影像服务* 进行的调用的许多对象。

> [!WARNING]
> 请务必记下自定义影像服务提供的终结点，因为下面的 JSON 结构已设置为使用 [*自定义视觉预测*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)v2.0。 如果你的版本不同，可能需要更新以下结构。

若要创建此类：

1.  右键单击 " **脚本** " 文件夹内，然后单击 " **创建**  >  **C \# 脚本** "。 调用脚本 *CustomVisionObjects* 。

2.  双击新的 **CustomVisionObjects** 脚本以通过 **Visual Studio** 打开它。

3.  将以下命名空间添加到文件顶部：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  删除 *CustomVisionObjects* 类中的 **开始 ( # B1** 并 **更新 ( # B3** 方法;此类现在应为空。

5.  将以下类添加到 *CustomVisionObjects* 类的 **外部** 。 *Newtonsoft.json* 库使用这些对象序列化和反序列化响应数据：

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>第8章-创建 VoiceRecognizer 类

此类将识别用户的语音输入。

若要创建此类：

1.  右键单击 " **脚本** " 文件夹内，然后单击 " **创建**  >  **C \# 脚本** "。 调用脚本 *VoiceRecognizer* 。

2.  双击新的 **VoiceRecognizer** 脚本以通过 **Visual Studio** 打开它。

3.  将以下命名空间添加到 *VoiceRecognizer* 类的上方：

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  然后，将以下变量添加到 *VoiceRecognizer* 类中的 *Start ( # B1* 方法之上：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  添加 **唤醒 ( # B1** 并 **开始 ( # B3** 方法，后者将设置在将标记关联到图像时要识别的用户 *关键字* ：

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  删除 **( # B1** 方法的更新。

7.  添加以下处理程序，只要识别语音输入，就会调用该处理程序：

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  在返回到 **Unity** 之前，请务必保存 **Visual Studio** 中所做的更改。

> [!NOTE]
> 不要担心可能出现错误的代码，因为您很快就会提供更多的类，这将修复这些问题。

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>第9章-创建 CustomVisionTrainer 类

此类将链接一系列 web 调用以训练 *自定义影像服务* 。 每次调用都将在代码的上方详细说明。

若要创建此类：

1.  右键单击 " **脚本** " 文件夹内，然后单击 " **创建**  >  **C \# 脚本** "。 调用脚本 *CustomVisionTrainer* 。

2.  双击新的 *CustomVisionTrainer* 脚本以通过 **Visual Studio** 打开它。

3.  将以下命名空间添加到 *CustomVisionTrainer* 类的上方：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  然后，将以下变量添加到 *CustomVisionTrainer* 类中的 **Start ( # B1** 方法之上。 

    > [!NOTE]
    > 此处使用的训练 URL 在 *自定义视觉培训 1.2* 文档中提供，并具有以下结构： https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > 有关详细信息，请访问 [*自定义视觉培训 v1.0 参考 API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。

    > [!WARNING]
    > 请务必记下自定义影像服务为你提供培训模式的终结点，因为在 **CustomVisionObjects** ) 类中使用的 JSON 结构已设置为与 [*自定义视觉培训*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)v1.0 一起使用 (。 如果有不同的版本，则可能需要更新 *对象* 结构。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > 请确保将你的 **服务密钥** 添加 (定型密钥) 值和 **项目 Id** 值，你之前记下;这是你 [在本课程前面部分中收集的值 (第2章 "第10步")](#chapter-2---training-your-custom-vision-project)。

5.  添加以下 **开始 ( # B1** 和 **唤醒 ( # B3** 方法。 这些方法在初始化时调用，并包含设置 UI 的调用：

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  删除 **( # B1** 方法的更新。 此类不需要此类。

7.  添加 **RequestTagSelection ( # B1** 方法。 此方法是在捕获图像并将其存储在设备中，并且现在已准备好提交到 *自定义影像服务* 的第一个调用。 此方法在定型 UI 中显示一组关键字，用户可以使用这些关键字标记已捕获的映像。 它还提醒 *VoiceRecognizer* 类开始倾听用户的语音输入。

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  添加 **VerifyTag ( # B1** 方法。 此方法将接收 **VoiceRecognizer** 类识别的语音输入并验证其有效性，然后开始训练过程。

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  添加 **SubmitImageForTraining ( # B1** 方法。 此方法将开始自定义影像服务训练过程。 第一步是从服务中检索与用户的经验证的语音输入相关联的 **标记 Id** 。 **标记 Id** 随后将连同图像一起上传。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. 添加 **TrainCustomVisionProject ( # B1** 方法。 提交并标记该映像后，将调用此方法。 它将创建一个新的迭代，该迭代将使用提交到服务的所有之前的图像以及刚刚上传的图像进行训练。 完成训练后，此方法将调用方法将新创建的 **迭代** 设置为 **默认值** ，以便用于分析的终结点是最新的定型迭代。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. 添加 **SetDefaultIteration ( # B1** 方法。 此方法会将以前创建和训练的迭代设置为 *默认值* 。 完成后，此方法将不得不删除服务中的上一个迭代。 撰写本课程时，在服务中允许同时存在的最大 10 (10) 迭代数限制。

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. 添加 **DeletePreviousIteration ( # B1** 方法。 此方法将查找并删除以前的非默认迭代：

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. 要添加到此类中的最后一个方法是 **GetImageAsByteArray ( # B1** 方法，用于在 web 调用上将捕获的图像转换为字节数组。

    ```csharp
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

14. 在返回到 **Unity** 之前，请务必保存 **Visual Studio** 中所做的更改。

## <a name="chapter-10---create-the-sceneorganiser-class"></a>第10章-创建 SceneOrganiser 类

此类将：

-   创建要附加到主相机的 **Cursor** 对象。

-   创建一个 **标签** 对象，该对象将在服务识别现实世界对象时显示。

-   通过向主摄像机附加相应的组件来设置它。

-   在 **分析模式** 下，将在运行时、相对于主摄像机位置的适当世界空间中生成标签，并显示从自定义影像服务收到的数据。

-   处于 **定型模式** 时，将生成 UI，该 UI 将显示训练过程的不同阶段。

若要创建此类：

1.  右键单击 " **脚本** " 文件夹内，然后单击 " **创建**  >  **C \# 脚本** "。 将脚本命名为 *SceneOrganiser* 。

2.  双击新的 *SceneOrganiser* 脚本以通过 **Visual Studio** 打开它。

3.  你只需要一个命名空间，并从 *SceneOrganiser* 类的上方删除其他命名空间：

    ```csharp
    using UnityEngine;
    ```

4.  然后，将以下变量添加到 *SceneOrganiser* 类中的 **Start ( # B1** 方法之上：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  删除 **开始 ( # B1** 并 **更新 ( # B3** 方法。

6.  在变量的下方，添加 **唤醒 ( # B1** 方法，这将初始化类并设置场景。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  现在，添加用于创建和定位主相机光标的 **CreateCameraCursor ( # B1** 方法，并添加 **CreateLabel ( # B3** 方法，该方法创建 **分析标签** 对象。

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. 添加 **SetCameraStatus ( # B1** 方法，该方法将处理旨在提供相机状态的文本网格的消息。

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. 将 **PlaceAnalysisLabel ( # B1** 和 **SetTagsToLastLabel ( # B3** 方法，该方法将生成数据并将其显示自定义影像服务到场景中。

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. 最后，添加 **CreateTrainingUI ( # B1** 方法，该方法将生成在应用程序处于定型模式时显示训练过程的多个阶段的 UI。 此方法也将伴随创建相机状态对象。

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. 在返回到 **Unity** 之前，请务必保存 **Visual Studio** 中所做的更改。

> [!IMPORTANT]
> 继续之前，请打开 **CustomVisionAnalyser** 类，并在 AnalyseLastImageCaptured 中 **( # B1** 方法， *取消注释* 以下行：
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>第11章-创建 ImageCapture 类

要创建的下一个类是 *ImageCapture* 类。

此类负责：

-   使用 HoloLens 相机捕获映像，并将其存储在 *App* 文件夹中。

-   处理用户的敲击手势。

-   维护用于确定应用程序是否将在 *分析* 模式或 *定型* 模式下运行的 *枚举* 值。

若要创建此类：

1.  中转到前面创建的 " **脚本** " 文件夹。

2.  右键单击文件夹内，然后单击 " **创建 > C \# 脚本** "。 将脚本命名为 *ImageCapture* 。

3.  双击新的 **ImageCapture** 脚本以通过 **Visual Studio** 打开它。

4.  将文件顶部的命名空间替换为以下内容：

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然后，将以下变量添加到 *ImageCapture* 类中的 **Start ( # B1** 方法之上：

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  现在需要添加用于 **唤醒 ( # B1** 和 **Start ( # B3** 方法的代码：

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  实现一个处理程序，该处理程序将在出现分流手势时调用。

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > 在 *分析* 模式下， **TapHandler** 方法充当开始或停止照片捕获循环的开关。
    >
    > 在 *定型* 模式下，它将从相机捕获图像。
    >
    > 如果光标为绿色，则表示相机可用于拍摄映像。
    >
    > 如果光标为红色，则表示相机处于繁忙状态。

8.  添加应用程序用于启动映像捕获过程并存储映像的方法。

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  添加在捕获照片时要调用的处理程序，并将其添加到已准备好进行分析的时间。 然后，将结果传递给 *CustomVisionAnalyser* 或 *CustomVisionTrainer* ，具体取决于设置了代码的模式。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 在返回到 **Unity** 之前，请务必保存 **Visual Studio** 中所做的更改。

11. 现在，所有脚本都已完成，请返回 Unity 编辑器，然后在 " *层次结构" 面板* 中单击 " **脚本** " 文件夹中的 **SceneOrganiser** 类，并将其拖到 **主相机** 对象。

## <a name="chapter-12---before-building"></a>第12章-生成之前

若要对应用程序进行全面测试，需要将其旁加载到 HoloLens。

在执行此操作之前，请确保：

- [第2章](#chapter-2---training-your-custom-vision-project)中提到的所有设置都已正确设置。

- **主相机** "检查器" 面板中的所有字段均已正确分配。

- 脚本 **SceneOrganiser** 已附加到 **摄像机主** 对象。

- 请确保将你的 **预测密钥** 插入到 **predictionKey** 变量。

- 已在 **predictionEndpoint** 变量中插入了 **预测终结点** 。

- 已将 **定型密钥** 插入 *CustomVisionTrainer* 类的 **trainingKey** 变量中。

- 已在 *CustomVisionTrainer* 类的 **projectId** 变量中插入了 **项目 ID** 。

## <a name="chapter-13---build-and-sideload-your-application"></a>第13章-构建并旁加载应用程序

开始 *生成* 过程：

1.  请参阅 **文件 > 生成设置** 。

2.  勾选 **Unity C \# 项目** 。

3.  单击“生成”  。 Unity 将启动 **文件资源管理器** 窗口，在该窗口中，需要创建一个文件夹，然后选择要在其中生成应用的文件夹。 立即创建该文件夹并将其命名为 **应用** 。 选择 **应用** 文件夹后，单击 " **选择文件夹** "。

4.  Unity 将开始向 **应用** 文件夹生成项目。

5.  Unity 完成生成后 (可能需要一些时间) ，它将在你的生成的位置上打开 " **文件资源管理器** " 窗口 (检查任务栏，因为它可能不会始终出现在 windows 上，但会通知你添加了新的窗口) 。

在 HoloLens 上部署：

1.  需要为远程部署) 提供 HoloLens (的 IP 地址，并确保 HoloLens 处于 **开发人员模式** 。 要执行此操作：

    1.  在戴上 HoloLens 的同时，请打开 **设置** 。

    2.  中转到 **网络 & Internet**  >  **wi-fi**  >  **高级选项**

    3.  记下 **IPv4** 地址。

    4.  接下来，导航回 " **设置** "，然后为 **Update & Security**  >  **开发人员** 更新 & 安全性

    5.  设置 **开发人员模式** 。

2.  导航到新的 Unity 生成 ( **应用** 文件夹) 并通过 **Visual Studio** 打开解决方案文件。

3.  在 *解决方案配置* 中，选择 " **调试** "。

4.  在 *解决方案平台* 中，选择 " **X86，远程计算机** "。 系统将提示你插入远程设备的 **IP 地址** (HoloLens，在本例中，你记) 。

    ![设置 IP 地址](images/AzureLabs-Lab302b-34.png)

5. 中转到 " **生成** " 菜单，然后单击 " **部署解决方案** "，将应用程序旁加载到 HoloLens。

6. 应用现在应显示在你的 HoloLens 上已安装的应用列表中，可以启动了！

> [!NOTE]
> 若要部署到沉浸式耳机，请将 " **解决方案平台** " 设置为 " *本地计算机* "，并将 **配置** 设置为 " *调试* "，将 " *x86* " 设置为 **平台** 。 然后，使用 " **生成** " 菜单项选择 " *部署解决方案* "，将部署到本地计算机。 

## <a name="to-use-the-application"></a>使用应用程序：

若要在 *定型* 模式和 *预测* 模式间切换应用功能，需要更新 **AppMode** 变量，该变量位于 *ImageCapture* 类中的 " **唤醒 ( # B1** " 方法中。

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
或
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

在 *定型* 模式下：

- 查看 **鼠标** 或 **键盘** ，并使用 **点击手势** 。

- 接下来，将显示文本，要求你提供标记。

- 说 **鼠标** 或 **键盘** 。


在 *预测* 模式下：

- 查看对象并使用 **点击动作** 。

- 文本将显示，并显示检测到的对象，并且最高的概率 (这是标准化) 。

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>第14章-评估并改善自定义视觉模型

若要使您的服务更准确，需要继续训练用于预测的模型。 这是通过将新应用程序与 *培训* 和 *预测* 模式结合使用来实现的，后者要求你访问门户，本章将介绍这一点。 准备多次重新访问您的门户，以不断改善您的模型。

1. 再次转到 Azure 自定义视觉门户，在项目中，从页面顶部中心 (选择 " *预测* " 选项卡) ：

    ![选择预测选项卡](images/AzureLabs-Lab302b-35.png)

2. 在应用程序运行时，你将看到所有已发送到服务的映像。 如果你将鼠标悬停在这些图像上，它们将为你提供对该映像进行的预测：

    ![预测图像列表](images/AzureLabs-Lab302b-36.png)

3. 选择其中一个映像，将其打开。 打开后，您将看到对该图像的预测。 如果预测是正确的，并且您希望将此图像添加到服务的训练模型，请单击 " *我的标记* " 输入框，然后选择您要关联的标记。 完成后，单击右下角的 " *保存并关闭* " 按钮，然后继续转到下一张图像。

    ![选择要打开的图像](images/AzureLabs-Lab302b-37.png)

4. 返回到图像网格后，你会注意到，已将标记添加到 (并保存) 的映像将被删除。 如果你发现你认为没有标记项的任何图像，则可以删除它们，方法是单击该图像上的勾选标记 (可以对几个图像执行此操作) 然后单击网格页右上角的 " *删除* "。 在下面的弹出窗口中，可以单击 *"是"、"删除* " 或 " *否* " 以确认删除或取消。 

    ![删除映像](images/AzureLabs-Lab302b-38.png)

5. 准备好继续时，单击右上方的绿色 *训练* 按钮。 你的服务模型将使用你现在提供 (的所有映像定型，使其更准确) 。 训练完成后，请确保再次单击 "设置 *默认值* " 按钮，使 *预测 URL* 继续使用最新的服务迭代。

    ![开始培训服务模型 ](images/AzureLabs-Lab302b-39.png) ![ 选择 "设置默认值" 选项](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>已完成的自定义视觉 API 应用程序

恭喜，你构建了一个使用 Azure 自定义视觉 API 来识别真实世界对象的混合现实应用，为服务模型定型，并显示对所见内容的信心。

![完成的项目示例](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习1

训练 **自定义影像服务** 来识别更多对象。

### <a name="exercise-2"></a>练习2

若要在了解的情况下进行扩展，请完成以下练习：

在识别对象时播放声音。

### <a name="exercise-3"></a>练习3

使用 API 来重新训练你的服务，使其与你的应用程序正在分析的映像相同，以便使服务更准确 (同时) 的预测和培训。
