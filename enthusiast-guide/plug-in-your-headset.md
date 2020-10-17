---
title: 接入头戴显示设备
description: 了解如何将 Windows Mixed Reality 耳机连接到 USB 3.0 和 HDMI，以及如何将耳机连接到耳机。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，耳机，设置，入门
appliesto:
- Windows 10
ms.openlocfilehash: 46b40a09c88013515911026cbd03a6fc6d19e1ca
ms.sourcegitcommit: 2cdc2e38990fff24972d98f9e74f0dabacbffa7d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2020
ms.locfileid: "92153508"
---
# <a name="plug-in-your-headset"></a>接入头戴显示设备

## <a name="connect-your-headset-to-your-pcs-usb-30-port"></a>将耳机连接到电脑的 USB 3.0 端口

确定计算机上的 USB 3.0 端口并插入 USB 电缆。 USB 3.0 端口具有 SS () 写入它们的速度。 它们通常 (，但并不总是) 蓝色。

如果你的 PC 上没有足够的开放 USB 端口，则可以使用 [支持 AC 电源的外部 usb 3.0 集线器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)。

## <a name="connect-your-headset-to-your-pcs-hdmi-out-port"></a>将耳机连接到电脑的 HDMI 输出端口

确定计算机上的 HDMI 输出端口，并插入耳机的 HDMI 电缆。 请确保 **不** 会插入端口中的 HDMI！

## <a name="connect-headphones-to-your-headset"></a>将耳机连接到耳机

除非你购买了 HMD 太空耳机、HP 回音或 HP 回音 G2 (（它们具有集成的 AKG 耳机和集成的双阵列麦克风) ），否则，你将需要连接耳机，)  (可以将耳机插入耳机的 3.5 mm 音频插孔。

## <a name="common-issues"></a>常见问题
* 在插入 USB 3.0 电缆之前插入了 HDMI 电缆。  请确保在插入 HDMI 电缆 **之前** 插入 USB 3.0 电缆。
* 已在 HMD 的 USB 电缆旁插入蓝牙适配器。  如果使用的是蓝牙适配器， **请勿** 将耳机的 USB 电缆插在该适配器旁边，因为产生的无线电干扰可能会对蓝牙性能产生负面影响。
* 将 HDMI 电缆插入到 iGPU HDMI 端口，而不是 dGPU HDMI 端口 (适用于) 的 Pc。 某些台式 Pc 既有 (iGPU) 的集成的图形处理单元，又 (dGPU) ，并且通常会禁用 iGPU 端口。 如果你的电脑有 dGPU，则你的耳机需要插入到 dGPU 中。  
* 如果你的电脑没有 HDMI 端口，则可能需要一个适配器。 在[此处查看推荐的适配器的完整列表](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)。 
* 正在将耳机连接到 Surface 设备。 请阅读 [使用带有 Windows Mixed Reality 的图面](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)。

## <a name="see-also"></a>另请参阅

* [耳机连接疑难解答](headset-connectivity.md)
* [安装 Windows Mixed Reality](install-windows-mixed-reality.md)
* [推荐的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* [电脑硬件最低要求指南](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
