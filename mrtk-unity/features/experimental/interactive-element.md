---
title: 交互元素
description: InteractiveElement MRTK 文档
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Interactive 元素， 可交互
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144761"
---
# <a name="interactive-element-experimental"></a>Interactive 元素 [实验]

MRTK 输入系统的简化集中入口点。 包含状态管理方法、事件管理和核心交互状态的状态设置逻辑。

Interactive Element 是 Unity 2019.3 及更新版中支持的实验性功能，因为它利用 Unity 2019.3 的新功能： [序列化引用](https://docs.unity3d.com/ScriptReference/SerializeReference.html)。

### <a name="interactive-element-inspector"></a>Interactive 元素检查器

在播放模式下，Interactive Element 检查器提供可视反馈，指示当前状态是否处于活动状态。 如果状态处于活动状态，则以蓝绿色突出显示该状态。  如果状态不处于活动状态，则颜色不会更改。 检查器中状态旁边的数字是状态值，如果状态处于活动状态，则值为 1，如果状态不活动，则值为 0。

![交互式元素与虚拟手部交互](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>核心状态

Interactive 元素包含核心状态，并支持添加 [自定义状态](#custom-states)。  核心状态是已在 中定义状态设置逻辑的状态 `BaseInteractiveElement` 状态。 下面是当前输入驱动核心状态的列表： 

### <a name="current-core-states"></a>当前核心状态

- [默认值](#default-state) 

近近交互核心状态：
- [焦点](#focus-state) 

近交互核心状态：

- [焦点附近](#focus-near-state)
- [触控](#touch-state)

远交互核心状态：
- [最大焦点](#focus-far-state)
- [选择远](#select-far-state)

其他核心状态：
- [Clicked](#clicked-state)
- [开启和关闭切换](#toggle-on-and-toggle-off-state)
- [Speech 关键字](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>如何通过检查器添加核心状态

1. 在交互式元素的检查器中导航到 " **添加核心状态** "。

    ![通过检查器添加核心状态](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. 选择 " **选择状态** " 按钮，选择要添加的核心状态。 菜单中的状态按交互类型进行排序。

    ![使用所选状态通过检查器添加核心状态](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. 打开 "事件配置 foldout"，查看与状态关联的事件和属性。

    ![使用事件配置通过检查器添加核心状态](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>如何通过脚本添加核心状态

使用 `AddNewState(stateName)` 方法添加核心状态。 有关可用核心状态名称的列表，请使用 `CoreInteractionState` 枚举。

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>状态内部结构 

交互式元素中的状态为类型 `InteractionState` 。  `InteractionState`包含以下属性：

- **名称**：状态的名称。
- **值**：状态值。  如果状态为 "on"，则 "状态" 值为 "1"。 如果状态为 "关"，则 "状态" 值为 "0"。
- **活动**：状态当前是否处于活动状态。 当状态为 on 时，活动属性的值为 true，如果状态为 off，则为 false。 
- **交互类型**：状态的交互类型是指状态适用的交互类型。 
  - `None`：不支持任何形式的输入交互。
  - `Near`：近乎交互支持。 当有向外的人与其他游戏对象直接联系时，输入被视为接近交互，即，可表述的手接近于世界空间中游戏对象的位置的位置。
  - `Far`：远交互支持。 不需要直接联系游戏对象时，会将输入视为交互。 例如，通过控制器射线或注视的输入被视为远交互输入。
  - `NearAndFar`：包含近和远交互支持。 
  - `Other`：指针独立交互支持。
- **事件配置**：状态的事件配置是序列化事件配置文件入口点。 

所有这些属性都是在 `State Manager` 包含在交互式元素中的内部设置的。 若要修改状态，请使用以下帮助器方法：

**状态设置 Helper 方法**

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

获取状态的事件配置特定于状态本身。 每个核心状态都有特定的事件配置类型，下面概述了描述每个核心状态的各节。

下面是获取状态事件配置的一般化示例：

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>默认状态

默认状态始终存在于交互式元素上。  此状态仅在所有其他状态均不处于活动状态时才处于活动状态。  如果任何其他状态变为活动状态，则将在内部将默认状态设置为 "关闭"。 

将使用状态列表中显示的默认值和焦点状态初始化交互式元素。 默认状态始终需要存在于状态列表中。 

#### <a name="getting-default-state-events"></a>获取默认状态事件

默认状态的事件配置类型： `StateEvents`

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a>焦点状态

焦点状态是近和远交互状态，可被视为与悬停等效的混合现实。 对于焦点状态，几乎交互与远端交互之间的区别是当前活动指针类型。  如果焦点状态的指针类型是 "获取" 指针，则会将交互视为接近交互。  如果主指针不是 ""，则会将交互视为远交互。 默认情况下，在交互式元素中显示焦点状态。

**焦点状态行为** 
 ![具有虚拟手交互的焦点状态](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

**焦点状态检查器** 
 ![Inpsector 中的焦点状态](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>正在获取焦点状态事件

焦点状态的事件配置类型： `FocusEvents`

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a>专注于 vs 重心的行为 

![使用虚拟手部交互进行近近和远焦点](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>焦点接近状态

当引发焦点事件且主指针为"开小马"指针（指示近交互）时，将设置"焦点附近"状态。 

**焦点接近状态行为** 
 ![通过虚拟手部交互将焦点放在接近状态](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**焦点近状态检查器** 
 ![检查器中靠近组件的焦点](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>获取 FocusNear 状态事件

FocusNear 状态的事件配置类型： `FocusEvents`

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a>焦点远点状态

当主指针不是"焦点指针"时，将设置"焦点远"状态。  例如，默认控制器射线指针和 GGV (凝视、手势、语音) 指针被视为远交互指针。

**焦点远状态行为** 
 ![与虚拟手部交互远的焦点状态](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

**焦点远状态检查器** 
 ![检查器中的焦点远部分](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>获取焦点远场状态事件

FocusFar 状态的事件配置类型： `FocusEvents`

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a>触控状态

触摸状态是一种近交互状态，当一个明确表达的手直接触摸对象时，将设置此状态。  直接触摸意味着铰接手的索引指非常接近对象的世界位置。 默认情况下，如果将 Touch 状态添加到状态列表，则组件将附加到 `NearInteractionTouchableVolume` 对象。  检测 Touch  `NearInteractionTouchableVolume` `NearInteractionTouchable` 事件需要存在 或 组件。  和 之间的区别在于，基于对象的碰撞体检测触摸，并检测平面 `NearInteractionTouchableVolume` `NearInteractionTouchable` `NearInteractionTouchableVolume` `NearInteractionTouchable` 的已定义区域中的触摸。

**触摸状态行为** 
 ![具有虚拟手交互的触摸状态](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

**触控状态检查器** 
 ![检查器中的触摸状态组件](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>获取触摸状态事件

触摸状态的事件配置类型： `TouchEvents`

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a>选择 Far 状态

选择的状态为 "选择" `IMixedRealityPointerHandler` 。  此状态是一种远交互状态，检测到远交互单击 (轻点击) ，并通过使用 far 交互指针（例如，默认控制器射线指针或 GGV 指针）进行保存。  在事件配置 foldout 下，"选择最多" 状态具有一个选项 `Global` 。 如果 `Global` 为 true，则 `IMixedRealityPointerHandler` 将注册为全局输入处理程序。  如果处理程序注册为 global，则不需要将焦点放在对象上来触发输入系统事件。  例如，如果用户想要在无论焦点的对象是什么时候都需要知道无论哪个对象处于焦点，则将设置 `Global` 为 true。 

**选择 Far 状态行为** 
 ![选择 "与虚拟手交互"](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**选择 Far 状态检查器** 
 ![在检查器中选择 "远端" 组件](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>获取选择远端状态事件

SelectFar 状态的事件配置类型： `SelectFarEvents`

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a>单击状态

单击状态由远处交互，单击 (默认情况下) 选择 "远端状态"。  此状态在内部切换到 on，调用 OnClicked 事件，然后立即切换到 off。 

> [!NOTE]
> 基于状态活动的检查器中的可视反馈对于已单击状态不存在，因为它会立即打开并关闭。 

**单击状态行为** 
 ![处于虚拟手交互状态的已单击状态](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

**单击的状态检查器** 
 ![单击检查器中的状态组件](../images/interactive-element/InEditor/ClickedStateInspector.png)

**近键和远键单击状态示例**  
可以使用 方法通过其他入口点触发单击 `interactiveElement.TriggerClickedState()` 的状态。  例如，如果用户还希望近交互触摸触发对对象的单击，则他们会将 方法添加为触控 `TriggerClickedState()` 状态中的侦听器。   

![具有虚拟手部交互的近近状态](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>获取已单击状态事件

&quot;已单击状态&quot;的事件配置类型： `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>"打开"和"关闭"状态

"打开"和"切换关闭"状态是一对，两者都需要存在以用于切换行为。  默认情况下，"打开"和"关闭"状态通过远部交互触发，单击"选择远 ("按钮) 。  默认情况下，"切换关闭"状态在开始时处于活动状态，这意味着切换将初始化为"关闭"。  如果用户希望"开启"状态在开始时处于活动状态，则"打开切换"状态设置为 `IsSelectedOnStart` true。

**ToggleOn 和 Toggle Off 状态行为** 
 ![使用虚拟手部交互打开和关闭](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**ToggleOn 和 Toggle Off 状态检查器** 
 ![在检查器中切换组件](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**近切换状态和远切换状态示例**  
与"已单击"状态类似，切换状态设置可以使用 方法具有多个 `interactiveElement.SetToggleStates()` 入口点。 例如，如果用户希望触摸作为附加入口点来设置切换状态，则他们将 方法添加到处于 `SetToggleStates()` Touch 状态的事件之一。 

![使用虚拟手部交互进行近近切换](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>启用和关闭状态事件

ToggleOn 状态的事件配置类型： `ToggleOnEvents`  
ToggleOff 状态的事件配置类型： `ToggleOffEvents`

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a>语音关键字状态

语音关键字状态侦听混合现实语音配置文件中定义的关键字。 在运行时之前，必须在语音命令配置文件中注册任何新的关键字 () 下面的步骤。 

**Speech 关键字状态行为** 
 ![具有虚拟交互的语音关键字](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

**Speech 关键字状态检查器** 
 ![检查器中的语音关键字组件](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> 通过按以上 gif 中的 F5 键，在编辑器中触发了语音关键字状态。 以下步骤概述了在编辑器中进行语音测试设置。 

#### <a name="how-to-register-a-speech-commandkeyword"></a>如何注册语音命令/关键字

1. 选择 **MixedRealityToolkit** 游戏对象

1. 选择 " **复制并自定义** 当前配置文件"

1. 导航到 "输入" 部分，然后选择 " **克隆** " 以启用对输入配置文件的修改

1. 向下滚动到输入配置文件中的语音部分，并克隆语音配置文件

    ![MRTK 游戏对象中的语音关键字配置文件](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. 选择 "添加新语音命令"

    ![在 MRTK 配置文件中添加新的语音关键字](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. 输入 new 关键字。 可选：将 KeyCode 更改为 F5 (或另一个 KeyCode) ，以允许在编辑器中进行测试。 

    ![在 MRTK 配置文件中配置 speech 关键字](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. 返回到交互式元素的语音关键字状态检查器，然后选择 "**添加关键字**" 

    ![向交互式元素组件添加关键字](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![关键字验证和注册](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. 输入刚刚在语音配置文件中注册的新关键字

    ![输入新的语音关键字](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


若要在编辑器中测试语音关键字状态，请按步骤 6 (F5 中定义的 KeyCode) 模拟语音关键字识别事件。

#### <a name="getting-speech-keyword-state-events&quot;></a>获取语音关键字状态事件

SpeechKeyword 状态的事件配置类型： `SpeechKeywordEvents`

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>(&quot;SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a>自定义状态

### <a name="how-to-create-a-custom-state-via-inspector"></a>如何通过检查器创建自定义状态 

通过检查器创建的自定义状态将初始化为默认状态事件配置。 自定义状态的默认事件配置为 类型，包含 `StateEvents` OnStateOn 和 OnStateOff 事件。

1. 在 Interactive 元素 **的检查器中** 导航到"创建自定义状态"。
    
    ![创建自定义状态](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. 输入新状态的名称。 此名称必须唯一，不能与现有的核心状态相同。 
    
    ![输入新自定义状态的名称](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. 选择 **"设置状态名称** "以添加到状态列表。
    
    ![将自定义状态添加到状态列表](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   此自定义状态使用包含 和 事件 `StateEvents` 的默认事件配置 `OnStateOn` `OnStateOff` 进行初始化。 若要为新状态创建自定义事件配置，请参阅：使用自定义事件配置 [创建自定义状态](#creating-a-custom-state-with-a-custom-event-configuration)。
    
    ![交互式元素组件中显示的新状态](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a>如何通过脚本创建自定义状态

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>使用自定义事件配置创建自定义状态 

名为 **键盘** 的自定义状态的示例文件位于此处： MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

以下步骤介绍了创建自定义状态事件配置和接收方文件的现有示例。

1. 考虑状态名称。  此名称必须唯一，并且不能与现有的核心状态相同。 出于本示例的目的，状态名称将是 **键盘**。

1. 创建两个 .cs 文件，分别为 state name + "接收方" 和状态名称 + "事件"。 需要在内部考虑这些文件的命名，并且必须遵循状态名称 + 事件/接收方约定。 

    ![键盘状态脚本](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. 有关文件内容的更多详细信息，请参阅 KeyboardEvents 和 KeyboardReceiver 文件。 新的事件配置类必须从继承 `BaseInteractionEventConfiguration` ，而新的事件接收器类必须继承自 `BaseEventReceiver` 。  有关键盘状态的状态设置的示例位于 `CustomStateSettingExample.cs` 文件中。 

1. 使用状态名称将状态添加到 Interactive 元素，如果事件配置和事件接收器文件存在，则会识别状态名称。  自定义事件配置文件中的属性应显示在检查器中。

    ![向交互式元素添加自定义状态 ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ 在交互式元素中识别的自定义状态](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. 有关事件配置和事件接收器文件的更多示例，请参阅以下路径中的文件：    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>示例场景 

交互式元素 + 状态可视化工具的示例场景位于此处： MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![带有交互式元素和状态可视化工具的示例场景](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Compressable 按钮

示例场景包含名为和的 prototyping `CompressableButton` `CompressableButtonToggle` ，这些 prototyping 镜像 `PressableButtonHoloLens2` 使用交互式元素和状态可视化工具构造的按钮的行为。 `CompressableButton`组件当前将和的组合为 `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` 作为基类。 

## <a name="state-visualizer-experimental"></a>状态可视化工具 [实验]

状态可视化工具组件根据链接的交互式元素组件中定义的状态将动画添加到对象。 此组件创建动画资产，将其放置在 MixedRealityToolkit 文件夹中，通过将动画处理属性添加到目标游戏对象，启用简化的动画关键帧设置。 若要在状态之间启用动画过渡，将创建 Animator 控制器资产，并使用关联的参数和任何状态转换生成默认的状态机。  可以在 Unity 的 Animator 窗口中查看状态机。

### <a name="state-visualizer-and-unity-animation-system"></a>状态可视化工具和 Unity 动画系统

状态可视化工具当前利用了 Unity 动画系统。 

当按下状态可视化工具中的 " **生成新动画剪辑** " 按钮时，将基于交互元素中的状态名称生成新的动画剪辑资产，并将其放置在 MixedRealityToolkit 文件夹中。 每个状态容器中的动画剪辑属性都设置为关联的动画剪辑。

![状态可视化工具组件中的动画剪辑](../images/interactive-element/StateVisualizer/AnimationClips.png)

还会生成 [Animator 状态机](https://docs.unity3d.com/Manual/AnimationOverview.html) 来管理动画剪辑间的平滑转换。  默认情况下，状态机利用 " [任何" 状态](https://docs.unity3d.com/Manual/class-State.html) 以允许交互式元素中任何状态之间的转换。 

[还会针对每种状态生成](https://docs.unity3d.com/Manual/AnimationParameters.html) 在动画器中触发的状态可视化工具，在状态可视化工具中使用触发器参数来触发动画。

![Unity 状态机](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>运行时限制 

必须通过检查器将状态可视化工具添加到对象，并且不能通过脚本添加。  修改 AnimatorStateMachine/AnimationController 的属性包含在编辑器命名空间 () 生成应用时将 `UnityEditor.Animations` 被删除。

## <a name="how-to-use-the-state-visualizer"></a>如何使用状态可视化工具

1. 创建多维数据集
1. 附加 Interactive 元素
1. 附加状态可视化工具
1. 选择 **"生成新动画剪辑"**

    ![生成新的动画剪辑](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![在可视化工具与交互式元素组件中显示生成的动画剪辑](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. 在"焦点状态"容器中，选择" **添加目标"**

    ![添加状态可视化工具目标](../images/interactive-element/StateVisualizer/AddTarget.png)

1. 将当前游戏对象拖到目标字段 

    ![设置状态可视化工具目标](../images/interactive-element/StateVisualizer/SetTarget.png)

1. 打开多维数据集动画属性折叠
1. 选择"Animatable"属性下拉菜单，然后选择" **颜色"**

    ![设置状态可视化工具颜色](../images/interactive-element/StateVisualizer/SetColor.png)

1. 选择 **"添加颜色动画"属性**

    ![选择可视化工具颜色动画属性](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. 选择颜色 

    ![从色轮选择可视化工具颜色](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. 按下播放并观察过渡颜色更改

    ![具有虚拟手交互的过渡颜色更改示例](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>动画处理属性

动画处理属性的主要目的是简化动画剪辑关键帧设置。  如果用户熟悉 Unity 动画系统并且希望直接在生成的动画剪辑上设置关键帧，则它们只需将动画处理属性添加到目标对象并在 Unity 的动画窗口中打开剪辑 (Windows > 动画 > 动画) 。 

如果使用动画的动画处理属性，则曲线类型将设置为 EaseInOut。

**当前动画处理属性：**
- [刻度偏移量](#scale-offset)
- [位置偏移量](#position-offset)
- [颜色](#color)
- [着色器颜色](#shader-color)
- [着色器浮动](#shader-float)
- [着色器矢量](#shader-vector)

### <a name="scale-offset"></a>刻度偏移量

Scale Offset 动画处理属性采用对象的当前小数位数，并添加定义的偏移量。

![与虚拟手交互的缩放偏移](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>位置偏移量

Position Offset 动画处理属性采用对象的当前位置，并添加定义的偏移量。

![与虚拟手交互的位置偏移量](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Color

如果材料具有主颜色属性，则 Color Animatable 属性表示材料的主颜色。 此属性对 属性进行 `material._Color` 动画处理。

![通过虚拟手部交互更改焦点颜色](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>着色器颜色

着色器颜色 Animatable 属性是指颜色类型的着色器属性。 所有着色器属性都需要属性名称。 下面的 gif 演示了对名为 Fill_Color颜色属性进行动画处理，该属性不是主要材料颜色。  观察材料检查器中的更改值。

![使用虚拟手部交互的着色颜色](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>着色器 Float

着色器 Float Animatable 属性引用 float 类型的着色器属性。 所有着色器属性都需要属性名称。 在下面的 gif 中，观察"金属"属性的材料检查器中不断变化的值。 

![具有虚拟手部交互的着色器浮动](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>着色器向量

着色器矢量 Animatable 属性引用 Vector4 类型的着色器属性。 所有着色器属性都需要属性名称。 在下面的 gif 中，观察"主图"属性的平铺 (检查器Tex_ST) 值。 

![具有虚拟手部交互的着色器向量](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>如何查找可着色器属性名称

1. 导航到窗口 > 动画 > 动画
1. 确保在层次结构中选择了具有状态可视化工具的对象
1. 在动画窗口中选择任何动画剪辑
1. 选择 " **添加属性**"，打开网格呈现器 foldout 

    ![在 Animator 窗口中添加动画属性](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. 此列表包含所有动画处理属性名称的名称 

    ![Animator 窗口中的网格呈现器动画属性](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>另请参阅

- [**按钮**](../ux-building-blocks/button.md)
- [**边界控制**](../ux-building-blocks/bounds-control.md)
- [**网格对象集合**](../ux-building-blocks/object-collection.md)
- [**RadialView 求解器**](../ux-building-blocks/solvers/solver.md)
