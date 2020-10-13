---
title: 使用 Windows 设备门户
description: 使用适用于 HoloLens 的 Windows 设备门户可以通过 Wi-Fi 或 USB 远程配置和管理设备。 Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。 设备门户包含许多工具，可帮助你管理 HoloLens 以及调试和优化应用。
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Windows 设备门户，HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 398b9ee312c8d49e3468980e5e2c1be556c17162
ms.sourcegitcommit: 252b52f7541a6e15aa33322286855af8a3924fc1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862994"
---
# <a name="using-the-windows-device-portal"></a><span data-ttu-id="d1aa7-106">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="d1aa7-106">Using the Windows Device Portal</span></span>

<table>
<tr>
<th><span data-ttu-id="d1aa7-107">功能</span><span class="sxs-lookup"><span data-stu-id="d1aa7-107">Feature</span></span></th><th style="width:150px"><span data-ttu-id="d1aa7-108"><a href="../../hololens-hardware-details.md">HoloLens（第一代）</a></span><span class="sxs-lookup"><span data-stu-id="d1aa7-108"><a href="../../hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="d1aa7-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d1aa7-109">HoloLens 2</span></span></th><th style="width:150px">
</tr><tr>
<td> <span data-ttu-id="d1aa7-110">Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="d1aa7-110">Windows Device Portal</span></span></td><td style="text-align: center;"> <span data-ttu-id="d1aa7-111">✔️</span><span class="sxs-lookup"><span data-stu-id="d1aa7-111">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d1aa7-112">✔️</span><span class="sxs-lookup"><span data-stu-id="d1aa7-112">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

<span data-ttu-id="d1aa7-113">使用适用于 HoloLens 的 Windows 设备门户可以通过 Wi-Fi 或 USB 远程配置和管理设备。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-113">The Windows Device Portal for HoloLens lets you configure and manage your device remotely over Wi-Fi or USB.</span></span> <span data-ttu-id="d1aa7-114">Device Portal 是 HoloLens 上的 Web 服务器，你可以从电脑上的 Web 浏览器连接到它。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-114">The Device Portal is a web server on your HoloLens that you can connect to from a web browser on your PC.</span></span> <span data-ttu-id="d1aa7-115">设备门户包含许多工具，可帮助你管理 HoloLens 以及调试和优化应用。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-115">The Device Portal includes many tools that will help you manage your HoloLens and debug and optimize your apps.</span></span>

<span data-ttu-id="d1aa7-116">本文档专门介绍适用于 HoloLens 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-116">This documentation is specifically about the Windows Device Portal for HoloLens.</span></span> <span data-ttu-id="d1aa7-117">若要使用适用于桌面（包括 Windows Mixed Reality）的 Windows 设备门户，请参阅 [Windows 设备门户概述](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-117">To use the Windows Device portal for desktop (including for Windows Mixed Reality), see [Windows Device Portal overview](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

## <a name="setting-up-hololens-to-use-windows-device-portal"></a><span data-ttu-id="d1aa7-118">将 HoloLens 设置为使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="d1aa7-118">Setting up HoloLens to use Windows Device Portal</span></span>

1. <span data-ttu-id="d1aa7-119">打开 HoloLens 的电源，然后戴上设备。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-119">Power on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="d1aa7-120">针对 HoloLens2 执行[开始手势](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)，或者在 HoloLens（第一代）上执行[开花手势](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)，以启动主菜单。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-120">Perform the [Start gesture](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) for HoloLens2 or [Bloom](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (1st Gen) to launch the main menu.</span></span> 
3. <span data-ttu-id="d1aa7-121">凝视“设置”磁贴，然后在 HoloLens（第一代）上执行[隔空敲击](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)手势，或者在 HoloLens 2 上通过[触摸或手部射线](https://docs.microsoft.com/hololens/hololens2-basic-usage)选择该磁贴。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-121">Gaze at the **Settings** tile and perform the [air-tap](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) gesture on HoloLens (1st Gen) or select it on HoloLens 2 by [touching it or using a Hand ray](https://docs.microsoft.com/hololens/hololens2-basic-usage).</span></span> 
4. <span data-ttu-id="d1aa7-122">选择“更新”菜单项。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-122">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="d1aa7-123">选择“面向开发人员”菜单项。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-123">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="d1aa7-124">启用“开发人员模式”。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-124">Enable **Developer Mode**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1aa7-125">如果你使用的是多用户而不是管理员，则进入开发人员模式的功能可能灰显。请确保你是[设备上的管理员](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-125">If you're in multi-user and not an admin, the ability to enter Developer Mode may be grayed out. Please ensure that you are an **[admin on the device](https://docs.microsoft.com/hololens/security-adminless-os)**.</span></span>

7. <span data-ttu-id="d1aa7-126">[向下滚动](../../design/gaze-and-commit.md#composite-gestures)并启用“设备门户”。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-126">[Scroll down](../../design/gaze-and-commit.md#composite-gestures) and enable **Device Portal**.</span></span>
8. <span data-ttu-id="d1aa7-127">如果要设置 Windows 设备门户以便可以通过 USB 或 Wi-Fi 将应用部署到此 HoloLens，请单击“配对”以[生成配对 PIN](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-127">If you are setting up Windows Device Portal so you can deploy apps to this HoloLens over USB or Wi-Fi, click **Pair** to [generate a pairing PIN](using-visual-studio.md).</span></span> <span data-ttu-id="d1aa7-128">在首次部署期间，请在“PIN”弹出窗口中保持打开“设置”应用，直到在 Visual Studio 中输入了 PIN 才将它关闭。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-128">Leave the Settings app at the PIN popup until you enter the PIN into Visual Studio during your first deployment.</span></span>

![在 Windows Holographic 的“设置”应用中启用开发人员模式](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a><span data-ttu-id="d1aa7-130">通过 Wi-Fi 进行连接</span><span class="sxs-lookup"><span data-stu-id="d1aa7-130">Connecting over Wi-Fi</span></span>

1. <span data-ttu-id="d1aa7-131">[将 HoloLens 连接到 Wi-Fi](../../connecting-to-wi-fi-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-131">[Connect your HoloLens to Wi-Fi](../../connecting-to-wi-fi-on-hololens.md).</span></span>
2. <span data-ttu-id="d1aa7-132">通过以下任一方法查找设备的 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-132">Look up your device's IP address by either:</span></span>
   * <span data-ttu-id="d1aa7-133">依次转到“设置”>“网络和 Internet”>“Wi-Fi”>“高级选项”。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-133">Going to **Settings > Network & Internet > Wi-Fi > Advanced Options**.</span></span>
   * <span data-ttu-id="d1aa7-134">转到“设置”>“网络和 Internet”，然后选择“硬件属性” 。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-134">Going to **Settings > Network & Internet** and selecting **Hardware properties**.</span></span>

![HoloLens 2 设置](images/using-windows-portal-img-02.jpg)

3. <span data-ttu-id="d1aa7-136">在电脑上的 Web 浏览器中，转到 https://<HOLOLENS IP 地址></span><span class="sxs-lookup"><span data-stu-id="d1aa7-136">From a web browser on your PC, go to https://<YOUR_HOLOLENS_IP_ADDRESS></span></span>
   * <span data-ttu-id="d1aa7-137">浏览器中将显示以下消息：“此网站的安全证书有问题。”</span><span class="sxs-lookup"><span data-stu-id="d1aa7-137">The browser will display the following message: "There's a problem with this website's security certificate".</span></span> <span data-ttu-id="d1aa7-138">由于颁发给 Device Portal 的证书是测试证书，因此会显示上述消息。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-138">This happens because the certificate which is issued to the Device Portal is a test certificate.</span></span> <span data-ttu-id="d1aa7-139">你可以暂时忽略此证书错误并继续。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-139">You can ignore this certificate error for now and proceed.</span></span>

## <a name="connecting-over-usb"></a><span data-ttu-id="d1aa7-140">通过 USB 进行连接</span><span class="sxs-lookup"><span data-stu-id="d1aa7-140">Connecting over USB</span></span>

1. <span data-ttu-id="d1aa7-141">[安装所需的工具](../install-the-tools.md)，确保电脑上安装了带有 Windows 10 开发人员工具的 Visual Studio，以启用 USB 连接。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-141">[Install the tools](../install-the-tools.md) to make sure you have Visual Studio with the Windows 10 developer tools installed on your PC to enable USB connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1aa7-142">如果在 USB 连接方面遇到问题，请再次检查 USB 设备连接可选组件是否已作为 [Visual Studio工具包](../install-the-tools.md#installation-checklist)的一部分安装。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-142">If you're having issues with USB connectivity double check that the USB Device Connectivity optional component is installed as part of your **[Visual Studio tool package](../install-the-tools.md#installation-checklist)**.</span></span>

2. <span data-ttu-id="d1aa7-143">使用适用于 HoloLens（第一代）的 micro-USB 数据线或适用于 HoloLens 2 的 USB-C 数据线将 HoloLens 连接到电脑。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-143">Connect your HoloLens to your PC with a micro-USB cable for HoloLens (1st Gen) or USB-C for HoloLens 2.</span></span>
3. <span data-ttu-id="d1aa7-144">在电脑上的 Web 浏览器中，转到 [https://127.0.0.1:10080](https://127.0.0.1:10080)。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-144">From a web browser on your PC, go to [https://127.0.0.1:10080](https://127.0.0.1:10080).</span></span>

### <a name="moving-files-over-usb"></a><span data-ttu-id="d1aa7-145">通过 USB 移动文件</span><span class="sxs-lookup"><span data-stu-id="d1aa7-145">Moving files over USB</span></span>

<span data-ttu-id="d1aa7-146">无需进行任何其他设置，即可将文件从电脑移动到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-146">You can move files from your PC to your HoloLens without any additional setup.</span></span>
1. <span data-ttu-id="d1aa7-147">使用 USB 线将电脑连接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="d1aa7-147">Connect your PC to your HoloLens with a USB cord</span></span>
2. <span data-ttu-id="d1aa7-148">将文件拖动到桌面上的“PC\\[Your_HoloLens_Device_Name]\Internal Storage”中</span><span class="sxs-lookup"><span data-stu-id="d1aa7-148">Drag your files into **PC\\[Your_HoloLens_Device_Name]\Internal Storage** on your desktop</span></span>
3. <span data-ttu-id="d1aa7-149">打开“开始”菜单，然后在 HoloLens 上选择“所有应用”>“文件资源管理器” </span><span class="sxs-lookup"><span data-stu-id="d1aa7-149">Open the **Start Menu** and select **All apps > File Explorer** on your HoloLens</span></span>

> [!NOTE]
> <span data-ttu-id="d1aa7-150">可能需要选择面板左侧的“此设备”，才能从“最近使用”进行导航以查找文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-150">You may need to select **This device** on the left side of the panel to navigate away from "Recently used" to locate your files.</span></span> 

## <a name="connecting-to-an-emulator"></a><span data-ttu-id="d1aa7-151">连接到仿真器</span><span class="sxs-lookup"><span data-stu-id="d1aa7-151">Connecting to an emulator</span></span>

<span data-ttu-id="d1aa7-152">也可以将 Device Portal 与仿真器结合使用。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-152">You can also use the Device Portal with your emulator.</span></span> <span data-ttu-id="d1aa7-153">若要连接到设备门户，请使用[工具栏](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-153">To connect to the Device Portal, use the [toolbar](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="d1aa7-154">单击此图标：![“打开设备门户”图标](images/emulator-deviceportal.png) **打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-154">Click on this icon: ![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

## <a name="creating-a-username-and-password"></a><span data-ttu-id="d1aa7-155">创建用户名和密码</span><span class="sxs-lookup"><span data-stu-id="d1aa7-155">Creating a Username and Password</span></span>

<span data-ttu-id="d1aa7-156">![设置对 Windows 设备门户的访问](images/windows-device-portal-credentials-reset-page-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-156">![Set up access to Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)</span></span><br>
<span data-ttu-id="d1aa7-157">*设置对 Windows 设备门户的访问*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-157">*Set up access to Windows Device Portal*</span></span>

<span data-ttu-id="d1aa7-158">首次连接到 HoloLens 上的 Device Portal 时，需要创建用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-158">The first time you connect to the Device Portal on your HoloLens, you will need to create a username and password.</span></span>
1. <span data-ttu-id="d1aa7-159">在电脑上的 Web 浏览器中，输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-159">In a web browser on your PC, enter the IP address of the HoloLens.</span></span> <span data-ttu-id="d1aa7-160">将打开“设置访问”页面。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-160">The Set up access page opens.</span></span>
2. <span data-ttu-id="d1aa7-161">单击或敲击“请求 PIN”，然后查看 HoloLens 屏幕以获取生成的 PIN。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-161">Click or tap **Request pin** and look at the HoloLens display to get the generated PIN.</span></span>
3. <span data-ttu-id="d1aa7-162">在“设备上显示的 PIN”文本框中输入该 PIN。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-162">Enter the PIN in the **PIN displayed on your device** textbox.</span></span>
4. <span data-ttu-id="d1aa7-163">输入将用于连接到 Device Portal 的用户名。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-163">Enter the user name you will use to connect to the Device Portal.</span></span> <span data-ttu-id="d1aa7-164">无需使用 Microsoft 帐户 (MSA) 名称或域名作为用户名。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-164">It doesn't need to be a Microsoft Account (MSA) name or a domain name.</span></span>
5. <span data-ttu-id="d1aa7-165">输入密码并进行确认。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-165">Enter a password and confirm it.</span></span> <span data-ttu-id="d1aa7-166">密码长度必须至少为七个字符。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-166">The password must be at least seven characters in length.</span></span> <span data-ttu-id="d1aa7-167">无需使用 MSA 密码或域密码作为密码。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-167">It doesn't need to be an MSA or domain password.</span></span>
6. <span data-ttu-id="d1aa7-168">单击“配对”以连接到 HoloLens 上的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-168">Click **Pair** to connect to Windows Device Portal on the HoloLens.</span></span>

<span data-ttu-id="d1aa7-169">今后如果你想要更改此用户名和密码，可以导航到 https://<HOLOLENS IP 地址>/devicepair.htm 来访问设备安全性页，然后重复上述过程。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-169">If you wish to change this username or password at any time, you can repeat this process by visiting the device security page by  navigating to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm.</span></span>

## <a name="security-certificate"></a><span data-ttu-id="d1aa7-170">安全证书</span><span class="sxs-lookup"><span data-stu-id="d1aa7-170">Security certificate</span></span>

<span data-ttu-id="d1aa7-171">如果在浏览器中看到“证书错误”，可以通过创建与该设备的信任关系来修复该错误。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-171">If you see a "certificate error" in your browser, you can fix it by creating a trust relationship with the device.</span></span>

<span data-ttu-id="d1aa7-172">每个 HoloLens 会生成唯一的自签名证书以供其 SSL 连接使用。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-172">Each HoloLens generates a unique self-signed certificate for its SSL connection.</span></span> <span data-ttu-id="d1aa7-173">默认情况下，此证书不受电脑的 Web 浏览器信任，因此你可能会看到“证书错误”。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-173">By default, this certificate is not trusted by your PC's web browser and you may get a "certificate error".</span></span> <span data-ttu-id="d1aa7-174">通过从你的 HoloLens 下载此证书（借助 USB 或信任的 WLAN 网络）并在你的电脑上信任该证书，可以安全地连接到设备。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-174">By downloading this certificate from your HoloLens (over USB or a Wi-Fi network you trust) and trusting it on your PC, you can securely connect to your device.</span></span>
1. <span data-ttu-id="d1aa7-175">**确保在安全网络（USB 或信任的 Wi-Fi 网络）中操作。**</span><span class="sxs-lookup"><span data-stu-id="d1aa7-175">**Make sure you are on a secure network (USB or a Wi-Fi network you trust).**</span></span>
2. <span data-ttu-id="d1aa7-176">从设备门户上的“安全性”页下载此设备的证书。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-176">Download this device's certificate from the "Security" page on the Device Portal.</span></span>
   * <span data-ttu-id="d1aa7-177">导航到 https://<HOLOLENS IP 地址>/devicepair.htm</span><span class="sxs-lookup"><span data-stu-id="d1aa7-177">Navigate to: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm</span></span>
   * <span data-ttu-id="d1aa7-178">打开“系统”>“首选项”对应的节点。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-178">Open the node for System > Preferences.</span></span> 
   * <span data-ttu-id="d1aa7-179">向下滚动到“设备安全性”，然后单击“下载此设备的证书”按钮。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-179">Scroll down to Device Security, click the "Download this device's certificate" button.</span></span>
3. <span data-ttu-id="d1aa7-180">在电脑上安装“受信任的根证书颁发机构”存储中的证书。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-180">Install the certificate in the "Trusted Root Certification Authorities" store on your PC.</span></span>
   * <span data-ttu-id="d1aa7-181">在 Windows 菜单中键入：管理计算机证书并启动小程序。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-181">From the Windows menu, type: Manage Computer Certificates and start the applet.</span></span>
   * <span data-ttu-id="d1aa7-182">展开“受信任的根证书颁发机构”文件夹。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-182">Expand the **Trusted Root Certification Authority** folder.</span></span>
   * <span data-ttu-id="d1aa7-183">单击“证书”文件夹。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-183">Click the **Certificates** folder.</span></span>
   * <span data-ttu-id="d1aa7-184">在“操作”菜单中选择：“所有任务”>“导入...”</span><span class="sxs-lookup"><span data-stu-id="d1aa7-184">From the Action menu, select: All Tasks > Import...</span></span>
   * <span data-ttu-id="d1aa7-185">使用从 Device Portal 下载的证书文件，完成“证书导入向导”。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-185">Complete the Certificate Import Wizard, using the certificate file you downloaded from the Device Portal.</span></span>
4. <span data-ttu-id="d1aa7-186">重新启动浏览器。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-186">Restart the browser.</span></span>

>[!NOTE]
> <span data-ttu-id="d1aa7-187">此证书仅在该设备上受信任，如果刷写了设备，用户必须再次执行此过程。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-187">This certificate will only be trusted for the device and the user will have to go through the process again if the device is flashed.</span></span>


## <a name="device-portal-pages"></a><span data-ttu-id="d1aa7-188">Device Portal 页面</span><span class="sxs-lookup"><span data-stu-id="d1aa7-188">Device Portal Pages</span></span>

### <a name="home"></a><span data-ttu-id="d1aa7-189">主页</span><span class="sxs-lookup"><span data-stu-id="d1aa7-189">Home</span></span>

<span data-ttu-id="d1aa7-190">![Microsoft HoloLens 上的 Windows 设备门户主页](images/using-windows-portal-img-04.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-190">![Windows Device Portal home page on Microsoft HoloLens](images/using-windows-portal-img-04.png)</span></span><br>
<span data-ttu-id="d1aa7-191">*Microsoft HoloLens 上的 Windows 设备门户主页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-191">*Windows Device Portal home page on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-192">Device Portal 会话从主页开始。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-192">Your Device Portal session starts at the Home page.</span></span> <span data-ttu-id="d1aa7-193">可从主页的左侧导航栏访问其他页面。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-193">Access other pages from the navigation bar along the left side of the home page.</span></span>

<span data-ttu-id="d1aa7-194">主页顶部的工具栏提供对常用状态和功能的访问。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-194">The toolbar at the top of the page provides access to commonly used status and features.</span></span>
* <span data-ttu-id="d1aa7-195">**联机**：指示设备是否已连接到 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-195">**Online**: Indicates whether the device is connected to Wi-Fi.</span></span>
* <span data-ttu-id="d1aa7-196">**关机**：关闭设备。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-196">**Shutdown**: Turns off the device.</span></span>
* <span data-ttu-id="d1aa7-197">**重启**：关闭再打开设备的电源。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-197">**Restart**: Cycles power on the device.</span></span>
* <span data-ttu-id="d1aa7-198">**安全**：打开“设备安全性”页。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-198">**Security**: Opens the Device Security page.</span></span>
* <span data-ttu-id="d1aa7-199">**冷**：指示设备的温度。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-199">**Cool**: Indicates the temperature of the device.</span></span>
* <span data-ttu-id="d1aa7-200">**交流电源**：指示设备是否已接上电源并正在充电。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-200">**A/C**: Indicates whether the device is plugged in and charging.</span></span>
* <span data-ttu-id="d1aa7-201">**帮助**：打开 REST 接口文档页。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-201">**Help**: Opens the REST interface documentation page.</span></span>

<span data-ttu-id="d1aa7-202">主页将显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-202">The home page shows the following info:</span></span>
* <span data-ttu-id="d1aa7-203">**设备状态：** 监视设备的运行状况并报告严重错误。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-203">**Device Status:** monitors the health of your device and reports critical errors.</span></span>
* <span data-ttu-id="d1aa7-204">**Windows 信息：** 显示 HoloLens 的名称，以及当前安装的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-204">**Windows information:** shows the name of the HoloLens and the currently installed version of Windows.</span></span>
* <span data-ttu-id="d1aa7-205">**首选项**部分包含以下设置：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-205">**Preferences** section contains the following settings:</span></span>
   * <span data-ttu-id="d1aa7-206">**IPD**：设置瞳孔间距 (IPD)，它是在用户直视前方时两个瞳孔中心之间的距离，以毫米为单位。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-206">**IPD**: Sets the interpupillary distance (IPD), which is the distance, in millimeters, between the center of the user's pupils when looking straight ahead.</span></span> <span data-ttu-id="d1aa7-207">该设置将立即生效。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-207">The setting takes effect immediately.</span></span> <span data-ttu-id="d1aa7-208">在设置你的设备时，会自动计算该默认值。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-208">The default value was calculated automatically when you set up your device.</span></span>
   * <span data-ttu-id="d1aa7-209">**设备名称**：为 HoloLens 指定一个名称。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-209">**Device name**: Assign a name to the HoloLens.</span></span> <span data-ttu-id="d1aa7-210">更改此值后，必须重新启动设备才能使该值生效。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-210">You must reboot the device after changing this value for it to take effect.</span></span> <span data-ttu-id="d1aa7-211">单击“保存”后，对话框将询问是要立即重新启动还是稍后重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-211">After clicking **Save**, a dialog will ask if you want to reboot the device immediately or reboot later.</span></span>
   * <span data-ttu-id="d1aa7-212">**睡眠设置**：设置当设备已接上电源并使用电池时进入睡眠状态之前要等待的时长。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-212">**Sleep settings**: Sets the length of time to wait before the device goes to sleep when it's plugged in and when it's on battery.</span></span>

### <a name="3d-view"></a><span data-ttu-id="d1aa7-213">3D 视图</span><span class="sxs-lookup"><span data-stu-id="d1aa7-213">3D View</span></span>

<span data-ttu-id="d1aa7-214">![Microsoft HoloLens 上 Windows 设备门户中的“3D 视图”页](images/using-windows-portal-img-05.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-214">![3D View page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-05.png)</span></span><br>
<span data-ttu-id="d1aa7-215">*Microsoft HoloLens 上 Windows 设备门户中的“3D 视图”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-215">*3D View page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-216">使用“3D 视图”页面可查看 HoloLens 感知周围环境的方式。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-216">Use the 3D View page to see how HoloLens interprets your surroundings.</span></span> <span data-ttu-id="d1aa7-217">使用鼠标即可导览该视图：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-217">Navigate the view by using the mouse:</span></span>
* <span data-ttu-id="d1aa7-218">旋转：单击左键并移动鼠标；</span><span class="sxs-lookup"><span data-stu-id="d1aa7-218">Rotate: left click + mouse;</span></span>
* <span data-ttu-id="d1aa7-219">平移：单击右键并移动鼠标；</span><span class="sxs-lookup"><span data-stu-id="d1aa7-219">Pan: right click + mouse;</span></span>
* <span data-ttu-id="d1aa7-220">缩放：滑动鼠标滚轮。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-220">Zoom: mouse scroll.</span></span>
* <span data-ttu-id="d1aa7-221">**跟踪选项**</span><span class="sxs-lookup"><span data-stu-id="d1aa7-221">**Tracking options**</span></span>
   * <span data-ttu-id="d1aa7-222">通过选中“强制视觉跟踪”可打开持续视觉跟踪。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-222">Turn on continuous visual tracking by checking **Force visual tracking**.</span></span> 
   * <span data-ttu-id="d1aa7-223">“暂停”会停止视觉跟踪。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-223">**Pause** stops visual tracking.</span></span>
* <span data-ttu-id="d1aa7-224">**视图选项**：设置 3D 视图中的选项：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-224">**View options**: Set options on the 3D view:</span></span>
  * <span data-ttu-id="d1aa7-225">**跟踪**：指示视觉跟踪是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-225">**Tracking**: Indicates whether visual tracking is active.</span></span>
  * <span data-ttu-id="d1aa7-226">**显示地面**：显示方格形式的地平面。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-226">**Show floor**: Displays a checkered floor plane.</span></span>
  * <span data-ttu-id="d1aa7-227">**显示锥体**：显示视锥。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-227">**Show frustum**: Displays the view frustum.</span></span>
  * <span data-ttu-id="d1aa7-228">**显示防抖动平面**：显示 HoloLens 用于稳定动作的平面。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-228">**Show stabilization plane**: Displays the plane that HoloLens uses for stabilizing motion.</span></span>
  * <span data-ttu-id="d1aa7-229">**显示网格**：显示代表周围环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-229">**Show mesh**: Displays the spatial mapping mesh that represents your surroundings.</span></span>
  * <span data-ttu-id="d1aa7-230">**显示空间定位点**：显示活动应用的空间定位点。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-230">**Show spatial anchors**: Displays spatial anchors for the active app.</span></span> <span data-ttu-id="d1aa7-231">必须单击“更新”按钮才能获取和刷新定位点。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-231">You must click the Update button to get and refresh the anchors.</span></span>
  * <span data-ttu-id="d1aa7-232">**显示细节**：显示手的位置、头部旋转四元数，以及设备原点矢量的实时变化。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-232">**Show details**: Displays hand positions, head rotation quaternions, and the device origin vector as they change in real time.</span></span>
  * <span data-ttu-id="d1aa7-233">**全屏按钮**：以全屏模式显示 3D 视图。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-233">**Full screen button**: Shows the 3D View in full screen mode.</span></span> <span data-ttu-id="d1aa7-234">按 ESC 键可退出全屏视图。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-234">Press ESC to exit full screen view.</span></span>
* <span data-ttu-id="d1aa7-235">**图面重构**：单击或敲击“更新”可显示设备的最新空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-235">**Surface reconstruction**: Click or tap **Update** to display the latest spatial mapping mesh from the device.</span></span> <span data-ttu-id="d1aa7-236">完成整个过程可能需要一些时间（但最多只需几秒钟）。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-236">A full pass may take some time to complete (up to a few seconds).</span></span> <span data-ttu-id="d1aa7-237">在 3D 视图中，网格不会自动更新，必须手动单击“更新”才能获取设备的最新网格。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-237">The mesh does not update automatically in the 3D view, and you must manually click **Update** to get the latest mesh from the device.</span></span> <span data-ttu-id="d1aa7-238">单击“保存”可在电脑上将当前的空间映射网格保存为 obj 文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-238">Click **Save** to save the current spatial mapping mesh as an obj file on your PC.</span></span>
* <span data-ttu-id="d1aa7-239">**空间定位点**：单击“更新”可显示或更新活动应用的空间定位点。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-239">**Spatial anchors**: Click Update to display or update the spatial anchors for the active app.</span></span>

### <a name="map-manager"></a><span data-ttu-id="d1aa7-240">地图管理器</span><span class="sxs-lookup"><span data-stu-id="d1aa7-240">Map Manager</span></span>

<span data-ttu-id="d1aa7-241">通过地图管理器，可跨设备共享地图，这可用于为基于位置的娱乐客户设置共享体验。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-241">Map Manager allows you to share maps across devices, which can be used to setup shared experiences for Location Based Entertainment customers.</span></span> <span data-ttu-id="d1aa7-242">该工具允许你导入和导出系统地图和定位点。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-242">The tool allows you to import and export system maps and anchors.</span></span>  

<span data-ttu-id="d1aa7-243">若要访问地图管理器，请登录设备门户并选择“混合现实”->“地图管理器”：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-243">To access the Map Manager, log into the Device Portal and select **Mixed Reality -> Map Manager**:</span></span> 

<span data-ttu-id="d1aa7-244">![Windows 设备门户中的“地图管理器”页](images/using-windows-portal-img-06.png)
Microsoft HoloLens 上 Windows 设备门户中的“地图管理器”页\*\*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-244">![Map manager page in Windows Device Portal](images/using-windows-portal-img-06.png)
*Map Manager page in Windows Device Portal on Microsoft HoloLens*</span></span>

#### <a name="exporting-and-importing-maps"></a><span data-ttu-id="d1aa7-245">导出和导入地图</span><span class="sxs-lookup"><span data-stu-id="d1aa7-245">Exporting and importing maps</span></span>

<span data-ttu-id="d1aa7-246">若要导出地图，请单击“导出系统地图和定位点”。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-246">To export maps, click **Export System Map & Anchors**.</span></span> <span data-ttu-id="d1aa7-247">此操作可能需要一段时间，所以在导出地图时，请准备好等待 30-60 秒。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-247">This could take a while so be prepared to wait for 30-60 seconds while the map is exported.</span></span> <span data-ttu-id="d1aa7-248">完成后，文件将下载到浏览器中。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-248">Once it’s complete, the file will be downloaded in your browser.</span></span>  

<span data-ttu-id="d1aa7-249">若要导入地图和定位点，请分别单击“上传地图文件”和“上传定位点文件”，然后选择已经导出的地图或定位点文件 。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-249">To import maps and anchors, click **Upload a map file** and **Upload an anchor file** respectively and select a map or anchor file that you've already exported.</span></span> <span data-ttu-id="d1aa7-250">上传的地图或定位点文件可能来自你的设备或任何其他 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-250">The uploaded map or anchor file can come from your or any other HoloLens device.</span></span> 

> [!NOTE]
> <span data-ttu-id="d1aa7-251">在 HoloLens 上，还可以导入和导出空间映射数据库。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-251">On HoloLens, it's also possible to import and export the spatial mapping data base.</span></span> <span data-ttu-id="d1aa7-252">然而，这在非 HoloLens 设备上不起作用。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-252">However, this doesn't work on non-HoloLens devices.</span></span>  


### <a name="mixed-reality-capture"></a><span data-ttu-id="d1aa7-253">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="d1aa7-253">Mixed Reality Capture</span></span>

<span data-ttu-id="d1aa7-254">![Microsoft HoloLens 上 Windows 设备门户中的“混合现实捕获”页](images/using-windows-portal-img-07.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-254">![Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-07.png)</span></span><br>
<span data-ttu-id="d1aa7-255">*Microsoft HoloLens 上 Windows 设备门户中的“混合现实捕获”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-255">*Mixed Reality Capture page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-256">使用“混合现实捕获”页面可保存 HoloLens 中的媒体流。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-256">Use the Mixed Reality Capture page to save media streams from the HoloLens.</span></span>
* <span data-ttu-id="d1aa7-257">**捕获设置**：通过检查以下设置来控制捕获的媒体流：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-257">**Capture Settings**: Control the media streams that are captured by checking the following settings:</span></span>
  * <span data-ttu-id="d1aa7-258">**全息影像**：捕获视频流中的全息内容。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-258">**Holograms**: Captures the holographic content in the video stream.</span></span> <span data-ttu-id="d1aa7-259">呈现全息图时使用的是单声道，而不是立体声。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-259">Holograms are rendered in mono, not stereo.</span></span>
  * <span data-ttu-id="d1aa7-260">**PV 相机**：捕获照片/视频相机中的视频流。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-260">**PV camera**: Captures the video stream from the photo/video camera.</span></span>
  * <span data-ttu-id="d1aa7-261">**麦克风音频**：捕获麦克风阵列中的音频。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-261">**Mic Audio**: Captures audio from the microphone array.</span></span>
  * <span data-ttu-id="d1aa7-262">**应用音频**：捕获当前正在运行的应用中的音频。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-262">**App Audio**: Captures audio from the currently running app.</span></span>
  * <span data-ttu-id="d1aa7-263">**从相机渲染**：从照片/视频相机的角度对齐捕获内容，前提是[正在运行的应用支持此功能](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)（仅限 HoloLens 2）。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-263">**Render from Camera**: Aligns the capture to be from the perspective of the photo/video camera, if [supported by the running app](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (HoloLens 2 only).</span></span>
  * <span data-ttu-id="d1aa7-264">**实时预览质量**：选择用于实时预览的屏幕分辨率、帧速率和流处理速率。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-264">**Live preview quality**: Select the screen resolution, frame rate, and streaming rate for the live preview.</span></span>
* <span data-ttu-id="d1aa7-265">**音频设置**（仅限 HoloLens 2）：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-265">**Audio Settings** (HoloLens 2 only):</span></span>
  * <span data-ttu-id="d1aa7-266">**音频媒介类别**：选择在处理麦克风时使用的类别。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-266">**Audio Media Category**: Select the category is used when processing the microphone.</span></span> <span data-ttu-id="d1aa7-267">“默认值”将包括某些环境，这些环境中的“通信”会应用背景噪音消除。 </span><span class="sxs-lookup"><span data-stu-id="d1aa7-267">**Default**  will include some of the environment whereas **Communications** applies background noise cancellation.</span></span>
  * <span data-ttu-id="d1aa7-268">**应用音频增益**：应用于应用音频音量的增益。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-268">**App Audio Gain**: The gain applied to app audio's volume.</span></span>
  * <span data-ttu-id="d1aa7-269">**麦克风音频增益**：应用于麦克风音频音量的增益。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-269">**Mic Audio Gain**: The gain applied to mic audio's volume.</span></span>
* <span data-ttu-id="d1aa7-270">**照片和视频设置**（HoloLens 2，版本 2004 或更高版本）：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-270">**Photo and Video Settings** (HoloLens 2, version 2004 or later):</span></span>
  * <span data-ttu-id="d1aa7-271">**捕获配置文件**：选择拍摄照片和视频时使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-271">**Capture Profile**: Select the profile used when taking photos and videos.</span></span> <span data-ttu-id="d1aa7-272">配置文件决定可用的分辨率和帧速率。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-272">The profile determines which resolutions and frame-rates are available.</span></span>
  * <span data-ttu-id="d1aa7-273">**照片分辨率**：拍摄照片时使用的分辨率。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-273">**Photo Resolution**: The resolution the photo will be taken with.</span></span>
  * <span data-ttu-id="d1aa7-274">**视频分辨率和帧速率**：拍摄视频时使用的分辨率和帧速率。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-274">**Video Resolution and Frame-rate**: The resolution and frame-rate the video will be taken with.</span></span>
  * <span data-ttu-id="d1aa7-275">**视频稳定缓冲区**：拍摄视频时使用的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-275">**Video Stabilization Buffer**: The buffer size used when taking a video.</span></span> <span data-ttu-id="d1aa7-276">此值越大，弥补快速移动的效果越好。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-276">The higher the value, the better it can compensate for quick movements.</span></span>
* <span data-ttu-id="d1aa7-277">单击或敲击“实时预览”按钮可显示捕获流。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-277">Click or tap the **Live preview** button to show the capture stream.</span></span> <span data-ttu-id="d1aa7-278">“停止实时预览”会停止捕获流。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-278">**Stop live preview** stops the capture stream.</span></span>
* <span data-ttu-id="d1aa7-279">单击或敲击“录制”可使用指定的设置开始录制混合现实流。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-279">Click or tap **Record** to start recording the mixed-reality stream, using the specified settings.</span></span> <span data-ttu-id="d1aa7-280">“停止录制”会结束录制，并保存录制内容。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-280">**Stop recording** ends the recording and saves it.</span></span>
* <span data-ttu-id="d1aa7-281">单击或敲击“拍摄照片”可从捕获流中捕获静止图像。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-281">Click or tap **Take photo** to take a still image from the capture stream.</span></span>
* <span data-ttu-id="d1aa7-282">单击或点击“还原默认设置”，可还原音频、照片和视频设置的默认设置。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-282">Click or tap **Restore Default Settings** to restore the default settings for audio, photo, and video settings.</span></span>
* <span data-ttu-id="d1aa7-283">**视频和照片**：显示在设备上捕获的视频和照片列表。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-283">**Videos and photos**: Shows a list of video and photo captures taken on the device.</span></span>

<span data-ttu-id="d1aa7-284">此页面上的所有设置都适用于使用 Windows 设备门户完成的捕获，但一些设置还适用于系统 MRC（“开始”菜单、硬件按钮、全局语音命令、Miracast）和自定义 MRC 记录器。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-284">All settings on this page apply to captures taken using Windows Device Portal, but some additionally apply to System MRC (start menu, hardware buttons, global voice commands, Miracast) and to custom MRC Recorders.</span></span>

|  <span data-ttu-id="d1aa7-285">设置</span><span class="sxs-lookup"><span data-stu-id="d1aa7-285">Setting</span></span>  |  <span data-ttu-id="d1aa7-286">适用于系统 MRC</span><span class="sxs-lookup"><span data-stu-id="d1aa7-286">Applies to System MRC</span></span>  |  <span data-ttu-id="d1aa7-287">适用于自定义 MRC 记录器</span><span class="sxs-lookup"><span data-stu-id="d1aa7-287">Applies to Custom MRC Recorders</span></span> |
|----------|----------|----------|
|  <span data-ttu-id="d1aa7-288">全息影像</span><span class="sxs-lookup"><span data-stu-id="d1aa7-288">Holograms</span></span>  |  <span data-ttu-id="d1aa7-289">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-289">No</span></span>  |  <span data-ttu-id="d1aa7-290">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-290">No</span></span> |
|  <span data-ttu-id="d1aa7-291">PV 摄像头</span><span class="sxs-lookup"><span data-stu-id="d1aa7-291">PV camera</span></span>  |  <span data-ttu-id="d1aa7-292">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-292">No</span></span>  |  <span data-ttu-id="d1aa7-293">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-293">No</span></span> |
|  <span data-ttu-id="d1aa7-294">麦克风音频</span><span class="sxs-lookup"><span data-stu-id="d1aa7-294">Mic Audio</span></span>  |  <span data-ttu-id="d1aa7-295">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-295">No</span></span>  |  <span data-ttu-id="d1aa7-296">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-296">No</span></span> |
|  <span data-ttu-id="d1aa7-297">应用音频</span><span class="sxs-lookup"><span data-stu-id="d1aa7-297">App Audio</span></span>  |  <span data-ttu-id="d1aa7-298">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-298">No</span></span>  |  <span data-ttu-id="d1aa7-299">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-299">No</span></span> |
|  <span data-ttu-id="d1aa7-300">从摄像头渲染</span><span class="sxs-lookup"><span data-stu-id="d1aa7-300">Render from Camera</span></span>  |  <span data-ttu-id="d1aa7-301">是</span><span class="sxs-lookup"><span data-stu-id="d1aa7-301">Yes</span></span>    |  <span data-ttu-id="d1aa7-302">是（可以重写）</span><span class="sxs-lookup"><span data-stu-id="d1aa7-302">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="d1aa7-303">实时预览质量</span><span class="sxs-lookup"><span data-stu-id="d1aa7-303">Live preview quality</span></span>  |  <span data-ttu-id="d1aa7-304">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-304">No</span></span>  |  <span data-ttu-id="d1aa7-305">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-305">No</span></span> |
|  <span data-ttu-id="d1aa7-306">音频媒介类别</span><span class="sxs-lookup"><span data-stu-id="d1aa7-306">Audio Media Category</span></span>  |  <span data-ttu-id="d1aa7-307">是</span><span class="sxs-lookup"><span data-stu-id="d1aa7-307">Yes</span></span>  |  <span data-ttu-id="d1aa7-308">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-308">No</span></span> |
|  <span data-ttu-id="d1aa7-309">应用音频增益</span><span class="sxs-lookup"><span data-stu-id="d1aa7-309">App Audio Gain</span></span>  |  <span data-ttu-id="d1aa7-310">是</span><span class="sxs-lookup"><span data-stu-id="d1aa7-310">Yes</span></span>  |  <span data-ttu-id="d1aa7-311">是（可以重写）</span><span class="sxs-lookup"><span data-stu-id="d1aa7-311">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="d1aa7-312">麦克风音频增益</span><span class="sxs-lookup"><span data-stu-id="d1aa7-312">Mic Audio Gain</span></span>  |  <span data-ttu-id="d1aa7-313">是</span><span class="sxs-lookup"><span data-stu-id="d1aa7-313">Yes</span></span>  |  <span data-ttu-id="d1aa7-314">是（可以重写）</span><span class="sxs-lookup"><span data-stu-id="d1aa7-314">Yes (can be overridden)</span></span> |
|  <span data-ttu-id="d1aa7-315">捕获配置文件</span><span class="sxs-lookup"><span data-stu-id="d1aa7-315">Capture Profile</span></span>  |  <span data-ttu-id="d1aa7-316">是</span><span class="sxs-lookup"><span data-stu-id="d1aa7-316">Yes</span></span>  |  <span data-ttu-id="d1aa7-317">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-317">No</span></span> |
|  <span data-ttu-id="d1aa7-318">照片分辨率</span><span class="sxs-lookup"><span data-stu-id="d1aa7-318">Photo Resolution</span></span>  |  <span data-ttu-id="d1aa7-319">是</span><span class="sxs-lookup"><span data-stu-id="d1aa7-319">Yes</span></span>  |  <span data-ttu-id="d1aa7-320">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-320">No</span></span> |
|  <span data-ttu-id="d1aa7-321">视频分辨率和帧速率</span><span class="sxs-lookup"><span data-stu-id="d1aa7-321">Video Resolution and Frame-rate</span></span>  |  <span data-ttu-id="d1aa7-322">是</span><span class="sxs-lookup"><span data-stu-id="d1aa7-322">Yes</span></span>  |  <span data-ttu-id="d1aa7-323">否</span><span class="sxs-lookup"><span data-stu-id="d1aa7-323">No</span></span> |
|  <span data-ttu-id="d1aa7-324">视频稳定缓冲区</span><span class="sxs-lookup"><span data-stu-id="d1aa7-324">Video Stabilization Buffer</span></span>  |  <span data-ttu-id="d1aa7-325">是</span><span class="sxs-lookup"><span data-stu-id="d1aa7-325">Yes</span></span>  |  <span data-ttu-id="d1aa7-326">是（可以重写）</span><span class="sxs-lookup"><span data-stu-id="d1aa7-326">Yes (can be overridden)</span></span> |

> [!NOTE]
> <span data-ttu-id="d1aa7-327">[同步 MRC 存在限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-327">There are [limitations to simultaneous MRC](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):</span></span>
> * <span data-ttu-id="d1aa7-328">如果当 Windows 设备门户正在录制视频时某个应用尝试访问照片/视频相机，则视频录制将会停止。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-328">If an app tries to access the photo/video camera while Windows Device Portal is recording a video, the video recording will stop.</span></span>
>   * <span data-ttu-id="d1aa7-329">如果应用以 SharedReadOnly 模式访问照片/视频相机，HoloLens 2 将不会停止视频录制。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-329">HoloLens 2 will not stop recording video if the app accesses the photo/video camera with SharedReadOnly mode.</span></span>
> * <span data-ttu-id="d1aa7-330">如果应用正在使用照片/视频相机，则 Windows 设备门户可以拍摄照片或录制视频。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-330">If an app is actively using the photo/video camera, Windows Device Portal is able to take a photo or record a video.</span></span>
> * <span data-ttu-id="d1aa7-331">实时传送视频流：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-331">Live streaming:</span></span>
>   * <span data-ttu-id="d1aa7-332">从 Windows 设备门户实时传送视频流时，HoloLens（第一代）会阻止应用访问照片/视频相机。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-332">HoloLens (1st gen) prevents an app from accessing the photo/video camera while live streaming from Windows Device Portal.</span></span>
>   * <span data-ttu-id="d1aa7-333">如果应用正在使用照片/视频相机，则 HoloLens（第一代）将无法实时传送视频流。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-333">HoloLens (1st gen) will fail to live stream if an app is actively using the photo/video camera.</span></span>
>   * <span data-ttu-id="d1aa7-334">当应用尝试以 ExclusiveControl 模式访问照片/视频相机时，HoloLens 2 会自动停止实时传送视频流。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-334">HoloLens 2 automatically stops live streaming when an app tries to access the photo/video camera in ExclusiveControl mode.</span></span>
>   * <span data-ttu-id="d1aa7-335">当应用正在使用 PV 相机时，HoloLens 2 可以启动实时传送视频流。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-335">HoloLens 2 is able to start a live stream while an app is actively using the PV camera.</span></span>

### <a name="performance-tracing"></a><span data-ttu-id="d1aa7-336">性能跟踪</span><span class="sxs-lookup"><span data-stu-id="d1aa7-336">Performance Tracing</span></span>

<span data-ttu-id="d1aa7-337">![Microsoft HoloLens 上 Windows 设备门户中的“性能跟踪”页](images/using-windows-portal-img-08.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-337">![Performance Tracing page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-08.png)</span></span><br>
<span data-ttu-id="d1aa7-338">*Microsoft HoloLens 上 Windows 设备门户中的“性能跟踪”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-338">*Performance Tracing page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-339">从 HoloLens 中捕获 [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) 跟踪。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-339">Capture [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) traces from your HoloLens.</span></span>
* <span data-ttu-id="d1aa7-340">**可用配置文件**：从下拉列表中选择 WPR 配置文件，然后单击或敲击“开始”以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-340">**Available profiles**: Select the WPR profile from the dropdown, and click or tap **Start** to start tracing.</span></span>
* <span data-ttu-id="d1aa7-341">**自定义配置文件**：单击或敲击“浏览”以从电脑中选择 WPR 配置文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-341">**Custom profiles**: Click or tap **Browse** to choose a WPR profile from your PC.</span></span> <span data-ttu-id="d1aa7-342">单击或敲击“上传并启动”以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-342">Click or tap **Upload and start** to start tracing.</span></span>

<span data-ttu-id="d1aa7-343">若要停止跟踪，请单击“停止”链接。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-343">To stop the trace, click the stop link.</span></span> <span data-ttu-id="d1aa7-344">请保持打开此页，直到跟踪文件完成下载。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-344">Stay on this page until the trace file has completed downloading.</span></span>

<span data-ttu-id="d1aa7-345">可以打开捕获的 ETL 文件以供在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中进行分析。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-345">Captured ETL files can be opened for analysis in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).</span></span>

### <a name="processes"></a><span data-ttu-id="d1aa7-346">进程</span><span class="sxs-lookup"><span data-stu-id="d1aa7-346">Processes</span></span>

<span data-ttu-id="d1aa7-347">![Microsoft HoloLens 上 Windows 设备门户中的“进程”页](images/using-windows-portal-img-09.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-347">![Processes page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-09.png)</span></span><br>
<span data-ttu-id="d1aa7-348">*Microsoft HoloLens 上 Windows 设备门户中的“进程”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-348">*Processes page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-349">显示有关当前正在运行的进程的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-349">Shows details about currently running processes.</span></span> <span data-ttu-id="d1aa7-350">这包括应用和系统进程。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-350">This includes both apps and system processes.</span></span>

### <a name="system-performance"></a><span data-ttu-id="d1aa7-351">系统性能</span><span class="sxs-lookup"><span data-stu-id="d1aa7-351">System Performance</span></span>

<span data-ttu-id="d1aa7-352">![Microsoft HoloLens 上 Windows 设备门户中的“系统性能”页](images/using-windows-portal-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-352">![System Performance page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-10.png)</span></span><br>
<span data-ttu-id="d1aa7-353">*Microsoft HoloLens 上 Windows 设备门户中的“系统性能”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-353">*System Performance page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-354">显示系统诊断信息的实时图形，如电源使用情况、帧速率和 CPU 负载。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-354">Shows real-time graphs of system diagnostic info, like power usage, frame rate, and CPU load.</span></span>

<span data-ttu-id="d1aa7-355">可用的指标如下所示：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-355">These are the available metrics:</span></span>
* <span data-ttu-id="d1aa7-356">**SoC 电源**：片上系统的瞬时用电量，为一分钟平均值</span><span class="sxs-lookup"><span data-stu-id="d1aa7-356">**SoC power**: Instantaneous system-on-chip power utilization, averaged over one minute</span></span>
* <span data-ttu-id="d1aa7-357">**系统电源**：系统的瞬时用电量，为一分钟平均值</span><span class="sxs-lookup"><span data-stu-id="d1aa7-357">**System power**: Instantaneous system power utilization, averaged over one minute</span></span>
* <span data-ttu-id="d1aa7-358">**帧速率**：每秒帧数、每秒丢失的垂直消隐数和连续丢失的垂直消隐数</span><span class="sxs-lookup"><span data-stu-id="d1aa7-358">**Frame rate**: Frames per second, missed VBlanks per second, and consecutive missed VBlanks</span></span>
* <span data-ttu-id="d1aa7-359">**GPU**：GPU 引擎利用率、总可用量的百分比</span><span class="sxs-lookup"><span data-stu-id="d1aa7-359">**GPU**: GPU engine utilization, percent of total available</span></span>
* <span data-ttu-id="d1aa7-360">**CPU**：总可用量的百分比</span><span class="sxs-lookup"><span data-stu-id="d1aa7-360">**CPU**: percent of total available</span></span>
* <span data-ttu-id="d1aa7-361">**I/O**：读取和写入次数</span><span class="sxs-lookup"><span data-stu-id="d1aa7-361">**I/O**: Reads and writes</span></span>
* <span data-ttu-id="d1aa7-362">**网络**：接收和发送数据量</span><span class="sxs-lookup"><span data-stu-id="d1aa7-362">**Network**: Received and sent</span></span>
* <span data-ttu-id="d1aa7-363">**内存**：总计、已用、已提交、已分页和未分页</span><span class="sxs-lookup"><span data-stu-id="d1aa7-363">**Memory**: Total, in use, committed, paged, and non-paged</span></span>

### <a name="apps"></a><span data-ttu-id="d1aa7-364">“应用”</span><span class="sxs-lookup"><span data-stu-id="d1aa7-364">Apps</span></span>

<span data-ttu-id="d1aa7-365">![Microsoft HoloLens 上 Windows 设备门户中的“应用”页](images/using-windows-portal-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-365">![Apps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-11.png)</span></span><br>
<span data-ttu-id="d1aa7-366">*Microsoft HoloLens 上 Windows 设备门户中的“应用”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-366">*Apps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-367">管理 HoloLens 上安装的应用。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-367">Manages the apps that are installed on the HoloLens.</span></span>
* <span data-ttu-id="d1aa7-368">**已安装的应用**：删除和启动应用。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-368">**Installed apps**: Remove and start apps.</span></span>
* <span data-ttu-id="d1aa7-369">**正在运行的应用**：列出当前正在运行的应用。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-369">**Running apps**: Lists apps that are running currently.</span></span>
* <span data-ttu-id="d1aa7-370">**安装应用**：从计算机/网络上的文件夹中选择应用包进行安装。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-370">**Install app**: Select app packages for installation from a folder on your computer/network.</span></span>
* <span data-ttu-id="d1aa7-371">**依赖项**：为要安装的应用添加依赖项。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-371">**Dependency**: Add dependencies for the app you are going to install.</span></span>
* <span data-ttu-id="d1aa7-372">**部署**：将所选应用和依赖项部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-372">**Deploy**: Deploy the selected app + dependencies to the HoloLens.</span></span>

### <a name="app-crash-dumps"></a><span data-ttu-id="d1aa7-373">应用故障转储</span><span class="sxs-lookup"><span data-stu-id="d1aa7-373">App Crash Dumps</span></span>

<span data-ttu-id="d1aa7-374">![Microsoft HoloLens 上 Windows 设备门户中的“应用故障转储”页](images/using-windows-portal-img-12.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-374">![App Crash Dumps page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-12.png)</span></span><br>
<span data-ttu-id="d1aa7-375">*Microsoft HoloLens 上 Windows 设备门户中的“应用故障转储”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-375">*App Crash Dumps page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-376">此页面允许你收集旁加载应用的故障转储。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-376">This page allows you to collect crash dumps for your side-loaded apps.</span></span> <span data-ttu-id="d1aa7-377">对于要收集其故障转储的每个应用，请选中对应的“已启用故障转储”复选框。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-377">Check the **Crash Dumps Enabled** checkbox for each app for which you want to collect crash dumps.</span></span> <span data-ttu-id="d1aa7-378">返回到此页面可收集故障转储。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-378">Return to this page to collect crash dumps.</span></span> <span data-ttu-id="d1aa7-379">可[在 Visual Studio 中打开转储文件进行调试](https://msdn.microsoft.com/library/d5zhxt22.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-379">Dump files can be [opened in Visual Studio for debugging](https://msdn.microsoft.com/library/d5zhxt22.aspx).</span></span>

### <a name="file-explorer"></a><span data-ttu-id="d1aa7-380">文件资源浏览器</span><span class="sxs-lookup"><span data-stu-id="d1aa7-380">File Explorer</span></span>

<span data-ttu-id="d1aa7-381">![Microsoft HoloLens 上 Windows 设备门户中的“文件资源浏览器”页](images/using-windows-portal-img-13.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-381">![File Explorer page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-13.png)</span></span><br>
<span data-ttu-id="d1aa7-382">*Microsoft HoloLens 上 Windows 设备门户中的“文件资源浏览器”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-382">*File Explorer page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-383">使用文件资源管理器可以浏览、上传和下载文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-383">Use the file explorer to browse, upload, and download files.</span></span> <span data-ttu-id="d1aa7-384">对于从 Visual Studio 或设备门户部署的应用，可以处理“文档”文件夹、“图片”文件夹和本地存储文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-384">You can work with files in the Documents folder, Pictures folder, and in the local storage folders for apps that you deployed from Visual Studio or the Device Portal.</span></span>

### <a name="kiosk-mode"></a><span data-ttu-id="d1aa7-385">展台模式</span><span class="sxs-lookup"><span data-stu-id="d1aa7-385">Kiosk Mode</span></span>

>[!NOTE]
><span data-ttu-id="d1aa7-386">展台模式仅适用于 [Microsoft HoloLens Commercial Suite](../../commercial-features.md)。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-386">Kiosk mode is only available with the [Microsoft HoloLens Commercial Suite](../../commercial-features.md).</span></span>

![Microsoft HoloLens 上 Windows 设备门户中的“展台模式”页](images/using-windows-portal-img-14.png)

<span data-ttu-id="d1aa7-388">有关如何通过 Windows 设备门户启用展台模式的最新说明，请查看 Windows IT 专业人员中心内的[在展台模式下设置 HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 一文。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-388">Check the [Set up HoloLens in kiosk mode](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) article in Windows IT Pro Center for up-to-date instructions on enabling kiosk mode via Windows Device Portal.</span></span>

### <a name="logging"></a><span data-ttu-id="d1aa7-389">日志记录</span><span class="sxs-lookup"><span data-stu-id="d1aa7-389">Logging</span></span>

<span data-ttu-id="d1aa7-390">![Microsoft HoloLens 上 Windows 设备门户中的“日志记录”页](images/using-windows-portal-img-15.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-390">![Logging page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-15.png)</span></span><br>
<span data-ttu-id="d1aa7-391">*Microsoft HoloLens 上 Windows 设备门户中的“日志记录”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-391">*Logging page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-392">管理 HoloLens 上的实时 Windows 事件跟踪 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-392">Manages realtime Event Tracing for Windows (ETW) on the HoloLens.</span></span>

<span data-ttu-id="d1aa7-393">选中“隐藏提供程序”以仅显示“事件”列表。 </span><span class="sxs-lookup"><span data-stu-id="d1aa7-393">Check **Hide providers** to show the **Events** list only.</span></span>
* <span data-ttu-id="d1aa7-394">**已注册的提供程序**：选择 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-394">**Registered providers**: Select the ETW provider and the tracing level.</span></span> <span data-ttu-id="d1aa7-395">跟踪级别是以下值之一：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-395">Tracing level is one of these values:</span></span>
   1. <span data-ttu-id="d1aa7-396">异常退出或终止</span><span class="sxs-lookup"><span data-stu-id="d1aa7-396">Abnormal exit or termination</span></span>
   2. <span data-ttu-id="d1aa7-397">严重错误</span><span class="sxs-lookup"><span data-stu-id="d1aa7-397">Severe errors</span></span>
   3. <span data-ttu-id="d1aa7-398">警告</span><span class="sxs-lookup"><span data-stu-id="d1aa7-398">Warnings</span></span>
   4. <span data-ttu-id="d1aa7-399">非错误警告</span><span class="sxs-lookup"><span data-stu-id="d1aa7-399">Non-error warnings</span></span>

<span data-ttu-id="d1aa7-400">单击或敲击“启用”以开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-400">Click or tap **Enable** to start tracing.</span></span> <span data-ttu-id="d1aa7-401">提供程序将添加到“已启用的提供程序”下拉列表。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-401">The provider is added to the **Enabled Providers** dropdown.</span></span>
* <span data-ttu-id="d1aa7-402">**自定义提供程序**：选择自定义 ETW 提供程序和跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-402">**Custom providers**: Select a custom ETW provider and the tracing level.</span></span> <span data-ttu-id="d1aa7-403">根据其 GUDI 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-403">Identify the provider by its GUID.</span></span> <span data-ttu-id="d1aa7-404">不要在 GUID 中包含括号。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-404">Don't include brackets in the GUID.</span></span>
* <span data-ttu-id="d1aa7-405">**已启用的提供程序**：列出已启用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-405">**Enabled providers**: Lists the enabled providers.</span></span> <span data-ttu-id="d1aa7-406">从下拉列表中选择一个提供程序，然后单击或敲击“禁用”可停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-406">Select a provider from the dropdown and click or tap **Disable** to stop tracing.</span></span> <span data-ttu-id="d1aa7-407">单击或敲击“全部停止”会暂停所有跟踪。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-407">Click or tap **Stop all** to suspend all tracing.</span></span>
* <span data-ttu-id="d1aa7-408">**提供程序历史记录**：显示已在当前会话期间启用的 ETW 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-408">**Providers history**: Shows the ETW providers that were enabled during the current session.</span></span> <span data-ttu-id="d1aa7-409">单击或敲击“启用”可激活已禁用的提供程序。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-409">Click or tap **Enable** to activate a provider that was disabled.</span></span> <span data-ttu-id="d1aa7-410">单击或敲击“清除”可清除历史记录。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-410">Click or tap **Clear** to clear the history.</span></span>
* <span data-ttu-id="d1aa7-411">**事件**：以表格格式列出来自选定提供程序的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-411">**Events**: Lists ETW events from the selected providers in table format.</span></span> <span data-ttu-id="d1aa7-412">此表将实时更新。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-412">This table is updated in real time.</span></span> <span data-ttu-id="d1aa7-413">在该表格下方，单击“清除”按钮可删除其中的所有 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-413">Beneath the table, click the **Clear** button to delete all ETW events from the table.</span></span> <span data-ttu-id="d1aa7-414">这不会禁用任何提供程序。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-414">This does not disable any providers.</span></span> <span data-ttu-id="d1aa7-415">可以单击“保存到文件”以将当前收集的 ETW 事件本地导出到 CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-415">You can click **Save to file** to export the currently collected ETW events to a CSV file locally.</span></span>
* <span data-ttu-id="d1aa7-416">**筛选器**：用于按 ID、关键字、级别、提供程序名称、任务名称或文本筛选收集的 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-416">**Filters**: Allow you to filter the ETW events collected by ID, Keyword, Level, Provider Name, Task Name, or Text.</span></span> <span data-ttu-id="d1aa7-417">可将多个条件组合在一起：</span><span class="sxs-lookup"><span data-stu-id="d1aa7-417">You can combine several criteria together:</span></span>
   1. <span data-ttu-id="d1aa7-418">对于应用到同一属性的条件，将显示可满足其中任何一个条件的事件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-418">For criteria applying to the same property, events that can satisfy any one of these criteria are shown.</span></span>
   2. <span data-ttu-id="d1aa7-419">对于应用到不同属性的条件，事件必须满足所有条件</span><span class="sxs-lookup"><span data-stu-id="d1aa7-419">For criteria applying to a different property, events must satisfy all of the criteria</span></span>

<span data-ttu-id="d1aa7-420">例如，可以指定条件 *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-420">For example, you can specify the criteria *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')*</span></span>

### <a name="simulation"></a><span data-ttu-id="d1aa7-421">模拟</span><span class="sxs-lookup"><span data-stu-id="d1aa7-421">Simulation</span></span>

<span data-ttu-id="d1aa7-422">![Microsoft HoloLens 上 Windows 设备门户中的“模拟”页](images/using-windows-portal-img-16.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-422">![Simulation page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-16.png)</span></span><br>
<span data-ttu-id="d1aa7-423">*Microsoft HoloLens 上 Windows 设备门户中的“模拟”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-423">*Simulation page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-424">允许你记录和播放用于测试的输入数据。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-424">Allows you to record and play back input data for testing.</span></span>
* <span data-ttu-id="d1aa7-425">**捕获房间**：用于下载模拟房间文件，该文件包含用户周围环境的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-425">**Capture room**: Used to download a simulated room file that contains the spatial mapping mesh for the user's surroundings.</span></span> <span data-ttu-id="d1aa7-426">为该房间命名，然后单击“捕获”以在电脑上将该数据保存为 .xef 文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-426">Name the room and then click **Capture** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="d1aa7-427">此房间文件可以加载到 HoloLens 仿真器中。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-427">This room file can be loaded into the HoloLens emulator.</span></span>
* <span data-ttu-id="d1aa7-428">**录制**：选中要录制的流、为录制内容命名，然后单击或敲击“录制”开始录制。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-428">**Recording**: Check the streams to record, name the recording, and click or tap **Record** to start recoding.</span></span> <span data-ttu-id="d1aa7-429">使用 HoloLens 执行操作，然后单击“停止”在电脑上将数据保存为 .xef 文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-429">Perform actions with your HoloLens and then click **Stop** to save the data as a .xef file on your PC.</span></span> <span data-ttu-id="d1aa7-430">可以在 HoloLens 仿真器或设备上加载此文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-430">This file can be loaded on the HoloLens emulator or device.</span></span>
* <span data-ttu-id="d1aa7-431">**播放**：单击或敲击“上传录制内容”可从电脑中选择 xef 文件，然后将数据发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-431">**Playback**: Click or tap **Upload recording** to select a xef file from your PC and send the data to the HoloLens.</span></span>
* <span data-ttu-id="d1aa7-432">**控制模式**：在 HoloLens 上，从下拉列表中选择“默认”或“模拟”，然后单击或敲击“设置”按钮选中该模式。  </span><span class="sxs-lookup"><span data-stu-id="d1aa7-432">**Control mode**: Select **Default** or **Simulation** from the dropdown, and click or tap the **Set** button to select the mode on the HoloLens.</span></span> <span data-ttu-id="d1aa7-433">相反，选择“模拟”会禁用 HoloLens 上的真实传感器，并使用已上载的模拟数据。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-433">Choosing "Simulation" disables the real sensors on your HoloLens and uses uploaded simulated data instead.</span></span> <span data-ttu-id="d1aa7-434">如果切换到“模拟”，HoloLens 将不会响应真实用户，除非切换回“默认”。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-434">If you switch to "Simulation", your HoloLens will not respond to the real user until you switch back to "Default".</span></span>

### <a name="networking"></a><span data-ttu-id="d1aa7-435">网络</span><span class="sxs-lookup"><span data-stu-id="d1aa7-435">Networking</span></span>

<span data-ttu-id="d1aa7-436">![Microsoft HoloLens 上 Windows 设备门户中的“网络”页](images/using-windows-portal-img-17.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-436">![Networking page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-17.png)</span></span><br>
<span data-ttu-id="d1aa7-437">*Microsoft HoloLens 上 Windows 设备门户中的“网络”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-437">*Networking page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-438">管理 HoloLens 上的 Wi-Fi 连接。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-438">Manages Wi-Fi connections on the HoloLens.</span></span>
* <span data-ttu-id="d1aa7-439">**WiFi 适配器**：使用下拉控件选择 Wi-Fi 适配器和配置文件。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-439">**WiFi adapters**: Select a Wi-Fi adapter and profile by using the dropdown controls.</span></span> <span data-ttu-id="d1aa7-440">单击或敲击“连接”以使用选定的适配器。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-440">Click or tap **Connect** to use the selected adapter.</span></span>
* <span data-ttu-id="d1aa7-441">**可用网络**：列出 HoloLens 可连接到的 Wi-Fi 网络。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-441">**Available networks**: Lists the Wi-Fi networks that the HoloLens can connect to.</span></span> <span data-ttu-id="d1aa7-442">单击或敲击“刷新”可更新列表。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-442">Click or tap **Refresh** to update the list.</span></span>
* <span data-ttu-id="d1aa7-443">**IP 配置**：显示网络连接的 IP 地址和其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-443">**IP configuration**: Shows the IP address and other details of the network connection.</span></span>

### <a name="virtual-input"></a><span data-ttu-id="d1aa7-444">虚拟输入</span><span class="sxs-lookup"><span data-stu-id="d1aa7-444">Virtual Input</span></span>

<span data-ttu-id="d1aa7-445">![Microsoft HoloLens 上 Windows 设备门户中的“虚拟输入”页](images/using-windows-portal-img-18.png)</span><span class="sxs-lookup"><span data-stu-id="d1aa7-445">![Virtual Input page in Windows Device Portal on Microsoft HoloLens](images/using-windows-portal-img-18.png)</span></span><br>
<span data-ttu-id="d1aa7-446">*Microsoft HoloLens 上 Windows 设备门户中的“虚拟输入”页*</span><span class="sxs-lookup"><span data-stu-id="d1aa7-446">*Virtual Input page in Windows Device Portal on Microsoft HoloLens*</span></span>

<span data-ttu-id="d1aa7-447">将键盘输入从远程计算机发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-447">Sends keyboard input from the remote machine to the HoloLens.</span></span>

<span data-ttu-id="d1aa7-448">单击或敲击**虚拟键盘**下的区域可将键击发送到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-448">Click or tap the region under **Virtual keyboard** to enable sending keystrokes to the HoloLens.</span></span> <span data-ttu-id="d1aa7-449">在“输入文本”文本框中键入内容，然后单击或敲击“发送”可将键击发送到活动应用。 </span><span class="sxs-lookup"><span data-stu-id="d1aa7-449">Type in the **Input text** textbox and click or tap **Send** to send the keystrokes to the active app.</span></span>

## <a name="device-portal-rest-apis"></a><span data-ttu-id="d1aa7-450">设备门户 REST API</span><span class="sxs-lookup"><span data-stu-id="d1aa7-450">Device Portal REST API's</span></span>

<span data-ttu-id="d1aa7-451">设备门户中的所有内容都是基于 [REST API](device-portal-api-reference.md) 创建的，你可以选择性地使用这些 API 来访问数据和以编程方式控制设备。</span><span class="sxs-lookup"><span data-stu-id="d1aa7-451">Everything in the device portal is built on top of [REST API's](device-portal-api-reference.md) that you can optionally use to access the data and control your device programmatically.</span></span>
