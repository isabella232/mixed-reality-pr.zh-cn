---
title: Windows Mixed Reality 疑难解答
description: 高级 Windows Mixed Reality 故障排除，超出了标准使用者支持文档的范围。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持
ms.openlocfilehash: bf972c70f46ad9045005b953e28831df3ee9906e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677558"
---
# <a name="troubleshooting-windows-mixed-reality-faqs"></a>Windows Mixed Reality (常见问题的疑难解答) 

## <a name="understanding-common-installation-error-messages"></a>了解常见安装错误消息

### <a name="your-pc-cant-run-windows-mixed-reality"></a>"你的电脑无法运行 Windows Mixed Reality"

你的电脑不满足运行 Windows Mixed Reality 所需的 [最低要求](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 。 这可能是因为计算机的硬件设置与 Windows Mixed Reality 不兼容，或者你需要 [更新到最新版本的 windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq)。 

请注意，Windows Mixed Reality 需要至少支持 WDDM 2.2 的图形卡驱动程序，因此请确保具有制造商提供的最新驱动程序更新。 如果 Windows Mixed Reality 安装程序显示您的图形卡无法满足要求，而您认为图形卡有问题，请确保将您的耳机插入正确的卡。

### <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"您差不多，这台电脑不满足运行 Windows Mixed Reality 所需的最低要求"

你的 PC 不满足 Windows Mixed Reality 中最佳体验所需的 [最低要求](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 。 你的电脑可能能够运行沉浸式耳机，但可能无法运行某些应用程序，或者可能存在性能问题。

请注意，Windows Mixed Reality 需要至少支持 WDDM 2.2 的图形卡驱动程序，因此请确保具有制造商提供的最新驱动程序更新。 如果 Windows Mixed Reality 安装程序显示您的图形卡无法满足要求，而您认为图形卡有问题，请确保将您的耳机插入正确的卡。

### <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"在可以设置 Windows Mixed Reality 之前，管理员将需要为你的组织启用它。 了解更多 "

你可能在使用企业托管网络，而你的组织正在使用 Windows Server Update Services (WSUS) 或具有可能会阻止下载的其他策略。 请联系组织的 IT 部门或系统管理员，以 [启用 Windows Mixed Reality](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable)。

### <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"我们无法下载混合现实软件" 或 "在我们进行一些下载时挂起"

* 有时挂起的更新可能会阻止混合现实软件下载。 转到 " **设置" > 更新 & 安全 > Windows 更新** ，并确保已打开 "Windows 更新"。 然后下载并安装任何等待安装的更新。 如果在尝试执行这些步骤时出现 Windows 更新错误，请转到 [此处](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)。
* 请确保你的电脑已连接到 internet，并且至少有2GB 的可用存储空间。 检查网络状态： **设置 > 网络 & Internet > 状态** 。 如果无法连接到 internet，请访问 [此处](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues) 获取帮助。  
* 重启电脑，然后重试。 

如果先前的解决方案不起作用，请尝试执行以下操作：
* 如果 Wi-fi 网络连接设置为 " [按流量计费](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq)"，请将其更改为 "不按流量"。 若要关闭按流量计费的连接，请转到： " **设置" > 网络 & Internet > 状态 > "更改连接属性" > 设置为按流量计费的连接** ，然后选择 "关闭"。  
* 如果最近安装了更新，则可能会导致问题。 建议您不要删除任何已安装的更新，尤其是安全更新，使您的 PC 保持安全，但有时删除最新的更新可帮助确定问题的根源。 要执行此操作： 
    * 请参阅 " **设置" > 更新 & 安全 > 查看已安装的更新历史记录 > 卸载更新**
    * 选择上次安装的更新，然后选择 "卸载"。
    * 出现 "是否确实要卸载此更新？" 提示时 回答 "是"。 如果在尝试执行这些步骤时收到错误，请转到 [此处](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)。 
    * 重启电脑，然后重试。 
    * 如果 Windows Mixed Reality 安装正确，请在 "设置" **> Windows 更新 > 检查更新** ，并查看 Windows mixed reality 是否继续运行。 如果未正确安装，请重新安装最新更新，并与 Windows 支持部门联系。 

### <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"出现错误，无法启动 Windows Mixed Reality"
* 从电脑拔下耳机电缆。
* 重启电脑。
* 转到 " **设置" > 更新 & 安全 > Windows 更新** ，并确保已打开 "Windows 更新"。 然后下载并安装任何等待更新。
* 将耳机重新连接到电脑，然后重试安装。

如果上述步骤不起作用，请尝试卸载然后重新安装 Windows Mixed Reality：
* **> Mixed reality** 中转到 "设置" > 卸载，然后选择 "卸载"。 
* 重启你的电脑。 
* 若要再次开始安装过程，只需将耳机插入 PC 即可。
    

## <a name="troubleshooting-setup-questions"></a>安装问题疑难解答 

### <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>我的 Xbox 控制器不能与 Windows Mixed Reality 一起使用。

* 确保控制器已打开、完全充电并连接到 PC。
* 更换控制器的电池。
* 如果使用的是蓝牙控制器，请在计算机上的 " **设置" > 设备 "> 蓝牙 & 其他设备** ，并确保其配对 (应在页面) 上列出。

### <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>我无法将输入 (控制器、游戏板、鼠标/键盘) 连接到 Windows Mixed Reality。

在戴戴戴显示设备上时，输入应通过耳机的状态传感器自动切换到混合现实体验。 桌面上应显示一个蓝色栏：

![向耳机定向输入的 Windows 桌面](images/1050px-windowsy.png)

如果输入未自动切换，则需要手动切换耳机的输入。 为此，可以在键盘上键入 " **Windows 键 + Y** " (，并将输入切换回桌面) 。

### <a name="when-i-plug-in-my-headset-nothing-happens-the-mixed-reality-portal-doesnt-open"></a>接通耳机后，没有任何反应。 混合现实门户不会打开。
混合现实门户是指通过 Windows Mixed Reality 安装程序的应用程序，它设计为在你插入兼容的耳机时自动打开。 如果未打开，请在 "搜索" 框中输入 "混合现实门户"，从此处打开该应用。 如果找不到混合现实门户，这可能意味着你需要 [更新到最新版本的 Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq)。

### <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>如何实现在 "固定" 和 "所有体验" 之间进行选择吗？

如果在头戴式耳机设置期间或更高版本中选择 "固定和放置"，则将使用头戴式耳机而不使用边界。 您可以坐在那里，但您需要停留在一个地方，因为您没有边界来帮助您避免物理障碍。 某些应用程序可能会设计为使用边界，因此你可能无法使用这些应用程序，或者如果你在没有边界的情况下使用它们，则可能没有相同的体验。 请参阅 "什么是边界，为什么要创建一个？" 以获取详细信息。

如果你选择 "所有体验"，你将设置一个边界，你可以使用适用于边界以及不需要的应用和体验。 

### <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-into-the-windows-mixed-reality-home"></a>了解混合现实首次启动时未运行，并直接进入 Windows Mixed Reality 主页。

可以按照 [重新运行步骤](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience)重新运行学习体验。 


## <a name="boundary-setup-and-other-questions"></a>边界设置和其他问题

### <a name="whats-a-boundary-and-why-should-i-create-one"></a>什么是边界，为何要创建它？

边界定义了在戴上 Windows Mixed Reality 沉浸式耳机时可以移动的区域。 由于你在使用头戴式耳机时看不到你的环境，因此请务必创建边界以帮助避免障碍。 边界看起来就像混合现实中的白色轮廓，并在接近它时出现。 当你看到此情况时，会减慢移动速度，并避免超出边界或扩展粗枝。

边界内的区域应该无家具、低悬挂光装置、天花板风扇等，因此不会出现任何东西。 [了解 Windows Mixed Reality 中的运行状况和安全性](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)。

### <a name="how-do-i-create-a-boundary"></a>如何实现创建边界？

首次设置耳机时，安装应用 (混合现实门户) 会指导你完成创建边界的步骤。 但你可以随时创建一个。 要执行此操作：
1. 在桌面上选择 " **启动 > 混合现实门户** "。 
2. 打开 "菜单"。
3. 选择 "运行安装程序" 以创建新边界。

如果其他人使用你的耳机，请确保它们了解边界以及如何使用它。 如果将耳机移动到新位置，则需要设置一个适用于该空间的新边界。

### <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>尝试创建边界时，收到错误消息。

* 创建边界时，请勿接近墙壁或其他障碍。
* 请确保在跟踪边界时，将耳机置于 waist 高度，并面对计算机。
* 请确保传感器未被阻止且有足够的光线。
* 正在跟踪的空间应大于三个平方米。
* 空间不应太大或太复杂。 坚持使用简单的几何形状，无需太多的旋转。
* 请不要在跟踪时返回到自己的路径。
* 如果你的角落停滞，请重新开始。

### <a name="during-start-up-of-mixed-reality-im-stuck-at-the-step-turn-your-head-side-to-side-and-then-at-the-floor"></a>在混合现实的启动过程中，我一直在步骤 "将您的头部转向一边，然后在地面"。

此步骤允许耳机识别空间，并还原任何现有的虚拟楼层和边界。 当你放在你的耳机上时，此扫描过程可能需要长达10秒的时间。 完成后，你将处于混合现实家里，否则系统将提示你再次设置边界。

如果扫描过程所用时间超过10秒，则耳机中的邻近感应传感器可能出现问题：
1. 检查是否已从邻近感应传感器中删除不干胶标签。 邻近感应感应器位于耳机内，大致位于 forehead 的中心。
2. 检查邻近感应传感器是否正在将输入切换到你的耳机：使用手指覆盖并抽出几次近程传感器，验证输入是否正在切换到耳机。 你应在电脑顶部看到 " **Windows 键 + Y** " 横幅。 您可以通过在键盘上键入 **Windows Key + Y** ，随时手动切换到耳机的输入。

### <a name="i-see-a-message-that-says-my-boundary-cant-be-found-what-should-i-do"></a>我看到一条消息，指出找不到边界。   应采取何种操作？

Windows Mixed Reality 在识别现有边界时可能会遇到问题。 你可以创建新边界，也可以在 "已安装" 和 "运行" 模式下使用你的设备。 

### <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>我看到一条消息，显示 "丢失跟踪" 或 "我们没有此空间的边界"。

您必须创建一个新边界。 要执行此操作：
* 选择 " **开始 > 混合现实门户** 。
* 选择 "运行安装程序"。

### <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>边界始终可见。 如何使其消失？

当你接近它时，会出现边界。 如果边界包含的任何部分都具有较窄或不规则的形状，则您可能最终会接近它并导致其出现，而不像您所希望的那样。 若要解决此问题，请尝试使用更大、更普通的形状再次创建边界。 要执行此操作：
* 选择 " **开始 > 混合现实门户** 。
* 选择 "运行安装程序"。

### <a name="how-can-i-turn-off-the-boundary-temporarily"></a>如何暂时关闭边界？

* 选择 " **开始 > 混合现实门户** 。
* 打开 "菜单"。 
* 将 "边界" 转换为 "关"。 请确保在边界关闭时保持在一个位置。


## <a name="problems-in-windows-mixed-reality-home"></a>Windows Mixed Reality 主页中的问题

### <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>我的控制器未显示在我的 Windows Mixed Reality 主页中。

请确保控制器具有完全电池并且使用蓝牙正确配对。 尝试使用 Windows 按钮关闭和打开控制器。 如果仍然看不到控制器，请尝试配对，然后在 " **设备 > Bluetooth** " 下的 "设置" 菜单中重新配对每个控制器。

### <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height-or-it-is-slanted"></a>我的 Windows Mixed Reality 主页的底层看起来不是正确的高度或倾斜。

选择 " **开始 > 会议室调整** ，一旦将应用置于世界各地就会启动，以便在戴上耳机时进行更改。 在此应用中，你将被定向到使用触摸板 (运动控制器) 或方向板 (游戏板) 调整地面高度。 如果地面正确，请使用 Windows 按钮退出。

### <a name="my-headset-has-stopped-tracking"></a>我的耳机已停止跟踪。

请确保灯亮起，并且没有任何内容阻碍耳机前面的内部跟踪相机。 如果跟踪丢失，可能需要几秒钟才能恢复。 如果跟踪未恢复，请尝试重新启动 Windows Mixed Reality 门户。 有关更多详细信息，请参阅 [跟踪故障排除](tracking.md) 。

### <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop-screen"></a>我无法在我的桌面上显示我在我的耳机上看到的内容的预览。

混合现实门户在屏幕底部有一个 " **播放** " 按钮，可用于在桌面屏幕上显示您在手机上看到的内容的预览。 但出于性能原因，此功能仅适用于在 Windows Mixed Reality 上运行的 Pc，超 (90Hz) 。

## <a name="headset-connectivity-issues"></a>耳机连接问题

### <a name="my-computer-does-not-have-an-hdmi-port"></a>计算机没有 HDMI 端口。
如果计算机没有 HDMI 端口，但具有 DisplayPort (DP) ，微型 DisplayPort (miniDP) 或 USB 类型 C (USB-c) 端口来输出视频，则可能需要使用 [支持的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)。

### <a name="can-i-use-usb-or-hdmi-extension-cables-with-windows-mixed-reality-headsets"></a>能否对 Windows Mixed Reality 耳机使用 USB 或 HDMI 扩展缆线？
Windows Mixed Reality 耳机不支持使用 USB 或 HDMI 扩展电缆。 使用这些电缆可能会显著影响混合现实体验，因为在计算机的 USB 控制器与混合现实耳机之间产生的信号完整性和总线功率发生变化。 如果头戴式耳机短暂显示蓝屏，然后在使用过程中打开黑色和混合现实门户的重启或完全取消枚举，或者耳机音频在黑色和正确显示器之间闪烁，请尝试使用不带分机线缆的耳机。

### <a name="i-am-getting-a-check-your-display-cable-error"></a>我收到 "检查显示电缆" 错误。

* 如果使用任何适配器将耳机连接到电脑，请确保它们支持 Windows Mixed Reality。 在将 HMD 连接到适配器之前，还要尝试将适配器连接到 PC。
* 如果你的电脑同时具有集成图形和离散图形，请确保在活动图形卡上使用 HDMI 端口。 在某些情况下，这可能意味着需要将电脑显示器连接到非 HDMI 端口。
* 如果你的电脑同时具有集成图形和离散图形，并且集成的图形较旧且不支持 Windows Mixed Reality，请尝试禁用集成的 GPU。
* 将电脑监视器连接到电脑的 HDMI 端口。 请确保图形驱动程序是最新的。 直接从 AMD、Nvidia 或 Intel 下载并安装它们，因为它们可能比发布到 Windows 更新的内容新。
* 请确保已将耳机的 HDMI 电缆插到电脑上的 **hdmi 输出** 端口，而不是端口中的 hdmi 端口。
* Windows 可能无法检测显示电缆连接。 打开设备管理器，查看耳机是否列在 "监视器" 下面。 否则，请选择 " **操作" > 扫描硬件更改** 。 

### <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>我看到一条消息，显示 "戴上耳机"，即使我的耳机已打开。

当你放在你的耳机上时，Windows Mixed Reality 可能需要几秒钟才能重新加载空间。 如果此消息不会消失，请确保已从邻近感应传感器（位于重用功能区之间的耳机内）中删除了保护标签。 如果这不能解决问题，请与你的耳机制造商联系。

### <a name="a-message-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>即使已插入耳机，消息也会显示 "连接耳机"。

1. 确保将耳机的 USB 和 HDMI 电缆连接到计算机上的正确端口。 下面介绍如何识别正确的端口：
    * USB 3.0 端口有一个特殊的徽标，其中 "SS" 标记 (表示 "SuperSpeed" ) 。 端口的内部片通常为蓝色，而旧的 USB 2.0 端口通常在内部为黑色或白色。
    * 如果计算机有两个 HDMI 端口，请使用连接到图形卡的端口，而不是计算机的主板。 这并不总是很明显，但不同的端口通常位于计算机上的扩展插槽中。 如果尝试一个端口但它不起作用，请尝试其他端口。
2. 从耳机拔下并插入 USB 和 HDMI 电缆，确保它们已安全连接。 插入 USB 电缆时，请不要在插入 USB 电缆期间暂停。
3. 打开设备管理器并确认你的耳机是否列在 "Mixed Reality 设备" 下。 双击 "Mixed Reality 设备" 下的耳机，并确认设备状态指示 "此设备正常运行"。 设备管理器中列出的设备上的黄色感叹号指示连接到电脑的设备所报告的错误。
    * 如果在设备管理器中列出了 "Hololens 传感器" 并带有黄色惊叹号，请双击该设备。 如果出现 **"代码10：未安装此设备的驱动程序"。此设备没有兼容的驱动程序 "** ，请按照 [说明](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset) 手动安装耳机驱动程序。
    * 如果你在你的电脑上使用多个混合现实耳机，并已在之前手动安装混合现实耳机驱动程序，则在某些情况下，手动驱动程序更新可能仅适用于当时连接的耳机，而不适用于其他耳机。 在这种情况下，你将看到 **"代码31：此设备无法正常工作，因为 Windows 无法加载此设备所需的驱动程序"。 (代码 31) 。设备管理器中的 ALPC 消息不再可用 "** 。 在设备管理器中，右键单击 "Mixed Reality 设备" 下的耳机，然后选择 "卸载设备"。 选择 "确定" 以确认并拔出并 replug 你的耳机。
4. 如果你查看耳机的部分枚举 (一系列 USB 设备枚举，但设备管理器) 中 "Mixed Reality 耳机" 下没有任何内容，请尝试使用外部 USB 3.0 集线器。
5. 请参阅耳机制造商的网站并更新耳机的驱动程序和固件。
6. 将耳机连接到另一台电脑并打开设备管理器。 即使该 PC 与 Windows Mixed Reality 不完全兼容，你也可以查看你的耳机是否枚举。 如果耳机不在多台电脑上枚举，则可能存在硬件问题。

**适用于 Surface 用户的说明：** 较早版本的 Surface Dock 和 Surface Book USB 集线器固件更新软件与混合现实耳机不兼容。 如果在 Surface PC 上收到 "连接耳机" 消息，请检查是否有任何设备在设备管理器中报告了 **"代码10：设备无法启动" 错误** 。 如果是这样，请 [删除冲突的驱动程序](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)。 只需执行此操作一次。

**适用于 Windows 10 N 用户的说明：** 如果你的计算机运行的是 Windows 10 N，则在插入混合现实耳机后，会看到 **"代码28：安装类不存在或无效" 设备管理器错误** 。 Windows Mixed Reality 不支持 N 版本的 Windows 10。 有关详细信息，请按照这些 [说明](troubleshooting-windows-mixed-reality.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 进行操作。

### <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>消息显示 "检查 USB 电缆" 或 "USB 速度不足"。

* 请确保使用的是计算机上受支持的 USB 3.0 端口：
    * 请确保将耳机的 USB 电缆全部插入。
    * 运行 [Windows Mixed REALITY PC 检查](https://aka.ms/pccheckapp) 应用，以确保支持你的电脑的 USB 3.0 控制器。
    * 尝试电脑上的其他每个 USB 3.0 端口。 某些电脑具有多个 USB 3.0 控制器。
    * 暂时断开连接到电脑的所有 USB 设备，并仅连接耳机。
    * 在自定义构建的 Pc 上，即使某个端口可能标记为 USB 3.0 端口，它也可能连接到 USB 2.0 控制器。 在手机网络连接上，打开设备管理器，找到并单击从耳机枚举的任何设备，然后参阅 **按连接查看 > 设备** "。
* 尝试在另一台电脑上戴上耳机。 如果其他 PC 与 Windows Mixed Reality 不完全兼容，请签入设备管理器查看 "USB 速度是否不足" 消息。 如果耳机未在多台电脑上正确枚举，则耳机可能出现故障。

### <a name="the-mixed-reality-portal-did-not-launch-automatically-after-i-plugged-in-my-headset"></a>我接通耳机后，混合现实门户未自动启动。

可能由于根本问题而无法正确检测到耳机。 尝试手动启动混合现实门户，并查找显示的任何错误消息。 

### <a name="my-headset-stopped-working-after-putting-my-pc-to-sleep-in-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>将电脑置于睡眠状态后，耳机停止工作，在休眠模式下，或在重新启动我的电脑时连接到我的耳机时停止工作。

1. 打开设备管理器并确认你的耳机是否列在 "Mixed Reality 设备" 下。
2. 双击 "Mixed Reality 设备" 下的耳机，并确认设备状态指示 "此设备正常运行"。
3. 如果出现 "代码 43" 错误，指出设备已停止工作，或者如果你没有在 "Mixed Reality 设备" 下看到你的耳机，请将其拔出，然后在你的耳机的 USB 电缆中拔出和 replug。 Microsoft 正在调查可能导致此错误的潜在软件/驱动程序互操作性问题。 此问题会影响少量 Pc，预计会在将来对混合现实耳机驱动程序的更新中得到解决。

### <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>我的耳机会使我的电脑在计算机进入睡眠状态或处于休眠模式时， (蓝屏) 生成 Bug 检查。

Microsoft 正在调查潜在的软件/驱动程序互操作性问题，这可能会导致少量的 Pc 生成 "9F" Bug 检查 (蓝屏) 当电脑进入睡眠状态或连接到耳机时处于休眠模式时）。 此问题应在以后对混合现实耳机驱动程序的更新中得到解决。

### <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>接通耳机后，耳机驱动程序未自动安装。

在新电脑上，或安装有新安装的 Windows 10 副本的电脑上，耳机驱动程序可在其他 Windows 更新后排队，并且可能不会立即安装。 如果有 "N" 版 Windows，则需要切换到 Windows 10 的常规版本，才能使用 Windows Mixed Reality。 手动安装：

1. 请参阅 **开始 > 设备管理器** 并在 "其他设备" 下查看 "HoloLens 传感器" 设备的 "其他设备"，其中包含黄色感叹号： ![ 设备管理器 HoloLens 传感器的视图](images/hololenssensors.png)
2. 右键单击该设备，然后选择 "属性"。 如果设备的属性读取 **此设备的驱动程序未安装 (代码 28)** ，请关闭该窗口，然后继续。 如果有另一条消息，请按照本页其余部分的故障排除步骤操作。
![设备管理器中的 HoloLens 传感器的代码28](images/code28.png)
3. 再次右键单击该设备，然后选择 "更新驱动程序 ..."然后，在设备更新后 "自动搜索更新的驱动程序软件"，你应会在设备管理器： ![ Mixed Reality 设备显示在设备管理器](images/mixedrealitydevices.png)

如果手动安装不起作用，或在其他设备下找不到该驱动程序，则可能需要卸载现有的驱动程序，然后重新安装它。 若要执行该操作：
1. 请参阅 **开始 > 设备管理器** 并在 "混合现实设备" 下查看头戴显示设备。 设备状态应指示 "设备正常运行"。
2. 右键单击该设备，然后选择 "卸载设备"。
3. 在出现的新弹出窗口中，选中复选框 "删除此设备的驱动程序软件"，然后选择 "卸载"。
4. 完成后，拔出电脑的耳机，并重新插回。 Windows 更新现在会下载并安装新的驱动程序。

### <a name="troubleshooting-flowchart"></a>故障排除流程图

![连接耳机/检查 USB 电缆](images/hmd-connectivity2.jpg)


## <a name="mixed-reality-headset-display-problems"></a>混合现实耳机显示问题 ##

### <a name="my-headset-displays-are-black"></a>我的耳机显示为黑色。

* 检查您的 PC 性能和稳定性：
    * 使用任务管理器查看是否有任何进程支持您的 PC 的 CPU、GPU 和/或磁盘驱动器。
    * 使用事件查看器) 查看 Windows (中的应用程序和系统事件日志，以查看是否有经常崩溃并生成 Windows 错误报告 (WER) 报告的应用程序。
    * 检查 Windows 更新，确保你的 Windows 版本是最新版本。 可能需要多次选择 "检查更新"。
* 检查应用和游戏稳定性：
    * 确保你的计算机满足最低系统要求，以运行任何不能正常运行的应用/游戏。    
    * 确保你的 GPU 驱动程序版本是最新版本，并检查新驱动程序是否存在任何新的性能和兼容性问题和回归。
    * 如果你使用的是 SteamVR 应用和游戏，请确保 SteamVR 和 SteamVR 组件的 Windows Mixed Reality 是最新的。
* 检查 HDMI 适配器的兼容性：
    * 请确保 HDMI 电缆一直处于插入的方向。
    * 如果使用的是 HDMI 适配器 (例如，微型 DisplayPort to HDMI 适配器) ，请确保它与 Windows Mixed Reality 兼容。 适配器必须支持 HDMI 2.0，并且有许多较早的适配器仅支持1080p。 请参阅 [Windows Mixed Reality 的推荐适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)。
    * 插头顺序很重要。 在将耳机连接到适配器之前，请将 HDMI 适配器连接到电脑，尤其是在使用 USB 到 HDMI 适配器的情况下。 
    * 如果正在使用，请尝试删除扩展电缆。
* 检查图形卡和驱动程序兼容性：
    * 使用 PC 监视器尝试您的 PC 的 HDMI 端口。 某些 Pc 可能有多个 HDMI 端口，而且并非所有计算机都处于活动状态。
    * 如果你的电脑同时 (iGPU) 和离散图形处理单位 (dGPU) ，则请确保已将其插入 dGPU 的 HDMI 端口。<br> ![HDMI 端口](images/HP_HDMI_Ports_s.png)
    * 仔细检查 GPU 驱动程序版本。 请确保它是最新的，还应注意任何新的性能和兼容性问题以及新驱动程序的回归。
    * 如果在笔记本电脑上使用混合现实，并且已从图形卡制造商的网站安装了更新的图形驱动程序，请尝试降级到电脑制造商网站上提供的最新图形卡驱动程序，或 Windows 更新上。
    * 如果有多台电脑监视器连接到您的 PC，请尝试暂时断开除一台 PC 监视器以外的所有连接。
    * 如果已为电脑监视器设置自定义刷新速率，请尝试暂时还原为标准刷新率，如60Hz。
    * 如果最近更改了图形卡而不重新安装 Windows，请检查耳机式监视器是否仍然安装了正确的驱动程序。 接通耳机后，确认 "Mixed Reality 耳机" 列在设备管理器的 "监视器" 节点下。
    * 如果你的电脑具有 Nvidia 图形卡，请确保已禁用 Nvidia 的3D 远景软件。
    * 对于某些图形卡 (特别) 的显卡，HDMI 端口可能不支持 HDMI 2.0，或者可能与 Windows Mixed Reality 完全兼容。 请使用[活动的 DisplayPort 1.2 到 HDMI 2.0 适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)尝试使用图形卡的 DisplayPort 端口
    * Hp Omen 电脑（HP 产品编号为 1RJ99EA # 阿尔）具有与 Windows Mixed Reality 不兼容的 HDMI 端口。 为此，请打开 "HP 支持助手"，将在应用底部列出产品编号。
    * 如果你的电脑具有 AMD R9 系列图形卡，并且你使用的是 Samsung 混合现实耳机，则需要将头戴显示设备的固件更新为版本1.0.8 或更高版本，以便将你的图形卡的 HDMI 端口与耳机配合使用。
    * 如果使用的是 Surface Book 2，请确保使用的是从 [USB 到 HDMI 适配器的接口](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)。
* 检查混合现实耳机硬件问题：
    * 若要确认或排除混合现实耳机的硬件问题，请尝试将混合现实耳机连接到另一台 PC。 
    * 首先检查计算机兼容性和安装问题，因为症状非常类似。
* 请检查以确保已将 USB 电缆插入 USB 3.0 或更快的端口。 USB 3.0 端口具有 SS () 写入它们的速度。 它们通常 (，但并不总是) 彩色蓝色。        

如果有帮助，请参阅下面的耳机黑色屏幕疑难解答流程图。

![黑屏/看不到任何内容](images/hmd-connectivity.jpg)

### <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>有些使用后，耳机显示偶尔会变黑。

* 尝试禁用 PC 可能具有的任何 USB 挂起或节能功能。 例如， [usb 选择性挂起](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend) 在 Windows 电源选项中，在设备管理器中选择 "允许计算机关闭此设备以节省电源" 设置，并在 PC 的固件中保存任何 usb 节能设置。
* 暂时断开连接到电脑的任何其他 USB 设备和外围设备。
* 仔细检查 GPU 驱动程序版本。 请确保它是最新的，还应注意任何新的性能和兼容性问题以及新驱动程序的回归。

### <a name="one-of-the-displays-on-my-headset-is-black"></a>我的耳机上显示的一个显示为黑色。

* 如果使用的是 HDMI 适配器，请确保它支持 HDMI 2.0。
* 删除任何可能使用的 USB 和 HDMI 扩展电缆。
* 请确保您的图形驱动程序是最新的。
* 尝试将混合现实耳机置于另一台电脑上。

### <a name="my-headset-displays-turn-blue-for-a-moment-and-then-mixed-reality-portal-reinitializes"></a>我的耳机显示暂时为蓝色，然后混合现实门户重新初始化。

这通常表示你的电脑上偶尔出现 USB 控制器可靠性问题：
* 请尝试其他 USB 端口。 你的电脑可能有多个 USB 3.0 控制器。
* 如果适用) ，请 (删除任何扩展电缆。
* 尝试从您的 PC 中拔出所有其他 USB 设备。
* 尝试将外部驱动的 USB 3.0 集线器连接到您的 PC，并将您的耳机连接到中心。
* 如果使用的是台式计算机，请考虑购买 USB 3.0 PCIe 卡，将另一个 USB 控制器添加到您的 PC。

### <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>我的耳机使我的 PC 挂起或在启动时显示黑屏。

在某些电脑上，在打开或重启电脑时，让你的耳机保持接通电源可能会影响其启动过程。 你的电脑可以选择耳机显示为 "主监视器" 以显示 PC 启动进度，或者可能会阻止其启动并显示 "挂起" 和/或产生报警音错误代码。 此行为很大程度上取决于 PC 制造商和型号，以及/或者图形卡的品牌和型号。 解决方法：
* 将耳机连接到图形卡上的其他端口 (可能需要使用适配器) 使用其他端口。
* 请确保您的 PC 的 BIOS/UEFI 固件是最新的 (，但如果您喜欢这样做) ，只需更新您的 PC BIOS/UEFI 固件。

### <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>使用 Surface PC 时，电脑或耳机显示闪烁、闪烁或保持黑屏。

* 请确保使用的是支持 HDMI 2.0 的 HDMI 适配器。 许多老式的 HDMI 适配器仅支持1080p 分辨率，这对于混合现实耳机来说是不够的。
* 请确保您的图形驱动程序是最新的。 除了检查 Windows 更新之外，您可能还希望查看 PC 制造商的网站中是否有更新的图形驱动程序。
* 某些 Surface 设备与 Windows Mixed Reality 不兼容。 了解有关 [Surface 兼容性和要求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)的详细信息。

### <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>关机后，我的耳机显示不起作用。

从耳机拔下 HDMI 电缆和 USB 电缆，然后将其重新插回。

### <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>我的耳机显示显得非常断断续续，但混合现实门户的预览窗口显示良好。

* 请确保您的 PC 的系统资源 (CPU、内存和硬盘驱动器) 可用且不会被其他应用程序或过程极限。
* 更新图形驱动程序。

### <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>在设备管理器中收到 "安装类不存在或无效" 错误。

如果在设备管理器中看到 "HoloLens 传感器" 带有黄色惊叹号，请双击该设备了解更多详细信息。 如果看到一条消息，指出 "未安装此设备的驱动程序。  (代码 28) -安装类不存在或无效 "，这通常是因为你的电脑正在运行 [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)。请注意，N 版 Windows 10 不支持 Windows Mixed Reality，你将需要安装非 N 版本的 Windows 10。

### <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>我的 WMR 环境在移动头时出现抖动或 stutters，并显示双重视觉。

在具有集成图形和 Nvidia GPU 的便携式计算机上，在一段时间后出现错误，使上一个帧在下一帧之后显示，从而使双愿景在偏航、音调或滚动移动过程中移动的速度更快。 此问题似乎出现在 Nvidia 图形驱动程序436.48 之后的驱动程序中。  安装此驱动程序将解决此问题，直至 Nvidia 解决更新的驱动程序中的问题。 若要直接安装 Nvidia 图形驱动程序436.48，请访问 [nvidia](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)。

### <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>我使用耳机时遇到 discomfort。
有关 Windows Mixed Reality 中舒适的一般信息，请参阅 [Windows Mixed reality 沉浸式耳机运行状况、安全和舒适](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)。 有关特定耳机的详细信息，请与耳机制造商联系。

### <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>如何在我的耳机中获得更清晰的视图？
尝试调整耳机大小。 通过向上、向下或向左和向右移动，调整传送带的位置，并调整传送带，使其感觉 snug。

如果耳机支持，还可以调整其校准设置。 如果头戴式耳机有调整校准的旋钮，请使用。 如果没有，请参阅 " **设置" > 混合现实 > 视觉质量** 并调整其中的校准。 有关特定设备的校准的详细信息，请与耳机制造商联系。

## <a name="mixed-reality-portal-error-messages-and-problems"></a>混合现实门户错误消息和问题

### <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>我收到 "出现错误" 的错误消息，或在混合现实门户中遇到问题。

重启 Windows Mixed Reality：
1. 从电脑拔下耳机电缆。
2. 重启你的电脑。
3. 重新连接耳机。

如果这不起作用，请确保电脑识别你的耳机：
1. 选择“启动”。
2. 在搜索框中键入 "设备管理器"，并在列表中选择它。 
3. 展开 "Mixed reality 设备"，并查看是否列出了你的耳机。 

如果未列出，请尝试以下操作：
1. 将耳机插入电脑上的不同端口（如果可用）。
2. 查看 Windows 更新中的最新软件更新。
3. 卸载并重新安装 Windows Mixed Reality：
    1. 从电脑拔下耳机电缆。
    2. 选择 " **设置" > 混合现实 > 卸载** "。
    3. 选择 " **设置" > 设备 > 蓝牙 & "其他设备** " 以取消配对运动控制器。 选择每个控制器，然后选择 "删除设备"。
    4. 将您的耳机插回您的 PC 上，重新安装 Windows Mixed Reality。
    
### <a name="im-getting-a-check-your-usb-cable-error-message"></a>我收到 "检查 USB 电缆" 错误消息。

将耳机连接到不同的 USB 端口 (，并确保它是 SuperSpeed USB 3.0) 。 同时，尝试删除耳机与计算机之间的所有扩展器或集线器。

### <a name="im-getting-a-check-your-display-cable-error-message"></a>我收到 "检查显示电缆" 错误消息。

请尝试以下做法：
* 将耳机连接到 DisplayPort 1.2 或更高版本，1.4 或者连接到或更高版本。 确保端口与电脑上最先进的图形卡相对应。
* 如果使用的是适配器，请确保它支持4K。
* 尝试使用不同的 HDMI 端口。
* 如果将外部监视器连接到 HDMI 端口，请尝试将其插入 DisplayPort，并将 HDMI 端口用于耳机。


## <a name="something-went-wrong-error-codes-and-how-to-resolve-them"></a>"出现错误" 的错误代码及其解决方法

| **Windows 10 错误代码** (版本 1809/版本1709、1803)  | **错误消息和故障排除建议**                    |
|-------------------------------------------------------------|--------------------------------------------------------------------|
|   1-4 / 2197815297-4  | **检查您的显示电缆：确保耳机的显示电缆已正确插入。** <br/><br/><ol start="1"><li>拔出耳机的 USB 和 HDMI 电缆，然后重新插回。</li><li>选中设备管理器并确认在 "监视器" 下，出现 "混合现实耳机" 的监视器。</li><li>请确保图形驱动程序是最新的 (从图形卡制造商的网站) 。</li><li>如果使用适配器连接耳机，请确保它 [支持 Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)。</li><li>如果图形卡同时具有 DisplayPort 和 HDMI 端口，请尝试使用图形卡上的 DisplayPort 端口，并使用支持的混合现实 DisplayPort 到 HDMI 适配器。</li><li>在电脑上尝试使用其他 USB 3.0 端口</li></ol> |
|   1-5 / 2197815297-5  | **检查显示电缆：耳机显示无法正确初始化。尝试重启电脑并重新连接耳机。**<br/><br/>Windows 看到了你的耳机式监视器，但 Windows Mixed Reality 与混合现实耳机上的显示器通信时遇到问题。 解决方法：<br/><ol start="1"><li>请确保图形驱动程序是最新的 (从图形卡制造商的网站) 。</li><li>如果使用适配器连接耳机，请确保它 [支持 Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)。</li><li>如果图形卡同时具有 DisplayPort 和 HDMI 端口，请尝试使用图形卡上的 DisplayPort 端口，并使用支持的混合现实 DisplayPort 到 HDMI 适配器。</li><li>尝试重启电脑。</li></ol> |
|   7-1、7-2、7-3/2181038087-1、2181038087-2、2181038087-3  | **Windows Mixed Reality 连接到耳机时遇到问题。尝试拔出耳机，并将其重新插入。**<br/><br/>混合现实耳机未能完全初始化。 这很可能是暂时性错误。 拔出耳机，并将其重新插回以解决此问题。
|   7-4 / 2181038087-4  | **Windows Mixed Reality 连接到耳机时遇到问题。尝试拔出耳机，并将其重新插入。**<br/><br/>混合现实耳机驱动程序无法在你的耳机上初始化跟踪相机。 这很可能是暂时性错误。 拔出耳机并再次插上，以解决此问题。
|   7-5 / 2181038087-5  | **Windows Mixed Reality 连接到耳机时遇到问题。尝试将你的耳机插入其他 USB 端口，并暂时拔下连接到电脑的任何其他 USB 设备。**<br/><br/>Windows Mixed Reality 在混合现实摄像机帧时间戳和你的电脑时间戳之间丢失了同步。 这可能是暂时性错误，也可能是 USB 信号完整性问题的指示。 解决方法：</li><li>暂时拔出所有 USB 设备和外围设备，取下所有延长电缆，并插入耳机。</li><li>在电脑上禁用任何 USB 挂起/节能功能，如在 Windows 电源选项中选择性挂起、在 Windows 电源选项设备管理器中选择 "允许计算机关闭此设备以节省电源" 设置，以及 PC 固件中的任何 USB 节能设置。</li></ul>
|   7-6 / 2181038087-6  | **耳机固件存在问题。尝试拔出耳机，并将其重新插入。** <br/><br/>这可能是暂时性的错误。 尝试拔出耳机，并重新插入。 如果这不起作用：</li><li>检查 Windows 更新以确保你运行的是最新的耳机驱动程序。</li><li>尝试在另一台电脑上戴上耳机。 如果看到相同的错误消息，则需要为你的耳机提供服务。</li></ul>
|   7-7 / 2181038087-7  | **Windows Mixed Reality 连接到耳机时遇到问题。尝试将你的耳机插入其他 USB 端口，并暂时拔下连接到电脑的任何其他 USB 设备。**<br/><br/>混合现实耳机驱动程序无法初始化耳机上的固件。 这可能是暂时性的错误。 尝试拔出耳机，并重新插入。 如果这不起作用：<li>暂时拔出 USB 设备和外围设备，无需运行 Windows Mixed Reality。</li><li>检查 Windows 更新以确保你运行的是最新的可用耳机驱动程序。</li></ul>
|   7-11 / 2181038087-11 | **CPU 太旧，无法与 Windows Mixed Reality 兼容。**<br/><br/>你的电脑未通过兼容性检查，因为 CPU 缺少混合现实运动控制器所需的 AVX 指令集。 需要使用 [Windows Mixed Reality 兼容的 PC](https://www.microsoft.com/en-us/windows/view-all-devices?col=wmr-pcs#icons)。
|   7-12 / 2181038087-12 | **你的耳机连接到不兼容的 USB 控制器。尝试将你的耳机插入到其他 USB 端口（如果可用）。或者，尝试安装 Microsoft USB 驱动程序来代替任何不兼容的驱动程序。**<br/><br/>你的耳机可能插入到连接到不兼容的非 Microsoft USB 控制器驱动程序的 USB 端口。 这些 USB 3.0 控制器驱动程序通常不会读取和处理 [ContainerID 描述符](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-containerids-in-windows)，这会将混合现实耳机的不同部分聚合到一个内聚的单元中 (以便从正确的耳机播放音频，视频输出正确的显示器，并从正确的传感器) 请求跟踪数据。 更改 USB 控制器驱动程序： <ol start="1"><li>启动设备管理器。</li><li>展开 "通用串行总线控制器" 的类别，然后单击右键，为包含 "可扩展主机控制器" 文本的每个项卸载驱动程序 **，** 名称中不包含 "Microsoft"。</li><li>选择 "删除此设备的驱动程序软件" 以确保删除旧的驱动程序。</li><li>验证包含文本 "可扩展主机控制器" 的每个项在结尾都有 "Microsoft"。</li><li>插入 HMD。</li></ol>或者，如果此问题是间歇性的，则 HMD 可能无法正确响应 HMD 驱动程序中的命令。 若要解决此问题，请将 HMD 拔出30或更多秒，并重新插入。 | 
|   7-13 / 2181038087-13 | **你的耳机连接到不兼容的 USB 控制器。尝试将你的耳机插入到其他 USB 端口（如果可用）。如果没有，则需要安装新的 USB 3.0 控制器。**<br/><br/>Windows Mixed Reality 无法将混合现实摄像机帧时间戳同步到你的电脑时间戳。 这很可能是由不支持 ITP (同步时间戳数据包) 的不兼容 USB 3.0 主机控制器导致的。 请与你的电脑制造商联系，查看是否可以启用 ITP，或切换到另一个具有 ITP 支持的 USB 主机控制器。 |
|   7-14 / 2181038087-14 | **Windows Mixed Reality 连接到耳机时遇到问题。尝试拔出耳机，并将其重新插入。**<br/><br/>Windows Mixed Reality 在混合现实耳机上初始化状态传感器时遇到问题。 在设备管理器中，耳机将显示错误消息 "PoseThread 无法初始化存在传感器"。 解决方法：<br/><ol start="1"><li>拔出耳机，并重新插入。 确保拔出 USB 电缆。</li><li>尝试在您的 PC 上运行另一个 USB 端口。</li><li>尝试在另一台电脑上戴上耳机，查看耳机是否完全在该电脑上设备管理器。</li><li>检查您的计算机上是否安装了任何其他冲突的 HID 驱动程序，例如，通过键盘或鼠标。  (在设备管理器中查找具有问号徽标的任何 HID 设备。 ) </li><li>如果你使用的是运行 Windows 10 版本1709或版本1803的 Samsung Mixed Reality 头戴式耳机，请按照错误代码2181038087-12 的说明进行操作，以检查 USB 3.0 控制器是否正在运行非 Microsoft USB 控制器驱动程序。</li></ol> |
|   7-15 / 2181038087-15 | **Windows Mixed Reality 检测到安装了不兼容的 WinUSB 驱动程序。**<br/><br/><ol start="1"><li>确保你的电脑上的 WinUSB 驱动程序是 Windows 附带的驱动程序，并且任何第三方 USB 驱动程序未在你的电脑上覆盖 WinUSB 的副本。</li><li>如果问题仍然存在，你可能需要恢复或重新安装 Windows 安装。</li></ol> |
|   13-11/-            | 混合现实门户在 Windows 上遇到应用注册问题。 使用事件查看器) 查看应用程序事件日志 (，查看是否存在其他详细信息。 |
|   14-1/-            | 混合现实门户无法初始化图形和组合堆栈。 解决方法：<ul><li>桌面窗口管理器 (DWM，Windows 图形堆栈) 的关键组件可能会崩溃。 使用事件查看器) 查看应用程序事件 (日志，以查看是否发生这种情况。</li><li>尝试全新卸载图形驱动程序，然后从图形卡制造商的网站安装最新的图形驱动程序。</li></ul> |
|   14-2/C0001160-101  | **连接到你的耳机时遇到问题。尝试删除可能使用的任何分机电缆，并确保已将耳机连接到图形卡的正确端口。如果使用的是任何适配器，请确保它们与混合现实兼容。如果仍有问题，请尝试更新图形驱动程序。**<br/><br/>混合现实显示和组合堆栈初始化失败。 您的 PC 的图形卡或图形卡驱动程序可能与 Windows Mixed Reality 不兼容。 若要检查此内容： <ul><li>仔细检查您的 PC 是否满足 Windows Mixed Reality 的最低系统要求。</li><li>如果在 Windows 10、版本1809或更高版本上使用 Dell Inspiron 5577 电脑，你可能会看到此错误，原因是与 Dell 的 "真彩色图形处理" 功能发生冲突。 若要解决此问题，请使用 Dell 的 "真彩色" 应用关闭 "真彩色" 功能，然后尝试再次运行混合现实门户。</li><li>在台式计算机上，安装图形卡制造商网站上的最新图形驱动程序。 在便携式计算机上，为制造商网站上的品牌和型号安装最新的图形驱动程序。</li><li>如果有第三方图形或显示软件/附件，请暂时卸载这些应用和驱动程序。</li><li>选择 "重试" 以查看是否是暂时性问题。</li></ul> |
|   14-3/-             | **连接到你的耳机时遇到问题。尝试删除可能使用的任何分机电缆，并确保已将耳机连接到图形卡的正确端口。如果使用的是任何适配器，请确保它们与混合现实兼容。如果仍有问题，请尝试更新图形驱动程序。** <br/><br/><ul><li>如果你使用的是任何自定义模式或 PC 监视器上的刷新速率，请尝试将其刷新率设置为60Hz。</li><li>请确保所使用的任何适配器都支持 Windows Mixed Reality。</li><li>尝试从图形卡制造商的网站安装最新的图形驱动程序。</li><li>单击 "重试" 以查看是否是暂时性问题。</li></ul> |
| 14-4/-             | **连接到你的耳机时遇到问题。尝试删除可能使用的任何分机电缆，并确保已将耳机连接到图形卡的正确端口。如果使用的是任何适配器，请确保它们与混合现实兼容。如果仍有问题，请尝试更新图形驱动程序。** <br/><br/><ul><li>你的电脑的电脑监视器数量可能超过了图形适配器可支持的数量。 断开除您的主 PC 监视器以外的所有连接。</li><li>请确保所使用的任何适配器都支持 Windows Mixed Reality。</li><li>安装图形卡制造商网站上的最新图形驱动程序。</li><li>单击 "重试" 以查看是否是暂时性问题。</li></ul> |
|   15-5/-             | **混合现实门户丢失了与核心混合现实和它所依赖的 Windows 组件的同步。**<br/><br/><ul><li>这可能是由于你的电脑出现性能问题。 请确保在任务管理器中未限定 CPU、GPU 和 HDD。</li><li>暂时断开所有其他 USB 设备与计算机的连接。</li><li>重启你的电脑。</li></ul> |
|   -/H0002000-0    | **你的电脑操作系统已进入不匹配的 Windows Mixed Reality 状态**<br/><br/>检查 Windows 更新是否有更新。 |
|   -/S0002261-101，S0002361-101 | **混合现实 shell 组件存在问题，导致无法正常启动混合现实门户**<br/><br/><ul><li>使用电脑上的事件查看器打开应用程序日志，以检查在尝试启动 Windows Mixed Reality 时是否出现任何应用程序崩溃。</li><li>请确保您的图形驱动程序是最新的。</li><li>你使用的 HDMI 适配器与 Windows Mixed Reality 不兼容。 请参阅 [此处](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) (DP) 转换器的支持和推荐的 HDMI 到迷你显示端口。</li></ul> |


## <a name="motion-controller-problems"></a>运动控制器问题

### <a name="my-motion-controllers-arent-working-properly"></a>运动控制器不能正常工作。

如果 [运动控制器](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) 没有工作、未连接或在戴上耳机时看不到控制器的图像，请尝试以下操作：
1. 请确保已打开控制器。 若要将其打开，请按住 Windows 按钮两秒钟。
2. 请确保控制器完全充电，如果不是，则更换电池。
3. 将控制器保持在您的前方，同时关闭控制器并将其打开。 按住 Windows 按钮四秒钟，使控制器关闭，然后再次按住该控制器两秒钟，以将其打开。 
4. 选择 " **设置" > 设备 > 蓝牙 &** 计算机上的其他设备，并确保控制器已按配对方式列出。 如果不是，则需要将 [它们配对](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality)。 
5. 请确保运动控制器显示为 "已连接"。 "配对" 不一定表示控制器已连接到 PC。 控制器应出现在 "鼠标，键盘 & 笔" 类别下。 "其他设备" 下的运动控制器未通过配对过程，因此不起作用。 检查运动控制器 Led 指示灯：强光亮起的控制器已配对并且已连接，dimly 发亮控制器未连接。
6. 在电脑上，请参阅 **开始 > 混合现实门户** ，并选择 "菜单"。 你应该会看到你的运动控制器以及状态消息：
    * 就绪–控制器都已设置好。
    * 丢失跟踪–混合现实门户找不到控制器。 将其放在头戴戴显示设备前面，按 "Windows" 按钮4秒钟再重新启动，然后再次2秒钟。
    * 电池电量低–更换控制器电池。
7. 如果使用的是外部 USB 蓝牙适配器，请确保将其插入到黑色 USB 2.0 端口。 还应尽可能远离任何其他无线发送器或 USB 闪存驱动器（包括耳机的 USB 连接器）连接。 
8. 通过右键单击 Windows "开始" 菜单并选择 "设备管理器"，验证 PC 中是否只有一个蓝牙收音机。 展开 "蓝牙" 部分，并查找一个适配器。 如果你使用的是带内置收音机的台式计算机配置，请检查是否已连接外部天线。 如果未连接外部天线，则可能会导致跟踪问题。 或使用外部蓝牙转换器 (USB) ，禁用内部蓝牙功能，然后重试配对和连接。
9. 关闭蓝牙设置窗口（如果已打开）。 如果在后台打开，则需要对蓝牙协议进行大量的额外调用。
10. 检查运动控制器上的虚拟电池电量水平。 在混合现实中，打开控制器，可以看到电池图标。 如果它是红色，请更换电池。 通常，在连接控制器后，电池报告会报告高于实际水平。 等待大约15秒钟，让电池电量稳定，然后阅读该级别。
11. **> 设备 > 蓝牙 & 其他设备** 中删除蓝牙耳机和扬声器，并关闭设备。 在混合现实耳机上使用耳机插孔或内置扬声器获得最佳音频体验。
12. 如果你有与电脑配对的其他蓝牙设备，如耳机或 gamepads，请将其删除。 选择 " **设置" > 设备上 > 蓝牙 & 其他设备** "，选择设备，然后选择" 删除设备 "。
13. 拔出耳机上的 USB 电缆，并将其重新插回计算机，以便在电脑上重新启动控制器功能。
14. 当控制器正在进行固件更新时，它会闪烁。 等待固件更新完成，控制器应显示为混合现实。
15. 确保你的电脑已连接到 5GHz Wi-fi 网络。 如果便携式计算机连接到 2.4 GHz Wifi 网络，则通常会共享蓝牙连接。 这可能会对 Wifi 或蓝牙性能产生负面影响，具体取决于产品设计。 在网络适配器设置中将首选带区更改为5Ghz。 如果网络不支持5GHz，则可以使用蓝牙转换器，而不是使用内部蓝牙功能。
16. 如果你的蓝牙设置已经配对了运动控制器，则在删除这些设备之前，Windows 将不会发现这些新设备 (如果已使用特定的转换器添加这些设备，则只能使用该转换器) 来删除它们。
17. 如果你的电脑具有内置的蓝牙，并且你有连接问题，请尝试改用 USB 蓝牙适配器。 为此，需要在设备管理器关闭内置蓝牙无线电，然后将其他蓝牙设备与新的适配器配对。

### <a name="motion-controller-troubleshooting-flowchart"></a>运动控制器疑难解答流程图

![运动控制器的疑难解答流程图](images/motion-controllers.jpg)

### <a name="my-controller-is-stuck-in-an-infinite-reboot-buzzing-after-leds-cycle"></a>) Led 循环后，控制器停滞在无限重启 (。

这是一个关键电池指示器，因此请确保设备中有新电池。 如果问题仍然存在，请执行 [设备恢复](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) ，将控制器重置为出厂设置。

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>我尝试配对控制器，但它们永远不会显示在蓝牙设置的 "添加新的设备菜单" 中。

请检查是否已将控制器配对，请将其删除，然后重试。 如果问题仍然存在，请重新启动计算机，然后重试。 如果失败，请参阅 [蓝牙常见问题解答](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。

### <a name="wi-fi-speeds-becomes-slow-on-my-notebook-when-motion-controllers-are-turned-on"></a>当动作控制器开启时，笔记本的 wi-fi 速度会变慢。

当连接到 2.4 GHz 接入点时，笔记本可能与蓝牙共享其 Wi-fi 天线。 如果可以将带区首选项切换到5GHz，请从设备管理器中进行检查。 如果5GHz 网络不可用并且性能受到严重影响，请考虑使用蓝牙转换器。

![可以通过设备管理器找到 Wifi 波段选择设置](images/wifi5ghz.png)

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>第二个控制器需要很长时间才能重新连接。

如果同时打开了运动控制器，某些较早的 Intel 无线电系统会出现此问题。 避免同时打开控制器。

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>在电脑崩溃后，Qualcomm 蓝牙无线电无法配对控制器。

Qualcomm (QCA) 在 Windows 崩溃后，10.0.0.448 之前的蓝牙无线电驱动程序可能会以错误状态结束。 完全关闭 PC 以解决此问题。 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>我通过 Marvell 收音机遇到控制器跟踪问题。

请参阅 **设备管理器 > 蓝牙 > MARVELL AVASTAR 蓝牙无线电适配器 > 属性 > 驱动程序** ，并确保使用的是 driver 15.68.9210.47 或更高版本。

### <a name="the-mixed-reality-portal-is-working-but-my-motion-controllers-are-tracking-poorly-controllers-keep-flying-away-shaking-etc"></a>混合现实门户正在运行，但运动控制器跟踪性能不佳 (控制器保持飞行、摇动等 ) 。

1. 某些照明条件可能会影响跟踪。 请确保未向直射直射，并确保您的 HMD (看不到很多的点光源，例如，如圣诞节树) 的灯光字符串。 
2. 查看 [蓝牙常见问题解答](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。 这些症状通常是由于控制器与主机之间的通信失败引起的，并指示蓝牙链接质量较差。

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>运动控制器 Led 未亮起，但按钮和操纵杆仍适用于混合现实门户。

运动控制器校准缓存可能已损坏。 若要删除缓存，请在管理员命令提示符下运行以下命令：

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

此文件夹在 Windows 资源管理器中不可访问，只能从管理员命令提示符中修改。 删除文件夹后，请重新启动计算机，然后重新连接运动控制器以还原校准文件。

### <a name="motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>运动控制器不会出现在 SteamVR 的应用和游戏中。

如果可以在 cliff 房子中看到运动控制器，而不是在 SteamVR 应用和游戏中查看，则可能是运动控制器型号驱动程序安装不正确。 此驱动程序通过 Windows 更新自动下载和安装，但如果你在具有企业策略的 PC 上，或者如果 Windows 更新受到限制，则可能需要手动安装此驱动程序。 检查运动控制器型号驱动程序是否正确安装：
1. 打开这两个运动控制器，并确保它们在 "设备" 下的 "设置" 应用中显示为 "已连接" **> Bluetooth & 其他设备** 。 如果它们没有显示，或者显示为 "配对"，请将 [它们配对](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality)。
2. 打开设备管理器并在 "蓝牙" 下查找 "运动控制器-左" 和 "运动控制器-右"。
3. 选择任一设备，然后 **按连接查看 > 设备** "。
4. 现在，你将看到动作控制器蓝牙设备的视图汇总到蓝牙收音机。 在与两个运动控制器相同的节点下，应该有两个 "蓝牙 HID 设备" 设备，并且在每个蓝牙 HID 设备下，都应该是名为 "运动控制器" 的设备，并) 灰色图标 (。
5. 双击每个 "运动控制器" 设备，然后单击 " **驱动程序** " 选项卡。确认列出的驱动程序版本与 [其中一个运动控制器型号驱动程序版本](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history)相对应。

若要手动下载和安装运动控制器模型驱动程序，请访问 [此页](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) ，并查找与你的 Windows 10 版本对应的驱动程序版本。 下载页上提供了安装说明。

### <a name="the-motion-controllers-firmware-update-takes-significantly-longer-than-two-minutes"></a>运动控制器固件更新所需的时间明显超过两分钟。

查看 [蓝牙常见问题解答](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。 通常不太常见的蓝牙链接质量导致了这些问题。

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>我刚插入了新电池，但控制器虚拟电池电量不表示完全水平。

为 AA 电池调整了运动控制器电池电量水平。 即使完全充电，某些低电压充电电池也可能不会报告为完整。

### <a name="my-controller-does-not-vibrate-when-battery-is-low"></a>当电池电量低时，控制器不振动。

电池电量降低时，将禁用 Haptics。 更换电池。

### <a name="my-device-vibrated-three-times-and-then-shutdown"></a>我的设备 vibrated 三次，然后关闭。

电池电量不足，并达到切削阈值。 更换电池。

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>我的 Samsung 运动控制器的触摸板处于离线状态或具有死点。

这可能是硬件缺陷，应返回给零售商或设备制造商提供更换或交换。

### <a name="the-controller-isnt-working-correctly-and-i-cant-update-the-device"></a>控制器工作不正常，无法更新设备。

将其还原为出厂条件 (需要全新电池) ：
1. 拔出并关闭控制器电源。
2. 打开电池盖子。
3. 插入新电池。
4. 按住 "配对" 按钮 (电池) 下底部的选项卡。
5. 按住 "配对" 按钮时，通过按住 Windows 按钮5秒钟来打开控制器， (使这两个按钮按下) 。
6. 释放按钮并等待控制器开启。 这最多需要15秒的时间，并且在发生设备恢复时不会出现任何迹象。 如果设备在立即开机，则表明 "恢复" 按钮序列未注册，需要重试。
7. 中转到 " **设置" > bluetooth > 其他设备** "，然后选择" 运动控制器-左 "或" 运动控制器-右 "和" 删除设备 ") ，从蓝牙设置中删除旧的控制器关联。 
8. 再次将控制器与电脑配对。
9. 连接到主机和 HMD 后，设备将更新到最新的可用固件。

### <a name="lights-and-indicators"></a>光源和指示器

LED 星座环形和 haptics 指示运动控制器的状态。

| 状态    | 导致状态的原因 | 与状态关联的光线和振动行为 |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **开机**               | 按住控制器上的 Windows 按钮两秒钟，以打开控制器。       | Led 打开，控制器 vibrates 一次。 |
| **关机**              | 按住控制器上的 Windows 按钮四秒钟以关闭控制器。      | Led 关闭，控制器 vibrates 两次。 |
| **Sleeping**               | 当控制器 motionless 30 秒时，控制器会自动进入睡眠状态。 控制器在检测到运动时将自动唤醒，但设备未与主机 PC 配对的情况除外。 在这种情况下，需要按按钮才能唤醒。 | 处于睡眠状态时，指示灯关闭并每隔三秒闪烁一次。 |
| **组合**                | 在电池大小写内按住配对按钮三秒。     | Led 在配对模式下缓慢脉冲，并在退出配对模式时转为稳定状态。 如果配对成功，则控制器 vibrates 一次; 如果配对失败并超时，则为 vibrates 三次。 |
| **控制器连接/断开与电脑的连接** | 控制器成功连接后，控制器已成功连接到 PC，或在使用时控制器断开连接，因为某种原因。| 控制器 vibrates 计算机连接或断开连接。 |
| **低电池电量水平**      | 电池电量低。| 电池电量不足时没有 LED 或振动指示。 耳机上控制器表示形式的句柄上有一个电池指示器图标。 当电池电量低时，指示器图标将显示1/4。 |
| **严重电池电量水平** | 当电池电量为 "关键" 时开机。 "严重" 电池电量表示电量不足，控制器将自动关闭。| 控制器 vibrates 三次，并在打开时自动关闭。 当你使用此状态时，电池指示器图标将显示红色。 |


### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>如何判断我是否在使用蓝牙技术？

运动控制器使用在许多消费者设备中找到的相同蓝牙技术，其设计目的是使用任何最近的 PC 中包含的蓝牙功能。 若要验证你的计算机是否具有蓝牙无线电 (设备是否已通过混合现实兼容性检查器) ： 
* 右键单击 Windows "开始" 菜单，然后选择 "设备管理器"。 
* 展开 "蓝牙" 部分，并查找适配器。 
* 如果你的电脑没有蓝牙，则建议使用一个 [PLUGABLE USB 蓝牙4.0 低能量微适配器](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom)。
![示例设备管理器的屏幕截图。 适配器是蓝牙收音机。](images/devicemanagerbtadapterpic.png) 


### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-motion-controllers"></a>我的 PC 具有蓝牙技术，但我的运动控制器有问题。

动作控制器应与其他蓝牙键盘、鼠标和游戏控制器一起工作，但体验会因使用的键盘、鼠标或游戏控制器的型号而异。 可以执行以下操作来提高性能：
* 如果你的计算机具有蓝牙功能，但运动控制器仍有问题，请考虑将蓝牙无线电替换为插入到 USB 的 Plugable 外部蓝牙适配器。 请注意，一次只能有一个蓝牙无线电适配器处于活动状态。 如果除了插入现有收音机外，还插入外部广播，则需要在设备管理器中禁用现有蓝牙无线电 (右键单击该适配器，然后选择 "禁用设备" ) 并取消对以前的所有蓝牙设备的配对。
* 如果使用的是 USB 蓝牙适配器，请将其连接到 USB 2.0 端口 (2.0 端口为黑色，未标记为 "SS" ) （如果可用）。 端口应以物理方式与以下内容分开：
    - HMD USB 连接器
    - 闪存驱动器
    - 硬盘驱动器
    - 无线 USB 接收器（如键盘/鼠标键盘的理想接收方）理想情况下，从这些其他连接器将 USB 蓝牙适配器插入到计算机的另一侧。
* 不要安装任何第三方软件。
* 关闭蓝牙设置窗口（如果已打开）。 使其在后台处于打开状态，这意味着需要对蓝牙协议进行大量的额外调用。
* 禁用蓝牙 & "其他设备" 下的 "显示通知以便使用 Swift 对进行连接" 设置，以减少主机收音机扫描活动。
* 如果使用的是内部蓝牙卡，请确保使用的是外部蓝牙天线。 
  * 在这种情况下缺少外部蓝牙天线会导致跟踪问题。 
  * 如果此操作不起作用，请在禁用内部蓝牙后 (USB) 使用外部蓝牙转换器。
* 设备在蓝牙设置中的 "鼠标、键盘 & 笔" 类别下出现，这一点很重要。 如果在 "其他设备" 下，则取消配对并配对设备。
* 删除、取消配对蓝牙耳机和扬声器电源。 Windows Mixed Reality 不支持这些。 可以在混合现实耳机上使用耳机插孔或内置扬声器获得最佳音频体验。

### <a name="how-can-i-pair-my-motion-controllers-to-a-windows-mixed-reality-headset-with-built-in-bluetooth-radio-or-return-them-to-their-factory-pairing"></a>如何将我的运动控制器与内置蓝牙收音机的 Windows Mixed Reality 耳机配对，或将其返回给工厂配对？

某些 Windows Mixed Reality 耳机，包括 Acer OJO 500 和 Samsung 太空 +，内置蓝牙无线电收发器用于运动控制器。 这些耳机附带的运动控制器与工厂中的耳机预配对，无需您的 PC 具有单独的蓝牙收音机。 例如， _可以_ 将这些运动控制器手动配对到您的 PC 的蓝牙无线电设备，以与没有内置蓝牙无线电收发器的 Windows Mixed Reality 耳机配合使用。 若要将运动控制器返回到工厂配对，或将其与带有内置蓝牙收音机的 Windows Mixed Reality 耳机配对，请运行耳机的设备附带应用 (例如，"Acer OJO 500" 应用或 "Samsung HMD 太空 + 安装" 应用程序，在首次将耳机插入) 时自动安装，并按照运动控制器配对的说明进行操作。


## <a name="performance-questions"></a>性能问题

### <a name="how-can-i-tell-if-the-windows-mixed-reality-headset-is-rendering-at-60hz-or-90hz-framerate"></a>如何判断 Windows Mixed Reality 耳机是否以60Hz 或90Hz 的帧速率呈现？

检查 **设备门户 > 性能** "选项卡。 

**注意** ：如果有与 HDMI 2.0 端口的离散 GPU 和具有4个或更多物理内核的 CPU，则应该获得 90 Hz。 如果 GPU 仅有 HDMI 1.4 输出，可以使用 DisplayPort 到 [HDMI 2.0 适配器](https://holodocswiki.com/wiki/Recommended_adapters_for_Windows_Mixed_Reality_Capable_PCs) 作为解决方法。 

**注意** ： **耳机显示 > 视觉质量设置** 仅影响 Windows Mixed Reality 主体验的呈现。

### <a name="what-do-i-do-if-my-pc-appears-to-be-running-slowly"></a>如果我的 PC 看起来运行缓慢，我该怎么办？

由于许多原因，系统可能会缓慢，在大多数情况下，这会在几秒钟后下降。 如果在很长一段时间内遇到此问题：
1. 关闭桌面上所有未使用的应用程序。
2. 确保便携式计算机已插入电源。
3. 确保电脑未预热。
4. 降低 Windows Mixed Reality 主页的视觉质量。
5. 请确保具有最新的 PC 图形驱动程序 (参阅图形驱动程序部分) 。

### <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>我的 PC 正在预热，因为我运行了混合现实体验。 如何实现将其设置为酷？

1. 确保电池已充电并接通电源。
2. 请确保未阻止吹入或移出电脑的风扇。
3. 在相对较酷的环境中使用 PC。
4. 请确保没有热源 (例如，sun 或热通风口) PC。

### <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>我的视觉对象不连贯、负载缓慢或外观不佳。
* 请确保将耳机插入 PC 上的正确图形卡。 某些 Pc 同时具有集成显卡和离散显卡。 离散卡通常会提供最佳性能。 [了解有关 PC 硬件的详细信息](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)。
* 关闭桌面上未使用的应用程序。
* 请确保你的头戴显示 snugly (向下移动，或者向左和向右移动以调整) 。
* **> 混合现实 > 耳机显示** ，在 "设置" 中调整耳机的视觉设置。 当 "视觉质量" 设置为 "自动" 时，我们将为你的电脑选择最佳混合现实体验。 若要获得更多视觉细节，请将 "视觉质量" 设置为 "高"。 如果你的视觉对象不连贯，你可能想要选择较低的设置。
* 尝试调整头戴显示设备的校准。 应对重用功能区进行调整，使之与你的 interpupillary 距离 (IPD) ，瞳孔之间的距离。 如果你不知道 IPD，optometrist 应能够为你衡量。 此外，还设计了用于度量 IPD 的网站。 了解 IPD 后，请使用耳机的校准旋钮进行调整。 如果耳机没有校准旋钮，请选择 " **设置" > 混合现实 > 耳机显示** 并调整 "校准控制"。


## <a name="tracking-system-problems"></a>跟踪系统问题

### <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>系统找不到边界，并显示了安装程序 UI。

这意味着跟踪系统无法识别您的环境。 如果你在新的环境中，则必须设置 [边界](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)。 如果以前在此环境中使用了该设备，并设置了边界：
* 请确保空间充足。
* 请确保已使设备磨损，并看看房间。 设备必须观察您的环境，以了解它的位置。 如果你的边界位于办公桌或表上，则它将找不到边界。
* 拔出设备，关闭 Windows Mixed Reality，并再次插入设备。
* 环境中的某些内容可能已更改，设备不再识别。 尝试设置新边界。

如果这些步骤不能解决问题，请删除环境数据并再次设置边界。

### <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>系统向我提供 UI，要求我为所有经验或已安装/所有经验选择设置，并且我看到我的界限。

设备查找界限所用的时间太长。 你可以通过选择使用边界的选项来绕过此消息，并且你将在你的边界存在的情况下进入 Windows Mixed Reality 主页。

### <a name="i-frequently-see-a-message-saying-ive-lost-my-bounds"></a>我经常会看到一条消息，指出 "我已经失去界限"。

跟踪系统正在跟踪并识别您的环境。 在此状态下，设备将不再显示你的边界，并且头戴式耳机切换到3DOF，使你能够在实际定位边界之前碰撞到现实世界中的东西。 解决方法：
1. 请确保房间具有足够的光线。
2. 如果最近 redecorated 或重新建模房间，请重新运行安装程序。
3. 拔出设备，关闭 Windows Mixed Reality，并再次将其插入。
4. 清除环境数据并再次设置设备。
5. 如果消息仍然存在，请与客户支持联系。

### <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>我可以找出，但无法转换 (我在 3DOF) 。

这意味着跟踪系统无法生成姿势，或应用程序已停止使用新的姿势数据来呈现。 检查下列项目：
* 请确保空间充足。
* 请确保会议室有足够的详细信息可供跟踪。
* 拔出设备，关闭 Windows Mixed Reality，并再次插入设备。
* 如果消息仍然存在，请联系客户支持部门

### <a name="the-view-in-the-hmd-is-completely-frozen"></a>HMD 中的视图被完全冻结。

这通常意味着应用程序或系统级组件发生了故障。 尝试执行以下操作：
1. 按 "home" 按钮退出应用程序。
2. 拔出设备，关闭 MRP 并重新插回设备。
3. 重启电脑。

### <a name="i-frequently-see-a-black-border-around-the-edges-of-the-view-in-the-hmd-sometimes-it-looks-like-im-looking-down-a-tunnel"></a>我经常在 HMD 的视图边缘周围看到黑色边框。 有时，似乎正在按下一个隧道。

这意味着应用程序不能在您的 PC 上击中帧速率，系统使用旧帧在 HMD 中呈现视图。 由于应用程序仅呈现您正在查看的世界部分，因此，如果这些应用程序不一直达到帧速率，则系统将尝试继续从以前的视图开始渲染世界，并使用黑色填充缺少的详细信息。 如果经常发生这种情况：
1. 关闭或终止所有不需要的程序以释放内存和 CPU。
2. 减少应用程序中的详细信息设置。
3. 减小 Windows Mixed Reality 设置中的详细信息设置。

### <a name="the-view-in-the-hmd-is-jittering-and-stuttering-a-lot"></a>HMD 中的视图是 jittering 和断断续续。

出现这种情况的原因有多种。 主要原因是系统无法将内容呈现给耳机，或者跟踪系统遇到问题。 检查下列项目：
1. 请确保您的 PC 不受资源争用。 打开任务管理器并确保计算资源是免费的 (例如，80% CPU free，ram 和磁盘 IO 的400MB 低于 80% ) 。
2. 请确保你具有适用于你的硬件的最新图形驱动程序。 有关详细信息，请参阅图形驱动程序部分。
3. 请确保空间充足。
4. 拔出设备，关闭 Windows Mixed Reality，并再次插入设备。
5. 重启你的计算机。
6. 如果问题仍然存在，请与客户支持联系。

### <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-before-returning-to-normal"></a>在返回到 normal 之前，世界上的冻结，可能会短暂地倾斜或翻转。

这可能是由于应用或系统级别组件出现严重错误，或者暂时缺少内存或 CPU 资源。 检查下列项目：
1. 打开 "任务管理器"，确保至少有20% 的 CPU 可用内存和400MB 内存可用 (例如，80% CPU 可用空间，ram 和磁盘 IO 的400MB 低于 80% ) 。
2. 打开 "事件查看器"，并在冻结时间附近，跳到 " **Windows 日志" > 应用程序和错误** 事件项。 检查是否有任何进程崩溃。
3. 如果此问题仍然存在，请尝试重启电脑。

### <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>世界翻转并返回到正常状态。

这通常是由于从耳机获取传感器数据以通知跟踪算法时出错引起的。 如果经常发生这种情况：
1. 将耳机插入到其他 USB 3.0 端口。
2. 将耳机直接插入 PC，而不是 USB 3.0 集线器。
3. 如果问题仍然存在，请与客户支持联系。

### <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-fine-in-windows-mixed-reality"></a>世界是倾斜的，但我可以在 Windows Mixed Reality 中进行导航和演练。

这通常是由将传感器数据错误记录到电脑上存储的环境数据中引起的。 这可能会导致 Windows Mixed Reality 显示为倾斜，有时会永久显示。 请尝试以下做法：
1. 拔下 HMD，关闭 Windows Mixed Reality 并插上耳机。
2. 重启电脑。
3. 清除你的环境数据。

## <a name="webvr-questions"></a>WebVR 问题

### <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>从边缘查看 VR 内容时为什么看不到我的控制器？

并非所有 WebVR 内容都是为支持运动控制器而编写的。 WebVR 允许内容开发人员支持不同类型的输入，例如游戏控制器或运动控制器。 如果你在站点上看不到控制器，则它可能不支持移动控制器。

### <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>为什么无法在沉浸式 WebVR 视图中使用鼠标？

这是 WebVR 规范的一项可选功能。 并非所有浏览器都支持此功能，并且并不是所有的 WebVR 内容都是为了支持鼠标输入而编写的。 WebVR 允许内容开发人员支持不同类型的输入，例如鼠标、键盘、游戏控制器或运动控制器。 鼠标输入行为因浏览器而异。 在 Microsoft Edge 中，网站作者必须确保在向耳机提供时使用 "pointerlock" 才能正常工作。

### <a name="why-does-my-controller-look-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>为什么控制器看上去类似于 Naopak/Oculus，有奇怪的方向，或按钮映射不正确？

该网站可能没有完全的动作控制器支持。

### <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardiannew-york-times-etc-from-edge-in-vr"></a>为什么我不能从 Youtube/Facebook/Vimeo/监护人/纽约时间等中查看360学位视频？

就像任何其他 web 规范或标准一样，作者也可以选择实现它。 WebVR 规范允许网站直接从浏览器启动 VR 体验，这些网站的作者目前尚未实现此规范。 在某些平台上，可以使用可下载的应用来查看这些供应商的 VR 内容。

### <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>为什么无法从 Firefox 或 Chrome 进入 VR？

目前，Windows Mixed Reality 设备目前仅支持 WebVR。

### <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>当我从网站输入 "VR" 时，为什么我在我的耳机中看到了空白屏幕？

网站可能未实现对多 GPU 计算机的支持 (包括混合 GPU 便携式计算机) 。 尝试执行以下操作：
* 重载页面。
* 在台式计算机上，将耳机插入与显示 Microsoft Edge 的监视器相同的图形适配器中。 将两者插到更高的显卡，而不是集成图形适配器中。

### <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>当我在观看从边缘观看视频时退出 VR 时，声音将继续播放，但边缘窗口灰显。

这是在混合现实 cliffhouse 中从边缘运行 WebVR 时的已知问题。 若要解决此问题，请按键盘上的 esc 键，而不是按 windows 按钮退出 WebVR 体验，或通过选择并停止视频来激活灰显边缘窗口。

### <a name="can-i-use-webvr-on-the-hololens"></a>能否在 HoloLens 上使用 WebVR？

Microsoft 目前还没有在 HoloLens 上公布有关 WebVR 的任何信息。

### <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>从边缘查看 WebVR 内容时，为什么我的视图处于地面级别？

网站未正确支持 Windows Mixed Reality 耳机。 要解决此问题：
1. 将耳机置于空间的基底。
2. 使用 Microsoft Edge 在桌面上导航到 WebVR 页面， (不在混合现实) 内。
3. 单击网页上的按钮进入 "VR"。
4. 请等待5-10 秒钟，让体验完全进入沉浸式模式。
5. 拿起耳机，将其放在您的头上。

### <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>在某些 WebVR 体验中，显示器的分辨率非常低。

网站未正确支持高分辨率耳机。 解决方法：
* 如果从桌面 (而不是从混合现实 cliffhouse) 中启动 WebVR，请在进入 VR 之前确保窗口最大化。
* 输入 VR 后，请避免调整 Microsoft Edge 窗口的大小。

### <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>为什么当我更改浏览器选项卡时，WebVR 沉浸式视图退出？

这是预期的行为。 出于安全原因，只有活动的浏览器选项卡可以访问连接的耳机。

### <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>为什么听不到特定 WebVR 体验的音频？

网站可能使用的是 Microsoft Edge 当前不支持的 OGG 音频文件格式。

你可以在 [问题跟踪](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)程序中直接向 Microsoft Edge 浏览器团队报告断开的网站，也可以通过 twitter 使用 [#EdgeBug 井号标签](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)来向其报告。

### <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>为什么 Haptic 的反馈在 WebVR 中不能与运动控制器一起使用？

Microsoft Edge 目前不支持 WebVR 游戏板 API 扩展上的 haptics。


## <a name="steamvr-questions"></a>SteamVR 问题

### <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-immersive-headset"></a>如何在 Windows Mixed Reality 沉浸式耳机上播放 SteamVR 游戏？

你必须在你的电脑上安装适用于 SteamVR 的 Windows Mixed Reality 并设置 SteamVR：
* [下载并安装 SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)。
* 启动 SteamVR。 SteamVR 教程应该会自动启动。
* 将耳机连接到电脑，并打开运动控制器。
* 加载 Windows Mixed Reality 主页并显示控制器后，请在桌面上打开流应用。
* 使用流应用从您的流库中启动 SteamVR 游戏。 若要在不停用耳机的情况下启动 SteamVR 游戏，可以在 Windows Mixed Reality 的 " **开始" > 所有应用** 中找到并启动它们。 

### <a name="i-get-a-message-that-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>我收到一条消息，显示 "要将 SteamVR 与 Windows Mixed Reality 一起使用"，则需要安装最新的 Windows 更新 "或" 必需的 Windows 开发人员模式 "。

1. 确保你的计算机运行的是最新版本的 Windows 10。 若要查看此信息，请参阅 " **设置" > 系统 > 关于** 。 在 "Windows 规范" 下，确保 "OS Build" 为16299.64 或更高版本。
2. 请确保没有任何等待下载或安装的更新。 请参阅 " **设置" > 更新 & 安全 > Windows 更新** ，然后选择 "检查更新"。 可能需要多次检查更新，以便继续检查更新，直到没有更多更新可用，然后重启电脑。

### <a name="steamvr-is-crashing-after-updating-windows"></a>更新 Windows 后，SteamVR 崩溃。

SteamVR 的某些较旧版本的 Windows Mixed Reality 不再与 Windows 兼容。 对于 SteamVR，可能有旧版本的 Windows Mixed Reality。 若要确保你是最新的：
1. 在您的流库中，请参阅 **软件 > Windows Mixed Reality For SteamVR** 。
2. 右键单击它并跳到 "属性"。
3. 选择 "更新" 选项卡，然后选择 "始终保持此应用程序最新"。
4. 转到 "本地文件" 选项卡，然后选择 "验证应用程序文件的完整性" 来强制更新。
5. 重新启动流和 SteamVR。

如果在更新后 SteamVR 仍崩溃，则可能会在计算机上为 SteamVR 安装两个 Windows Mixed Reality。 若要确认是否属于这种情况：
1. 找到%localappdata%\openvr\openvrpaths.vrpath 并在记事本中打开它。
2. 在 "外部驱动程序" 部分，查找 "MixedRealityVRDriver" 的多个条目 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. 如果看到多个条目，请删除这两个条目中较早的条目。 请注意，如果只有一个条目，则行末尾不应再有逗号，例如：
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. 保存文件并将其关闭。
5. 重新启动流和 SteamVR。

### <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>我的控制器在 SteamVR 中不能按预期方式工作。

1. 关闭 SteamVR。
2. 返回到混合现实回家，确认控制器正在按预期方式工作。
3. 再次启动 SteamVR 体验，控制器应恢复正常。
4. 如果问题仍然存在，请使用 [Windows 反馈中心](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) 在混合现实类别下提供反馈，并在摘要中包括 SteamVR。

请注意，在不同的游戏中，你将以不同的方式使用移动控制器。 下面是一些可帮助你入门的基础知识：
* 若要打开 "流" 仪表板，请在左侧操纵杆上按 "向下"。
* 若要退出 SteamVR 游戏并返回到 Windows Mixed Reality 主页，请按 Windows 按钮。 然后选择屏幕上显示的混合现实主页按钮。

### <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>在 SteamVR 中，我的左控制器和右控制器反转。

关闭控制器并将其左移，然后将其左移一，然后将其打开。

### <a name="my-games-are-running-slowly"></a>游戏运行速度缓慢。

1. 确认你的电脑满足 Windows Mixed Reality 中 SteamVR 的规范
2. 确认你的电脑满足你正在播放的 SteamVR 游戏的规格。
2. 在桌面上的混合现实门户中，选择 "暂停" 停止桌面预览。
3. 按照上述说明确保你运行的是 Windows 10 内部版本16299.64 或更高版本。
4. 请确保您的 PC 具有最新的图形驱动程序。
5. 检查任务管理器以查看您的计算机上可能正在运行的其他进程并使用资源。
6. 检查流是否正在后台下载游戏。 这可能会消耗资源并使游戏运行不佳。
7. 存在一个已知的性能问题，它会影响一小类不具有可见窗口的应用程序，例如 SteamVR Home。 大多数应用不属于此类别，并且在将来的更新中会提供修补程序。

如果仍遇到意外性能问题，请使用 Windows 反馈中心向我们发送反馈。 请确保按照说明操作以 [包含 SteamVR 性能跟踪](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)。 

### <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR 显示了一个组合器错误 (例如，"Shared IPC 合成器 Connect Failed (400) " ) 。

存在一个已知问题，如果头戴显示在两个不同的视频适配器上，可能会发生这种情况。 将监视器连接到与耳机相同的适配器，并将该监视器配置为 "设置" 应用中的主监视器 **> 系统 > 显示** 。

### <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>SteamVR 内容显示在错误的位置，例如，位于其下的地面或上方。

重置位置： 
1. 单击左侧控制器的操纵杆，打开 "SteamVR 仪表板"。
2. 选择 "设置" 按钮。
3. 选择 "重置固定位置"。

### <a name="my-steam-app-closed-unexpectedly"></a>我的流应用意外关闭。

如果你锁定电脑屏幕、删除头戴显示设备、切换用户或电脑进入睡眠状态，则流应用将关闭。


## <a name="speech-and-audio-problems"></a>语音和音频问题

### <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>我在我的耳机中听不到任何声音，或通过我的计算机而不是我的耳机播放声音。

* 如果沉浸式耳机不包含内置耳机，则需要将耳机连接到耳机上的音频插孔。 插孔通常位于耳机面板或重用功能区的后面。 如果找不到，请与你的耳机制造商联系。
* 某些音频耳机有物理按钮来控制音量。 如果音频不起作用，请检查卷是否已关闭或静音。
* Windows Mixed Reality 旨在在混合现实门户运行时通过沉浸式耳机播放声音，并已将耳机连接到该门户。 当你离开或翻转面板时，请关闭混合现实门户应用程序，或在15分钟内未使用该应用程序时，音频将切换到默认的 Windows 播放设备。 你可以在 "设置" 中更改此设置 **> 混合现实 > 音频和语音。**
* 请确保将音频耳机完全插入音频插孔。 特别要注意的是，Acer 耳机可能需要更多的警惕，以确保音频耳机始终处于插接方向。
* 检查音频耳机/麦克风是否已插入耳机，而不是计算机。
* Windows 声音控制面板只显示已启用的音频终结点，而不是已禁用的终结点。 当你不戴上耳机时，耳机音频设备将被禁用，因此你必须在 "声音控制面板" 中右键单击，然后选择 "显示已禁用的设备" 进行查看;设备名称为 "Realtek USB 2.0 音频"。 完成此操作后，可以将 "属性" 页中的名称更改为更容易识别的内容。 可以为播放和录制选项卡执行此操作。
* 如果音频在混合现实应用中不工作 (例如，Netflix) ，则这可能是由于已知问题导致的，该问题不会自动更新 Windows Mixed Reality 来匹配操作系统版本。 若要解决此问题并获得最佳混合现实体验，请转到 " **设置" > 更新 & 安全 > Windows 更新 > 检查是否有更新** 。

**注意：** Windows Mixed Reality 空间音频最适合用于直接内置或直接连接到沉浸式耳机的耳机。 连接到 PC 的 PC 扬声器或耳机可能不适用于空间音频。

**注意：** Windows Mixed Reality 不支持蓝牙音频耳机。

### <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>我遇到了突然发生的变化、音频丢失或嗡嗡声。

* 某些应用程序（包括许多通过 SteamVR 启动的应用程序）可能会在音频设备随着你开始或停止混合现实门户而发生变化时丢失音频或挂起。 打开混合现实门户应用以更正此错误后，请重新启动应用。
* 如果另一台多媒体 USB 设备 (如 web cam) 与 Windows Mixed Reality 耳机共享同一内部或外部 USB 集线器，则耳机音频插孔/耳机可能会偶尔发出声音或根本没有音频。 将耳机插入使用不同集线器的 USB 端口，或断开连接/禁用其他 USB 多媒体设备。
* 如果你注意到耳机上连接了耳机的噪音太大，则可能是电脑的 USB 集线器无法为 Windows Mixed Reality 耳机提供足够的电源。 如果发生这种情况，请立即提交 [反馈中心](https://docs.microsoft.com/hololens/hololens-feedback) bug。 解决方法有助于不使用扩展电缆，使用专用的外部电源 USB 3.0 集线器，或尝试在电脑上使用其他 USB 端口。

### <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>我的蓝牙音频耳机未按预期工作。

Microsoft 不建议将蓝牙音频耳机用于 Windows Mixed Reality。 蓝牙音频外设不适用于 Windows Mixed Reality 声音和空间音效，蓝牙音频耳机无法同时支持麦克风输入和立体声输出，因此，在使用 gamechat 或其他语音输入时，您不会听到立体声或 spatialized 声音。 蓝牙音频耳机还会对运动控制器体验产生负面影响。 

### <a name="sound-isnt-coming-from-expected-directions"></a>声音并非来自预期方向。

Windows Mixed Reality 主页包含的空间音质 (音频，这听起来像是来自家庭) 的应用。 当您从每个应用程序中翻到更近或更远的距离时，声音方向和级别会改变以使真实感更进一步。 下面是意外声音方向的一些原因： 
* 当你在家中打开并播放支持后台的音乐应用的音乐时 (例如，在家庭中) Groove 音乐，然后 (像游戏) 那样打开沉浸式的 它的显示时间可能大于之前，因为您与声音之间没有任何距离。
* 如果在使用 Windows Mixed Reality 耳机之前已在主机 PC 上启用 Cortana，则可能会丢失适用于 Windows Mixed Reality 主页中的应用的空间声音。 若要解决此问题，请在启动 Windows Mixed Reality 之前，在桌面的 "设置" 中将 "允许 Cortana 响应你好小娜" **> 设置** 为 "Sonic"，或者在 Windows mixed reality 主页的 "桌面应用" 窗口中启用 "Windows for 耳机"：
    1. 在桌面任务栏上左键单击扬声器图标，并从音频设备列表中选择它。
    2. 右键单击桌面任务栏上的扬声器图标，然后在 "扬声器设置" 菜单中选择 "Windows Sonic 用于耳机"。
    3. 为所有音频设备重复以下步骤， (终结点) 。

### <a name="speech-commands-are-not-working-as-expected"></a>语音命令未按预期方式工作。

* 若要使用语音命令，你的电脑上的语音和语言设置必须设置为 [Windows Mixed Reality 中支持的语言](https://support.microsoft.com/en-us/help/4039262/windows-10-mixed-reality-setup-faq#Languages)。 若要检查您的 Windows 语音和语言设置，请选择 " **设置" > time & language > 区域 & 语言** 和 **设置 > time & language > 语音** 。
* 如果耳机没有内置麦克风，则需要使用麦克风将耳机连接到耳机或电脑。 要使麦克风输入在您磨损时自动切换到你的耳机，请转到 " **设置" > 混合现实 > 音频和语音** ，并打开 "当我戴上耳机时，切换到耳机麦克风"。
* 某些音频耳机有一个 "物理" 按钮，可将麦克风静音并取消静音。 如果语音命令不起作用，请检查是否已将麦克风静音。
* 带有麦克风的音频耳机，dangles 从 earbud 电缆连接时，不能很好地在环境干扰的环境中执行语音命令。
* 首次在混合现实门户会话中调用 Cortana 时，Cortana 可能会很慢。 请参阅 " **设置" > cortana > 与 Cortana 交谈** ，并确保已启用 "允许 Cortana 响应你好 cortana"。
* 在某些电脑上，手机网络连接麦克风的默认语音捕获增益可能会设置得太低。 如果遇到不可靠的语音命令或听写，可以尝试运行麦克风安装疑难解答。 您可以通过 " **设置" > Time & Language > 语音** "来访问此疑难解答，然后在" 麦克风 "部分选择" 入门 "。 通过桌面应用在 Windows Mixed Reality 主页中完成此操作，同时戴上耳机，影响用于 Windows Mixed Reality 的麦克风。 选择疑难解答向导中的相应终结点。

### <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>我只有一个音频耳机，并想要将其用于桌面和耳机。

如果只有一个音频耳机并且没有内置耳机的耳机，请将音频耳机连接到主机 PC 而不是耳机。 然后关闭 MRP 设置中的 "切换到耳机音频"。

### <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>我要切换到杜比 Atmos 来寻找耳机。

Windows Mixed Reality 环境及其应用程序使用 Windows Sonic 实现耳机空间音频技术，该技术是为混合现实体验定制的。 其他空间音频技术（如耳机的杜比 Atmos）可应用于全屏应用程序（如 SteamVR 游戏，但不适用于 Windows Mixed Reality shell 环境和应用程序 (例如，将 web 浏览器放置在 Cliff 房子的墙壁上，或在天空 Loft) 使用 Windows Sonic 实现耳机空间音效和噪音。


## <a name="questions-about-desktop-in-mixed-reality"></a>有关混合现实中的桌面的问题

### <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>如何实现在混合现实中访问我的 PC 桌面？
您可以使用桌面应用程序访问混合现实中的 PC 桌面。 从 Windows 的 "耳机" **按钮启动 > 所有应用 > 桌面** "。 

### <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>如何在混合现实中查看多个监视器？
默认情况下，桌面应用会自动切换为显示具有焦点的监视器。 如果要在混合现实中查看所有监视器： 
* 单击应用左上角的 "监视" 图标
* 禁用 "自动切换监视器"
* 选择要查看的监视器
* 启动桌面应用程序的另一个实例
* 选择要在该实例上查看的监视器 
* 对于所有物理监视器重复此操作，请注意，每次重新启动混合现实时，都必须重新选择要在每个桌面应用上显示的监视器。 

### <a name="my-desktop-app-only-shows-a-black-screen"></a>我的桌面应用程序只显示黑屏。
如果你的电脑具有 Nvidia 混合 GPU，则问题可能是由于 Nvidia 设备在离散 GPU 而不是集成的 GPU 上运行 runtimebroker.exe。 若要解决此问题，请按照 "[如何实现创建新程序的 Optimus 设置](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)" 下的说明操作。 添加 C:\windows\system32\runtimebroker.exe，并强制其在 "集成图形" 处理器上运行。 


## <a name="other-questions"></a>其他问题

### <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-getting-stuck"></a>我的 Samsung 太空或太空 + 耳机固件更新堵塞。

Samsung 拥有并发布通过其 "Samsung HMD 太空安装程序" 和 "Samsung HMD 太空 + Setup" 设备配套应用交付的耳机固件更新。 若要获得更多详细信息并了解 Samsung 固件更新问题，请联系 Samsung 客户服务。

如果固件更新过程停滞，而且没有进展超过五分钟：
* 暂时拔出所有其他 USB 设备，然后重试固件更新。
* 将 Samsung 耳机连接到电脑上的其他 USB 3.0 端口。
* 禁用和/或卸载任何可能会干扰固件更新的软件，例如千兆 AORUS App Center。
* 使用其他 PC 来执行 Samsung 耳机固件更新。

### <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>使用 Windows Mixed Reality 时，Wi-fi 会变慢。

如果使用的是 2.4 GHz Wi-fi 连接，则运动控制器可能会减慢 Wi-fi 的速度。 尝试以下任一项：
* 切换到 5GHz Wi-fi 连接（如果有）。 [了解详细信息](https://support.microsoft.com/en-us/help/4000461)。
* 使用单独的蓝牙适配器将运动控制器连接到您的 PC。 请参阅 [建议的适配器](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)。

### <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>我收到一条消息，指出我的 PC 已接通电源并向其收费。 为什么？

如果使用便携式计算机，则当电脑完全充电并接通电源时，Windows Mixed Reality 的效果最佳。 

### <a name="what-is-the-experience-options-setting"></a>什么是体验选项设置？

体验选项将 ( **设置 > 混合现实 > 耳机显示 > 体验) 选项** ，使你可以更改 Windows Mixed reality 性能设置。 这使你能够在一系列内容中为你的硬件配置选择可能的最佳体验。 90Hz 体验适用于所有系统，但你可能希望尝试自动查看所需的设置。 选项如下：
* 自动： Windows Mixed Reality 将确定硬件配置的最佳体验。 对于大多数人来说，这是开始的最佳选择。
* 60Hz：将刷新率设置为60Hz，并关闭某些功能，如混合现实门户中的视频捕获和预览。
* 90Hz：将刷新率设置为90Hz。

### <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality 支持哪些语言？

Windows Mixed Reality 提供以下语言版本。 如果你的电脑设置为另一种语言，你仍可以使用 Windows Mixed Reality，但界面将以英语 (美国) ，并且语音命令和听写将不可用。

* 简体中文（中国）
* 英语（澳大利亚）
* 英语（加拿大）
* 英语（英国）
* 英语（美国）
* 法语（加拿大）
* 法语（法国）
* 德语（德国）
* 意大利语（意大利）
* 日语（日本）
* 西班牙语(墨西哥)
* 西班牙语(西班牙)

Windows Mixed Reality 屏幕键盘仅适用于英语 (美国) 。 若要以另一种语言输入文本，请使用连接到电脑的物理键盘。 你还可以使用上面列出的受支持的 Windows Mixed Reality 语言之一来使用听写，只需在屏幕键盘上选择 "麦克风" 即可。

Windows Mixed Reality 还提供以下语言版本，无需语音命令或听写功能：

* 繁体中文 (台湾和中国香港) 
* 荷兰语（荷兰）
* 韩语(韩国)
* 俄语（俄罗斯）

### <a name="i-have-questions-about-my-headset-hardware"></a>我对我的耳机硬件有疑问。

有关手机支持的详细信息，请咨询制造商。 可以在框中提供产品指南，也可以尝试使用制造商的网站。


## <a name="how-to-uninstall-windows-mixed-reality"></a>如何卸载 Windows Mixed Reality

### <a name="how-do-i-uninstall-windows-mixed-reality"></a>如何实现卸载 Windows Mixed Reality？

1. 断开耳机与电脑的连接。
2. 关闭混合现实门户。
2. 请参阅  **开始 > 设置 > Mixed Reality** ，然后选择 "卸载"。

如果已准备好开始使用头戴显示，请将其插入，混合现实门户将引导你完成安装过程。

### <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>我收到了 "我们无法完成 Windows Mixed Reality 的卸载" 消息。

这意味着，某些文件（包括有关您的环境的信息）可能仍在您的计算机上。 如果你决定稍后重新安装 Windows Mixed Reality，这可能会导致问题。 你可以通过修改注册表并使用 Windows PowerShell 来运行命令，从你的电脑中手动删除任何剩余的 Windows Mixed Reality 信息。 _如果不正确地修改注册表，则可能会出现严重问题。请确保仔细执行这些步骤。为了增加保护，请在修改注册表之前对其进行备份，以便在发生问题时可以还原。_ 有关详细信息，请参阅 [如何在 Windows 中备份和 restory 注册表](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)。 

使用以下命令卸载 Windows mixed reality：
1. 重启你的电脑。
2. 在 **搜索** 框中，键入 "regedit"，然后选择 **"是** "。
3. 删除以下注册表值：
   <ul>
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>，然后删除 <b>FirstRunSucceeded</b>。</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic\speechandaudio</b>，然后删除 <b>PreferDesktopSpeaker</b> 和 <b>PreferDesktopMic</b>。</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\Holographic</b>，然后删除 <b>DisableSpeechInput</b>。 注意：必须在已使用 Windows Mixed Reality 的 PC 上为每个用户帐户删除 HHKEY_CURRENT_USER 中的注册表项。</li> 
    <li><b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\perceptionsimulationextensions</b>，然后删除 <b>DeviceID</b> 和 <b>Mode</b>。</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>，然后删除 <b>OnDeviceLearningCompleted</b>。</li> 
   </ul>
4. 删除以下注册表项： <ul>
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\ Speech_OneCore \Settings\HolographicPreferences</b></li><br/></ul>
5. 关闭注册表编辑器。
6. 导航到 **C:\users\ 用户名 name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** ，然后删除 **RoomBounds.json** 。 对已使用 Windows Mixed Reality 的每个用户重复此步骤。
7. 打开管理 cmd 提示符并导航到 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** 。 然后， (删除 " **HeadTracking data** " 文件夹的内容，而不) 的文件夹本身。
8. 在 **搜索框** 中键入 "powershell"，右键单击 " **Windows powershell** "，然后选择 "以 **管理员身份运行** "。
9. 在 Windows PowerShell 中，执行以下操作： <ul>
   <li>在命令提示符下复制并粘贴以下内容，然后按 Enter： <b>Dism/Online/Get-Capabilities</b></li> 
   <li>复制以 (开头的功能标识（如果它在此处没有&#39;），这意味着将不&#39;安装此项。 在这种情况下，请跳到步骤 10 ) 。</li> 
   <li>复制并粘贴以下命令提示符，然后按 Enter： <b>Dism/Online/Remove-Capability/CapabilityName：在上一步中复制的功能标识</b></li>
   </ul>
10. 重启电脑。




