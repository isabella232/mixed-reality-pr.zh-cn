---
title: 凝视和停留
description: " (眼/head) 注视和停留输入模型的一般概述。"
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality，注视，停留，交互，设计，眼睛跟踪，头跟踪，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: e8005551e08248a73098bd0f9c198b0919e2471a
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847345"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="97d00-104">凝视和停留</span><span class="sxs-lookup"><span data-stu-id="97d00-104">Gaze and dwell</span></span>

<span data-ttu-id="97d00-105">手拿工具和零件，手势可能是没有意义或无法实现。</span><span class="sxs-lookup"><span data-stu-id="97d00-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="97d00-106">在某些上下文中，语音命令也可能不可靠，例如在过大的情况下。</span><span class="sxs-lookup"><span data-stu-id="97d00-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="97d00-107">注视和停留提供了一种熟悉且易于掌握的机制，用于在 HoloLens 上完成工作和无人参与。</span><span class="sxs-lookup"><span data-stu-id="97d00-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="97d00-108">此外，注视和停留是一个很好的回退，这与操作环境中的干扰干扰或静默约束无关。</span><span class="sxs-lookup"><span data-stu-id="97d00-108">Additionally, gaze and dwell is a great fallback, which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="97d00-109">我们区分 _注视和停留_ 区的两个变体： [打印头和](gaze-and-dwell-head.md) 停留区， [注视眼睛和停留](gaze-and-dwell-eyes.md)区。</span><span class="sxs-lookup"><span data-stu-id="97d00-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="97d00-110">方案</span><span class="sxs-lookup"><span data-stu-id="97d00-110">Scenarios</span></span>

<span data-ttu-id="97d00-111">注视和停留在某个人的 transact-sql 与其他任务繁忙的情况下，以及因环境或社交限制而导致的语音不是100%。</span><span class="sxs-lookup"><span data-stu-id="97d00-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="97d00-112">一个很好的例子是穿戴 HoloLens 的人在修理汽车发动机时获取参考信息。</span><span class="sxs-lookup"><span data-stu-id="97d00-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="97d00-113">倚靠在发动机舱内时，他们的手拿着工具或支撑着身体。</span><span class="sxs-lookup"><span data-stu-id="97d00-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="97d00-114">车库空间很大，工具不断敲打声和嘈杂声，难以使用语音命令。</span><span class="sxs-lookup"><span data-stu-id="97d00-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="97d00-115">注视和停留允许使用 HoloLens 的人员自信地浏览其参考材料，而不会中断工作流。</span><span class="sxs-lookup"><span data-stu-id="97d00-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="97d00-116">设备支持</span><span class="sxs-lookup"><span data-stu-id="97d00-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="97d00-117"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="97d00-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="97d00-118"><a href="../hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="97d00-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="97d00-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="97d00-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="97d00-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="97d00-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="97d00-121">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="97d00-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="97d00-122">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="97d00-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="97d00-123">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="97d00-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="97d00-124">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="97d00-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="97d00-125">眼睛凝视和停留</span><span class="sxs-lookup"><span data-stu-id="97d00-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="97d00-126">❌ 不可用</span><span class="sxs-lookup"><span data-stu-id="97d00-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="97d00-127">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="97d00-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="97d00-128">❌ 不可用</span><span class="sxs-lookup"><span data-stu-id="97d00-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="97d00-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97d00-129">See also</span></span>

* [<span data-ttu-id="97d00-130">基于眼睛的交互</span><span class="sxs-lookup"><span data-stu-id="97d00-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="97d00-131">HoloLens 2 中的眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="97d00-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="97d00-132">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="97d00-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="97d00-133">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="97d00-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="97d00-134">手 - 手势</span><span class="sxs-lookup"><span data-stu-id="97d00-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="97d00-135">手 - 指向并提交</span><span class="sxs-lookup"><span data-stu-id="97d00-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="97d00-136">本能交互</span><span class="sxs-lookup"><span data-stu-id="97d00-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="97d00-137">语音输入</span><span class="sxs-lookup"><span data-stu-id="97d00-137">Voice input</span></span>](voice-input.md)
