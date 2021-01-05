---
title: 耳机连接常见问题
description: 耳机连接 Windows Mixed Reality 耳机连接故障排除，超过了标准使用者支持文档。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，耳机
appliesto:
- Windows 10
ms.openlocfilehash: f42994561d032245f4f0345ad494eb38015f3682
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725588"
---
# <a name="headset-connectivity-faqs"></a>耳机连接常见问题

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>计算机没有 HDMI 和/或显示端口

可能需要使用适配器。 若要查看支持的适配器列表，请参阅 [此处](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 。

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>能否通过 Windows Mixed Reality 耳机使用 USB 或 HDMI 和/或 DisplayPort 扩展电缆

Windows Mixed Reality 耳机不正式支持使用 USB、HDMI 或 DisplayPort 延长电缆。 如果你正在使用这些电缆，则混合现实体验可能会受到影响，因为你的电脑 USB 控制器与混合现实耳机之间的信号完整性和总线功率发生变化。 如果是以下情况，请尝试在不使用分机线的情况下使用耳机
* 耳机显示短暂显示蓝屏，然后在使用过程中将黑色和混合现实门户重启或完全取消枚举
* 耳机音频切出或变为 glitchy
* 耳机在黑色和正确显示器之间闪烁

## <a name="i-am-getting-a-check-your-display-cable-error"></a>我收到 "检查显示电缆" 错误

* 如果正在使用任何适配器将耳机连接到电脑，请确保它们支持 Windows Mixed Reality 并且支持4K。 将耳机连接到适配器之前，还要尝试将适配器连接到 PC。
* 尝试使用不同的 HDMI 或 DisplayPort 端口。
* 将耳机连接到 DisplayPort 1.2 或更高版本，1.4 或者连接到或更高版本。 确保端口与电脑上最先进的图形卡相对应。
* 如果你的电脑同时具有集成图形和离散图形，请确保在活动的图形卡上使用 HDMI 或 DisplayPort 端口。 这可能意味着需要将电脑显示器连接到非 HDMI 端口。
* 如果你的电脑同时具有集成图形和离散图形，并且集成的图形较旧且不支持 Windows Mixed Reality，请尝试禁用集成的 GPU。
* 将电脑监视器连接到电脑的 HDMI 或 DisplayPort 端口。 请确保图形驱动程序是最新的。 直接从 AMD、Nvidia 或 Intel 下载并安装驱动程序，因为它们可能比发布到 Windows 更新的驱动程序更高。
* 如果将外部监视器连接到 HDMI 端口，请尝试将其插入 DisplayPort，并将 HDMI 端口用于耳机。
* 请确保已将耳机的 HDMI 电缆插到了 PC 上的 "HDMI out" 端口，而不是连接到 "HDMI" 端口。
* Windows 可能无法检测显示电缆连接。 打开设备管理器，查看耳机是否列在 "监视器" 下面。 否则，请选择 " **操作" > 扫描硬件更改**。 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>出现一条消息，显示 "放在你的耳机上"，但我的耳机已打开

当你放在你的耳机上时，Windows Mixed Reality 可能需要几秒钟才能重新加载空间。 如果此消息不会消失，请确保已从重用功能区的耳机内的邻近感应传感器中删除保护贴纸。 如果问题仍然存在，请与你的耳机制造商联系。

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>显示一条消息 "连接耳机"，但我已插入我的耳机

- 请确保将耳机的 USB 和 HDMI 或 DisplayPort 电缆连接到电脑上的正确端口。 下面介绍如何识别正确的端口：

    - USB 3.0 端口有一个特殊的徽标，其中 "SS" 标记 (表示 "SuperSpeed" ) 。 端口的内部片通常为蓝色，但较旧的 USB 2.0 端口通常为黑色或白色。
    - 如果计算机有两个 HDMI 或 DisplayPort 端口，请使用连接到图形卡的端口，而不是计算机的主板。 这并不总是显而易见的，尽管离散端口通常位于计算机上的扩展插槽中。 如果尝试一个端口但它不起作用，请尝试其他端口。

- 从耳机拔下并插入 USB 和 HDMI 或 DisplayPort 电缆，确保它们已安全连接。 插入 USB 电缆时，请不要在插入 USB 电缆期间暂停。
- 如果你看到耳机的部分枚举（例如，一系列 USB 设备枚举，但在设备管理器 "Mixed Reality 耳机" 下没有任何内容），请尝试使用外部电源的 USB 3.0 集线器。
- 请参阅耳机制造商的网站并更新耳机的驱动程序和固件。
- 将耳机连接到另一台电脑并打开设备管理器。 即使该 PC 与 Windows Mixed Reality 不完全兼容，你也可以查看你的耳机是否枚举。 如果耳机未在多台电脑上枚举，则可能存在硬件问题。

> [!NOTE]
> 对于 Surface 用户：更早版本的 Surface Dock 和 Surface Book USB 集线器固件更新软件与混合现实耳机不兼容。 如果在 Surface PC 上收到 "连接耳机" 消息，请在设备管理器中检查是否有任何设备报告 "代码10：设备无法启动" 错误。 如果是这样，请 [删除冲突的驱动程序](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)。 只需执行此操作一次。

适用于 Windows 10-N 用户的说明：如果你的电脑运行的是 Windows 10 N，则在插入混合现实耳机后，会看到 "代码28：安装类不存在或无效" 设备管理器错误。 Windows Mixed Reality 不支持 N 版本的 Windows 10。 有关详细信息，请按照这些 [说明](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 进行操作。

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>消息显示 "检查 USB 电缆" 或 "USB 速度不足"

* 请确保使用的是计算机上受支持的 USB 3.0 端口：

    * 请确保将耳机的 USB 电缆全部插入。
    * 运行 [Windows Mixed Reality 门户](install-windows-mixed-reality.md#launch-mixed-reality-portal) ，确保你的 PC 的 USB 3.0 控制器受支持。
    * 将耳机连接到电脑上的其他 USB 3.0 端口。 某些电脑具有多个 USB 3.0 控制器。
    * 暂时断开连接到电脑的所有 USB 设备，并仅连接耳机。
    * 在自定义构建的 Pc 上，即使某个端口可能标记为 USB 3.0 端口，它也可能连接到 USB 2.0 控制器。 连接手机网络后，请打开设备管理器，找到并单击从耳机枚举的任何设备，然后单击 " **按连接查看 > 设备**"。
* 尝试在另一台电脑上戴上耳机。 如果其他 PC 与 Windows Mixed Reality 不完全兼容，请查看设备管理器查看是否显示 "USB 速度不足" 消息。 如果在多台电脑上无法正确枚举，则耳机可能出现故障。
* 删除耳机与计算机之间的所有扩展器或集线器。

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>我接通耳机后，混合现实门户未启动

可能由于根本问题而无法正确检测到你的耳机。 手动启动混合现实门户，并查找显示的任何错误消息。

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>当我的电脑进入睡眠或休眠模式时，或者当使用我的耳机连接重启我的电脑时，耳机停止工作

1. 打开设备管理器并确认你的耳机是否列在 "Mixed Reality 设备" 下。
2. 在 "Mixed Reality 设备" 下选择你的耳机，并确认设备状态指示 "此设备是否正常运行"。
3. 如果出现 "代码 43" 错误，指出设备已停止工作，或者你没有在 "Mixed Reality 设备" 下看到你的头戴显示 Microsoft 正在调查潜在的软件/驱动程序互操作性问题，这可能会导致此错误。 此问题会影响少量 Pc，预计会在将来对混合现实耳机驱动程序的更新中得到解决。

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>我的耳机会使我的 PC 生成 Bug 检查 (蓝屏，使我的电脑进入睡眠状态或处于休眠模式时) 

请确保位于10.0.19041.2034 驱动程序或更高版本。

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>接通耳机后，耳机驱动程序未自动安装

在新电脑上，或安装有新安装的 Windows 10 副本的电脑上，耳机驱动程序可在其他 Windows 更新后排队，并且可能不会立即安装。

1. 请参阅 **开始 > 设备管理器** 并在 "混合现实设备" 下查看头戴显示设备。 设备状态应指示 "设备正常运行"。
2. 右键单击该设备，然后选择 "更新驱动程序"。

如果这不起作用，请尝试卸载该驱动程序：

1. 请参阅 **开始 > 设备管理器** 并在 "混合现实设备" 下查看头戴显示设备。 设备状态应指示 "设备正常运行"。
2. 右键单击该设备，然后选择 "卸载设备"。
3. 在出现的新弹出窗口中，选中复选框 "删除此设备的驱动程序软件"，然后选择 "卸载"。
4. 完成后，拔出电脑的耳机，并重新插回。 Windows 更新现在会下载并安装新的驱动程序。

注意：如果你有一个 N 版本的 Windows，则需要切换到 Windows 10 的常规版本以使用 Windows Mixed Reality。