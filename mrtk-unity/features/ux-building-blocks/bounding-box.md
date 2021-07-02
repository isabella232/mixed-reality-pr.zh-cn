---
title: 边界框
description: MRTK 中的边界框概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 边界框
ms.openlocfilehash: e8e3587ba871e127590a975b688a70db337daa19
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177542"
---
# <a name="bounding-box"></a>边界框

![边界框](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> 边界框已弃用，并替换为其后续 [边界控件](bounds-control.md)。 使用 [迁移选项之一](#migrating-to-bounds-control) 升级现有游戏对象。

该 [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) 脚本提供在混合现实中转换对象的基本功能。 边界框将在全息影像周围显示一个立方体，以指示它可以进行交互。 多维数据集的角和边缘上的句柄允许缩放或旋转对象。 边界框还会响应用户输入。 例如HoloLens 2，边界框响应手指邻近性，提供视觉反馈以帮助感知与对象的距离。 可以轻松自定义所有交互和视觉对象。

有关详细信息，请参阅应用程序[设置中的边界框](/windows/mixed-reality/app-bar-and-bounding-box)Windows 开发人员中心。

## <a name="example-scene"></a>示例场景

可以在场景中找到边界框配置 `BoundingBoxExamples` 的示例。

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>如何使用 Unity Inspector 添加和配置边界框

1. 将 Box 碰撞体添加到对象
2. 将 `BoundingBox` 脚本分配给对象
3. 配置选项，例如"激活"方法 ("检查器 [属性](#inspector-properties) "部分) 
4.  (可选) 为样式边界框分配预制件HoloLens 2材料[ (请参阅下面的](#handle-styles)处理样式) 

> [!NOTE]
> 使用 *检查器* 中的 *"* 目标对象"和"边界替代"字段，分配对象中具有多个子组件的特定对象和碰撞体。

![边界框 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>如何在代码中添加和配置边界框

1. 实例化多维数据集 GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. 使用 `BoundingBox` AddComponent 参数将脚本分配给具有碰撞体<> () 

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. 配置选项 (请参阅下面的 [检查](#inspector-properties) 器属性) 

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1.  (可选) 为样式边界框HoloLens 2预制件和材料。 这仍然需要通过检查器进行分配，因为应该动态加载材料与预制材料。

> [!NOTE]
> 不建议使用 Unity 的"资源"文件夹或 [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 动态加载着色器，因为在运行时可能缺少着色器排列。

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>示例：使用 MinMaxScaleConstraint 设置最小、最大边界框刻度

若要设置最小和最大缩放，请使用 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 。 还可使用 MinMaxScaleConstraint 为 设置最小和最大缩放 [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>示例：在游戏对象周围添加边界框

若要在对象周围添加边界框，只需向该对象 `BoundingBox` 添加组件：

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>检查器属性

### <a name="target-object"></a>“目标对象”

此属性指定边界框操作将转换的对象。 如果未设置对象，则边界框默认为所有者对象。

### <a name="bounds-override"></a>边界替代

为边界计算设置 对象中的盒碰撞体。

### <a name="activation-behavior"></a>激活行为

有几种选项可以激活边界框接口。

* *开始激活*：场景启动后，边界框将变为可见。
* *通过邻近感应激活*：当明确手靠近对象时，边界框将变为可见。
* *通过指针激活*：当边界框以手部射线指针为目标时，该边界框将变为可见。
* *手动激活*：边界框不会自动显示。 可以通过访问 boundingBox.Active 属性通过脚本手动激活它。

### <a name="scale-minimum"></a>最小缩放

允许的最小小数位。 此属性已弃用，最好添加 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 脚本。 如果添加此脚本，则从该脚本（而不是边界框）取最小小数位。

### <a name="scale-maximum"></a>缩放最大值

允许的最大小数位。 此属性已弃用，最好添加 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 脚本。 如果添加此脚本，则从该脚本（而不是边界框）获得最大规模。

### <a name="box-display"></a>框显示

各种边界框可视化选项。

如果将"平展轴"设置为"平展自动"，则脚本将禁止沿具有最小范围轴的操作。 这导致一个 2D 边界框，通常用于精简对象。

### <a name="handles"></a>句柄数

可以分配材料与预制材料来替代句柄样式。 如果未分配任何句柄，这些句柄将显示为默认样式。

## <a name="events"></a>事件

边界框提供以下事件。 此示例使用这些事件播放音频反馈。

* **旋转已启动**：旋转开始时触发。
* **旋转结束**：旋转结束时触发。
* **缩放已** 启动：缩放开始时触发。
* **缩放结束**：缩放结束时触发。

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>句柄样式

默认情况下，当你仅分配脚本时，它将显示第一代HoloLens [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) 句柄。 若要HoloLens 2样式句柄，需要分配适当的句柄预制和材料。

![边界框句柄样式](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

下面是样式边界框句柄的预制HoloLens 2和缩放值。 可以在场景中找到 `BoundingBoxExamples` 此示例。

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>处理 (样式设置HoloLens 2设置) 

* **处理材料**：BoundingBoxHandleWhite.mat
* **处理抓取材料**：BoundingBoxHandleBlueGrabbed.mat
* **缩放句柄预制**：MRTK_BoundingBox_ScaleHandle.prefab
* **缩放句柄 Slate 预制**：MRTK_BoundingBox_ScaleHandle_Slate.prefab
* **缩放句柄大小**：0.016 (1.6cm) 
* **缩放手柄碰撞体填充**：0.016 (使可抓取碰撞体略大于处理可视) 
* **旋转句柄预制**：MRTK_BoundingBox_RotateHandle.prefab
* **旋转句柄大小**：0.016
* **旋转手柄碰撞体填充**：0.016 (使可抓取碰撞体稍微大于处理可视) 

### <a name="proximity-setup-for-hololens-2-style"></a>样式 (的邻近HoloLens 2设置) 

根据与手的距离，使用动画显示和隐藏句柄。 它具有两步缩放动画。

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **邻近效果活动**：启用基于邻近的句柄激活
* **处理中等邻近度**：第一步缩放的距离
* **处理邻近感应**：第 2 步缩放的距离
* **远距**：手超过边界框交互范围时句柄资产的默认缩放值 ("处理中等邻近度"定义的距离。 默认情况下，使用 0 隐藏句柄) 
* **中等比例**：当手位于边界框交互范围内时，句柄资产的缩放值 ("处理近距"定义的距离。 使用 1 显示正常大小) 
* **关闭刻度**：当手在抓取交互范围范围内时，句柄资产 ("句柄邻近度"定义的距离。 使用 1.x 显示更大的) 

## <a name="making-an-object-movable-with-manipulation-handler"></a>使用操作处理程序使对象可移动

边界框可以与 结合使用， [`ManipulationHandler.cs`](manipulation-handler.md) 以使用远交互使对象可移动。 操作处理程序支持一种和两方交互。 可以使用[手动跟踪](../input/hand-tracking.md)来与对象进行交互。

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

为了使边界框边缘在使用远距离交互时以相同的方式运行 [`ManipulationHandler`](manipulation-handler.md) ，建议在操作结束时连接其事件以进行操作  /   `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` ，如以上屏幕截图中所示。

## <a name="migrating-to-bounds-control"></a>迁移到边界控件

使用 [范围框](bounding-box.md) 的现有 prototyping 和实例可以通过 [迁移窗口](../tools/migration-window.md) 升级到新的边界控件，该窗口是 MRTK 工具包的一部分。

对于升级边界框的单个实例，还会在组件的属性检查器中提供一个迁移选项。

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
