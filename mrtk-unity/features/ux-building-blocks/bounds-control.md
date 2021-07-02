---
title: 边界控件
description: MRTK 中的边界控制概述
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，边界控制，
ms.openlocfilehash: f5f5e1f463f741eb23f75c9826034b8974baf947
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176462"
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
* **句柄忽略碰撞体**：如果碰撞体在此处链接，则句柄将忽略与此碰撞体的任何冲突。
* **处理预制碰撞体类型**：要与创建的句柄一起使用的碰撞体类型。
* **显示 X 的句柄**：控制 X 轴句柄的可见性。
* **显示 Y 的句柄**：控制 Y 轴句柄的可见性。
* **显示 Z 的句柄**：控制 Z 轴句柄的可见性。

### <a name="links-configuration-wireframe"></a>将配置 (线框) 

链接配置启用边界控件的线框功能。 可以配置以下属性：

* **线框材料**：应用于线框网格的材料。
* **线框边缘半径**：线框的粗细。
* **线框形状**：线框的形状可以按三次方或圆条形。
* **显示线框**：控制线框的可见性。

### <a name="proximity-effect-configuration"></a>邻近效果配置

根据与手的距离，使用动画显示和隐藏句柄。 它具有两步缩放动画。 默认设置为HoloLens 2行为。

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **邻近效果活动**：启用基于邻近的句柄激活
* **对象中等邻近度**：第一步缩放的距离
* **对象邻近度**：第二步缩放的距离
* **远距**：手超过边界控制交互范围时，句柄资产的默认缩放值 ("处理中等邻近度"定义的距离。 默认情况下，使用 0 隐藏句柄) 
* **中等比例**：当手在边界控件交互范围范围内时，句柄资产 ("句柄邻近度"定义的距离。 使用 1 显示正常大小) 
* **关闭刻度**：当手在抓取交互范围范围内时，句柄资产 ("句柄邻近度"定义的距离。 使用 1.x 显示更大的) 
* **远距增长速率**：手从中等到远距移动时，对邻近缩放对象缩放的速率。
* **中等增长速率**：当手从中向近移动时，对邻近缩放对象进行缩放的速率。
* **近距增长速率**：当手从靠近对象中心移动时，对邻近缩放的对象缩放速率进行速率。

## <a name="constraint-system"></a>约束系统

边界控件支持 [在使用边界](constraint-manager.md) 控件句柄时使用约束管理器来限制或修改转换、旋转或缩放行为。

属性检查器将在下拉列表中显示附加到同一游戏对象的所有可用约束管理器，并可以选择滚动并突出显示所选约束管理器。

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>事件

边界控件提供以下事件。 此示例使用这些事件播放音频反馈。

* **旋转已启动**：旋转开始时触发。
* **旋转已停止**：在旋转停止时触发。
* **缩放已** 启动：缩放开始时触发。
* **缩放已停止**：缩放停止时触发。
* **翻译已启动**：翻译开始时触发。
* **Translate Stopped：** 在转换停止时触发。

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>弹性 (实验) 

通过边界控件操作对象时，可以使用弹性。 请注意， [弹性系统](../experimental/elastic-system.md) 仍处于试验状态。 若要启用弹性，请链接现有弹性管理器组件，或通过 按钮创建并链接新的弹性 `Add Elastics Manager` 管理器。

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>句柄样式

默认情况下，当你仅分配脚本时，它将显示第一代HoloLens [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 句柄。 若要HoloLens 2样式句柄，需要分配适当的句柄预制和材料。

![边界控件句柄样式 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

下面是样式边界控件句柄的预制HoloLens 2和缩放值。 可以在场景中找到 `BoundsControlExamples` 此示例。

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

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

## <a name="transformation-changes-with-object-manipulator"></a>使用对象操控器进行转换更改

边界控件可以与 结合使用， [`ObjectManipulator.cs`](object-manipulator.md) 以允许某些类型的操作，例如 (操作。 无需使用) 即可移动对象。 操作处理程序支持单手和双手交互。 [手部](../input/hand-tracking.md) 跟踪可用于与接近的对象交互。

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

为了使边界控件边缘在使用 的远端交互移动它时的行为方式相同，建议将其 On [`ObjectManipulator`](object-manipulator.md) Manipulation Started On Manipulation On Manipulation *Started* On  /  *Manipulation 的* 事件分别连接到 ，如上面的屏幕截图 `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` 所示。

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>如何使用 Unity Inspector 添加和配置边界控件

1. 将 Box 碰撞体添加到对象
2. 将 `BoundsControl` 脚本分配给对象
3. 配置选项，例如"激活"方法 ("检查器 [属性](#inspector-properties) "部分) 
4.  (可选) 为样式边界HoloLens 2分配预制件和材料[ (请参阅下面的](#handle-styles)处理样式) 

> [!NOTE]
> 使用 *检查器* 中的 *"* 目标对象"和"边界替代"字段，分配对象中具有多个子组件的特定对象和碰撞体。

![边界控制](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>如何在代码中添加和配置边界控件

1. 实例化多维数据集 GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. 使用 `BoundsControl` AddComponent 参数将脚本分配给具有碰撞体<> () 

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. 直接在控件上或通过其中一个可脚本配置配置选项[ (检查器](#inspector-properties)属性和[配置部分) ](#configuration-objects)

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1.  (可选) 为样式边界控件HoloLens 2预制件和材料。 这仍然需要通过检查器进行分配，因为应该动态加载材料与预制材料。

> [!NOTE]
> 不建议使用 Unity 的"资源"文件夹或 [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 动态加载着色器，因为在运行时可能缺少着色器排列。

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

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>示例：使用 MinMaxScaleConstraint 设置最小、最大边界控制规模

若要设置最小和最大缩放，请将 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 附加到控件。 边界控件自动附加并激活约束管理器，因此 MinMaxScaleConstraint 会在附加和配置转换更改后自动应用于转换更改。

还可使用 MinMaxScaleConstraint 为 设置最小和最大缩放 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 。

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>示例：在游戏对象周围添加边界控件

若要在对象周围添加边界控件，只需向该对象 `BoundsControl` 添加组件：

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>从边界框迁移

使用边界框的现有预制件和实例[](bounding-box.md)可以通过作为 MRTK 工具包一部分的迁移窗口升级到[](../tools/migration-window.md)新的边界控件。

升级边界框的单个实例时，组件的属性检查器中还有一个迁移选项。

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>另请参阅

* [对象操控器](object-manipulator.md)
* [约束管理器](constraint-manager.md)
* [迁移时限](../tools/migration-window.md)
* [弹性系统 (实验) ](../experimental/elastic-system.md)
