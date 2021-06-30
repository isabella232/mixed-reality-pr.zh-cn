---
title: 移植概述
description: 概述用于将现有应用程序引入 HoloLens 和 VR 混合现实的各种移植选项。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 移植， unity， 中间件， 引擎， UWP， Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042268"
---
# <a name="porting-overview"></a><span data-ttu-id="ff809-104">移植概述</span><span class="sxs-lookup"><span data-stu-id="ff809-104">Porting overview</span></span>

<span data-ttu-id="ff809-105">在移植或升级混合现实的现有项目时，移植过程取决于应用是使用 Unity 还是 Unreal Engine 构建的，并且面向 HoloLens (第一代) 或 HoloLens 2 或 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="ff809-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="ff809-106">此概述页包含我们针对每个平台和设备的当前建议 - 请务必返回查看，因为这些流程始终在变化。</span><span class="sxs-lookup"><span data-stu-id="ff809-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="ff809-107">首先，根据 [Unity](#unity) 和 [Unreal](#unreal) 建议设置项目目标，然后遵循一个或多个移植方案：</span><span class="sxs-lookup"><span data-stu-id="ff809-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="ff809-108">HoloLens (第一代) HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ff809-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="ff809-109">沉浸式 VR 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="ff809-109">Immersive VR headsets</span></span>](#immersive-vr-headsets)
- [<span data-ttu-id="ff809-110">2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="ff809-110">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="ff809-111">建议的项目目标</span><span class="sxs-lookup"><span data-stu-id="ff809-111">Recommended project targets</span></span>

<span data-ttu-id="ff809-112">无论将应用移植到另一个目标设备，都保持项目最新状态非常重要。</span><span class="sxs-lookup"><span data-stu-id="ff809-112">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="ff809-113">请参阅下面列出的基于引擎的资源，了解我们当前的建议。</span><span class="sxs-lookup"><span data-stu-id="ff809-113">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="ff809-114">Unity</span><span class="sxs-lookup"><span data-stu-id="ff809-114">Unity</span></span>

<span data-ttu-id="ff809-115">有关 [建议的 Unity 和](../unity/choosing-unity-version.md) MRTK 版本最新指南，请参阅选择 Unity 版本页。</span><span class="sxs-lookup"><span data-stu-id="ff809-115">See the [Choosing a Unity version](../unity/choosing-unity-version.md) page for up-to-date guidance on the recommended Unity and MRTK versions.</span></span>

### <a name="unreal"></a><span data-ttu-id="ff809-116">Unreal</span><span class="sxs-lookup"><span data-stu-id="ff809-116">Unreal</span></span>

<span data-ttu-id="ff809-117">有关 [建议的 Unreal](../unreal/unreal-project-setup.md) 和 MRTK 版本最新指南，请参阅设置 Unreal 项目页。</span><span class="sxs-lookup"><span data-stu-id="ff809-117">See the [Setting up your Unreal project](../unreal/unreal-project-setup.md) page for up-to-date guidance on the recommended Unreal and MRTK versions.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="ff809-118">移植方案</span><span class="sxs-lookup"><span data-stu-id="ff809-118">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="ff809-119">HoloLens (第一代) Unity 应用HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ff809-119">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="ff809-120">如果要移植到 HoloLens 2 的现有 HoloLens (第一代) Unity 应用程序，请按照 [HoloLens](./porting-hl1-hl2.md)移植文章中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ff809-120">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="immersive-vr-headsets"></a><span data-ttu-id="ff809-121">沉浸式 VR 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="ff809-121">Immersive VR headsets</span></span>

<span data-ttu-id="ff809-122">如果为其他 VR 设备生成了内容，则需要重定任何供应商特定的 VR SDK 和可能的输入映射 API。</span><span class="sxs-lookup"><span data-stu-id="ff809-122">If you've built content for other VR devices, you'll need to retarget any vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="ff809-123">可以在沉浸式应用移植指南 中查找 Unity 和 Unreal 移植 [方案的信息](porting-guides.md)。</span><span class="sxs-lookup"><span data-stu-id="ff809-123">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

<span data-ttu-id="ff809-124">有关要针对头戴显示设备更新的 SteamVR Windows Mixed Reality，请参阅 [我们的 SteamVR 更新指南](updating-your-steamvr-application-for-windows-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="ff809-124">For SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="ff809-125">2D 通用 Windows 应用程序</span><span class="sxs-lookup"><span data-stu-id="ff809-125">2D Universal Windows applications</span></span>

<span data-ttu-id="ff809-126">如果要移植到 Windows Mixed Reality 沉浸式头戴显示设备或 HoloLens 的现有 2D UWP 应用，请按照移植 [2D UWP](building-2d-apps.md) 应用了解 Windows Mixed Reality 说明。</span><span class="sxs-lookup"><span data-stu-id="ff809-126">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>