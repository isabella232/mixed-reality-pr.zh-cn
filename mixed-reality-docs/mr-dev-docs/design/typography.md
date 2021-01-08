---
title: 版式
description: 了解如何设计文本，并将其实现为重要元素，以便在混合现实应用体验中提供信息。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality，设计，样式，字体，版式，ui，ux，文本，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens
ms.openlocfilehash: 38acc8c0d2c7dbd7bcb192f82bb1bb52838323ac
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007647"
---
# <a name="typography"></a><span data-ttu-id="8125d-104">版式</span><span class="sxs-lookup"><span data-stu-id="8125d-104">Typography</span></span>

![HoloLens 中的版式示例](images/typography-cover.png)<br>


<span data-ttu-id="8125d-106">文本是在应用程序体验中提供信息的重要元素。</span><span class="sxs-lookup"><span data-stu-id="8125d-106">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="8125d-107">就像2D 屏幕上的版式一样，目标应清晰且易懂。</span><span class="sxs-lookup"><span data-stu-id="8125d-107">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="8125d-108">由于混合现实的三维方面，有机会以更好的方式影响文本和总体用户体验。</span><span class="sxs-lookup"><span data-stu-id="8125d-108">With the three-dimensional aspect of mixed reality, there's an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="8125d-109">当我们谈到3D 中的类型时，我们倾向于容量耗尽3D 文本。</span><span class="sxs-lookup"><span data-stu-id="8125d-109">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="8125d-110">除了某些标识设计和一些其他有限的应用程序，延伸文本往往会降低文本的可读性。</span><span class="sxs-lookup"><span data-stu-id="8125d-110">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="8125d-111">尽管我们正在设计3D 体验，但我们对类型使用2D，因为它更清晰且更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="8125d-111">Even though we're designing experiences for 3D, we use 2D for the type because it's more legible and easier to read.</span></span>

<span data-ttu-id="8125d-112">在 HoloLens 中，类型是使用基于附加颜色系统的轻型的影像构建的。</span><span class="sxs-lookup"><span data-stu-id="8125d-112">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="8125d-113">就像其他全息影像一样，可以将类型放在实际的环境中，在该环境中，可以从任何角度进行世界锁定和观察。</span><span class="sxs-lookup"><span data-stu-id="8125d-113">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="8125d-114">类型和环境之间的 [视差](https://en.wikipedia.org/wiki/Parallax) 效果也增加了体验的深度。</span><span class="sxs-lookup"><span data-stu-id="8125d-114">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="8125d-115">混合现实中的版式</span><span class="sxs-lookup"><span data-stu-id="8125d-115">Typography in mixed reality</span></span>

<span data-ttu-id="8125d-116">混合现实中的版式规则与其他任何地方都没有什么不同。</span><span class="sxs-lookup"><span data-stu-id="8125d-116">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="8125d-117">物理世界和虚拟世界中的文本都需要更清晰且更易读。</span><span class="sxs-lookup"><span data-stu-id="8125d-117">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="8125d-118">文本可能位于墙上，或在物理对象上重叠。</span><span class="sxs-lookup"><span data-stu-id="8125d-118">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="8125d-119">它可以与数字用户界面一起浮动。</span><span class="sxs-lookup"><span data-stu-id="8125d-119">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="8125d-120">无论使用何种上下文，都将使用相同的印刷规则来进行读取和识别。</span><span class="sxs-lookup"><span data-stu-id="8125d-120">Whatever the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="8125d-121">创建清晰的层次结构</span><span class="sxs-lookup"><span data-stu-id="8125d-121">Create clear hierarchy</span></span>

<span data-ttu-id="8125d-122">使用不同类型的大小和权重生成对比度和层次结构。</span><span class="sxs-lookup"><span data-stu-id="8125d-122">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="8125d-123">在整个应用程序体验中定义类型斜坡并遵循它将提供具有一致的信息层次结构的丰富用户体验。</span><span class="sxs-lookup"><span data-stu-id="8125d-123">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="8125d-124">![键入斜坡示例](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8125d-124">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="8125d-125">*定义类型斜坡，并在整个应用体验中执行*</span><span class="sxs-lookup"><span data-stu-id="8125d-125">*Define your type ramp and follow it throughout the app experience*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="8125d-126">限制字体</span><span class="sxs-lookup"><span data-stu-id="8125d-126">Limit your fonts</span></span>

<span data-ttu-id="8125d-127">避免在一个上下文中使用两个以上的不同字体系列。</span><span class="sxs-lookup"><span data-stu-id="8125d-127">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="8125d-128">字体过多会破坏体验的协调和一致性，并使其难以使用信息。</span><span class="sxs-lookup"><span data-stu-id="8125d-128">Too many fonts will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="8125d-129">在 HoloLens 中，由于信息是在物理环境上重叠的，因此使用太多字体样式会降低体验。</span><span class="sxs-lookup"><span data-stu-id="8125d-129">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="8125d-130">Segoe UI 是所有 Microsoft 数字设计的字体。</span><span class="sxs-lookup"><span data-stu-id="8125d-130">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="8125d-131">它在 Windows Mixed Reality shell 中一致地使用。</span><span class="sxs-lookup"><span data-stu-id="8125d-131">It's used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="8125d-132">您可以从 [Windows 设计工具包页](https://docs.microsoft.com/windows/uwp/design-downloads/)下载 Segoe UI 的字体文件。</span><span class="sxs-lookup"><span data-stu-id="8125d-132">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="8125d-133">有关 Segoe UI 字样的详细信息</span><span class="sxs-lookup"><span data-stu-id="8125d-133">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="8125d-134">避免精简字体粗细</span><span class="sxs-lookup"><span data-stu-id="8125d-134">Avoid thin font weights</span></span>

<span data-ttu-id="8125d-135">避免在42磅下为类型大小使用光源或 semilight 字体粗细，因为精简垂直笔划将振动并降低清晰度。</span><span class="sxs-lookup"><span data-stu-id="8125d-135">Avoid using light or semilight font weights for type sizes under 42 pt because thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="8125d-136">具有足够笔划粗细的新式字体很好地运行。</span><span class="sxs-lookup"><span data-stu-id="8125d-136">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="8125d-137">例如，使用常规或粗体时，Arial 和 Arial 可以在 HoloLens 中清晰地显示。</span><span class="sxs-lookup"><span data-stu-id="8125d-137">For example, Helvetica and Arial are legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="8125d-138">Color</span><span class="sxs-lookup"><span data-stu-id="8125d-138">Color</span></span>

<span data-ttu-id="8125d-139">在 HoloLens 中，由于全息影像是使用加法光源系统构建的，因此白色文本非常清晰。</span><span class="sxs-lookup"><span data-stu-id="8125d-139">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="8125d-140">你可以在 "开始" 菜单和应用栏上找到白色文本的示例。</span><span class="sxs-lookup"><span data-stu-id="8125d-140">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="8125d-141">即使在不使用 HoloLens 的背面的情况下白色文本也能正常工作，复杂的物理背景也可能使类型难以阅读。</span><span class="sxs-lookup"><span data-stu-id="8125d-141">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="8125d-142">建议在黑色或彩色背面使用白色文本，以改善用户的注意力，并尽量减少物理背景中的干扰。</span><span class="sxs-lookup"><span data-stu-id="8125d-142">We recommend using white text on a dark or colored back plate to improve the user's focus and minimize the distraction from a physical background.</span></span>

<br>


<span data-ttu-id="8125d-143">![建议在黑色或彩色背面使用白色文本。 ](images/typography-whiteonblack2-1000px.jpg)
*深色或彩色后面板上的白色文本的示例。*</span><span class="sxs-lookup"><span data-stu-id="8125d-143">![We recommend using white text on a dark or colored back plate.](images/typography-whiteonblack2-1000px.jpg)
*Examples of white text on a dark or colored back plate.*</span></span>
<br>

<span data-ttu-id="8125d-144">若要使用深色文本，您应该使用一个亮点，使其可供阅读。</span><span class="sxs-lookup"><span data-stu-id="8125d-144">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="8125d-145">在 "附加颜色系统" 中，黑色显示为透明。</span><span class="sxs-lookup"><span data-stu-id="8125d-145">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="8125d-146">这意味着，如果没有彩色的背面印版，则不会显示黑色文本。</span><span class="sxs-lookup"><span data-stu-id="8125d-146">This means you won't see the black text without a colored back plate.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8125d-147">![白底黑白色文本的示例](images/typography-whiteonblack.png)</span><span class="sxs-lookup"><span data-stu-id="8125d-147">![Examples of white on black and black on white text](images/typography-whiteonblack.png)</span></span><br>
        <span data-ttu-id="8125d-148">*白底黑白色文本的示例*</span><span class="sxs-lookup"><span data-stu-id="8125d-148">*Examples of white on black and black on white text*</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8125d-149">![系统应用中的黑色文本示例-存储和设置](images/640px-typography-blackonwhite.jpg)</span><span class="sxs-lookup"><span data-stu-id="8125d-149">![Examples of black text in the system apps - Store and Settings](images/640px-typography-blackonwhite.jpg)</span></span><br>
        <span data-ttu-id="8125d-150">*系统应用中的黑色文本示例-存储和设置*</span><span class="sxs-lookup"><span data-stu-id="8125d-150">*Examples of black text in the system apps - Store and Settings*</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a><span data-ttu-id="8125d-151">建议的字体大小</span><span class="sxs-lookup"><span data-stu-id="8125d-151">Recommended font size</span></span>

<span data-ttu-id="8125d-152">正如你所料，在电脑或平板电脑设备上使用的类型大小 (通常在12–32pt 之间，) 在2米的距离处查看小。</span><span class="sxs-lookup"><span data-stu-id="8125d-152">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look small at a distance of 2 meters.</span></span> <span data-ttu-id="8125d-153">这取决于每种字体的特征，但通常情况下，建议的最小查看角度和清晰度的字体高度基于用户研究研究0.35 °-0.4 °/12.21-13.97 mm。</span><span class="sxs-lookup"><span data-stu-id="8125d-153">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97 mm based on our user research studies.</span></span> <span data-ttu-id="8125d-154">与 Unity 页面的 [文本中](../develop/unity/text-in-unity.md) 引入的缩放系数大约为35-40 磅。</span><span class="sxs-lookup"><span data-stu-id="8125d-154">It's about 35-40 pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md) page.</span></span> 

<span data-ttu-id="8125d-155">对于位于 0.45 m (45 厘米) 的近距离交互，最小清晰字体的查看角度和高度为0.4 °-0.5 °/3.14 –3.9 毫米。</span><span class="sxs-lookup"><span data-stu-id="8125d-155">For the near interaction at 0.45 m(45 cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="8125d-156">它大约为 9-12 pt，其中的缩放系数在 [Unity 文本中](../develop/unity/text-in-unity.md)引入。</span><span class="sxs-lookup"><span data-stu-id="8125d-156">It's about 9-12 pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md).</span></span>

<span data-ttu-id="8125d-157">![近和远交互范围内的近和远交互范围 ](images/typography-distance-1000px.jpg)
 *内容*</span><span class="sxs-lookup"><span data-stu-id="8125d-157">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="8125d-158">最小清晰字体大小</span><span class="sxs-lookup"><span data-stu-id="8125d-158">The minimum legible font size</span></span>

| <span data-ttu-id="8125d-159">距离</span><span class="sxs-lookup"><span data-stu-id="8125d-159">Distance</span></span> | <span data-ttu-id="8125d-160">查看角度</span><span class="sxs-lookup"><span data-stu-id="8125d-160">Viewing angle</span></span> | <span data-ttu-id="8125d-161">文本高度</span><span class="sxs-lookup"><span data-stu-id="8125d-161">Text height</span></span> | <span data-ttu-id="8125d-162">字号 \* \*</span><span class="sxs-lookup"><span data-stu-id="8125d-162">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="8125d-163">45厘米 (直接操作距离) </span><span class="sxs-lookup"><span data-stu-id="8125d-163">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="8125d-164">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="8125d-164">0.4°-0.5°</span></span> | <span data-ttu-id="8125d-165">3.14 –3.9 毫米</span><span class="sxs-lookup"><span data-stu-id="8125d-165">3.14–3.9mm</span></span> | <span data-ttu-id="8125d-166">8.9-11.13 pt</span><span class="sxs-lookup"><span data-stu-id="8125d-166">8.9–11.13pt</span></span> |
| <span data-ttu-id="8125d-167">2 m</span><span class="sxs-lookup"><span data-stu-id="8125d-167">2 m</span></span> | <span data-ttu-id="8125d-168">0.35 °0.4 °</span><span class="sxs-lookup"><span data-stu-id="8125d-168">0.35°-0.4°</span></span> | <span data-ttu-id="8125d-169">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="8125d-169">12.21–13.97mm</span></span> | <span data-ttu-id="8125d-170">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="8125d-170">34.63-39.58 pt</span></span> |

### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="8125d-171">可读性更清晰的字号</span><span class="sxs-lookup"><span data-stu-id="8125d-171">The comfortably legible font size</span></span>

| <span data-ttu-id="8125d-172">距离</span><span class="sxs-lookup"><span data-stu-id="8125d-172">Distance</span></span> | <span data-ttu-id="8125d-173">查看角度</span><span class="sxs-lookup"><span data-stu-id="8125d-173">Viewing angle</span></span> | <span data-ttu-id="8125d-174">文本高度</span><span class="sxs-lookup"><span data-stu-id="8125d-174">Text height</span></span> | <span data-ttu-id="8125d-175">字号 \* \*</span><span class="sxs-lookup"><span data-stu-id="8125d-175">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="8125d-176">45厘米 (直接操作距离) </span><span class="sxs-lookup"><span data-stu-id="8125d-176">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="8125d-177">0.65 °0.8 °</span><span class="sxs-lookup"><span data-stu-id="8125d-177">0.65°-0.8°</span></span> | <span data-ttu-id="8125d-178">5.1-6.3 毫米</span><span class="sxs-lookup"><span data-stu-id="8125d-178">5.1-6.3 mm</span></span> | <span data-ttu-id="8125d-179">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="8125d-179">14.47-17.8 pt</span></span> |
| <span data-ttu-id="8125d-180">2 m</span><span class="sxs-lookup"><span data-stu-id="8125d-180">2 m</span></span> | <span data-ttu-id="8125d-181">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="8125d-181">0.6°-0.75°</span></span> | <span data-ttu-id="8125d-182">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="8125d-182">20.9-26.2 mm</span></span> | <span data-ttu-id="8125d-183">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="8125d-183">59.4-74.2 pt</span></span> |


<span data-ttu-id="8125d-184">Segoe UI (Windows) 默认字体在大多数情况下都适用。</span><span class="sxs-lookup"><span data-stu-id="8125d-184">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="8125d-185">避免使用较小尺寸的轻型或半字形系列，因为精简垂直笔划会振动，并将降低清晰度。</span><span class="sxs-lookup"><span data-stu-id="8125d-185">Avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="8125d-186">具有足够笔划粗细的新式字体很好地运行。</span><span class="sxs-lookup"><span data-stu-id="8125d-186">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="8125d-187">例如，Arial 和 Arial 外观丰富多彩，并在 HoloLens 中以常规或粗体权重清晰。</span><span class="sxs-lookup"><span data-stu-id="8125d-187">For example, Helvetica and Arial look gorgeous and are legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="8125d-188">**有关 Unity 中文本大小计算的详细信息，请参阅 [unity 中的文本](../develop/unity/text-in-unity.md)**</span><span class="sxs-lookup"><span data-stu-id="8125d-188">**For more detailed information about text size calculation in Unity, refer to [Text in Unity](../develop/unity/text-in-unity.md)**</span></span>

<span data-ttu-id="8125d-189">![查看角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *查看距离、角度和文本高度*</span><span class="sxs-lookup"><span data-stu-id="8125d-189">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

<br>

---

## <a name="resources"></a><span data-ttu-id="8125d-190">资源</span><span class="sxs-lookup"><span data-stu-id="8125d-190">Resources</span></span>

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[<span data-ttu-id="8125d-191">Segoe 字体</span><span class="sxs-lookup"><span data-stu-id="8125d-191">Segoe fonts</span></span>](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    <span data-ttu-id="8125d-192"> (Zip 文件) </span><span class="sxs-lookup"><span data-stu-id="8125d-192">(Zip file)</span></span><br>
    ### <a name="hololens-fontbr"></a>[<span data-ttu-id="8125d-193">HoloLens 字体</span><span class="sxs-lookup"><span data-stu-id="8125d-193">HoloLens font</span></span>](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    <span data-ttu-id="8125d-194"> (Zip 文件) </span><span class="sxs-lookup"><span data-stu-id="8125d-194">(Zip file)</span></span><br>
    <br>
    <span data-ttu-id="8125d-195">*映像： HoloLens 字体提供 Windows Mixed Reality 中使用的符号字形。*</span><span class="sxs-lookup"><span data-stu-id="8125d-195">*Image: The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.*</span></span>
    :::column-end:::
        :::column:::
        ![HoloLens 字体提供 Windows Mixed Reality 中使用的符号字形](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a><span data-ttu-id="8125d-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8125d-197">See also</span></span>

* [<span data-ttu-id="8125d-198">Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="8125d-198">Text in Unity</span></span>](../develop/unity/text-in-unity.md)
* [<span data-ttu-id="8125d-199">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="8125d-199">Color, light, and materials</span></span>](../color,-light-and-materials.md)
