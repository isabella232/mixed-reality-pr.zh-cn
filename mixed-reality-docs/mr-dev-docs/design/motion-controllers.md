---
title: 运动控制器
description: 了解如何在应用程序中使用混合现实运动控制器设置、对和管理器输入交互。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 控制器，运动控制器，配对，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，滚动，手柄，状态
ms.openlocfilehash: 367c9d9e0179c82af05af3fded9341ff7960d19e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583659"
---
# <a name="motion-controllers"></a><span data-ttu-id="bd6a8-104">运动控制器</span><span class="sxs-lookup"><span data-stu-id="bd6a8-104">Motion controllers</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="bd6a8-105">运动控制器是允许用户在混合现实中采取措施的 [硬件附件](../discover/hardware-accessories.md) 。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-105">Motion controllers are [hardware accessories](../discover/hardware-accessories.md) that allow users to take action in mixed reality.</span></span> <span data-ttu-id="bd6a8-106">动作控制器优于 [手势](gaze-and-commit.md#composite-gestures) 的优势在于，控制器在空间中有精确的位置，允许与数字对象进行精细的交互。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-106">An advantage of motion controllers over [gestures](gaze-and-commit.md#composite-gestures) is that the controllers have a precise position in space, allowing for fine grained interaction with digital objects.</span></span> <span data-ttu-id="bd6a8-107">对于 Windows Mixed Reality 沉浸式耳机，运动控制器是用户在其世界中采取措施的主要方式。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-107">For Windows Mixed Reality immersive headsets, motion controllers are the primary way that users will take action in their world.</span></span><br>
        <br>
        <span data-ttu-id="bd6a8-108">*映像： Windows Mixed Reality 运动控制器*</span><span class="sxs-lookup"><span data-stu-id="bd6a8-108">*Image: A Windows Mixed Reality motion controller*</span></span>
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality 运动控制器](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a><span data-ttu-id="bd6a8-110">设备支持</span><span class="sxs-lookup"><span data-stu-id="bd6a8-110">Device support</span></span>

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><span data-ttu-id="bd6a8-111"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="bd6a8-111"><strong>Feature</strong></span></span></td>
     <td><span data-ttu-id="bd6a8-112"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="bd6a8-112"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="bd6a8-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="bd6a8-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="bd6a8-114"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="bd6a8-114"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="bd6a8-115">运动控制器</span><span class="sxs-lookup"><span data-stu-id="bd6a8-115">Motion controllers</span></span></td>
     <td>❌</td>
     <td>❌</td>
     <td><span data-ttu-id="bd6a8-116">✔️</span><span class="sxs-lookup"><span data-stu-id="bd6a8-116">✔️</span></span></td>
</tr>
</table>

## <a name="hardware-details"></a><span data-ttu-id="bd6a8-117">硬件详细信息</span><span class="sxs-lookup"><span data-stu-id="bd6a8-117">Hardware details</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="bd6a8-118">Windows Mixed Reality 运动控制器使用沉浸式耳机中的传感器在视图的字段中提供精确而快速的移动跟踪。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-118">Windows Mixed Reality motion controllers offer precise and responsive movement tracking in your field of view using the sensors in the immersive headset.</span></span> <span data-ttu-id="bd6a8-119">不需要在空间的墙壁上安装硬件。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-119">There's no need to install hardware on the walls in your space.</span></span> <span data-ttu-id="bd6a8-120">这些运动控制器将提供与 Windows Mixed Reality 沉浸式耳机相同的设置和可移植性。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-120">These motion controllers will offer the same ease of setup and portability as Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="bd6a8-121">我们的设备合作伙伴计划投放市场并在零售货架上销售这些控制器。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-121">Our device partners plan to market and sell these controllers on retail shelves this holiday.</span></span>

<span data-ttu-id="bd6a8-122">![了解控制器](images/controllerimage-750px.png)</span><span class="sxs-lookup"><span data-stu-id="bd6a8-122">![Get to know your controller](images/controllerimage-750px.png)</span></span><br>
<span data-ttu-id="bd6a8-123">*了解控制器*</span><span class="sxs-lookup"><span data-stu-id="bd6a8-123">*Get to know your controller*</span></span>

<span data-ttu-id="bd6a8-124">**功能：**</span><span class="sxs-lookup"><span data-stu-id="bd6a8-124">**Features:**</span></span>
* <span data-ttu-id="bd6a8-125">光学跟踪</span><span class="sxs-lookup"><span data-stu-id="bd6a8-125">Optical tracking</span></span>
* <span data-ttu-id="bd6a8-126">触发器</span><span class="sxs-lookup"><span data-stu-id="bd6a8-126">Trigger</span></span>
* <span data-ttu-id="bd6a8-127">抓取按钮</span><span class="sxs-lookup"><span data-stu-id="bd6a8-127">Grab button</span></span>
* <span data-ttu-id="bd6a8-128">控制</span><span class="sxs-lookup"><span data-stu-id="bd6a8-128">Thumbstick</span></span>
* <span data-ttu-id="bd6a8-129">触摸板</span><span class="sxs-lookup"><span data-stu-id="bd6a8-129">Touchpad</span></span>

## <a name="setup"></a><span data-ttu-id="bd6a8-130">设置</span><span class="sxs-lookup"><span data-stu-id="bd6a8-130">Setup</span></span>

### <a name="before-you-begin"></a><span data-ttu-id="bd6a8-131">开始之前</span><span class="sxs-lookup"><span data-stu-id="bd6a8-131">Before you begin</span></span>

<span data-ttu-id="bd6a8-132">需要的软件：</span><span class="sxs-lookup"><span data-stu-id="bd6a8-132">**You'll need:**</span></span>
* <span data-ttu-id="bd6a8-133">两个运动控制器的集合。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-133">A set of two motion controllers.</span></span>
* <span data-ttu-id="bd6a8-134">四个 AA 电池。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-134">Four AA batteries.</span></span>
* <span data-ttu-id="bd6a8-135">支持蓝牙4.0 的 PC。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-135">A PC with Bluetooth 4.0 support.</span></span>

<span data-ttu-id="bd6a8-136">**检查 Windows、Unity 和驱动程序更新**</span><span class="sxs-lookup"><span data-stu-id="bd6a8-136">**Check for Windows, Unity, and driver updates**</span></span>
* <span data-ttu-id="bd6a8-137">若要进行混合现实开发，请参阅安装适用于 Windows、Unity 等的首选版本的 [工具](../develop/install-the-tools.md) 。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-137">Visit [Install the tools](../develop/install-the-tools.md) for the preferred versions of Windows, Unity, and so on, for mixed reality development.</span></span>
* <span data-ttu-id="bd6a8-138">请确保具有最新的 [耳机和运动控制器驱动程序](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-138">Make sure you have the most up-to-date [headset and motion controller drivers](/windows/mixed-reality/enthusiast-guide/mixed-reality-software).</span></span>

### <a name="pairing-controllers"></a><span data-ttu-id="bd6a8-139">配对控制器</span><span class="sxs-lookup"><span data-stu-id="bd6a8-139">Pairing controllers</span></span>

<span data-ttu-id="bd6a8-140">可以使用 Windows 设置（如任何其他蓝牙设备）将运动控制器绑定到主机。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-140">Motion controllers can be bonded with host PC using Windows settings like any other Bluetooth device.</span></span>

1. <span data-ttu-id="bd6a8-141">将两个 AA 电池插入控制器背面。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-141">Insert two AA batteries into the back of the controller.</span></span> <span data-ttu-id="bd6a8-142">暂时停止电池护盖。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-142">Leave the battery cover off for now.</span></span>
2. <span data-ttu-id="bd6a8-143">如果你使用的是外部 USB 蓝牙适配器而不是内置蓝牙收音机，请在继续操作之前查看 [蓝牙最佳实践](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) 。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-143">If you're using an external USB Bluetooth Adapter instead of a built-in Bluetooth radio, review the [Bluetooth best practices](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) before proceeding.</span></span> <span data-ttu-id="bd6a8-144">对于带有内置收音机的桌面配置，请确保天线已连接。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-144">For desktop configuration with built-in radio, ensure antenna is connected.</span></span>
3. <span data-ttu-id="bd6a8-145">打开 **Windows 设置**  ->  **设备**  ->  **添加 bluetooth 或其他设备**  ->  **蓝牙**，并删除任何早期的 "运动控制器–右侧" 和 "运动控制器–左侧" 实例。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-145">Open **Windows Settings** -> **Devices** -> **Add Bluetooth or other device** -> **Bluetooth** and remove any earlier instances of “Motion controller – Right” and “Motion controller – Left”.</span></span> <span data-ttu-id="bd6a8-146">查看列表底部的 "其他设备" 类别。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-146">Check also Other devices category at the bottom of the list.</span></span>
4. <span data-ttu-id="bd6a8-147">选择 " **添加蓝牙或其他设备** "，并查看它是否开始发现蓝牙设备。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-147">Select **Add Bluetooth or other device** and see it starting to discover Bluetooth devices.</span></span>
5. <span data-ttu-id="bd6a8-148">按住控制器的 Windows 按钮，在 buzzes 后打开控制器。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-148">Press and hold the controller's Windows button to turn on the controller, release once it buzzes.</span></span>
6. <span data-ttu-id="bd6a8-149">按住 "电池" 舱中的 "配对" 按钮 ("选项卡) ，直至 Led 开始闪烁。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-149">Press and hold the pairing button (tab in the battery compartment) until the LEDs begin pulsing.</span></span>

:::row:::
    :::column:::
7. <span data-ttu-id="bd6a8-150">等待 "运动控制器-左" 或 "运动控制器-右" 显示到列表的底部。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-150">Wait "Motion controller - Left" or "Motion controller - Right" to appear to the bottom of the list.</span></span> <span data-ttu-id="bd6a8-151">选择要配对。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-151">Select to pair.</span></span> <span data-ttu-id="bd6a8-152">控制器将在连接时振动一次。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-152">Controller will vibrate once when connected.</span></span><br>
        <br>
        <span data-ttu-id="bd6a8-153">*Image：选择要配对的 "运动控制器";如果有多个实例，请从列表底部选择一个实例*</span><span class="sxs-lookup"><span data-stu-id="bd6a8-153">*Image: Select "Motion controller" to pair; if there are multiple instances, select one from the bottom of the list*</span></span>
    :::column-end:::
        :::column:::
       ![选择要配对的运动控制器，如果有多个实例，请从显示的列表底部选择一个](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. <span data-ttu-id="bd6a8-155">你会看到，控制器在 **"鼠标、键盘、& 笔" 类别** 下的 "蓝牙设置" 中显示为 " **已连接**"。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-155">You'll see the controller appear in the Bluetooth settings under **“Mouse, keyboard, & pen” category** as **Connected**.</span></span> <span data-ttu-id="bd6a8-156">此时，你可能会收到固件更新–请参阅 [下一部分](motion-controllers.md#updating-controller-firmware)。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-156">At this point, you may get a firmware update – see [next section](motion-controllers.md#updating-controller-firmware).</span></span>
9. <span data-ttu-id="bd6a8-157">重新连接电池盖子。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-157">Reattach battery cover.</span></span>
10. <span data-ttu-id="bd6a8-158">对第二个控制器重复步骤1-9。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-158">Repeat steps 1-9 for the second controller.</span></span>

<br>

:::row:::
    :::column:::
        <span data-ttu-id="bd6a8-159">成功配对两个控制器后，设置应如下所示，在 **"鼠标，键盘，& 笔" 类别** 下</span><span class="sxs-lookup"><span data-stu-id="bd6a8-159">After successfully pairing both controllers, your settings should look like the following, under **“Mouse, keyboard, & pen” category**</span></span> <br>
        <br>
        <span data-ttu-id="bd6a8-160">*图像：连接的运动控制器*</span><span class="sxs-lookup"><span data-stu-id="bd6a8-160">*Image: Motion controllers connected*</span></span>
    :::column-end:::
        :::column:::
       ![已连接动作控制器](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

<span data-ttu-id="bd6a8-162">如果在配对后关闭控制器，则其状态将显示为配对。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-162">If the controllers are turned off after pairing, their status will show up as Paired.</span></span> <span data-ttu-id="bd6a8-163">对于 "其他设备" 类别下的控制器，配对可能只有部分完成。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-163">For controllers permanently under the “Other devices” category, pairing may have only partially completed.</span></span> <span data-ttu-id="bd6a8-164">在这种情况下，请再次运行配对步骤，使控制器正常运行。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-164">In this case, run the pairing steps again to get controller functional.</span></span>

### <a name="updating-controller-firmware"></a><span data-ttu-id="bd6a8-165">正在更新控制器固件</span><span class="sxs-lookup"><span data-stu-id="bd6a8-165">Updating controller firmware</span></span>

* <span data-ttu-id="bd6a8-166">如果沉浸式耳机连接到您的 PC，并提供新的控制器固件，则在您下次打开时，会自动将该固件推送到运动控制器。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-166">If an immersive headset is connected to your PC with new controller firmware is available, the firmware will be pushed to your motion controllers automatically the next time you turn them on.</span></span> <span data-ttu-id="bd6a8-167">控制器固件更新通过一种在循环动作中照亮 LED 象限的模式来表示，并且需要1-2 分钟。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-167">Controller firmware updates are indicated by a pattern of illuminating LED quadrants in a circular motion, and take 1-2 minutes.</span></span>


:::row:::
    :::column:::
* <span data-ttu-id="bd6a8-168">固件更新完成后，控制器将重新启动并重新连接。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-168">After the firmware update completes, the controllers will reboot and reconnect.</span></span> <span data-ttu-id="bd6a8-169">这两个控制器现在都应连接。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-169">Both controllers should be connected now.</span></span> <br>
        <br>
        <span data-ttu-id="bd6a8-170">*映像：在蓝牙设置中连接的控制器*</span><span class="sxs-lookup"><span data-stu-id="bd6a8-170">*Image: Controllers connected in Bluetooth settings*</span></span>
    :::column-end:::
        :::column:::
       ![已连接控制器](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* <span data-ttu-id="bd6a8-172">验证控制器是否正常工作：</span><span class="sxs-lookup"><span data-stu-id="bd6a8-172">Verify your controllers work properly:</span></span>
    1. <span data-ttu-id="bd6a8-173">启动 **混合现实门户** ，并输入混合现实主页。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-173">Launch **Mixed Reality Portal** and enter your Mixed Reality Home.</span></span>
    2. <span data-ttu-id="bd6a8-174">移动控制器并验证跟踪、测试按钮并验证 [teleportation](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 是否正常工作。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-174">Move your controllers and verify tracking, test buttons, and verify [teleportation](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) works.</span></span> <span data-ttu-id="bd6a8-175">如果没有，请检查 [运动控制器故障排除](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-175">If they don't, then check out [motion controller troubleshooting](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).</span></span>

## <a name="gazing-and-pointing"></a><span data-ttu-id="bd6a8-176">Gazing 和指向</span><span class="sxs-lookup"><span data-stu-id="bd6a8-176">Gazing and pointing</span></span>

<span data-ttu-id="bd6a8-177">Windows Mixed Reality 支持两个用于交互的关键模型; **注视并提交** 和 **提交**：</span><span class="sxs-lookup"><span data-stu-id="bd6a8-177">Windows Mixed Reality supports two key models for interaction; **gaze and commit** and **point and commit**:</span></span>
* <span data-ttu-id="bd6a8-178">使用 " **注视" 和 "提交**"，用户可通过其 [注视](gaze-and-commit.md)来定位对象，并使用手接器、游戏板、clicker 或声音来选择对象。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-178">With **gaze and commit**, users target an object with their [gaze](gaze-and-commit.md), and then select objects with hand air-taps, a gamepad, a clicker, or their voice.</span></span>
* <span data-ttu-id="bd6a8-179">通过 **点和提交**，用户可以在目标对象上目标为支持指针的运动控制器，然后使用控制器的触发器选择对象。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-179">With **point and commit**, a user can aim a pointing-capable motion controller at the target object and then select objects with the controller's trigger.</span></span>

<span data-ttu-id="bd6a8-180">支持使用运动控制器的应用也应尽可能启用注视驱动的交互，使用户能够选择他们使用的输入设备。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-180">Apps that support pointing with motion controllers should also enable gaze-driven interactions where possible, to give users a choice in what input devices they use.</span></span>

### <a name="managing-recoil-when-pointing"></a><span data-ttu-id="bd6a8-181">在指向时管理 recoil</span><span class="sxs-lookup"><span data-stu-id="bd6a8-181">Managing recoil when pointing</span></span>

<span data-ttu-id="bd6a8-182">使用运动控制器进行指向和提交时，用户将通过拉取其触发器来使用控制器进行定位和交互。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-182">When using motion controllers to point and commit, your users will use the controller to target and interact by pulling its trigger.</span></span> <span data-ttu-id="bd6a8-183">请求触发器 vigorously 的用户最终可能会在其触发器拉取的末尾比预期的更高。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-183">Users who pull the trigger vigorously may end up aiming the controller higher at the end of their trigger pull than they'd intended.</span></span>

<span data-ttu-id="bd6a8-184">若要管理用户拉取触发器时可能发生的任何此类 recoil，则当触发器的模拟轴值超过0.0 时，应用程序可以对齐其目标射线。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-184">To manage any such recoil that may occur when users pull the trigger, your app can snap its targeting ray when the trigger's analog axis value rises above 0.0.</span></span> <span data-ttu-id="bd6a8-185">然后，只要在短时间窗口中最后一次按下时，就可以使用该目标射线来执行操作，然后将触发器值达到1.0。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-185">You can then take action using that targeting ray a few frames later once the trigger value reaches 1.0, as long as the final press occurs within a short time window.</span></span> <span data-ttu-id="bd6a8-186">使用较高级别的 [复合分流手势](gaze-and-commit.md#composite-gestures)时，Windows 将管理此目标光线捕获和超时。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-186">When using the higher-level [composite Tap gesture](gaze-and-commit.md#composite-gestures), Windows will manage this targeting ray capture and timeout for you.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="bd6a8-187">手柄姿势与指针姿势</span><span class="sxs-lookup"><span data-stu-id="bd6a8-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="bd6a8-188">Windows Mixed Reality 支持采用不同外形规格的运动控制器，其中每个控制器的设计在用户的手位置与应用程序在呈现控制器时应使用的自然 "转发" 方向不同。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-188">Windows Mixed Reality supports motion controllers in different form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="bd6a8-189">为了更好地表示这些控制器，可以针对每个交互源调查两种类型的姿势： **手柄姿势** 和 **指针构成**。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-189">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source; the **grip pose** and the **pointer pose**.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="bd6a8-190">抓握姿势</span><span class="sxs-lookup"><span data-stu-id="bd6a8-190">Grip pose</span></span>

<span data-ttu-id="bd6a8-191">**手柄姿势** 表示由 HoloLens 检测到的掌托的位置，或包含运动控制器的掌托的位置。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-191">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="bd6a8-192">在沉浸式耳机上，手柄姿势最适合用于呈现 **用户的手** 或 **持有用户的对象**，例如剑或机枪。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-192">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="bd6a8-193">可视化运动控制器时也使用手柄姿势，因为用于运动控制器的 Windows 提供的 **呈现模型** 使用手柄姿势作为原点和旋转中心。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-193">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="bd6a8-194">手柄姿势的定义具体如下：</span><span class="sxs-lookup"><span data-stu-id="bd6a8-194">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="bd6a8-195">**手柄位置**：在固定控制器时，掌上质心，向左或向右调整以使其在手柄内居中。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-195">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="bd6a8-196">在 Windows Mixed Reality 运动控制器上，此位置通常与 "抓住" 按钮对齐。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-196">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="bd6a8-197">**手柄方向的右轴**：当你完全打开手形成一个平面的五指形姿势时，与你的掌上的光线 (从右手掌向后) </span><span class="sxs-lookup"><span data-stu-id="bd6a8-197">The **grip orientation's Right axis**: When you completely open your hand to form a flat five-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="bd6a8-198">**手柄方向的正向轴**：当您关闭手中的部分 (时，就如同按住控制器) 一样，通过您的非拇指形来表示 "转发" 的射线。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-198">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="bd6a8-199">**手柄方向的上轴**：向右和向后定义隐含的上轴。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-199">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="bd6a8-200">指针姿势</span><span class="sxs-lookup"><span data-stu-id="bd6a8-200">Pointer pose</span></span>

<span data-ttu-id="bd6a8-201">**指针姿势** 代表着控制器的末端。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-201">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="bd6a8-202">系统提供的指针姿势最适合用于在 **呈现控制器模型本身** 时进行 raycast。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-202">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="bd6a8-203">如果要渲染某个其他虚拟对象来替代控制器（如虚拟压力），则应指出该虚拟对象的最自然的光线，如沿应用定义的机枪模型的桶向下移动的射线。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-203">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="bd6a8-204">由于用户可以看到虚拟对象，而不是物理控制器，因此，使用虚拟对象指向虚拟对象可能会更自然地使用应用。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-204">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="bd6a8-205">控制器跟踪状态</span><span class="sxs-lookup"><span data-stu-id="bd6a8-205">Controller tracking state</span></span>

<span data-ttu-id="bd6a8-206">与耳机一样，Windows Mixed Reality 运动控制器不需要外部跟踪传感器的设置。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-206">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="bd6a8-207">相反，控制器由耳机本身中的传感器跟踪。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-207">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="bd6a8-208">如果用户将控制器移出耳机的视图，则在大多数情况下，Windows 将继续推断控制器位置，并将其提供给应用。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-208">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="bd6a8-209">如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-209">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="bd6a8-210">此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-210">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="bd6a8-211">许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-211">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="bd6a8-212">显式跟踪状态的推理</span><span class="sxs-lookup"><span data-stu-id="bd6a8-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="bd6a8-213">希望根据跟踪状态以不同方式对位置进行处理的应用可能会进一步检查控制器状态的属性，如 SourceLossRisk 和 PositionAccuracy：</span><span class="sxs-lookup"><span data-stu-id="bd6a8-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as SourceLossRisk and PositionAccuracy:</span></span>

<table>
<tr>
<th> <span data-ttu-id="bd6a8-214">跟踪状态</span><span class="sxs-lookup"><span data-stu-id="bd6a8-214">Tracking state</span></span> </th><th> <span data-ttu-id="bd6a8-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="bd6a8-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="bd6a8-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="bd6a8-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="bd6a8-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="bd6a8-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="bd6a8-218"><b>高准确度</b> </span><span class="sxs-lookup"><span data-stu-id="bd6a8-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="bd6a8-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="bd6a8-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bd6a8-220">高</span><span class="sxs-lookup"><span data-stu-id="bd6a8-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bd6a8-221">是</span><span class="sxs-lookup"><span data-stu-id="bd6a8-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd6a8-222"><b>高准确度 (丢失) 的风险 </b> </span><span class="sxs-lookup"><span data-stu-id="bd6a8-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="bd6a8-223">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="bd6a8-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bd6a8-224">高</span><span class="sxs-lookup"><span data-stu-id="bd6a8-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bd6a8-225">是</span><span class="sxs-lookup"><span data-stu-id="bd6a8-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd6a8-226"><b>近似准确度</b> </span><span class="sxs-lookup"><span data-stu-id="bd6a8-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="bd6a8-227">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="bd6a8-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="bd6a8-228">近似</span><span class="sxs-lookup"><span data-stu-id="bd6a8-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bd6a8-229">是</span><span class="sxs-lookup"><span data-stu-id="bd6a8-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bd6a8-230"><b>无位置</b> </span><span class="sxs-lookup"><span data-stu-id="bd6a8-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="bd6a8-231">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="bd6a8-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="bd6a8-232">近似</span><span class="sxs-lookup"><span data-stu-id="bd6a8-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="bd6a8-233">false</span><span class="sxs-lookup"><span data-stu-id="bd6a8-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="bd6a8-234">这些运动控制器跟踪状态的定义如下：</span><span class="sxs-lookup"><span data-stu-id="bd6a8-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="bd6a8-235">**高准确度：** 尽管运动控制器位于耳机的视图中，但它通常会根据视觉对象跟踪提供高准确性位置。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="bd6a8-236">一种移动控制器，该控制器会暂时离开了耳机传感器， (例如，通过用户的另一种方式，) 会根据控制器本身的惯性跟踪，在短时间内继续返回高准确度姿势。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-236">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (for example, by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="bd6a8-237">**高准确度 (丢失) 的风险：** 当用户将运动控制器移出耳机的视图边缘后，耳机不久就无法直观地跟踪控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="bd6a8-238">此应用通过查看 **SourceLossRisk** 到1.0，来了解控制器何时到达此 FOV 边界。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="bd6a8-239">此时，应用程序可以选择暂停需要稳定的高质量姿势流的控制器手势。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-239">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="bd6a8-240">**近似准确性：** 如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="bd6a8-241">此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="bd6a8-242">许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="bd6a8-243">对于输入要求较高的应用，可以通过检查 **PositionAccuracy** 属性，从 **高** 准确度到 **接近** 准确性，从而为用户提供更多的 hitbox。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="bd6a8-244">**无位置：** 尽管控制器可以在很长时间内正常运行，但有时系统也知道，甚至在当前情况下，该位置都没有意义。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="bd6a8-245">例如，已打开的控制器可能从未被可视化地观察到，或者用户可能会关闭控制器，然后由其他人选取。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-245">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="bd6a8-246">在这种情况下，系统不会提供应用程序的任何位置，并且 **TryGetPosition** 将返回 false。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-246">At those times, the system won't provide any position to the app, and **TryGetPosition** will return false.</span></span>

## <a name="interactions-low-level-spatial-input"></a><span data-ttu-id="bd6a8-247">交互：低级别空间输入</span><span class="sxs-lookup"><span data-stu-id="bd6a8-247">Interactions: Low-level spatial input</span></span>

<span data-ttu-id="bd6a8-248">各种双手和运动控制器的核心交互是 **选择**、 **菜单**、 **抓住**、 **触摸板**、 **操纵杆** 和 **Home**。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-248">The core interactions across hands and motion controllers are **Select**, **Menu**, **Grasp**, **Touchpad**, **Thumbstick**, and **Home**.</span></span>
* <span data-ttu-id="bd6a8-249">**选择** "是"，这是用于激活全息影像的主要交互，其中包含一个按下的发布。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-249">**Select** is the primary interaction to activate a hologram, consisting of a press followed by a release.</span></span> <span data-ttu-id="bd6a8-250">对于运动控制器，可以使用控制器的触发器执行 Select 按下。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-250">For motion controllers, you perform a Select press using the controller's trigger.</span></span> <span data-ttu-id="bd6a8-251">通过 [语音命令](voice-input.md) "select" 执行选择的其他方法。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-251">Other ways to perform a Select are by speaking the [voice command](voice-input.md) "Select".</span></span> <span data-ttu-id="bd6a8-252">可以在任何应用中使用相同的选择交互。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-252">The same select interaction can be used within any app.</span></span> <span data-ttu-id="bd6a8-253">请考虑选择作为鼠标单击的等效项;你一次学习的通用操作，然后应用于所有应用。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-253">Think of Select as the equivalent of a mouse click; a universal action that you learn once and then apply across all your apps.</span></span>
* <span data-ttu-id="bd6a8-254">**菜单** 是用于对对象进行操作的辅助交互，用于获取上下文菜单或执行其他辅助操作。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-254">**Menu** is the secondary interaction for acting on an object, used to pull up a context menu or take some other secondary action.</span></span> <span data-ttu-id="bd6a8-255">使用运动控制器，可以使用控制器的 *菜单* 按钮执行菜单操作。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-255">With motion controllers, you can take a menu action using the controller's *menu* button.</span></span> <span data-ttu-id="bd6a8-256"> (即其上带有汉堡 "menu" 图标的按钮) </span><span class="sxs-lookup"><span data-stu-id="bd6a8-256">(that is, the button with the hamburger "menu" icon on it)</span></span>
* <span data-ttu-id="bd6a8-257">**抓住** ，用户可以直接对对象执行操作，以便对其进行操作。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-257">**Grasp** is how users can directly take action on objects at their hand to manipulate them.</span></span> <span data-ttu-id="bd6a8-258">借助运动控制器，你可以通过紧密地挤压你的前来执行抓住操作。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-258">With motion controllers, you can do a grasp action by squeezing your fist tightly.</span></span> <span data-ttu-id="bd6a8-259">运动控制器可以通过抓取按钮、棕榈触发器或其他传感器检测抓住。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-259">A motion controller may detect a Grasp with a grab button, palm trigger, or other sensor.</span></span>
* <span data-ttu-id="bd6a8-260">**触摸板** 允许用户在运动控制器的触摸板图面上调整两个尺寸的操作，并通过单击触摸板上的 "向下" 来提交操作。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-260">**Touchpad** allows the user to adjust an action in two dimensions along the surface of a motion controller's touchpad, committing the action by clicking down on the touchpad.</span></span> <span data-ttu-id="bd6a8-261">触摸板提供按下状态、接触状态和标准化的 XY 坐标。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-261">Touchpads provide a pressed state, touched state, and normalized XY coordinates.</span></span> <span data-ttu-id="bd6a8-262">X 和 Y 范围介于循环触摸板范围内的-1 到1之间，中心位于 (0，0) 。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-262">X and Y range from -1 to 1 across the range of the circular touchpad, with a center at (0, 0).</span></span> <span data-ttu-id="bd6a8-263">对于 X，-1 位于左侧，1位于右侧。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-263">For X, -1 is on the left and 1 is on the right.</span></span> <span data-ttu-id="bd6a8-264">对于 Y，-1 位于底部，1位于顶部。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-264">For Y, -1 is on the bottom and 1 is on the top.</span></span>
* <span data-ttu-id="bd6a8-265">使用 **操纵杆**，用户可以通过在其循环范围内移动运动控制器的操纵杆，并通过单击操纵杆提交操作来调整两个尺寸的操作。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-265">**Thumbstick** allows the user to adjust an action in two dimensions by moving a motion controller's thumbstick within its circular range, committing the action by clicking down on the thumbstick.</span></span> <span data-ttu-id="bd6a8-266">Thumbsticks 还提供按下状态和标准化的 XY 坐标。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-266">Thumbsticks also provide a pressed state and normalized XY coordinates.</span></span> <span data-ttu-id="bd6a8-267">X 和 Y 范围介于循环触摸板范围内的-1 到1之间，中心位于 (0，0) 。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-267">X and Y range from -1 to 1 across the range of the circular touchpad, with a center at (0, 0).</span></span> <span data-ttu-id="bd6a8-268">对于 X，-1 位于左侧，1位于右侧。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-268">For X, -1 is on the left and 1 is on the right.</span></span> <span data-ttu-id="bd6a8-269">对于 Y，-1 位于底部，1位于顶部。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-269">For Y, -1 is on the bottom and 1 is on the top.</span></span>
* <span data-ttu-id="bd6a8-270">**Home** 是一种特殊的系统操作，用于返回到 "开始" 菜单。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-270">**Home** is a special system action that is used to go back to the Start Menu.</span></span> <span data-ttu-id="bd6a8-271">这类似于按键盘上的 Windows 键或 Xbox 控制器上的 Xbox 按钮。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-271">It's similar to pressing the Windows key on a keyboard or the Xbox button on an Xbox controller.</span></span> <span data-ttu-id="bd6a8-272">可以通过按下动作控制器上的 "Windows" 按钮来回家。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-272">You can go Home by pressing the Windows button on a motion controller.</span></span> <span data-ttu-id="bd6a8-273">请注意，你始终可以通过说 "你好 Cortana，回家" 开始。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-273">Note, you can always return to Start by saying "Hey Cortana, Go Home".</span></span> <span data-ttu-id="bd6a8-274">应用无法专门对 Home 操作做出反应，因为这些操作由系统处理。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-274">Apps can't react specifically to Home actions, as these are handled by the system.</span></span>

## <a name="composite-gestures-high-level-spatial-input"></a><span data-ttu-id="bd6a8-275">复合手势：高级空间输入</span><span class="sxs-lookup"><span data-stu-id="bd6a8-275">Composite gestures: High-level spatial input</span></span>

<span data-ttu-id="bd6a8-276">可在一段时间内跟踪 [手手势](gaze-and-commit.md#composite-gestures) 和运动控制器以检测一组通用的高级 **[复合手势](gaze-and-commit.md#composite-gestures)**。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-276">Both [hand gestures](gaze-and-commit.md#composite-gestures) and motion controllers can be tracked over time to detect a common set of high-level **[composite gestures](gaze-and-commit.md#composite-gestures)**.</span></span> <span data-ttu-id="bd6a8-277">这使您的应用程序能够检测高级 **分流**、 **定格**、 **操作** 和 **导航** 手势，无论用户最终使用的是手还是控制器。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-277">This enables your app to detect high-level **tap**, **hold**, **manipulation** and **navigation** gestures, whether users end up using hands or controllers.</span></span>

## <a name="rendering-the-motion-controller-model"></a><span data-ttu-id="bd6a8-278">呈现运动控制器模型</span><span class="sxs-lookup"><span data-stu-id="bd6a8-278">Rendering the motion controller model</span></span>

<span data-ttu-id="bd6a8-279">**3d 控制器模型** Windows 可让应用程序在系统中当前处于活动状态的每个运动控制器呈现模型。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-279">**3D controller models** Windows makes available to apps a renderable model of each motion controller currently active in the system.</span></span> <span data-ttu-id="bd6a8-280">通过让应用在运行时动态加载和表述这些系统提供的控制器模型，你可以确保你的应用程序与将来的任何控制器设计兼容。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-280">By having your app dynamically load and articulate these system-provided controller models at runtime, you can ensure your app is forward-compatible to any future controller designs.</span></span>

<span data-ttu-id="bd6a8-281">我们建议在控制器的 **手柄姿势** 上呈现所有呈现模型，因为模型的原点与物理世界中的这一点对齐。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-281">We recommend rendering all renderable models at the **grip pose** of the controller, as the origin of the model is aligned with this point in the physical world.</span></span> <span data-ttu-id="bd6a8-282">如果要渲染控制器模型，则可能需要从 **指针姿势** raycast 到场景，这表示该控制器的物理设计需要点，这表示用户自然会想到的射线。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-282">If you're rendering controller models, you may then wish to raycast into your scene from the **pointer pose**, which represents the ray along which users will naturally expect to point, given that controller's physical design.</span></span>

<span data-ttu-id="bd6a8-283">有关如何在 Unity 中动态加载控制器模型的详细信息，请参阅在 [unity 中呈现运动控制器模型](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity) 部分。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-283">For more information about how to load controller models dynamically in Unity, see the [Rendering the motion controller model in Unity](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity) section.</span></span>

<span data-ttu-id="bd6a8-284">**2d 控制器线条** 图虽然我们建议将应用内控制器提示和命令附加到应用内控制器模型本身，但某些开发人员可能希望在平面 "教程" 或 "操作方法" UI 中使用运动控制器的2D 线条图表示形式。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-284">**2D controller line art** While we recommend attaching in-app controller tips and commands to the in-app controller models themselves, some developers may want to use 2D line art representations of the motion controllers in flat "tutorial" or "how-to" UI.</span></span> <span data-ttu-id="bd6a8-285">对于这些开发人员，我们制作了。以下两种情况下均提供 png 运动控制器线条图形文件 (右键单击以保存) 。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-285">For those developers, we've made .png motion controller line art files available in both black and white below (right-click to save).</span></span>

![运动控制器线条图预览](images/motioncontrollers-black-preview-300px.png)

[<span data-ttu-id="bd6a8-287">"" 中的整分辨率运动控制器线条艺术</span><span class="sxs-lookup"><span data-stu-id="bd6a8-287">Full-resolution motion controllers line art in '''white'''</span></span>](images/motioncontrollers-white.png)
 
[<span data-ttu-id="bd6a8-288">"" 中的整分辨率动作控制器线条图黑色 ""</span><span class="sxs-lookup"><span data-stu-id="bd6a8-288">Full-resolution motion controllers line art in '''black'''</span></span>](images/motioncontrollers-black.png)

## <a name="faq"></a><span data-ttu-id="bd6a8-289">常见问题解答</span><span class="sxs-lookup"><span data-stu-id="bd6a8-289">FAQ</span></span>

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a><span data-ttu-id="bd6a8-290">是否可以将运动控制器配对到多台电脑？</span><span class="sxs-lookup"><span data-stu-id="bd6a8-290">Can I pair motion controllers to multiple PCs?</span></span>

<span data-ttu-id="bd6a8-291">运动控制器支持与单台 PC 配对。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-291">Motion controllers support pairing with a single PC.</span></span> <span data-ttu-id="bd6a8-292">按照 [动作控制器设置](motion-controllers.md#setup) 来配对控制器的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-292">Follow instructions on [motion controller setup](motion-controllers.md#setup) to pair your controllers.</span></span>

### <a name="how-do-i-update-motion-controller-firmware"></a><span data-ttu-id="bd6a8-293">如何实现更新运动控制器固件？</span><span class="sxs-lookup"><span data-stu-id="bd6a8-293">How do I update motion controller firmware?</span></span>

<span data-ttu-id="bd6a8-294">运动控制器固件是耳机驱动程序的一部分，如有必要，它将在连接时自动更新。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-294">Motion controller firmware is part of the headset driver and will be updated automatically on connection, if necessary.</span></span> <span data-ttu-id="bd6a8-295">固件更新通常需要1-2 分钟的时间，具体取决于蓝牙无线电和链接质量。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-295">Firmware updates typically take 1-2 minutes depending on Bluetooth radio and link quality.</span></span> <span data-ttu-id="bd6a8-296">在极少数情况下，控制器固件更新可能需要长达10分钟的时间，这可能表示 Bluetooth 连接或无线电干扰较差。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-296">In rare cases, controller firmware updates may take up to 10 minutes, which can indicate poor Bluetooth connectivity or radio interference.</span></span> <span data-ttu-id="bd6a8-297">请参阅 [发烧指南中的蓝牙最佳实践](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) ，以解决连接问题。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-297">See [Bluetooth best practices in the Enthusiast Guide](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) to troubleshoot connectivity issues.</span></span> <span data-ttu-id="bd6a8-298">固件更新之后，控制器将重新启动并重新连接到主机计算机 (你可能会注意到，Led 对于跟踪) 会有所鲜。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-298">After a firmware update, controllers will reboot and reconnect to the host PC (you may notice the LEDs go bright for tracking).</span></span> <span data-ttu-id="bd6a8-299">如果固件更新被中断 (例如，控制器丢失了电源) ，则在下次打开控制器时，将再次尝试此固件。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-299">If a firmware update is interrupted (for example, the controllers lose power), it will be attempted again the next time the controllers are powered on.</span></span>

### <a name="how-i-can-check-battery-level"></a><span data-ttu-id="bd6a8-300">如何检查电池电量级别？</span><span class="sxs-lookup"><span data-stu-id="bd6a8-300">How I can check battery level?</span></span>

<span data-ttu-id="bd6a8-301">在 [Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)中，您可以打开控制器以查看其在虚拟模型反面上的电量级别。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-301">In the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md), you can turn your controller over to see its battery level on the reverse side of the virtual model.</span></span> <span data-ttu-id="bd6a8-302">没有物理电池电量指标。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-302">There's no physical battery level indicator.</span></span>

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a><span data-ttu-id="bd6a8-303">是否可以使用这些不带耳机的控制器？</span><span class="sxs-lookup"><span data-stu-id="bd6a8-303">Can you use these controllers without a headset?</span></span> <span data-ttu-id="bd6a8-304">仅针对游戏杆/触发器/etc 输入？</span><span class="sxs-lookup"><span data-stu-id="bd6a8-304">Just for the joystick/trigger/etc input?</span></span>

<span data-ttu-id="bd6a8-305">不适用于通用 Windows 应用程序。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-305">Not for Universal Windows Applications.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="bd6a8-306">疑难解答</span><span class="sxs-lookup"><span data-stu-id="bd6a8-306">Troubleshooting</span></span>

<span data-ttu-id="bd6a8-307">请参阅发烧指南中的 [运动控制器故障排除](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) 。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-307">See [motion controller troubleshooting](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) in the Enthusiast Guide.</span></span>

## <a name="filing-motion-controller-feedbackbugs"></a><span data-ttu-id="bd6a8-308">存档运动控制器反馈/bug</span><span class="sxs-lookup"><span data-stu-id="bd6a8-308">Filing motion controller feedback/bugs</span></span>

<span data-ttu-id="bd6a8-309">使用 "Mixed Reality-> 输入" 类别在反馈中心[向我们提供反馈](/hololens/hololens-feedback)。</span><span class="sxs-lookup"><span data-stu-id="bd6a8-309">[Give us feedback](/hololens/hololens-feedback) in Feedback Hub, using the "Mixed Reality -> Input" category.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd6a8-310">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd6a8-310">See also</span></span>

* [<span data-ttu-id="bd6a8-311">Unity 中的运动控制器</span><span class="sxs-lookup"><span data-stu-id="bd6a8-311">Motion controllers in Unity</span></span>](../develop/unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="bd6a8-312">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="bd6a8-312">Hands and motion controllers in DirectX</span></span>](../develop/native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="bd6a8-313">笔势</span><span class="sxs-lookup"><span data-stu-id="bd6a8-313">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="bd6a8-314">发烧本指南： Windows Mixed Reality 主页</span><span class="sxs-lookup"><span data-stu-id="bd6a8-314">Enthusiast's Guide: Your Windows Mixed Reality home</span></span>](/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [<span data-ttu-id="bd6a8-315">发烧本指南：在 Windows Mixed Reality 中使用游戏 & 应用</span><span class="sxs-lookup"><span data-stu-id="bd6a8-315">Enthusiast's Guide: Using games & apps in Windows Mixed Reality</span></span>](/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [<span data-ttu-id="bd6a8-316">由内而外跟踪的工作原理</span><span class="sxs-lookup"><span data-stu-id="bd6a8-316">How inside-out tracking works</span></span>](/windows/mixed-reality/enthusiast-guide/tracking-system)