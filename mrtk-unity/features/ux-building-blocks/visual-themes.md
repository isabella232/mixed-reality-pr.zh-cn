---
title: 视觉主题
description: 概述视觉主题在 MRTK 中灵活控制 UX 资产
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，MRTK 主题，
ms.openlocfilehash: d97c470bf1d77299c6848990cdc69d886d432ecb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177169"
---
# <a name="visual-themes"></a><span data-ttu-id="020ba-104">视觉主题</span><span class="sxs-lookup"><span data-stu-id="020ba-104">Visual themes</span></span>

<span data-ttu-id="020ba-105">主题允许灵活控制 UX 资产，以响应各种状态转换。</span><span class="sxs-lookup"><span data-stu-id="020ba-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="020ba-106">这可能涉及更改按钮颜色、调整元素大小以响应焦点等。Visual Themes framework 由两个关键部分组成： 1) 配置和 2) 运行时引擎。</span><span class="sxs-lookup"><span data-stu-id="020ba-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="020ba-107">[主题配置](#theme-configuration) 是属性和类型的定义，而 [主题引擎](#theme-engines) 是使用配置并实现逻辑以在运行时更新转换、材料等的类。</span><span class="sxs-lookup"><span data-stu-id="020ba-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="020ba-108">主题配置</span><span class="sxs-lookup"><span data-stu-id="020ba-108">Theme configuration</span></span>

<span data-ttu-id="020ba-109">主题配置是 [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) ，用于定义如何在运行时初始化主题引擎。</span><span class="sxs-lookup"><span data-stu-id="020ba-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="020ba-110">它们定义在应用运行时响应输入或其他状态更改时要使用的属性和值。</span><span class="sxs-lookup"><span data-stu-id="020ba-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="020ba-111">作为 [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 资产，只能定义一次主题配置，然后在不同的 UX 组件之间重复使用。</span><span class="sxs-lookup"><span data-stu-id="020ba-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="020ba-112">若要创建新 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 资产：</span><span class="sxs-lookup"><span data-stu-id="020ba-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="020ba-113">在 *Project 窗口* 中右键单击</span><span class="sxs-lookup"><span data-stu-id="020ba-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="020ba-114">选择 "**创建**  >  **混合现实 Toolkit**  >  **主题**</span><span class="sxs-lookup"><span data-stu-id="020ba-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="020ba-115">示例主题配置资产位于下 `MRTK/SDK/Features/UX/Interactable/Themes` 。</span><span class="sxs-lookup"><span data-stu-id="020ba-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Inspector 中的主题 ScriptableObject 示例](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="020ba-117">状态</span><span class="sxs-lookup"><span data-stu-id="020ba-117">States</span></span>

<span data-ttu-id="020ba-118">创建新的时 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ，要设置的第一件事是可用的状态。</span><span class="sxs-lookup"><span data-stu-id="020ba-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="020ba-119">State *属性指示* 主题配置需要定义多少个值，因为每个状态都有一个值。</span><span class="sxs-lookup"><span data-stu-id="020ba-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="020ba-120">在上面的示例图像中， [为种不可交互组件定义的默认状态为 "](interactable.md#general-input-settings) *默认*"、" *焦点*"、" *按下*" 和 " *已禁用*"。</span><span class="sxs-lookup"><span data-stu-id="020ba-120">In the example image above, the [default states defined for the Interactable](interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="020ba-121">这些定义在 `DefaultInteractableStates` (资产/MRTK/SDK/功能/UX/种不可交互/州) 资产文件中定义。</span><span class="sxs-lookup"><span data-stu-id="020ba-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="020ba-122">若要创建新 [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) 资产：</span><span class="sxs-lookup"><span data-stu-id="020ba-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="020ba-123">在 *Project 窗口* 中右键单击</span><span class="sxs-lookup"><span data-stu-id="020ba-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="020ba-124">选择 "**创建**  >  **混合现实 Toolkit**  >  **状态**</span><span class="sxs-lookup"><span data-stu-id="020ba-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![检查检查器中的 ScriptableObject 示例](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="020ba-126">[`State`](xref:Microsoft.MixedReality.Toolkit.UI.States)ScriptableObject 定义状态列表，以及要为这些状态创建的 *StateModel* 类型。</span><span class="sxs-lookup"><span data-stu-id="020ba-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="020ba-127">*StateModel* 是一个类，用于在 [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) 运行时扩展和实现状态机逻辑，以生成当前状态。</span><span class="sxs-lookup"><span data-stu-id="020ba-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="020ba-128">此类的当前状态通常由运行时的主题引擎用来指示要针对材料属性、GameObject 转换等设置哪些值。</span><span class="sxs-lookup"><span data-stu-id="020ba-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="020ba-129">主题引擎属性</span><span class="sxs-lookup"><span data-stu-id="020ba-129">Theme engine properties</span></span>

<span data-ttu-id="020ba-130">除了 *状态* 外， [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 资产还为这些引擎定义了一系列主题引擎和关联属性。</span><span class="sxs-lookup"><span data-stu-id="020ba-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="020ba-131">[主题引擎](#theme-engines)再次定义逻辑，以便在运行时针对 GameObject 设置正确的值。</span><span class="sxs-lookup"><span data-stu-id="020ba-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="020ba-132">[`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme)资产可以定义多个主题引擎，以实现针对多个 GameObject 属性的复杂视觉状态转换。</span><span class="sxs-lookup"><span data-stu-id="020ba-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="020ba-133">**主题运行时**</span><span class="sxs-lookup"><span data-stu-id="020ba-133">**Theme Runtime**</span></span>

<span data-ttu-id="020ba-134">定义将创建的主题引擎的类类型</span><span class="sxs-lookup"><span data-stu-id="020ba-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="020ba-135">**减轻**</span><span class="sxs-lookup"><span data-stu-id="020ba-135">**Easing**</span></span>

<span data-ttu-id="020ba-136">如果某些 *主题引擎* 将其属性 [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) 定义为 true，则支持各状态之间的缓动。</span><span class="sxs-lookup"><span data-stu-id="020ba-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="020ba-137">例如，当发生状态更改时，两种颜色之间的 lerping。</span><span class="sxs-lookup"><span data-stu-id="020ba-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="020ba-138">*持续时间* 定义从开始值到结束值的间隔时间，*动画曲线* 定义该时间段内的更改率（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="020ba-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="020ba-139">**着色器属性**</span><span class="sxs-lookup"><span data-stu-id="020ba-139">**Shader properties**</span></span>

<span data-ttu-id="020ba-140">如果某些 *主题引擎* 将其属性 [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) 定义为 true，则将在运行时修改特定的着色器属性。</span><span class="sxs-lookup"><span data-stu-id="020ba-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="020ba-141">*着色器* 和 *属性* 字段定义要面向的着色器属性。</span><span class="sxs-lookup"><span data-stu-id="020ba-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="020ba-142">通过代码创建主题配置</span><span class="sxs-lookup"><span data-stu-id="020ba-142">Create a theme configuration via code</span></span>

<span data-ttu-id="020ba-143">通常，通过 Unity 检查器设计主题配置更为简单，但在某些情况下，必须通过代码在运行时动态生成主题。</span><span class="sxs-lookup"><span data-stu-id="020ba-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="020ba-144">下面的代码片段提供了如何完成此任务的示例。</span><span class="sxs-lookup"><span data-stu-id="020ba-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="020ba-145">为了帮助加速开发，以下帮助器方法可用于简化安装。</span><span class="sxs-lookup"><span data-stu-id="020ba-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="020ba-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -使用 [种不可交互](interactable.md) 组件中使用的四个默认状态值创建新的状态 ScriptableObject。</span><span class="sxs-lookup"><span data-stu-id="020ba-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](interactable.md) component.</span></span>

<span data-ttu-id="020ba-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -每个主题引擎都定义具有该主题运行时类型所需的正确属性的默认配置。</span><span class="sxs-lookup"><span data-stu-id="020ba-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="020ba-148">此帮助程序为给定的主题引擎类型创建定义。</span><span class="sxs-lookup"><span data-stu-id="020ba-148">This helper creates a definition for the given Theme Engine type.</span></span>

```c#
// This code example builds a Theme ScriptableObject that can be used with an Interactable component.
// A random color is selected for the on pressed state every time this code is executed.

// Use the default states utilized in the Interactable component
var defaultStates = Interactable.GetDefaultInteractableStates();

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

// Create the Theme configuration asset
Theme testTheme = ScriptableObject.CreateInstance<Theme>();
testTheme.States = defaultStates;
testTheme.Definitions = new List<ThemeDefinition>() { newThemeType };
```

## <a name="theme-engines"></a><span data-ttu-id="020ba-149">主题引擎</span><span class="sxs-lookup"><span data-stu-id="020ba-149">Theme engines</span></span>

<span data-ttu-id="020ba-150">[主题引擎](#theme-engines)是从类扩展的类 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) 。</span><span class="sxs-lookup"><span data-stu-id="020ba-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="020ba-151">这些类在运行时进行实例化，并 [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) 按照前面所述的对象进行配置。</span><span class="sxs-lookup"><span data-stu-id="020ba-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="020ba-152">默认主题引擎</span><span class="sxs-lookup"><span data-stu-id="020ba-152">Default theme engines</span></span>

<span data-ttu-id="020ba-153">MRTK 附带了一组默认主题引擎，如下所示：</span><span class="sxs-lookup"><span data-stu-id="020ba-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

- [`InteractableActivateTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableActivateTheme)
- [`InteractableAnimatorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAnimatorTheme)
- [`InteractableAudioTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioTheme)
- [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
- [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
- [`InteractableGrabScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableGrabScaleTheme)
- [`InteractableMaterialTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableMaterialTheme)
- [`InteractableOffsetTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOffsetTheme)
- [`InteractableRotationTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableRotationTheme)
- [`InteractableScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableScaleTheme)
- [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme)
- [`InteractableStringTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStringTheme)
- [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
- [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

<span data-ttu-id="020ba-154">可以在下找到默认主题引擎 `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` 。</span><span class="sxs-lookup"><span data-stu-id="020ba-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="020ba-155">自定义主题引擎</span><span class="sxs-lookup"><span data-stu-id="020ba-155">Custom theme engines</span></span>

<span data-ttu-id="020ba-156">如前文所述，主题引擎定义为从类扩展的类 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) 。</span><span class="sxs-lookup"><span data-stu-id="020ba-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="020ba-157">因此，新的主题引擎只需扩展此类并实现以下内容：</span><span class="sxs-lookup"><span data-stu-id="020ba-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="020ba-158">强制实现</span><span class="sxs-lookup"><span data-stu-id="020ba-158">Mandatory implementations</span></span>

<span data-ttu-id="020ba-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (x： MixedReality。Toolkit。无.InteractableThemeBase) </span><span class="sxs-lookup"><span data-stu-id="020ba-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="020ba-160">对于可以通过标识的给定属性， `ThemeStateProperty.Name` 在目标 GameObject 主机上设置其当前状态值 (即</span><span class="sxs-lookup"><span data-stu-id="020ba-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="020ba-161">设置材料颜色等) 。</span><span class="sxs-lookup"><span data-stu-id="020ba-161">set the material color, etc).</span></span> <span data-ttu-id="020ba-162">此 *索引* 指示要访问的当前状态值，并使用介于0和 1 *之间的 float* 作为值之间的缓动/lerping。</span><span class="sxs-lookup"><span data-stu-id="020ba-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="020ba-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)` (x： MixedReality。Toolkit。无.InteractableThemeBase. GetProperty) </span><span class="sxs-lookup"><span data-stu-id="020ba-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="020ba-164">对于可以通过标识的给定属性， `ThemeStateProperty.Name` 返回在目标主机 GameObject 上设置的当前值 (即</span><span class="sxs-lookup"><span data-stu-id="020ba-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="020ba-165">当前的材料颜色、当前的本地位置偏移量等) 。</span><span class="sxs-lookup"><span data-stu-id="020ba-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="020ba-166">这主要用于缓存状态之间的缓动时的起始值。</span><span class="sxs-lookup"><span data-stu-id="020ba-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="020ba-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()` (x： MixedReality。Toolkit。无.InteractableThemeBase. GetDefaultThemeDefinition) </span><span class="sxs-lookup"><span data-stu-id="020ba-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="020ba-168">返回一个 [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) 对象，该对象定义自定义主题所需的默认属性和配置</span><span class="sxs-lookup"><span data-stu-id="020ba-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="020ba-169">公共定义的受保护变体 `SetValue()` ，除了提供的 ThemePropertyValue 以外，无需使用索引和/或百分比配置。</span><span class="sxs-lookup"><span data-stu-id="020ba-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="020ba-170">建议替代</span><span class="sxs-lookup"><span data-stu-id="020ba-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="020ba-171">在此处执行任何针对提供的 *GameObject* 参数的初始化步骤，并使用 *ThemeDefinition* 参数中定义的属性和配置。</span><span class="sxs-lookup"><span data-stu-id="020ba-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="020ba-172">建议 `base.Init(host, settings)` 在重写开始时调用。</span><span class="sxs-lookup"><span data-stu-id="020ba-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="020ba-173">如果自定义主题引擎可支持通过属性配置的值之间的缓动 [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) 。</span><span class="sxs-lookup"><span data-stu-id="020ba-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="020ba-174">如果自定义主题引擎可支持面向着色器属性，则为。</span><span class="sxs-lookup"><span data-stu-id="020ba-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="020ba-175">建议从现有的基础结构中进行扩展， [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 以便有效地通过 [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)设置/获取着色器属性。</span><span class="sxs-lookup"><span data-stu-id="020ba-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="020ba-176">着色器属性信息通过和存储在每个中 [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) 。</span><span class="sxs-lookup"><span data-stu-id="020ba-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="020ba-177">如果扩展 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) ，还可以通过 *New* 替代 [DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) ，这也很有用。</span><span class="sxs-lookup"><span data-stu-id="020ba-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="020ba-178">示例代码： `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="020ba-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="020ba-179">此外，下面的类扩展 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 类，该类再次使用 [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 修改着色器属性值。</span><span class="sxs-lookup"><span data-stu-id="020ba-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="020ba-180">此方法 [可帮助提高性能](https://docs.unity3d.com/Manual/DrawCallBatching.html) ，因为当值更改时， *MaterialPropertyBlocks* 不会创建新的实例材料。</span><span class="sxs-lookup"><span data-stu-id="020ba-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="020ba-181">但是，访问典型的 [材料](https://docs.unity3d.com/ScriptReference/Material.html) 类属性将不会返回预期值。</span><span class="sxs-lookup"><span data-stu-id="020ba-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="020ba-182">使用 *MaterialPropertyBlocks* 获取和验证当前材料属性值 (即</span><span class="sxs-lookup"><span data-stu-id="020ba-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="020ba-183">*_Color* 或 *_MainTex*) 。</span><span class="sxs-lookup"><span data-stu-id="020ba-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="020ba-184">指示主题将任何修改后的属性重置回其原始值（在此主题引擎初始化时，在主机 GameObject 上设置）。</span><span class="sxs-lookup"><span data-stu-id="020ba-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="020ba-185">自定义主题引擎示例</span><span class="sxs-lookup"><span data-stu-id="020ba-185">Custom theme engine example</span></span>

<span data-ttu-id="020ba-186">下面的类是一个自定义新主题引擎的示例。</span><span class="sxs-lookup"><span data-stu-id="020ba-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="020ba-187">此实现将查找已初始化主机对象上的 [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) 组件，并根据当前状态控制其可见性。</span><span class="sxs-lookup"><span data-stu-id="020ba-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

// This class demonstrates a custom theme to control a Host's MeshRenderer visibility
public class MeshVisibilityTheme : InteractableThemeBase
{
    // Bool visibility does not make sense for lerping
    public override bool IsEasingSupported => false;

    // No material or shaders are being modified
    public override bool AreShadersSupported => false;

    // Cache reference to the MeshRenderer component on our Host
    private MeshRenderer meshRenderer;

    public MeshVisibilityTheme()
    {
        Types = new Type[] { typeof(MeshRenderer) };
        Name = "Mesh Visibility Theme";
    }

    // Define a default configuration to simplify initialization of this theme engine
    // There is only one state property with a value per available state
    // This state property is a boolean that defines whether the renderer is enabled
    public override ThemeDefinition GetDefaultThemeDefinition()
    {
        return new ThemeDefinition()
        {
            ThemeType = GetType(),
            StateProperties = new List<ThemeStateProperty>()
            {
                new ThemeStateProperty()
                {
                    Name = "Mesh Visible",
                    Type = ThemePropertyTypes.Bool,
                    Values = new List<ThemePropertyValue>(),
                    Default = new ThemePropertyValue() { Bool = true }
                },
            },
            CustomProperties = new List<ThemeProperty>()
        };
    }

    // When initializing, cache a reference to the MeshRenderer component
    public override void Init(GameObject host, ThemeDefinition definition)
    {
        base.Init(host, definition);

        meshRenderer = host.GetComponent<MeshRenderer>();
    }

    // Get the current state of the MeshRenderer visibility
    public override ThemePropertyValue GetProperty(ThemeStateProperty property)
    {
        return new ThemePropertyValue()
        {
            Bool = meshRenderer.enabled
        };
    }

    // Update the MeshRenderer visibility based on the property state value data
    public override void SetValue(ThemeStateProperty property, int index, float percentage)
    {
        meshRenderer.enabled = property.Values[index].Bool;
    }
}
```

## <a name="end-to-end-example"></a><span data-ttu-id="020ba-188">端到端示例</span><span class="sxs-lookup"><span data-stu-id="020ba-188">End-to-end example</span></span>

<span data-ttu-id="020ba-189">下面的代码示例扩展了前面部分中定义的自定义主题引擎，下面的代码示例演示了如何在运行时控制此主题。</span><span class="sxs-lookup"><span data-stu-id="020ba-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="020ba-190">具体而言，如何设置主题的当前状态，以便正确更新 MeshRenderer 可见性。</span><span class="sxs-lookup"><span data-stu-id="020ba-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="020ba-191">`theme.OnUpdate(state,force)` 通常应在 Update () 方法中调用，以支持在值之间使用缓动/lerping 的主题引擎。</span><span class="sxs-lookup"><span data-stu-id="020ba-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

public class MeshVisibilityController : MonoBehaviour
{
    private MeshVisibilityTheme themeEngine;
    private bool hideMesh = false;

    private void Start()
    {
        // Define the default configuration. State 0 will be on while State 1 will be off
        var themeDefinition = ThemeDefinition.GetDefaultThemeDefinition<MeshVisibilityTheme>().Value;
        themeDefinition.StateProperties[0].Values = new List<ThemePropertyValue>()
        {
            new ThemePropertyValue() { Bool = true }, // show state
            new ThemePropertyValue() { Bool = false }, // hide state
        };

        // Create the actual Theme engine and initialize it with the GameObject we are attached to
        themeEngine = (MeshVisibilityTheme)InteractableThemeBase.CreateAndInitTheme(themeDefinition, this.gameObject);
    }

    private void Update()
    {
        // Update the theme engine to set our MeshRenderer visibility
        // based on our current state (i.e the hideMesh variable)
        themeEngine.OnUpdate(Convert.ToInt32(hideMesh));
    }

    public void ToggleVisibility()
    {
        // Alternate state of visibility
        hideMesh = !hideMesh;
    }
}
```

## <a name="see-also"></a><span data-ttu-id="020ba-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="020ba-192">See also</span></span>

- [<span data-ttu-id="020ba-193">可交互</span><span class="sxs-lookup"><span data-stu-id="020ba-193">Interactable</span></span>](interactable.md)
