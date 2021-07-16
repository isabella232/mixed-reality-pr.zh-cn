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
# <a name="creating-an-input-system-data-provider"></a><span data-ttu-id="bc988-104">创建输入系统数据提供程序</span><span class="sxs-lookup"><span data-stu-id="bc988-104">Creating an input system data provider</span></span>

<span data-ttu-id="bc988-105">混合现实 Toolkit 输入系统是一种可扩展的系统，用于启用输入设备支持。</span><span class="sxs-lookup"><span data-stu-id="bc988-105">The Mixed Reality Toolkit input system is an extensible system for enabling input device support.</span></span> <span data-ttu-id="bc988-106">若要添加对新硬件平台的支持，可能需要自定义输入数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="bc988-106">To add support for a new hardware platform, a custom input data provider may be required.</span></span>

<span data-ttu-id="bc988-107">本文介绍如何为输入系统创建自定义数据访问接口（也称为设备管理器）。</span><span class="sxs-lookup"><span data-stu-id="bc988-107">This article describes how to create custom data providers, also called device managers, for the input system.</span></span> <span data-ttu-id="bc988-108">此处所示的示例代码来自 [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) 。</span><span class="sxs-lookup"><span data-stu-id="bc988-108">The example code shown here is from the [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager).</span></span>

> <span data-ttu-id="bc988-109">在此示例中使用的完整代码可在 MRTK/Providers/WindowsMixedReality 文件夹中找到。</span><span class="sxs-lookup"><span data-stu-id="bc988-109">The complete code used in this example can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="bc988-110">命名空间和文件夹结构</span><span class="sxs-lookup"><span data-stu-id="bc988-110">Namespace and folder structure</span></span>

<span data-ttu-id="bc988-111">数据访问接口可以作为第三方加载项分发，也可以作为 Microsoft Mixed Reality Toolkit 的一部分分发。</span><span class="sxs-lookup"><span data-stu-id="bc988-111">Data providers can be distributed as a third party add-on or as a part of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="bc988-112">向 MRTK 提交新数据提供程序的批准过程将根据具体情况发生变化，并将在初始提议时进行传达。</span><span class="sxs-lookup"><span data-stu-id="bc988-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span>

> [!Important]
> <span data-ttu-id="bc988-113">如果将输入系统数据提供程序提交到 [混合现实 Toolkit 存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，则命名空间 **必须** 以 MixedReality 开头。Toolkit (例如： MixedReality。Toolkit。WindowsMixedReality) ，代码应位于 MRTK/Providers 下的文件夹中 (例如： MRTK/Providers/WindowsMixedReality) 。</span><span class="sxs-lookup"><span data-stu-id="bc988-113">If an input system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: Microsoft.MixedReality.Toolkit.WindowsMixedReality) and the code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/WindowsMixedReality).</span></span>

### <a name="namespace"></a><span data-ttu-id="bc988-114">命名空间</span><span class="sxs-lookup"><span data-stu-id="bc988-114">Namespace</span></span>

<span data-ttu-id="bc988-115">数据访问接口需要有一个命名空间来缓解潜在的名称冲突。</span><span class="sxs-lookup"><span data-stu-id="bc988-115">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="bc988-116">建议命名空间包括以下组件。</span><span class="sxs-lookup"><span data-stu-id="bc988-116">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="bc988-117">公司名称</span><span class="sxs-lookup"><span data-stu-id="bc988-117">Company name</span></span>
- <span data-ttu-id="bc988-118">功能区域</span><span class="sxs-lookup"><span data-stu-id="bc988-118">Feature area</span></span>

<span data-ttu-id="bc988-119">例如，Contoso 公司创建的输入数据提供程序可能是 "MixedReality"。Toolkit。输入 "。</span><span class="sxs-lookup"><span data-stu-id="bc988-119">For example, an input data provider created by the Contoso company may be "Contoso.MixedReality.Toolkit.Input".</span></span>

### <a name="recommended-folder-structure"></a><span data-ttu-id="bc988-120">推荐的文件夹结构</span><span class="sxs-lookup"><span data-stu-id="bc988-120">Recommended folder structure</span></span>

<span data-ttu-id="bc988-121">建议在文件夹层次结构中排列数据提供程序的源代码，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="bc988-121">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![文件夹结构示例](../images/input/ExampleProviderFolderStructure.png)

<span data-ttu-id="bc988-123">其中，ContosoInput 包含数据提供程序的实现，Editor 文件夹包含检查器 (和任何其他 Unity 编辑器特定代码) ，纹理文件夹包含受支持控制器的图像，而配置文件包含一个或多个预配置文件。</span><span class="sxs-lookup"><span data-stu-id="bc988-123">Where ContosoInput contains the implementation of the data provider, the Editor folder contains the inspector (and any other Unity editor specific code), the Textures folder contains images of the supported controllers, and Profiles contains one or more pre-made profiles.</span></span>

> [!Note]
> <span data-ttu-id="bc988-124">可以在 MixedRealityToolkit\StandardAssets\Textures 文件夹中找到一些公共控制器映像。</span><span class="sxs-lookup"><span data-stu-id="bc988-124">Some common controller images can be found in the MixedRealityToolkit\StandardAssets\Textures folder.</span></span>

## <a name="implement-the-data-provider"></a><span data-ttu-id="bc988-125">实现数据访问接口</span><span class="sxs-lookup"><span data-stu-id="bc988-125">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="bc988-126">指定接口和/或基类继承</span><span class="sxs-lookup"><span data-stu-id="bc988-126">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="bc988-127">所有输入系统数据提供程序必须实现 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 接口，该接口指定输入系统所需的最小功能。</span><span class="sxs-lookup"><span data-stu-id="bc988-127">All input system data providers must implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, which specifies the minimum functionality required by the input system.</span></span> <span data-ttu-id="bc988-128">MRTK foundation 包含 [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 类，该类提供此所需功能的默认实现。</span><span class="sxs-lookup"><span data-stu-id="bc988-128">The MRTK foundation includes the [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) class which provides a default implementation of this required functionality.</span></span> <span data-ttu-id="bc988-129">对于基于 Unity 的 UInput 类构建的设备， [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) 可以将类用作基类。</span><span class="sxs-lookup"><span data-stu-id="bc988-129">For devices that build upon Unity's UInput class, the [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) class can be used as a base class.</span></span>

> [!Note]
> <span data-ttu-id="bc988-130">`BaseInputDeviceManager`和 `UnityJoystickManager` 类提供所需的 `IMixedRealityInputDeviceManager` 实现。</span><span class="sxs-lookup"><span data-stu-id="bc988-130">The `BaseInputDeviceManager` and `UnityJoystickManager` classes provide the required `IMixedRealityInputDeviceManager` implementation.</span></span>

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> <span data-ttu-id="bc988-131">`IMixedRealityCapabilityCheck` 由用 `WindowsMixedRealityDeviceManager` 来指示它为一组输入功能提供支持，具体而言，就是明确的手势，注视着声音和运动控制器。</span><span class="sxs-lookup"><span data-stu-id="bc988-131">`IMixedRealityCapabilityCheck` is used by the `WindowsMixedRealityDeviceManager` to indicate that it provides support for a set of input capabilities, specifically; articulated hands, gaze-gesture-voice hands and motion controllers.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="bc988-132">应用 MixedRealityDataProvider 特性</span><span class="sxs-lookup"><span data-stu-id="bc988-132">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="bc988-133">创建输入系统数据提供程序的一个关键步骤是将属性应用于 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 类。</span><span class="sxs-lookup"><span data-stu-id="bc988-133">A key step of creating an input system data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="bc988-134">此步骤允许在输入系统配置文件中选择提供程序时，设置该提供程序的默认配置文件和平台 () 。</span><span class="sxs-lookup"><span data-stu-id="bc988-134">This step enables setting the default profile and platform(s) for the provider, when selected in the input system profile.</span></span>

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="bc988-135">实现 IMixedRealityDataProvider 方法</span><span class="sxs-lookup"><span data-stu-id="bc988-135">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="bc988-136">一旦定义了类，下一步就是提供接口的实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="bc988-136">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!Note]
> <span data-ttu-id="bc988-137">`BaseInputDeviceManager`类通过 `BaseService` 类只为方法提供空实现 `IMixedRealityDataProvider` 。</span><span class="sxs-lookup"><span data-stu-id="bc988-137">The `BaseInputDeviceManager` class, via the `BaseService` class, provides only empty implementations for `IMixedRealityDataProvider` methods.</span></span> <span data-ttu-id="bc988-138">这些方法的详细信息通常是特定于数据访问接口的。</span><span class="sxs-lookup"><span data-stu-id="bc988-138">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="bc988-139">应由数据提供程序实现的方法如下：</span><span class="sxs-lookup"><span data-stu-id="bc988-139">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="bc988-140">实现数据访问接口逻辑</span><span class="sxs-lookup"><span data-stu-id="bc988-140">Implement the data provider logic</span></span>

<span data-ttu-id="bc988-141">下一步是添加用于管理输入设备的逻辑，包括要支持的任何控制器。</span><span class="sxs-lookup"><span data-stu-id="bc988-141">The next step is to add the logic for managing the input devices, including any controllers to be supported.</span></span>

### <a name="implement-the-controller-classes"></a><span data-ttu-id="bc988-142">实现控制器类</span><span class="sxs-lookup"><span data-stu-id="bc988-142">Implement the controller classes</span></span>

 <span data-ttu-id="bc988-143">的示例 `WindowsMixedRealityDeviceManager` 定义并实现了以下控制器类。</span><span class="sxs-lookup"><span data-stu-id="bc988-143">The example of the `WindowsMixedRealityDeviceManager` defines and implements the following controller classes.</span></span>

> <span data-ttu-id="bc988-144">每个这些类的源代码可在 MRTK/Providers/WindowsMixedReality 文件夹中找到。</span><span class="sxs-lookup"><span data-stu-id="bc988-144">The source code for each of these classes can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

- <span data-ttu-id="bc988-145">WindowsMixedRealityArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="bc988-145">WindowsMixedRealityArticulatedHand.cs</span></span>
- <span data-ttu-id="bc988-146">WindowsMixedRealityController</span><span class="sxs-lookup"><span data-stu-id="bc988-146">WindowsMixedRealityController.cs</span></span>
- <span data-ttu-id="bc988-147">WindowsMixedRealityGGVHand</span><span class="sxs-lookup"><span data-stu-id="bc988-147">WindowsMixedRealityGGVHand.cs</span></span>

> [!Note]
> <span data-ttu-id="bc988-148">并非所有设备管理器都支持多种控制器类型。</span><span class="sxs-lookup"><span data-stu-id="bc988-148">Not all device managers will support multiple controller types.</span></span>

#### <a name="apply-the-mixedrealitycontroller-attribute"></a><span data-ttu-id="bc988-149">应用 MixedRealityController 特性</span><span class="sxs-lookup"><span data-stu-id="bc988-149">Apply the MixedRealityController attribute</span></span>

<span data-ttu-id="bc988-150">接下来，将 [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) 属性应用于类。</span><span class="sxs-lookup"><span data-stu-id="bc988-150">Next, apply the [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribute to the class.</span></span> <span data-ttu-id="bc988-151">此属性指定控制器的类型 (例如：已表述的手势) ，左右手使用习惯 (例如：左或右) 和可选控制器图像。</span><span class="sxs-lookup"><span data-stu-id="bc988-151">This attribute specifies the type of controller (ex: articulated hand), the handedness (ex: left or right) and an optional controller image.</span></span>

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a><span data-ttu-id="bc988-152">配置交互映射</span><span class="sxs-lookup"><span data-stu-id="bc988-152">Configure the interaction mappings</span></span>

<span data-ttu-id="bc988-153">下一步是定义控制器支持的交互映射集。</span><span class="sxs-lookup"><span data-stu-id="bc988-153">The next step is to define the set of interaction mappings supported by the controller.</span></span> <span data-ttu-id="bc988-154">对于通过 Unity 的输入类接收其数据的设备， [控制器映射工具](../tools/controller-mapping-tool.md) 是一个有用的资源，用于确认要分配到交互的正确轴和按钮映射。</span><span class="sxs-lookup"><span data-stu-id="bc988-154">For devices that receive their data via Unity's Input class, the [controller mapping tool](../tools/controller-mapping-tool.md) is a helpful resource to confirm the correct axis and button mappings to assign to interactions.</span></span>

<span data-ttu-id="bc988-155">下面的示例从类中缩写 `GenericOpenVRController` ，该类位于 MRTK/Providers/OpenVR 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="bc988-155">The following example is abbreviated from the `GenericOpenVRController` class, located in the MRTK/Providers/OpenVR folder.</span></span>

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
><span data-ttu-id="bc988-156">[`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary)类为 Unity 输入轴和按钮定义提供符号常数。</span><span class="sxs-lookup"><span data-stu-id="bc988-156">The [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) class provides symbolic constants for the Unity input axis and button definitions.</span></span>

### <a name="raise-notification-events"></a><span data-ttu-id="bc988-157">引发通知事件</span><span class="sxs-lookup"><span data-stu-id="bc988-157">Raise notification events</span></span>

<span data-ttu-id="bc988-158">为了使应用程序能够响应用户的输入，数据访问接口引发与和接口中定义的控制器状态更改对应的通知 [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) 事件 [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 。</span><span class="sxs-lookup"><span data-stu-id="bc988-158">To enable applications to respond to input from the user, the data provider raises notification events corresponding to controller state changes as defined in the [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) and [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces.</span></span>

<span data-ttu-id="bc988-159">对于 "数字 (" 按钮) 类型控件，引发 OnInputDown 和 OnInputUp 事件。</span><span class="sxs-lookup"><span data-stu-id="bc988-159">For digital (button) type controls, raise the OnInputDown and OnInputUp events.</span></span>

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

<span data-ttu-id="bc988-160">对于模拟控件 (例如：触摸板位置) 应引发 InputChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="bc988-160">For analog controls (ex: touchpad position) the InputChanged event should be raised.</span></span>

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="bc988-161">添加 Unity 探查器检测</span><span class="sxs-lookup"><span data-stu-id="bc988-161">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="bc988-162">性能在混合现实应用程序中非常重要。</span><span class="sxs-lookup"><span data-stu-id="bc988-162">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="bc988-163">每个组件都增加了应用程序必须考虑的一些开销。</span><span class="sxs-lookup"><span data-stu-id="bc988-163">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="bc988-164">为此，必须确保所有输入数据提供程序在内部循环和经常使用的代码路径中包含 Unity 探查器检测。</span><span class="sxs-lookup"><span data-stu-id="bc988-164">To this end, it is important that all input data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="bc988-165">建议在检测自定义提供程序时实现 MRTK 使用的模式。</span><span class="sxs-lookup"><span data-stu-id="bc988-165">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

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
> <span data-ttu-id="bc988-166">用于标识探查器标记的名称是任意的。</span><span class="sxs-lookup"><span data-stu-id="bc988-166">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="bc988-167">MRTK 使用以下模式。</span><span class="sxs-lookup"><span data-stu-id="bc988-167">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="bc988-168">"[product] className. 方法名称-可选注释"</span><span class="sxs-lookup"><span data-stu-id="bc988-168">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="bc988-169">建议自定义数据访问接口遵循类似的模式，以帮助在分析跟踪时简化特定组件和方法的标识。</span><span class="sxs-lookup"><span data-stu-id="bc988-169">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="bc988-170">创建配置文件和检查器</span><span class="sxs-lookup"><span data-stu-id="bc988-170">Create the profile and inspector</span></span>

<span data-ttu-id="bc988-171">在混合现实 Toolkit 中，使用[配置文件](../profiles/profiles.md)配置数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="bc988-171">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

<span data-ttu-id="bc988-172">具有其他配置选项的数据提供程序 (ex： [InputSimulationService](../input-simulation/input-simulation-service.md)) 应创建配置文件和检查器，以允许客户修改行为，使其最适合应用程序的需求。</span><span class="sxs-lookup"><span data-stu-id="bc988-172">Data providers with additional configuration options (ex: [InputSimulationService](../input-simulation/input-simulation-service.md)) should create a profile and inspector to allow customers to modify the behavior to best suit the needs of the application.</span></span>

> <span data-ttu-id="bc988-173">本部分中的示例的完整代码可在 MRTK 中找到。Services/InputSimulation 文件夹。</span><span class="sxs-lookup"><span data-stu-id="bc988-173">The complete code for the example in this section can be found in the MRTK.Services/InputSimulation folder.</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="bc988-174">定义配置文件</span><span class="sxs-lookup"><span data-stu-id="bc988-174">Define the profile</span></span>

<span data-ttu-id="bc988-175">配置文件内容应反映观察程序的可访问属性， (例如：更新间隔) 。</span><span class="sxs-lookup"><span data-stu-id="bc988-175">Profile contents should mirror the accessible properties of the observer (ex: update interval).</span></span> <span data-ttu-id="bc988-176">每个接口中定义的所有用户可配置属性都应包含在配置文件中。</span><span class="sxs-lookup"><span data-stu-id="bc988-176">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

<span data-ttu-id="bc988-177">`CreateAssetMenu`特性可应用到配置文件类，使客户能够使用 **> Mixed Reality Toolkit > 配置文件**"菜单创建 > 资产创建配置文件实例。</span><span class="sxs-lookup"><span data-stu-id="bc988-177">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create > Assets > Mixed Reality Toolkit > Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="bc988-178">实现检查器</span><span class="sxs-lookup"><span data-stu-id="bc988-178">Implement the inspector</span></span>

<span data-ttu-id="bc988-179">配置文件检查器是用于配置和查看配置文件内容的用户界面。</span><span class="sxs-lookup"><span data-stu-id="bc988-179">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="bc988-180">每个配置文件检查器应扩展 ["BaseMixedRealityToolkitConfigurationProfileInspector"](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 类。</span><span class="sxs-lookup"><span data-stu-id="bc988-180">Each profile inspector should extend the [\`BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

<span data-ttu-id="bc988-181">`CustomEditor`属性向 Unity 通知该检查器应用到的资产类型。</span><span class="sxs-lookup"><span data-stu-id="bc988-181">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

## <a name="create-assembly-definitions"></a><span data-ttu-id="bc988-182">创建 () 的程序集定义</span><span class="sxs-lookup"><span data-stu-id="bc988-182">Create assembly definition(s)</span></span>

<span data-ttu-id="bc988-183">混合现实 Toolkit 使用程序集定义 ([asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 文件指定组件之间的依赖关系，并协助 Unity 减少编译时间。</span><span class="sxs-lookup"><span data-stu-id="bc988-183">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="bc988-184">建议为所有数据访问接口及其编辑器组件创建程序集定义文件。</span><span class="sxs-lookup"><span data-stu-id="bc988-184">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="bc988-185">使用前面示例中的 [文件夹结构](#recommended-folder-structure) ，ContosoInput 数据提供程序有两个 asmdef 文件。</span><span class="sxs-lookup"><span data-stu-id="bc988-185">Using the [folder structure](#recommended-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoInput data provider.</span></span>

<span data-ttu-id="bc988-186">第一个程序集定义适用于数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="bc988-186">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="bc988-187">在此示例中，它将被称为 ContosoInput，并将位于该示例的 ContosoInput 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="bc988-187">For this example, it will be called ContosoInput and will be located in the example's ContosoInput folder.</span></span>
<span data-ttu-id="bc988-188">此程序集定义必须指定对 MixedReality 的依赖关系。Toolkit 以及它所依赖的任何其他程序集。</span><span class="sxs-lookup"><span data-stu-id="bc988-188">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="bc988-189">ContosoInputEditor 程序集定义将指定配置文件检查器和任何特定于编辑器的代码。</span><span class="sxs-lookup"><span data-stu-id="bc988-189">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="bc988-190">此文件必须位于编辑器代码的根文件夹中。</span><span class="sxs-lookup"><span data-stu-id="bc988-190">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="bc988-191">在此示例中，该文件将位于 ContosoInput\Editor 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="bc988-191">In this example, the file will be located in the ContosoInput\Editor folder.</span></span> <span data-ttu-id="bc988-192">此程序集定义将包含对 ContosoInput 程序集的引用以及：</span><span class="sxs-lookup"><span data-stu-id="bc988-192">This assembly definition will contain a reference to the ContosoInput assembly as well as:</span></span>

- <span data-ttu-id="bc988-193">MixedReality。Toolkit</span><span class="sxs-lookup"><span data-stu-id="bc988-193">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="bc988-194">MixedReality。Toolkit。编辑器. 检查器</span><span class="sxs-lookup"><span data-stu-id="bc988-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="bc988-195">MixedReality。Toolkit。编辑器。实用工具</span><span class="sxs-lookup"><span data-stu-id="bc988-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="bc988-196">注册数据提供程序</span><span class="sxs-lookup"><span data-stu-id="bc988-196">Register the data provider</span></span>

<span data-ttu-id="bc988-197">创建后，数据访问接口可以注册到输入系统，并在应用程序中使用。</span><span class="sxs-lookup"><span data-stu-id="bc988-197">Once created, the data provider can be registered with the input system and be used in the application.</span></span>

![注册的输入系统数据提供程序](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a><span data-ttu-id="bc988-199">打包和分发</span><span class="sxs-lookup"><span data-stu-id="bc988-199">Packaging and distribution</span></span>

<span data-ttu-id="bc988-200">作为第三方组件分发的数据提供程序具有与开发人员首选项一起打包和分发的特定详细信息。</span><span class="sxs-lookup"><span data-stu-id="bc988-200">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="bc988-201">最常见的解决方案可能是生成 .unitypackage，然后通过 Unity 资产存储进行分发。</span><span class="sxs-lookup"><span data-stu-id="bc988-201">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="bc988-202">如果提交数据提供程序并将其作为 Microsoft Mixed Reality Toolkit 包的一部分接受，Microsoft MRTK 团队将打包并分发它作为 MRTK 产品/服务一部分。</span><span class="sxs-lookup"><span data-stu-id="bc988-202">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc988-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc988-203">See also</span></span>

- [<span data-ttu-id="bc988-204">输入系统</span><span class="sxs-lookup"><span data-stu-id="bc988-204">Input system</span></span>](overview.md)
- [<span data-ttu-id="bc988-205">`BaseInputDeviceManager` 类</span><span class="sxs-lookup"><span data-stu-id="bc988-205">`BaseInputDeviceManager` class</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [<span data-ttu-id="bc988-206">`IMixedRealityInputDeviceManager` 接口</span><span class="sxs-lookup"><span data-stu-id="bc988-206">`IMixedRealityInputDeviceManager` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [<span data-ttu-id="bc988-207">`IMixedRealityInputHandler` 接口</span><span class="sxs-lookup"><span data-stu-id="bc988-207">`IMixedRealityInputHandler` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [<span data-ttu-id="bc988-208">`IMixedRealityInputHandler<T>` 接口</span><span class="sxs-lookup"><span data-stu-id="bc988-208">`IMixedRealityInputHandler<T>` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [<span data-ttu-id="bc988-209">`IMixedRealityDataProvider` 接口</span><span class="sxs-lookup"><span data-stu-id="bc988-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="bc988-210">`IMixedRealityCapabilityCheck` 接口</span><span class="sxs-lookup"><span data-stu-id="bc988-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="bc988-211">控制器映射工具</span><span class="sxs-lookup"><span data-stu-id="bc988-211">Controller Mapping Tool</span></span>](../tools/controller-mapping-tool.md)
