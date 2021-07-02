---
title: 输入模拟服务
description: 有关 MRTK 中的输入模拟服务的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 66b79c14bbd0ea8c188aba684b9bd1034de31bf9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176958"
---
# <a name="input-simulation-service"></a><span data-ttu-id="69752-104">输入模拟服务</span><span class="sxs-lookup"><span data-stu-id="69752-104">Input simulation service</span></span>

![MRTK 输入模拟](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

<span data-ttu-id="69752-106">使用 MRTK 的输入模拟，可以在 Unity 编辑器中测试各种类型的交互，而无需生成和部署到设备。</span><span class="sxs-lookup"><span data-stu-id="69752-106">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="69752-107">这样，你可快速在设计和开发过程中访问想法。</span><span class="sxs-lookup"><span data-stu-id="69752-107">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="69752-108">使用键盘和鼠标组合来控制模拟输入。</span><span class="sxs-lookup"><span data-stu-id="69752-108">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="69752-109">输入模拟服务模拟 Unity 编辑器中可能不可用的设备和平台的行为。</span><span class="sxs-lookup"><span data-stu-id="69752-109">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="69752-110">示例包括：</span><span class="sxs-lookup"><span data-stu-id="69752-110">Examples include:</span></span>

* <span data-ttu-id="69752-111">HoloLens或 VR 设备头跟踪</span><span class="sxs-lookup"><span data-stu-id="69752-111">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="69752-112">HoloLens手势</span><span class="sxs-lookup"><span data-stu-id="69752-112">HoloLens hand gestures</span></span>
* <span data-ttu-id="69752-113">HoloLens 2手部跟踪</span><span class="sxs-lookup"><span data-stu-id="69752-113">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="69752-114">HoloLens 2眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="69752-114">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="69752-115">VR 设备控制器</span><span class="sxs-lookup"><span data-stu-id="69752-115">VR device controllers</span></span>

> [!WARNING]
> <span data-ttu-id="69752-116">在仿真模式下使用 Unity 的 XR 全息仿真 = "在编辑器中>模拟时，这不起作用。</span><span class="sxs-lookup"><span data-stu-id="69752-116">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="69752-117">Unity 的编辑器内模拟将控制 MRTK 的输入模拟。</span><span class="sxs-lookup"><span data-stu-id="69752-117">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="69752-118">若要使用 MRTK 输入模拟服务，需要将 XR 全息仿真设置为仿真模式 = *"None"*</span><span class="sxs-lookup"><span data-stu-id="69752-118">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="how-to-use-mrtk-input-simulation"></a><span data-ttu-id="69752-119">如何使用 MRTK 输入模拟</span><span class="sxs-lookup"><span data-stu-id="69752-119">How to use MRTK Input simulation</span></span> 

<span data-ttu-id="69752-120">在 MRTK 的配置文件中，默认启用输入模拟。</span><span class="sxs-lookup"><span data-stu-id="69752-120">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span> <span data-ttu-id="69752-121">只需单击"播放 **"** 按钮即可运行支持输入模拟的场景。</span><span class="sxs-lookup"><span data-stu-id="69752-121">You can simply click **Play** button to run the scene with input simulation support.</span></span>

* <span data-ttu-id="69752-122">按 **W、A、S、D、Q、E** 键移动相机。</span><span class="sxs-lookup"><span data-stu-id="69752-122">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="69752-123">按住 **鼠标右键** 并移动鼠标四周。</span><span class="sxs-lookup"><span data-stu-id="69752-123">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="69752-124">若要启动模拟手部，请按空格键 (右键) 左 **移 (左移)**</span><span class="sxs-lookup"><span data-stu-id="69752-124">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="69752-125">若要在视图中保留模拟手部，请按 **T** 或 **Y** 键</span><span class="sxs-lookup"><span data-stu-id="69752-125">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="69752-126">若要旋转模拟手部，请按住 **Ctrl 键** 并移动鼠标</span><span class="sxs-lookup"><span data-stu-id="69752-126">To rotate simulated hands, press and hold **Ctrl key** and move mouse</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="69752-127">在编辑器输入模拟备忘单中</span><span class="sxs-lookup"><span data-stu-id="69752-127">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="69752-128">在 HandInteractionExamples 场景中按 **左 Ctrl + H，** 显示具有输入模拟控件的备忘单。</span><span class="sxs-lookup"><span data-stu-id="69752-128">Press **Left Ctrl + H** in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

> ![MRTK 输入模拟备忘单](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="69752-130">启用输入模拟服务</span><span class="sxs-lookup"><span data-stu-id="69752-130">Enabling the input simulation service</span></span>

<span data-ttu-id="69752-131">在"输入系统数据提供程序"配置下，可以使用以下内容配置输入模拟服务。</span><span class="sxs-lookup"><span data-stu-id="69752-131">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="69752-132">**类型** 必须为 *Microsoft.MixedReality.Toolkit。Input > SimulationService*。</span><span class="sxs-lookup"><span data-stu-id="69752-132">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="69752-133">**受支持的平台 (默认)** 包括所有 *编辑器* 平台，因为服务使用键盘和鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="69752-133">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="69752-134">输入模拟服务可以在其他平台终结点（例如独立）上使用， (支持的平台) **属性以** 包含所需的目标。</span><span class="sxs-lookup"><span data-stu-id="69752-134">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a><span data-ttu-id="69752-135">相机控件</span><span class="sxs-lookup"><span data-stu-id="69752-135">Camera control</span></span>

<span data-ttu-id="69752-136">输入模拟服务可以模拟头部运动。</span><span class="sxs-lookup"><span data-stu-id="69752-136">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="69752-137">旋转相机</span><span class="sxs-lookup"><span data-stu-id="69752-137">Rotating the camera</span></span>

1. <span data-ttu-id="69752-138">将鼠标悬停在视区编辑器窗口上。</span><span class="sxs-lookup"><span data-stu-id="69752-138">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="69752-139">*如果按钮按下不起作用，可能需要单击窗口以赋予其输入焦点。*</span><span class="sxs-lookup"><span data-stu-id="69752-139">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="69752-140">按并按住鼠标 **"查找 (** 按钮"默认按钮：右键) 。</span><span class="sxs-lookup"><span data-stu-id="69752-140">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="69752-141">在视区窗口中移动鼠标以旋转照相机。</span><span class="sxs-lookup"><span data-stu-id="69752-141">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="69752-142">使用滚轮在视图方向周围滚动照相机。</span><span class="sxs-lookup"><span data-stu-id="69752-142">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="69752-143">可以通过更改输入模拟配置文件中的鼠标查找 **速度** 设置来配置相机旋转速度。</span><span class="sxs-lookup"><span data-stu-id="69752-143">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="69752-144">或者，使用"水平查找垂直"轴将相机旋转为默认 /  (：游戏控制器右滚动) 。</span><span class="sxs-lookup"><span data-stu-id="69752-144">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="69752-145">移动摄像头</span><span class="sxs-lookup"><span data-stu-id="69752-145">Moving the camera</span></span>

<span data-ttu-id="69752-146">使用"**移动水平** / **移动垂直** 轴"将相机 (默认值：WASD 键或游戏控制器左滚动) 。</span><span class="sxs-lookup"><span data-stu-id="69752-146">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="69752-147">还可以在工具窗口中显式设置相机位置和旋转角度。</span><span class="sxs-lookup"><span data-stu-id="69752-147">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="69752-148">可以使用"重置"按钮将相机重置为 **默认值** 。</span><span class="sxs-lookup"><span data-stu-id="69752-148">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="69752-149">控制器模拟</span><span class="sxs-lookup"><span data-stu-id="69752-149">Controller simulation</span></span>

<span data-ttu-id="69752-150">输入模拟支持模拟控制器设备 (即运动控制器和手部) 。</span><span class="sxs-lookup"><span data-stu-id="69752-150">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="69752-151">这些虚拟控制器可以与支持常规控制器的任何对象（如按钮或可抓取对象）交互。</span><span class="sxs-lookup"><span data-stu-id="69752-151">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="69752-152">控制器模拟模式</span><span class="sxs-lookup"><span data-stu-id="69752-152">Controller simulation mode</span></span>

<span data-ttu-id="69752-153">在输入 [模拟工具窗口中，](#input-simulation-tools-window)**默认控制器模拟模式** 设置在三个不同的输入模型之间切换。</span><span class="sxs-lookup"><span data-stu-id="69752-153">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="69752-154">还可以在输入模拟配置文件中设置此默认模式。</span><span class="sxs-lookup"><span data-stu-id="69752-154">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="69752-155">*手部*：模拟具有联合位置数据的完全铰接式手部设备。</span><span class="sxs-lookup"><span data-stu-id="69752-155">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="69752-156">模拟HoloLens 2模型。</span><span class="sxs-lookup"><span data-stu-id="69752-156">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="69752-157">可以在此模式下模拟基于手部精确定位或使用触摸的交互。</span><span class="sxs-lookup"><span data-stu-id="69752-157">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="69752-158">*手势：* 使用敲击和基本手势模拟简化的手势模型。</span><span class="sxs-lookup"><span data-stu-id="69752-158">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="69752-159">模拟[HoloLens模型](/windows/mixed-reality/gestures)。</span><span class="sxs-lookup"><span data-stu-id="69752-159">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="69752-160">焦点使用凝视指针进行控制。</span><span class="sxs-lookup"><span data-stu-id="69752-160">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="69752-161">Air *Tap* 手势用于与按钮交互。</span><span class="sxs-lookup"><span data-stu-id="69752-161">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="69752-162">*运动控制器*：模拟与 VR 头戴显示设备一同使用的动作控制器，其工作方式类似于与手部远部交互。</span><span class="sxs-lookup"><span data-stu-id="69752-162">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="69752-163">使用控制器交互模型模拟 VR 头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="69752-163">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="69752-164">触发器、抓取键和菜单键通过键盘和鼠标输入进行模拟。</span><span class="sxs-lookup"><span data-stu-id="69752-164">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="69752-165">模拟控制器移动</span><span class="sxs-lookup"><span data-stu-id="69752-165">Simulating controller movement</span></span>

<span data-ttu-id="69752-166">按并按住"**左/** 右控制器操作 (键"：左控制器的左移和右控制器) 空格键以获得对任一控制器的控制。</span><span class="sxs-lookup"><span data-stu-id="69752-166">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="69752-167">按下操作键时，控制器将显示在视区中。</span><span class="sxs-lookup"><span data-stu-id="69752-167">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="69752-168">释放操作密钥后，控制器会在控制器隐藏超时 **短后消失**。</span><span class="sxs-lookup"><span data-stu-id="69752-168">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="69752-169">控制器可以相对于输入模拟工具窗口中的相机进行切换和冻结，[](#input-simulation-tools-window)或者按"左/右切换控制器 **键" (** 默认值 *：T* 表示左侧 *，Y* 表示右键) 。</span><span class="sxs-lookup"><span data-stu-id="69752-169">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="69752-170">再次按切换键以再次隐藏控制器。</span><span class="sxs-lookup"><span data-stu-id="69752-170">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="69752-171">若要操作控制器，需要保留 **左/** 右控制器操作键。</span><span class="sxs-lookup"><span data-stu-id="69752-171">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="69752-172">双击" **左/右控制器操作键"** 还可以打开/关闭控制器。</span><span class="sxs-lookup"><span data-stu-id="69752-172">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="69752-173">鼠标移动将在视图平面中移动控制器。</span><span class="sxs-lookup"><span data-stu-id="69752-173">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="69752-174">控制器可以使用鼠标滚轮 进一步或更靠近 **相机**。</span><span class="sxs-lookup"><span data-stu-id="69752-174">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="69752-175">若要使用鼠标旋转控制器，请按住左 **/** 右控制器操作键 (*左* 移或空格键) 和控制器旋转按钮 **(** 默认值：*左 Ctrl* 按钮) ，然后移动鼠标以旋转控制器。</span><span class="sxs-lookup"><span data-stu-id="69752-175">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="69752-176">可以通过更改输入模拟配置文件中的"鼠标控制器旋转 **速度** "设置来配置控制器旋转速度。</span><span class="sxs-lookup"><span data-stu-id="69752-176">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="69752-177">还可以在输入模拟工具窗口中更改所有[](#input-simulation-tools-window)手部放置，包括将手重置为默认值。</span><span class="sxs-lookup"><span data-stu-id="69752-177">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="69752-178">其他配置文件设置</span><span class="sxs-lookup"><span data-stu-id="69752-178">Additional profile settings</span></span>

* <span data-ttu-id="69752-179">**控制器深度乘数** 控制鼠标滚轮深度移动的敏感度。</span><span class="sxs-lookup"><span data-stu-id="69752-179">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="69752-180">较大的数字将加快控制器缩放。</span><span class="sxs-lookup"><span data-stu-id="69752-180">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="69752-181">**默认控制器距离** 是控制器与相机的初始距离。</span><span class="sxs-lookup"><span data-stu-id="69752-181">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="69752-182">单击" **重置** "按钮控制器也会在此距离放置控制器。</span><span class="sxs-lookup"><span data-stu-id="69752-182">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="69752-183">**控制器抖动量** 向控制器添加随机运动。</span><span class="sxs-lookup"><span data-stu-id="69752-183">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="69752-184">此功能可用于模拟设备上不准确的控制器跟踪，并确保交互能够很好地处理干扰输入。</span><span class="sxs-lookup"><span data-stu-id="69752-184">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="69752-185">手势</span><span class="sxs-lookup"><span data-stu-id="69752-185">Hand gestures</span></span>

<span data-ttu-id="69752-186">还可以模拟手势，例如收缩、抓取、抓取等。</span><span class="sxs-lookup"><span data-stu-id="69752-186">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="69752-187">使用左移/右控制器 **操作** 键或左移 (*空格\*\*键启用手动*) </span><span class="sxs-lookup"><span data-stu-id="69752-187">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="69752-188">操作时，按住鼠标按钮以执行手势。</span><span class="sxs-lookup"><span data-stu-id="69752-188">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="69752-189">每个鼠标按钮都可以进行映射，以使用鼠标手势的左 */中/右* 手势设置将手部形状转换为不同的手势。</span><span class="sxs-lookup"><span data-stu-id="69752-189">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="69752-190">" *默认手势"* 是在未按下任何按钮时手的形状。</span><span class="sxs-lookup"><span data-stu-id="69752-190">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="69752-191">收缩 *手势* 是此时执行"选择"操作的唯一手势。</span><span class="sxs-lookup"><span data-stu-id="69752-191">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="69752-192">单手操作</span><span class="sxs-lookup"><span data-stu-id="69752-192">One-hand manipulation</span></span>

1. <span data-ttu-id="69752-193">按住左 **移/右控制器操作** 键 (*左移\*\*或空格键)*</span><span class="sxs-lookup"><span data-stu-id="69752-193">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="69752-194">指向对象</span><span class="sxs-lookup"><span data-stu-id="69752-194">Point at object</span></span>
3. <span data-ttu-id="69752-195">按住鼠标按钮进行收缩</span><span class="sxs-lookup"><span data-stu-id="69752-195">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="69752-196">使用鼠标移动对象</span><span class="sxs-lookup"><span data-stu-id="69752-196">Use your mouse to move the object</span></span>
5. <span data-ttu-id="69752-197">释放鼠标按钮以停止交互</span><span class="sxs-lookup"><span data-stu-id="69752-197">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="69752-198">双手操作</span><span class="sxs-lookup"><span data-stu-id="69752-198">Two-hand manipulation</span></span>

<span data-ttu-id="69752-199">对于同时使用两只手操作对象，建议使用持久性手模式。</span><span class="sxs-lookup"><span data-stu-id="69752-199">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="69752-200">按切换键按 *"T/Y"* 按钮 (两手) 。</span><span class="sxs-lookup"><span data-stu-id="69752-200">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="69752-201">一次操作一次：</span><span class="sxs-lookup"><span data-stu-id="69752-201">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="69752-202">按住 **空间** 以控制右手</span><span class="sxs-lookup"><span data-stu-id="69752-202">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="69752-203">将指针移到要抓取对象的位置</span><span class="sxs-lookup"><span data-stu-id="69752-203">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="69752-204">按 **鼠标左键** 以激活 *挤压* 手势。</span><span class="sxs-lookup"><span data-stu-id="69752-204">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="69752-205">释放 **空间** 以停止控制右手。</span><span class="sxs-lookup"><span data-stu-id="69752-205">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="69752-206">手型会被冻结并锁定到 *挤压* 手势，因为它不再被操作。</span><span class="sxs-lookup"><span data-stu-id="69752-206">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="69752-207">用另一种方式重复此过程，在第二个位置抓取相同的对象。</span><span class="sxs-lookup"><span data-stu-id="69752-207">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="69752-208">由于这两个指针都抓取了同一个对象，因此可以移动其中的任何一个对象来执行双向操作。</span><span class="sxs-lookup"><span data-stu-id="69752-208">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="69752-209">GGV (注视、手势和语音) 交互</span><span class="sxs-lookup"><span data-stu-id="69752-209">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="69752-210">默认情况下，当场景中不存在任何已表述的手时，将在编辑器中启用 GGV 交互。</span><span class="sxs-lookup"><span data-stu-id="69752-210">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="69752-211">旋转相机，将注视光标指向种不可交互对象 (鼠标右键) </span><span class="sxs-lookup"><span data-stu-id="69752-211">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="69752-212">单击并按住 **鼠标左键** 以进行交互</span><span class="sxs-lookup"><span data-stu-id="69752-212">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="69752-213">再次旋转相机以操纵对象</span><span class="sxs-lookup"><span data-stu-id="69752-213">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="69752-214">你可以关闭此功能，方法是在输入模拟配置文件中切换 " *启用手动免费输入* " 选项。</span><span class="sxs-lookup"><span data-stu-id="69752-214">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="69752-215">此外，还可以使用模拟指针进行 GGV 交互</span><span class="sxs-lookup"><span data-stu-id="69752-215">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="69752-216">通过将 **手形模拟模式** 切换到 [输入模拟配置文件](#enabling-the-input-simulation-service)中的 *手势* 来启用 GGV 模拟</span><span class="sxs-lookup"><span data-stu-id="69752-216">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="69752-217">旋转相机，将注视光标指向种不可交互对象 (鼠标右键) </span><span class="sxs-lookup"><span data-stu-id="69752-217">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="69752-218">按住 **空间** 以控制右手</span><span class="sxs-lookup"><span data-stu-id="69752-218">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="69752-219">单击并按住 **鼠标左键** 以进行交互</span><span class="sxs-lookup"><span data-stu-id="69752-219">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="69752-220">使用鼠标移动对象</span><span class="sxs-lookup"><span data-stu-id="69752-220">Use your mouse to move the object</span></span>
1. <span data-ttu-id="69752-221">释放鼠标按钮以停止交互</span><span class="sxs-lookup"><span data-stu-id="69752-221">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="69752-222">引发传送事件</span><span class="sxs-lookup"><span data-stu-id="69752-222">Raising Teleport Events</span></span>

<span data-ttu-id="69752-223">若要在输入模拟中引发传送事件，请在输入模拟配置文件中配置手手势设置，使其中一个执行 **传送开始** 手势，而另一个执行 **传送结束** 手势。</span><span class="sxs-lookup"><span data-stu-id="69752-223">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="69752-224">传送 **开始** 手势将显示传送指针，而 **传送结束** gesure 将完成传送操作并移动用户。</span><span class="sxs-lookup"><span data-stu-id="69752-224">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="69752-225">生成的传送的 y 位置取决于沿 y 轴的摄像机置换。</span><span class="sxs-lookup"><span data-stu-id="69752-225">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="69752-226">在编辑器中，默认情况下此值为0，因此使用 **Q** 和 **E** 键将其调整为适当的高度。</span><span class="sxs-lookup"><span data-stu-id="69752-226">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![输入模拟传送设置](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="69752-228">运动控制器交互</span><span class="sxs-lookup"><span data-stu-id="69752-228">Motion controller interaction</span></span>

<span data-ttu-id="69752-229">模拟的运动控制器的操作方式与所表述的操作方式相同。</span><span class="sxs-lookup"><span data-stu-id="69752-229">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="69752-230">当触发器、抓取和菜单键分别映射到 *鼠标左键*、 *G* 和 *M* 键时，交互模型类似于清晰的手写内容交互。</span><span class="sxs-lookup"><span data-stu-id="69752-230">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="69752-231">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="69752-231">Eye tracking</span></span>

<span data-ttu-id="69752-232">可以通过检查 [输入模拟配置文件](#enabling-the-input-simulation-service)中的 "**模拟眼睛位置**" 选项来启用 [目视跟踪模拟](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor)。</span><span class="sxs-lookup"><span data-stu-id="69752-232">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="69752-233">这不应与 GGV 或运动控制器样式交互一起使用 (因此请确保将 **默认控制器模拟模式** 设置为 "带) 的 *手写* "。</span><span class="sxs-lookup"><span data-stu-id="69752-233">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="69752-234">"输入模拟工具" 窗口</span><span class="sxs-lookup"><span data-stu-id="69752-234">Input simulation tools window</span></span>

<span data-ttu-id="69752-235">从 **混合现实**  >  **Toolkit**  >  **实用程序**  >  **输入模拟** 菜单启用 "输入模拟工具" 窗口。</span><span class="sxs-lookup"><span data-stu-id="69752-235">Enable the input simulation tools window from the  **Mixed Reality** > **Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="69752-236">此窗口提供在播放模式下对输入模拟状态的访问。</span><span class="sxs-lookup"><span data-stu-id="69752-236">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons-optional"></a><span data-ttu-id="69752-237">视区按钮 (可选) </span><span class="sxs-lookup"><span data-stu-id="69752-237">Viewport buttons (optional)</span></span>

<span data-ttu-id="69752-238">可在输入模拟配置文件中的 " **指示器 prefab**" 下指定用于控制基本手布局的 prefab。</span><span class="sxs-lookup"><span data-stu-id="69752-238">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="69752-239">这是一个可选的实用工具，可以在 " [输入模拟工具" 窗口](#input-simulation-tools-window)中访问相同的功能。</span><span class="sxs-lookup"><span data-stu-id="69752-239">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="69752-240">默认情况下，视区指示器处于禁用状态，因为它们目前可能会干扰 Unity UI 交互。</span><span class="sxs-lookup"><span data-stu-id="69752-240">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="69752-241">请参阅问题 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)。</span><span class="sxs-lookup"><span data-stu-id="69752-241">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="69752-242">若要启用，请将 InputSimulationIndicators prefab 添加到 **指示器 prefab**。</span><span class="sxs-lookup"><span data-stu-id="69752-242">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="69752-243">手动图标显示模拟手的状态：</span><span class="sxs-lookup"><span data-stu-id="69752-243">Hand icons show the state of the simulated hands:</span></span>

* ![未跟踪的手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="69752-245&quot;>不跟踪。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;69752-245&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;69752-246&quot;>单击 &quot;启用&quot;。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;69752-246&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;69752-247&quot;>![跟踪的手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;跟踪的手形图标") 只跟踪该手型，而不是由用户控制。</span><span class="sxs-lookup"><span data-stu-id="69752-247">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="69752-248">单击以隐藏手。</span><span class="sxs-lookup"><span data-stu-id="69752-248">Click to hide the hand.</span></span>
* <span data-ttu-id="69752-249">![受控手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "受控手形图标") 由用户跟踪和控制。</span><span class="sxs-lookup"><span data-stu-id="69752-249">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="69752-250">单击以隐藏手。</span><span class="sxs-lookup"><span data-stu-id="69752-250">Click to hide the hand.</span></span>
* <span data-ttu-id="69752-251">![重置手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "重置手形图标") 单击可将手形重置为默认位置。</span><span class="sxs-lookup"><span data-stu-id="69752-251">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>


## <a name="see-also"></a><span data-ttu-id="69752-252">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69752-252">See also</span></span>

* <span data-ttu-id="69752-253">[输入系统配置文件](../input/input-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="69752-253">[Input System profile](../input/input-providers.md).</span></span>
