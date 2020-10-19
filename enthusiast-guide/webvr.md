---
title: 将 WebVR 与 Windows Mixed Reality 一起使用
description: 介绍 WebVR，以及如何在 Windows Mixed Reality 耳机上与 Microsoft Edge 结合使用。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，WebVR，Edge，Microsoft Edge，web 浏览
ms.openlocfilehash: e57ad060a1a539e90631d1b9f1808d1e8466e669
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174343"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="90e69-104">将 WebVR 与 Windows Mixed Reality 一起使用</span><span class="sxs-lookup"><span data-stu-id="90e69-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT] 
><span data-ttu-id="90e69-105">大多数新式 web 浏览器的 WebVR 支持 WebXR，这是为取代了 VR 耳机创建沉浸式 web 体验的新标准。</span><span class="sxs-lookup"><span data-stu-id="90e69-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="90e69-106">请安装 [新的 Microsoft Edge](using-microsoft-edge.md) for WebXR 支持。</span><span class="sxs-lookup"><span data-stu-id="90e69-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="90e69-107">什么是 WebVR？</span><span class="sxs-lookup"><span data-stu-id="90e69-107">What is WebVR?</span></span>

<span data-ttu-id="90e69-108">[WebVR](https://webvr.info) 是一个开放规范，可以在浏览器中体验 VR。</span><span class="sxs-lookup"><span data-stu-id="90e69-108">[WebVR](https://webvr.info) is an open specification that makes it possible to experience VR in your browser.</span></span> <span data-ttu-id="90e69-109">如果某个网站实现 WebVR 支持并提供3D 内容，则它可以在耳机中显示沉浸式内容，同时提供用户同意。</span><span class="sxs-lookup"><span data-stu-id="90e69-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="90e69-110">WebVR 与在 VR 中浏览网站之间的区别是什么？</span><span class="sxs-lookup"><span data-stu-id="90e69-110">What is the difference between WebVR and browsing the web in VR?</span></span>

<span data-ttu-id="90e69-111">WebVR 是一种技术，允许网站作者将 VR 功能添加到页面。</span><span class="sxs-lookup"><span data-stu-id="90e69-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="90e69-112">页面使用 WebVR API 来显示三维内容 (例如360度视频或3D 模型，或将三维游戏) 到整个耳机。</span><span class="sxs-lookup"><span data-stu-id="90e69-112">The WebVR API is used by a page to display 3D content (such as 360 degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="90e69-113">**示例：** 在 [cnn.com/vr](http://cnn.com/vr)上查看360视频。</span><span class="sxs-lookup"><span data-stu-id="90e69-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="90e69-114">如果页面支持 WebVR，它将添加一个按钮或其他用户界面元素，你可以单击该按钮来进入 VR。</span><span class="sxs-lookup"><span data-stu-id="90e69-114">If a page supports WebVR, it will add a button or other UI element that you can click to enter VR.</span></span>

<span data-ttu-id="90e69-115">在 VR 中浏览 web 意味着在戴上耳机时使用 Edge 浏览器，这是 Cliffhouse 中的2D 应用程序石板。</span><span class="sxs-lookup"><span data-stu-id="90e69-115">Browsing the web in VR means using the Edge browser while you are wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="90e69-116">所有网站是否支持 WebVR？</span><span class="sxs-lookup"><span data-stu-id="90e69-116">Do all websites support WebVR?</span></span>

<span data-ttu-id="90e69-117">否。</span><span class="sxs-lookup"><span data-stu-id="90e69-117">No.</span></span> <span data-ttu-id="90e69-118">网站作者必须选择使用 WebVR，而且他们可能会创建针对特定浏览器、耳机和控制器进行了优化的网站。</span><span class="sxs-lookup"><span data-stu-id="90e69-118">Website authors must opt-in to use WebVR and furthermore they may create sites that are optimized for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="90e69-119">例如，某些 WebVR 内容仅针对 mobile VR 设备进行了优化。</span><span class="sxs-lookup"><span data-stu-id="90e69-119">For example, some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="90e69-120">另外，请记住，网站需要显式创建和提供 WebVR 内容。</span><span class="sxs-lookup"><span data-stu-id="90e69-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="90e69-121">具有一些 WebVR 兼容内容的站点数每天都在增长。</span><span class="sxs-lookup"><span data-stu-id="90e69-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="90e69-122">我可以使用我的 Naopak/Oculus 等来查看 Microsoft Edge 中的 WebVR 内容吗？</span><span class="sxs-lookup"><span data-stu-id="90e69-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge?</span></span>

<span data-ttu-id="90e69-123">否。</span><span class="sxs-lookup"><span data-stu-id="90e69-123">No.</span></span> <span data-ttu-id="90e69-124">必须使用 Windows Mixed Reality 耳机才能使用 WebVR。</span><span class="sxs-lookup"><span data-stu-id="90e69-124">You must use a Windows Mixed Reality headset to use WebVR in Edge.</span></span> <span data-ttu-id="90e69-125">但是，你可以在另一个浏览器中访问 WebVR 内容;请参阅位于以下位置的兼容设备和浏览器的完整列表： [WebVR. rocks](http://webvr.rocks/)。</span><span class="sxs-lookup"><span data-stu-id="90e69-125">However, you may be able to access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="90e69-126">在哪里可以找到 WebVR 开发人员文档？</span><span class="sxs-lookup"><span data-stu-id="90e69-126">Where can I find the WebVR developer documentation?</span></span>

<span data-ttu-id="90e69-127">开发人员文档位于此处： [WebVR 开发人员文档](https://docs.microsoft.com/microsoft-edge/webvr/)。</span><span class="sxs-lookup"><span data-stu-id="90e69-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="90e69-128">我发现了一个具有 WebVR 的网站，该网站在 Windows Mixed Reality 中不起作用。</span><span class="sxs-lookup"><span data-stu-id="90e69-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="90e69-129">我该怎么办？</span><span class="sxs-lookup"><span data-stu-id="90e69-129">What do I do?</span></span>

<span data-ttu-id="90e69-130">你可以在 [问题跟踪](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)程序中直接向 Microsoft Edge 浏览器团队报告断开的网站，也可以通过 twitter 使用 [#EdgeBug 井号标签](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)来向其报告。</span><span class="sxs-lookup"><span data-stu-id="90e69-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="90e69-131">你还可以在 "类别" 下使用 Windows 反馈中心应用记录 bug：</span><span class="sxs-lookup"><span data-stu-id="90e69-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="90e69-132">Microsoft Edge-> 网站问题</span><span class="sxs-lookup"><span data-stu-id="90e69-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="90e69-133">如果 WebVR 正常工作，应该测试哪一页？</span><span class="sxs-lookup"><span data-stu-id="90e69-133">What is a good page to test if WebVR is working?</span></span>

<span data-ttu-id="90e69-134">请参阅 [webvr.info 示例](http://webvr.info/samples/XX-vr-controllers.html)。</span><span class="sxs-lookup"><span data-stu-id="90e69-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="90e69-135">如何实现设置 WebVR？</span><span class="sxs-lookup"><span data-stu-id="90e69-135">How do I set up WebVR?</span></span>

<span data-ttu-id="90e69-136">若要在 Windows Mixed Reality 耳机上体验 WebVR 内容 (使用硬件或模拟) 你必须：</span><span class="sxs-lookup"><span data-stu-id="90e69-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation) you must:</span></span>
1. <span data-ttu-id="90e69-137">确保你的耳机已连接。</span><span class="sxs-lookup"><span data-stu-id="90e69-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="90e69-138">在桌面上或在混合现实中启动 Microsoft Edge。</span><span class="sxs-lookup"><span data-stu-id="90e69-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="90e69-139">导航到启用了 WebVR 的页。</span><span class="sxs-lookup"><span data-stu-id="90e69-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="90e69-140">单击页面中的 "输入 VR" 按钮 (该按钮的位置和视觉表示形式可能因网站) 而异。</span><span class="sxs-lookup"><span data-stu-id="90e69-140">Click the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="90e69-141">它看起来可能类似于： </span><span class="sxs-lookup"><span data-stu-id="90e69-141">It may look similar to:</span></span>\
   ![VR Goggles 映像](images/75px-enter-vr.png)
5. <span data-ttu-id="90e69-143">首次在特定域上尝试输入 VR 时，浏览器将要求同意使用沉浸式视图，并单击 "是"：</span><span class="sxs-lookup"><span data-stu-id="90e69-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, click yes:</span></span> ![首次尝试在特定域上进入 VR 时显示的同意 UI](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="90e69-145">你的耳机应该开始显示 WebVR 内容。</span><span class="sxs-lookup"><span data-stu-id="90e69-145">Your headset should begin displaying the WebVR content.</span></span>


## <a name="see-also"></a><span data-ttu-id="90e69-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90e69-146">See also</span></span>

* [<span data-ttu-id="90e69-147">> WebVR 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="90e69-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="90e69-148">如何进入你的第一个 WebVR 体验</span><span class="sxs-lookup"><span data-stu-id="90e69-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="90e69-149">在 Windows Mixed Reality 中使用游戏和应用</span><span class="sxs-lookup"><span data-stu-id="90e69-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="90e69-150">混合现实主页</span><span class="sxs-lookup"><span data-stu-id="90e69-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="90e69-151">跟踪系统</span><span class="sxs-lookup"><span data-stu-id="90e69-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="90e69-152">运动控制器</span><span class="sxs-lookup"><span data-stu-id="90e69-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="90e69-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="90e69-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="90e69-154">申报反馈</span><span class="sxs-lookup"><span data-stu-id="90e69-154">Filing feedback</span></span>](filing-feedback.md)
