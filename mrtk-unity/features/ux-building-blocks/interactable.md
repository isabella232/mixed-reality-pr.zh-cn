---
title: 可交互
description: MRTK 中可交互脚本组件的概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 可交互， 事件，
ms.openlocfilehash: a0aee99d01ae59a8ebedc4d62a4b0aaf844a7afaa6961bbfd05238dd9d5b673d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206762"
---
# <a name="interactable"></a>可交互

![可交互](../images/interactable/InteractableExamples.png)

组件 [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 是一个一体式容器，使任何对象都可以轻松 *交互* 并响应输入。 可交互可充当所有类型的输入（包括触摸、手部射线、语音等）的全功能，这些交互会漏斗到[](#events)事件和[视觉主题](visual-themes.md)响应中。 此组件提供了一种简单的方式来创建按钮、更改具有焦点的对象的颜色等。

## <a name="how-to-configure-interactable"></a>如何配置 Interactable

组件允许配置三个主要部分：

1) [常规输入配置](#general-input-settings)
1) [针对](visual-themes.md) 多个 GameObject 的视觉对象主题
1) [事件处理程序](#events)

### <a name="general-input-settings"></a>常规输入设置

![常规可交互设置](../images/interactable/InputFeatures_short.png)

**状态**

*状态* 是 [一个 ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html)参数，用于定义可交互配置文件和视觉主题 的交互阶段 [](#interactable-profiles)（如按下或 [观察](visual-themes.md)）。

**DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) 随 MRTK 现成提供，是可交互 *组件的默认* 参数。

![检查器中的状态 ScriptableObject 示例](../images/interactable/DefaultInteractableStates.png)

*DefaultInteractableStates* 资产包含四种状态，并利用 [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) 状态模型实现。

* **默认值**：不执行任何操作，这是最隔离的基状态。

* **焦点**：正在指向对象。 这是一种单一状态，当前未设置其他状态，但它将排名为"默认"。

* **按**：对象被指向，并且正在按下按钮或手。 "按状态"对"默认"和"焦点"进行排名。 此状态也将设置为"物理按下"的回退。

* **已禁用**：按钮不应是交互式的，视觉反馈将让用户知道此按钮是否由于某种原因目前不可使用。 理论上，禁用状态可以包含所有其他状态，但在关闭"启用"后，"禁用"状态会超过所有其他状态。

根据列表中的顺序 (#) 位值分配给状态。

> [!NOTE]
> 在创建可交互组件时，通常建议使用 **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) 。 
>
> 但是，有 17 种可交互状态可用于驱动主题，但有些状态由其他组件驱动。 下面是具有内置功能的列表。
>
> * 已访问：已单击"可交互"。
> * 已切换：按钮处于切换状态或维度索引为奇数。
> * 手势：手部或控制器已按下，并且已从原始位置移动。
> * VoiceCommand：语音命令用于触发"可交互"。
> * PhysicalTouch：当前检测到触摸输入， [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 请使用 启用。
> * 抓取：手当前正在抓取对象边界， [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 用于启用

**Enabled**

切换是否将启用可交互对象。 这对应于代码中的 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 。

Interactable *的 enabled* 属性不同于通过 GameObject/Component (配置的 enabled 属性，即 SetActive 等) 。 禁用 GameObject 或 *可* 交互 MonoBehaviour 将禁用类中所有内容（包括输入、视觉主题、事件等）的运行。通过 禁用 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 将禁用大多数输入处理，并重置相关的输入状态。 但是， 类仍将运行每个帧并接收将被忽略的输入事件。 这可用于显示处于禁用状态（可通过视觉主题完成）的可交互对象。 一个典型的示例是提交按钮，等待所有必需的输入字段完成。

**输入操作**

从 [可交互组件](../input/input-actions.md) 应响应的输入配置或控制器映射配置文件 *中选择* 输入操作。

可以通过 在运行时在代码中配置此属性 [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) 。

**IsGlobal**

如果为 true，这会将组件标记为所选输入操作 的全局 [输入侦听器](../input/input-actions.md)。 默认行为为 false，这会将输入限制为仅此 *可* 交互碰撞体/GameObject。

可以通过 在运行时在代码中配置此属性 [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) 。

**语音命令**

[来自](../input/speech.md)MRTK 语音命令配置文件的语音命令，用于触发 OnClick 事件进行语音交互。

可以通过 在运行时在代码中配置此属性 [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) 。

**需要焦点**

如果为 true，则语音命令将仅在且仅在指针已有焦点时激活可交互对象。 如果为 false， *则 Interactable* 将充当所选语音命令的全局侦听器。 默认行为为 true，因为多个全局语音侦听器可能难以在场景中组织。

可以通过 在运行时在代码中配置此属性 [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) 。

**选择模式**

此属性定义选择逻辑。 单击 *可交互* 对象时，它将进入下一个 *维度* 级别。 *维度* 类似于排名，并定义输入 (的状态，即 焦点，按等) 。 它们可用于定义切换状态或与按钮关联的其他多级状态。 当前维度级别由 跟踪 `Interactable.DimensionIndex` 。

可用的选择模式包括：

* **按钮**  - *维度*= 1，可单击的简单 *可交互*
* **切换**  - *维度*= 2，*关闭* 状态之间的可 / *交互备用* 项
* **多维度**  - *维度>* = 3，每次单击都会增加当前维度级别 + 1。 用于定义列表的按钮状态等。

*"可* 交互"还允许每个维度 定义多个 *主题*。 例如，当 *SelectionMode=Toggle* 时，当取消选择 *"* 可交互"时，可以应用一个主题，在选择组件时应用另一 *个主题*。

可以通过 在运行时查询当前选择模式 [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) 。 可以通过设置 属性以匹配所需的功能，  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) 在运行时更新模式。 此外，可以通过 访问对 *切换和**多* 维度模式有用的当前维度 [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) 。

### <a name="interactable-profiles"></a>可交互配置文件

*配置文件* 是创建 GameObject 和视觉主题 [之间的关系的项](visual-themes.md)。 配置文件定义发生状态更改时主题 [将操作的内容](#general-input-settings)。

主题与材料非常类似。 它们是可编写脚本的对象，其中包含将基于当前状态分配给对象的属性列表。 主题也可重新使用，并可在多个可 *交互的* UX 对象之间分配。

**销毁时重置**

视觉对象主题根据所选主题引擎的类和类型修改目标 GameObject 上的各种属性。 如果 *销毁可* 交互组件时重置为 true，则组件将活动主题的所有修改属性重置为原始值。 否则，销毁后，可交互组件将保留任何修改后的属性。 在后一种情况下，除非由另一个外部组件更改，否则值的最后一个状态将保持。 默认值为 false。

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a>事件

每个 *可交互* 组件都有一个 *OnClick* 事件，该事件在仅选择组件时触发。 但是 *，可以使用 Interactable* 来检测输入事件，而不只是 *OnClick*。

单击" *添加事件* "按钮，添加新类型的事件接收器定义。 添加后，选择所需的事件类型。

![事件示例](../images/interactable/Events.png))

有不同类型的事件接收器可响应不同类型的输入。 MRTK 附带以下一组现用接收器。

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

可以通过创建扩展 的新类来创建自定义接收器 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 。

![事件切换接收器示例](../images/interactable/Event_toggle.png)

*切换事件接收器的示例*

### <a name="interactable-receivers"></a>可交互的接收方

 [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver)组件允许在源可交互组件外部定义事件。  *InteractableReceiver* 将侦听由另一个可交互 触发的筛选 *事件类型*。 如果未 *直接分配 Interactable* 属性，则搜索范围属性定义 *InteractableReceiver* 侦听事件的方向，这些事件位于自身、父级或子 GameObject 中。

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) 的行为方式类似，但用于匹配事件的列表。

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>创建自定义事件

与 [视觉主题](visual-themes.md#custom-theme-engines)一样，可以扩展事件以检测任何状态模式或公开功能。

可以通过两种主要方式创建自定义事件：

1) 扩展 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 类以创建自定义事件，该事件会显示在事件类型的下拉列表中。 默认情况下提供 Unity 事件，但可以添加其他 Unity 事件，也可以将 事件设置为隐藏 Unity 事件。 此功能允许设计器与项目的工程师一起创建自定义事件，设计器可以在编辑器中设置该事件。

1) 扩展 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) 类以创建可驻留在可交互对象或其他对象上的完全自定义事件组件。 将 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) 引用 *可交互的* 以检测状态更改。

#### <a name="example-of-extending-receiverbase"></a>扩展示例 `ReceiverBase`

类 [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) 显示有关可交互 *对象的状态* 信息，并是如何创建自定义事件接收器的示例。

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

在创建自定义事件接收器时，以下方法可用于重写/实现 。 [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 是可用于检测状态模式/转换的抽象方法。 此外， [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 和 [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 方法可用于在选择"可交互"时创建自定义事件逻辑。

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>在检查器中显示自定义事件接收器字段

*ReceiverBase* 脚本 [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) 使用属性在检查器中公开自定义属性。 下面是 Vector3 的示例，这是一个包含工具提示和标签信息的自定义属性。 选中可交互 GameObject 并添加关联的事件接收器类型时，此属性将在检查器中显示 *为* 可配置。

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>如何使用可交互

### <a name="building-a-simple-button"></a>生成简单按钮

可以通过将可交互组件添加到配置为接收输入事件的 GameObject 来创建一个简单的按钮。 它可以在它上或子项上具有碰撞体来接收输入。 如果对 *基于* Unity UI 的 GameObject 使用"可交互"，则它应在 Canvas GameObject 下。

通过创建新配置文件、分配 GameObject 本身并创建新主题，进一步执行按钮。 此外，使用 *OnClick* 事件进行事件处理。

> [!NOTE]
> 使 [按钮可按下](button.md) 需要 [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 组件。 此外， [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) 需要组件将按下事件漏斗到 *可交互* 组件。

### <a name="creating-toggle-and-multi-dimension-buttons"></a>创建切换按钮和多维度按钮

#### <a name="toggle-button"></a>切换按钮

若要使按钮能够切换，请更改 [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 字段以键入 `Toggle` 。 在 *"配置文件* "部分中，为启用"可交互"时所使用的每个 *配置文件添加一* 个新的切换主题。

当 [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 设置为 Toggle 时， *可以使用 IsToggled* 复选框在运行时初始化时设置控件的默认值。

*CanSelect* 表示 *可交互* 对象可以从 *关闭* 到打开，而 *CanDeselect* 表示相反。

![配置文件切换视觉对象主题示例](../images/interactable/Profile_toggle.png)

开发人员可以利用 和 [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 接口通过代码获取/设置 *可交互的切换* 状态。

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>切换按钮集合

通常，有一个切换按钮列表，其中在任何给定时间只能有一个按钮处于活动状态，也称为径向集或单选按钮等。

使用 [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) 组件启用此功能。 此控件可确保 *在任何给定时间* 仅打开一个可交互对象。 *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) 也是一个很好的现用起点。

创建自定义径向按钮组：

1) 创建多个 *可交互* GameObjects/buttons
1) 设置每个 *可交互* 的 *SelectionMode* = Toggle、CanSelect = true 和 *CanDeselect* = false 
1) 在所有可交互对象上创建空的父 GameObject，并添加 *InteractableToggleCollection* 组件
1) 将所有 *可交互项* 添加到 *InteractableToggleCollection* 上的 *ToggleList*
1) 设置 *InteractableToggleCollection.CurrentIndex* 属性，以确定在开始时默认选择哪个按钮

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>多维按钮

多维度选择模式用于创建顺序按钮或具有两个步骤的按钮，例如使用三个值控制速度、快速 (1x) 、更快的 (2x) 或最快 (3x) 。

由于维度是数值，因此可以添加最多 9 个主题来控制每个速度设置的文本标签或按钮纹理，每个步骤使用不同的主题。

每次单击事件都会在运行时 `DimensionIndex` 将 前进 1，直到 `Dimensions` 达到值。 然后，周期将重置为 0。

![多维配置文件示例](../images/interactable/Profile_multiDimensions.png)

开发人员可以评估 [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 以确定当前处于活动状态的维度。

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>在运行时创建可交互

*可在运行时* 轻松添加到任何 GameObject。 以下示例演示如何分配具有可视主题 [的配置文件](visual-themes.md)。

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a>通过代码的可交互事件

可以使用以下示例通过代码将操作 [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) 添加到基事件。

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

使用 [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 函数在运行时动态添加事件接收器。

下面的示例代码演示如何添加 [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，用于侦听焦点输入/退出，并定义在事件实例启动时要执行的操作代码。

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

下面的示例代码演示如何添加 [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，它侦听可切换的 *Interactables* 上的选定/取消选定状态转换，并定义在事件实例启动时要执行的操作代码。

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a>另请参阅

* [视觉对象主题](visual-themes.md)
* [输入操作](../input/input-actions.md)
* [语音命令](../input/speech.md)
* [按钮](button.md)
* [MRTK 标准着色器](../rendering/MRTK-standard-shader.md)
