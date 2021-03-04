---
title: 设计适用于全息显示器的内容
description: 了解有关在 HoloLens 设备上进行全息显示的设计准则和最佳实践。
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 设计，全息显示，内容设计，深色主题，浅色主题，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，设计，像素
ms.openlocfilehash: 6bf65b9e40e42f1609b1108b366ac65637fcf106
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759272"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="8c0e8-104">设计适用于全息显示器的内容</span><span class="sxs-lookup"><span data-stu-id="8c0e8-104">Designing content for holographic display</span></span>

![Ulnar 端位置](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="8c0e8-106">设计全息显示器内容时，需要考虑几个元素，以便获得最佳体验。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="8c0e8-107">下面列出了下面的一些建议，你可以在 ["颜色、光线和材料](color-light-and-materials.md) " 页面上详细了解全息版显示的特征。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="8c0e8-108">大型表面上明亮的颜色挑战</span><span class="sxs-lookup"><span data-stu-id="8c0e8-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="8c0e8-109">根据我们的 HoloLens 体验研究和测试，我们发现，在大范围的显示中使用明亮的颜色可能会导致几个问题：</span><span class="sxs-lookup"><span data-stu-id="8c0e8-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="8c0e8-110">**眼睛疲劳**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-110">**Eye fatigue**</span></span> 

<span data-ttu-id="8c0e8-111">由于全息显示是累加的，因此具有明亮颜色的全息影像会占用更少的颜色。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="8c0e8-112">在较大的显示区域中，颜色明亮，很容易导致用户的眼睛疲劳。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="8c0e8-113">**手动封闭**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-113">**Hand occlusion**</span></span> 

<span data-ttu-id="8c0e8-114">明亮的颜色使用户在直接与对象交互时很难看到其手。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="8c0e8-115">由于用户无法看到其手，因此很难感觉到该手指与目标表面之间的深度/距离。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="8c0e8-116">Finger 游标有助于弥补此问题，但在明亮的表面上，它仍会有挑战性。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="8c0e8-117">![颜色和手封闭 ](images/color_handocclusion.jpg)
 *很难看到鲜艳的彩色内容 backplate*</span><span class="sxs-lookup"><span data-stu-id="8c0e8-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="8c0e8-118">**颜色一致性**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-118">**Color uniformity**</span></span>

<span data-ttu-id="8c0e8-119">由于全息显示器的特性，显示屏上的一个较亮的区域可能会变得 blotchy。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="8c0e8-120">通过使用暗色方案，你可以最大程度地减少此问题。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="8c0e8-121">颜色选择设计准则</span><span class="sxs-lookup"><span data-stu-id="8c0e8-121">Design guidelines for color choices</span></span>

<span data-ttu-id="8c0e8-122">**为 UI 背景使用暗色**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="8c0e8-123">通过使用暗色方案，你可以最大程度地减少眼睛疲劳并改善直接交互的置信度。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="8c0e8-124">![用于 ](images/color_dark_examples.jpg)
 *内容背景的深色颜色示例* 的深色颜色示例</span><span class="sxs-lookup"><span data-stu-id="8c0e8-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="8c0e8-125">**使用 semibold 或粗体字体粗细**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="8c0e8-126">HoloLens 允许你的体验显示漂亮的高分辨率文本。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="8c0e8-127">但是，建议您避免使用细的字体粗细，如浅色或半光，因为垂直笔划可以在小字号内抖动。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="8c0e8-128">![ (上部面板的粗体或半粗体字体粗细) 会提高清晰度 ](images/color_font_examples.jpg)
 *粗体或半粗体字体粗细， (上面板) 提高清晰度*</span><span class="sxs-lookup"><span data-stu-id="8c0e8-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="8c0e8-129">**使用 MRTK 的 HolographicBackplate 材料**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="8c0e8-130">HolographicBackplate 材料适用于 HoloLens shell 中的几个 UI 面板。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="8c0e8-131">其中一项功能是在用户根据面板移动其位置时对用户可见的 iridescence 效果。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="8c0e8-132">Backplate 颜色在一系列预定义的光谱上略有变化，从而创造生动生动的动态视觉效果，而不会干扰内容的可读性。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="8c0e8-133">此微妙的颜色转变还用于弥补任何次要颜色不规则性。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="8c0e8-134">透明或半透明 UI backplate 的挑战</span><span class="sxs-lookup"><span data-stu-id="8c0e8-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="8c0e8-135">![透明 ](images/color_transparent_examples.jpg)
 *ui backplate 的* 透明 ui 示例</span><span class="sxs-lookup"><span data-stu-id="8c0e8-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="8c0e8-136">**视觉对象复杂性和辅助功能**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="8c0e8-137">由于全息对象与物理环境混合，透明或半透明窗口上的内容或 UI 清晰度可能会下降。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="8c0e8-138">此外，当透明全息对象重叠在一起时，这可能会使用户难以在不太深入的情况下进行交互。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="8c0e8-139">**“性能”**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-139">**Performance**</span></span>

<span data-ttu-id="8c0e8-140">若要正确呈现透明或半透明对象，必须将其与存在于后台的任何对象进行排序和混合。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="8c0e8-141">透明对象的排序具有适度的 CPU 开销，混合具有相当大的 GPU 开销，因为它不允许 GPU 通过 z 剔除来执行隐藏的图面删除 (例如</span><span class="sxs-lookup"><span data-stu-id="8c0e8-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="8c0e8-142">深度测试) 。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-142">depth testing).</span></span> <span data-ttu-id="8c0e8-143">不允许隐藏的图面会增加最终呈现的像素所需的操作的数目。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="8c0e8-144">这将导致更多压力填充率约束。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="8c0e8-145">**LSR 技术的全息影像稳定性问题**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="8c0e8-146">若要改善全息 reprojection 或全息图稳定性，应用程序可以为每个呈现的帧提交系统的深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="8c0e8-147">使用 reprojection 的深度缓冲区时，需要为每个颜色呈现的像素写入一个相应深度的深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="8c0e8-148">具有深度值的任何像素还应具有颜色值。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="8c0e8-149">如果未遵循上述指导原则，呈现图像中缺少有效深度信息的区域可能会 reprojected 生成项目的方式，这通常作为类似于波形的失真显示。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="8c0e8-150">透明元素的设计准则</span><span class="sxs-lookup"><span data-stu-id="8c0e8-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="8c0e8-151">**使用不透明的 UI 背景**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-151">**Use opaque UI background**</span></span>

<span data-ttu-id="8c0e8-152">默认情况下，透明或半透明对象不会写入深度以允许进行适当的混合。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="8c0e8-153">缓解此问题的方法包括：使用不透明对象，并确保半透明对象接近于不透明的对象 (例如，在不透明的 backplate) 前面添加半透明的按钮、强制半透明对象写入深度 (不适用于所有方案) ，或呈现代理对象，这些对象只在帧末尾提供深度值。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="8c0e8-154">MRTK 中的解决方案-Unity： https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="8c0e8-154">Solutions within MRTK-Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="8c0e8-155">通过使用纯和不透明的 backplate，我们可以确保可读性和交互置信度。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="8c0e8-156">**最大程度地减少受影响的像素数**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="8c0e8-157">如果项目必须使用透明对象，请尝试最大程度地减少受影响的像素数。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="8c0e8-158">例如，如果某一对象仅在某些条件下可见 (如) 的加法光亮效果，则在该对象完全不可见时禁用该对象 (而不是将附加颜色设置为黑色) 。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="8c0e8-159">对于使用带有 alpha 掩码的四核创建的简单二维形状，请考虑改为使用不透明着色器来创建形状的网格表示形式。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="8c0e8-160">MRTK 中的深色 UI 示例 (混合现实工具包) 适用于 Unity</span><span class="sxs-lookup"><span data-stu-id="8c0e8-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="8c0e8-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供了许多基于深色方案的 UI 构建基块示例。</span><span class="sxs-lookup"><span data-stu-id="8c0e8-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="8c0e8-162">邻近菜单</span><span class="sxs-lookup"><span data-stu-id="8c0e8-162">Near Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/near-menu.md)
* [<span data-ttu-id="8c0e8-163">对话框</span><span class="sxs-lookup"><span data-stu-id="8c0e8-163">Dialog</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/dialog.md)
* [<span data-ttu-id="8c0e8-164">手动菜单</span><span class="sxs-lookup"><span data-stu-id="8c0e8-164">Hand Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="8c0e8-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c0e8-165">See also</span></span>

* [<span data-ttu-id="8c0e8-166">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="8c0e8-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="8c0e8-167">光标</span><span class="sxs-lookup"><span data-stu-id="8c0e8-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8c0e8-168">手部射线</span><span class="sxs-lookup"><span data-stu-id="8c0e8-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8c0e8-169">Button</span><span class="sxs-lookup"><span data-stu-id="8c0e8-169">Button</span></span>](button.md)
* [<span data-ttu-id="8c0e8-170">可交互对象</span><span class="sxs-lookup"><span data-stu-id="8c0e8-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8c0e8-171">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="8c0e8-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8c0e8-172">操作</span><span class="sxs-lookup"><span data-stu-id="8c0e8-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8c0e8-173">手动菜单</span><span class="sxs-lookup"><span data-stu-id="8c0e8-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8c0e8-174">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="8c0e8-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8c0e8-175">对象集合</span><span class="sxs-lookup"><span data-stu-id="8c0e8-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8c0e8-176">语音命令</span><span class="sxs-lookup"><span data-stu-id="8c0e8-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8c0e8-177">键盘</span><span class="sxs-lookup"><span data-stu-id="8c0e8-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8c0e8-178">工具提示</span><span class="sxs-lookup"><span data-stu-id="8c0e8-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8c0e8-179">平板</span><span class="sxs-lookup"><span data-stu-id="8c0e8-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="8c0e8-180">滑块</span><span class="sxs-lookup"><span data-stu-id="8c0e8-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="8c0e8-181">着色器</span><span class="sxs-lookup"><span data-stu-id="8c0e8-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="8c0e8-182">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="8c0e8-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8c0e8-183">显示进度</span><span class="sxs-lookup"><span data-stu-id="8c0e8-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8c0e8-184">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="8c0e8-184">Surface magnetism</span></span>](surface-magnetism.md)
