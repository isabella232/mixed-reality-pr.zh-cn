---
title: 将 SteamVR 与 Windows Mixed Reality
description: 了解如何在具有兼容电脑的 Windows Mixed Reality和控制器上设置和播放 SteamVR 游戏。
ms.topic: article
keywords: Windows Mixed Reality、混合现实、虚拟现实、VR、MR、游戏、SteamVR、流、系统要求
ms.openlocfilehash: 0d79b0c2079875b32387d616e77c5f497ab4aa59
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110149"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a><span data-ttu-id="b04d4-104">将 SteamVR 与 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b04d4-104">Using SteamVR with Windows Mixed Reality</span></span>

<span data-ttu-id="b04d4-105">Windows Mixed Reality使用 SteamVR，用户可以在沉浸式头戴显示设备Windows Mixed Reality SteamVR 体验。</span><span class="sxs-lookup"><span data-stu-id="b04d4-105">Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="b04d4-106">安装适用于 SteamVR Windows Mixed Reality后，用户可以从桌面或 Steam 库启动其最喜欢的 SteamVR 应用程序，并直接在 Windows 头戴显示设备上播放它们。</span><span class="sxs-lookup"><span data-stu-id="b04d4-106">After installing the Windows Mixed Reality for SteamVR, users can launch their favorite SteamVR applications from their desktop or Steam library and play them directly on their Windows headset.</span></span>

## <a name="get-your-pc-ready"></a><span data-ttu-id="b04d4-107">准备好电脑</span><span class="sxs-lookup"><span data-stu-id="b04d4-107">Get your PC ready</span></span>

* <span data-ttu-id="b04d4-108">确保没有挂起的更新：选择"启动">"设置 **>"&"> Windows 更新"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-108">Make sure you have no pending updates: Select **Start > Settings > Update & Security > Windows Update**.</span></span> <span data-ttu-id="b04d4-109">如果更新可用，请选择"**立即安装"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-109">If updates are available, select **Install now**.</span></span> <span data-ttu-id="b04d4-110">如果没有可用的更新，请选择 **"检查更新"，** 然后安装任何新更新。</span><span class="sxs-lookup"><span data-stu-id="b04d4-110">If no updates are available, select **Check for updates**, and then install any new ones.</span></span>
* <span data-ttu-id="b04d4-111">Pc 要求因 Steam 上的应用和内容而异。</span><span class="sxs-lookup"><span data-stu-id="b04d4-111">PC requirements vary for the apps and content on Steam.</span></span> <span data-ttu-id="b04d4-112">请参阅每个标题的最低要求。</span><span class="sxs-lookup"><span data-stu-id="b04d4-112">See the minimum requirements per title.</span></span> <span data-ttu-id="b04d4-113">具有 GTX 1070 图形卡 (或等效) 和 Intel® Core™ i7 处理器的电脑应为各种标题提供良好的体验。</span><span class="sxs-lookup"><span data-stu-id="b04d4-113">A PC with a GTX 1070 graphics card (or equivalent) and an Intel® Core™ i7 processor should offer a good experience for a broad range of titles.</span></span>
* <span data-ttu-id="b04d4-114">设置 [Windows Mixed Reality（](set-up-windows-mixed-reality.md) 如果尚未设置）。</span><span class="sxs-lookup"><span data-stu-id="b04d4-114">Set up up [Windows Mixed Reality](set-up-windows-mixed-reality.md) if you haven't already.</span></span> 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a><span data-ttu-id="b04d4-115">为 SteamVR Windows Mixed Reality设置服务</span><span class="sxs-lookup"><span data-stu-id="b04d4-115">Set up Windows Mixed Reality for SteamVR</span></span>

1. [<span data-ttu-id="b04d4-116">下载并安装 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="b04d4-116">Download and install SteamVR.</span></span>](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. <span data-ttu-id="b04d4-117">准备就绪后，启动 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="b04d4-117">When ready, start SteamVR.</span></span> <span data-ttu-id="b04d4-118">SteamVR 教程应会自动启动。</span><span class="sxs-lookup"><span data-stu-id="b04d4-118">The SteamVR Tutorial should start automatically.</span></span>

> <span data-ttu-id="b04d4-119">**注意：** 对于 SteamVR 设置的高级故障排除，请确保已安装以下软件组件：</span><span class="sxs-lookup"><span data-stu-id="b04d4-119">**Note:** For advanced troubleshooting of your SteamVR setup, make sure you have the following software components installed:</span></span>
> 1. <span data-ttu-id="b04d4-120">安装 [Steam](http://store.steampowered.com/about/) **并登录\*\*\*\*或创建新帐户。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-120">Install [Steam](http://store.steampowered.com/about/) and **login** or **create a new account.**</span></span>
> 2. <span data-ttu-id="b04d4-121">安装 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)。</span><span class="sxs-lookup"><span data-stu-id="b04d4-121">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).</span></span> <span data-ttu-id="b04d4-122">插入头戴显示设备后，启动"Steam"，应会看到一个提示你安装 SteamVR 的对话框。</span><span class="sxs-lookup"><span data-stu-id="b04d4-122">With your headset plugged in, launch Steam and you should see a dialog prompting you to install SteamVR.</span></span> <span data-ttu-id="b04d4-123">按照对话框中的提示进行安装。</span><span class="sxs-lookup"><span data-stu-id="b04d4-123">Follow the prompts on the dialog to install it.</span></span>
    * <span data-ttu-id="b04d4-124">如果看不到弹出窗口，请导航到库 的"工具"部分来安装 *SteamVR。*</span><span class="sxs-lookup"><span data-stu-id="b04d4-124">If you don't see the popup, install SteamVR by navigating to the *Tools* section of your *library*.</span></span> <span data-ttu-id="b04d4-125">在列表中找到"SteamVR"，然后右键单击并选择"*安装游戏"。*</span><span class="sxs-lookup"><span data-stu-id="b04d4-125">Locate SteamVR in the list and then right-click and select *Install Game*.</span></span>
> 3. <span data-ttu-id="b04d4-126">安装[Windows Mixed Reality适用于 SteamVR 的 。](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="b04d4-126">Install [Windows Mixed Reality for SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).</span></span>

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a><span data-ttu-id="b04d4-127">在Windows Mixed Reality Internet 访问的环境中为 SteamVR 设置连接</span><span class="sxs-lookup"><span data-stu-id="b04d4-127">Set up Windows Mixed Reality for SteamVR in an environment without internet access</span></span>

<span data-ttu-id="b04d4-128">**在可移植存储设备上存储必要的介质**</span><span class="sxs-lookup"><span data-stu-id="b04d4-128">**Store the necessary media on a portable storage device**</span></span>
1. <span data-ttu-id="b04d4-129">按照 [上述Windows Mixed Reality](https://store.steampowered.com/app/250820/SteamVR/) 在具有完全 Internet 访问权限的电脑上使用 SteamVR 安装 [SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) 和适用于 [SteamVR](http://store.steampowered.com/about/) 的客户端。</span><span class="sxs-lookup"><span data-stu-id="b04d4-129">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/) and [Windows Mixed Reality for SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) as directed above using [Steam](http://store.steampowered.com/about/) on a PC with full internet access.</span></span>
2. <span data-ttu-id="b04d4-130">在"Steam"中，打开"库"部分，找到标记为"工具"的部分。</span><span class="sxs-lookup"><span data-stu-id="b04d4-130">In Steam, open the Library section and find the part labeled "Tools".</span></span>
3. <span data-ttu-id="b04d4-131">安装 SteamVR 后，右键单击条目"SteamVR"，在生成的弹出菜单中，单击条目"属性"。</span><span class="sxs-lookup"><span data-stu-id="b04d4-131">Once SteamVR is installed, right-click the entry "SteamVR" and in the resulting popup menu, click on the entry "Properties".</span></span>
4. <span data-ttu-id="b04d4-132">将打开包含多个选项卡的新窗口。</span><span class="sxs-lookup"><span data-stu-id="b04d4-132">A new window with multiple tabs will open.</span></span> <span data-ttu-id="b04d4-133">选择选项卡"本地文件"，然后单击标记为"浏览本地文件"的按钮。</span><span class="sxs-lookup"><span data-stu-id="b04d4-133">Select the tab "LOCAL FILES" and click on the button labeled "BROWSE LOCAL FILES".</span></span>
5. <span data-ttu-id="b04d4-134">将打开包含 SteamVR 运行时的目录。</span><span class="sxs-lookup"><span data-stu-id="b04d4-134">The directory containing the SteamVR Runtime will open.</span></span> <span data-ttu-id="b04d4-135">将名为"SteamVR ("的整个) 复制到你选择的可移植介质上 (例如 USB u 盘) 。</span><span class="sxs-lookup"><span data-stu-id="b04d4-135">Copy this entire directory (named SteamVR) onto a portable medium of your choice (e.g. a USB thumb drive).</span></span>
6. <span data-ttu-id="b04d4-136">对于 SteamVR Windows Mixed Reality，以及要安装在目标电脑上的任何与 SteamVR 兼容的应用，请执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="b04d4-136">Do the same with Windows Mixed Reality for SteamVR, and any SteamVR-compatible apps you would like to install on the target PC.</span></span>

<span data-ttu-id="b04d4-137">**在目标电脑上运行 SteamVR**</span><span class="sxs-lookup"><span data-stu-id="b04d4-137">**Run SteamVR on the target PC**</span></span>
1. <span data-ttu-id="b04d4-138">将便携式存储设备插入目标电脑后，将 SteamVR、MixedRealityVRDriver 和其他文件夹移到目标电脑上的方便位置。</span><span class="sxs-lookup"><span data-stu-id="b04d4-138">After plugging the portable storage device into the target PC, move the SteamVR, MixedRealityVRDriver, and other folders to a convenient place on the target PC.</span></span>
<span data-ttu-id="b04d4-139">![在目标电脑上Windows Mixed Reality的 SteamVR 和适用于 SteamVR 的流](images/steamvr-install-files.png)</span><span class="sxs-lookup"><span data-stu-id="b04d4-139">![SteamVR and Windows Mixed Reality for SteamVR installed on target PC](images/steamvr-install-files.png)</span></span>

2. <span data-ttu-id="b04d4-140">确保 SteamVR 和 MixedRealityVRDriver 在同一文件夹中，打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="b04d4-140">Ensuring SteamVR and MixedRealityVRDriver are in the same folder, open a command prompt.</span></span> <span data-ttu-id="b04d4-141">对于此示例，我们假设包含文件夹位于 *C：\SteamVRInstall*。</span><span class="sxs-lookup"><span data-stu-id="b04d4-141">For the sake of this example, we will assume the containing folder is at *C:\SteamVRInstall*.</span></span> <span data-ttu-id="b04d4-142">在这种情况下，应在命令提示符下运行：</span><span class="sxs-lookup"><span data-stu-id="b04d4-142">In that case, in the command prompt you should run:</span></span>
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
<span data-ttu-id="b04d4-143"> (请注意，如果运行的是 32 位版本的 Windows，则上述路径的部分 `win64` `win32` 应为 。) </span><span class="sxs-lookup"><span data-stu-id="b04d4-143">(Note that if you're running a 32-bit version of Windows, the `win64` part of the path above should be `win32` instead.)</span></span>

<span data-ttu-id="b04d4-144">这将允许运行时在自定义Windows Mixed Reality中查找适用于 SteamVR 驱动程序的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="b04d4-144">This will allow the runtime to find the Windows Mixed Reality for SteamVR driver in your custom installation.</span></span>

4. <span data-ttu-id="b04d4-145">若要运行 SteamVR，应双击位于SteamVR\bin\win64\vrstartup.exe的文件 *"vrstartup.exe";* 如果目标电脑运行的是 32 位版本的 *Windows，* 则双击SteamVR\bin\win32\vrstartup.exe。</span><span class="sxs-lookup"><span data-stu-id="b04d4-145">In order to run SteamVR you should double-click the file "vrstartup.exe" located at *SteamVR\bin\win64\vrstartup.exe*, or *SteamVR\bin\win32\vrstartup.exe* if the target PC is running a 32-bit version of Windows.</span></span>

<span data-ttu-id="b04d4-146">有关详细信息 [和故障排除，请参阅 Steamworks 文档页](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)。</span><span class="sxs-lookup"><span data-stu-id="b04d4-146">See the [Steamworks documentation page for more information and troubleshooting](https://partner.steamgames.com/doc/features/steamvr/enterprise#2).</span></span>

## <a name="play-steamvr-games"></a><span data-ttu-id="b04d4-147">播放 SteamVR 游戏</span><span class="sxs-lookup"><span data-stu-id="b04d4-147">Play SteamVR games</span></span>

1. <span data-ttu-id="b04d4-148">将头戴显示设备连接到电脑并打开运动控制器。</span><span class="sxs-lookup"><span data-stu-id="b04d4-148">Connect your headset to your PC and turn on your motion controllers.</span></span>
2. <span data-ttu-id="b04d4-149">加载Windows Mixed Reality控制器后，在桌面上打开 Steam 应用。</span><span class="sxs-lookup"><span data-stu-id="b04d4-149">Once the Windows Mixed Reality home has loaded and your controllers are visible, open the Steam app on your desktop.</span></span>
3. <span data-ttu-id="b04d4-150">使用 Steam 应用从 Steam 库启动 SteamVR 游戏。</span><span class="sxs-lookup"><span data-stu-id="b04d4-150">Use the Steam app to launch a SteamVR game from your Steam library.</span></span>

<span data-ttu-id="b04d4-151">**提示**：若要在不关闭头戴显示设备的情况下启动 SteamVR 游戏，请使用桌面应用 (**启动 > Desktop**) 在 Windows Mixed Reality 中查看电脑桌面并与之Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="b04d4-151">**Tip**: To launch SteamVR games without taking off your headset, use the Desktop app (**Start > Desktop**) to view and interact with your PC desktop inside Windows Mixed Reality.</span></span>

## <a name="using-motion-controllers-with-steamvr"></a><span data-ttu-id="b04d4-152">将运动控制器与 SteamVR 一起使用</span><span class="sxs-lookup"><span data-stu-id="b04d4-152">Using Motion Controllers with SteamVR</span></span>

<span data-ttu-id="b04d4-153">你将在不同的游戏中以不同方式使用运动控制器。</span><span class="sxs-lookup"><span data-stu-id="b04d4-153">You'll use your motion controllers differently in different games.</span></span> <span data-ttu-id="b04d4-154">下面是一些可帮助你入门的基础知识：</span><span class="sxs-lookup"><span data-stu-id="b04d4-154">Here are a few basics to help you get started:</span></span>

* <span data-ttu-id="b04d4-155">若要打开"流"仪表板，请直接按下左侧或右侧滚动块。</span><span class="sxs-lookup"><span data-stu-id="b04d4-155">To open the Steam dashboard, press straight down on the left or right thumbstick.</span></span>
* <span data-ttu-id="b04d4-156">若要退出 SteamVR 游戏并返回到Windows Mixed Reality，请按 Windows 按钮。</span><span class="sxs-lookup"><span data-stu-id="b04d4-156">To exit a SteamVR game and return to the Windows Mixed Reality home, press the Windows button.</span></span>

## <a name="changing-the-resolution"></a><span data-ttu-id="b04d4-157">更改分辨率</span><span class="sxs-lookup"><span data-stu-id="b04d4-157">Changing the resolution</span></span>

<span data-ttu-id="b04d4-158">如果希望以更高的分辨率播放游戏，随时可以在"SteamVR"->"设置"->"应用程序"窗口中调整"应用程序解析"滑块。</span><span class="sxs-lookup"><span data-stu-id="b04d4-158">You can adjust the Application Resolution slider in the SteamVR -> Settings -> Applications window at any time if you'd like to play games at a higher resolution.</span></span> <span data-ttu-id="b04d4-159">\*\*使用分辨率更高的乘数时，可以预期游戏对电脑造成更大压力。</span><span class="sxs-lookup"><span data-stu-id="b04d4-159">\*\*When using a higher resolution multiplier you can expect the game to put more strain on your PC.</span></span> <span data-ttu-id="b04d4-160">如果增加乘数并看到性能下降，请重新将滑块调整为默认级别，然后重启游戏以确保更改生效。</span><span class="sxs-lookup"><span data-stu-id="b04d4-160">If you increase the multiplier and see degraded performance, readjust the slider to the default level and restart the game to ensure that the change takes effect.</span></span>![调整应用程序分辨率](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a><span data-ttu-id="b04d4-162">使用多个头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="b04d4-162">Using multiple headsets</span></span>

<span data-ttu-id="b04d4-163">如果你是 VR 运动家，可以定期在同一电脑上使用多个 VR 头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="b04d4-163">If you're a VR enthusiast, you might regularly use more than one VR headset on the same PC.</span></span> <span data-ttu-id="b04d4-164">如果是这种情况，请注意，当插入 Windows Mixed Reality头戴显示设备时，SteamVR 游戏将始终启动到 Windows Mixed Reality头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="b04d4-164">If that's the case note that when a Windows Mixed Reality headset is plugged in, SteamVR games will always launch to the Windows Mixed Reality headset.</span></span> <span data-ttu-id="b04d4-165">如果要在另一个头戴显示设备上启动 SteamVR 游戏，请确保在继续操作Windows Mixed Reality头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="b04d4-165">If you'd like to launch SteamVR games on another headset make sure to first unplug the Windows Mixed Reality headset before continuing.</span></span>

## <a name="preview-programs"></a><span data-ttu-id="b04d4-166">预览程序</span><span class="sxs-lookup"><span data-stu-id="b04d4-166">Preview programs</span></span>

<span data-ttu-id="b04d4-167">我们发布定期更新，以提高在沉浸式头戴显示设备上使用 SteamVR Windows Mixed Reality可靠性和整体体验。</span><span class="sxs-lookup"><span data-stu-id="b04d4-167">We release regular updates to improve the performance, reliability, and overall experience of using SteamVR on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="b04d4-168">尽管这些预览计划都不需要，但如果希望更快、更频繁地获取更新，我们建议你加入它们 (并提供有关这些更新的反馈！) 。</span><span class="sxs-lookup"><span data-stu-id="b04d4-168">While none of these preview programs are required, we encourage you to join them if you would like to get updates sooner and more frequently (and give us feedback on those updates!).</span></span>

### <a name="windows-mixed-reality-for-steamvr-beta"></a><span data-ttu-id="b04d4-169">Windows Mixed Reality SteamVR Beta 版本</span><span class="sxs-lookup"><span data-stu-id="b04d4-169">Windows Mixed Reality for SteamVR Beta</span></span>

<span data-ttu-id="b04d4-170">Windows Mixed Reality适用于 SteamVR 的组件是从 Steam Store 安装的组件，使 SteamVR 能够与 Windows Mixed Reality头戴显示设备一起工作。</span><span class="sxs-lookup"><span data-stu-id="b04d4-170">Windows Mixed Reality for SteamVR is the component you install from the Steam Store that enables SteamVR to work with your Windows Mixed Reality headset.</span></span>  <span data-ttu-id="b04d4-171">我们会定期发布对此"网桥"的更新，而 Steam 会自动安装更新。</span><span class="sxs-lookup"><span data-stu-id="b04d4-171">We publish updates to this "bridge" regularly and Steam installs them automatically.</span></span>

<span data-ttu-id="b04d4-172">如果希望更频繁地获取更新，我们建议你加入我们的公共 Beta 版本。</span><span class="sxs-lookup"><span data-stu-id="b04d4-172">If you want to get updates more frequently, we encourage you to join our public Beta.</span></span>  <span data-ttu-id="b04d4-173">更新首先会转到 Beta 受众，我们会使用他们的反馈确保更新是高质量的，然后再将其发布到所有用户。</span><span class="sxs-lookup"><span data-stu-id="b04d4-173">Updates go to our Beta audience first, and we use their feedback to make sure the updates are high quality before publishing them to all users.</span></span>  <span data-ttu-id="b04d4-174">如果你不在我们的 Beta 计划中，最终会获得所有相同的修补程序和功能，但在 Beta 用户测试它们之后。</span><span class="sxs-lookup"><span data-stu-id="b04d4-174">If you’re not in our Beta program, you’ll eventually get all of the same fixes and features, but after they've been tested by our Beta users.</span></span>

<span data-ttu-id="b04d4-175">若要联接：：</span><span class="sxs-lookup"><span data-stu-id="b04d4-175">To join:</span></span>

  1. <span data-ttu-id="b04d4-176">在"流"中，使用"库"菜单 **下的** 下拉列表筛选为"**软件"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-176">In Steam, use the drop-down under the **Library** menu to filter to **Software**.</span></span>
  2. <span data-ttu-id="b04d4-177">在列表中，右键单击 **"Windows Mixed Reality"，然后选择**"属性 **"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-177">In the list, right-click **Windows Mixed Reality for SteamVR** and select **Properties**.</span></span>
  3. <span data-ttu-id="b04d4-178">选择 **"Betas"** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="b04d4-178">Select the **Betas** tab.</span></span>
  4. <span data-ttu-id="b04d4-179">选择加入 **"beta - 公共 beta 版本"，然后选择** " **关闭"** 以确认。</span><span class="sxs-lookup"><span data-stu-id="b04d4-179">Opt in to **"beta - public beta"** and select **Close** to confirm.</span></span> <span data-ttu-id="b04d4-180">beta 访问代码字段应留空。</span><span class="sxs-lookup"><span data-stu-id="b04d4-180">The beta access code field should be left blank.</span></span>
  
### <a name="steamvr-beta"></a><span data-ttu-id="b04d4-181">SteamVR Beta</span><span class="sxs-lookup"><span data-stu-id="b04d4-181">SteamVR Beta</span></span>

<span data-ttu-id="b04d4-182">SteamVR 由"流"生成和释放，在所有 SteamVR 头戴显示设备中很常见。</span><span class="sxs-lookup"><span data-stu-id="b04d4-182">SteamVR is built and released by Valve and is common across all SteamVR headsets.</span></span>  <span data-ttu-id="b04d4-183">它遵循类似的模型，在向所有用户发布 Beta 成员之前发布更新。</span><span class="sxs-lookup"><span data-stu-id="b04d4-183">It follows a similar model of releasing updates to Beta members before publishing to all users.</span></span>

<span data-ttu-id="b04d4-184">若要联接：：</span><span class="sxs-lookup"><span data-stu-id="b04d4-184">To join:</span></span>

  1. <span data-ttu-id="b04d4-185">在"流"中，使用"库"菜单 **下的** 下拉列表筛选为"**工具"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-185">In Steam, use the drop-down under the **Library** menu to filter to **Tools**.</span></span>
  2. <span data-ttu-id="b04d4-186">在列表中，右键单击 **"SteamVR"，** 然后选择"属性 **"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-186">In the list, right-click **SteamVR** and select **Properties**.</span></span>
  3. <span data-ttu-id="b04d4-187">选择 **"Betas"** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="b04d4-187">Select the **Betas** tab.</span></span>
  4. <span data-ttu-id="b04d4-188">选择加入 **"beta - 公共 beta 版本"，然后选择** " **关闭"** 以确认。</span><span class="sxs-lookup"><span data-stu-id="b04d4-188">Opt in to **"beta - public beta"** and select **Close** to confirm.</span></span>  <span data-ttu-id="b04d4-189">beta 访问代码字段应留空。 ![在 SteamVR 的属性对话框中切换到 SteamVR beta 版本](images/steamvr-beta.png)</span><span class="sxs-lookup"><span data-stu-id="b04d4-189">The beta access code field should be left blank.![Switch to the SteamVR beta in the properties dialog for SteamVR](images/steamvr-beta.png)</span></span>

### <a name="windows-insider-program"></a><span data-ttu-id="b04d4-190">Windows 预览体验计划</span><span class="sxs-lookup"><span data-stu-id="b04d4-190">Windows Insider Program</span></span>

<span data-ttu-id="b04d4-191">Windows Mixed Reality是 Windows 10 的一Windows 10。</span><span class="sxs-lookup"><span data-stu-id="b04d4-191">Windows Mixed Reality is a part of Windows 10.</span></span>  <span data-ttu-id="b04d4-192">影响 SteamVR 用户的许多修补程序和功能都随 Windows OS 一起提供。</span><span class="sxs-lookup"><span data-stu-id="b04d4-192">Many fixes and features that affect SteamVR users come with the Windows OS.</span></span>  <span data-ttu-id="b04d4-193">若要试用最新的预览Windows 10版本，建议加入[Windows 预览体验计划。](https://insider.windows.com)</span><span class="sxs-lookup"><span data-stu-id="b04d4-193">If you want to try the latest Windows 10 preview builds, we encourage you to join the [Windows Insider Program](https://insider.windows.com).</span></span>

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a><span data-ttu-id="b04d4-194">为 SteamVR 应用启用运动重新项目</span><span class="sxs-lookup"><span data-stu-id="b04d4-194">Enabling motion reprojection for SteamVR Apps</span></span>

<span data-ttu-id="b04d4-195">Windows Mixed Reality的流式处理具有实验性运动重现功能，使 90 FPS 重新保护更流畅。</span><span class="sxs-lookup"><span data-stu-id="b04d4-195">Windows Mixed Reality for SteamVR has an experimental motion reprojection feature to make 90 FPS reprojection more smooth.</span></span>

<span data-ttu-id="b04d4-196">启用运动重新项目时，所有 Steam VR 游戏在名义上以 1/2 帧速率呈现 (45 fps 而不是 90 FPS) ，而 Windows Mixed Reality for SteamVR 使用 GPU 生成的运动矢量来推断下一帧。</span><span class="sxs-lookup"><span data-stu-id="b04d4-196">When motion reprojection is enabled, all Steam VR games will render nominally at ½ frame rate (45 fps instead of 90 FPS) while Windows Mixed Reality for SteamVR uses motion vectors generated by the GPU to extrapolate the next frame.</span></span> <span data-ttu-id="b04d4-197">对于在给定电脑上可靠地达到 60 FPS+ 的 SteamVR 游戏，这应该可以带来可靠的 90 FPS 体验，偶尔出现项目，同时保持舒适体验。</span><span class="sxs-lookup"><span data-stu-id="b04d4-197">For SteamVR games that reliably hit 60 FPS+ on a given PC, this should result in a solid 90 FPS experience with occasional artifacts while maintaining a comfortable experience.</span></span>

<span data-ttu-id="b04d4-198">可用的运动重现模式如下所示：</span><span class="sxs-lookup"><span data-stu-id="b04d4-198">The available motion reprojection modes are as follows:</span></span>

* <span data-ttu-id="b04d4-199">**SteamVR 每应用设置**：允许通过"SteamVR 设置"UI 控制运动重新项目。</span><span class="sxs-lookup"><span data-stu-id="b04d4-199">**SteamVR per-app setting**: Allows you to control motion reprojection through the SteamVR Settings UI.</span></span> <span data-ttu-id="b04d4-200">然后，可以打开"SteamVR 设置"，转到"视频> Per-Application视频设置"，然后选择"运动平滑处理"选项。</span><span class="sxs-lookup"><span data-stu-id="b04d4-200">You can then open SteamVR Settings, go to Video > Per-Application Video Settings, and select an option for "Motion Smoothing."</span></span>
* <span data-ttu-id="b04d4-201">**自动**：使运动重现能够在游戏呈现速度过慢而维持 90 FPS 时自动打开。</span><span class="sxs-lookup"><span data-stu-id="b04d4-201">**Auto**: Enables motion reprojection to turn on automatically when a game is rendering too slowly to maintain 90 FPS.</span></span> <span data-ttu-id="b04d4-202">当游戏开始保持 90 FPS 或以小于 45 FPS 开始渲染时，运动重新保护将关闭。</span><span class="sxs-lookup"><span data-stu-id="b04d4-202">When a game begins to maintain 90 FPS or starts rendering at less than 45 FPS, motion reprojection will turn off.</span></span> <span data-ttu-id="b04d4-203">始终启用异步旋转重新项目。</span><span class="sxs-lookup"><span data-stu-id="b04d4-203">Asynchronous rotational reprojection is enabled always.</span></span>
* <span data-ttu-id="b04d4-204">**运动向量**：强制应用程序始终以半帧速率运行，并重排运动矢量。</span><span class="sxs-lookup"><span data-stu-id="b04d4-204">**Motion Vector**: Forces the application to always run at half-framerate with motion vector reprojection.</span></span>
* <span data-ttu-id="b04d4-205">**无**：禁用运动重新项目。</span><span class="sxs-lookup"><span data-stu-id="b04d4-205">**None**: Disables motion reprojection.</span></span>

<span data-ttu-id="b04d4-206">**预期的视觉对象项目**</span><span class="sxs-lookup"><span data-stu-id="b04d4-206">**Expected Visual Artifacts**</span></span> 

1. <span data-ttu-id="b04d4-207">使用大于 150% 的应用程序分辨率时，可能会遇到模糊处理。</span><span class="sxs-lookup"><span data-stu-id="b04d4-207">When using an application resolution greater than 150%, you may experience blurring.</span></span> <span data-ttu-id="b04d4-208">使用运动重现时，建议使用小于 150% 的值。</span><span class="sxs-lookup"><span data-stu-id="b04d4-208">When using motion reprojection, we recommend using a value less than 150%.</span></span>
2. <span data-ttu-id="b04d4-209">清晰对比度的边缘或文本（尤其是在游戏内 HUD 或菜单上）可能会由于分离而暂时出现扭曲或扭曲。</span><span class="sxs-lookup"><span data-stu-id="b04d4-209">Sharp contrast edges or text, especially on in-game HUDs or menus, may look temporarily warped or distorted because of disocclusion.</span></span>
3. <span data-ttu-id="b04d4-210">在此模式下，SteamVR Home 和电脑上无法可靠地达到 50-60 FPS 的其他许多游戏将继续体验不佳。</span><span class="sxs-lookup"><span data-stu-id="b04d4-210">SteamVR Home and many other games that don't reliably hit 50-60 FPS on your PC will continue to have a poor experience with this mode.</span></span>
4. <span data-ttu-id="b04d4-211">某些游戏已报告以 50% 的速度运行，或者延迟增加 (延迟) 。</span><span class="sxs-lookup"><span data-stu-id="b04d4-211">Some games have been reported to run at 50% speed or with increased latency (lag).</span></span> <span data-ttu-id="b04d4-212">通过下面的说明报告 [Windows 反馈中心](filing-feedback.md) 游戏。</span><span class="sxs-lookup"><span data-stu-id="b04d4-212">Report these games through the [Windows Feedback Hub](filing-feedback.md) instructions below.</span></span>

<span data-ttu-id="b04d4-213">最初，我们针对最新一代 NVidia GPU 提供实验性支持。</span><span class="sxs-lookup"><span data-stu-id="b04d4-213">Initially we have experimental support for recent generation NVidia GPUs.</span></span> <span data-ttu-id="b04d4-214">我们将继续在更多 GPU 上循环访问和改进运动重现支持，并且我们期待收到你的反馈。</span><span class="sxs-lookup"><span data-stu-id="b04d4-214">We're continuing to iterate and improve our motion reprojection support on more GPUs, and we’re eager to hear your feedback.</span></span>

<span data-ttu-id="b04d4-215">**支持的 GPU：** Nvidia GeForce GTX1060、AMD RX470 或更好，Windows Mixed Reality兼容的图形驱动程序。</span><span class="sxs-lookup"><span data-stu-id="b04d4-215">**Supported GPUs:** Nvidia GeForce GTX1060, AMD RX470 or better, with Windows Mixed Reality compatible graphics drivers installed.</span></span>

<span data-ttu-id="b04d4-216">启用运动重新项目：</span><span class="sxs-lookup"><span data-stu-id="b04d4-216">To enable motion reprojection:</span></span>

1. <span data-ttu-id="b04d4-217">确保已按照上述说明选择Windows Mixed Reality **SteamVR Beta** 版本。</span><span class="sxs-lookup"><span data-stu-id="b04d4-217">Make sure you've opted into the **Windows Mixed Reality for SteamVR Beta** using the instructions above.</span></span>
2. <span data-ttu-id="b04d4-218">打开 SteamVR 仪表板。</span><span class="sxs-lookup"><span data-stu-id="b04d4-218">Open the SteamVR dashboard.</span></span>
3. <span data-ttu-id="b04d4-219">选择左侧具有"流"徽标的按钮Windows Mixed Reality打开 **"Windows Mixed Reality"设置"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-219">Select the button on the left side with the Windows Mixed Reality logo to open **Windows Mixed Reality for SteamVR** Settings.</span></span>
4. <span data-ttu-id="b04d4-220">在弹出的 UI 中，选择"图形"选项卡。</span><span class="sxs-lookup"><span data-stu-id="b04d4-220">In the UI that pops up, select the Graphics tab.</span></span>
5. <span data-ttu-id="b04d4-221">选择"自动"作为"默认 SteamVR 应用运动重现模式"，以启用自动运动重现。</span><span class="sxs-lookup"><span data-stu-id="b04d4-221">Select "Auto" for "Default SteamVR app motion reprojection mode" to enable automatic motion reprojection.</span></span>

![使用 SettingsUX & LSR 指示器启用 LSR](images/settingsux-enable-lsr.gif)

<span data-ttu-id="b04d4-223">**运动重现指示器**</span><span class="sxs-lookup"><span data-stu-id="b04d4-223">**Motion Reprojection Indicator**</span></span>

<span data-ttu-id="b04d4-224">运动重现指示器有助于诊断实验性自动运动重新项目功能的问题。</span><span class="sxs-lookup"><span data-stu-id="b04d4-224">The motion reprojection indicator helps diagnose issues with the experimental automatic motion reprojection feature.</span></span> <span data-ttu-id="b04d4-225">设置为 true 时，在自动运动重新保护期间，头戴显示设备左上方会显示一个指示器。</span><span class="sxs-lookup"><span data-stu-id="b04d4-225">When set to true, you'll see an indicator in the top-left of your headset display during automatic motion reprojection.</span></span> <span data-ttu-id="b04d4-226">此指示器的颜色和位置对应于当前运动重现模式 - 有关示例，请参阅下图。</span><span class="sxs-lookup"><span data-stu-id="b04d4-226">The color and position of this indicator corresponds to the current motion reprojection mode - see the diagram below for examples.</span></span>

![mvLSR 指示器](images/mvLSRIndicator.png)

<span data-ttu-id="b04d4-228">绿色 = 运动重现处于关闭状态，因为应用程序可以以全帧速率呈现。</span><span class="sxs-lookup"><span data-stu-id="b04d4-228">Green = motion reprojection is off because the application can render at full framerate.</span></span>

<span data-ttu-id="b04d4-229">由于应用程序占用了 CPU，因此，"青色 = 运动重新项目"为"打开"状态。</span><span class="sxs-lookup"><span data-stu-id="b04d4-229">Cyan = motion reprojection is on because the application is cpu bound.</span></span>

<span data-ttu-id="b04d4-230">蓝色 = 运动重新项目已打开，因为应用程序已绑定 gpu。</span><span class="sxs-lookup"><span data-stu-id="b04d4-230">Blue = motion reprojection is on because the application is gpu bound.</span></span>

<span data-ttu-id="b04d4-231">红色 = 运动重新重现处于关闭状态，因为应用程序以小于一半帧速率运行;如果已启用，请尝试减少超级采样。</span><span class="sxs-lookup"><span data-stu-id="b04d4-231">Red = motion reprojection is off because the application is running at less than half framerate; try reducing super sampling if enabled.</span></span>

<span data-ttu-id="b04d4-232">绿色 + 青色 + 蓝色 = 运动重排为半帧速率模式，或应用程序请求的重排运动。</span><span class="sxs-lookup"><span data-stu-id="b04d4-232">Green + Cyan + Blue = motion reprojection is in half-framerate mode or the application requested motion reprojection.</span></span>

## <a name="sharing-feedback-on-steamvr"></a><span data-ttu-id="b04d4-233">共享有关 SteamVR 的反馈</span><span class="sxs-lookup"><span data-stu-id="b04d4-233">Sharing feedback on SteamVR</span></span>

<span data-ttu-id="b04d4-234">在改进 SteamVR 体验方面，你的Windows Mixed Reality非常有用。</span><span class="sxs-lookup"><span data-stu-id="b04d4-234">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="b04d4-235">通过 提交所有反馈和 bug [Windows 反馈中心。](filing-feedback.md)</span><span class="sxs-lookup"><span data-stu-id="b04d4-235">Submit all feedback and bugs through the [Windows Feedback Hub](filing-feedback.md).</span></span> <span data-ttu-id="b04d4-236">请遵循以下建议，帮助我们从你的反馈中获得最大帮助：</span><span class="sxs-lookup"><span data-stu-id="b04d4-236">Follow these suggestions to help us get the most from your feedback:</span></span>

1. <span data-ttu-id="b04d4-237">在反馈中心中，指示你在"什么是反馈？"中报告新问题。</span><span class="sxs-lookup"><span data-stu-id="b04d4-237">In Feedback Hub, indicate that you're reporting a new Problem in the "What kind of feedback is it?"</span></span> <span data-ttu-id="b04d4-238">部分位于顶部。</span><span class="sxs-lookup"><span data-stu-id="b04d4-238">section at the top.</span></span>
2. <span data-ttu-id="b04d4-239">选择" **混合现实"** 类别和 **"应用** "子类别。</span><span class="sxs-lookup"><span data-stu-id="b04d4-239">Select the **Mixed Reality** category and the **Apps** subcategory.</span></span>
3. <span data-ttu-id="b04d4-240">将单词"SteamVR"放在问题摘要中。</span><span class="sxs-lookup"><span data-stu-id="b04d4-240">Put the word "SteamVR" in the problem summary.</span></span> <span data-ttu-id="b04d4-241">这有助于我们找到你的反馈。</span><span class="sxs-lookup"><span data-stu-id="b04d4-241">That helps us find your feedback.</span></span>
4. <span data-ttu-id="b04d4-242">描述遇到问题时使用的 SteamVR 游戏或应用程序。</span><span class="sxs-lookup"><span data-stu-id="b04d4-242">Describe what SteamVR game or application you were using when you come across the issue.</span></span>
5. <span data-ttu-id="b04d4-243">请考虑将 SteamVR 系统报告附加到反馈。</span><span class="sxs-lookup"><span data-stu-id="b04d4-243">Consider attaching a SteamVR System Report to your feedback.</span></span> <span data-ttu-id="b04d4-244">这提供了更多日志，可帮助我们诊断问题。</span><span class="sxs-lookup"><span data-stu-id="b04d4-244">This provides more logs that can help us diagnose your problem.</span></span>
    1. <span data-ttu-id="b04d4-245">在"SteamVR 窗口 (显示控制器状态的小窗口) 在标题上选择以打开菜单。</span><span class="sxs-lookup"><span data-stu-id="b04d4-245">On the SteamVR Window (the small windows that shows your controller status) select on the title to open the menu.</span></span>
    2. <span data-ttu-id="b04d4-246">选择"创建系统报表"。</span><span class="sxs-lookup"><span data-stu-id="b04d4-246">Select "Create System Report".</span></span>
    3. <span data-ttu-id="b04d4-247">保存到文件。</span><span class="sxs-lookup"><span data-stu-id="b04d4-247">Save to File.</span></span>
    4. <span data-ttu-id="b04d4-248">将生成的文件直接附加到反馈中心条目。</span><span class="sxs-lookup"><span data-stu-id="b04d4-248">Attach the generated file to your Feedback Hub entry directly.</span></span>
6. <span data-ttu-id="b04d4-249">如果你的反馈与 SteamVR 性能有关，请收集混合现实性能跟踪：</span><span class="sxs-lookup"><span data-stu-id="b04d4-249">If your feedback is about SteamVR performance, collect a Mixed Reality Performance trace:</span></span> 
    1. <span data-ttu-id="b04d4-250">选择" **重新创建我的问题"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="b04d4-250">Select the **Recreate my Problem** button.</span></span>
    2. <span data-ttu-id="b04d4-251">在"包含关于的数据"旁边的下拉列表中，选择"**混合现实性能"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-251">In the drop-down next to "include data about", select **Mixed Reality Performance**.</span></span>
    3. <span data-ttu-id="b04d4-252">确保游戏正在运行，然后选择"开始 **捕获"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-252">Make sure the game is running and select **Start Capture**.</span></span>
    4. <span data-ttu-id="b04d4-253">在游戏上花费几秒钟来捕获跟踪。</span><span class="sxs-lookup"><span data-stu-id="b04d4-253">Spend a few seconds playing the game to capture the trace.</span></span> <span data-ttu-id="b04d4-254">不要捕获跟踪超过 10-15 秒，否则它太大，无法提交。</span><span class="sxs-lookup"><span data-stu-id="b04d4-254">Don't capture the trace for more than 10-15 seconds, or it will be too large to submit.</span></span>
    5. <span data-ttu-id="b04d4-255">选择"**停止捕获"。**</span><span class="sxs-lookup"><span data-stu-id="b04d4-255">Select **Stop Capture**.</span></span>
7. <span data-ttu-id="b04d4-256">完成 **其余** 字段后，选择"提交"。</span><span class="sxs-lookup"><span data-stu-id="b04d4-256">Select **Submit** once you've completed the rest of the fields.</span></span>

<span data-ttu-id="b04d4-257">如果你有要分享的问题或意见，还可以在我们的 Steam 论坛上 [与我们联系](http://steamcommunity.com/app/719950/discussions/)。</span><span class="sxs-lookup"><span data-stu-id="b04d4-257">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="see-also"></a><span data-ttu-id="b04d4-258">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b04d4-258">See also</span></span>

* [<span data-ttu-id="b04d4-259">使用 Windows Mixed Reality 对 SteamVR 进行故障排除</span><span class="sxs-lookup"><span data-stu-id="b04d4-259">Troubleshooting SteamVR with Windows Mixed Reality</span></span>](steamvr-questions.md)
* [<span data-ttu-id="b04d4-260">在应用程序中使用Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b04d4-260">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="b04d4-261">在 Unity 中使用 HP 控制器</span><span class="sxs-lookup"><span data-stu-id="b04d4-261">Using HP Controllers in Unity</span></span>](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [<span data-ttu-id="b04d4-262">在 Unreal 中使用 HP 控制器</span><span class="sxs-lookup"><span data-stu-id="b04d4-262">Using HP Controllers in Unreal</span></span>](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [<span data-ttu-id="b04d4-263">提交 bug 和反馈</span><span class="sxs-lookup"><span data-stu-id="b04d4-263">Filing bugs and feedback</span></span>](filing-feedback.md)
