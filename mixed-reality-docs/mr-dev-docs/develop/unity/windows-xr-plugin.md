---
title: 使用 Windows XR 插件
description: 了解如何使用 Windows XR 支持在具有和没有 MRTK 的情况下设置 Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity， 混合现实， 开发， 入门， 新项目， Windows Mixed Reality， UWP， XR， 性能， 旧版， mrtk， 窗口
ms.openlocfilehash: 44de6b418995b75d9e199f03922f89016b76c5cd
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743646"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="8a5e2-104">使用 Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="8a5e2-104">Using Windows XR plugin</span></span>

<span data-ttu-id="8a5e2-105">对于面向 Unity 2020 的开发人员，Windows XR 插件允许访问 HoloLens 2 和 Windows Mixed Reality 头戴显示设备上的混合现实功能。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="8a5e2-106">Unity 2019 也支持此插件，尽管在此版本上使用此插件时，Azure 空间定位点存在一些已知的不兼容。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="8a5e2-107">虽然 Microsoft 和社区已创建开源工具（如混合现实工具包 [ (MRTK) ） ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 来自动设置 WMR 环境，但许多开发人员希望从头构建自己的体验。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="8a5e2-108">以下文档将演示如何正确设置混合现实开发项目，无论你是否使用 MRTK。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="8a5e2-109">需要更改的设置分为两类：每项目设置和按场景设置。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="8a5e2-110">使用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="8a5e2-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="8a5e2-111">用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="8a5e2-112">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="8a5e2-113">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8a5e2-114">试用我们的 MRTK 教程</span><span class="sxs-lookup"><span data-stu-id="8a5e2-114">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="8a5e2-115">有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="8a5e2-116">不带 MRTK 的手动设置</span><span class="sxs-lookup"><span data-stu-id="8a5e2-116">Manual setup without MRTK</span></span>

<span data-ttu-id="8a5e2-117">如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="8a5e2-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](images/wmr-config-img-3.png)

<span data-ttu-id="8a5e2-119">如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="8a5e2-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="8a5e2-120">选择 **"文件>生成设置..."**</span><span class="sxs-lookup"><span data-stu-id="8a5e2-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="8a5e2-121">在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**</span><span class="sxs-lookup"><span data-stu-id="8a5e2-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="8a5e2-122">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="8a5e2-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="8a5e2-123">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="8a5e2-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="8a5e2-124">将“生成类型”设置为“D3D” </span><span class="sxs-lookup"><span data-stu-id="8a5e2-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="8a5e2-125">将“UWP SDK”设置为“最近安装的版本” </span><span class="sxs-lookup"><span data-stu-id="8a5e2-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="8a5e2-126">将“生成配置”设置为“发布”，因为调试存在已知的性能问题 </span><span class="sxs-lookup"><span data-stu-id="8a5e2-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

<span data-ttu-id="8a5e2-128">设置平台后，需要让 Unity 知道在导出时创建[](../../design/app-views.md)沉浸式视图而不是 2D 视图：</span><span class="sxs-lookup"><span data-stu-id="8a5e2-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="8a5e2-129">在 Unity 编辑器中，导航到"编辑 **>项目设置"，然后选择\*\*\*\*"XR 插件管理"**</span><span class="sxs-lookup"><span data-stu-id="8a5e2-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="8a5e2-130">选择 **"安装 XR 插件管理"**</span><span class="sxs-lookup"><span data-stu-id="8a5e2-130">Select **Install XR Plugin Management**</span></span>

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-5.png)

3. <span data-ttu-id="8a5e2-132">选择 **"启动时初始化 XR"，\*\*\*\*然后选择Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="8a5e2-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-7.png)

4. <span data-ttu-id="8a5e2-134">展开 **"XR 插件管理"部分，** 然后选择 **"Univeral Windows 平台设置"** 选项卡</span><span class="sxs-lookup"><span data-stu-id="8a5e2-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="8a5e2-135">如果使用的是 Unity 2020 或更高版本，则会看到用于检查 **OpenXR** 或 **Windows Mixed Reality。**</span><span class="sxs-lookup"><span data-stu-id="8a5e2-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="8a5e2-136">可以选择任一运行时。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-136">You can choose either runtime.</span></span>  <span data-ttu-id="8a5e2-137">如果你专门针对 HoloLens 2 或 HP Reverb G2 进行开发，并决定试用 **OpenXR，** 请选择 OpenXR 框，查看使用适用于 Unity 的混合现实 [OpenXR](openxr-getting-started.md) 插件指南，在返回到本教程之前，请正确设置这些设备</span><span class="sxs-lookup"><span data-stu-id="8a5e2-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="8a5e2-138">从 Unity 2020 LTS 开始，Microsoft 将采用 OpenXR 开发。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="8a5e2-139">迁移到此路径时，在 Unity 2021.1 中，Windows XR 插件将在 2021.2 中弃用并删除，使 OpenXR 成为唯一受支持的路径。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="8a5e2-140">有关详细信息，请参阅 [使用混合现实 OpenXR 插件](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="8a5e2-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="8a5e2-141">如果决定选择"深度提交 **Windows Mixed Reality，** 请选中所有框，将"深度提交模式"设置为"深度 **16 位"**</span><span class="sxs-lookup"><span data-stu-id="8a5e2-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中Windows Mixed Reality部分](images/wmr-config-img-8.png)