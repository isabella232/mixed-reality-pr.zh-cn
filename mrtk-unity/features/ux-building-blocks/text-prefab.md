---
title: TextPrefab
description: MRTK 中的 TextPrefab 概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， TMP，
ms.openlocfilehash: 7d50a35e3761cf2313a43fcc6ad43ed5bd3064a1
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489287"
---
# <a name="text-prefab"></a><span data-ttu-id="e5e6c-104">文本预制</span><span class="sxs-lookup"><span data-stu-id="e5e6c-104">Text prefab</span></span>

<span data-ttu-id="e5e6c-105">这些预制器针对图像中的呈现质量进行了Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-105">These prefabs are optimized for the rendering quality in Windows Mixed Reality.</span></span> <span data-ttu-id="e5e6c-106">有关详细信息，请阅读 Microsoft Windows 开发人员中心 上的 [Unity](/windows/mixed-reality/text-in-unity) 中的文本。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-106">For more information, please read the guideline [Text in Unity](/windows/mixed-reality/text-in-unity) on Microsoft Windows Dev Center.</span></span>

## <a name="prefabs"></a><span data-ttu-id="e5e6c-107">预制</span><span class="sxs-lookup"><span data-stu-id="e5e6c-107">Prefabs</span></span>

### <a name="3dtextprefab"></a><span data-ttu-id="e5e6c-108">3DTextPrefab</span><span class="sxs-lookup"><span data-stu-id="e5e6c-108">3DTextPrefab</span></span>

<span data-ttu-id="e5e6c-109">3D 文本网格预制 (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) ，优化了 2 米距离的缩放因子。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-109">3D Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="e5e6c-110"> (请阅读以下说明) </span><span class="sxs-lookup"><span data-stu-id="e5e6c-110">(Please read the instructions below)</span></span>

### <a name="uitextprefab"></a><span data-ttu-id="e5e6c-111">UITextPrefab</span><span class="sxs-lookup"><span data-stu-id="e5e6c-111">UITextPrefab</span></span>

<span data-ttu-id="e5e6c-112">UI 文本网格预制 (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) ，优化了 2 米距离的缩放因子。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-112">UI Text Mesh prefab (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) with optimized scaling factor at 2-meter distance.</span></span> <span data-ttu-id="e5e6c-113"> (请阅读以下说明) </span><span class="sxs-lookup"><span data-stu-id="e5e6c-113">(Please read the instructions below)</span></span>

## <a name="fonts"></a><span data-ttu-id="e5e6c-114">字体</span><span class="sxs-lookup"><span data-stu-id="e5e6c-114">Fonts</span></span>

<span data-ttu-id="e5e6c-115">混合现实工具包 (Assets/MRTK/Core/StandardAssets/Fonts) 开源字体。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-115">Open-source fonts (Assets/MRTK/Core/StandardAssets/Fonts) included in Mixed Reality Toolkit.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5e6c-116">文本预制使用开源字体"Seikik"。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-116">Text Prefab uses the open source font 'Selawik'.</span></span> <span data-ttu-id="e5e6c-117">若要使用不同的字体使用文本预制，请导入字体文件，并按照以下说明操作。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-117">To use Text Prefab with a different font, please import the font file and follow the instructions below.</span></span> <span data-ttu-id="e5e6c-118">以下示例演示如何将"Segoe UI"字体与文本预制。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-118">Below example shows how to use 'Segoe UI' font with Text Prefab.</span></span>

![导入Segoe UI字体文件](../images/text-prefab/TextPrefabInstructions01.png)

1. <span data-ttu-id="e5e6c-120">将字体纹理分配给 3DTextSegoeUI.mat 材料。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-120">Assign font texture to 3DTextSegoeUI.mat material.</span></span>

    ![分配字体纹理](../images/text-prefab/TextPrefabInstructions02.png)

1. <span data-ttu-id="e5e6c-122">在3DTextSegoeUI 材料上，选择着色器自定义/3DTextShader。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-122">On 3DTextSegoeUI.mat material, select the shader Custom/3DTextShader.shader.</span></span>

    ![分配着色器](../images/text-prefab/TextPrefabInstructions03.png)

1. <span data-ttu-id="e5e6c-124">向 prototyping 中的文本组件分配 Segoe UI 字体和3DTextSegoeUI 材料。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-124">Assign Segoe UI font and 3DTextSegoeUI material to the text components in the prefabs.</span></span>

    ![分配字体文件和材料](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a><span data-ttu-id="e5e6c-126">在 Unity 中使用字体</span><span class="sxs-lookup"><span data-stu-id="e5e6c-126">Working with Fonts in Unity</span></span>

<span data-ttu-id="e5e6c-127">将新的 3D TextMesh 添加到 Unity 中的场景时，有两个显而易见的问题。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-127">When adding a new 3D TextMesh to a scene in Unity there are two issues that are visually apparent.</span></span> <span data-ttu-id="e5e6c-128">其中一种字体显得非常大，字体显示得非常模糊。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-128">One, the font appears very large and two, the font appears very blurry.</span></span> <span data-ttu-id="e5e6c-129">还需要注意的是，检查器中的默认字体大小值设置为零。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-129">It is also interesting to notice that the default Font Size value is set to zero in the Inspector.</span></span> <span data-ttu-id="e5e6c-130">用13替换此零值将不会显示大小的差异，因为13实际上是默认值。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-130">Replacing this zero value with 13 will show no difference in size, because 13 is actually the default value.</span></span>

<span data-ttu-id="e5e6c-131">Unity 假设添加到场景的所有新元素都是大小为1个 Unity 单元，或为100% 的转换比例，这会在 HoloLens 上转换为约1米。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-131">Unity assumes all new elements added to a scene is 1 Unity Unit in size, or 100%  Transform scale, which translates to about 1 meter on the HoloLens.</span></span> <span data-ttu-id="e5e6c-132">如果是字体，则三维 TextMesh 的边界框会传入，默认情况下，高度约为1米。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-132">In the case of fonts, the bounding box for a 3D TextMesh comes in, by default at about 1 meter in height.</span></span>

### <a name="font-scale-and-font-sizes"></a><span data-ttu-id="e5e6c-133">字体比例和字体大小</span><span class="sxs-lookup"><span data-stu-id="e5e6c-133">Font Scale and Font Sizes</span></span>

<span data-ttu-id="e5e6c-134">大多数可视化设计器都使用点来定义现实世界中的字体大小以及其设计程序。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-134">Most visual designers use Points to define font sizes in the real world, as well as their design programs.</span></span> <span data-ttu-id="e5e6c-135">大约 2835 (2，834.645666399962) 点在1米以内。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-135">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="e5e6c-136">根据点系统转换为1米和 Unity 的默认 TextMesh 字体大小13，将13除以2835的简单数学计算等于 0.0046 (0.004586111116 为完全) 提供一个良好的标准缩放以开始使用，但某些可能要舍入为0.005。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-136">Based on the point system conversion to 1 meter and Unity's default TextMesh Font Size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with, though some may wish to round to 0.005.</span></span>

<span data-ttu-id="e5e6c-137">无论采用哪种方式，将文本对象或容器缩放为这些值，都不会允许1:1 从设计程序转换字体大小，但也提供了标准来保持整个应用程序或游戏的一致性。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-137">Either way, scaling the Text object or container to these values will not only allow for the 1:1 conversion of font sizes from a design program, but also provides a standard to maintain consistency throughout the application or game.</span></span>

### <a name="ui-text"></a><span data-ttu-id="e5e6c-138">UI 文本</span><span class="sxs-lookup"><span data-stu-id="e5e6c-138">UI Text</span></span>

<span data-ttu-id="e5e6c-139">将基于 UI 或画布的文本元素添加到场景时，大小差异仍为大于。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-139">When adding a UI or canvas based Text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="e5e6c-140">这两种大小的差异大约为1000%，这会使基于 UI 的文本组件的缩放系数成为 0.00046 (0.0004586111116，以便精确) 或0.0005 舍入值。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-140">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based Text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="e5e6c-141">**免责声明**：任何字体的默认值都可能受该字体的纹理大小或字体导入到 Unity 的方式影响。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-141">**Disclaimer**: The default value of any font may be effected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="e5e6c-142">这些测试是根据 Unity 中的默认 Arial 字体以及其他一种导入的字体执行的。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-142">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

![具有缩放系数的字体大小](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[<span data-ttu-id="e5e6c-144">Text3DSe一ik.mat</span><span class="sxs-lookup"><span data-stu-id="e5e6c-144">Text3DSelawik.mat</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

<span data-ttu-id="e5e6c-145">支持遮挡的 3DTextPrefab 材料。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-145">Material for 3DTextPrefab with occlusion support.</span></span> <span data-ttu-id="e5e6c-146">需要 3DTextShader.shader</span><span class="sxs-lookup"><span data-stu-id="e5e6c-146">Requires 3DTextShader.shader</span></span>

![默认字体材料与 3DTextSegoeUI 材料](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[<span data-ttu-id="e5e6c-148">Text3DShader.shader</span><span class="sxs-lookup"><span data-stu-id="e5e6c-148">Text3DShader.shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

<span data-ttu-id="e5e6c-149">支持遮挡的 3DTextPrefab 着色器。</span><span class="sxs-lookup"><span data-stu-id="e5e6c-149">Shader for 3DTextPrefab with occlusion support.</span></span>