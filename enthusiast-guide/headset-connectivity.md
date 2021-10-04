---
title: 头戴显示设备连接常见问题解答
description: 头戴显示Windows Mixed Reality头戴显示设备连接故障排除，超出了标准使用者支持文档。
author: qianwen
ms.author: v-qianwen
ms.date: 09/30/2021
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 故障排除， 错误， 帮助， 支持， 头戴显示设备
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 47c726c5beeac0463fe4286bd7a949e4e4d4cc45
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436607"
---
# <a name="headset-connectivity-faqs"></a>头戴显示设备连接常见问题解答

## <a name="my-headset-will-not-wake-up"></a>我的头戴显示设备不会唤醒

如果头戴显示设备正在睡眠，并且单击唤醒按钮不起作用，请重启电脑。

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>我的计算机没有一个MIMI 和/或显示端口

可能需要使用适配器。 转到 [此处](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) ，查看支持的适配器列表。

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>能否在头戴显示设备中使用 USB 或 WINDOWS MIXED REALITY和/或 DisplayPort 扩展电缆

Windows Mixed Reality头戴显示设备不正式支持使用 USB、USB 或 DisplayPort 扩展电缆。 如果使用这些电缆，则混合现实体验可能会由于电脑的 USB 控制器和混合现实头戴显示设备之间的信号完整性和总线电源差异而受到影响。 如果发生以下问题，请尝试在无扩展电缆的情况下使用头戴显示设备：

* 头戴显示简要显示蓝屏，然后变为黑色，混合现实门户重启或完全取消枚举
* 头戴显示设备音频剪切或变得小问题
* 头戴显示设备在黑色和正确显示器之间闪烁

## <a name="i-am-getting-a-check-your-display-cable-error"></a>我收到"检查显示电缆"错误

* 如果使用任何适配器将头戴显示设备连接到电脑，请确保它们支持Windows Mixed Reality 4K。 此外，在将头戴显示设备连接到适配器之前，请尝试将适配器连接到电脑。
* 请尝试使用不同的"下一个""或"DisplayPort"端口。
* 连接头戴显示设备连接到 DisplayPort 1.2 或更高版本，或将头戴显示设备连接到 1.4 或更高版本。 请确保端口与电脑上的最先进的图形卡相对应。
* 如果电脑同时具有集成图形和离散图形，请确保在活动图形卡上使用"GPU"或"DisplayPort"端口。 这可能意味着需要将电脑显示器连接到非 PC 端口。
* 如果电脑同时具有集成图形和离散图形，并且集成图形较旧且不支持Windows Mixed Reality，请尝试禁用集成 GPU。
* 连接电脑监视器连接到电脑的"下一台"或"DisplayPort"端口。 确保图形驱动程序是最新的。 直接从 AMD、Nvidia 或 Intel 下载并安装驱动程序，因为它们可能比发布到 Windows 更新的版本更新。
* 如果已将外部监视器插入了一个适用于该端口的外部监视器，请尝试改为将其插入 DisplayPort，然后使用适用于头戴显示设备的外部监视器。
* 确保将头戴显示设备的电脑上的"USB 输出"端口插入了头戴显示设备（而不是"在中）"端口。
* Windows可能无法检测显示电缆连接。 打开设备管理器，查看头戴显示设备是否列在"监视器"下。 如果没有，请选择"**操作>扫描硬件更改"。**

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>一条消息显示"放在头戴显示设备上"，但我的头戴显示设备已打开

在头戴显示设备上Windows Mixed Reality可能需要几秒钟来重新加载空间。 如果此消息未消失，请确保已从头戴显示设备内部（在镜头之间）的邻近传感器中删除保护性标签。 如果问题仍然存在，请与头戴显示设备制造商联系。

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>一条消息显示"连接头戴显示设备"，但我已插入头戴显示设备

- 确保头戴显示设备 USB 和MIMI 或 DisplayPort 电缆已连接到电脑上的正确端口。 下面是如何标识正确端口的：

    - USB 3.0 端口有一个特殊的徽标，其"SS"标记 (指示"SuperSpeed") 。 端口内部通常为蓝色，但内部较旧的 USB 2.0 端口通常为黑色或白色。
    - 如果计算机有两个"开始"或"DisplayPort"端口，请使用连接到图形卡的端口，而不是计算机的主板。 这并不总是很明显，尽管离散端口通常位于计算机的扩展槽中。 如果尝试一个端口，但该端口不起作用，请尝试另一个端口。

- 从头戴显示设备拔下并插入 USB 和 PCI 或 DisplayPort 电缆，以确保它们已安全连接。 插入 USB 电缆时，请尝试在插入 USB 电缆期间不要暂停。
- 如果看到头戴显示设备的部分枚举（例如，一系列 USB 设备枚举，但在 设备管理器 中的"混合现实头戴显示设备"下没有任何内容，请尝试使用外部电源 USB 3.0 集线器。
- 转到头戴显示设备制造商的网站，更新头戴显示设备驱动程序和固件。
- 连接头戴显示设备连接到另一台电脑并打开设备管理器。 即使该电脑与 Windows Mixed Reality完全兼容，也可以检查头戴显示设备是否枚举。 如果头戴显示设备未枚举多个电脑，则可能是硬件问题。

> [!NOTE]
> 对于 Surface 用户：早期版本的 Surface Dock 和 Surface Book USB 中心固件更新软件与混合现实头戴显示设备不兼容。 如果在 Surface 电脑上收到"连接头戴显示设备"消息，请检查是否有设备在设备上报告"代码 10：设备无法启动"错误设备管理器。 如果是这样， [请删除冲突的驱动程序](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)。 只需执行一次此操作。

Windows 10-N 和 Windows 11-N 用户注意：如果电脑运行的是 Windows 10-N 或 Windows 11-N，则插入混合现实头戴显示设备后，在 设备管理器 中会看到"代码 28：安装类不存在或无效"错误。 Windows 10 Windows 11 不支持 N Windows Mixed Reality。 有关详细信息 [，请按照](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) 这些说明操作。

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>消息显示"检查 USB 电缆"或"USB 速度不足"

* 请确保在电脑上使用受支持的 USB 3.0 端口：

    * 确保头戴显示设备 USB 电缆一路插入。
    * 运行[Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal)门户，确保电脑的 USB 3.0 控制器受支持。
    * 连接头戴显示设备连接到电脑上的其他 USB 3.0 端口。 某些电脑具有多个 USB 3.0 控制器。
    * 暂时断开连接到电脑的所有 USB 设备，并仅连接头戴显示设备。
    * 在自定义构建的 PC 上，即使端口可能标记为 USB 3.0 端口，它也可能连接到 USB 2.0 控制器。 连接头戴显示设备后，设备管理器，找到并单击从头戴显示设备枚举的任何设备，然后转到"按连接查看>**设备"。**
* 在另一台电脑上试用头戴显示设备。 如果其他电脑与 Windows Mixed Reality完全兼容，设备管理器检查是否看到"USB 速度不足"消息。 如果它在多个 PC 上未正确枚举，则头戴显示设备可能已损坏。
* 删除头戴显示设备与计算机之间的任何扩展程序或集线器。

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>插入混合现实门户头戴显示设备后，设备未启动

由于基础问题，可能未正确检测到头戴显示设备。 手动混合现实门户，并查找显示的任何错误消息。

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>我的头戴显示设备在电脑进入睡眠或休眠模式时或在连接了头戴显示设备时重启电脑时停止工作

1. 打开设备管理器，确认头戴显示设备在"混合现实设备"下列出。
2. 在"混合现实设备"下选择头戴显示设备，并确认设备状态指示"此设备正常工作"。
3. 如果看到"代码 43"错误，指出设备已停止工作，或者未看到头戴显示设备在"混合现实设备"下列出，请拔下头戴显示设备的 USB 电缆，然后重新插入。 Microsoft 正在调查潜在的软件/驱动程序互操作性问题，这可能会导致此错误。 此问题会影响少量电脑，预计在将来对混合现实头戴显示设备驱动程序的更新中会得到解决。

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>我的头戴显示设备导致我的电脑在 (进入睡眠) 进入休眠模式时，在蓝屏模式下生成 Bug 检查

确保使用 10.0.19041.2034 驱动程序或更高版本。

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>插入头戴显示设备时，头戴显示设备驱动程序不会自动安装

在新电脑或具有新安装的 Windows 10 或 Windows 11 副本的 PC 上，头戴显示设备驱动程序可以与其他 Windows 更新一起排队，并且可能不会立即安装。

1. 转到" **开始> 设备管理器，** 在头戴显示设备的"混合现实设备"下查看。 设备状态应指示"设备正常工作"。
2. 右键单击设备并选择"更新驱动程序"。

如果不起作用，请尝试卸载驱动程序：

1. 转到" **开始> 设备管理器，** 在头戴显示设备的"混合现实设备"下查看。 设备状态应指示"设备正常工作"。
2. 右键单击设备并选择"卸载设备"。
3. 在出现的新弹出窗口中，选中"删除此设备的驱动程序软件"复选框，然后选择"卸载"。
4. 完成后，从电脑中拔下头戴显示设备，然后重新插入。 Windows更新现在将下载并安装新的驱动程序。

注意：如果有 N 版 Windows，则需要切换到 Windows 10 或 Windows 11 的常规版本，Windows Mixed Reality。