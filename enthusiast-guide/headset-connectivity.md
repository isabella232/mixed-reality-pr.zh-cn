---
title: 头戴显示设备连接常见问题解答
description: 头戴显示Windows Mixed Reality头戴显示设备连接故障排除，超出了标准使用者支持文档。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 故障排除， 错误， 帮助， 支持， 头戴显示设备
appliesto:
- Windows 10
ms.openlocfilehash: 2d46275fd86eedbe93a81bc97c156f29794e8c42
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143232"
---
# <a name="headset-connectivity-faqs"></a>头戴显示设备连接常见问题解答

## <a name="my-headset-will-not-wake-up"></a>我的头戴显示设备不会唤醒

如果头戴显示设备正在睡眠，并且单击唤醒按钮不起作用，请重启电脑。

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>我的计算机没有一个MIMI 和/或显示端口

可能需要使用适配器。 转到 [此处](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) ，查看支持的适配器列表。

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>能否在头戴显示设备中使用 USB 或 WINDOWS MIXED REALITY和/或 DisplayPort 扩展电缆

Windows Mixed Reality头戴显示设备不正式支持使用 USB、USB 或 DisplayPort 扩展电缆。 如果使用这些电缆，则混合现实体验可能会由于电脑的 USB 控制器和混合现实头戴显示设备之间的信号完整性和总线电源差异而受到影响。 如果发生以下问题，请尝试在无扩展电缆的情况下使用头戴显示设备：

* 头戴显示简要显示蓝屏，然后变为黑色混合现实门户重启或完全取消枚举
* 头戴显示设备音频剪切或变得小问题
* 头戴显示设备在黑色和正确显示器之间闪烁

## <a name="i-am-getting-a-check-your-display-cable-error"></a>我收到"检查显示电缆"错误

* 如果使用任何适配器将头戴显示设备连接到电脑，请确保它们支持Windows Mixed Reality 4K。 此外，在将头戴显示设备连接到适配器之前，请尝试将适配器连接到电脑。
* 请尝试使用不同的"下一个""或"DisplayPort"端口。
* 将耳机连接到 DisplayPort 1.2 或更高版本，1.4 或者连接到或更高版本。 确保端口与电脑上最先进的图形卡相对应。
* 如果你的电脑同时具有集成图形和离散图形，请确保在活动的图形卡上使用 HDMI 或 DisplayPort 端口。 这可能意味着需要将电脑显示器连接到非 HDMI 端口。
* 如果你的电脑同时具有集成图形和离散图形，并且集成的图形较旧且不支持 Windows Mixed Reality，请尝试禁用集成的 GPU。
* 将电脑监视器连接到电脑的 HDMI 或 DisplayPort 端口。 请确保图形驱动程序是最新的。 直接从 AMD、Nvidia 或 Intel 下载并安装驱动程序，因为它们可能比发布到 Windows 更新的驱动程序更高。
* 如果将外部监视器连接到 HDMI 端口，请尝试将其插入 DisplayPort，并将 HDMI 端口用于耳机。
* 请确保已将耳机的 HDMI 电缆插到了 PC 上的 "HDMI out" 端口，而不是连接到 "HDMI" 端口。
* Windows 可能无法检测显示电缆连接。 打开 Device Manager，查看耳机是否列在 "监视器" 下面。 否则，请选择 " **操作" > 扫描硬件更改**。

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>出现一条消息，显示 "放在你的耳机上"，但我的耳机已打开

当你放在你的耳机上时，Windows Mixed Reality 可能需要几秒钟才能重新加载空间。 如果此消息不会消失，请确保已从重用功能区的耳机内的邻近感应传感器中删除保护贴纸。 如果问题仍然存在，请与你的耳机制造商联系。

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>显示一条消息 "连接耳机"，但我已插入我的耳机

- 请确保将耳机的 USB 和 HDMI 或 DisplayPort 电缆连接到电脑上的正确端口。 下面介绍如何识别正确的端口：

    - USB 3.0 端口有一个特殊的徽标，其"SS"标记 (指示"SuperSpeed") 。 端口内部通常为蓝色，但内部较旧的 USB 2.0 端口通常为黑色或白色。
    - 如果计算机有两个"开始"或"DisplayPort"端口，请使用连接到图形卡的端口，而不是计算机的主板。 这并不总是很明显，尽管离散端口通常位于计算机的扩展槽中。 如果尝试一个端口，但该端口不起作用，请尝试另一个端口。

- 从头戴显示设备拔下并插入 USB 和 PCI 或 DisplayPort 电缆，以确保它们已安全连接。 插入 USB 电缆时，请尝试在插入 USB 电缆期间不要暂停。
- 如果看到头戴显示设备的部分枚举（例如，一系列 USB 设备枚举，但在 设备管理器 中的"混合现实头戴显示设备"下没有任何内容，请尝试使用外部电源 USB 3.0 集线器。
- 转到头戴显示设备制造商的网站，更新头戴显示设备驱动程序和固件。
- 将头戴显示设备连接到另一台电脑并打开设备管理器。 即使该电脑与 Windows Mixed Reality完全兼容，也可以检查头戴显示设备是否枚举。 如果头戴显示设备未枚举多个电脑，则可能是硬件问题。

> [!NOTE]
> 对于 Surface 用户：早期版本的 Surface Dock 和 Surface Book USB 中心固件更新软件与混合现实头戴显示设备不兼容。 如果在 Surface 电脑上收到"连接头戴显示设备"消息，请检查是否有设备在设备上报告"代码 10：设备无法启动"设备管理器。 如果是这样， [请删除冲突的驱动程序](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)。 只需执行一次此操作。

Windows 10-N 用户注意：如果电脑运行的是 Windows 10 N，则插入混合现实头戴显示设备后，设备管理器 中出现"代码 28：安装类不存在或无效"错误。 不支持 N Windows 10版本Windows Mixed Reality。 有关详细信息 [，请按照](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 这些说明操作。

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>消息显示 "检查 USB 电缆" 或 "USB 速度不足"

* 请确保使用的是计算机上受支持的 USB 3.0 端口：

    * 请确保将耳机的 USB 电缆全部插入。
    * 运行 [Windows Mixed Reality 门户](install-windows-mixed-reality.md#launch-mixed-reality-portal) ，确保你的 PC 的 USB 3.0 控制器受支持。
    * 将耳机连接到电脑上的其他 USB 3.0 端口。 某些电脑具有多个 USB 3.0 控制器。
    * 暂时断开连接到电脑的所有 USB 设备，并仅连接耳机。
    * 在自定义构建的 Pc 上，即使某个端口可能标记为 USB 3.0 端口，它也可能连接到 USB 2.0 控制器。 连接手机网络后，请打开 Device Manager，找到并单击从耳机枚举的任何设备，然后单击 " **按连接查看 > 设备**"。
* 尝试在另一台电脑上戴上耳机。 如果其他 PC 与 Windows Mixed Reality 不完全兼容，请查看 Device Manager 查看是否显示 "USB 速度不足" 消息。 如果在多台电脑上无法正确枚举，则耳机可能出现故障。
* 删除耳机与计算机之间的所有扩展器或集线器。

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>我接通耳机后，混合现实门户未启动

可能由于根本问题而无法正确检测到你的耳机。 手动启动混合现实门户，并查找显示的任何错误消息。

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>当我的电脑进入睡眠或休眠模式时，或者当使用我的耳机连接重启我的电脑时，耳机停止工作

1. 打开 Device Manager 并确认你的耳机是否列在 "Mixed Reality 设备" 下。
2. 在 "Mixed Reality 设备" 下选择你的耳机，并确认设备状态指示 "此设备是否正常运行"。
3. 如果出现 "代码 43" 错误，指出设备已停止工作，或者你没有在 "Mixed Reality 设备" 下看到你的头戴显示 Microsoft 正在调查潜在的软件/驱动程序互操作性问题，这可能会导致此错误。 此问题会影响少量的电脑，预计在将来对混合现实头戴显示设备驱动程序的更新中会得到解决。

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>我的头戴显示设备导致我的电脑在 (睡眠) 进入休眠模式时，在蓝屏模式下生成 Bug 检查

请确保使用 10.0.19041.2034 驱动程序或更高版本。

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>插入头戴显示设备时，头戴显示设备驱动程序不会自动安装

在新电脑或具有新安装的 Windows 10 的 PC 上，头戴显示设备驱动程序可能会与其他 Windows 更新一起排队，并且可能不会立即安装。

1. 转到" **开始> 设备管理器，** 在头戴显示设备的"混合现实设备"下查看。 设备状态应指示"设备正常工作"。
2. 右键单击设备并选择"更新驱动程序"。

如果不起作用，请尝试卸载驱动程序：

1. 转到" **开始> 设备管理器，** 在头戴显示设备的"混合现实设备"下查看。 设备状态应指示"设备正常工作"。
2. 右键单击设备并选择"卸载设备"。
3. 在出现的新弹出窗口中，选中复选框"删除此设备的驱动程序软件"，然后选择"卸载"。
4. 完成后，从电脑中拔下头戴显示设备，然后重新插入。 Windows 更新下载并安装新驱动程序。

注意：如果有 N 版 Windows，则需要切换到 Windows 的常规版本Windows 10以Windows Mixed Reality。