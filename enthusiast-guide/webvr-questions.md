---
title: WebVR 常见问题
description: Web 混合现实故障排除，超过了标准使用者支持文档。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，WebVR
ms.openlocfilehash: e03051008921f87e18cae3a9f6db369e54c56b94
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131931"
---
# <a name="webvr-faqs"></a><span data-ttu-id="76cde-104">WebVR 常见问题</span><span class="sxs-lookup"><span data-stu-id="76cde-104">WebVR FAQs</span></span>

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a><span data-ttu-id="76cde-105">为什么在从边缘查看 VR 内容时看不到控制器</span><span class="sxs-lookup"><span data-stu-id="76cde-105">Why can’t I see my controllers when viewing VR content from Edge</span></span>

<span data-ttu-id="76cde-106">并非所有 WebVR 内容都是为支持运动控制器而编写的。</span><span class="sxs-lookup"><span data-stu-id="76cde-106">Not all WebVR content is authored to support motion controllers.</span></span> <span data-ttu-id="76cde-107">WebVR 允许内容开发人员支持不同类型的输入，例如游戏控制器或运动控制器。</span><span class="sxs-lookup"><span data-stu-id="76cde-107">WebVR allows content developers to support different types of input, such as game controllers or motion controllers.</span></span> <span data-ttu-id="76cde-108">如果你在站点上看不到控制器，则它可能不支持运动控制器。</span><span class="sxs-lookup"><span data-stu-id="76cde-108">If you do not see your controllers on a site, it probably doesn’t have motion controller support.</span></span>

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a><span data-ttu-id="76cde-109">为什么无法在沉浸式 WebVR 视图中使用鼠标</span><span class="sxs-lookup"><span data-stu-id="76cde-109">Why can't I use the mouse in an immersive WebVR view</span></span>

<span data-ttu-id="76cde-110">这是 WebVR 规范的一项可选功能。</span><span class="sxs-lookup"><span data-stu-id="76cde-110">This is an optional feature of the WebVR specification.</span></span> <span data-ttu-id="76cde-111">并非所有浏览器都支持此功能，并且并不是所有的 WebVR 内容都是为了支持鼠标输入而编写的。</span><span class="sxs-lookup"><span data-stu-id="76cde-111">Not all browsers support this feature, and not all WebVR content is authored to support mouse input.</span></span> <span data-ttu-id="76cde-112">WebVR 允许内容开发人员支持不同类型的输入，例如鼠标、键盘、游戏控制器或运动控制器。</span><span class="sxs-lookup"><span data-stu-id="76cde-112">WebVR allows content developers to support different types of input, such as mouse, keyboard, game controllers or motion controllers.</span></span> <span data-ttu-id="76cde-113">鼠标输入行为因浏览器而异。</span><span class="sxs-lookup"><span data-stu-id="76cde-113">Mouse input behavior varies per browser.</span></span> <span data-ttu-id="76cde-114">在 Microsoft Edge 中，网站作者必须确保在向耳机提供时使用 "pointerlock" 才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="76cde-114">Within Microsoft Edge, website authors must ensure they take 'pointerlock' when presenting to the headset for mouse input to work.</span></span>

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a><span data-ttu-id="76cde-115">为什么无法查看来自 Youtube/Facebook/Vimeo/监护人的360学位视频，等等</span><span class="sxs-lookup"><span data-stu-id="76cde-115">Why can’t I view 360 degree videos from Youtube/Facebook/Vimeo/The Guardian, etc. from Edge in VR</span></span>

<span data-ttu-id="76cde-116">WebVR 规范允许网站直接从浏览器启动 VR 体验，这些网站的作者目前尚未实现此规范。</span><span class="sxs-lookup"><span data-stu-id="76cde-116">There is a WebVR specification that allows websites to launch VR experiences directly from the browser and the authors of these websites have not implemented this specification at this time.</span></span> <span data-ttu-id="76cde-117">在某些平台上，可以使用可下载的应用来查看这些供应商的 VR 内容。</span><span class="sxs-lookup"><span data-stu-id="76cde-117">There may be downloadable apps on some platforms that enable viewing of VR content from these vendors.</span></span>

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a><span data-ttu-id="76cde-118">为什么无法通过 Firefox 或 Chrome 进入 VR</span><span class="sxs-lookup"><span data-stu-id="76cde-118">Why can’t I enter VR from Firefox or Chrome</span></span>

<span data-ttu-id="76cde-119">目前，Windows Mixed Reality 设备目前仅支持 WebVR。</span><span class="sxs-lookup"><span data-stu-id="76cde-119">WebVR is only supported by Windows Mixed Reality devices in Edge at this time.</span></span>

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a><span data-ttu-id="76cde-120">当我从网站输入 "VR" 时，为什么我在我的耳机中看到了空白屏幕</span><span class="sxs-lookup"><span data-stu-id="76cde-120">When I enter VR from a website, why do I see a blank screen in my headset</span></span>

<span data-ttu-id="76cde-121">网站可能未实现对多 GPU 计算机的支持 (包括混合 GPU 便携式计算机) 。</span><span class="sxs-lookup"><span data-stu-id="76cde-121">The website may not have implemented support for multi GPU machines (including hybrid GPU laptops).</span></span> <span data-ttu-id="76cde-122">尝试执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="76cde-122">Try to:</span></span>

* <span data-ttu-id="76cde-123">重载页面。</span><span class="sxs-lookup"><span data-stu-id="76cde-123">Reload the page.</span></span>
* <span data-ttu-id="76cde-124">在台式计算机上，将耳机插入与显示 Microsoft Edge 的监视器相同的图形适配器中。</span><span class="sxs-lookup"><span data-stu-id="76cde-124">On desktop machines, plug the headset into the same graphics adapter as the monitor that is displaying Microsoft Edge.</span></span> <span data-ttu-id="76cde-125">将两者插到更高的显卡，而不是集成图形适配器中。</span><span class="sxs-lookup"><span data-stu-id="76cde-125">Plug both into the higher powered graphics card, not into the integrated graphics adapter.</span></span>

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a><span data-ttu-id="76cde-126">从边缘观看视频时退出 VR 时，声音将继续播放，但边缘窗口灰显</span><span class="sxs-lookup"><span data-stu-id="76cde-126">When I exit VR when watching a video from Edge, the sound continues playing but the Edge window is grayed out</span></span>

<span data-ttu-id="76cde-127">这是在混合现实 Cliff 房子中从边缘运行 WebVR 时的已知问题。</span><span class="sxs-lookup"><span data-stu-id="76cde-127">This is a known issue when running WebVR from Edge in the Mixed Reality Cliff House.</span></span> <span data-ttu-id="76cde-128">若要解决此问题，请按键盘上的 esc 键，而不是按 windows 按钮退出 WebVR 体验，或通过选择并停止视频来激活灰显边缘窗口。</span><span class="sxs-lookup"><span data-stu-id="76cde-128">To resolve it, press escape on the keyboard rather than pressing the windows button to exit the WebVR experience, or activate the greyed out Edge window by selecting it and then stop the video.</span></span>

## <a name="can-i-use-webvr-on-the-hololens"></a><span data-ttu-id="76cde-129">能否在 HoloLens 上使用 WebVR</span><span class="sxs-lookup"><span data-stu-id="76cde-129">Can I use WebVR on the HoloLens</span></span>

<span data-ttu-id="76cde-130">Microsoft 目前还没有在 HoloLens 上公布有关 WebVR 的任何信息。</span><span class="sxs-lookup"><span data-stu-id="76cde-130">Microsoft has not announced anything about WebVR on the HoloLens at this point.</span></span>

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a><span data-ttu-id="76cde-131">从边缘查看 WebVR 内容时，为什么我的视图处于地面级别</span><span class="sxs-lookup"><span data-stu-id="76cde-131">Why is my view at floor level when viewing WebVR content from Edge</span></span>

<span data-ttu-id="76cde-132">网站未正确支持 Windows Mixed Reality 耳机。</span><span class="sxs-lookup"><span data-stu-id="76cde-132">The website does not properly support Windows Mixed Reality headsets.</span></span> <span data-ttu-id="76cde-133">要解决此问题：</span><span class="sxs-lookup"><span data-stu-id="76cde-133">To work around this:</span></span>

1. <span data-ttu-id="76cde-134">将耳机置于空间的基底。</span><span class="sxs-lookup"><span data-stu-id="76cde-134">Place the headset on the floor of your space.</span></span>
2. <span data-ttu-id="76cde-135">使用 Microsoft Edge 在桌面上导航到 WebVR 页面， (不在混合现实) 内。</span><span class="sxs-lookup"><span data-stu-id="76cde-135">Navigate to the WebVR page using Microsoft Edge on your desktop (not within mixed reality).</span></span>
3. <span data-ttu-id="76cde-136">选择 "Enter VR"。</span><span class="sxs-lookup"><span data-stu-id="76cde-136">Select "Enter VR".</span></span>
4. <span data-ttu-id="76cde-137">等待5到10秒，以完全进入沉浸式模式。</span><span class="sxs-lookup"><span data-stu-id="76cde-137">Wait five to 10 seconds for the experience to fully enter immersive mode.</span></span>
5. <span data-ttu-id="76cde-138">戴上耳机。</span><span class="sxs-lookup"><span data-stu-id="76cde-138">Put on the headset.</span></span>

## <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a><span data-ttu-id="76cde-139">在某些 WebVR 体验中，显示器的分辨率非常低</span><span class="sxs-lookup"><span data-stu-id="76cde-139">The display is very low resolution in some WebVR experiences</span></span>

<span data-ttu-id="76cde-140">这些网站不能正确支持高分辨率耳机。</span><span class="sxs-lookup"><span data-stu-id="76cde-140">Those websites do not properly support high resolution headsets.</span></span> <span data-ttu-id="76cde-141">解决方法：</span><span class="sxs-lookup"><span data-stu-id="76cde-141">To workaround this:</span></span>

* <span data-ttu-id="76cde-142">如果从 (桌面启动 WebVR，而不是混合现实 Cliff 房子) ，请在选择 "输入 VR" 之前确保窗口最大化。</span><span class="sxs-lookup"><span data-stu-id="76cde-142">If launching WebVR from the desktop (rather than the mixed reality Cliff House), ensure the window is maximized before selecting "Enter VR".</span></span>
* <span data-ttu-id="76cde-143">输入 VR 后，请避免调整 Microsoft Edge 窗口的大小。</span><span class="sxs-lookup"><span data-stu-id="76cde-143">Avoid resizing the Microsoft Edge window after you have entered VR.</span></span>

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a><span data-ttu-id="76cde-144">为什么当我更改浏览器选项卡时 WebVR 沉浸式视图退出</span><span class="sxs-lookup"><span data-stu-id="76cde-144">Why does the WebVR immersive view exit when I change browser tabs</span></span>

<span data-ttu-id="76cde-145">这是预期行为。</span><span class="sxs-lookup"><span data-stu-id="76cde-145">This is expected behavior.</span></span> <span data-ttu-id="76cde-146">出于安全原因，只有活动的浏览器选项卡可以访问连接的耳机。</span><span class="sxs-lookup"><span data-stu-id="76cde-146">For security reasons, only the active browser tab can access connected headsets.</span></span>

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a><span data-ttu-id="76cde-147">为什么无法在特定的 WebVR 体验中听到音频</span><span class="sxs-lookup"><span data-stu-id="76cde-147">Why can't I hear audio on a particular WebVR experience</span></span>

<span data-ttu-id="76cde-148">网站可能使用的是 Microsoft Edge 当前不支持的 OGG 音频文件格式。</span><span class="sxs-lookup"><span data-stu-id="76cde-148">The website may be using the OGG audio file format, which Microsoft Edge does not currently support.</span></span>

<span data-ttu-id="76cde-149">你可以在 [问题跟踪](https://developer.microsoft.com/microsoft-edge/platform/issues/)程序中直接向 Microsoft Edge 浏览器团队报告断开的网站，也可以通过 twitter 使用 [#EdgeBug 井号标签](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)来向其报告。</span><span class="sxs-lookup"><span data-stu-id="76cde-149">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a><span data-ttu-id="76cde-150">为什么 haptic 反馈在 WebVR 中不能与运动控制器一起使用</span><span class="sxs-lookup"><span data-stu-id="76cde-150">Why does haptic feedback not work in WebVR with motion controllers</span></span>

<span data-ttu-id="76cde-151">Microsoft Edge 目前不支持 WebVR 游戏板 API 扩展上的 haptics。</span><span class="sxs-lookup"><span data-stu-id="76cde-151">Microsoft Edge does not currently support haptics on the WebVR gamepad API extensions.</span></span>