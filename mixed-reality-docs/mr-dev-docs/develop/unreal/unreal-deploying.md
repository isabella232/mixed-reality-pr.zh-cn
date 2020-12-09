---
title: 在 Unreal 中部署到设备
description: 将 Unreal 中的设备部署到 HoloLens 2 的指南
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，mixed reality，部署到设备，PC，文档，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
appliesto:
- HoloLens 2
ms.openlocfilehash: 390bd1a9f1bc643efb1a342421e8c96574e74334
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925906"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="5367f-104">在 Unreal 中部署到设备</span><span class="sxs-lookup"><span data-stu-id="5367f-104">Deploy to device in Unreal</span></span>

<span data-ttu-id="5367f-105">可通过两种方法将 Unreal 应用程序部署到 HoloLens 2：</span><span class="sxs-lookup"><span data-stu-id="5367f-105">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="5367f-106">直接从 Unreal 编辑器</span><span class="sxs-lookup"><span data-stu-id="5367f-106">Directly from the Unreal editor</span></span>
* <span data-ttu-id="5367f-107">作为通过设备门户上传的包</span><span class="sxs-lookup"><span data-stu-id="5367f-107">As a package uploaded via the device portal</span></span>

<span data-ttu-id="5367f-108">这两个选项都要求你将 HoloLens 设置为使用 [设备门户](../platform-capabilities-and-apis/using-the-windows-device-portal.md) 进行开发。</span><span class="sxs-lookup"><span data-stu-id="5367f-108">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="5367f-109">从 Unreal 编辑器部署到设备</span><span class="sxs-lookup"><span data-stu-id="5367f-109">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="5367f-110">选择 " **启动** " 按钮旁边的下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="5367f-110">Select the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="5367f-111">最初，HoloLens 设备选项将显示为灰色。</span><span class="sxs-lookup"><span data-stu-id="5367f-111">Initially, the HoloLens device option will be grayed out.</span></span>

![启动下拉选项](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="5367f-113">打开 **设备管理器** ，请注意，你的 HoloLens 不会自动显示在设备列表中。</span><span class="sxs-lookup"><span data-stu-id="5367f-113">Open the **Device Manager** and note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="5367f-114">展开 " **添加未列出的设备** " 部分。</span><span class="sxs-lookup"><span data-stu-id="5367f-114">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="5367f-115">选择 " **HoloLens** " 作为 **平台**。</span><span class="sxs-lookup"><span data-stu-id="5367f-115">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="5367f-116">输入设备的 IP 地址和端口信息，用冒号分隔作为设备标识符。</span><span class="sxs-lookup"><span data-stu-id="5367f-116">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="5367f-117">例如，当通过 USB) 连接时 ("127.0.0.1： 10080"。</span><span class="sxs-lookup"><span data-stu-id="5367f-117">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="5367f-118">使用设备门户的用户名和密码凭据。</span><span class="sxs-lookup"><span data-stu-id="5367f-118">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="5367f-119">点击 " **添加** " 并关闭 "设备管理器"。</span><span class="sxs-lookup"><span data-stu-id="5367f-119">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="5367f-120">如果出现错误，如地址或用户凭据错误，则会在输出日志中打印一条消息。</span><span class="sxs-lookup"><span data-stu-id="5367f-120">If there's an error, such as wrong address or user credentials, a message will print to the Output Log.</span></span>

![添加未列出的设备](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="5367f-122">再次选择 " **启动** " 按钮旁的下拉箭头，此时应会看到刚刚添加的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="5367f-122">Select the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="5367f-123">选择要生成并部署到 HoloLens 的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="5367f-123">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="5367f-124">构建设备可能需要重新编译着色器 (尤其是在第一次运行) 上，这可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="5367f-124">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="5367f-125">不要让设备进入睡眠状态，直到应用程序运行 (可能需要) 。</span><span class="sxs-lookup"><span data-stu-id="5367f-125">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="5367f-126">否则，着色器编译将失败！</span><span class="sxs-lookup"><span data-stu-id="5367f-126">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="5367f-127">通过设备门户部署到设备</span><span class="sxs-lookup"><span data-stu-id="5367f-127">Deploying to device via device portal</span></span>

<span data-ttu-id="5367f-128">可在 [Unreal 教程系列](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)中找到有关打包和部署应用的详细说明。</span><span class="sxs-lookup"><span data-stu-id="5367f-128">You can find detailed instructions on packaging and deploying an app in the [Unreal tutorial series](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5367f-129">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="5367f-129">Next Development Checkpoint</span></span>

<span data-ttu-id="5367f-130">如果遵循我们的 Unreal 开发旅程，就是在部署阶段。</span><span class="sxs-lookup"><span data-stu-id="5367f-130">If you're following the Unreal development journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="5367f-131">在此处，你可以继续添加高级服务：</span><span class="sxs-lookup"><span data-stu-id="5367f-131">From here, you can continue to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5367f-132">高级服务</span><span class="sxs-lookup"><span data-stu-id="5367f-132">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="5367f-133">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#4-streaming-and-deploying-to-a-device)。</span><span class="sxs-lookup"><span data-stu-id="5367f-133">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
