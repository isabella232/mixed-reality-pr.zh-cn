---
title: 获取有关电脑兼容性的帮助
description: 使用 Windows Mixed Reality 的应用程序和设备时，请及时了解解决计算机兼容性问题的资源。
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality，Mixed reality，虚拟现实，VR，先生，反馈，反馈中心，bug
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 1a07326da871eead6b13fe8350f37a22f8d27c23
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436556"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>获取 Windows Mixed Reality 中的 PC 兼容性帮助

设置 Windows Mixed Reality 或使用[混合现实门户](install-windows-mixed-reality.md)时，你会收到一份报告，指出你的电脑是否已完成任务。 本文详细介绍了你可能会在以下部分中看到的内容。

在继续操作之前，请尝试以下最常见的修补程序： 

> [!div class="checklist"]
> * 确保计算机满足 [最低计算机硬件兼容性要求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * 检查 [图形卡和处理器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 是否兼容
> * 检查 [建议的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 列表
> * 通过选择 "**开始" > 设置 > 更新 & 安全性 > 检查更新** 来更新图形驱动程序 

如果你想要联系，可以 [询问社区](https://answers.microsoft.com)， [联系支持人员](https://support.microsoft.com/contactus/)，或转到 [疑难解答](troubleshooting-windows-mixed-reality.md) 信息。

## <a name="youre-good-to-go"></a>准备就绪

祝您这样的消息，如果您看到一条 **不错** 的消息，则您的 PC 可以 Windows Mixed Reality 运行！ 计算机硬件和配置之间仍存在差异，因此，每台电脑上的混合现实体验可能不相同。

## <a name="supports-some-features"></a>支持某些功能

如果你看到 "**支持某些功能**" 消息，则你的电脑可能会运行一些 Windows Mixed Reality 体验，但可能无法提供最佳体验。 可能的缺点包括滞后图形、性能点击量，以及一些你根本无法运行的应用程序和游戏。 我们列出了你可能会看到的消息，以及以下内容：

* [这台电脑的集成显卡包含单声道 RAM](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [这台电脑的混合图形配置具有不兼容的 PCIe 链接](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [这台电脑的图形驱动程序可能无法正常工作 Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [这台电脑的处理器可能无法正常运行 Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [这台电脑可能没有兼容的 USB 配置](#this-pc-might-not-have-a-compatible-usb-configuration)
* [对于控制器，这台电脑没有蓝牙4。0](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [根据你的耳机，你可能需要蓝牙适配器才能使用运动控制器](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [这台电脑没有自供电 USB 端口](#this-pc-doesnt-have-a-self-powered-usb-port)
* [这台电脑的图形卡将无法用于 Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [此电脑的图形驱动程序不能与 Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [这台电脑的处理器不能与 Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [这台电脑没有足够的可用磁盘空间来运行 Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [这台电脑正在运行不支持的 Windows 版本 Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [这台电脑未在运行最新版本的 Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [这台电脑未运行最新版本的 Windows 11](#this-pc-isnt-running-the-latest-version-of-windows-11)
* [此电脑没有 USB 3.0 端口](#this-pc-has-no-usb-30-port)
* [无法通过远程桌面运行此应用](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>这台电脑的集成显卡包含单声道 RAM

集成图形卡将在具有双通道 RAM 的 pc 上提供最佳 Windows Mixed Reality 体验。 如果遇到性能问题：

> [!div class="checklist"]
> * 安装 [兼容的独立图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * 安装其他 RAM 杆以创建双通道 RAM
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>这台电脑的混合图形配置具有不兼容的 PCIe 链接

PCIe 代表 *外围组件互连 Express*，这是 PC 用于与图形卡通信的连接。 您的配置可能会正常运行，但如果遇到问题，则需要切换到 [兼容的 PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>这台电脑的图形驱动程序可能无法正常工作 Windows Mixed Reality

尝试使用 Windows 更新下载新的图形驱动程序：

> [!div class="checklist"]
> * 选择 "**开始 > 设置 > 更新 & 安全性 > 检查更新** 或转到你的电脑或图形卡制造商的网站
> * [检查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果这不起作用，则需要：

> [!div class="checklist"]
> * 添加 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>这台电脑的处理器可能无法正常运行 Windows Mixed Reality

你的电脑处理器可能无法与 Windows Mixed Reality 良好工作，因为它没有足够的核心。 如果 Windows Mixed Reality 不能正常运行：

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
2. 从结果中选择 " **Device Manager** "。
3. 展开 "通用串行总线控制器" 类别，查看列出的设备并卸载所有不兼容的驱动程序。
    * 如果列表中包含 "可扩展主机控制器" 项，但设备名称末尾没有 "Microsoft"，则该驱动程序与 Windows Mixed Reality 不兼容。 需要将其卸载。 若要卸载某个驱动程序，请在列表中右键单击该设备，然后选择 " **卸载设备**"。 选中 " **删除此设备的驱动程序软件** " 复选框，然后选择 " **卸载**"。
    * 如果该列表包含名称中包含 "Etron" 的 "可扩展主机控制器" 项，该 USB 控制器与 Windows Mixed Reality 不兼容。 需要在电脑上使用不同的 USB 端口，或购买不同的 USB 3.0 主机控制器。
4. 重启你的电脑。
5. 返回到 Device Manager 并再次查找可扩展的主机控制器项。 如果你现在在设备名称的末尾看到 "Microsoft"，你就可以开始了。 如果未执行此操作，请重复执行卸载步骤，删除任何额外的非 Microsoft 驱动程序版本。

> [!div class="checklist"]
> * 如果仍然不起作用，请将 PCIe USB 卡添加到 PC。

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>对于控制器，这台电脑没有蓝牙4。0

2018及更高版本的 Windows Mixed Reality 耳机已经有内置蓝牙，但是如果你有较旧的耳机，则混合现实运动控制器需要蓝牙4.0。 你仍可以[将 Windows Mixed Reality 与 Xbox 控制器](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)、[鼠标和键盘](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)或[USB 蓝牙适配器一起使用，以将运动控制器连接](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)到你的 PC。 [查看建议的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>根据你的耳机，你可能需要蓝牙适配器才能使用运动控制器

某些耳机内置了蓝牙，因此控制器可以直接配对耳机。 其他人需要 PC 中的蓝牙无线电 (或) 使用运动控制器单独的转换器。 有关详细信息，请参阅 [推荐的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) 页。

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>这台电脑没有自供电 USB 端口

连接 Windows Mixed Reality 耳机需要自驱动的 USB 3.0 端口。 连接已[通电的 USB 3.0 集线器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)连接到电脑，并使用该集线器连接耳机。

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>这台电脑的图形卡将无法用于 Windows Mixed Reality

这台电脑的图形卡与 Windows Mixed Reality 不兼容。 你将需要：

> [!div class="checklist"]
> * 添加 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>此电脑的图形驱动程序不能与 Windows Mixed Reality

这台电脑的图形驱动程序不能与 Windows Mixed Reality 一起使用。 尝试使用 Windows 更新下载新的图形驱动程序：

> [!div class="checklist"]
> * 选择 "**开始 > 设置 > 更新 & 安全性 > 检查更新** 或转到你的电脑或图形卡制造商的网站
> * [检查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果这不起作用，则需要：

> [!div class="checklist"]
> * 添加 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到兼容的 [电脑](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>此电脑的处理器无法与 Windows Mixed Reality

此电脑的处理器不支持 AVX/Popcnt 指令。 若要Windows Mixed Reality，需要：

> [!div class="checklist"]
> * 将其替换为兼容的 [图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到兼容的 [电脑](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>此电脑没有足够的可用磁盘空间来运行Windows Mixed Reality

Windows Mixed Reality设置和最佳性能，需要 10 GB 的可用磁盘空间。 清除驱动器上的一些空间，然后尝试从头开始设置。

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>此电脑运行的是不支持Windows版本的 Windows Mixed Reality

Windows Mixed Reality适用于[Windows 10 家庭版、Windows 10 专业版](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab)和 Windows [](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab) [11。](https://www.microsoft.com/software-download/windows11) 需要安装其中一个版本，以使用Windows Mixed Reality。

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>此电脑未运行最新版本Windows 10

Windows Mixed Reality需要Windows 10 Fall Creators Update。 [更新电脑，](https://support.microsoft.com/help/4028685) 然后重试。

### <a name="this-pc-isnt-running-the-latest-version-of-windows-11"></a>此电脑未运行最新版本的 Windows 11

Windows Mixed Reality需要 Windows 11 最新版本。 [更新电脑，](https://www.microsoft.com/software-download/windows11) 然后重试。

### <a name="this-pc-has-no-usb-30-port"></a>此电脑没有 USB 3.0 端口

需要一个 USB 3.0 端口来连接 Windows Mixed Reality头戴显示设备。 如果使用的是台式电脑，请添加 PCIe USB 卡。 对于笔记本电脑，需要切换到兼容的 [电脑](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="you-cant-run-this-app-via-remote-desktop"></a>无法通过远程桌面运行此应用

若要Windows Mixed Reality，需要一台连接了监视器的电脑。 如果使用的是虚拟机或没有监视器，请尝试使用虚拟显示适配器。 这是一个设备，可插入电脑的 DisplayPort 并模拟计算机显示器。

## <a name="getting-the-best-performance"></a>获得最佳性能

某些硬件配置可能会导致应用程序Windows Mixed Reality。 对于加载缓慢、视觉对象变慢或视觉质量不佳等问题，请尝试以下常见修复：

* 关闭在电脑桌面上运行的任何打开的应用
* 如果使用的是 USB-C 或 DisplayPort 到MIC 适配器，请尝试其他适配器。 请参阅建议的适配器
* 如果附加的监视器连接到电脑的图形卡，请断开其连接
* 尝试从 Windows Store 下载一些不同的混合现实应用-其中一些可能更符合计算机设置
* 查看我们的 [性能问题文档](performance-questions.md)

如果仍遇到性能问题，请更新以下[Windows Mixed Reality设置，](set-up-windows-mixed-reality.md)以获得最佳用户体验：

* 体验
* 解决方法
* 帧速率
* 校准

> [!NOTE]
> 如果看到一条消息，指出"此硬件配置可能适用于 Windows Mixed Reality，但尚未经过测试"，则长时间运行 Windows Mixed Reality 时，可能会遇到一些性能问题。

## <a name="working-with-steamvr"></a>使用 SteamVR

从 SteamVR 中享受游戏是体验 VR 所提供的一切的一种好方法。 但是，你需要确保从沉浸 [式设备获得](performance-questions.md) 最佳性能。 安装 Steam[后：](https://store.steampowered.com/about)

* 按照将[SteamVR 与 Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)
* 安装 [SteamVR 性能测试](https://store.steampowered.com/app/323910/SteamVR_Performance_Test) 应用

## <a name="next-vr-checkpoint"></a>下一个 VR 检查点

如果你遵循我们布局的 VR 旅程，你几乎已准备好购买设备。 在此处，可以继续到最后一个，然后再购买检查点：

> [!div class="nextstepaction"]
> [购买常见问题解答](before-you-buy-faqs.md)

或者直接跳到入门部分：

> [!div class="nextstepaction"]
> [设置Windows Mixed Reality](set-up-windows-mixed-reality.md)

你始终可以随时 [返回到 VR](vr-journey.md) 旅程。