---
title: 设置 XR 配置
description: 了解有关 HoloLens 应用程序开发的最新 Unity XR 配置建议。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603703"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="93543-104">设置 XR 配置</span><span class="sxs-lookup"><span data-stu-id="93543-104">Setting up your XR configuration</span></span>

<span data-ttu-id="93543-105">[选择 Unity 版本](choosing-unity-version.md)后，下一步是选择用于构建混合现实应用的 XR 配置：</span><span class="sxs-lookup"><span data-stu-id="93543-105">Once you've [chosen a Unity version](choosing-unity-version.md), the next step is to select the XR configuration you'll use to build your mixed reality app:</span></span>

## <a name="choosing-an-xr-configuration"></a><span data-ttu-id="93543-106">选择 XR 配置</span><span class="sxs-lookup"><span data-stu-id="93543-106">Choosing an XR configuration</span></span>

<span data-ttu-id="93543-107">启动新的 Unity 项目时，可以选择多个 XR 配置：**混合现实 OpenXR 插件**、 **Windows XR 插件** 和 **旧内置 XR**。</span><span class="sxs-lookup"><span data-stu-id="93543-107">When you start a new Unity project, you have various XR configurations you can select from: the **Mixed Reality OpenXR plugin**, the **Windows XR plugin** and **Legacy Built-in XR**.</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="93543-108">用 MRTK 设置项目</span><span class="sxs-lookup"><span data-stu-id="93543-108">Setting up your project with MRTK</span></span>

<span data-ttu-id="93543-109">为混合现实设置 Unity 项目的最简单方法是将混合现实 Toolkit (MRTK) 。</span><span class="sxs-lookup"><span data-stu-id="93543-109">The easiest way to get your Unity project set up for mixed reality is with the Mixed Reality Toolkit (MRTK).</span></span>  <span data-ttu-id="93543-110">MRTK for Unity 是一个开源的跨平台开发工具包，旨在简化混合现实应用程序的构建。</span><span class="sxs-lookup"><span data-stu-id="93543-110">MRTK for Unity is an open-source, cross-platform development kit designed to make it easy to build amazing mixed reality applications.</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="93543-112">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="93543-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span>  <span data-ttu-id="93543-113">在 MRTK 版本2中，你可以加快应用程序开发 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 耳机以及许多其他的 VR/AR 设备。</span><span class="sxs-lookup"><span data-stu-id="93543-113">With MRTK version 2, you can speed up your application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and many other VR/AR devices.</span></span> <span data-ttu-id="93543-114">该项目旨在减少进入障碍，使每个人都可以构建混合现实应用程序，并在我们的所有增长时向社区提供反馈。</span><span class="sxs-lookup"><span data-stu-id="93543-114">The project is aimed at reducing barriers to entry, enabling everyone to build mixed reality applications and contribute back to the community as we all grow.</span></span>

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

<span data-ttu-id="93543-115">若要了解有关混合现实 Toolkit 的详细信息，请参阅[MRTK 文档](/windows/mixed-reality/mrtk-unity)。</span><span class="sxs-lookup"><span data-stu-id="93543-115">To learn more about the Mixed Reality Toolkit, check out the [MRTK documentation](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="93543-116">无 MRTK 的手动设置</span><span class="sxs-lookup"><span data-stu-id="93543-116">Manual setup without MRTK</span></span>

<span data-ttu-id="93543-117">尽管 Microsoft 和社区创建了开源工具，例如[混合现实 Toolkit (MRTK) ](/windows/mixed-reality/mrtk-unity)自动为混合现实设置你的环境，但某些开发人员可能希望从头开始构建自己的体验。</span><span class="sxs-lookup"><span data-stu-id="93543-117">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) that will automatically set up your environment for mixed reality, some developers may wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]