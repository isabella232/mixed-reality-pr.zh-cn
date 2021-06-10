---
title: 通过 Unity 进行托管调试
description: 本文介绍如何在 Unity IL2CPP UWP 项目上运行托管调试器。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity，visual studio，调试，il2cpp，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，UWP
ms.openlocfilehash: 8e3967971220fa453f4e60639bd08f2554a8dd7e
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547078"
---
# <a name="managed-debugging-with-unity"></a><span data-ttu-id="51300-104">通过 Unity 进行托管调试</span><span class="sxs-lookup"><span data-stu-id="51300-104">Managed debugging with Unity</span></span>

<span data-ttu-id="51300-105">按照以下步骤将托管调试器附加到适用于 HoloLens 和 HoloLens 2 的 Unity IL2CPP UWP 生成。</span><span class="sxs-lookup"><span data-stu-id="51300-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="51300-106">你需要位于支持 [多播](https://en.wikipedia.org/wiki/Multicast)的网络上。</span><span class="sxs-lookup"><span data-stu-id="51300-106">You'll need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
2. <span data-ttu-id="51300-107">请参阅 **UWP 发布设置功能** 并查看 **InternetClientServer** 和 **PrivateNetworkClientServer**：</span><span class="sxs-lookup"><span data-stu-id="51300-107">Go to **UWP Publishing Settings Capabilities** and check **InternetClientServer** and **PrivateNetworkClientServer**:</span></span>

    ![UWP 发布设置功能](images/il2cpp-debugging-capabilities.png)

3. <span data-ttu-id="51300-109">配置 Unity UWP 生成设置：</span><span class="sxs-lookup"><span data-stu-id="51300-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="51300-110">开发生成</span><span class="sxs-lookup"><span data-stu-id="51300-110">Development Build</span></span>
    - <span data-ttu-id="51300-111">脚本调试</span><span class="sxs-lookup"><span data-stu-id="51300-111">Script Debugging</span></span>
    - <span data-ttu-id="51300-112">等待托管调试器 (可选) </span><span class="sxs-lookup"><span data-stu-id="51300-112">Wait for Managed Debugger (optional)</span></span>

    ![UWP 生成设置](images/il2cpp-debugging-build.png)

4. <span data-ttu-id="51300-114">在 Unity 中构建。</span><span class="sxs-lookup"><span data-stu-id="51300-114">Build in Unity.</span></span>
5. <span data-ttu-id="51300-115">生成 Visual Studio 解决方案并将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="51300-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="51300-116">你应以 " **调试** " 或 " **发布** " 配置进行构建。</span><span class="sxs-lookup"><span data-stu-id="51300-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="51300-117">**主** 配置将禁用 Unity 探查器，并可防止优化调试。</span><span class="sxs-lookup"><span data-stu-id="51300-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="51300-118">（可选）在解决方案的 appxmanifest.xml 中的功能列表中验证 **Internet (客户端 & 服务器)** 和 **专用网络 (客户端 & 服务器)** 。</span><span class="sxs-lookup"><span data-stu-id="51300-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
6. <span data-ttu-id="51300-119">确保你的设备已连接到与你的电脑相同的网络，并在设备上启动该应用。</span><span class="sxs-lookup"><span data-stu-id="51300-119">Make sure your device is connected to the same network as your PC and start the app on your device.</span></span>
7. <span data-ttu-id="51300-120">请确保设备 **未** 通过 USB 连接到你的电脑。</span><span class="sxs-lookup"><span data-stu-id="51300-120">Make sure the device **is not** connected to your PC via USB.</span></span>
8. <span data-ttu-id="51300-121">双击 Unity 中的一个脚本，并中转到 Visual Studio 解决方案，打开它以查看和编辑。</span><span class="sxs-lookup"><span data-stu-id="51300-121">Double-click one of your scripts in Unity and go to the Visual Studio solution that opens to view and edit.</span></span>
9. <span data-ttu-id="51300-122">调试-> 附加 Unity 调试器。</span><span class="sxs-lookup"><span data-stu-id="51300-122">Debug -> Attach Unity Debugger.</span></span>

    ![附加 Unity 调试器](images/il2cpp-debugging-attach.png)

10. <span data-ttu-id="51300-124">在列表中选择你的设备，然后单击 "确定" 以附加。</span><span class="sxs-lookup"><span data-stu-id="51300-124">Select your device in the list and click "OK" to attach.</span></span>

    ![设备列表](images/il2cpp-debugging-machines.png)
