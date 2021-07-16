---
title: 创建输入系统数据提供程序
description: 用于在 MRTK 中创建输入系统和数据提供程序的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 0b6012871a4d4988fdb70336a3c33455f479bcac
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281925"
---
# <a name="creating-an-input-system-data-provider"></a>创建输入系统数据提供程序

混合现实 Toolkit 输入系统是一种可扩展的系统，用于启用输入设备支持。 若要添加对新硬件平台的支持，可能需要自定义输入数据提供程序。

本文介绍如何为输入系统创建自定义数据访问接口（也称为设备管理器）。 此处所示的示例代码来自 [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) 。

> 在此示例中使用的完整代码可在 MRTK/Providers/WindowsMixedReality 文件夹中找到。

## <a name="namespace-and-folder-structure"></a>命名空间和文件夹结构

数据访问接口可以作为第三方加载项分发，也可以作为 Microsoft Mixed Reality Toolkit 的一部分分发。 向 MRTK 提交新数据提供程序的批准过程将根据具体情况发生变化，并将在初始提议时进行传达。

> [!Important]
> 如果将输入系统数据提供程序提交到 [混合现实 Toolkit 存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，则命名空间 **必须** 以 MixedReality 开头。Toolkit (例如： MixedReality。Toolkit。WindowsMixedReality) ，代码应位于 MRTK/Providers 下的文件夹中 (例如： MRTK/Providers/WindowsMixedReality) 。

### <a name="namespace"></a>命名空间

数据访问接口需要有一个命名空间来缓解潜在的名称冲突。 建议命名空间包括以下组件。

- 公司名称
- 功能区域

例如，Contoso 公司创建的输入数据提供程序可能是 "MixedReality"。Toolkit。输入 "。

### <a name="recommended-folder-structure"></a>推荐的文件夹结构

建议在文件夹层次结构中排列数据提供程序的源代码，如下图所示。

![文件夹结构示例](../images/input/ExampleProviderFolderStructure.png)

其中，ContosoInput 包含数据提供程序的实现，Editor 文件夹包含检查器 (和任何其他 Unity 编辑器特定代码) ，纹理文件夹包含受支持控制器的图像，而配置文件包含一个或多个预配置文件。

> [!Note]
> 可以在 MixedRealityToolkit\StandardAssets\Textures 文件夹中找到一些公共控制器映像。

## <a name="implement-the-data-provider"></a>实现数据访问接口

### <a name="specify-interface-andor-base-class-inheritance"></a>指定接口和/或基类继承

所有输入系统数据提供程序必须实现 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 接口，该接口指定输入系统所需的最小功能。 MRTK foundation 包含 [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 类，该类提供此所需功能的默认实现。 对于基于 Unity 的 UInput 类构建的设备， [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) 可以将类用作基类。

> [!Note]
> `BaseInputDeviceManager`和 `UnityJoystickManager` 类提供所需的 `IMixedRealityInputDeviceManager` 实现。

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` 由用 `WindowsMixedRealityDeviceManager` 来指示它为一组输入功能提供支持，具体而言，就是明确的手势，注视着声音和运动控制器。

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>应用 MixedRealityDataProvider 特性

创建输入系统数据提供程序的一个关键步骤是将属性应用于 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 类。 此步骤允许在输入系统配置文件中选择提供程序时，设置该提供程序的默认配置文件和平台 () 。

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>实现 IMixedRealityDataProvider 方法

一旦定义了类，下一步就是提供接口的实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。

> [!Note]
> `BaseInputDeviceManager`类通过 `BaseService` 类只为方法提供空实现 `IMixedRealityDataProvider` 。 这些方法的详细信息通常是特定于数据访问接口的。

应由数据提供程序实现的方法如下：

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>实现数据访问接口逻辑

下一步是添加用于管理输入设备的逻辑，包括要支持的任何控制器。

### <a name="implement-the-controller-classes"></a>实现控制器类

 的示例 `WindowsMixedRealityDeviceManager` 定义并实现了以下控制器类。

> 每个这些类的源代码可在 MRTK/Providers/WindowsMixedReality 文件夹中找到。

- WindowsMixedRealityArticulatedHand
- WindowsMixedRealityController
- WindowsMixedRealityGGVHand

> [!Note]
> 并非所有设备管理器都支持多种控制器类型。

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>应用 MixedRealityController 特性

接下来，将 [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) 属性应用于类。 此属性指定控制器的类型 (例如：已表述的手势) ，左右手使用习惯 (例如：左或右) 和可选控制器图像。

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>配置交互映射

下一步是定义控制器支持的交互映射集。 对于通过 Unity 的输入类接收其数据的设备， [控制器映射工具](../tools/controller-mapping-tool.md) 是一个有用的资源，用于确认要分配到交互的正确轴和按钮映射。

下面的示例从类中缩写 `GenericOpenVRController` ，该类位于 MRTK/Providers/OpenVR 文件夹中。

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
>[`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary)类为 Unity 输入轴和按钮定义提供符号常数。

### <a name="raise-notification-events"></a>引发通知事件

为了使应用程序能够响应用户的输入，数据访问接口引发与和接口中定义的控制器状态更改对应的通知 [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) 事件 [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 。

对于 "数字 (" 按钮) 类型控件，引发 OnInputDown 和 OnInputUp 事件。

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

对于模拟控件 (例如：触摸板位置) 应引发 InputChanged 事件。

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>添加 Unity 探查器检测

性能在混合现实应用程序中非常重要。 每个组件都增加了应用程序必须考虑的一些开销。 为此，必须确保所有输入数据提供程序在内部循环和经常使用的代码路径中包含 Unity 探查器检测。

建议在检测自定义提供程序时实现 MRTK 使用的模式。

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> 用于标识探查器标记的名称是任意的。 MRTK 使用以下模式。
>
> "[product] className. 方法名称-可选注释"
>
> 建议自定义数据访问接口遵循类似的模式，以帮助在分析跟踪时简化特定组件和方法的标识。

## <a name="create-the-profile-and-inspector"></a>创建配置文件和检查器

在混合现实 Toolkit 中，使用[配置文件](../profiles/profiles.md)配置数据访问接口。

具有其他配置选项的数据提供程序 (ex： [InputSimulationService](../input-simulation/input-simulation-service.md)) 应创建配置文件和检查器，以允许客户修改行为，使其最适合应用程序的需求。

> 本部分中的示例的完整代码可在 MRTK 中找到。Services/InputSimulation 文件夹。

### <a name="define-the-profile"></a>定义配置文件

配置文件内容应反映观察程序的可访问属性， (例如：更新间隔) 。 每个接口中定义的所有用户可配置属性都应包含在配置文件中。

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

`CreateAssetMenu`特性可应用到配置文件类，使客户能够使用 **> Mixed Reality Toolkit > 配置文件**"菜单创建 > 资产创建配置文件实例。

### <a name="implement-the-inspector"></a>实现检查器

配置文件检查器是用于配置和查看配置文件内容的用户界面。 每个配置文件检查器应扩展 ["BaseMixedRealityToolkitConfigurationProfileInspector"](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 类。

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

`CustomEditor`属性向 Unity 通知该检查器应用到的资产类型。

## <a name="create-assembly-definitions"></a>创建 () 的程序集定义

混合现实 Toolkit 使用程序集定义 ([asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 文件指定组件之间的依赖关系，并协助 Unity 减少编译时间。

建议为所有数据访问接口及其编辑器组件创建程序集定义文件。

使用前面示例中的 [文件夹结构](#recommended-folder-structure) ，ContosoInput 数据提供程序有两个 asmdef 文件。

第一个程序集定义适用于数据访问接口。 在此示例中，它将被称为 ContosoInput，并将位于该示例的 ContosoInput 文件夹中。
此程序集定义必须指定对 MixedReality 的依赖关系。Toolkit 以及它所依赖的任何其他程序集。

ContosoInputEditor 程序集定义将指定配置文件检查器和任何特定于编辑器的代码。 此文件必须位于编辑器代码的根文件夹中。 在此示例中，该文件将位于 ContosoInput\Editor 文件夹中。 此程序集定义将包含对 ContosoInput 程序集的引用以及：

- MixedReality。Toolkit
- MixedReality。Toolkit。编辑器. 检查器
- MixedReality。Toolkit。编辑器。实用工具

## <a name="register-the-data-provider"></a>注册数据提供程序

创建后，数据访问接口可以注册到输入系统，并在应用程序中使用。

![注册的输入系统数据提供程序](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>打包和分发

作为第三方组件分发的数据提供程序具有与开发人员首选项一起打包和分发的特定详细信息。 最常见的解决方案可能是生成 .unitypackage，然后通过 Unity 资产存储进行分发。

如果提交数据提供程序并将其作为 Microsoft Mixed Reality Toolkit 包的一部分接受，Microsoft MRTK 团队将打包并分发它作为 MRTK 产品/服务一部分。

## <a name="see-also"></a>另请参阅

- [输入系统](overview.md)
- [`BaseInputDeviceManager` 类](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` 接口](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` 接口](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` 接口](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` 接口](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` 接口](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [控制器映射工具](../tools/controller-mapping-tool.md)
