---
title: 性能常见问题解答
description: 高级 Windows Mixed Reality 故障排除，超出了标准使用者支持文档的范围。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，性能
appliesto:
- Windows 10
ms.openlocfilehash: 2150d605ecf29bb0bcf88f0f76a0193046f74ed5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677584"
---
# <a name="performance-faqs"></a><span data-ttu-id="fec50-104">性能常见问题解答</span><span class="sxs-lookup"><span data-stu-id="fec50-104">Performance FAQs</span></span>

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60hz-or-90hz-framerate"></a><span data-ttu-id="fec50-105">我的 Windows Mixed Reality 耳机呈现是否以60Hz 或90Hz 的帧速率显示？</span><span class="sxs-lookup"><span data-stu-id="fec50-105">Is my Windows Mixed Reality headset rendering at 60Hz or 90Hz framerate?</span></span>

<span data-ttu-id="fec50-106">如果有与 HDMI 2.0 端口的离散 GPU 和具有四个或更多物理内核的 CPU，则应该获得 90 Hz。</span><span class="sxs-lookup"><span data-stu-id="fec50-106">If you have a discrete GPU with HDMI 2.0 ports and a CPU with four or more physical cores, you should be getting 90 Hz.</span></span> <span data-ttu-id="fec50-107">若要确认，请检查 **设备门户 > 性能** "选项卡。</span><span class="sxs-lookup"><span data-stu-id="fec50-107">To confirm, check the **Device Portal > Performance** tab.</span></span> 

<span data-ttu-id="fec50-108">注意：如果 GPU 仅有 HDMI 1.4 输出，可以使用 DisplayPort 到 [HDMI 2.0 适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 作为解决方法。</span><span class="sxs-lookup"><span data-stu-id="fec50-108">Note: If your GPU only has a HDMI 1.4 output, you can use a DisplayPort to [HDMI 2.0 adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) as a workaround.</span></span> 

<span data-ttu-id="fec50-109">注意： "耳机显示" 中的视觉质量设置只影响 Windows Mixed Reality 主页体验的呈现。</span><span class="sxs-lookup"><span data-stu-id="fec50-109">Note: The visual quality settings in "Headset display" only affect the rendering of the Windows Mixed Reality home experience.</span></span>

## <a name="my-pc-is-running-slowly"></a><span data-ttu-id="fec50-110">我的 PC 运行速度缓慢。</span><span class="sxs-lookup"><span data-stu-id="fec50-110">My PC is running slowly.</span></span>

<span data-ttu-id="fec50-111">由于很多原因，系统的运行速度可能会很慢，在大多数情况下，这只是最后几秒钟。</span><span class="sxs-lookup"><span data-stu-id="fec50-111">The system may be slow for many reasons and in most cases this only last a few seconds.</span></span> <span data-ttu-id="fec50-112">如果在很长一段时间内遇到此问题：</span><span class="sxs-lookup"><span data-stu-id="fec50-112">If you experience this problem over long periods of time:</span></span>
1. <span data-ttu-id="fec50-113">关闭桌面上所有未使用的应用程序。</span><span class="sxs-lookup"><span data-stu-id="fec50-113">Close all unused application on the desktop.</span></span>
2. <span data-ttu-id="fec50-114">确保便携式计算机已插入电源。</span><span class="sxs-lookup"><span data-stu-id="fec50-114">Ensure that your laptop is plugged into a power source.</span></span>
3. <span data-ttu-id="fec50-115">请确保电脑未预热。</span><span class="sxs-lookup"><span data-stu-id="fec50-115">Make sure that the PC is not warming up.</span></span>
4. <span data-ttu-id="fec50-116">降低 Windows Mixed Reality 主页的视觉质量。</span><span class="sxs-lookup"><span data-stu-id="fec50-116">Lower the visual quality in your Windows Mixed Reality home.</span></span>
5. <span data-ttu-id="fec50-117">确保你具有适用于你的电脑的最新 [图形驱动程序](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) 。</span><span class="sxs-lookup"><span data-stu-id="fec50-117">Ensure that you have the latest [graphics drivers](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) for your PC.</span></span>

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a><span data-ttu-id="fec50-118">我的 PC 正在预热，因为我运行了混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="fec50-118">My PC is warming up as I run the Mixed Reality experiences.</span></span> <span data-ttu-id="fec50-119">如何实现将其设置为酷？</span><span class="sxs-lookup"><span data-stu-id="fec50-119">How do I keep it cool?</span></span>

1. <span data-ttu-id="fec50-120">检查电池是否已充电并接通电源。</span><span class="sxs-lookup"><span data-stu-id="fec50-120">Check that the battery is charged and the power source is plugged in.</span></span>
2. <span data-ttu-id="fec50-121">请确保电脑风扇未被阻止。</span><span class="sxs-lookup"><span data-stu-id="fec50-121">Make sure that the PC fans are not blocked.</span></span>
3. <span data-ttu-id="fec50-122">在相对较酷的环境中使用 PC。</span><span class="sxs-lookup"><span data-stu-id="fec50-122">Use the PC in a relatively cool environment.</span></span>
4. <span data-ttu-id="fec50-123">请确保没有热源 (例如，sun 或热通风口) PC。</span><span class="sxs-lookup"><span data-stu-id="fec50-123">Make sure there are no heat sources (for example, the sun or heat vents) pointed at the PC.</span></span>

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a><span data-ttu-id="fec50-124">我的视觉对象不连贯、负载缓慢或外观不佳。</span><span class="sxs-lookup"><span data-stu-id="fec50-124">My visuals are choppy, load slowly, or don't look good.</span></span>
* <span data-ttu-id="fec50-125">请确保将耳机插入 PC 上的正确图形卡。</span><span class="sxs-lookup"><span data-stu-id="fec50-125">Make sure your headset is plugged into the correct graphics card on your PC.</span></span> <span data-ttu-id="fec50-126">某些 Pc 同时具有集成显卡和离散显卡。</span><span class="sxs-lookup"><span data-stu-id="fec50-126">Some PCs have both integrated and discrete graphics cards.</span></span> <span data-ttu-id="fec50-127">离散卡通常会提供最佳性能。</span><span class="sxs-lookup"><span data-stu-id="fec50-127">The discrete card will generally provide the best performance.</span></span> <span data-ttu-id="fec50-128">[了解有关 PC 硬件的详细信息](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)。</span><span class="sxs-lookup"><span data-stu-id="fec50-128">[Learn more about PC hardware](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).</span></span>
* <span data-ttu-id="fec50-129">关闭桌面上未使用的应用程序。</span><span class="sxs-lookup"><span data-stu-id="fec50-129">Close unused applications on your desktop.</span></span>
* <span data-ttu-id="fec50-130">请确保你的头戴显示 snugly (向下移动它，或向左和向右移动，以调整) 。</span><span class="sxs-lookup"><span data-stu-id="fec50-130">Make sure your headset fits snugly (move it lower and higher, or left and right, to adjust).</span></span>
* <span data-ttu-id="fec50-131">**> 混合现实 > 耳机显示** ，在 "设置" 中调整耳机的视觉设置。</span><span class="sxs-lookup"><span data-stu-id="fec50-131">Adjust your headset's visual settings in **Settings > Mixed reality > Headset display** .</span></span> <span data-ttu-id="fec50-132">如果 "视觉质量" 设置为 "自动"，则会自动选择电脑的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="fec50-132">When "Visual quality" is set to "Automatic", the mixed reality experience for your PC will be chosen automatically.</span></span> <span data-ttu-id="fec50-133">有关更多视觉对象的详细信息，请将 "视觉质量" 设置为 "高"。</span><span class="sxs-lookup"><span data-stu-id="fec50-133">For more visual detail, set "Visual quality" to "High".</span></span> <span data-ttu-id="fec50-134">如果视觉对象不连贯，请选择较低的设置。</span><span class="sxs-lookup"><span data-stu-id="fec50-134">If your visuals are choppy, select a lower setting.</span></span>
* <span data-ttu-id="fec50-135">调整耳机校准旋钮，确保重用功能区设置为瞳孔 (（称为 IPD) 之间的正确距离。</span><span class="sxs-lookup"><span data-stu-id="fec50-135">Adjust the headset calibration knob to make sure that the lenses are set to the correct distance between your pupils (called IPD).</span></span> <span data-ttu-id="fec50-136">如果你不知道 IPD，optometrist 应能够为你测量，或者使用旨在度量 IPD 的网站。</span><span class="sxs-lookup"><span data-stu-id="fec50-136">If you don't know your IPD, an optometrist should be able to measure it for you, or use a website designed to measure IPD.</span></span> <span data-ttu-id="fec50-137">如果耳机没有校准旋钮，请选择 " **设置" > 混合现实 > 耳机显示** 并调整 "校准控制"。</span><span class="sxs-lookup"><span data-stu-id="fec50-137">If the headset doesn't have a calibration knob, select **Settings > Mixed reality > Headset display** and adjust the "Calibration control".</span></span>
* <span data-ttu-id="fec50-138">如果使用的是 DisplayPort 或到 HDMI 适配器，请尝试其他适配器。</span><span class="sxs-lookup"><span data-stu-id="fec50-138">If you’re using a USB-C or DisplayPort to HDMI adapter, try a different one.</span></span> <span data-ttu-id="fec50-139">请参阅 [建议的适配器。](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)</span><span class="sxs-lookup"><span data-stu-id="fec50-139">See [recommended adapters.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)</span></span>
* <span data-ttu-id="fec50-140">断开可能连接到您的 PC 图形卡的任何其他显示器。</span><span class="sxs-lookup"><span data-stu-id="fec50-140">Disconnect any extra monitors that may be connected to your PC’s graphics card.</span></span>
* <span data-ttu-id="fec50-141">尝试使用 Windows 应用商店中的一些不同的混合现实应用程序，某些应用程序可能更适合您的计算机设置。</span><span class="sxs-lookup"><span data-stu-id="fec50-141">Try some different mixed reality apps from the Windows Store — some may work better with your computer setup.</span></span>
