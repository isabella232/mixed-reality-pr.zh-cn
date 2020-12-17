---
title: 更新适用于 Windows Mixed Reality 的 SteamVR 应用
description: 更新 SteamVR 应用程序以最大程度地兼容 Windows Mixed Reality 耳机的最佳实践。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR，兼容性，移植，HoloLens 第一代，混合现实耳机，windows mixed reality 耳机，迁移，Windows 10，流，运动控制器，haptics
ms.openlocfilehash: 94b6aad63156d752858c6566174ff01e6127d75d
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612901"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a><span data-ttu-id="a5fb6-104">更新适用于 Windows Mixed Reality 的 SteamVR 应用</span><span class="sxs-lookup"><span data-stu-id="a5fb6-104">Updating SteamVR apps for Windows Mixed Reality</span></span>

<span data-ttu-id="a5fb6-105">我们鼓励开发人员测试并优化其 SteamVR 体验，以便在 Windows Mixed Reality 耳机上运行。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="a5fb6-106">本文档介绍了在 Windows Mixed Reality 上体验出色运行的常见改进。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-106">This documentation covers common improvements you can make to get your experiences running great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="a5fb6-107">初始设置说明</span><span class="sxs-lookup"><span data-stu-id="a5fb6-107">Initial setup instructions</span></span>

<span data-ttu-id="a5fb6-108">若要在 Windows Mixed Reality 上开始测试您的游戏或应用程序，请确保先遵循我们的 [入门指南。](https://aka.ms/WindowsMixedRealitySteamVR)</span><span class="sxs-lookup"><span data-stu-id="a5fb6-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](https://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="a5fb6-109">控制器型号</span><span class="sxs-lookup"><span data-stu-id="a5fb6-109">Controller Models</span></span>

1. <span data-ttu-id="a5fb6-110">如果应用呈现控制器模型：</span><span class="sxs-lookup"><span data-stu-id="a5fb6-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="a5fb6-111">使用 [Windows Mixed Reality 运动控制器模型](../../design/motion-controllers.md#rendering-the-motion-controller-model)</span><span class="sxs-lookup"><span data-stu-id="a5fb6-111">Use the [Windows Mixed Reality motion controller models](../../design/motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="a5fb6-112">使用 IVRRenderModel：： GetComponentState 获取对组件部分的本地转换 (例如，指针姿势) </span><span class="sxs-lookup"><span data-stu-id="a5fb6-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (for example, Pointer pose)</span></span>
2. <span data-ttu-id="a5fb6-113">具有左右手使用习惯概念的经验应从输入 Api 获取提示，以区分控制器 [ (Unity 示例) ](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="a5fb6-113">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="a5fb6-114">控制</span><span class="sxs-lookup"><span data-stu-id="a5fb6-114">Controls</span></span>

<span data-ttu-id="a5fb6-115">设计或调整控件布局时，请记住以下保留命令集：</span><span class="sxs-lookup"><span data-stu-id="a5fb6-115">When designing or adjusting your control layout, keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="a5fb6-116">在 **左侧和右侧的模拟操纵杆** 中，会保留在 " **流" 仪表板** 中。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-116">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard**.</span></span>

> [!NOTE]
> <span data-ttu-id="a5fb6-117">如果使用的是 HP 回音 G2 控制器，请单击 " **流" 仪表板** 的 "向右菜单按钮"。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-117">If you're using an HP Reverb G2 controller, clicking the right menu button is reserved for the **Steam Dashboard**.</span></span>

2. <span data-ttu-id="a5fb6-118">**Windows 按钮** 将始终向 Windows Mixed Reality 主页返回用户。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-118">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="a5fb6-119">如果可能，则默认为基于操纵杆的 teleportation，以匹配 [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation 行为</span><span class="sxs-lookup"><span data-stu-id="a5fb6-119">If possible, default to thumbstick-based teleportation to match the [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="a5fb6-120">工具提示和 UI</span><span class="sxs-lookup"><span data-stu-id="a5fb6-120">Tooltips and UI</span></span>

<span data-ttu-id="a5fb6-121">许多 VR 游戏都利用运动控制器工具提示和覆盖来向用户的应用程序或游戏讲解最重要的命令。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-121">Many VR games take advantage of motion controller tooltips and overlays to teach users their app or games most important commands.</span></span> <span data-ttu-id="a5fb6-122">为 Windows Mixed reality 优化应用程序时，我们建议查看此部分体验，确保工具提示映射到 Windows 控制器模型。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-122">When tuning your application for Windows Mixed reality, we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="a5fb6-123">此外，如果你在其中显示了控制器图像的任何点，请确保使用 Windows Mixed Reality 运动控制器提供更新的图像。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-123">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="a5fb6-124">Haptics</span><span class="sxs-lookup"><span data-stu-id="a5fb6-124">Haptics</span></span>

<span data-ttu-id="a5fb6-125">从 [windows 10 2018 年4月的更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)开始，现在支持 Haptics 在 Windows Mixed Reality 上的 SteamVR 体验。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-125">Beginning with the [Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="a5fb6-126">如果你的 SteamVR 应用或游戏已包含对 haptics 的支持，则它现在应 (，而不会) 使用 [Windows Mixed Reality 运动控制器](../../design/motion-controllers.md)的其他工作。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-126">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](../../design/motion-controllers.md).</span></span>

<span data-ttu-id="a5fb6-127">Windows Mixed Reality 运动控制器使用标准的 haptics 马达，而不是在其他 SteamVR 运动控制器中找到的线性传动装置。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-127">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers.</span></span> <span data-ttu-id="a5fb6-128">这可能会导致用户体验略有不同。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-128">This can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="a5fb6-129">因此，建议通过 Windows Mixed Reality 运动控制器来测试和优化 haptics 设计。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-129">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="a5fb6-130">例如，有时短 haptic 脉冲 (5-10 ms) 在 Windows Mixed Reality 运动控制器上不太明显。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-130">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="a5fb6-131">若要生成更明显的脉冲，请尝试发送更长的 "单击" (40-70 ms) ，以使该马达更长时间启动，然后再次将其关闭。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-131">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70 ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="a5fb6-132">从 Windows Mixed Reality 开始菜单启动 SteamVR 应用</span><span class="sxs-lookup"><span data-stu-id="a5fb6-132">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="a5fb6-133">对于通过流分发的 VR 体验，我们已 [更新 SteamVR 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 以及最新的 [windows 版本](https://insider.windows.com)。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-133">For VR experiences distributed through Steam, we've [updated Windows Mixed Reality for SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows releases](https://insider.windows.com).</span></span> <span data-ttu-id="a5fb6-134">SteamVR 标题现在会自动显示在 "所有应用" 列表的 "Windows Mixed Reality 开始" 菜单中。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-134">SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="a5fb6-135">Windows Mixed Reality 徽标</span><span class="sxs-lookup"><span data-stu-id="a5fb6-135">Windows Mixed Reality logo</span></span>

<span data-ttu-id="a5fb6-136">若要为标题显示 Windows Mixed Reality 支持，请转到应用登录页上的 "编辑存储页" 链接，选择 "基本信息" 选项卡，然后向下滚动到 "虚拟现实"。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-136">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, select the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="a5fb6-137">取消选中 "隐藏 Windows Mixed Reality"，然后发布到应用商店。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-137">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="a5fb6-138">Bug 和反馈</span><span class="sxs-lookup"><span data-stu-id="a5fb6-138">Bugs and feedback</span></span>

<span data-ttu-id="a5fb6-139">如果要改善 Windows Mixed Reality SteamVR 体验，你的反馈非常有用。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-139">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="a5fb6-140">通过 [Windows 反馈中心](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)提交所有反馈和 bug。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-140">Submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="a5fb6-141">下面是 [有关如何使你的 SteamVR 反馈尽可能有用](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)的一些提示。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-141">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="a5fb6-142">如果你有任何疑问或意见要分享，你也可以通过我们的 [流论坛](https://steamcommunity.com/app/719950/discussions/)联系我们。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-142">If you have questions or comments to share, you can also reach us on our [Steam forum](https://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="a5fb6-143">常见问题和疑难解答</span><span class="sxs-lookup"><span data-stu-id="a5fb6-143">FAQs and troubleshooting</span></span>

<span data-ttu-id="a5fb6-144">如果正在运行设置或播放体验的一般问题，请 [查看最新的故障排除步骤](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。</span><span class="sxs-lookup"><span data-stu-id="a5fb6-144">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5fb6-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5fb6-145">See also</span></span>

* [<span data-ttu-id="a5fb6-146">安装工具</span><span class="sxs-lookup"><span data-stu-id="a5fb6-146">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="a5fb6-147">耳机和运动控制器驱动程序历史记录</span><span class="sxs-lookup"><span data-stu-id="a5fb6-147">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="a5fb6-148">Windows Mixed Reality 最小电脑硬件兼容性指南</span><span class="sxs-lookup"><span data-stu-id="a5fb6-148">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
