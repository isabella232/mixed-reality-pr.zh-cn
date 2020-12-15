---
title: 使用 Windows Mixed Reality 模拟器
description: 使用 Windows Mixed Reality 模拟器，无需 Windows Mixed Reality 沉浸式耳机即可在电脑上测试混合现实应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality，模拟器，测试
ms.openlocfilehash: 4ed3355df242f1df35c009e53149d834ea113e1f
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530295"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="7c62a-104">使用 Windows Mixed Reality 模拟器</span><span class="sxs-lookup"><span data-stu-id="7c62a-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="7c62a-105">使用 Windows Mixed Reality 模拟器，无需 Windows Mixed Reality 沉浸式耳机即可在电脑上测试混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="7c62a-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="7c62a-106">Windows 10 创意者更新中提供了模拟器。</span><span class="sxs-lookup"><span data-stu-id="7c62a-106">The simulator is available with the Windows 10 Creators Update.</span></span> <span data-ttu-id="7c62a-107">模拟器与 [HoloLens 模拟器](using-the-hololens-emulator.md)类似，但模拟器不使用虚拟机。</span><span class="sxs-lookup"><span data-stu-id="7c62a-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator doesn't use a virtual machine.</span></span> <span data-ttu-id="7c62a-108">模拟应用在 Windows 10 桌面用户会话中运行，就像使用沉浸式耳机一样。</span><span class="sxs-lookup"><span data-stu-id="7c62a-108">Simulated apps run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="7c62a-109">沉浸式耳机上传感器读取的人工和环境输入使用键盘、鼠标或 Xbox 控制器进行模拟。</span><span class="sxs-lookup"><span data-stu-id="7c62a-109">The human and environmental inputs read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="7c62a-110">应用不需要任何修改即可在模拟器中运行，并且不知道它们不在沉浸式耳机上运行。</span><span class="sxs-lookup"><span data-stu-id="7c62a-110">Apps don't need any modification to run in the simulator, and don't know they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="7c62a-111">启用 Windows Mixed Reality 模拟器</span><span class="sxs-lookup"><span data-stu-id="7c62a-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="7c62a-112">**启用** 开发人员模式-> 更新和安全性-为开发人员 ></span><span class="sxs-lookup"><span data-stu-id="7c62a-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="7c62a-113">从桌面启动 **混合现实门户**</span><span class="sxs-lookup"><span data-stu-id="7c62a-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="7c62a-114">如果这是你第一次启动门户，则需要完成安装体验</span><span class="sxs-lookup"><span data-stu-id="7c62a-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="7c62a-115">选择 **入门**</span><span class="sxs-lookup"><span data-stu-id="7c62a-115">Select **Get started**</span></span>
   2. <span data-ttu-id="7c62a-116">选择 " **我同意** 接受协议"</span><span class="sxs-lookup"><span data-stu-id="7c62a-116">Select **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="7c62a-117">对于开发人员，请选择 " **设置" 进行模拟 ()** 在不使用物理设备的情况下继续进行安装</span><span class="sxs-lookup"><span data-stu-id="7c62a-117">Select **Set up for simulation (for developers)** to continue through setup without a physical device</span></span>
   4. <span data-ttu-id="7c62a-118">选择 " **设置** " 以确认你的选择</span><span class="sxs-lookup"><span data-stu-id="7c62a-118">Select **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="7c62a-119">选择混合现实门户左侧的 " **开发人员** " 按钮</span><span class="sxs-lookup"><span data-stu-id="7c62a-119">Select the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="7c62a-120">将模拟切换开关切换到 **打开**</span><span class="sxs-lookup"><span data-stu-id="7c62a-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="7c62a-121">默认情况下，启用模拟将安装并启用左模拟的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="7c62a-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="7c62a-122">在 Windows 10 可能2019更新之前，安装模拟 6 DOF 控制器需要管理员权限。</span><span class="sxs-lookup"><span data-stu-id="7c62a-122">Before the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="7c62a-123">接受 "用户帐户控制" 对话框（如果有）。</span><span class="sxs-lookup"><span data-stu-id="7c62a-123">Accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="7c62a-124">现在，你应该已运行模拟！</span><span class="sxs-lookup"><span data-stu-id="7c62a-124">You should now be running with simulation!</span></span>

<span data-ttu-id="7c62a-125">如果要在 "设置" 中禁用开发人员模式，则应首先在混合现实门户的 "**开发人员**" 部分中将模拟切换开关设置为 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="7c62a-125">If you want to disable Developer mode in Settings, you should first turn the Simulation toggle switch to **Off** in the **For developers** section of the Mixed Reality Portal.</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="7c62a-126">将应用部署到混合现实模拟器</span><span class="sxs-lookup"><span data-stu-id="7c62a-126">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="7c62a-127">由于模拟器在没有虚拟机的情况下在本地 PC 上运行，因此你可以在调试时将通用 Windows 应用程序部署到 **本地计算机** 。</span><span class="sxs-lookup"><span data-stu-id="7c62a-127">Since the simulator runs on your local PC without a Virtual Machine, you can deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="7c62a-128">基本模拟器输入</span><span class="sxs-lookup"><span data-stu-id="7c62a-128">Basic simulator input</span></span>

<span data-ttu-id="7c62a-129">控制模拟器类似于许多常见的3D 视频游戏和 [HoloLens 模拟器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="7c62a-129">Controlling the simulator is similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="7c62a-130">可以使用键盘、鼠标或 Xbox 控制器提供输入。</span><span class="sxs-lookup"><span data-stu-id="7c62a-130">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="7c62a-131">可以通过定向模拟用户的操作，戴上沉浸式耳机来控制模拟器。</span><span class="sxs-lookup"><span data-stu-id="7c62a-131">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="7c62a-132">你的操作将移动模拟用户，并与应用进行交互，使其与沉浸式耳机上的响应相同。</span><span class="sxs-lookup"><span data-stu-id="7c62a-132">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="7c62a-133">**前后左右走动** - 使用键盘上的 WASD 键，或 Xbox 控制器上的左摇杆。</span><span class="sxs-lookup"><span data-stu-id="7c62a-133">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="7c62a-134">**查找、向下、向左** 、向右选择并拖动鼠标、使用键盘上的箭头键或 Xbox 控制器上的右摇杆。</span><span class="sxs-lookup"><span data-stu-id="7c62a-134">**Look up, down, left, and right** - Select and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="7c62a-135">**操作按钮按下控制器** -右键单击鼠标，按键盘上的 enter 键，或使用 Xbox 控制器上的按钮。</span><span class="sxs-lookup"><span data-stu-id="7c62a-135">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="7c62a-136">**"主页" 按钮按下控制器** -按键盘上的 Windows 键或 F2 键，或按 Xbox 控制器上的 B 按钮。</span><span class="sxs-lookup"><span data-stu-id="7c62a-136">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="7c62a-137">**用于滚动的控制器移动** -按住 Alt 键和鼠标右键，然后向上或向下拖动鼠标。</span><span class="sxs-lookup"><span data-stu-id="7c62a-137">**Controller movement for scrolling** - Hold the Alt key and the right mouse button, then drag the mouse up / down.</span></span> <span data-ttu-id="7c62a-138">在 Xbox 控制器中，按住右触发器和按钮，并将右摇杆向下和向下移动。</span><span class="sxs-lookup"><span data-stu-id="7c62a-138">In an Xbox controller, hold down the right trigger and A button and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="7c62a-139">跟踪控制器</span><span class="sxs-lookup"><span data-stu-id="7c62a-139">Tracked controllers</span></span>

<span data-ttu-id="7c62a-140">混合现实模拟器最多可以模拟两个手持跟踪的运动控制器。</span><span class="sxs-lookup"><span data-stu-id="7c62a-140">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="7c62a-141">在混合现实门户中使用切换开关启用它们。</span><span class="sxs-lookup"><span data-stu-id="7c62a-141">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="7c62a-142">每个模拟控制器都有：</span><span class="sxs-lookup"><span data-stu-id="7c62a-142">Each simulated controller has:</span></span>
* <span data-ttu-id="7c62a-143">位置和方向（空间）</span><span class="sxs-lookup"><span data-stu-id="7c62a-143">Position and orientation in space</span></span>
* <span data-ttu-id="7c62a-144">“主页”按钮</span><span class="sxs-lookup"><span data-stu-id="7c62a-144">Home button</span></span>
* <span data-ttu-id="7c62a-145">“菜单”按钮</span><span class="sxs-lookup"><span data-stu-id="7c62a-145">Menu button</span></span>
* <span data-ttu-id="7c62a-146">手柄按钮</span><span class="sxs-lookup"><span data-stu-id="7c62a-146">Grip button</span></span>
* <span data-ttu-id="7c62a-147">触摸板</span><span class="sxs-lookup"><span data-stu-id="7c62a-147">Touchpad</span></span>
* <span data-ttu-id="7c62a-148">控制</span><span class="sxs-lookup"><span data-stu-id="7c62a-148">Thumbstick</span></span>
* <span data-ttu-id="7c62a-149">电池电量水平</span><span class="sxs-lookup"><span data-stu-id="7c62a-149">Battery level</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7c62a-150">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="7c62a-150">Next Development Checkpoint</span></span>

<span data-ttu-id="7c62a-151">如果你遵循我们规划的 Unity 开发检查点历程，则你就处于部署阶段之中。</span><span class="sxs-lookup"><span data-stu-id="7c62a-151">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="7c62a-152">在这里，你可以继续下一 [主题](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) 或直接跳转到添加高级服务。</span><span class="sxs-lookup"><span data-stu-id="7c62a-152">From here, you can continue to the next [topic](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) or jump directly to adding advanced services.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c62a-153">高级服务</span><span class="sxs-lookup"><span data-stu-id="7c62a-153">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a><span data-ttu-id="7c62a-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c62a-154">See also</span></span>
* [<span data-ttu-id="7c62a-155">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="7c62a-155">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="7c62a-156">高级混合现实模拟器输入</span><span class="sxs-lookup"><span data-stu-id="7c62a-156">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="7c62a-157">Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="7c62a-157">Spatial mapping in Unity</span></span>](../../develop/unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="7c62a-158">DirectX 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="7c62a-158">Spatial mapping in DirectX</span></span>](../../develop/native/spatial-mapping-in-directx.md)
