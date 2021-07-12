---
title: 创建全息远程处理电脑应用程序
description: 完成本课程可以了解如何创建电脑应用程序来远程处理从电脑到 HoloLens 2 的混合现实体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 电脑全息远程处理, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392492"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="ac5b5-104">2.创建全息远程处理电脑应用程序</span><span class="sxs-lookup"><span data-stu-id="ac5b5-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="ac5b5-105">本教程将介绍如何创建用于全息远程处理的电脑应用并随时连接到 HoloLens 2，从而提供一种在混合现实中直观显示 3D 内容的方式。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="ac5b5-106">目标</span><span class="sxs-lookup"><span data-stu-id="ac5b5-106">Objectives</span></span>

* <span data-ttu-id="ac5b5-107">为全息远程处理配置 Unity</span><span class="sxs-lookup"><span data-stu-id="ac5b5-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="ac5b5-108">了解如何通过 Visual Studio 生成和部署应用程序</span><span class="sxs-lookup"><span data-stu-id="ac5b5-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="ac5b5-109">开发全息远程处理应用程序并连接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="ac5b5-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="ac5b5-110">配置功能</span><span class="sxs-lookup"><span data-stu-id="ac5b5-110">Configuring the capabilities</span></span>

<span data-ttu-id="ac5b5-111">在“项目设置”窗口中，展开“发布设置”，向下滚动到“功能”部分，然后选择下面除现有功能外显示的功能复选框 。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-111">In the **Project Settings** window, expand the **Publishing Settings**, scroll down to the Capabilities section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="ac5b5-112">Internet 客户端服务器</span><span class="sxs-lookup"><span data-stu-id="ac5b5-112">Internet Clint server</span></span>
* <span data-ttu-id="ac5b5-113">专用网络客户端服务器</span><span class="sxs-lookup"><span data-stu-id="ac5b5-113">Private Network Client Server</span></span>

![启用功能](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a><span data-ttu-id="ac5b5-115">在电脑上构建应用程序</span><span class="sxs-lookup"><span data-stu-id="ac5b5-115">Build your application to PC</span></span>

<span data-ttu-id="ac5b5-116">全息远程处理应用现可在你的电脑上生成内容。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="ac5b5-117">请按照以下步骤进行这些更改，以在电脑上构建该应用程序。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="ac5b5-118">测试“全息远程处理”远程应用程序</span><span class="sxs-lookup"><span data-stu-id="ac5b5-118">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="ac5b5-119">若要将电脑应用程序连接到 HoloLens 2，请执行以下过程：</span><span class="sxs-lookup"><span data-stu-id="ac5b5-119">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="ac5b5-120">1.在 HoloLens 2 设备上安装“远程播放器”应用程序</span><span class="sxs-lookup"><span data-stu-id="ac5b5-120">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="ac5b5-121">在 HoloLens 2 上，访问 Store 应用并搜索“远程播放器”。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-121">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="ac5b5-122">选择“远程播放器”应用。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-122">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="ac5b5-123">点击“安装”，下载并安装该应用。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-123">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="ac5b5-124">2.将全息远程处理电脑应用连接到远程播放器</span><span class="sxs-lookup"><span data-stu-id="ac5b5-124">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="ac5b5-125">在 HoloLens 上启动“远程播放器”。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-125">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="ac5b5-126">记下 HoloLens IP 地址。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-126">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="ac5b5-127">远程播放器启动后，会立即将其显示为全息图。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-127">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="ac5b5-128">在电脑上打开全息远程处理电脑应用程序。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-128">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="ac5b5-129">启动该应用程序后，输入 IP 地址，然后单击“连接”按钮进行连接 。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-129">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ac5b5-130">祝贺</span><span class="sxs-lookup"><span data-stu-id="ac5b5-130">Congratulations</span></span>

<span data-ttu-id="ac5b5-131">本教程介绍了如何创建全息远程处理远程应用并随时连接到 HoloLens 2，从而提供一种在混合现实中直观显示 3D 内容的方式。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-131">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="ac5b5-132">将 HoloLens 连接到全息远程处理电脑应用程序后，你应该会看到混合现实体验流式传输到 HoloLens 2 设备。</span><span class="sxs-lookup"><span data-stu-id="ac5b5-132">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
