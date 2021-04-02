---
title: 使用 Windows XR 插件
description: 了解如何使用 Windows XR 支持设置具有和没有 MRTK 的 Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目，Windows Mixed Reality，UWP，XR，性能，旧，mrtk，Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938097"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="5f971-104">使用 Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="5f971-104">Using Windows XR plugin</span></span>

<span data-ttu-id="5f971-105">对于面向 Unity 2020 的开发人员，Windows XR 插件允许在 HoloLens 2 和 Windows Mixed Reality 耳机上访问混合现实功能。</span><span class="sxs-lookup"><span data-stu-id="5f971-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="5f971-106">此插件在 Unity 2019 上也受支持，但在该版本上使用此插件时，Azure 空间锚有一些已知的不兼容性。</span><span class="sxs-lookup"><span data-stu-id="5f971-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="5f971-107">尽管 Microsoft 和社区创建了开源工具，例如 [混合现实工具包 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 将自动设置 WMR 环境，但许多开发人员希望从根本上构建他们的经验。</span><span class="sxs-lookup"><span data-stu-id="5f971-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="5f971-108">如果你使用的是 MRTK，则以下文档将演示如何正确设置用于混合现实开发的项目。</span><span class="sxs-lookup"><span data-stu-id="5f971-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="5f971-109">需要更改的设置分为两类：每个项目的设置和每场景设置。</span><span class="sxs-lookup"><span data-stu-id="5f971-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="5f971-110">用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="5f971-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="5f971-111">用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="5f971-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="5f971-112">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="5f971-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="5f971-113">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="5f971-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5f971-114">试用我们的 MRTK 教程</span><span class="sxs-lookup"><span data-stu-id="5f971-114">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="5f971-115">有关更多功能的详细信息，请参阅 [MRTK 的文档](/windows/mixed-reality/mrtk-unity) 。</span><span class="sxs-lookup"><span data-stu-id="5f971-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="5f971-116">无 MRTK 的手动设置</span><span class="sxs-lookup"><span data-stu-id="5f971-116">Manual setup without MRTK</span></span>

<span data-ttu-id="5f971-117">如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="5f971-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

<span data-ttu-id="5f971-119">如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="5f971-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="5f971-120">选择 **文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="5f971-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="5f971-121">选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="5f971-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="5f971-122">将 **体系结构** 设置为 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="5f971-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="5f971-123">将 **目标设备** 设置为 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="5f971-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="5f971-124">将 **生成类型** 设置为 **D3D**</span><span class="sxs-lookup"><span data-stu-id="5f971-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="5f971-125">将 **UWP SDK** 设置为 **安装的最新版本**</span><span class="sxs-lookup"><span data-stu-id="5f971-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="5f971-126">将 **生成配置** 设置为 **发布** ，因为调试存在已知的性能问题</span><span class="sxs-lookup"><span data-stu-id="5f971-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

<span data-ttu-id="5f971-128">设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../design/app-views.md) 而不是2d 视图：</span><span class="sxs-lookup"><span data-stu-id="5f971-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="5f971-129">在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"，然后选择 " **XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="5f971-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="5f971-130">选择 "**安装 XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="5f971-130">Select **Install XR Plugin Management**</span></span>

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-5.png)

3. <span data-ttu-id="5f971-132">选择 **"启动时初始化 XR" 和 "** **Windows Mixed Reality** "</span><span class="sxs-lookup"><span data-stu-id="5f971-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-7.png)

4. <span data-ttu-id="5f971-134">展开 " **XR 插件管理** " 部分，并选择 " **通用 Windows 平台设置** " 选项卡</span><span class="sxs-lookup"><span data-stu-id="5f971-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="5f971-135">如果使用的是 Unity 2020 或更高版本，则会看到用于检查 **OpenXR** 或 **Windows Mixed Reality** 的选项。</span><span class="sxs-lookup"><span data-stu-id="5f971-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="5f971-136">您可以选择 "运行时"。</span><span class="sxs-lookup"><span data-stu-id="5f971-136">You can choose either runtime.</span></span>  <span data-ttu-id="5f971-137">如果你要专门针对 HoloLens 2 或 HP 回音 G2 进行开发，并决定尝试 **OpenXR**，请选择 "OpenXR" 框，并查看本指南，以 [了解如何使用适用于 Unity 的 Mixed Reality OpenXR 插件](openxr-getting-started.md) 为这些设备正确设置，然后再返回到本教程</span><span class="sxs-lookup"><span data-stu-id="5f971-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="5f971-138">从 Unity 2020 LTS 开始，Microsoft 正在接纳 OpenXR 的开发。</span><span class="sxs-lookup"><span data-stu-id="5f971-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="5f971-139">随着我们迁移到此路径，在 Unity 2021.1 中，Windows XR 插件将被弃用并在2021.2 中删除，从而使 OpenXR 成为唯一支持的路径。</span><span class="sxs-lookup"><span data-stu-id="5f971-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="5f971-140">可以在 [使用混合现实 OpenXR 插件](openxr-getting-started.md)中找到详细信息。</span><span class="sxs-lookup"><span data-stu-id="5f971-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="5f971-141">如果决定选择 **Windows Mixed Reality** 插件，请选中所有复选框，并将 **深度提交模式** 设置为 **深度16位**</span><span class="sxs-lookup"><span data-stu-id="5f971-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![突出显示了 Windows Mixed Reality 部分的 "项目设置" 窗口的屏幕截图已在 unity 编辑器中打开](images/wmr-config-img-8.png)
