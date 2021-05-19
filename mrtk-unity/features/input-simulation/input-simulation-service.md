---
title: 输入模拟服务
description: 有关 MRTK 中的输入模拟服务的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 81e7dcab7e0f349d05521f93d75bba6927761fd1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145092"
---
# <a name="input-simulation-service"></a><span data-ttu-id="48c62-104">输入模拟服务</span><span class="sxs-lookup"><span data-stu-id="48c62-104">Input simulation service</span></span>

<span data-ttu-id="48c62-105">输入模拟服务模拟 Unity 编辑器中可能不可用的设备和平台的行为。</span><span class="sxs-lookup"><span data-stu-id="48c62-105">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="48c62-106">示例包括：</span><span class="sxs-lookup"><span data-stu-id="48c62-106">Examples include:</span></span>

* <span data-ttu-id="48c62-107">HoloLens 或 VR 设备头跟踪</span><span class="sxs-lookup"><span data-stu-id="48c62-107">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="48c62-108">HoloLens 手势</span><span class="sxs-lookup"><span data-stu-id="48c62-108">HoloLens hand gestures</span></span>
* <span data-ttu-id="48c62-109">HoloLens 2手部跟踪</span><span class="sxs-lookup"><span data-stu-id="48c62-109">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="48c62-110">HoloLens 2眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="48c62-110">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="48c62-111">VR 设备控制器</span><span class="sxs-lookup"><span data-stu-id="48c62-111">VR device controllers</span></span>

<span data-ttu-id="48c62-112">用户可以在运行时使用传统键盘和鼠标组合来控制模拟设备。</span><span class="sxs-lookup"><span data-stu-id="48c62-112">Users can use a conventional keyboard and mouse combination to control simulated devices at runtime.</span></span> <span data-ttu-id="48c62-113">此方法允许在 Unity 编辑器中测试交互，而无需先部署到设备。</span><span class="sxs-lookup"><span data-stu-id="48c62-113">This approach allows testing of interactions in the Unity editor without first deploying to a device.</span></span>

> [!WARNING]
> <span data-ttu-id="48c62-114">在仿真模式下使用 Unity 的 XR 全息仿真 = "在编辑器中>模拟时，这不起作用。</span><span class="sxs-lookup"><span data-stu-id="48c62-114">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="48c62-115">Unity 的编辑器内模拟将控制 MRTK 的输入模拟。</span><span class="sxs-lookup"><span data-stu-id="48c62-115">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="48c62-116">若要使用 MRTK 输入模拟服务，需要将 XR 全息仿真设置为仿真模式 = *"None"*</span><span class="sxs-lookup"><span data-stu-id="48c62-116">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="48c62-117">启用输入模拟服务</span><span class="sxs-lookup"><span data-stu-id="48c62-117">Enabling the input simulation service</span></span>

<span data-ttu-id="48c62-118">在 MRTK 的配置文件中，默认启用输入模拟。</span><span class="sxs-lookup"><span data-stu-id="48c62-118">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span>

<span data-ttu-id="48c62-119">在"输入系统数据提供程序"配置下，可以使用以下内容配置输入模拟服务。</span><span class="sxs-lookup"><span data-stu-id="48c62-119">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="48c62-120">**类型** 必须是 *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*。</span><span class="sxs-lookup"><span data-stu-id="48c62-120">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="48c62-121">**受支持的平台 (默认)** 包括所有 *编辑器* 平台，因为服务使用键盘和鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="48c62-121">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="48c62-122">输入模拟服务可以在其他平台终结点（例如独立）上使用， (支持的平台) **属性以** 包含所需的目标。</span><span class="sxs-lookup"><span data-stu-id="48c62-122">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <span data-ttu-id="48c62-123">![输入模拟支持的平台](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span><span class="sxs-lookup"><span data-stu-id="48c62-123">![Input Simulation Supported Platforms](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="48c62-124">"输入模拟工具" 窗口</span><span class="sxs-lookup"><span data-stu-id="48c62-124">Input simulation tools window</span></span>

<span data-ttu-id="48c62-125">从 **混合现实工具包**  >  **实用工具**  >  **输入模拟** 菜单启用 "输入模拟工具" 窗口。</span><span class="sxs-lookup"><span data-stu-id="48c62-125">Enable the input simulation tools window from the  **Mixed Reality Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="48c62-126">此窗口提供在播放模式下对输入模拟状态的访问。</span><span class="sxs-lookup"><span data-stu-id="48c62-126">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons"></a><span data-ttu-id="48c62-127">视区按钮</span><span class="sxs-lookup"><span data-stu-id="48c62-127">Viewport buttons</span></span>

<span data-ttu-id="48c62-128">可在输入模拟配置文件中的 " **指示器 prefab**" 下指定用于控制基本手布局的 prefab。</span><span class="sxs-lookup"><span data-stu-id="48c62-128">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="48c62-129">这是一个可选的实用工具，可以在 " [输入模拟工具" 窗口](#input-simulation-tools-window)中访问相同的功能。</span><span class="sxs-lookup"><span data-stu-id="48c62-129">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="48c62-130">默认情况下，视区指示器处于禁用状态，因为它们目前可能会干扰 Unity UI 交互。</span><span class="sxs-lookup"><span data-stu-id="48c62-130">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="48c62-131">请参阅问题 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)。</span><span class="sxs-lookup"><span data-stu-id="48c62-131">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="48c62-132">若要启用，请将 InputSimulationIndicators prefab 添加到 **指示器 prefab**。</span><span class="sxs-lookup"><span data-stu-id="48c62-132">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="48c62-133">手动图标显示模拟手的状态：</span><span class="sxs-lookup"><span data-stu-id="48c62-133">Hand icons show the state of the simulated hands:</span></span>

* ![未跟踪的手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="48c62-135&quot;>不跟踪。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;48c62-135&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;48c62-136&quot;>单击 &quot;启用&quot;。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;48c62-136&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;48c62-137&quot;>![跟踪的手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;跟踪的手形图标") 只跟踪该手型，而不是由用户控制。</span><span class="sxs-lookup"><span data-stu-id="48c62-137">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="48c62-138">单击以隐藏手。</span><span class="sxs-lookup"><span data-stu-id="48c62-138">Click to hide the hand.</span></span>
* <span data-ttu-id="48c62-139">![受控手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "受控手形图标") 由用户跟踪和控制。</span><span class="sxs-lookup"><span data-stu-id="48c62-139">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="48c62-140">单击以隐藏手。</span><span class="sxs-lookup"><span data-stu-id="48c62-140">Click to hide the hand.</span></span>
* <span data-ttu-id="48c62-141">![重置手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "重置手形图标") 单击可将手形重置为默认位置。</span><span class="sxs-lookup"><span data-stu-id="48c62-141">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="48c62-142">在编辑器输入模拟工作表中</span><span class="sxs-lookup"><span data-stu-id="48c62-142">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="48c62-143">在 HandInteractionExamples 场景中按左 Ctrl + H，以显示包含输入模拟控件的 "工作表"。</span><span class="sxs-lookup"><span data-stu-id="48c62-143">Press Left Ctrl + H in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

![输入模拟备忘单](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

## <a name="camera-control"></a><span data-ttu-id="48c62-145">照相机控件</span><span class="sxs-lookup"><span data-stu-id="48c62-145">Camera control</span></span>

<span data-ttu-id="48c62-146">头移动可由输入模拟服务模拟。</span><span class="sxs-lookup"><span data-stu-id="48c62-146">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="48c62-147">旋转相机</span><span class="sxs-lookup"><span data-stu-id="48c62-147">Rotating the camera</span></span>

1. <span data-ttu-id="48c62-148">将鼠标悬停在视区编辑器窗口之上。</span><span class="sxs-lookup"><span data-stu-id="48c62-148">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="48c62-149">*如果按钮按下不起作用，则您可能需要单击窗口以使其输入焦点。*</span><span class="sxs-lookup"><span data-stu-id="48c62-149">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="48c62-150">按住鼠标的 " **查找" 按钮** (默认：鼠标右键) 。</span><span class="sxs-lookup"><span data-stu-id="48c62-150">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="48c62-151">在视区窗口中移动鼠标，旋转相机。</span><span class="sxs-lookup"><span data-stu-id="48c62-151">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="48c62-152">使用滚轮按视图方向滚动相机。</span><span class="sxs-lookup"><span data-stu-id="48c62-152">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="48c62-153">可以通过更改输入模拟配置文件中的 " **鼠标外观速度** " 设置来配置照相机旋转速度。</span><span class="sxs-lookup"><span data-stu-id="48c62-153">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="48c62-154">另外，还可以使用 "**横向**" / **外观垂直** 轴旋转相机 (默认：游戏控制器右操纵杆) 。</span><span class="sxs-lookup"><span data-stu-id="48c62-154">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="48c62-155">移动摄像头</span><span class="sxs-lookup"><span data-stu-id="48c62-155">Moving the camera</span></span>

<span data-ttu-id="48c62-156">使用 "**移动水平** / **移动垂直** 轴" (默认值： WASD 键或游戏控制器左操纵杆) 移动相机。</span><span class="sxs-lookup"><span data-stu-id="48c62-156">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="48c62-157">还可以在 "工具" 窗口中显式设置相机位置和旋转角度。</span><span class="sxs-lookup"><span data-stu-id="48c62-157">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="48c62-158">可以使用 " **重置** " 按钮将相机重置为其默认值。</span><span class="sxs-lookup"><span data-stu-id="48c62-158">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="48c62-159">控制器模拟</span><span class="sxs-lookup"><span data-stu-id="48c62-159">Controller simulation</span></span>

<span data-ttu-id="48c62-160">输入模拟支持 (模拟控制器设备，如运动控制器和) 。</span><span class="sxs-lookup"><span data-stu-id="48c62-160">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="48c62-161">这些虚拟控制器可以与支持常规控制器的任何对象（如按钮或 grabbable 对象）进行交互。</span><span class="sxs-lookup"><span data-stu-id="48c62-161">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="48c62-162">控制器模拟模式</span><span class="sxs-lookup"><span data-stu-id="48c62-162">Controller simulation mode</span></span>

<span data-ttu-id="48c62-163">在 " [输入模拟工具" 窗口](#input-simulation-tools-window) 中， **默认的控制器模拟模式** 设置在三个不同的输入模型之间切换。</span><span class="sxs-lookup"><span data-stu-id="48c62-163">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="48c62-164">还可以在输入模拟配置文件中设置此默认模式。</span><span class="sxs-lookup"><span data-stu-id="48c62-164">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="48c62-165">*手部*：模拟具有联合位置数据的完全铰接式手部设备。</span><span class="sxs-lookup"><span data-stu-id="48c62-165">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="48c62-166">模拟HoloLens 2模型。</span><span class="sxs-lookup"><span data-stu-id="48c62-166">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="48c62-167">可以在此模式下模拟基于手部精确定位或使用触摸的交互。</span><span class="sxs-lookup"><span data-stu-id="48c62-167">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="48c62-168">*手势：* 使用敲击和基本手势模拟简化的手势模型。</span><span class="sxs-lookup"><span data-stu-id="48c62-168">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="48c62-169">模拟 [HoloLens 交互模型](/windows/mixed-reality/gestures)。</span><span class="sxs-lookup"><span data-stu-id="48c62-169">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="48c62-170">焦点使用凝视指针进行控制。</span><span class="sxs-lookup"><span data-stu-id="48c62-170">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="48c62-171">Air *Tap* 手势用于与按钮交互。</span><span class="sxs-lookup"><span data-stu-id="48c62-171">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="48c62-172">*运动控制器*：模拟与 VR 头戴显示设备一同使用的动作控制器，其工作方式类似于与手部远部交互。</span><span class="sxs-lookup"><span data-stu-id="48c62-172">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="48c62-173">使用控制器交互模型模拟 VR 头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="48c62-173">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="48c62-174">触发器、抓取键和菜单键通过键盘和鼠标输入进行模拟。</span><span class="sxs-lookup"><span data-stu-id="48c62-174">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="48c62-175">模拟控制器移动</span><span class="sxs-lookup"><span data-stu-id="48c62-175">Simulating controller movement</span></span>

<span data-ttu-id="48c62-176">按并按住"**左/** 右控制器操作 (键"：左控制器的左移和右控制器) 空格键以获得对任一控制器的控制。</span><span class="sxs-lookup"><span data-stu-id="48c62-176">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="48c62-177">按下操作键时，控制器将显示在视区中。</span><span class="sxs-lookup"><span data-stu-id="48c62-177">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="48c62-178">释放操作密钥后，控制器会在控制器隐藏超时 **短后消失**。</span><span class="sxs-lookup"><span data-stu-id="48c62-178">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="48c62-179">控制器可以相对于输入模拟工具窗口中的相机进行切换和冻结，[](#input-simulation-tools-window)或者按"左/右切换控制器 **键" (** 默认值 *：T* 表示左侧 *，Y* 表示右键) 。</span><span class="sxs-lookup"><span data-stu-id="48c62-179">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="48c62-180">再次按切换键以再次隐藏控制器。</span><span class="sxs-lookup"><span data-stu-id="48c62-180">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="48c62-181">若要操作控制器，需要保留 **左/** 右控制器操作键。</span><span class="sxs-lookup"><span data-stu-id="48c62-181">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="48c62-182">双击" **左/右控制器操作键"** 还可以打开/关闭控制器。</span><span class="sxs-lookup"><span data-stu-id="48c62-182">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="48c62-183">鼠标移动将在视图平面中移动控制器。</span><span class="sxs-lookup"><span data-stu-id="48c62-183">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="48c62-184">可以使用 **鼠标滚轮** 将控制器进一步或更接近相机。</span><span class="sxs-lookup"><span data-stu-id="48c62-184">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="48c62-185">若要使用鼠标旋转控制器，请将 **左/右控制器操作键** (*左移* 或 *空间*) *，* **控制器旋转按钮** (默认：左按 *Ctrl* 按钮) ，然后移动鼠标来旋转控制器。</span><span class="sxs-lookup"><span data-stu-id="48c62-185">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="48c62-186">可以通过更改输入模拟配置文件中的 " **鼠标控制器旋转速度** " 设置来配置控制器旋转速度。</span><span class="sxs-lookup"><span data-stu-id="48c62-186">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="48c62-187">也可以在 " [输入模拟工具" 窗口](#input-simulation-tools-window)中更改所有位置，包括将指针重置为默认值。</span><span class="sxs-lookup"><span data-stu-id="48c62-187">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="48c62-188">其他配置文件设置</span><span class="sxs-lookup"><span data-stu-id="48c62-188">Additional profile settings</span></span>

* <span data-ttu-id="48c62-189">**控制器深度乘数** 控制鼠标滚轮深度移动的灵敏度。</span><span class="sxs-lookup"><span data-stu-id="48c62-189">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="48c62-190">数字越大，控制器缩放就会提高。</span><span class="sxs-lookup"><span data-stu-id="48c62-190">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="48c62-191">**默认控制器距离** 是控制器与照相机的初始距离。</span><span class="sxs-lookup"><span data-stu-id="48c62-191">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="48c62-192">单击 " **重置** " 按钮控制器也会将控制器置于此距离。</span><span class="sxs-lookup"><span data-stu-id="48c62-192">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="48c62-193">**控制器抖动量** 将随机运动添加到控制器。</span><span class="sxs-lookup"><span data-stu-id="48c62-193">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="48c62-194">此功能可用于在设备上模拟不准确的控制器跟踪，并确保交互工作非常适合于输入。</span><span class="sxs-lookup"><span data-stu-id="48c62-194">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="48c62-195">手势</span><span class="sxs-lookup"><span data-stu-id="48c62-195">Hand gestures</span></span>

<span data-ttu-id="48c62-196">也可以模拟手写手势，如收缩、抓取、闲逛等。</span><span class="sxs-lookup"><span data-stu-id="48c62-196">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="48c62-197">使用 **左/右控制器操作键** 启用手动控制 (*左移* 或 *空间*) </span><span class="sxs-lookup"><span data-stu-id="48c62-197">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="48c62-198">进行操作时，按住鼠标按钮以执行手动手势。</span><span class="sxs-lookup"><span data-stu-id="48c62-198">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="48c62-199">每个鼠标按钮都可以映射，使用 *鼠标左键或中键笔势* 设置将手形形状转换为不同的笔势。</span><span class="sxs-lookup"><span data-stu-id="48c62-199">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="48c62-200">当没有按下任何按钮时， *默认的手势* 将为手形形状。</span><span class="sxs-lookup"><span data-stu-id="48c62-200">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="48c62-201">此时，只会执行 "选择" 操作的 "选中 *" 的笔势* 。</span><span class="sxs-lookup"><span data-stu-id="48c62-201">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="48c62-202">一次操作</span><span class="sxs-lookup"><span data-stu-id="48c62-202">One-hand manipulation</span></span>

1. <span data-ttu-id="48c62-203">按住左 **/右控制器操作键** (*左移* 或 *空间*) </span><span class="sxs-lookup"><span data-stu-id="48c62-203">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="48c62-204">指向对象</span><span class="sxs-lookup"><span data-stu-id="48c62-204">Point at object</span></span>
3. <span data-ttu-id="48c62-205">按住鼠标按钮进行收缩</span><span class="sxs-lookup"><span data-stu-id="48c62-205">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="48c62-206">使用鼠标移动对象</span><span class="sxs-lookup"><span data-stu-id="48c62-206">Use your mouse to move the object</span></span>
5. <span data-ttu-id="48c62-207">释放鼠标按钮以停止交互</span><span class="sxs-lookup"><span data-stu-id="48c62-207">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="48c62-208">双手操作</span><span class="sxs-lookup"><span data-stu-id="48c62-208">Two-hand manipulation</span></span>

<span data-ttu-id="48c62-209">对于同时使用两只手操作对象，建议使用持久性手模式。</span><span class="sxs-lookup"><span data-stu-id="48c62-209">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="48c62-210">按切换键按 *"T/Y"* 按钮 (两手) 。</span><span class="sxs-lookup"><span data-stu-id="48c62-210">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="48c62-211">一次操作一只手：</span><span class="sxs-lookup"><span data-stu-id="48c62-211">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="48c62-212">按住 **空格** 可控制右侧</span><span class="sxs-lookup"><span data-stu-id="48c62-212">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="48c62-213">将手移到要抓取对象的地方</span><span class="sxs-lookup"><span data-stu-id="48c62-213">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="48c62-214">按 \**鼠标左键\*\*\*激活收缩手势*。</span><span class="sxs-lookup"><span data-stu-id="48c62-214">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="48c62-215">释放 **空间** 以停止控制右侧。</span><span class="sxs-lookup"><span data-stu-id="48c62-215">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="48c62-216">手将就地冻结并锁定到收缩手势中，因为它不再被操作。</span><span class="sxs-lookup"><span data-stu-id="48c62-216">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="48c62-217">另一方面重复此过程，在另一个位置抓取同一个对象。</span><span class="sxs-lookup"><span data-stu-id="48c62-217">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="48c62-218">现在，两只手都抓取同一个对象，可以移动其中一个，以执行两手操作。</span><span class="sxs-lookup"><span data-stu-id="48c62-218">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="48c62-219">GGV (凝视、手势和语音) 交互</span><span class="sxs-lookup"><span data-stu-id="48c62-219">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="48c62-220">默认情况下，GGV 交互在编辑器中启用，而场景中没有可表达的手。</span><span class="sxs-lookup"><span data-stu-id="48c62-220">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="48c62-221">旋转相机，将凝视光标指向可交互 (鼠标按钮) </span><span class="sxs-lookup"><span data-stu-id="48c62-221">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="48c62-222">单击并按住 **鼠标左键** 进行交互</span><span class="sxs-lookup"><span data-stu-id="48c62-222">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="48c62-223">再次旋转相机以操作对象</span><span class="sxs-lookup"><span data-stu-id="48c62-223">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="48c62-224">可以通过在输入模拟配置文件中切换"启用 *无手输入"* 选项来关闭此选项。</span><span class="sxs-lookup"><span data-stu-id="48c62-224">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="48c62-225">此外，还可以使用模拟指针进行 GGV 交互</span><span class="sxs-lookup"><span data-stu-id="48c62-225">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="48c62-226">通过将 **手形模拟模式** 切换到 [输入模拟配置文件](#enabling-the-input-simulation-service)中的 *手势* 来启用 GGV 模拟</span><span class="sxs-lookup"><span data-stu-id="48c62-226">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="48c62-227">旋转相机，将注视光标指向种不可交互对象 (鼠标右键) </span><span class="sxs-lookup"><span data-stu-id="48c62-227">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="48c62-228">按住 **空间** 以控制右手</span><span class="sxs-lookup"><span data-stu-id="48c62-228">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="48c62-229">单击并按住 **鼠标左键** 以进行交互</span><span class="sxs-lookup"><span data-stu-id="48c62-229">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="48c62-230">使用鼠标移动对象</span><span class="sxs-lookup"><span data-stu-id="48c62-230">Use your mouse to move the object</span></span>
1. <span data-ttu-id="48c62-231">释放鼠标按钮以停止交互</span><span class="sxs-lookup"><span data-stu-id="48c62-231">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="48c62-232">引发传送事件</span><span class="sxs-lookup"><span data-stu-id="48c62-232">Raising Teleport Events</span></span>

<span data-ttu-id="48c62-233">若要在输入模拟中引发 "传送" 事件，请在输入模拟配置文件中配置 "手手势" 设置，以便其中一个操作执行 **传送开始** 手势，而另一个执行 **传送结束** 手势。</span><span class="sxs-lookup"><span data-stu-id="48c62-233">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="48c62-234">传送 **开始** 手势将显示传送指针，而 **传送结束** gesure 将完成传送操作并移动用户。</span><span class="sxs-lookup"><span data-stu-id="48c62-234">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="48c62-235">生成的传送的 y 位置取决于沿 y 轴的摄像机置换。</span><span class="sxs-lookup"><span data-stu-id="48c62-235">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="48c62-236">在编辑器中，默认情况下此值为0，因此使用 **Q** 和 **E** 键将其调整为适当的高度。</span><span class="sxs-lookup"><span data-stu-id="48c62-236">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![输入模拟传送设置](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="48c62-238">运动控制器交互</span><span class="sxs-lookup"><span data-stu-id="48c62-238">Motion controller interaction</span></span>

<span data-ttu-id="48c62-239">模拟的运动控制器的操作方式与所表述的操作方式相同。</span><span class="sxs-lookup"><span data-stu-id="48c62-239">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="48c62-240">当触发器、抓取和菜单键分别映射到 *鼠标左键*、 *G* 和 *M* 键时，交互模型类似于清晰的手写内容交互。</span><span class="sxs-lookup"><span data-stu-id="48c62-240">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="48c62-241">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="48c62-241">Eye tracking</span></span>

<span data-ttu-id="48c62-242">可以通过检查 [输入模拟配置文件](#enabling-the-input-simulation-service)中的 "**模拟眼睛位置**" 选项来启用 [目视跟踪模拟](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor)。</span><span class="sxs-lookup"><span data-stu-id="48c62-242">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="48c62-243">这不应与 GGV 或运动控制器样式交互一起使用 (因此请确保将 **默认控制器模拟模式** 设置为 "带) 的 *手写* "。</span><span class="sxs-lookup"><span data-stu-id="48c62-243">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="see-also"></a><span data-ttu-id="48c62-244">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48c62-244">See also</span></span>

* <span data-ttu-id="48c62-245">[输入系统配置文件](../input/input-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="48c62-245">[Input System profile](../input/input-providers.md).</span></span>