---
title: 在 Unreal 中部署到设备
description: 将 Unreal 中的设备部署到 HoloLens 2 的指南
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，mixed reality，部署到设备，PC，文档
appliesto:
- HoloLens 2
ms.openlocfilehash: abd5e5c28ec5e66c4f73df8edf5e0ac0212d170a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677328"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="0ebad-104">在 Unreal 中部署到设备</span><span class="sxs-lookup"><span data-stu-id="0ebad-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="0ebad-105">概述</span><span class="sxs-lookup"><span data-stu-id="0ebad-105">Overview</span></span>
<span data-ttu-id="0ebad-106">可通过两种方法将 Unreal 应用程序部署到 HoloLens 2：</span><span class="sxs-lookup"><span data-stu-id="0ebad-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="0ebad-107">直接从 Unreal 编辑器</span><span class="sxs-lookup"><span data-stu-id="0ebad-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="0ebad-108">作为通过设备门户上传的包</span><span class="sxs-lookup"><span data-stu-id="0ebad-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="0ebad-109">这两个选项都要求你将 HoloLens 设置为使用 [设备门户](../platform-capabilities-and-apis/using-the-windows-device-portal.md) 进行开发。</span><span class="sxs-lookup"><span data-stu-id="0ebad-109">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="0ebad-110">从 Unreal 编辑器部署到设备</span><span class="sxs-lookup"><span data-stu-id="0ebad-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="0ebad-111">单击 " **启动** " 按钮旁的下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="0ebad-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="0ebad-112">最初，HoloLens 设备选项将显示为灰色。</span><span class="sxs-lookup"><span data-stu-id="0ebad-112">Initially, the HoloLens device option will be grayed out.</span></span>

![启动下拉选项](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="0ebad-114">打开 **设备管理器** 。</span><span class="sxs-lookup"><span data-stu-id="0ebad-114">Open the **Device Manager** .</span></span> <span data-ttu-id="0ebad-115">请注意，HoloLens 不会自动显示在设备列表中。</span><span class="sxs-lookup"><span data-stu-id="0ebad-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="0ebad-116">展开 " **添加未列出的设备** " 部分。</span><span class="sxs-lookup"><span data-stu-id="0ebad-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="0ebad-117">选择 " **HoloLens** " 作为 **平台** 。</span><span class="sxs-lookup"><span data-stu-id="0ebad-117">Select **HoloLens** as your **Platform** .</span></span>

5. <span data-ttu-id="0ebad-118">输入设备的 IP 地址和端口信息，用冒号分隔作为设备标识符。</span><span class="sxs-lookup"><span data-stu-id="0ebad-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="0ebad-119">例如，当通过 USB) 连接时 ("127.0.0.1： 10080"。</span><span class="sxs-lookup"><span data-stu-id="0ebad-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="0ebad-120">使用设备门户的用户名和密码凭据。</span><span class="sxs-lookup"><span data-stu-id="0ebad-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="0ebad-121">点击 " **添加** " 并关闭 "设备管理器"。</span><span class="sxs-lookup"><span data-stu-id="0ebad-121">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="0ebad-122">如果错误 (例如错误的地址、用户名或密码) ，则会在输出日志中打印一条消息。</span><span class="sxs-lookup"><span data-stu-id="0ebad-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![添加未列出的设备](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="0ebad-124">再次单击 " **启动** " 按钮旁的下拉箭头，此时应会看到刚刚添加的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="0ebad-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="0ebad-125">选择要生成并部署到 HoloLens 的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="0ebad-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="0ebad-126">构建设备可能需要重新编译着色器 (尤其是在第一次运行) 上，这可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="0ebad-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="0ebad-127">不要让设备进入睡眠状态，直到应用程序运行 (可能需要) 。</span><span class="sxs-lookup"><span data-stu-id="0ebad-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="0ebad-128">否则，着色器编译将失败！</span><span class="sxs-lookup"><span data-stu-id="0ebad-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="0ebad-129">通过设备门户部署到设备</span><span class="sxs-lookup"><span data-stu-id="0ebad-129">Deploying to device via device portal</span></span>

<span data-ttu-id="0ebad-130">可以在使用 Unreal 教程系列的入门的最后一部分中找到有关 [打包和部署应用](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) 的详细说明。</span><span class="sxs-lookup"><span data-stu-id="0ebad-130">You can find detailed instructions on [packaging and deploying an app](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0ebad-131">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="0ebad-131">Next Development Checkpoint</span></span>

<span data-ttu-id="0ebad-132">如果遵循我们已 Unreal 的开发检查点旅程，就是在部署阶段。</span><span class="sxs-lookup"><span data-stu-id="0ebad-132">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="0ebad-133">在这里，你可以继续添加高级服务：</span><span class="sxs-lookup"><span data-stu-id="0ebad-133">From here, you can proceed to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0ebad-134">高级服务</span><span class="sxs-lookup"><span data-stu-id="0ebad-134">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="0ebad-135">随时可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#4-deploying-to-a-device) 。</span><span class="sxs-lookup"><span data-stu-id="0ebad-135">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-deploying-to-a-device) at any time.</span></span>
