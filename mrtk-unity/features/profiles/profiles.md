---
title: 配置文件
description: MRTK 中的文档配置文件
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，配置文件，
ms.openlocfilehash: 785d402e924a534627dfd1d742d2019d9ce9dd5a
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908240"
---
# <a name="profiles"></a><span data-ttu-id="29600-104">配置文件</span><span class="sxs-lookup"><span data-stu-id="29600-104">Profiles</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

<span data-ttu-id="29600-105">配置 MRTK 的主要方法之一是通过基础包中提供的配置文件。</span><span class="sxs-lookup"><span data-stu-id="29600-105">One of the main ways that the MRTK is configured is through the profiles available in the foundation package.</span></span> <span data-ttu-id="29600-106">[`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)场景中的主对象将具有活动配置文件，这是一个 ScriptableObject。</span><span class="sxs-lookup"><span data-stu-id="29600-106">The main [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object in a scene will have the active profile, which is a ScriptableObject.</span></span> <span data-ttu-id="29600-107">顶级 MRTK 配置文件包含主要核心系统每个核心的子配置文件数据，其中每个核心系统都设计为配置其对应子系统的行为。</span><span class="sxs-lookup"><span data-stu-id="29600-107">The top level MRTK Configuration Profile contains sub-profile data for each core of the primary core systems, each of which are designed to configure the behavior of their corresponding subsystems.</span></span> <span data-ttu-id="29600-108">此外，这些子配置文件也是 ScriptableObjects 的，因此可以在其下包含一个级别的其他配置文件对象的引用。</span><span class="sxs-lookup"><span data-stu-id="29600-108">Furthermore, these sub-profiles are also ScriptableObjects and thus can contain references to other profile objects one level below them.</span></span> <span data-ttu-id="29600-109">实质上是一个完整的连接配置文件树，它们构成了有关如何初始化 MRTK 子系统和功能的配置信息。</span><span class="sxs-lookup"><span data-stu-id="29600-109">There is essentially an entire tree of connected profiles that make up the configuration information for how to initialize the MRTK subsystems and features.</span></span>

<span data-ttu-id="29600-110">例如，输入系统的行为由输入系统配置文件控制，如 `DefaultMixedRealityInputSystemProfile` (资产/MRTK/SDK/配置文件) 。</span><span class="sxs-lookup"><span data-stu-id="29600-110">For example, the input system's behavior is governed by an input system profile, like the `DefaultMixedRealityInputSystemProfile` (Assets/MRTK/SDK/Profiles).</span></span>

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<span data-ttu-id="29600-111"><sup>分析检查器</sup></span><span class="sxs-lookup"><span data-stu-id="29600-111"><sup>Profile Inspector</sup></span></span>

## <a name="background"></a><span data-ttu-id="29600-112">背景</span><span class="sxs-lookup"><span data-stu-id="29600-112">Background</span></span>

<span data-ttu-id="29600-113">配置文件主要用于支持跨多个设备的特定方案，这些设备通过数据提供程序进行处理。</span><span class="sxs-lookup"><span data-stu-id="29600-113">Profiles are mainly intended to support specific scenarios across multiple devices, which are handled via the data providers.</span></span> <span data-ttu-id="29600-114">通过这种方式，可以将应用设计为设备 agnosticly，并让 MRTK 和配置文件的数据提供程序处理跨平台支持。</span><span class="sxs-lookup"><span data-stu-id="29600-114">This way, an app can be designed as device-agnosticly as possible and let the MRTK and the profile's data providers handle cross-platform support.</span></span>

<span data-ttu-id="29600-115">还会围绕特定设备的输入功能构建一些配置文件，例如，默认为 GGV-样式交互的 HoloLens 1 配置文件。</span><span class="sxs-lookup"><span data-stu-id="29600-115">There are also profiles built around the input features of specific devices, such as the HoloLens 1 profile which defaults to GGV-style interactions.</span></span>

## <a name="xr-sdk"></a><span data-ttu-id="29600-116">XR SDK</span><span class="sxs-lookup"><span data-stu-id="29600-116">XR SDK</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="29600-117">使用所有默认的 MRTK 配置文件，这些配置文件都是跨 Unity 的 XR 管道配置的。</span><span class="sxs-lookup"><span data-stu-id="29600-117">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="29600-118">以前的 "DefaultOpenXRConfigurationProfile" 和 "DefaultXRSDKConfigurationProfile" 现在标记为已过时。</span><span class="sxs-lookup"><span data-stu-id="29600-118">The previous "DefaultOpenXRConfigurationProfile" and "DefaultXRSDKConfigurationProfile" are now labeled obsolete.</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="29600-119">目前提供了两个配置文件用于 XR SDK `DefaultXRSDKConfigurationProfile` 和 `DefaultHoloLens2XRSDKConfigurationProfile` 。</span><span class="sxs-lookup"><span data-stu-id="29600-119">Currently, there are two profiles provided for XR SDK, `DefaultXRSDKConfigurationProfile` and `DefaultHoloLens2XRSDKConfigurationProfile`.</span></span> <span data-ttu-id="29600-120">因此，并不是所有的示例场景都受到完全支持，因为存在场景和方案特定的配置。</span><span class="sxs-lookup"><span data-stu-id="29600-120">As a result, not all samples scenes are fully supported due to scene- and scenario-specific configurations.</span></span> <span data-ttu-id="29600-121">使用和的任何 `DefaultMixedRealityToolkitConfigurationProfile` 样本 `DefaultHoloLens2ConfigurationProfile` _都可以_ 交换到其对应的 XR SDK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="29600-121">Any samples that use `DefaultMixedRealityToolkitConfigurationProfile` and `DefaultHoloLens2ConfigurationProfile` _can_ be swapped over to their corresponding XR SDK profiles.</span></span> <span data-ttu-id="29600-122">如果将 OpenXR 与 XR SDK 配合使用，请改用 `DefaultOpenXRConfigurationProfile` 。</span><span class="sxs-lookup"><span data-stu-id="29600-122">If you're using OpenXR with XR SDK, use the `DefaultOpenXRConfigurationProfile` instead.</span></span>

<span data-ttu-id="29600-123">还需要执行其他工作来简化配置并支持所有的示例场景，同时可以并行配置旧的 XR 和 XR SDK。</span><span class="sxs-lookup"><span data-stu-id="29600-123">Additional work is being undertaken to ease configuration and support all sample scenes, allowing for both legacy XR and XR SDK to be configured side-by-side.</span></span> <span data-ttu-id="29600-124">请参阅问题 [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) 跟踪。</span><span class="sxs-lookup"><span data-stu-id="29600-124">See issue [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) for tracking.</span></span>
::: moniker-end

<span data-ttu-id="29600-125">有关在旧 XR 和 XR SDK 之间转换配置文件的详细信息，请参阅为 [XR SDK 管道配置 MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) 。</span><span class="sxs-lookup"><span data-stu-id="29600-125">See [Configuring MRTK for the XR SDK pipeline](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) for more information on converting profiles between legacy XR and XR SDK.</span></span>

## <a name="default-profile"></a><span data-ttu-id="29600-126">默认配置文件</span><span class="sxs-lookup"><span data-stu-id="29600-126">Default profile</span></span>

<span data-ttu-id="29600-127">MRTK 提供了一组默认配置文件，涵盖了 MRTK 支持的大多数平台和方案。</span><span class="sxs-lookup"><span data-stu-id="29600-127">The MRTK provides a set of default profiles which cover most platforms and scenarios that the MRTK supports.</span></span> <span data-ttu-id="29600-128">例如，当你选择 " `DefaultMixedRealityToolkitConfigurationProfile` (资产/MRTK/SDK/配置文件" 时) 你将能够在 "VR (OpenVR、WMR) 和 HoloLens (1" 和 "2) 上尝试方案。</span><span class="sxs-lookup"><span data-stu-id="29600-128">For example, when you select the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) you will be able to try out scenarios on VR (OpenVR, WMR) and HoloLens (1 and 2).</span></span>

<span data-ttu-id="29600-129">请注意，由于这是一个常规的使用配置文件，因此不会针对任何特定用例进行优化。</span><span class="sxs-lookup"><span data-stu-id="29600-129">Note that because this is a general use profile, it's not optimized for any particular use case.</span></span> <span data-ttu-id="29600-130">如果希望具有更适合其他平台的高性能/特定设置，请参阅下面的其他配置文件，这些配置文件在各自的平台上稍微调整更好。</span><span class="sxs-lookup"><span data-stu-id="29600-130">If you want to have more performant/specific settings that are better on other platforms, see the other profiles below, which are slightly tweaked to be better on their respective platforms.</span></span>

## <a name="hololens-2-profile"></a><span data-ttu-id="29600-131">HoloLens 2 配置文件</span><span class="sxs-lookup"><span data-stu-id="29600-131">HoloLens 2 profile</span></span>

<span data-ttu-id="29600-132">MRTK 还提供了一个默认配置文件，该配置文件在 HoloLens 2： `DefaultHoloLens2ConfigurationProfile` (资产/MRTK/SDK/profile/HoloLens2) 上经过优化，可用于部署和测试。</span><span class="sxs-lookup"><span data-stu-id="29600-132">The MRTK also provides a default profile that is optimized for deployment and testing on the HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2).</span></span>

<span data-ttu-id="29600-133">当系统提示选择 MixedRealityToolkit 对象的配置文件时，请使用此配置文件而不是默认的所选配置文件。</span><span class="sxs-lookup"><span data-stu-id="29600-133">When prompted to choose a profile for the MixedRealityToolkit object, use this profile instead of the default selected profile.</span></span>

<span data-ttu-id="29600-134">HoloLens2 配置文件与默认配置文件之间的主要区别是：</span><span class="sxs-lookup"><span data-stu-id="29600-134">The key differences between the HoloLens2 profile and the Default Profile are:</span></span>

<span data-ttu-id="29600-135">**禁用** 的功能：</span><span class="sxs-lookup"><span data-stu-id="29600-135">**Disabled** features:</span></span>

- [<span data-ttu-id="29600-136">边界系统</span><span class="sxs-lookup"><span data-stu-id="29600-136">Boundary system</span></span>](../boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="29600-137">传送系统</span><span class="sxs-lookup"><span data-stu-id="29600-137">Teleport system</span></span>](../teleport-system/teleport-system.md)
- [<span data-ttu-id="29600-138">空间感知系统</span><span class="sxs-lookup"><span data-stu-id="29600-138">Spatial awareness system</span></span>](../spatial-awareness/spatial-awareness-getting-started.md)
- <span data-ttu-id="29600-139">由于性能开销) ，[手动网格可视化](../input/hand-tracking.md) (</span><span class="sxs-lookup"><span data-stu-id="29600-139">[Hand mesh visualization](../input/hand-tracking.md) (due to performance overhead)</span></span>

<span data-ttu-id="29600-140">**已启用** 的系统：</span><span class="sxs-lookup"><span data-stu-id="29600-140">**Enabled** systems:</span></span>

- <span data-ttu-id="29600-141">[目视跟踪提供程序](../input/eye-tracking/eye-tracking-main.md)</span><span class="sxs-lookup"><span data-stu-id="29600-141">The [eye tracking provider](../input/eye-tracking/eye-tracking-main.md)</span></span>
- <span data-ttu-id="29600-142">目视输入模拟</span><span class="sxs-lookup"><span data-stu-id="29600-142">Eye input simulation</span></span>

<span data-ttu-id="29600-143">照相机配置文件设置将设置为 "匹配"，以便编辑器质量和播放器质量相同。</span><span class="sxs-lookup"><span data-stu-id="29600-143">Camera profile settings are set to match so that the editor quality and player quality are the same.</span></span> <span data-ttu-id="29600-144">这不同于默认照相机配置文件，其中不透明显示设置为较高的质量。</span><span class="sxs-lookup"><span data-stu-id="29600-144">This is different from the default camera profile where opaque displays are set to a higher quality.</span></span> <span data-ttu-id="29600-145">此更改意味着编辑器内的质量会降低，这将与设备上呈现的内容更匹配。</span><span class="sxs-lookup"><span data-stu-id="29600-145">This change means that in-editor quality will be lower, which will more closely match what will be rendered on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="29600-146">默认情况下，基于客户端反馈关闭空间感知系统-它是一种有趣的可视化效果，通常是关闭的，但通常是关闭的，以避免视觉干扰，并使其在其上出现额外性能下降。</span><span class="sxs-lookup"><span data-stu-id="29600-146">The Spatial Awareness system is turned off by default based on client feedback - it is an interesting visualization to see initially but is typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span> <span data-ttu-id="29600-147">可以按照 [此处的说明](../spatial-awareness/spatial-awareness-getting-started.md)重新启用系统。</span><span class="sxs-lookup"><span data-stu-id="29600-147">The system can be re-enabled by following the [instructions here](../spatial-awareness/spatial-awareness-getting-started.md).</span></span>
