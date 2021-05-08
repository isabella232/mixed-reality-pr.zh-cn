---
title: Unity 中的文本
description: 若要在 Unity 中显示文本，可以使用两种类型的文本组件：UI 文本和 3D 文本网格。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、设计、控件、字体、版式、ui、ux、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、MRTK、混合现实工具包
ms.openlocfilehash: dde8989998cf422c40ada927c0d8462cb4cd97b9
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489277"
---
# <a name="text-in-unity"></a>Unity 中的文本

文本是全息应用中最重要的组件之一。 若要在 Unity 中显示文本，可以使用三种类型的文本组件：UI 文本、3D 文本网格和文本网格 Pro。 默认情况下，UI 文本和 3D 文本网格看起来模糊且太大。 更改几个变量会导致在 HoloLens 中具有可管理大小的更清晰、质量更高的文本。 通过使用 UI 文本和 3D 文本网格组件时，可以通过应用缩放因子获取适当的维度来实现更好的呈现质量。

![如何获取清晰美观的文本](images/hug-text-02-640px.png)<br>
*Unity 中的模糊默认文本*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>使用 Unity 的 3D 文本 (文本网格) UI 文本

Unity 假定添加到场景中的所有新元素都是一个 Unity 单位，即 100% 转换比例。 一个 Unity 单元在 HoloLens 上转换为大约 1 米。 对于字体，3D TextMesh 的边界框默认以大约 1 米的高度进入。

![在 Unity 中处理字体](images/640px-hug-text-03.png)<br>
*默认 Unity 3D 文本 (文本网格) 占用一个 Unity 单元，即 1 米*

<br>

大多数可视化设计器使用点来定义现实世界中的字号。 2835 (2，834.645666399962) 1 米。 根据点系统转换为 1 米和 Unity 的默认文本网格字号 13，13 除以 2835 的简单数学等于 0.0046 (0.0045861111111116) 这为从 (开始提供了一个很好的标准小数位，其中一些可能希望舍入为 0.005) 。 将文本对象或容器缩放为这些值不仅允许在设计程序中对字体大小进行 1：1 转换，而且还提供一个标准，以便在整个体验中保持一致性。

![Unity 3D 文本和 UI 文本的缩放值](images/Text_In_Unity_Measurements1.png)<br>
*Unity 3D 文本和 UI 文本的缩放值*

<br>

![包含优化值的 Unity 3D 文本网格](images/hug-text-05-1000px.png)<br>
*包含优化值的 Unity 3D 文本网格*

<br>

将基于 UI 或画布的文本元素添加到场景时，大小差异仍为大于。 这两种大小的差异大约为1000%，这会使基于 UI 的文本组件的缩放系数成为 0.00046 (0.0004586111116，以便精确) 或0.0005 舍入值。

![包含优化值的 Unity UI 文本](images/hug-text-04-1000px.png)<br>
*包含优化值的 Unity UI 文本*

<br>

>[!NOTE]
>任何字体的默认值都可能受该字体的纹理大小或字体导入到 Unity 的方式影响。 这些测试是根据 Unity 中默认的 Arial 字体以及另一个导入的字体来执行的。

## <a name="working-with-text-mesh-pro"></a>使用文本网格 Pro

通过 Unity 的文本网格 Pro，可以保护文本呈现质量。 它支持清晰的文本轮廓，而不考虑使用 [带符号距离字段 (.sdf) ](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 方法的距离。 使用我们在上面用于3D 文本网格和 UI 文本的相同计算方法，我们可以找到适当的缩放值，以便与传统排字点一起使用。 由于大小为36的默认3D 文本网格 Pro 字体的边界大小为 2.5 Unity 单位 (2.5 m) ，因此，我们可以使用0.005 值来获取点大小。 UI 菜单下的文本网格 Pro 的默认边界大小为25个 Unity 单位 (25 m) 。 这为缩放值提供了0.0005。

![Unity 3D 文本和 UI 的缩放值](images/Text_In_Unity_Measurements2.png)<br>
*Unity 3D 文本和 UI 的缩放值*

## <a name="recommended-text-size"></a>建议的文本大小

正如你所料，在电脑或平板电脑设备上使用的类型大小 (通常在12–32pt 之间，) 在2米的距离处查看小。 它取决于每种字体的特征，但根据我们的用户研究，建议的最小查看角度和字体高度通常约为 0.35°-0.4°/12.21-13.97 mm。 它大约是 35-40 pt，上面引入了缩放因子。

对于 0.45 m (45 cm) 的近交互，最小可读字体的查看角度和高度为 0.4°-0.5° / 3.14–3.9mm。 它大约是 9-12 pt，上面引入了缩放因子。

![近近交互范围 ](images/typography-distance-1000px.jpg)
 *和远交互范围内容*

### <a name="the-minimum-legible-font-size"></a>最小可读字号

| 距离 | 视角 | 文本高度 | 字体大小 |
|---------|---------|---------|---------|
| 45 cm (操作距离)  | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2 m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>清晰易读的字号

| 距离 | 视角 | 文本高度 | 字体大小 |
|---------|---------|---------|---------|
| 45 cm (操作距离)  | 0.65°-0.8° | 5.1-6.3 毫米 | 14.47-17.8 pt |
| 2 m | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |

Segoe UI (Windows) 默认字体在大多数情况下都适用。 不过，请避免使用较小尺寸的轻型或半字形系列，因为精简垂直笔划将振动，并将降低清晰度。 具有足够笔划粗细的新式字体很好地运行。 例如，Arial 和 Arial 外观丰富多彩，并在 HoloLens 中以常规或粗体权重清晰。

![查看角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *查看距离、角度和文本高度*

## <a name="text-with-mixed-reality-toolkit-v2"></a>带有混合现实工具包 v2 的文本

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>用适当的尺寸锐化文本呈现质量

根据这些缩放因素，我们已 [使用 UI 文本和3D 文本网格创建了文本 prototyping](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)。 开发人员可以使用这些 prototyping 来获得清晰的文本和一致的字体大小。

![用适当的尺寸锐化文本呈现质量](images/hug-text-06-1000px.png)<br>
*用适当的尺寸锐化文本呈现质量*

### <a name="shader-with-occlusion-support"></a>具有封闭支持的着色器

Unity 的默认字体材料不支持封闭。 因此，默认情况下，你会看到对象后面的文本。 我们包含了一个 [支持封闭的简单着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader)。 下图显示了具有默认字体材料的文本 (左侧) 右侧具有适当遮挡 (的文本) 。

![支持遮挡的着色器](images/hug-text-07-1000px.png)<br>
*支持遮挡的着色器*

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发旅程，则你正在探索 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [语音输入](voice-input-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅

* [MRTK 中的文本预制](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [版式](../../design/typography.md)
