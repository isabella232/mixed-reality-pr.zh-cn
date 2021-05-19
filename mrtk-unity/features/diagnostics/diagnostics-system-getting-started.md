---
title: 诊断系统入门
description: 用于在 MRTK 中启用和禁用诊断的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 66d68902dd9ffa36a5b30c1130a8640d154ac5e1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144723"
---
# <a name="diagnostic-system"></a><span data-ttu-id="4b1fa-104">诊断系统</span><span class="sxs-lookup"><span data-stu-id="4b1fa-104">Diagnostic system</span></span>

<span data-ttu-id="4b1fa-105">混合现实工具包诊断系统提供在应用程序中运行的诊断工具，以启用对应用程序问题的分析。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="4b1fa-106">诊断系统的第一个版本包含 [视觉探查器](using-visual-profiler.md) ，以允许在使用应用程序时分析性能问题。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="4b1fa-107">入门</span><span class="sxs-lookup"><span data-stu-id="4b1fa-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b1fa-108">**_强烈_** 建议在整个产品开发周期中启用诊断系统，并在生成和发布最终版本之前禁用该系统。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="4b1fa-109">开始使用诊断系统需要执行两个重要步骤。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="4b1fa-110">[启用](#enable-diagnostics) 诊断系统</span><span class="sxs-lookup"><span data-stu-id="4b1fa-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="4b1fa-111">[配置](#configure-diagnostic-options) 诊断选项</span><span class="sxs-lookup"><span data-stu-id="4b1fa-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="4b1fa-112">启用诊断</span><span class="sxs-lookup"><span data-stu-id="4b1fa-112">Enable diagnostics</span></span>

<span data-ttu-id="4b1fa-113">诊断系统由 MixedRealityToolkit 对象管理 (或另一个 [服务注册](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 器组件) 管理。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="4b1fa-114">以下步骤假定使用 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="4b1fa-115">其他服务注册机构所需的步骤可能不同。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="4b1fa-116">选择场景层次结构中的 MixedRealityToolkit 对象。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 配置场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="4b1fa-118">将检查器面板导航到 "诊断系统" 部分，并选中 "启用"</span><span class="sxs-lookup"><span data-stu-id="4b1fa-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="4b1fa-119">选择诊断系统实现</span><span class="sxs-lookup"><span data-stu-id="4b1fa-119">Select the Diagnostics System implementation</span></span>

    ![选择诊断系统实现](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="4b1fa-121">默认配置文件 `DefaultMixedRealityToolkitConfigurationProfile` (资产/MRTK/SDK/配置文件) 的用户会将该诊断系统预配置为使用该 [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) 对象。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="4b1fa-122">配置诊断选项</span><span class="sxs-lookup"><span data-stu-id="4b1fa-122">Configure diagnostic options</span></span>

<span data-ttu-id="4b1fa-123">诊断系统使用配置文件来指定要显示的组件并配置其设置。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="4b1fa-124">有关可用组件设置的详细信息，请参阅 [配置诊断系统](configuring-diagnostics.md) 。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b1fa-125">虽然可以在开发应用程序时使用 Unity 的播放模式，而无需生成和部署步骤，但使用在目标硬件和平台上运行的已编译应用程序评估诊断系统结果非常重要。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="4b1fa-126">从编辑器中运行时，性能诊断（如 [Visual Profiler）](using-visual-profiler.md)可能无法准确反映实际的应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="4b1fa-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b1fa-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b1fa-127">See also</span></span>

- [<span data-ttu-id="4b1fa-128">诊断 API 文档</span><span class="sxs-lookup"><span data-stu-id="4b1fa-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="4b1fa-129">配置诊断系统</span><span class="sxs-lookup"><span data-stu-id="4b1fa-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="4b1fa-130">使用 Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="4b1fa-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)
