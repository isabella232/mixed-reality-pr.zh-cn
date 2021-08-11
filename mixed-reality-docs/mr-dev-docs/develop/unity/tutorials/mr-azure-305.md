---
title: HoloLens（第一代）和 Azure 305 - 功能和存储
description: 完成本课程，了解如何在混合Azure 存储应用程序中实现函数和函数。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure， 混合现实， 学院， unity， 教程， api， 函数， 存储， hololens， 沉浸式， vr， Windows 10， Visual Studio
ms.openlocfilehash: 337b1d3fb23450325805237a6ba975861260760b7d37028b8d717bad99b9d233
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193824"
---
# <a name="hololens-1st-gen-and-azure-305-functions-and-storage"></a>HoloLens (第一代) Azure 305：函数和存储

<br>

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来将发布一系列新的教程，演示如何针对 HoloLens 2。  发布这些教程时，此通知将更新为指向这些教程的链接。

<br> 

![final product -start](images/AzureLabs-Lab5-00.png)

本课程将学习如何在混合现实Azure Functions创建和使用数据Azure 存储存储数据。

*Azure Functions* 是一项 Microsoft 服务，可让开发人员在 Azure 中运行小段代码"函数"。 这提供了一种将工作委托给云（而不是本地应用程序）的方法，这可带来许多好处。 *Azure Functions* 多种开发语言，包括 \# \# C、F、Node.js、Java 和 PHP。 有关详细信息，请访问文章[Azure Functions 。](/azure/azure-functions/functions-overview)

*Azure 存储* 是一项 Microsoft 云服务，它允许开发人员存储数据，并保证数据高度可用、安全、持久、可缩放和冗余。 这意味着 Microsoft 将处理所有维护和关键问题。 有关详细信息，请访问 Azure 存储[文章](/azure/storage/common/storage-introduction)。

完成本课程后，你将拥有一个混合现实沉浸式头戴显示设备应用程序，该应用程序能够执行以下操作：

1.  允许用户在场景周围凝视。
2.  当用户凝视 3D"按钮"时，触发对象的生成。
3.  生成的对象由 Azure 函数选择。
4.  生成每个对象时，应用程序将对象类型存储在 *Azure 文件*（位于 *Azure 存储）。*
5.  第二次加载时，将检索 *Azure* 文件数据，并用于重播来自应用程序的上一个实例的生成操作。

在应用程序中，由你决定如何将结果与设计集成。 本课程旨在教授如何将 Azure 服务与 Unity Project。 你的工作是利用从本课程中获得的知识来增强混合现实应用程序。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 和 Azure 305：Functions 和存储</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 虽然本课程主要重点介绍Windows Mixed Reality VR () 头戴显示设备，但也可以将本课程中学习到Microsoft HoloLens。 随着课程的进行，你将看到有关支持此课程可能需要采用的任何更改HoloLens。

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
- Azure 帐户的订阅，用于创建 Azure 资源
- 用于 Azure 设置和数据检索的 Internet 访问

## <a name="before-you-start"></a>开始之前

为了避免在生成此项目时遇到问题，强烈建议在根文件夹或近根文件夹中创建本教程中提到的项目 (长文件夹路径可能会导致生成时) 。

## <a name="chapter-1---the-azure-portal"></a>第 1 章 - Azure 门户

若要使用 **Azure 存储 服务**，需要在 Azure 门户 中创建和配置 **存储** 帐户。

1.  登录到 Azure  [门户](https://portal.azure.com)。

    > [!NOTE]
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室环境中遵循本教程，请询问讲师或其中一位讲师，以帮助设置新帐户。

2.  登录后，单击左上角的"新建"，搜索"存储 *帐户"，* 然后单击"**输入"。**

    ![azure 存储搜索](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > 在较 **新的** 门户中，"新建"一词可能已被替换为"创建资源"。

3.  新页面将提供帐户服务 *Azure 存储说明*。 在此提示的左下角， **选择"创建** "按钮，创建与此服务的关联。

    ![创建服务](images/AzureLabs-Lab5-02.png)

4.  单击"创建" **后**：

    1.  插入 *帐户* 的名称，请注意，此字段仅接受数字和小写字母。

    2.  对于 *"部署模型"，* 请选择 **"资源管理器"。**

    3.  对于 *"帐户类型***"，存储 (常规用途 v1) 。**

    4.  如果要 *创建新的* 资源组组 (，请确定资源组) 。 理想情况下，位置将位于应用程序将运行的区域。 某些 Azure 资产仅在某些区域可用。

    5.  对于 *"复制***"，请选择"读取访问异地冗余存储 (RA-GRS) "**。

    6.  对于“性能”，请选择“标准”。

    7.  将 *"需要安全传输"* 保留为 **"已禁用"。**

    8.  选择一个“订阅”  。

    9. 选择一 *个资源组* 或创建一个新资源组。 资源组提供了一种方法来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将与单个项目关联的所有 Azure 服务 (例如，这些实验室) 位于公共资源组) 。 

        > 若要详细了解 Azure 资源组，请访问 [资源组一文](/azure/azure-resource-manager/resource-group-portal)。

    10. 还需要确认你已了解适用于此服务的条款和条件。

    11. 选择“创建”。 

        ![输入服务信息](images/AzureLabs-Lab5-03.png)

5.  单击"创建 **"** 后，必须等待服务创建完成，这可能需要一分钟。

6.  创建服务实例后，门户中会显示一条通知。

    ![Azure 门户中的新通知](images/AzureLabs-Lab5-04.png)

7.  单击通知以浏览新的服务实例。

    ![转到资源](images/AzureLabs-Lab5-05.png)

8.  单击 **通知中的"** 转到资源"按钮，浏览新的服务实例。 你将使用新的帐户存储 *实例*。

    ![访问密钥](images/AzureLabs-Lab5-06.png)

9.  单击 *"访问* 密钥"以显示此云服务的终结点。 使用 *记事本* 或类似项复制密钥之一，供以后使用。 另请注意 *"连接字符串* "值，因为它将在稍后创建的 *AzureServices* 类中使用。

    ![复制连接字符串](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>第 2 章 - 设置 Azure 函数

现在，你将在 **Azure** **服务中** 编写 Azure 函数。

可以使用 Azure **函数** 执行几乎与在代码中对经典函数执行的任何操作，不同之处在于，具有用于访问 Azure 帐户的凭据的任何应用程序都可以访问此函数。

若要创建 Azure 函数，请执行：

1.  在 *Azure 门户中*，单击 **左上角的"** 新建"，搜索"*函数应用*"，然后单击"**输入"。**

    ![创建函数应用](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > 在较 **新的** 门户中，"新建"一词可能已被替换为"创建资源"。

2.  新页面将提供 *Azure Function App 服务* 的说明。 在此提示的左下角， **选择"创建** "按钮，创建与此服务的关联。

    ![函数应用信息](images/AzureLabs-Lab5-09.png)

3.  单击"创建" **后**：

    1.  提供应用 *名称*。 此处只能使用字母和数字 (大写或小写字母) 。

    2.  选择 *首选订阅*。

    3. 选择一 *个资源组* 或创建一个新资源组。 资源组提供了一种方法来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将与单个项目关联的所有 Azure 服务 (例如，这些实验室) 位于公共资源组) 。 

        > 若要详细了解 Azure 资源组，请访问 [资源组一文](/azure/azure-resource-manager/resource-group-portal)。

    4.  对于本练习 *，请选择Windows* OS 作为所选 **OS。**

    5.  为 *"托管* 计划 **"选择"消耗计划"。**

    6.  如果要 *创建新的* 资源组组 (，请确定资源组) 。 理想情况下，位置将位于应用程序将运行的区域。 某些 Azure 资产仅在某些区域可用。 为获得最佳性能，请选择与存储帐户相同的区域。

    7.  对于 *存储，* 请选择"**使用现有**"，然后使用下拉菜单找到以前创建的存储。

    8.  对于 *本Insights，* 请让"应用程序"保持关闭状态。

        ![输入函数应用详细信息](images/AzureLabs-Lab5-10.png)

4.  单击“创建”按钮。

5.  单击"创建 **"** 后，必须等待服务创建完成，这可能需要一分钟。

6.  创建服务实例后，门户中会显示一条通知。

    ![新的 Azure 门户通知](images/AzureLabs-Lab5-11.png)

7.  单击通知以浏览新的服务实例。 

    ![转到资源函数应用](images/AzureLabs-Lab5-12.png)

8.  单击 **通知中的"** 转到资源&quot;按钮，浏览新的服务实例。 你将被带至新的 *Function App 服务* 实例。

9.  在 *&quot;函数应用&quot;* 仪表板上，将鼠标悬停在左侧面板中的&quot;函数&quot;上，然后单击 **&quot;+ (")** 符号。

    ![创建新函数](images/AzureLabs-Lab5-13.png)

10. 下一页上，确保 **已选择"Webhook + API"，** 对于"选择语言"，请选择 **"CSharp"，** 因为这将是本教程使用的语言。  最后，单击" **创建此函数"** 按钮。

    ![选择 Web hook csharp](images/AzureLabs-Lab5-14.png)

11. 应会访问 run.csx (的代码页，) ，请单击左侧面板中"函数"列表中的新创建函数。

    ![打开新函数](images/AzureLabs-Lab5-15.png)

12. 将以下代码复制到函数中。 调用时，此函数将仅返回介于 0 和 2 之间的随机整数。 不必担心现有代码，可随意将其粘贴到顶部。

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. 选择“保存”。

14. 结果应如下图所示。

15. 单击" **获取函数 URL"** 并记下 *显示的* 终结点。 需要将其插入到本课程稍后将创建的 *AzureServices* 类中。

    ![获取函数终结点](images/AzureLabs-Lab5-16.png)

    ![插入函数终结点](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>第 3 章 - 设置 Unity 项目

以下是使用混合现实进行开发的典型设置，因此，是其他项目的良好模板。

设置并测试混合现实沉浸式头戴显示设备。

> [!NOTE]
> 本课程 **不需要** 运动控制器。 如果需要支持设置沉浸式头戴显示设备，请访问 [混合现实设置文章](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  打开 Unity，然后单击"新建 **"。**

    ![创建新的 Unity 项目](images/AzureLabs-Lab5-17.png)

2.  现在需要提供 Unity Project名称。 插入 **MR_Azure_Functions**。 确保项目类型设置为 **3D**。 将" *位置* "设置为适合你记住 (，越靠近根目录越好) 。 然后单击"创建 **项目"。**

    ![为新的 Unity 项目命名](images/AzureLabs-Lab5-18.png)

3.  打开 Unity 后，值得检查 **默认脚本编辑器** 是否设置为 **Visual Studio。** 转到"**编辑**  >  **首选项"，** 然后从新窗口导航到"**外部工具"。** 将 **"外部脚本编辑器"****更改为 Visual Studio 2017。** 关闭 **"首选项"** 窗口。

    ![将 Visual Studio 设置为脚本编辑器](images/AzureLabs-Lab5-19.png)

4.  接下来，单击"切换设置"按钮，转到"文件生成"Windows"平台"，将平台切换到"通用  >  **平台**"。 

    ![将平台切换到 uwp](images/AzureLabs-Lab5-20.png)

5.  转到 **"**  >  **文件生成设置** 并确保：

    1. **目标设备** 设置为"任何 **设备"。**

        > 对于Microsoft HoloLens，将 **"目标设备"** 设置为 *HoloLens。*

    2. **生成类型** 设置为 **D3D**

    3. **SDK** 设置为"最新 **安装"**

    4. **Visual Studio版本** 设置为"最新 **安装"**

    5. **"生成和运行** "设置为" **本地计算机"**

    6. 保存场景并将其添加到生成。

        1.  为此，选择"**添加打开的场景"。** 将显示保存窗口。

            ![添加打开的场景](images/AzureLabs-Lab5-21.png)

        2.  为此和任何将来的场景创建新文件夹，然后选择"新建文件夹"按钮，以创建新文件夹，将其命名为 **"场景"。**

            ![创建场景文件夹](images/AzureLabs-Lab5-22.png)

        3.  打开新创建的 **"场景**"文件夹，然后在"文件名 **：** 文本"字段中键入 **"FunctionsScene"，** 然后按"保存 **"。**

            ![保存函数场景](images/AzureLabs-Lab5-23.png)

6.  目前，"**生成设置中的** 其余设置应保留为默认值。

    ![保留默认生成设置](images/AzureLabs-Lab5-24.png)

7.  在"*生成设置* 窗口中，单击"播放器设置按钮，这将在 *检查* 器所在的空间中打开相关面板。

    ![检查器中的播放器设置](images/AzureLabs-Lab5-25.png)

8.  在此面板中，需要验证一些设置：

    1.  在"**其他设置** 选项卡中：

        1.  **脚本运行时版本** 应为试验版 **(.NET** 4.6 等效) ，这将触发需要重启编辑器。
        2.  **脚本后端应为** **.NET**
        3.  **API 兼容性级别** 应为 **.NET 4.6**

    2.  在"**发布设置** 选项卡中的"**功能"下**，选中：
        
        -  **InternetClient**

            ![设置功能](images/AzureLabs-Lab5-26.png)

    3.  在面板的下方，在"发布 设置) "下找到的 **"XR** 设置 ("中，勾选"支持虚拟现实"，确保Windows Mixed Reality  **SDK。**

        ![设置 XR 设置](images/AzureLabs-Lab5-27.png)

9.  返回到 *"生成设置* *Unity C#* 项目不再灰度;勾选此 旁边的复选框。

    ![tick c# projects](images/AzureLabs-Lab5-28.png)

10.  关闭“生成设置”窗口。

11. 保存场景和Project (  >  **保存场景/文件**  >  **保存项目**) 。

## <a name="chapter-4---setup-main-camera"></a>第 4 章 - 设置主相机

> [!IMPORTANT]
> 如果要跳过 *Unity 设置* 本课程的组件，并继续直接编写代码，请随意下载 [此 .unitypackage，](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)并作为自定义包将其导入 [项目中](https://docs.unity3d.com/Manual/AssetPackages.html)。 这还将包含下一章中的 DLL。 导入后，从 [第7章](#chapter-7---create-the-azureservices-class)继续。 

1.  在 " *层次结构" 面板* 中，你会看到一个名为 " **主相机**" 的对象，此对象表示你在应用程序中 "内部" 后的 "头" 点。

2.  在您前面的 Unity 仪表板中，选择 " **GameObject" 主摄像机**。 你将注意到 "*检查器" 面板* (通常会在面板中找到，) 会显示该 *GameObject* 的各种组件，并在顶部、*照相机* 和一些其他组件上进行 *变换*。 需要重置主摄像机的转换，以便正确定位。

3.  为此，请选择相机 *转换* 组件旁边的 **齿轮** 图标，然后选择 "**重置**"。

    ![重置转换](images/AzureLabs-Lab5-29.png)

4.  然后，将 **转换** 组件更新为如下所示：

    |         |    转换位置   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **是**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | 转换-旋转 |       |
    | :---: | :------------------: | :----:|
    | **X** | **是**                | **Z** |
    | 0     | 0                    | 0     |

    |       | 转换-缩放 |       |
    | :---: | :---------------: | :---: |
    | **X** | **是**             | **Z** |
    | 1     | 1                 | 1     |

    ![设置相机转换](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>第5章-设置 Unity 场景

1.  右键单击 " *层次结构" 面板* 的空白区域中的 " **3d 对象**" 下的 "添加 **平面**"。

    ![创建新平面](images/AzureLabs-Lab5-31.png)

2.  选择 " **平面** " 对象后，在 " *检查器" 面板* 中更改以下参数：

    |       | 转换位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **是**                | **Z** |
    | 0     | 0                    | 4     |

    |       | 转换-缩放 |       |
    | :---: | :---------------: | :---: |
    | **X** | **是**             | **Z** |
    | 10    | 1                 | 10    |

    ![设置平面位置和刻度](images/AzureLabs-Lab5-32.png)

    ![平面的场景视图](images/AzureLabs-Lab5-33.png)

3.  右键单击 " *层次结构&quot; 面板* 的空白区域中的 &quot; **三维对象**&quot; 下的 &quot;添加 **多维数据集**&quot;。

    1.  将多维数据集重命名为 **GazeButton** (选中多维数据集后，按 &quot;F2" ) 。

    2.  在 " *检查器" 面板* 中更改以下参数：

        |       | 转换位置 |       |
        | :---: | :------------------: |:-----:|
        | **X** | **是**                | **Z** |
        | 0     | 3                    | 5     |


        ![设置注视按钮转换](images/AzureLabs-Lab5-34.png)

        ![注视按钮场景视图](images/AzureLabs-Lab5-35.png)

    3.  单击 " **标记** " 下拉按钮，然后单击 " **添加标记** " 以打开 " *标记 & 层" 窗格*。

        ![添加新标记](images/AzureLabs-Lab5-36.png)

        ![选择加号](images/AzureLabs-Lab5-37.png)

    4.  选择 " **+ (加)** " 按钮，然后在 " *新标记名称* " 字段中，输入 **GazeButton**，然后按 " **保存**"。

        ![命名新标记](images/AzureLabs-Lab5-38.png)

    5.  单击 "*层次结构" 面板* 中的 **GazeButton** 对象，然后在 "*检查器" 面板* 中，分配新创建的 **GazeButton** 标记。

        ![为新标记分配 "注视" 按钮](images/AzureLabs-Lab5-39.png)

4.  右键单击 "*层次结构" 面板* 中的 **GazeButton** 对象，然后添加一个 **空的 GameObject** (，该对象将作为 *子* 对象添加) 。

5.  选择新的对象，并将其重命名为 **ShapeSpawnPoint**。

    1.  在 " *检查器" 面板* 中更改以下参数：

        |       | 转换位置 |       |
        | :---: | :------------------: |:----: |
        | **X** |**是**                 | **Z** |
        | 0     | -1                   | 0     |

        ![更新形状衍生点转换](images/AzureLabs-Lab5-40.png)

        ![形状生成点场景视图](images/AzureLabs-Lab5-41.png)

6.  接下来，你将创建一个 **3D 文本** 对象，以提供有关 Azure 服务状态的反馈。

    再次右键单击 "层次结构" 面板中的 **GazeButton** ，并添加一个 **3d 对象**  >  **3d 文本** 对象作为 *子* 对象。

    ![创建新的3D 文本对象](images/AzureLabs-Lab5-42.png)

7.  将 **3D 文本** 对象重命名为 **AzureStatusText**。

8.  按如下所示更改 **AzureStatusText** 对象转换：

    |       | 转换位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **是**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | 转换-缩放 |       |
    | :---: | :---------------: | :---: |
    | **X** | **是**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > 请不要担心它看起来是离线的，因为在更新以下文本网格组件时，将修复这种情况。

9.  更改 **文本网格** 组件以匹配以下内容：

    ![设置文本网格组件](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > 此处所选的颜色是十六进制颜色： **000000FF**，但可以随意选择自己的颜色，只需确保它是可读的。

10. 层次结构面板结构现在应如下所示：

    ![层次结构中的文本网格](images/AzureLabs-Lab5-43b.png)

10. 您的场景现在应如下所示：

    ![场景视图中的文本网格](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>第6章-导入 Unity Azure 存储

你将对 Unity 使用 Azure 存储， (这种自身利用 .net SDK for Azure) 。 有关详细信息，请参阅[Unity Azure 存储](/sandbox/gamedev/unity/azure-storage-unity)。

当前 Unity 中存在一个已知问题，需要在导入后重新配置插件。 此部分中 (4-7 的这些步骤) 解决 bug 后不再需要这些步骤。

若要将 SDK 导入到自己的项目中，请确保已从 GitHub 下载最新的["unitypackage"](https://aka.ms/azstorage-unitysdk)。 然后执行以下操作：

1.  使用 "  **资产**  >  **导入包**  >  **自定义包**" 菜单选项将 unitypackage 文件添加到 Unity。

2.  在弹出的 "**导入 Unity 包**" 框中，可以选择 "**插件**" 存储下的所有内容  >  。 取消选中所有其他内容，因为本课程不需要这样做。

    ![导入到包](images/AzureLabs-Lab5-45.png)

3.  单击 " **导入** " 按钮，将项添加到项目。

4.  在 "*插件*" 下的 "*存储*" 文件夹中，在 "Project" 视图中，选择 "*仅* 以下插件"：

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![取消选中任何平台](images/AzureLabs-Lab5-46.png)

5.  选择 *这些特定插件* 后，**取消选中***任何平台* 并 **取消选中**" *WSAPlayer* "，然后单击 "**应用**"。

    ![应用平台 dll](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > 我们正在将这些特定插件标记为仅在 Unity 编辑器中使用。 这是因为在从 Unity 导出项目后，将使用 WSA 文件夹中的相同插件的不同版本。

6.  在 *存储* 插件 "文件夹中，选择" 仅限 "：

    -   Microsoft.Data.Services.Client

        ![为 dll 设置不处理](images/AzureLabs-Lab5-48.png)

7.  选中 "*平台设置* 下的"**不处理**"框，然后单击"**应用**"。

    ![不应用处理](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > 我们正在将此插件标记为 "不处理"，因为 Unity 程序集 patcher 在处理此插件时遇到困难。 即使未处理插件，该插件仍可正常工作。

## <a name="chapter-7---create-the-azureservices-class"></a>第7章-创建 Azure 服务类

要创建的第一个类是 *azure 服务* 类。

*Azure 服务* 类将负责：

-   存储 Azure 帐户凭据。

-   调用 Azure 应用函数。

-   在 Azure 云中存储上传和下载数据文件。

若要创建此类：

1.  右键单击 "*资产*" 文件夹，该文件夹位于 "Project" 面板中的 "**创建**  >  **文件夹**"。 命名文件夹 **脚本**。

    ![创建新文件夹](images/AzureLabs-Lab5-50.png)

    ![调用文件夹-脚本](images/AzureLabs-Lab5-51.png)

2.  双击刚创建的文件夹以将其打开。

3.  右键单击文件夹内的 "**创建**  >  **c # 脚本**"。 调用脚本 *azure 服务*。

4.  双击新的 *azure 服务* 类，以 *Visual Studio* 打开它。

5.  将以下命名空间添加到 *azure 服务* 的顶部：

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  在 *azure 服务* 类中添加以下检查器字段：

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  然后在 *azure 服务* 类中添加以下成员变量：

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > 请确保将 *终结点* 和 *连接字符串* 值替换为 Azure 门户中的 azure 存储值

8.  现在需要添加 *唤醒 ()* 和 *启动 ()* 方法的代码。 类初始化时，将调用这些方法：

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > 我们将在 [以后的章节](#chapter-10---completing-the-azureservices-class)中填写 *CallAzureFunctionForNextShape ()* 的代码。

9.  删除 () 方法的 *更新* ，因为此类将不会使用它。

10. 在 Visual Studio 中保存更改，然后返回到 Unity。

11. 单击 "脚本" 文件夹中的 *azure 服务* 类，并将其拖到 " *层次结构" 面板* 中的主相机对象。

12. 选择主摄像机，并从 **GazeButton** 对象下获取 **AzureStatusText** 子对象，并将其放置在 *检查器* 的 **AzureStatusText** 引用目标字段中，以提供对 *azure 服务* 脚本的引用。

    ![分配 azure 状态文本引用目标](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>第8章-创建 ShapeFactory 类

要创建的下一个脚本是 *ShapeFactory* 类。 此类的作用是在请求时创建一个新的形状，并保存在 *形状历史记录列表* 中创建的形状的历史记录。 每次创建形状时，都将在 *new-azureservice* 类中更新 *形状历史记录列表*，然后将其存储在 *Azure 存储* 中。 当应用程序启动时，如果在您的 *Azure 存储* 中找到存储文件，则将检索和重播 *形状历史记录列表*，其中包含提供生成的形状是来自存储还是新的 **3d 文本** 对象。

若要创建此类：

1.  中转到前面创建的 " **脚本** " 文件夹。

2.  右键单击文件夹内的 "**创建**  >  **c # 脚本**"。 调用脚本 *ShapeFactory*。

3.  双击新的 " *ShapeFactory* " 脚本，用 *Visual Studio* 打开它。

4.  确保 *ShapeFactory* 类包含以下命名空间：

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  将下面显示的变量添加到 *ShapeFactory* 类，并将 *Start ()* 和 *唤醒 ()* 函数替换为以下内容：

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  *CreateShape ()* 方法基于提供的 *整数* 参数生成基元形状。 布尔参数用于指定当前创建的形状是来自存储还是新的。 在 *ShapeFactory* 类中，将以下代码放在前面的方法之前：

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  返回到 Unity 之前，请务必在 Visual Studio 中保存所做的更改。

8.  返回 Unity 编辑器，单击 "**脚本**" 文件夹中的 *ShapeFactory* 类并将其拖到 "*层次结构" 面板* 中的 **主相机** 对象。

9. 选择主相机后，你会注意到 *ShapeFactory* 脚本组件缺少 *生成点* 引用。 若要修复此问题，请将 **ShapeSpawnPoint** 对象从 " *层次结构" 面板* 拖动到 " **生成点** 引用目标"。

    ![设置形状工厂引用目标](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>第9章-创建注视类

你需要创建的最后一个脚本是看不到 *的类。*

此类负责创建将从主相机向前投影的 **Raycast** ，以检测用户正在查看的对象。 在这种情况下，Raycast 需要确定用户是否正在查看场景中的 **GazeButton** 对象并触发行为。

若要创建此类：

1.  中转到前面创建的 " **脚本** " 文件夹。

2.  右键单击 "Project" 面板中的 "**创建**  >  **c # 脚本**"。 调用脚本 *注视*。

3.  双击新的 "*注视*" 脚本，用 Visual Studio 打开它 *。*

4.  确保脚本顶部包含以下命名空间：

    ```csharp
        using UnityEngine;
    ```

5.  然后在 *注视* 类中添加以下变量：

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> 其中一些变量将能够在 *编辑器* 中进行编辑。

6.  现在需要添加 *唤醒 ()* 和 *启动 ()* 方法的代码。

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  添加下面的代码，它将在开始时创建一个 cursor 对象，以及 *更新 ()* 方法，该方法将运行 Raycast 方法，并在 GazeEnabled 布尔值的切换位置：

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. 接下来，添加 *UpdateRaycast ()* 方法，该方法将投影 Raycast 并检测命中目标。

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. 最后，添加 *ResetFocusedObject ()* 方法，该方法将切换 GazeButton 对象的当前颜色，以指示是否正在创建新的形状。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  在返回到 Unity 之前，请将所做的更改保存在 Visual Studio 中。

11.  单击 "脚本" 文件夹中的 "*注视*" 类并将其拖到 "*层次结构" 面板* 中的 **主相机** 对象。

## <a name="chapter-10---completing-the-azureservices-class"></a>第10章-完成 Azure 服务类

当其他脚本准备就绪后，现在可以 *完成* *azure 服务* 类。 这将通过以下步骤实现：

1.  添加一个名为 *CreateCloudIdentityAsync ()* 的新方法来设置与 Azure 进行通信所需的身份验证变量。

    > 此方法还会检查是否存在包含形状列表的以前存储的文件。
    >
    > **如果找到该文件**，它将禁用用户 *注视*，并根据形状的模式（在 **Azure 存储文件** 中存储）触发形状创建。 用户可以查看此内容，因为 **文本网格** 会提供 "存储" 或 "新建"，具体取决于形状原点。
    >
    > **如果找不到文件**，它将启用 *注视*，使用户能够在查看场景中的 **GazeButton** 对象时创建形状。

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  下一个代码段来自 *Start ()* 方法，将对 *CreateCloudIdentityAsync ()* 方法进行调用。 可随意复制当前 *开始 ()* 方法，如下所示：

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  填写方法 *CallAzureFunctionForNextShape ()* 的代码。 你将使用之前创建的 *Azure Function App* 来请求形状索引。 接收到新形状后，此方法会将形状发送到 *ShapeFactory* 类，以在场景中创建新的形状。 使用下面的代码完成 *CallAzureFunctionForNextShape ()* 的正文。

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  添加一个方法来创建字符串，方法是连接形状历史记录列表中存储的整数，然后将其保存到 *Azure 存储文件* 中。

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  添加一个方法，用于检索存储在位于 *Azure 存储文件* 中的文件中的文本，并将其 *反序列化为* 列表。

6.  完成此过程后，该方法将重新启用注视，使用户可以将更多形状添加到场景中。

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  在返回到 Unity 之前，请将所做的更改保存在 Visual Studio 中。

## <a name="chapter-11---build-the-uwp-solution"></a>第11章-构建 UWP 解决方案

开始生成过程：

1.  请参阅 **文件**  >  **生成设置**。

    ![构建应用程序](images/AzureLabs-Lab5-54.png)

2.  单击“生成”。 Unity 将启动 *文件资源管理器* 窗口，在该窗口中，需要创建一个文件夹，然后选择要在其中生成应用的文件夹。 立即创建该文件夹并将其命名为 *应用*。 选择 *应用* 文件夹后，按 " **选择文件夹**"。

3.  Unity 将开始向 *应用* 文件夹生成项目。

4.  Unity 完成生成后 (可能需要一些时间) ，它将在你的生成的位置上打开 " *文件资源管理器* " 窗口 (检查任务栏，因为它可能不会始终出现在 windows 上，但会通知你添加了新的窗口) 。

## <a name="chapter-12---deploying-your-application"></a>第12章-部署应用程序

若要部署应用程序：

1.  导航到在 [上一章](#chapter-11---build-the-uwp-solution)中创建的 *应用* 文件夹。 你将看到一个文件，其中包含你的应用程序的名称，扩展名为 ".sln"，因此，要在 *Visual Studio* 中打开它。

2.  在 **解决方案平台** 中，选择 " **X86，本地计算机**"。

3.  在 **解决方案配置** 中，选择 " **调试**"。

    > 对于 Microsoft HoloLens，你可能会发现将其设置为 *远程计算机* 会更容易，因此你不会受限到计算机上。 不过，还需要执行以下操作：
    > - 知道 HoloLens 的 **IP 地址**，该地址可以在 **设置**  >  **网络 & Internet**  >  **wi-fi**  >  **高级选项** 中找到; IPv4 是应使用的地址。 
    > - 确保 **开发人员模式** 已 **打开**;**设置**  >  **更新 &**  >  **为开发人员提供** 安全性。

    ![部署解决方案](images/AzureLabs-Lab5-55.png)

4.  请在 " **生成** " 菜单中，单击 " **部署解决方案** "，将应用程序旁加载到计算机上。

5.  应用现在应显示在已安装的应用列表中，可以启动和测试！

## <a name="your-finished-azure-functions-and-storage-application"></a>已完成的 Azure Functions 和存储应用程序

恭喜，你构建了一个同时利用 Azure Functions 和 Azure 存储服务的混合现实应用。 你的应用程序将能够在存储的数据上进行绘制，并提供基于该数据的操作。

![最终产品-结束](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习 1

创建第二个生成点，并记录创建对象的生成点。 加载数据文件时，请重播从其最初创建的位置生成的形状。

### <a name="exercise-2"></a>练习 2

创建一种方法来重新启动应用程序，而不必每次都重新打开它。 **加载场景** 是一种很好的起点。 完成此操作后，创建一种方法来清除 *Azure 存储* 中存储的列表，以便可以轻松地从应用程序重置。