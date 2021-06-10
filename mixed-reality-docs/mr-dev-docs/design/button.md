---
title: Button
description: 了解如何使用按钮触发立即操作，这是一个混合现实的基础组件。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合现实，控件，交互，ui，ux，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，按钮
ms.openlocfilehash: ddad8b23950bddd03dd4024497c212d1cc950fb0
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600366"
---
# <a name="button"></a><span data-ttu-id="e8cea-104">Button</span><span class="sxs-lookup"><span data-stu-id="e8cea-104">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="e8cea-106">利用按钮，用户可以在混合现实体验中触发即时操作。</span><span class="sxs-lookup"><span data-stu-id="e8cea-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="e8cea-107">HoloLens 2 中的按钮具有视觉提示和实用，可帮助用户提高交互置信度。</span><span class="sxs-lookup"><span data-stu-id="e8cea-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="e8cea-108">![显示了接近光效果的按钮](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="e8cea-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="e8cea-109">**邻近感应**</span><span class="sxs-lookup"><span data-stu-id="e8cea-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e8cea-110">![所选的具有焦点突出显示效果的按钮](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="e8cea-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="e8cea-111">**焦点突出显示**</span><span class="sxs-lookup"><span data-stu-id="e8cea-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="e8cea-112">![所显示的压缩箱效果按下的按钮](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="e8cea-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="e8cea-113">**压缩箱**</span><span class="sxs-lookup"><span data-stu-id="e8cea-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e8cea-114">![所示的触发脉冲效果按下的按钮](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="e8cea-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="e8cea-115">**触发暂停**</span><span class="sxs-lookup"><span data-stu-id="e8cea-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="e8cea-116">MRTK (混合现实工具包) 适用于 Unity</span><span class="sxs-lookup"><span data-stu-id="e8cea-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="e8cea-117">**[MRTK For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供各种类型的按钮 prototyping，包括 hololens 2 和 hololens (第一代) 的 shell 样式按钮。</span><span class="sxs-lookup"><span data-stu-id="e8cea-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="e8cea-118">HoloLens 2 按钮 prefab 包含多个详细实用，有助于提高用户置信度：</span><span class="sxs-lookup"><span data-stu-id="e8cea-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="e8cea-119">基于邻近性的突出显示</span><span class="sxs-lookup"><span data-stu-id="e8cea-119">Proximity-based highlight</span></span>
* <span data-ttu-id="e8cea-120">压缩前端固定架</span><span class="sxs-lookup"><span data-stu-id="e8cea-120">Compressing front cage</span></span>
* <span data-ttu-id="e8cea-121">对触发器的脉冲效果。</span><span class="sxs-lookup"><span data-stu-id="e8cea-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="e8cea-122">有关更多说明和自定义示例，请查看 [MRTK-按钮](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 。</span><span class="sxs-lookup"><span data-stu-id="e8cea-122">Check out the [MRTK - Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="e8cea-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8cea-123">See also</span></span>

* [<span data-ttu-id="e8cea-124">光标</span><span class="sxs-lookup"><span data-stu-id="e8cea-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e8cea-125">手部射线</span><span class="sxs-lookup"><span data-stu-id="e8cea-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="e8cea-126">Button</span><span class="sxs-lookup"><span data-stu-id="e8cea-126">Button</span></span>](button.md)
* [<span data-ttu-id="e8cea-127">可交互对象</span><span class="sxs-lookup"><span data-stu-id="e8cea-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e8cea-128">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="e8cea-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e8cea-129">操作</span><span class="sxs-lookup"><span data-stu-id="e8cea-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e8cea-130">手动菜单</span><span class="sxs-lookup"><span data-stu-id="e8cea-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="e8cea-131">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="e8cea-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="e8cea-132">对象集合</span><span class="sxs-lookup"><span data-stu-id="e8cea-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e8cea-133">语音命令</span><span class="sxs-lookup"><span data-stu-id="e8cea-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="e8cea-134">键盘</span><span class="sxs-lookup"><span data-stu-id="e8cea-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="e8cea-135">工具提示</span><span class="sxs-lookup"><span data-stu-id="e8cea-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="e8cea-136">平板</span><span class="sxs-lookup"><span data-stu-id="e8cea-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="e8cea-137">滑块</span><span class="sxs-lookup"><span data-stu-id="e8cea-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="e8cea-138">着色器</span><span class="sxs-lookup"><span data-stu-id="e8cea-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="e8cea-139">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="e8cea-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e8cea-140">显示进度</span><span class="sxs-lookup"><span data-stu-id="e8cea-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="e8cea-141">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="e8cea-141">Surface magnetism</span></span>](surface-magnetism.md)