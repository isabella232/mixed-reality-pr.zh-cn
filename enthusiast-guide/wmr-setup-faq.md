---
title: Windows Mixed Reality 开发人员工具包常见问题解答
description: 获取在使用 Windows Mixed Reality 应用程序和设备时的常见问题的解答。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
appliesto:
- Windows 10
ms.openlocfilehash: 87eb22e600ca2426bdd3fec1fd428c11d9c45313
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581809"
---
# <a name="windows-mixed-reality-setup-faq"></a><span data-ttu-id="6c720-104">Windows Mixed Reality 开发人员工具包常见问题解答</span><span class="sxs-lookup"><span data-stu-id="6c720-104">Windows Mixed Reality Setup FAQ</span></span>

<span data-ttu-id="6c720-105">下面是一些信息，可帮助解决在设置 Windows Mixed Reality 沉浸式头戴式耳机时可能遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="6c720-105">Here’s some info to help troubleshoot problems you might run into when you set up your Windows Mixed Reality immersive headset.</span></span>

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a><span data-ttu-id="6c720-106">我收到一条消息，指出 "我们无法下载窗口混合现实软件"，或者安装程序卡在 "我们进行一些下载时挂起" 页面</span><span class="sxs-lookup"><span data-stu-id="6c720-106">I get a message that says “We couldn’t download the Window Mixed Reality software,” or setup is stuck on the “Hang tight while we do some downloading” page</span></span>

<span data-ttu-id="6c720-107">请尝试以下步骤：</span><span class="sxs-lookup"><span data-stu-id="6c720-107">Try the following steps:</span></span>

* <span data-ttu-id="6c720-108">转到 " **设置" > 更新 & 安全 > Windows 更新** ，并确保已打开 "Windows 更新"。</span><span class="sxs-lookup"><span data-stu-id="6c720-108">Go to **Settings  > Update & security > Windows Update** and make sure Windows Update is turned on.</span></span> <span data-ttu-id="6c720-109">然后，下载并安装任何等待安装的更新。</span><span class="sxs-lookup"><span data-stu-id="6c720-109">Then, download and install any updates that are waiting to be installed.</span></span>
* <span data-ttu-id="6c720-110">请确保你的电脑已连接到 internet，并且至少有 2 GB 的可用存储空间。</span><span class="sxs-lookup"><span data-stu-id="6c720-110">Make sure your PC is connected to the internet and has at least 2 GB of free storage space.</span></span>
* <span data-ttu-id="6c720-111">重启电脑，然后重试。</span><span class="sxs-lookup"><span data-stu-id="6c720-111">Restart your PC and try again.</span></span> <span data-ttu-id="6c720-112">可能需要重复几次，或者运行 Windows 更新疑难解答来清除挂起的更新。</span><span class="sxs-lookup"><span data-stu-id="6c720-112">You may need to repeat several times or run the Windows Update troubleshooter to clear pending updates.</span></span>

> [!NOTE]
> * <span data-ttu-id="6c720-113">如果你使用的是企业托管网络，请与你的管理员联系。</span><span class="sxs-lookup"><span data-stu-id="6c720-113">If you're on an enterprise managed network, check with your administrator.</span></span> <span data-ttu-id="6c720-114">它们可能需要启用 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="6c720-114">They might need to enable Windows Mixed Reality.</span></span> <span data-ttu-id="6c720-115">正在查找 IT pro 说明？</span><span class="sxs-lookup"><span data-stu-id="6c720-115">Looking for the IT pro instructions?</span></span> <span data-ttu-id="6c720-116">请参阅 **[此文](/windows/application-management/manage-windows-mixed-reality)**。</span><span class="sxs-lookup"><span data-stu-id="6c720-116">See **[this article](/windows/application-management/manage-windows-mixed-reality)**.</span></span>
> * <span data-ttu-id="6c720-117">如果 Wi-Fi 网络连接设置为 "按流量计费"，请将其更改为 "不按流量"。</span><span class="sxs-lookup"><span data-stu-id="6c720-117">If your Wi-Fi network connection is set to metered, change it to unmetered.</span></span> <span data-ttu-id="6c720-118">**[了解详细信息](https://support.microsoft.com/help/4028458)**</span><span class="sxs-lookup"><span data-stu-id="6c720-118">**[Learn more](https://support.microsoft.com/help/4028458)**</span></span>

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a><span data-ttu-id="6c720-119">我收到一条消息，指出出现 "出现错误，无法启动 Windows Mixed Reality"。</span><span class="sxs-lookup"><span data-stu-id="6c720-119">I get a message that says "Something went wrong, and we couldn't start Windows Mixed Reality."</span></span>

<span data-ttu-id="6c720-120">请尝试以下步骤：</span><span class="sxs-lookup"><span data-stu-id="6c720-120">Try the following steps:</span></span>

1. <span data-ttu-id="6c720-121">将耳机从计算机拔下 (两个电缆) 。</span><span class="sxs-lookup"><span data-stu-id="6c720-121">Unplug your headset from your computer (both cables).</span></span>
2. <span data-ttu-id="6c720-122">重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="6c720-122">Restart your computer.</span></span>
3. <span data-ttu-id="6c720-123">转到 " **设置" > 更新 & 安全 > Windows 更新** ，并确保已打开 "Windows 更新"。</span><span class="sxs-lookup"><span data-stu-id="6c720-123">Go **Settings  > Update & security > Windows Update** and make sure Windows Update is turned on.</span></span> <span data-ttu-id="6c720-124">然后，下载并安装任何等待安装的更新。</span><span class="sxs-lookup"><span data-stu-id="6c720-124">Then, download and install any updates that are waiting to be installed.</span></span>
4. <span data-ttu-id="6c720-125">将耳机重新连接到计算机，然后重试安装。</span><span class="sxs-lookup"><span data-stu-id="6c720-125">Reconnect your headset to the computer, then try setup again.</span></span>

<span data-ttu-id="6c720-126">如果上述步骤不起作用，请尝试卸载然后重新安装 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="6c720-126">If the above steps don’t work, try uninstalling and then reinstalling Windows Mixed Reality.</span></span> <span data-ttu-id="6c720-127">请参阅 " **设置" > 混合现实 > 卸载** 并选择 " **卸载**"。</span><span class="sxs-lookup"><span data-stu-id="6c720-127">Go to **Settings  > Mixed reality > Uninstall** and select **Uninstall**.</span></span> <span data-ttu-id="6c720-128">然后重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="6c720-128">Then restart your computer.</span></span> <span data-ttu-id="6c720-129">若要再次开始安装过程，只需将耳机插入 PC 即可。</span><span class="sxs-lookup"><span data-stu-id="6c720-129">To start the setup process again, just plug your headset into your PC.</span></span>

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a><span data-ttu-id="6c720-130">当我插入我的耳机时，混合现实门户不会打开</span><span class="sxs-lookup"><span data-stu-id="6c720-130">The Mixed Reality Portal doesn’t open when I plug in my headset</span></span>

<span data-ttu-id="6c720-131">混合现实门户是指通过 Windows Mixed Reality 安装程序的应用程序，它设计为在你插入兼容的耳机时自动打开。</span><span class="sxs-lookup"><span data-stu-id="6c720-131">Mixed Reality Portal, the app that takes you through Windows Mixed Reality setup, is designed to open automatically when you plug in a compatible headset.</span></span> <span data-ttu-id="6c720-132">如果未打开，请在 "搜索" 框中输入 "混合现实门户" 以打开应用。</span><span class="sxs-lookup"><span data-stu-id="6c720-132">If it doesn’t open, go to Start and type "Mixed Reality Portal" in the Search box to open the app.</span></span> <span data-ttu-id="6c720-133">如果找不到混合现实门户，可能需要 [更新到最新版本的 Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq) 。</span><span class="sxs-lookup"><span data-stu-id="6c720-133">You might need to [update to the latest version of Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq) if you can’t find the Mixed Reality Portal.</span></span>

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a><span data-ttu-id="6c720-134">我收到一条消息，指出我的 PC 无法运行 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6c720-134">I get a message that says my PC can’t run Windows Mixed Reality</span></span>

<span data-ttu-id="6c720-135">如果收到此消息，则你的电脑不满足运行 Windows Mixed Reality 所需的 [最低要求](https://support.microsoft.com/help/4039260) 。</span><span class="sxs-lookup"><span data-stu-id="6c720-135">If you get this message, your PC doesn’t meet the [minimum requirements](https://support.microsoft.com/help/4039260) needed to run Windows Mixed Reality.</span></span> <span data-ttu-id="6c720-136">计算机的硬件设置可能与 Windows Mixed Reality 不兼容，或者可能需要 [更新到最新版本的 windows](https://support.microsoft.com/help/12373)。</span><span class="sxs-lookup"><span data-stu-id="6c720-136">The computer’s hardware setup might not be compatible with Windows Mixed Reality, or you may need to [update to the latest version of Windows](https://support.microsoft.com/help/12373).</span></span>

<span data-ttu-id="6c720-137">图形卡说明：</span><span class="sxs-lookup"><span data-stu-id="6c720-137">Notes on graphics cards:</span></span>

* <span data-ttu-id="6c720-138">如果 Windows Mixed Reality 安装程序显示您的图形卡无法满足要求，而您认为图形卡有问题，请确保将您的耳机插入正确的卡。</span><span class="sxs-lookup"><span data-stu-id="6c720-138">If Windows Mixed Reality setup says your graphics card doesn’t meet the requirements and you think it does, make sure your headset is plugged into the correct card.</span></span>
* <span data-ttu-id="6c720-139">咨询您的图形卡制造商以获取最新的驱动程序更新。</span><span class="sxs-lookup"><span data-stu-id="6c720-139">Check with your graphics card manufacturer for the latest driver update.</span></span> <span data-ttu-id="6c720-140">Windows Mixed Reality 需要至少支持 WDDM 2.2 的图形卡驱动程序。</span><span class="sxs-lookup"><span data-stu-id="6c720-140">Windows Mixed Reality requires a graphics card driver that supports at least WDDM 2.2.</span></span>

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a><span data-ttu-id="6c720-141">我收到一条消息，指出： "你几乎在那里，这台电脑不满足运行 Windows Mixed Reality 所需的最低要求。"</span><span class="sxs-lookup"><span data-stu-id="6c720-141">I get a message that says, “You’re nearly there—this PC doesn’t meet the minimum requirements needed to run Windows Mixed Reality.”</span></span>

<span data-ttu-id="6c720-142">如果收到此消息，则表示您的 PC 不满足在 Windows Mixed Reality 中获得最佳体验所需的最低要求。</span><span class="sxs-lookup"><span data-stu-id="6c720-142">If you get this message, your PC doesn’t meet the minimum requirements needed for the best experience in Windows Mixed Reality.</span></span> <span data-ttu-id="6c720-143">你的电脑可以运行沉浸式耳机，但可能无法运行某些应用程序，或者可能存在性能问题。</span><span class="sxs-lookup"><span data-stu-id="6c720-143">Your PC can run an immersive headset, but may not be able to run certain apps or might have problems with performance.</span></span>

## <a name="my-xbox-controller-isnt-working"></a><span data-ttu-id="6c720-144">我的 Xbox 控制器不工作</span><span class="sxs-lookup"><span data-stu-id="6c720-144">My Xbox controller isn’t working</span></span>

<span data-ttu-id="6c720-145">请尝试以下步骤：</span><span class="sxs-lookup"><span data-stu-id="6c720-145">Try the following steps:</span></span>

* <span data-ttu-id="6c720-146">确保控制器已打开、完全充电并连接到 PC。</span><span class="sxs-lookup"><span data-stu-id="6c720-146">Make sure your controller is turned on, fully charged, and connected to the PC.</span></span>
* <span data-ttu-id="6c720-147">更换控制器的电池。</span><span class="sxs-lookup"><span data-stu-id="6c720-147">Replace the controller’s batteries.</span></span>
* <span data-ttu-id="6c720-148">如果你使用的是蓝牙控制器，请参阅 " **设置" > 设备 "> 蓝牙 & 其他设备** 上的" 设备 "，并确保其配对 (你应看到它在页面) 上列出。</span><span class="sxs-lookup"><span data-stu-id="6c720-148">If you're using a Bluetooth controller, go to **Settings  > Devices > Bluetooth & other devices** on your PC and make sure it's paired (you should see it listed on the page).</span></span>

[<span data-ttu-id="6c720-149">了解有关 Xbox 控制器的详细信息</span><span class="sxs-lookup"><span data-stu-id="6c720-149">Learn more about Xbox controllers</span></span>](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a><span data-ttu-id="6c720-150">运动控制器不起作用</span><span class="sxs-lookup"><span data-stu-id="6c720-150">My motion controllers aren't working</span></span>

<span data-ttu-id="6c720-151">请尝试以下步骤：</span><span class="sxs-lookup"><span data-stu-id="6c720-151">Try the following steps:</span></span>

* <span data-ttu-id="6c720-152">确保你的控制器已打开并完全充电。</span><span class="sxs-lookup"><span data-stu-id="6c720-152">Make sure your controllers are turned on and fully charged.</span></span>
* <span data-ttu-id="6c720-153">更换控制器电池。</span><span class="sxs-lookup"><span data-stu-id="6c720-153">Replace the controllers’ batteries.</span></span>
* <span data-ttu-id="6c720-154">将控制器保持在您的前方，同时关闭控制器并将其打开。</span><span class="sxs-lookup"><span data-stu-id="6c720-154">Turn the controllers off and on again while holding them in front of you.</span></span> <span data-ttu-id="6c720-155">按住 Windows 按钮4秒钟关闭控制器，然后再次按住该控制器2秒钟，以将其打开。</span><span class="sxs-lookup"><span data-stu-id="6c720-155">Press and hold the Windows  button for 4 seconds to turn off a controller, then press and hold it again for 2 seconds to turn it on.</span></span>
* <span data-ttu-id="6c720-156">请访问 " **设置" > 设备上 > 蓝牙 & 其他设备** 上的设备，并确保它们已配对， (应会看到页面) 上列出它们。</span><span class="sxs-lookup"><span data-stu-id="6c720-156">Go to **Settings  > Devices > Bluetooth & other devices** on your PC and make sure they’re paired (you should see them listed on the page).</span></span>

[<span data-ttu-id="6c720-157">了解有关运动控制器的详细信息</span><span class="sxs-lookup"><span data-stu-id="6c720-157">Learn more about motion controllers</span></span>](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a><span data-ttu-id="6c720-158">我收到一条消息，显示 "连接耳机"，即使我已插入我的耳机</span><span class="sxs-lookup"><span data-stu-id="6c720-158">I get a message that says, “Connect your headset” even though I’ve plugged in my headset</span></span>

<span data-ttu-id="6c720-159">请尝试以下步骤：</span><span class="sxs-lookup"><span data-stu-id="6c720-159">Try the following steps:</span></span>

- <span data-ttu-id="6c720-160">请确保将耳机连接到计算机上的正确端口。</span><span class="sxs-lookup"><span data-stu-id="6c720-160">Make sure your headset is connected to the correct ports on your computer.</span></span> <span data-ttu-id="6c720-161">它应插入到电脑的单独图形卡和 USB 3.0 端口。</span><span class="sxs-lookup"><span data-stu-id="6c720-161">It should be plugged into the PC’s discrete graphics card and a USB 3.0 port.</span></span> <span data-ttu-id="6c720-162">下面介绍如何识别正确的端口：</span><span class="sxs-lookup"><span data-stu-id="6c720-162">Here's how to identify the correct ports:</span></span>
    - <span data-ttu-id="6c720-163">USB 3.0 端口有一个特殊的徽标，其中 "SS" 标记 (表示 "SuperSpeed" ) 。</span><span class="sxs-lookup"><span data-stu-id="6c720-163">USB 3.0 ports have a special logo with an "SS" mark (indicating "SuperSpeed").</span></span> <span data-ttu-id="6c720-164">端口的内部片通常为蓝色，但较旧的 USB 2.0 端口通常为黑色或白色。</span><span class="sxs-lookup"><span data-stu-id="6c720-164">The port's inside piece is normally blue, but older USB 2.0 ports are typically black or white on the inside.</span></span>
    - <span data-ttu-id="6c720-165">如果计算机有两个 HDMI 端口，请使用连接到图形卡的端口，而不是计算机的主板。</span><span class="sxs-lookup"><span data-stu-id="6c720-165">If your computer has two HDMI ports, use the one that connects to the graphics card, not the computer's motherboard.</span></span> <span data-ttu-id="6c720-166">这并不总是显而易见的，尽管离散端口通常位于计算机上的扩展插槽中。</span><span class="sxs-lookup"><span data-stu-id="6c720-166">It's not always obvious, which is which, though discrete ports are often located in an expansion slot on the computer.</span></span> <span data-ttu-id="6c720-167">如果尝试一个端口但它不起作用，请尝试其他端口。</span><span class="sxs-lookup"><span data-stu-id="6c720-167">If you try one port and it doesn't work, try the other.</span></span>
- <span data-ttu-id="6c720-168">请参阅耳机制造商的网站并更新耳机的驱动程序和固件。</span><span class="sxs-lookup"><span data-stu-id="6c720-168">Go to the headset manufacturer’s website and update the drivers and firmware for your headset.</span></span>

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a><span data-ttu-id="6c720-169">在混合现实启动过程中，我停滞在 "转向你的一端，然后在地板"</span><span class="sxs-lookup"><span data-stu-id="6c720-169">During Mixed Reality start up, I'm stuck at "Turn your head side to side, and then at the floor"</span></span>

<span data-ttu-id="6c720-170">此步骤允许耳机识别空间，并还原任何现有的虚拟楼层和边界。</span><span class="sxs-lookup"><span data-stu-id="6c720-170">This step lets your headset recognize your space and restore any existing virtual floor and boundary.</span></span> <span data-ttu-id="6c720-171">当你放在你的耳机上时，此扫描过程可能需要长达10秒的时间。</span><span class="sxs-lookup"><span data-stu-id="6c720-171">When you put on your headset, this scanning process can take up to 10 seconds.</span></span> <span data-ttu-id="6c720-172">完成后，你将处于 Windows Mixed Reality 主页，否则系统将提示你重新设置边界。</span><span class="sxs-lookup"><span data-stu-id="6c720-172">After it's complete, you'll either be in Windows Mixed Reality home or you'll be prompted to set up your boundary again.</span></span>

<span data-ttu-id="6c720-173">如果扫描过程所用时间超过10秒，则耳机中的邻近感应传感器可能出现问题：</span><span class="sxs-lookup"><span data-stu-id="6c720-173">If the scanning process takes longer than 10 seconds, there could be a problem with the proximity sensor in the headset:</span></span>

1. <span data-ttu-id="6c720-174">检查是否已从邻近感应传感器中删除不干胶标签。</span><span class="sxs-lookup"><span data-stu-id="6c720-174">Check that the sticker has been removed from the proximity sensor.</span></span> <span data-ttu-id="6c720-175">邻近感应感应器位于耳机内，大致位于 forehead 的中心。</span><span class="sxs-lookup"><span data-stu-id="6c720-175">The proximity sensor is located inside the headset roughly where the center of your forehead would be.</span></span>
2. <span data-ttu-id="6c720-176">检查邻近感应传感器是否正在将输入切换到你的耳机：使用手指覆盖并抽出几次近程传感器，验证输入是否正在切换到耳机。</span><span class="sxs-lookup"><span data-stu-id="6c720-176">Check that your proximity sensor is toggling input to your headset: with your finger, cover and uncover the proximity sensor a few times to verify input is switching to the headset.</span></span> <span data-ttu-id="6c720-177">你应在电脑顶部看到 " **Windows 键 + Y** " 横幅。</span><span class="sxs-lookup"><span data-stu-id="6c720-177">You should see the **Windows Key + Y** banner at the top of your PC.</span></span> <span data-ttu-id="6c720-178">您可以通过在键盘上键入 **Windows Key + Y** ，随时手动切换到耳机的输入。</span><span class="sxs-lookup"><span data-stu-id="6c720-178">You can manually switch input to the headset at any time by typing **Windows Key + Y** on your keyboard.</span></span>

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a><span data-ttu-id="6c720-179">我的 Windows Mixed Reality 主页的底层看起来不是正确的高度</span><span class="sxs-lookup"><span data-stu-id="6c720-179">The floor of my Windows Mixed Reality home doesn't appear to be at the correct height</span></span>

<span data-ttu-id="6c720-180">选择 **开始 > 楼层调整**，一旦将应用放入世界，就会启动，以便在戴上耳机时进行更改。</span><span class="sxs-lookup"><span data-stu-id="6c720-180">Select **Start > Floor Adjustment**, which will launch once you place the app in the world, to make changes while you're wearing the headset.</span></span> <span data-ttu-id="6c720-181">在此应用中，你将被定向到使用触摸板 (运动控制器) 或方向板 (游戏板) 调整地面高度。</span><span class="sxs-lookup"><span data-stu-id="6c720-181">In this app, you'll be directed to use the touch pad (motion controller) or direction pad (gamepad) to adjust the floor height.</span></span> <span data-ttu-id="6c720-182">如果地面正确，请使用 Windows 按钮返回到你的主页。</span><span class="sxs-lookup"><span data-stu-id="6c720-182">When the floor feels correct, use the Windows button to return to your home.</span></span>

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a><span data-ttu-id="6c720-183">我无法在我的桌面上显示我在我的耳机上看到的内容的预览</span><span class="sxs-lookup"><span data-stu-id="6c720-183">I can't show a preview of what I'm seeing in my headset on my desktop</span></span>

<span data-ttu-id="6c720-184">Windows Mixed Reality 门户在屏幕底部有一个 " **播放** " 按钮，可让你在桌面屏幕上预览你在手机上看到的内容。</span><span class="sxs-lookup"><span data-stu-id="6c720-184">Windows Mixed Reality Portal has a **Play** button at the bottom of the screen that allows you to preview what you're seeing in your headset on your desktop screen.</span></span> <span data-ttu-id="6c720-185">出于性能方面的考虑，此功能仅适用于在 Windows Mixed Reality 上运行的 Pc 上的 Ultra (90 Hz) 。</span><span class="sxs-lookup"><span data-stu-id="6c720-185">For performance reasons, this feature is only available on PCs running at Windows Mixed Reality Ultra (90 Hz).</span></span>

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a><span data-ttu-id="6c720-186">如何在我的耳机中获得更清晰的视图</span><span class="sxs-lookup"><span data-stu-id="6c720-186">How can I get a clearer view in my headset</span></span>

<span data-ttu-id="6c720-187">尝试调整耳机大小。</span><span class="sxs-lookup"><span data-stu-id="6c720-187">Try adjusting the fit of your headset.</span></span> <span data-ttu-id="6c720-188">通过向上、向下或向左和向右移动，调整传送带的位置，并调整传送带，使其感觉 snug。</span><span class="sxs-lookup"><span data-stu-id="6c720-188">Adjust its position on your face by moving it up and down or left and right, and adjust the straps so it feels snug.</span></span>

<span data-ttu-id="6c720-189">如果耳机支持，还可以调整其校准设置。</span><span class="sxs-lookup"><span data-stu-id="6c720-189">If your headset supports it, you can also adjust its calibration settings.</span></span> <span data-ttu-id="6c720-190">如果头戴式耳机有调整校准的旋钮，请使用。</span><span class="sxs-lookup"><span data-stu-id="6c720-190">If the headset has a knob to adjust calibration, use that.</span></span> <span data-ttu-id="6c720-191">如果没有，请参阅 " **设置" > 混合现实 > 视觉质量** 并调整其中的校准。</span><span class="sxs-lookup"><span data-stu-id="6c720-191">If it doesn’t, go to **Settings  > Mixed reality > Visual quality** and adjust the calibration there.</span></span> <span data-ttu-id="6c720-192">有关特定设备的校准的详细信息，请与耳机制造商联系。</span><span class="sxs-lookup"><span data-stu-id="6c720-192">For more information on calibration for your specific device, check with your headset manufacturer.</span></span>

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a><span data-ttu-id="6c720-193">当我插入我的耳机时，无任何反应—混合现实门户不会打开</span><span class="sxs-lookup"><span data-stu-id="6c720-193">When I plug in my headset, nothing happens—Mixed Reality Portal doesn’t open</span></span>

<span data-ttu-id="6c720-194">混合现实门户是指通过 Windows Mixed Reality 安装程序的应用程序，它设计为在你插入兼容的耳机时自动打开。</span><span class="sxs-lookup"><span data-stu-id="6c720-194">Mixed Reality Portal, the app that takes you through Windows Mixed Reality setup, is designed to open automatically when you plug in a compatible headset.</span></span> <span data-ttu-id="6c720-195">如果未打开，请在 **搜索** 框中转到 "**开始**" 并键入 "**混合现实门户**"，打开该应用。</span><span class="sxs-lookup"><span data-stu-id="6c720-195">If it doesn’t open, go to **Start** and type **Mixed Reality Portal** in the **Search**  box to open the app from there.</span></span> <span data-ttu-id="6c720-196">如果找不到混合现实门户，这可能意味着您需要 [更新到最新版本的 Windows](https://support.microsoft.com/help/12373) ，或者您的耳机未正确连接到 PC。</span><span class="sxs-lookup"><span data-stu-id="6c720-196">If you can’t find Mixed Reality Portal, that might mean you need to [update to the latest version of Windows](https://support.microsoft.com/help/12373) or that your headset isn't correctly connected to the PC.</span></span>

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a><span data-ttu-id="6c720-197">我的 head 装入显示在关闭并快速启动后无法正常工作</span><span class="sxs-lookup"><span data-stu-id="6c720-197">My head mount display doesn't work after I shut down and do a fast startup</span></span>

<span data-ttu-id="6c720-198">试试看：</span><span class="sxs-lookup"><span data-stu-id="6c720-198">Try this:</span></span>

* <span data-ttu-id="6c720-199">从打印头安装显示器拔下显示电缆和 USB 电缆，然后将其插回。</span><span class="sxs-lookup"><span data-stu-id="6c720-199">Unplug the display cable and the USB cable from the head mount display and then plug them back in.</span></span>

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a><span data-ttu-id="6c720-200">使用 Windows Mixed Reality 时，Wi-Fi 会减缓</span><span class="sxs-lookup"><span data-stu-id="6c720-200">My Wi-Fi slows down when I use Windows Mixed Reality</span></span>

<span data-ttu-id="6c720-201">如果使用的是 2.4 GHz Wi-Fi 连接，则运动控制器可能会减慢 Wi-fi 的速度。</span><span class="sxs-lookup"><span data-stu-id="6c720-201">If you're using a 2.4-GHz Wi-Fi connection, your motion controllers might slow down your Wi-Fi.</span></span> <span data-ttu-id="6c720-202">请尝试执行以下步骤之一：</span><span class="sxs-lookup"><span data-stu-id="6c720-202">Try one of the following steps:</span></span>

* <span data-ttu-id="6c720-203">切换到 5 GHz Wi-Fi 连接（如果有）。</span><span class="sxs-lookup"><span data-stu-id="6c720-203">Switch to a 5-GHz Wi-Fi connection, if one is available.</span></span> <span data-ttu-id="6c720-204">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="6c720-204">Learn more</span></span>
* <span data-ttu-id="6c720-205">使用单独的蓝牙适配器将运动控制器连接到您的 PC。</span><span class="sxs-lookup"><span data-stu-id="6c720-205">Use a separate Bluetooth adapter to connect your motion controllers to your PC.</span></span> [<span data-ttu-id="6c720-206">查看建议的适配器</span><span class="sxs-lookup"><span data-stu-id="6c720-206">See recommended adapters</span></span>](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> <span data-ttu-id="6c720-207">较新的耳机对通过内置的蓝牙芯片直接通过内置的蓝牙芯片，而不会遇到此问题。</span><span class="sxs-lookup"><span data-stu-id="6c720-207">Newer headsets pair directly to the controllers through a built-in Bluetooth chip and shouldn’t experience this issue.</span></span>

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a><span data-ttu-id="6c720-208">我收到 "出现错误" 错误消息，或在混合现实门户中遇到问题</span><span class="sxs-lookup"><span data-stu-id="6c720-208">I got a "Something went wrong" error message, or I'm having problems in the Mixed Reality Portal</span></span>

<span data-ttu-id="6c720-209">若要获取有关特定错误代码的详细信息，请查看 [此处](error-codes.md)。</span><span class="sxs-lookup"><span data-stu-id="6c720-209">To get more information about a specific error code, look [here](error-codes.md).</span></span> <span data-ttu-id="6c720-210">你还可以尝试：</span><span class="sxs-lookup"><span data-stu-id="6c720-210">You can also try to:</span></span>

<span data-ttu-id="6c720-211">重启 Windows Mixed Reality：</span><span class="sxs-lookup"><span data-stu-id="6c720-211">Restart Windows Mixed Reality:</span></span>

1. <span data-ttu-id="6c720-212">从电脑拔下耳机电缆。</span><span class="sxs-lookup"><span data-stu-id="6c720-212">Disconnect both headset cables from your PC.</span></span>
2. <span data-ttu-id="6c720-213">重启你的电脑。</span><span class="sxs-lookup"><span data-stu-id="6c720-213">Restart your PC.</span></span>
3. <span data-ttu-id="6c720-214">重新连接耳机。</span><span class="sxs-lookup"><span data-stu-id="6c720-214">Reconnect your headset.</span></span>

<span data-ttu-id="6c720-215">确保你的电脑能识别你的耳机：</span><span class="sxs-lookup"><span data-stu-id="6c720-215">Make sure that your PC recognizes your headset:</span></span>

1. <span data-ttu-id="6c720-216">选择“启动”。</span><span class="sxs-lookup"><span data-stu-id="6c720-216">Select Start.</span></span>
2. <span data-ttu-id="6c720-217">在搜索框中键入 "设备管理器"，并在列表中选择它。</span><span class="sxs-lookup"><span data-stu-id="6c720-217">Type "Device Manager" in the search box and select it in the list.</span></span>
3. <span data-ttu-id="6c720-218">展开 "Mixed reality 设备"，并查看是否列出了你的耳机。</span><span class="sxs-lookup"><span data-stu-id="6c720-218">Expand "Mixed reality devices" and see if your headset is listed.</span></span>

<span data-ttu-id="6c720-219">如果未列出：</span><span class="sxs-lookup"><span data-stu-id="6c720-219">If it isn't listed:</span></span>

1. <span data-ttu-id="6c720-220">将耳机插入电脑上的不同端口（如果可用）。</span><span class="sxs-lookup"><span data-stu-id="6c720-220">Plug the headset into different ports on the PC, if available.</span></span>
2. <span data-ttu-id="6c720-221">查看 Windows 更新中的最新软件更新。</span><span class="sxs-lookup"><span data-stu-id="6c720-221">Check for the latest software updates from Windows Update.</span></span>
3. <span data-ttu-id="6c720-222">卸载并重新安装 Windows Mixed Reality：</span><span class="sxs-lookup"><span data-stu-id="6c720-222">Uninstall and reinstall Windows Mixed Reality:</span></span>
    1. <span data-ttu-id="6c720-223">从电脑拔下耳机电缆。</span><span class="sxs-lookup"><span data-stu-id="6c720-223">Disconnect both headset cables from your PC.</span></span>
    2. <span data-ttu-id="6c720-224">选择 " **设置" > 混合现实 > 卸载**"。</span><span class="sxs-lookup"><span data-stu-id="6c720-224">Select **Settings  > Mixed reality > Uninstall**.</span></span>
    3. <span data-ttu-id="6c720-225">如果运动控制器与电脑配对，请选择 " **设置" > 设备 > 蓝牙 & 其他设备** 进行取消配对。</span><span class="sxs-lookup"><span data-stu-id="6c720-225">If your motion controllers are paired to your PC, select **Settings  > Devices  > Bluetooth & other devices** to unpair them.</span></span> <span data-ttu-id="6c720-226">选择每个控制器，然后选择 "删除设备"。</span><span class="sxs-lookup"><span data-stu-id="6c720-226">Select each controller, and "Remove device".</span></span> <span data-ttu-id="6c720-227">如果控制器与耳机配对，则可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="6c720-227">If your controllers are paired to your headset, you can skip this step.</span></span>
    4. <span data-ttu-id="6c720-228">将您的耳机插回您的 PC 上，重新安装 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="6c720-228">Plug your headset back into your PC to reinstall Windows Mixed Reality.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c720-229">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c720-229">See also</span></span>

* [<span data-ttu-id="6c720-230">询问社区</span><span class="sxs-lookup"><span data-stu-id="6c720-230">Ask the community</span></span>](https://answers.microsoft.com)
* [<span data-ttu-id="6c720-231">联系我们以获取支持</span><span class="sxs-lookup"><span data-stu-id="6c720-231">Contact us for support</span></span>](https://support.microsoft.com/contactus/)
* [<span data-ttu-id="6c720-232">疑难解答</span><span class="sxs-lookup"><span data-stu-id="6c720-232">Troubleshooting</span></span>](troubleshooting-windows-mixed-reality.md)