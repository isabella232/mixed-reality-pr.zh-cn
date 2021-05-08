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
# <a name="text-prefab"></a>文本预制

这些预制器针对图像中的呈现质量进行了Windows Mixed Reality。 有关详细信息，请阅读 Microsoft Windows 开发人员中心 上的 [Unity](/windows/mixed-reality/text-in-unity) 中的文本。

## <a name="prefabs"></a>预制

### <a name="3dtextprefab"></a>3DTextPrefab

3D 文本网格预制 (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) ，优化了 2 米距离的缩放因子。  (请阅读以下说明) 

### <a name="uitextprefab"></a>UITextPrefab

UI 文本网格预制 (Assets/MRTK/SDK/StandardAssets/Prefabs/Text) ，优化了 2 米距离的缩放因子。  (请阅读以下说明) 

## <a name="fonts"></a>字体

混合现实工具包 (Assets/MRTK/Core/StandardAssets/Fonts) 开源字体。

> [!IMPORTANT]
> 文本预制使用开源字体"Seikik"。 若要使用不同的字体使用文本预制，请导入字体文件，并按照以下说明操作。 以下示例演示如何将"Segoe UI"字体与文本预制。

![导入Segoe UI字体文件](../images/text-prefab/TextPrefabInstructions01.png)

1. 将字体纹理分配给 3DTextSegoeUI.mat 材料。

    ![分配字体纹理](../images/text-prefab/TextPrefabInstructions02.png)

1. 在3DTextSegoeUI 材料上，选择着色器自定义/3DTextShader。

    ![分配着色器](../images/text-prefab/TextPrefabInstructions03.png)

1. 向 prototyping 中的文本组件分配 Segoe UI 字体和3DTextSegoeUI 材料。

    ![分配字体文件和材料](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>在 Unity 中使用字体

将新的 3D TextMesh 添加到 Unity 中的场景时，有两个显而易见的问题。 其中一种字体显得非常大，字体显示得非常模糊。 还需要注意的是，检查器中的默认字体大小值设置为零。 用13替换此零值将不会显示大小的差异，因为13实际上是默认值。

Unity 假设添加到场景的所有新元素都是大小为1个 Unity 单元，或为100% 的转换比例，这会在 HoloLens 上转换为约1米。 如果是字体，则三维 TextMesh 的边界框会传入，默认情况下，高度约为1米。

### <a name="font-scale-and-font-sizes"></a>字体比例和字体大小

大多数可视化设计器都使用点来定义现实世界中的字体大小以及其设计程序。 大约 2835 (2，834.645666399962) 点在1米以内。 根据点系统转换为1米和 Unity 的默认 TextMesh 字体大小13，将13除以2835的简单数学计算等于 0.0046 (0.004586111116 为完全) 提供一个良好的标准缩放以开始使用，但某些可能要舍入为0.005。

无论采用哪种方式，将文本对象或容器缩放为这些值，都不会允许1:1 从设计程序转换字体大小，但也提供了标准来保持整个应用程序或游戏的一致性。

### <a name="ui-text"></a>UI 文本

将基于 UI 或画布的文本元素添加到场景时，大小差异仍为大于。 这两种大小的差异大约为1000%，这会使基于 UI 的文本组件的缩放系数成为 0.00046 (0.0004586111116，以便精确) 或0.0005 舍入值。

**免责声明**：任何字体的默认值都可能受该字体的纹理大小或字体导入到 Unity 的方式影响。 这些测试是根据 Unity 中的默认 Arial 字体以及其他一种导入的字体执行的。

![具有缩放系数的字体大小](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSe一ik.mat](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

支持遮挡的 3DTextPrefab 材料。 需要 3DTextShader.shader

![默认字体材料与 3DTextSegoeUI 材料](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader.shader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

支持遮挡的 3DTextPrefab 着色器。