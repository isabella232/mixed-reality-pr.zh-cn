---
title: 性能常见问题解答
description: 性能Windows Mixed Reality故障排除，超出了标准使用者支持文档。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 故障排除， 错误， 帮助， 支持， 性能
appliesto:
- Windows 10
ms.openlocfilehash: 6754923a07d4c75c6f0f44aad07c5d3c55c28ae4673900531d8a4af663d9e7c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219413"
---
# <a name="performance-faqs"></a>性能常见问题解答

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60-hz-or-90-hz-framerate"></a>我的头戴显示Windows Mixed Reality 60 Hz 或 90-Hz 帧速率渲染

如果有一个离散的 GPU 和一个包含 4 个或多个物理核心的 GPU 和 2.0 端口，则应该获得 90 Hz。 若要确认，请查看 **"设备门户 >"** 选项卡。

注意：如果 GPU 只有一个按 1.4 输出的 GPU，可以使用 DisplayPort [toMI 2.0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 适配器作为解决方法。

注意："头戴显示"中的视觉质量设置仅影响Windows Mixed Reality呈现。

## <a name="my-pc-is-running-slowly"></a>我的电脑运行缓慢

由于多种原因，系统可能会变慢，通常只会持续几秒钟。 如果长时间遇到此问题：

1. 关闭桌面上所有未使用的应用程序。
2. 确保笔记本电脑已插入电源。
3. 确保电脑未预热。
4. 降低主页中的视觉Windows Mixed Reality质量。
5. 确保拥有电脑 [的最新](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) 图形驱动程序。

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>运行混合现实体验时，我的电脑正在预热。 如何实现保持冷

1. 检查电池是否已充电且电源已接通电源。
2. 确保未阻止电脑风扇。
3. 在相对冷的环境中使用电脑。
4. 请确保没有热源 (例如，在电脑上) 或热口。

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>我的视觉对象很不稳定、加载速度缓慢，或者看起来不好

* 确保头戴显示设备已插入电脑上的正确图形卡。 某些电脑具有集成和离散图形卡。 离散卡通常提供最佳性能。 [详细了解电脑硬件](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。
* 关闭桌面上未使用的应用程序。
* 确保头戴显示设备适合 (或左右移动，以调整) 。
* 在"混合现实"和"头戴显示设置 >**中>视觉设置**。 当"视觉质量"设置为"自动"时，将自动选择电脑的混合现实体验。 有关视觉对象的详细信息，将"视觉质量"设置为"高"。 如果视觉对象不稳定，请选择较低的设置。
* 调整头戴显示设备校准手柄，确保将镜头设置为与名为 IPD (之间的正确) 。 如果不知道 IPD，optometrist 可以测量它，或使用旨在测量 IPD 的网站。 如果头戴显示设备没有校准手柄，请选择"设置 >头戴显示设备>混合现实 **"，并** 调整"校准控件"。
* 如果使用的是 USB-C 或 DisplayPort 到MIC 适配器，请尝试其他适配器。 请参阅 [建议的适配器。](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* 断开可能连接到电脑图形卡的任何额外监视器。
* 尝试来自 Windows Store 的一些混合现实应用 - 某些应用可能更符合计算机设置要求。
