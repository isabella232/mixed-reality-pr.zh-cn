---
title: BoundsControl
description: MRTK 中的边界控制概述
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，边界控制，
ms.openlocfilehash: 65558861955f782cf9d81a8bb4ec3a31dee03fde
ms.sourcegitcommit: 95ea5f3cf873acc93c4614fbccaa093e0f5186f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2021
ms.locfileid: "110487724"
---
# <a name="bounds-control"></a>边界控件

![边界控件](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl* 是先前在 *BoundingBox* 中找到的操作行为的新组件。 界限控制在安装中做出了大量改进和简化，并添加了新功能。 此组件替换为不推荐使用的边界框。

该 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 脚本提供了用于在混合现实中转换对象的基本功能。 边界控件将在全息图周围显示一个框，以指示可以与交互。 框的角部和边缘上的控点允许缩放、旋转或平移对象。 边界控件也会对用户输入做出反应。 例如，在 HoloLens 2 上，边界控制响应手指邻近，提供可视反馈以帮助感觉与对象的距离。 可以轻松地自定义所有交互和视觉对象。

## <a name="example-scene"></a>示例场景

可以在场景中找到界限控制配置的示例 `BoundsControlExamples` 。

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>检查器属性

### <a name="target-object"></a>“目标对象”

此属性指定将由边界控制操作转换的对象。 如果未设置对象，则默认为 owner 对象。

### <a name="activation-behavior"></a>激活行为

有几个选项可用于激活边界控制接口。

* *启动时激活*：启动场景后，边界控制就变得可见。
* "*按邻近范围激活*"：当有向右指的可表述的手势接近对象时，边界控件变为可见。
* *按指针激活*：边界控件在面向手形指针时变为可见。
* *通过邻近感应和指针激活*：边界控件在处于手形指针的目标时变为可见，或在靠近对象的右侧显示。
* *手动激活*：边界控件不会自动变得可见。 可以通过在脚本中访问 boundsControl 属性来手动激活它。

### <a name="bounds-override"></a>界限重写

设置从对象进行边界计算的框碰撞器。

### <a name="box-padding"></a>框填充

向用于计算控件范围的碰撞器边界添加填充。 这不仅会影响交互，还会影响视觉对象。

### <a name="flatten-axis"></a>平展轴

指示控件是否在一个轴中平展，使其成为二维，并在该轴上禁用操作。 此功能可用于清单等精简对象。
如果将 "平展轴" 设置为 " *平整自动* "，脚本会自动选取最小范围的轴作为拼合轴。

### <a name="smoothing"></a>平滑处理

"平滑" 部分允许配置控件缩放和旋转的平滑行为。

### <a name="visuals"></a>视觉对象

可以通过修改相应的视觉对象配置之一来配置边界控件的外观。
视觉对象配置可以是链接或内联的可编写脚本的对象，并在 " [配置对象" 部分](#configuration-objects)更详细地介绍。

## <a name="configuration-objects"></a>配置对象

控件附带一组配置对象，这些对象可存储为可编脚本的对象，并在不同的实例或 prototyping 之间共享。 配置可以作为单个可编脚本的资产文件或 prototyping 中嵌套的可编脚本的资产来共享和链接。 还可以直接在实例上定义进一步的配置，而无需链接到外部或嵌套的可编写脚本的资产。

边界控制检查器将通过在属性检查器中显示一条消息，指示配置是共享还是内联为当前实例的一部分。 此外，共享实例不会直接在 "边界控制" 属性窗口中进行编辑，而是将其链接到的资产直接修改，以避免对共享配置的任何意外更改。

当前界限控制提供以下功能的配置对象选项：

* 句柄数
  * [缩放句柄](#scale-handles-configuration)
  * [旋转控点](#rotation-handles-configuration)
  * [翻译句柄](#translation-handles-configuration)
* [链接/线框](#links-configuration-wireframe)
* [框显示](#box-configuration)
* [邻近效果](#proximity-effect-configuration)

### <a name="box-configuration"></a>Box 配置

Box 配置负责呈现具有通过碰撞器大小和框填充定义的边界的实心框。 可以设置以下属性：

* **Box 材质**：定义在不发生交互时应用于呈现的框的材料。 只有在设置了此材料的情况下，才会呈现框。
* **框获取材料**：用户通过通过近距离或远距离交互进行获取与控件进行交互时，框的材料。
* **平展轴显示比例**：如果其中一个轴为 [平展](#flatten-axis)，则应用于框显示的刻度。

### <a name="scale-handles-configuration"></a>缩放句柄配置

此属性抽屉允许修改界限控制的缩放控点的行为和可视化效果。

* **处理材料**：应用于图柄的材料。
* **处理可处理的材料**：应用到该抓取句柄的材料。
* **处理 prefab**：可选 prefab 作为刻度控点。 如果未设置 MRTK，则会将多维数据集用作默认多维数据集。
* **控点大小**：缩放句柄的大小。
* **碰撞器填充**：要添加到控点碰撞器的填充。
* **操作时绘制接入**：活动时，将从交互点开始到当前手或指针位置绘制接入线。
* **处理忽略碰撞** 器：如果碰撞器在此处链接，则处理将忽略与此碰撞器的任何冲突。
* **处理石板 prefab**：在控件展开后用于该句柄的 prefab。
* **显示刻度控点**：控件句柄的可见性。
* **缩放行为**：可以设置为统一或非均匀缩放。

### <a name="rotation-handles-configuration"></a>旋转控点配置

此配置定义旋转控点的行为。

* **处理材料**：应用于图柄的材料。
* **处理可处理的材料**：应用到该抓取句柄的材料。
* **处理 prefab**：句柄的可选 prefab。 如果设置为 "无"，MRTK 将使用一个球体作为默认值。
* **句柄大小**：句柄的大小。
* **碰撞器填充**：要添加到控点碰撞器的填充。
* **操作时绘制接入**：活动时，将从交互点开始到当前手或指针位置绘制接入线。
* **处理忽略碰撞** 器：如果碰撞器在此处链接，则处理将忽略与此碰撞器的任何冲突。
* **处理 prefab 碰撞器类型**：要与创建的句柄一起使用的碰撞器类型。
* 显示 x 轴的句柄的 X：控件可见性的 **图柄**。
* **显示 y** 轴控点的句柄。
* **显示 z** 轴控点的显示手柄（z）：控件的可见性。

### <a name="translation-handles-configuration"></a>翻译句柄配置

允许为边界控件启用和配置转换句柄。 请注意，每个默认禁用翻译句柄。

* **处理材料**：应用于图柄的材料。
* **处理可处理的材料**：应用到该抓取句柄的材料。
* **处理 prefab**：句柄的可选 prefab。 如果设置为 "无"，MRTK 将使用一个球体作为默认值。
* **句柄大小**：句柄的大小。
* **碰撞器填充**：要添加到控点碰撞器的填充。
* **操作时绘制接入**：活动时，将从交互点开始到当前手或指针位置绘制接入线。
* **处理忽略碰撞** 器：如果碰撞器在此处链接，则处理将忽略与此碰撞器的任何冲突。
* **处理 prefab 碰撞器类型**：要与创建的句柄一起使用的碰撞器类型。
* 显示 x 轴的句柄的 X：控件可见性的 **图柄**。
* **显示 y** 轴控点的句柄。
* **显示 z** 轴控点的显示手柄（z）：控件的可见性。

### <a name="links-configuration-wireframe"></a>链接配置 (线框) 

链接配置启用了边界控件的线框功能。 可以配置以下属性：

* **线框材料**：应用到线框网格的材料。
* **线框边缘半径**：线框的粗细。
* **线框形状**：线框或圆柱形可以是线框的形状。
* **显示线框**：控件线框的可见性。

### <a name="proximity-effect-configuration"></a>邻近效果配置

显示和隐藏带有动画的带动画的图柄。 它具有两步缩放动画。 默认值设置为 "HoloLens 2 样式行为"。

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **邻近效果活动**：启用基于近程的句柄激活
* **对象中等** 距离：第一步缩放的距离
* **对象近** 近：第二步缩放的距离
* **远规模**：当手超出边界控制交互的范围时，句柄资产的默认缩放值 (按 "句柄中等距离" 定义的距离。 默认情况下，使用0隐藏句柄) 
* **中** 度：当手位于边界控件交互范围内时，该手柄资产的缩放值 (按 "句柄接近接近" 定义的距离。 使用1显示正常大小) 
* **关闭规模**：当手处于抓取交互范围内时，句柄资产的缩放值 (按 "句柄接近接近度" 定义的距离。 使用1.x 显示更大的) 
* **远比特率**：向邻近缩放的对象在从中到远的邻近度移动时缩放。
* **中度增长率**：向邻近缩放的对象在手中移动时可缩放。
* **关闭增长速率**：当手从近到对象中心移动时，可缩放邻近缩放对象。

## <a name="constraint-system"></a>约束系统

使用界限控制句柄时，界限控制支持使用 [约束管理器](constraint-manager.md) 来限制或修改翻译、旋转或缩放行为。

属性检查器将在下拉列表中显示附加到同一游戏对象的所有可用约束管理器以及用于滚动和突出显示所选约束管理器的选项。

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>事件

界限控制提供以下事件。 此示例使用这些事件来播放音频反馈。

* **旋转已开始**：旋转开始时激发。
* **旋转停止**：旋转停止时激发。
* **已开始缩放**：缩放开始时激发。
* **缩放已停止**：缩放停止时激发。
* **已开始翻译**：转换开始时激发。
* **转换已停止**：转换停止时激发。

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>池中弹性 (试验性) 

在通过边界控件操作对象时，可以使用池中弹性。 请注意， [池中弹性系统](../elastics/elastic-system.md) 仍处于试验状态。 若要启用池中弹性，请链接现有的池中弹性 manager 组件或通过按钮创建和链接新的池中弹性管理器 `Add Elastics Manager` 。

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>句柄样式

默认情况下，当你只分配 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 脚本时，它将显示 HoloLens 1 代样式的句柄。 若要使用 HoloLens 2 样式句柄，需要分配正确的句柄 prototyping 和材料。

![边界控件句柄样式2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

下面是 HoloLens 2 样式边界控件句柄的 prototyping、材料和缩放值。 您可以在场景中找到此示例 `BoundsControlExamples` 。

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a>为 HoloLens 2 样式处理 (设置) 

* **处理材料**： BoundingBoxHandleWhite
* **处理抓取材料**： BoundingBoxHandleBlueGrabbed
* **缩放句柄 Prefab**： MRTK_BoundingBox_ScaleHandle。 Prefab
* **缩放句柄石板 Prefab**： MRTK_BoundingBox_ScaleHandle_Slate。 Prefab
* **缩放句柄大小**： 0.016 (1.6 厘米) 
* **刻度控点碰撞器填充**： 0.016 (使 grabbable 碰撞器略微大于处理视觉对象) 
* **旋转控点 Prefab**： MRTK_BoundingBox_RotateHandle。 Prefab
* **旋转控点大小**：0.016
* **旋转控点碰撞边距**： 0.016 (使 grabbable 碰撞器略微大于处理视觉对象) 

## <a name="transformation-changes-with-object-manipulator"></a>对象操控器的转换更改

边界控件可以与结合使用 [`ObjectManipulator.cs`](object-manipulator.md) ，以允许某些类型的操作 (例如。 在不使用句柄的情况下移动对象) 。 操作处理程序支持一种和两方交互。 可以使用[手动跟踪](../input/hand-tracking.md)来与对象进行交互。

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

为了使边界控件边缘在使用远距离交互进行移动时以相同的方式运行 [`ObjectManipulator`](object-manipulator.md) ，建议在操作结束时连接其事件以进行操作  /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` ，如以上屏幕截图所示。

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>如何使用 Unity 检查器添加和配置绑定控件

1. 向对象添加框碰撞器
2. 将 `BoundsControl` 脚本分配给对象
3. 配置选项，如 "激活" 方法 (参阅下面的 [检查器属性](#inspector-properties) 部分) 
4.  (可选) 为 HoloLens 2 样式边界控件分配 prototyping 和材料 (参见下面的 " [句柄样式](#handle-styles) " 部分) 

> [!NOTE]
> 使用 "检查器" 中的 " *目标对象* " 和 " *边界替代* " 字段，可以在具有多个子组件的对象中分配特定对象和碰撞器。

![边界控制](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>如何在代码中添加和配置边界控件

1. 实例化 cube GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. `BoundsControl`使用 AddComponent<>，将脚本分配给包含碰撞器的对象 () 

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. 直接在控件上或通过一个可脚本化的配置配置选项 (参阅下面的 [检查器属性](#inspector-properties) 和 [配置](#configuration-objects) 部分) 

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1.  (可选) 为 HoloLens 2 样式边界控件分配 prototyping 和材料。 这仍需要通过检查器进行的分配，因为应该动态加载材料和 prototyping。

> [!NOTE]
> 使用 Unity 的 "资源" 文件夹或 [着色器。]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 不建议查找动态加载着色器，因为在运行时可能会缺少着色器排列。

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>示例：使用 MinMaxScaleConstraint 设置最小值、最大边界控制比例

若要设置最小和最大刻度，请将添加 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 到控件。 当边界控制自动附加和激活约束管理器时，MinMaxScaleConstraint 将自动应用于附加和配置后的转换更改。

还可以使用 MinMaxScaleConstraint 设置的最小和最大刻度 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 。

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>示例：围绕游戏对象添加边界控件

若要在对象周围添加边界控件，只需向 `BoundsControl` 其添加一个组件：

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>从边界框迁移

使用 [范围框](bounding-box.md) 的现有 prototyping 和实例可以通过 [迁移窗口](../tools/migration-window.md) 升级到新的边界控件，该窗口是 MRTK 工具包的一部分。

对于升级边界框的单个实例，还会在组件的属性检查器中提供一个迁移选项。

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>另请参阅

* [对象操控器](object-manipulator.md)
* [约束管理器](constraint-manager.md)
* [迁移时限](../tools/migration-window.md)
* [池中弹性系统 (试验性) ](../elastics/elastic-system.md)
