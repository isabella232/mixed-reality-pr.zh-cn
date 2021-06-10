---
title: 停留
description: 停留交互
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: 停留，Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647751"
---
# <a name="dwell"></a><span data-ttu-id="de51b-104">停留</span><span class="sxs-lookup"><span data-stu-id="de51b-104">Dwell</span></span>

![停留英雄](../images/dwell/MRTK_UX_Dwell.png)

<span data-ttu-id="de51b-106">打印头和停留在某个人正忙于处理其他任务的情况下非常有用。</span><span class="sxs-lookup"><span data-stu-id="de51b-106">Head-gaze and dwell are great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="de51b-107">当语音不是100% 可靠或由于环境或社交限制而可用时，此功能也很有用。</span><span class="sxs-lookup"><span data-stu-id="de51b-107">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="de51b-108">MRTK 的停留示例演示了具有可配置的响应时间和视觉反馈的不同类型的 UI 组件。</span><span class="sxs-lookup"><span data-stu-id="de51b-108">MRTK's dwell examples demonstrate different types of UI components with configurable response time and visual feedback.</span></span>

<span data-ttu-id="de51b-109">有关设计建议，请参阅 [打印头和停留指导原则](/windows/mixed-reality/design/gaze-and-dwell-head) 。</span><span class="sxs-lookup"><span data-stu-id="de51b-109">Please see [Head-gaze and dwell guideline](/windows/mixed-reality/design/gaze-and-dwell-head) page for the design recommendations.</span></span>

## <a name="dwell-scripts"></a><span data-ttu-id="de51b-110">停留脚本</span><span class="sxs-lookup"><span data-stu-id="de51b-110">Dwell scripts</span></span>

- <span data-ttu-id="de51b-111">**DwellHandler**：将停留模态添加到 UI 目标。</span><span class="sxs-lookup"><span data-stu-id="de51b-111">**DwellHandler**: Adds a dwell modality to the UI target.</span></span>
- <span data-ttu-id="de51b-112">**DwellStateType**：停留处理程序的状态。</span><span class="sxs-lookup"><span data-stu-id="de51b-112">**DwellStateType**: The states of the dwell handler.</span></span>
- <span data-ttu-id="de51b-113">**DwellUnityEvent**：停留事件的 Unity 事件。</span><span class="sxs-lookup"><span data-stu-id="de51b-113">**DwellUnityEvent**: Unity event for a dwell event.</span></span> <span data-ttu-id="de51b-114">包含指针引用。</span><span class="sxs-lookup"><span data-stu-id="de51b-114">Contains the pointer reference.</span></span>
- <span data-ttu-id="de51b-115">**BaseDwellPressableButton** ：触发 PressableButtonHoloLens2 prototyping 中的 OnClick () 事件的脚本 `Interactable` 。</span><span class="sxs-lookup"><span data-stu-id="de51b-115">**BaseDwellPressableButton.cs** : A script that triggers OnClick() event in `Interactable` of PressableButtonHoloLens2 prefabs.</span></span>
- <span data-ttu-id="de51b-116">**ToggleDwellPressableButton** ：此脚本 `_BorderWidth` `dwellVisualImage` 使用 MRTK 标准着色器修改的属性。</span><span class="sxs-lookup"><span data-stu-id="de51b-116">**ToggleDwellPressableButton.cs** : This script modifies `_BorderWidth` property of the `dwellVisualImage` which is using MRTK Standard Shader.</span></span>

## <a name="dwell-profiles"></a><span data-ttu-id="de51b-117">停留配置文件</span><span class="sxs-lookup"><span data-stu-id="de51b-117">Dwell profiles</span></span>
<span data-ttu-id="de51b-118">停留 **处理程序** 使用停留配置文件来配置各种阈值。</span><span class="sxs-lookup"><span data-stu-id="de51b-118">Dwell profiles are used by the **Dwell Handler** to configure the various thresholds.</span></span>
- <span data-ttu-id="de51b-119">**ButtonDwellProfile**</span><span class="sxs-lookup"><span data-stu-id="de51b-119">**ButtonDwellProfile.asset**</span></span>
- <span data-ttu-id="de51b-120">**InstandDwellProfile**</span><span class="sxs-lookup"><span data-stu-id="de51b-120">**InstandDwellProfile.asset**</span></span>
- <span data-ttu-id="de51b-121">**DwellProfileWithDecay**</span><span class="sxs-lookup"><span data-stu-id="de51b-121">**DwellProfileWithDecay.asset**</span></span>

## <a name="prefabs"></a><span data-ttu-id="de51b-122">Prototyping</span><span class="sxs-lookup"><span data-stu-id="de51b-122">Prefabs</span></span>

<span data-ttu-id="de51b-123">这些 prototyping 是 HoloLens 2 样式 pressable 按钮 prototyping 的变体，它具有支持停留交互的附加组件。</span><span class="sxs-lookup"><span data-stu-id="de51b-123">These prefabs are variants of the HoloLens 2 style pressable button prefabs that have additional components to support dwell interactions.</span></span>

- <span data-ttu-id="de51b-124">**PressableButtonHoloLens2_Dwell. prefab**</span><span class="sxs-lookup"><span data-stu-id="de51b-124">**PressableButtonHoloLens2_Dwell.prefab**</span></span>
- <span data-ttu-id="de51b-125">**PressableButtonHoloLens2_32x96_Dwell. prefab**</span><span class="sxs-lookup"><span data-stu-id="de51b-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span></span>
- <span data-ttu-id="de51b-126">**PressableButtonHoloLens2ToggleDwell. prefab**</span><span class="sxs-lookup"><span data-stu-id="de51b-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span></span>
- <span data-ttu-id="de51b-127">**PressableButtonHoloLens2Toggle_32x96_Dwell. prefab**</span><span class="sxs-lookup"><span data-stu-id="de51b-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span></span>

<span data-ttu-id="de51b-128">这些 prototyping 具有附加的 backplate 组件 **QuadDwellVisual** ，用于可视化停留输入状态。</span><span class="sxs-lookup"><span data-stu-id="de51b-128">These prefabs have an additional backplate component **QuadDwellVisual** to visualize the dwell input state.</span></span> <span data-ttu-id="de51b-129">已分配 **HolographicBackPlateDwellVisual** 材料。</span><span class="sxs-lookup"><span data-stu-id="de51b-129">It has **HolographicBackPlateDwellVisual.mat** material assigned.</span></span> <span data-ttu-id="de51b-130">**ToggleDwellPressableButton** 将更新 MRTK 标准着色器的 **_BorderWidth** 属性，以可视化停留在的输入。</span><span class="sxs-lookup"><span data-stu-id="de51b-130">**ToggleDwellPressableButton.cs** updates the **_BorderWidth** property of MRTK Standard shader to visualize the dwell input.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a><span data-ttu-id="de51b-131">示例场景</span><span class="sxs-lookup"><span data-stu-id="de51b-131">Example scene</span></span>

<span data-ttu-id="de51b-132">您可以在场景中找到示例 `DwellExample` 。</span><span class="sxs-lookup"><span data-stu-id="de51b-132">You can find examples in the `DwellExample` scene.</span></span> <span data-ttu-id="de51b-133">示例场景显示了容量耗尽 UI 示例和 Unity UI 示例。</span><span class="sxs-lookup"><span data-stu-id="de51b-133">The example scene shows both volumetric UI examples and Unity UI examples.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a><span data-ttu-id="de51b-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de51b-134">See also</span></span>

- [<span data-ttu-id="de51b-135">**按钮**</span><span class="sxs-lookup"><span data-stu-id="de51b-135">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="de51b-136">**可交互**</span><span class="sxs-lookup"><span data-stu-id="de51b-136">**Interactable**</span></span>](interactable.md)
