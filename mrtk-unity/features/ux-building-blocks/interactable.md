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
# <a name="interactable"></a><span data-ttu-id="d1e6c-104">可交互</span><span class="sxs-lookup"><span data-stu-id="d1e6c-104">Interactable</span></span>

![可交互](../images/interactable/InteractableExamples.png)

<span data-ttu-id="d1e6c-106">组件是一个一体式 [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 容器，使任何对象都可以轻松地 *种不可交互* 输入并做出响应。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="d1e6c-107">种不可交互充当所有类型的输入（包括触摸、手写光线、语音等）的全部捕获，并将这些交互转换为 [事件](#events) 和 [视觉主题](visual-themes.md) 响应。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](visual-themes.md) responses.</span></span> <span data-ttu-id="d1e6c-108">此组件提供一种简单的方法来生成按钮、更改具有焦点的对象上的颜色等。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="d1e6c-109">如何配置种不可交互</span><span class="sxs-lookup"><span data-stu-id="d1e6c-109">How to configure Interactable</span></span>

<span data-ttu-id="d1e6c-110">组件允许配置的三个主要部分：</span><span class="sxs-lookup"><span data-stu-id="d1e6c-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="d1e6c-111">常规输入配置</span><span class="sxs-lookup"><span data-stu-id="d1e6c-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="d1e6c-112">面向多个 Gameobject 的[视觉主题](visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="d1e6c-112">[Visual Themes](visual-themes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="d1e6c-113">事件处理程序</span><span class="sxs-lookup"><span data-stu-id="d1e6c-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="d1e6c-114">一般输入设置</span><span class="sxs-lookup"><span data-stu-id="d1e6c-114">General input settings</span></span>

![常规种不可交互设置](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="d1e6c-116">**状态**</span><span class="sxs-lookup"><span data-stu-id="d1e6c-116">**States**</span></span>

<span data-ttu-id="d1e6c-117">*状态* 是 [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 参数，用于定义 [种不可交互配置文件](#interactable-profiles) 和 [视觉主题](visual-themes.md)的交互阶段，如按下或观察。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](visual-themes.md).</span></span>

<span data-ttu-id="d1e6c-118">**DefaultInteractableStates** (资产/MRTK/SDK/FEATURES/UX/种不可交互/州/DefaultInteractableStates) 随内置了 MRTK，是 *种不可交互* 组件的默认参数。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![检查检查器中的 ScriptableObject 示例](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="d1e6c-120">*DefaultInteractableStates* 资产包含四种状态，并利用 [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) 状态模型实现。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="d1e6c-121">**默认**：不会发生任何情况，这是最隔离的基本状态。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="d1e6c-122">**焦点**：对象指向。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="d1e6c-123">这是一种状态，当前未设置任何其他状态，但它的默认值为默认值。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="d1e6c-124">**按下**：对象将指向，按钮或手按下。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="d1e6c-125">按下状态的默认值和焦点。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="d1e6c-126">此状态也将设置为 "物理按下"。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="d1e6c-127">**已禁用**：该按钮不应为交互式，并且视觉反馈会让用户知道此按钮目前不可用的原因。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="d1e6c-128">理论上，禁用状态可能包含所有其他状态，但启用后关闭时，禁用状态胜过所有其他状态。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="d1e6c-129">根据列表中的顺序，会将位值 ( # ) 分配给状态。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="d1e6c-130">通常建议在创建 *种不可交互* 组件时，使用 **DefaultInteractableStates** (资产/MRTK/SDK/功能/UX/种不可交互/州/DefaultInteractableStates）) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="d1e6c-131">不过，有17个可用来驱动主题的种不可交互状态，但某些状态应由其他组件驱动。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="d1e6c-132">下面是包含内置功能的列表。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="d1e6c-133">已访问：已单击种不可交互。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="d1e6c-134">切换：按钮处于切换状态，或者维度索引为奇数。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="d1e6c-135">手势：手型或控制器已按下，并已从原始位置移动。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="d1e6c-136">VoiceCommand：使用语音命令触发了种不可交互。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="d1e6c-137">PhysicalTouch：当前检测到触摸输入，请使用 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 启用。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="d1e6c-138">抓住：手头当前在对象的边界内抓取， [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 并使用启用</span><span class="sxs-lookup"><span data-stu-id="d1e6c-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="d1e6c-139">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="d1e6c-139">**Enabled**</span></span>

<span data-ttu-id="d1e6c-140">切换种不可交互是否开始启用。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="d1e6c-141">这对应于 [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 代码中的。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="d1e6c-142">*种不可交互的* enabled 属性不同于通过 GameObject/Component 配置的 enabled 属性 (即</span><span class="sxs-lookup"><span data-stu-id="d1e6c-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="d1e6c-143">SetActive 等) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-143">SetActive etc).</span></span> <span data-ttu-id="d1e6c-144">禁用 GameObject 或 *种不可交互* MonoBehaviour 将禁止运行类中的所有内容，包括输入、视觉主题、事件等。禁用 via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) 将禁用大多数输入处理，并重置相关输入状态。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="d1e6c-145">但是，类仍将运行每个帧并接收输入事件，这些事件将被忽略。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="d1e6c-146">这对于在禁用状态下显示种不可交互非常有用，可以通过视觉主题来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="d1e6c-147">这种情况的一个典型示例是 "提交" 按钮，等待所有必需的输入字段完成。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="d1e6c-148">**输入操作**</span><span class="sxs-lookup"><span data-stu-id="d1e6c-148">**Input Actions**</span></span>

<span data-ttu-id="d1e6c-149">从 *种不可交互* 组件应响应的输入配置或控制器映射配置文件中选择 [输入操作](../input/input-actions.md)。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-149">Select the [input action](../input/input-actions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="d1e6c-150">此属性可在运行时通过代码进行配置 [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="d1e6c-151">**IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="d1e6c-151">**IsGlobal**</span></span>

<span data-ttu-id="d1e6c-152">如果为 true，则会将组件标记为选定 [输入操作](../input/input-actions.md)的全局输入侦听器。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-152">If true, this will mark the component as a global input listener for the selected [input action](../input/input-actions.md).</span></span> <span data-ttu-id="d1e6c-153">默认行为是 false，它会将输入限制为仅限此 *种不可交互* 碰撞器/GameObject。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="d1e6c-154">此属性可在运行时通过代码进行配置 [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="d1e6c-155">**语音命令**</span><span class="sxs-lookup"><span data-stu-id="d1e6c-155">**Speech Command**</span></span>

<span data-ttu-id="d1e6c-156">MRTK 语音命令配置文件中的[语音命令](../input/speech.md)，触发用于语音交互的 OnClick 事件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-156">[Speech command](../input/speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="d1e6c-157">此属性可在运行时通过代码进行配置 [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="d1e6c-158">**需要焦点**</span><span class="sxs-lookup"><span data-stu-id="d1e6c-158">**Requires Focus**</span></span>

<span data-ttu-id="d1e6c-159">如果为 true，则当且仅当它已具有指针的焦点时，语音命令才会激活 *种不可交互* 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="d1e6c-160">如果为 false，则 *种不可交互* 将充当所选语音命令的全局侦听器。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="d1e6c-161">默认行为是 "true"，因为多个全局语音侦听器可能很难在场景中进行组织。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="d1e6c-162">此属性可在运行时通过代码进行配置 [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="d1e6c-163">**选择模式**</span><span class="sxs-lookup"><span data-stu-id="d1e6c-163">**Selection Mode**</span></span>

<span data-ttu-id="d1e6c-164">此属性定义选择逻辑。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-164">This property defines the selection logic.</span></span> <span data-ttu-id="d1e6c-165">当单击 *种不可交互* 时，它将循环访问下一个 *维度* 级别。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="d1e6c-166">*维度* 类似于排名，并定义输入以外的状态 (例如</span><span class="sxs-lookup"><span data-stu-id="d1e6c-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="d1e6c-167">重点，按 etc) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-167">focus, press etc).</span></span> <span data-ttu-id="d1e6c-168">它们有助于定义切换状态或与按钮关联的其他多排名状态。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="d1e6c-169">跟踪当前维度级别 `Interactable.DimensionIndex` 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="d1e6c-170">可用的选择模式包括：</span><span class="sxs-lookup"><span data-stu-id="d1e6c-170">The selection modes available are:</span></span>

* <span data-ttu-id="d1e6c-171">**按钮**  - *维数*= 1，简单的可单击 *种不可交互*</span><span class="sxs-lookup"><span data-stu-id="d1e6c-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="d1e6c-172">**切换**  - *维数*= 2，*种不可交互\*\*在* / *off* 状态之间交替</span><span class="sxs-lookup"><span data-stu-id="d1e6c-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="d1e6c-173">**多维度**  - *维度*>= 3，则每次单击都会增加当前的维度级别 + 1。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="d1e6c-174">适用于将按钮状态定义到列表等。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="d1e6c-175">*种不可交互* 还允许为每个 *维度* 定义多个主题。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="d1e6c-176">例如，当 *SelectionMode = 切换* 时，当 *取消选择\*\*种不可交互* 时，可能会应用一个主题，并在 *选择* 组件时应用另一个主题。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="d1e6c-177">当前选择模式可在运行时通过进行查询 [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="d1e6c-178">可以通过将  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) 属性设置为与所需的功能，来在运行时更新模式。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="d1e6c-179">此外，可以通过访问当前维度（用于 *切换* 和 *多维度* 模式） [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="d1e6c-180">种不可交互配置文件</span><span class="sxs-lookup"><span data-stu-id="d1e6c-180">Interactable profiles</span></span>

<span data-ttu-id="d1e6c-181">*配置文件* 是在 GameObject 和 [视觉主题](visual-themes.md)之间创建关系的项。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](visual-themes.md).</span></span> <span data-ttu-id="d1e6c-182">配置文件定义当 [发生状态更改](#general-input-settings)时，主题将操作哪些内容。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="d1e6c-183">主题工作非常类似于材料。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-183">Themes work a lot like materials.</span></span> <span data-ttu-id="d1e6c-184">它们是可编写脚本的对象，这些对象包含将根据当前状态分配给对象的属性列表。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="d1e6c-185">主题也可重复使用，并且可以跨多个 *种不可交互* UX 对象进行分配。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="d1e6c-186">**销毁时重置**</span><span class="sxs-lookup"><span data-stu-id="d1e6c-186">**Reset On Destroy**</span></span>

<span data-ttu-id="d1e6c-187">Visual themes 修改目标 GameObject 上的各种属性，具体取决于所选的主题引擎的类和类型。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="d1e6c-188">如果在销毁种不可交互组件时 *重置时重置* 为 true，则组件会将活动主题中所有已修改的属性重置为其原始值。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="d1e6c-189">否则，在销毁后，种不可交互组件会按原样保留所有修改的属性。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="d1e6c-190">在后一种情况下，除非由另一个外部组件更改，否则值的最后一个状态将保持不变。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="d1e6c-191">默认值为 false。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a><span data-ttu-id="d1e6c-192">事件</span><span class="sxs-lookup"><span data-stu-id="d1e6c-192">Events</span></span>

<span data-ttu-id="d1e6c-193">每个 *种不可交互* 组件都有一个 *OnClick* 事件，该事件在组件简单地处于选中状态时触发。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="d1e6c-194">但是， *种不可交互* 可用于检测除 *OnClick* 以外的输入事件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="d1e6c-195">单击 " *添加事件* " 按钮，添加新类型的事件接收器定义。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="d1e6c-196">添加后，选择所需的事件类型。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-196">Once added, select the type of Event desired.</span></span>

![事件示例](../images/interactable/Events.png)<span data-ttu-id="d1e6c-198">)</span><span class="sxs-lookup"><span data-stu-id="d1e6c-198">)</span></span>

<span data-ttu-id="d1e6c-199">事件接收器有不同类型，可对不同类型的输入进行响应。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="d1e6c-200">MRTK 附带了以下一组接收方。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="d1e6c-201">可以通过创建一个扩展的新类来创建自定义接收器 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![事件切换接收方示例](../images/interactable/Event_toggle.png)

<span data-ttu-id="d1e6c-203">*切换事件接收器的示例*</span><span class="sxs-lookup"><span data-stu-id="d1e6c-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="d1e6c-204">种不可交互接收方</span><span class="sxs-lookup"><span data-stu-id="d1e6c-204">Interactable receivers</span></span>

 <span data-ttu-id="d1e6c-205">[`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver)组件允许在源 *种不可交互* 组件外部定义事件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="d1e6c-206">*InteractableReceiver* 将侦听其他 *种不可交互* 激发的筛选事件类型。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="d1e6c-207">如果未直接分配 *种不可交互* 属性，则 " *搜索范围* " 属性将定义 *InteractableReceiver* 侦听事件的方向，该方向是在其自身、父或子 GameObject 中。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="d1e6c-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) 以类似方式进行操作，但对于匹配事件的列表。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a><span data-ttu-id="d1e6c-209">创建自定义事件</span><span class="sxs-lookup"><span data-stu-id="d1e6c-209">Create custom events</span></span>

<span data-ttu-id="d1e6c-210">与 [视觉主题](visual-themes.md#custom-theme-engines)一样，可以扩展事件以检测任何状态模式或公开功能。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-210">Like [Visual Themes](visual-themes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="d1e6c-211">可以通过两种主要方式创建自定义事件：</span><span class="sxs-lookup"><span data-stu-id="d1e6c-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="d1e6c-212">扩展 [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 类以创建将在事件类型的下拉列表中显示的自定义事件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="d1e6c-213">默认情况下，将提供 Unity 事件，但可以添加其他 Unity 事件，或者可以将事件设置为隐藏 Unity 事件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="d1e6c-214">此功能允许设计器与项目上的工程一起使用，以创建设计器可在编辑器中设置的自定义事件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="d1e6c-215">扩展 [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) 类，以创建可以驻留在 *种不可交互* 或其他对象上的完全自定义事件组件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="d1e6c-216">[`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)将引用 *种不可交互* 以检测状态更改。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="d1e6c-217">扩展示例 `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="d1e6c-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="d1e6c-218">[`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI)类显示有关 *种不可交互* 的状态信息，并举例说明如何创建自定义事件接收器。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="d1e6c-219">以下方法可用于在创建自定义事件接收器时重写/实现。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="d1e6c-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 是一个抽象方法，可用于检测状态模式/转换。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="d1e6c-221">此外，在 [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) 选择 *种不可交互* 时，和方法可用于创建自定义事件逻辑。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

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

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="d1e6c-222">在检查器中显示自定义事件接收器字段</span><span class="sxs-lookup"><span data-stu-id="d1e6c-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="d1e6c-223">*ReceiverBase* 脚本使用 [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) 特性来公开检查器中的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="d1e6c-224">下面是一个 System.numerics.vector2 示例，它是包含工具提示和标签信息的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="d1e6c-225">选择 *种不可交互* GameObject 并添加关联的 *事件接收器* 类型时，此属性将在检查器中显示为可配置。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="d1e6c-226">如何使用种不可交互</span><span class="sxs-lookup"><span data-stu-id="d1e6c-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="d1e6c-227">构建简单的按钮</span><span class="sxs-lookup"><span data-stu-id="d1e6c-227">Building a simple button</span></span>

<span data-ttu-id="d1e6c-228">可以通过将 *种不可交互* 组件添加到配置为接收输入事件的 GameObject，创建一个简单的按钮。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="d1e6c-229">它可以在它上面或子上有一个碰撞器来接收输入。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="d1e6c-230">如果将 *种不可交互* 用于基于 Unity UI 的 gameobject，则它应位于画布 GameObject 下。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="d1e6c-231">通过创建新的配置文件，分配 GameObject 本身并创建新的主题，使按钮进一步操作。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="d1e6c-232">此外，使用 *OnClick* 事件可以进行一些操作。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="d1e6c-233">使 [按钮 pressable](button.md) 需要 [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 组件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-233">Making a [button pressable](button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="d1e6c-234">此外，还 [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) 需要组件将事件按漏斗到 *种不可交互* 组件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="d1e6c-235">创建切换和多维度按钮</span><span class="sxs-lookup"><span data-stu-id="d1e6c-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="d1e6c-236">切换按钮</span><span class="sxs-lookup"><span data-stu-id="d1e6c-236">Toggle button</span></span>

<span data-ttu-id="d1e6c-237">若要使按钮切换，请将字段更改 [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 为 "类型" `Toggle` 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-237">To make a button Toggle-able, change the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="d1e6c-238">在 " *配置文件* " 部分中，将为 *种不可交互* 切换时使用的每个配置文件添加一个新的切换主题。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="d1e6c-239">当 [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) 设置为切换时， *IsToggled* 复选框可用于在运行时初始化时设置控件的默认值。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="d1e6c-240">*CanSelect* 表示 *种不可交互* 可以从 *off* 切换到 *on* ，而 *CanDeselect* 表示反转。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![配置文件切换视觉对象示例](../images/interactable/Profile_toggle.png)

<span data-ttu-id="d1e6c-242">开发人员可以利用 [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 和 [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 接口通过代码获取/设置 *种不可交互* 的切换状态。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="d1e6c-243">切换按钮集合</span><span class="sxs-lookup"><span data-stu-id="d1e6c-243">Toggle button collection</span></span>

<span data-ttu-id="d1e6c-244">通常，有一个切换按钮列表，在任何给定时间（也称为径向集或单选按钮等），只有一个按钮可以处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="d1e6c-245">使用 [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) 组件启用此功能。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="d1e6c-246">此控制确保在任何给定时间，只切换一 *种不可交互* 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="d1e6c-247">*RadialSet* (资产/MRTK/SDK/FEATURES/UX/种不可交互/Prototyping/RadialSet) 也是一种现成的良好起点。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="d1e6c-248">若要创建自定义的径向按钮组：</span><span class="sxs-lookup"><span data-stu-id="d1e6c-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="d1e6c-249">创建多个 *种不可交互* gameobject/按钮</span><span class="sxs-lookup"><span data-stu-id="d1e6c-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="d1e6c-250">将每个 *种不可交互* 设置为 *SelectionMode* = 切换， *CanSelect* = true，并将 *CanDeselect* = false</span><span class="sxs-lookup"><span data-stu-id="d1e6c-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="d1e6c-251">在所有 *Interactables* 上创建一个空的父 GameObject，并添加 *InteractableToggleCollection* 组件</span><span class="sxs-lookup"><span data-stu-id="d1e6c-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="d1e6c-252">将所有 *Interactables* 添加到 *InteractableToggleCollection* 上的 *ToggleList*</span><span class="sxs-lookup"><span data-stu-id="d1e6c-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="d1e6c-253">设置 *InteractableToggleCollection CurrentIndex* 属性，以确定默认情况下在开始时选择哪个按钮</span><span class="sxs-lookup"><span data-stu-id="d1e6c-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="d1e6c-254">多维按钮</span><span class="sxs-lookup"><span data-stu-id="d1e6c-254">Multi-dimensional button</span></span>

<span data-ttu-id="d1e6c-255">多维度选择模式用于创建顺序按钮，或具有两个以上步骤的按钮，如使用三个值控制速度、Fast (1x) 、速度 (2 到3或更快 (3) 倍) 。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="d1e6c-256">如果维度为数值，则可以添加最多9个主题来控制每个速度设置的按钮的文本标签或纹理，并为每个步骤使用不同的主题。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="d1e6c-257">每次单击事件都将 `DimensionIndex` 在运行时前进1，直到 `Dimensions` 达到值。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="d1e6c-258">然后，循环将重置为0。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-258">Then the cycle will reset to 0.</span></span>

![多维配置文件示例](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="d1e6c-260">开发人员可以评估 [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 以确定当前处于活动状态的维度。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="d1e6c-261">在运行时创建种不可交互</span><span class="sxs-lookup"><span data-stu-id="d1e6c-261">Create Interactable at runtime</span></span>

<span data-ttu-id="d1e6c-262">在运行时，可以轻松地将 *种不可交互* 添加到任何 GameObject。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="d1e6c-263">下面的示例演示如何使用 [视觉对象主题](visual-themes.md)来分配配置文件。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-263">The following example demonstrates how to assign a profile with a [visual theme](visual-themes.md).</span></span>

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

### <a name="interactable-events-via-code"></a><span data-ttu-id="d1e6c-264">通过代码种不可交互事件</span><span class="sxs-lookup"><span data-stu-id="d1e6c-264">Interactable events via code</span></span>

<span data-ttu-id="d1e6c-265">可以通过代码将操作添加到基 [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) 事件，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="d1e6c-266">使用 [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 函数在运行时动态添加事件接收器。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="d1e6c-267">下面的示例代码演示了如何添加 [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，它侦听焦点/退出，并定义在事件实例激发时要执行的操作代码。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="d1e6c-268">下面的示例代码演示了如何添加 [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)，它侦听对切换 *Interactables* 的选定/取消选择状态转换，并定义在事件实例激发时要执行的操作代码。</span><span class="sxs-lookup"><span data-stu-id="d1e6c-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d1e6c-269">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1e6c-269">See also</span></span>

* [<span data-ttu-id="d1e6c-270">视觉主题</span><span class="sxs-lookup"><span data-stu-id="d1e6c-270">Visual Themes</span></span>](visual-themes.md)
* [<span data-ttu-id="d1e6c-271">输入操作</span><span class="sxs-lookup"><span data-stu-id="d1e6c-271">Input Actions</span></span>](../input/input-actions.md)
* [<span data-ttu-id="d1e6c-272">语音命令</span><span class="sxs-lookup"><span data-stu-id="d1e6c-272">Speech Commands</span></span>](../input/speech.md)
* [<span data-ttu-id="d1e6c-273">按钮</span><span class="sxs-lookup"><span data-stu-id="d1e6c-273">Buttons</span></span>](button.md)
* [<span data-ttu-id="d1e6c-274">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="d1e6c-274">MRTK Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
