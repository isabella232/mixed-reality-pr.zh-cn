---
title: 视觉主题
description: 概述视觉主题在 MRTK 中灵活控制 UX 资产
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，MRTK 主题，
ms.openlocfilehash: f7e0b10f51947884c4d23191fd147315084c5295e9b48953bb5de10b7cbc0d22
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223962"
---
# <a name="visual-themes"></a>视觉主题

主题允许灵活控制 UX 资产，以响应各种状态转换。 这可能涉及更改按钮颜色、调整元素大小以响应焦点等。Visual Themes framework 由两个关键部分组成： 1) 配置和 2) 运行时引擎。

[主题配置](#theme-configuration) 是属性和类型的定义，而 [主题引擎](#theme-engines) 是使用配置并实现逻辑以在运行时更新转换、材料等的类。

## <a name="theme-configuration"></a>主题配置

主题配置是 [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) ，用于定义如何在运行时初始化主题引擎。 它们定义在应用运行时响应输入或其他状态更改时要使用的属性和值。 作为 [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 资产，只能定义一次主题配置，然后在不同的 UX 组件之间重复使用。

若要创建新 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 资产：

1) 在 *Project 窗口* 中右键单击
1) 选择 "**创建**  >  **混合现实 Toolkit**  >  **主题**

示例主题配置资产位于下 `MRTK/SDK/Features/UX/Interactable/Themes` 。

![Inspector 中的主题 ScriptableObject 示例](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>状态

创建新的时 [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) ，要设置的第一件事是可用的状态。 State *属性指示* 主题配置需要定义多少个值，因为每个状态都有一个值。 在上面的示例图像中， [为种不可交互组件定义的默认状态为 "](interactable.md#general-input-settings) *默认*"、" *焦点*"、" *按下*" 和 " *已禁用*"。 这些定义在 `DefaultInteractableStates` (资产/MRTK/SDK/功能/UX/种不可交互/州) 资产文件中定义。

若要创建新 [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) 资产：

1) 在 *Project 窗口* 中右键单击
1) 选择 "**创建**  >  **混合现实 Toolkit**  >  **状态**

![检查检查器中的 ScriptableObject 示例](../images/interactable/DefaultInteractableStates.png)

[`State`](xref:Microsoft.MixedReality.Toolkit.UI.States)ScriptableObject 定义状态列表，以及要为这些状态创建的 *StateModel* 类型。 *StateModel* 是一个类，用于在 [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) 运行时扩展和实现状态机逻辑，以生成当前状态。 此类的当前状态通常由运行时的主题引擎用来指示要针对材料属性、GameObject 转换等设置哪些值。

### <a name="theme-engine-properties"></a>主题引擎属性

除了 *状态* 外， [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) 资产还为这些引擎定义了一系列主题引擎和关联属性。 [主题引擎](#theme-engines)再次定义逻辑，以便在运行时针对 GameObject 设置正确的值。

[`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme)资产可以定义多个主题引擎，以实现针对多个 GameObject 属性的复杂视觉状态转换。

**主题运行时**

定义将创建的主题引擎的类类型

**减轻**

如果某些 *主题引擎* 将其属性 [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) 定义为 true，则支持各状态之间的缓动。 例如，当发生状态更改时，两种颜色之间的 lerping。 *持续时间* 定义从开始值到结束值的间隔时间，*动画曲线* 定义该时间段内的更改率（以秒为单位）。

**着色器属性**

如果某些 *主题引擎* 将其属性 [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) 定义为 true，则将在运行时修改特定的着色器属性。 *着色器* 和 *属性* 字段定义要面向的着色器属性。

### <a name="create-a-theme-configuration-via-code"></a>通过代码创建主题配置

通常，通过 Unity 检查器设计主题配置更为简单，但在某些情况下，必须通过代码在运行时动态生成主题。 下面的代码片段提供了如何完成此任务的示例。

为了帮助加速开发，以下帮助器方法可用于简化安装。

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -使用 [种不可交互](interactable.md) 组件中使用的四个默认状态值创建新的状态 ScriptableObject。

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -每个主题引擎都定义具有该主题运行时类型所需的正确属性的默认配置。 此帮助程序为给定的主题引擎类型创建定义。

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

## <a name="theme-engines"></a>主题引擎

[主题引擎](#theme-engines)是从类扩展的类 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) 。 这些类在运行时进行实例化，并 [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) 按照前面所述的对象进行配置。

### <a name="default-theme-engines"></a>默认主题引擎

MRTK 附带了一组默认主题引擎，如下所示：

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

可以在下找到默认主题引擎 `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` 。

### <a name="custom-theme-engines"></a>自定义主题引擎

如前文所述，主题引擎定义为从类扩展的类 [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) 。 因此，新的主题引擎只需扩展此类并实现以下内容：

#### <a name="mandatory-implementations"></a>强制实现

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (x： MixedReality。Toolkit。无.InteractableThemeBase) 

对于可以通过标识的给定属性， `ThemeStateProperty.Name` 在目标 GameObject 主机上设置其当前状态值 (即 设置材料颜色等) 。 此 *索引* 指示要访问的当前状态值，并使用介于0和 1 *之间的 float* 作为值之间的缓动/lerping。

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)` (x： MixedReality。Toolkit。无.InteractableThemeBase. GetProperty) 

对于可以通过标识的给定属性， `ThemeStateProperty.Name` 返回在目标主机 GameObject 上设置的当前值 (即 当前的材料颜色、当前的本地位置偏移量等) 。 这主要用于缓存状态之间的缓动时的起始值。

`public abstract ThemeDefinition GetDefaultThemeDefinition()` (x： MixedReality。Toolkit。无.InteractableThemeBase. GetDefaultThemeDefinition) 

返回一个 [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) 对象，该对象定义自定义主题所需的默认属性和配置

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

公共定义的受保护变体 `SetValue()` ，除了提供的 ThemePropertyValue 以外，无需使用索引和/或百分比配置。

#### <a name="recommended-overrides"></a>建议替代

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

在此处执行任何针对提供的 *GameObject* 参数的初始化步骤，并使用 *ThemeDefinition* 参数中定义的属性和配置。 建议 `base.Init(host, settings)` 在重写开始时调用。

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

如果自定义主题引擎可支持通过属性配置的值之间的缓动 [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) 。

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

如果自定义主题引擎可支持面向着色器属性，则为。 建议从现有的基础结构中进行扩展， [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 以便有效地通过 [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)设置/获取着色器属性。 着色器属性信息通过和存储在每个中 [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) 。

> [!NOTE]
> 如果扩展 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) ，还可以通过 *New* 替代 [DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) ，这也很有用。
>
> 示例代码： `protected new const string DefaultShaderProperty = "_Color";`
>
> 此外，下面的类扩展 [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) 类，该类再次使用 [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) 修改着色器属性值。 此方法 [可帮助提高性能](https://docs.unity3d.com/Manual/DrawCallBatching.html) ，因为当值更改时， *MaterialPropertyBlocks* 不会创建新的实例材料。 但是，访问典型的 [材料](https://docs.unity3d.com/ScriptReference/Material.html) 类属性将不会返回预期值。 使用 *MaterialPropertyBlocks* 获取和验证当前材料属性值 (即 *_Color* 或 *_MainTex*) 。
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

指示主题将任何修改后的属性重置回其原始值（在此主题引擎初始化时，在主机 GameObject 上设置）。  

### <a name="custom-theme-engine-example"></a>自定义主题引擎示例

下面的类是一个自定义新主题引擎的示例。 此实现将查找已初始化主机对象上的 [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) 组件，并根据当前状态控制其可见性。

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

## <a name="end-to-end-example"></a>端到端示例

下面的代码示例扩展了前面部分中定义的自定义主题引擎，下面的代码示例演示了如何在运行时控制此主题。 具体而言，如何设置主题的当前状态，以便正确更新 MeshRenderer 可见性。

> [!NOTE]
> `theme.OnUpdate(state,force)` 通常应在 Update () 方法中调用，以支持在值之间使用缓动/lerping 的主题引擎。

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

## <a name="see-also"></a>另请参阅

- [可交互](interactable.md)
