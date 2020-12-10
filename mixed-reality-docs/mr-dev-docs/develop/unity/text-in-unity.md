---
title: Unity 中的文本
description: 若要在 Unity 中显示文本，可以使用两种类型的文本组件： UI 文本和三维文本网格。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality，设计，控件，字体，版式，ui，ux，混合现实耳机，windows Mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: da2932234793a6db160d3bc2bd6dba02318c83bd
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010488"
---
# <a name="text-in-unity"></a><span data-ttu-id="2248d-104">Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="2248d-104">Text in Unity</span></span>

<span data-ttu-id="2248d-105">文本是全息应用中最重要的组件之一。</span><span class="sxs-lookup"><span data-stu-id="2248d-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="2248d-106">若要在 Unity 中显示文本，可使用三种类型的文本组件： UI 文本、三维文本网格和文本网格 Pro。</span><span class="sxs-lookup"><span data-stu-id="2248d-106">To display text in Unity, there are three types of text components you can use—UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="2248d-107">默认情况下，UI 文本和三维文本网格显示模糊并且太大。</span><span class="sxs-lookup"><span data-stu-id="2248d-107">By default, UI Text and 3D Text Mesh appear blurry and are too large.</span></span> <span data-ttu-id="2248d-108">更改几个变量会导致更清晰、更高质量的文本，在 HoloLens 中可管理。</span><span class="sxs-lookup"><span data-stu-id="2248d-108">Changing a few variables results in sharper, higher-quality text with a manageable size in HoloLens.</span></span> <span data-ttu-id="2248d-109">使用 UI 文本和3D 文本网格组件时，可以通过应用缩放系数来获取适当的尺寸，从而获得更好的渲染质量。</span><span class="sxs-lookup"><span data-stu-id="2248d-109">You can achieve better rendering quality by applying a scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components.</span></span>

<span data-ttu-id="2248d-110">![如何获取明锐而漂亮的文本](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="2248d-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="2248d-111">*Unity 中的默认文本模糊*</span><span class="sxs-lookup"><span data-stu-id="2248d-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a><span data-ttu-id="2248d-112">使用 Unity 的3D 文本 (文本网格) 和 UI 文本</span><span class="sxs-lookup"><span data-stu-id="2248d-112">Working with Unity's 3D Text (Text Mesh) and UI Text</span></span>

<span data-ttu-id="2248d-113">Unity 假设添加到场景中的所有新元素都是一个大小为的 Unity 单元或100% 的变换比例。</span><span class="sxs-lookup"><span data-stu-id="2248d-113">Unity assumes all new elements added to a scene are one Unity Unit in size, or 100% transform scale.</span></span> <span data-ttu-id="2248d-114">一个 Unity 单元在 HoloLens 上转换为约1米。</span><span class="sxs-lookup"><span data-stu-id="2248d-114">One Unity unit translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="2248d-115">对于字体，默认情况下，3D TextMesh 的边界框在大约1米内进入。</span><span class="sxs-lookup"><span data-stu-id="2248d-115">For fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="2248d-116">![在 Unity 中使用字体](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="2248d-116">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="2248d-117">*默认 Unity 3D 文本 (文本网格) 占用一个 Unity 单元（1米）*</span><span class="sxs-lookup"><span data-stu-id="2248d-117">*Default Unity 3D Text (Text Mesh) occupies one Unity Unit, which is 1 meter*</span></span>

<br>

<span data-ttu-id="2248d-118">大多数可视化设计器使用点来定义真实环境中的字体大小。</span><span class="sxs-lookup"><span data-stu-id="2248d-118">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="2248d-119">大约 2835 (2，834.645666399962) 点在1米以内。</span><span class="sxs-lookup"><span data-stu-id="2248d-119">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="2248d-120">根据点系统转换为1米和 Unity 的默认文本网格字体大小13，将13除以2835的简单数学计算为 0.0046 (0.004586111116 为精确) ，这会提供良好的标准缩放， (一些可能需要舍入到 0.005) 。</span><span class="sxs-lookup"><span data-stu-id="2248d-120">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) which provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="2248d-121">在设计程序中，将文本对象或容器缩放为这些值不仅会允许1:1 转换字体大小，而且还可以提供标准，以便您可以保持整个体验的一致性。</span><span class="sxs-lookup"><span data-stu-id="2248d-121">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="2248d-122">![Unity 3D 文本和 UI 文本的缩放值](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="2248d-122">![Scaling values for the Unity 3D Text and UI Text](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="2248d-123">*Unity 3D 文本和 UI 文本的缩放值*</span><span class="sxs-lookup"><span data-stu-id="2248d-123">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<br>

<span data-ttu-id="2248d-124">![包含优化值的 Unity 3D 文本网格](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="2248d-124">![Unity 3D Text Mesh with optimized values](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="2248d-125">*包含优化值的 Unity 3D 文本网格*</span><span class="sxs-lookup"><span data-stu-id="2248d-125">*Unity 3D Text Mesh with optimized values*</span></span>

<br>

<span data-ttu-id="2248d-126">将基于 UI 或画布的文本元素添加到场景时，大小差异仍为大于。</span><span class="sxs-lookup"><span data-stu-id="2248d-126">When adding a UI or canvas-based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="2248d-127">这两种大小的差异大约为1000%，这会使基于 UI 的文本组件的缩放系数成为 0.00046 (0.0004586111116，以便精确) 或0.0005 舍入值。</span><span class="sxs-lookup"><span data-stu-id="2248d-127">The differences in the two sizes are about 1000%, which would bring the scale factor for UI-based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="2248d-128">![包含优化值的 Unity UI 文本](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="2248d-128">![Unity UI Text with optimized values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="2248d-129">*包含优化值的 Unity UI 文本*</span><span class="sxs-lookup"><span data-stu-id="2248d-129">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="2248d-130">任何字体的默认值都可能受该字体的纹理大小或字体导入到 Unity 的方式影响。</span><span class="sxs-lookup"><span data-stu-id="2248d-130">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="2248d-131">这些测试是根据 Unity 中默认的 Arial 字体以及另一个导入的字体来执行的。</span><span class="sxs-lookup"><span data-stu-id="2248d-131">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="2248d-132">使用文本网格 Pro</span><span class="sxs-lookup"><span data-stu-id="2248d-132">Working with Text Mesh Pro</span></span>

<span data-ttu-id="2248d-133">通过 Unity 的文本网格 Pro，可以保护文本呈现质量。</span><span class="sxs-lookup"><span data-stu-id="2248d-133">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="2248d-134">它支持清晰的文本轮廓，而不考虑使用 [带符号距离字段 (.sdf) ](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 方法的距离。</span><span class="sxs-lookup"><span data-stu-id="2248d-134">It supports crisp text outlines regardless of the distance using the [Signed Distance Field (SDF)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="2248d-135">使用我们在上面用于3D 文本网格和 UI 文本的相同计算方法，我们可以找到适当的缩放值，以便与传统排字点一起使用。</span><span class="sxs-lookup"><span data-stu-id="2248d-135">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find the proper scaling values to use with conventional typographic points.</span></span> <span data-ttu-id="2248d-136">由于大小为36的默认3D 文本网格 Pro 字体的边界大小为 2.5 Unity 单位 (2.5 m) ，因此，我们可以使用0.005 值来获取点大小。</span><span class="sxs-lookup"><span data-stu-id="2248d-136">Since the default 3D Text Mesh Pro font with the size of 36 has a bounding size of 2.5 Unity units (2.5 m), we can use a scaling value of 0.005 to get the point size.</span></span> <span data-ttu-id="2248d-137">UI 菜单下的文本网格 Pro 的默认边界大小为25个 Unity 单位 (25 m) 。</span><span class="sxs-lookup"><span data-stu-id="2248d-137">The Text Mesh Pro under the UI menu has a default bounding size of 25 Unity units (25 m).</span></span> <span data-ttu-id="2248d-138">这为缩放值提供了0.0005。</span><span class="sxs-lookup"><span data-stu-id="2248d-138">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="2248d-139">![Unity 3D 文本和 UI 的缩放值](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="2248d-139">![Scaling values for the Unity 3D Text and UI](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="2248d-140">*Unity 3D 文本和 UI 的缩放值*</span><span class="sxs-lookup"><span data-stu-id="2248d-140">*Scaling values for the Unity 3D Text and UI*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="2248d-141">建议的文本大小</span><span class="sxs-lookup"><span data-stu-id="2248d-141">Recommended text size</span></span>
<span data-ttu-id="2248d-142">正如你所料，在电脑或平板电脑设备上使用的类型大小 (通常在12–32pt 之间，) 在2米的距离处查看小。</span><span class="sxs-lookup"><span data-stu-id="2248d-142">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look small at a distance of 2 meters.</span></span> <span data-ttu-id="2248d-143">这取决于每种字体的特征，但通常情况下，建议的最小查看角度和清晰度的字体高度基于用户研究研究0.35 °-0.4 °/12.21-13.97 mm。</span><span class="sxs-lookup"><span data-stu-id="2248d-143">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97 mm based on our user research studies.</span></span> <span data-ttu-id="2248d-144">这与上面介绍的缩放系数大约为35-40 磅。</span><span class="sxs-lookup"><span data-stu-id="2248d-144">It's about 35-40 pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="2248d-145">对于位于 0.45 m (45 厘米) 的近距离交互，最小清晰字体的查看角度和高度为0.4 °-0.5 °/3.14 –3.9 毫米。</span><span class="sxs-lookup"><span data-stu-id="2248d-145">For the near interaction at 0.45 m (45 cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="2248d-146">这与上面介绍的缩放系数大约为9-12 磅。</span><span class="sxs-lookup"><span data-stu-id="2248d-146">It's about 9-12 pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="2248d-147">![近和远交互范围内的近和远交互范围 ](images/typography-distance-1000px.jpg)
 *内容*</span><span class="sxs-lookup"><span data-stu-id="2248d-147">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="2248d-148">最小清晰字体大小</span><span class="sxs-lookup"><span data-stu-id="2248d-148">The minimum legible font size</span></span>
| <span data-ttu-id="2248d-149">距离</span><span class="sxs-lookup"><span data-stu-id="2248d-149">Distance</span></span> | <span data-ttu-id="2248d-150">查看角度</span><span class="sxs-lookup"><span data-stu-id="2248d-150">Viewing angle</span></span> | <span data-ttu-id="2248d-151">文本高度</span><span class="sxs-lookup"><span data-stu-id="2248d-151">Text height</span></span> | <span data-ttu-id="2248d-152">字体大小</span><span class="sxs-lookup"><span data-stu-id="2248d-152">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="2248d-153">45厘米 (直接操作距离) </span><span class="sxs-lookup"><span data-stu-id="2248d-153">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="2248d-154">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="2248d-154">0.4°-0.5°</span></span> | <span data-ttu-id="2248d-155">3.14 –3.9 毫米</span><span class="sxs-lookup"><span data-stu-id="2248d-155">3.14–3.9mm</span></span> | <span data-ttu-id="2248d-156">8.9-11.13 pt</span><span class="sxs-lookup"><span data-stu-id="2248d-156">8.9–11.13pt</span></span> |
| <span data-ttu-id="2248d-157">2 m</span><span class="sxs-lookup"><span data-stu-id="2248d-157">2 m</span></span> | <span data-ttu-id="2248d-158">0.35 °0.4 °</span><span class="sxs-lookup"><span data-stu-id="2248d-158">0.35°-0.4°</span></span> | <span data-ttu-id="2248d-159">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="2248d-159">12.21–13.97mm</span></span> | <span data-ttu-id="2248d-160">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="2248d-160">34.63-39.58 pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="2248d-161">可读性更清晰的字号</span><span class="sxs-lookup"><span data-stu-id="2248d-161">The comfortably legible font size</span></span>
| <span data-ttu-id="2248d-162">距离</span><span class="sxs-lookup"><span data-stu-id="2248d-162">Distance</span></span> | <span data-ttu-id="2248d-163">查看角度</span><span class="sxs-lookup"><span data-stu-id="2248d-163">Viewing angle</span></span> | <span data-ttu-id="2248d-164">文本高度</span><span class="sxs-lookup"><span data-stu-id="2248d-164">Text height</span></span> | <span data-ttu-id="2248d-165">字体大小</span><span class="sxs-lookup"><span data-stu-id="2248d-165">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="2248d-166">45厘米 (直接操作距离) </span><span class="sxs-lookup"><span data-stu-id="2248d-166">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="2248d-167">0.65 °0.8 °</span><span class="sxs-lookup"><span data-stu-id="2248d-167">0.65°-0.8°</span></span> | <span data-ttu-id="2248d-168">5.1-6.3 毫米</span><span class="sxs-lookup"><span data-stu-id="2248d-168">5.1-6.3 mm</span></span> | <span data-ttu-id="2248d-169">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="2248d-169">14.47-17.8 pt</span></span> |
| <span data-ttu-id="2248d-170">2 m</span><span class="sxs-lookup"><span data-stu-id="2248d-170">2 m</span></span> | <span data-ttu-id="2248d-171">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="2248d-171">0.6°-0.75°</span></span> | <span data-ttu-id="2248d-172">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="2248d-172">20.9-26.2 mm</span></span> | <span data-ttu-id="2248d-173">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="2248d-173">59.4-74.2 pt</span></span> |

<span data-ttu-id="2248d-174">Segoe UI (Windows) 默认字体在大多数情况下都适用。</span><span class="sxs-lookup"><span data-stu-id="2248d-174">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="2248d-175">不过，请避免使用较小尺寸的轻型或半字形系列，因为精简垂直笔划将振动，并将降低清晰度。</span><span class="sxs-lookup"><span data-stu-id="2248d-175">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="2248d-176">具有足够笔划粗细的新式字体很好地运行。</span><span class="sxs-lookup"><span data-stu-id="2248d-176">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="2248d-177">例如，Arial 和 Arial 外观丰富多彩，并在 HoloLens 中以常规或粗体权重清晰。</span><span class="sxs-lookup"><span data-stu-id="2248d-177">For example, Helvetica and Arial look gorgeous and are legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="2248d-178">![查看角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *查看距离、角度和文本高度*</span><span class="sxs-lookup"><span data-stu-id="2248d-178">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="text-with-mixed-reality-toolkit-v2"></a><span data-ttu-id="2248d-179">带有混合现实工具包 v2 的文本</span><span class="sxs-lookup"><span data-stu-id="2248d-179">Text with Mixed Reality Toolkit v2</span></span>

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="2248d-180">用适当的尺寸锐化文本呈现质量</span><span class="sxs-lookup"><span data-stu-id="2248d-180">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="2248d-181">根据这些缩放因素，我们已 [使用 UI 文本和3D 文本网格创建了文本 prototyping](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)。</span><span class="sxs-lookup"><span data-stu-id="2248d-181">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="2248d-182">开发人员可以使用这些 prototyping 来获得清晰的文本和一致的字体大小。</span><span class="sxs-lookup"><span data-stu-id="2248d-182">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="2248d-183">![用适当的尺寸锐化文本呈现质量](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="2248d-183">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="2248d-184">*用适当的尺寸锐化文本呈现质量*</span><span class="sxs-lookup"><span data-stu-id="2248d-184">*Sharp text rendering quality with proper dimension*</span></span>

### <a name="shader-with-occlusion-support"></a><span data-ttu-id="2248d-185">具有封闭支持的着色器</span><span class="sxs-lookup"><span data-stu-id="2248d-185">Shader with occlusion support</span></span>

<span data-ttu-id="2248d-186">Unity 的默认字体材料不支持封闭。</span><span class="sxs-lookup"><span data-stu-id="2248d-186">Unity's default font material doesn't support occlusion.</span></span> <span data-ttu-id="2248d-187">因此，默认情况下，你会看到对象后面的文本。</span><span class="sxs-lookup"><span data-stu-id="2248d-187">Because of this, you'll see the text behind the objects by default.</span></span> <span data-ttu-id="2248d-188">我们包含了一个 [支持封闭的简单着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader)。</span><span class="sxs-lookup"><span data-stu-id="2248d-188">We've included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="2248d-189">下图显示了默认字体材料 (左) 的文本，以及具有适当封闭 (右) 的文本。</span><span class="sxs-lookup"><span data-stu-id="2248d-189">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="2248d-190">![具有封闭支持的着色器](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="2248d-190">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="2248d-191">*具有封闭支持的着色器*</span><span class="sxs-lookup"><span data-stu-id="2248d-191">*Shader with occlusion support*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2248d-192">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="2248d-192">Next Development Checkpoint</span></span>

<span data-ttu-id="2248d-193">如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="2248d-193">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="2248d-194">从这里，你可以继续执行下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="2248d-194">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2248d-195">语音输入</span><span class="sxs-lookup"><span data-stu-id="2248d-195">Voice input</span></span>](voice-input-in-unity.md)

<span data-ttu-id="2248d-196">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="2248d-196">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2248d-197">共享体验</span><span class="sxs-lookup"><span data-stu-id="2248d-197">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="2248d-198">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="2248d-198">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="2248d-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2248d-199">See also</span></span>
* [<span data-ttu-id="2248d-200">MRTK 中的文本 Prefab</span><span class="sxs-lookup"><span data-stu-id="2248d-200">Text Prefab in the MRTK</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="2248d-201">版式</span><span class="sxs-lookup"><span data-stu-id="2248d-201">Typography</span></span>](../../design/typography.md)
