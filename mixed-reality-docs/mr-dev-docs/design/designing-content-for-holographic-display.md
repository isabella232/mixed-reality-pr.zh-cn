---
title: 设计适用于全息显示器的内容
description: 全息显示器的设计准则和最佳实践
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 设计，全息显示，内容设计，深色主题，浅色主题，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，设计，像素
ms.openlocfilehash: ea3fbda7aff80f0878521deb433c88b16abeab19
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702633"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="012aa-104">设计适用于全息显示器的内容</span><span class="sxs-lookup"><span data-stu-id="012aa-104">Designing content for holographic display</span></span>

![Ulnar 端位置](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="012aa-106">设计全息显示器内容时，需要考虑几个元素，以便获得最佳体验。</span><span class="sxs-lookup"><span data-stu-id="012aa-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="012aa-107">下面列出了下面的一些建议，你可以在 ["颜色、光线和材料](color-light-and-materials.md) " 页面上详细了解全息版显示的特征。</span><span class="sxs-lookup"><span data-stu-id="012aa-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="012aa-108">大型表面上明亮的颜色挑战</span><span class="sxs-lookup"><span data-stu-id="012aa-108">Challenges with bright color on a large surface</span></span> 
<span data-ttu-id="012aa-109">基于用户的研究和测试各种类型的 HoloLens 体验，我们发现，在大区域显示中使用明亮的颜色可能会导致几个问题：</span><span class="sxs-lookup"><span data-stu-id="012aa-109">Based on our user research and testing on various types of HoloLens experiences, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="012aa-110">**眼睛疲劳**</span><span class="sxs-lookup"><span data-stu-id="012aa-110">**Eye fatigue**</span></span> 

<span data-ttu-id="012aa-111">由于全息显示是累加的，因此鲜艳颜色会使用更多灯光来显示全息影像。</span><span class="sxs-lookup"><span data-stu-id="012aa-111">Since holographic display is additive, bright color uses more light to display holograms.</span></span> <span data-ttu-id="012aa-112">在较大的显示区域中，颜色明亮，很容易导致用户的眼睛疲劳。</span><span class="sxs-lookup"><span data-stu-id="012aa-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="012aa-113">**手动封闭**</span><span class="sxs-lookup"><span data-stu-id="012aa-113">**Hand occlusion**</span></span> 

<span data-ttu-id="012aa-114">明亮的颜色使用户在直接与对象交互时很难看到其手。</span><span class="sxs-lookup"><span data-stu-id="012aa-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="012aa-115">由于用户无法看到其手，因此很难发现指针与目标表面之间的深度/距离。</span><span class="sxs-lookup"><span data-stu-id="012aa-115">Since the user cannot see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="012aa-116">Finger 游标有助于弥补此问题，但在明亮的表面上，它仍会有挑战性。</span><span class="sxs-lookup"><span data-stu-id="012aa-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="012aa-117">![颜色和手封闭 ](images/color_handocclusion.jpg)
 *很难看到鲜艳的彩色内容 backplate*</span><span class="sxs-lookup"><span data-stu-id="012aa-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="012aa-118">**颜色一致性**</span><span class="sxs-lookup"><span data-stu-id="012aa-118">**Color uniformity**</span></span>

<span data-ttu-id="012aa-119">由于全息显示器的特性，显示屏上的一个较亮的区域可能会变得 blotchy。</span><span class="sxs-lookup"><span data-stu-id="012aa-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="012aa-120">通过使用暗色方案，你可以最大程度地减少此问题。</span><span class="sxs-lookup"><span data-stu-id="012aa-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines"></a><span data-ttu-id="012aa-121">设计准则</span><span class="sxs-lookup"><span data-stu-id="012aa-121">Design guidelines</span></span>

<span data-ttu-id="012aa-122">**为 UI 背景使用暗色**</span><span class="sxs-lookup"><span data-stu-id="012aa-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="012aa-123">通过使用暗色方案，你可以最大程度地减少眼睛疲劳并改善直接交互的置信度。</span><span class="sxs-lookup"><span data-stu-id="012aa-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="012aa-124">![深色 UI 示例 ](images/color_dark_examples.jpg)
 *用于内容背景的深色颜色*</span><span class="sxs-lookup"><span data-stu-id="012aa-124">![Dark UI examples](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="012aa-125">**使用 semibold 或粗体字体粗细**</span><span class="sxs-lookup"><span data-stu-id="012aa-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="012aa-126">HoloLens 允许你的体验显示漂亮的高分辨率文本。</span><span class="sxs-lookup"><span data-stu-id="012aa-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="012aa-127">不过，建议您避免使用细的字体粗细，如浅色或半光，因为垂直笔划可以在小字号内抖动。</span><span class="sxs-lookup"><span data-stu-id="012aa-127">However, it is recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="012aa-128">![深色 UI ](images/color_font_examples.jpg)
 *(上面板的粗体或半粗字体粗细) 改善可读性*</span><span class="sxs-lookup"><span data-stu-id="012aa-128">![Dark UI examples](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="012aa-129">**使用 MRTK 的 HolographicBackplate 材料**</span><span class="sxs-lookup"><span data-stu-id="012aa-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="012aa-130">HolographicBackplate 材料适用于 HoloLens shell 中的几个 UI 面板。</span><span class="sxs-lookup"><span data-stu-id="012aa-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="012aa-131">其中一项功能是用户在将其相对于面板之间移动时对其显示的 iridescence 效果。</span><span class="sxs-lookup"><span data-stu-id="012aa-131">One of its features is an iridescence effect that is visible to users as they shift their position in relation to the panel.</span></span> <span data-ttu-id="012aa-132">Backplate 颜色在一系列预定义的光谱上略有变化，从而创造生动生动的动态视觉效果，而不会干扰内容的可读性。</span><span class="sxs-lookup"><span data-stu-id="012aa-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="012aa-133">此微妙的颜色转变还用于弥补任何次要颜色不规则性。</span><span class="sxs-lookup"><span data-stu-id="012aa-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="012aa-134">透明或半透明 UI backplate 的挑战</span><span class="sxs-lookup"><span data-stu-id="012aa-134">Challenges with transparent or translucent UI backplate</span></span> 
<span data-ttu-id="012aa-135">![透明 ](images/color_transparent_examples.jpg)
 *ui backplate 的* 透明 ui 示例</span><span class="sxs-lookup"><span data-stu-id="012aa-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="012aa-136">**视觉对象复杂性和辅助功能**</span><span class="sxs-lookup"><span data-stu-id="012aa-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="012aa-137">由于全息对象与物理环境混合，因此透明或半透明窗口上的内容或 UI 的可读性可能会下降。</span><span class="sxs-lookup"><span data-stu-id="012aa-137">Since holographic objects are blended with the physical environment, the legibility of the content or UI on the transparent or translucent window could be degraded.</span></span> <span data-ttu-id="012aa-138">此外，当透明全息对象重叠在一起时，这可能会使用户难以在不太深入的情况下进行交互。</span><span class="sxs-lookup"><span data-stu-id="012aa-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="012aa-139">**“性能”**</span><span class="sxs-lookup"><span data-stu-id="012aa-139">**Performance**</span></span>

<span data-ttu-id="012aa-140">若要正确呈现透明或半透明对象，必须将其与存在于后台的任何对象进行排序和混合。</span><span class="sxs-lookup"><span data-stu-id="012aa-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects which exist in the background.</span></span> <span data-ttu-id="012aa-141">透明对象的排序具有适度的 CPU 开销，混合具有相当大的 GPU 开销，因为它不允许 GPU 通过 z 剔除执行隐藏的图面 (例如</span><span class="sxs-lookup"><span data-stu-id="012aa-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it does not allow the GPU to perform hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="012aa-142">深度测试) 。</span><span class="sxs-lookup"><span data-stu-id="012aa-142">depth testing).</span></span> <span data-ttu-id="012aa-143">不允许隐藏面删除会增加需要为最终呈现的像素计算的操作的数量，从而增加对填充速率约束的压力。</span><span class="sxs-lookup"><span data-stu-id="012aa-143">Not allowing hidden surface removal increases the number of operations that need to be computed for the final rendered pixel, and thus puts more pressure on fill rate constraints.</span></span>

<span data-ttu-id="012aa-144">**LSR 技术的全息影像稳定性问题**</span><span class="sxs-lookup"><span data-stu-id="012aa-144">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="012aa-145">若要改善全息 reprojection 或全息图稳定性，应用程序可以为每个呈现的帧提交系统的深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="012aa-145">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="012aa-146">使用 reprojection 的深度缓冲区时，一个规则是，对于呈现了相应深度值的每个颜色像素，都必须将其写入深度缓冲区 (并且具有深度值的任何像素也应) 颜色值。</span><span class="sxs-lookup"><span data-stu-id="012aa-146">When using the depth buffer for reprojection one rule is that for every color pixel rendered a corresponding depth value must be written to the depth buffer (and any pixel with a depth value should also have color value).</span></span> <span data-ttu-id="012aa-147">如果未遵循以上指导原则，呈现图像中缺少有效深度信息的区域可能会 reprojected，从而产生 (通常作为类似于波形的扭曲) 出现的项目。</span><span class="sxs-lookup"><span data-stu-id="012aa-147">If the above guidance is not followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts (often visible as a wave-like distortion).</span></span>


## <a name="design-guidelines"></a><span data-ttu-id="012aa-148">设计准则</span><span class="sxs-lookup"><span data-stu-id="012aa-148">Design guidelines</span></span>
<span data-ttu-id="012aa-149">**使用不透明的 UI 背景**</span><span class="sxs-lookup"><span data-stu-id="012aa-149">**Use opaque UI background**</span></span>

<span data-ttu-id="012aa-150">默认情况下，透明或半透明对象不会写入深度以允许进行适当的混合。</span><span class="sxs-lookup"><span data-stu-id="012aa-150">By default, transparent or translucent objects do not write depth to allow for proper blending.</span></span> <span data-ttu-id="012aa-151">缓解此问题的方法包括：使用不透明对象，并确保半透明对象接近于不透明的对象 (例如，在不透明的 backplate) 前面添加半透明的按钮、强制半透明对象写入深度 (不适用于所有方案) ，或呈现仅在帧末尾提供深度值的代理对象。</span><span class="sxs-lookup"><span data-stu-id="012aa-151">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="012aa-152">MRTK 中的解决方案-Unity： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="012aa-152">Solutions within MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="012aa-153">通过使用纯和不透明的 backplate，我们可以确保可读性和交互置信度。</span><span class="sxs-lookup"><span data-stu-id="012aa-153">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="012aa-154">**最大程度地减少受影响的像素数**</span><span class="sxs-lookup"><span data-stu-id="012aa-154">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="012aa-155">如果项目必须使用透明对象，请尝试最大程度地减少受影响的像素数。</span><span class="sxs-lookup"><span data-stu-id="012aa-155">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="012aa-156">例如，如果某一对象仅在某些条件下可见 (如) 的加法发光效果），则在该对象完全不可见时禁用该对象 (而不是将附加颜色设置为黑色) 。</span><span class="sxs-lookup"><span data-stu-id="012aa-156">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it is fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="012aa-157">对于使用带有 alpha 掩码的四核创建的简单二维形状，请考虑改为使用不透明着色器来创建形状的网格表示形式。</span><span class="sxs-lookup"><span data-stu-id="012aa-157">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="012aa-158">MRTK 中的深色 UI 示例 (混合现实工具包) 适用于 Unity</span><span class="sxs-lookup"><span data-stu-id="012aa-158">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="012aa-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供了许多基于深色方案的 UI 构建基块示例。</span><span class="sxs-lookup"><span data-stu-id="012aa-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="012aa-160">邻近菜单</span><span class="sxs-lookup"><span data-stu-id="012aa-160">Near Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [<span data-ttu-id="012aa-161">对话框</span><span class="sxs-lookup"><span data-stu-id="012aa-161">Dialog</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [<span data-ttu-id="012aa-162">手动菜单</span><span class="sxs-lookup"><span data-stu-id="012aa-162">Hand Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="012aa-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="012aa-163">See also</span></span>
* [<span data-ttu-id="012aa-164">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="012aa-164">Color, light and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="012aa-165">光标</span><span class="sxs-lookup"><span data-stu-id="012aa-165">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="012aa-166">手部射线</span><span class="sxs-lookup"><span data-stu-id="012aa-166">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="012aa-167">Button</span><span class="sxs-lookup"><span data-stu-id="012aa-167">Button</span></span>](button.md)
* [<span data-ttu-id="012aa-168">可交互对象</span><span class="sxs-lookup"><span data-stu-id="012aa-168">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="012aa-169">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="012aa-169">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="012aa-170">操作</span><span class="sxs-lookup"><span data-stu-id="012aa-170">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="012aa-171">手动菜单</span><span class="sxs-lookup"><span data-stu-id="012aa-171">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="012aa-172">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="012aa-172">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="012aa-173">对象集合</span><span class="sxs-lookup"><span data-stu-id="012aa-173">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="012aa-174">语音命令</span><span class="sxs-lookup"><span data-stu-id="012aa-174">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="012aa-175">键盘</span><span class="sxs-lookup"><span data-stu-id="012aa-175">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="012aa-176">工具提示</span><span class="sxs-lookup"><span data-stu-id="012aa-176">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="012aa-177">平板</span><span class="sxs-lookup"><span data-stu-id="012aa-177">Slate</span></span>](slate.md)
* [<span data-ttu-id="012aa-178">滑块</span><span class="sxs-lookup"><span data-stu-id="012aa-178">Slider</span></span>](slider.md)
* [<span data-ttu-id="012aa-179">着色器</span><span class="sxs-lookup"><span data-stu-id="012aa-179">Shader</span></span>](shader.md)
* [<span data-ttu-id="012aa-180">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="012aa-180">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="012aa-181">显示进度</span><span class="sxs-lookup"><span data-stu-id="012aa-181">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="012aa-182">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="012aa-182">Surface magnetism</span></span>](surface-magnetism.md)
