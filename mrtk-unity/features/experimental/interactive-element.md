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
# <a name="interactive-element-experimental"></a><span data-ttu-id="8c880-104">Interactive 元素 [实验]</span><span class="sxs-lookup"><span data-stu-id="8c880-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="8c880-105">MRTK 输入系统的简化集中入口点。</span><span class="sxs-lookup"><span data-stu-id="8c880-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="8c880-106">包含状态管理方法、事件管理和核心交互状态的状态设置逻辑。</span><span class="sxs-lookup"><span data-stu-id="8c880-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="8c880-107">Interactive Element 是 Unity 2019.3 及更新版中支持的实验性功能，因为它利用 Unity 2019.3 的新功能： [序列化引用](https://docs.unity3d.com/ScriptReference/SerializeReference.html)。</span><span class="sxs-lookup"><span data-stu-id="8c880-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="8c880-108">Interactive 元素检查器</span><span class="sxs-lookup"><span data-stu-id="8c880-108">Interactive Element Inspector</span></span>

<span data-ttu-id="8c880-109">在播放模式下，Interactive Element 检查器提供可视反馈，指示当前状态是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="8c880-110">如果状态处于活动状态，则以蓝绿色突出显示该状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="8c880-111">如果状态不处于活动状态，则颜色不会更改。</span><span class="sxs-lookup"><span data-stu-id="8c880-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="8c880-112">检查器中状态旁边的数字是状态值，如果状态处于活动状态，则值为 1，如果状态不活动，则值为 0。</span><span class="sxs-lookup"><span data-stu-id="8c880-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![交互式元素与虚拟手部交互](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="8c880-114">核心状态</span><span class="sxs-lookup"><span data-stu-id="8c880-114">Core States</span></span>

<span data-ttu-id="8c880-115">Interactive 元素包含核心状态，并支持添加 [自定义状态](#custom-states)。</span><span class="sxs-lookup"><span data-stu-id="8c880-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="8c880-116">核心状态是已在 中定义状态设置逻辑的状态 `BaseInteractiveElement` 状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="8c880-117">下面是当前输入驱动核心状态的列表：</span><span class="sxs-lookup"><span data-stu-id="8c880-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="8c880-118">当前核心状态</span><span class="sxs-lookup"><span data-stu-id="8c880-118">Current Core States</span></span>

- [<span data-ttu-id="8c880-119">默认值</span><span class="sxs-lookup"><span data-stu-id="8c880-119">Default</span></span>](#default-state) 

<span data-ttu-id="8c880-120">近近交互核心状态：</span><span class="sxs-lookup"><span data-stu-id="8c880-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="8c880-121">焦点</span><span class="sxs-lookup"><span data-stu-id="8c880-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="8c880-122">近交互核心状态：</span><span class="sxs-lookup"><span data-stu-id="8c880-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="8c880-123">焦点附近</span><span class="sxs-lookup"><span data-stu-id="8c880-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="8c880-124">触控</span><span class="sxs-lookup"><span data-stu-id="8c880-124">Touch</span></span>](#touch-state)

<span data-ttu-id="8c880-125">远交互核心状态：</span><span class="sxs-lookup"><span data-stu-id="8c880-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="8c880-126">最大焦点</span><span class="sxs-lookup"><span data-stu-id="8c880-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="8c880-127">选择远</span><span class="sxs-lookup"><span data-stu-id="8c880-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="8c880-128">其他核心状态：</span><span class="sxs-lookup"><span data-stu-id="8c880-128">Other Core States:</span></span>
- [<span data-ttu-id="8c880-129">Clicked</span><span class="sxs-lookup"><span data-stu-id="8c880-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="8c880-130">开启和关闭切换</span><span class="sxs-lookup"><span data-stu-id="8c880-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="8c880-131">Speech 关键字</span><span class="sxs-lookup"><span data-stu-id="8c880-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="8c880-132">如何通过检查器添加核心状态</span><span class="sxs-lookup"><span data-stu-id="8c880-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="8c880-133">在交互式元素的检查器中导航到 " **添加核心状态** "。</span><span class="sxs-lookup"><span data-stu-id="8c880-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![通过检查器添加核心状态](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="8c880-135">选择 " **选择状态** " 按钮，选择要添加的核心状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="8c880-136">菜单中的状态按交互类型进行排序。</span><span class="sxs-lookup"><span data-stu-id="8c880-136">The states in the menu are sorted by interaction type.</span></span>

    ![使用所选状态通过检查器添加核心状态](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="8c880-138">打开 "事件配置 foldout"，查看与状态关联的事件和属性。</span><span class="sxs-lookup"><span data-stu-id="8c880-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![使用事件配置通过检查器添加核心状态](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="8c880-140">如何通过脚本添加核心状态</span><span class="sxs-lookup"><span data-stu-id="8c880-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="8c880-141">使用 `AddNewState(stateName)` 方法添加核心状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="8c880-142">有关可用核心状态名称的列表，请使用 `CoreInteractionState` 枚举。</span><span class="sxs-lookup"><span data-stu-id="8c880-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="8c880-143">状态内部结构</span><span class="sxs-lookup"><span data-stu-id="8c880-143">States Internal Structure</span></span> 

<span data-ttu-id="8c880-144">交互式元素中的状态为类型 `InteractionState` 。</span><span class="sxs-lookup"><span data-stu-id="8c880-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="8c880-145">`InteractionState`包含以下属性：</span><span class="sxs-lookup"><span data-stu-id="8c880-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="8c880-146">**名称**：状态的名称。</span><span class="sxs-lookup"><span data-stu-id="8c880-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="8c880-147">**值**：状态值。</span><span class="sxs-lookup"><span data-stu-id="8c880-147">**Value**: The state value.</span></span>  <span data-ttu-id="8c880-148">如果状态为 "on"，则 "状态" 值为 "1"。</span><span class="sxs-lookup"><span data-stu-id="8c880-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="8c880-149">如果状态为 "关"，则 "状态" 值为 "0"。</span><span class="sxs-lookup"><span data-stu-id="8c880-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="8c880-150">**活动**：状态当前是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="8c880-151">当状态为 on 时，活动属性的值为 true，如果状态为 off，则为 false。</span><span class="sxs-lookup"><span data-stu-id="8c880-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="8c880-152">**交互类型**：状态的交互类型是指状态适用的交互类型。</span><span class="sxs-lookup"><span data-stu-id="8c880-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="8c880-153">`None`：不支持任何形式的输入交互。</span><span class="sxs-lookup"><span data-stu-id="8c880-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="8c880-154">`Near`：近乎交互支持。</span><span class="sxs-lookup"><span data-stu-id="8c880-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="8c880-155">当有向外的人与其他游戏对象直接联系时，输入被视为接近交互，即，可表述的手接近于世界空间中游戏对象的位置的位置。</span><span class="sxs-lookup"><span data-stu-id="8c880-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="8c880-156">`Far`：远交互支持。</span><span class="sxs-lookup"><span data-stu-id="8c880-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="8c880-157">不需要直接联系游戏对象时，会将输入视为交互。</span><span class="sxs-lookup"><span data-stu-id="8c880-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="8c880-158">例如，通过控制器射线或注视的输入被视为远交互输入。</span><span class="sxs-lookup"><span data-stu-id="8c880-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="8c880-159">`NearAndFar`：包含近和远交互支持。</span><span class="sxs-lookup"><span data-stu-id="8c880-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="8c880-160">`Other`：指针独立交互支持。</span><span class="sxs-lookup"><span data-stu-id="8c880-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="8c880-161">**事件配置**：状态的事件配置是序列化事件配置文件入口点。</span><span class="sxs-lookup"><span data-stu-id="8c880-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="8c880-162">所有这些属性都是在 `State Manager` 包含在交互式元素中的内部设置的。</span><span class="sxs-lookup"><span data-stu-id="8c880-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="8c880-163">若要修改状态，请使用以下帮助器方法：</span><span class="sxs-lookup"><span data-stu-id="8c880-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="8c880-164">**状态设置 Helper 方法**</span><span class="sxs-lookup"><span data-stu-id="8c880-164">**State Setting Helper Methods**</span></span>

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

<span data-ttu-id="8c880-165">获取状态的事件配置特定于状态本身。</span><span class="sxs-lookup"><span data-stu-id="8c880-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="8c880-166">每个核心状态都有特定的事件配置类型，下面概述了描述每个核心状态的各节。</span><span class="sxs-lookup"><span data-stu-id="8c880-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="8c880-167">下面是获取状态事件配置的一般化示例：</span><span class="sxs-lookup"><span data-stu-id="8c880-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="8c880-168">默认状态</span><span class="sxs-lookup"><span data-stu-id="8c880-168">Default State</span></span>

<span data-ttu-id="8c880-169">默认状态始终存在于交互式元素上。</span><span class="sxs-lookup"><span data-stu-id="8c880-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="8c880-170">此状态仅在所有其他状态均不处于活动状态时才处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="8c880-171">如果任何其他状态变为活动状态，则将在内部将默认状态设置为 "关闭"。</span><span class="sxs-lookup"><span data-stu-id="8c880-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="8c880-172">将使用状态列表中显示的默认值和焦点状态初始化交互式元素。</span><span class="sxs-lookup"><span data-stu-id="8c880-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="8c880-173">默认状态始终需要存在于状态列表中。</span><span class="sxs-lookup"><span data-stu-id="8c880-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="8c880-174">获取默认状态事件</span><span class="sxs-lookup"><span data-stu-id="8c880-174">Getting Default State Events</span></span>

<span data-ttu-id="8c880-175">默认状态的事件配置类型： `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="8c880-175">Event configuration type for the Default State: `StateEvents`</span></span>

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

### <a name="focus-state"></a><span data-ttu-id="8c880-176">焦点状态</span><span class="sxs-lookup"><span data-stu-id="8c880-176">Focus State</span></span>

<span data-ttu-id="8c880-177">焦点状态是近和远交互状态，可被视为与悬停等效的混合现实。</span><span class="sxs-lookup"><span data-stu-id="8c880-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="8c880-178">对于焦点状态，几乎交互与远端交互之间的区别是当前活动指针类型。</span><span class="sxs-lookup"><span data-stu-id="8c880-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="8c880-179">如果焦点状态的指针类型是 "获取" 指针，则会将交互视为接近交互。</span><span class="sxs-lookup"><span data-stu-id="8c880-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="8c880-180">如果主指针不是 ""，则会将交互视为远交互。</span><span class="sxs-lookup"><span data-stu-id="8c880-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="8c880-181">默认情况下，在交互式元素中显示焦点状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="8c880-182">**焦点状态行为** 
 ![具有虚拟手交互的焦点状态](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="8c880-182">**Focus State Behavior**
![Focus state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="8c880-183">**焦点状态检查器** 
 ![Inpsector 中的焦点状态](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="8c880-183">**Focus State Inspector**
![Focus state in the Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events&quot;></a><span data-ttu-id=&quot;8c880-184&quot;>正在获取焦点状态事件</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-184&quot;>Getting Focus State Events</span></span>

<span data-ttu-id=&quot;8c880-185&quot;>焦点状态的事件配置类型： `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-185&quot;>Event configuration type for the Focus State: `FocusEvents`</span></span>

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

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="8c880-186">专注于 vs 重心的行为</span><span class="sxs-lookup"><span data-stu-id="8c880-186">Focus Near vs Focus Far Behavior</span></span> 

![使用虚拟手部交互进行近近和远焦点](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="8c880-188">焦点接近状态</span><span class="sxs-lookup"><span data-stu-id="8c880-188">Focus Near State</span></span>

<span data-ttu-id="8c880-189">当引发焦点事件且主指针为"开小马"指针（指示近交互）时，将设置"焦点附近"状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="8c880-190">**焦点接近状态行为** 
 ![通过虚拟手部交互将焦点放在接近状态](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="8c880-190">**Focus Near State Behavior**
![Focus near state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="8c880-191">**焦点近状态检查器** 
 ![检查器中靠近组件的焦点](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="8c880-191">**Focus Near State Inspector**
![Focus near component in the Inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events&quot;></a><span data-ttu-id=&quot;8c880-192&quot;>获取 FocusNear 状态事件</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-192&quot;>Getting FocusNear State Events</span></span>

<span data-ttu-id=&quot;8c880-193&quot;>FocusNear 状态的事件配置类型： `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-193&quot;>Event configuration type for the FocusNear State: `FocusEvents`</span></span>

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

### <a name="focus-far-state"></a><span data-ttu-id="8c880-194">焦点远点状态</span><span class="sxs-lookup"><span data-stu-id="8c880-194">Focus Far State</span></span>

<span data-ttu-id="8c880-195">当主指针不是"焦点指针"时，将设置"焦点远"状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="8c880-196">例如，默认控制器射线指针和 GGV (凝视、手势、语音) 指针被视为远交互指针。</span><span class="sxs-lookup"><span data-stu-id="8c880-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="8c880-197">**焦点远状态行为** 
 ![与虚拟手部交互远的焦点状态](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="8c880-197">**Focus Far State Behavior**
![Focus state far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="8c880-198">**焦点远状态检查器** 
 ![检查器中的焦点远部分](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="8c880-198">**Focus Far State Inspector**
![Focus far component in the Inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events&quot;></a><span data-ttu-id=&quot;8c880-199&quot;>获取焦点远场状态事件</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-199&quot;>Getting Focus Far State Events</span></span>

<span data-ttu-id=&quot;8c880-200&quot;>FocusFar 状态的事件配置类型： `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-200&quot;>Event configuration type for the FocusFar State: `FocusEvents`</span></span>

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

### <a name="touch-state"></a><span data-ttu-id="8c880-201">触控状态</span><span class="sxs-lookup"><span data-stu-id="8c880-201">Touch State</span></span>

<span data-ttu-id="8c880-202">触摸状态是一种近交互状态，当一个明确表达的手直接触摸对象时，将设置此状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="8c880-203">直接触摸意味着铰接手的索引指非常接近对象的世界位置。</span><span class="sxs-lookup"><span data-stu-id="8c880-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="8c880-204">默认情况下，如果将 Touch 状态添加到状态列表，则组件将附加到 `NearInteractionTouchableVolume` 对象。</span><span class="sxs-lookup"><span data-stu-id="8c880-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="8c880-205">检测 Touch  `NearInteractionTouchableVolume` `NearInteractionTouchable` 事件需要存在 或 组件。</span><span class="sxs-lookup"><span data-stu-id="8c880-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="8c880-206">和 之间的区别在于，基于对象的碰撞体检测触摸，并检测平面 `NearInteractionTouchableVolume` `NearInteractionTouchable` `NearInteractionTouchableVolume` `NearInteractionTouchable` 的已定义区域中的触摸。</span><span class="sxs-lookup"><span data-stu-id="8c880-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="8c880-207">**触摸状态行为** 
 ![具有虚拟手交互的触摸状态](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="8c880-207">**Touch State Behavior**
![Touch state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="8c880-208">**触控状态检查器** 
 ![检查器中的触摸状态组件](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="8c880-208">**Touch State Inspector**
![Touch state component in the Inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events&quot;></a><span data-ttu-id=&quot;8c880-209&quot;>获取触摸状态事件</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-209&quot;>Getting Touch State Events</span></span>

<span data-ttu-id=&quot;8c880-210&quot;>触摸状态的事件配置类型： `TouchEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-210&quot;>Event configuration type for the Touch State: `TouchEvents`</span></span>

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

### <a name="select-far-state"></a><span data-ttu-id="8c880-211">选择 Far 状态</span><span class="sxs-lookup"><span data-stu-id="8c880-211">Select Far State</span></span>

<span data-ttu-id="8c880-212">选择的状态为 "选择" `IMixedRealityPointerHandler` 。</span><span class="sxs-lookup"><span data-stu-id="8c880-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="8c880-213">此状态是一种远交互状态，检测到远交互单击 (轻点击) ，并通过使用 far 交互指针（例如，默认控制器射线指针或 GGV 指针）进行保存。</span><span class="sxs-lookup"><span data-stu-id="8c880-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="8c880-214">在事件配置 foldout 下，"选择最多" 状态具有一个选项 `Global` 。</span><span class="sxs-lookup"><span data-stu-id="8c880-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="8c880-215">如果 `Global` 为 true，则 `IMixedRealityPointerHandler` 将注册为全局输入处理程序。</span><span class="sxs-lookup"><span data-stu-id="8c880-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="8c880-216">如果处理程序注册为 global，则不需要将焦点放在对象上来触发输入系统事件。</span><span class="sxs-lookup"><span data-stu-id="8c880-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="8c880-217">例如，如果用户想要在无论焦点的对象是什么时候都需要知道无论哪个对象处于焦点，则将设置 `Global` 为 true。</span><span class="sxs-lookup"><span data-stu-id="8c880-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="8c880-218">**选择 Far 状态行为** 
 ![选择 "与虚拟手交互"](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="8c880-218">**Select Far State Behavior**
![Select far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="8c880-219">**选择 Far 状态检查器** 
 ![在检查器中选择 "远端" 组件](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="8c880-219">**Select Far State Inspector**
![Select far component in the Inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events&quot;></a><span data-ttu-id=&quot;8c880-220&quot;>获取选择远端状态事件</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-220&quot;>Getting Select Far State Events</span></span>

<span data-ttu-id=&quot;8c880-221&quot;>SelectFar 状态的事件配置类型： `SelectFarEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-221&quot;>Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

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

### <a name="clicked-state"></a><span data-ttu-id="8c880-222">单击状态</span><span class="sxs-lookup"><span data-stu-id="8c880-222">Clicked State</span></span>

<span data-ttu-id="8c880-223">单击状态由远处交互，单击 (默认情况下) 选择 "远端状态"。</span><span class="sxs-lookup"><span data-stu-id="8c880-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="8c880-224">此状态在内部切换到 on，调用 OnClicked 事件，然后立即切换到 off。</span><span class="sxs-lookup"><span data-stu-id="8c880-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="8c880-225">基于状态活动的检查器中的可视反馈对于已单击状态不存在，因为它会立即打开并关闭。</span><span class="sxs-lookup"><span data-stu-id="8c880-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="8c880-226">**单击状态行为** 
 ![处于虚拟手交互状态的已单击状态](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="8c880-226">**Clicked State Behavior**
![Clicked state with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="8c880-227">**单击的状态检查器** 
 ![单击检查器中的状态组件](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="8c880-227">**Clicked State Inspector**
![Click state component in the Inspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="8c880-228">**近键和远键单击状态示例**</span><span class="sxs-lookup"><span data-stu-id="8c880-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="8c880-229">可以使用 方法通过其他入口点触发单击 `interactiveElement.TriggerClickedState()` 的状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="8c880-230">例如，如果用户还希望近交互触摸触发对对象的单击，则他们会将 方法添加为触控 `TriggerClickedState()` 状态中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="8c880-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![具有虚拟手部交互的近近状态](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a><span data-ttu-id=&quot;8c880-232&quot;>获取已单击状态事件</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-232&quot;>Getting Clicked State Events</span></span>

<span data-ttu-id=&quot;8c880-233&quot;>&quot;已单击状态&quot;的事件配置类型： `ClickedEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-233&quot;>Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="8c880-234">"打开"和"关闭"状态</span><span class="sxs-lookup"><span data-stu-id="8c880-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="8c880-235">"打开"和"切换关闭"状态是一对，两者都需要存在以用于切换行为。</span><span class="sxs-lookup"><span data-stu-id="8c880-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="8c880-236">默认情况下，"打开"和"关闭"状态通过远部交互触发，单击"选择远 ("按钮) 。</span><span class="sxs-lookup"><span data-stu-id="8c880-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="8c880-237">默认情况下，"切换关闭"状态在开始时处于活动状态，这意味着切换将初始化为"关闭"。</span><span class="sxs-lookup"><span data-stu-id="8c880-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="8c880-238">如果用户希望"开启"状态在开始时处于活动状态，则"打开切换"状态设置为 `IsSelectedOnStart` true。</span><span class="sxs-lookup"><span data-stu-id="8c880-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="8c880-239">**ToggleOn 和 Toggle Off 状态行为** 
 ![使用虚拟手部交互打开和关闭](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="8c880-239">**ToggleOn and Toggle Off State Behavior**
![Toggle on and off with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="8c880-240">**ToggleOn 和 Toggle Off 状态检查器** 
 ![在检查器中切换组件](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="8c880-240">**ToggleOn and Toggle Off State Inspector**
![Toggle component in the Inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="8c880-241">**近切换状态和远切换状态示例**</span><span class="sxs-lookup"><span data-stu-id="8c880-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="8c880-242">与"已单击"状态类似，切换状态设置可以使用 方法具有多个 `interactiveElement.SetToggleStates()` 入口点。</span><span class="sxs-lookup"><span data-stu-id="8c880-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="8c880-243">例如，如果用户希望触摸作为附加入口点来设置切换状态，则他们将 方法添加到处于 `SetToggleStates()` Touch 状态的事件之一。</span><span class="sxs-lookup"><span data-stu-id="8c880-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![使用虚拟手部交互进行近近切换](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a><span data-ttu-id=&quot;8c880-245&quot;>启用和关闭状态事件</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-245&quot;>Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id=&quot;8c880-246&quot;>ToggleOn 状态的事件配置类型： `ToggleOnEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-246&quot;>Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id=&quot;8c880-247&quot;>ToggleOff 状态的事件配置类型： `ToggleOffEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-247&quot;>Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

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

### <a name="speech-keyword-state"></a><span data-ttu-id="8c880-248">语音关键字状态</span><span class="sxs-lookup"><span data-stu-id="8c880-248">Speech Keyword State</span></span>

<span data-ttu-id="8c880-249">语音关键字状态侦听混合现实语音配置文件中定义的关键字。</span><span class="sxs-lookup"><span data-stu-id="8c880-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="8c880-250">在运行时之前，必须在语音命令配置文件中注册任何新的关键字 () 下面的步骤。</span><span class="sxs-lookup"><span data-stu-id="8c880-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="8c880-251">**Speech 关键字状态行为** 
 ![具有虚拟交互的语音关键字](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="8c880-251">**Speech Keyword State Behavior**
![Speech keyword with virtual interaction](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="8c880-252">**Speech 关键字状态检查器** 
 ![检查器中的语音关键字组件](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="8c880-252">**Speech Keyword State Inspector**
![Speech keyword component in the Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="8c880-253">通过按以上 gif 中的 F5 键，在编辑器中触发了语音关键字状态。</span><span class="sxs-lookup"><span data-stu-id="8c880-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="8c880-254">以下步骤概述了在编辑器中进行语音测试设置。</span><span class="sxs-lookup"><span data-stu-id="8c880-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="8c880-255">如何注册语音命令/关键字</span><span class="sxs-lookup"><span data-stu-id="8c880-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="8c880-256">选择 **MixedRealityToolkit** 游戏对象</span><span class="sxs-lookup"><span data-stu-id="8c880-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="8c880-257">选择 " **复制并自定义** 当前配置文件"</span><span class="sxs-lookup"><span data-stu-id="8c880-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="8c880-258">导航到 "输入" 部分，然后选择 " **克隆** " 以启用对输入配置文件的修改</span><span class="sxs-lookup"><span data-stu-id="8c880-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="8c880-259">向下滚动到输入配置文件中的语音部分，并克隆语音配置文件</span><span class="sxs-lookup"><span data-stu-id="8c880-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![MRTK 游戏对象中的语音关键字配置文件](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="8c880-261">选择 "添加新语音命令"</span><span class="sxs-lookup"><span data-stu-id="8c880-261">Select Add a New Speech Command</span></span>

    ![在 MRTK 配置文件中添加新的语音关键字](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="8c880-263">输入 new 关键字。</span><span class="sxs-lookup"><span data-stu-id="8c880-263">Enter the new keyword.</span></span> <span data-ttu-id="8c880-264">可选：将 KeyCode 更改为 F5 (或另一个 KeyCode) ，以允许在编辑器中进行测试。</span><span class="sxs-lookup"><span data-stu-id="8c880-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![在 MRTK 配置文件中配置 speech 关键字](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="8c880-266">返回到交互式元素的语音关键字状态检查器，然后选择 "**添加关键字**"</span><span class="sxs-lookup"><span data-stu-id="8c880-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![向交互式元素组件添加关键字](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![关键字验证和注册](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="8c880-269">输入刚刚在语音配置文件中注册的新关键字</span><span class="sxs-lookup"><span data-stu-id="8c880-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![输入新的语音关键字](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="8c880-271">若要在编辑器中测试语音关键字状态，请按步骤 6 (F5 中定义的 KeyCode) 模拟语音关键字识别事件。</span><span class="sxs-lookup"><span data-stu-id="8c880-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="8c880-272">获取语音关键字状态事件</span><span class="sxs-lookup"><span data-stu-id="8c880-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="8c880-273">SpeechKeyword 状态的事件配置类型： `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="8c880-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>("SpeechKeyword");

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

## <a name="custom-states"></a><span data-ttu-id="8c880-274">自定义状态</span><span class="sxs-lookup"><span data-stu-id="8c880-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="8c880-275">如何通过检查器创建自定义状态</span><span class="sxs-lookup"><span data-stu-id="8c880-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="8c880-276">通过检查器创建的自定义状态将初始化为默认状态事件配置。</span><span class="sxs-lookup"><span data-stu-id="8c880-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="8c880-277">自定义状态的默认事件配置为 类型，包含 `StateEvents` OnStateOn 和 OnStateOff 事件。</span><span class="sxs-lookup"><span data-stu-id="8c880-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="8c880-278">在 Interactive 元素 **的检查器中** 导航到"创建自定义状态"。</span><span class="sxs-lookup"><span data-stu-id="8c880-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![创建自定义状态](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="8c880-280">输入新状态的名称。</span><span class="sxs-lookup"><span data-stu-id="8c880-280">Enter the name of the new state.</span></span> <span data-ttu-id="8c880-281">此名称必须唯一，不能与现有的核心状态相同。</span><span class="sxs-lookup"><span data-stu-id="8c880-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![输入新自定义状态的名称](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="8c880-283">选择 **"设置状态名称** "以添加到状态列表。</span><span class="sxs-lookup"><span data-stu-id="8c880-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![将自定义状态添加到状态列表](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="8c880-285">此自定义状态使用包含 和 事件 `StateEvents` 的默认事件配置 `OnStateOn` `OnStateOff` 进行初始化。</span><span class="sxs-lookup"><span data-stu-id="8c880-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="8c880-286">若要为新状态创建自定义事件配置，请参阅：使用自定义事件配置 [创建自定义状态](#creating-a-custom-state-with-a-custom-event-configuration)。</span><span class="sxs-lookup"><span data-stu-id="8c880-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![交互式元素组件中显示的新状态](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a><span data-ttu-id=&quot;8c880-288&quot;>如何通过脚本创建自定义状态</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c880-288&quot;>How to Create a Custom State via Script</span></span>

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

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="8c880-289">使用自定义事件配置创建自定义状态</span><span class="sxs-lookup"><span data-stu-id="8c880-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="8c880-290">名为 **键盘** 的自定义状态的示例文件位于此处： MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span><span class="sxs-lookup"><span data-stu-id="8c880-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="8c880-291">以下步骤介绍了创建自定义状态事件配置和接收方文件的现有示例。</span><span class="sxs-lookup"><span data-stu-id="8c880-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="8c880-292">考虑状态名称。</span><span class="sxs-lookup"><span data-stu-id="8c880-292">Think of a state name.</span></span>  <span data-ttu-id="8c880-293">此名称必须唯一，并且不能与现有的核心状态相同。</span><span class="sxs-lookup"><span data-stu-id="8c880-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="8c880-294">出于本示例的目的，状态名称将是 **键盘**。</span><span class="sxs-lookup"><span data-stu-id="8c880-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="8c880-295">创建两个 .cs 文件，分别为 state name + "接收方" 和状态名称 + "事件"。</span><span class="sxs-lookup"><span data-stu-id="8c880-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="8c880-296">需要在内部考虑这些文件的命名，并且必须遵循状态名称 + 事件/接收方约定。</span><span class="sxs-lookup"><span data-stu-id="8c880-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![键盘状态脚本](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="8c880-298">有关文件内容的更多详细信息，请参阅 KeyboardEvents 和 KeyboardReceiver 文件。</span><span class="sxs-lookup"><span data-stu-id="8c880-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="8c880-299">新的事件配置类必须从继承 `BaseInteractionEventConfiguration` ，而新的事件接收器类必须继承自 `BaseEventReceiver` 。</span><span class="sxs-lookup"><span data-stu-id="8c880-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="8c880-300">有关键盘状态的状态设置的示例位于 `CustomStateSettingExample.cs` 文件中。</span><span class="sxs-lookup"><span data-stu-id="8c880-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="8c880-301">使用状态名称将状态添加到 Interactive 元素，如果事件配置和事件接收器文件存在，则会识别状态名称。</span><span class="sxs-lookup"><span data-stu-id="8c880-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="8c880-302">自定义事件配置文件中的属性应显示在检查器中。</span><span class="sxs-lookup"><span data-stu-id="8c880-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="8c880-303">![向交互式元素添加自定义状态 ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ 在交互式元素中识别的自定义状态](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="8c880-303">![Adding custom state to interactive element](../images/interactive-element/InEditor/AddKeyboardState.png) ![Custom state recognized in the interactive element](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="8c880-304">有关事件配置和事件接收器文件的更多示例，请参阅以下路径中的文件：</span><span class="sxs-lookup"><span data-stu-id="8c880-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="8c880-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span><span class="sxs-lookup"><span data-stu-id="8c880-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="8c880-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span><span class="sxs-lookup"><span data-stu-id="8c880-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="8c880-307">示例场景</span><span class="sxs-lookup"><span data-stu-id="8c880-307">Example Scene</span></span> 

<span data-ttu-id="8c880-308">交互式元素 + 状态可视化工具的示例场景位于此处： MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span><span class="sxs-lookup"><span data-stu-id="8c880-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![带有交互式元素和状态可视化工具的示例场景](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="8c880-310">Compressable 按钮</span><span class="sxs-lookup"><span data-stu-id="8c880-310">Compressable Button</span></span>

<span data-ttu-id="8c880-311">示例场景包含名为和的 prototyping `CompressableButton` `CompressableButtonToggle` ，这些 prototyping 镜像 `PressableButtonHoloLens2` 使用交互式元素和状态可视化工具构造的按钮的行为。</span><span class="sxs-lookup"><span data-stu-id="8c880-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="8c880-312">`CompressableButton`组件当前将和的组合为 `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` 作为基类。</span><span class="sxs-lookup"><span data-stu-id="8c880-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

## <a name="state-visualizer-experimental"></a><span data-ttu-id="8c880-313">状态可视化工具 [实验]</span><span class="sxs-lookup"><span data-stu-id="8c880-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="8c880-314">状态可视化工具组件根据链接的交互式元素组件中定义的状态将动画添加到对象。</span><span class="sxs-lookup"><span data-stu-id="8c880-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="8c880-315">此组件创建动画资产，将其放置在 MixedRealityToolkit 文件夹中，通过将动画处理属性添加到目标游戏对象，启用简化的动画关键帧设置。</span><span class="sxs-lookup"><span data-stu-id="8c880-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="8c880-316">若要在状态之间启用动画过渡，将创建 Animator 控制器资产，并使用关联的参数和任何状态转换生成默认的状态机。</span><span class="sxs-lookup"><span data-stu-id="8c880-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="8c880-317">可以在 Unity 的 Animator 窗口中查看状态机。</span><span class="sxs-lookup"><span data-stu-id="8c880-317">The state machine can be viewed in Unity's Animator window.</span></span>

### <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="8c880-318">状态可视化工具和 Unity 动画系统</span><span class="sxs-lookup"><span data-stu-id="8c880-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="8c880-319">状态可视化工具当前利用了 Unity 动画系统。</span><span class="sxs-lookup"><span data-stu-id="8c880-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="8c880-320">当按下状态可视化工具中的 " **生成新动画剪辑** " 按钮时，将基于交互元素中的状态名称生成新的动画剪辑资产，并将其放置在 MixedRealityToolkit 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8c880-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="8c880-321">每个状态容器中的动画剪辑属性都设置为关联的动画剪辑。</span><span class="sxs-lookup"><span data-stu-id="8c880-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![状态可视化工具组件中的动画剪辑](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="8c880-323">还会生成 [Animator 状态机](https://docs.unity3d.com/Manual/AnimationOverview.html) 来管理动画剪辑间的平滑转换。</span><span class="sxs-lookup"><span data-stu-id="8c880-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="8c880-324">默认情况下，状态机利用 " [任何" 状态](https://docs.unity3d.com/Manual/class-State.html) 以允许交互式元素中任何状态之间的转换。</span><span class="sxs-lookup"><span data-stu-id="8c880-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="8c880-325">[还会针对每种状态生成](https://docs.unity3d.com/Manual/AnimationParameters.html) 在动画器中触发的状态可视化工具，在状态可视化工具中使用触发器参数来触发动画。</span><span class="sxs-lookup"><span data-stu-id="8c880-325">[State visualizers triggered in the animator](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![Unity 状态机](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="8c880-327">运行时限制</span><span class="sxs-lookup"><span data-stu-id="8c880-327">Runtime Limitations</span></span> 

<span data-ttu-id="8c880-328">必须通过检查器将状态可视化工具添加到对象，并且不能通过脚本添加。</span><span class="sxs-lookup"><span data-stu-id="8c880-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="8c880-329">修改 AnimatorStateMachine/AnimationController 的属性包含在编辑器命名空间 () 生成应用时将 `UnityEditor.Animations` 被删除。</span><span class="sxs-lookup"><span data-stu-id="8c880-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="8c880-330">如何使用状态可视化工具</span><span class="sxs-lookup"><span data-stu-id="8c880-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="8c880-331">创建多维数据集</span><span class="sxs-lookup"><span data-stu-id="8c880-331">Create a Cube</span></span>
1. <span data-ttu-id="8c880-332">附加 Interactive 元素</span><span class="sxs-lookup"><span data-stu-id="8c880-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="8c880-333">附加状态可视化工具</span><span class="sxs-lookup"><span data-stu-id="8c880-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="8c880-334">选择 **"生成新动画剪辑"**</span><span class="sxs-lookup"><span data-stu-id="8c880-334">Select **Generate New Animation Clips**</span></span>

    ![生成新的动画剪辑](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![在可视化工具与交互式元素组件中显示生成的动画剪辑](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="8c880-337">在"焦点状态"容器中，选择" **添加目标"**</span><span class="sxs-lookup"><span data-stu-id="8c880-337">In the Focus state container, select **Add Target**</span></span>

    ![添加状态可视化工具目标](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="8c880-339">将当前游戏对象拖到目标字段</span><span class="sxs-lookup"><span data-stu-id="8c880-339">Drag the current game object to the target field</span></span> 

    ![设置状态可视化工具目标](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="8c880-341">打开多维数据集动画属性折叠</span><span class="sxs-lookup"><span data-stu-id="8c880-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="8c880-342">选择"Animatable"属性下拉菜单，然后选择" **颜色"**</span><span class="sxs-lookup"><span data-stu-id="8c880-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![设置状态可视化工具颜色](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="8c880-344">选择 **"添加颜色动画"属性**</span><span class="sxs-lookup"><span data-stu-id="8c880-344">Select **Add the Color Animatable Property**</span></span>

    ![选择可视化工具颜色动画属性](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="8c880-346">选择颜色</span><span class="sxs-lookup"><span data-stu-id="8c880-346">Choose a Color</span></span> 

    ![从色轮选择可视化工具颜色](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="8c880-348">按下播放并观察过渡颜色更改</span><span class="sxs-lookup"><span data-stu-id="8c880-348">Press play and observe the transitional color change</span></span>

    ![具有虚拟手交互的过渡颜色更改示例](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="8c880-350">动画处理属性</span><span class="sxs-lookup"><span data-stu-id="8c880-350">Animatable Properties</span></span>

<span data-ttu-id="8c880-351">动画处理属性的主要目的是简化动画剪辑关键帧设置。</span><span class="sxs-lookup"><span data-stu-id="8c880-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="8c880-352">如果用户熟悉 Unity 动画系统并且希望直接在生成的动画剪辑上设置关键帧，则它们只需将动画处理属性添加到目标对象并在 Unity 的动画窗口中打开剪辑 (Windows > 动画 > 动画) 。</span><span class="sxs-lookup"><span data-stu-id="8c880-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="8c880-353">如果使用动画的动画处理属性，则曲线类型将设置为 EaseInOut。</span><span class="sxs-lookup"><span data-stu-id="8c880-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="8c880-354">**当前动画处理属性：**</span><span class="sxs-lookup"><span data-stu-id="8c880-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="8c880-355">刻度偏移量</span><span class="sxs-lookup"><span data-stu-id="8c880-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="8c880-356">位置偏移量</span><span class="sxs-lookup"><span data-stu-id="8c880-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="8c880-357">颜色</span><span class="sxs-lookup"><span data-stu-id="8c880-357">Color</span></span>](#color)
- [<span data-ttu-id="8c880-358">着色器颜色</span><span class="sxs-lookup"><span data-stu-id="8c880-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="8c880-359">着色器浮动</span><span class="sxs-lookup"><span data-stu-id="8c880-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="8c880-360">着色器矢量</span><span class="sxs-lookup"><span data-stu-id="8c880-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="8c880-361">刻度偏移量</span><span class="sxs-lookup"><span data-stu-id="8c880-361">Scale Offset</span></span>

<span data-ttu-id="8c880-362">Scale Offset 动画处理属性采用对象的当前小数位数，并添加定义的偏移量。</span><span class="sxs-lookup"><span data-stu-id="8c880-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![与虚拟手交互的缩放偏移](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="8c880-364">位置偏移量</span><span class="sxs-lookup"><span data-stu-id="8c880-364">Position Offset</span></span>

<span data-ttu-id="8c880-365">Position Offset 动画处理属性采用对象的当前位置，并添加定义的偏移量。</span><span class="sxs-lookup"><span data-stu-id="8c880-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![与虚拟手交互的位置偏移量](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="8c880-367">Color</span><span class="sxs-lookup"><span data-stu-id="8c880-367">Color</span></span>

<span data-ttu-id="8c880-368">如果材料具有主颜色属性，则 Color Animatable 属性表示材料的主颜色。</span><span class="sxs-lookup"><span data-stu-id="8c880-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="8c880-369">此属性对 属性进行 `material._Color` 动画处理。</span><span class="sxs-lookup"><span data-stu-id="8c880-369">This property animates the `material._Color` property.</span></span>

![通过虚拟手部交互更改焦点颜色](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="8c880-371">着色器颜色</span><span class="sxs-lookup"><span data-stu-id="8c880-371">Shader Color</span></span>

<span data-ttu-id="8c880-372">着色器颜色 Animatable 属性是指颜色类型的着色器属性。</span><span class="sxs-lookup"><span data-stu-id="8c880-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="8c880-373">所有着色器属性都需要属性名称。</span><span class="sxs-lookup"><span data-stu-id="8c880-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="8c880-374">下面的 gif 演示了对名为 Fill_Color颜色属性进行动画处理，该属性不是主要材料颜色。</span><span class="sxs-lookup"><span data-stu-id="8c880-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="8c880-375">观察材料检查器中的更改值。</span><span class="sxs-lookup"><span data-stu-id="8c880-375">Observe the changing values in the material inspector.</span></span>

![使用虚拟手部交互的着色颜色](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="8c880-377">着色器 Float</span><span class="sxs-lookup"><span data-stu-id="8c880-377">Shader Float</span></span>

<span data-ttu-id="8c880-378">着色器 Float Animatable 属性引用 float 类型的着色器属性。</span><span class="sxs-lookup"><span data-stu-id="8c880-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="8c880-379">所有着色器属性都需要属性名称。</span><span class="sxs-lookup"><span data-stu-id="8c880-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="8c880-380">在下面的 gif 中，观察"金属"属性的材料检查器中不断变化的值。</span><span class="sxs-lookup"><span data-stu-id="8c880-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![具有虚拟手部交互的着色器浮动](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="8c880-382">着色器向量</span><span class="sxs-lookup"><span data-stu-id="8c880-382">Shader Vector</span></span>

<span data-ttu-id="8c880-383">着色器矢量 Animatable 属性引用 Vector4 类型的着色器属性。</span><span class="sxs-lookup"><span data-stu-id="8c880-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="8c880-384">所有着色器属性都需要属性名称。</span><span class="sxs-lookup"><span data-stu-id="8c880-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="8c880-385">在下面的 gif 中，观察"主图"属性的平铺 (检查器Tex_ST) 值。</span><span class="sxs-lookup"><span data-stu-id="8c880-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![具有虚拟手部交互的着色器向量](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="8c880-387">如何查找可着色器属性名称</span><span class="sxs-lookup"><span data-stu-id="8c880-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="8c880-388">导航到窗口 > 动画 > 动画</span><span class="sxs-lookup"><span data-stu-id="8c880-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="8c880-389">确保在层次结构中选择了具有状态可视化工具的对象</span><span class="sxs-lookup"><span data-stu-id="8c880-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="8c880-390">在动画窗口中选择任何动画剪辑</span><span class="sxs-lookup"><span data-stu-id="8c880-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="8c880-391">选择 " **添加属性**"，打开网格呈现器 foldout</span><span class="sxs-lookup"><span data-stu-id="8c880-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![在 Animator 窗口中添加动画属性](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="8c880-393">此列表包含所有动画处理属性名称的名称</span><span class="sxs-lookup"><span data-stu-id="8c880-393">This list contains the names of all the Animatable property names</span></span> 

    ![Animator 窗口中的网格呈现器动画属性](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="8c880-395">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c880-395">See also</span></span>

- [<span data-ttu-id="8c880-396">**按钮**</span><span class="sxs-lookup"><span data-stu-id="8c880-396">**Buttons**</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="8c880-397">**边界控制**</span><span class="sxs-lookup"><span data-stu-id="8c880-397">**Bounds Control**</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="8c880-398">**网格对象集合**</span><span class="sxs-lookup"><span data-stu-id="8c880-398">**Grid Object Collection**</span></span>](../ux-building-blocks/object-collection.md)
- [<span data-ttu-id="8c880-399">**RadialView 求解器**</span><span class="sxs-lookup"><span data-stu-id="8c880-399">**RadialView Solver**</span></span>](../ux-building-blocks/solvers/solver.md)
