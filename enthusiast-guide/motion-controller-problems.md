---
title: 运动控制器常见问题
description: 高级 Windows Mixed Reality 故障排除，超出了标准使用者支持文档的范围。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，动作控制器
appliesto:
- Windows 10
ms.openlocfilehash: 2a45f16cfbe62cb1263fcb1a1e7f5c76ea0b9268
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677598"
---
# <a name="motion-controller-faqs"></a>运动控制器常见问题

## <a name="general-questions"></a>常规问题

### <a name="what-do-the-vibrations-and-lights-mean"></a>Vibrations 和灯光是什么意思？

LED 星座环形和 haptics 指示运动控制器的状态。

| 状态    | 与状态关联的行为 | 如何进入/退出状态 | 
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **开机**               | Led 打开，控制器 vibrates 一次。 | 按住控制器上的 Windows 按钮两秒钟，以打开控制器。  | 
| **关机**              |  Led 关闭，控制器 vibrates 两次。 | 按住控制器上的 Windows 按钮四秒钟以关闭控制器。   |
| **Sleeping**               |  处于睡眠状态时，指示灯关闭并每隔三秒闪烁一次。 | 当控制器 motionless 30 秒时，控制器会自动进入睡眠状态。 控制器检测到运动时唤醒，但设备未与主机 PC 配对的情况除外。 在这种情况下，按按钮将其唤醒。 |
| **组合**                |  Led 在配对模式下缓慢脉冲，并在退出配对模式时转为稳定状态。 如果配对成功，则控制器 vibrates 一次; 如果配对失败，则会出现三次，否则会超时。 | 按下并按住电池盒内部的配对按钮三秒。     |
| **控制器连接/断开与电脑的连接** |  控制器 vibrates 计算机连接或断开连接。 | 如果控制器已成功连接到电脑，或者控制器在使用期间与 PC 断开连接，则会发生这种情况。|
| **低电池电量水平**      | 当电池电量低 (没有 LED 指示) ，将禁用 Haptics。 当电池电量不足时，耳机上控制器手柄上的电池指示器图标将显示1/4。 | 更换电池。 | 
| **严重电池电量水平** |  控制器 vibrates 三次，并在打开时自动关闭。 电池指示器图标将变为红色。 | 更换电池。 如果问题仍然存在，请将 [设备还原为其出厂设置](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

### <a name="my-motion-controllers-arent-working-properly"></a>运动控制器不能正常工作。

如果 [运动控制器](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) 没有工作、未连接或在戴上耳机时看不到控制器的图像，请尝试以下操作：
1. 请确保已打开控制器。 若要将其打开，请按住 Windows 按钮两秒钟。
2. 请确保控制器完全充电，如果不是，则更换电池。
3. 将控制器保持在您的前方，同时关闭控制器并将其打开。 按住 Windows 按钮四秒钟，使控制器关闭，然后再次按住该控制器两秒钟，以将其打开。 
4. 如果控制器已配对到你的电脑，请参阅 " **设置" > 设备 "> 蓝牙 & 其他设备** ; 或者，如果控制器已配对到你的耳机，请参阅 > **运动控制器 > 用户界面设备设备管理器** 。 请确保控制器已按配对方式列出。 如果不是，则将 [它们配对](motion-controller-problems.md#how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc)。 
5. 请确保运动控制器显示为 "已连接"。 "配对" 不一定表示控制器已连接到 PC。 控制器应出现在 "鼠标，键盘 & 笔" 类别下。 "其他设备" 下的运动控制器未通过配对过程，因此不起作用。 检查运动控制器 Led 指示灯：强光亮起的控制器已配对并且已连接，dimly 发亮控制器未连接。
6. 在电脑上，请参阅 **开始 > 混合现实门户** ，并选择 "菜单"。 你应该会看到你的运动控制器以及状态消息：
    * 就绪–控制器都已设置好。
    * 丢失跟踪–混合现实门户找不到控制器。 将其放在耳机前面，并按四秒钟的 "Windows" 按钮重新启动，然后再次两秒钟。
    * 电池电量低–更换控制器电池。
7. 如果使用的是外部 USB 蓝牙适配器，请确保已将其插入到 USB 2.0 端口中， (通常情况下并不总是黑色) 。 还应尽可能从任何其他无线发送器或 USB 闪存驱动器（包括耳机的 USB 连接器）接通电源。 
8. 若要验证 PC 中是否只有一个蓝牙广播，请跳到 **设备管理器 > 蓝牙** ，然后查找一个适配器。 如果你使用的是带内置收音机的台式计算机配置，请检查是否已连接外部天线。 如果未连接外部天线，则可能会导致跟踪问题。 或使用外部蓝牙转换器 (USB) ，禁用内部蓝牙功能，然后重试配对和连接。
9. 如果在后台打开了 "蓝牙设置" 窗口，则会对蓝牙协议进行许多额外调用。 关闭它。
10. 通过在混合现实中打开控制器以查看电池图标来检查运动控制器上的虚拟电池级别。 在读取级别之前，请等待大约15秒，因为在连接控制器后，报告级别比实际级别更高。 如果图标为红色，则更换电池。 
11. **> 设备 > 蓝牙 & 其他设备** 中删除蓝牙耳机和扬声器，并关闭设备。 在混合现实耳机上使用耳机插孔或内置扬声器获得最佳音频体验。
12. 删除可能与电脑配对的其他蓝牙设备，如耳机或 gamepads。 中转到 " **设置" > 设备 "> 蓝牙 & 其他设备** "，选择设备，然后选择 "删除设备"。
13. 拔出耳机上的 USB 电缆，并将其插回计算机以重新启动 Windows Mixed Reality。
14. 当控制器正在进行固件更新时，它会闪烁。 等待更新完成，控制器应在混合现实中出现。
15. 确保你的电脑已连接到 5GHz Wi-fi 网络。 如果便携式计算机连接到 2.4 GHz Wifi 网络，则通常会共享蓝牙连接。 这可能会对 Wifi 或蓝牙性能产生负面影响，具体取决于产品设计。 在网络适配器设置中将首选带区更改为5GHz。 如果网络不支持5GHz，则可以使用蓝牙转换器，而不是使用内部蓝牙功能。
16. 如果你的蓝牙设置已经配对了运动控制器，则在删除这些设备之前，Windows 将不会发现这些新设备 (如果已使用特定的转换器添加这些设备，则只能使用该转换器) 来删除它们。
17. 如果你的电脑具有内置的蓝牙，并且你遇到连接问题，请尝试使用 USB 蓝牙适配器。 为此，请在设备管理器关闭内置蓝牙无线电，然后将其他蓝牙设备与新的适配器配对。

### <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>控制器在混合现实中抖动、停滞或闪烁，并消失。 

* 如果你的电脑运行在 2.4 GHz wifi 上，请切换至 5 GHz wifi。 
* 如果你使用的是外部蓝牙适配器，请确保将其插入 USB 2.0 端口， (通常（但不总是）黑色) ，远离其他无线发送器或 USB 闪存驱动器。 
* 在 "设置" 中运行蓝牙疑难解答 **> 更新 & 安全 > > 蓝牙的故障排除** 。 

### <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>控制器停滞在无限重启。

这是一个关键电池指示器。 将新电池放入设备，如果问题仍然存在，请将 [控制器重置为出厂设置](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)。

### <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>混合现实门户正在运行，但我的控制器 (飞出、摇动等 ) 正在跟踪。

1. 照明条件会影响跟踪。 请确保未向直射直射，并确保您的 HMD (看不到很多的点光源，例如，如圣诞节树) 的灯光字符串。 
2. 这些症状通常是由于控制器与主机之间的通信失败引起的，并指示蓝牙链接质量较差。 请参阅 [有关蓝牙的问题](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>运动控制器 Led 未亮起，但按钮和操纵杆仍适用于混合现实门户。

运动控制器校准缓存可能已损坏。 若要删除缓存，请在管理员命令提示符下运行以下命令：

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

此文件夹在 Windows 资源管理器中不可访问，只能从管理员命令提示符中修改。 删除文件夹后，请重新启动计算机，然后重新连接运动控制器以还原校准文件。

### <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>我的控制器看起来像是 Naopak/Oculus，具有奇怪的方向，或者这些按钮未正确映射。

该网站可能没有完全的动作控制器支持。

### <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>运动控制器没有出现在 SteamVR 的应用和游戏中。

首先，请确保您的控制器电池已收费。 如果电池失效或中断，控制器将无法工作。 

如果你可以在 Cliff 房子中看到你的控制器，而不是 SteamVR 应用和游戏中的控制器，则运动控制器型号驱动程序可能安装不正确。 检查运动控制器型号驱动程序是否正确安装：
1. 打开这两个运动控制器。 如果控制器已配对到你的电脑，请参阅 " **设置" > 设备 "> 蓝牙 & 其他设备** ; 或者，如果控制器已配对到你的耳机，请参阅 > **运动控制器 > 用户界面设备设备管理器** 。 确保它们显示为 "已连接"。 如果它们没有显示，或者显示为 "配对"，请将 [它们配对](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality)。
2. 中转到 **设备管理器 > 蓝牙** ，并查找 "运动控制器"。
3. 选择该设备，然后 **按连接查看 > 设备** "。
4. 中转到 " **系统设置" > 设备 "> 蓝牙 & 其他设备 > 其他** 设备，以查看它们是否可见。 其中有两个 "蓝牙 HID 设备" 设备，在每个蓝牙 HID 设备下，都应该是名为 "运动控制器" 的设备， (与运动控制器) 在同一节点中的灰色图标。
5. 双击每个 "运动控制器" 设备，然后单击 "驱动程序" 选项卡。确认列出的驱动程序版本对应于 [这些版本](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history)之一。
6. 否则，请运行 Windows 更新，这将自动下载并安装驱动程序。 如果你在具有企业策略的 PC 上，或者如果 Windows 更新受到限制，则可能需要手动安装运动控制器模型驱动程序。 为此，请访问 [此页](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) ，并查找与你的 Windows 10 版本对应的驱动程序版本。 下载页上提供了安装说明。

### <a name="the-controller-firmware-update-takes-significantly-longer-than-two-minutes"></a>控制器固件更新花费的时间明显超过两分钟。

查看 " [蓝牙问题" 部分](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。 蓝牙链接质量差通常会导致这些问题。

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>我刚插入了新电池，但控制器虚拟电池电量不表示完全水平。

为 AA 电池调整了运动控制器电池电量水平。 某些低电压充电电池可能不会报告为完全充电，不过它们完全充电。

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>我的 Samsung 运动控制器的触摸板处于离线状态或具有死点。

这可能是硬件缺陷，应返回给零售商或设备制造商提供更换或交换。

### <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>如何将控制器还原为出厂设置？

将其还原为出厂条件 (需要全新电池) ：
1. 拔出并关闭控制器电源。
2. 打开电池盖子。
3. 插入新电池。
4. 按住 "配对" 按钮 (电池) 下底部的选项卡。
5. 按住 "配对" 按钮时，通过按住 Windows 按钮5秒钟来打开控制器， (使这两个按钮按下) 。
6. 释放按钮并等待控制器开启。 这最多需要15秒的时间，并且在发生设备恢复时不会出现任何迹象。 如果设备在立即开机，则表明 "恢复" 按钮序列未注册，需要重试。
7. 如果控制器已配对到电脑，请参阅 " **设置" > "蓝牙 > 其他设备** "，选择 "运动控制器"，然后选择 "删除设备" 从蓝牙设置中删除控制器关联。 
8. 将控制器与耳机或电脑再次[配对](set-up-windows-mixed-reality.md#if-you-need-to-pair-your-motion-controllers-with-your-pc)。
9. 连接主机和耳机后，设备将更新到最新的可用固件。

### <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>我是否可以将我的 Xbox 控制器与我的电脑配对，以便在耳机中使用它？

可以按照 [这些说明](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)，将蓝牙 Xbox 控制器与耳机一起使用。 

如果有有线 Xbox 控制器，请将其插入 PC。

有些游戏和应用程序使用 Xbox 控制器的方式与在混合现实中使用的不同。 若要将控制器用于游戏或应用，请在应用栏上选择 "用作游戏板"，或说 "用作游戏板"。 若要将控制器切换回 mixed reality，请再次选择 "将其用作游戏板"，或说 "与注视一起使用"。 



## <a name="if-your-motion-controllers-are-paired-to-your-headset"></a>如果运动控制器与耳机配对：

### <a name="should-i-pair-my-controllers-to-a-windows-mixed-reality-headset-that-has-built-in-bluetooth-radio"></a>我是否应将控制器与具有内置蓝牙收音机的 Windows Mixed Reality 耳机配对？

某些 Windows Mixed Reality 耳机，包括 Acer OJO 500 和 Samsung 太空 +，内置蓝牙无线电收发器用于运动控制器。 这些耳机附带的运动控制器与工厂中的耳机预配对，无需您的 PC 具有单独的蓝牙收音机。 例如， _可以_ 将这些运动控制器手动配对到您的 PC 的蓝牙无线电设备，以与没有内置蓝牙无线电收发器的 Windows Mixed Reality 耳机配合使用。 

### <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>如果 Windows Mixed Reality 已在电脑上设置，则如何实现配对新控制器？
如果要将控制器与耳机配对，请使用配套应用 ([混合现实门户](install-windows-mixed-reality.md#launch-mixed-reality-portal) 可以帮助你找到要启动的伴随应用，或提供可从) 中选择的伴生应用列表。

### <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>配对的控制器不会显示在混合现实门户中。 

* 按住耳机前面的控制器，并按四秒钟的 "Windows" 按钮重新启动它们，然后再次两秒钟。 
* 如果在 **> 人体学接口设备设备管理器** 中看到 "运动控制器"，请再次执行配对过程。 
* 如果控制器 Led 正在循环，则一次打开一个光源的象限，然后将其关闭，它们将进行固件更新。 等待更新完成，控制器应在混合现实中出现。 
* 如果使用的是外部蓝牙适配器，请确保将适配器插入 USB 2.0 端口， (通常（但不总是）黑色) ，远离其他无线发送器或 USB 3.0 设备。 
* 如果电脑刚刚崩溃并使用了 Qualcomm 适配器，则重置可能不起作用。 若要解决此问题，请从计算机背面拔下电源 (或如果在笔记本电脑上按下电源按钮10秒钟) 并重新启动计算机。 
* 在 "设置" 中运行蓝牙疑难解答 **> 更新 & 安全 > > 蓝牙的故障排除** 。  

### <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>如何将控制器返还给工厂配对？

若要将运动控制器返回到工厂配对，或将其与带有内置蓝牙收音机的 Windows Mixed Reality 耳机配对，请运行耳机的设备附带应用 (例如，"Acer OJO 500" 应用或 "Samsung HMD 太空 + 安装" 应用程序，在首次将耳机插入) 时自动安装，并按照运动控制器配对的说明进行操作。



## <a name="if-your-motion-controllers-are-paired-to-your-pc"></a>**如果运动控制器已配对到你的电脑：**

### <a name="my-motion-controllers-are-not-pairing"></a>运动控制器不配对。 

* 如果控制器未打开，请插入新电池。 如果这不能解决此问题，请在按住配对按钮的同时打开设备，将设备还原为其出厂设置。 有关更多详细信息，请参阅 [设备恢复步骤](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) 。 
* 如果控制器已打开，并且你使用的是外部蓝牙适配器，请确保将适配器插入 USB 2.0 端口， (通常（但不总是）黑色) ，远离其他无线发送器或 USB 闪存驱动器。 如果仍不起作用，请在 "设置" 中运行蓝牙疑难解答 > 更新 & 安全 > > 蓝牙的故障排除。 
* 如果使用的是 Qualcomm 适配器，而电脑刚刚崩溃，请重新启动计算机。 
* 尝试重新启动不配对的运动控制器，一次重启一次，然后重启电脑。 
* 运动控制器缓存可能已损坏。 若要解决此问题，请参阅以下 [步骤](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)。 
* 如果这些步骤未解决问题，则应与制造商联系。 

### <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>配对的控制器不会显示在混合现实门户中。 

* 按住耳机前面的控制器，并按四秒钟的 "Windows" 按钮重新启动它们，然后再次两秒钟。 
* 如果控制器在 "设置" 中显示为 "已连接" **> Bluetooth & 其他设备** ，取消配对它们并再次执行配对过程。 
* 如果控制器 Led 正在循环，则一次打开一个光源的象限，然后将其关闭，它们将进行固件更新。 等待更新完成，控制器应在混合现实中出现。 
* 如果使用外部蓝牙适配器，请确保将适配器插入 USB 2.0 端口， (通常是黑色) ，远离其他无线发送器或 USB 3.0 设备。 
* 如果电脑刚刚崩溃并使用了 Qualcomm 适配器，则重置可能不起作用。 若要解决此问题，请从计算机背面拔下电源 (或如果在笔记本电脑上按下电源按钮10秒钟) 并重新启动计算机。 
* 在 "设置" 中运行蓝牙疑难解答 **> 更新 & 安全 > > 蓝牙的故障排除** 。  

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>我尝试配对控制器，但它们永远不会显示在蓝牙设置的 "添加新的设备菜单" 中。

检查是否已将控制器配对。 如果执行此操作，请将其删除，然后重试。 如果问题仍然存在，请重启电脑。 如果失败，请参阅 [有关蓝牙](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)的详细信息。

### <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>如果 Windows Mixed Reality 已在电脑上设置，则如何实现配对新控制器？

1. 将两个 AA 电池插入每个控制器。 不要将电池盖装回。
2. 按住 Windows 按钮两秒钟，打开每个控制器。 他们打开时，他们会有任何嗡嗡。
3. 将控制器置于配对模式。 "配对" 按钮位于 "电池" 隔离舱 (查看此 [图像](set-up-windows-mixed-reality.md#if-you-need-to-pair-your-motion-controllers-with-your-pc)) 。 按住此键，直到控制器指示灯开始闪烁。
4. 中转到 " **设置" > 设备 "> 蓝牙 & 其他设备** "，然后 **将蓝牙或其他设备添加 > 蓝牙** 。 出现控制器时，选择它们以配对。

注意：如果另一组运动控制器与你的电脑配对，你将需要取消配对这些控制器，然后再将它们配对。 如果将一组运动控制器与当前 PC 配对，然后将其与另一台电脑配对，则需要在使用当前 PC 之前取消配对并重新配对它们。

### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>如何判断我是否在使用蓝牙技术？

运动控制器使用在许多消费者设备中找到的相同蓝牙技术，其设计目的是使用任何最近的 PC 中包含的蓝牙功能。 如果你的电脑通过了混合现实兼容性检查，则它应具有蓝牙收音机。 要验证： 
* 打开 "设备管理器"。 
* 展开 "蓝牙" 部分，并查找适配器。 

![示例设备管理器的屏幕截图。 适配器是蓝牙收音机。](images/devicemanagerbtadapterpic.png) 

如果你的电脑没有蓝牙，则建议使用一个 [PLUGABLE USB 蓝牙4.0 低能量微适配器](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom)。

### <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>当动作控制器打开时，wi-fi 会减缓我的笔记本。

当连接到 2.4 GHz 接入点时，笔记本可能与蓝牙共享其 Wi-fi 天线。 如果可以将带区首选项切换到5GHz，请签入设备管理器。 如果5GHz 网络不可用并且性能受到严重影响，请考虑使用蓝牙转换器。

![可以通过设备管理器找到 Wifi 波段选择设置](images/wifi5ghz.png)

### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>我的 PC 具有蓝牙技术，但我的控制器有问题。

动作控制器应与其他蓝牙键盘、鼠标和游戏控制器一起工作，但体验会因使用的键盘、鼠标或游戏控制器的型号而异。 可以执行以下操作来提高性能：
* 如果你的计算机具有蓝牙功能，但运动控制器仍有问题，请考虑将蓝牙无线电替换为插入到 USB 的 Plugable 外部蓝牙适配器。 一次只能有一个蓝牙无线电适配器处于活动状态。 如果除了插入现有收音机外，还插入外部广播，则需要在设备管理器中禁用现有蓝牙无线电 (右键单击该适配器，然后选择 "禁用设备" ) 和取消对以前的所有蓝牙设备的配对。
* 如果使用的是 USB 蓝牙适配器，请将其连接到 USB 2.0 端口 (2.0 端口通常为黑色，未标记为 "SS" ) （如果可用）。 端口应以物理方式与以下内容分开：
    - HMD USB 连接器
    - 闪存驱动器
    - 硬盘驱动器
    - 无线 USB 接收器（如键盘/鼠标键盘的理想接收方）理想情况下，从这些其他连接器将 USB 蓝牙适配器插入到计算机的另一侧。
* 关闭蓝牙设置窗口（如果已打开）。 使其在后台处于打开状态，这意味着需要对蓝牙协议进行大量的额外调用。
* 如果你的耳机已配对到你的电脑，请使用 Windows 蓝牙驱动程序堆栈，并且不要安装任何第三方蓝牙驱动程序堆栈。 第三方软件可能无法正常工作。
* 禁用 "蓝牙 & 其他设备" 下的 "使用 Swift 对进行连接" 设置中的 "显示通知"。
* 如果使用的是内部蓝牙卡，请确保使用的是外部蓝牙天线，否则可能会遇到跟踪问题。 如果此操作不起作用，请在禁用内部蓝牙后 (USB) 使用外部蓝牙转换器。
* 设备应显示在蓝牙设置中的 "鼠标、键盘 & 笔" 类别下。 如果它在 "其他设备" 下，则取消配对并配对设备。
* 拔下、取消配对和关闭蓝牙耳机和扬声器电源。 Windows Mixed Reality 不支持这些。 在混合现实耳机上使用耳机插孔或内置扬声器获得最佳音频体验。

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>第二个控制器需要很长时间才能重新连接。

如果同时打开了运动控制器，某些较早的 Intel 无线电系统会出现此问题。 避免同时打开控制器。

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>在电脑崩溃后，Qualcomm 蓝牙无线电无法配对控制器。

Qualcomm (QCA) 在 Windows 崩溃后，10.0.0.448 之前的蓝牙无线电驱动程序可能会以错误状态结束。 完全关闭 PC 以解决此问题。 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>我通过 Marvell 收音机遇到控制器跟踪问题。

请参阅 **设备管理器 > 蓝牙 > MARVELL AVASTAR 蓝牙无线电适配器 > 属性 > 驱动程序** ，并确保使用的是 driver 15.68.9210.47 或更高版本。
