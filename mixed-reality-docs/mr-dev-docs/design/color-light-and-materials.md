---
title: 颜色、光线和材料
description: 为混合现实设计内容需要认真考虑在你的体验中使用的每个视觉资产的颜色、照明和材料。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，颜色，细，材料
ms.openlocfilehash: 76237b1b08df98850a4989987ed608dae29b6b5c
ms.sourcegitcommit: 24d96bf3bb9a3143445e018195edae99d91684c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92683213"
---
# <a name="color-light-and-materials"></a><span data-ttu-id="04325-104">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="04325-104">Color, light and materials</span></span>
![颜色、光线和材料](images/RemoteRendering.jpg)

<span data-ttu-id="04325-106">为混合现实设计内容需要认真考虑在你的体验中使用的每个视觉资产的颜色、照明和材料。</span><span class="sxs-lookup"><span data-stu-id="04325-106">Designing content for mixed reality requires careful consideration of color, lighting, and materials for each of the visual assets used in your experience.</span></span> <span data-ttu-id="04325-107">这些决策可用于美观目的，如使用光线和材料来设置沉浸式环境的音调和功能，如使用各种颜色来提醒用户即将发生的操作。</span><span class="sxs-lookup"><span data-stu-id="04325-107">These decisions can be for both aesthetic purposes, like using light and material to set the tone of an immersive environment, and functional purposes, like using striking colors to alert users of an impending action.</span></span> <span data-ttu-id="04325-108">必须将每个决策与体验目标设备的机会和约束进行权衡。</span><span class="sxs-lookup"><span data-stu-id="04325-108">Each of these decisions must be weighed against the opportunities and constraints of your experience’s target device.</span></span>

<span data-ttu-id="04325-109">下面是特定于在沉浸式耳机上呈现资产的准则。</span><span class="sxs-lookup"><span data-stu-id="04325-109">Below are guidelines specific to rendering assets on both immersive and holographic headsets.</span></span> <span data-ttu-id="04325-110">其中的许多内容都与其他技术领域密切相关，并且可在本文末尾的 " [另请参阅](color-light-and-materials.md#see-also) " 一节中找到相关主题的列表。</span><span class="sxs-lookup"><span data-stu-id="04325-110">Many of these are closely tied to other technical areas and a list of related subjects can be found in the [See also](color-light-and-materials.md#see-also) section at the end of this article.</span></span>

## <a name="rendering-on-immersive-vs-holographic-devices"></a><span data-ttu-id="04325-111">在沉浸式与全息设备上渲染</span><span class="sxs-lookup"><span data-stu-id="04325-111">Rendering on immersive vs. holographic devices</span></span>

<span data-ttu-id="04325-112">与全息耳机中呈现的内容相比，在沉浸式耳机中呈现的内容看起来会有所不同。</span><span class="sxs-lookup"><span data-stu-id="04325-112">Content rendered in immersive headsets will appear visually different when compared to content rendered in holographic headsets.</span></span> <span data-ttu-id="04325-113">虽然沉浸式耳机通常会像在二维屏幕上一样呈现内容，但使用彩色的全息耳机（如 HoloLens）可以呈现全息影像。</span><span class="sxs-lookup"><span data-stu-id="04325-113">While immersive headsets generally render content much as you would expect on a 2D screen, holographic headsets like HoloLens use color-sequential, see-through RGB displays to renders holograms.</span></span>

<span data-ttu-id="04325-114">在全息耳机上，请始终花时间测试您的全息体验。</span><span class="sxs-lookup"><span data-stu-id="04325-114">Always take time to test your holographic experiences in a holographic headset.</span></span> <span data-ttu-id="04325-115">即使是专门为全息设备构建内容，内容的外观也会有所不同，如辅助监视器、快照和 spectator 视图中所示。</span><span class="sxs-lookup"><span data-stu-id="04325-115">The appearance of content, even if it is built specifically for holographic devices, will differ as seen on secondary monitors, snapshots, and in spectator view.</span></span> <span data-ttu-id="04325-116">请记住，在设备上进行测试，测试全息影像的照明，并从所有两侧 (以及从上到下，) 内容呈现方式。</span><span class="sxs-lookup"><span data-stu-id="04325-116">Remember to walk around experiences with a device, testing the lighting of holograms and observing from all sides (as well as from above and below) how your content is rendered.</span></span> <span data-ttu-id="04325-117">请确保在设备上的一系列亮度设置中进行测试，因为所有用户不太可能会共享假设的默认值，以及不同的照明条件集。</span><span class="sxs-lookup"><span data-stu-id="04325-117">Be sure to test at a range of brightness settings on the device, as it is unlikely all users will share an assumed default, as well as a diverse set of lighting conditions.</span></span>

## <a name="fundamentals-of-rendering-on-holographic-devices"></a><span data-ttu-id="04325-118">全息设备上呈现的基本知识</span><span class="sxs-lookup"><span data-stu-id="04325-118">Fundamentals of rendering on holographic devices</span></span>
* <span data-ttu-id="04325-119">**全息设备具有累加性显示器** –通过向现实世界中的灯光添加光源来创建全息影像–白色将显示为明亮，而黑色将显示为透明。</span><span class="sxs-lookup"><span data-stu-id="04325-119">**Holographic devices have additive displays** – Holograms are created by adding light to the light from the real world – white will appear brightly, while black will appear transparent.</span></span>

* <span data-ttu-id="04325-120">**颜色影响因用户的环境而异** –用户房间内有很多不同的照明条件。</span><span class="sxs-lookup"><span data-stu-id="04325-120">**Colors impact varies with the user’s environment** – There are many diverse lighting conditions in a user’s room.</span></span> <span data-ttu-id="04325-121">创建具有适当的对比度级别的内容，以便清晰地提供帮助。</span><span class="sxs-lookup"><span data-stu-id="04325-121">Create content with appropriate levels of contrast to help with clarity.</span></span>

* <span data-ttu-id="04325-122">**避免动态照明** –在全息体验中均匀发亮的全息影像是最有效的。</span><span class="sxs-lookup"><span data-stu-id="04325-122">**Avoid dynamic lighting** – Holograms that are uniformly lit in holographic experiences are the most efficient.</span></span> <span data-ttu-id="04325-123">使用 "高级" 时，动态照明可能会超出移动设备的功能。</span><span class="sxs-lookup"><span data-stu-id="04325-123">Using advanced, dynamic lighting will likely exceed the capabilities of mobile devices.</span></span> <span data-ttu-id="04325-124">需要动态照明时，建议使用 [混合现实工具包标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)。</span><span class="sxs-lookup"><span data-stu-id="04325-124">When dynamic lighting is required, it is recommended to use the [Mixed Reality Toolkit Standard shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md).</span></span> 

## <a name="designing-with-color"></a><span data-ttu-id="04325-125">用 color 设计</span><span class="sxs-lookup"><span data-stu-id="04325-125">Designing with color</span></span>

<span data-ttu-id="04325-126">由于附加显示器的性质，某些颜色在全息显示器上显示的颜色可能不同。</span><span class="sxs-lookup"><span data-stu-id="04325-126">Due to the nature of additive displays, certain colors can appear different on holographic displays.</span></span> <span data-ttu-id="04325-127">某些颜色将在照明环境中弹出，而其他颜色显示的有影响力更少。</span><span class="sxs-lookup"><span data-stu-id="04325-127">Some colors will pop in lighting environments while others will appear as less impactful.</span></span> <span data-ttu-id="04325-128">冷颜色通常会 recede 到背景中，而热颜色会跳到前台。</span><span class="sxs-lookup"><span data-stu-id="04325-128">Cool colors tend to recede into the background while warm colors jump to the foreground.</span></span> <span data-ttu-id="04325-129">在浏览经验时，请考虑以下因素：</span><span class="sxs-lookup"><span data-stu-id="04325-129">Consider these factors as you explore color in your experiences:</span></span>

* <span data-ttu-id="04325-130">**呈现浅色颜色** -白色显示非常明亮，应慎用。</span><span class="sxs-lookup"><span data-stu-id="04325-130">**Rendering light colors** - White appears very bright and should be used sparingly.</span></span> <span data-ttu-id="04325-131">大多数情况下，请考虑有关 R 235 G 235 B 235 的空白值。</span><span class="sxs-lookup"><span data-stu-id="04325-131">For most cases, consider a white value around R 235 G 235 B 235.</span></span> <span data-ttu-id="04325-132">较大的亮点可能导致用户 discomfort。</span><span class="sxs-lookup"><span data-stu-id="04325-132">Large bright areas may cause user discomfort.</span></span> <span data-ttu-id="04325-133">对于 UI 窗口的 backplate，建议使用深色颜色。</span><span class="sxs-lookup"><span data-stu-id="04325-133">For the UI window's backplate, it is recommended to use dark colors.</span></span>

* <span data-ttu-id="04325-134">**呈现深色颜色** -由于加法显示的性质，深色颜色显示为透明。</span><span class="sxs-lookup"><span data-stu-id="04325-134">**Rendering dark colors** - Due to the nature of additive displays, dark colors appear transparent.</span></span> <span data-ttu-id="04325-135">实心黑色对象将与现实环境中的显示效果完全不同。</span><span class="sxs-lookup"><span data-stu-id="04325-135">A solid black object will appear no different from the real world.</span></span> <span data-ttu-id="04325-136">请参阅下面的 Alpha 通道。</span><span class="sxs-lookup"><span data-stu-id="04325-136">See Alpha channel below.</span></span> <span data-ttu-id="04325-137">若要使显示 "黑色"，请尝试使用非常深的灰色 RGB 值，如16、16、16。</span><span class="sxs-lookup"><span data-stu-id="04325-137">To give the appearance of “black” try a very dark grey RGB value such as 16,16,16.</span></span>

* <span data-ttu-id="04325-138">**颜色一致性** -通常，全息影像呈现得非常明亮，因此，无论背景如何，都可以保持颜色一致性。</span><span class="sxs-lookup"><span data-stu-id="04325-138">**Color uniformity** - Typically holograms are rendered brightly enough so that they maintain color uniformity, regardless of the background.</span></span> <span data-ttu-id="04325-139">大区域可能会变得 blotchy。</span><span class="sxs-lookup"><span data-stu-id="04325-139">Large areas may become blotchy.</span></span> <span data-ttu-id="04325-140">避免出现鲜艳、纯色的大型区域。</span><span class="sxs-lookup"><span data-stu-id="04325-140">Avoid large regions of bright, solid color.</span></span>

* <span data-ttu-id="04325-141">**Gamut** 从一种颜色的 "宽范围" 中获益，从概念上讲类似于 Adobe RGB。</span><span class="sxs-lookup"><span data-stu-id="04325-141">**Gamut** - HoloLens benefits from a "wide gamut" of color, conceptually similar to Adobe RGB.</span></span> <span data-ttu-id="04325-142">因此，某些颜色可能会在设备中表现出不同的质量和表示形式。</span><span class="sxs-lookup"><span data-stu-id="04325-142">As a result, some colors can exhibit different qualities and representation in the device.</span></span>

* <span data-ttu-id="04325-143">**伽玛** -所呈现图像的亮度和对比度将因沉浸式和全息设备而异。</span><span class="sxs-lookup"><span data-stu-id="04325-143">**Gamma** - The brightness and contrast of the rendered image will vary between immersive and holographic devices.</span></span> <span data-ttu-id="04325-144">这些设备的差异经常会使颜色和阴影变暗，更亮或更不亮。</span><span class="sxs-lookup"><span data-stu-id="04325-144">These device differences often appear to make dark areas of color and shadows, more or less bright.</span></span>

* <span data-ttu-id="04325-145">**颜色分离** -也称为 "color 细分情况" 或 "color fringing"，当用户跟踪对象的眼睛时，最常发生颜色分离 (包括光标) 。</span><span class="sxs-lookup"><span data-stu-id="04325-145">**Color separation** - Also called "color breakup" or "color fringing", color separation most commonly occurs with moving holograms (including cursor) when a user tracks objects with their eyes.</span></span>

## <a name="technical-considerations"></a><span data-ttu-id="04325-146">技术注意事项</span><span class="sxs-lookup"><span data-stu-id="04325-146">Technical considerations</span></span>
* <span data-ttu-id="04325-147">" **别名** "-深思熟虑后得出的，它是锯齿、锯齿或 "楼梯段" 的边缘与现实世界之间的边缘。</span><span class="sxs-lookup"><span data-stu-id="04325-147">**Aliasing** - Be considerate of aliasing, jagged or “stair steps” where the edge of a hologram’s geometry meets the real world.</span></span> <span data-ttu-id="04325-148">如果使用具有高细节的纹理，则会加剧此效果。</span><span class="sxs-lookup"><span data-stu-id="04325-148">Using textures with high detail can aggravate this effect.</span></span> <span data-ttu-id="04325-149">应映射和筛选已启用纹理。</span><span class="sxs-lookup"><span data-stu-id="04325-149">Textures should be mapped and filtering enabled.</span></span> <span data-ttu-id="04325-150">请考虑在对象周围创建黑色边缘边框，以淡化全息影像边缘或添加纹理。</span><span class="sxs-lookup"><span data-stu-id="04325-150">Consider fading the edges of holograms or adding a texture that creates a black edge border around objects.</span></span> <span data-ttu-id="04325-151">尽可能避免精简几何。</span><span class="sxs-lookup"><span data-stu-id="04325-151">Avoid thin geometry where possible.</span></span>

* <span data-ttu-id="04325-152">**Alpha 通道** -对于没有渲染全息图的任何部分，必须清除 alpha 通道，使其完全透明。</span><span class="sxs-lookup"><span data-stu-id="04325-152">**Alpha channel** - You must clear your alpha channel to fully transparent for any parts where you are not rendering a hologram.</span></span> <span data-ttu-id="04325-153">在从设备或通过 Spectator 视图拍摄图像/视频时，使 alpha 不确定会导致视觉对象。</span><span class="sxs-lookup"><span data-stu-id="04325-153">Leaving the alpha undefined leads to visual artifacts when taking images/videos from the device or with Spectator View.</span></span>

* <span data-ttu-id="04325-154">**纹理软化** -由于浅是全息显示屏中的加法，因此最好避免较大的纯色区域，因为它们通常不会产生预期的视觉效果。</span><span class="sxs-lookup"><span data-stu-id="04325-154">**Texture softening** - Since light is additive in holographic displays, it is best to avoid large regions of bright, solid color as they often do not produce the intended visual effect.</span></span>

## <a name="design-guidelines-for-holographic-display"></a><span data-ttu-id="04325-155">全息显示器的设计准则</span><span class="sxs-lookup"><span data-stu-id="04325-155">Design guidelines for holographic display</span></span>
![颜色和手封闭](images/color_handocclusion.jpg)

<span data-ttu-id="04325-157">设计全息显示器内容时，需要考虑几个元素来获得最佳体验。</span><span class="sxs-lookup"><span data-stu-id="04325-157">When designing content for holographic displays, there are several elements that you need to consider achieving the best experience.</span></span> <span data-ttu-id="04325-158">有关指导原则和建议，请访问 [设计用于全息显示的内容](designing-content-for-holographic-display.md) 。</span><span class="sxs-lookup"><span data-stu-id="04325-158">Please visit [Designing content for holographic display](designing-content-for-holographic-display.md) for the guidelines and recommendations.</span></span>

## <a name="storytelling-with-light-and-color"></a><span data-ttu-id="04325-159">带有浅和颜色的故事分享</span><span class="sxs-lookup"><span data-stu-id="04325-159">Storytelling with light and color</span></span>

<span data-ttu-id="04325-160">光源和颜色可帮助你在用户的环境中更自然地显示全息影像，并为用户提供指导和帮助。</span><span class="sxs-lookup"><span data-stu-id="04325-160">Light and color can help make your holograms appear more naturally in a user's environment as well as offer guidance and help for the user.</span></span> <span data-ttu-id="04325-161">对于全息体验，请在探索光照和颜色时考虑以下因素：</span><span class="sxs-lookup"><span data-stu-id="04325-161">For holographic experiences, consider these factors as you explore lighting and color:</span></span>

:::row:::
    :::column:::
* <span data-ttu-id="04325-162">**Vignetting** -"vignette" 效果用于加深材料，有助于将用户的注意力集中在视图的中心。</span><span class="sxs-lookup"><span data-stu-id="04325-162">**Vignetting** - A 'vignette' effect to darken materials can help focus the user's attention on the center of the field of view.</span></span> <span data-ttu-id="04325-163">这种效果会将全息图的材料从用户的注视向量变暗。</span><span class="sxs-lookup"><span data-stu-id="04325-163">This effect darkens the hologram's material at some radius from the user's gaze vector.</span></span> <span data-ttu-id="04325-164">请注意，当用户从倾斜或 glancing 角度查看全息影像时，这也是有效的。</span><span class="sxs-lookup"><span data-stu-id="04325-164">Note that this is also effective when the user views holograms from an oblique or glancing angle.</span></span>

* <span data-ttu-id="04325-165">**强调** ：通过对比颜色、亮度和照明来吸引对象或交互点。</span><span class="sxs-lookup"><span data-stu-id="04325-165">**Emphasis** - Draw attention to objects or points of interaction by contrasting colors, brightness, and lighting.</span></span> <span data-ttu-id="04325-166">若要详细了解故事分享中的照明方法，请参阅 [像素 Cinematography-适用于计算机图形的照明方法](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)。</span><span class="sxs-lookup"><span data-stu-id="04325-166">For a more detailed look at lighting methods in storytelling, see [Pixel Cinematography - A Lighting Approach for Computer Graphics](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).</span></span><br>
        <br>
        <span data-ttu-id="04325-167">*图像：使用 color 显示故事分享元素的强调，此处显示的内容位于 [片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)的场景中。*</span><span class="sxs-lookup"><span data-stu-id="04325-167">*Image: Use of color to show emphasis for storytelling elements, shown here in a scene from [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*</span></span>
    :::column-end:::
        :::column:::
        ![使用 "颜色" 显示对故事分享元素的强调，此处显示在片段的场景中。](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a><span data-ttu-id="04325-169">材料</span><span class="sxs-lookup"><span data-stu-id="04325-169">Materials</span></span>

:::row:::
    :::column:::
<span data-ttu-id="04325-170">材料是用于制作真实全息影像的重要元素。</span><span class="sxs-lookup"><span data-stu-id="04325-170">Materials are crucial elements for making realistic holograms.</span></span> <span data-ttu-id="04325-171">通过提供适当的视觉特征，你可以制作出引人注目的全息对象，这些对象可与物理环境完美融合。</span><span class="sxs-lookup"><span data-stu-id="04325-171">By providing proper visual characteristics, you can make compelling holographic objects that can blend well with the physical environment.</span></span> <span data-ttu-id="04325-172">材料对于为各种类型的用户输入交互提供可视反馈也很重要。</span><span class="sxs-lookup"><span data-stu-id="04325-172">Materials are also important for providing visual feedback for the various types of user input interactions.</span></span>  

<span data-ttu-id="04325-173">[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) 提供了一个 MRTK 标准着色器，其中包含可用于视觉反馈的各种视觉效果选项。</span><span class="sxs-lookup"><span data-stu-id="04325-173">[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides an MRTK Standard Shader with various visual effect options that can be used for visual feedback.</span></span> <span data-ttu-id="04325-174">例如，当用户的手指接近对象的表面时，可以使用 "邻近感应" 属性来提供灯光效果。</span><span class="sxs-lookup"><span data-stu-id="04325-174">For example, you can use 'Proximity Light' property to provide a lighting effect when the user's finger is approaching the object's surface.</span></span> <span data-ttu-id="04325-175">了解有关[MRTK 标准着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)的详细信息</span><span class="sxs-lookup"><span data-stu-id="04325-175">Learn more about [MRTK Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)</span></span>
    :::column-end:::
        :::column:::
    <span data-ttu-id="04325-176">*视频循环：基于与边界框* 
     ![ 的邻近的视觉反馈示例视觉对象反馈](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="04325-176">*Video loop: Example of visual feedback based on proximity to a bounding box*
![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span>

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a><span data-ttu-id="04325-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04325-177">See also</span></span>
* [<span data-ttu-id="04325-178">设计适用于全息显示器的内容</span><span class="sxs-lookup"><span data-stu-id="04325-178">Designing content for holographic display</span></span>](designing-content-for-holographic-display.md)
* [<span data-ttu-id="04325-179">颜色分离</span><span class="sxs-lookup"><span data-stu-id="04325-179">Color Separation</span></span>](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [<span data-ttu-id="04325-180">全息影像</span><span class="sxs-lookup"><span data-stu-id="04325-180">Holograms</span></span>](../discover/hologram.md)
* [<span data-ttu-id="04325-181">Microsoft 设计语言-颜色</span><span class="sxs-lookup"><span data-stu-id="04325-181">Microsoft Design Language - color</span></span>](https://www.microsoft.com/design/color)
* [<span data-ttu-id="04325-182">通用 Windows 平台-颜色</span><span class="sxs-lookup"><span data-stu-id="04325-182">Universal Windows Platform - color</span></span>](https://docs.microsoft.com/windows/uwp/style/color)
