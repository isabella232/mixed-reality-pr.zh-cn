---
title: 使用 Windows 设备门户
description: 了解如何使用 Windows 设备门户通过 Wi-Fi 或 USB 远程配置和管理设备。
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Windows 设备门户，HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d772175683208ac0e3ed4b3163ca561da416c1cf
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112919808"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="fc36b-104">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="fc36b-104">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="fc36b-105">功能</span><span class="sxs-lookup"><span data-stu-id="fc36b-105">Feature</span></span></th><th style="width:150px"><span data-ttu-id="fc36b-106"><a href="/hololens/hololens1-hardware">HoloLens（第一代）</a></span><span class="sxs-lookup"><span data-stu-id="fc36b-106"><a href="/hololens/hololens1-hardware">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="fc36b-107">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fc36b-107">HoloLens 2</span></span></th><th style="width:150px">
</tr><tr>
<td> <span data-ttu-id="fc36b-108">Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="fc36b-108">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="fc36b-109">✔️</span><span class="sxs-lookup"><span data-stu-id="fc36b-109">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="fc36b-110">✔️</span><span class="sxs-lookup"><span data-stu-id="fc36b-110">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="fc36b-111">使用适用于 HoloLens 的 Windows 设备门户可以通过 Wi-Fi 或 USB 远程配置和管理设备。</span><span class="sxs-lookup"><span data-stu-id="fc36b-111">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="fc36b-112">Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。</span><span class="sxs-lookup"><span data-stu-id="fc36b-112">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="fc36b-113">设备门户包含许多工具，可帮助你管理 HoloLens 以及调试和优化应用。</span><span class="sxs-lookup"><span data-stu-id="fc36b-113">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="fc36b-114">本文档专门介绍适用于 HoloLens 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="fc36b-114">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="fc36b-115">若要使用适用于桌面（包括 Windows Mixed Reality）的 Windows 设备门户，请参阅 [Windows 设备门户概述](/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="fc36b-115">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="fc36b-116">将 HoloLens 设置为使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="fc36b-116">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="fc36b-117">打开 HoloLens 的电源，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="fc36b-117">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="fc36b-118">针对 HoloLens2 使用[开始手势](/hololens/hololens2-basic-usage#start-gesture)，或者在 HoloLens（第 1 代）上使用[开花手势](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)，以启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="fc36b-118">Use the [Start gesture](/hololens/hololens2-basic-usage#start-gesture) for HoloLens2 or [Bloom](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (1st Gen) to launch the main menu.</span></span> 
3. <span data-ttu-id="fc36b-119">凝视“设置”磁贴，在 HoloLens（第 1 代）上，使用[隔空敲击](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)手势。</span><span class="sxs-lookup"><span data-stu-id="fc36b-119">Gaze at the **Settings** tile and do an [air-tap](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) gesture on HoloLens (1st Gen).</span></span> <span data-ttu-id="fc36b-120">在 HoloLens 2 上，还可以通过[触摸或使用手部射线](/hololens/hololens2-basic-usage)选择该磁贴。</span><span class="sxs-lookup"><span data-stu-id="fc36b-120">You can also select it on HoloLens 2 by [touching it or using a Hand ray](/hololens/hololens2-basic-usage).</span></span> 
4. <span data-ttu-id="fc36b-121">选择“更新”菜单项。</span><span class="sxs-lookup"><span data-stu-id="fc36b-121">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="fc36b-122">选择“面向开发人员”  菜单项。</span><span class="sxs-lookup"><span data-stu-id="fc36b-122">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="fc36b-123">启用“开发人员模式”。</span><span class="sxs-lookup"><span data-stu-id="fc36b-123">Enable **Developer Mode**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc36b-124">如果你使用的是多用户而不是管理员，则进入开发人员模式的功能可能灰显。请确保你是[设备上的管理员](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="fc36b-124">If you're in multi-user and not an admin, the ability to enter Developer Mode may be grayed out. Please ensure that you are an **[admin on the device](/hololens/security-adminless-os)**.</span></span>

7. <span data-ttu-id="fc36b-125">[向下滚动](../../design/gaze-and-commit.md#composite-gestures)并启用“设备门户”。</span><span class="sxs-lookup"><span data-stu-id="fc36b-125">[Scroll down](../../design/gaze-and-commit.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="fc36b-126">如果要设置 Windows 设备门户以便可以通过 USB 或 Wi-Fi 将应用部署到此 HoloLens，请选择“配对”以[生成配对 PIN](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="fc36b-126">If you're setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, select **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="fc36b-127">在首次部署期间，请在“PIN”弹出窗口中保持打开“设置”应用，直到在 Visual Studio 中输入了 PIN 才将它关闭。</span><span class="sxs-lookup"><span data-stu-id="fc36b-127">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

![在 Windows Holographic 的“设置”应用中启用开发人员模式](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="fc36b-129">通过 Wi-Fi 进行连接</span><span class="sxs-lookup"><span data-stu-id="fc36b-129">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="fc36b-130">[将 HoloLens 连接到 Wi-Fi](/hololens/hololens-network)。</span><span class="sxs-lookup"><span data-stu-id="fc36b-130">[Connect your HoloLens to Wi-Fi](/hololens/hololens-network).</span></span>
2. <span data-ttu-id="fc36b-131">通过以下任一方法查找设备的 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="fc36b-131">Look up your device's IP address by either:</span></span>
  * <span data-ttu-id="fc36b-132">依次转到“设置”>“网络和 Internet”>“Wi-Fi”>“高级选项”。</span><span class="sxs-lookup"><span data-stu-id="fc36b-132">Going to **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
  * <span data-ttu-id="fc36b-133">转到“设置”>“网络和 Internet”，然后选择“硬件属性” 。</span><span class="sxs-lookup"><span data-stu-id="fc36b-133">Going to **Settings > Network & Internet** and selecting **Hardware properties**.</span></span>
  * <span data-ttu-id="fc36b-134">使用“我的 IP 地址是什么？”</span><span class="sxs-lookup"><span data-stu-id="fc36b-134">Using the "What's my IP address?"</span></span> <span data-ttu-id="fc36b-135">语音命令。</span><span class="sxs-lookup"><span data-stu-id="fc36b-135">voice command.</span></span>

![HoloLens 2 设置](images/using-windows-portal-img-02.jpg)

3. <span data-ttu-id="fc36b-137">在电脑上的 Web 浏览器中，转到 https://<HOLOLENS IP 地址></span><span class="sxs-lookup"><span data-stu-id="fc36b-137">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="fc36b-138">浏览器中将显示以下消息：“此网站的安全证书有问题”，因为颁发给设备门户的证书是测试证书。</span><span class="sxs-lookup"><span data-stu-id="fc36b-138">The browser will display the following message: "There's a problem with this website's security certificate" because the certificate, which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="fc36b-139">你可以暂时忽略此证书错误并继续。</span><span class="sxs-lookup"><span data-stu-id="fc36b-139">You can ignore this certificate error for now and continue.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="fc36b-140">通过 USB 进行连接</span><span class="sxs-lookup"><span data-stu-id="fc36b-140">Connecting over USB</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc36b-141">根据新的浏览器标准，不再建议使用 IpOverUsb，因为它需要使用端口 10080。</span><span class="sxs-lookup"><span data-stu-id="fc36b-141">IpOverUsb is no longer recommended per new browser standards as it requires the use of port 10080.</span></span> <span data-ttu-id="fc36b-142">如果仍希望使用 IpOverUsb，请在 Visual Studio 安装期间选中“USB 设备连接”框，默认情况下不会选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="fc36b-142">If you still wish to use IpOverUsb, check the 'USB Device Connectivity' box during Visual Studio installation, which isn't checked by default.</span></span> <span data-ttu-id="fc36b-143">相反，我们建议使用 UsbNcm 进行连接，默认情况下，HoloLens 2 支持这个连接选项。</span><span class="sxs-lookup"><span data-stu-id="fc36b-143">Instead, we recommend connecting with UsbNcm, which is supported by default on HoloLens 2.</span></span> <span data-ttu-id="fc36b-144">如果您使用 HoloLens 1，建议使用 WiFi 连接到电脑。</span><span class="sxs-lookup"><span data-stu-id="fc36b-144">If you are using a HoloLens 1, we recommend connecting to your PC using WiFi.</span></span>

1. <span data-ttu-id="fc36b-145">如果 HoloLens 2 运行的是 Windows Holographic 版本 21H1 或更高版本，请转到“设置”应用中的“适用于开发人员”，并确保“设备发现”已打开。</span><span class="sxs-lookup"><span data-stu-id="fc36b-145">If your HoloLens 2 is running Windows Holographic version 21H1 or higher, go to 'For developers' in the Settings app and make sure that 'Device discovery' is toggled ON.</span></span> 
2. <span data-ttu-id="fc36b-146">使用 USB-C 线缆将 HoloLens 2 连接到电脑。</span><span class="sxs-lookup"><span data-stu-id="fc36b-146">Connect your HoloLens 2 to your PC with a USB-C cable.</span></span>
3. <span data-ttu-id="fc36b-147">查找 UsbNcm IP。</span><span class="sxs-lookup"><span data-stu-id="fc36b-147">Find your UsbNcm IP.</span></span> <span data-ttu-id="fc36b-148">可通过多种方式进行查找：</span><span class="sxs-lookup"><span data-stu-id="fc36b-148">There are a few ways to do this:</span></span>
  * <span data-ttu-id="fc36b-149">在设备上的“设置”应用中（此方法仅适用于运行 Windows Holographic 版本 21H1 或更高版本的 HoloLenses，并且打开了“设备发现”）。</span><span class="sxs-lookup"><span data-stu-id="fc36b-149">In the Settings app on the device (This method only works for HoloLenses running Windows Holographic version 21H1 or higher, with 'Device discovery' toggled ON.)</span></span>
    1. <span data-ttu-id="fc36b-150">转到设备上的“设置”应用。</span><span class="sxs-lookup"><span data-stu-id="fc36b-150">Go into the Settings app on the device.</span></span>
    2. <span data-ttu-id="fc36b-151">前往“更新和安全”>“适用于开发人员”。</span><span class="sxs-lookup"><span data-stu-id="fc36b-151">Go to "Update & Security" > "For developers."</span></span> <span data-ttu-id="fc36b-152">这里也可以启用设备门户。</span><span class="sxs-lookup"><span data-stu-id="fc36b-152">This is the same place you enabled Device Portal.</span></span>
    3. <span data-ttu-id="fc36b-153">在页面底部，复制“以太网”IP 地址。</span><span class="sxs-lookup"><span data-stu-id="fc36b-153">At the bottom of the page, copy your **Ethernet** IP address.</span></span> <span data-ttu-id="fc36b-154">这是 UsbNcm IP。</span><span class="sxs-lookup"><span data-stu-id="fc36b-154">This is your UsbNcm IP.</span></span> 
    <span data-ttu-id="fc36b-155">![HoloLens 2 设置 - UsbNcm IP](images/deviceportal_usbncm_ipaddress.jpg)</span><span class="sxs-lookup"><span data-stu-id="fc36b-155">![HoloLens 2 settings - UsbNcm IP](images/deviceportal_usbncm_ipaddress.jpg)</span></span>

  * <span data-ttu-id="fc36b-156">在设备门户中</span><span class="sxs-lookup"><span data-stu-id="fc36b-156">In Device Portal</span></span> 
    1. <span data-ttu-id="fc36b-157">在设备上，使用 HoloLens 的 WiFi 地址打开设备门户。</span><span class="sxs-lookup"><span data-stu-id="fc36b-157">On your device, open Device Portal using your HoloLens' WiFi address.</span></span> <span data-ttu-id="fc36b-158">如果您不知道 HoloLens WiFi 地址，可以使用语音命令“我的 IP 地址是什么？”</span><span class="sxs-lookup"><span data-stu-id="fc36b-158">If you don't know your HoloLens' WiFi address, you can use the voice command "What's my IP address?"</span></span>
    2. <span data-ttu-id="fc36b-159">前往“设置”>“网络”</span><span class="sxs-lookup"><span data-stu-id="fc36b-159">Go to System > Networking</span></span>
    3. <span data-ttu-id="fc36b-160">在页面最右侧“IP 配置”面板中，找到以“说明：UsbNcm 功能”开头的部分。</span><span class="sxs-lookup"><span data-stu-id="fc36b-160">On the far right side of the page in the "IP Configuration" panel, locate the section that starts with "Description: UsbNcm Function."</span></span>
    4. <span data-ttu-id="fc36b-161">UsbNcm IP 位于“IPv4 地址”行中。</span><span class="sxs-lookup"><span data-stu-id="fc36b-161">Your UsbNcm IP is the "IPv4 address" line.</span></span> <span data-ttu-id="fc36b-162">可以复制地址或单击该地址 - 这是一个超链接，它将使用 UsbNcm IP 重新打开设备门户。</span><span class="sxs-lookup"><span data-stu-id="fc36b-162">You can copy the address or just click on the address - it is a hyperlink which will reopen Device Portal using the UsbNcm IP.</span></span>
  
  * <span data-ttu-id="fc36b-163">在命令提示符中</span><span class="sxs-lookup"><span data-stu-id="fc36b-163">In a command prompt</span></span>
    1. <span data-ttu-id="fc36b-164">在任何命令提示符中，导航到安装了 Windows 10 SDK 的 bin\<SDK version>\x86 文件夹，如 C:\Program Files (x86)\Windows Kits\10\bin\10.0.19041.0\x86。</span><span class="sxs-lookup"><span data-stu-id="fc36b-164">In any command prompt, navigate to the bin\<SDK version>\x86 folder where your Windows 10 SDK is installed, such as C:\Program Files (x86)\Windows Kits\10\bin\10.0.19041.0\x86.</span></span>
    2. <span data-ttu-id="fc36b-165">键入“winappdeploycmd devices”并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="fc36b-165">Type "winappdeploycmd devices" and press Enter.</span></span>
    3. <span data-ttu-id="fc36b-166">在输出中，查找“模型/名称”列显示 HoloLens 设备名称的条目，例如 HOLOLENS-xxxxxx。</span><span class="sxs-lookup"><span data-stu-id="fc36b-166">In the output, look for the entry where the Model/Name column is your HoloLens device name, such as HOLOLENS-xxxxxx.</span></span> <span data-ttu-id="fc36b-167">UsbNcm IP 位于此行的开头，显示为 169.254.x.x 格式的自动私有 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="fc36b-167">The UsbNcm IP is at the start of this line and will be an Automatic Private IP address in the form of 169.254.x.x.</span></span> <span data-ttu-id="fc36b-168">复制此地址。</span><span class="sxs-lookup"><span data-stu-id="fc36b-168">Copy this address.</span></span> 
 
4. <span data-ttu-id="fc36b-169">如果您复制了 UsbNcm IP，请使用电脑上的 Web 浏览器转到 https:// 后跟 UsbNcm IP。</span><span class="sxs-lookup"><span data-stu-id="fc36b-169">If you copied your UsbNcm IP, from a web browser on your PC go to https:// followed by your UsbNcm IP.</span></span>

### <a name="moving-files-over-usb"></a><span data-ttu-id="fc36b-170">通过 USB 移动文件</span><span class="sxs-lookup"><span data-stu-id="fc36b-170">Moving files over USB</span></span>

<span data-ttu-id="fc36b-171">无需进行任何其他设置，即可将文件从电脑移动到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fc36b-171">You can move files from your PC to your HoloLens without any additional setup.</span></span>
1. <span data-ttu-id="fc36b-172">使用 USB 线将电脑连接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="fc36b-172">Connect your PC to your HoloLens with a USB cord</span></span>
2. <span data-ttu-id="fc36b-173">将文件拖动到桌面上的“PC\\[Your_HoloLens_Device_Name]\Internal Storage”中</span><span class="sxs-lookup"><span data-stu-id="fc36b-173">Drag your files into **PC\\[Your_HoloLens_Device_Name]\Internal Storage** on your desktop</span></span>
3. <span data-ttu-id="fc36b-174">打开“开始”菜单，然后在 HoloLens 上选择“所有应用”>“文件资源管理器” </span><span class="sxs-lookup"><span data-stu-id="fc36b-174">Open the **Start Menu** and select **All apps > File Explorer** on your HoloLens</span></span>

> [!NOTE]
> <span data-ttu-id="fc36b-175">可能需要选择面板左侧的“此设备”，才能从“最近使用”进行导航以查找文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-175">You may need to select **This device** on the left side of the panel to navigate away from "Recently used" to locate your files.</span></span> 

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="fc36b-176">连接到仿真器</span><span class="sxs-lookup"><span data-stu-id="fc36b-176">Connecting to an emulator</span></span>

<span data-ttu-id="fc36b-177">也可以将 Device Portal 与仿真器结合使用。</span><span class="sxs-lookup"><span data-stu-id="fc36b-177">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="fc36b-178">若要连接到设备门户，请使用[工具栏](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="fc36b-178">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="fc36b-179">选择此图标：![“打开设备门户”图标](images/emulator-deviceportal.png) **打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="fc36b-179">Select this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="fc36b-180">创建用户名和密码</span><span class="sxs-lookup"><span data-stu-id="fc36b-180">Creating a Username and Password</span></span>

<span data-ttu-id="fc36b-181">![设置对 Windows 设备门户的访问](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-181">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="fc36b-182">*设置对 Windows 设备门户的访问*</span><span class="sxs-lookup"><span data-stu-id="fc36b-182">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="fc36b-183">首次连接到 HoloLens 上的设备门户时，需要创建用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="fc36b-183">The first time you connect to the Device Portal on your HoloLens, you'll need to create a username and password.</span></span>
1. <span data-ttu-id="fc36b-184">在电脑上的 Web 浏览器中，输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="fc36b-184">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="fc36b-185">“设置访问”页面随即打开。</span><span class="sxs-lookup"><span data-stu-id="fc36b-185">The Setup access page opens.</span></span>
2. <span data-ttu-id="fc36b-186">选择或点击“请求 PIN”，然后查看 HoloLens 屏幕以获取生成的 PIN。</span><span class="sxs-lookup"><span data-stu-id="fc36b-186">Select or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="fc36b-187">在“设备上显示的 PIN”文本框中输入该 PIN。</span><span class="sxs-lookup"><span data-stu-id="fc36b-187">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="fc36b-188">输入将用于连接到设备门户的用户名。</span><span class="sxs-lookup"><span data-stu-id="fc36b-188">Enter the user name you'll use to connect to the Device Portal.</span></span> <span data-ttu-id="fc36b-189">无需使用 Microsoft 帐户 (MSA) 名称或域名作为用户名。</span><span class="sxs-lookup"><span data-stu-id="fc36b-189">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="fc36b-190">输入密码并进行确认。</span><span class="sxs-lookup"><span data-stu-id="fc36b-190">Enter a password and confirm it.</span></span> <span data-ttu-id="fc36b-191">密码长度必须至少为七个字符。</span><span class="sxs-lookup"><span data-stu-id="fc36b-191">The password must be at least seven characters in length.</span></span> <span data-ttu-id="fc36b-192">无需使用 MSA 密码或域密码作为密码。</span><span class="sxs-lookup"><span data-stu-id="fc36b-192">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="fc36b-193">单击“配对”以连接到 HoloLens 上的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="fc36b-193">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="fc36b-194">今后如果你想要更改此用户名和密码，可以导航到 https://<HOLOLENS IP 地址>/devicepair.htm 来访问设备安全性页，然后重复上述过程。</span><span class="sxs-lookup"><span data-stu-id="fc36b-194">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="fc36b-195">安全证书</span><span class="sxs-lookup"><span data-stu-id="fc36b-195">Security certificate</span></span>

<span data-ttu-id="fc36b-196">如果在浏览器中看到“证书错误”，可以通过创建与该设备的信任关系来修复该错误。</span><span class="sxs-lookup"><span data-stu-id="fc36b-196">If you see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="fc36b-197">每个 HoloLens 会生成自签名证书以供其 SSL 连接使用。</span><span class="sxs-lookup"><span data-stu-id="fc36b-197">Each HoloLens generates a self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="fc36b-198">默认情况下，此证书不受电脑的 Web 浏览器信任，因此你可能会看到“证书错误”。</span><span class="sxs-lookup"><span data-stu-id="fc36b-198">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="fc36b-199">可以通过 USB 或信任的 Wi-Fi 网络从 HoloLens 下载此证书并在电脑上信任它，从而安全地连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="fc36b-199">You can securely connect to your device by downloading this certificate from your HoloLens over USB or a Wi-Fi network you trust and trusting it on your PC.</span></span>
1. <span data-ttu-id="fc36b-200">**确保在安全网络（USB 或信任的 Wi-Fi 网络）中操作。**</span><span class="sxs-lookup"><span data-stu-id="fc36b-200">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="fc36b-201">从设备门户上的“安全性”页下载此设备的证书。</span><span class="sxs-lookup"><span data-stu-id="fc36b-201">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="fc36b-202">导航到 https://<HOLOLENS IP 地址>/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="fc36b-202">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
   * <span data-ttu-id="fc36b-203">打开“系统”>“首选项”对应的节点。</span><span class="sxs-lookup"><span data-stu-id="fc36b-203">Open the node for System > Preferences.</span></span> 
   * <span data-ttu-id="fc36b-204">向下滚动到“设备安全性”，然后选择“下载此设备的证书”按钮。</span><span class="sxs-lookup"><span data-stu-id="fc36b-204">Scroll down to Device Security, select the "Download this device's certificate" button.</span></span>
3. <span data-ttu-id="fc36b-205">在电脑上安装“受信任的根证书颁发机构”存储中的证书。</span><span class="sxs-lookup"><span data-stu-id="fc36b-205">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="fc36b-206">在 Windows 菜单中键入：管理计算机证书并启动小程序。</span><span class="sxs-lookup"><span data-stu-id="fc36b-206">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="fc36b-207">展开“受信任的根证书颁发机构”文件夹。</span><span class="sxs-lookup"><span data-stu-id="fc36b-207">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="fc36b-208">选择“证书”文件夹。</span><span class="sxs-lookup"><span data-stu-id="fc36b-208">Select the **Certificates** folder.</span></span>
   * <span data-ttu-id="fc36b-209">在“操作”菜单中选择：“所有任务”>“导入...”</span><span class="sxs-lookup"><span data-stu-id="fc36b-209">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="fc36b-210">使用从 Device Portal 下载的证书文件，完成“证书导入向导”。</span><span class="sxs-lookup"><span data-stu-id="fc36b-210">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="fc36b-211">重新启动浏览器。</span><span class="sxs-lookup"><span data-stu-id="fc36b-211">Restart the browser.</span></span>

>[!NOTE]
> <span data-ttu-id="fc36b-212">此证书仅在该设备上受信任，如果刷写了设备，用户必须再次执行此过程。</span><span class="sxs-lookup"><span data-stu-id="fc36b-212">This certificate will only be trusted for the device and the user will have to go through the process again if the device is flashed.</span></span>

## <a name="sideloading-applications"></a><span data-ttu-id="fc36b-213">旁加载应用程序</span><span class="sxs-lookup"><span data-stu-id="fc36b-213">Sideloading applications</span></span>

### <a name="installing-a-certificate"></a><span data-ttu-id="fc36b-214">安装证书</span><span class="sxs-lookup"><span data-stu-id="fc36b-214">Installing a certificate</span></span>

1. <span data-ttu-id="fc36b-215">在 Windows 设备门户中，导航到“应用管理器”页</span><span class="sxs-lookup"><span data-stu-id="fc36b-215">In Windows Device Portal, navigate to the **Apps** manager page</span></span>
2. <span data-ttu-id="fc36b-216">在“部署应用”部分中，选择“安装证书”</span><span class="sxs-lookup"><span data-stu-id="fc36b-216">In the Deploy apps section, select **Install Certificate**</span></span>
3. <span data-ttu-id="fc36b-217">在“选择用于对应用包进行签名的证书文件(.cer)”中，选择“选择文件”，并浏览到与要旁加载的应用包关联的证书</span><span class="sxs-lookup"><span data-stu-id="fc36b-217">Under Select certificate file (.cer) used to sign an app package, select Choose File and browse to the certificate associated with the app package that you want to sideload</span></span>
4. <span data-ttu-id="fc36b-218">选择“安装”以开始安装</span><span class="sxs-lookup"><span data-stu-id="fc36b-218">Select **Install** to start the installation</span></span>

![在 Windows 设备门户中打开的“应用管理器”页的屏幕截图](images/sideloading-1.png)

### <a name="installing-an-app"></a><span data-ttu-id="fc36b-220">安装应用</span><span class="sxs-lookup"><span data-stu-id="fc36b-220">Installing an app</span></span>

> [!NOTE]
> <span data-ttu-id="fc36b-221">为了使应用能够通过设备门户成功安装，必须使用证书对其进行签名，此证书必须在尝试安装该应用前安装到设备上。</span><span class="sxs-lookup"><span data-stu-id="fc36b-221">In order for an app to install successfully via Device Portal it must be signed by a certificate, this certificate must be installed to the device prior to attempting to install the app.</span></span> <span data-ttu-id="fc36b-222">有关说明，请参阅[上一节](#installing-a-certificate)。</span><span class="sxs-lookup"><span data-stu-id="fc36b-222">See the [previous section](#installing-a-certificate) for instructions.</span></span>

1. <span data-ttu-id="fc36b-223">已从[ Visual Studio 中创建应用包](using-visual-studio.md)时，可以从生成的文件中将其远程安装到设备上：</span><span class="sxs-lookup"><span data-stu-id="fc36b-223">When you've [created an app package from Visual Studio](using-visual-studio.md), you can remotely install it onto your device from the generated files:</span></span>

![应用包文件内容的屏幕截图](images/sideloading-2.png)

2. <span data-ttu-id="fc36b-225">在 Windows 设备门户中，导航到“应用管理器”页</span><span class="sxs-lookup"><span data-stu-id="fc36b-225">In Windows Device Portal, navigate to the **Apps** manager page</span></span>
3. <span data-ttu-id="fc36b-226">在“部署应用”部分中，选择“本地存储” </span><span class="sxs-lookup"><span data-stu-id="fc36b-226">In the **Deploy** apps section, select **Local Storage**</span></span>
4. <span data-ttu-id="fc36b-227">在“选择应用程序包”下，选择“选择文件”，并浏览到要旁加载的应用包</span><span class="sxs-lookup"><span data-stu-id="fc36b-227">Under Select the application package, select Choose File and browse to the app package that you want to sideload</span></span>
5. <span data-ttu-id="fc36b-228">如果要与应用安装一起安装可选包或框架包，请选中相应的框，然后选择“下一步”：</span><span class="sxs-lookup"><span data-stu-id="fc36b-228">Check the respective boxes if you want to install optional or framework packages along with the app installation and select **Next**:</span></span>

![突出显示“本地存储”选项卡的 Windows 设备门户中打开的“应用管理器”页的屏幕截图](images/sideloading-3.png)

6. <span data-ttu-id="fc36b-230">选择“安装”以开始安装</span><span class="sxs-lookup"><span data-stu-id="fc36b-230">Select **Install** to start the installation</span></span>
 
![已成功完成安装的 Windows 设备门户中打开的“应用管理器”页的屏幕截图](images/sideloading-4.png) 

<span data-ttu-id="fc36b-232">安装完成后，在 HoloLens 上返回“所有应用”页，并启动新安装的应用程序！</span><span class="sxs-lookup"><span data-stu-id="fc36b-232">Once the installation is complete, go back to the **All apps** page on your HoloLens and launch your newly installed application!</span></span>

## <a name="device-portal-pages"></a><span data-ttu-id="fc36b-233">Device Portal 页面</span><span class="sxs-lookup"><span data-stu-id="fc36b-233">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="fc36b-234">主页</span><span class="sxs-lookup"><span data-stu-id="fc36b-234">Home</span></span>

<span data-ttu-id="fc36b-235">![Microsoft HoloLens 上的 Windows 设备门户主页](images/using-windows-portal-img-04.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-235">![Windows Device Portal home page on Microsoft HoloLens](images/using-windows-portal-img-04.png)</span></span><br>
<span data-ttu-id="fc36b-236">*Microsoft HoloLens 上的 Windows 设备门户主页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-236">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-237">Device Portal 会话从主页开始。</span><span class="sxs-lookup"><span data-stu-id="fc36b-237">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="fc36b-238">可从主页的左侧导航栏访问其他页面。</span><span class="sxs-lookup"><span data-stu-id="fc36b-238">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="fc36b-239">主页顶部的工具栏提供对常用状态和功能的访问。</span><span class="sxs-lookup"><span data-stu-id="fc36b-239">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="fc36b-240">**联机**：指示设备是否已连接到 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="fc36b-240">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="fc36b-241">**关机**：关闭设备。</span><span class="sxs-lookup"><span data-stu-id="fc36b-241">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="fc36b-242">**重启**：关闭再打开设备的电源。</span><span class="sxs-lookup"><span data-stu-id="fc36b-242">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="fc36b-243">**安全**：打开“设备安全性”页。</span><span class="sxs-lookup"><span data-stu-id="fc36b-243">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="fc36b-244">**冷**：指示设备的温度。</span><span class="sxs-lookup"><span data-stu-id="fc36b-244">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="fc36b-245">**交流电源**：指示设备是否已接上电源并正在充电。</span><span class="sxs-lookup"><span data-stu-id="fc36b-245">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="fc36b-246">**帮助**：打开 REST 接口文档页。</span><span class="sxs-lookup"><span data-stu-id="fc36b-246">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="fc36b-247">主页将显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="fc36b-247">The home page shows the following info:</span></span>
* <span data-ttu-id="fc36b-248">**设备状态：** 监视设备的运行状况并报告严重错误。</span><span class="sxs-lookup"><span data-stu-id="fc36b-248">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="fc36b-249">**Windows 信息：** 显示 HoloLens 的名称，以及当前安装的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="fc36b-249">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="fc36b-250">**首选项** 部分包含以下设置：</span><span class="sxs-lookup"><span data-stu-id="fc36b-250">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="fc36b-251">**IPD**：设置瞳孔间距 (IPD) - 在用户直视前方时两个瞳孔中心之间的距离，以毫米为单位。</span><span class="sxs-lookup"><span data-stu-id="fc36b-251">**IPD**: Sets the interpupillary distance (IPD) - the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="fc36b-252">该设置将立即生效。</span><span class="sxs-lookup"><span data-stu-id="fc36b-252">The setting takes effect immediately.</span></span> <span data-ttu-id="fc36b-253">在设置你的设备时，会自动计算该默认值。</span><span class="sxs-lookup"><span data-stu-id="fc36b-253">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="fc36b-254">**设备名称**：为 HoloLens 指定一个名称。</span><span class="sxs-lookup"><span data-stu-id="fc36b-254">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="fc36b-255">更改此值后，需重启设备才能使其生效。</span><span class="sxs-lookup"><span data-stu-id="fc36b-255">eboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="fc36b-256">单击“保存”后，对话框将询问是要立即重新启动还是稍后重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="fc36b-256">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="fc36b-257">**睡眠设置**：设置当设备已接上电源并使用电池时进入睡眠状态之前要等待的时长。</span><span class="sxs-lookup"><span data-stu-id="fc36b-257">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="fc36b-258">3D 视图</span><span class="sxs-lookup"><span data-stu-id="fc36b-258">3D View</span></span>

<span data-ttu-id="fc36b-259">![Microsoft HoloLens 上 Windows 设备门户中的“3D 视图”页](images/using-windows-portal-img-05.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-259">![3D View page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-05.png)</span></span><br>
<span data-ttu-id="fc36b-260">*Microsoft HoloLens 上 Windows 设备门户中的“3D 视图”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-260">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-261">使用“3D 视图”页面可查看 HoloLens 感知周围环境的方式。</span><span class="sxs-lookup"><span data-stu-id="fc36b-261">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="fc36b-262">使用鼠标即可导览该视图：</span><span class="sxs-lookup"><span data-stu-id="fc36b-262">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="fc36b-263">旋转：单击左键并移动鼠标；</span><span class="sxs-lookup"><span data-stu-id="fc36b-263">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="fc36b-264">平移：单击右键并移动鼠标；</span><span class="sxs-lookup"><span data-stu-id="fc36b-264">Pan: right click + mouse;</span></span>
* <span data-ttu-id="fc36b-265">缩放：滑动鼠标滚轮。</span><span class="sxs-lookup"><span data-stu-id="fc36b-265">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="fc36b-266">**跟踪选项**</span><span class="sxs-lookup"><span data-stu-id="fc36b-266">**Tracking options**</span></span>
   * <span data-ttu-id="fc36b-267">通过选中“强制视觉跟踪”可打开持续视觉跟踪。</span><span class="sxs-lookup"><span data-stu-id="fc36b-267">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="fc36b-268">“暂停”会停止视觉跟踪。</span><span class="sxs-lookup"><span data-stu-id="fc36b-268">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="fc36b-269">**视图选项**：设置 3D 视图中的选项：</span><span class="sxs-lookup"><span data-stu-id="fc36b-269">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="fc36b-270">**跟踪**：指示视觉跟踪是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="fc36b-270">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="fc36b-271">**显示地面**：显示方格形式的地平面。</span><span class="sxs-lookup"><span data-stu-id="fc36b-271">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="fc36b-272">**显示锥体**：显示视锥。</span><span class="sxs-lookup"><span data-stu-id="fc36b-272">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="fc36b-273">**显示防抖动平面**：显示 HoloLens 用于稳定动作的平面。</span><span class="sxs-lookup"><span data-stu-id="fc36b-273">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="fc36b-274">**显示网格**：显示代表周围环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="fc36b-274">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="fc36b-275">**显示空间定位点**：显示活动应用的空间定位点。</span><span class="sxs-lookup"><span data-stu-id="fc36b-275">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="fc36b-276">选择“更新”按钮以获取和刷新定位点。</span><span class="sxs-lookup"><span data-stu-id="fc36b-276">Select the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="fc36b-277">**显示细节**：显示手的位置、头部旋转四元数，以及设备原点矢量的实时变化。</span><span class="sxs-lookup"><span data-stu-id="fc36b-277">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="fc36b-278">**全屏按钮**：以全屏模式显示 3D 视图。</span><span class="sxs-lookup"><span data-stu-id="fc36b-278">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="fc36b-279">按 ESC 键可退出全屏视图。</span><span class="sxs-lookup"><span data-stu-id="fc36b-279">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="fc36b-280">**图面重构**：选择或点击“更新”可显示设备的最新空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="fc36b-280">**Surface reconstruction**: Select or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="fc36b-281">完成整个过程可能需要一些时间（但最多只需几秒钟）。</span><span class="sxs-lookup"><span data-stu-id="fc36b-281">A full pass may take some time to complete (up to a few seconds).</span></span> <span data-ttu-id="fc36b-282">在 3D 视图中，网格不会自动更新，必须手动选择“更新”才能获取设备的最新网格。</span><span class="sxs-lookup"><span data-stu-id="fc36b-282">The mesh doesn't update automatically in the 3D view, and you must manually select **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="fc36b-283">选择“保存”可在电脑上将当前的空间映射网格保存为 obj 文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-283">Select **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="fc36b-284">**空间定位点**：选择“更新”可显示或更新活动应用的空间定位点。</span><span class="sxs-lookup"><span data-stu-id="fc36b-284">**Spatial anchors**: Select Update to display or update the spatial anchors for the active app.</span></span>

### <a name="map-manager"></a><span data-ttu-id="fc36b-285">地图管理器</span><span class="sxs-lookup"><span data-stu-id="fc36b-285">Map Manager</span></span>

<span data-ttu-id="fc36b-286">通过地图管理器，可跨设备共享地图，这可用于为基于位置的娱乐客户设置共享体验。</span><span class="sxs-lookup"><span data-stu-id="fc36b-286">Map Manager allows you to share maps across devices, which can be used to set up shared experiences for Location-Based Entertainment customers.</span></span> <span data-ttu-id="fc36b-287">该工具允许你导入和导出系统地图和定位点。</span><span class="sxs-lookup"><span data-stu-id="fc36b-287">The tool allows you to import and export system maps and anchors.</span></span>  

<span data-ttu-id="fc36b-288">若要访问地图管理器，请登录设备门户并选择“混合现实”->“地图管理器”：</span><span class="sxs-lookup"><span data-stu-id="fc36b-288">To access the Map Manager, log into the Device Portal and select **Mixed Reality -> Map Manager**:</span></span> 

<span data-ttu-id="fc36b-289">![Windows 设备门户中的“地图管理器”页](images/using-windows-portal-img-06.png)
Microsoft HoloLens 上 Windows 设备门户中的“地图管理器”页</span><span class="sxs-lookup"><span data-stu-id="fc36b-289">![Map manager page in Windows Device Portal](images/using-windows-portal-img-06.png)
*Map Manager page in Windows Device Portal on Microsoft HoloLens*</span></span>

#### <a name="exporting-and-importing-maps"></a><span data-ttu-id="fc36b-290">导出和导入地图</span><span class="sxs-lookup"><span data-stu-id="fc36b-290">Exporting and importing maps</span></span>

<span data-ttu-id="fc36b-291">要导出地图，请选择“导出系统地图和定位点”。</span><span class="sxs-lookup"><span data-stu-id="fc36b-291">To export maps, select **Export System Map & Anchors**.</span></span> <span data-ttu-id="fc36b-292">此操作可能需要一段时间，所以在导出地图时，请准备好等待 30-60 秒。</span><span class="sxs-lookup"><span data-stu-id="fc36b-292">This could take a while so be prepared to wait for 30-60 seconds while the map is exported.</span></span> <span data-ttu-id="fc36b-293">完成后，文件将下载到浏览器中。</span><span class="sxs-lookup"><span data-stu-id="fc36b-293">Once it’s complete, the file will be downloaded in your browser.</span></span>  

<span data-ttu-id="fc36b-294">要导入地图和定位点，请分别选择“上传地图文件”和“上传定位点文件”，然后选择已经导出的地图或定位点文件 。</span><span class="sxs-lookup"><span data-stu-id="fc36b-294">To import maps and anchors, select **Upload a map file** and **Upload an anchor file** respectively and select a map or anchor file that you've already exported.</span></span> <span data-ttu-id="fc36b-295">上传的地图或定位点文件可能来自任何其他 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="fc36b-295">The uploaded map or anchor file can come from any other HoloLens device.</span></span> 

> [!NOTE]
> <span data-ttu-id="fc36b-296">在 HoloLens 上，还可以导入和导出空间映射数据库。</span><span class="sxs-lookup"><span data-stu-id="fc36b-296">On HoloLens, it's also possible to import and export the spatial mapping data base.</span></span> <span data-ttu-id="fc36b-297">然而，这在非 HoloLens 设备上不起作用。</span><span class="sxs-lookup"><span data-stu-id="fc36b-297">However, this doesn't work on non-HoloLens devices.</span></span>  


### <a name="mixed-reality-capture"></a><span data-ttu-id="fc36b-298">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="fc36b-298">Mixed Reality Capture</span></span>

<span data-ttu-id="fc36b-299">![Microsoft HoloLens 上 Windows 设备门户中的“混合现实捕获”页](images/using-windows-portal-img-07.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-299">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-07.png)</span></span><br>
<span data-ttu-id="fc36b-300">*Microsoft HoloLens 上 Windows 设备门户中的“混合现实捕获”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-300">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-301">使用“混合现实捕获”页面可保存 HoloLens 中的媒体流。</span><span class="sxs-lookup"><span data-stu-id="fc36b-301">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="fc36b-302">**捕获设置**：通过检查以下设置来控制捕获的媒体流：</span><span class="sxs-lookup"><span data-stu-id="fc36b-302">**Capture Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="fc36b-303">**全息影像**：捕获视频流中的全息内容。</span><span class="sxs-lookup"><span data-stu-id="fc36b-303">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="fc36b-304">呈现全息图时使用的是单声道，而不是立体声。</span><span class="sxs-lookup"><span data-stu-id="fc36b-304">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="fc36b-305">**PV 相机**：捕获照片/视频相机中的视频流。</span><span class="sxs-lookup"><span data-stu-id="fc36b-305">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="fc36b-306">**麦克风音频**：捕获麦克风阵列中的音频。</span><span class="sxs-lookup"><span data-stu-id="fc36b-306">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="fc36b-307">**应用音频**：捕获当前正在运行的应用中的音频。</span><span class="sxs-lookup"><span data-stu-id="fc36b-307">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="fc36b-308">**从相机渲染**：从照片/视频相机的角度对齐捕获内容，前提是 [正在运行的应用支持此功能](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)（仅限 HoloLens 2）。</span><span class="sxs-lookup"><span data-stu-id="fc36b-308">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="fc36b-309">**实时预览质量**：选择用于实时预览的屏幕分辨率、帧速率和流处理速率。</span><span class="sxs-lookup"><span data-stu-id="fc36b-309">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="fc36b-310">**音频设置**（仅限 HoloLens 2）：</span><span class="sxs-lookup"><span data-stu-id="fc36b-310">**Audio Settings** (HoloLens 2 only):</span></span>
  * <span data-ttu-id="fc36b-311">**音频媒介类别**：选择在处理麦克风时使用的类别。</span><span class="sxs-lookup"><span data-stu-id="fc36b-311">**Audio Media Category**: Select the category is used when processing the microphone.</span></span> <span data-ttu-id="fc36b-312">“默认值”将包括某些环境，而“通信”会应用背景噪音消除 。</span><span class="sxs-lookup"><span data-stu-id="fc36b-312">**Default**  will include some of the environment, while **Communications** applies background noise cancellation.</span></span>
  * <span data-ttu-id="fc36b-313">**应用音频增益**：应用于应用音频音量的增益。</span><span class="sxs-lookup"><span data-stu-id="fc36b-313">**App Audio Gain**: The gain applied to app audio's volume.</span></span>
  * <span data-ttu-id="fc36b-314">**麦克风音频增益**：应用于麦克风音频音量的增益。</span><span class="sxs-lookup"><span data-stu-id="fc36b-314">**Mic Audio Gain**: The gain applied to mic audio's volume.</span></span>
* <span data-ttu-id="fc36b-315">**照片和视频设置**（HoloLens 2，版本 2004 或更高版本）：</span><span class="sxs-lookup"><span data-stu-id="fc36b-315">**Photo and Video Settings** (HoloLens 2, version 2004 or later):</span></span>
  * <span data-ttu-id="fc36b-316">**捕获配置文件**：选择拍摄照片和视频时使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-316">**Capture Profile**: Select the profile used when taking photos and videos.</span></span> <span data-ttu-id="fc36b-317">配置文件决定可用的分辨率和帧速率。</span><span class="sxs-lookup"><span data-stu-id="fc36b-317">The profile determines which resolutions and frame-rates are available.</span></span>
  * <span data-ttu-id="fc36b-318">**照片分辨率**：拍摄照片时使用的分辨率。</span><span class="sxs-lookup"><span data-stu-id="fc36b-318">**Photo Resolution**: The resolution the photo will be taken with.</span></span>
  * <span data-ttu-id="fc36b-319">**视频分辨率和帧速率**：拍摄视频时使用的分辨率和帧速率。</span><span class="sxs-lookup"><span data-stu-id="fc36b-319">**Video Resolution and Frame-rate**: The resolution and frame-rate the video will be taken with.</span></span>
  * <span data-ttu-id="fc36b-320">**视频稳定缓冲区**：拍摄视频时使用的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="fc36b-320">**Video Stabilization Buffer**: The buffer size used when taking a video.</span></span> <span data-ttu-id="fc36b-321">此值越大，弥补快速移动的效果越好。</span><span class="sxs-lookup"><span data-stu-id="fc36b-321">The higher the value, the better it can compensate for quick movements.</span></span>
* <span data-ttu-id="fc36b-322">选择或点击“实时预览”按钮可显示捕获流。</span><span class="sxs-lookup"><span data-stu-id="fc36b-322">Select or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="fc36b-323">“停止实时预览”会停止捕获流。</span><span class="sxs-lookup"><span data-stu-id="fc36b-323">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="fc36b-324">选择或点击“录制”可使用指定的设置开始录制混合现实流。</span><span class="sxs-lookup"><span data-stu-id="fc36b-324">Select or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="fc36b-325">“停止录制”会结束录制，并保存录制内容。</span><span class="sxs-lookup"><span data-stu-id="fc36b-325">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="fc36b-326">选择或点击“拍摄照片”可从捕获流中捕获静止图像。</span><span class="sxs-lookup"><span data-stu-id="fc36b-326">Select or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="fc36b-327">选择或点击“还原默认设置”，可还原音频、照片和视频设置的默认设置。</span><span class="sxs-lookup"><span data-stu-id="fc36b-327">Select or tap **Restore Default Settings** to restore the default settings for audio, photo, and video settings.</span></span>
* <span data-ttu-id="fc36b-328">**视频和照片**：显示在设备上捕获的视频和照片列表。</span><span class="sxs-lookup"><span data-stu-id="fc36b-328">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

<span data-ttu-id="fc36b-329">此页面上的所有设置都适用于使用 Windows 设备门户完成的捕获。</span><span class="sxs-lookup"><span data-stu-id="fc36b-329">All settings on this page apply to captures taken using Windows Device Portal.</span></span> <span data-ttu-id="fc36b-330">一些设置还适用于系统 MRC（包括“开始”菜单、硬件按钮、全局语音命令、Miracast）和自定义 MRC 记录器。</span><span class="sxs-lookup"><span data-stu-id="fc36b-330">Some additionally apply to System MRC, including start menu, hardware buttons, global voice commands, Miracast, and custom MRC Recorders.</span></span>

|  <span data-ttu-id="fc36b-331">设置</span><span class="sxs-lookup"><span data-stu-id="fc36b-331">Setting</span></span>  |  <span data-ttu-id="fc36b-332">适用于系统 MRC</span><span class="sxs-lookup"><span data-stu-id="fc36b-332">Applies to System MRC</span></span>  |  <span data-ttu-id="fc36b-333">适用于自定义 MRC 记录器</span><span class="sxs-lookup"><span data-stu-id="fc36b-333">Applies to Custom MRC Recorders</span></span> |
|----------|----------|----------|
|  <span data-ttu-id="fc36b-334">全息影像</span><span class="sxs-lookup"><span data-stu-id="fc36b-334">Holograms</span></span>  |  <span data-ttu-id="fc36b-335">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-335">No</span></span>  |  <span data-ttu-id="fc36b-336">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-336">No</span></span> |
|  <span data-ttu-id="fc36b-337">PV 摄像头</span><span class="sxs-lookup"><span data-stu-id="fc36b-337">PV camera</span></span>  |  <span data-ttu-id="fc36b-338">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-338">No</span></span>  |  <span data-ttu-id="fc36b-339">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-339">No</span></span> |
|  <span data-ttu-id="fc36b-340">麦克风音频</span><span class="sxs-lookup"><span data-stu-id="fc36b-340">Mic Audio</span></span>  |  <span data-ttu-id="fc36b-341">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-341">No</span></span>  |  <span data-ttu-id="fc36b-342">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-342">No</span></span> |
|  <span data-ttu-id="fc36b-343">应用音频</span><span class="sxs-lookup"><span data-stu-id="fc36b-343">App Audio</span></span>  |  <span data-ttu-id="fc36b-344">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-344">No</span></span>  |  <span data-ttu-id="fc36b-345">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-345">No</span></span> |
|  <span data-ttu-id="fc36b-346">从摄像头渲染</span><span class="sxs-lookup"><span data-stu-id="fc36b-346">Render from Camera</span></span>  |  <span data-ttu-id="fc36b-347">是</span><span class="sxs-lookup"><span data-stu-id="fc36b-347">Yes</span></span>    |  <span data-ttu-id="fc36b-348">是（可以重写）</span><span class="sxs-lookup"><span data-stu-id="fc36b-348">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="fc36b-349">实时预览质量</span><span class="sxs-lookup"><span data-stu-id="fc36b-349">Live preview quality</span></span>  |  <span data-ttu-id="fc36b-350">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-350">No</span></span>  |  <span data-ttu-id="fc36b-351">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-351">No</span></span> |
|  <span data-ttu-id="fc36b-352">音频媒介类别</span><span class="sxs-lookup"><span data-stu-id="fc36b-352">Audio Media Category</span></span>  |  <span data-ttu-id="fc36b-353">是</span><span class="sxs-lookup"><span data-stu-id="fc36b-353">Yes</span></span>  |  <span data-ttu-id="fc36b-354">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-354">No</span></span> |
|  <span data-ttu-id="fc36b-355">应用音频增益</span><span class="sxs-lookup"><span data-stu-id="fc36b-355">App Audio Gain</span></span>  |  <span data-ttu-id="fc36b-356">是</span><span class="sxs-lookup"><span data-stu-id="fc36b-356">Yes</span></span>  |  <span data-ttu-id="fc36b-357">是（可以重写）</span><span class="sxs-lookup"><span data-stu-id="fc36b-357">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="fc36b-358">麦克风音频增益</span><span class="sxs-lookup"><span data-stu-id="fc36b-358">Mic Audio Gain</span></span>  |  <span data-ttu-id="fc36b-359">是</span><span class="sxs-lookup"><span data-stu-id="fc36b-359">Yes</span></span>  |  <span data-ttu-id="fc36b-360">是（可以重写）</span><span class="sxs-lookup"><span data-stu-id="fc36b-360">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="fc36b-361">捕获配置文件</span><span class="sxs-lookup"><span data-stu-id="fc36b-361">Capture Profile</span></span>  |  <span data-ttu-id="fc36b-362">是</span><span class="sxs-lookup"><span data-stu-id="fc36b-362">Yes</span></span>  |  <span data-ttu-id="fc36b-363">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-363">No</span></span> |
|  <span data-ttu-id="fc36b-364">照片分辨率</span><span class="sxs-lookup"><span data-stu-id="fc36b-364">Photo Resolution</span></span>  |  <span data-ttu-id="fc36b-365">是</span><span class="sxs-lookup"><span data-stu-id="fc36b-365">Yes</span></span>  |  <span data-ttu-id="fc36b-366">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-366">No</span></span> |
|  <span data-ttu-id="fc36b-367">视频分辨率和帧速率</span><span class="sxs-lookup"><span data-stu-id="fc36b-367">Video Resolution and Frame-rate</span></span>  |  <span data-ttu-id="fc36b-368">是</span><span class="sxs-lookup"><span data-stu-id="fc36b-368">Yes</span></span>  |  <span data-ttu-id="fc36b-369">否</span><span class="sxs-lookup"><span data-stu-id="fc36b-369">No</span></span> |
|  <span data-ttu-id="fc36b-370">视频稳定缓冲区</span><span class="sxs-lookup"><span data-stu-id="fc36b-370">Video Stabilization Buffer</span></span>  |  <span data-ttu-id="fc36b-371">是</span><span class="sxs-lookup"><span data-stu-id="fc36b-371">Yes</span></span>  |  <span data-ttu-id="fc36b-372">是（可以重写）</span><span class="sxs-lookup"><span data-stu-id="fc36b-372">Yes (can be overridden)</span></span> |

> [!NOTE]
> <span data-ttu-id="fc36b-373">[同步 MRC 存在限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)：</span><span class="sxs-lookup"><span data-stu-id="fc36b-373">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="fc36b-374">如果当 Windows 设备门户正在录制视频时某个应用尝试访问照片/视频相机，则视频录制将会停止。</span><span class="sxs-lookup"><span data-stu-id="fc36b-374">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="fc36b-375">如果应用以 SharedReadOnly 模式访问照片/视频相机，HoloLens 2 将不会停止视频录制。</span><span class="sxs-lookup"><span data-stu-id="fc36b-375">HoloLens 2 will not stop recording video if the app accesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="fc36b-376">如果应用正在使用照片/视频相机，则 Windows 设备门户可以拍摄照片或录制视频。</span><span class="sxs-lookup"><span data-stu-id="fc36b-376">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="fc36b-377">实时传送视频流：</span><span class="sxs-lookup"><span data-stu-id="fc36b-377">Live streaming:</span></span>
>   * <span data-ttu-id="fc36b-378">从 Windows 设备门户实时传送视频流时，HoloLens（第一代）会阻止应用访问照片/视频相机。</span><span class="sxs-lookup"><span data-stu-id="fc36b-378">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="fc36b-379">如果应用正在使用照片/视频相机，则 HoloLens（第一代）将无法实时传送视频流。</span><span class="sxs-lookup"><span data-stu-id="fc36b-379">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="fc36b-380">当应用尝试以 ExclusiveControl 模式访问照片/视频相机时，HoloLens 2 会自动停止实时传送视频流。</span><span class="sxs-lookup"><span data-stu-id="fc36b-380">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="fc36b-381">当应用正在使用 PV 相机时，HoloLens 2 可以启动实时传送视频流。</span><span class="sxs-lookup"><span data-stu-id="fc36b-381">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="fc36b-382">性能跟踪</span><span class="sxs-lookup"><span data-stu-id="fc36b-382">Performance Tracing</span></span>

<span data-ttu-id="fc36b-383">![Microsoft HoloLens 上 Windows 设备门户中的“性能跟踪”页](images/using-windows-portal-img-08.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-383">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-08.png)</span></span><br>
<span data-ttu-id="fc36b-384">*Microsoft HoloLens 上 Windows 设备门户中的“性能跟踪”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-384">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-385">从 HoloLens 中捕获 [Windows Performance Recorder](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR) 跟踪。</span><span class="sxs-lookup"><span data-stu-id="fc36b-385">Capture [Windows Performance Recorder](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="fc36b-386">**可用配置文件**：从下拉列表中选择 WPR 配置文件，然后选择或点击“开始”以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="fc36b-386">**Available profiles**: Select the WPR profile from the dropdown, and select or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="fc36b-387">**自定义配置文件**：选择或点击“浏览”以从电脑中选择 WPR 配置文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-387">**Custom profiles**: Select or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="fc36b-388">选择或点击“上传并启动”以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="fc36b-388">Select or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="fc36b-389">要停止跟踪，请选择“停止”链接。</span><span class="sxs-lookup"><span data-stu-id="fc36b-389">To stop the trace, select the stop link.</span></span> <span data-ttu-id="fc36b-390">请保持打开此页，直到跟踪文件完成下载。</span><span class="sxs-lookup"><span data-stu-id="fc36b-390">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="fc36b-391">可以打开捕获的 ETL 文件以供在 [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)) 中进行分析。</span><span class="sxs-lookup"><span data-stu-id="fc36b-391">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)).</span></span>

### <a name="processes"></a><span data-ttu-id="fc36b-392">进程</span><span class="sxs-lookup"><span data-stu-id="fc36b-392">Processes</span></span>

<span data-ttu-id="fc36b-393">![Microsoft HoloLens 上 Windows 设备门户中的“进程”页](images/using-windows-portal-img-09.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-393">![Processes page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-09.png)</span></span><br>
<span data-ttu-id="fc36b-394">*Microsoft HoloLens 上 Windows 设备门户中的“进程”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-394">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-395">显示有关当前正在运行的进程的详细信息。</span><span class="sxs-lookup"><span data-stu-id="fc36b-395">Shows details about currently running processes.</span></span> <span data-ttu-id="fc36b-396">这包括应用和系统进程。</span><span class="sxs-lookup"><span data-stu-id="fc36b-396">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="fc36b-397">系统性能</span><span class="sxs-lookup"><span data-stu-id="fc36b-397">System Performance</span></span>

<span data-ttu-id="fc36b-398">![Microsoft HoloLens 上 Windows 设备门户中的“系统性能”页](images/using-windows-portal-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-398">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-10.png)</span></span><br>
<span data-ttu-id="fc36b-399">*Microsoft HoloLens 上 Windows 设备门户中的“系统性能”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-399">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-400">显示系统诊断信息的实时图形，如电源使用情况、帧速率和 CPU 负载。</span><span class="sxs-lookup"><span data-stu-id="fc36b-400">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="fc36b-401">可用的指标如下所示：</span><span class="sxs-lookup"><span data-stu-id="fc36b-401">These are the available metrics:</span></span>
* <span data-ttu-id="fc36b-402">**SoC 电源**：片上系统的瞬时用电量，为一分钟平均值</span><span class="sxs-lookup"><span data-stu-id="fc36b-402">**SoC power**: Instantaneous system-on-chip power usage, averaged over one minute</span></span>
* <span data-ttu-id="fc36b-403">**系统电源**：系统的瞬时用电量，为一分钟平均值</span><span class="sxs-lookup"><span data-stu-id="fc36b-403">**System power**: Instantaneous system power usage, averaged over one minute</span></span>
* <span data-ttu-id="fc36b-404">**帧速率**：每秒帧数、每秒丢失的垂直消隐数和连续丢失的垂直消隐数</span><span class="sxs-lookup"><span data-stu-id="fc36b-404">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="fc36b-405">**GPU**：GPU 引擎利用率、总可用量的百分比</span><span class="sxs-lookup"><span data-stu-id="fc36b-405">**GPU**: GPU engine usage, percent of total available</span></span>
* <span data-ttu-id="fc36b-406">**CPU**：总可用量的百分比</span><span class="sxs-lookup"><span data-stu-id="fc36b-406">**CPU**: percent of total available</span></span>
* <span data-ttu-id="fc36b-407">**I/O**：读取和写入次数</span><span class="sxs-lookup"><span data-stu-id="fc36b-407">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="fc36b-408">**网络**：接收和发送数据量</span><span class="sxs-lookup"><span data-stu-id="fc36b-408">**Network**: Received and sent</span></span>
* <span data-ttu-id="fc36b-409">**内存**：总计、已用、已提交、已分页和未分页</span><span class="sxs-lookup"><span data-stu-id="fc36b-409">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="fc36b-410">“应用”</span><span class="sxs-lookup"><span data-stu-id="fc36b-410">Apps</span></span>

<span data-ttu-id="fc36b-411">![Microsoft HoloLens 上 Windows 设备门户中的“应用”页](images/using-windows-portal-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-411">![Apps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-11.png)</span></span><br>
<span data-ttu-id="fc36b-412">*Microsoft HoloLens 上 Windows 设备门户中的“应用”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-412">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-413">管理 HoloLens 上安装的应用。</span><span class="sxs-lookup"><span data-stu-id="fc36b-413">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="fc36b-414">**已安装的应用**：删除和启动应用。</span><span class="sxs-lookup"><span data-stu-id="fc36b-414">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="fc36b-415">**正在运行的应用**：列出当前正在运行的应用。</span><span class="sxs-lookup"><span data-stu-id="fc36b-415">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="fc36b-416">**安装应用**：从计算机/网络上的文件夹中选择应用包进行安装。</span><span class="sxs-lookup"><span data-stu-id="fc36b-416">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="fc36b-417">**依赖项**：为要安装的应用添加依赖项。</span><span class="sxs-lookup"><span data-stu-id="fc36b-417">**Dependency**: Add dependencies for the app you're going to install.</span></span>
* <span data-ttu-id="fc36b-418">**部署**：将所选应用和依赖项部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fc36b-418">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="fc36b-419">应用故障转储</span><span class="sxs-lookup"><span data-stu-id="fc36b-419">App Crash Dumps</span></span>

<span data-ttu-id="fc36b-420">![Microsoft HoloLens 上 Windows 设备门户中的“应用故障转储”页](images/using-windows-portal-img-12.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-420">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-12.png)</span></span><br>
<span data-ttu-id="fc36b-421">*Microsoft HoloLens 上 Windows 设备门户中的“应用故障转储”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-421">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-422">此页面允许你收集旁加载应用的故障转储。</span><span class="sxs-lookup"><span data-stu-id="fc36b-422">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="fc36b-423">对于要收集其故障转储的每个应用，请选中对应的“已启用故障转储”复选框。</span><span class="sxs-lookup"><span data-stu-id="fc36b-423">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="fc36b-424">返回到此页面可收集故障转储。</span><span class="sxs-lookup"><span data-stu-id="fc36b-424">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="fc36b-425">可[在 Visual Studio 中打开转储文件进行调试](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files)。</span><span class="sxs-lookup"><span data-stu-id="fc36b-425">Dump files can be [opened in Visual Studio for debugging](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="fc36b-426">文件资源浏览器</span><span class="sxs-lookup"><span data-stu-id="fc36b-426">File Explorer</span></span>

<span data-ttu-id="fc36b-427">![Microsoft HoloLens 上 Windows 设备门户中的“文件资源浏览器”页](images/using-windows-portal-img-13.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-427">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-13.png)</span></span><br>
<span data-ttu-id="fc36b-428">*Microsoft HoloLens 上 Windows 设备门户中的“文件资源浏览器”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-428">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-429">使用文件资源管理器可以浏览、上传和下载文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-429">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="fc36b-430">对于从 Visual Studio 或设备门户部署的应用，可以处理“文档”文件夹、“图片”文件夹和本地存储文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-430">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="fc36b-431">展台模式</span><span class="sxs-lookup"><span data-stu-id="fc36b-431">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="fc36b-432">展台模式仅适用于 [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features)。</span><span class="sxs-lookup"><span data-stu-id="fc36b-432">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features).</span></span>

![Microsoft HoloLens 上 Windows 设备门户中的“展台模式”页](images/using-windows-portal-img-14.png)

<span data-ttu-id="fc36b-434">有关如何通过 Windows 设备门户启用展台模式的最新说明，请查看 Windows IT 专业人员中心内的[在展台模式下设置 HoloLens](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 一文。</span><span class="sxs-lookup"><span data-stu-id="fc36b-434">Check the [Set up HoloLens in kiosk mode](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="fc36b-435">日志记录</span><span class="sxs-lookup"><span data-stu-id="fc36b-435">Logging</span></span>

<span data-ttu-id="fc36b-436">![Microsoft HoloLens 上 Windows 设备门户中的“日志记录”页](images/using-windows-portal-img-15.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-436">![Logging page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-15.png)</span></span><br>
<span data-ttu-id="fc36b-437">*Microsoft HoloLens 上 Windows 设备门户中的“日志记录”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-437">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-438">管理 HoloLens 上的实时 Windows 事件跟踪 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="fc36b-438">Manages real-time Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="fc36b-439">选中“隐藏提供程序”以仅显示“事件”列表。 </span><span class="sxs-lookup"><span data-stu-id="fc36b-439">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="fc36b-440">**已注册的提供程序**：选择 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="fc36b-440">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="fc36b-441">跟踪级别是以下值之一：</span><span class="sxs-lookup"><span data-stu-id="fc36b-441">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="fc36b-442">异常退出或终止</span><span class="sxs-lookup"><span data-stu-id="fc36b-442">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="fc36b-443">严重错误</span><span class="sxs-lookup"><span data-stu-id="fc36b-443">Severe errors</span></span>
   3. <span data-ttu-id="fc36b-444">警告</span><span class="sxs-lookup"><span data-stu-id="fc36b-444">Warnings</span></span>
   4. <span data-ttu-id="fc36b-445">非错误警告</span><span class="sxs-lookup"><span data-stu-id="fc36b-445">Non-error warnings</span></span>

<span data-ttu-id="fc36b-446">选择或点击“启用”以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="fc36b-446">Select or tap **Enable** to start tracing.</span></span> <span data-ttu-id="fc36b-447">提供程序将添加到“已启用的提供程序”下拉列表。</span><span class="sxs-lookup"><span data-stu-id="fc36b-447">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="fc36b-448">**自定义提供程序**：选择自定义 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="fc36b-448">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="fc36b-449">根据其 GUDI 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="fc36b-449">Identify the provider by its GUID.</span></span> <span data-ttu-id="fc36b-450">不要在 GUID 中包含括号。</span><span class="sxs-lookup"><span data-stu-id="fc36b-450">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="fc36b-451">**已启用的提供程序**：列出已启用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="fc36b-451">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="fc36b-452">从下拉列表中选择一个提供程序，然后单击或敲击“禁用”可停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="fc36b-452">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="fc36b-453">单击或敲击“全部停止”会暂停所有跟踪。</span><span class="sxs-lookup"><span data-stu-id="fc36b-453">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="fc36b-454">**提供程序历史记录**：显示已在当前会话期间启用的 ETW 提供程序。</span><span class="sxs-lookup"><span data-stu-id="fc36b-454">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="fc36b-455">单击或敲击“启用”可激活已禁用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="fc36b-455">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="fc36b-456">单击或敲击“清除”可清除历史记录。</span><span class="sxs-lookup"><span data-stu-id="fc36b-456">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="fc36b-457">**事件**：以表格格式列出来自选定提供程序的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-457">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="fc36b-458">此表将实时更新。</span><span class="sxs-lookup"><span data-stu-id="fc36b-458">This table is updated in real time.</span></span> <span data-ttu-id="fc36b-459">在该表格下方，单击“清除”按钮可删除其中的所有 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-459">Beneath the table, click the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="fc36b-460">这不会禁用任何提供程序。</span><span class="sxs-lookup"><span data-stu-id="fc36b-460">This doesn't disable any providers.</span></span> <span data-ttu-id="fc36b-461">可以单击“保存到文件”以将当前收集的 ETW 事件本地导出到 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-461">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="fc36b-462">**筛选器**：用于按 ID、关键字、级别、提供程序名称、任务名称或文本筛选收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-462">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="fc36b-463">可将多个条件组合在一起：</span><span class="sxs-lookup"><span data-stu-id="fc36b-463">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="fc36b-464">对于应用到同一属性的条件，将显示可满足其中任何一个条件的事件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-464">For criteria applying to the same property, events that can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="fc36b-465">对于应用到不同属性的条件，事件必须满足所有条件</span><span class="sxs-lookup"><span data-stu-id="fc36b-465">For criteria applying to a different property, events must satisfy all of the criteria</span></span>

<span data-ttu-id="fc36b-466">例如，可以指定条件 *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span><span class="sxs-lookup"><span data-stu-id="fc36b-466">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="fc36b-467">模拟</span><span class="sxs-lookup"><span data-stu-id="fc36b-467">Simulation</span></span>

<span data-ttu-id="fc36b-468">![Microsoft HoloLens 上 Windows 设备门户中的“模拟”页](images/using-windows-portal-img-16.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-468">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-16.png)</span></span><br>
<span data-ttu-id="fc36b-469">*Microsoft HoloLens 上 Windows 设备门户中的“模拟”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-469">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-470">允许你记录和播放用于测试的输入数据。</span><span class="sxs-lookup"><span data-stu-id="fc36b-470">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="fc36b-471">**捕获房间**：用于下载模拟房间文件，该文件包含用户周围环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="fc36b-471">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="fc36b-472">命名该房间，然后单击“捕获”以在电脑上将该数据保存为 .xef 文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-472">Name the room and then click **Capture** to save the data as an .xef file on your PC.</span></span> <span data-ttu-id="fc36b-473">此房间文件可以加载到 HoloLens 仿真器中。</span><span class="sxs-lookup"><span data-stu-id="fc36b-473">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="fc36b-474">**录制**：选中要录制的流、为录制内容命名，然后单击或敲击“录制”开始录制。</span><span class="sxs-lookup"><span data-stu-id="fc36b-474">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="fc36b-475">使用你的 HoloLens 执行操作，然后单击“停止”以在电脑上将该数据保存为 .xef 文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-475">Perform actions with your HoloLens and then click **Stop** to save the data as an .xef file on your PC.</span></span> <span data-ttu-id="fc36b-476">可以在 HoloLens 仿真器或设备上加载此文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-476">This file can be loaded on the HoloLens emulator or device.</span></span>
  >[!NOTE]
  ><span data-ttu-id="fc36b-477">“录制”功能目前仅在第一代 HoloLens 上可用。</span><span class="sxs-lookup"><span data-stu-id="fc36b-477">The Recording feature is currently only available on the HoloLens 1st gen.</span></span> <span data-ttu-id="fc36b-478">HoloLens 2 目前尚不支持录制功能，但支持播放现有的录制内容。</span><span class="sxs-lookup"><span data-stu-id="fc36b-478">Recording is not yet supported on HoloLens 2, but Playback of existing recordings is supported.</span></span>
* <span data-ttu-id="fc36b-479">**播放**：单击或敲击“上传录制内容”可从电脑中选择 xef 文件，然后将数据发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fc36b-479">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="fc36b-480">**控制模式**：在 HoloLens 上，从下拉列表中选择“默认”或“模拟”，然后单击或敲击“设置”按钮选中该模式。  </span><span class="sxs-lookup"><span data-stu-id="fc36b-480">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="fc36b-481">相反，选择“模拟”会禁用 HoloLens 上的真实传感器，并使用已上载的模拟数据。</span><span class="sxs-lookup"><span data-stu-id="fc36b-481">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="fc36b-482">如果切换到“模拟”，HoloLens 将不会响应真实用户，除非切换回“默认”。</span><span class="sxs-lookup"><span data-stu-id="fc36b-482">If you switch to "Simulation", your HoloLens won't respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="fc36b-483">网络</span><span class="sxs-lookup"><span data-stu-id="fc36b-483">Networking</span></span>

<span data-ttu-id="fc36b-484">![Microsoft HoloLens 上 Windows 设备门户中的“网络”页](images/using-windows-portal-img-17.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-484">![Networking page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-17.png)</span></span><br>
<span data-ttu-id="fc36b-485">*Microsoft HoloLens 上 Windows 设备门户中的“网络”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-485">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-486">管理 HoloLens 上的 Wi-Fi 连接。</span><span class="sxs-lookup"><span data-stu-id="fc36b-486">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="fc36b-487">**WiFi 适配器**：使用下拉控件选择 Wi-Fi 适配器和配置文件。</span><span class="sxs-lookup"><span data-stu-id="fc36b-487">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="fc36b-488">单击或敲击“连接”以使用选定的适配器。</span><span class="sxs-lookup"><span data-stu-id="fc36b-488">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="fc36b-489">**可用网络**：列出 HoloLens 可连接到的 Wi-Fi 网络。</span><span class="sxs-lookup"><span data-stu-id="fc36b-489">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="fc36b-490">单击或敲击“刷新”可更新列表。</span><span class="sxs-lookup"><span data-stu-id="fc36b-490">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="fc36b-491">**IP 配置**：显示网络连接的 IP 地址和其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="fc36b-491">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="fc36b-492">虚拟输入</span><span class="sxs-lookup"><span data-stu-id="fc36b-492">Virtual Input</span></span>

<span data-ttu-id="fc36b-493">![Microsoft HoloLens 上 Windows 设备门户中的“虚拟输入”页](images/using-windows-portal-img-18.png)</span><span class="sxs-lookup"><span data-stu-id="fc36b-493">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-18.png)</span></span><br>
<span data-ttu-id="fc36b-494">*Microsoft HoloLens 上 Windows 设备门户中的“虚拟输入”页*</span><span class="sxs-lookup"><span data-stu-id="fc36b-494">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="fc36b-495">将键盘输入从远程计算机发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fc36b-495">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="fc36b-496">单击或敲击 **虚拟键盘** 下的区域可将键击发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="fc36b-496">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="fc36b-497">在“输入文本”文本框中键入内容，然后单击或敲击“发送”可将键击发送到活动应用。 </span><span class="sxs-lookup"><span data-stu-id="fc36b-497">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="fc36b-498">设备门户 REST API</span><span class="sxs-lookup"><span data-stu-id="fc36b-498">Device Portal REST APIs</span></span>

<span data-ttu-id="fc36b-499">设备门户中的所有内容都是基于 [REST API](device-portal-api-reference.md) 创建的，你可以选择性地使用这些 API 来访问数据和以编程方式控制设备。</span><span class="sxs-lookup"><span data-stu-id="fc36b-499">Everything in the device portal is built on top of [REST APIs](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="fc36b-500">故障排除</span><span class="sxs-lookup"><span data-stu-id="fc36b-500">Troubleshooting</span></span>

### <a name="how-to-fix-the-its-lonely-here-message"></a><span data-ttu-id="fc36b-501">如何消除“此处没有其他内容”消息</span><span class="sxs-lookup"><span data-stu-id="fc36b-501">How to fix the "It's lonely here" message</span></span>

> [!NOTE]
> <span data-ttu-id="fc36b-502">如果页面在 HoloLens（第 1 代）上使用之前先在 HoloLens 2 上使用，那么在从 HoloLens 2 转到 HoloLens（第 1 代）后，可能导致只有这些页面，不显示其他任何内容。</span><span class="sxs-lookup"><span data-stu-id="fc36b-502">Going from a HoloLens 2 to HoloLens (1st gen) may cause the pages to become lonely if used on the HoloLens 2 prior to use on the HoloLens (1st gen).</span></span>

![“设备门户”页面中的“此处没有其他内容”消息](images/using-windows-portal-img-19.png)

1. <span data-ttu-id="fc36b-504">从右上角菜单中选择“重置布局”：</span><span class="sxs-lookup"><span data-stu-id="fc36b-504">Select **Reset layout** from the top-left Menu:</span></span>

![从设备门户菜单中选择“重置布局”](images/using-windows-portal-img-20.png)

2. <span data-ttu-id="fc36b-506">在“重置工作区”标题下单击“重置布局” 。</span><span class="sxs-lookup"><span data-stu-id="fc36b-506">Click **Reset layout** under the **Reset workspace** heading.</span></span> <span data-ttu-id="fc36b-507">门户页面将自动刷新并显示你的内容。</span><span class="sxs-lookup"><span data-stu-id="fc36b-507">The portal page will automatically refresh and display your content.</span></span>

![从“重置工作区”页面中选择“重置布局”](images/using-windows-portal-img-21.png)
