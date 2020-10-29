---
title: Windows Mixed Reality 设置常见问题
description: 获取使用 Windows Mixed Reality 时常见安装问题的答案。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
appliesto:
- Windows 10
ms.openlocfilehash: 2e7276e7d734770e29ce41db9a19ef40555fea30
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677522"
---
# <a name="windows-mixed-reality-setup-faq"></a>Windows Mixed Reality 设置常见问题

下面是一些信息，可帮助解决在设置 Windows Mixed Reality 沉浸式头戴式耳机时可能遇到的问题。

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>我收到一条消息，指出 "我们无法下载窗口混合现实软件"，或者安装程序卡在 "我们进行一些下载时挂起" 页上。

请尝试以下做法：
* 转到 " **设置" > 更新 & 安全 > Windows 更新** ，并确保已打开 "Windows 更新"。 然后，下载并安装任何等待安装的更新。
* 请确保你的电脑已连接到 internet，并且至少有2GB 的可用存储空间。
* 重启电脑，然后重试。 可能需要重复几次，或者运行 Windows 更新疑难解答来清除挂起的更新。 

> [!NOTE]
> * 如果你使用的是企业托管网络，请与你的管理员联系。 它们可能需要启用 Windows Mixed Reality。 正在查找 IT pro 说明？ 请参阅 **[此文](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)** 。
> * 如果 Wi-fi 网络连接设置为 "按流量计费"，请将其更改为 "不按流量"。 **[了解详细信息](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>我收到一条消息，指出出现 "出现错误，无法启动 Windows Mixed Reality"。

请尝试以下做法：
1. 将耳机从计算机拔下 (两个电缆) 。
2. 重新启动计算机。
3. 转到 " **设置" > 更新 & 安全 > Windows 更新** ，并确保已打开 "Windows 更新"。 然后，下载并安装任何等待安装的更新。
4. 将耳机重新连接到计算机，然后重试安装。

如果上述步骤不起作用，请尝试卸载然后重新安装 Windows Mixed Reality。 请参阅 " **设置" > 混合现实 > 卸载** 并选择 " **卸载** "。 然后重新启动计算机。 若要再次开始安装过程，只需将耳机插入 PC 即可。

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>我收到一条消息，指出我的 PC 无法运行 Windows Mixed Reality。

如果收到此消息，则你的电脑不满足运行 Windows Mixed Reality 所需的 [最低要求](https://support.microsoft.com/help/4039260) 。 这可能是因为计算机的硬件设置与 Windows Mixed Reality 不兼容，或者你需要 [更新到最新版本的 windows](https://support.microsoft.com/help/12373)。

图形卡说明：

* 如果 Windows Mixed Reality 安装程序显示您的图形卡无法满足要求，而您认为图形卡有问题，请确保将您的耳机插入正确的卡。
* 咨询您的图形卡制造商以获取最新的驱动程序更新。 Windows Mixed Reality 需要至少支持 WDDM 2.2 的图形卡驱动程序。

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>我收到一条消息，指出： "你几乎在那里，这台电脑不满足运行 Windows Mixed Reality 所需的最低要求。"

如果收到此消息，则表示您的 PC 不满足在 Windows Mixed Reality 中获得最佳体验所需的最低要求。 你的电脑或许能够运行沉浸式耳机，但可能无法运行某些应用程序，或者可能存在性能问题。

## <a name="my-xbox-controller-isnt-working"></a>我的 Xbox 控制器不能正常工作。

请尝试以下做法：

* 确保控制器已打开、完全充电并连接到 PC。
* 更换控制器的电池。
* 如果你使用的是蓝牙控制器，请参阅 " **设置" > 设备 "> 蓝牙 & 其他设备** 上的" 设备 "，并确保其配对 (你应看到它在页面) 上列出。

[了解有关 Xbox 控制器的详细信息](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>运动控制器不起作用。
 
请尝试以下做法：

* 确保你的控制器已打开并完全充电。
* 更换控制器电池。
* 将控制器保持在您的前方，同时关闭控制器并将其打开。 按住 Windows 按钮4秒钟，使控制器关闭，然后再次按下并保持2秒，以将其打开。 
* 请访问 " **设置" > 设备上 > 蓝牙 & 其他设备** 上的设备，并确保它们已配对， (应会看到页面) 上列出它们。

[了解有关运动控制器的详细信息](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>我收到一条消息，显示 "连接耳机"，即使我已插入我的耳机

请尝试以下做法：

* 请确保将耳机连接到计算机上的正确端口。 它应插入到电脑的单独图形卡和 USB 3.0 端口。 下面介绍如何识别正确的端口：
    * USB 3.0 端口有一个特殊的徽标，其中 "SS" 标记 (表示 "SuperSpeed" ) 。 端口的内部片通常为蓝色，而旧的 USB 2.0 端口通常在内部为黑色或白色。
    * 如果计算机有两个 HDMI 端口，请使用连接到图形卡的端口，而不是计算机的主板。 这并不总是很明显，但不同的端口通常位于计算机上的扩展插槽中。 如果尝试一个端口但它不起作用，请尝试其他端口。
* 请参阅耳机制造商的网站并更新耳机的驱动程序和固件。

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>尝试创建边界时，收到错误消息。

下面是创建边界的一些准则：

* 切勿接近墙壁或其他障碍。
* 请确保在跟踪边界时，将耳机置于 waist 高度，并面对计算机。
* 请确保传感器未被阻止且有足够的光线。
* 跟踪的空间应大于3个平方米。
* 空间不应太大或太复杂，请坚持使用简单的几何形状，而不会有很多旋转。
* 请不要在跟踪时返回到自己的路径。
* 如果你的角落停滞，请重新开始。

**如果我选择 "仅限上的"，则我有哪种类型的体验？**

"仅限固定和放置" 表示你将在没有边界的情况下使用耳机。 你需要保留在一个位置，因为你没有边界来帮助你避免物理障碍。 此外，某些应用和游戏可能设计为与边界一起使用，因此它们可能无法按预期工作。

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>如何在我的耳机中获得更清晰的视图？

尝试调整耳机大小。 通过向上、向下或向左和向右移动，调整传送带的位置，并调整传送带，使其感觉 snug。

如果耳机支持，还可以调整其校准设置。 如果头戴式耳机有调整校准的旋钮，请使用。 如果没有，请参阅 " **设置" > 混合现实 > 视觉质量** 并调整其中的校准。 有关特定设备的校准的详细信息，请与耳机制造商联系。

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality 支持哪些语言？

Windows Mixed Reality 提供以下语言版本。 如果你的电脑设置为另一种语言，你仍可以使用 Windows Mixed Reality，但界面将以英语 (美国) ，并且语音命令和听写将不可用。

* 简体中文（中国）
* 英语（澳大利亚）
* 英语（加拿大）
* 英语（英国）
* 英语（美国）
* 法语（加拿大）
* 法语（法国）
* 德语（德国）
* 意大利语（意大利）
* 日语（日本）
* 西班牙语(墨西哥)
* 西班牙语(西班牙)

你还可以使用上面列出的受支持的 Windows Mixed Reality 语言之一来使用听写，只需在屏幕键盘上选择 " **麦克风**  " 即可。

Windows Mixed Reality 还提供以下语言版本，无需语音命令或听写功能：

* 繁体中文 (台湾和中国香港) 
* 荷兰语（荷兰）
* 韩语(韩国)
* 俄语（俄罗斯）

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>当我插入我的耳机时，无任何反应—混合现实门户不会打开。

混合现实门户是指通过 Windows Mixed Reality 安装程序的应用程序，它设计为在你插入兼容的耳机时自动打开。 如果未打开，请在 **搜索** 框中转到 " **开始** " 并键入 " **混合现实门户** "，打开该应用。 如果找不到混合现实门户，这可能意味着您需要 [更新到最新版本的 Windows](https://support.microsoft.com/help/12373) ，或者您的耳机未正确连接到 PC。

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer"></a>我在我的耳机中听不到任何声音，或通过我的计算机播放声音。

如果沉浸式耳机不包含内置耳机，则需要将耳机连接到耳机上的音频插孔。  (插孔通常位于耳机面板或重用功能区的后面;如果找不到你的耳机制造商，请与你的耳机制造商联系。 )  

某些音频耳机有物理按钮来控制音量。 如果音频不起作用，请检查卷是否已关闭或静音。

Windows Mixed Reality 旨在在您戴上声音时通过沉浸式耳机播放声音，并使耳机连接到它。 当你将面板上滑或上滑上时，音频将切换到默认的 Windows 播放设备。 你可以在 "设置" 中更改此设置 **> 混合现实 > 音频和语音** 。

> [!NOTE]
> * Windows Mixed Reality 空间音频最适合用于直接内置或直接连接到沉浸式耳机的耳机。 连接到 PC 的 PC 扬声器或耳机可能不适用于空间音频。
> * Windows Mixed Reality 不支持蓝牙音频耳机。

## <a name="speech-commands-arent-working"></a>语音命令不起作用。

若要使用语音命令，你的电脑的语音和语言设置必须设置为 Windows Mixed Reality 支持的一种 [语言](#what-languages-are-supported-in-windows-mixed-reality) 。 若要对此进行检查，请转到 " **设置" > time & language > 区域 & 语言** 和 **设置 > time & language > 语言语音** 。

如果耳机没有内置 mic，则需要将带麦克风的耳机连接到耳机或电脑。 若要让 mic 输入在戴上时自动切换到你的耳机，请转到 " **设置" > 混合现实 > 音频和语音** ，并确保在戴上 **耳机时，切换到 "耳机麦克风** "。

某些音频耳机有一个 "物理" 按钮，可将麦克风静音并取消静音。 如果语音命令不起作用，请检查你的 mic 是否已静音。

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>我的 head 装入显示在关闭后不起作用，请快速启动。

试试看：

* 从打印头安装显示器拔下显示电缆和 USB 电缆，然后将其插回。

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>使用 Windows Mixed Reality 时，Wi-fi 会变慢

如果使用的是 2.4 GHz Wi-fi 连接，则运动控制器可能会减慢 Wi-fi 的速度。 尝试以下任一项：

* 切换到 5 GHz Wi-fi 连接（如果有）。 了解更多
* 使用单独的蓝牙适配器将运动控制器连接到您的 PC。 [查看建议的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> 较新的耳机对通过内置的蓝牙芯片直接通过内置的蓝牙芯片，而不会遇到此问题。 

## <a name="see-also"></a>请参阅
* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)
* [故障排除](troubleshooting-windows-mixed-reality.md)

