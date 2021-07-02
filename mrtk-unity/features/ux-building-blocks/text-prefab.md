---
title: 文本预制
description: MRTK 中的 TextPrefab 概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， TMP，
ms.openlocfilehash: 1839109043cfad9a20697c5d6526b349fd7ea2e4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175645"
---
# <a name="text-prefab"></a><span data-ttu-id="de1a0-104">文本预制</span><span class="sxs-lookup"><span data-stu-id="de1a0-104">Text prefab</span></span>

<span data-ttu-id="de1a0-105">这些预制器针对图像中的呈现质量进行了Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="de1a0-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="de1a0-106">有关详细信息，请阅读 Microsoft Windows 开发人员中心 上的[Unity](/windows/mixed-reality/text-in-unity)中的文本。</span><span class="sxs-lookup"><span data-stu-id="de1a0-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="de1a0-107">预制</span><span class="sxs-lookup"><span data-stu-id="de1a0-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="de1a0-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="de1a0-108">3DTextPrefab</span></span>

<span data-ttu-id="de1a0-109">3D 文本网格预制 (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) ，优化了 2 米距离的缩放因子。</span><span class="sxs-lookup"><span data-stu-id="de1a0-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="de1a0-110"> (请阅读以下说明) </span><span class="sxs-lookup"><span data-stu-id="de1a0-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="de1a0-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="de1a0-111">UITextPrefab</span></span>

<span data-ttu-id="de1a0-112">UI 文本网格预制 (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) ，优化了 2 米距离的缩放因子。</span><span class="sxs-lookup"><span data-stu-id="de1a0-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="de1a0-113"> (请阅读以下说明) </span><span class="sxs-lookup"><span data-stu-id="de1a0-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="de1a0-114">字体</span><span class="sxs-lookup"><span data-stu-id="de1a0-114">Fonts</span></span>

<span data-ttu-id="de1a0-115">混合现实 (中包含的开源字体 (Assets/MRTK/Core/StandardAssets/) Fonts Toolkit。</span><span class="sxs-lookup"><span data-stu-id="de1a0-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de1a0-116">文本预制使用开源字体"Seikik"。</span><span class="sxs-lookup"><span data-stu-id="de1a0-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="de1a0-117">若要使用不同的字体使用文本预制，请导入字体文件，并按照以下说明操作。</span><span class="sxs-lookup"><span data-stu-id="de1a0-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="de1a0-118">以下示例演示如何将"Segoe UI"字体与文本预制。</span><span class="sxs-lookup"><span data-stu-id="de1a0-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![导入Segoe UI字体文件](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="de1a0-120">将字体纹理分配给 3DTextSegoeUI.mat 材料。</span><span class="sxs-lookup"><span data-stu-id="de1a0-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![分配字体纹理](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="de1a0-122">在 3DTextSegoeUI.mat 材料上，选择着色器 Custom/3DTextShader.shader。</span><span class="sxs-lookup"><span data-stu-id="de1a0-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![分配着色器](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="de1a0-124">将Segoe UI字体和 3DTextSegoeUI 材料分配给预制件中的文本组件。</span><span class="sxs-lookup"><span data-stu-id="de1a0-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![分配字体文件和材料](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="de1a0-126">在 Unity 中处理字体</span><span class="sxs-lookup"><span data-stu-id="de1a0-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="de1a0-127">在 Unity 中向场景添加新的 3D TextMesh 时，有两个明显的问题。</span><span class="sxs-lookup"><span data-stu-id="de1a0-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="de1a0-128">一种是字体非常大，二是字体非常模糊。</span><span class="sxs-lookup"><span data-stu-id="de1a0-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="de1a0-129">另请注意，检查器中的默认字号值设置为零。</span><span class="sxs-lookup"><span data-stu-id="de1a0-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="de1a0-130">将这个零值替换为 13 不会显示大小差异，因为 13 实际上是默认值。</span><span class="sxs-lookup"><span data-stu-id="de1a0-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="de1a0-131">Unity 假定添加到场景中的所有新元素的大小为 1 Unity 单位，或 100% 的转换比例，这可转换为场景中大约 1 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="de1a0-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="de1a0-132">对于字体，3D TextMesh 的界限框默认位于大约 1 米的高度。</span><span class="sxs-lookup"><span data-stu-id="de1a0-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="de1a0-133">字号和字号</span><span class="sxs-lookup"><span data-stu-id="de1a0-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="de1a0-134">大多数可视化设计器使用 Points 定义现实世界中的字号及其设计程序。</span><span class="sxs-lookup"><span data-stu-id="de1a0-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="de1a0-135">2835 (2，834.645666399962) 1 米。</span><span class="sxs-lookup"><span data-stu-id="de1a0-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="de1a0-136">根据点系统转换为 1 米和 Unity 的默认 TextMesh 字号 13，13 除以 2835 的简单数学等于 0.0046 (0.004586111111116，精确到) 提供了一个很好的标准小数位，但有些可能希望舍入到 0.005。</span><span class="sxs-lookup"><span data-stu-id="de1a0-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="de1a0-137">无论哪种方式，将 Text 对象或容器缩放为这些值不仅允许从设计程序对字体大小进行 1：1 转换，而且还提供一个标准来在整个应用程序或游戏中保持一致性。</span><span class="sxs-lookup"><span data-stu-id="de1a0-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="de1a0-138">UI 文本</span><span class="sxs-lookup"><span data-stu-id="de1a0-138">UI Text</span></span>

<span data-ttu-id="de1a0-139">将基于 UI 或画布的文本元素添加到场景时，大小差异仍然较大。</span><span class="sxs-lookup"><span data-stu-id="de1a0-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="de1a0-140">这两种大小的差异大约是 1000%，这导致基于 UI 的文本组件的缩放因子为 0.00046 (0.0004586111111116 对于舍入值来说，精确为) 或 0.0005。</span><span class="sxs-lookup"><span data-stu-id="de1a0-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="de1a0-141">**免责声明**：任何字体的默认值都可能会受该字体的纹理大小或该字体导入 Unity 时的效果。</span><span class="sxs-lookup"><span data-stu-id="de1a0-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="de1a0-142">这些测试是根据 Unity 中的默认 Arial 字体以及其他一种导入的字体执行的。</span><span class="sxs-lookup"><span data-stu-id="de1a0-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![具有缩放系数的字体大小](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="de1a0-144">Text3DSe一ik.mat</span><span class="sxs-lookup"><span data-stu-id="de1a0-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="de1a0-145">支持遮挡的 3DTextPrefab 材料。</span><span class="sxs-lookup"><span data-stu-id="de1a0-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="de1a0-146">需要 3DTextShader.shader</span><span class="sxs-lookup"><span data-stu-id="de1a0-146">Requires 3DTextShader.shader</span></span>

![默认字体材料与 3DTextSegoeUI 材料](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="de1a0-148">Text3DShader.shader</span><span class="sxs-lookup"><span data-stu-id="de1a0-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="de1a0-149">支持遮挡的 3DTextPrefab 着色器。</span><span class="sxs-lookup"><span data-stu-id="de1a0-149">Shader for 3DTextPrefab with occlusion support.</span></span>
