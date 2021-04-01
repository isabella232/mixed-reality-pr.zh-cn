---
title: 集成 Azure 存储
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现 Azure 表存储和 Azure Blob 存储。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, hololens 2, azure 存储, azure 云服务, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 189fea44da6d2da7cd98629a4a67c2f7c9340d2b
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550327"
---
# <a name="2-integrating-azure-storage"></a><span data-ttu-id="1c0b2-104">2.集成 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="1c0b2-104">2. Integrating Azure storage</span></span>

<span data-ttu-id="1c0b2-105">本教程将介绍如何将实体数据保存到 Azure 表存储并将缩略图图像保存到 Azure Blob 存储。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-105">In this tutorial, you will learn how to save entity data to Azure Table storage and thumbnail images to Azure Blob storage.</span></span> <span data-ttu-id="1c0b2-106">通过此功能，可以将跨会话和设备的带数据（例如 ID、名称、缩略图等）的跟踪对象存储到云并进行检索。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-106">This feature will allow us to store and retrieve *Tracked Objects* with data like ID, Name, Thumbnail Image, etc. across sessions and devices to the cloud.</span></span>

## <a name="objectives"></a><span data-ttu-id="1c0b2-107">目标</span><span class="sxs-lookup"><span data-stu-id="1c0b2-107">Objectives</span></span>

* <span data-ttu-id="1c0b2-108">了解有关 Azure 存储的基础知识</span><span class="sxs-lookup"><span data-stu-id="1c0b2-108">Learn the basics about Azure storage</span></span>
* <span data-ttu-id="1c0b2-109">了解如何存储、修改和检索表存储中的数据</span><span class="sxs-lookup"><span data-stu-id="1c0b2-109">Learn how to store, modify and retrieve data from Table storage</span></span>
* <span data-ttu-id="1c0b2-110">了解如何在 Blob 存储中存储和删除图像</span><span class="sxs-lookup"><span data-stu-id="1c0b2-110">Learn how to store and delete images from Blob storage</span></span>

## <a name="understanding-azure-storage"></a><span data-ttu-id="1c0b2-111">了解 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="1c0b2-111">Understanding Azure storage</span></span>

<span data-ttu-id="1c0b2-112">Azure 存储是云中的 Microsoft 存储解决方案，可适应多种场景和需求。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-112">**Azure storage** is a Microsoft storage solution on the cloud that can cover many scenarios and requirements.</span></span> <span data-ttu-id="1c0b2-113">它可以大规模扩展，并且开发人员也很容易使用它。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-113">It can scale massively and is easily approachable by developers.</span></span> <span data-ttu-id="1c0b2-114">所有服务可以在一个 Azure 存储帐户下使用。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-114">All services can be consumed under the umbrella of an **Azure storage Account**.</span></span> <span data-ttu-id="1c0b2-115">对于我们的用例，我们将使用表存储和 Blob 存储 。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-115">For our use case we will use *Table storage* and *Blob storage*.</span></span>

<span data-ttu-id="1c0b2-116">了解有关 [Azure 存储服务](/azure/storage/blobs/storage-blobs-overview)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-116">Learn more about [Azure storage services](/azure/storage/blobs/storage-blobs-overview).</span></span>

### <a name="azure-table-storage"></a><span data-ttu-id="1c0b2-117">Azure 表存储</span><span class="sxs-lookup"><span data-stu-id="1c0b2-117">Azure Table storage</span></span>

<span data-ttu-id="1c0b2-118">借助此服务，我们能够以 NoSQL 方式存储数据，在此项目中，我们将使用它来存储跟踪对象的相关信息，例如名称、说明、空间定位点 ID 等。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-118">This services allows us to store data in a NoSQL fashion, in this project we will use it to store information about the *Tracked Object* such as: name, description, spatial anchor id, and more.</span></span>

<span data-ttu-id="1c0b2-119">在演示应用程序的上下文中，你需要两个表，一个用于存储有关项目的信息以及有关经训练模型状态的信息（详见[集成 Azure 自定义视觉](mr-learning-azure-03.md)教程），另一个用于存储有关跟踪对象的信息。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-119">In context of the demo application, you need two Tables, one to store information about the project with information about the state of trained models more about that in the ([Integrating Azure Custom Vision](mr-learning-azure-03.md)) tutorial and a second table to store information about *Tracked Objects*.</span></span>

<span data-ttu-id="1c0b2-120">了解有关 [Azure 表存储](/azure/storage/tables/table-storage-overview)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-120">Learn more about [Azure Table storage](/azure/storage/tables/table-storage-overview).</span></span>

### <a name="azure-blob-storage"></a><span data-ttu-id="1c0b2-121">Azure Blob 存储</span><span class="sxs-lookup"><span data-stu-id="1c0b2-121">Azure Blob storage</span></span>

<span data-ttu-id="1c0b2-122">此服务允许存储大型二进制文件，你将使用它，将为跟踪对象拍摄的照片存储为缩略图。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-122">This service allows to store large binary files, you will use this to store photos taken for *Tracked Objects* as thumbnail.</span></span>
<span data-ttu-id="1c0b2-123">对于演示应用程序，需要一个 Blob 容器来存储图像。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-123">For of the demo application you need one Blob Container to store the images.</span></span>

<span data-ttu-id="1c0b2-124">了解有关 [Azure Blob 存储](/azure/storage/blobs/storage-blobs-introduction)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-124">Learn more about [Azure Blob storage](/azure/storage/blobs/storage-blobs-introduction).</span></span>

## <a name="preparing-azure-storage"></a><span data-ttu-id="1c0b2-125">准备 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="1c0b2-125">Preparing Azure Storage</span></span>

<span data-ttu-id="1c0b2-126">要使用 Azure 存储服务，需要一个 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-126">To consume the Azure storage services you will need an Azure storage account.</span></span> <span data-ttu-id="1c0b2-127">若要创建存储帐户，请参阅[创建存储帐户](/azure/storage/common/storage-account-create?tabs=azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-127">To create a storage account, see [Create a storage account](/azure/storage/common/storage-account-create?tabs=azure-portal).</span></span> <span data-ttu-id="1c0b2-128">若要了解有关存储帐户的详细信息，请参阅 [Azure 存储帐户概述](/azure/storage/common/storage-account-overview)。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-128">To learn more about storage accounts, see [Azure storage account overview](/azure/storage/common/storage-account-overview).</span></span>

<span data-ttu-id="1c0b2-129">拥有存储帐户后，可从 Azure 门户检索连接字符串，本课程的下一部分将会用到它。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-129">Once you have a storage account, you can retrieve the connection string from the **Azure Portal** which will be needed in the next section of this lesson.</span></span>

### <a name="optional-azure-storage-explorer"></a><span data-ttu-id="1c0b2-130">可选 Azure 存储资源管理器</span><span class="sxs-lookup"><span data-stu-id="1c0b2-130">Optional Azure Storage Explorer</span></span>

<span data-ttu-id="1c0b2-131">虽然可从应用程序内的 UI 查看并验证所有数据更改，但建议安装 [Azure 存储资源管理器](https://azure.microsoft.com/features/storage-explorer/)。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-131">While you can see and verify all data changes from the UI inside the application, we recommend to install [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="1c0b2-132">此工具可用于直观地查看 Azure 存储中的数据，在调试和学习时很有帮助。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-132">This tool allows you to visually see the data in the Azure storage and is of great help when debugging and learning.</span></span>

> [!TIP]
> <span data-ttu-id="1c0b2-133">若要在 Unity 编辑器中进行测试，可以使用本地模拟器：</span><span class="sxs-lookup"><span data-stu-id="1c0b2-133">For testing from inside the Unity editor you can use a local emulator:</span></span>
>
> * <span data-ttu-id="1c0b2-134">在 Windows 10 中，可使用 [Azure 存储模拟器](/azure/storage/common/storage-use-emulator)</span><span class="sxs-lookup"><span data-stu-id="1c0b2-134">on Windows 10 you can use [Azure Storage Emulator](/azure/storage/common/storage-use-emulator)</span></span>
> * <span data-ttu-id="1c0b2-135">在 MacOS/Linux 中，可以使用适用于 Docker 的 [Azurite Docker 映像](https://hub.docker.com/_/microsoft-azure-storage-azurite)</span><span class="sxs-lookup"><span data-stu-id="1c0b2-135">on MacOS/Linux you can use [Azurite Docker Image](https://hub.docker.com/_/microsoft-azure-storage-azurite) for Docker</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="1c0b2-136">准备场景</span><span class="sxs-lookup"><span data-stu-id="1c0b2-136">Preparing the scene</span></span>

<span data-ttu-id="1c0b2-137">在“层次结构”窗口中，找到“DataManager”对象并选择它。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-137">In the Hierarchy window, locate the **DataManager** object and select it.</span></span>

![检查器中显示了 DataManager 脚本组件配置字段的 Unity](images/mr-learning-azure/tutorial2-section4-step1-1.png)

<span data-ttu-id="1c0b2-139">在“检查器”窗口中，你将看到“DataManager(脚本)”组件是存储所有 Azure 存储相关设置的位置 。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-139">From the Inspector window you will see that the **DataManager (script)** component is where all **Azure storage** related settings are kept.</span></span> <span data-ttu-id="1c0b2-140">所有相关设置均已设置，只需将“连接字符串”字段替换为从 Azure 门户检索的连接字符串即可。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-140">All relevant settings are already set, you just need to replace the *Connection String* field with the one you can retrieve from the Azure Portal.</span></span> <span data-ttu-id="1c0b2-141">如果使用本地 Azure 存储模拟器解决方案，则可以保留已提供的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-141">If you are using a local Azure storage emulator solution, then you can keep the already provided *Connection String*.</span></span>

<span data-ttu-id="1c0b2-142">“DataManager(脚本)”负责与 UI 组件上的其他控制器脚本使用的表存储和 Blob 存储进行对话  。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-142">The **DataManager (script)** is responsible for talking to the **Table storage** and **Blob storage** which is consumed by other controller scripts on the UI components.</span></span>

## <a name="writing-and-reading-data-from-azure-table-storage"></a><span data-ttu-id="1c0b2-143">向 Azure 表存储写入和由其读取数据</span><span class="sxs-lookup"><span data-stu-id="1c0b2-143">Writing and reading data from Azure Table storage</span></span>

<span data-ttu-id="1c0b2-144">一切准备就绪后，就可以创建跟踪对象了。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-144">With everything prepared it's time to create a *Tracked Object*.</span></span>

<span data-ttu-id="1c0b2-145">在 HoloLens 上打开应用程序，单击“设置对象”，然后你会在层次结构中看到 EnterObjectName 对象变为活动状态。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-145">Open the application on your HoloLens, click on the **Set Object** and you will see how the *EnterObjectName* object will become active in the hierarchy.</span></span> <span data-ttu-id="1c0b2-146">在此菜单中，单击搜索栏，然后键入想要赋予跟踪对象的名称 。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-146">In this menu click on the *search bar* and type in the name you want to give the *Tracked Object*.</span></span> <span data-ttu-id="1c0b2-147">提供名称后，单击“设置对象”按钮。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-147">After providing a name click on the **Set object** button.</span></span> <span data-ttu-id="1c0b2-148">这将在 Azure 表存储上创建跟踪对象，然后你将看到“对象卡”。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-148">This will create the *Tracked Object* on the Azure Table storage and you will see now the **Object Card**.</span></span>

<span data-ttu-id="1c0b2-149">该对象卡是跟踪对象的 UI 表示，并将在本系列教程中多次扮演重要角色。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-149">This **Object Card** is a UI representation of the *Tracked Object* and will have an important role several times in this tutorial series.</span></span>

<span data-ttu-id="1c0b2-150">现在，单击描述文本框并键入“汽车”，然后单击“保存”按钮以保存更改。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-150">Now click on the description *text box* and type in "Car", after that click on the **Save** button to save the changes.</span></span> <span data-ttu-id="1c0b2-151">停止应用程序，然后重新运行它。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-151">Stop the application and rerun it.</span></span>

<span data-ttu-id="1c0b2-152">现在，单击“搜索对象”，然后在搜索栏中键入之前创建跟踪对象时使用的名称 。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-152">Now this time click on **Search Object** and type in the *search bar* the name you have used before when creating the *Tracked Object*.</span></span> <span data-ttu-id="1c0b2-153">你将看到从 Azure 表存储中检索出了包含所有数据的“对象卡” 。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-153">You will see that the **Object Card** with all the data is retrieved from the **Azure Table storage**.</span></span>

<span data-ttu-id="1c0b2-154">可随时关闭“对象卡”和创建新的跟踪对象并编辑其数据。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-154">Feel free to close the **Object Card** and create new *Tracked Objects* and edit their data.</span></span>

> [!TIP]
> <span data-ttu-id="1c0b2-155">如果已安装 [Azure 存储资源管理器](https://azure.microsoft.com/features/storage-explorer/)，则查看对象表，其中将显示创建的跟踪对象 。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-155">If you have installed the [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) then look into the *objects* table and you will see there the created *Tracked Object*.</span></span>

## <a name="uploading-and-download-image-from-azure-blob-storage"></a><span data-ttu-id="1c0b2-156">向 Azure Blob 存储上传和由其下载图像</span><span class="sxs-lookup"><span data-stu-id="1c0b2-156">Uploading and Download image from Azure Blob storage</span></span>

<span data-ttu-id="1c0b2-157">在本部分，你将使用 Azure Blob 存储上传和下载图像，这些图像将用作跟踪对象的缩略图。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-157">In this section you will use the Azure Blob storage to upload and download images that will be used as thumbnails for *Tracked Objects*.</span></span>

> [!NOTE]
> <span data-ttu-id="1c0b2-158">在本教程中，应用程序将拍摄照片，以将图像上传到 Blob 存储。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-158">In this tutorial the application will take photos to upload images to the Blob storage.</span></span> <span data-ttu-id="1c0b2-159">如果在 Unity 编辑器中本地运行此应用程序，请确保已将网络摄像头连接到计算机。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-159">If you are running this locally from the Unity editor, then make sure that you have a webcam connected to your computer.</span></span>

<span data-ttu-id="1c0b2-160">在 HoloLens 上打开应用程序，单击“设置对象”，然后在搜索栏中键入名称“汽车”。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-160">Open the application on your HoloLens, click on **Set Object** and type in the *search bar* the name "Car".</span></span> <span data-ttu-id="1c0b2-161">现在，应可看到“对象卡”。单击“摄像头”按钮，系统将指示你进行 AirTap 拍照 。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-161">Now you should see the **Object Card**, click on the **Camera** button and you will be instructed to do an AirTap to take a photo.</span></span> <span data-ttu-id="1c0b2-162">拍照后，将显示一条消息，通知你正在进行上传，不久后图像应显示在占位符之前的位置。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-162">After taking a photo you will see a message that informs you about the active upload and after a while the image should appear where the placeholder was before.</span></span>

<span data-ttu-id="1c0b2-163">现在，重新运行该应用程序并搜索跟踪对象，并且以前上传的图像应显示为缩略图。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-163">Now rerun the application and search for the *Tracked Object* and the previously uploaded image should appear as thumbnail.</span></span>

## <a name="deleting-image-from-azure-blob-storage"></a><span data-ttu-id="1c0b2-164">从 Azure Blob 存储删除图像</span><span class="sxs-lookup"><span data-stu-id="1c0b2-164">Deleting image from Azure Blob storage</span></span>

<span data-ttu-id="1c0b2-165">在上一部分，你已将新图像上传到 Azure Blob 存储，在本部分，你将删除跟踪对象的图像缩略图。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-165">In the previous section you uploaded new images to Azure Blob storage, in this section you will delete an image thumbnail for *Tracked Objects*.</span></span>

<span data-ttu-id="1c0b2-166">在 HoloLens 上打开应用程序，单击“设置对象”，然后在搜索栏中键入名称“汽车”。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-166">Open the application on your HoloLens, click on **Set Object** and type in the *search bar* the name "Car".</span></span> <span data-ttu-id="1c0b2-167">现在应该会看到带有缩略图的“对象卡”。单击“删除”按钮 。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-167">Now you should see the **Object Card** with the thumbnail image, click on the **Delete** button.</span></span> <span data-ttu-id="1c0b2-168">你会注意到缩略图图像已替换为占位符图像。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-168">You will notice that the thumbnail image is replaced by the placeholder image.</span></span>

<span data-ttu-id="1c0b2-169">现在，重新运行该应用程序并搜索先前删除的缩略图的跟踪对象，此时应仅显示占位符图像。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-169">Now rerun the application and search for the *Tracked Object* of the previously deleted thumbnail, you should only see the placeholder image.</span></span>

## <a name="congratulations"></a><span data-ttu-id="1c0b2-170">祝贺</span><span class="sxs-lookup"><span data-stu-id="1c0b2-170">Congratulations</span></span>

<span data-ttu-id="1c0b2-171">本教程介绍了如何使用 Azure 存储服务来保持非结构化数据，例如示例中以缩略图图像的形式存储的云中 HoloLens 2 演示应用程序的跟踪对象和二进制文件 。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-171">In this tutorial you learned how Azure storage services can be used to persist unstructured data, like in our case **Tracked Objects** and binaries in form of thumbnail images for the **HoloLens 2** demo application on the cloud.</span></span>

<span data-ttu-id="1c0b2-172">下一教程将介绍如何使用 Azure 自定义视觉来检测与跟踪对象关联的图像。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-172">In the next tutorial you will learn how to use Azure Custom Vision to detect images associated with a *Tracked Object*.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c0b2-173">下一教程：3.集成 Azure 自定义视觉</span><span class="sxs-lookup"><span data-stu-id="1c0b2-173">Next tutorial: 3. Integrating Azure Custom Vision</span></span>](mr-learning-azure-03.md)