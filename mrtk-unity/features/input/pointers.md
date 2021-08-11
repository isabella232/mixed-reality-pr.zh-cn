---
title: 指针
description: 有关 MRTK 中的指针的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 指针，
ms.openlocfilehash: 9fec02e7866aaf867c7145491bfd84f727e039cdd7a4323ace9c65f74e49480a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190970"
---
# <a name="pointers"></a>指针

![指针](../images/pointers/MRTK_Pointer_Main.png)

本文介绍如何在实际操作中配置和响应指针输入，与指针 [体系结构相比](../../architecture/controllers-pointers-and-focus.md)

检测到新控制器时，指针在运行时自动实例。 可以将多个指针附加到控制器。 例如，对于默认指针配置文件，Windows Mixed Reality控制器将分别获取一条线和一个双曲指针，用于正常选择和远程传送。

## <a name="pointer-configuration"></a>指针配置

指针通过 配置为 MRTK 中输入系统的一部分 [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) 。 此类型的配置文件将分配给 [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) MRTK 配置检查器中的 。 指针配置文件确定游标、在运行时可用的指针类型，以及这些指针如何相互通信以决定哪个指针处于活动状态。

- *指向范围* - 定义指针可以与 GameObject 交互的最大距离。

- *指向光线转换层掩码* - 这是一个优先的 LayerMasks 数组，用于确定任何给定指针可以与哪个可能的 GameObject 交互，以及要尝试的交互顺序。 这有助于确保指针先与其他场景对象交互 UI 元素。
![指针配置文件示例](../images/input/pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>指针选项配置

默认的 MRTK 指针配置文件配置包括以下指针类和关联的现用预制项。 在运行时可用于系统的指针列表在指针配置文件中的指针 *选项* 下定义。 开发人员可以利用此列表重新配置现有指针、添加新指针或删除指针。

![指针选项配置文件示例](../images/input/pointers/PointerOptionsProfile.PNG)

每个指针条目由以下一组数据定义：

- *控制器* 类型 - 指针有效的控制器集。
  - 例如， *一个手指* 负责"放大"对象，默认情况下，它标记为仅支持铰接式手部控制器类型。 指针仅在控制器可用时实例化，特别是控制器类型定义可以使用哪些控制器创建此指针预制。

- *手部* - 允许仅为特定手部实例化指针， (/右手) 

> [!NOTE]
> 将 *指针项的"手* 部"属性设置为"无"将有效地从系统禁用该属性，作为从列表中删除该指针的替代方法。

- *指针预制 -* 当开始跟踪与指定控制器类型和手部匹配的控制器时，将实例化此预制资产。

可以有多个与控制器关联的指针。 例如，在 `DefaultHoloLens2InputSystemProfile` (Assets/MRTK/SDK/Profiles/HoloLens2/) 中，已表达手部控制器与 *一个和* *DefaultControllerPointer* (相关联，即 手部射线) 。

> [!NOTE]
> MRTK 在 *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers 中提供一组指针预制项*。 只要它包含 *Assets/MRTK/SDK/Features/UX/Scripts/Pointers* 或实现 的其他任何脚本中的指针脚本之一，就可以生成新的 [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) 自定义预制。

### <a name="default-pointer-classes"></a>默认指针类

以下类是可用的现用 MRTK 指针，在上面概述的默认 *MRTK 指针配置文件* 中定义。 在 *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers* 下提供的每个指针预制件都包含附加的指针组件之一。

![MRTK 默认指针](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>远指针

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 *Base 指针类 LinePointer* 从输入源绘制一条线 (即，控制器) 指针方向，并支持此方向的单个光线投射。 通常，子类（如 和远程端口指针）会实例化并利用 (这些子类还会绘制线条来指示远程传送最终在) 而不是此类（主要提供常见功能）的位置。 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

对于 Oculus、Vive 和 Windows Mixed Reality 等运动控制器，旋转将匹配控制器的旋转。 对于其他控制器HoloLens 2手部，旋转与系统提供的手部指向姿势匹配。

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*CurvePointer* 通过允许沿曲线进行多步光线投射来扩展 *LinePointer* 类。 此基指针类对于曲线实例（如远程传送指针）非常有用，其中直线一直放大到一个双曲中。

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

从 扩展 *的 ShellHandRayPointer* 的实现 [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) 用作 *MRTK* 指针配置文件 的默认实现。 *DefaultControllerPointer* 预制实现 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 类。

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

GGVPointer 也称为凝视/手势/语音 *(GGV)* 指针，主要通过凝视和声调或凝视和语音选择交互为 HoloLens 1 样式的外观和点击交互提供支持。 GGV 指针的位置和方向由头部的位置和旋转驱动。

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

*TouchPointer* 负责处理 Unity Touch 输入 (即触摸屏) 。 这些是"远距离交互"，因为触摸屏幕的行为将光线从相机投射到场景中可能远的位置。

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

*MousePointer* 为屏幕提供世界光线广播，用于进行远场交互，但支持鼠标而不是触摸。

![鼠标指针](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> 鼠标支持在 MRTK 中默认不可用，但可以通过将类型为 的新输入数据提供程序添加到 MRTK 输入配置文件并将 分配给数据提供程序来 [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) 启用。

#### <a name="near-pointers"></a>近指针

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

*[使用可触控](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* 对象与支持"近交互可触摸"的游戏对象进行交互。 是具有附加脚本的 GameObject。 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 对于 UnityUI，此指针查找 NearInteractionTouchableUnityUIs。  该运行器使用 SphereCast 来确定最接近的可触摸元素，并用于为可按下按钮等内容提供电源。

 使用 组件配置 GameObject 时，请确保将 localForward 参数配置为指向按钮或其他应可触摸 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 的对象的前面。  另请确保可触摸对象 *边界与可* 触摸对象边界匹配。

有用的小笔指针属性：

- *TouchableDistance：* 可触摸表面与之交互的最大距离
- *视觉对象：* 用于在手指上 (手指上呈现手指提示视觉对象的游戏对象，默认情况下) 。
- *线条*：从手指绘制到活动输入图面的可选线条。
- *放大层掩码* - 一个优先的 LayerMasks 数组，用于确定指针可以与哪个可能的 GameObject 交互，以及要尝试的交互顺序。 请注意，GameObject 还必须具有 `NearInteractionTouchable` 组件才能与一个指针交互。

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

*[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* 使用 [UnityEngine.Physics.OverlapSphere](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html)来识别最靠近交互的对象，该对象对于"可抓取"输入（如 ） [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 很有用 `ManipulationHandler` 。 与函数对类似，为了与 Sphere 指针交互，游戏对象必须 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 包含作为脚本 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 的组件。

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

有用的 Sphere 指针属性：

- *球体强制转换半径*：用于查询可抓取对象的球体的半径。
- *近对象边距*：球体强制转换半径顶部的距离，用于查询对象是否靠近指针。 总近对象检测半径为球体强制转换半径 + 近对象边距
- *近对象扇区角度*：指针的向前轴周围的角度，用于查询附近的对象。 使 `IsNearObject` 查询函数像一个圆锥体。 默认设置为 66 度，以匹配 Hololens 2 行为

![修改为只查询向前的对象的球体指针](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- *近对象平滑因子*：用于近对象检测的平滑因子。 如果在近对象半径中检测到对象，则查询的半径随后变为"近对象半径 "* (1 + 近对象平滑因子) ，以降低敏感度，使对象更难离开检测范围。
- *抓取层掩码* - 一个优先的 LayerMasks 数组，用于确定指针可以与哪个可能的 GameObject 交互，以及要尝试的交互顺序。 请注意，GameObject 还必须具有 `NearInteractionGrabbable` 与 SpherePointer 交互的 。
    > [!NOTE]
    > 在 MRTK 提供的默认 GrabPointer 预制中禁用空间感知层。 这样做是为了降低对空间网格执行球体重叠查询对性能的影响。 可以通过修改 GrabPointer 预制项来启用此功能。
- *忽略不在 FOV 中的* 碰撞体 - 是否忽略可能在指针附近，但实际上不在可视 FOV 中的碰撞体。
这可以防止意外抓取，并允许手部射线在接近可抓取设备但看不到它时打开。 出于性能原因，Visual *FOV* 是通过圆锥体而不是典型 frustum 定义的。 此圆锥体居中并面向与相机的叶面相同，其半径等于显示高度的一半 (或垂直 FOV) 。

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a>Teleport 指针

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) 在采取操作时，将引发 (请求，即 将按下"远程) 按钮以移动用户。
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) 在采取操作时，将引发 (请求，即 通过双曲线光线) ，将按下 teleport 按钮以移动用户。

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a>混合现实平台的指针支持

下表详细说明了通常用于 MRTK 中常见平台的指针类型。 注意：可以将不同的指针类型添加到这些平台。 例如，可以将一个操作指针或 Sphere 指针添加到 VR。 此外，带游戏板的 VR 设备可以使用 GGV 指针。

|       指针              | OpenVR  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| ShellHandRayPointer | 有效   | 有效                 |            | 有效      |
| TeleportPointer     | 有效   | 有效                 |            |            |
| GGVPointer          |         |                       | 有效      |            |
| SpherePointer       |         |                       |            | 有效      |
| 将Pointer         |         |                       |            | 有效      |

## <a name="pointer-interactions-via-code"></a>通过代码的指针交互

### <a name="pointer-event-interfaces"></a>指针事件接口

实现以下一个或多个接口并分配到具有 的 GameObject 的 MonoBehaviour 将接收由关联接口定义的指针 `Collider` 交互事件。

| 事件 | 说明 | Handler |
| --- | --- | --- |
| 在焦点更改/焦点更改之前 | 在游戏对象失去焦点和每次指针更改焦点时获得焦点时引发。 | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
焦点输入/退出 | 第一个指针进入游戏对象时，在游戏对象上引发，最后一个指针离开游戏对象时失去焦点。 | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
指针向下/拖动/向上/单击 | 引发到报表指针按下、拖动和释放。 | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
Touch Started/Updated/Completed | 由触摸感知指针（如报告触摸 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 活动）引发。 | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler)[`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)和 应在引发它们的对象中进行处理。 可以全局接收焦点事件，但与其他输入事件不同，全局事件处理程序不会基于焦点阻止接收事件 (该事件由全局处理程序和焦点集中的相应对象) 。

#### <a name="pointer-input-events-in-action"></a>操作中的指针输入事件

MRTK 输入系统以类似于常规输入事件 的方式识别并处理指针 [输入事件](input-events.md#input-events-in-action)。 不同之处在于，指针输入事件仅由焦点中的 GameObject 由触发输入事件的指针以及任何全局输入处理程序处理。 常规输入事件由所有活动指针的焦点 GameObject 处理。

1. MRTK 输入系统识别已发生的输入事件
1. MRTK 输入系统将输入事件的相关接口函数激发到所有已注册的全局输入处理程序
1. 输入系统确定哪个 GameObject 是触发事件的指针的焦点
    1. 输入系统利用 Unity 的事件 [系统](https://docs.unity3d.com/Manual/EventSystem.html) 为焦点 GameObject 上的所有匹配组件发射相关的接口函数
    1. 如果输入事件被标记为已用，则[](input-events.md#how-to-stop-input-events)进程将结束，并且不再有 GameObject 接收回调。
        - 示例：实现 接口的组件将搜索 [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) GameObject 增益或失去焦点
        - 注意：如果在当前 GameObject 上找不到与所需接口匹配的组件，Unity 事件系统将向上冒泡以搜索父 GameObject。
1. 如果未注册全局输入处理程序，并且未找到具有匹配组件/接口的 GameObject，则输入系统将调用每个已注册回退的输入处理程序

#### <a name="example"></a>示例

下面是一个示例脚本，该脚本在指针采用或离开焦点或指针选择对象时更改附加呈现器的颜色。

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a>查询指针

可以通过循环访问可用的输入源来收集当前处于活动状态的所有 (，即 控制器和输入) ，以发现哪些指针已附加到它们。

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a>主指针

开发人员可以订阅 FocusProviders PrimaryPointerChanged 事件，在焦点中的主指针发生更改时收到通知。 这非常有助于确定用户当前是否正在通过凝视、手部射线或其他输入源与场景交互。

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

 (`PrimaryPointerExample` Assets/MRTK/Examples/Demos/Input/Scene/PrimaryPointer) 场景演示了如何使用 for 事件来响应 [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) 新的主指针。

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a>指针结果

指针 [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) 属性包含场景查询的当前结果，该结果用于确定具有焦点的对象。 对于光线广播指针，与默认为运动控制器、凝视输入和手部射线创建的指针一样，它将包含光线广播命中的位置和法线。

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

场景 `PointerResultExample` (Assets/MRTK/Examples/Demos/Input/Scene/PointerResult/PointerResultExample.unity) 演示如何使用指针在命中位置生成 [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) 对象。

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a>禁用指针

若要启用和禁用指针 (例如，若要禁用手部射线) ，请通过 设置给定指针 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 类型的 [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) 。

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

有关 [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) 更多 [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 示例，请参阅 和 。

## <a name="pointer-interactions-via-editor"></a>通过编辑器的指针交互

对于由 处理的指针事件，MRTK 提供组件形式的进一步便利，该组件允许通过 Unity 事件直接处理指针 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) 事件。

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a>指针范围

远指针具有设置，用于限制它们光线广播以及与场景中其他对象的交互距离。
默认情况下，此值设置为 10 米。 选择此值是保持与 shell HoloLens一致。

可以通过更新预制件组件的字段 `DefaultControllerPointer` [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 来更改这一点：

*指针* 范围 - 控制指针将与之交互的最大距离。

*默认指针* 范围 - 这控制指针不与任何内容交互时呈现的指针光线/线条的长度。

## <a name="see-also"></a>另请参阅

- [指针体系结构](../../architecture/controllers-pointers-and-focus.md)
- [输入事件数](input-events.md)
