---
title: 设计适用于全息显示器的内容
description: 了解 HoloLens 设备上全息显示的设计准则和最佳做法。
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 设计， 全息显示， 内容设计， 深色主题， 浅色主题， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包， 设计， 像素
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600316"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="a6199-104">设计适用于全息显示器的内容</span><span class="sxs-lookup"><span data-stu-id="a6199-104">Designing content for holographic display</span></span>

![Ulnar 手部位置](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="a6199-106">设计全息显示器的内容时，需要考虑几个元素，以获得最佳体验。</span><span class="sxs-lookup"><span data-stu-id="a6199-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="a6199-107">下面列出了一些建议，可以在"颜色、光线和材料"页上详细了解全息[显示器的特征。](color-light-and-materials.md)</span><span class="sxs-lookup"><span data-stu-id="a6199-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="a6199-108">大型表面上的亮色挑战</span><span class="sxs-lookup"><span data-stu-id="a6199-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="a6199-109">根据我们的 HoloLens 体验研究与测试，我们发现在大量显示器中使用亮色可能会导致多个问题：</span><span class="sxs-lookup"><span data-stu-id="a6199-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="a6199-110">**眼动**</span><span class="sxs-lookup"><span data-stu-id="a6199-110">**Eye fatigue**</span></span> 

<span data-ttu-id="a6199-111">由于全息显示是累加性的，因此具有亮色的全息影像使用更多的光。</span><span class="sxs-lookup"><span data-stu-id="a6199-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="a6199-112">显示较大区域中的亮色、纯色很容易让用户感到眼动。</span><span class="sxs-lookup"><span data-stu-id="a6199-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="a6199-113">**手部遮挡**</span><span class="sxs-lookup"><span data-stu-id="a6199-113">**Hand occlusion**</span></span> 

<span data-ttu-id="a6199-114">亮色使得用户在直接与对象交互时难以看到手部。</span><span class="sxs-lookup"><span data-stu-id="a6199-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="a6199-115">由于用户看不到手部，因此很难感知手/手指与目标图面的深度/距离。</span><span class="sxs-lookup"><span data-stu-id="a6199-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="a6199-116">手指光标有助于弥补此问题，但它在亮白色表面上仍然具有挑战性。</span><span class="sxs-lookup"><span data-stu-id="a6199-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="a6199-117">![颜色和手部遮挡 难以在亮色内容底板上 ](images/color_handocclusion.jpg)
 *看到手*</span><span class="sxs-lookup"><span data-stu-id="a6199-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="a6199-118">**颜色一致性**</span><span class="sxs-lookup"><span data-stu-id="a6199-118">**Color uniformity**</span></span>

<span data-ttu-id="a6199-119">由于全息显示器的特征，显示器上的大亮区域可能会变得浮点。</span><span class="sxs-lookup"><span data-stu-id="a6199-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="a6199-120">通过使用深色配色方案，可以最大程度地减少此问题。</span><span class="sxs-lookup"><span data-stu-id="a6199-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="a6199-121">颜色选择的设计准则</span><span class="sxs-lookup"><span data-stu-id="a6199-121">Design guidelines for color choices</span></span>

<span data-ttu-id="a6199-122">**对 UI 背景使用深色**</span><span class="sxs-lookup"><span data-stu-id="a6199-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="a6199-123">通过使用深色配色方案，可以最大程度地减少眼动，并提高直接手部交互的置信度。</span><span class="sxs-lookup"><span data-stu-id="a6199-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="a6199-124">![用于内容背景的深色颜色示例 用于内容背景 ](images/color_dark_examples.jpg)
 *的深色示例*</span><span class="sxs-lookup"><span data-stu-id="a6199-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="a6199-125">**使用半双曲或粗体字体粗细**</span><span class="sxs-lookup"><span data-stu-id="a6199-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="a6199-126">HoloLens 允许体验显示美观的高分辨率文本。</span><span class="sxs-lookup"><span data-stu-id="a6199-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="a6199-127">但是，建议避免字体粗细，如浅色或半浅，因为垂直笔划可能会以较小的字体大小抖动。</span><span class="sxs-lookup"><span data-stu-id="a6199-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="a6199-128">![在上面板中 (粗或半粗体字体粗) 提高上面板上半 (粗或半粗体字体粗细) 提高 ](images/color_font_examples.jpg)
 *可读性*</span><span class="sxs-lookup"><span data-stu-id="a6199-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="a6199-129">**使用 MRTK 的 HolographicBackplate 材料**</span><span class="sxs-lookup"><span data-stu-id="a6199-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="a6199-130">HolographicBackplate 材料应用于 HoloLens shell 中的多个 UI 面板。</span><span class="sxs-lookup"><span data-stu-id="a6199-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="a6199-131">它的一个功能是一种网格效果，当用户基于面板移动其位置时，用户可以看到该效果。</span><span class="sxs-lookup"><span data-stu-id="a6199-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="a6199-132">反板颜色在预定义的色系中以小微方式移动，从而创建一种吸引力和动态视觉效果，而不会干扰内容的可读性。</span><span class="sxs-lookup"><span data-stu-id="a6199-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="a6199-133">这种细微的颜色变化还有助于补偿任何次要的颜色异常。</span><span class="sxs-lookup"><span data-stu-id="a6199-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="a6199-134">透明或半透明 UI 底板的挑战</span><span class="sxs-lookup"><span data-stu-id="a6199-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="a6199-135">![透明 UI ](images/color_transparent_examples.jpg)
 *示例透明 UI 底板示例*</span><span class="sxs-lookup"><span data-stu-id="a6199-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="a6199-136">**视觉复杂性和可访问性**</span><span class="sxs-lookup"><span data-stu-id="a6199-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="a6199-137">由于全息对象与物理环境混合，因此透明或半透明窗口上的内容或 UI 可读性可能会下降。</span><span class="sxs-lookup"><span data-stu-id="a6199-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="a6199-138">此外，当透明全息对象彼此叠加时，由于深度令人困惑，用户难以交互。</span><span class="sxs-lookup"><span data-stu-id="a6199-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="a6199-139">**“性能”**</span><span class="sxs-lookup"><span data-stu-id="a6199-139">**Performance**</span></span>

<span data-ttu-id="a6199-140">若要正确呈现透明或半透明对象，必须排序这些对象，并与存在于后台的任何对象混合。</span><span class="sxs-lookup"><span data-stu-id="a6199-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="a6199-141">透明对象的排序具有适度的 CPU 成本，混合具有相当的 GPU 成本，因为它不允许 GPU 通过 z-culling 执行隐藏表面 (即</span><span class="sxs-lookup"><span data-stu-id="a6199-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="a6199-142">深度测试) 。</span><span class="sxs-lookup"><span data-stu-id="a6199-142">depth testing).</span></span> <span data-ttu-id="a6199-143">不允许隐藏表面移除会增加最终呈现像素所需的操作数。</span><span class="sxs-lookup"><span data-stu-id="a6199-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="a6199-144">这会使填充速率受到更多压力约束。</span><span class="sxs-lookup"><span data-stu-id="a6199-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="a6199-145">**深度 LSR 技术的全息影像稳定性问题**</span><span class="sxs-lookup"><span data-stu-id="a6199-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="a6199-146">为了提高全息重新投影或全息影像稳定性，应用程序可以针对每个渲染帧向系统提交深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="a6199-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="a6199-147">使用深度缓冲区进行重新分析时，需要为每个颜色呈现的像素编写一个深度缓冲区，以对应深度。</span><span class="sxs-lookup"><span data-stu-id="a6199-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="a6199-148">具有深度值的任何像素也应具有颜色值。</span><span class="sxs-lookup"><span data-stu-id="a6199-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="a6199-149">如果未遵循上述指南，可能会以生成项目的方式重新重现呈现的图像中缺少有效深度信息的区域，这些项目通常以波形扭曲方式显示。</span><span class="sxs-lookup"><span data-stu-id="a6199-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="a6199-150">透明元素的设计准则</span><span class="sxs-lookup"><span data-stu-id="a6199-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="a6199-151">**使用不透明 UI 背景**</span><span class="sxs-lookup"><span data-stu-id="a6199-151">**Use opaque UI background**</span></span>

<span data-ttu-id="a6199-152">默认情况下，透明或半透明对象不会写入深度以允许适当的混合。</span><span class="sxs-lookup"><span data-stu-id="a6199-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="a6199-153">缓解此问题的方法包括：使用不透明对象，确保半透明对象显示在不透明对象附近 (如不透明底板) 前面的半透明按钮、强制半透明对象写入深度 (不适用于所有方案) 或呈现代理对象（仅在帧末尾提供深度值）。</span><span class="sxs-lookup"><span data-stu-id="a6199-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="a6199-154">MRTK-Unity 中的解决方案：/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="a6199-154">Solutions within MRTK-Unity: /windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="a6199-155">通过使用实心不透明的底板，我们可以确保可读性和交互置信度。</span><span class="sxs-lookup"><span data-stu-id="a6199-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="a6199-156">**最小化受影响的像素数**</span><span class="sxs-lookup"><span data-stu-id="a6199-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="a6199-157">如果项目必须使用透明对象，请尝试最大程度地减少受影响的像素数。</span><span class="sxs-lookup"><span data-stu-id="a6199-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="a6199-158">例如，如果对象仅在特定条件下可见 (如累加光效果) ，则当对象完全不可见时 (禁用该对象，而不是将加法色设置为黑色) 。</span><span class="sxs-lookup"><span data-stu-id="a6199-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="a6199-159">对于使用带 alpha 掩码的四边形创建的简单 2D 形状，请考虑改为使用不透明着色器创建形状的网格表示形式。</span><span class="sxs-lookup"><span data-stu-id="a6199-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a6199-160">MRTK 中的深色 UI (Mixed Reality Toolkit) for Unity</span><span class="sxs-lookup"><span data-stu-id="a6199-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="a6199-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 基于深色配色方案提供了许多 UI 构建基块示例。</span><span class="sxs-lookup"><span data-stu-id="a6199-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="a6199-162">近菜单</span><span class="sxs-lookup"><span data-stu-id="a6199-162">Near Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [<span data-ttu-id="a6199-163">对话框</span><span class="sxs-lookup"><span data-stu-id="a6199-163">Dialog</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [<span data-ttu-id="a6199-164">手部菜单</span><span class="sxs-lookup"><span data-stu-id="a6199-164">Hand Menu</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a><span data-ttu-id="a6199-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6199-165">See also</span></span>

* [<span data-ttu-id="a6199-166">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="a6199-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="a6199-167">光标</span><span class="sxs-lookup"><span data-stu-id="a6199-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a6199-168">手部射线</span><span class="sxs-lookup"><span data-stu-id="a6199-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a6199-169">Button</span><span class="sxs-lookup"><span data-stu-id="a6199-169">Button</span></span>](button.md)
* [<span data-ttu-id="a6199-170">可交互对象</span><span class="sxs-lookup"><span data-stu-id="a6199-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a6199-171">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="a6199-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a6199-172">操作</span><span class="sxs-lookup"><span data-stu-id="a6199-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a6199-173">手动菜单</span><span class="sxs-lookup"><span data-stu-id="a6199-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a6199-174">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="a6199-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a6199-175">对象集合</span><span class="sxs-lookup"><span data-stu-id="a6199-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a6199-176">语音命令</span><span class="sxs-lookup"><span data-stu-id="a6199-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a6199-177">键盘</span><span class="sxs-lookup"><span data-stu-id="a6199-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a6199-178">工具提示</span><span class="sxs-lookup"><span data-stu-id="a6199-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a6199-179">平板</span><span class="sxs-lookup"><span data-stu-id="a6199-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="a6199-180">滑块</span><span class="sxs-lookup"><span data-stu-id="a6199-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="a6199-181">着色器</span><span class="sxs-lookup"><span data-stu-id="a6199-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="a6199-182">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="a6199-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a6199-183">显示进度</span><span class="sxs-lookup"><span data-stu-id="a6199-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a6199-184">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="a6199-184">Surface magnetism</span></span>](surface-magnetism.md)