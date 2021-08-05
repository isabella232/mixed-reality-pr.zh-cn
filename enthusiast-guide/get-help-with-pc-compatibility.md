---
title: 获取有关电脑兼容性的帮助
description: 使用应用程序和设备时，请及时获得解决电脑兼容性问题Windows Mixed Reality资源。
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 反馈， 反馈中心， bug
appliesto:
- Windows 10
ms.openlocfilehash: cd5598147823670d1aa00eddda844bea21d7da262339624613f3724cbc5157fa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189209"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>获取有关电脑兼容性的帮助Windows Mixed Reality

在设置Windows Mixed Reality或混合现实门户时，你将获得一个报告[](install-windows-mixed-reality.md)，说明电脑是否由任务完成。 我们在下面各节中详细介绍了你可能会看到的内容。

在进一步操作之前，请尝试以下最常见的修复： 

> [!div class="checklist"]
> * 确保计算机满足最低 [电脑硬件兼容性要求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * 检查图形 [卡和处理器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 是否兼容
> * 检查 [建议的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 列表
> * 通过选择"启动并更新> 设置 >**安全性&更新>检查更新** 

如果要联系，可以询问社区、[联系](https://support.microsoft.com/contactus/)支持人员[](https://answers.microsoft.com)或了解[故障排除](troubleshooting-windows-mixed-reality.md)信息。

## <a name="youre-good-to-go"></a>你可继续

好消息，如果看到"好 **去**"消息，电脑可以运行Windows Mixed Reality！ 计算机硬件和配置之间仍然存在差异，因此混合现实体验可能并非每个电脑上都相同。

## <a name="supports-some-features"></a>支持某些功能

如果看到"支持某些功能"消息，电脑可以运行一些Windows Mixed Reality体验，但可能无法提供最佳体验。 可能的缺点包括图形滞后、性能下降，以及一些你无法运行的应用程序和游戏。 下面列出了你可能会看到的消息以及要执行哪些操作：

* [此电脑具有带单通道 RAM 的集成图形卡](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [此电脑具有具有不兼容 PCIe 链接的混合图形配置](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [此电脑的图形驱动程序可能无法很好地与 Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [此电脑的处理器可能不能很好地与 Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [此电脑可能没有兼容的 USB 配置](#this-pc-might-not-have-a-compatible-usb-configuration)
* [此电脑没有控制器蓝牙 4.0](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [根据头戴显示设备，可能需要一个蓝牙适配器来使用运动控制器](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [此电脑没有自供电 USB 端口](#this-pc-doesnt-have-a-self-powered-usb-port)
* [此电脑的图形卡无法与Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [此电脑的图形驱动程序无法与 Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [此电脑的处理器无法与 Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [此电脑没有足够的可用磁盘空间来运行Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [此电脑运行的是不支持Windows版本的 Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [此电脑未运行最新版本Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [此电脑没有 USB 3.0 端口](#this-pc-has-no-usb-30-port)
* [无法通过远程桌面运行此应用](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>此电脑具有带单通道 RAM 的集成图形卡

集成图形卡在具有Windows Mixed Reality RAM 的 PC 上提供最佳的集成体验。 如果遇到性能问题：

> [!div class="checklist"]
> * 安装兼容的 [离散图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * 安装额外的 RAM 条以创建双通道 RAM
> * 切换到兼容的 [电脑](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>此电脑具有具有不兼容 PCIe 链接的混合图形配置

PCIe 代表 *外围组件互连 Express，* 这是电脑用来与图形卡通信的连接。 配置可能正常工作，但如果遇到问题，则需要切换到兼容的 [电脑](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>此电脑的图形驱动程序可能无法很好地与 Windows Mixed Reality

尝试使用以下方法下载新的图形驱动程序Windows更新：

> [!div class="checklist"]
> * 选择 **"> 设置 >更新&安全性>检查** 更新或访问电脑或图形卡制造商的网站
> * [检查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果不起作用，则需要：

> [!div class="checklist"]
> * 添加 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到兼容的 [电脑](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>此电脑的处理器可能不能很好地与 Windows Mixed Reality

电脑的处理器可能无法很好地与Windows Mixed Reality，因为它没有足够的核心。 如果Windows Mixed Reality运行良好：

> [!div class="checklist"]
> * 将处理器替换为 [兼容的处理器](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 
> * 切换到兼容的 [电脑](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>此电脑可能没有兼容的 USB 配置

对于运行 Windows Mixed Reality：

> [!div class="checklist"]
> * 请查看 [建议适配器文档](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) ，了解常见兼容性问题的解决方案
> * 考虑使用 [外部电源 USB 集线器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

如果问题仍然存在：

> [!div class="checklist"]
> * 将头戴显示设备插入其他 USB 端口（如果有）。
> * 如果不起作用，请卸载电脑的当前 USB 驱动程序，然后重新安装 Microsoft 驱动程序：

1. 选择 **"启动**"，然后在"搜索"框中键入" **设备管理器** "。
2. 从 **设备管理器** 选择"设置"。
3. 展开通用串行总线控制器的类别，查看列出的设备，并卸载任何不兼容的驱动程序。
    * 如果列表包含设备名称末尾没有"Microsoft"的"eXtensible 主机控制器"项，则该驱动程序与 Windows Mixed Reality。 需要卸载它。 若要卸载驱动程序，请右键单击列表中的设备，然后选择"**卸载设备"。** 选中"**删除此设备的驱动程序软件"复选框**，然后选择"卸载 **"。**
    * 如果列表中包含名称中包含"Etron"的"eXtensible 主机控制器"项，则 USB 控制器与Windows Mixed Reality。 需要在电脑上使用不同的 USB 端口，或购买不同的 USB 3.0 主机控制器。
4. 重启你的电脑。
5. 返回到设备管理器并再次找到 eXtensible 主机控制器项。 如果现在设备名称的末尾显示"Microsoft"，则你可以继续操作。 如果没有，请重复卸载步骤以删除驱动程序的任何额外的非 Microsoft 版本。

> [!div class="checklist"]
> * 如果仍然不起作用，请向电脑添加 PCIe USB 卡。

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>此电脑没有控制器蓝牙 4.0

2018 及Windows Mixed Reality头戴显示设备已具有内置 蓝牙，但如果具有较旧的头戴显示设备，则混合现实运动控制器需要蓝牙 4.0。 你仍然可以将[Windows Mixed Reality Xbox](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)控制器、鼠标和键盘或[](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)[USB](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)蓝牙适配器一起用于将运动控制器连接到电脑。 [请参阅建议的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>根据头戴显示设备，可能需要一个蓝牙适配器来使用运动控制器

某些头戴显示蓝牙内置，因此控制器可以直接与头戴显示设备配对。 其他设备蓝牙电脑设备中的 (或单独的) 使用运动控制器。 有关详细信息，请参阅建议的 [适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) 页。

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>此电脑没有自供电 USB 端口

连接头戴显示设备需要自Windows Mixed Reality 3.0 端口。 连接[USB 3.0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)集线器连接到电脑，并使用该集线器连接头戴显示设备。

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>此电脑的图形卡无法与Windows Mixed Reality

此电脑的图形卡与 Windows Mixed Reality。 你将需要：

> [!div class="checklist"]
> * 添加 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到兼容的 [电脑](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>此电脑的图形驱动程序无法与 Windows Mixed Reality

此电脑的图形驱动程序无法与 Windows Mixed Reality。 尝试使用以下方法下载新的图形驱动程序Windows更新：

> [!div class="checklist"]
> * 选择 **"> 设置 >更新&安全性>检查** 更新或访问电脑或图形卡制造商的网站
> * [检查更新](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

如果不起作用，则需要：

> [!div class="checklist"]
> * 添加 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>这台电脑的处理器不能与 Windows Mixed Reality

这台电脑的处理器不支持 AVX/Popcnt 指令。 若要运行 Windows Mixed Reality，需要：

> [!div class="checklist"]
> * 将其替换为 [兼容的图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * 切换到 [兼容的 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>这台电脑没有足够的可用磁盘空间来运行 Windows Mixed Reality

Windows Mixed Reality 需要 10 GB 的可用磁盘空间来安装和最佳性能。 请清除驱动器上的一些空间，然后重新尝试设置。

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>这台电脑正在运行不支持的 Windows 版本 Windows Mixed Reality

Windows Mixed Reality 适用于[Windows 10 家庭版](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab)和[Windows 10 专业版](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab)。 需要安装其中一个版本 Windows Mixed Reality。

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>这台电脑未在运行最新版本的 Windows 10

Windows Mixed Reality 要求 Windows 10 Fall Creators Update。 请[更新你的电脑](https://support.microsoft.com/help/4028685)，然后重试。

### <a name="this-pc-has-no-usb-30-port"></a>此电脑没有 USB 3.0 端口

需要一个 USB 3.0 端口来连接 Windows Mixed Reality 耳机。 如果使用的是台式计算机，请添加 PCIe USB 卡。 对于便携式计算机，需要切换到 [兼容的 PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)。

### <a name="you-cant-run-this-app-via-remote-desktop"></a>无法通过远程桌面运行此应用

若要使用 Windows Mixed Reality，需要一个连接了监视器的 PC。 如果你使用的是虚拟机或没有监视器，请尝试使用虚拟显示适配器。 这是一种插入 PC DisplayPort 并模拟计算机显示的设备。

## <a name="getting-the-best-performance"></a>获得最佳性能

某些硬件配置可能会导致 Windows Mixed Reality 性能问题。 对于速度缓慢、视觉对象不稳定或视觉质量差等问题，请尝试以下常见修复：

* 关闭您的 PC 桌面上运行的任何打开的应用程序
* 如果使用的是 DisplayPort 或到 HDMI 适配器，请尝试其他适配器。 查看建议的适配器
* 如果有额外的监视器连接到 PC 的图形卡，请将其断开连接
* 尝试从 Windows 存储中下载一些不同的混合现实应用，某些应用程序可能更适合你的计算机设置
* 查看我们的 [性能问题文档](performance-questions.md)

如果仍存在性能问题，请更新以下[Windows Mixed Reality](set-up-windows-mixed-reality.md)设置以获得最佳用户体验：

* 体验
* 解决方法
* 帧速率
* 校准

> [!NOTE]
> 如果看到一条消息，指出 "此硬件配置可能与 Windows Mixed Reality 一起使用，但尚未对其进行测试，则在长时间运行 Windows Mixed Reality 时可能会遇到一些性能问题。

## <a name="working-with-steamvr"></a>使用 SteamVR

通过 SteamVR 的 "欣赏游戏" 是一种体验所有 VR 产品/服务的好方法。 但是，你需要确保在沉浸式设备上 [获得最佳性能](performance-questions.md) 。 安装 [流](https://store.steampowered.com/about)后：

* 按照[使用 SteamVR 与 Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)的说明进行操作
* 安装 [SteamVR 性能测试](https://store.steampowered.com/app/323910/SteamVR_Performance_Test) 应用

## <a name="next-vr-checkpoint"></a>下一个 VR 检查点

如果你正在关注我们所做的 VR 旅程，就可以开始购买设备了。 在这里，你可以继续在购买检查点之前的最后一步：

> [!div class="nextstepaction"]
> [购买常见问题解答](before-you-buy-faqs.md)

或者直接转到 "入门" 部分：

> [!div class="nextstepaction"]
> [设置 Windows Mixed Reality](set-up-windows-mixed-reality.md)

随时都可以返回到 [VR 旅程](vr-journey.md) 。