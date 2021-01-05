---
title: 将 SteamVR 与 Windows Mixed Reality 一起使用
description: 如何在 Windows Mixed Reality 耳机上播放 SteamVR 游戏和兼容的电脑。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，游戏，SteamVR，流，系统要求
ms.openlocfilehash: e91c5b7fcaed2f048e79843c47ae613761a5d3ad
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725738"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a><span data-ttu-id="ef08b-104">将 SteamVR 与 Windows Mixed Reality 一起使用</span><span class="sxs-lookup"><span data-stu-id="ef08b-104">Using SteamVR with Windows Mixed Reality</span></span>

<span data-ttu-id="ef08b-105">适用于 SteamVR 的 windows Mixed Reality 允许用户在 Windows Mixed Reality 沉浸式耳机上运行 SteamVR 体验。</span><span class="sxs-lookup"><span data-stu-id="ef08b-105">Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="ef08b-106">安装适用于 SteamVR 的 Windows Mixed Reality 后，用户可以从其桌面或流库中启动他们最喜爱的 SteamVR 应用程序，并直接在其 Windows 耳机上播放它们。</span><span class="sxs-lookup"><span data-stu-id="ef08b-106">After installing the Windows Mixed Reality for SteamVR, users can launch their favorite SteamVR applications from their desktop or Steam library and play them directly on their Windows headset.</span></span>

## <a name="get-your-pc-ready"></a><span data-ttu-id="ef08b-107">准备好你的电脑</span><span class="sxs-lookup"><span data-stu-id="ef08b-107">Get your PC ready</span></span>

* <span data-ttu-id="ef08b-108">请确保没有挂起的更新：选择 " **启动 > 设置" > Update & Security > Windows 更新**"。</span><span class="sxs-lookup"><span data-stu-id="ef08b-108">Make sure you have no pending updates: Select **Start > Settings > Update & Security > Windows Update**.</span></span> <span data-ttu-id="ef08b-109">如果有可用更新，请选择 " **立即安装**"。</span><span class="sxs-lookup"><span data-stu-id="ef08b-109">If updates are available, select **Install now**.</span></span> <span data-ttu-id="ef08b-110">如果没有可用的更新，请选择 " **检查更新**"，然后安装任何新更新。</span><span class="sxs-lookup"><span data-stu-id="ef08b-110">If no updates are available, select **Check for updates**, and then install any new ones.</span></span>
* <span data-ttu-id="ef08b-111">电脑要求对于流上的应用和内容有所不同。</span><span class="sxs-lookup"><span data-stu-id="ef08b-111">PC requirements vary for the apps and content on Steam.</span></span> <span data-ttu-id="ef08b-112">请参阅每个标题的最低要求。</span><span class="sxs-lookup"><span data-stu-id="ef08b-112">See the minimum requirements per title.</span></span> <span data-ttu-id="ef08b-113">使用 GTX 1070 图形卡 (或等效) 并且 Intel®内核™ i7 处理器的电脑应为广泛的头衔提供良好的体验。</span><span class="sxs-lookup"><span data-stu-id="ef08b-113">A PC with a GTX 1070 graphics card (or equivalent) and an Intel® Core™ i7 processor should offer a good experience for a broad range of titles.</span></span>

## <a name="set-up-windows-mixed-reality-for-steamvr"></a><span data-ttu-id="ef08b-114">为 SteamVR 设置 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ef08b-114">Set up Windows Mixed Reality for SteamVR</span></span>

1. <span data-ttu-id="ef08b-115">设置 [Windows Mixed Reality](set-up-windows-mixed-reality.md) （如果尚未安装）</span><span class="sxs-lookup"><span data-stu-id="ef08b-115">Set up up [Windows Mixed Reality](set-up-windows-mixed-reality.md) if you haven't already</span></span>
2. <span data-ttu-id="ef08b-116">安装 [流](http://store.steampowered.com/about/) 并 **登录** ，或 **创建新帐户。**</span><span class="sxs-lookup"><span data-stu-id="ef08b-116">Install [Steam](http://store.steampowered.com/about/) and **login** or **create a new account.**</span></span>
3. <span data-ttu-id="ef08b-117">安装 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)。</span><span class="sxs-lookup"><span data-stu-id="ef08b-117">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/).</span></span> <span data-ttu-id="ef08b-118">戴上耳机后，启动流，你会看到一个对话框，提示你安装 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="ef08b-118">With your headset plugged in, launch Steam and you should see a dialog prompting you to install SteamVR.</span></span> <span data-ttu-id="ef08b-119">按照对话框中的提示安装该对话框。</span><span class="sxs-lookup"><span data-stu-id="ef08b-119">Follow the prompts on the dialog to install it.</span></span>
    * <span data-ttu-id="ef08b-120">如果看不到弹出窗口，请通过导航到 *库* 的 "*工具*" 部分来安装 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="ef08b-120">If you don't see the popup, install SteamVR by navigating to the *Tools* section of your *library*.</span></span> <span data-ttu-id="ef08b-121">在列表中找到 "SteamVR"，然后右键单击并选择 " *安装游戏*"。</span><span class="sxs-lookup"><span data-stu-id="ef08b-121">Locate SteamVR in the list and then right-click and select *Install Game*.</span></span>
4. <span data-ttu-id="ef08b-122">安装 [适用于 SteamVR 的 Windows Mixed Reality](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)。</span><span class="sxs-lookup"><span data-stu-id="ef08b-122">Install [Windows Mixed Reality for SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).</span></span>

## <a name="play-steamvr-games"></a><span data-ttu-id="ef08b-123">玩 SteamVR 游戏</span><span class="sxs-lookup"><span data-stu-id="ef08b-123">Play SteamVR games</span></span>

1. <span data-ttu-id="ef08b-124">将耳机连接到电脑，并打开运动控制器。</span><span class="sxs-lookup"><span data-stu-id="ef08b-124">Connect your headset to your PC and turn on your motion controllers.</span></span>
2. <span data-ttu-id="ef08b-125">加载 Windows Mixed Reality 主页并显示控制器后，请在桌面上打开流应用。</span><span class="sxs-lookup"><span data-stu-id="ef08b-125">Once the Windows Mixed Reality home has loaded and your controllers are visible, open the Steam app on your desktop.</span></span>
3. <span data-ttu-id="ef08b-126">使用流应用从您的流库中启动 SteamVR 游戏。</span><span class="sxs-lookup"><span data-stu-id="ef08b-126">Use the Steam app to launch a SteamVR game from your Steam library.</span></span>

<span data-ttu-id="ef08b-127">**提示**：若要在不停用耳机的情况下启动 SteamVR 游戏，请使用桌面应用 (**启动 > 桌面**) ，在 Windows MIXED Reality 内查看 PC 桌面并与其交互。</span><span class="sxs-lookup"><span data-stu-id="ef08b-127">**Tip**: To launch SteamVR games without taking off your headset, use the Desktop app (**Start > Desktop**) to view and interact with your PC desktop inside Windows Mixed Reality.</span></span>

## <a name="using-motion-controllers-with-steamvr"></a><span data-ttu-id="ef08b-128">将运动控制器用于 SteamVR</span><span class="sxs-lookup"><span data-stu-id="ef08b-128">Using Motion Controllers with SteamVR</span></span>

<span data-ttu-id="ef08b-129">不同游戏中的运动控制器使用方式有所不同。</span><span class="sxs-lookup"><span data-stu-id="ef08b-129">You'll use your motion controllers differently in different games.</span></span> <span data-ttu-id="ef08b-130">下面是一些可帮助你入门的基础知识：</span><span class="sxs-lookup"><span data-stu-id="ef08b-130">Here are a few basics to help you get started:</span></span>

* <span data-ttu-id="ef08b-131">若要打开 "流" 仪表板，请在左或右操纵杆上按向下。</span><span class="sxs-lookup"><span data-stu-id="ef08b-131">To open the Steam dashboard, press straight down on the left or right thumbstick.</span></span>
* <span data-ttu-id="ef08b-132">若要退出 SteamVR 游戏并返回到 Windows Mixed Reality 主页，请按 Windows 按钮。</span><span class="sxs-lookup"><span data-stu-id="ef08b-132">To exit a SteamVR game and return to the Windows Mixed Reality home, press the Windows button.</span></span>

## <a name="changing-the-resolution"></a><span data-ttu-id="ef08b-133">更改分辨率</span><span class="sxs-lookup"><span data-stu-id="ef08b-133">Changing the resolution</span></span>

<span data-ttu-id="ef08b-134">如果要以更高的分辨率玩游戏，可以随时在 "SteamVR-> 设置-> 应用程序" 窗口中调整应用程序分辨率滑块。</span><span class="sxs-lookup"><span data-stu-id="ef08b-134">You can adjust the Application Resolution slider in the SteamVR -> Settings -> Applications window at any time if you'd like to play games at a higher resolution.</span></span> <span data-ttu-id="ef08b-135">\* \* 当使用较高的分辨率乘数时，您会希望游戏对您的 PC 造成更大的压力。</span><span class="sxs-lookup"><span data-stu-id="ef08b-135">\*\*When using a higher resolution multiplier you can expect the game to put more strain on your PC.</span></span> <span data-ttu-id="ef08b-136">如果增加乘数并查看性能下降，请将滑块重新调整为默认级别，并重新启动游戏以确保更改生效。</span><span class="sxs-lookup"><span data-stu-id="ef08b-136">If you increase the multiplier and see degraded performance, readjust the slider to the default level and restart the game to ensure that the change takes effect.</span></span>![调整应用程序分辨率](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a><span data-ttu-id="ef08b-138">使用多个耳机</span><span class="sxs-lookup"><span data-stu-id="ef08b-138">Using multiple headsets</span></span>

<span data-ttu-id="ef08b-139">如果你是一位 VR 发烧，你可能会定期在同一台电脑上使用多个 VR 耳机。</span><span class="sxs-lookup"><span data-stu-id="ef08b-139">If you're a VR enthusiast, you might regularly use more than one VR headset on the same PC.</span></span> <span data-ttu-id="ef08b-140">如果是这样，请注意，当插入 Windows Mixed Reality 耳机时，SteamVR 游戏将始终启动 Windows Mixed Reality 耳机。</span><span class="sxs-lookup"><span data-stu-id="ef08b-140">If that's the case note that when a Windows Mixed Reality headset is plugged in, SteamVR games will always launch to the Windows Mixed Reality headset.</span></span> <span data-ttu-id="ef08b-141">如果要在另一个耳机上启动 SteamVR 游戏，请先拔下 Windows Mixed Reality 耳机，然后再继续。</span><span class="sxs-lookup"><span data-stu-id="ef08b-141">If you'd like to launch SteamVR games on another headset make sure to first unplug the Windows Mixed Reality headset before continuing.</span></span>

## <a name="preview-programs"></a><span data-ttu-id="ef08b-142">预览计划</span><span class="sxs-lookup"><span data-stu-id="ef08b-142">Preview programs</span></span>

<span data-ttu-id="ef08b-143">我们发布了定期更新，以提高在 Windows Mixed Reality 沉浸式耳机上使用 SteamVR 的性能、可靠性和总体体验。</span><span class="sxs-lookup"><span data-stu-id="ef08b-143">We release regular updates to improve the performance, reliability, and overall experience of using SteamVR on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="ef08b-144">尽管这些预览程序都不是必需的，但如果想要更快地 (更新，并向我们提供有关这些更新的反馈，则建议你加入这些程序！ ) 。</span><span class="sxs-lookup"><span data-stu-id="ef08b-144">While none of these preview programs are required, we encourage you to join them if you would like to get updates sooner and more frequently (and give us feedback on those updates!).</span></span>

### <a name="windows-mixed-reality-for-steamvr-beta"></a><span data-ttu-id="ef08b-145">适用于 SteamVR Beta 的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ef08b-145">Windows Mixed Reality for SteamVR Beta</span></span>

<span data-ttu-id="ef08b-146">适用于 SteamVR 的 Windows Mixed Reality 是从流应用商店中安装的组件，可使 SteamVR 与 Windows Mixed Reality 耳机一起工作。</span><span class="sxs-lookup"><span data-stu-id="ef08b-146">Windows Mixed Reality for SteamVR is the component you install from the Steam Store that enables SteamVR to work with your Windows Mixed Reality headset.</span></span>  <span data-ttu-id="ef08b-147">我们会定期将更新发布到此 "桥"，然后自动将其安装。</span><span class="sxs-lookup"><span data-stu-id="ef08b-147">We publish updates to this "bridge" regularly and Steam installs them automatically.</span></span>

<span data-ttu-id="ef08b-148">如果您想要更频繁地获取更新，我们鼓励您加入我们的公共 Beta。</span><span class="sxs-lookup"><span data-stu-id="ef08b-148">If you want to get updates more frequently, we encourage you to join our public Beta.</span></span>  <span data-ttu-id="ef08b-149">更新首先会转向我们的测试人员，并在将更新发布给所有用户之前，使用他们的反馈来确保更新质量高。</span><span class="sxs-lookup"><span data-stu-id="ef08b-149">Updates go to our Beta audience first, and we use their feedback to make sure the updates are high quality before publishing them to all users.</span></span>  <span data-ttu-id="ef08b-150">如果你不在我们的 Beta 版计划中，你最终会获得所有相同的修补程序和功能，但在我们的 Beta 用户进行测试后即可。</span><span class="sxs-lookup"><span data-stu-id="ef08b-150">If you’re not in our Beta program, you’ll eventually get all of the same fixes and features, but after they've been tested by our Beta users.</span></span>

<span data-ttu-id="ef08b-151">加入：</span><span class="sxs-lookup"><span data-stu-id="ef08b-151">To join:</span></span>

  1. <span data-ttu-id="ef08b-152">在 "流" 中，使用 " **库** " 菜单下的下拉箭头来筛选 **软件**。</span><span class="sxs-lookup"><span data-stu-id="ef08b-152">In Steam, use the drop-down under the **Library** menu to filter to **Software**.</span></span>
  2. <span data-ttu-id="ef08b-153">在列表中，右键单击 " **SteamVR 的 Windows Mixed Reality** "，然后选择 " **属性**"。</span><span class="sxs-lookup"><span data-stu-id="ef08b-153">In the list, right-click **Windows Mixed Reality for SteamVR** and select **Properties**.</span></span>
  3. <span data-ttu-id="ef08b-154">选择 " **测试** 版" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ef08b-154">Select the **Betas** tab.</span></span>
  4. <span data-ttu-id="ef08b-155">选择 **"beta-公共 beta"** 并选择 " **关闭** " 以确认。</span><span class="sxs-lookup"><span data-stu-id="ef08b-155">Opt in to **"beta - public beta"** and select **Close** to confirm.</span></span> <span data-ttu-id="ef08b-156">"Beta 访问代码" 字段应留空。</span><span class="sxs-lookup"><span data-stu-id="ef08b-156">The beta access code field should be left blank.</span></span>
  
### <a name="steamvr-beta"></a><span data-ttu-id="ef08b-157">SteamVR Beta</span><span class="sxs-lookup"><span data-stu-id="ef08b-157">SteamVR Beta</span></span>

<span data-ttu-id="ef08b-158">SteamVR 是由阀门构建和发布的，在所有 SteamVR 耳机上都是通用的。</span><span class="sxs-lookup"><span data-stu-id="ef08b-158">SteamVR is built and released by Valve and is common across all SteamVR headsets.</span></span>  <span data-ttu-id="ef08b-159">它遵循在发布到所有用户之前发布 Beta 成员更新的类似模型。</span><span class="sxs-lookup"><span data-stu-id="ef08b-159">It follows a similar model of releasing updates to Beta members before publishing to all users.</span></span>

<span data-ttu-id="ef08b-160">加入：</span><span class="sxs-lookup"><span data-stu-id="ef08b-160">To join:</span></span>

  1. <span data-ttu-id="ef08b-161">在 "流" 中，使用 " **库** " 菜单下的下拉箭头来筛选 **工具**。</span><span class="sxs-lookup"><span data-stu-id="ef08b-161">In Steam, use the drop-down under the **Library** menu to filter to **Tools**.</span></span>
  2. <span data-ttu-id="ef08b-162">在列表中，右键单击 **SteamVR** ，然后选择 " **属性**"。</span><span class="sxs-lookup"><span data-stu-id="ef08b-162">In the list, right-click **SteamVR** and select **Properties**.</span></span>
  3. <span data-ttu-id="ef08b-163">选择 " **测试** 版" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ef08b-163">Select the **Betas** tab.</span></span>
  4. <span data-ttu-id="ef08b-164">选择 **"beta-公共 beta"** 并选择 " **关闭** " 以确认。</span><span class="sxs-lookup"><span data-stu-id="ef08b-164">Opt in to **"beta - public beta"** and select **Close** to confirm.</span></span>  <span data-ttu-id="ef08b-165">"Beta 访问代码" 字段应留空。 ![切换到 SteamVR 的 "属性" 对话框中的 "SteamVR beta"。](images/steamvr-beta.png)</span><span class="sxs-lookup"><span data-stu-id="ef08b-165">The beta access code field should be left blank.![Switch to the SteamVR beta in the properties dialog for SteamVR](images/steamvr-beta.png)</span></span>

### <a name="windows-insider-program"></a><span data-ttu-id="ef08b-166">Windows 预览体验计划</span><span class="sxs-lookup"><span data-stu-id="ef08b-166">Windows Insider Program</span></span>

<span data-ttu-id="ef08b-167">Windows Mixed Reality 是 Windows 10 的一部分。</span><span class="sxs-lookup"><span data-stu-id="ef08b-167">Windows Mixed Reality is a part of Windows 10.</span></span>  <span data-ttu-id="ef08b-168">影响 SteamVR 用户的许多修补程序和功能都包含 Windows 操作系统。</span><span class="sxs-lookup"><span data-stu-id="ef08b-168">Many fixes and features that affect SteamVR users come with the Windows OS.</span></span>  <span data-ttu-id="ef08b-169">如果要尝试最新的 Windows 10 预览版，我们建议加入 [Windows 预览体验计划](https://insider.windows.com)。</span><span class="sxs-lookup"><span data-stu-id="ef08b-169">If you want to try the latest Windows 10 preview builds, we encourage you to join the [Windows Insider Program](https://insider.windows.com).</span></span>

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a><span data-ttu-id="ef08b-170">为 SteamVR 应用启用运动 reprojection</span><span class="sxs-lookup"><span data-stu-id="ef08b-170">Enabling motion reprojection for SteamVR Apps</span></span>

<span data-ttu-id="ef08b-171">适用于 SteamVR 的 Windows Mixed Reality 具有试验性运动 reprojection 功能，使 90 FPS reprojection 更平稳。</span><span class="sxs-lookup"><span data-stu-id="ef08b-171">Windows Mixed Reality for SteamVR has an experimental motion reprojection feature to make 90 FPS reprojection more smooth.</span></span>

<span data-ttu-id="ef08b-172">启用动作 reprojection 后，所有流的 VR 游戏将以1/2 帧速率呈现通常 (45 fps，而不是 90 FPS) ，而 SteamVR 的 Windows Mixed Reality 使用 GPU 生成的运动向量来推断下一帧。</span><span class="sxs-lookup"><span data-stu-id="ef08b-172">When motion reprojection is enabled, all Steam VR games will render nominally at ½ frame rate (45 fps instead of 90 FPS) while Windows Mixed Reality for SteamVR uses motion vectors generated by the GPU to extrapolate the next frame.</span></span> <span data-ttu-id="ef08b-173">对于在给定的 PC 上可靠地命中 60 FPS + 的 SteamVR 游戏，这应该会在保持舒适的体验的同时，偶尔产生稳定的 90 FPS 体验。</span><span class="sxs-lookup"><span data-stu-id="ef08b-173">For SteamVR games that reliably hit 60 FPS+ on a given PC, this should result in a solid 90 FPS experience with occasional artifacts while maintaining a comfortable experience.</span></span>

<span data-ttu-id="ef08b-174">可用的运动 reprojection 模式如下所示：</span><span class="sxs-lookup"><span data-stu-id="ef08b-174">The available motion reprojection modes are as follows:</span></span>

* <span data-ttu-id="ef08b-175">**SteamVR 每个应用设置**：允许通过 STEAMVR 设置 UI 控制运动 reprojection。</span><span class="sxs-lookup"><span data-stu-id="ef08b-175">**SteamVR per-app setting**: Allows you to control motion reprojection through the SteamVR Settings UI.</span></span> <span data-ttu-id="ef08b-176">然后，可以打开 SteamVR 设置，Per-Application 视频设置中转到视频 >，并选择 "运动平滑处理" 选项。</span><span class="sxs-lookup"><span data-stu-id="ef08b-176">You can then open SteamVR Settings, go to Video > Per-Application Video Settings, and select an option for "Motion Smoothing."</span></span>
* <span data-ttu-id="ef08b-177">**自动**：当游戏呈现速度太慢而无法维护 90 FPS 时，使运动 reprojection 自动打开。</span><span class="sxs-lookup"><span data-stu-id="ef08b-177">**Auto**: Enables motion reprojection to turn on automatically when a game is rendering too slowly to maintain 90 FPS.</span></span> <span data-ttu-id="ef08b-178">当游戏开始维护 90 FPS 或在小于 45 FPS 时开始呈现时，运动 reprojection 将关闭。</span><span class="sxs-lookup"><span data-stu-id="ef08b-178">When a game begins to maintain 90 FPS or starts rendering at less than 45 FPS, motion reprojection will turn off.</span></span> <span data-ttu-id="ef08b-179">异步旋转 reprojection 始终处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="ef08b-179">Asynchronous rotational reprojection is enabled always.</span></span>
* <span data-ttu-id="ef08b-180">**运动向量**：强制应用程序始终以半帧速率和运动矢量 reprojection 运行。</span><span class="sxs-lookup"><span data-stu-id="ef08b-180">**Motion Vector**: Forces the application to always run at half-framerate with motion vector reprojection.</span></span>
* <span data-ttu-id="ef08b-181">**None**：禁用运动 reprojection。</span><span class="sxs-lookup"><span data-stu-id="ef08b-181">**None**: Disables motion reprojection.</span></span>

<span data-ttu-id="ef08b-182">**预期的视觉对象**</span><span class="sxs-lookup"><span data-stu-id="ef08b-182">**Expected Visual Artifacts**</span></span> 

1. <span data-ttu-id="ef08b-183">如果使用的应用程序分辨率大于150%，则可能会遇到模糊效果。</span><span class="sxs-lookup"><span data-stu-id="ef08b-183">When using an application resolution greater than 150%, you may experience blurring.</span></span> <span data-ttu-id="ef08b-184">使用运动 reprojection 时，我们建议使用小于150% 的值。</span><span class="sxs-lookup"><span data-stu-id="ef08b-184">When using motion reprojection, we recommend using a value less than 150%.</span></span>
2. <span data-ttu-id="ef08b-185">清晰对比度边缘或文本（特别是在游戏中的 HUDs 或菜单上）可能会因为 disocclusion 而暂时歪曲或失真。</span><span class="sxs-lookup"><span data-stu-id="ef08b-185">Sharp contrast edges or text, especially on in-game HUDs or menus, may look temporarily warped or distorted because of disocclusion.</span></span>
3. <span data-ttu-id="ef08b-186">在您的 PC 上，SteamVR 家庭和很多其他不可靠地碰到 50-60 FPS 的游戏将继续在此模式下出现不佳的体验。</span><span class="sxs-lookup"><span data-stu-id="ef08b-186">SteamVR Home and many other games that don't reliably hit 50-60 FPS on your PC will continue to have a poor experience with this mode.</span></span>
4. <span data-ttu-id="ef08b-187">某些游戏已报告为以50% 速度运行，或延迟延迟 (lag) 。</span><span class="sxs-lookup"><span data-stu-id="ef08b-187">Some games have been reported to run at 50% speed or with increased latency (lag).</span></span> <span data-ttu-id="ef08b-188">通过下面的 [Windows 反馈中心](filing-feedback.md) 说明报告这些游戏。</span><span class="sxs-lookup"><span data-stu-id="ef08b-188">Report these games through the [Windows Feedback Hub](filing-feedback.md) instructions below.</span></span>

<span data-ttu-id="ef08b-189">最初，我们对最近的一代 NVidia Gpu 进行了实验性支持。</span><span class="sxs-lookup"><span data-stu-id="ef08b-189">Initially we have experimental support for recent generation NVidia GPUs.</span></span> <span data-ttu-id="ef08b-190">我们将继续循环访问更多 Gpu 上的 reprojection 支持，并积极倾听你的反馈。</span><span class="sxs-lookup"><span data-stu-id="ef08b-190">We're continuing to iterate and improve our motion reprojection support on more GPUs, and we’re eager to hear your feedback.</span></span>

<span data-ttu-id="ef08b-191">**支持的 gpu：** 安装了 Windows Mixed Reality 兼容图形驱动程序的 Nvidia GeForce GTX1060、AMD RX470 或更高性能。</span><span class="sxs-lookup"><span data-stu-id="ef08b-191">**Supported GPUs:** Nvidia GeForce GTX1060, AMD RX470 or better, with Windows Mixed Reality compatible graphics drivers installed.</span></span>

<span data-ttu-id="ef08b-192">若要启用运动 reprojection：</span><span class="sxs-lookup"><span data-stu-id="ef08b-192">To enable motion reprojection:</span></span>

1. <span data-ttu-id="ef08b-193">请确保已使用上述说明选择加入 **SteamVR Beta 的 Windows Mixed Reality** 。</span><span class="sxs-lookup"><span data-stu-id="ef08b-193">Make sure you've opted into the **Windows Mixed Reality for SteamVR Beta** using the instructions above.</span></span>
2. <span data-ttu-id="ef08b-194">打开 SteamVR 仪表板。</span><span class="sxs-lookup"><span data-stu-id="ef08b-194">Open the SteamVR dashboard.</span></span>
3. <span data-ttu-id="ef08b-195">选择左侧带有 Windows Mixed Reality 徽标的按钮，为 SteamVR 设置打开 **Windows Mixed reality** 。</span><span class="sxs-lookup"><span data-stu-id="ef08b-195">Select the button on the left side with the Windows Mixed Reality logo to open **Windows Mixed Reality for SteamVR** Settings.</span></span>
4. <span data-ttu-id="ef08b-196">在弹出的 UI 中，选择 "图形" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ef08b-196">In the UI that pops up, select the Graphics tab.</span></span>
5. <span data-ttu-id="ef08b-197">选择 "自动" 作为 "默认 SteamVR 应用动作 reprojection 模式" 以启用自动运动 reprojection。</span><span class="sxs-lookup"><span data-stu-id="ef08b-197">Select "Auto" for "Default SteamVR app motion reprojection mode" to enable automatic motion reprojection.</span></span>

![启用 SettingsUX 的 LSR & LSR 指示器](images/settingsux-enable-lsr.gif)

<span data-ttu-id="ef08b-199">**运动 Reprojection 指示器**</span><span class="sxs-lookup"><span data-stu-id="ef08b-199">**Motion Reprojection Indicator**</span></span>

<span data-ttu-id="ef08b-200">运动 reprojection 指示器有助于诊断试验性自动运动 reprojection 功能的问题。</span><span class="sxs-lookup"><span data-stu-id="ef08b-200">The motion reprojection indicator helps diagnose issues with the experimental automatic motion reprojection feature.</span></span> <span data-ttu-id="ef08b-201">如果设置为 true，则会在自动运动 reprojection 过程中的耳机显示的左上角看到指示器。</span><span class="sxs-lookup"><span data-stu-id="ef08b-201">When set to true, you'll see an indicator in the top-left of your headset display during automatic motion reprojection.</span></span> <span data-ttu-id="ef08b-202">此指示器的颜色和位置与当前运动 reprojection 模式相对应-有关示例，请参阅下图。</span><span class="sxs-lookup"><span data-stu-id="ef08b-202">The color and position of this indicator corresponds to the current motion reprojection mode - see the diagram below for examples.</span></span>

![mvLSR 指示器](images/mvLSRIndicator.png)

<span data-ttu-id="ef08b-204">绿色 = 运动 reprojection 是关闭的，因为应用程序可以以完整的帧速率呈现。</span><span class="sxs-lookup"><span data-stu-id="ef08b-204">Green = motion reprojection is off because the application can render at full framerate.</span></span>

<span data-ttu-id="ef08b-205">蓝绿色 = 运动 reprojection 为 on，因为应用程序是 cpu 界限。</span><span class="sxs-lookup"><span data-stu-id="ef08b-205">Cyan = motion reprojection is on because the application is cpu bound.</span></span>

<span data-ttu-id="ef08b-206">Blue = 运动 reprojection 为 on，因为应用程序是 gpu 界限。</span><span class="sxs-lookup"><span data-stu-id="ef08b-206">Blue = motion reprojection is on because the application is gpu bound.</span></span>

<span data-ttu-id="ef08b-207">Red = 运动 reprojection 为 off，因为应用程序的运行时间不到半帧率;如果启用，请尝试减少超采样。</span><span class="sxs-lookup"><span data-stu-id="ef08b-207">Red = motion reprojection is off because the application is running at less than half framerate; try reducing super sampling if enabled.</span></span>

<span data-ttu-id="ef08b-208">绿色 + 青色 + 蓝色 = 运动 reprojection 为半帧速率模式，或应用程序请求运动 reprojection。</span><span class="sxs-lookup"><span data-stu-id="ef08b-208">Green + Cyan + Blue = motion reprojection is in half-framerate mode or the application requested motion reprojection.</span></span>

## <a name="sharing-feedback-on-steamvr"></a><span data-ttu-id="ef08b-209">在 SteamVR 上共享反馈</span><span class="sxs-lookup"><span data-stu-id="ef08b-209">Sharing feedback on SteamVR</span></span>

<span data-ttu-id="ef08b-210">如果要改善 Windows Mixed Reality SteamVR 体验，你的反馈非常有用。</span><span class="sxs-lookup"><span data-stu-id="ef08b-210">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="ef08b-211">通过 [Windows 反馈中心](filing-feedback.md)提交所有反馈和 bug。</span><span class="sxs-lookup"><span data-stu-id="ef08b-211">Submit all feedback and bugs through the [Windows Feedback Hub](filing-feedback.md).</span></span> <span data-ttu-id="ef08b-212">请遵循这些建议，帮助我们充分利用您的反馈意见：</span><span class="sxs-lookup"><span data-stu-id="ef08b-212">Follow these suggestions to help us get the most from your feedback:</span></span>

1. <span data-ttu-id="ef08b-213">在 "反馈中心" 中，指出你要在 "哪种类型的反馈" 中报告新问题。</span><span class="sxs-lookup"><span data-stu-id="ef08b-213">In Feedback Hub, indicate that you're reporting a new Problem in the "What kind of feedback is it?"</span></span> <span data-ttu-id="ef08b-214">部分。</span><span class="sxs-lookup"><span data-stu-id="ef08b-214">section at the top.</span></span>
2. <span data-ttu-id="ef08b-215">选择 " **混合现实** " 类别和 " **应用** " 子类别。</span><span class="sxs-lookup"><span data-stu-id="ef08b-215">Select the **Mixed Reality** category and the **Apps** subcategory.</span></span>
3. <span data-ttu-id="ef08b-216">在问题摘要中放入 "SteamVR" 一词。</span><span class="sxs-lookup"><span data-stu-id="ef08b-216">Put the word "SteamVR" in the problem summary.</span></span> <span data-ttu-id="ef08b-217">这可以帮助我们找到你的反馈。</span><span class="sxs-lookup"><span data-stu-id="ef08b-217">That helps us find your feedback.</span></span>
4. <span data-ttu-id="ef08b-218">描述遇到问题时使用的 SteamVR 游戏或应用程序。</span><span class="sxs-lookup"><span data-stu-id="ef08b-218">Describe what SteamVR game or application you were using when you come across the issue.</span></span>
5. <span data-ttu-id="ef08b-219">考虑将 SteamVR 系统报表附加到你的反馈。</span><span class="sxs-lookup"><span data-stu-id="ef08b-219">Consider attaching a SteamVR System Report to your feedback.</span></span> <span data-ttu-id="ef08b-220">这提供了更多的日志，可帮助我们诊断你的问题。</span><span class="sxs-lookup"><span data-stu-id="ef08b-220">This provides more logs that can help us diagnose your problem.</span></span>
    1. <span data-ttu-id="ef08b-221">在 "SteamVR" 窗口中 (显示控制器状态的小窗口) 选择标题以打开菜单。</span><span class="sxs-lookup"><span data-stu-id="ef08b-221">On the SteamVR Window (the small windows that shows your controller status) select on the title to open the menu.</span></span>
    2. <span data-ttu-id="ef08b-222">选择 "创建系统报表"。</span><span class="sxs-lookup"><span data-stu-id="ef08b-222">Select "Create System Report".</span></span>
    3. <span data-ttu-id="ef08b-223">保存到文件。</span><span class="sxs-lookup"><span data-stu-id="ef08b-223">Save to File.</span></span>
    4. <span data-ttu-id="ef08b-224">直接将生成的文件附加到反馈中心条目。</span><span class="sxs-lookup"><span data-stu-id="ef08b-224">Attach the generated file to your Feedback Hub entry directly.</span></span>
6. <span data-ttu-id="ef08b-225">如果你的反馈与 SteamVR 性能有关，请收集混合现实性能跟踪：</span><span class="sxs-lookup"><span data-stu-id="ef08b-225">If your feedback is about SteamVR performance, collect a Mixed Reality Performance trace:</span></span> 
    1. <span data-ttu-id="ef08b-226">选择 " **重新创建我的问题** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="ef08b-226">Select the **Recreate my Problem** button.</span></span>
    2. <span data-ttu-id="ef08b-227">在 "包含有关的数据" 旁边的下拉菜单中，选择 " **混合现实性能**"。</span><span class="sxs-lookup"><span data-stu-id="ef08b-227">In the drop-down next to "include data about", select **Mixed Reality Performance**.</span></span>
    3. <span data-ttu-id="ef08b-228">请确保游戏正在运行，然后选择 " **开始捕获**"。</span><span class="sxs-lookup"><span data-stu-id="ef08b-228">Make sure the game is running and select **Start Capture**.</span></span>
    4. <span data-ttu-id="ef08b-229">花费几秒钟时间来捕获跟踪。</span><span class="sxs-lookup"><span data-stu-id="ef08b-229">Spend a few seconds playing the game to capture the trace.</span></span> <span data-ttu-id="ef08b-230">请勿捕获超过10-15 秒的跟踪，或者将过大，无法提交。</span><span class="sxs-lookup"><span data-stu-id="ef08b-230">Don't capture the trace for more than 10-15 seconds, or it will be too large to submit.</span></span>
    5. <span data-ttu-id="ef08b-231">选择 " **停止捕获**"。</span><span class="sxs-lookup"><span data-stu-id="ef08b-231">Select **Stop Capture**.</span></span>
7. <span data-ttu-id="ef08b-232">完成剩余字段后，选择 " **提交** "。</span><span class="sxs-lookup"><span data-stu-id="ef08b-232">Select **Submit** once you've completed the rest of the fields.</span></span>

<span data-ttu-id="ef08b-233">如果你有任何疑问或意见要分享，你也可以通过我们的 [流论坛](http://steamcommunity.com/app/719950/discussions/)联系我们。</span><span class="sxs-lookup"><span data-stu-id="ef08b-233">If you have questions or comments to share, you can also reach us on our [Steam forum](http://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef08b-234">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef08b-234">See also</span></span>

* [<span data-ttu-id="ef08b-235">SteamVR 排查 Windows Mixed Reality 问题</span><span class="sxs-lookup"><span data-stu-id="ef08b-235">Troubleshooting SteamVR with Windows Mixed Reality</span></span>](steamvr-questions.md)
* [<span data-ttu-id="ef08b-236">在 Windows Mixed Reality 中使用游戏和应用</span><span class="sxs-lookup"><span data-stu-id="ef08b-236">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="ef08b-237">在 Unity 中使用 HP 控制器</span><span class="sxs-lookup"><span data-stu-id="ef08b-237">Using HP Controllers in Unity</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [<span data-ttu-id="ef08b-238">在 Unreal 中使用 HP 控制器</span><span class="sxs-lookup"><span data-stu-id="ef08b-238">Using HP Controllers in Unreal</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [<span data-ttu-id="ef08b-239">提交 bug 和反馈</span><span class="sxs-lookup"><span data-stu-id="ef08b-239">Filing bugs and feedback</span></span>](filing-feedback.md)
