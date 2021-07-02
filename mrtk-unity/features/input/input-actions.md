---
title: 输入操作
description: 在 MRTK 中创建输入操作的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， InputActions，
ms.openlocfilehash: cf6ce2af304ee1cd706d0111d66a97018113fb09
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176812"
---
# <a name="input-actions"></a><span data-ttu-id="9210c-104">输入操作</span><span class="sxs-lookup"><span data-stu-id="9210c-104">Input actions</span></span>

<span data-ttu-id="9210c-105">[**输入操作**](input-actions.md) 是原始输入的抽象，有助于将应用程序逻辑与生成输入的特定输入源隔离。</span><span class="sxs-lookup"><span data-stu-id="9210c-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="9210c-106">例如，定义"选择"操作，将其映射到鼠标左键、游戏板中的按钮和 6 DOF 控制器中的触发器等可能很有用。</span><span class="sxs-lookup"><span data-stu-id="9210c-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="9210c-107">然后，你可以让应用程序逻辑侦听"选择输入操作"事件，而不必了解可生成它的所有不同输入。</span><span class="sxs-lookup"><span data-stu-id="9210c-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="9210c-108">创建输入操作</span><span class="sxs-lookup"><span data-stu-id="9210c-108">Creating an input action</span></span>

<span data-ttu-id="9210c-109">输入操作在"输入操作配置文件"中配置，在混合现实 Toolkit 组件的"输入系统配置文件"内，指定操作的名称和输入类型 (轴 *约束) 可* 映射到：</span><span class="sxs-lookup"><span data-stu-id="9210c-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="9210c-110">这些是轴约束最常使用 **的值**：</span><span class="sxs-lookup"><span data-stu-id="9210c-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="9210c-111">轴约束</span><span class="sxs-lookup"><span data-stu-id="9210c-111">Axis Constraint</span></span> | <span data-ttu-id="9210c-112">说明</span><span class="sxs-lookup"><span data-stu-id="9210c-112">Description</span></span>
--- | ---
<span data-ttu-id="9210c-113">数码</span><span class="sxs-lookup"><span data-stu-id="9210c-113">Digital</span></span> | <span data-ttu-id="9210c-114">打开/关闭输入，如游戏板或鼠标中的二进制按钮。</span><span class="sxs-lookup"><span data-stu-id="9210c-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="9210c-115">单轴</span><span class="sxs-lookup"><span data-stu-id="9210c-115">Single Axis</span></span> | <span data-ttu-id="9210c-116">单轴倾斜输入，如游戏板中的模拟触发器。</span><span class="sxs-lookup"><span data-stu-id="9210c-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="9210c-117">双轴</span><span class="sxs-lookup"><span data-stu-id="9210c-117">Dual Axis</span></span> | <span data-ttu-id="9210c-118">双轴倾斜输入，如滚动块。</span><span class="sxs-lookup"><span data-stu-id="9210c-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="9210c-119">六个 Dof</span><span class="sxs-lookup"><span data-stu-id="9210c-119">Six Dof</span></span> | <span data-ttu-id="9210c-120">具有平移和旋转的 3D 姿势，如 6 个 DOF 控制器生成的 3D 姿势。</span><span class="sxs-lookup"><span data-stu-id="9210c-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="9210c-121">可以在 中查找完整列表 [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) 。</span><span class="sxs-lookup"><span data-stu-id="9210c-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="9210c-122">将输入映射到操作</span><span class="sxs-lookup"><span data-stu-id="9210c-122">Mapping input to actions</span></span>

<span data-ttu-id="9210c-123">将输入映射到 和 操作的方式取决于输入源的类型：</span><span class="sxs-lookup"><span data-stu-id="9210c-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="9210c-124">控制器输入</span><span class="sxs-lookup"><span data-stu-id="9210c-124">Controller input</span></span>

<span data-ttu-id="9210c-125">转到"输入 **系统配置文件"下的**"控制器 *输入映射配置文件"。*</span><span class="sxs-lookup"><span data-stu-id="9210c-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="9210c-126">可在这里找到所有受支持控制器的列表：</span><span class="sxs-lookup"><span data-stu-id="9210c-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="9210c-127">选择要配置的对话框，将显示一个对话框窗口，其中显示所有控制器输入，允许为其中每个输入设置操作：</span><span class="sxs-lookup"><span data-stu-id="9210c-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="9210c-128">语音输入</span><span class="sxs-lookup"><span data-stu-id="9210c-128">Speech input</span></span>

<span data-ttu-id="9210c-129">在 **"语音命令配置文件"** 的" *输入系统* 配置文件"下，可以找到当前定义的语音命令的列表。</span><span class="sxs-lookup"><span data-stu-id="9210c-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="9210c-130">若要将其中一个映射到操作，只需在"操作"下拉列表 *中选择* 它。</span><span class="sxs-lookup"><span data-stu-id="9210c-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="9210c-131">笔势输入</span><span class="sxs-lookup"><span data-stu-id="9210c-131">Gesture input</span></span>

<span data-ttu-id="9210c-132">" **笔势配置文件"** 在 *"输入系统配置文件"下* 包含所有定义的笔势。</span><span class="sxs-lookup"><span data-stu-id="9210c-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="9210c-133">可以在"操作"下拉列表中选择每个操作， *将其映射到操作* 。</span><span class="sxs-lookup"><span data-stu-id="9210c-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="9210c-134">处理输入操作</span><span class="sxs-lookup"><span data-stu-id="9210c-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="9210c-135">目前，只能使用本节中所述的方法处理数字类型的输入操作。</span><span class="sxs-lookup"><span data-stu-id="9210c-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="9210c-136">对于其他操作类型，必须改为直接处理相应输入的事件。</span><span class="sxs-lookup"><span data-stu-id="9210c-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="9210c-137">例如，若要处理映射到控制器输入的 6 DOF 操作，必须使用 T = [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 。</span><span class="sxs-lookup"><span data-stu-id="9210c-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="9210c-138">处理输入操作的最简单方法是使用 [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) 脚本。</span><span class="sxs-lookup"><span data-stu-id="9210c-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="9210c-139">这允许你定义想要侦听的操作，以及使用 Unity 事件对已启动和已结束事件的操作做出反应。</span><span class="sxs-lookup"><span data-stu-id="9210c-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="9210c-140">如果想进行更多控制，可以直接 [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) 在脚本中实现 接口。</span><span class="sxs-lookup"><span data-stu-id="9210c-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="9210c-141">有关通过 [**处理程序**](input-events.md) 接口处理事件的详细信息，请参阅输入事件部分。</span><span class="sxs-lookup"><span data-stu-id="9210c-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="9210c-142">示例</span><span class="sxs-lookup"><span data-stu-id="9210c-142">Examples</span></span>

<span data-ttu-id="9210c-143">请参阅示例场景，了解如何创建操作、将操作映射到控制器、语音和手势输入，并使用它在命令上 `MRTK/Examples/Demos/Input/Scenes/InputActions` 旋转对象。</span><span class="sxs-lookup"><span data-stu-id="9210c-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
