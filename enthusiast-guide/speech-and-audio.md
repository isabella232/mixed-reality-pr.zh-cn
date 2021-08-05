---
title: 语音和音频常见问题解答
description: 语音和音频Windows Mixed Reality我们的标准使用者支持文档之外的故障排除。
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 故障排除， 错误， 帮助， 支持， 音频问题， 语音问题
ms.openlocfilehash: d1d30cebb40d54d579e978013b9abc60981fa943d43b95a96f358092631b4d27
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208977"
---
# <a name="speech-and-audio-faqs"></a>语音和音频常见问题解答

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>我的头戴显示设备中无法听到任何声音，或者声音通过计算机而不是头戴显示设备播放

* 如果沉浸式头戴显示设备不包含内置耳机，请将耳机连接到头戴显示设备上的音频耳机。 该千克通常位于头戴显示设备视口或镜头后面或下面。 如果找不到，请咨询头戴显示设备制造商。
* 某些音频头戴显示设备具有用于控制音量的物理按钮。 如果音频不工作，请检查音量是关闭还是静音。
* 音频将切换到默认Windows设备： 
    * 如果关闭头戴显示设备
    * 向上翻转视器
    * 关闭 混合现实门户 应用
    * 当应用有 15 分钟未使用时。 
    * 可以在混合现实设置 >音频>**语音中更改此设置。**
* 确保音频头戴显示设备已插入音频端口。 特别是 Acer 头戴显示设备可能需要更加小心，以确保音频头戴显示设备已接通电源。
* 检查音频头戴显示设备/麦克风是否已插入头戴显示设备，而不是电脑。
* 系统 **控制面板中设置 >** 声音>只显示已启用的音频终结点，而不是已禁用的终结点。 如果你未戴头戴显示设备，将禁用头戴显示设备。 若要查看它，请右键单击"声音控制面板并选择"显示禁用的设备"。 设备名称为"Realtek USB2.0 Audio"，可在"属性"页中重命名。 可以同时对播放和录制选项卡执行此操作。
* 如果音频在混合现实应用中不工作，例如，使用 Netflix 应用。 这可能是由已知问题导致的，即Windows Mixed Reality更新为匹配 OS 版本。 若要解决此问题并获得最佳混合现实体验，请转到 设置 > 更新 & Security > Windows update >**检查更新**。

> [!NOTE]
> * Windows Mixed Reality空间音频最适合内置于沉浸式头戴显示设备或直接连接到沉浸式头戴显示设备中的耳机。 连接到电脑的电脑扬声器或耳机可能无法很好地用于空间音频。
> * Windows Mixed Reality不支持蓝牙头戴显示设备。

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>我遇到了突然的音量更改、音频丢失或响动

* 某些应用（例如通过 SteamVR 启动的应用）在启动或停止音频设备时，可能会丢失音频或挂起混合现实门户。 若要更正此错误，请重新打开混合现实门户并重启应用。
* 如果另一个多媒体 USB 设备 (例如 Web cam) 与 Windows Mixed Reality 头戴显示设备共享同一个内部或外部 USB 集线器，则头戴显示设备音频插口或耳机偶尔可能会发出响声或完全没有音频。 将头戴显示设备插入使用不同集线器的 USB 端口，或断开/禁用其他 USB 多媒体设备。
* 如果注意到连接的耳机发出一次巨大的噪音突发，则电脑的 USB 集线器可能无法为头戴显示设备提供Windows Mixed Reality电源。 如果发生这种情况，请 [提交反馈中心](/hololens/hololens-feedback) bug 并尝试：
    * 移除扩展电缆
    * 使用专用的外部电源 USB 3.0 集线器
    * 电脑上不同的 USB 端口

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>我的蓝牙音频头戴显示设备未如预期工作

Microsoft 不建议将音频头戴显示蓝牙与 Windows Mixed Reality。 蓝牙音频外围设备无法很好地处理Windows Mixed Reality和空间音效体验。 蓝牙音频头戴显示设备不能同时支持麦克风输入和立体声输出，因此在用于游戏聊天或其他语音输入时，不会听到立体声或空间化声音。 蓝牙头戴显示设备也会对运动控制器体验产生负面影响。

## <a name="sound-isnt-coming-from-expected-directions"></a>声音不是来自预期方向

"Windows Mixed Reality主页"包括 (音频的空间音效，这些音频听起来似乎来自位于"主页") 。 当你旋转并靠近每个应用时，声音方向和级别会发生变化，以提高真实感。 下面是意外声音指示的一些潜在原因：

* 如果从支持背景音乐应用打开并播放音乐 (例如 Groove 音乐) ，然后打开沉浸式 VR 体验（如游戏）时，音乐应用的声音会从空间声音交叉到立体声。 它看起来可能更响，因为你和声音之间不再有任何距离。
* 如果在使用 Cortana头戴显示设备之前在电脑上启用了Windows Mixed Reality，则可能会丢失应用于 Windows Mixed Reality 应用的空间声音。 若要解决此问题，在启动 Windows Mixed Reality 之前，在桌面上Cortana **设置 > Cortana"** 让 Cortana 响应 Hey Cortana"，或启用"用于耳机的 Windows Sonic"：
    1. 转到"主页"中的"桌面Windows Mixed Reality窗口。
    2. 在桌面任务栏上左键单击扬声器图标，然后从音频设备列表中选择它。
    3. 右键单击桌面任务栏上的说话人图标，然后选择"说话人设置用于耳机的 Windows Sonic"菜单中的"扬声器"。
    4. 针对所有音频设备重复这些步骤 (终结点) 。

## <a name="speech-commands-are-not-working-as-expected"></a>语音命令未如预期工作

* 若要使用语音命令，必须将电脑上的语音和语言设置设置为[Windows Mixed Reality。](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages) 若要检查Windows和语言设置，请选择"设置 > 时间&语言 **> 区域&语言**"和"设置 > 时间&**语言>语音**"。
* 如果头戴显示设备没有内置麦克风，则需要将麦克风的耳机连接到头戴显示设备或电脑。 若要在头戴显示设备时将麦克风输入开关自动切换到头戴显示设备，请转到设置 >混合现实 **> 音频和语音"，** 然后打开"当我戴头戴显示设备时，切换到头戴显示设备麦克风"。
* 某些音频头戴显示设备具有用于静音和取消麦克风静音的物理按钮。 如果语音命令不工作，请检查麦克风是否静音。
* 在具有环境干扰的环境中，具有从耳机电缆中传输的麦克风的音频头戴显示设备不能很好地执行语音命令。
* Cortana第一次在活动会话中调用她时，混合现实门户速度。 转到 **设置 > Cortana >"与** Cortana"，确保已启用"Cortana"你好Cortana"。
* 在某些 PC 上，已连接头戴显示设备麦克风的默认语音捕获增益可能设置得过低。 如果遇到不可靠的语音命令或听写，请运行麦克风设置疑难解答：
    1. 在头戴显示设备Windows Mixed Reality头戴显示设备时，转到 (桌面应用，以影响用于Windows Mixed Reality) 。
    2. 转到 **"设置 >语言&语音>时间"。**
    3. 在"麦克风入门选择"麦克风"。
    4. 在疑难解答向导中选择适当的终结点。

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>我只有一个音频头戴显示设备，我想同时用于桌面和头戴显示设备

如果只有一个音频头戴显示设备，并且没有带内置耳机的头戴显示设备，请将音频头戴显示设备连接到电脑而不是头戴显示设备。 然后关闭设备设置中的"切换到头戴显示设备混合现实门户音频"。

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>我想要切换到Dolby Atmos for Headphones

Windows Mixed Reality环境及其应用使用用于耳机的 Windows Sonic音频技术，该技术针对混合现实体验进行自定义。 其他空间音频技术（如 Dolby Atmos for Headphones）可应用于全屏幕应用（如 SteamVR 游戏）但不适用于 Windows Mixed Reality shell 环境和应用 (例如，将 Web 浏览器放置在 悬崖小屋 的墙上，或使用 用于耳机的 Windows Sonic 空间音效和音效设计的 Sky Placing) 。