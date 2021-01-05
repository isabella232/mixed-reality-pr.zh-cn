---
title: 混合现实门户错误消息
description: 高级 Windows Mixed Reality 门户消息疑难解答，超出了标准使用者支持文档的范围。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，混合现实门户
appliesto:
- Windows 10
ms.openlocfilehash: 2beb063afb3aea5f44be116e6cb906312447dbd8
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726038"
---
# <a name="mixed-reality-portal-error-messages"></a>混合现实门户错误消息

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>我收到 "出现错误" 的错误消息，或在混合现实门户中遇到问题。

重启 Windows Mixed Reality：
1. 从电脑拔下耳机电缆。
2. 重启你的电脑。
3. 重新连接耳机。

如果这不起作用，请确保电脑识别你的耳机：
1. 选择“启动”。
2. 在搜索框中键入 "设备管理器"，并在列表中选择它。 
3. 展开 "Mixed reality 设备"，并查看是否列出了你的耳机。 

如果未列出：
1. 将耳机插入电脑上的不同端口（如果可用）。
2. 查看 Windows 更新中的最新软件更新。
3. 卸载并重新安装 Windows Mixed Reality：
    1. 从电脑拔下耳机电缆。
    2. 选择 " **设置" > 混合现实 > 卸载**"。
    3. 选择 " **设置" > 设备 > 蓝牙 & "其他设备** " 以取消配对运动控制器。 选择每个控制器，然后选择 "删除设备"。
    4. 将您的耳机插回您的 PC 上，重新安装 Windows Mixed Reality。
    
## <a name="im-getting-a-check-your-usb-cable-error-message"></a>我收到 "检查 USB 电缆" 错误消息。

将耳机连接到不同的 USB 端口 (，并确保它是 SuperSpeed USB 3.0) 。 同时，尝试删除耳机与计算机之间的所有扩展器或集线器。

## <a name="im-getting-a-check-your-display-cable-error-message"></a>我收到 "检查显示电缆" 错误消息。

使用以下步骤解决此问题：
* 将耳机连接到 DisplayPort 1.2 或更高版本，1.4 或者连接到或更高版本。 确保端口与电脑上最先进的图形卡相对应。
* 如果使用的是适配器，请确保支持4K。
* 尝试使用不同的 HDMI 端口。
* 如果将外部监视器连接到 HDMI 端口，请尝试将其插入 DisplayPort，并将 HDMI 端口用于耳机。
