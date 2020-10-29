---
title: 跟踪常见问题解答
description: 高级 Windows Mixed Reality 故障排除，超出了标准使用者支持文档的范围。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，跟踪
ms.openlocfilehash: b29df6f17bed52d3115faede10cdce91a7ea637f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677556"
---
# <a name="tracking-faqs"></a><span data-ttu-id="b8e07-104">跟踪常见问题解答</span><span class="sxs-lookup"><span data-stu-id="b8e07-104">Tracking FAQs</span></span>

## <a name="my-headset-has-stopped-tracking"></a><span data-ttu-id="b8e07-105">我的耳机已停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="b8e07-105">My headset has stopped tracking.</span></span>

<span data-ttu-id="b8e07-106">请确保指示灯亮起，并且没有任何内容阻碍耳机前面的内部跟踪相机。</span><span class="sxs-lookup"><span data-stu-id="b8e07-106">Make sure the lights are on, and that there isn't anything obstructing the inside-out tracking cameras on the front of your headset.</span></span> <span data-ttu-id="b8e07-107">如果跟踪丢失，可能需要几秒钟才能恢复。</span><span class="sxs-lookup"><span data-stu-id="b8e07-107">If tracking is lost, it can take a few seconds to resume.</span></span> <span data-ttu-id="b8e07-108">如果它没有恢复，请重新启动 Windows Mixed Reality 门户。</span><span class="sxs-lookup"><span data-stu-id="b8e07-108">If it doesn't resume, restart the Windows Mixed Reality Portal.</span></span> 

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a><span data-ttu-id="b8e07-109">我可以找出，但无法转换 (我在 3DOF) 。</span><span class="sxs-lookup"><span data-stu-id="b8e07-109">I can look around but I can't translate (I'm stuck in 3DOF).</span></span>

<span data-ttu-id="b8e07-110">这意味着跟踪系统无法生成姿势，或应用程序已停止使用新的姿势数据来呈现。</span><span class="sxs-lookup"><span data-stu-id="b8e07-110">This means that the tracking system cannot generate pose, or the application has stopped using new pose data to render.</span></span> <span data-ttu-id="b8e07-111">检查下列项目：</span><span class="sxs-lookup"><span data-stu-id="b8e07-111">Check the following:</span></span>
* <span data-ttu-id="b8e07-112">请确保空间充足。</span><span class="sxs-lookup"><span data-stu-id="b8e07-112">Make sure the room has enough light.</span></span>
* <span data-ttu-id="b8e07-113">请确保会议室有足够的详细信息可供跟踪。</span><span class="sxs-lookup"><span data-stu-id="b8e07-113">Make sure the room has enough details to track.</span></span>
* <span data-ttu-id="b8e07-114">拔出设备，关闭 Windows Mixed Reality，并再次插入设备。</span><span class="sxs-lookup"><span data-stu-id="b8e07-114">Unplug the device, close Windows Mixed Reality, and plug in the device again.</span></span>
* <span data-ttu-id="b8e07-115">如果消息仍然存在，请联系 [客户支持部门](https://support.microsoft.com/)</span><span class="sxs-lookup"><span data-stu-id="b8e07-115">If the message persists, contact [customer support](https://support.microsoft.com/)</span></span>

## <a name="the-view-in-the-hmd-is-completely-frozen"></a><span data-ttu-id="b8e07-116">HMD 中的视图被完全冻结。</span><span class="sxs-lookup"><span data-stu-id="b8e07-116">The view in the HMD is completely frozen.</span></span>

<span data-ttu-id="b8e07-117">这通常意味着应用程序或系统级组件发生了故障。</span><span class="sxs-lookup"><span data-stu-id="b8e07-117">This usually means the application or a system level component has failed.</span></span> <span data-ttu-id="b8e07-118">尝试执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b8e07-118">Try to:</span></span>
1. <span data-ttu-id="b8e07-119">按 "home" 按钮退出应用程序。</span><span class="sxs-lookup"><span data-stu-id="b8e07-119">Press the "home" button to leave the application.</span></span>
2. <span data-ttu-id="b8e07-120">拔出设备，关闭 MRP 并重新插回设备。</span><span class="sxs-lookup"><span data-stu-id="b8e07-120">Unplug the device, close MRP and plug the device back in.</span></span>
3. <span data-ttu-id="b8e07-121">重启电脑。</span><span class="sxs-lookup"><span data-stu-id="b8e07-121">Restart the PC.</span></span>

## <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-down-before-returning-to-normal"></a><span data-ttu-id="b8e07-122">在返回到正常状态之前，世界会短暂冻结，可能会向下倾斜或颠倒。</span><span class="sxs-lookup"><span data-stu-id="b8e07-122">The world briefly froze and perhaps tilted or flipped upside down before returning to normal.</span></span>

<span data-ttu-id="b8e07-123">这可能是由于应用程序或系统级别组件出现严重错误，或者暂时缺乏内存或 CPU 资源。</span><span class="sxs-lookup"><span data-stu-id="b8e07-123">This could be caused by an application or system level component hitting a fatal error, or a temporary lack of memory or CPU resources.</span></span> <span data-ttu-id="b8e07-124">若要检查：</span><span class="sxs-lookup"><span data-stu-id="b8e07-124">To check:</span></span>
1. <span data-ttu-id="b8e07-125">打开任务管理器，确保至少20% 的 CPU 处于空闲状态，400MB 的内存可用，磁盘 IO 应该低于80%。</span><span class="sxs-lookup"><span data-stu-id="b8e07-125">Open Task Manager and ensure that at least 20% of the CPU is free, 400MB of memory is available and disk IO should be below 80%.</span></span>
2. <span data-ttu-id="b8e07-126">请参阅 **事件查看器 > Windows 日志 > 应用程序** ，以查看冻结时间周围的任何错误。</span><span class="sxs-lookup"><span data-stu-id="b8e07-126">Go to **Event Viewer > Windows Logs > Application** to look for any errors from around the time of the freeze.</span></span> <span data-ttu-id="b8e07-127">查找所有引用 HoloLens 传感器、混合现实或在此时间段内运行的应用程序的内容。</span><span class="sxs-lookup"><span data-stu-id="b8e07-127">Look for anything that refers to HoloLens sensors, Mixed Reality, or the application that you were running around that time.</span></span> <span data-ttu-id="b8e07-128">这些日志可能解释导致失败的原因。</span><span class="sxs-lookup"><span data-stu-id="b8e07-128">Those logs might explain what caused the failure.</span></span>
3. <span data-ttu-id="b8e07-129">如果问题仍然存在，请重启电脑。</span><span class="sxs-lookup"><span data-stu-id="b8e07-129">Restart the PC if the problem persists.</span></span>

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a><span data-ttu-id="b8e07-130">世界翻转并返回到正常状态。</span><span class="sxs-lookup"><span data-stu-id="b8e07-130">The world flipped upside down momentarily and returned to normal.</span></span>

<span data-ttu-id="b8e07-131">这通常是由于从耳机获取传感器数据以通知跟踪算法时出错引起的。</span><span class="sxs-lookup"><span data-stu-id="b8e07-131">This is typically caused by errors in obtaining sensor data from the headset to inform the tracking algorithms.</span></span> <span data-ttu-id="b8e07-132">如果经常发生这种情况：</span><span class="sxs-lookup"><span data-stu-id="b8e07-132">If this happens frequently:</span></span>
1. <span data-ttu-id="b8e07-133">将耳机插入到其他 USB 3.0 端口。</span><span class="sxs-lookup"><span data-stu-id="b8e07-133">Plug the headset into a different USB 3.0 port.</span></span>
2. <span data-ttu-id="b8e07-134">将耳机直接插入 PC 而不是 USB 3.0 集线器。</span><span class="sxs-lookup"><span data-stu-id="b8e07-134">Plug the headset directly into the PC rather than into a USB 3.0 hub.</span></span>
3. <span data-ttu-id="b8e07-135">如果问题仍然存在，请与 [客户支持](https://support.microsoft.com/)联系。</span><span class="sxs-lookup"><span data-stu-id="b8e07-135">If the problem persists, contact [customer support](https://support.microsoft.com/).</span></span>

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a><span data-ttu-id="b8e07-136">世界是倾斜的，但我可以在 Windows Mixed Reality 中导航并四处浏览。</span><span class="sxs-lookup"><span data-stu-id="b8e07-136">The world is tilted but I can navigate and walk around in Windows Mixed Reality.</span></span>

<span data-ttu-id="b8e07-137">如果传感器数据错误记录到电脑上的环境数据中，则可能会导致 Windows Mixed Reality 显示为倾斜，有时会永久显示。</span><span class="sxs-lookup"><span data-stu-id="b8e07-137">If sensor data errors are recorded into the environment data on your PC, it can cause Windows Mixed Reality to appear tilted, sometimes permanently.</span></span> <span data-ttu-id="b8e07-138">解决方法：</span><span class="sxs-lookup"><span data-stu-id="b8e07-138">To fix this:</span></span>
1. <span data-ttu-id="b8e07-139">拔出耳机，关闭 Windows Mixed Reality 并插上耳机。</span><span class="sxs-lookup"><span data-stu-id="b8e07-139">Unplug the headset, close Windows Mixed Reality and plug the headset back in.</span></span>
2. <span data-ttu-id="b8e07-140">重启电脑。</span><span class="sxs-lookup"><span data-stu-id="b8e07-140">Restart the PC.</span></span>
3. <span data-ttu-id="b8e07-141">清除你的环境数据。</span><span class="sxs-lookup"><span data-stu-id="b8e07-141">Clear your environment data.</span></span>

