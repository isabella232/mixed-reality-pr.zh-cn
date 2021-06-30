---
title: 弹性系统
description: 与 MRTK 中的弹性模拟相关的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， ElasticsSystem，
ms.openlocfilehash: 1f90864ee6d3b6756b863de600ade8423a44cacc
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121235"
---
# <a name="elastic-system-experimental"></a>弹性系统 (实验) 

![弹性系统](../images/elastics/Elastics_Main1.gif)

MRTK 附带了一个弹性模拟系统，其中包括各种可扩展且灵活的子类，为四维四元组、三维卷球和简单的线性 spring 系统提供绑定。

目前，以下支持弹性管理器的 MRTK [组件可以利用](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 弹性功能：

- [边界控件](../ux-building-blocks/bounds-control.md)
- [对象操控器](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a>弹性管理器

![弹性系统 2](../images/elastics/Elastics_Main.gif)

弹性管理器处理传递的转换，并馈送到弹性系统中。

可通过两个步骤为自定义组件启用弹性：

1. 在操作开始时调用 Initialize 方法，使用当前主机转换更新系统。
1. 每当应在更新的目标转换上执行弹性计算时查询 ApplyHostTransform。

请注意，一旦操作结束，弹性 (通过弹性管理器更新循环) 。 若要阻止此行为，可以将弹性自动更新 [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) 设置为 false。

默认情况下，将弹性管理器组件添加到游戏对象时，不会为任何转换类型启用弹性。
需要 `Manipulation types using elastic feedback` 为特定转换类型启用 字段，以创建所选类型的弹性配置和区。

### <a name="elastics-configurations"></a>弹性配置

与 [边界控制配置类似](../ux-building-blocks/bounds-control.md#configuration-objects)，弹性管理器附带一组配置对象，这些配置对象可以存储为可编写脚本的对象，并在不同的实例或预制件之间共享。 配置可以共享和链接为单独的可编写脚本的资产文件或预制项内的嵌套可脚本化资产。 还可以直接在实例上定义其他配置，而无需链接到外部或嵌套的可脚本化资产。

弹性管理器检查器将在属性检查器中显示消息，指示配置是作为当前实例的一部分进行共享还是内内。 此外，共享实例不能直接在弹性管理器属性窗口本身中编辑，但必须直接修改它链接到的资产，以避免对共享配置发生任何意外更改。

弹性管理器为以下转换类型提供配置对象选项，其中每种类型都由弹性配置 [对象表示](#elastic-configuration-object)：

- 翻译弹性
- 旋转弹性
- 缩放弹性

#### <a name="elastic-configuration-object"></a>弹性配置对象

弹性配置定义已设置好效果的微分系统的属性。
可以调整以下属性，但 MRTK 中已具有一组默认值：

- **质量**：模拟的中子元素的质量。
- **HandK：** 手部 spring 常量。
- **EndK：** 端帽 spring 常量。
- **SnapK：** 对齐点 spring 常量。
- **拖动**：拖动/拖动系数，与速度成正比。

### <a name="elastics-extents"></a>弹性区

弹性区设置因操作类型而异。 平移和缩放由卷 [弹性区表示](#volume-elastic-extent) ，旋转由四元弹性 [区 表示](#quaternion-elastic-extent)。

#### <a name="volume-elastic-extent"></a>卷弹性区

卷区定义一个三维空间，其中，可随意移动三维空间。

![弹性卷拉伸边界](../images/elastics/Elastics_Volume_Bounds.gif)

- **StretchBounds：** 表示弹性空间的下限。
- **UseBounds：** 系统是否应该遵守拉伸边界。 如果为 true，则当目标位置的当前迭代超出拉伸边界时，将应用结束强制。
- **SnapPoints：** 系统将对齐的空间内的点。
- **RepeatSnapPoints：** 将对齐点重复为无穷大。 现有对齐点将用作模数，其中实际对齐点映射到每个对齐点的最接近的整数倍数。
- **SnapRadius：** 对齐点开始强制 spring 的距离。

![弹性卷对齐网格](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a>四元数弹性区

四元数范围定义一个四维旋转空间，其中三维旋转的四维旋转空间可以自由旋转。

![弹性旋转示例](../images/elastics/Elastics_Rotation.gif)

- **SnapPoints：** 系统将对齐到的欧拉角度。
- **RepeatSnapPoints：** 重复对齐点。 现有对齐点将用作模数，其中实际对齐点映射到每个对齐点的最接近的整数倍数。
- **SnapRadius：** 弧角，对齐点开始强制以欧拉度表示的 spring。

## <a name="elastics-example-scene"></a>弹性示例场景

可以在场景中找到弹性配置 `ElasticSystemExample` 的示例。

![弹性示例场景](../images/elastics/Elastics_Example_Scene.png)
