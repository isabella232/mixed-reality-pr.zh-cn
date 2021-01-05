---
title: 在 Windows Mixed Reality 中获取有关 PC 兼容性的帮助
description: 使用 Windows Mixed Reality 时，帮助资源应对电脑兼容性问题。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
appliesto:
- Windows 10
ms.openlocfilehash: e55c66599e47abff35b872a494a6afbb48774171
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859516"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>在 Windows Mixed Reality 中获取有关 PC 兼容性的帮助

设置 Windows Mixed Reality 或使用 [混合现实门户](install-windows-mixed-reality.md)时，你会收到一份报告，指出你的电脑是否已达到该任务。 本文详细介绍了你可能会在以下部分中看到的内容。

在继续操作之前，请尝试以下最常见的修补程序： 

> [!div class="checklist"]
> * 确保计算机满足 [最低计算机硬件兼容性要求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * 检查 [图形卡和处理器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 是否兼容
> * 检查 [建议的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 列表
> * 通过选择 "开始 > 设置" 更新图形驱动程序 **> 更新 & 安全 > 检查更新** 

## <a name="youre-good-to-go"></a>准备就绪

祝您这样的消息，如果您看到一条消息， **则** 您的 PC 可以运行 Windows Mixed Reality！ 计算机硬件和配置之间仍存在差异，因此，每台电脑上的混合现实体验可能不相同。

## <a name="supports-some-features"></a>支持某些功能

如果你看到 " **支持某些功能** " 消息，则你的电脑可能会运行一些 Windows Mixed Reality 体验，但可能无法提供最佳体验。 可能的缺点包括滞后图形、性能点击量，以及一些你根本无法运行的应用程序和游戏。 我们列出了你可能会看到的消息以及如何处理它们。

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>这台电脑的集成显卡包含单声道 RAM

集成图形卡将在具有双通道 RAM 的 Pc 上提供最佳的 Windows Mixed Reality 体验。 如果遇到性能问题：

> [!div class="checklist"]
> * 安装 [兼容的独立图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * 安装其他 RAM 杆以创建双通道 RAM
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>这台电脑的混合图形配置具有不兼容的 PCIe 链接

PCIe 代表 *外围组件互连 Express*，这是 PC 用于与图形卡通信的连接。 您的配置可能会正常运行，但如果遇到问题，则需要切换到 [兼容的 PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>这台电脑的图形驱动程序可能无法正常使用 Windows Mixed Reality

尝试使用 Windows 更新下载新的图形驱动程序：

> [!div class="checklist"]
> * 选择 " **开始 > 设置" > 更新 & 安全 > 检查更新** 或转到你的电脑或图形卡制造商的网站
> * [检查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果这不起作用，则需要：

> [!div class="checklist"]
> * 添加 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>这台电脑的处理器可能无法与 Windows Mixed Reality 很好地配合使用

计算机的处理器可能无法与 Windows Mixed Reality 很好地配合，因为它没有足够的核心。 如果 Windows Mixed Reality 不能正常运行：

> [!div class="checklist"]
> * 将处理器替换为[兼容](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)的处理器 
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>这台电脑可能没有兼容的 USB 配置

对于运行 Windows Mixed Reality 的问题：

> [!div class="checklist"]
> * 查看我们 [推荐的适配器文档](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) ，以获取常见兼容性问题的解决方案
> * 请考虑使用 [外部电源 USB 集线器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

如果问题仍然存在，请执行以下操作：

> [!div class="checklist"]
> * 如果你有可用的 USB 端口，请将其插入到其他 USB 端口。
> * 如果这不起作用，请卸载您的 PC 的当前 USB 驱动程序，然后重新安装 Microsoft 驱动程序：

1. 选择 " **开始**"，然后在 **搜索** 框中键入 "设备管理器"。
2. 从结果中选择 " **设备管理器** "。
3. 展开 "通用串行总线控制器" 类别，查看列出的设备并卸载所有不兼容的驱动程序。
    * 如果列表中包含 "可扩展主机控制器" 项，但设备名称末尾没有 "Microsoft"，则该驱动程序与 Windows Mixed Reality 不兼容。 需要将其卸载。 若要卸载某个驱动程序，请在列表中右键单击该设备，然后选择 " **卸载设备**"。 选中 " **删除此设备的驱动程序软件** " 复选框，然后选择 " **卸载**"。
    * 如果该列表包含名称中包含 "Etron" 的 "可扩展主机控制器" 项，该 USB 控制器与 Windows Mixed Reality 不兼容。 需要在电脑上使用不同的 USB 端口，或购买不同的 USB 3.0 主机控制器。
4. 重启你的电脑。
5. 返回到设备管理器并再次查找可扩展的主机控制器项。 如果你现在在设备名称的末尾看到 "Microsoft"，你就可以开始了。 如果未执行此操作，请重复执行卸载步骤，删除任何额外的非 Microsoft 驱动程序版本。

> [!div class="checklist"]
> * 如果仍然不起作用，请将 PCIe USB 卡添加到 PC。

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>这台电脑没有适用于控制器的蓝牙4。0

2018和更高版本的 Windows Mixed Reality 耳机已经有内置的蓝牙，但如果你有较旧的耳机，则混合现实运动控制器需要蓝牙4.0。 你仍然可以 [将 Windows Mixed Reality 与 Xbox 控制器](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)、 [鼠标和键盘](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)或 [USB 蓝牙适配器一起使用，以将运动控制器连接](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) 到你的 PC。 [查看建议的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>根据你的耳机，你可能需要蓝牙适配器才能使用运动控制器

某些耳机内置了蓝牙，因此控制器可以直接配对耳机。 其他人需要电脑中的蓝牙无线电 (或单独的转换器) 才能使用运动控制器。 有关详细信息，请参阅 [推荐的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) 页。

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>这台电脑没有自供电 USB 端口

连接 Windows Mixed Reality 耳机需要自驱动的 USB 3.0 端口。 将已 [通电的 USB 3.0 集线器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) 连接到电脑，并使用该集线器连接耳机。

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>这台电脑的显卡不适用于 Windows Mixed Reality

这台电脑的图形卡与 Windows Mixed Reality 不兼容。 你需要：

> [!div class="checklist"]
> * 添加 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>这台电脑的图形驱动程序不能与 Windows Mixed Reality 一起使用

这台电脑的图形驱动程序不能与 Windows Mixed Reality 一起使用。 尝试使用 Windows 更新下载新的图形驱动程序：

> [!div class="checklist"]
> * 选择 " **开始 > 设置" > 更新 & 安全 > 检查更新** 或转到你的电脑或图形卡制造商的网站
> * [检查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果这不起作用，则需要：

> [!div class="checklist"]
> * 添加 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>这台电脑的处理器不适用于 Windows Mixed Reality

这台电脑的处理器不支持 AVX/Popcnt 指令。 若要运行 Windows Mixed Reality，你需要：

> [!div class="checklist"]
> * 将其替换为 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>这台电脑的可用磁盘空间不足，无法运行 Windows Mixed Reality

Windows Mixed Reality 需要 10 GB 的可用磁盘空间来设置和获得最佳性能。 请清除驱动器上的一些空间，然后重新尝试设置。

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>这台电脑运行的 Windows 版本不支持 Windows Mixed Reality

Windows Mixed Reality 适用于 [windows 10 家庭](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) 版和 [windows 10 专业](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab)版。 需要安装其中一个版本才能使用 Windows Mixed Reality。

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>此电脑未运行最新版本的 Windows 10

Windows Mixed Reality 需要 Windows 10 秋季创意者更新。 请[更新你的电脑](https://support.microsoft.com/help/4028685)，然后重试。

### <a name="this-pc-has-no-usb-30-port"></a>此电脑没有 USB 3.0 端口

需要一个 USB 3.0 端口来连接 Windows Mixed Reality 耳机。 如果使用的是台式计算机，请添加 PCIe USB 卡。 对于便携式计算机，需要切换到 [兼容的 PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="you-cant-run-this-app-via-remote-desktop"></a>无法通过远程桌面运行此应用

若要使用 Windows Mixed Reality，需要一个连接了监视器的 PC。 如果你使用的是虚拟机或没有监视器，请尝试使用虚拟显示适配器。 这是一种插入 PC DisplayPort 并模拟计算机显示的设备。

## <a name="getting-the-best-performance"></a>获得最佳性能

某些硬件配置可能会导致 Windows Mixed Reality 出现性能问题。 对于速度缓慢、视觉对象不稳定或视觉质量差等问题，请尝试以下常见修复：

* 关闭您的 PC 桌面上运行的任何打开的应用程序。
* 如果使用的是 DisplayPort 或到 HDMI 适配器，请尝试其他适配器。 查看建议的适配器
* 如果有额外的监视器连接到 PC 的图形卡，请将其断开连接。
* 尝试从 Windows 应用商店下载一些不同的混合现实应用，某些应用程序可能更适合您的计算机设置。

如果仍存在性能问题，请更新以下 [Windows Mixed Reality](set-up-windows-mixed-reality.md) 设置以获得最佳用户体验：

* 体验
* 解决方法
* 帧速率
* 校准

> [!NOTE]
> 如果看到一条消息，指出： "此硬件配置可能与 Windows Mixed Reality 一起工作，但尚未对其进行测试"，则在长时间运行 Windows Mixed Reality 时可能会遇到一些性能问题。

## <a name="working-with-steamvr"></a>使用 SteamVR

通过 SteamVR 的 "欣赏游戏" 是一种体验所有 VR 产品/服务的好方法。 但是，你需要确保在沉浸式设备上获得最佳性能。 安装 [流](https://store.steampowered.com/about)后：

* 按照[使用 SteamVR 与 Windows Mixed Reality 一起使用](using-steamvr-with-windows-mixed-reality.md)的说明进行操作
* 安装 [SteamVR 性能测试](https://store.steampowered.com/app/323910/SteamVR_Performance_Test) 应用

## <a name="next-vr-checkpoint"></a>下一个 VR 检查点

如果你正在关注我们所做的 VR 旅程，就可以开始购买设备了。 在这里，你可以继续在购买检查点之前的最后一步：

> [!div class="nextstepaction"]
> [购买常见问题解答](before-you-buy-faqs.md)

或者直接转到 "入门" 部分：

> [!div class="nextstepaction"]
> [设置 Windows Mixed Reality](set-up-windows-mixed-reality.md)

随时都可以返回到 [VR 旅程](vr-journey.md) 。

## <a name="see-also"></a>另请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)
* [疑难解答](troubleshooting-windows-mixed-reality.md)