---
title: 耳机连接常见问题
description: 高级 Windows Mixed Reality 耳机连接故障排除，超过了标准使用者支持文档。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，耳机
appliesto:
- Windows 10
ms.openlocfilehash: abdd0f04443e110f1eb19a31fb3d77e2f3bde929
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434548"
---
# <a name="headset-connectivity-faqs"></a>耳机连接常见问题

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>计算机没有 HDMI 和/或显示端口

可能需要使用适配器。 若要查看支持的适配器列表，请参阅 [此处](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 。

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>能否在 Windows Mixed Reality 耳机上使用 USB 或 HDMI 和/或 DisplayPort 扩展电缆？
Windows Mixed Reality 耳机不正式支持使用 USB、HDMI 或 DisplayPort 扩展电缆。 使用这些电缆可能会显著影响混合现实体验，因为在计算机的 USB 控制器与混合现实耳机之间产生的信号完整性和总线功率发生变化。 如果头戴式耳机短暂显示蓝屏，然后在使用过程中打开黑色和混合现实门户的重启或完全取消枚举，或者耳机音频切出或变为 glitchy，或者如果耳机在黑色和正确显示器之间闪烁，请尝试使用耳机，无需延长电缆。

## <a name="i-am-getting-a-check-your-display-cable-error"></a>我收到 "检查显示电缆" 错误

* 如果使用任何适配器将耳机连接到电脑，请确保它们支持 Windows Mixed Reality (适配器必须支持 4K) 。 将耳机连接到适配器之前，还要尝试将适配器连接到 PC。
* 尝试使用不同的 HDMI 和/或 DisplayPort 端口。
* 将耳机连接到 DisplayPort 1.2 或更高版本，1.4 或者连接到或更高版本。 确保端口与电脑上最先进的图形卡相对应。
* 如果你的电脑同时具有集成图形和离散图形，请确保在活动的图形卡上使用 HDMI 和/或 DisplayPort 端口。 这可能意味着需要将电脑显示器连接到非 HDMI 端口。
* 如果你的电脑同时具有集成图形和离散图形，并且集成的图形较旧且不支持 Windows Mixed Reality，请尝试禁用集成的 GPU。
* 将电脑监视器连接到电脑的 HDMI 和/或 DisplayPort 端口。 请确保图形驱动程序是最新的。 直接从 AMD、Nvidia 或 Intel 下载并安装它们，因为它们可能比发布到 Windows 更新的内容新。
* 如果将外部监视器连接到 HDMI 端口，请尝试将其插入 DisplayPort，并将 HDMI 端口用于耳机。
* 请确保已将耳机的 HDMI 电缆插到了 PC 上的 "HDMI out" 端口，而不是连接到 "HDMI" 端口。
* Windows 可能无法检测显示电缆连接。 打开设备管理器，查看耳机是否列在 "监视器" 下面。 否则，请选择 " **操作" > 扫描硬件更改**。 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>出现一条消息，显示 "放在你的耳机上"，但我的耳机已打开

当你放在你的耳机上时，Windows Mixed Reality 可能需要几秒钟才能重新加载空间。 如果此消息不会消失，请确保已从邻近感应传感器（位于重用功能区之间的耳机内）中删除了保护标签。 如果这不能解决问题，请与你的耳机制造商联系。

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>显示一条消息 "连接耳机"，但我已插入我的耳机

1. 请确保将耳机的 USB 和 HDMI 和/或 DisplayPort 电缆连接到电脑上的正确端口。 下面介绍如何识别正确的端口：
    * USB 3.0 端口有一个特殊的徽标，其中 "SS" 标记 (表示 "SuperSpeed" ) 。 端口的内部片通常为蓝色，而旧的 USB 2.0 端口通常在内部为黑色或白色。
    * 如果计算机有两个 HDMI 和/或 DisplayPort 端口，请使用连接到图形卡的端口，而不是计算机的主板。 这并不总是很明显，但不同的端口通常位于计算机上的扩展插槽中。 如果尝试一个端口但它不起作用，请尝试其他端口。
2. 从耳机拔下并插入 USB 和 HDMI 和/或 DisplayPort 电缆，确保它们已安全连接。 插入 USB 电缆时，请不要在插入 USB 电缆期间暂停。
3. 打开设备管理器并确认你的耳机是否列在 "Mixed Reality 设备" 下。 选择耳机后，设备状态应显示为 "此设备正常运行"。 设备上的黄色惊叹号设备管理器指示错误。
    * 如果在设备管理器中列出了 "Hololens 传感器" 并带有黄色惊叹号，请选择该设备。 如果出现 "代码10：未安装此设备的驱动程序"。 此设备没有兼容的驱动程序 "，请 [手动安装耳机驱动程序](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset)。
    * 如果你在电脑上使用多个混合现实耳机，并已手动安装混合现实耳机驱动程序，则手动驱动程序更新可能仅适用于当时连接的耳机，而不适用于其他耳机。 在这种情况下，你将看到 "代码31：此设备无法正常工作，因为 Windows 无法加载此设备所需的驱动程序"。  (代码 31) 。 设备管理器中的 ALPC 消息不再可用 "。 在 **设备管理器 > Mixed Reality 设备**上，右键单击耳机，然后选择 "卸载设备"。 选择 "确定" 以确认并拔出并 replug 你的耳机。
4. 如果你查看耳机的部分枚举 (一系列 USB 设备枚举，但设备管理器) 中 "Mixed Reality 耳机" 下没有任何内容，请尝试使用外部 USB 3.0 集线器。
5. 请参阅耳机制造商的网站并更新耳机的驱动程序和固件。
6. 将耳机连接到另一台电脑并打开设备管理器。 即使该 PC 与 Windows Mixed Reality 不完全兼容，你也可以查看你的耳机是否枚举。 如果耳机不在多台电脑上枚举，则可能存在硬件问题。

适用于 Surface 用户的备注： Surface Dock 的早期版本和 Surface Book USB 集线器固件更新软件与混合现实耳机不兼容。 如果在 Surface PC 上收到 "连接耳机" 消息，请检查是否有任何设备在设备管理器中报告了 "代码10：设备无法启动" 错误。 如果是这样，请 [删除冲突的驱动程序](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)。 只需执行此操作一次。

适用于 Windows 10 N 用户的说明：如果你的电脑运行的是 Windows 10 N，则在插入混合现实耳机后，你将看到 "代码28：安装类不存在或无效" 设备管理器错误。 Windows Mixed Reality 不支持 N 版本的 Windows 10。 有关详细信息，请按照这些 [说明](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 进行操作。

此信息也会显示在 [故障排除流程图](headset-connectivity-flowchart.md)中。

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>消息显示 "检查 USB 电缆" 或 "USB 速度不足"。

* 请确保使用的是计算机上受支持的 USB 3.0 端口：
    * 请确保将耳机的 USB 电缆全部插入。
    * 运行 [Windows Mixed Reality 门户](install-windows-mixed-reality.md#launch-mixed-reality-portal) ，确保你的 PC 的 USB 3.0 控制器受支持。
    * 将耳机连接到电脑上的其他 USB 3.0 端口。 某些电脑具有多个 USB 3.0 控制器。
    * 暂时断开连接到电脑的所有 USB 设备，并仅连接耳机。
    * 在自定义构建的 Pc 上，即使某个端口可能标记为 USB 3.0 端口，它也可能连接到 USB 2.0 控制器。 在手机网络连接上，打开设备管理器，找到并单击从耳机枚举的任何设备，然后参阅 **按连接查看 > 设备**"。
* 尝试在另一台电脑上戴上耳机。 如果其他 PC 与 Windows Mixed Reality 不完全兼容，请签入设备管理器查看 "USB 速度是否不足" 消息。 如果在多台电脑上无法正确枚举，则耳机可能出现故障。
* 删除耳机与计算机之间的所有扩展器或集线器。

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>我接通耳机后，混合现实门户没有启动。

可能由于根本问题而无法正确检测到耳机。 手动启动混合现实门户，并查找显示的任何错误消息。 

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>当我的电脑进入睡眠或休眠模式时，或者当我的戴戴戴显示在计算机上时，我的耳机停止工作。

1. 打开设备管理器并确认你的耳机是否列在 "Mixed Reality 设备" 下。
2. 在 "Mixed Reality 设备" 下选择你的耳机，并确认设备状态指示 "此设备是否正常运行"。
3. 如果出现 "代码 43" 错误，指出设备已停止工作，或者如果你没有在 "Mixed Reality 设备" 下看到你的耳机，请将其拔出，然后在你的耳机的 USB 电缆中拔出和 replug。 Microsoft 正在调查可能导致此错误的潜在软件/驱动程序互操作性问题。 此问题会影响少量 Pc，预计会在将来对混合现实耳机驱动程序的更新中得到解决。

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>我的耳机会使我的电脑在计算机进入睡眠状态或处于休眠模式时， (蓝屏) 生成 Bug 检查。
请确保位于10.0.18362.1062 驱动程序或更高版本。

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>接通耳机后，耳机驱动程序未自动安装。

在新电脑上，或安装有新安装的 Windows 10 副本的电脑上，耳机驱动程序可在其他 Windows 更新后排队，并且可能不会立即安装。 手动安装：
1. 请参阅 **开始 > 设备管理器** 并在 "其他设备" 下查看 "HoloLens 传感器" 设备的 "其他设备"，其中包含黄色感叹号： ![ 设备管理器 HoloLens 传感器的视图](images/hololenssensors.png)
2. 右键单击该设备，然后选择 "属性"。 如果设备的属性读取 "此设备的驱动程序未安装 (代码 28) "，请关闭该窗口，然后继续。 如果有另一条消息，请按照本页其余部分的故障排除步骤操作。
![设备管理器中的 HoloLens 传感器的代码28](images/code28.png)
3. 再次右键单击该设备，然后选择 "更新驱动程序 ..."然后，在设备更新后 "自动搜索更新的驱动程序软件"，你应会在设备管理器： ![ Mixed Reality 设备显示在设备管理器](images/mixedrealitydevices.png)

如果手动安装不起作用，或在其他设备下找不到该驱动程序，则可能需要卸载现有的驱动程序，然后重新安装它。 若要执行该操作：
1. 请参阅 **开始 > 设备管理器** 并在 "混合现实设备" 下查看头戴显示设备。 设备状态应指示 "设备正常运行"。
2. 右键单击该设备，然后选择 "卸载设备"。
3. 在出现的新弹出窗口中，选中复选框 "删除此设备的驱动程序软件"，然后选择 "卸载"。
4. 完成后，拔出电脑的耳机，并重新插回。 Windows 更新现在会下载并安装新的驱动程序。

注意：如果你有一个 N 版本的 Windows，则需要切换到 Windows 10 的常规版本以使用 Windows Mixed Reality。


