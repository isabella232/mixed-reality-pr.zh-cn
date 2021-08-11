---
title: HoloLens（第一代）和 Azure 308 - 跨设备通知
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure Azure Functions、Azure 存储和表。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure， 混合现实， 学院， unity， 教程， api， 通知， 函数， 表， 通知中心， hololens， 沉浸式， vr， Windows 10， Visual Studio
ms.openlocfilehash: 01d096297a9fbe25d39b2846acd2ee89b50edcfd26456f3f20ccd2c9bc26b514
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205285"
---
# <a name="hololens-1st-gen-and-azure-308-cross-device-notifications"></a>HoloLens (第一代) Azure 308：跨设备通知

<br>

>[!NOTE]
>混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。  我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。  我们将维护这些教程，使之持续适用于支持的设备。 将来将发布一系列新的教程，演示如何针对 HoloLens 2。  发布这些教程时，此通知将更新为指向这些教程的链接。

<br>

![final product -start](images/AzureLabs-Lab8-00.png)

本课程将学习如何使用 Azure 通知中心、Azure 表和 azure 表将通知中心功能添加到混合现实Azure Functions。

**Azure 通知中心** 是一项 Microsoft 服务，可让开发人员将定向的个性化推送通知发送到云中支持的任何平台。 这可有效地使开发人员能够与最终用户通信，甚至可以在各种应用程序之间进行通信，具体取决于方案。 有关详细信息，请访问 Azure **通知中心**[页](/azure/notification-hubs/notification-hubs-push-notification-overview)。

**Azure Functions** 是一项 Microsoft 服务，可让开发人员在 Azure 中运行小段代码"函数"。 这提供了一种将工作委托给云（而不是本地应用程序）的方法，这可带来许多好处。 **Azure Functions** 多种开发语言，包括 \# \# C、F、Node.js、Java 和 PHP。 有关详细信息，请访问 Azure Functions[页](/azure/azure-functions/functions-overview)。

**Azure 表** 是一项 Microsoft 云服务，可让开发人员将结构化SQL数据存储在云中，使其可在任何位置轻松访问。 该服务采用无架构设计，允许根据需要演变表，因此非常灵活。 有关详细信息，请访问 Azure **表**[页](/azure/cosmos-db/table-storage-overview)

完成本课程后，你将拥有一个混合现实沉浸式头戴显示设备应用程序和一个桌面电脑应用程序，该应用程序将能够执行以下操作：

1. 桌面电脑应用允许用户使用鼠标在 2D 空间中移动 (X 和 Y) 对象。

2. 电脑应用中的对象移动将使用 JSON 发送到云，JSON 将采用字符串形式，其中包含对象 ID、类型和转换信息 (X 和 Y 坐标) 。 

3. 混合现实应用与桌面应用具有相同的场景，它将从通知中心服务接收有关对象移动的通知 (该通知刚刚由桌面电脑应用应用更新) 。 

4. 收到包含对象 ID、类型和转换信息的通知后，混合现实应用将接收的信息应用到其自己的场景中。

在应用程序中，由你决定如何将结果与设计集成。 本课程旨在教授如何将 Azure 服务与 Unity Project。 你的工作是利用从本课程中获得的知识来增强混合现实应用程序。 本课程是一个自包含教程，不直接涉及任何其他混合现实实验室。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> MR 和 Azure 308：跨设备通知</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 虽然本课程主要重点介绍Windows Mixed Reality VR () 头戴显示设备，但也可以将本课程中学习到Microsoft HoloLens。 随着课程的进行，你将看到有关支持此课程可能需要采用的任何更改HoloLens。 使用语音HoloLens，你可能会注意到在语音捕获期间有一些回显。

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
- Azure 设置和访问通知中心的 Internet 访问

## <a name="before-you-start"></a>开始之前

- 为了避免在生成此项目时遇到问题，强烈建议在根文件夹或近根文件夹中创建本教程中提到的项目 (长文件夹路径可能会导致生成时) 。
- 你必须是 Microsoft 开发人员 门户和应用程序注册门户的所有者，否则你将无权访问第 [2 章中的应用](#chapter-2---retrieve-your-new-apps-credentials)。

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>第 1 章 - 在 Microsoft 开发人员 门户上创建应用程序

若要使用 **Azure 通知** 中心服务，需要在 Microsoft 开发人员 门户上创建应用程序，因为应用程序需要注册，以便它可以发送和接收通知。

1.  登录到 Microsoft 开发人员 [门户](https://developer.microsoft.com/dashboard)。

    > 需要登录到 Microsoft 帐户。

2.  在仪表板中，单击 **"创建新应用"。**

    ![创建应用](images/AzureLabs-Lab8-01.png)

3.  将出现一个弹出窗口，你需要为新应用保留名称。 在文本框中，插入适当的名称;如果所选名称可用，文本框右侧将显示一个刻度。 插入可用名称后，单击弹出窗口左下角的"保留产品名称"按钮。

    ![反转名称](images/AzureLabs-Lab8-02.png)

4.  创建应用后，即可进入下一章。

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>第 2 章 - 检索新应用凭据

登录到将列出新应用的应用程序注册门户，并检索用于在 Azure 门户 中设置通知中心 **服务的****凭据**。

1.  导航到 [应用程序注册门户](https://apps.dev.microsoft.com)。

    ![应用程序注册门户](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > 你需要使用 Microsoft 帐户登录。  
    > 这 **必须是** 你在上一章 中使用的 Microsoft 帐户 [](#chapter-1---create-an-application-on-the-microsoft-developer-portal)，以及 Windows Store 开发人员门户。

2.  将在"我的应用程序"部分 **下找到** 应用。 找到它后，单击它，你将进入一个新页面，其中应用名称加上"注册 **"。**

    ![新注册的应用](images/AzureLabs-Lab8-04.png)

3.  向下滚动注册页，找到应用程序的"**应用程序机密**"部分和 **"包 SID"。** 复制这两者，以用于下一章 **中的设置 Azure** 通知中心服务。

    ![应用程序机密](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>第 3 章 - 设置 Azure 门户：创建通知中心服务

检索应用凭据后，需要转到 Azure 门户，将在其中创建 Azure 通知中心服务。

1.  登录到 [Azure 门户](https://portal.azure.com)。

    > [!NOTE] 
    > 如果还没有 Azure 帐户，则需要创建一个。 如果在课堂或实验室环境中遵循本教程，请询问讲师或其中一位讲师，以帮助设置新帐户。

2.  登录后，单击左上角的"新建"，搜索"通知 **中心**"，然后单击"**_输入"。_** 

    ![搜索通知中心](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > 在 **较新的** 门户中，"新建"一词可能已被替换为"创建资源"。

3.  新页面将提供通知 *中心服务* 的说明。 在此提示的左下角， **选择"创建** "按钮，创建与此服务的关联。

    ![创建通知中心实例](images/AzureLabs-Lab8-07.png)

4.  单击"创建" ***后***：

    1.  插入此服务实例的所需名称。

    2.  提供 **一** 个能够与此应用关联的命名空间。

    3.  选择" **位置"。**

    4.  选择一 **个资源组** 或创建一个新资源组。 资源组提供了一种方法来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将与单个项目关联的所有 Azure 服务 (例如，这些实验室) 位于公共资源组) 。

        > 若要详细了解 Azure 资源组，请按照此 [链接了解如何管理资源组](/azure/azure-resource-manager/resource-group-portal)。 

    5.  选择适当的"**订阅"。**

    6.  还需要确认你已了解适用于此服务的条款和条件。

    7. 选择“创建”。 

        ![填写服务详细信息](images/AzureLabs-Lab8-08.png)

5.  单击 " **创建**" 后，需要等待创建服务，这可能需要一分钟时间。

6.  创建服务实例后，门户中将显示一个通知。

    ![通知](images/AzureLabs-Lab8-09.png)

7.  单击通知中的 " **中转到资源** " 按钮以浏览新服务实例。 你将转到新的 **通知中心** 服务实例。

    ![中转到资源](images/AzureLabs-Lab8-10.png)
    
8.  从 "概述" 页中，单击 " **Windows (WNS) "。** 右侧面板将更改为显示两个文本字段，它们需要你之前设置的应用中的 **包 SID** 和 **安全密钥**。

    ![新创建的集线器服务](images/AzureLabs-Lab8-11.png)

9. 将详细信息复制到正确的字段后，请单击 " **保存**"，在成功更新通知中心后，将收到通知。

    ![复制安全详细信息](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>第4章-设置 Azure 门户：创建表服务

创建通知中心服务实例后，请导航回到 Azure 门户，在该门户中创建一个存储资源来创建 Azure 表服务。

1.  如果尚未登录，请登录到 [Azure 门户](https://portal.azure.com)。

2.  登录后，单击左上角的 "**新建**"，搜索 **存储帐户**"，然后单击" **Enter**"。

    > [!NOTE] 
    > 在较新的门户中，可以使用 _ * Create a 资源 * * 来替换 word ***New** _。

3.  从列表中选择 **存储帐户-blob、文件、表、队列**。

    ![搜索存储帐户](images/AzureLabs-Lab8-13.png)

4.  新页将提供 **存储帐户** 服务的说明。 在此提示符下，选择 " **创建** " 按钮，创建此服务的实例。

    ![创建存储实例](images/AzureLabs-Lab8-14.png)

5.  单击 " **创建**" 后，将显示一个面板：

    1. 为此服务实例插入所需的 **名称** ， (必须全部为小写) 。

    2. 对于 **部署模型**，单击 " **资源管理器**"。

    3.  对于 "**帐户类型**"，请使用下拉菜单选择 **存储 ("常规用途 v1)**"。

    4. 选择适当的 **位置**。
    
    5.  对于 " **复制** " 下拉菜单，选择 " **读取-访问-异地冗余存储 (GRS)**"。

    6.  对于 " **性能**"，请单击 " **标准**"。

    7.  在 " **需要安全传输** " 部分中，选择 " **禁用**"。

    8.  从 " **订阅** " 下拉菜单中，选择相应的订阅。

    9.  选择一个 **资源组** ，或创建一个新的资源组。 资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。 建议保留与单个项目关联的所有 Azure 服务 (例如，这些实验室) 在常见资源组) 下。

        > 如果希望了解有关 Azure 资源组的详细信息，请参阅此 [链接，了解如何管理资源组](/azure/azure-resource-manager/resource-group-portal)。

    10. 如果这是一个选项，请将 **虚拟网络** 保持为 **禁用状态** 。

    11. 单击“**创建**”。

        ![填写存储详细信息](images/AzureLabs-Lab8-15.png)

6.  单击 " **创建**" 后，需要等待创建服务，这可能需要一分钟时间。

7.  创建服务实例后，门户中将显示一个通知。 单击通知以浏览新服务实例。

    ![新存储通知](images/AzureLabs-Lab8-16.png)

8.  单击通知中的 " **中转到资源** " 按钮以浏览新服务实例。 你将转到新的存储服务实例概述 "页。

    ![中转到资源](images/AzureLabs-Lab8-17.PNG)

9. 在 "概述" 页中，单击右侧的 " **表**"。
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. 右侧面板将更改为显示 **表服务** 信息，你需要添加一个新表。 单击左上角的 "表" 按钮即可执行此操作 **+**  。

    ![打开表](images/AzureLabs-Lab8-19.png)

11. 将显示一个新页，需要在其中输入 **表名称**。 这是将在后面章节中用于引用应用程序中的数据的名称。 插入适当的名称，然后单击 **"确定"**。

    ![创建新表](images/AzureLabs-Lab8-20.png)    

12. 创建新表后，可在 " **表服务** " 页的底部)  (查看它。

    ![已创建新表](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>第5章-完成中的 Azure 表 Visual Studio

由于已设置了 **表服务** 存储帐户，因此可以向其添加数据，这将用于存储和检索信息。 可以通过 **Visual Studio** 来编辑表。

1.  打开“Visual Studio”。

2.  从菜单中，单击 "**查看**  >  **Cloud Explorer**"。

    ![打开 cloud explorer](images/AzureLabs-Lab8-22.png)

3.  **Cloud Explorer** 将作为停靠项打开 (患者，因为加载可能需要一些时间) 。

    > [!NOTE] 
    > 如果用于创建 *存储帐户* 的订阅不可见，请确保具有： 
    > - 已登录到与 Azure 门户一起使用的帐户。
    > - 从 "帐户管理" 页中选择了你的订阅 (你可能需要从帐户设置) 应用筛选器：  
    >
    >   ![查找订阅](images/AzureLabs-Lab8-22-5.png)

4.  将显示你的 Azure 云服务。 找到 **存储帐户**，并单击其左侧的箭头以展开帐户。

    ![打开存储帐户](images/AzureLabs-Lab8-23.png)

5.  展开后，新创建的 **存储帐户** 应该可用。 单击存储左侧的箭头，然后在展开后，查找 " **表** " 并单击该按钮旁边的箭头，以显示在上一章中创建的 **表** 。 双击 **表**。

    ![打开场景对象表](images/AzureLabs-Lab8-24.png)

6.  你的表将在 Visual Studio 窗口的中心打开。 单击带有 **+** (加) 的表图标。

    ![添加新表](images/AzureLabs-Lab8-25.png)

7.  将显示一个窗口，提示你 *添加实体*。 您将创建三个实体，每个实体都有多个属性。 你会注意到已提供了 *PartitionKey* 和 *RowKey* ，因为表使用这些方法来查找数据。 

    ![分区和行键](images/AzureLabs-Lab8-26.png)

8. 按如下所示更新 **PartitionKey** 和 **RowKey** 的 *值* (记得为你添加的每个行属性执行此操作，但每次) 递增 RowKey：

    ![添加正确的值](images/AzureLabs-Lab8-26-5.png)

9.  单击 " **添加属性** " 以添加额外的数据行。 使第一个空表与下表匹配。

10. 完成后，单击 **"确定"** 。

    ![完成后单击 "确定"](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > 确保将 **X**、 **Y** 和 **Z** 条目的 **类型** 更改为 **Double**。 

11. 你会注意到，你的表现在具有一行数据。 再次单击 **+** (加号) 图标以添加另一个实体。

    ![第一行](images/AzureLabs-Lab8-27-5.png)

12. 创建其他属性，然后将新实体的值设置为与下面显示的值相匹配。

    ![添加多维数据集](images/AzureLabs-Lab8-28.png)

13. 重复上一步以添加另一个实体。 将此实体的值设置为下面显示的值。

    ![添加圆柱体](images/AzureLabs-Lab8-29.png)

14. 现在，你的表应如下所示。

    ![表完成](images/AzureLabs-Lab8-30.png)

15. 你已完成本章节。 请确保保存。

## <a name="chapter-6---create-an-azure-function-app"></a>第 6 章 - 创建 Azure 函数应用

创建 Azure 函数应用，桌面应用程序将调用该应用来更新表服务并通过通知 **中心 发送通知**。

首先，需要创建一个文件，使 Azure 函数能够加载所需的库。

1.  打开 **记事本 (** 按Windows键并键入记事本) 。

    ![打开记事本](images/AzureLabs-Lab8-31.png)

2.  打开记事本，将下面的 JSON 结构插入该结构。 完成操作后，将其保存为桌面上的project.js **上**。 命名正确非常重要：请确保其文件扩展名 **.txt名称。** 此文件定义函数将使用的库（如果已使用NuGet看起来很熟悉。

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  登录到 [Azure 门户](https://portal.azure.com)。

4.  登录后，单击左上角的"新建"，然后搜索"**函数应用**"，按 **Enter**。 

    ![搜索函数应用](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > 在较 **新的** 门户中，"新建"一词可能已被替换为"创建资源"。

5.  新页面将提供函数应用 **服务** 的说明。 在此提示的左下角， **选择"创建** "按钮，创建与此服务的关联。

    ![函数应用实例](images/AzureLabs-Lab8-33.png)

6.  单击"创建 **"后**，填写以下内容：

    1. 对于 **"应用名称**"，插入此服务实例所需的名称。

    2. 选择一个“订阅”  。

    3. 选择适合你的定价层，如果这是第一次创建 **函数应用服务**，你应可以使用免费层。

    4. 选择一 **个资源组** 或创建一个新资源组。 资源组提供了一种方法来监视、控制访问、预配和管理 Azure 资产集合的计费。 建议将与单个项目关联的所有 Azure 服务 (例如，这些实验室) 位于公共资源组) 。

        > 若要详细了解 Azure 资源组，请按照此 [链接了解如何管理资源组](/azure/azure-resource-manager/resource-group-portal)。

    5. 对于OS，Windows，因为这是预期平台。

    6. 选择 **托管计划** (本教程使用消耗 **计划**。

    7. 选择 **"****位置 (** 选择与在上一步骤中构建的存储相同的位置) 

    8. 对于 **"存储"** 部分，必须选择在上一存储中创建 **的"服务"。**

    9. 此应用中不需要 *应用程序Insights，* 因此请随意将应用程序保留 **为"关闭"。**

    10. 单击“**创建**”。

        ![创建新实例](images/AzureLabs-Lab8-34.png)

7.  单击"创建 **"** 后，必须等待服务创建完成，这可能需要一分钟。

8.  创建服务实例后，门户中会显示一条通知。

    ![新通知](images/AzureLabs-Lab8-35.png)

9.  单击通知以浏览新的服务实例。

10. 单击 **通知中的"** 转到资源"按钮，浏览新的服务实例。 

    ![转到资源](images/AzureLabs-Lab8-36.png)

11. 单击 **+** " ("，) " *函数"* 旁边的"新建 *"图标，以创建新的*。

    ![添加新函数](images/AzureLabs-Lab8-37.png)

12. 在中央面板中，将显示 **"函数** 创建"窗口。 忽略面板上半部分的信息，然后单击"自定义函数"，该函数位于蓝色区域 (底部附近，如下所示) 。

    ![自定义函数](images/AzureLabs-Lab8-38.png)

13. 窗口中的新页面将显示各种函数类型。 向下滚动以查看紫色类型，然后单击 **"HTTP PUT"** 元素。

    ![http put 链接](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > 可能需要进一步向下滚动页面 (如果 Azure 门户更新发生在) ，则此图像可能看起来不完全相同，但是，你正在寻找名为 *HTTP PUT* 的元素。

14. 将显示 **"HTTP PUT"** 窗口，你需要在窗口中配置函数， (下面的图像) 。

    1.  对于 **"语言"，** 使用下拉菜单选择"C"。 \#

    2.  对于 **"名称** "，请输入适当的名称。

    3.  在"**身份验证级别"** 下拉菜单中，选择"函数 **"。**

    4.  对于 **"表** 名称"部分，需要使用之前用于创建表服务的确切名称， (相同的字母大小写) 。

    5.  在 **"存储连接**"部分中，使用下拉菜单，然后从中选择存储帐户。 如果不存在，请单击"新建"超链接以及部分标题，以显示另一个应列出存储帐户的面板。

        ![新存储](images/AzureLabs-Lab8-40.png)

15. 单击 **"** 创建"，你将收到设置已成功更新的通知。

    ![create 函数](images/AzureLabs-Lab8-41.png)

16. 单击 **"创建**"后，将重定向到函数编辑器。

    ![更新函数代码](images/AzureLabs-Lab8-42.png)

17. 将以下代码插入函数编辑器 (替换函数编辑器中的) ：

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > 使用包含的库，函数接收在 Unity 场景中移动的对象的名称和位置 (作为 C# 对象（称为 **UnityGameObject**) ）。 然后，此对象用于更新所创建表中的对象参数。 之后， 函数将调用已创建的通知中心服务，该服务会通知所有已订阅的应用程序。

18. 代码就位后，单击"保存 **"。**

19. 接下来，单击 **\<** (右侧) 箭头图标。

    ![打开上传面板](images/AzureLabs-Lab8-43.png)

20. 面板会从右侧滑入。 在面板中，单击 **"Upload"，** 将显示"文件浏览器"。

21. 导航到之前在project.js中创建的 on 文件，记事本，然后单击"打开 **"** 按钮。 此文件定义函数将使用的库。

    ![上传 json](images/AzureLabs-Lab8-44.png)

22. 上传文件后，它将显示在右侧面板中。 单击它将在函数编辑器 **中打开** 它。 它的外观 **必须与步骤** 23 下 (图像完全相同) 。

23. 然后，在左侧面板的" **函数"** 下，单击" **集成"** 链接。

    ![集成函数](images/AzureLabs-Lab8-45.png)

24. 在下一页上的右上角，单击"高级编辑器" (，如下所示) 。 

    ![打开高级编辑器](images/AzureLabs-Lab8-46.png)

25. 将在 **function.js** 面板中打开一个 on 文件，需要将该文件替换为以下代码片段。 这将定义要生成的函数以及传递到函数中的参数。

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. 编辑器现在应如下图所示：

    ![返回到标准编辑器](images/AzureLabs-Lab8-47.png)

27. 你可能会注意到，刚插入的输入参数可能与表和存储详细信息不匹配，因此需要使用你的信息进行更新。 **请不要在此处这样做，** 因为下一步将介绍它。 只需单击 **页面** 右上角的"标准编辑器&quot;链接即可返回。

28. 返回到&quot;标准 **&quot;编辑器，** 单击&quot;**输入&quot;存储 (") "中的"Azure 表****"。** 
    
    ![表输入](images/AzureLabs-Lab8-47-5.png)

29. 请确保以下信息匹配 **，** 因为它们可能不同 (以下步骤中的图像) ：

    1.  **表** 名称：在表服务中创建的Azure 存储的名称。

    2.  **存储连接：** 单击 **"新建**"，它将与下拉菜单一起显示，并且窗口右侧将显示一个面板。

        ![新存储](images/AzureLabs-Lab8-48.png)

        1.  选择存储 **帐户**"，该帐户之前已创建用于托管 **函数应用。**

        2. 你会注意到，存储 **帐户** 连接值已创建。

        3. 完成后，请务必按 **"** 保存"。

    3.  " **输入** "页现在应与以下内容匹配，其中 **显示了** 你的信息。

        ![输入完成](images/AzureLabs-Lab8-49.png)

30. 接下来，单击 **"Azure 通知中心 (通知)** - 在 **"输出"下**。 确保以下信息与信息 **匹配** ，因为它们可能有所不同 (如下步骤所示) ：

    1.  **通知中心** 名称：这是之前 **创建的通知** 中心服务实例的名称。

    2.  **通知中心命名空间连接**：单击 **新的**，它显示在下拉菜单旁边。

        ![检查输出](images/AzureLabs-Lab8-50.png)

    3. "**连接**"弹出窗口 (下图) ，需要选择之前设置的通知中心的命名空间。  

    4. 从中间 **下拉菜单中选择** 通知中心名称。

    5.  将" **策略"** 下拉菜单设置为 **DefaultFullSharedAccessSignature**。

    6. 单击" **选择"** 按钮返回。

        ![输出更新](images/AzureLabs-Lab8-51.png)

31.  " **输出** "页现在应与以下内容匹配，但 **应改为与信息** 匹配。 确保按"保存 **"。**

> [!WARNING]
> *请勿直接编辑通知* 中心名称 (只要正确按照前面的步骤操作，高级编辑器所有操作都应当完成。

![输出完成](images/AzureLabs-Lab8-50.png)

32. 此时，应测试函数，以确保它正常工作。 若要实现此目的，请执行以下操作： 

    1. 再次导航到函数页：

        ![输出完成](images/AzureLabs-Lab8-50-1.png)

    2. 返回到函数页，单击页面最右侧"测试"选项卡，打开"测试 *"边栏* 选项卡：

        ![输出完成](images/AzureLabs-Lab8-50-2.png)

    3. 在边 **栏选项卡的** "请求正文"文本框中，粘贴以下代码：

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. 测试代码就位后，单击右下角的"运行"按钮，然后运行测试。 测试的输出日志将显示在控制台区域的函数代码下方。

        ![输出完成](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > 如果上述测试失败，则需要仔细检查是否完全遵循了上述步骤，尤其是集成面板 **中的设置**。 

## <a name="chapter-7---set-up-desktop-unity-project"></a>第 7 章 - 设置桌面 Unity Project

> [!IMPORTANT]
> 现在创建的桌面应用程序在 Unity 编辑器中将不起作用。 需要在编辑器外部运行，在生成应用程序后，使用 Visual Studio (或已部署的应用程序) 。 

下面是使用 Unity 和混合现实进行开发的典型设置，因此，是其他项目的良好模板。

设置并测试混合现实沉浸式头戴显示设备。

> [!NOTE] 
> 本课程 **不需要** 运动控制器。 如果需要支持设置沉浸式头戴显示设备，请按照此[链接了解如何设置 Windows Mixed Reality。](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

1.  打开 **Unity，** 然后单击"新建 **"。**

    ![新的 unity 项目](images/AzureLabs-Lab8-52.png)

2.  需要提供 Unity 名称Project **UnityDesktopNotifHub**。 确保项目类型设置为 **3D**。 将" **位置** "设置为适合你记住 (，越靠近根目录越好) 。 然后单击"创建 **项目"。**

    ![创建项目](images/AzureLabs-Lab8-53.png)

3.  打开 Unity 后，值得检查 **默认脚本编辑器** 是否设置为 **Visual Studio。** 转到"**编辑**  >  **首选项"，** 然后从新窗口导航到"**外部工具"。** 将 **"外部脚本编辑器"****更改为 Visual Studio 2017。** 关闭 **"首选项"** 窗口。

    ![设置外部 VS 工具](images/AzureLabs-Lab8-54.png)

4.  接下来，转到"**文件** 生成设置并选择"通用平台  >  **Windows"，** 然后单击"切换平台"按钮以应用所选内容。

    ![切换平台](images/AzureLabs-Lab8-55.png)

5.  仍在文件 **生成**  >  **设置，** 请确保：

    1.  **目标设备** 设置为" **任何设备"**

        > 此应用程序适用于桌面，因此必须是 **"任何设备"**

    2.  **生成类型** 设置为 **D3D**

    3.  **SDK** 设置为"最新 **安装"**

    4.  **Visual Studio版本** 设置为"最新 **安装"**

    5.  **"生成和运行** "设置为" **本地计算机"**

    6.  虽然在这里，但值得保存场景，并添加到生成中。

        1. 为此，选择"**添加打开的场景"。** 将显示保存窗口。

            ![添加打开的场景](images/AzureLabs-Lab8-56.png)

        2. 为此和任何将来的场景创建新文件夹，然后选择"新建文件夹"按钮，以创建新文件夹，将其命名为 **"场景"。**

            ![新场景文件夹](images/AzureLabs-Lab8-57.png)

        3. 打开新创建的 **"场景**"文件夹，然后在"文件名 **：** 文本"字段中，键入 **"NH \_ 桌面 \_ 场景**"，然后按"保存 **"。**

            ![新NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  目前，"**生成设置中的** 其余设置应保留为默认值。

6.  在同一窗口中单击"**播放器** 设置按钮，这将在检查器所在的空间中 **打开相关面板**。

7.  在此面板中，需要验证一些设置：

    1.  在"**其他设置** 选项卡中：

        1.  **脚本运行时版本** 应为实验 **性版本 A0.NET 4.6 等效)**

        2. **脚本后端应为** **.NET**

        3. **API 兼容性级别** 应为 **.NET 4.6**

            ![4.6 net 版本](images/AzureLabs-Lab8-59.png)

    2.  在"**发布设置** 选项卡中的"**功能"下**，选中：

        - **InternetClient**

            ![时钟周期 Internet 客户端](images/AzureLabs-Lab8-60.png)

8.  返回到"**生成设置** *Unity C \#* 项目不再灰度;勾选此旁边的复选框。

9.  关闭“生成设置”窗口  。

10. 保存场景和Project  >  **保存场景/**  >  **文件保存Project。**

    > [!IMPORTANT]
    > 如果要跳过此项目的 *Unity* 设置组件 (桌面应用) ，并直接继续编写代码，请随意下载此 [.unitypackage，](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)将其作为自定义包导入到项目中，然后继续学习第 [](https://docs.unity3d.com/Manual/AssetPackages.html) [9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)章 。  你仍然需要添加脚本组件。

## <a name="chapter-8---importing-the-dlls-in-unity"></a>第 8 章 - 在 Unity 中导入 DLL

你将使用适用于 Unity Azure 存储， (它本身利用适用于 Azure 的 .Net SDK) 。 有关详细信息，请参阅此[链接，了解适用于 Unity Azure 存储。](/sandbox/gamedev/unity/azure-storage-unity)

Unity 中当前存在一个已知问题，要求在导入后重新配置插件。 本部分 (4 - 7) 解决 bug 后不再需要这些步骤。

若要将 SDK 导入到自己的项目中，请确保已从 GitHub 下载了最新的 [**.unitypackage。**](https://aka.ms/azstorage-unitysdk) 然后执行以下操作：

1.  使用"资产导入包自定义包"菜单选项将 **.unitypackage****添加到 \> \>** Unity。

2.  在弹出 **的"导入 Unity** 包"框中，可以选择"插件"#A0"存储" \> 下的所有内容。  取消选中其他所有内容，因为本课程不需要它。

    ![导入到包](images/AzureLabs-Lab8-61.png)

3.  单击" ***导入*** "按钮，将项添加到项目。

4.  转到 **存储视图中**"插件"下的"Project"文件夹，仅选择以下 *插件*： 

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![取消选中"任何平台"](images/AzureLabs-Lab8-62.png)

5.  选中 *这些特定插件后，* 取消选中"**任何平台**"并 **取消选中****"WSAPlayer"，然后单击**"应用 **"。**

    ![应用平台 dll](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > 我们将这些特定插件标记为仅在 Unity 编辑器中使用。 这是因为从 Unity 导出项目后，WSA 文件夹中会使用不同版本的相同插件。

6.  在 **"存储** 插件"文件夹中，仅选择：

    -   Microsoft.Data.Services.Client

        ![set 不处理 dll](images/AzureLabs-Lab8-64.png)

7.  选中"**平台管理"下的"不** 处理 **"设置然后单击"** 应用 **_"。_**

    ![不应用任何处理](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > 我们将此插件标记为"不处理"，因为 Unity 程序集修补程序难以处理此插件。 即使未处理插件，该插件仍将正常工作。

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>第 9 章 - 在桌面 Unity 项目中创建 TableToScene 类

现在需要创建包含代码的脚本来运行此应用程序。

需要创建的第一个脚本是 **TableToScene，** 负责：

-   读取 Azure 表中的实体。
-   使用表数据确定要生成的对象以及位置。

需要创建的第二个脚本是 **CloudScene，** 负责：

-   注册左键单击事件，允许用户在场景周围拖动对象。
-   序列化此 Unity 场景中的对象数据，并发送到 Azure 函数应用。

若要创建此类，请：

1.  右键单击 **位于"创建** 文件夹"面板Project **中的"资产**  >  **文件夹"。** 将 **文件夹命名脚本**。

    ![创建脚本文件夹](images/AzureLabs-Lab8-66.png)

    ![创建脚本文件夹 2](images/AzureLabs-Lab8-67.png)

2.  双击刚刚创建的文件夹，打开它。

3.  在"脚本"文件夹中 **右键** 单击，然后单击"**创建**  >  **C# 脚本"。** 将脚本命名 **TableToScene**。

    ![new c# script ](images/AzureLabs-Lab8-68.png)
     ![ TableToScene rename](images/AzureLabs-Lab8-69.png)

4.  双击该脚本，在 2017 Visual Studio中打开它。

5.  添加以下命名空间：

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  在 类中，插入以下变量：

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > 将 **accountName** 值替换为 Azure 存储 服务名称和 **accountKey** 值，替换为在 Azure 门户中的 Azure 存储 服务中发现的密钥值 (请参阅下图) 。 
    >
    > ![提取帐户密钥](images/AzureLabs-Lab8-70.png)

7.  现在，添加 **Start ()****和"唤醒 ()** 方法以初始化 类。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  在 **TableToScene** 类中，添加 方法，该方法将检索 Azure 表中的值，并使用它们在场景中生成相应的基元。

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  在 **TableToScene** 类之外，需要定义应用程序用于序列化和反序列化表 **实体 的类**。

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. 在返回到 **Unity 编辑器** 之前，请确保保存。

11. 单击"**层次结构"****面板中的**"主相机"，以便其属性显示在检查 **器 中**。

12. 打开 **"脚本** "文件夹后，选择脚本 **TableToScene 文件** ，并将其拖动到 **主相机 上**。 结果应如下所示：

    ![将脚本添加到主相机](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>第 10 章 - 在桌面 Unity 中创建 CloudScene Project

需要创建的第二个脚本是 **CloudScene，** 负责：

-   注册左键单击事件，允许用户在场景周围拖动对象。

-   序列化此 Unity 场景中的对象数据，并发送到 Azure 函数应用。

创建第二个脚本：

1.  在"脚本"文件夹中 **右键** 单击，单击"**创建"，****然后单击"C \# 脚本"。** 将脚本 **命名 CloudScene**
    
    ![new c# script ](images/AzureLabs-Lab8-72.png)
     ![ rename CloudScene](images/AzureLabs-Lab8-73.png)

2.  添加以下命名空间：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  插入以下变量：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  将 **azureFunctionEndpoint** 值替换为 Azure 门户中 Azure Function App Service 中的 Azure Function App URL，如下图所示：

    ![获取函数 URL](images/AzureLabs-Lab8-74.png)

5.  现在，添加 **Start ()****和"唤醒 ()** 方法以初始化 类。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  在 **Update ()** 方法中，添加以下代码，用于检测鼠标输入和拖动，从而在场景中移动 GameObject。 如果用户拖放了对象，它将将对象的名称和坐标传递给 **UpdateCloudScene () 方法**，该方法将调用 Azure Function App 服务，该服务将更新 Azure 表并触发通知。

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  现在添加 **UpdateCloudScene ()** 方法，如下所示：

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  保存代码并返回到 Unity

9.  将 **CloudScene 脚本** 拖到 **主相机 上**。 

    1. 单击"**层次结构"****面板中的**"主相机"，以便其属性显示在检查 **器 中**。 

    2. 打开 **"脚本** "文件夹后，选择 **CloudScene** 脚本，并将其拖动到 **主相机 上**。 结果应如下所示：

        > ![将云脚本拖动到主相机上](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>第 11 章 - 将桌面Project UWP

此项目的 Unity 部分所需的一切现已完成。

1.  导航到"**生成设置 (**  >  **文件生成设置) 。**

2.  在"生成 **设置** 窗口中，单击"生成 **"。**

    ![生成项目](images/AzureLabs-Lab8-76.png)

3.  系统 **文件资源管理器** 窗口，提示你输入"生成"位置。 单击左上角的 ("新建文件夹"，创建一个新的文件夹) 将其命名为 **"生成"。**

    ![用于生成的新文件夹](images/AzureLabs-Lab8-77.png)

    1.  打开新的 **"生成"** 文件夹，再使用" (**文件夹"** 创建另一个文件夹) "NH **\_ 桌面 \_ 应用"。**

        ![文件夹名称NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  选中 **NH \_ 桌面 \_ 应用** 后。 单击"**选择文件夹"。** 生成项目需要一分钟左右时间。

4.  生成后 **，文件资源管理器** 显示新项目的位置。 不过，无需打开它，因为需要先创建另一个 Unity 项目，接下来的几个章节将介绍。


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>第 12 章 - 设置混合现实 Unity Project

以下是使用混合现实进行开发的典型设置，因此，是其他项目的良好模板。

1.  打开 **Unity，** 然后单击"新建 **"。**

    ![新的 unity 项目](images/AzureLabs-Lab8-79.png)

2.  现在，需要提供 Unity Project，插入 **UnityMRNotifHub**。 确保项目类型设置为 **3D**。 将" **位置** "设置为适合你记住 (，越靠近根目录越好) 。 然后单击"创建 **项目"。**

    ![名称 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  打开 Unity 后，值得检查 **默认脚本编辑器** 是否设置为 **Visual Studio。** 转到"**编辑**  >  **首选项"，** 然后从新窗口导航到"**外部工具"。** 将 **"外部脚本编辑器"****更改为 Visual Studio 2017。** 关闭 **"首选项"** 窗口。

    ![将外部编辑器设置为 VS](images/AzureLabs-Lab8-81.png)

4.  接下来，单击"切换设置"按钮，转到"文件生成"Windows"平台"，将平台切换到"通用  >  **平台**"。 

    ![将平台切换到 UWP](images/AzureLabs-Lab8-82.png)

5.  转到 **"**  >  **文件生成设置** 并确保：

    1.  **目标设备** 设置为" **任何设备"**

        > 对于Microsoft HoloLens，将"**目标设备"** 设置为 *HoloLens。*

    2.  **生成类型** 设置为 **D3D**

    3.  **SDK** 设置为"最新 **安装"**

    4.  **Visual Studio版本** 设置为"最新 **安装"**

    5.  **"生成和运行** "设置为" **本地计算机"**

    6.  虽然在这里，但值得保存场景，并添加到生成中。

        1. 为此，选择"**添加打开的场景"。** 将显示保存窗口。

            ![添加打开的场景](images/AzureLabs-Lab8-83.png)

        2. 为此和任何将来的场景创建新文件夹，然后选择"新建文件夹"按钮，以创建新文件夹，将其命名为 **"场景"。**

            ![新场景文件夹](images/AzureLabs-Lab8-84.png)

        3. 打开新创建的 **"场景**"文件夹，然后在"文件名 **：** 文本"字段中键入 **NH \_ MR \_ 场景**，然后按"保存 **"。**

            ![新场景 - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  目前，"**生成设置中的** 其余设置应保留为默认值。

6.  在同一窗口中单击"**播放器** 设置按钮，这将在检查器所在的空间中 **打开相关面板**。    

    ![打开播放器设置](images/AzureLabs-Lab8-86.png)

7.  在此面板中，需要验证一些设置：

    1.  在"**其他设置** 选项卡中：

        1.  **脚本运行时版本****应为实验性**（A0.NET 4.6 等效) 
        2.  **脚本后端应为** **_.NET_**
        3.  **API 兼容性级别** 应为 **.NET 4.6**

            ![api 兼容性](images/AzureLabs-Lab8-87.png)

    2.  在面板的下方，在"发布 设置) "下面的 **"XR** 设置 ("中，勾选"支持虚拟现实"，确保Windows Mixed Reality  **SDK**

        ![更新 xr 设置](images/AzureLabs-Lab8-88.png)        

    3.  在"**发布设置** 选项卡中的 **"功能"下**，包含：

        - **InternetClient**           

            ![时钟周期 Internet 客户端](images/AzureLabs-Lab8-89.png)

8.  返回到"**生成设置"** 中 **，Unity C#** 项目不再灰度：勾选此旁边的复选框。

9.  完成这些更改后，关闭"生成设置窗口。

10. 保存场景和Project  >  **保存场景/**  >  **文件保存Project。**

    > [!IMPORTANT]
    > 如果要跳过此项目的 *Unity* 设置组件 (混合现实应用) ，并继续直接进入代码，请随意下载此 [.unitypackage，](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)将其作为自定义包导入到项目中，然后继续学习第 [](https://docs.unity3d.com/Manual/AssetPackages.html)[14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)。 你仍然需要添加脚本组件。

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>第 13 章 - 导入混合现实 Unity Project

你将使用适用于 Unity Azure 存储的 (，该库使用适用于 Azure 的 .Net SDK) 。 请按照此[链接了解如何在 Unity Azure 存储应用](/sandbox/gamedev/unity/azure-storage-unity)。
Unity 中当前存在一个已知问题，要求在导入后重新配置插件。 本部分 (4 - 7) 解决 bug 后不再需要这些步骤。

若要将 SDK 导入到自己的项目中，请确保已下载最新的 [.unitypackage](https://aka.ms/azstorage-unitysdk)。 然后执行以下操作：

1.  使用"资产导入包自定义包"菜单选项，将从上述下载的 .unitypackage  >    >  添加到 Unity。

2.  在弹出 **的"导入 Unity** 包"框中，可以选择"插件"下的所有  >  存储。

    ![导入包](images/AzureLabs-Lab8-90.png)

3.  单击" **导入** "按钮，将项添加到项目。

4.  转到 **存储视图中**"插件"下的"Project"文件夹，仅选择以下 *插件*： 

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![选择插件](images/AzureLabs-Lab8-91.png)

5.  选中 *这些特定插件后，* 取消选中"**任何平台**"并 **取消选中****"WSAPlayer"，然后单击**"应用 **"。**

    ![应用平台更改](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > 将这些特定插件标记为仅在 Unity 编辑器中使用。 这是因为从 Unity 导出项目后，WSA 文件夹中会使用不同版本的相同插件。

6.  在 **"存储** 插件"文件夹中，仅选择：

    -   Microsoft.Data.Services.Client

        ![选择数据服务客户端](images/AzureLabs-Lab8-93.png)

7.  选中"**平台管理"下的"不** 处理 **"设置然后单击"** 应用 **"。**

    ![不处理](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > 你正在标记此插件"不处理"，因为 Unity 程序集修补器难以处理此插件。 即使未处理插件，该插件仍将正常工作。

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>第 14 章 - 在混合现实 Unity 项目中创建 TableToScene 类

**TableToScene** 类与第 9 章 [中介绍的类相同](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。 按照第 9 章中介绍的相同Project Unity，在混合现实 Unity 中[创建相同的类](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。

完成本章后，两个 **Unity 项目** 都将在主相机上设置此类。

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>第 15 章 - 在混合现实 Unity 中创建 NotificationReceiver Project

需要创建的第二个脚本是 **NotificationReceiver**，负责：

-   初始化时将应用注册到通知中心。
-   侦听来自通知中心的通知。
-   从接收的通知中反初始化对象数据。
-   基于反化数据移动场景中的 GameObject。

若要创建 **NotificationReceiver 脚本** ，请执行以下命令：

1.  在"脚本"文件夹中 **右键** 单击，单击"**创建"，****然后单击"C \# 脚本"。** 将脚本命名 **NotificationReceiver**。

    ![创建新的 c# 脚本 ](images/AzureLabs-Lab8-95.png)
     ![ 名称，名称为 NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  双击该脚本以打开它。

3.  添加以下命名空间：

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  插入以下变量：

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  将 **hubName** 值替换为通知中心服务名称，将 **hubListenEndpoint** 值替换为 Azure 门户中的"访问策略"选项卡中的终结点值 (请参阅下图) 。

    ![插入通知中心策略终结点](images/AzureLabs-Lab8-97.png)

6.  现在，添加 **Start ()****和"唤醒 ()** 方法以初始化 类。

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  添加 **WaitForNotification** 方法，使应用能够接收来自通知中心库的通知，而不会与主线程冲突：

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  以下方法 **InitNotificationAsync ()**，将在初始化时向通知中心服务注册应用程序。 代码被注释掉，因为 Unity 无法生成项目。 在门户中导入 Azure Messaging Nuget 包时，将删除Visual Studio。

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  每次收到通知时， () 将触发以下处理程序，即 Channel **\_ PushNotificationReceived**。 它将反初始化通知（即已在桌面应用程序上移动的 Azure 表实体），然后将 MR 场景中的相应 GameObject 移动到同一位置。 
    
    > [!IMPORTANT]
    > 代码被注释掉，因为代码引用了 Azure 消息库，你将在使用 Nuget 程序包管理器生成 Unity 项目后添加该库，Visual Studio。 因此，除非注释掉 Unity 项目，否则它将无法生成。请注意，如果生成项目，然后希望返回到 Unity，则需要重新 **注释** 该代码。

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. 在返回到 Unity 编辑器之前，请记得保存更改。

11. 单击"**层次结构"****面板中的**"主相机"，以便其属性显示在检查 **器 中**。

12. 打开 **"脚本** "文件夹后，选择 **"NotificationReceiver"** 脚本，并将其拖动到 **主相机 上**。 结果应如下所示：

    ![将通知接收器脚本拖动到相机](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > 如果要针对相机进行Microsoft HoloLens，则需要更新主相机的 *相机* 组件，以便： 
    > - 清除标志：纯色
    > - 背景色：黑色

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>第 16 章 - 将混合现实Project UWP

本章与上一项目的生成过程相同。 此项目的 Unity 部分所需的一切现已完成，因此现在可以从 Unity 生成它。

1.  导航到"**生成设置 (**  >  **文件生成设置) 。**

2.  在"**生成设置** 菜单中，确保 **"Unity C#** 项目"*已勾选 (这将允许你在生成后编辑此项目中的) 。

3.  完成此操作后，单击"生成 **"。**

    ![生成项目](images/AzureLabs-Lab8-99.png)

4.  系统 **文件资源管理器** 窗口，提示你输入"生成"位置。 单击左上角的 ("新建文件夹"，创建一个新的文件夹) 将其命名为 **"生成"。**

    ![创建生成文件夹](images/AzureLabs-Lab8-100.png)

    1.  打开新的 **"生成"** 文件夹，使用"新建文件夹 (**创建** 另一个文件夹，) "NH **MR \_ \_ 应用"。**

        ![创建NH_MR_Apps文件夹](images/AzureLabs-Lab8-101.png)

    2.  选中 **NH \_ MR \_ 应用** 后。 单击"**选择文件夹"。** 生成项目需要一分钟左右时间。

5.  生成后 **，文件资源管理器将在** 新项目的位置打开一个窗口。



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>第 17 章 - 将NuGet包添加到 UnityMRNotifHub 解决方案

> [!WARNING] 
> 请记住，添加以下 NuGet 包 (并取消注释下一章[) ](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)中的代码后，在 Unity Project 中重新打开时，Code 将出现错误。 如果要返回并继续在 Unity 编辑器中编辑，则需要注释该错误代码，然后在稍后返回到"错误代码"后再次取消注释Visual Studio。 

完成混合现实生成后，导航到你构建的混合现实项目，然后双击该文件夹中的解决方案 (.sln) 文件，以使用 Visual Studio 2017 打开解决方案。
现在需要添加 **WindowsAzure.Messaging.managed** NuGet包;这是一个库，用于从通知中心接收通知。

导入NuGet包：

1.  在 **"解决方案资源管理器"** 中，右键单击"解决方案"

2.  单击"**管理NuGet包"。**

    ![打开 nuget 管理器](images/AzureLabs-Lab8-102.png)

3.  选择 **"浏览**"选项卡，然后搜索"WindowsAzure.Messaging.managed"。

    ![查找 Windows azure 消息传送包](images/AzureLabs-Lab8-103.png)

4.  选择结果 (如下所示) ，在右侧窗口中，选中""旁边的复选框 **Project。** 这会在"程序集"旁边的复选框中Project一个刻度，以及 **"Assembly-CSharp"** 和 **"UnityMRNotifHub"项目旁边的** 复选框。

    ![勾选所有项目](images/AzureLabs-Lab8-104.png)

5.  最初提供的版本 **可能与** 此项目不兼容。 因此，单击"版本"旁边的下拉菜单，然后单击"版本 **0.1.7.9"，** 然后单击"安装 **"。**

6.  现已完成安装 NuGet 包。 找到在 **NotificationReceiver** 类中输入的注释代码并删除注释。



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>第 18 章 - 编辑 UnityMRNotifHub 应用程序、NotificationReceiver 类

在添加了 **NuGet** 包后，需要取消注释 **NotificationReceiver** 类中的一些代码。 

这包括：

1. 顶部的命名空间：

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. **InitNotificationsAsync 方法 ()** 代码：

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> 上面的代码包含注释：确保未意外取消注释该注释 (因为如果有注释，代码不会) 。

3. 最后，最后 **，Channel_PushNotificationReceived事件** ：

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

取消注释这些注释后，请确保保存，然后继续下一章。

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>第 19 章 - 将混合现实项目关联到应用商店应用

现在，需要将 **混合现实** 项目关联到在实验室开始时在 中创建的应用商店应用。

1.  打开解决方案。

2.  右键单击"UWP 应用"Project面板解决方案资源管理器，转到"应用商店 **"，并将** 应用与应用商店 **关联...。**

    ![开店关联](images/AzureLabs-Lab8-105.png)

3.  将出现一个新窗口，名为 **"将应用与 Windows Store 关联"。** 单击“下一步” 。

    ![转到下一屏幕](images/AzureLabs-Lab8-106.png)

4.  它将加载与已登录帐户关联的所有应用程序。 如果未登录到帐户，可以在此 **页上** 登录。

5.  找到 **在本教程开始时** 创建的"应用商店应用名称"，然后选择它。 然后单击“下一步”。

    ![查找并选择你的商店名称](images/AzureLabs-Lab8-107.png)

6.  单击"**关联"。**

    ![关联应用](images/AzureLabs-Lab8-108.png)

7.  应用现已 **与应用商店** 应用关联。 这是启用通知所必需的。

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>第 20 章 - 部署 UnityMRNotifHub 和 UnityDesktopNotifHub 应用程序

本章对于两个人可能更容易，因为结果将包括两个正在运行的应用，一个在计算机桌面上运行，另一个在沉浸式头戴显示设备中运行。

沉浸式头戴显示设备应用正在等待接收对场景的更改 (本地 GameObjects) 的位置更改，桌面应用将更改其本地场景 (位置更改) ，这些更改将共享给 MR 应用。 首先部署 MR 应用，然后部署桌面应用，以便接收方可以开始侦听。

若要在本地 **计算机上部署 UnityMRNotifHub** 应用，请运行以下代码：

1.  在 **2017** 年 1 月中打开 **UnityMRNotifHub** Visual Studio文件。

2.  在"**解决方案平台"中**，选择 **"x86，本地计算机"。**

3.  在"**解决方案配置"中，** 选择"**调试"。**

    ![设置项目配置](images/AzureLabs-Lab8-109.png)

4.  转到" **生成"菜单** 并单击" **部署解决方案** "，将应用程序旁加载到计算机。

5.  应用现在应显示在已安装的应用列表中，并准备好启动。

在本地计算机上 **部署 UnityDesktopNotifHub** 应用：

1.  在 **2017** 年 1 月中打开 **UnityDesktopNotifHub** 应用Visual Studio文件。

2.  在"**解决方案平台"中**，选择 **"x86，本地计算机"。**

3.  在"**解决方案配置"中，** 选择"**调试"。**

    ![设置项目配置](images/AzureLabs-Lab8-110.png)

4.  转到" **生成"菜单** 并单击" **部署解决方案** "，将应用程序旁加载到计算机。

5.  应用现在应显示在已安装的应用列表中，并准备好启动。

6.  启动混合现实应用程序，然后启动桌面应用程序。

在两个应用程序都运行后，使用鼠标左键 (移动桌面场景中) 。 这些位置更改将在本地进行、序列化并发送到函数应用服务。 然后，Function App 服务将更新表以及通知中心。 收到更新后，通知中心将直接将更新后的数据发送到所有已注册的应用程序 (（本例中为沉浸式头戴显示设备应用) ）后，该应用将反流式处理传入数据，并将新的位置数据应用到本地对象，并将其移动到场景中。


## <a name="your-finished-your-azure-notification-hubs-application"></a>已完成的 Azure 通知中心应用程序
 
祝贺你，你构建了一个混合现实应用，该应用利用 Azure 通知中心服务并允许应用之间的通信。
 
![final product -end](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>额外练习

### <a name="exercise-1"></a>练习 1

你能否了解如何更改 GameObject 的颜色并将该通知发送到查看场景的其他应用？

### <a name="exercise-2"></a>练习 2

能否将 GameObject 的移动添加到 MR 应用，并查看桌面应用中的更新场景？