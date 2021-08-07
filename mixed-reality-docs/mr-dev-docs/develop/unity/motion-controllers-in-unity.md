---
title: Unity 中的运动控制器
description: 了解如何使用 XR 和常用按钮和轴 API 通过运动控制器输入在 Unity 中对凝视采取措施。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 运动控制器、unity、输入、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、MRTK、混合现实Toolkit
ms.openlocfilehash: ccda5b11190e829ccc655989a6f679ef6ef647a920c01a3182548b23a3d85084
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216234"
---
# <a name="motion-controllers-in-unity"></a>Unity 中的运动控制器

在[Unity](gaze-in-unity.md)中，有两种对凝视采取措施的关键[](../../design/gaze-and-commit.md#composite-gestures)方法：手势和[](../../design/motion-controllers.md)运动控制器HoloLens沉浸式 HMD。 可以通过 Unity 中的相同 API 访问两个空间输入源的数据。

Unity 提供了两种主要方法来访问数据空间输入Windows Mixed Reality。 常见的 *Input.GetButton/Input.GetAxis* API 可跨多个 Unity XR SDK 工作，而特定于 Windows Mixed Reality 的 *InteractionManager/GestureRecognizer* API 则公开一组完整的空间输入数据。

## <a name="unity-xr-input-apis"></a>Unity XR 输入 API

对于新项目，我们建议从头开始使用新的 XR 输入 API。 

可在此处找到 [有关 XR API 详细信息](https://docs.unity3d.com/Manual/xr_input.html)。

## <a name="unity-buttonaxis-mapping-table"></a>Unity 按钮/轴映射表

用于运动控制器的 Unity Windows Mixed Reality通过 *Input.GetButton/GetAxis* API 支持下面列出的按钮和轴 ID。 "Windows MR 特定的"列是指 *InteractionSourceState* 类型中可用的属性。 以下各部分详细介绍了其中每个 API。

按钮/轴 ID 映射通常Windows Mixed Reality Oculus 按钮/轴 ID 匹配。

用于存储的按钮/轴 ID Windows Mixed Reality两个方面与 OpenVR 的映射不同：
1. 映射使用与 thumbstick 不同的触摸板 ID 来支持具有指纹和触摸板的控制器。
2. 映射可避免重载菜单按钮的 A 和 X 按钮 ID，使它们可用于物理 ABXY 按钮。

<table>
<tr>
<th rowspan="2">输入 </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">通用 Unity API</a><br /> (Input.GetButton/GetAxis)  </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows特定于 MR 的输入 API</a><br /> (XR。Wsa。输入) </th>
</tr><tr>
<th> 左侧 </th><th> 右侧</th>
</tr><tr>
<td> 选择按下的触发器 </td><td> 轴 9 = 1.0 </td><td> 轴 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> 选择触发器模拟值 </td><td> 轴 9 </td><td> 轴 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 选择部分按下的触发器 </td><td> 按钮 14 <i> (游戏板) </i> </td><td> 游戏板<i> (按钮</i>15)  </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> 按下菜单按钮 </td><td> 按钮 6* </td><td> 按钮 7* </td><td> menuPressed</td>
</tr><tr>
<td> 按下手柄按钮 </td><td> 轴 11 = 1.0 (无模拟) <br />按钮 4 <i> (游戏板) </i> </td><td> 轴 12 = 1.0 (无模拟) <br />按钮 5 <i> (游戏板) </i> </td><td> 抓住</td>
</tr><tr>
<td> Thumbstick X <i> (左侧：-1.0、右侧：1.0) </i> </td><td> 轴 1 </td><td> 轴 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Thumbstick Y <i> (top： -1.0， bottom： 1.0) </i> </td><td> 轴 2 </td><td> 轴 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> 已按下 Thumbstick </td><td> 按钮 8 </td><td> 按钮 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i> (左侧：-1.0、右侧：1.0) </i> </td><td> 轴 17* </td><td> 轴 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> 触控板 Y <i> (顶部：-1.0，底部：1.0) </i> </td><td> 轴 18* </td><td> 轴 20* </td><td> touchpadPosition.y</td>
</tr><tr>
<td> 触摸的触摸板 </td><td> 按钮 18* </td><td> 按钮 19* </td><td> touchpadTouched</td>
</tr><tr>
<td> 已按下触摸板 </td><td> 按钮 16* </td><td> 按钮 17* </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 手柄姿势或指针姿势 </td><td colspan="2"> <i>仅</i> 手柄姿势 <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">：XR。InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR。InputTracking.GetLocalRotation</a></td><td> 将 <i>手柄</i> 或 <i>指针作为</i> 参数传递：sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 跟踪状态 </td><td colspan="2"> <i>位置准确性和源丢失风险仅通过特定于 MR 的 API 提供</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>由于游戏板、Oculus Touch 和 OpenVR 使用的映射发生冲突，这些按钮/轴的ID 不同于 Unity 用于 OpenVR 的ID。

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

若要了解有关 Unity 中混合现实交互的基础知识，请访问 [Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)输入的 Unity 手册。 此 Unity 文档介绍了从控制器特定的输入到更通用 **InputFeatureUsage** 的映射、如何标识和分类可用的 XR 输入、如何从这些输入读取数据，等等。

混合现实 OpenXR 插件提供映射到标准 **InputFeatureUsage** 的其他输入交互配置文件，如下所示：

| InputFeatureUsage | HP Reverb G2 控制器 (OpenXR)  | HoloLens手动 (OpenXR)  |
| ---- | ---- | ---- |
| primary2DAxis | 操纵 杆 | |
| primary2DAxisClick | 下一步 - 单击 | |
| 触发器 | 触发器  | |
| 握 | 调整 | 空中分流或挤压 |
| primaryButton | [X/A]-按 | 隔空敲击 |
| secondaryButton | [Y/B]-按 | |
| gripButton | 手柄-按 | |
| triggerButton | 触发器-按 | |
| menuButton | 菜单 | |

## <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指针姿势

Windows Mixed Reality 支持采用各种外形规格的运动控制器。 每个控制器的设计不同于用户的位置与应用在呈现控制器时使用的自然 "转发" 方向之间的关系。

为了更好地表示这些控制器，可以针对每个交互源来调查两种类型的姿势， **手柄姿势** 和 **指针姿势**。 手柄姿势和指针姿势坐标都由全局 Unity 世界坐标中的所有 Unity Api 表示。

### <a name="grip-pose"></a>抓握姿势

**抓握姿势** 表示用户掌的位置，由 HoloLens 检测到或持有运动控制器。

在沉浸式耳机上，手柄姿势最适合用于呈现 **用户的手** 或 **持有用户的对象**。 可视化运动控制器时也使用手柄姿势。 用于运动控制器 Windows 提供的 **呈现模型** 使用手柄姿势作为原点和旋转中心。

手柄姿势的定义具体如下：
* **手柄位置**：在固定控制器时，掌上质心，向左或向右调整以使其在手柄内居中。 在 Windows Mixed Reality 运动控制器上，此位置通常与 "抓住" 按钮对齐。
* **手柄方向的右轴**：当你完全打开手形成一个平面的5指形姿势时，与你的掌上的光线 (从右手掌向后) 
* **手柄方向的正向轴**：当您关闭手中的部分 (时，就如同按住控制器) 一样，通过您的非拇指形来表示 "转发" 的射线。
* **手柄方向的上轴**：向右和向后定义隐含的上轴。

可以通过 Unity 的跨供应商输入 API (XR 来访问抓握姿势 *[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/旋转*) 或通过 Windows MR 专用 API (*sourcePose TryGetPosition/旋转*，请求为 **抓握** 节点) 提出数据。

### <a name="pointer-pose"></a>指针姿势

**指针姿势** 代表着控制器的末端。

系统提供的指针姿势最适合用于在 **呈现控制器模型本身** 时进行 raycast。 如果要渲染某个其他虚拟对象来替代控制器（如虚拟压力），则应指出该虚拟对象的最自然的射线，如沿应用定义的机枪模型的桶向下移动的射线。 由于用户可以看到虚拟对象，而不是物理控制器，因此，使用虚拟对象指向虚拟对象可能会更自然地使用应用。

目前，通过将 *InteractionSourceNode* 作为参数传入，Unity 仅可通过 Windows MR- *sourcePose. TryGetPosition/旋转*，在 Unity 中提供指针姿势。

### <a name="openxr"></a>OpenXR 

通过 OpenXR 输入交互可以访问两组姿势：

* 用于呈现对象的手柄姿势
* 目标是指进入世界。

有关此设计的详细信息以及这两个姿势之间的差异，请参阅 [OpenXR 规范输入子路径](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。

InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供的姿势都代表了 OpenXR **手柄** 的姿势。 与手柄姿势相关的 InputFeatureUsages 在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定义。

InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿势均代表 OpenXR **aim** 姿势。 这些 InputFeatureUsages 未在包含的任何 c # 文件中定义，因此你需要定义自己的 InputFeatureUsages，如下所示：

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a>Haptics

有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 unity [XR 输入-haptics 的 Unity 手册](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的文档。

## <a name="controller-tracking-state"></a>控制器跟踪状态

与耳机一样，Windows Mixed Reality 运动控制器不需要外部跟踪传感器的设置。 相反，控制器由耳机本身中的传感器跟踪。

如果用户将控制器移出耳机的视图，则在大多数情况下，Windows 继续推断控制器位置。 如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。

此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。 许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a>显式跟踪状态的推理

希望根据跟踪状态以不同方式对位置进行处理的应用可能会进一步检查控制器状态的属性，如 *SourceLossRisk* 和 *PositionAccuracy*：

<table>
<tr>
<th> 跟踪状态 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高准确度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> 是</td>
</tr><tr>
<td> <b>高准确度 (丢失) 的风险 </b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> 是</td>
</tr><tr>
<td> <b>近似准确度</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: green; color: white"> 是</td>
</tr><tr>
<td> <b>无位置</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: orange"> false</td>
</tr>
</table>

这些运动控制器跟踪状态的定义如下：
* **高准确度：** 尽管运动控制器位于耳机的视图中，但它通常会根据视觉对象跟踪提供高准确性位置。 一种移动控制器，该控制器暂时离开了 "查看" 字段或暂时不能从耳机传感器中遮盖 (例如，根据用户的另一种情况，) 将继续根据控制器本身的惯性跟踪来返回高准确度姿势。
* **高准确度 (丢失) 的风险：** 当用户将运动控制器移出耳机的视图边缘后，耳机不久就无法直观地跟踪控制器的位置。 此应用通过查看 **SourceLossRisk** 到1.0，来了解控制器何时到达此 FOV 边界。 此时，应用程序可以选择暂停需要稳定的高质量姿势流的控制器手势。
* **近似准确性：** 如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。 此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。 许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。 对于输入要求较高的应用，可以通过检查 **PositionAccuracy** 属性，从 **高** 准确度到 **接近** 准确性，从而为用户提供更多的 hitbox。
* **无位置：** 尽管控制器可以在很长时间内正常运行，但有时系统也知道，甚至在当前情况下，该位置都没有意义。 例如，已打开的控制器可能从未被可视化地观察到，或者用户可能会关闭控制器，然后由其他人选取。 在这种情况下，系统不会提供应用程序的任何位置，并且 *TryGetPosition* 将返回 false。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>常见 Unity Api (GetButton/GetAxis) 

**命名空间：** *UnityEngine*、 *UnityEngine. XR*<br>
**类型**： *输入*， *XR。InputTracking*

Unity 目前使用其常规 *输入. GetButton/GetAxis* api 公开 [Oculus sdk](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)和 Windows Mixed Reality 的输入，包括双手和运动控制器。 如果你的应用程序使用这些 Api 进行输入，则它可以在多个 XR Sdk 中轻松支持运动控制器，其中包括 Windows Mixed Reality。

### <a name="getting-a-logical-buttons-pressed-state"></a>获取逻辑按钮的按下状态

若要使用一般 Unity 输入 Api，通常先将按钮和轴向上滑到 [Unity 输入管理器](https://docs.unity3d.com/Manual/ConventionalGameInput.html)中的逻辑名称，然后将按钮或轴 id 绑定到每个名称。 然后，你可以编写引用该逻辑按钮/轴名称的代码。

例如，若要将左运动控制器的触发器按钮映射到 "提交" 操作，请参阅 "**编辑 >" 设置 Project** 在 Unity 内 > 输入 "，然后展开" 轴 "下" 提交 "部分的" 属性 "。 更改 " **正按钮** " 或 " **Alt 正** 向按钮" 属性以阅读 **游戏杆按钮 14**，如下所示：

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

## <a name="windows-specific-apis-xrwsainput"></a>Windows XR 的 (API。Wsa。输入) 

> [!CAUTION]
> 如果项目正在使用任何 XR。WSA API 正在逐步淘汰，以在将来的 Unity 版本中支持 XR SDK。 对于新项目，我们建议从头开始使用 XR SDK。 可在此处找到有关 [XR 输入系统和 API 详细信息](https://docs.unity3d.com/Manual/xr_input.html)。

**命名空间***：UnityEngine.XR.WSA.Input*<br>
**类型**：InteractionManager、InteractionSourceState、InteractionSource、InteractionSourceProperties、InteractionSourceKind、InteractionSourceLocation      

若要获取有关 HoloLens) Windows Mixed Reality 和运动控制器的 Windows Mixed Reality 手动输入 (的详细信息，可以选择在 *UnityEngine.XR.WSA.Input* 命名空间下使用特定于 Windows 的空间输入 API。 这使你可以访问其他信息，例如位置准确性或源类型，使你能够将手和控制器分开。

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
* 当用户按下控制器上的按钮时，系统收到按下前，无线延迟蓝牙大约 20 毫秒。
* 然后，如果使用的是前向预测姿势，则还有 10-20 毫秒的向前预测应用于当前帧的光子到达用户眼睛的时间。

这意味着轮询会提供源姿势或头部姿势，向前 30-40 毫秒，从用户头部和手在按下或松开时实际返回的 30-40 毫秒。  对于HoloLens输入，虽然没有无线传输延迟，但检测按下时存在类似的处理延迟。

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