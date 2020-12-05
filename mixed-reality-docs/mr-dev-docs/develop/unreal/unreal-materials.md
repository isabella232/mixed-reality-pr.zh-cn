---
title: Unreal 中的材料建议
description: Unreal 引擎中的资料概述。
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，开发，材料，文档，指南，功能，全息影像，游戏开发，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 11c10577bd3946facb96fd77b09265ab5ca26f24
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609568"
---
# <a name="material-recommendations-in-unreal"></a>Unreal 中的材料建议

你使用的材料可以直接影响你的项目在 Unreal 引擎中的运行情况。 此页面作为基本设置的快速入门，你应该使用这些设置来获得混合现实应用程序的最佳性能。

## <a name="using-customizeduvs"></a>使用 CustomizedUVs

如果需要对材料提供 UV 拼贴，请使用 CustomizedUVs，而不是直接修改纹理节点的 UV。 CustomizedUVs 使你可以在顶点着色器而不是像素着色器中操作 Uv-11。

![Unreal 中的材料设置](images/unreal-materials-img-01c.png)

可以在以下屏幕截图中的 [Unreal 引擎文档](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) 和最佳做法示例中找到材料详细信息：

建议[ ![ 在 Unreal ](images/unreal-materials-img-01.png) 中设置的材料设置](images/unreal-materials-img-01.png#lightbox) 
 *Recommended material setup*

不建议[ ![ 的材料设置 Unreal ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *不推荐的材料* 设置

## <a name="changing-blend-mode"></a>更改混合模式

除非有很强的理由，否则我们建议将混合模式设置为不透明。 屏蔽和半透明的材料速度缓慢。 有关详细信息，请 [参阅 Unreal 引擎文档](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)。

![更改混合模式](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>更新移动的照明

应关闭完全精度。 可以通过翻方向信息来拔下 Lightmap 照明。 禁用后，lightmaps 中的照明将是平面但更便宜。

![Unreal 中的移动材料设置](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>调整前向底纹

这些选项以性能为代价提高视觉保真。 为了获得最佳性能，应关闭它们。

![Unreal 中的前向底纹材料设置](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>设置材料半透明度

指示半透明材料应不受布隆或 DOF 影响。 由于这两种影响都非常罕见，因此默认情况下此设置应处于启用状态。

![Unreal 中的移动单独半透明度设置](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>可选设置

以下设置可能会提高性能，但请注意，它们会禁用某些功能。 仅当你确定不需要使用这些功能时才使用这些设置。

![Unreal 中的可选材料设置](images/unreal-materials-img-06.jpg)

如果材料不需要反射或闪光，则设置此选项可显著提高性能。 在内部测试中，它的速度与 "unlit" 的速度一样快，同时提供照明信息。

## <a name="best-practices"></a>最佳做法

下面的 "设置" 不是与材料相关的最佳实践。

创建参数时，最好尽可能使用 "静态参数"。 静态开关可用于删除内容的整个分支，而不会产生运行时开销。 实例可以具有不同的值，从而使模板化着色器设置为无性能损失。 缺点是创建了多个将导致重新编译着色器的排列。 尝试最大程度地减少材料中的静态参数数量以及这些静态参数的排列数。 在 [Unreal 引擎文档](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)中，可以找到有关呈现材料参数的更多详细信息。

![材料设置最佳方案](images/unreal-materials-img-07.jpg)

创建材料实例时，应将首选项指定为在 "材料实例动态" 上的 " **材料实例常量** "。 "**材料实例常量**" 是一种在运行时之前只计算一次的实例材料。

通过 "内容浏览器" 创建的材料实例 (**右键单击 > 创建材料实例** ，) 是一个材料实例常量。 通过代码创建 "材料实例动态"。 有关详细信息，请 [参阅 Unreal 引擎文档](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)。

![在 Unreal 中创建材料实例](images/unreal-materials-img-08.png)

密切关注材料/着色器的复杂性。 可以通过单击 "平台统计信息" 图标来查看各种平台上的材料成本。 你还可以在 [Unreal 引擎文档](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)中找到有关材料的更多详细信息。

![在 Unreal 中创建材料实例动态设置](images/unreal-materials-img-09.png)

您可以通过着色器复杂性 [视图模式](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)来快速了解着色器的相对复杂性。

* 查看模式热键： Alt + 8
* 控制台命令： viewmode shadercomplexity

![Unreal 中的材料复杂性](images/unreal-materials-img-10.png)

## <a name="see-also"></a>请参阅
* [移动材料](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [查看模式](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [材料实例](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
