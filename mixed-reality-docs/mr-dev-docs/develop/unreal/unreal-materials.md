---
title: Unreal 中的材料建议
description: Unreal 引擎中的材料概述。
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal， Unreal Engine 4， UE4， HoloLens， HoloLens 2， 开发， 材料， 文档， 指南， 功能， 全息影像， 游戏开发， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: d5ce702495c95e8ca6d07a0209a4bc7d02f5d4d682415b028d63995e8910a7e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187689"
---
# <a name="material-recommendations-in-unreal"></a>Unreal 中的材料建议

使用的材料直接影响项目在 Unreal Engine 中的运行性能。 本页充当基本设置的快速入门，你应该使用这些设置从混合现实应用程序中获得最佳性能。

## <a name="using-customizeduvs"></a>使用自定义的UV

如果需要在材料上提供 UV 平铺，请使用 CustomizedUV，而不是直接修改纹理节点的 UV。 自定义的 UV 允许操作顶点着色器中的 UV，而不是像素着色器。

![Unreal 中的材料设置](images/unreal-materials-img-01c.png)

可以在 [Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) 文档和最佳做法示例中找到具体的详细信息，如以下屏幕截图所示：

[ ![ Unreal 推荐材料设置 ](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox) 
 *中推荐的材料设置*

[ ![ ](images/unreal-materials-img-01b.png) Unreal 非推荐](images/unreal-materials-img-01b.png#lightbox)材料设置 
 *中的非推荐材料设置*

## <a name="changing-blend-mode"></a>更改混合模式

建议将混合模式设置为不透明，除非有一个强烈的理由需要这样做。 屏蔽和半透明材料速度缓慢。 有关材料的详细信息，请参阅 [Unreal Engine 文档](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)。

![更改混合模式](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>更新移动设备的照明

应关闭完全精度。 可以通过打开方向信息来向下拨号光图照明。 禁用后，光图的照明将平缓，但成本会更便宜。

![Unreal 中的移动材料设置](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>调整向前着色

这些选项以性能成本提高视觉保真度。 应将其关闭，以提高性能。

![Unreal 中的前向着色材料设置](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>设置材料半透明性

指示半透明材料不应受 bloom 或 DOF 的影响。 由于这两种效果在 MR 中很少见，因此默认情况下应启用此设置。

![Unreal 中的移动单独半透明设置](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>可选设置

以下设置可能会提高性能，但请注意，它们禁用了某些功能。 仅当你确定不需要使用这些功能时才使用这些设置。

![Unreal 中的可选材料设置](images/unreal-materials-img-06.jpg)

如果材料不需要反射或光照，则设置此选项可以极大地提高性能。 在内部测试中，它的速度与"未处理"一样快，同时提供照明信息。

## <a name="best-practices"></a>最佳实践

下面的设置与材料相关的最佳做法不同。

创建参数时，最好尽可能使用"静态参数"。 静态开关可用于删除材料的整个分支，无需运行时成本。 实例可以具有不同的值，因此可以设置模板着色器，而不会降低性能。 缺点是创建了多个会导致着色器重新编译的排列。 尝试最大程度地减少材料中的静态参数数以及所使用的这些静态参数的排列数。 有关呈现材料参数的更多详细信息，请参阅 [Unreal Engine 文档](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)。

![材料设置最佳做法](images/unreal-materials-img-07.jpg)

创建材料实例时，应优先选择"材料实例 **常量"，而** "材料实例动态"。 **材料实例常量** 是一种实例化材料，在运行时之前只计算一次。

通过内容浏览器创建的材料实例 (右键单击> **创建**) 实例常量。 材料实例动态是通过代码创建的。 有关材料实例的更多详细信息，请参阅 [Unreal Engine 文档](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)。

![在 Unreal 中创建材料实例](images/unreal-materials-img-08.png)

关注材料/着色器的复杂性。 可以通过单击"平台统计信息"图标来查看各种平台上的材料成本。 还可以在 [Unreal Engine](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)文档中找到有关材料的详细信息。

![在 Unreal 中创建材料实例动态设置](images/unreal-materials-img-09.png)

可以通过着色器复杂性视图模式 快速了解着色器的相对 [复杂性](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)。

* 视图模式热键：Alt + 8
* 控制台命令：viewmode shadercomplexity

![Unreal 中的材料复杂性](images/unreal-materials-img-10.png)

## <a name="see-also"></a>另请参阅
* [移动材料](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [视图模式](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [材料实例](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
