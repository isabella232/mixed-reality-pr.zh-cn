---
title: 混合现实门户错误消息
description: 高级Windows Mixed Reality门户消息故障排除，超出了标准使用者支持文档。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 故障排除， 错误， 帮助， 支持， 混合现实门户
appliesto:
- Windows 10
ms.openlocfilehash: c85030da129d90bb0a150ad50a6990e30b68c21bc7a3899c4182e87acd4b4fa5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186867"
---
# <a name="mixed-reality-portal-error-messages"></a>混合现实门户错误消息

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>我收到"出错"错误消息，或者遇到问题混合现实门户。

重启Windows Mixed Reality：
1. 将两条头戴显示设备电缆与电脑断开连接。
2. 重启你的电脑。
3. 重新连接头戴显示设备。

如果不起作用，请确保电脑识别头戴显示设备：
1. 选择“启动”。
2. 在搜索框中键入"设备管理器"，在列表中选择它。 
3. 展开"混合现实设备"，查看是否列出了头戴显示设备。 

如果未列出：
1. 将头戴显示设备插入电脑上的不同端口（如果可用）。
2. 检查更新中的最新Windows更新。
3. 卸载并重新安装Windows Mixed Reality：
    1. 将两条头戴显示设备电缆与电脑断开连接。
    2. 选择 **"设置 >混合现实>卸载"。**
    3. 选择 **设置 >设备> 蓝牙 &其他设备** 来配对运动控制器。 选择每个控制器，然后选择"删除设备"。
    4. 将头戴显示设备插入电脑，重新安装Windows Mixed Reality。
    
## <a name="im-getting-a-check-your-usb-cable-error-message"></a>我收到"检查 USB 电缆"错误消息。

连接头戴显示设备连接到不同的 USB 端口 (并确保它是超速 USB 3.0) 。 此外，请尝试删除头戴显示设备与计算机之间的任何扩展程序或集线器。

## <a name="im-getting-a-check-your-display-cable-error-message"></a>我收到"检查显示电缆"错误消息。

使用以下步骤排查问题：
* 连接头戴显示设备连接到 DisplayPort 1.2 或更高版本，或将头戴显示设备连接到 1.4 或更高版本。 请确保端口与电脑上的最先进的图形卡相对应。
* 如果使用的是适配器，请确保其支持 4K。
* 请尝试使用不同的MIDMI 端口。
* 如果已将外部监视器插入了一个适用于该端口的外部监视器，请尝试改为将其插入 DisplayPort，然后使用适用于头戴显示设备的外部监视器。
