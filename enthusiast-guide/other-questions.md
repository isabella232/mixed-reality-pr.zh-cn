---
title: 其他问题
description: 其他 Windows Mixed Reality 疑难解答技巧超出了标准使用者支持文档。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，卸载 Windows Mixed Reality，支持的语言
appliesto:
- Windows 10
ms.openlocfilehash: a49008cb7d6a51385cb0d4ece7dfae3018aefe88
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131861"
---
# <a name="other-questions"></a><span data-ttu-id="5d96b-104">其他问题</span><span class="sxs-lookup"><span data-stu-id="5d96b-104">Other questions</span></span>

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a><span data-ttu-id="5d96b-105">我的图形驱动程序不受支持 (我) 出现图形驱动程序故障错误。</span><span class="sxs-lookup"><span data-stu-id="5d96b-105">My graphics driver isn't supported (I'm getting graphics driver failure errors).</span></span>

<span data-ttu-id="5d96b-106">搜索并运行 "dxdiag"：</span><span class="sxs-lookup"><span data-stu-id="5d96b-106">Search for and run "dxdiag":</span></span>

1.  <span data-ttu-id="5d96b-107">如果结果为 "基本呈现器"，则不安装图形驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5d96b-107">If the result is “Basic Renderer”, the graphics driver is not installed.</span></span> <span data-ttu-id="5d96b-108">解决方法：</span><span class="sxs-lookup"><span data-stu-id="5d96b-108">To fix this:</span></span>
    * <span data-ttu-id="5d96b-109">请参阅 **设备管理器 > 操作 > 扫描硬件更改** 。</span><span class="sxs-lookup"><span data-stu-id="5d96b-109">Go to **Device Manager > Action > Scan for Hardware Changes** .</span></span>
    * <span data-ttu-id="5d96b-110">使用 Windows 更新更新驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5d96b-110">Use Windows Update to update the driver.</span></span>
    * <span data-ttu-id="5d96b-111">如果这不能解决问题，请前往制造商的网站并安装最新的驱动程序更新。</span><span class="sxs-lookup"><span data-stu-id="5d96b-111">If this doesn't fix the problem, go to the manufacturer’s website and install the latest driver update.</span></span> 
    * <span data-ttu-id="5d96b-112">如果更新不适用于 GPU，则设备上可能不支持 WMR。</span><span class="sxs-lookup"><span data-stu-id="5d96b-112">If an update isn't available for your GPU, WMR may not be supported on your device.</span></span> <span data-ttu-id="5d96b-113">如果你认为它应为，请联系 [支持人员](https://support.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="5d96b-113">If you think it should be, contact [support](https://support.microsoft.com).</span></span>
2.  <span data-ttu-id="5d96b-114">如果收到 "WDDM 2.1" 或更低版本，则会安装图形驱动程序，但它可能不是最新版本。</span><span class="sxs-lookup"><span data-stu-id="5d96b-114">If you get a “WDDM 2.1” or lower version, the graphics driver is installed but it might not be the latest version.</span></span> <span data-ttu-id="5d96b-115">获取最新版本：</span><span class="sxs-lookup"><span data-stu-id="5d96b-115">To get the latest version:</span></span>
    * <span data-ttu-id="5d96b-116">使用 Windows 更新更新驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5d96b-116">Use Windows Update to update the driver.</span></span>
    * <span data-ttu-id="5d96b-117">如果该更新未解决此问题，请前往制造商的网站并安装最新的驱动程序更新。</span><span class="sxs-lookup"><span data-stu-id="5d96b-117">If that update doesn't fix the problem, go to the manufacturer’s website and install the latest driver update.</span></span> 
    * <span data-ttu-id="5d96b-118">如果更新不适用于 GPU，则设备上可能不支持 WMR。</span><span class="sxs-lookup"><span data-stu-id="5d96b-118">If an update isn't available for your GPU, WMR may not be supported on your device.</span></span> <span data-ttu-id="5d96b-119">如果你认为它应为，请联系 [支持人员](https://support.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="5d96b-119">If you think it should be, contact [support](https://support.microsoft.com).</span></span>

<span data-ttu-id="5d96b-120">如果 Windows Mixed Reality 安装程序显示您的图形卡无法满足要求，而您认为图形卡有问题，请确保将您的耳机插入正确的卡。</span><span class="sxs-lookup"><span data-stu-id="5d96b-120">If Windows Mixed Reality setup says your graphics card doesn’t meet the requirements and you think it does, make sure your headset is plugged into the correct card.</span></span>

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a><span data-ttu-id="5d96b-121">我的 Samsung 太空或太空 + 耳机固件更新停滞。</span><span class="sxs-lookup"><span data-stu-id="5d96b-121">My Samsung Odyssey or Odyssey+ headset firmware update is stuck.</span></span>

<span data-ttu-id="5d96b-122">Samsung 拥有并发布通过其 "Samsung HMD 太空安装程序" 和 "Samsung HMD 太空 + Setup" 设备配套应用交付的耳机固件更新。</span><span class="sxs-lookup"><span data-stu-id="5d96b-122">Samsung owns and publishes headset firmware updates delivered via their "Samsung HMD Odyssey Setup" and "Samsung HMD Odyssey+ Setup" device companion apps.</span></span> <span data-ttu-id="5d96b-123">若要获得更多详细信息并了解 Samsung 固件更新问题，请联系 Samsung 客户服务。</span><span class="sxs-lookup"><span data-stu-id="5d96b-123">For more details and for help with Samsung firmware update issues, please reach out to Samsung customer service.</span></span>

<span data-ttu-id="5d96b-124">如果固件更新过程停滞，而且没有进展超过五分钟：</span><span class="sxs-lookup"><span data-stu-id="5d96b-124">If the firmware update process is getting stuck, and there has been no progress for more than five minutes:</span></span>

* <span data-ttu-id="5d96b-125">暂时拔出所有其他 USB 设备，然后重试固件更新。</span><span class="sxs-lookup"><span data-stu-id="5d96b-125">Unplug all of your other USB devices temporarily and retry the firmware update.</span></span>
* <span data-ttu-id="5d96b-126">将 Samsung 耳机连接到电脑上的其他 USB 3.0 端口。</span><span class="sxs-lookup"><span data-stu-id="5d96b-126">Connect your Samsung headset to a different USB 3.0 port on your PC.</span></span>
* <span data-ttu-id="5d96b-127">禁用和/或卸载任何可能会干扰固件更新的软件，例如千兆 AORUS App Center。</span><span class="sxs-lookup"><span data-stu-id="5d96b-127">Disable and/or uninstall any software installed that may interfere with firmware updates, like Gigabyte's AORUS App Center.</span></span>
* <span data-ttu-id="5d96b-128">使用其他 PC 来执行 Samsung 耳机固件更新。</span><span class="sxs-lookup"><span data-stu-id="5d96b-128">Use a different PC to perform the Samsung headset firmware update.</span></span>

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a><span data-ttu-id="5d96b-129">如何实现在混合现实中访问我的 PC 桌面？</span><span class="sxs-lookup"><span data-stu-id="5d96b-129">How do I access my PC desktop in mixed reality?</span></span>
<span data-ttu-id="5d96b-130">通过 Windows 中的 "耳机" 按钮启动桌面应用， **> 所有应用 > 桌面** 在混合现实中访问电脑桌面。</span><span class="sxs-lookup"><span data-stu-id="5d96b-130">Launch the Desktop app in the headset from **Windows Button > All apps > Desktop** to access your PC desktop in mixed reality.</span></span>

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a><span data-ttu-id="5d96b-131">如何在混合现实中查看多个监视器</span><span class="sxs-lookup"><span data-stu-id="5d96b-131">How can I see multiple monitors in Mixed Reality</span></span>

<span data-ttu-id="5d96b-132">默认情况下，桌面应用会自动切换为显示具有焦点的监视器。</span><span class="sxs-lookup"><span data-stu-id="5d96b-132">By default, Desktop app automatically switches to display the monitor with focus.</span></span> <span data-ttu-id="5d96b-133">如果要在混合现实中查看所有监视器：</span><span class="sxs-lookup"><span data-stu-id="5d96b-133">If you want to see all of your monitors in mixed reality:</span></span>

* <span data-ttu-id="5d96b-134">单击应用左上角的 "监视" 图标。</span><span class="sxs-lookup"><span data-stu-id="5d96b-134">Click the monitor icon on the top left corner of the app.</span></span>
* <span data-ttu-id="5d96b-135">禁用 "自动切换监视器"。</span><span class="sxs-lookup"><span data-stu-id="5d96b-135">Disable "Automatically Switch Monitor".</span></span>
* <span data-ttu-id="5d96b-136">选择要查看的监视器。</span><span class="sxs-lookup"><span data-stu-id="5d96b-136">Pick the monitor you want to see.</span></span>
* <span data-ttu-id="5d96b-137">启动桌面应用程序的另一个实例。</span><span class="sxs-lookup"><span data-stu-id="5d96b-137">Launch another instance of the Desktop app.</span></span>
* <span data-ttu-id="5d96b-138">选择要在该实例上查看的监视器。</span><span class="sxs-lookup"><span data-stu-id="5d96b-138">Pick the monitor you want to see on that instance.</span></span>
* <span data-ttu-id="5d96b-139">对于所有物理监视器重复此操作。</span><span class="sxs-lookup"><span data-stu-id="5d96b-139">Repeat for all of your physical monitors.</span></span>
<span data-ttu-id="5d96b-140">请注意，每次重新启动混合现实时，都必须重新选择要在每个桌面应用上显示的监视器。</span><span class="sxs-lookup"><span data-stu-id="5d96b-140">Note that you will have to reselect the monitor to show on each Desktop app every time you restart mixed reality.</span></span>

## <a name="my-desktop-app-only-shows-a-black-screen"></a><span data-ttu-id="5d96b-141">我的桌面应用程序只显示黑屏</span><span class="sxs-lookup"><span data-stu-id="5d96b-141">My Desktop app only shows a black screen</span></span>

<span data-ttu-id="5d96b-142">如果你的电脑具有 Nvidia 混合 GPU，则问题可能是由于 Nvidia 设备在离散 GPU 而不是集成的 GPU 上运行 runtimebroker.exe。</span><span class="sxs-lookup"><span data-stu-id="5d96b-142">If your PC has an Nvidia hybrid GPU, the issue may be caused by Nvidia device running the runtimebroker.exe on the discrete GPU instead of the integrated one.</span></span> <span data-ttu-id="5d96b-143">若要解决此问题，请按照 "[如何实现创建新程序的 Optimus 设置](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)" 下的说明操作。</span><span class="sxs-lookup"><span data-stu-id="5d96b-143">To fix this issue, follow these instructions under "[How do I create Optimus settings for a new program?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)"</span></span> <span data-ttu-id="5d96b-144">添加 C:\windows\system32\runtimebroker.exe，并强制其在 "集成图形" 处理器上运行。</span><span class="sxs-lookup"><span data-stu-id="5d96b-144">to add C:\windows\system32\runtimebroker.exe and force it to run on the "Integrated graphics" processor.</span></span> 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a><span data-ttu-id="5d96b-145">使用 Windows Mixed Reality 时，Wi-Fi 会减慢。</span><span class="sxs-lookup"><span data-stu-id="5d96b-145">My Wi-Fi slows down when I'm using Windows Mixed Reality.</span></span>

<span data-ttu-id="5d96b-146">如果使用 2.4 GHz Wi-Fi 连接，则运动控制器可能会减慢 Wi-fi 的速度。</span><span class="sxs-lookup"><span data-stu-id="5d96b-146">If you're using a 2.4GHz Wi-Fi connection, your motion controllers might slow down your Wi-Fi.</span></span> <span data-ttu-id="5d96b-147">尝试以下任一项：</span><span class="sxs-lookup"><span data-stu-id="5d96b-147">Try one of the following:</span></span>

* <span data-ttu-id="5d96b-148">切换到 5GHz Wi-Fi 连接（如果有）。</span><span class="sxs-lookup"><span data-stu-id="5d96b-148">Switch to a 5GHz Wi-Fi connection, if one is available.</span></span> <span data-ttu-id="5d96b-149">[了解详细信息](https://support.microsoft.com/help/4000461)。</span><span class="sxs-lookup"><span data-stu-id="5d96b-149">[Learn more](https://support.microsoft.com/help/4000461).</span></span>
* <span data-ttu-id="5d96b-150">使用单独的蓝牙适配器将运动控制器连接到您的 PC。</span><span class="sxs-lookup"><span data-stu-id="5d96b-150">Use a separate Bluetooth adapter to connect your motion controllers to your PC.</span></span> <span data-ttu-id="5d96b-151">请参阅 [建议的适配器](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)。</span><span class="sxs-lookup"><span data-stu-id="5d96b-151">See [recommended adapters](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).</span></span>

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a><span data-ttu-id="5d96b-152">我收到一条消息，指出我的 PC 已接通电源并向其收费。</span><span class="sxs-lookup"><span data-stu-id="5d96b-152">I got a message that said to plug in and charge my PC.</span></span> <span data-ttu-id="5d96b-153">为什么？</span><span class="sxs-lookup"><span data-stu-id="5d96b-153">Why?</span></span>

<span data-ttu-id="5d96b-154">如果使用便携式计算机，则当电脑完全充电并接通电源时，Windows Mixed Reality 的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="5d96b-154">If you're using a laptop, Windows Mixed Reality works best when the PC is both fully charged and plugged in.</span></span>

## <a name="what-is-the-experience-options-setting"></a><span data-ttu-id="5d96b-155">什么是体验选项设置？</span><span class="sxs-lookup"><span data-stu-id="5d96b-155">What is the Experience options setting?</span></span>

<span data-ttu-id="5d96b-156">此设置 ( **设置 > 混合现实 > 耳机显示 > 体验选项** ，) 允许你更改 Windows Mixed reality 性能设置。</span><span class="sxs-lookup"><span data-stu-id="5d96b-156">This setting ( **Settings > Mixed reality > Headset display > Experience options** ) allows you to change the Windows Mixed Reality performance settings.</span></span> <span data-ttu-id="5d96b-157">这样，你就可以为各种内容的硬件配置选择最佳体验。</span><span class="sxs-lookup"><span data-stu-id="5d96b-157">This enables you to choose the best experience for your hardware configuration across a range of content.</span></span> <span data-ttu-id="5d96b-158">以下是选项：</span><span class="sxs-lookup"><span data-stu-id="5d96b-158">These are the options:</span></span>
* <span data-ttu-id="5d96b-159">自动： Windows Mixed Reality 将确定硬件配置的最佳体验。</span><span class="sxs-lookup"><span data-stu-id="5d96b-159">Automatic: Windows Mixed Reality will determine the best experience for your hardware configuration.</span></span> <span data-ttu-id="5d96b-160">对于大多数人来说，这是开始的最佳选择。</span><span class="sxs-lookup"><span data-stu-id="5d96b-160">For most people, this is the best choice to start with.</span></span>
* <span data-ttu-id="5d96b-161">60Hz：将刷新率设置为60Hz，并关闭某些功能，如混合现实门户中的视频捕获和预览。</span><span class="sxs-lookup"><span data-stu-id="5d96b-161">60Hz: Sets the refresh rate to 60Hz and turns off certain features, such as video capture and preview in Mixed Reality Portal.</span></span>
* <span data-ttu-id="5d96b-162">90Hz：将刷新率设置为90Hz。</span><span class="sxs-lookup"><span data-stu-id="5d96b-162">90Hz: Sets the refresh rate to 90Hz.</span></span>

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a><span data-ttu-id="5d96b-163">Windows Mixed Reality 支持的语言</span><span class="sxs-lookup"><span data-stu-id="5d96b-163">What languages are supported in Windows Mixed Reality</span></span>

<span data-ttu-id="5d96b-164">Windows Mixed Reality 提供以下语言版本：</span><span class="sxs-lookup"><span data-stu-id="5d96b-164">Windows Mixed Reality is available in the following languages:</span></span>

* <span data-ttu-id="5d96b-165">简体中文（中国）</span><span class="sxs-lookup"><span data-stu-id="5d96b-165">Chinese Simplified (China)</span></span>
* <span data-ttu-id="5d96b-166">英语（澳大利亚）</span><span class="sxs-lookup"><span data-stu-id="5d96b-166">English (Australia)</span></span>
* <span data-ttu-id="5d96b-167">英语（加拿大）</span><span class="sxs-lookup"><span data-stu-id="5d96b-167">English (Canada)</span></span>
* <span data-ttu-id="5d96b-168">英语（英国）</span><span class="sxs-lookup"><span data-stu-id="5d96b-168">English (Great Britain)</span></span>
* <span data-ttu-id="5d96b-169">英语（美国）</span><span class="sxs-lookup"><span data-stu-id="5d96b-169">English (United States)</span></span>
* <span data-ttu-id="5d96b-170">法语（加拿大）</span><span class="sxs-lookup"><span data-stu-id="5d96b-170">French (Canada)</span></span>
* <span data-ttu-id="5d96b-171">法语（法国）</span><span class="sxs-lookup"><span data-stu-id="5d96b-171">French (France)</span></span>
* <span data-ttu-id="5d96b-172">德语（德国）</span><span class="sxs-lookup"><span data-stu-id="5d96b-172">German (Germany)</span></span>
* <span data-ttu-id="5d96b-173">意大利语（意大利）</span><span class="sxs-lookup"><span data-stu-id="5d96b-173">Italian (Italy)</span></span>
* <span data-ttu-id="5d96b-174">日语（日本）</span><span class="sxs-lookup"><span data-stu-id="5d96b-174">Japanese (Japan)</span></span>
* <span data-ttu-id="5d96b-175">西班牙语(墨西哥)</span><span class="sxs-lookup"><span data-stu-id="5d96b-175">Spanish (Mexico)</span></span>
* <span data-ttu-id="5d96b-176">西班牙语(西班牙)</span><span class="sxs-lookup"><span data-stu-id="5d96b-176">Spanish (Spain)</span></span>

<span data-ttu-id="5d96b-177">如果你的电脑设置为另一种语言，则可以使用 Windows Mixed Reality，但界面将显示为英语 (美国) ，并且语音命令和听写将不可用。</span><span class="sxs-lookup"><span data-stu-id="5d96b-177">You can use Windows Mixed Reality if your PC is set to a different language, but the interface will appear in English (United States), and speech commands and dictation won't be available.</span></span> <span data-ttu-id="5d96b-178">Windows Mixed Reality 屏幕键盘仅适用于英语 (美国) 。</span><span class="sxs-lookup"><span data-stu-id="5d96b-178">The Windows Mixed Reality onscreen keyboard is English (United States) only.</span></span> <span data-ttu-id="5d96b-179">若要以另一种语言输入文本，请使用连接到电脑的物理键盘。</span><span class="sxs-lookup"><span data-stu-id="5d96b-179">To enter text in another language, use a physical keyboard connected to your PC.</span></span> <span data-ttu-id="5d96b-180">你还可以使用上面列出的受支持的 Windows Mixed Reality 语言之一来使用听写，只需在屏幕键盘上选择 "麦克风" 即可。</span><span class="sxs-lookup"><span data-stu-id="5d96b-180">You can also use dictation in one of the supported Windows Mixed Reality languages listed above—just select microphone on the onscreen keyboard.</span></span>

<span data-ttu-id="5d96b-181">Windows Mixed Reality 还提供以下语言版本，无需语音命令或听写功能：</span><span class="sxs-lookup"><span data-stu-id="5d96b-181">Windows Mixed Reality is also available in the following languages without speech commands or dictation features:</span></span>
* <span data-ttu-id="5d96b-182">繁体中文 (台湾和中国香港) </span><span class="sxs-lookup"><span data-stu-id="5d96b-182">Chinese Traditional (Taiwan and Hong Kong)</span></span>
* <span data-ttu-id="5d96b-183">荷兰语（荷兰）</span><span class="sxs-lookup"><span data-stu-id="5d96b-183">Dutch (Netherlands)</span></span>
* <span data-ttu-id="5d96b-184">韩语(韩国)</span><span class="sxs-lookup"><span data-stu-id="5d96b-184">Korean (Korea)</span></span>
* <span data-ttu-id="5d96b-185">俄语（俄罗斯）</span><span class="sxs-lookup"><span data-stu-id="5d96b-185">Russian (Russia)</span></span>

## <a name="i-have-questions-about-my-headset-hardware"></a><span data-ttu-id="5d96b-186">我对我的耳机硬件有疑问。</span><span class="sxs-lookup"><span data-stu-id="5d96b-186">I have questions about my headset hardware.</span></span>

<span data-ttu-id="5d96b-187">有关手机支持的详细信息，请咨询制造商。</span><span class="sxs-lookup"><span data-stu-id="5d96b-187">For details about your headset, check with the manufacturer.</span></span> <span data-ttu-id="5d96b-188">可以在框中提供产品指南，也可以尝试使用制造商的网站。</span><span class="sxs-lookup"><span data-stu-id="5d96b-188">There may be a product guide in the box, or you can try the manufacturer’s website.</span></span>

## <a name="how-do-i-uninstall-windows-mixed-reality"></a><span data-ttu-id="5d96b-189">如何实现卸载 Windows Mixed Reality？</span><span class="sxs-lookup"><span data-stu-id="5d96b-189">How do I uninstall Windows Mixed Reality?</span></span>

1. <span data-ttu-id="5d96b-190">断开耳机与电脑的连接。</span><span class="sxs-lookup"><span data-stu-id="5d96b-190">Disconnect your headset from your PC.</span></span>
2. <span data-ttu-id="5d96b-191">关闭 Windows Mixed Reality 门户。</span><span class="sxs-lookup"><span data-stu-id="5d96b-191">Close Windows Mixed Reality Portal.</span></span>
2. <span data-ttu-id="5d96b-192">请参阅  **开始 > 设置 > Mixed Reality** ，然后选择 "卸载"。</span><span class="sxs-lookup"><span data-stu-id="5d96b-192">Go to  **Start > Settings > Mixed Reality** and select "Uninstall".</span></span>

<span data-ttu-id="5d96b-193">如果已准备好开始使用头戴显示，请将其插入，Windows Mixed Reality 门户将引导你完成安装过程。</span><span class="sxs-lookup"><span data-stu-id="5d96b-193">When you're ready to start using your headset again, plug it in, and Windows Mixed Reality Portal will take you through setup.</span></span>

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a><span data-ttu-id="5d96b-194">我收到了 "我们无法完成 Windows Mixed Reality 的卸载" 消息。</span><span class="sxs-lookup"><span data-stu-id="5d96b-194">I got a "We couldn't finish uninstalling Windows Mixed Reality" message.</span></span>

<span data-ttu-id="5d96b-195">某些文件（包括有关您的环境的信息）可能仍在您的计算机上。</span><span class="sxs-lookup"><span data-stu-id="5d96b-195">Some files, including information about your environment, might still be on your computer.</span></span> <span data-ttu-id="5d96b-196">如果你决定稍后重新安装 Windows Mixed Reality，这可能会导致问题。</span><span class="sxs-lookup"><span data-stu-id="5d96b-196">This can cause problems if you decide to reinstall Windows Mixed Reality later.</span></span> <span data-ttu-id="5d96b-197">你可以通过修改注册表并使用 Windows PowerShell 来运行命令，从你的电脑中手动删除任何剩余的 Windows Mixed Reality 信息。</span><span class="sxs-lookup"><span data-stu-id="5d96b-197">You can manually remove any remaining Windows Mixed Reality info from your PC by modifying the registry and using Windows PowerShell to run commands.</span></span> <span data-ttu-id="5d96b-198">_如果不正确地修改注册表，则可能会出现严重问题。请确保仔细执行这些步骤。为了增加保护，请在修改注册表之前对其进行备份，以便在发生问题时可以还原。_</span><span class="sxs-lookup"><span data-stu-id="5d96b-198">_If you modify the registry incorrectly, serious problems might occur. Make sure to follow these steps carefully. For added protection, back up your registry before you modify it so you can restore it if a problem occurrs._</span></span> <span data-ttu-id="5d96b-199">有关详细信息，请参阅 [如何在 Windows 中备份和 restory 注册表](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)。</span><span class="sxs-lookup"><span data-stu-id="5d96b-199">For more information, see [How to back up and restory the registry in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows).</span></span> 

<span data-ttu-id="5d96b-200">使用以下命令卸载 Windows mixed reality：</span><span class="sxs-lookup"><span data-stu-id="5d96b-200">To uninstall Windows mixed reality using these commands:</span></span>
1. <span data-ttu-id="5d96b-201">重启你的电脑。</span><span class="sxs-lookup"><span data-stu-id="5d96b-201">Restart your PC.</span></span>
2. <span data-ttu-id="5d96b-202">在 **搜索** 框中，键入 "regedit"，然后选择 "是"。</span><span class="sxs-lookup"><span data-stu-id="5d96b-202">In the **Search** box, type "regedit" and then select "Yes".</span></span>
3. <span data-ttu-id="5d96b-203">删除以下注册表值：</span><span class="sxs-lookup"><span data-stu-id="5d96b-203">Remove these registry values:</span></span>
   <ul>
    <li><span data-ttu-id="5d96b-204"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>"，然后删除" FirstRunSucceeded "。</span><span class="sxs-lookup"><span data-stu-id="5d96b-204"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, then delete "FirstRunSucceeded".</span></span></li> 
    <li><span data-ttu-id="5d96b-205"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>"，然后删除" PreferDesktopSpeaker "和" PreferDesktopMic "。</span><span class="sxs-lookup"><span data-stu-id="5d96b-205"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, then delete "PreferDesktopSpeaker" and "PreferDesktopMic".</span></span></li> 
    <li><span data-ttu-id="5d96b-206"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>，然后删除 "DisableSpeechInput"。</span><span class="sxs-lookup"><span data-stu-id="5d96b-206"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>, then delete "DisableSpeechInput".</span></span> <span data-ttu-id="5d96b-207">注意：必须在已使用 Windows Mixed Reality 的 PC 上为每个用户帐户删除 HHKEY_CURRENT_USER 中的注册表项。</span><span class="sxs-lookup"><span data-stu-id="5d96b-207">Note: The registry items in HHKEY_CURRENT_USER must be deleted for every user account on the PC that has used Windows Mixed Reality.</span></span></li> 
    <li><span data-ttu-id="5d96b-208"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>"，然后删除" DeviceID "和" Mode "。</span><span class="sxs-lookup"><span data-stu-id="5d96b-208"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, then delete "DeviceID" and "Mode".</span></span></li> 
    <li><span data-ttu-id="5d96b-209"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>"，然后删除" OnDeviceLearningCompleted "。</span><span class="sxs-lookup"><span data-stu-id="5d96b-209"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, then delete "OnDeviceLearningCompleted".</span></span></li> 
   </ul><span data-ttu-id="5d96b-210">
4. 删除以下注册表项：</span><span class="sxs-lookup"><span data-stu-id="5d96b-210">
4. Remove the following registry keys:</span></span> <ul>
   <li> <span data-ttu-id="5d96b-211"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span><span class="sxs-lookup"><span data-stu-id="5d96b-211"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span></span></li> 
   <li> <span data-ttu-id="5d96b-212"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span><span class="sxs-lookup"><span data-stu-id="5d96b-212"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span></span></li> 
   <li> <span data-ttu-id="5d96b-213"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></span><span class="sxs-lookup"><span data-stu-id="5d96b-213"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></span></span></li><br/></ul><span data-ttu-id="5d96b-214">
5. 关闭注册表编辑器。</span><span class="sxs-lookup"><span data-stu-id="5d96b-214">
5. Close the Registry Editor.</span></span>
<span data-ttu-id="5d96b-215">6. 请参阅 **C:\users\ 用户名 name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** 并删除 "RoomBounds.json"。</span><span class="sxs-lookup"><span data-stu-id="5d96b-215">6. Go to **C:\Users\user name\AppData\Local\Packages\Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy\LocalState** and delete "RoomBounds.json".</span></span> <span data-ttu-id="5d96b-216">对已使用 Windows Mixed Reality 的每个用户重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="5d96b-216">Repeat this for each user who has used Windows Mixed Reality.</span></span>
<span data-ttu-id="5d96b-217">7. 打开管理 cmd 提示符并中转到 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** 。</span><span class="sxs-lookup"><span data-stu-id="5d96b-217">7. Open admin cmd prompt and go to **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** .</span></span> <span data-ttu-id="5d96b-218">删除 "HeadTracking data" 文件夹的内容 (但不) 文件夹本身。</span><span class="sxs-lookup"><span data-stu-id="5d96b-218">Delete the contents of the "HeadTracking data" folder (but not the folder itself).</span></span>
<span data-ttu-id="5d96b-219">8. 在 "搜索框" 中键入 "powershell"，右键单击 "Windows PowerShell"，然后选择 "以管理员身份运行"。</span><span class="sxs-lookup"><span data-stu-id="5d96b-219">8. Type "powershell" in the "Search box", right-click "Windows PowerShell", and then select "Run as administrator".</span></span>
<span data-ttu-id="5d96b-220">9. 在 Windows PowerShell 中：</span><span class="sxs-lookup"><span data-stu-id="5d96b-220">9. In Windows PowerShell:</span></span> <ul>
   <li><span data-ttu-id="5d96b-221">在命令提示符处，复制并粘贴 <b>Dism/Online/Get-Capabilities</b>，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="5d96b-221">At the command prompt, copy and paste <b>Dism /online /Get-Capabilities</b>, then press Enter.</span></span></b></li> 
   <li><span data-ttu-id="5d96b-222">复制以 (开头的功能标识（如果不存在），这意味着未安装此项。</span><span class="sxs-lookup"><span data-stu-id="5d96b-222">Copy the Capability Identity that begins with Analog.Holographic.Desktop (if it isn't there, that means this item isn't installed.</span></span> <span data-ttu-id="5d96b-223">在这种情况下，请跳到步骤 10 ) 。</span><span class="sxs-lookup"><span data-stu-id="5d96b-223">In that case, skip to step 10 ).</span></span></li> 
   <li><span data-ttu-id="5d96b-224">复制并粘贴以下命令提示符，然后按 Enter： <b>Dism/Online/Remove-Capability/CapabilityName：在上一步中复制的功能标识</b></span><span class="sxs-lookup"><span data-stu-id="5d96b-224">Copy and paste the following command prompt, then press Enter: <b>Dism /online /Remove-Capability /CapabilityName:the Capability Identity copied in the last step</b></span></span></li>
   </ul><span data-ttu-id="5d96b-225">
10. 重启电脑。</span><span class="sxs-lookup"><span data-stu-id="5d96b-225">
10. Restart your PC.</span></span>

