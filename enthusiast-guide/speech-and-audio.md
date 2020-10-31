---
title: 语音和音频常见问题解答
description: 语音和音频 Windows Mixed Reality 故障排除，超出了标准使用者支持文档的范围。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，音频问题，语音问题
ms.openlocfilehash: 811c58196073a2a55af58978a4248033a1c4aef2
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131841"
---
# <a name="speech-and-audio-faqs"></a>语音和音频常见问题解答

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>我在我的耳机中听不到任何声音，或通过我的计算机而不是我的耳机播放声音

* 如果沉浸式耳机不包含内置耳机，请将耳机连接到耳机上的音频插孔。 插孔通常位于耳机面板或重用功能区的后面。 如果找不到，请与你的耳机制造商联系。
* 某些音频耳机有物理按钮来控制音量。 如果音频不起作用，请检查卷是否已关闭或静音。
* 如果你关闭了头戴显示器，请将面板向上翻转，关闭混合现实门户应用，或者在15分钟内未使用该应用，则音频将切换到默认的 Windows 播放设备。 你可以在 "设置" 中更改此设置 **> 混合现实 > 音频和语音。**
* 请确保已将音频耳机完全插入音频插孔。 特别要注意的是，Acer 耳机可能需要更多的警惕，以确保已接通音频耳机。
* 检查音频耳机/麦克风是否已插入耳机，而不是计算机。
* 设置中的 "声音控制面板" **> 系统 > 声音** 仅显示已启用的音频终结点，而不是已禁用的终结点。 当你不戴上耳机时，耳机音频设备将被禁用。 若要查看它，请在声音控制面板中右键单击，然后选择 "显示已禁用的设备"。 设备名称为 "Realtek USB 2.0 音频" (可以在) 的 "属性" 页中将其重命名。 可以为播放和录制选项卡执行此操作。
* 如果音频在混合现实应用中不工作 (例如，Netflix) ，则这可能是由于已知问题导致的，该问题不会自动更新 Windows Mixed Reality 来匹配操作系统版本。 若要解决此问题并获得最佳混合现实体验，请转到 " **设置" > 更新 & 安全 > Windows 更新 > 检查是否有更新** 。

> [!NOTE]
> * Windows Mixed Reality 空间音频最适合用于直接内置或直接连接到沉浸式耳机的耳机。 连接到 PC 的 PC 扬声器或耳机可能不适用于空间音频。
> * Windows Mixed Reality 不支持蓝牙音频耳机。

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>出现突然的卷更改、音频丢失或蜂鸣声

* 某些应用程序（包括许多通过 SteamVR 启动的应用程序）可能会在音频设备随着你开始或停止混合现实门户而发生变化时丢失音频或挂起。 若要更正此错误，请重新打开混合现实门户并重新启动应用。
* 如果另一台多媒体 USB 设备 (如 web cam) 与 Windows Mixed Reality 耳机共享同一内部或外部 USB 集线器，则耳机音频插孔或耳机可能偶尔会有蜂鸣音或根本没有音频。 将耳机插入使用不同集线器的 USB 端口，或断开连接/禁用其他 USB 多媒体设备。
* 如果你注意到耳机上连接了耳机的噪音太大，则可能是电脑的 USB 集线器无法为 Windows Mixed Reality 耳机提供足够的电源。 如果出现这种情况，请提交 [反馈中心](https://docs.microsoft.com/hololens/hololens-feedback) 错误，然后重试：
    * 删除扩展电缆
    * 使用专用的外部电源 USB 3.0 集线器
    * 计算机上的其他 USB 端口

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>我的蓝牙音频耳机未按预期工作

Microsoft 不建议将蓝牙音频耳机用于 Windows Mixed Reality。 蓝牙音频外设不适用于 Windows Mixed Reality 声音和空间音效，蓝牙音频耳机无法同时支持麦克风输入和立体声输出，因此，在使用 gamechat 或其他语音输入时，您不会听到立体声或 spatialized 声音。 蓝牙音频耳机还会对运动控制器体验产生负面影响。

## <a name="sound-isnt-coming-from-expected-directions"></a>声音并非来自预期方向

Windows Mixed Reality 主页包含的空间音效 (音频，与家庭) 中的应用程序类似。 当您从每个应用程序中翻到更近或更远的距离时，声音方向和级别会改变以使真实感更进一步。 下面是意外声音方向的一些可能原因：

* 如果从支持后台的音乐应用打开并播放音乐 (如家里) 的 Groove 音乐，然后打开沉浸式的 VR 体验（如游戏），则来自音乐应用的声音将从空间音效 crossfade 到立体声。 它可能会变得更大，因为您与声音之间没有任何距离。
* 如果在使用 Windows Mixed Reality 耳机之前已在电脑上启用 Cortana，则可能会丢失适用于 Windows Mixed Reality 主页中的应用的空间声音。 若要解决此问题，请在启动 Windows Mixed Reality 之前，在桌面上的 " **设置" > cortana** "中关闭" 让 Cortana 响应你好 cortana "，或启用" windows Sonic for 耳机 "：
    1. 在 Windows Mixed Reality 主页中转到 "桌面应用" 窗口。
    2. 在桌面任务栏上左键单击扬声器图标，并从音频设备列表中选择它。
    3. 右键单击桌面任务栏上的扬声器图标，然后在 "扬声器设置" 菜单中选择 "Windows Sonic 用于耳机"。
    4. 为所有音频设备重复以下步骤， (终结点) 。

## <a name="speech-commands-are-not-working-as-expected"></a>语音命令未按预期方式工作

* 若要使用语音命令，你的电脑上的语音和语言设置必须设置为 [Windows Mixed Reality 中支持的语言](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages)。 若要检查您的 Windows 语音和语言设置，请选择 " **设置" > time & language > 区域 & 语言** 和 **设置 > time & language > 语音** 。
* 如果耳机没有内置麦克风，则需要使用麦克风将耳机连接到耳机或电脑。 要使麦克风输入在您磨损时自动切换到你的耳机，请转到 " **设置" > 混合现实 > 音频和语音** ，并打开 "当我戴上耳机时，切换到耳机麦克风"。
* 某些音频耳机有一个 "物理" 按钮，可将麦克风静音并取消静音。 如果语音命令不起作用，请检查是否已将麦克风静音。
* 带有麦克风的音频耳机，dangles 从 earbud 电缆连接时，不能很好地在环境干扰的环境中执行语音命令。
* 首次在混合现实门户会话中调用 Cortana 时，Cortana 可能会很慢。 请参阅 " **设置" > cortana > 与 Cortana 交谈** ，并确保已启用 "允许 Cortana 响应你好 cortana"。
* 在某些电脑上，手机网络连接麦克风的默认语音捕获增益可能会设置得太低。 如果遇到不可靠的语音命令或听写，请运行麦克风安装疑难解答：
    1. 在戴上耳机 (的同时，在 Windows Mixed Reality 主页中转到桌面应用，以影响用于 Windows Mixed Reality) 的麦克风。
    2. 转到 " **设置" > Time & Language > Speech** "。
    3. 在 "麦克风" 部分选择 "入门"。
    4. 选择疑难解答向导中的相应终结点。

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>我只有一个音频耳机，并想要将其用于桌面和耳机

如果只有一个音频耳机，但没有内置耳机的耳机，请将音频耳机连接到电脑而不是耳机。 然后在混合现实门户设置中关闭 "切换到耳机音频"。

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>我想切换到杜比 Atmos 来实现耳机

Windows Mixed Reality 环境及其应用使用 Windows Sonic 实现耳机空间音频技术，该技术是针对混合现实体验自定义的。 其他空间音频技术（如耳机的杜比 Atmos）可应用于全屏应用（如 SteamVR 游戏，但不适用于 Windows Mixed Reality shell 环境和应用） (例如，将 web 浏览器放置在 Cliff 房子或天空 Loft) 上，并已使用 Windows Sonic 实现耳机空间音效和噪音。
