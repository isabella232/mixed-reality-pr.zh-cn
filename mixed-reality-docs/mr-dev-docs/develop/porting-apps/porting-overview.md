---
title: 移植概述
description: 概述使现有应用程序成为混合现实的各种移植选项。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 移植，unity，中间件，引擎，UWP，Win32
ms.openlocfilehash: d8cbb62500a81a29a00f4d32eaed0c2df3f5149d
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612831"
---
# <a name="porting-overview"></a><span data-ttu-id="75a8f-104">移植概述</span><span class="sxs-lookup"><span data-stu-id="75a8f-104">Porting overview</span></span>

<span data-ttu-id="75a8f-105">当涉及到迁移或升级现有项目以满足混合现实的需要时，移植旅程取决于你的应用程序是通过 Unity 还是 Unreal 引擎生成的，并面向 HoloLens (第一代) 或 HoloLens 2 或 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="75a8f-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="75a8f-106">此概述页面包含我们针对每个平台和设备的当前建议-请务必检查，因为这些过程始终会更改。</span><span class="sxs-lookup"><span data-stu-id="75a8f-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="75a8f-107">首先，根据我们的 [Unity](#unity) 和 [Unreal](#unreal) 建议设置项目目标，然后执行一个或多个移植方案：</span><span class="sxs-lookup"><span data-stu-id="75a8f-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="75a8f-108">HoloLens (第一代) 到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="75a8f-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="75a8f-109">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="75a8f-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="75a8f-110">SteamVR 应用</span><span class="sxs-lookup"><span data-stu-id="75a8f-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="75a8f-111">2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="75a8f-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="75a8f-112">推荐的项目目标</span><span class="sxs-lookup"><span data-stu-id="75a8f-112">Recommended project targets</span></span>

<span data-ttu-id="75a8f-113">无论你将应用程序移植到另一台目标设备，都要使你的项目保持最新状态，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="75a8f-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="75a8f-114">有关我们当前的建议，请参阅下面列出的基于引擎的资源。</span><span class="sxs-lookup"><span data-stu-id="75a8f-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="75a8f-115">Unity</span><span class="sxs-lookup"><span data-stu-id="75a8f-115">Unity</span></span>

<span data-ttu-id="75a8f-116">我们当前对混合现实的 Unity 开发建议是 **使用旧 XR 包的 unity 2019 LTS**。</span><span class="sxs-lookup"><span data-stu-id="75a8f-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="75a8f-117">如果你的项目使用混合现实工具包，请仔细检查是否正在使用最新版本，即当前为 **MRTK 2.5**。</span><span class="sxs-lookup"><span data-stu-id="75a8f-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="75a8f-118">尽管此版本的 Unity 提供了 XR SDK，但 Azure 空间锚不与此安装程序兼容。</span><span class="sxs-lookup"><span data-stu-id="75a8f-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="75a8f-119">将使用适用于 Unity 的 Azure 空间定位包的未来版本更新此建议。</span><span class="sxs-lookup"><span data-stu-id="75a8f-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span> 
> 
> * <span data-ttu-id="75a8f-120">如果不需要 Azure 空间锚，可以 [配置适用于 XR 的 Unity 项目](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) 并 [开始 MRTK 和 XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html)。</span><span class="sxs-lookup"><span data-stu-id="75a8f-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).</span></span>
> 
> * <span data-ttu-id="75a8f-121">如果你当前使用的是项目中的 XR SDK，并且想要使用 Azure 空间锚，请卸载 XR SDK，并重新安装旧版 XR 包以恢复你的项目设置。</span><span class="sxs-lookup"><span data-stu-id="75a8f-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>


### <a name="unreal"></a><span data-ttu-id="75a8f-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="75a8f-122">Unreal</span></span> 

<span data-ttu-id="75a8f-123">我们当前对混合现实的 Unreal 开发建议是 **Unreal 引擎 4.26**。</span><span class="sxs-lookup"><span data-stu-id="75a8f-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="75a8f-124">如果你的项目使用混合现实工具包 UX 工具，请确保使用最新版本，该版本目前为 **UXT 0.10**。</span><span class="sxs-lookup"><span data-stu-id="75a8f-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="75a8f-125">移植方案</span><span class="sxs-lookup"><span data-stu-id="75a8f-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="75a8f-126">HoloLens (第一代) Unity 应用到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="75a8f-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="75a8f-127">如果你有一个现有的 HoloLens (第一代) Unity 应用程序，你想要将其移植到 HoloLens 2，请按照 [HoloLens 移植一文](../unity/mrtk-porting-guide.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="75a8f-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](../unity/mrtk-porting-guide.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="75a8f-128">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="75a8f-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="75a8f-129">如果为其他设备（如 Oculus Rift 或 HP 回音 G2）生成了内容，则需要重定特定于供应商的 VR Sdk 和可能的输入映射 Api。</span><span class="sxs-lookup"><span data-stu-id="75a8f-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="75a8f-130">可以在我们的 [沉浸式应用移植指南](porting-guides.md)中查找 Unity 和 Unreal 移植方案的相关信息。</span><span class="sxs-lookup"><span data-stu-id="75a8f-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="75a8f-131">SteamVR 应用程序</span><span class="sxs-lookup"><span data-stu-id="75a8f-131">SteamVR applications</span></span>

<span data-ttu-id="75a8f-132">对于要为 Windows Mixed Reality 耳机更新的任何 SteamVR 体验，请参阅我们的 [SteamVR 更新指南](updating-your-steamvr-application-for-windows-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="75a8f-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="75a8f-133">2D 通用 Windows 应用程序</span><span class="sxs-lookup"><span data-stu-id="75a8f-133">2D Universal Windows applications</span></span>

<span data-ttu-id="75a8f-134">如果你想要将现有的 2D UWP 应用程序移植到 Windows Mixed Reality 沉浸式耳机或 HoloLens，请遵循我们 [的移植 2D uwp apps For Windows Mixed reality](building-2d-apps.md) 说明。</span><span class="sxs-lookup"><span data-stu-id="75a8f-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>

