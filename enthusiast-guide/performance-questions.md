---
title: 性能常见问题解答
description: 性能 Windows Mixed Reality 故障排除，超出了标准使用者支持文档的范围。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，性能
appliesto:
- Windows 10
ms.openlocfilehash: d6b37f8f6c964222b90fff57f0ba994c14fcaeab
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131961"
---
# <a name="performance-faqs"></a>性能常见问题解答

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60hz-or-90hz-framerate"></a>我的 Windows Mixed Reality 耳机呈现是以60Hz 还是90Hz 的帧速率

如果有与 HDMI 2.0 端口的离散 GPU 和具有四个或更多物理内核的 CPU，则应该获得 90 Hz。 若要确认，请检查 **设备门户 > 性能** "选项卡。

注意：如果 GPU 仅有 HDMI 1.4 输出，可以使用 DisplayPort 到 [HDMI 2.0 适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 作为解决方法。

注意： "耳机显示" 中的视觉质量设置只影响 Windows Mixed Reality 主页体验的呈现。

## <a name="my-pc-is-running-slowly"></a>我的 PC 运行速度缓慢

由于很多原因，系统的运行速度可能会很慢，在大多数情况下，这只是最后几秒钟。 如果在很长一段时间内遇到此问题：

1. 关闭桌面上所有未使用的应用程序。
2. 确保便携式计算机已插入电源。
3. 请确保电脑未预热。
4. 降低 Windows Mixed Reality 主页的视觉质量。
5. 确保你具有适用于你的电脑的最新 [图形驱动程序](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) 。

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>我的 PC 正在预热，因为我运行了混合现实体验。 如何实现使其很酷

1. 检查电池是否已充电并接通电源。
2. 请确保电脑风扇未被阻止。
3. 在相对较酷的环境中使用 PC。
4. 请确保没有热源 (例如，sun 或热通风口) PC。

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>我的视觉对象不连贯、负载缓慢或外观不佳

* 请确保将耳机插入 PC 上的正确图形卡。 某些 Pc 同时具有集成显卡和离散显卡。 离散卡通常会提供最佳性能。 [了解有关 PC 硬件的详细信息](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。
* 关闭桌面上未使用的应用程序。
* 请确保你的头戴显示 snugly (向下移动它，或向左和向右移动，以调整) 。
* **> 混合现实 > 耳机显示** ，在 "设置" 中调整耳机的视觉设置。 如果 "视觉质量" 设置为 "自动"，则会自动选择电脑的混合现实体验。 有关更多视觉对象的详细信息，请将 "视觉质量" 设置为 "高"。 如果视觉对象不连贯，请选择较低的设置。
* 调整耳机校准旋钮，确保重用功能区设置为瞳孔 (（称为 IPD) 之间的正确距离。 如果你不知道 IPD，optometrist 应能够为你测量，或者使用旨在度量 IPD 的网站。 如果耳机没有校准旋钮，请选择 " **设置" > 混合现实 > 耳机显示** 并调整 "校准控制"。
* 如果使用的是 DisplayPort 或到 HDMI 适配器，请尝试其他适配器。 请参阅 [建议的适配器。](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* 断开可能连接到您的 PC 图形卡的任何其他显示器。
* 尝试使用 Windows 应用商店中的一些不同的混合现实应用程序，某些应用程序可能更适合您的计算机设置。
