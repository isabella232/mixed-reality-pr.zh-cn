---
title: MRTK 教程简介
description: 本课程从零开始介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, 求解器, 眼动跟踪, 语音命令
ms.localizationpriority: high
ms.openlocfilehash: abee2163c3b92897396ea35cc43ae025e8e7b804
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175486"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="60156-104">1.MRTK 教程简介</span><span class="sxs-lookup"><span data-stu-id="60156-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="60156-105">欢迎使用入门教程系列！</span><span class="sxs-lookup"><span data-stu-id="60156-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="60156-106">这些教程将介绍混合现实工具包 (MRTK) 及其提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="60156-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="60156-107">此外，还将构建一个混合现实体验，让用户可在其中浏览按 NASA 的“好奇号”火星探测车建模的全息图。</span><span class="sxs-lookup"><span data-stu-id="60156-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="60156-108">本系列结束后，你将牢牢把握 MRTK 及其如何加速开发过程。</span><span class="sxs-lookup"><span data-stu-id="60156-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="60156-109">本系列教程的设计遵循一定的顺序，因此请按正确的顺序学习：</span><span class="sxs-lookup"><span data-stu-id="60156-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="60156-110">[简介](mr-learning-base-01.md)（你已经位于这里）</span><span class="sxs-lookup"><span data-stu-id="60156-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="60156-111">初始化项目并部署第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="60156-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="60156-112">配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="60156-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="60156-113">定位场景中的对象</span><span class="sxs-lookup"><span data-stu-id="60156-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="60156-114">使用求解器创建动态内容</span><span class="sxs-lookup"><span data-stu-id="60156-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="60156-115">创建用户界面</span><span class="sxs-lookup"><span data-stu-id="60156-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="60156-116">与 3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="60156-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="60156-117">使用眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="60156-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="60156-118">使用语音命令</span><span class="sxs-lookup"><span data-stu-id="60156-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="60156-119">目标</span><span class="sxs-lookup"><span data-stu-id="60156-119">Objectives</span></span>

* <span data-ttu-id="60156-120">了解如何针对 MRTK 配置 Unity</span><span class="sxs-lookup"><span data-stu-id="60156-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="60156-121">了解如何生成和部署到设备</span><span class="sxs-lookup"><span data-stu-id="60156-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="60156-122">了解如何使用 MRTK 的一些主要功能</span><span class="sxs-lookup"><span data-stu-id="60156-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="60156-123">创建完整的混合现实体验</span><span class="sxs-lookup"><span data-stu-id="60156-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="60156-124">必备条件</span><span class="sxs-lookup"><span data-stu-id="60156-124">Prerequisites</span></span>

* <span data-ttu-id="60156-125">一台 Windows 10 电脑，其中已[安装](../../install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="60156-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="60156-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="60156-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="60156-127">一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="60156-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="60156-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> 并装有 Unity 2020.3 LTS 或 Unity 2019.4 LTS（OpenXR 要求使用 2020.3.8 或更高版本以防发生错误）</span><span class="sxs-lookup"><span data-stu-id="60156-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020.3 LTS or Unity 2019.4 LTS installed (**OpenXR requires 2020.3.8 or later to prevent bugs**)</span></span>

<span data-ttu-id="60156-129">安装 Unity 时，请务必在“平台”下检查以下组件。</span><span class="sxs-lookup"><span data-stu-id="60156-129">When installing Unity, please make sure to check following components under **'Platforms'**.</span></span>

* <span data-ttu-id="60156-130">**通用 Windows 平台生成支持**</span><span class="sxs-lookup"><span data-stu-id="60156-130">**Universal Windows Platform Build Support**</span></span>
* <span data-ttu-id="60156-131">**Windows 生成支持 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="60156-131">**Windows Build Support (IL2CPP)**</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

<span data-ttu-id="60156-132">如果安装 Unity 时未使用这些选项，可以通过 Unity Hub 中的“添加模块”菜单添加它们。</span><span class="sxs-lookup"><span data-stu-id="60156-132">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub.</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> <span data-ttu-id="60156-133">建议用于本系列教程的 MRTK 版本是 MRTK 2.7.2</span><span class="sxs-lookup"><span data-stu-id="60156-133">The recommended MRTK version for this tutorial series is MRTK 2.7.2</span></span>

> [!Important]
> <span data-ttu-id="60156-134">本系列教程支持 Unity 2020 LTS（当前版本 2020.3.x）（如果您使用 Open XR 或 Windows XR 插件）以及 Unity 2019 LTS（当前版本 2019.4.x）（如果您使用旧版 WSA 或 Windows XR 插件）。</span><span class="sxs-lookup"><span data-stu-id="60156-134">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="60156-135">这将取代上述链接的先决条件中所述的任何 Unity 版本要求。</span><span class="sxs-lookup"><span data-stu-id="60156-135">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60156-136">下一教程：2.初始化项目并部署第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="60156-136">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
