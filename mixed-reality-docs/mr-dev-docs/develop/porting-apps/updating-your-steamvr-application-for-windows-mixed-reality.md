---
title: 更新你的 SteamVR 应用程序
description: 更新 SteamVR 应用程序以最大程度地提高 Windows Mixed Reality 耳机的最佳实践。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR，兼容性
ms.openlocfilehash: 4a1439bed8743396cba13fa4d65debc62487ab46
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638503"
---
# <a name="updating-your-steamvr-application"></a><span data-ttu-id="dd375-104">更新你的 SteamVR 应用程序</span><span class="sxs-lookup"><span data-stu-id="dd375-104">Updating your SteamVR application</span></span>
<span data-ttu-id="dd375-105">我们鼓励开发人员测试并优化其 SteamVR 体验，以便在 Windows Mixed Reality 耳机上运行。</span><span class="sxs-lookup"><span data-stu-id="dd375-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="dd375-106">本文档介绍了开发人员可以执行的一些常见改进，以确保其体验在 Windows Mixed Reality 上运行良好。</span><span class="sxs-lookup"><span data-stu-id="dd375-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="dd375-107">初始设置说明</span><span class="sxs-lookup"><span data-stu-id="dd375-107">Initial setup instructions</span></span>

<span data-ttu-id="dd375-108">若要在 Windows Mixed Reality 上开始测试您的游戏或应用程序，请确保先遵循我们的 [入门指南。](https://aka.ms/WindowsMixedRealitySteamVR)</span><span class="sxs-lookup"><span data-stu-id="dd375-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](https://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="dd375-109">控制器型号</span><span class="sxs-lookup"><span data-stu-id="dd375-109">Controller Models</span></span>
1. <span data-ttu-id="dd375-110">如果应用呈现控制器模型：</span><span class="sxs-lookup"><span data-stu-id="dd375-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="dd375-111">使用 [Windows Mixed Reality 运动控制器模型](../../design/motion-controllers.md#rendering-the-motion-controller-model)</span><span class="sxs-lookup"><span data-stu-id="dd375-111">Use the [Windows Mixed Reality motion controller models](../../design/motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="dd375-112">使用 IVRRenderModel：： GetComponentState 获取对组件部件的本地转换 (例如。</span><span class="sxs-lookup"><span data-stu-id="dd375-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="dd375-113">指针姿势) </span><span class="sxs-lookup"><span data-stu-id="dd375-113">Pointer pose)</span></span>
2. <span data-ttu-id="dd375-114">具有左右手使用习惯概念的经验应从输入 Api 获取提示，以区分控制器 [ (Unity 示例) ](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="dd375-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="dd375-115">控制</span><span class="sxs-lookup"><span data-stu-id="dd375-115">Controls</span></span>

<span data-ttu-id="dd375-116">设计或调整控件布局时，请记住以下保留命令集：</span><span class="sxs-lookup"><span data-stu-id="dd375-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="dd375-117">在 **左侧和右侧的模拟操纵杆** 中，会保留在 " **流" 仪表板** 中。</span><span class="sxs-lookup"><span data-stu-id="dd375-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard** .</span></span>

> [!NOTE]
> <span data-ttu-id="dd375-118">如果使用的是 HP 回音 G2 控制器，请单击 " **流" 仪表板** 的 "向右菜单按钮"。</span><span class="sxs-lookup"><span data-stu-id="dd375-118">If you're using an HP Reverb G2 controller, clicking the right menu button is reserved for the **Steam Dashboard** .</span></span>

2. <span data-ttu-id="dd375-119">**Windows 按钮** 将始终向 Windows Mixed Reality 主页返回用户。</span><span class="sxs-lookup"><span data-stu-id="dd375-119">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="dd375-120">如果可能，则默认为基于拇指的 teleportation，以匹配 [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation 行为</span><span class="sxs-lookup"><span data-stu-id="dd375-120">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="dd375-121">工具提示和 UI</span><span class="sxs-lookup"><span data-stu-id="dd375-121">Tooltips and UI</span></span>

<span data-ttu-id="dd375-122">许多 VR 游戏都利用了运动控制器工具提示和覆盖向用户讲授其游戏或应用程序的最重要命令。</span><span class="sxs-lookup"><span data-stu-id="dd375-122">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="dd375-123">优化 Windows Mixed reality 应用程序时，我们建议查看此部分体验，确保工具提示映射到 Windows 控制器模型。</span><span class="sxs-lookup"><span data-stu-id="dd375-123">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="dd375-124">此外，如果你在其中显示了控制器图像的任何点，请确保使用 Windows Mixed Reality 运动控制器提供更新的图像。</span><span class="sxs-lookup"><span data-stu-id="dd375-124">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="dd375-125">Haptics</span><span class="sxs-lookup"><span data-stu-id="dd375-125">Haptics</span></span>

<span data-ttu-id="dd375-126">从 [windows 10 2018 年4月的更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)开始，现在支持 Haptics 在 Windows Mixed Reality 上的 SteamVR 体验。</span><span class="sxs-lookup"><span data-stu-id="dd375-126">Beginning with the [Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="dd375-127">如果你的 SteamVR 应用或游戏已包含对 haptics 的支持，则它现在应 (，而不会) 使用 [Windows Mixed Reality 运动控制器](../../design/motion-controllers.md)的其他工作。</span><span class="sxs-lookup"><span data-stu-id="dd375-127">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](../../design/motion-controllers.md).</span></span>

<span data-ttu-id="dd375-128">Windows Mixed Reality 运动控制器使用标准的 haptics 马达，而不是在其他 SteamVR 运动控制器中找到的线性传动装置，这可能会导致用户体验略有不同。</span><span class="sxs-lookup"><span data-stu-id="dd375-128">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="dd375-129">因此，建议通过 Windows Mixed Reality 运动控制器来测试和优化 haptics 设计。</span><span class="sxs-lookup"><span data-stu-id="dd375-129">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="dd375-130">例如，有时短 haptic 脉冲 (5-10 ms) 在 Windows Mixed Reality 运动控制器上不太明显。</span><span class="sxs-lookup"><span data-stu-id="dd375-130">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="dd375-131">若要生成更明显的脉冲，请尝试发送较长的 "单击" (40-70ms) ，以使该马达在被告知再次关机之前更长时间启动。</span><span class="sxs-lookup"><span data-stu-id="dd375-131">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="dd375-132">从 Windows Mixed Reality 开始菜单启动 SteamVR 应用</span><span class="sxs-lookup"><span data-stu-id="dd375-132">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="dd375-133">对于通过流发布的 VR 体验，我们已 [更新了适用于 SteamVR Beta 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 以及最新的 [windows 有问必答](https://insider.windows.com) RS5 航班，以便 SteamVR 标题现在会自动显示在 "所有应用" 列表的 "Windows mixed reality 开始" 菜单中。</span><span class="sxs-lookup"><span data-stu-id="dd375-133">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="dd375-134">安装这些软件版本后，客户现在可以直接从 Windows Mixed Reality 家里开始 SteamVR 标题，无需删除耳机。</span><span class="sxs-lookup"><span data-stu-id="dd375-134">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="dd375-135">Windows Mixed Reality 徽标</span><span class="sxs-lookup"><span data-stu-id="dd375-135">Windows Mixed Reality logo</span></span>

<span data-ttu-id="dd375-136">若要为标题显示 Windows Mixed Reality 支持，请转到应用登录页上的 "编辑存储页" 链接，单击 "基本信息" 选项卡，然后向下滚动到 "虚拟现实"。</span><span class="sxs-lookup"><span data-stu-id="dd375-136">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="dd375-137">取消选中 "隐藏 Windows Mixed Reality"，然后发布到应用商店。</span><span class="sxs-lookup"><span data-stu-id="dd375-137">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="dd375-138">Bug 和反馈</span><span class="sxs-lookup"><span data-stu-id="dd375-138">Bugs and feedback</span></span>

<span data-ttu-id="dd375-139">如果要改善 Windows Mixed Reality SteamVR 体验，你的反馈非常有用。</span><span class="sxs-lookup"><span data-stu-id="dd375-139">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="dd375-140">请通过 [Windows 反馈中心](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)提交所有反馈和 bug。</span><span class="sxs-lookup"><span data-stu-id="dd375-140">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="dd375-141">下面是 [有关如何使你的 SteamVR 反馈尽可能有用](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)的一些提示。</span><span class="sxs-lookup"><span data-stu-id="dd375-141">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="dd375-142">如果你有任何疑问或意见要分享，你也可以通过我们的 [流论坛](https://steamcommunity.com/app/719950/discussions/)联系我们。</span><span class="sxs-lookup"><span data-stu-id="dd375-142">If you have questions or comments to share, you can also reach us on our [Steam forum](https://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="dd375-143">常见问题和疑难解答</span><span class="sxs-lookup"><span data-stu-id="dd375-143">FAQs and troubleshooting</span></span>

<span data-ttu-id="dd375-144">如果正在运行设置或播放体验的一般问题，请 [查看最新的故障排除步骤](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。</span><span class="sxs-lookup"><span data-stu-id="dd375-144">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd375-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd375-145">See also</span></span>
* [<span data-ttu-id="dd375-146">安装工具</span><span class="sxs-lookup"><span data-stu-id="dd375-146">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="dd375-147">耳机和运动控制器驱动程序历史记录</span><span class="sxs-lookup"><span data-stu-id="dd375-147">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="dd375-148">Windows Mixed Reality 最小电脑硬件兼容性指南</span><span class="sxs-lookup"><span data-stu-id="dd375-148">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
