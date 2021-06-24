---
title: 输入模拟服务
description: 有关 MRTK 中的输入模拟服务的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 5420f3f2d20d07585007a58f5cf70d8e2027efc6
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588842"
---
# <a name="input-simulation-service"></a><span data-ttu-id="88ed1-104">输入模拟服务</span><span class="sxs-lookup"><span data-stu-id="88ed1-104">Input simulation service</span></span>

![MRTK 输入模拟](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

<span data-ttu-id="88ed1-106">借助 MRTK 的输入模拟，你可以在 Unity 编辑器中测试各种类型的交互，而无需生成并部署到设备。</span><span class="sxs-lookup"><span data-stu-id="88ed1-106">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="88ed1-107">这使你可以在设计和开发过程中快速循环你的想法。</span><span class="sxs-lookup"><span data-stu-id="88ed1-107">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="88ed1-108">使用键盘和鼠标组合来控制模拟输入。</span><span class="sxs-lookup"><span data-stu-id="88ed1-108">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="88ed1-109">输入模拟服务模拟可能在 Unity 编辑器中不可用的设备和平台的行为。</span><span class="sxs-lookup"><span data-stu-id="88ed1-109">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="88ed1-110">示例包括：</span><span class="sxs-lookup"><span data-stu-id="88ed1-110">Examples include:</span></span>

* <span data-ttu-id="88ed1-111">HoloLens 或 VR 设备标题跟踪</span><span class="sxs-lookup"><span data-stu-id="88ed1-111">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="88ed1-112">HoloLens 手势</span><span class="sxs-lookup"><span data-stu-id="88ed1-112">HoloLens hand gestures</span></span>
* <span data-ttu-id="88ed1-113">HoloLens 2 已表述的手动跟踪</span><span class="sxs-lookup"><span data-stu-id="88ed1-113">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="88ed1-114">HoloLens 2 目视跟踪</span><span class="sxs-lookup"><span data-stu-id="88ed1-114">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="88ed1-115">VR 设备控制器</span><span class="sxs-lookup"><span data-stu-id="88ed1-115">VR device controllers</span></span>

> [!WARNING]
> <span data-ttu-id="88ed1-116">当使用 Unity 的 XR 全息模拟 > 模拟模式 = "在编辑器中模拟" 时，此操作不起作用。</span><span class="sxs-lookup"><span data-stu-id="88ed1-116">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="88ed1-117">Unity 的编辑器内模拟将从 MRTK 的输入模拟中控制。</span><span class="sxs-lookup"><span data-stu-id="88ed1-117">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="88ed1-118">若要使用 MRTK 输入模拟服务，需要将 XR 全息仿真设置为仿真模式 = *"无"*</span><span class="sxs-lookup"><span data-stu-id="88ed1-118">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="how-to-use-mrtk-input-simulation"></a><span data-ttu-id="88ed1-119">如何使用 MRTK 输入模拟</span><span class="sxs-lookup"><span data-stu-id="88ed1-119">How to use MRTK Input simulation</span></span> 

<span data-ttu-id="88ed1-120">默认情况下，在 MRTK 附带的配置文件中启用输入模拟。</span><span class="sxs-lookup"><span data-stu-id="88ed1-120">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span> <span data-ttu-id="88ed1-121">只需单击 " **播放** " 按钮即可运行具有输入模拟支持的场景。</span><span class="sxs-lookup"><span data-stu-id="88ed1-121">You can simply click **Play** button to run the scene with input simulation support.</span></span>

* <span data-ttu-id="88ed1-122">按 **W、A、S、D、Q、E** 键移动相机。</span><span class="sxs-lookup"><span data-stu-id="88ed1-122">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="88ed1-123">按住鼠标 **右键** ，并移动鼠标以进行浏览。</span><span class="sxs-lookup"><span data-stu-id="88ed1-123">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="88ed1-124">若要启动模拟手势，请按 **空格键 (向右)** 或 **向左 Shift 键 (左手)**</span><span class="sxs-lookup"><span data-stu-id="88ed1-124">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="88ed1-125">若要在视图中保持模拟，请按 **T** 或 **Y** 键</span><span class="sxs-lookup"><span data-stu-id="88ed1-125">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="88ed1-126">要旋转模拟手，请按住 **Ctrl 键** 并移动鼠标</span><span class="sxs-lookup"><span data-stu-id="88ed1-126">To rotate simulated hands, press and hold **Ctrl key** and move mouse</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="88ed1-127">在编辑器输入模拟工作表中</span><span class="sxs-lookup"><span data-stu-id="88ed1-127">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="88ed1-128">在 HandInteractionExamples 场景中按 **左 Ctrl + H** ，以显示包含输入模拟控件的 "工作表"。</span><span class="sxs-lookup"><span data-stu-id="88ed1-128">Press **Left Ctrl + H** in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

> ![MRTK 输入模拟备忘单](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="88ed1-130">启用输入模拟服务</span><span class="sxs-lookup"><span data-stu-id="88ed1-130">Enabling the input simulation service</span></span>

<span data-ttu-id="88ed1-131">在输入系统数据提供程序配置下，可通过以下方式配置输入模拟服务。</span><span class="sxs-lookup"><span data-stu-id="88ed1-131">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="88ed1-132">**类型** 必须是 *MixedReality > InputSimulationService*。</span><span class="sxs-lookup"><span data-stu-id="88ed1-132">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="88ed1-133">默认情况下，**支持的平台 ()** 包含所有 *编辑器* 平台，因为该服务使用键盘和鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="88ed1-133">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="88ed1-134">可以通过将 **支持的平台 (s)** 属性更改为包含所需的目标，在其他平台终结点（如独立）上使用输入模拟服务。</span><span class="sxs-lookup"><span data-stu-id="88ed1-134">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a><span data-ttu-id="88ed1-135">照相机控件</span><span class="sxs-lookup"><span data-stu-id="88ed1-135">Camera control</span></span>

<span data-ttu-id="88ed1-136">头移动可由输入模拟服务模拟。</span><span class="sxs-lookup"><span data-stu-id="88ed1-136">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="88ed1-137">旋转相机</span><span class="sxs-lookup"><span data-stu-id="88ed1-137">Rotating the camera</span></span>

1. <span data-ttu-id="88ed1-138">将鼠标悬停在视区编辑器窗口之上。</span><span class="sxs-lookup"><span data-stu-id="88ed1-138">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="88ed1-139">*如果按钮按下不起作用，则您可能需要单击窗口以使其输入焦点。*</span><span class="sxs-lookup"><span data-stu-id="88ed1-139">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="88ed1-140">按住鼠标的 " **查找" 按钮** (默认：鼠标右键) 。</span><span class="sxs-lookup"><span data-stu-id="88ed1-140">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="88ed1-141">在视区窗口中移动鼠标，旋转相机。</span><span class="sxs-lookup"><span data-stu-id="88ed1-141">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="88ed1-142">使用滚轮按视图方向滚动相机。</span><span class="sxs-lookup"><span data-stu-id="88ed1-142">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="88ed1-143">可以通过更改输入模拟配置文件中的 " **鼠标外观速度** " 设置来配置照相机旋转速度。</span><span class="sxs-lookup"><span data-stu-id="88ed1-143">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="88ed1-144">另外，还可以使用 "**横向**" / **外观垂直** 轴旋转相机 (默认：游戏控制器右操纵杆) 。</span><span class="sxs-lookup"><span data-stu-id="88ed1-144">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="88ed1-145">移动摄像头</span><span class="sxs-lookup"><span data-stu-id="88ed1-145">Moving the camera</span></span>

<span data-ttu-id="88ed1-146">使用 "**移动水平** / **移动垂直** 轴" (默认值： WASD 键或游戏控制器左操纵杆) 移动相机。</span><span class="sxs-lookup"><span data-stu-id="88ed1-146">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="88ed1-147">还可以在 "工具" 窗口中显式设置相机位置和旋转角度。</span><span class="sxs-lookup"><span data-stu-id="88ed1-147">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="88ed1-148">可以使用 " **重置** " 按钮将相机重置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="88ed1-148">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="88ed1-149">控制器模拟</span><span class="sxs-lookup"><span data-stu-id="88ed1-149">Controller simulation</span></span>

<span data-ttu-id="88ed1-150">输入模拟支持 (模拟控制器设备，如运动控制器和) 。</span><span class="sxs-lookup"><span data-stu-id="88ed1-150">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="88ed1-151">这些虚拟控制器可以与支持常规控制器的任何对象（如按钮或 grabbable 对象）进行交互。</span><span class="sxs-lookup"><span data-stu-id="88ed1-151">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="88ed1-152">控制器模拟模式</span><span class="sxs-lookup"><span data-stu-id="88ed1-152">Controller simulation mode</span></span>

<span data-ttu-id="88ed1-153">在 " [输入模拟工具" 窗口](#input-simulation-tools-window) 中， **默认的控制器模拟模式** 设置在三个不同的输入模型之间切换。</span><span class="sxs-lookup"><span data-stu-id="88ed1-153">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="88ed1-154">此默认模式也可以在输入模拟配置文件中进行设置。</span><span class="sxs-lookup"><span data-stu-id="88ed1-154">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="88ed1-155">明确 *说明：模拟* 带有联合位置数据的一个完全表述的手形设备。</span><span class="sxs-lookup"><span data-stu-id="88ed1-155">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="88ed1-156">模拟 HoloLens 2 交互模型。</span><span class="sxs-lookup"><span data-stu-id="88ed1-156">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="88ed1-157">可以在此模式下模拟基于手或使用触摸的精确定位的交互。</span><span class="sxs-lookup"><span data-stu-id="88ed1-157">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="88ed1-158">*手势：通过* 使用 "分流" 和 "基本" 手势模拟简化的手模型。</span><span class="sxs-lookup"><span data-stu-id="88ed1-158">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="88ed1-159">模拟 [HoloLens 交互模型](/windows/mixed-reality/gestures)。</span><span class="sxs-lookup"><span data-stu-id="88ed1-159">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="88ed1-160">使用注视指针控制焦点。</span><span class="sxs-lookup"><span data-stu-id="88ed1-160">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="88ed1-161">*Air 攻丝* 笔势用于与按钮交互。</span><span class="sxs-lookup"><span data-stu-id="88ed1-161">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="88ed1-162">*运动控制器*：模拟与 VR 耳机一起使用的运动控制器，其工作方式类似于与清晰的手势交互。</span><span class="sxs-lookup"><span data-stu-id="88ed1-162">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="88ed1-163">模拟 VR 耳机与控制器交互模型。</span><span class="sxs-lookup"><span data-stu-id="88ed1-163">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="88ed1-164">通过键盘和鼠标输入模拟触发器、抓取和菜单键。</span><span class="sxs-lookup"><span data-stu-id="88ed1-164">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="88ed1-165">模拟控制器移动</span><span class="sxs-lookup"><span data-stu-id="88ed1-165">Simulating controller movement</span></span>

<span data-ttu-id="88ed1-166">按住 **左/右控制器操作键** (默认值：左侧控制器的 *左移* 和右控制器的 *空间*) 以获得控制器的控制。</span><span class="sxs-lookup"><span data-stu-id="88ed1-166">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="88ed1-167">按下操作键时，控制器将显示在视区中。</span><span class="sxs-lookup"><span data-stu-id="88ed1-167">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="88ed1-168">释放操作密钥后，控制器将在短 **控制器隐藏超时** 后消失。</span><span class="sxs-lookup"><span data-stu-id="88ed1-168">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="88ed1-169">控制器可以在 " [输入模拟工具" 窗口](#input-simulation-tools-window) 中的相机之间切换，也可以通过按 " **切换左/右" 控制器键** (默认值 *： "* 左" 和 " *Y* " 右) 。</span><span class="sxs-lookup"><span data-stu-id="88ed1-169">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="88ed1-170">再次按切换键，以再次隐藏控制器。</span><span class="sxs-lookup"><span data-stu-id="88ed1-170">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="88ed1-171">若要操作控制器，需要保留 **左/右控制器操作密钥** 。</span><span class="sxs-lookup"><span data-stu-id="88ed1-171">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="88ed1-172">双击 **左/右控制器操作键** 还可以开启/关闭控制器。</span><span class="sxs-lookup"><span data-stu-id="88ed1-172">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="88ed1-173">鼠标移动将在视图平面移动控制器。</span><span class="sxs-lookup"><span data-stu-id="88ed1-173">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="88ed1-174">可以使用 **鼠标滚轮** 将控制器进一步或更接近相机。</span><span class="sxs-lookup"><span data-stu-id="88ed1-174">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="88ed1-175">若要使用鼠标旋转控制器，请将 **左/右控制器操作键** (*左移* 或 *空间*) *，* **控制器旋转按钮** (默认：左按 *Ctrl* 按钮) ，然后移动鼠标来旋转控制器。</span><span class="sxs-lookup"><span data-stu-id="88ed1-175">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="88ed1-176">可以通过更改输入模拟配置文件中的 " **鼠标控制器旋转速度** " 设置来配置控制器旋转速度。</span><span class="sxs-lookup"><span data-stu-id="88ed1-176">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="88ed1-177">也可以在 " [输入模拟工具" 窗口](#input-simulation-tools-window)中更改所有位置，包括将指针重置为默认值。</span><span class="sxs-lookup"><span data-stu-id="88ed1-177">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="88ed1-178">其他配置文件设置</span><span class="sxs-lookup"><span data-stu-id="88ed1-178">Additional profile settings</span></span>

* <span data-ttu-id="88ed1-179">**控制器深度乘数** 控制鼠标滚轮深度移动的灵敏度。</span><span class="sxs-lookup"><span data-stu-id="88ed1-179">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="88ed1-180">数字越大，控制器缩放就会提高。</span><span class="sxs-lookup"><span data-stu-id="88ed1-180">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="88ed1-181">**默认控制器距离** 是控制器与照相机的初始距离。</span><span class="sxs-lookup"><span data-stu-id="88ed1-181">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="88ed1-182">单击 " **重置** " 按钮控制器也会将控制器置于此距离。</span><span class="sxs-lookup"><span data-stu-id="88ed1-182">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="88ed1-183">**控制器抖动量** 将随机运动添加到控制器。</span><span class="sxs-lookup"><span data-stu-id="88ed1-183">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="88ed1-184">此功能可用于在设备上模拟不准确的控制器跟踪，并确保交互工作非常适合于输入。</span><span class="sxs-lookup"><span data-stu-id="88ed1-184">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="88ed1-185">手势</span><span class="sxs-lookup"><span data-stu-id="88ed1-185">Hand gestures</span></span>

<span data-ttu-id="88ed1-186">也可以模拟手写手势，如收缩、抓取、闲逛等。</span><span class="sxs-lookup"><span data-stu-id="88ed1-186">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="88ed1-187">使用 **左/右控制器操作键** 启用手动控制 (*左移* 或 *空间*) </span><span class="sxs-lookup"><span data-stu-id="88ed1-187">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="88ed1-188">进行操作时，按住鼠标按钮以执行手动手势。</span><span class="sxs-lookup"><span data-stu-id="88ed1-188">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="88ed1-189">每个鼠标按钮都可以映射，使用 *鼠标左键或中键笔势* 设置将手形形状转换为不同的笔势。</span><span class="sxs-lookup"><span data-stu-id="88ed1-189">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="88ed1-190">当没有按下任何按钮时， *默认的手势* 将为手形形状。</span><span class="sxs-lookup"><span data-stu-id="88ed1-190">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="88ed1-191">此时，只会执行 "选择" 操作的 "选中 *" 的笔势* 。</span><span class="sxs-lookup"><span data-stu-id="88ed1-191">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="88ed1-192">一次操作</span><span class="sxs-lookup"><span data-stu-id="88ed1-192">One-hand manipulation</span></span>

1. <span data-ttu-id="88ed1-193">按住左 **/右控制器操作键** (*左移* 或 *空间*) </span><span class="sxs-lookup"><span data-stu-id="88ed1-193">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="88ed1-194">指向对象</span><span class="sxs-lookup"><span data-stu-id="88ed1-194">Point at object</span></span>
3. <span data-ttu-id="88ed1-195">按住鼠标按钮进行挤压</span><span class="sxs-lookup"><span data-stu-id="88ed1-195">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="88ed1-196">使用鼠标移动对象</span><span class="sxs-lookup"><span data-stu-id="88ed1-196">Use your mouse to move the object</span></span>
5. <span data-ttu-id="88ed1-197">释放鼠标按钮以停止交互</span><span class="sxs-lookup"><span data-stu-id="88ed1-197">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="88ed1-198">双重操作</span><span class="sxs-lookup"><span data-stu-id="88ed1-198">Two-hand manipulation</span></span>

<span data-ttu-id="88ed1-199">若要同时处理两个对象，建议使用永久性的手动模式。</span><span class="sxs-lookup"><span data-stu-id="88ed1-199">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="88ed1-200">按下切换键 (*T/Y*) 切换。</span><span class="sxs-lookup"><span data-stu-id="88ed1-200">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="88ed1-201">一次操作一只手：</span><span class="sxs-lookup"><span data-stu-id="88ed1-201">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="88ed1-202">按住 **空格** 可控制右侧</span><span class="sxs-lookup"><span data-stu-id="88ed1-202">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="88ed1-203">将手移到要抓取对象的地方</span><span class="sxs-lookup"><span data-stu-id="88ed1-203">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="88ed1-204">按 \**鼠标左键\*\*\*激活收缩手势*。</span><span class="sxs-lookup"><span data-stu-id="88ed1-204">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="88ed1-205">释放 **空间** 以停止控制右侧。</span><span class="sxs-lookup"><span data-stu-id="88ed1-205">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="88ed1-206">手将就地冻结并锁定到收缩手势中，因为它不再被操作。</span><span class="sxs-lookup"><span data-stu-id="88ed1-206">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="88ed1-207">另一方面重复此过程，在另一个位置抓取同一个对象。</span><span class="sxs-lookup"><span data-stu-id="88ed1-207">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="88ed1-208">现在，两只手都抓取同一个对象，可以移动其中一个，以执行两手操作。</span><span class="sxs-lookup"><span data-stu-id="88ed1-208">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="88ed1-209">GGV (凝视、手势和语音) 交互</span><span class="sxs-lookup"><span data-stu-id="88ed1-209">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="88ed1-210">默认情况下，GGV 交互在编辑器中启用，而场景中没有可表达的手。</span><span class="sxs-lookup"><span data-stu-id="88ed1-210">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="88ed1-211">旋转相机，将凝视光标指向可交互 (鼠标按钮) </span><span class="sxs-lookup"><span data-stu-id="88ed1-211">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="88ed1-212">单击并按住 **鼠标左键** 进行交互</span><span class="sxs-lookup"><span data-stu-id="88ed1-212">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="88ed1-213">再次旋转相机以操作对象</span><span class="sxs-lookup"><span data-stu-id="88ed1-213">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="88ed1-214">可以通过在输入模拟配置文件中切换"启用 *无手输入"* 选项来关闭此选项。</span><span class="sxs-lookup"><span data-stu-id="88ed1-214">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="88ed1-215">此外，可以使用模拟手进行 GGV 交互</span><span class="sxs-lookup"><span data-stu-id="88ed1-215">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="88ed1-216">通过切换输入模拟配置文件 \**中的手势模拟模式\*\*\*来* 启用 GGV [模拟](#enabling-the-input-simulation-service)</span><span class="sxs-lookup"><span data-stu-id="88ed1-216">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="88ed1-217">旋转相机，将凝视光标指向可交互 (鼠标按钮) </span><span class="sxs-lookup"><span data-stu-id="88ed1-217">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="88ed1-218">按住 **空格** 可控制右侧</span><span class="sxs-lookup"><span data-stu-id="88ed1-218">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="88ed1-219">单击并按住 **鼠标左键** 进行交互</span><span class="sxs-lookup"><span data-stu-id="88ed1-219">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="88ed1-220">使用鼠标移动对象</span><span class="sxs-lookup"><span data-stu-id="88ed1-220">Use your mouse to move the object</span></span>
1. <span data-ttu-id="88ed1-221">释放鼠标按钮以停止交互</span><span class="sxs-lookup"><span data-stu-id="88ed1-221">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="88ed1-222">引发 Teleport 事件</span><span class="sxs-lookup"><span data-stu-id="88ed1-222">Raising Teleport Events</span></span>

<span data-ttu-id="88ed1-223">若要在输入模拟中引发远程端口事件，请配置输入模拟配置文件中的手势设置，以便一个执行 **远程** 端口启动手势，而另一个执行 **远程端口结束** 手势。</span><span class="sxs-lookup"><span data-stu-id="88ed1-223">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="88ed1-224">**Teleport 开始** 手势将启动 Teleport 指针，而 **Teleport End** gesure 将完成远程端口操作并移动用户。</span><span class="sxs-lookup"><span data-stu-id="88ed1-224">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="88ed1-225">生成的远程端口的 y 位置取决于相机沿 y 轴的位移。</span><span class="sxs-lookup"><span data-stu-id="88ed1-225">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="88ed1-226">在编辑器中，默认为 0，因此请使用 **Q** 和 **E** 键调整到适当的高度。</span><span class="sxs-lookup"><span data-stu-id="88ed1-226">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![输入模拟远程端口设置](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="88ed1-228">运动控制器交互</span><span class="sxs-lookup"><span data-stu-id="88ed1-228">Motion controller interaction</span></span>

<span data-ttu-id="88ed1-229">模拟运动控制器的操控方式与定手操作方式相同。</span><span class="sxs-lookup"><span data-stu-id="88ed1-229">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="88ed1-230">交互模型类似于手部远部交互，而触发器、抓取键和菜单键分别映射到 *鼠标* 左键 *、G* 键 *和 M* 键。</span><span class="sxs-lookup"><span data-stu-id="88ed1-230">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="88ed1-231">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="88ed1-231">Eye tracking</span></span>

<span data-ttu-id="88ed1-232">[可以通过检查](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) 输入模拟配置文件 中的 **"模拟眼睛位置** "选项来 [启用眼动跟踪模拟](#enabling-the-input-simulation-service)。</span><span class="sxs-lookup"><span data-stu-id="88ed1-232">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="88ed1-233">这不应与 GGV 或运动控制器样式交互 (因此请确保将"默认控制器模拟模式"设置为"定点手部) 。</span><span class="sxs-lookup"><span data-stu-id="88ed1-233">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="88ed1-234">输入模拟工具窗口</span><span class="sxs-lookup"><span data-stu-id="88ed1-234">Input simulation tools window</span></span>

<span data-ttu-id="88ed1-235">从"混合现实工具包实用工具""输入模拟"菜单中  >    >    >  **启用输入模拟工具** 窗口。</span><span class="sxs-lookup"><span data-stu-id="88ed1-235">Enable the input simulation tools window from the  **Mixed Reality** > **Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="88ed1-236">此窗口提供对播放模式期间输入模拟状态的访问。</span><span class="sxs-lookup"><span data-stu-id="88ed1-236">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons-optional"></a><span data-ttu-id="88ed1-237">视区按钮 (可选) </span><span class="sxs-lookup"><span data-stu-id="88ed1-237">Viewport buttons (optional)</span></span>

<span data-ttu-id="88ed1-238">可在"指示器预制"下的输入模拟配置文件中指定用于控制基本手部放置的编辑器中按钮 **的预制。**</span><span class="sxs-lookup"><span data-stu-id="88ed1-238">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="88ed1-239">这是一个可选实用工具，可以在输入模拟工具窗口中访问 [相同的功能](#input-simulation-tools-window)。</span><span class="sxs-lookup"><span data-stu-id="88ed1-239">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="88ed1-240">视区指示器默认处于禁用状态，因为它们当前有时会干扰 Unity UI 交互。</span><span class="sxs-lookup"><span data-stu-id="88ed1-240">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="88ed1-241">请参阅问题[#6106。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)</span><span class="sxs-lookup"><span data-stu-id="88ed1-241">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="88ed1-242">若要启用，将 InputSimulationIndicators 预制添加到 **指示器预制。**</span><span class="sxs-lookup"><span data-stu-id="88ed1-242">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="88ed1-243">手部图标显示模拟手的状态：</span><span class="sxs-lookup"><span data-stu-id="88ed1-243">Hand icons show the state of the simulated hands:</span></span>

* ![未跟踪手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="88ed1-245&quot;>手未跟踪。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;88ed1-245&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;88ed1-246&quot;>单击以启用手部。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;88ed1-246&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;88ed1-247&quot;>![跟踪手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;跟踪手形图标") 手被跟踪，但不由用户控制。</span><span class="sxs-lookup"><span data-stu-id="88ed1-247">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="88ed1-248">单击可隐藏手部。</span><span class="sxs-lookup"><span data-stu-id="88ed1-248">Click to hide the hand.</span></span>
* <span data-ttu-id="88ed1-249">![受控手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "受控手形图标") 手由用户跟踪和控制。</span><span class="sxs-lookup"><span data-stu-id="88ed1-249">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="88ed1-250">单击可隐藏手部。</span><span class="sxs-lookup"><span data-stu-id="88ed1-250">Click to hide the hand.</span></span>
* <span data-ttu-id="88ed1-251">![重置手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "重置手形图标") 单击以将手重置为默认位置。</span><span class="sxs-lookup"><span data-stu-id="88ed1-251">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>


## <a name="see-also"></a><span data-ttu-id="88ed1-252">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88ed1-252">See also</span></span>

* <span data-ttu-id="88ed1-253">[输入系统配置文件](../input/input-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="88ed1-253">[Input System profile](../input/input-providers.md).</span></span>