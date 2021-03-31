---
title: 使用旧的内置 XR 支持
description: 了解如何使用旧内置 XR 支持设置具有和没有 MRTK 的 Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目，Windows Mixed Reality，UWP，XR，性能，旧，mrtk
ms.openlocfilehash: 0860154034a63d5058da09a3b842e70bc3775dc5
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938100"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="0a603-104">使用旧的内置 XR 支持</span><span class="sxs-lookup"><span data-stu-id="0a603-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="0a603-105">用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="0a603-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="0a603-106">用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="0a603-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="0a603-107">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="0a603-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="0a603-108">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="0a603-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0a603-109">试用我们的 MRTK 教程</span><span class="sxs-lookup"><span data-stu-id="0a603-109">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="0a603-110">有关更多功能的详细信息，请参阅 [MRTK 的文档](/windows/mixed-reality/mrtk-unity) 。</span><span class="sxs-lookup"><span data-stu-id="0a603-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="0a603-111">无 MRTK 的手动设置</span><span class="sxs-lookup"><span data-stu-id="0a603-111">Manual setup without MRTK</span></span>

<span data-ttu-id="0a603-112">如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="0a603-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

<span data-ttu-id="0a603-114">如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="0a603-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="0a603-115">选择 **文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="0a603-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="0a603-116">选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="0a603-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="0a603-117">将 **体系结构** 设置为 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="0a603-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="0a603-118">将 **目标设备** 设置为 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="0a603-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="0a603-119">将 **生成类型** 设置为 **D3D**</span><span class="sxs-lookup"><span data-stu-id="0a603-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="0a603-120">将 **UWP SDK** 设置为 **安装的最新版本**</span><span class="sxs-lookup"><span data-stu-id="0a603-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="0a603-121">将 **生成配置** 设置为 **发布** ，因为调试存在已知的性能问题</span><span class="sxs-lookup"><span data-stu-id="0a603-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

<span data-ttu-id="0a603-123">设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../design/app-views.md) 而不是2d 视图。</span><span class="sxs-lookup"><span data-stu-id="0a603-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="0a603-124">旧版 XR 在 Unity 2019 中已弃用，并已在 Unity 2020 中删除。</span><span class="sxs-lookup"><span data-stu-id="0a603-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="0a603-125">从生成设置中打开 **播放机设置** ... **窗口** 并展开 **XR 设置** 组</span><span class="sxs-lookup"><span data-stu-id="0a603-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="0a603-126">在 " **XR 设置** " 部分中，选择 " **支持的虚拟现实** " 以添加虚拟现实设备列表</span><span class="sxs-lookup"><span data-stu-id="0a603-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="0a603-127">将 **深度格式** 设置为 **16 位深度** 并启用 **深度缓冲共享**</span><span class="sxs-lookup"><span data-stu-id="0a603-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="0a603-128">将 **立体声渲染模式** 设置为 **单一传递实例**</span><span class="sxs-lookup"><span data-stu-id="0a603-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="0a603-129">如果要使用全息远程处理，请选择 " **支持 WSA 全息远程处理** "</span><span class="sxs-lookup"><span data-stu-id="0a603-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![突出显示了 "播放机设置" 部分的 "项目设置" 窗口的屏幕截图](images/wmr-config-img-9.png)