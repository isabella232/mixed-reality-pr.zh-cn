---
title: 耳机显示 Faq
description: 显示针对耳机显示问题的 Windows Mixed Reality 故障排除，超出了标准消费者支持文档的范围。
author: qianw211
ms.author: v-qianwen
ms.date: 09/30/2020
ms.topic: article
keywords: Windows Mixed Reality，Mixed reality，虚拟现实，VR，先生，故障排除，错误，帮助，支持
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 5a7c7979c9d93d917633cbfed23dc82597368a43
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436675"
---
# <a name="headset-display-faqs"></a>耳机显示 Faq

## <a name="my-headset-displays-are-black"></a>我的耳机显示为黑色

* 检查您的 PC 性能和稳定性：
    * 使用任务管理器查看是否有任何进程支持您的 PC 的 CPU、GPU 或磁盘驱动器。
    * 检查 **事件查看器 > Windows 日志** 中的 "应用程序" 和 "系统" 日志，以查看应用是否崩溃并生成 Windows 错误报告 (WER) 报告。
    * 检查 Windows 更新，确保 Windows 的版本是最新版本。 可能需要多次选择 "检查更新"。
* 检查应用和游戏稳定性：
    * 确保你的电脑满足任何未正常运行的应用程序或游戏的最低系统要求。
    * 确保你的 GPU 驱动程序版本是最新版本，并检查新驱动程序是否存在任何新的性能和兼容性问题和回归。
    * 如果你使用的是 SteamVR 应用和游戏，请确保 SteamVR 和 SteamVR 组件的 Windows Mixed Reality 都是最新的。
* 检查 HDMI 适配器的兼容性：
    * 请确保 HDMI 电缆一直处于插入的方向。
    * 如果使用的是 HDMI 适配器 (例如，微型 DisplayPort to HDMI 适配器) ，请确保它与 Windows Mixed Reality 兼容。 适配器必须支持 HDMI 2.0，并且有许多较早的适配器仅支持1080p。 请参阅[Windows Mixed Reality 的推荐适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)。
    * 插头顺序很重要。 在将耳机连接到适配器之前，连接 HDMI 适配器连接到电脑，尤其是在使用 USB 到 HDMI 适配器的情况下。
    * 如果正在使用，请尝试删除扩展电缆。
* 检查图形卡和驱动程序兼容性：
    * 使用 PC 监视器尝试您的 PC 的 HDMI 端口。 某些 Pc 可能有多个 HDMI 端口，而且并非所有计算机都处于活动状态。
    * 如果你的电脑具有集成的图形处理单元 (iGPU) 和离散图形处理单元 (dGPU) ，请确保已插入 dGPU 的 HDMI 端口。
    * 仔细检查 GPU 驱动程序版本。 请确保它是最新的，还应注意任何新的性能和兼容性问题以及新驱动程序的回归。
    * 如果在笔记本电脑上使用混合现实，并且已从图形卡制造商的网站安装了更新的图形驱动程序，请尝试降级到电脑制造商网站上提供的最新图形卡驱动程序，或 Windows 更新上。
    * 如果你有多台电脑监视器连接到电脑，请尝试暂时断开连接，而不是一台 PC 监视器。
    * 如果已为电脑监视器设置自定义刷新速率，请尝试暂时还原为标准刷新率，如 60 Hz。
    * 如果最近更改了图形卡而不重新安装 Windows，请检查耳机监视器是否仍然安装了正确的驱动程序。 接通耳机后，确认 "Mixed Reality 耳机" 列在 Device Manager 的 "监视器" 节点下。
    * 如果你的电脑具有 Nvidia 图形卡，请确保已禁用 Nvidia 的3D 远景软件。
    * 对于某些显卡 (特别) 的卡，HDMI 端口可能不支持 HDMI 2.0，或可能不与 Windows Mixed Reality 完全兼容。 尝试使用 [DisplayPort 1.2 到 HDMI 2.0 适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)的图形卡的 DisplayPort。
    * hp Omen 电脑（hp 产品编号为 1RJ99EA # 阿尔）具有与 Windows Mixed Reality 不兼容的 HDMI 端口 (打开 "HP 支持助手"，号码将列在应用) 的底部。
    * 如果你的电脑具有 AMD R9 系列显卡，而你使用的是 Samsung 混合现实耳机，请将耳机固件更新到版本1.0.8 或更高版本，以便将你的图形卡的 HDMI 端口与耳机一起使用。
    * 如果你使用的是 Surface Book 2，请确保使用的是从[USB 到 HDMI 适配器的接口](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)。
* 检查混合现实耳机硬件问题：
    * 若要针对耳机确认或排除硬件问题，请将混合现实耳机连接到另一台 PC。
    * 首先检查计算机兼容性和安装问题，因为症状类似。
* 请确保已将 USB 电缆插入 USB 3.0 或更快的端口。 USB 3.0 端口具有 SS () 旁边的超级速度，并且通常彩色为蓝色。

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>某些使用后，耳机显示偶尔变为黑色

* 尝试在电脑上禁用任何 USB 挂起或节能功能。 例如，在 **设置 > 系统 > Power & 睡眠 > [USB 选择性挂起](/windows-hardware/drivers/usbcon/usb-selective-suspend)**，Device Manager 中的 "允许计算机关闭此设备以节省电源" 设置，以及 PC 固件中任何 USB 节能设置。
* 暂时断开连接到电脑的任何其他 USB 设备和外围设备。
* 检查你的 GPU 驱动程序版本是否为最新版本，并检查新驱动程序是否存在任何新的性能和兼容性问题和回归。

## <a name="one-of-the-displays-on-my-headset-is-black"></a>我的头戴显示设备上显示的一个显示黑色

* 如果使用的是 HDMI 适配器，请确保它支持 HDMI 2.0。
* 删除任何可能使用的 USB 和 HDMI 扩展电缆。
* 请确保图形驱动程序是最新的。
* 尝试将混合现实耳机置于另一台电脑上。

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>我的耳机显示为蓝色，然后混合现实门户重新初始化

这通常表示你的电脑上偶尔出现 USB 控制器可靠性问题：

* 请尝试其他 USB 端口。 你的电脑可能有多个 USB 3.0 控制器。
* 如果适用) ，请 (删除任何扩展电缆。
* 拔下 PC 中的所有其他 USB 设备。
* 连接外部接通电源的 USB 3.0 集线器连接到电脑，并将耳机连接到中心。
* 如果使用的是台式计算机，请考虑购买 USB 3.0 PCIe 卡，将另一个 USB 控制器添加到您的 PC。

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>我的耳机使我的 PC 挂起或在启动时显示黑屏

在某些电脑上，在打开或重启电脑时，让你的耳机保持接通电源可能会影响其启动过程。 你的电脑可以选择耳机显示为 "主监视器" 以显示 PC 启动进度、不能正常启动或 "挂起" 或产生报警音错误代码。 此行为取决于计算机制造商和型号，或者图形卡的品牌和型号。 解决方法：

* 连接耳机到图形卡上的另一个端口 (可能需要使用适配器来) 使用其他端口。
* 请确保您的 PC 的 BIOS/UEFI 固件是最新的 (但仅更新您的 PC 的 BIOS/UEFI 固件) 。

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>使用 Surface PC 时，电脑或耳机显示闪烁、闪烁或保持黑屏

* 请确保使用的是支持 HDMI 2.0 的 HDMI 适配器。 许多老式的 HDMI 适配器仅支持1080p 分辨率，这对于混合现实耳机来说是不够的。
* 请确保您的图形驱动程序是最新的。 请查看 Windows 更新和 PC 制造商的网站以获取更新的图形驱动程序。
* 某些 Surface 设备与 Windows Mixed Reality 不兼容。 了解有关 [Surface 兼容性和要求](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)的详细信息。

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>我的耳机显示在关闭后不起作用，请快速启动

从耳机拔下 HDMI 电缆和 USB 电缆，然后将其重新插回。

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>我的耳机显示断断续续，但混合现实门户的预览窗口显示良好

* 请确保您的 PC 的系统资源 (CPU、内存和硬盘驱动器) 可用，而不会被其他应用程序或进程使用。
* 更新图形驱动程序。

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>在 Device Manager 中收到 "安装类不存在或无效" 错误

如果在 Device Manager 中看到 "HoloLens 传感器" 带有黄色惊叹号，请选择该设备了解更多详细信息。 如果看到一条消息，指出 "未安装此设备的驱动程序。  (代码 28) -安装类不存在或无效 "，这通常是因为你的电脑运行[Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)。N 版本的 Windows 10 和 Windows 11 不支持 Windows Mixed Reality，你将需要安装 Windows 10 或 Windows 11 的非 N 版本。

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>我的 WMR 环境在移动头时出现抖动或 stutters，并显示双重视觉

在具有集成图形和 Nvidia GPU 的便携式计算机上，在一段时间后出现错误，使上一个帧在下一帧之后显示，从而使双愿景在偏航、音调或滚动移动过程中移动的速度更快。 此问题似乎出现在 Nvidia 图形驱动程序436.48 之后的驱动程序中。  安装此驱动程序将解决此问题，直至 Nvidia 解决更新的驱动程序中的问题。 若要直接安装 Nvidia 图形驱动程序436.48，请访问 [nvidia](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)。

## <a name="im-uncomfortable-in-my-headset"></a>我对我的耳机不舒服

有关 Windows Mixed Reality 的舒适的一般信息，请参阅[Windows Mixed Reality 沉浸式耳机运行状况、安全和舒适](wmr-health-safety-comfort.md)。 有关特定耳机的详细信息，请与耳机制造商联系。

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>如何在我的耳机中获得更清晰的视图

尝试调整耳机大小。 将其上移和下移，或向左和向右移动，并调整传送带，使其感觉 snug。

如果头戴式耳机有调整校准的旋钮，请调整其校准设置。 否则，请 **设置 > 混合现实 > 视觉质量** 并调整其中的校准。 有关特定设备的校准的详细信息，请与耳机制造商联系。

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>我经常会看到头戴显示在视图周围的黑色边框。 有时，就像我向下看隧道一样

这意味着应用程序无法达到电脑上的帧速率，并且系统正在使用旧帧在头戴显示设备中呈现视图。 由于应用程序只呈现你正在查看的部分世界，因此，如果它们不一致地达到其帧速率，系统将尝试从以前的角度呈现世界，并且会用黑色填充缺失的详细信息。 如果这种情况频繁发生：

1. 关闭或停止所有不需要的程序以释放内存和 CPU。
2. 减少应用程序中的详细信息设置。
3. 转到 **"设置 >混合现实>头** 戴显示"，以减少设备主页中显示的Windows Mixed Reality量。

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>头戴显示设备中的视图非常抖动和抖动

系统可能无法向头戴显示设备呈现内容，或者跟踪系统可能遇到问题：

1. 打开任务管理器，确保电脑有足够的计算资源。 应具有 80% 的可用 CPU、400 MB 的 RAM，磁盘 IO 应低于 80%。
2. 确保具有适用于硬件的最新图形驱动程序。 请参阅图形 [驱动程序部分](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver)。
3. 确保房间有足够的光线。
4. 拔下设备，Windows Mixed Reality，然后再次插入。
5. 重启你的电脑。
6. 如果问题仍然存在，请联系 [客户支持](https://support.microsoft.com/)。