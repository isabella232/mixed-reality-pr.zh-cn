---
title: 空间音频教程-1。 向项目添加空间音频
description: 将 Microsoft Spatializer 插件添加到 Unity 项目以访问 HoloLens 2 HRTF 硬件卸载。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，head 相关传输函数，回音，Microsoft Spatializer
ms.openlocfilehash: 7ed1355e3c522fcd94a96dd761a8a9ebb01c4c4c
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590039"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="09e8c-105">1. 将空间音频添加到 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="09e8c-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="09e8c-106">概述</span><span class="sxs-lookup"><span data-stu-id="09e8c-106">Overview</span></span>

<span data-ttu-id="09e8c-107">欢迎使用 HoloLens2 上 Unity 的空间音频教程。</span><span class="sxs-lookup"><span data-stu-id="09e8c-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="09e8c-108">在本系列教程中，你将了解如何在 HoloLens 2 上使用与头相关的传输功能 (HRTF) 卸载，以及如何在使用 HRTF 卸载时启用回响。</span><span class="sxs-lookup"><span data-stu-id="09e8c-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="09e8c-109">[Microsoft Spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)包含此教程序列的已完成 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="09e8c-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="09e8c-110">若要了解如何使用基于 HRTF 的 spatialization 技术来 spatialize 声音，并提供有关其有用时间的建议，请参阅 [空间音效设计](/windows/mixed-reality/spatial-sound-design)。</span><span class="sxs-lookup"><span data-stu-id="09e8c-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="09e8c-111">什么是 HRTF 卸载？</span><span class="sxs-lookup"><span data-stu-id="09e8c-111">What is HRTF offload?</span></span>

<span data-ttu-id="09e8c-112">使用基于 HRTF 的算法处理音频需要大量的专用计算。</span><span class="sxs-lookup"><span data-stu-id="09e8c-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="09e8c-113">HoloLens 2 包括专用硬件，可以利用这些硬件来避免应用程序处理器的负担，从而将处理基于 HRTF 的算法。</span><span class="sxs-lookup"><span data-stu-id="09e8c-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="09e8c-114">Microsoft spatializer 插件为应用程序提供了一种简单的方法，使应用程序能够利用专用的 HRTF 硬件，使应用程序可以将更多应用程序处理器用于除了空间音频以外的其他操作。</span><span class="sxs-lookup"><span data-stu-id="09e8c-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="09e8c-115">目标</span><span class="sxs-lookup"><span data-stu-id="09e8c-115">Objectives</span></span>

* <span data-ttu-id="09e8c-116">导入和启用 Microsoft spatializer 插件</span><span class="sxs-lookup"><span data-stu-id="09e8c-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="09e8c-117">启用开发人员工作站上的空间音频</span><span class="sxs-lookup"><span data-stu-id="09e8c-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="09e8c-118">必备条件</span><span class="sxs-lookup"><span data-stu-id="09e8c-118">Prerequisites</span></span>

* <span data-ttu-id="09e8c-119">一台 Windows 10 电脑，其中已[安装](../../install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="09e8c-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="09e8c-120">基本 C# 编程知识</span><span class="sxs-lookup"><span data-stu-id="09e8c-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="09e8c-121">一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="09e8c-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="09e8c-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已装载 Unity 2019 LTS 且已添加通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="09e8c-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="09e8c-123">我们 **强烈建议** 先完成 [入门](mr-learning-base-01.md) 教程系列，或先熟悉 Unity 和 MRTK，然后再继续。</span><span class="sxs-lookup"><span data-stu-id="09e8c-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="09e8c-124">建议对本系列教程使用 Unity 2019 LTS。</span><span class="sxs-lookup"><span data-stu-id="09e8c-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="09e8c-125">这将取代上述链接的先决条件中所述的所有 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="09e8c-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="09e8c-126">创建和准备 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="09e8c-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="09e8c-127">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="09e8c-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="09e8c-128">为此，请先执行[初始化项目和第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：</span><span class="sxs-lookup"><span data-stu-id="09e8c-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="09e8c-129">[创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="09e8c-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="09e8c-130">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="09e8c-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="09e8c-131">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="09e8c-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="09e8c-132">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="09e8c-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="09e8c-133">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="09e8c-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="09e8c-134">[创建和设置场景](mr-learning-base-02.md#creating-and-configuring-the-scene) 并为场景提供一个合适的名称，例如 *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="09e8c-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="09e8c-135">然后，按照 [更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 说明进行操作，以确保场景的 MRTK 配置文件为 **DefaultHoloLens2ConfigurationProfile** ，并将空间感知网格的显示选项改为 " **封闭**"。</span><span class="sxs-lookup"><span data-stu-id="09e8c-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="09e8c-136">向项目添加 Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="09e8c-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="09e8c-137">下载并导入 Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">SpatialAudio. unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="09e8c-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="09e8c-138">有关如何导入 Unity 自定义包的提醒，可以参阅 [导入教程资产](mr-learning-base-04.md#importing-the-tutorial-assets) 说明。</span><span class="sxs-lookup"><span data-stu-id="09e8c-138">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="09e8c-139">启用 Microsoft Spatializer 插件</span><span class="sxs-lookup"><span data-stu-id="09e8c-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="09e8c-140">导入 **Microsoft Spatializer** 后，需要启用它。</span><span class="sxs-lookup"><span data-stu-id="09e8c-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="09e8c-141">打开 **> 项目设置-> 音频**"，然后将 **Spatializer 插件** 更改为" Microsoft Spatializer "。</span><span class="sxs-lookup"><span data-stu-id="09e8c-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![显示 spatializer 插件的项目设置](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="09e8c-143">启用工作站上的空间音频</span><span class="sxs-lookup"><span data-stu-id="09e8c-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="09e8c-144">在桌面版本的 Windows 上，默认情况下禁用空间音频。</span><span class="sxs-lookup"><span data-stu-id="09e8c-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="09e8c-145">右键单击任务栏中的音量图标即可启用此项。</span><span class="sxs-lookup"><span data-stu-id="09e8c-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="09e8c-146">若要获得有关在 HoloLens 2 上收到的内容的最佳表示，请选择 " **空间音效-> Windows Sonic 用于耳机**"。</span><span class="sxs-lookup"><span data-stu-id="09e8c-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![桌面空间音频设置](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="09e8c-148">仅当计划在 Unity 编辑器中测试项目时，才需要此设置。</span><span class="sxs-lookup"><span data-stu-id="09e8c-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="09e8c-149">祝贺</span><span class="sxs-lookup"><span data-stu-id="09e8c-149">Congratulations</span></span>

<span data-ttu-id="09e8c-150">在本教程中，你将了解如何导入和启用 Microsoft Spatializer 插件，还可以在工作站上启用空间音频了解到。</span><span class="sxs-lookup"><span data-stu-id="09e8c-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="09e8c-151">在下一教程中，你将了解如何在 unity 项目中添加空间音频。</span><span class="sxs-lookup"><span data-stu-id="09e8c-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="09e8c-152">下一教程： Spatializing 按钮交互声音</span><span class="sxs-lookup"><span data-stu-id="09e8c-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
