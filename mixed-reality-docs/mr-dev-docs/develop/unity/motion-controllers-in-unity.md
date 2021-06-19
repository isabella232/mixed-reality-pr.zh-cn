---
title: Unity 中的运动控制器
description: 了解如何使用 XR 和通用按钮和轴 Api 在 Unity 中通过运动控制器输入采取措施。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 运动控制器，unity，输入，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: d8f9ce292c0ab1cfa89faf58f0e5b90322192b35
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394511"
---
# <a name="motion-controllers-in-unity"></a>Unity 中的运动控制器

您可以通过两种主要方式在您的 [HMD 中进行](gaze-in-unity.md)操作，在 HoloLens 和沉浸式的中的 [手势](../../design/gaze-and-commit.md#composite-gestures) 和 [运动控制器](../../design/motion-controllers.md) 。 可以通过 Unity 中的相同 Api 访问空间输入的两个源的数据。

Unity 提供了两种主要方法来访问 Windows Mixed Reality 的空间输入数据。 常见的 *GetButton/GetAxis* api 跨多个 Unity XR sdk 工作，而特定于 Windows Mixed Reality 的 *InteractionManager/GestureRecognizer* api 会公开一组完整的空间输入数据。

## <a name="unity-xr-input-apis"></a>Unity XR 输入 Api

对于新项目，建议从头开始使用新的 XR 输入 Api。 

可在此处找到有关 [XR api](https://docs.unity3d.com/Manual/xr_input.html)的详细信息。

## <a name="unity-buttonaxis-mapping-table"></a>Unity 按钮/轴映射表

适用于 Windows Mixed Reality 运动控制器的 Unity 输入管理器支持通过 *GetButton/GetAxis* api 在下面列出的按钮和轴 id。 "Windows MR 特定" 列是指 *InteractionSourceState* 类型可用的属性。 以下各节将详细介绍其中的每个 Api。

Windows Mixed Reality 的按钮/轴 ID 映射通常与 Oculus 按钮/轴 Id 匹配。

Windows Mixed Reality 的按钮/轴 ID 映射在以下两个方面不同于 OpenVR 的映射：
1. 该映射使用不同于操纵杆的触摸板 Id，以支持同时具有 thumbsticks 和触摸板的控制器。
2. 映射避免了对菜单按钮的 A 和 X 按钮 Id 进行重载，以使它们可用于物理 ABXY 按钮。

<table>
<tr>
<th rowspan="2">输入 </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">通用 Unity API</a><br /> (GetButton/GetAxis)  </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR 专用输入 API</a><br /> (XR。WSA.输入) </th>
</tr><tr>
<th> 左手 </th><th> 右手</th>
</tr><tr>
<td> 选择触发按下 </td><td> 轴 9 = 1。0 </td><td> 轴 10 = 1。0 </td><td> selectPressed</td>
</tr><tr>
<td> 选择触发器模拟值 </td><td> 轴9 </td><td> 轴10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 选择触发器部分按下 </td><td> 按钮 14 <i> (游戏板兼容) </i> </td><td> 按钮 15 <i> (游戏板兼容) </i> </td><td> selectPressedAmount &gt; 0。0</td>
</tr><tr>
<td> 按下菜单按钮 </td><td> 按钮 6 * </td><td> 按钮 7 * </td><td> menuPressed</td>
</tr><tr>
<td> 按下手柄按钮 </td><td> Axis 11 = 1.0 (没有模拟值) <br />按钮 4 <i> (游戏板兼容) </i> </td><td> 轴 12 = 1.0 (没有模拟值) <br />按钮 5 <i> (游戏板兼容) </i> </td><td> grasped</td>
</tr><tr>
<td> 操纵杆 X <i> (左：-1.0，right： 1.0) </i> </td><td> 轴1 </td><td> 轴4 </td><td> thumbstickPosition</td>
</tr><tr>
<td> 操纵杆 Y <i> (顶部：-1.0、底部： 1.0) </i> </td><td> 轴2 </td><td> 轴5 </td><td> thumbstickPosition</td>
</tr><tr>
<td> 已按下操纵杆 </td><td> 按钮8 </td><td> 按钮9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> 触摸板 X <i> (左：-1.0，右： 1.0) </i> </td><td> 轴 17 * </td><td> 轴 19 * </td><td> touchpadPosition</td>
</tr><tr>
<td> 触摸板 Y <i> (顶部：-1.0、底部： 1.0) </i> </td><td> Axis 18 * </td><td> 轴 20 * </td><td> touchpadPosition</td>
</tr><tr>
<td> 接触触摸板 </td><td> 按钮 18 * </td><td> 按钮 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> 已按触摸板 </td><td> 按钮 16 * </td><td> 按钮 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 手柄姿势或指针姿势 </td><td colspan="2"> 仅限<i>抓握</i>： <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> Pass <i>手柄</i> 或 <i>指针</i> 作为参数： SourceState. sourcePose. TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 跟踪状态 </td><td colspan="2"> <i>位置准确性和源丢失风险仅通过 MR 专用 API 提供</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>这些按钮/轴 Id 不同于 Unity 用于 OpenVR 的 Id，因为 gamepads、Oculus 触控和 OpenVR 所使用的映射中出现冲突。

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->

### <a name="openxr"></a>OpenXR

若要了解有关 Unity 中混合现实交互的基础知识，请访问 unity [手动 For UNITY XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。 此 Unity 文档介绍了从特定于控制器的输入到更可归纳的 **InputFeatureUsage** 的映射，如何识别和分类可用的 XR 输入，如何从这些输入中读取数据等。

Mixed Reality OpenXR 插件提供附加的输入交互配置文件，这些配置文件映射到标准 **InputFeatureUsage**，如下所述：

| InputFeatureUsage | HP 回音 G2 控制器 (OpenXR)  | HoloLens 手型 (OpenXR)  |
| ---- | ---- | ---- |
| primary2DAxis | 操纵杆 | |
| primary2DAxisClick | 游戏杆-单击 | |
| 触发器 | 触发器  | |
| 调整 | 握 | 敲击或敲击 |
| primaryButton | [X/A] - 按 | 隔空敲击 |
| secondaryButton | [Y/B] - 按 | |
| gripButton | 手柄 - 按 | |
| triggerButton | 触发器 - 按 | |
| menuButton | 菜单 | |

## <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指向姿势

Windows Mixed Reality支持各种外形因素中的运动控制器。 每个控制器的设计在用户手部位置与应用在呈现控制器时应该用于指向的自然"向前"方向之间的关系有所不同。

为了更好地表示这些控制器，可以针对每个交互源调查两种类型的姿势：手柄 **姿势** 和 **指针姿势**。 手柄姿势和指针姿势坐标都由全局 Unity 世界坐标的所有 Unity API 表示。

### <a name="grip-pose"></a>手柄姿势

手柄 **姿势** 表示用户手部的位置，由 HoloLens 检测或持有运动控制器。

在沉浸式头戴显示设备中，手柄姿势最适合用于呈现用户手部或用户手 **部中持有的对象**。 在可视化运动控制器时，也使用手柄姿势。 Windows **为运动控制器** 提供的可呈现模型使用手柄姿势作为旋转的原点和中心。

手柄姿势的定义具体如下：
* 手柄 **位置**：自然按住控制器时，通过向左或向右调整以将手柄中的位置居中时，手心中心。 在Windows Mixed Reality控制器上，此位置通常与"抓取"按钮对齐。
* 手柄 **方向的** 右轴：完全打开手形成平面 5 指姿势时，与手部正常的射线从左 (向前，从右手心向后) 
* 手柄方向 **的** 向前轴：当你部分关闭手部 (就像按住控制器) 一样，指向"向前"的射线通过由非滚动手指组成的管道。
* 手柄 **方向的上轴**：右侧和向前定义隐含的向上轴。

可以通过 Unity 的跨供应商输入 API 或 XR 访问手柄 (*[姿势。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation*) 或 Windows MR 特定的 API (*sourceState.sourcePose.TryGetPosition/Rotation，* 请求手柄节点节点的姿势) 。 

### <a name="pointer-pose"></a>指针姿势

指针 **姿势** 表示指向向前的控制器的提示。

在呈现控制器模型本身时，系统提供的指针姿势最适合用于 **光线广播**。 如果要呈现一些其他虚拟对象（例如虚拟照片）来更换控制器，则应该指向该虚拟对象最自然的射线，例如沿应用定义的"手形"模型群移动的射线。 由于用户可以看到虚拟对象，而不是物理控制器，因此使用应用的用户可能更自然地指向虚拟对象。

目前，指针姿势仅在 Unity 中通过特定于 Windows MR 的 API *sourceState.sourcePose.TryGetPosition/Rotation* 提供，并作为参数传递 *InteractionSourceNode.Pointer。*

### <a name="openxr"></a>OpenXR 

可以通过 OpenXR 输入交互访问两组姿势：

* 手柄为在手中呈现对象而造成
* 目的是指向世界。

有关此设计以及两种姿势之间的差异，请参阅 [OpenXR 规范 - 输入子路径](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。

InputFeatureUsages  DevicePosition、DeviceRotation、DeviceVelocity和 **DeviceAngularVelocity** 提供的姿势均表示 OpenXR 手柄姿势。   与手柄姿势相关的 InputFeatureUsages 在 Unity [的 CommonUsages 中定义](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)。

InputFeatureUsages  PointerPosition、PointerRotation、PointerVelocity和 **PointerAngularVelocity** 提供的姿势均表示 OpenXR 目标姿势。   这些 InputFeatureUsages 未在任何包含的 C# 文件中定义，因此需要定义自己的 InputFeatureUsages，如下所示：

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a>Haptics

有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 Unity Manual [for Unity XR Input - Haptics （Unity XR 输入 - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)的 Unity 手册）。

## <a name="controller-tracking-state"></a>控制器跟踪状态

与头戴显示设备一样，Windows Mixed Reality控制器不需要设置外部跟踪传感器。 相反，控制器由头戴显示设备本身的传感器进行跟踪。

如果用户将控制器从头戴显示设备视场中移开，则在大多数情况下，Windows 将继续推断控制器位置。 当控制器丢失视觉跟踪的时间足够长时，控制器的位置将下降至近似准确性位置。

此时，系统会将控制器进行正文锁定，跟踪用户移动时的位置，同时仍使用其内部方向传感器公开控制器的真实方向。 许多使用控制器指向和激活 UI 元素的应用都可以正常运行，同时大致准确无误，而无需用户通知。

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a>有关显式跟踪状态的原因

希望根据跟踪状态以不同方式处理位置的应用可能会进一步检查控制器状态的属性，例如 *SourceLossRisk* 和 *PositionAccuracy*：

<table>
<tr>
<th> 跟踪状态 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>准确度高</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高准确度 (有丢失数据) </b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>近似准确度</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>无位置</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: orange"> false</td>
</tr>
</table>

这些运动控制器跟踪状态的定义如下：
* **高精度：** 虽然运动控制器位于头戴显示设备视场内，但它通常基于视觉跟踪提供高精度位置。 暂时离开视场或被头戴显示设备传感器短暂遮盖（例如，被用户另一手遮挡）的移动控制器) 将基于控制器本身的惯性跟踪，在短时间内继续返回高精度姿势。 (
* **高准确度 (有丢失数据) ：** 当用户将运动控制器移到头戴显示设备视场的边缘之后，头戴显示设备很快就会无法直观地跟踪控制器的位置。 应用通过看到 **SourceLossRisk** 达到 1.0，知道控制器何时到达此 FOV 边界。 此时，应用可以选择暂停需要稳定高质量手势流的控制器手势。
* **近似准确度：** 当控制器丢失视觉跟踪的时间足够长时，控制器的位置将下降至近似准确性位置。 此时，系统会将控制器进行正文锁定，跟踪用户移动时的位置，同时仍使用其内部方向传感器公开控制器的真实方向。 许多使用控制器指向和激活 UI 元素的应用可以正常运行，同时大致准确，无需用户通知。 具有较重输入要求的应用可以选择通过检查 **PositionAccuracy** 属性来检测从"高准确度"到"近似准确度"的下降，例如，在此期间，在屏幕外目标上为用户提供更丰富的命中框。  
* **无位置：** 虽然控制器可以长时间以近似精度运行，但有时系统知道，即使是人体锁定的位置目前也无意义。 例如，打开的控制器可能从未在视觉上观察到，或者用户可能会关闭随后由其他人选取的控制器。 此时，系统不会向应用提供任何位置 *，TryGetPosition* 将返回 false。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>Input.GetButton/GetAxis (的常见 Unity API) 

**命名空间***：UnityEngine、UnityEngine.XR* <br>
**类型**： *输入* *、XR。InputTracking*

Unity 当前使用常规 *Input.GetButton/Input.GetAxis* API 公开 [Oculus](https://docs.unity3d.com/Manual/OculusControllers.html)SDK、OpenVR [SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 和 Windows Mixed Reality 的输入，包括手部和运动控制器。 如果应用使用这些 API 进行输入，则可以轻松地支持跨多个 XR SDK（包括 Windows Mixed Reality）。

### <a name="getting-a-logical-buttons-pressed-state"></a>获取逻辑按钮的按下状态

若要使用常规 Unity 输入 API，通常首先将按钮和轴与 [Unity 输入](https://docs.unity3d.com/Manual/ConventionalGameInput.html)管理器中的逻辑名称连接，将按钮或轴 ID 绑定到每个名称。 然后，可以编写引用该逻辑按钮/轴名称的代码。

例如，若要将左侧运动控制器的触发器按钮映射到"提交"操作，请转到"编辑 **> 项目设置">** Unity 中的"输入"，然后展开"轴"下的"提交"部分的属性。 更改" **正按钮"** 或 **"Alt 正按钮** "属性以读取 **按钮 14，** 如下所示：

![Unity 的 InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

然后，脚本可以使用 *Input.GetButton 检查"提交&quot;操作*：

```cs
if (Input.GetButton(&quot;Submit"))
{
  // ...
}
```
可以通过更改"轴"下的 **"大小"属性来****添加更多逻辑按钮**。

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>直接获取物理按钮的按下状态

还可使用 *Input.GetKey* 按其完全限定名称手动访问按钮：

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>获取手部或运动控制器的姿势

可以使用 XR 访问控制器的位置和 *旋转。InputTracking*：

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> 上面的代码表示控制器的手柄姿势 (其中用户持有控制器) ，这可用于在用户手部或控制器本身的模型中呈现一个手部或手部。
> 
> 此手柄姿势与指针姿势之间的关系 (控制器的指针指向的位置) 控制器之间可能有所不同。 目前，只有通过特定于 MR 的输入 API 才能访问控制器的指针姿势，如以下各节所述。

## <a name="windows-specific-apis-xrwsainput"></a>XR 中特定于 Windows (API。Wsa。输入) 

> [!CAUTION]
> 如果项目正在使用任何 XR。WSA API 正在逐步淘汰，以在将来的 Unity 版本中支持 XR SDK。 对于新项目，我们建议从头开始使用 XR SDK。 可在此处找到有关 [XR 输入系统和 API 详细信息](https://docs.unity3d.com/Manual/xr_input.html)。

**命名空间***：UnityEngine.XR.WSA.Input*<br>
**类型**：InteractionManager、InteractionSourceState、InteractionSource、InteractionSourceProperties、InteractionSourceKind、InteractionSourceLocation      

若要获取有关适用于 HoloLens) 和运动控制器的 Windows Mixed Reality 手动输入 (的更多详细信息，可以选择在 *UnityEngine.XR.WSA.Input* 命名空间下使用特定于 Windows 的空间输入 API。 这使你可以访问其他信息，例如位置准确性或源类型，使你能够将手和控制器分开。

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>轮询手部和运动控制器的状态

可以使用 (*GetCurrentReading* 方法轮询手部或运动控制器) 每个交互源的状态。

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

返回 *的每个 InteractionSourceState* 表示当前时刻的交互源。 *InteractionSourceState* 公开如下信息：
* 选择 [/菜单](../../design/motion-controllers.md) / (/触摸板/Thumbstick) 

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* 特定于运动控制器的其他数据，例如触摸板和/或 thumbstick 的 XY 坐标和触摸状态

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* InteractionSourceKind，用于了解源是手还是运动控制器

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>轮询向前预测的呈现姿势

* 轮询来自手和控制器的交互源数据时，你获取的姿势是向前预测的，此时此帧的光子将到达用户眼睛。  向前预测的姿势最适合用于 **呈现每个** 帧的控制器或持有的对象。  如果以控制器的给定按下或发布为目标，如果使用下面所述的历史事件 API，则最准确。

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* 还可以获取此当前帧的向前预测头部姿势。  与源姿势一样，这可用于呈现光标，不过，如果使用下面所述的历史事件 API，面向给定的按下或发布将最准确。

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>处理交互源事件

若要处理输入事件及其准确的历史姿势数据，可以处理交互源事件，而不是轮询。

处理交互源事件：
* 注册 *InteractionManager* 输入事件。 对于你感兴趣的每种类型的交互事件，需要订阅它。

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* 处理 事件。 订阅交互事件后，将在适当时获取回调。 在 *SourcePressed* 示例中，这将在检测到源之后以及释放或丢失源之前发生。

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>如何停止处理事件

如果不再对事件感兴趣，或者要销毁已订阅该事件的对象，则需要停止处理事件。 若要停止处理事件，请取消订阅该事件。

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>交互源事件列表

可用的交互源事件包括：
* *InteractionSourceDetected (* 源变为活动) 
* *InteractionSourceLost (* 变为非活动) 
* *InteractionSourcePressed* (点击、按下按钮或"选择") 
* *InteractionSourceReleased* (点击结束、按钮释放或"选择"话语结束) 
* *InteractionSourceUpdated (* 移动或以其他方式更改某些状态) 

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>历史目标事件造成与按下或发布最准确的匹配

前面所述的轮询 API 为应用提供前向预测的姿势。  虽然这些预测的姿势最适合呈现控制器或虚拟桌面对象，但未来姿势并不是目标的最佳，有两个关键原因：
* 当用户按下控制器上的按钮时，系统接收按下前，蓝牙上的无线延迟可能约 20 毫秒。
* 然后，如果使用的是前向预测姿势，则还有 10-20 毫秒的向前预测应用于当前帧的光子到达用户眼睛的时间。

这意味着轮询会提供源姿势或头部姿势，向前 30-40 毫秒，从用户头部和手在按下或松开时实际返回的 30-40 毫秒。  对于 HoloLens 手动输入，虽然没有无线传输延迟，但存在类似的处理延迟来检测按下。

若要根据用户对手或控制器按下的原始意图准确定位，应使用该 *InteractionSourcePressed* 或 *InteractionSourceReleased* 输入事件的历史源姿势或头部姿势。

可以使用来自用户头部或控制器的历史姿势数据的按下或释放目标：
* 发生手势或控制器按下时头部姿势，可用于确定用户正在[的目标位置：](../../design/gaze-and-commit.md) 

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* 源在运动控制器按下发生时的姿势，可用于确定用户指向控制器的位置。   这将是遇到按下的控制器的状态。  如果要呈现控制器本身，可以请求指针姿势而不是手柄姿势，以从用户将考虑的呈现控制器的自然提示中发射目标射线：

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>事件处理程序示例

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a>MRTK 中的运动控制器

可以从输入 [管理器访问手势](/windows/mixed-reality/mrtk-unity/features/input/controllers) 和运动控制器。

## <a name="follow-along-with-tutorials"></a>按照教程进行操作

混合现实学院中提供了分步教程和更详细的自定义示例：

- [MR 输入 211：手势](tutorials/holograms-211.md)
- [MR 输入 213：运动控制器](../../deprecated/mixed-reality-213.md)

[![MR 输入 213 - 运动控制器](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*MR 输入 213 - 运动控制器*

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发旅程，则你正在探索 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [手部和眼部跟踪](./hand-eye-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅

* [头部凝视并提交](../../design/gaze-and-commit.md)
* [运动控制器](../../design/motion-controllers.md)