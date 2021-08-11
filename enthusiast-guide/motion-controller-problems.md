---
title: 运动控制器常见问题解答
description: 控制器Windows Mixed Reality标准使用者支持文档之外的故障排除。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 故障排除， 错误， 帮助， 支持， 运动控制器
appliesto:
- Windows 10
ms.openlocfilehash: e477ed07e20fb06e270c9a6e13e20defecfc6328896983ed12c4b79ea2197e44
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219735"
---
# <a name="motion-controller-faqs"></a>运动控制器常见问题解答

## <a name="what-do-the-vibrations-and-lights-mean"></a>振动和光的含义是什么

LED 钟环和触点指示运动控制器的状态。

| 州省/自治区/直辖市    | 与状态关联的行为 | 如何进入/退出状态 |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **开机**               | LED 打开，控制器振动一次。 | 按住控制器上的Windows按钮两秒钟以打开控制器。  |
| **关机**              |  LED 关闭，控制器振动两次。 | 按住控制器上的Windows按钮四秒钟以关闭控制器。   |
| **睡觉**               |  LED 在睡眠状态期间关闭并每隔三秒闪烁一次。 | 控制器在 30 秒无运动时自动进入睡眠状态。 控制器在检测到运动时唤醒，除非设备未与主机电脑配对。 在这种情况下，按 按钮将其唤醒。 |
| **配对**                |  LED 在配对模式下缓慢脉冲，在退出配对模式时稳定。 如果配对成功，控制器会振动一次;如果配对不成功，则控制器会振动三次，然后退出。 | 在电池箱内按住配对按钮三秒钟。     |
| **控制器与电脑连接/断开连接** |  控制器在电脑连接或断开连接时振动一次。 | 当控制器在打开电脑后成功连接到电脑，或者控制器在使用期间与电脑断开连接时发生。|
| **低电池电量**      | 当电池不足时，将禁用 (没有 LED 指示) 。 当电池电量不足时，头戴显示设备控制器句柄上的电池指示器图标将显示 1/4 已满。 | 更换电池。 | 
| **严重电池级别** |  控制器在打开后会振动三次，然后自动关闭。 电池指示器图标将变红。 | 更换电池。 如果问题仍然存在， [将设备还原到其工厂设置](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>我的运动控制器无法正常工作

如果 [运动控制器](controllers-in-wmr.md) 在头戴显示设备时无法工作、连接或显示控制器的图像：

1. 确保控制器已打开。 若要打开它们，请按住"Windows按钮两秒钟。
2. 确保控制器已完全充电，如果没有，请更换电池。
3. 将控制器放在你前面时，再次关闭和打开控制器。 按住"Windows按钮四秒钟以关闭控制器。 再次按住它两秒钟以将其打开。
4. 检查运动控制器是否正确 [配对](controllers-in-wmr.md#pair-motion-controllers)。
5. 检查运动控制器 LED：亮光控制器已配对且已连接，而暗光控制器未连接。
6. 转到" **在电脑上> 混合现实门户"，** 然后选择"菜单"。 应会看到列出的运动控制器以及状态消息：
    * 就绪 - 控制器已全部设置。
    * 丢失跟踪 – 混合现实门户找不到控制器。 在头戴显示设备前面按住它们，然后按 Windows按钮将其重启，然后再次按两秒。
    * 电池不足 – 更换控制器电池。
7. 如果使用的是外部 USB 蓝牙 适配器，请确保它已插入 USB 2.0 端口 (它们通常是但并不总是黑色) 。 它还应尽可能从任何其他无线发送器或 USB 闪存驱动器（包括头戴显示设备的 USB 连接器）插入。 
8. 转到 **设备管理器 > 蓝牙** 并查找一个适配器，检查电脑中蓝牙一个无线无线电。 如果使用带内置无线电的台式电脑配置，请检查是否连接了外部天线。 如果未连接外部天线，则可能会导致跟踪问题。 或者使用外部蓝牙 usb () ，禁用内部蓝牙功能，然后重试配对和连接。
9. 如果蓝牙设置"窗口在后台打开，则对协议执行蓝牙调用。 关闭它。
10. 在混合现实中打开控制器以查看电池图标，检查运动控制器上的虚拟电池级别。 在读取级别之前等待大约 15 秒，因为报告级别在连接控制器后立即高于实际级别。 如果图标为红色，请更换电池。
11. 将蓝牙设备和其他设备设置 >扬声器> 蓝牙 &，并关闭设备。 在混合现实头戴显示设备上使用耳机插口或内置扬声器，获得最佳音频体验。
12. 删除蓝牙电脑配对的其他设备，例如耳机或游戏板。 转到 **设置 >设备> 蓝牙 &设备**"，选择设备，然后选择"删除设备"。
13. 拔下头戴显示设备上的 USB 电缆，将其插回电脑以重启Windows Mixed Reality。
14. 控制器进行固件更新时指示灯闪烁。 等待更新完成，控制器应出现在混合现实中。
15. 确保电脑已连接到 5 GHz Wi-Fi网络。 如果笔记本电脑已连接到 2.4 GHz Wi-Fi网络，则它通常共享 蓝牙 连接。 这可能对性能Wi-Fi或蓝牙性能产生负面影响，具体取决于系统设计。 在网络适配器设置中，将首选带区更改为 5 GHz。 如果网络不支持 5 GHz，可以使用 蓝牙，而不是内部 蓝牙功能。
16. 如果蓝牙设置已配对运动控制器，Windows在删除新设备之前不会发现新设备。 如果已使用特定适配器添加它们，则只能使用该适配器删除它们。
17. 如果电脑具有内置蓝牙并且遇到连接问题，请尝试使用 USB 蓝牙适配器。 为此，请关闭 设备管理器 中的内置 蓝牙 单选设备管理器，然后将其他蓝牙设备与新适配器配对。

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>我的控制器抖动、停滞或闪烁，在混合现实中消失

* 如果电脑在 2.4 GHz wifi 上运行，请切换到 5-GHz wifi。 
* 如果使用的是外部 蓝牙 适配器，请确保该适配器已插入 USB 2.0 端口 (该端口通常（但并不总是）黑色) ，远离其他无线发送器或 USB 闪存驱动器。
* 在 蓝牙 设置 > Update **& Security > 中>故障排除> 蓝牙。**

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>我的控制器停滞在无限重启中

这是一个关键电池指示器。 将新电池放在设备中，如果问题仍然存在， [将控制器重置为出厂设置](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)。

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>尽管混合现实门户正常，但我的控制器跟踪 (飞行、飞行等) 

1. 照明条件可能会影响跟踪。 确保不会向直接光照公开，并且具有对 HMD 设备可见的最小点光源 (例如，树状树等光) 。
2. 这些症状是由控制器和主机电脑之间的通信失败引起的，表明链接质量蓝牙不佳。 请参阅[有关 蓝牙](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)的问题。

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>运动控制器 LED 未亮起，但按钮和滚动块仍可在混合现实门户

运动控制器校准缓存可能已损坏。 若要删除缓存，在管理员命令提示符下运行以下命令：

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

此文件夹在资源管理器中Windows，只能从管理员命令提示符进行修改。 删除文件夹后，重启电脑并重新连接运动控制器以还原校准文件。

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>我的控制器看起来像 Vive/Oculus，方向异常，或者按钮映射不正确

该网站可能没有完全运动控制器支持。

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>我的运动控制器未显示在 SteamVR 应用和游戏

首先，请确保控制器的电池已收费。 如果电池失效或中断，控制器将无法工作。

如果你可以在 Cliff 房子中看到你的控制器，而不是 SteamVR 应用和游戏中的控制器，则运动控制器型号驱动程序可能安装不正确。 检查运动控制器型号驱动程序是否正确安装：

1. 打开这两个运动控制器。 检查运动控制器是否 [配对正确](controllers-in-wmr.md#pair-motion-controllers)。
2. 中转到 **Device Manager > 人体学接口设备** ，并查找 "运动控制器"。
3. 双击每个 "运动控制器" 设备，然后单击 "驱动程序" 选项卡。确认列出的驱动程序版本对应于 [这些版本](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history)之一。
4. 如果驱动程序版本不匹配，或者找不到名为 "运动控制器" 的设备，请运行 Windows 更新。  这将自动下载并安装驱动程序。 如果你在具有企业策略的 PC 上，或者如果 Windows 更新受到限制，则可能需要手动安装运动控制器模型驱动程序。 为此，请访问 [此页](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) ，并查找与控制器硬件对应的驱动程序版本。 下载页上提供了安装说明。

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>控制器固件更新所需的时间超过两分钟

查看[蓝牙问题 "部分](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)。 不良蓝牙链接质量通常会导致这些问题。

## <a name="i-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>我插入了新电池，但控制器虚拟电池电量不表示完全级别

为 AA 电池调整了运动控制器电池电量水平。 即使完全充电，某些低电压充电电池也可能不会报告为完整。

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>我的 Samsung 运动控制器的触摸板处于离线状态或具有死点

这可能是硬件缺陷，应返回给零售商或设备制造商提供更换或交换。

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>如何将控制器还原为出厂设置

将其还原为出厂条件 (需要全新电池) ：

1. 拔出并关闭控制器电源。
2. 打开电池盖子。
3. 插入新电池。
4. 按住 "配对" 按钮 (电池) 下底部的选项卡。
5. 按住 "配对" 按钮的同时，通过按住 "Windows" 按钮5秒钟来打开控制器， (使这两个按钮按) 。
6. 释放按钮并等待控制器开启。 这最多需要15秒的时间，并且在发生设备恢复时不会出现任何迹象。 如果设备在立即开机，则 "恢复" 按钮序列未注册，需要重试。
7. 如果控制器已配对到你的电脑，请参阅 **设置 > 蓝牙 > 其他设备**"，选择" 运动控制器 "，然后选择" 删除设备 "从蓝牙设置中删除控制器关联。
8. 将控制器与耳机或电脑再次[配对](controllers-in-wmr.md#pair-motion-controllers)。
9. 连接主机和耳机后，设备将更新到最新的可用固件。

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>我可以将我的 Xbox 控制器与我的电脑配对，以便在耳机中使用它

可以按照以下[说明](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)，将蓝牙 Xbox 控制器配对，以将其与头戴式耳机一起使用。

如果有有线 Xbox 控制器，请将其插入 PC。

有些游戏和应用程序使用 Xbox 控制器的方式与在混合现实中使用的不同。 若要将控制器用于游戏或应用，请在应用栏上选择 "用作游戏板"，或说 "用作游戏板"。 若要将控制器切换回 mixed reality，请再次选择 "将其用作游戏板"，或说 "与注视一起使用"。 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>如果已在电脑上设置 Windows Mixed Reality，则如何实现配对新控制器

如果要将控制器与耳机配对，请使用配套应用 ([混合现实门户](install-windows-mixed-reality.md#launch-mixed-reality-portal) 可以帮助你找到要启动的伴随应用，或提供可从) 中选择的伴生应用列表。

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>如何将控制器返回给工厂配对

若要将运动控制器返回到其工厂配对，或将其与带有内置蓝牙收音机的 Windows Mixed Reality 耳机配对，请运行耳机的设备附属应用，并按照运动控制器配对的说明进行操作。 例如，首次接通耳机时，会自动安装 "Acer OJO 500" 应用或 "Samsung HMD 太空 + 安装" 应用。

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>我的运动控制器不能配对到我的电脑

* 如果控制器未打开，请插入新电池。 如果这不能解决此问题，请在按住配对按钮的同时打开设备，将设备还原为其出厂设置。 有关详细信息，请参阅 [设备恢复步骤](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)。
* 如果在使用外部蓝牙适配器时控制器开启，请确保将适配器插入 USB 2.0 端口 (，这通常是，但并非始终是黑色) ，远离其他无线发送器或 USB 闪存驱动器。 如果仍不起作用，请在设置中运行蓝牙疑难解答 > Update & Security > > 蓝牙疑难解答。
* 如果使用的是 Qualcomm 适配器，而电脑刚刚崩溃，请重启电脑。
* 尝试重新启动不配对的运动控制器，一次重启一次，然后重启电脑。
* 运动控制器缓存可能已损坏。 若要解决此问题，请参阅以下 [步骤](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)。
* 如果步骤解决了问题，则应与制造商联系。

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>我的配对控制器不会显示在混合现实门户中

* 按住耳机前面的控制器，并按四秒钟的 "Windows" 按钮重新启动它们，然后再次两秒钟。
* 如果控制器显示为 "已连接"，请取消配对它们，并再次执行 [配对过程](controllers-in-wmr.md#pair-motion-controllers) 。
* 如果控制器 Led 在每次打开和关闭时都有一个光源的四分之一，则它们正在进行固件更新。 等待更新完成，控制器应在混合现实中出现。
* 如果使用外部蓝牙适配器，请确保将适配器插入 USB 2.0 端口， (为黑色) ，远离其他无线发送器或 USB 3.0 设备。
* 如果电脑刚刚崩溃并使用了 Qualcomm 适配器，则重置可能不起作用。 若要解决此问题，请从计算机背面拔下电源 (或如果在笔记本电脑上按下电源按钮10秒钟) 并重新启动计算机。
* **设置 > Update & Security >** 蓝牙疑难解答中运行疑难解答 > 蓝牙。  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>我尝试配对控制器，但它们永远不会显示在 "蓝牙设置" 中的 "添加新设备" 菜单

检查是否已将控制器配对。 如果执行此操作，请将其删除，然后重试。 如果问题仍然存在，请重启电脑。 如果失败，请参阅[有关蓝牙](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)的详细信息。

注意：如果另一组运动控制器与你的电脑配对，你将需要取消配对这些控制器，然后再将它们配对。 如果将一组运动控制器与当前 PC 配对，然后将其与另一台电脑配对，则需要在使用当前 PC 之前取消配对并重新配对它们。

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>如何判断我使用的是蓝牙技术

运动控制器使用在多个使用者设备中找到的相同蓝牙技术，其设计用于处理任何最近的 PC 中包含的蓝牙功能。 如果你的电脑通过了混合现实兼容性检查，则它应具有蓝牙的收音机。 要验证：

* 打开 "Device Manager"。
* 展开 "蓝牙" 部分，并查找适配器。

![示例 Device Manager 的屏幕截图。 适配器是蓝牙的收音机。](images/devicemanagerbtadapterpic.png)

如果你的电脑没有蓝牙，请使用可插入 USB 蓝牙4.0 低能耗微适配器。

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>当动作控制器打开时，Wi-Fi 在笔记本上减速

当连接到 2.4 GHz 接入点时，笔记本可能与蓝牙共享其 Wi-Fi 天线。 如果可以将带区首选项切换为 5 GHz，请签入 Device Manager。 如果 5 GHz 网络不可用并且性能受到严重影响，请考虑使用蓝牙的转换器。

![可以通过设备管理器找到 Wifi 波段选择设置](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers&quot;></a>我的 PC 已蓝牙技术，但我的控制器有问题

运动控制器应与其他蓝牙键盘、鼠标和游戏控制器一起工作。 体验将因使用的键盘、鼠标或游戏控制器的型号而异。 可以执行以下操作来提高性能：

* 如果您的计算机有蓝牙但运动控制器仍有问题，请考虑将蓝牙收音机替换为插到 USB 的可插入外部蓝牙适配器。 一次只能有一个蓝牙的无线电适配器处于活动状态。 如果将外部广播与现有收音机一起插入，则需要在 Device Manager 中禁用现有蓝牙无线。 右键单击该适配器，然后选择 &quot;禁用设备&quot; 并取消配对/重新配对你以前蓝牙的所有设备。
* 如果使用的是 USB 蓝牙适配器，请将其连接到 USB 2.0 端口， (2.0 端口通常为黑色并且未标记为 &quot;SS" ) （如果可用）。 端口应以物理方式与以下内容分开：
    - HMD USB 连接器
    - 闪存驱动器
    - 硬盘驱动器
    - 无线 USB 接收器（如键盘/鼠标键盘的理想接收方）理想情况下，将 USB 蓝牙适配器插入到计算机的另一侧。
* 关闭 "蓝牙设置" 窗口（如果已打开）。 在后台打开它意味着对协议协议进行蓝牙调用。
* 如果头戴显示设备已与电脑配对，请使用 Windows 蓝牙驱动程序堆栈，并且不要安装任何第三方蓝牙驱动程序堆栈。 第三方软件可能无法正常工作。
* 禁用"其他设备迅速配对"下的"显示通知以使用设备进行连接"设置蓝牙 &以减少主机无线电扫描活动。
* 如果使用内部天线蓝牙，请确保使用的是外部天线蓝牙，否则可能会遇到跟踪问题。 如果此操作不起作用，在禁用内部连接蓝牙 USB () 使用外部蓝牙。
* 设备应显示在设置中的"鼠标、键盘&笔"类别蓝牙下。 如果设备位于"其他设备"下，则配对并配对设备。
* 删除、配对和关闭蓝牙和扬声器。 不支持这些Windows Mixed Reality。 使用混合现实头戴显示设备上的耳机插口或内置扬声器获得最佳音频体验。

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>我的第二个控制器需要很长时间才能重新连接

如果同时打开运动控制器，某些较旧的 Intel 无线电会遇到此问题。 避免同时打开控制器。

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>电脑崩溃蓝牙我的 Qualcomm 单选机无法对控制器进行配对

Qualcomm (Qualcomm) 蓝牙 10.0.0.448 之前无线电驱动程序可能在发生 Windows 故障后最终处于错误状态。 完全关闭电脑以解决此问题。

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>我遇到使用单选机进行控制器跟踪时表现不佳的情况

转到 **设备管理器 > 蓝牙 >选择"设备管理器 > 蓝牙 > AVASTAR 蓝牙** Radio Adapter > Properties > Driver"，并确保使用的是驱动程序 15.68.9210.47 或更高版本。
