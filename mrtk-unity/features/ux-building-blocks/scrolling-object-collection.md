---
title: 滚动对象集合
description: 概述菜单类型 MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，滚动对象
ms.openlocfilehash: 0ed1d61aed203a5daa45c5d89990e66115cc3abb
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300112"
---
# <a name="scrolling-object-collection"></a>滚动对象集合

![滚动对象集合](../images/scrolling-collection/ScrollingCollection_Main.jpg)

MRTK 滚动对象集合是一个 UX 组件，通过包含的可查看区域启用3D 内容滚动。 滚动移动可由近或远的输入交互以及离散分页触发。 它支持交互式和非交互式对象。

## <a name="getting-started-with-the-scrolling-object-collection"></a>滚动对象集合入门

### <a name="setting-up-the-scene"></a>设置场景

1. 创建新的 unity 场景。
1. 通过导航到 **混合现实工具包**"  >  **添加到场景" 并配置，** 将 MRTK 添加到场景中。

### <a name="setting-up-the-scrolling-object"></a>设置滚动对象

1. 在场景中创建一个空游戏对象，并将其位置更改为 (0，0，1) 。
1. 向游戏对象添加 [滚动对象集合](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) 组件。

    添加滚动对象集合时，会自动将一个框碰撞器和 [近交互可触摸](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 组件连接到根游戏对象。 这些组件允许 scroll 对象侦听近和远交互输入事件，如指针触摸或单击。  

    MRTK 滚动对象集合具有两个在根滚动对象层次结构下作为子游戏对象创建的重要元素：
    * `Container` -所有滚动内容对象都必须是容器游戏对象的子项。
    * `Clipping bounds` -如果启用了滚动内容屏蔽，则剪辑边界元素可确保仅显示其边界内的可滚动内容。 剪切边界游戏对象包含两个组件：禁用的框碰撞器和 [剪切框](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)。

![滚动对象集合元素](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>向滚动对象添加内容

滚动对象集合可以与 [网格对象集合](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 结合使用，以便在大小和间距相同的对齐元素网格中布局内容。

1. 创建一个空游戏对象作为滚动容器的子级。
1. 向游戏对象添加网格对象集合组件。
1. 对于垂直单列滚动，在 "检查器" 选项卡中，按如下所示配置网格对象集合：
    * **列** 数：1
    * **布局**：列 then 行
    * **定位点**：左上
1. 根据内容对象的尺寸更改 **单元格的宽度** 和 **高度** 。
1. 添加内容对象作为网格对象的子级。
1. 按 " **更新集合**"。

![网格布局](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> 任何滚动内容对象材料必须使用 [MRTK 标准着色器](../rendering/MRTK-standard-shader.md) ，才能使可视区域上的剪辑效果正常工作。

> [!NOTE]
> 如果启用了滚动内容屏蔽，则滚动对象集合将向附加了呈现器的任何内容对象添加 [材料实例](../rendering/material-instance.md) 组件。 此组件用于管理实例材料生存期并提高内存性能。

### <a name="configuring-the-scrolling-viewable-area"></a>配置滚动可查看区域

1. 对于垂直滚动浏览对象的单个列，请在 "检查器" 选项卡中，按如下所示配置滚动对象集合：
    * **单元格/层**：1
    * 根据所需的可见行数选择 **每页的层** 数
1. 根据内容对象的尺寸更改 **页面单元宽度**、 **高度** 和 **深度** 。

请注意，当前已禁用滚动可见区域外的内容对象，而与滚动线框相交的对象可能会被剪辑基元部分屏蔽。

![可视区域](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>在编辑器中测试滚动对象集合

1. 按下 "播放" 并按住空格键以显示输入模拟手。
1. 移动手直到滚动碰撞器或任何滚动交互内容处于焦点状态，并通过单击并上下拖动鼠标并触发滚动移动。

## <a name="controlling-the-scrolling-object-from-code"></a>从代码控制滚动对象

MRTK 滚动对象集合公开了一些公共方法，这些公共方法允许移动滚动容器，方法是根据属性配置对齐滚动容器的位置 `pagination` 。

有关如何访问滚动对象集合分页接口的示例，可在文件夹下使用 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` 。 可 [滚动分页](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) 示例脚本可以链接到场景中的任何现有的滚动对象集合。 然后，该脚本可以由显示 Unity 事件的场景组件引用 (例如， [MRTK 按钮](button.md)) 。

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }       
}
```

## <a name="scrolling-object-collection-properties"></a>滚动对象集合属性

| 常规                                                                                                                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 滚动方向             | 内容应滚动的方向。|

| 分页                   |               说明                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 单元格数               | 向上滚动视图中的行中的单元格数或左侧滚动视图中列的单元格数。                                                                                                         |
| 每页层数               | 滚动区域中可见层的数目。                                                                                                                                                                         |
| 页面单元                    | 分页单元格的尺寸。                  |

| 高级设置            |                  说明                                                                                                                                                                                    |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 掩码编辑模式               | 用于定义剪辑框掩码边界的编辑模式。 选择 "自动" 可自动使用分页值。 选择 "手动" 以启用对剪切框对象的直接操作。|
| 碰撞器编辑模式           | 用于定义滚动交互碰撞器边界的编辑模式。 选择 "自动" 可自动使用分页值。 选择 "手动" 以启用碰撞器的直接操作。|
| 可以滚动                   | 启用/禁用对近/远交互的滚动。                  |
| 在预呈现时使用            | 切换 scrollingObjectCollection 是否将使用摄像 OnPreRender 事件来管理内容可见性。                  |
| 分页曲线             | 用于分页的动画曲线。                  |
| 动画长度             | PaginationCurve 计算所需的时间量，以秒为单位)  (。                  |
| 手动增量滚动阈值  | 在触发滚动拖动之前，当前指针可以沿滚动方向行进的距离（以米为单位）。                  |
| 正面触摸距离         | 定位用于验证在滚动视图前面是否启动了触摸屏交互的本地 xy 平面的距离（以米为单位）。                  |
| 发布阈值            | 从与已释放的触摸开始转换所需的滚动边界，收回量（以米为单位）。                  |

| 速度 |               说明                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 速度类型       | 滚动条的所需速度过渡类型。                                                                                        |
| 速度乘数     | 要应用到滚动条的 (额外) 速度量。                                                                                                                                                        |
| 速度 dampen     | 应用到速度的衰减量。 |
| 弹跳乘数     | 当使用每个帧的衰减或每个项的衰减时，将更多弹跳添加到列表的 overscroll。 |

| 调试选项 |            说明                                                                                                                                                                         |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 掩码已启用       | 滚动内容的可见性模式。 默认值将屏蔽滚动可查看区域之外的所有对象。                                                                                        |
| 显示阈值平面     | 如果为 true，则编辑器将呈现围绕滚动边界的触摸释放阈值平面。                                                                                                                                                        |
| 调试分页     | 使用此部分可在运行时调试滚动分页。 |

| 事件|    说明                                                                                                                                                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 单击时       | 当滚动背景碰撞器或其任何交互式内容收到单击时触发的事件。                                                                                        |
| 开始触控     | 当滚动背景碰撞器或其任何交互式内容收到近交互触摸时触发的事件。                                                                                                                                                        |
| On touch 结束     | 通过使近交互指针跨越某个版本阈值平面终止活动触摸交互时触发的事件。 |
| 起步后     | 滚动容器由交互、速度 fallofff 或分页开始移动时触发的事件。 |
| 在动力结束时     | 滚动容器停止交互、速度 fallofff 或分页时触发的事件。 |

## <a name="scrolling-example-scene"></a>滚动示例场景

**ScrollingObjectCollection** 示例场景包含3个可滚动的示例，每个示例都有不同的速度衰减配置。 示例场景包含用于显示在层次结构中默认禁用的表面布局行为的墙壁。 示例场景可以在文件夹下找到 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` 。

![滚动对象集合示例场景](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>滚动示例 prototyping

为方便起见，可以使用两个滚动对象集合 prototyping。 示例 prototyping 可以在文件夹下找到 ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` 。

![滚动对象集合 prototyping](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>另请参阅

* [剪辑基元](../rendering/clipping-primitive.md)
* [材料实例](../rendering/material-instance.md)
* [标准着色器](../rendering/MRTK-standard-shader.md)
* [对象集合](object-collection.md)
