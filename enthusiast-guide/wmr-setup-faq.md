---
title: Windows Mixed Reality 开发人员工具包常见问题解答
description: 获取在使用 Windows Mixed Reality 应用程序和设备时的常见问题的解答。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
appliesto:
- Windows 10
ms.openlocfilehash: 87eb22e600ca2426bdd3fec1fd428c11d9c45313
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581809"
---
# <a name="windows-mixed-reality-setup-faq"></a>Windows Mixed Reality 开发人员工具包常见问题解答

下面是一些信息，可帮助解决在设置 Windows Mixed Reality 沉浸式头戴式耳机时可能遇到的问题。

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>我收到一条消息，指出 "我们无法下载窗口混合现实软件"，或者安装程序卡在 "我们进行一些下载时挂起" 页面

请尝试以下步骤：

* 转到 " **设置" > 更新 & 安全 > Windows 更新** ，并确保已打开 "Windows 更新"。 然后，下载并安装任何等待安装的更新。
* 请确保你的电脑已连接到 internet，并且至少有 2 GB 的可用存储空间。
* 重启电脑，然后重试。 可能需要重复几次，或者运行 Windows 更新疑难解答来清除挂起的更新。

> [!NOTE]
> * 如果你使用的是企业托管网络，请与你的管理员联系。 它们可能需要启用 Windows Mixed Reality。 正在查找 IT pro 说明？ 请参阅 **[此文](/windows/application-management/manage-windows-mixed-reality)**。
> * 如果 Wi-Fi 网络连接设置为 "按流量计费"，请将其更改为 "不按流量"。 **[了解详细信息](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>我收到一条消息，指出出现 "出现错误，无法启动 Windows Mixed Reality"。

请尝试以下步骤：

1. 将耳机从计算机拔下 (两个电缆) 。
2. 重新启动计算机。
3. 转到 " **设置" > 更新 & 安全 > Windows 更新** ，并确保已打开 "Windows 更新"。 然后，下载并安装任何等待安装的更新。
4. 将耳机重新连接到计算机，然后重试安装。

如果上述步骤不起作用，请尝试卸载然后重新安装 Windows Mixed Reality。 请参阅 " **设置" > 混合现实 > 卸载** 并选择 " **卸载**"。 然后重新启动计算机。 若要再次开始安装过程，只需将耳机插入 PC 即可。

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>当我插入我的耳机时，混合现实门户不会打开

混合现实门户是指通过 Windows Mixed Reality 安装程序的应用程序，它设计为在你插入兼容的耳机时自动打开。 如果未打开，请在 "搜索" 框中输入 "混合现实门户" 以打开应用。 如果找不到混合现实门户，可能需要 [更新到最新版本的 Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq) 。

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>我收到一条消息，指出我的 PC 无法运行 Windows Mixed Reality

如果收到此消息，则你的电脑不满足运行 Windows Mixed Reality 所需的 [最低要求](https://support.microsoft.com/help/4039260) 。 计算机的硬件设置可能与 Windows Mixed Reality 不兼容，或者可能需要 [更新到最新版本的 windows](https://support.microsoft.com/help/12373)。

图形卡说明：

* 如果 Windows Mixed Reality 安装程序显示您的图形卡无法满足要求，而您认为图形卡有问题，请确保将您的耳机插入正确的卡。
* 咨询您的图形卡制造商以获取最新的驱动程序更新。 Windows Mixed Reality 需要至少支持 WDDM 2.2 的图形卡驱动程序。

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>我收到一条消息，指出： "你几乎在那里，这台电脑不满足运行 Windows Mixed Reality 所需的最低要求。"

如果收到此消息，则表示您的 PC 不满足在 Windows Mixed Reality 中获得最佳体验所需的最低要求。 你的电脑可以运行沉浸式耳机，但可能无法运行某些应用程序，或者可能存在性能问题。

## <a name="my-xbox-controller-isnt-working"></a>我的 Xbox 控制器不工作

请尝试以下步骤：

* 确保控制器已打开、完全充电并连接到 PC。
* 更换控制器的电池。
* 如果你使用的是蓝牙控制器，请参阅 " **设置" > 设备 "> 蓝牙 & 其他设备** 上的" 设备 "，并确保其配对 (你应看到它在页面) 上列出。

[了解有关 Xbox 控制器的详细信息](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>运动控制器不起作用

请尝试以下步骤：

* 确保你的控制器已打开并完全充电。
* 更换控制器电池。
* 将控制器保持在您的前方，同时关闭控制器并将其打开。 按住 Windows 按钮4秒钟关闭控制器，然后再次按住该控制器2秒钟，以将其打开。
* 请访问 " **设置" > 设备上 > 蓝牙 & 其他设备** 上的设备，并确保它们已配对， (应会看到页面) 上列出它们。

[了解有关运动控制器的详细信息](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>我收到一条消息，显示 "连接耳机"，即使我已插入我的耳机

请尝试以下步骤：

- 请确保将耳机连接到计算机上的正确端口。 它应插入到电脑的单独图形卡和 USB 3.0 端口。 下面介绍如何识别正确的端口：
    - USB 3.0 端口有一个特殊的徽标，其中 "SS" 标记 (表示 "SuperSpeed" ) 。 端口的内部片通常为蓝色，但较旧的 USB 2.0 端口通常为黑色或白色。
    - 如果计算机有两个 HDMI 端口，请使用连接到图形卡的端口，而不是计算机的主板。 这并不总是显而易见的，尽管离散端口通常位于计算机上的扩展插槽中。 如果尝试一个端口但它不起作用，请尝试其他端口。
- 请参阅耳机制造商的网站并更新耳机的驱动程序和固件。

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>在混合现实启动过程中，我停滞在 "转向你的一端，然后在地板"

此步骤允许耳机识别空间，并还原任何现有的虚拟楼层和边界。 当你放在你的耳机上时，此扫描过程可能需要长达10秒的时间。 完成后，你将处于 Windows Mixed Reality 主页，否则系统将提示你重新设置边界。

如果扫描过程所用时间超过10秒，则耳机中的邻近感应传感器可能出现问题：

1. 检查是否已从邻近感应传感器中删除不干胶标签。 邻近感应感应器位于耳机内，大致位于 forehead 的中心。
2. 检查邻近感应传感器是否正在将输入切换到你的耳机：使用手指覆盖并抽出几次近程传感器，验证输入是否正在切换到耳机。 你应在电脑顶部看到 " **Windows 键 + Y** " 横幅。 您可以通过在键盘上键入 **Windows Key + Y** ，随时手动切换到耳机的输入。

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>我的 Windows Mixed Reality 主页的底层看起来不是正确的高度

选择 **开始 > 楼层调整**，一旦将应用放入世界，就会启动，以便在戴上耳机时进行更改。 在此应用中，你将被定向到使用触摸板 (运动控制器) 或方向板 (游戏板) 调整地面高度。 如果地面正确，请使用 Windows 按钮返回到你的主页。

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>我无法在我的桌面上显示我在我的耳机上看到的内容的预览

Windows Mixed Reality 门户在屏幕底部有一个 " **播放** " 按钮，可让你在桌面屏幕上预览你在手机上看到的内容。 出于性能方面的考虑，此功能仅适用于在 Windows Mixed Reality 上运行的 Pc 上的 Ultra (90 Hz) 。

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>如何在我的耳机中获得更清晰的视图

尝试调整耳机大小。 通过向上、向下或向左和向右移动，调整传送带的位置，并调整传送带，使其感觉 snug。

如果耳机支持，还可以调整其校准设置。 如果头戴式耳机有调整校准的旋钮，请使用。 如果没有，请参阅 " **设置" > 混合现实 > 视觉质量** 并调整其中的校准。 有关特定设备的校准的详细信息，请与耳机制造商联系。

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>当我插入我的耳机时，无任何反应—混合现实门户不会打开

混合现实门户是指通过 Windows Mixed Reality 安装程序的应用程序，它设计为在你插入兼容的耳机时自动打开。 如果未打开，请在 **搜索** 框中转到 "**开始**" 并键入 "**混合现实门户**"，打开该应用。 如果找不到混合现实门户，这可能意味着您需要 [更新到最新版本的 Windows](https://support.microsoft.com/help/12373) ，或者您的耳机未正确连接到 PC。

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>我的 head 装入显示在关闭并快速启动后无法正常工作

试试看：

* 从打印头安装显示器拔下显示电缆和 USB 电缆，然后将其插回。

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>使用 Windows Mixed Reality 时，Wi-Fi 会减缓

如果使用的是 2.4 GHz Wi-Fi 连接，则运动控制器可能会减慢 Wi-fi 的速度。 请尝试执行以下步骤之一：

* 切换到 5 GHz Wi-Fi 连接（如果有）。 了解详细信息
* 使用单独的蓝牙适配器将运动控制器连接到您的 PC。 [查看建议的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> 较新的耳机对通过内置的蓝牙芯片直接通过内置的蓝牙芯片，而不会遇到此问题。

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>我收到 "出现错误" 错误消息，或在混合现实门户中遇到问题

若要获取有关特定错误代码的详细信息，请查看 [此处](error-codes.md)。 你还可以尝试：

重启 Windows Mixed Reality：

1. 从电脑拔下耳机电缆。
2. 重启你的电脑。
3. 重新连接耳机。

确保你的电脑能识别你的耳机：

1. 选择“启动”。
2. 在搜索框中键入 "设备管理器"，并在列表中选择它。
3. 展开 "Mixed reality 设备"，并查看是否列出了你的耳机。

如果未列出：

1. 将耳机插入电脑上的不同端口（如果可用）。
2. 查看 Windows 更新中的最新软件更新。
3. 卸载并重新安装 Windows Mixed Reality：
    1. 从电脑拔下耳机电缆。
    2. 选择 " **设置" > 混合现实 > 卸载**"。
    3. 如果运动控制器与电脑配对，请选择 " **设置" > 设备 > 蓝牙 & 其他设备** 进行取消配对。 选择每个控制器，然后选择 "删除设备"。 如果控制器与耳机配对，则可以跳过此步骤。
    4. 将您的耳机插回您的 PC 上，重新安装 Windows Mixed Reality。

## <a name="see-also"></a>另请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)
* [疑难解答](troubleshooting-windows-mixed-reality.md)