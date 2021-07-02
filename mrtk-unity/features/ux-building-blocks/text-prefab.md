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
# <a name="text-prefab"></a>文本预制

这些预制器针对图像中的呈现质量进行了Windows Mixed Reality。 有关详细信息，请阅读 Microsoft Windows 开发人员中心 上的[Unity](/windows/mixed-reality/text-in-unity)中的文本。

## <a name="prefabs"></a>预制

### <a name="3dtextprefab"></a>3DTextPrefab

3D 文本网格预制 (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) ，优化了 2 米距离的缩放因子。  (请阅读以下说明) 

### <a name="uitextprefab"></a>UITextPrefab

UI 文本网格预制 (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) ，优化了 2 米距离的缩放因子。  (请阅读以下说明) 

## <a name="fonts"></a>字体

混合现实 (中包含的开源字体 (Assets/MRTK/Core/StandardAssets/) Fonts Toolkit。

> [!IMPORTANT]
> 文本预制使用开源字体"Seikik"。 若要使用不同的字体使用文本预制，请导入字体文件，并按照以下说明操作。 以下示例演示如何将"Segoe UI"字体与文本预制。

![导入Segoe UI字体文件](../images/text-prefab/TextPrefabInstructions01.png)

1. 将字体纹理分配给 3DTextSegoeUI.mat 材料。

    ![分配字体纹理](../images/text-prefab/TextPrefabInstructions02.png)

1. 在 3DTextSegoeUI.mat 材料上，选择着色器 Custom/3DTextShader.shader。

    ![分配着色器](../images/text-prefab/TextPrefabInstructions03.png)

1. 将Segoe UI字体和 3DTextSegoeUI 材料分配给预制件中的文本组件。

    ![分配字体文件和材料](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>在 Unity 中处理字体

在 Unity 中向场景添加新的 3D TextMesh 时，有两个明显的问题。 一种是字体非常大，二是字体非常模糊。 另请注意，检查器中的默认字号值设置为零。 将这个零值替换为 13 不会显示大小差异，因为 13 实际上是默认值。

Unity 假定添加到场景中的所有新元素的大小为 1 Unity 单位，或 100% 的转换比例，这可转换为场景中大约 1 HoloLens。 对于字体，3D TextMesh 的界限框默认位于大约 1 米的高度。

### <a name="font-scale-and-font-sizes"></a>字号和字号

大多数可视化设计器使用 Points 定义现实世界中的字号及其设计程序。 2835 (2，834.645666399962) 1 米。 根据点系统转换为 1 米和 Unity 的默认 TextMesh 字号 13，13 除以 2835 的简单数学等于 0.0046 (0.004586111111116，精确到) 提供了一个很好的标准小数位，但有些可能希望舍入到 0.005。

无论哪种方式，将 Text 对象或容器缩放为这些值不仅允许从设计程序对字体大小进行 1：1 转换，而且还提供一个标准来在整个应用程序或游戏中保持一致性。

### <a name="ui-text"></a>UI 文本

将基于 UI 或画布的文本元素添加到场景时，大小差异仍然较大。 这两种大小的差异大约是 1000%，这导致基于 UI 的文本组件的缩放因子为 0.00046 (0.0004586111111116 对于舍入值来说，精确为) 或 0.0005。

**免责声明**：任何字体的默认值都可能会受该字体的纹理大小或该字体导入 Unity 时的效果。 这些测试是根据 Unity 中的默认 Arial 字体以及其他一种导入的字体执行的。

![具有缩放系数的字体大小](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSe一ik.mat](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

支持遮挡的 3DTextPrefab 材料。 需要 3DTextShader.shader

![默认字体材料与 3DTextSegoeUI 材料](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader.shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

支持遮挡的 3DTextPrefab 着色器。
