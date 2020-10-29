---
title: 使用 Windows Mixed Reality 常见问题解答
description: 获取使用 Windows Mixed Reality 时的常见问题的解答。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
appliesto:
- Windows 10
ms.openlocfilehash: 62b6b61f74abfd77ba61563639ff719576551f07
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677538"
---
# <a name="using-windows-mixed-reality-faq"></a>使用 Windows Mixed Reality 常见问题解答

如果你需要使用 Windows Mixed Reality 沉浸式耳机的相关帮助，请查看以下主题，了解常规信息和故障排除。

仍需帮助？ 若要进行高级故障排除，请参阅此文。

## <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>我看到一条消息，显示 "丢失跟踪" 或 "我们没有此空间的边界"。

在桌面上选择 " **启动 > 混合现实门户** "。 选择 " **菜单** "，然后选择 " **运行安装程序** " 以创建新边界。 Windows Mixed Reality 支持多个位置，并且将在启动时识别你处于启动状态的空间，前提是该会议室未发生显著更改。  


## <a name="i-cant-hear-any-sound-or-the-sound-is-coming-from-my-computer-instead-of-my-headset"></a>听不到任何声音，或声音来自我的计算机而不是我的耳机

如果沉浸式耳机不包含内置耳机，则需要将耳机连接到耳机上的音频插孔。  (插孔通常位于耳机面板或重用功能区的后面;如果找不到你的耳机制造商，请与你的耳机制造商联系。 )  

某些音频耳机有物理按钮来控制音量。 如果音频不起作用，请检查卷是关闭还是静音。

Windows Mixed Reality 旨在在您戴上声音时通过沉浸式耳机播放声音，并使耳机连接到它。 当你将面板上滑或上滑上时，音频将切换到默认的 Windows 播放设备。 你可以在 "设置" 中更改此设置 **> 混合现实 > 音频和语音** 。

> [!NOTE]
> * Windows Mixed Reality 空间音频最适合用于直接内置或直接连接到沉浸式耳机的耳机。 连接到 PC 的 PC 扬声器或耳机可能不适用于空间音频。
> * Windows Mixed Reality 不支持蓝牙音频耳机。

## <a name="speech-commands-arent-working"></a>语音命令不起作用

若要使用语音命令，你的电脑的语音和语言设置必须设置为 [受支持的 Windows Mixed Reality 区域和语言](wmr-setup-faq.md#what-languages-are-supported-in-windows-mixed-reality)。 若要检查您的 Windows 区域和语言，请选择 " **设置" > Time & language > region & language** "。 若要检查您的语音语言，请选择 " **设置" > Time & language > Speech** "。

如果耳机没有内置麦克风，请将耳机和麦克风一起连接到耳机或电脑。 若要在耳机直接连接到耳机时自动切换到你的耳机，请选择 " **设置" > 混合现实 > 音频和语音** ，并确保在戴上 **耳机时，切换到 "耳机麦克风** "。

某些音频耳机有一个 "物理" 按钮，可将麦克风静音并取消静音。 如果语音命令不起作用，请检查 mic 是否已静音。

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>边界始终可见。 如何使其消失？

当你接近边界时，它将显示。 如果边界包含的任何部分都具有较窄或不规则的形状，您可能最终会接近它并导致其出现，而不像您所希望的那样。 若要解决此问题，请尝试使用更大、更普通的形状再次创建边界。 选择桌面上的 " **开始 > 混合现实门户** "，然后选择 " **运行安装程序** "。 

还可以从混合现实门户中暂时关闭边界：选择 **菜单** ，然后使用切换关闭边界。 当边界关闭时，您需要停留在一个位置以避免出现障碍。

## <a name="im-having-trouble-with-my-motion-controllers"></a>我无法处理运动控制器

如果运动控制器不能正常工作、未连接或在戴上耳机时看不到控制器的图像，请尝试以下操作：

* 请确保已打开控制器。 若要将其打开，请按住 **Windows** 按钮2秒。
* 选择 "开始 > 计算机上的 **混合现实门户** "，然后选择 " **菜单** "，你应该会看到已列出的运动控制器以及状态消息：
    * 就绪–控制器都已设置好。
    * 丢失跟踪–混合现实门户找不到控制器。 将其放在头戴戴显示设备前面，按 " **Windows** " 按钮4秒钟再重新启动，然后再次2秒钟。
    * 电池电量低–更换控制器电池。
* 如果使用 Wi-fi，请尝试将电脑连接到 5GHz Wi-fi 网络，以减少无线干扰。 
* 对于直接与控制器配对的较新耳机，选择 **"..."** 按钮， **然后选择** " **设置控制器** "。 这会转到耳机应用，将控制器与耳机配对。  
* 对于不具备内置蓝牙以便控制器直接配对的老式耳机：  
    * 选择 "设置" > 设备 > 蓝牙 & 计算机上的其他设备，并确保控制器已按配对方式列出。如果不是，则需要将它们配对。 
    * 如果有与电脑配对的其他蓝牙设备，如耳机或 gamepads，请尝试删除一些蓝牙设备。 选择 " **设置" > 设备上 > 蓝牙 & 其他设备** "，选择设备，然后选择" **删除设备** "。
    * **> 设备 > 蓝牙 & 其他设备** 中删除蓝牙耳机和扬声器，并关闭设备。 
    * 如果使用的是 USB 蓝牙适配器，请确保将其插入到黑色 USB 2.0 端口，并尽可能远离任何其他无线发送器或 USB 闪存驱动器（包括耳机的 USB 连接器）连接。 
    * 如果你的电脑具有内置的蓝牙，并且你有连接问题，请尝试改用 USB 蓝牙适配器。  (为此，你还需要关闭 [设备管理器](https://support.microsoft.com/help/4026149)中内置的蓝牙无线电，然后将其他蓝牙设备与新的适配器配对。 ) 
* 如果 "设置" 应用打开到 "蓝牙 & 其他设备" 页，请将其关闭。

## <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>我使用耳机时遇到 discomfort

有关 Windows Mixed Reality 中舒适的一般信息，请参阅 [Windows Mixed reality 沉浸式耳机运行状况、安全和舒适](wmr-health-safety-comfort.md)。 有关特定耳机的详细信息，请与耳机制造商联系。

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>我的视觉对象不连贯、负载缓慢或外观不佳

如果你的混合现实视觉对象看不到最好，请尝试以下做法。

* 请确保将耳机插入 PC 上的正确图形卡。 某些 Pc 同时具有集成显卡和离散显卡。 离散卡通常会提供最佳性能。 [了解有关 PC 硬件的详细信息](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。
* 关闭桌面上未使用的应用。
* 调整耳机大小：将其向下、向下或向左和向右移动，并确保其适合 snugly。
* 将耳机的视觉设置 ( **设置 > 混合现实 > 耳机显示** ) 。 当 " **视觉质量** " 设置为 " **自动** " 时，我们将为你的电脑选择最佳混合现实体验。 若要获得更多视觉细节，请将 **视觉质量** 设置为 **高** 。 如果你的视觉对象不连贯，你可能想要选择较低的设置。
* 尝试调整头戴显示设备的校准。 应对重用功能区进行调整，使之与你的 interpupillary 距离 (IPD) ，瞳孔之间的距离。 如果你不知道 IPD，optometrist 应能够为你衡量。 此外，还设计了用于度量 IPD 的网站。 了解 IPD 后，请使用耳机的校准旋钮进行调整。 如果耳机没有校准旋钮，请选择 " **设置" > 混合现实 > 耳机显示** 并调整校准控件。

## <a name="i-have-questions-about-my-headset-hardware"></a>我对我的耳机硬件有疑问

有关手机支持的详细信息，请咨询制造商。 可以在框中提供产品指南，也可以尝试使用制造商的网站。

## <a name="the-floor-in-mixed-reality-seems-to-be-in-the-wrong-spot"></a>混合现实中的地面似乎位于错误的位置

如果地面看上去 (例如，你觉得你的浮动) ，请选择 " **开始" > 房间调整** ，同时戴上耳机进行更改。

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>我收到一条消息，指出我的 PC 已接通电源并向其收费。 为什么？

如果使用便携式计算机，则当电脑完全充电并接通电源时，Windows Mixed Reality 的效果最佳。 

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>如何实现卸载 Windows Mixed Reality？

选择 " **开始 > 设置" > Mixed reality** ，然后选择 " **卸载** "。 请确保在卸载之前断开耳机与电脑的连接并关闭混合现实门户。

如果已准备好开始使用头戴显示，请将其插入，混合现实门户将引导你完成安装过程。

> [!NOTE]
> 如果看到一条消息，指出 "我们无法完成 Windows Mixed Reality 的删除操作"，这意味着某些文件（包括有关环境的信息）可能仍在计算机上。 如果以后决定重新安装 Windows Mixed Reality，这可能会导致问题。
> 
> 若要了解如何从你的电脑中手动删除任何剩余的 Windows Mixed Reality 信息，请参阅 **[此文](troubleshooting-windows-mixed-reality.md#how-to-uninstall-windows-mixed-reality)** 。 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>使用 Windows Mixed Reality 时，Wi-fi 会变慢

如果使用的是 2.4 GHz Wi-fi 连接，则运动控制器可能会减慢 Wi-fi 的速度。 尝试以下任一项：

<!-- TODO: Use Windows Mixed Reality PC hardware guidelines interlink -->
* 切换到 5GHz Wi-fi 连接（如果有）。 [了解详细信息](https://support.microsoft.com/help/4000461)
* 使用单独的蓝牙适配器将运动控制器连接到您的 PC。 [查看建议的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

## <a name="what-is-the-experience-options-setting"></a>什么是体验选项设置？

体验选项将 ( **设置 > 混合现实 > 耳机显示 > 体验选项** ) 使你能够更改 Windows Mixed reality 性能设置。 这使你能够在一系列内容中为你的硬件配置选择可能的最佳体验。 90Hz 体验适用于所有系统，但你可能希望首先尝试自动执行，以查看你首选的设置。

选项如下：

* 自动或让 Windows 决定： Windows Mixed Reality 将确定硬件配置的最佳体验。 对于大多数人来说，这是开始的最佳选择。
* 60Hz：将刷新率设置为60Hz，并关闭某些功能，如混合现实门户中的视频捕获和预览。
* 90Hz：如果头戴显示设备可以运行，则将刷新频率设置为90Hz。 如果电缆问题导致耳机无法在90Hz 运行，则在选择此模式时，可能会看到 "启动时出错"。 

## <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>我看到一条消息，显示 "戴上耳机"，即使我的耳机已打开

在戴戴戴显示设备时，Windows Mixed Reality 需要一些时间来重新加载空间。 这可能需要几秒钟时间。 如果此消息不会消失，请确保已从邻近感应传感器（位于耳机内的重用功能区）中删除了保护标签。 如果已删除不干胶标签，但仍有问题，请与耳机制造商联系。 在键盘上按 **Win + Y** 将在邻近感应传感器未自动触发的情况下手动触发耳机运行。 

仍需帮助？ 若要进行高级故障排除，请参阅 [此文](troubleshooting-windows-mixed-reality.md)。

## <a name="see-also"></a>请参阅
* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)