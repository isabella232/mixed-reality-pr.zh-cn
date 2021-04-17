---
title: 可交互
description: MRTK 中种不可交互脚本组件概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，种不可交互，事件，
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581559"
---
# <a name="interactable"></a>可交互

![可交互](../images/interactable/InteractableExamples.png)

组件是一个一体式 [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 容器，使任何对象都可以轻松地 *种不可交互* 输入并做出响应。 种不可交互充当所有类型的输入（包括触摸、手写光线、语音等）的全部捕获，并将这些交互转换为 [事件](#events) 和 [视觉主题](visual-themes.md) 响应。 此组件提供一种简单的方法来生成按钮、更改具有焦点的对象上的颜色等。

## <a name="how-to-configure-interactable"></a>如何配置种不可交互

组件允许配置的三个主要部分：

1) [常规输入配置](#general-input-settings)
1) 面向多个 Gameobject 的[视觉主题](visual-themes.md)
1) [事件处理程序](#events)

### <a name="general-input-settings"></a>一般输入设置

![常规种不可交互设置](../images/interactable/InputFeatures_short.png)

**状态**

*状态* 是 [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 参数，用于定义 [种不可交互配置文件](#interactable-profiles) 和 [视觉主题](visual-themes.md)的交互阶段，如按下或观察。

**DefaultInteractableStates** (资产/MRTK/SDK/FEATURES/UX/种不可交互/州/DefaultInteractableStates) 随内置了 MRTK，是 *种不可交互* 组件的默认参数。

![检查检查器中的 ScriptableObject 示例](../images/interactable/DefaultInteractableStates.png)

*DefaultInteractableStates* 资产包含四种状态，并利用 [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) 状态模型实现。

* **默认**：不会发生任何情况，这是最隔离的基本状态。

* **焦点**：对象指向。 这是一种状态，当前未设置任何其他状态，但它的默认值为默认值。

* **按下**：对象将指向，按钮或手按下。 按下状态的默认值和焦点。 此状态也将设置为 "物理按下"。

* **已禁用**：该按钮不应为交互式，并且视觉反馈会让用户知道此按钮目前不可用的原因。 理论上，禁用状态可能包含所有其他状态，但启用后关闭时，禁用状态胜过所有其他状态。

根据列表中的顺序，会将位值 ( # ) 分配给状态。

> [!NOTE]
> 通常建议在创建 *种不可交互* 组件时，使用 **DefaultInteractableStates** (资产/MRTK/SDK/功能/UX/种不可交互/州/DefaultInteractableStates）) 。
>
> 不过，有17个可用来驱动主题的种不可交互状态，但某些状态应由其他组件驱动。 下面是包含内置功能的列表。
>
> * 已访问：已单击种不可交互。
> * 切换：按钮处于切换状态，或者维度索引为奇数。
> * 手势：手型或控制器已按下，并已从原始位置移动。
> * VoiceCommand：使用语音命令触发了种不可交互。
> * PhysicalTouch：当前检测到触摸输入，请使用 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 启用。
> * 抓住：手头当前在对象的边界内抓取， [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 并使用启用

**Enabled**

切换种不可交互是否开始启用。 这对应于 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 代码中的。

*种不可交互的* enabled 属性不同于通过 GameObject/Component 配置的 enabled 属性 (即 SetActive 等) 。 禁用 GameObject 或 *种不可交互* MonoBehaviour 将禁止运行类中的所有内容，包括输入、视觉主题、事件等。禁用 via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 将禁用大多数输入处理，并重置相关输入状态。 但是，类仍将运行每个帧并接收输入事件，这些事件将被忽略。 这对于在禁用状态下显示种不可交互非常有用，可以通过视觉主题来完成此操作。 这种情况的一个典型示例是 "提交" 按钮，等待所有必需的输入字段完成。

**输入操作**

从 *种不可交互* 组件应响应的输入配置或控制器映射配置文件中选择 [输入操作](../input/input-actions.md)。

此属性可在运行时通过代码进行配置 [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) 。

**IsGlobal**

如果为 true，则会将组件标记为选定 [输入操作](../input/input-actions.md)的全局输入侦听器。 默认行为是 false，它会将输入限制为仅限此 *种不可交互* 碰撞器/GameObject。

此属性可在运行时通过代码进行配置 [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) 。

**语音命令**

MRTK 语音命令配置文件中的[语音命令](../input/speech.md)，触发用于语音交互的 OnClick 事件。

此属性可在运行时通过代码进行配置 [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) 。

**需要焦点**

如果为 true，则当且仅当它已具有指针的焦点时，语音命令才会激活 *种不可交互* 。 如果为 false，则 *种不可交互* 将充当所选语音命令的全局侦听器。 默认行为是 "true"，因为多个全局语音侦听器可能很难在场景中进行组织。

此属性可在运行时通过代码进行配置 [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) 。

**选择模式**

此属性定义选择逻辑。 当单击 *种不可交互* 时，它将循环访问下一个 *维度* 级别。 *维度* 类似于排名，并定义输入以外的状态 (例如 重点，按 etc) 。 它们有助于定义切换状态或与按钮关联的其他多排名状态。 跟踪当前维度级别 `Interactable.DimensionIndex` 。

可用的选择模式包括：

* **按钮**  - *维数*= 1，简单的可单击 *种不可交互*
* **切换**  - *维数*= 2，*种不可交互**在* / *off* 状态之间交替
* **多维度**  - *维度*>= 3，则每次单击都会增加当前的维度级别 + 1。 适用于将按钮状态定义到列表等。

*种不可交互* 还允许为每个 *维度* 定义多个主题。 例如，当 *SelectionMode = 切换* 时，当 *取消选择**种不可交互* 时，可能会应用一个主题，并在 *选择* 组件时应用另一个主题。

当前选择模式可在运行时通过进行查询 [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) 。 可以通过将  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) 属性设置为与所需的功能，来在运行时更新模式。 此外，可以通过访问当前维度（用于 *切换* 和 *多维度* 模式） [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) 。

### <a name="interactable-profiles"></a>种不可交互配置文件

*配置文件* 是在 GameObject 和 [视觉主题](visual-themes.md)之间创建关系的项。 配置文件定义当 [发生状态更改](#general-input-settings)时，主题将操作哪些内容。

主题工作非常类似于材料。 它们是可编写脚本的对象，这些对象包含将根据当前状态分配给对象的属性列表。 主题也可重复使用，并且可以跨多个 *种不可交互* UX 对象进行分配。

**销毁时重置**

Visual themes 修改目标 GameObject 上的各种属性，具体取决于所选的主题引擎的类和类型。 如果在销毁种不可交互组件时 *重置时重置* 为 true，则组件会将活动主题中所有已修改的属性重置为其原始值。 否则，在销毁后，种不可交互组件会按原样保留所有修改的属性。 在后一种情况下，除非由另一个外部组件更改，否则值的最后一个状态将保持不变。 默认值为 false。

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a>事件

每个 *种不可交互* 组件都有一个 *OnClick* 事件，该事件在组件简单地处于选中状态时触发。 但是， *种不可交互* 可用于检测除 *OnClick* 以外的输入事件。

单击 " *添加事件* " 按钮，添加新类型的事件接收器定义。 添加后，选择所需的事件类型。

![事件示例](../images/interactable/Events.png))

事件接收器有不同类型，可对不同类型的输入进行响应。 MRTK 附带了以下一组接收方。

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

可以通过创建一个扩展的新类来创建自定义接收器 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 。

![事件切换接收方示例](../images/interactable/Event_toggle.png)

*切换事件接收器的示例*

### <a name="interactable-receivers"></a>种不可交互接收方

 [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver)组件允许在源 *种不可交互* 组件外部定义事件。 *InteractableReceiver* 将侦听其他 *种不可交互* 激发的筛选事件类型。 如果未直接分配 *种不可交互* 属性，则 " *搜索范围* " 属性将定义 *InteractableReceiver* 侦听事件的方向，该方向是在其自身、父或子 GameObject 中。

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) 以类似方式进行操作，但对于匹配事件的列表。

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>创建自定义事件

与 [视觉主题](visual-themes.md#custom-theme-engines)一样，可以扩展事件以检测任何状态模式或公开功能。

可以通过两种主要方式创建自定义事件：

1) 扩展 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 类以创建将在事件类型的下拉列表中显示的自定义事件。 默认情况下，将提供 Unity 事件，但可以添加其他 Unity 事件，或者可以将事件设置为隐藏 Unity 事件。 此功能允许设计器与项目上的工程一起使用，以创建设计器可在编辑器中设置的自定义事件。

1) 扩展 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) 类，以创建可以驻留在 *种不可交互* 或其他对象上的完全自定义事件组件。 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)将引用 *种不可交互* 以检测状态更改。

#### <a name="example-of-extending-receiverbase"></a>扩展示例 `ReceiverBase`

[`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI)类显示有关 *种不可交互* 的状态信息，并举例说明如何创建自定义事件接收器。

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

以下方法可用于在创建自定义事件接收器时重写/实现。 [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 是一个抽象方法，可用于检测状态模式/转换。 此外，在 [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 选择 *种不可交互* 时，和方法可用于创建自定义事件逻辑。

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

*ReceiverBase* 脚本使用 [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) 特性来公开检查器中的自定义属性。 下面是一个 System.numerics.vector2 示例，它是包含工具提示和标签信息的自定义属性。 选择 *种不可交互* GameObject 并添加关联的 *事件接收器* 类型时，此属性将在检查器中显示为可配置。

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>如何使用种不可交互

### <a name="building-a-simple-button"></a>构建简单的按钮

可以通过将 *种不可交互* 组件添加到配置为接收输入事件的 GameObject，创建一个简单的按钮。 它可以在它上面或子上有一个碰撞器来接收输入。 如果将 *种不可交互* 用于基于 Unity UI 的 gameobject，则它应位于画布 GameObject 下。

通过创建新的配置文件，分配 GameObject 本身并创建新的主题，使按钮进一步操作。 此外，使用 *OnClick* 事件可以进行一些操作。

> [!NOTE]
> 使 [按钮 pressable](button.md) 需要 [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 组件。 此外，还 [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) 需要组件将事件按漏斗到 *种不可交互* 组件。

### <a name="creating-toggle-and-multi-dimension-buttons"></a>创建切换和多维度按钮

#### <a name="toggle-button"></a>切换按钮

若要使按钮切换，请将字段更改 [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 为 "类型" `Toggle` 。 在 " *配置文件* " 部分中，将为 *种不可交互* 切换时使用的每个配置文件添加一个新的切换主题。

当 [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 设置为切换时， *IsToggled* 复选框可用于在运行时初始化时设置控件的默认值。

*CanSelect* 表示 *种不可交互* 可以从 *off* 切换到 *on* ，而 *CanDeselect* 表示反转。

![配置文件切换视觉对象示例](../images/interactable/Profile_toggle.png)

开发人员可以利用 [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 和 [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 接口通过代码获取/设置 *种不可交互* 的切换状态。

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>切换按钮集合

通常，有一个切换按钮列表，在任何给定时间（也称为径向集或单选按钮等），只有一个按钮可以处于活动状态。

使用 [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) 组件启用此功能。 此控制确保在任何给定时间，只切换一 *种不可交互* 。 *RadialSet* (资产/MRTK/SDK/FEATURES/UX/种不可交互/Prototyping/RadialSet) 也是一种现成的良好起点。

若要创建自定义的径向按钮组：

1) 创建多个 *种不可交互* gameobject/按钮
1) 将每个 *种不可交互* 设置为 *SelectionMode* = 切换， *CanSelect* = true，并将 *CanDeselect* = false
1) 在所有 *Interactables* 上创建一个空的父 GameObject，并添加 *InteractableToggleCollection* 组件
1) 将所有 *Interactables* 添加到 *InteractableToggleCollection* 上的 *ToggleList*
1) 设置 *InteractableToggleCollection CurrentIndex* 属性，以确定默认情况下在开始时选择哪个按钮

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>多维按钮

多维度选择模式用于创建顺序按钮，或具有两个以上步骤的按钮，如使用三个值控制速度、Fast (1x) 、速度 (2 到3或更快 (3) 倍) 。

如果维度为数值，则可以添加最多9个主题来控制每个速度设置的按钮的文本标签或纹理，并为每个步骤使用不同的主题。

每次单击事件都将 `DimensionIndex` 在运行时前进1，直到 `Dimensions` 达到值。 然后，循环将重置为0。

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

### <a name="create-interactable-at-runtime"></a>在运行时创建种不可交互

在运行时，可以轻松地将 *种不可交互* 添加到任何 GameObject。 下面的示例演示如何使用 [视觉对象主题](visual-themes.md)来分配配置文件。

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

### <a name="interactable-events-via-code"></a>通过代码种不可交互事件

可以通过代码将操作添加到基 [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) 事件，如下例所示。

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

使用 [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 函数在运行时动态添加事件接收器。

下面的示例代码演示了如何添加 [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，它侦听焦点/退出，并定义在事件实例激发时要执行的操作代码。

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

下面的示例代码演示了如何添加 [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，它侦听对切换 *Interactables* 的选定/取消选择状态转换，并定义在事件实例激发时要执行的操作代码。

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

* [视觉主题](visual-themes.md)
* [输入操作](../input/input-actions.md)
* [语音命令](../input/speech.md)
* [按钮](button.md)
* [MRTK 标准着色器](../rendering/MRTK-standard-shader.md)
