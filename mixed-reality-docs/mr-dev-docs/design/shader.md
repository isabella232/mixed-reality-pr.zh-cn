---
title: 着色器
description: 了解混合现实工具包标准着色器如何提供各种类型的视觉效果，这些效果可用于混合现实应用中的全息影像。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合现实，控件，交互，ui，ux，着色器，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，视觉效果
ms.openlocfilehash: 046969d1d16c2bddcf5b0a392d721c291b945a94
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759118"
---
# <a name="shader"></a><span data-ttu-id="c3271-104">着色器</span><span class="sxs-lookup"><span data-stu-id="c3271-104">Shader</span></span>

![着色器](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="c3271-106">由于全息对象与真实环境中的物理对象混合在一起，因此向用户提供视觉提示非常重要。</span><span class="sxs-lookup"><span data-stu-id="c3271-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="c3271-107">混合现实工具包标准着色器提供各种类型的视觉效果，可与全息影像一起使用。</span><span class="sxs-lookup"><span data-stu-id="c3271-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="c3271-108">着色系统使用单个灵活的着色器来实现类似于 Unity 的标准着色器的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="c3271-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="c3271-109">着色器实现了 [熟知的设计系统原则](https://www.microsoft.com/design/fluent/#/) ，并在混合现实设备上保持高性能。</span><span class="sxs-lookup"><span data-stu-id="c3271-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="c3271-110">使用 MRTK (混合现实工具包的视觉效果示例) 标准着色器</span><span class="sxs-lookup"><span data-stu-id="c3271-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="c3271-111">![移动](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="c3271-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="c3271-112">**邻近感应**</span><span class="sxs-lookup"><span data-stu-id="c3271-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c3271-113">![旋转](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="c3271-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="c3271-114">**边框细**</span><span class="sxs-lookup"><span data-stu-id="c3271-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="c3271-115">MRTK for Unity 中的标准着色器</span><span class="sxs-lookup"><span data-stu-id="c3271-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="c3271-116">MRTK-标准着色器</span><span class="sxs-lookup"><span data-stu-id="c3271-116">MRTK - Standard shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/rendering/mrtk-standard-shader.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="c3271-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3271-117">See also</span></span>

* [<span data-ttu-id="c3271-118">光标</span><span class="sxs-lookup"><span data-stu-id="c3271-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c3271-119">手部射线</span><span class="sxs-lookup"><span data-stu-id="c3271-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c3271-120">Button</span><span class="sxs-lookup"><span data-stu-id="c3271-120">Button</span></span>](button.md)
* [<span data-ttu-id="c3271-121">可交互对象</span><span class="sxs-lookup"><span data-stu-id="c3271-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c3271-122">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="c3271-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c3271-123">操作</span><span class="sxs-lookup"><span data-stu-id="c3271-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c3271-124">手动菜单</span><span class="sxs-lookup"><span data-stu-id="c3271-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c3271-125">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="c3271-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c3271-126">对象集合</span><span class="sxs-lookup"><span data-stu-id="c3271-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c3271-127">语音命令</span><span class="sxs-lookup"><span data-stu-id="c3271-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c3271-128">键盘</span><span class="sxs-lookup"><span data-stu-id="c3271-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c3271-129">工具提示</span><span class="sxs-lookup"><span data-stu-id="c3271-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c3271-130">平板</span><span class="sxs-lookup"><span data-stu-id="c3271-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="c3271-131">滑块</span><span class="sxs-lookup"><span data-stu-id="c3271-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="c3271-132">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="c3271-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c3271-133">显示进度</span><span class="sxs-lookup"><span data-stu-id="c3271-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c3271-134">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="c3271-134">Surface magnetism</span></span>](surface-magnetism.md)
