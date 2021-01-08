---
title: 开始手势
description: 了解如何使用开始手势调用 HoloLens 和 Windows Mixed Reality 沉浸式耳机上的 "开始" 菜单。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实，手势，交互，设计，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，布隆
ms.openlocfilehash: 9e29d483375db103cebc30be9117e40899a9f81f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009427"
---
# <a name="start-gesture"></a><span data-ttu-id="31367-104">开始手势</span><span class="sxs-lookup"><span data-stu-id="31367-104">Start gesture</span></span>

<span data-ttu-id="31367-105">开始手势是用于调用 "开始" 菜单的笔势。</span><span class="sxs-lookup"><span data-stu-id="31367-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="31367-106">它相当于按键盘上的 Windows 键、Xbox 控制器上的 Xbox 按钮或沉浸式头戴移动设备上的 Windows 按钮。</span><span class="sxs-lookup"><span data-stu-id="31367-106">It's the equivalent of pressing the Windows key on keyboards, the Xbox button on Xbox controllers, or the Windows button on immersive headset motion controllers.</span></span> <span data-ttu-id="31367-107">请特别注意每个混合现实设备上的保留系统笔势，以防在设计交互时出现冲突。</span><span class="sxs-lookup"><span data-stu-id="31367-107">Pay special attention to reserved system gestures on each Mixed Reality device to prevent conflicts when you're designing interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="31367-108">设备支持</span><span class="sxs-lookup"><span data-stu-id="31367-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="31367-109"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="31367-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="31367-110"><a href="../hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="31367-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="31367-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="31367-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="31367-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="31367-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="31367-113">开花</span><span class="sxs-lookup"><span data-stu-id="31367-113">Bloom</span></span></td>
        <td><span data-ttu-id="31367-114">✔️</span><span class="sxs-lookup"><span data-stu-id="31367-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="31367-115">手腕按钮</span><span class="sxs-lookup"><span data-stu-id="31367-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="31367-116">✔️</span><span class="sxs-lookup"><span data-stu-id="31367-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="31367-117">眼睛和掌上手掌</span><span class="sxs-lookup"><span data-stu-id="31367-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="31367-118">✔️</span><span class="sxs-lookup"><span data-stu-id="31367-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="31367-119">开花</span><span class="sxs-lookup"><span data-stu-id="31367-119">Bloom</span></span>

<span data-ttu-id="31367-120">我们设计为 "布隆" 以在 HoloLens (第一代) 中打开 "开始" 菜单，这是一个模拟的开花的符号手势。</span><span class="sxs-lookup"><span data-stu-id="31367-120">We designed “Bloom” to bring up the start menu in HoloLens (1st gen), which is a symbolic gesture mimicking a flower blossom.</span></span> <span data-ttu-id="31367-121">这是确保 footed 交互的独特之处，它易于使用，并且可以快速撤回。</span><span class="sxs-lookup"><span data-stu-id="31367-121">It's distinctive for sure-footed interaction, easy of use, and quick to recall.</span></span> <span data-ttu-id="31367-122">若要使用手势，请用手掌将您的手拿在一起，然后将手指向外伸展。</span><span class="sxs-lookup"><span data-stu-id="31367-122">To use the gesture, hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="31367-123">![布隆关闭](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="31367-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="31367-124">**步骤1：将手掌集中到一起**</span><span class="sxs-lookup"><span data-stu-id="31367-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="31367-125">![布隆打开](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="31367-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="31367-126">**步骤2：掌上手掌**</span><span class="sxs-lookup"><span data-stu-id="31367-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="31367-127">开始手势</span><span class="sxs-lookup"><span data-stu-id="31367-127">Start gesture</span></span>

<span data-ttu-id="31367-128">在 HoloLens 2 中，我们将布隆手势替换为虚拟手腕按钮，这对于用户来说更是 instinctual。</span><span class="sxs-lookup"><span data-stu-id="31367-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button, which is more instinctual for users.</span></span> <span data-ttu-id="31367-129">通过向用户显示手腕上的按钮，用户可以以直观的方式进行访问，并将其与他人一起使用。</span><span class="sxs-lookup"><span data-stu-id="31367-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="31367-130">![手腕按钮就绪](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="31367-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="31367-131">**步骤1：掌上以显示 "手腕" 按钮**</span><span class="sxs-lookup"><span data-stu-id="31367-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="31367-132">![手腕按钮按下](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="31367-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="31367-133">**步骤2：按 "手腕" 按钮**</span><span class="sxs-lookup"><span data-stu-id="31367-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a><span data-ttu-id="31367-134">单向开始手势</span><span class="sxs-lookup"><span data-stu-id="31367-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31367-135">对于要运行的单移交开始手势：</span><span class="sxs-lookup"><span data-stu-id="31367-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="31367-136">您必须更新到2019年11月更新 (生成 18363.1039) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="31367-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="31367-137">您的眼睛必须在设备上校准，以便目视跟踪能够正常工作。</span><span class="sxs-lookup"><span data-stu-id="31367-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="31367-138">查看 "开始" 图标时，如果看不到轨道点，则不会在设备上校准眼睛。</span><span class="sxs-lookup"><span data-stu-id="31367-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="31367-139">还可以只使用一只手。</span><span class="sxs-lookup"><span data-stu-id="31367-139">You can also use the Start gesture with only one hand.</span></span> <span data-ttu-id="31367-140">抓住掌上手掌，并查看内部手腕上的 " **开始" 图标** 。</span><span class="sxs-lookup"><span data-stu-id="31367-140">Hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="31367-141">**保持您的眼睛，同时** 将您的拇指和食指汇聚在一起。</span><span class="sxs-lookup"><span data-stu-id="31367-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="31367-142">![手腕按钮就绪](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="31367-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="31367-143">**步骤1：掌上以显示 "手腕" 按钮**</span><span class="sxs-lookup"><span data-stu-id="31367-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="31367-144">![手腕按钮挤压](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="31367-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="31367-145">**步骤2：目视看着按钮，然后捏紧**</span><span class="sxs-lookup"><span data-stu-id="31367-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="31367-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31367-146">See also</span></span>

* [<span data-ttu-id="31367-147">本能交互</span><span class="sxs-lookup"><span data-stu-id="31367-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="31367-148">眼睛-注视</span><span class="sxs-lookup"><span data-stu-id="31367-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="31367-149">语音输入</span><span class="sxs-lookup"><span data-stu-id="31367-149">Voice input</span></span>](voice-input.md)
