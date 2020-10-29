---
title: 1. 入门
description: 教程系列第 1 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 5c4ce7c50e252a7b52a1d2e29d47642cfcda6e10
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91696839"
---
# <a name="1-getting-started"></a><span data-ttu-id="9f161-104">1.入门</span><span class="sxs-lookup"><span data-stu-id="9f161-104">1. Getting started</span></span>

<span data-ttu-id="9f161-105">无论你是混合现实新手还是经验丰富的专业人员，都可以使用 [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) 和 [Unreal Engine](https://www.unrealengine.com/en-US/) 开始你的体验之旅。</span><span class="sxs-lookup"><span data-stu-id="9f161-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="9f161-106">本系列教程将为你提供有关如何使用 [UX Tools 插件](https://github.com/microsoft/MixedReality-UXTools-Unreal)构建交互式象棋应用的分步指南，该插件是 [Unreal 混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unreal)的一部分。</span><span class="sxs-lookup"><span data-stu-id="9f161-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="9f161-107">该插件将帮助你通过代码、蓝图和示例将常见的 UX 功能添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="9f161-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![在视口中结束场景](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="9f161-109">在本系列文章结束时，你将拥有以下方面的实操经验：</span><span class="sxs-lookup"><span data-stu-id="9f161-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="9f161-110">开始新项目</span><span class="sxs-lookup"><span data-stu-id="9f161-110">Starting a new project</span></span>
* <span data-ttu-id="9f161-111">设置混合现实</span><span class="sxs-lookup"><span data-stu-id="9f161-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="9f161-112">使用用户输入</span><span class="sxs-lookup"><span data-stu-id="9f161-112">Working with user input</span></span>
* <span data-ttu-id="9f161-113">添加按钮</span><span class="sxs-lookup"><span data-stu-id="9f161-113">Adding buttons</span></span>
* <span data-ttu-id="9f161-114">在模拟器或设备上播放</span><span class="sxs-lookup"><span data-stu-id="9f161-114">Playing on an emulator or device</span></span>


## <a name="prerequisites"></a><span data-ttu-id="9f161-115">必备知识</span><span class="sxs-lookup"><span data-stu-id="9f161-115">Prerequisites</span></span>
<span data-ttu-id="9f161-116">在开始之前，请确保已安装以下项：</span><span class="sxs-lookup"><span data-stu-id="9f161-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="9f161-117">Windows 10 1809 或更高版本</span><span class="sxs-lookup"><span data-stu-id="9f161-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="9f161-118">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="9f161-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9f161-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 或更高版本</span><span class="sxs-lookup"><span data-stu-id="9f161-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="9f161-120">[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 Microsoft HoloLens 2 设备，或仿真器</span><span class="sxs-lookup"><span data-stu-id="9f161-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="9f161-121">具有以下工作负载的 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9f161-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="9f161-122">安装 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9f161-122">Installing Visual Studio 2019</span></span>
<span data-ttu-id="9f161-123">有几个步骤可以确保具有所有必需的 Visual Studio 包：</span><span class="sxs-lookup"><span data-stu-id="9f161-123">There are a few steps to ensure you have all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="9f161-124">安装最新版本的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="9f161-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="9f161-125">安装以下[工作负载](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads)：</span><span class="sxs-lookup"><span data-stu-id="9f161-125">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span></span>
    * <span data-ttu-id="9f161-126">使用 C++ 的桌面开发</span><span class="sxs-lookup"><span data-stu-id="9f161-126">Desktop development with C++</span></span>
    * <span data-ttu-id="9f161-127">.NET 桌面开发</span><span class="sxs-lookup"><span data-stu-id="9f161-127">.NET desktop development</span></span>
    * <span data-ttu-id="9f161-128">通用 Windows 平台开发</span><span class="sxs-lookup"><span data-stu-id="9f161-128">Universal Windows Platform development</span></span>

3. <span data-ttu-id="9f161-129">安装以下[组件](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components)：</span><span class="sxs-lookup"><span data-stu-id="9f161-129">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span></span>
    * <span data-ttu-id="9f161-130">编译器、生成工具和运行时 > MSVC v142 - VS 2019 C++ ARM64 生成工具（最新版本）</span><span class="sxs-lookup"><span data-stu-id="9f161-130">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="9f161-131">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="9f161-131">That's it!</span></span> <span data-ttu-id="9f161-132">一切准备就绪，现在可以开始象棋项目了。</span><span class="sxs-lookup"><span data-stu-id="9f161-132">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="9f161-133">下一节：2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="9f161-133">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)