---
title: 发行说明 - 2017 年 10 月
description: 随时了解 Windows Mixed Reality 2017 年 10 月Windows 10 Fall Creators Update (发行说明) 。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 发行说明， 版本， windows 10， 内部版本， rs3， os
ms.openlocfilehash: 09a33e1bc4a13c75e4c8a0ee250c7b67eb8e68e21220840037085e727acfb1f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190591"
---
# <a name="release-notes---october-2017"></a>发行说明 - 2017 年 10 月

欢迎使用Windows Mixed Reality！ 此版本 **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** 引入了对沉浸式头戴显示设备 [Windows Mixed Reality和运动控制器](/windows/mixed-reality/discover/immersive-headset-hardware-details)[的支持](/windows/mixed-reality/design/motion-controllers)。 现在，可以探索新世界、玩 VR 游戏，以及连接到支持Windows Mixed Reality[沉浸式娱乐](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。

Windows Mixed Reality头戴显示设备和运动控制器的发布是团队大量努力的推动，也是 Windows Mixed Reality 平台（包括[Microsoft HoloLens）。](/windows/mixed-reality/hololens-hardware-details) [](/windows/mixed-reality/discover/mixed-reality) 尽管HoloLens未收到更新，但Windows 10 Fall Creators Update尚未停止HoloLens工作。 我们将从我们最近的工作中从整个Windows Mixed Reality大量学习和见解。 事实上，Windows Mixed Reality沉浸式头戴显示设备和运动控制器也是开发HoloLens一个很好的入口点，因为相同的 API、工具和概念适用于这两者。

若要更新到每个设备的最新版本，请打开 设置 **应用，** 转到"更新&**安全性**"，然后选择"检查 **更新"** 按钮。 在 Windows 10 电脑上，还可使用 Windows 媒体创建工具 手动安装[Windows 10 Fall Creators Update。](https://www.microsoft.com/software-download/windows10)

 **桌面的最新版本：Windows 10** Desktop 2017 年 10 月 (**10.0.16299.15** Windows 10 Fall Creators Update) <br>
 **HoloLens** 最新版本 [：Windows 10 全息版 2016](release-notes-august-2016.md)年 8 月 **(10.0.14393.0，Windows 10** 周年更新) 

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Windows Mixed Reality

该Windows 10 Fall Creators Update正式引入了对Windows Mixed Reality头戴显示设备与运动控制器的支持，Windows 10全球第一个空间操作系统。 以下是一些亮点：
* **[各种头戴](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** 显示设备 - Windows Mixed Reality合作伙伴提供不同的头戴显示设备类型，价格从与运动控制器捆绑在一起的费用为 399 美元。
* **[运动控制器](/windows/mixed-reality/design/motion-controllers)**- Windows Mixed Reality运动控制器通过无线方式与电脑配对蓝牙具有六个自由跟踪、大量输入方法和 IMUS。
* **[轻松设置和可移植](./recommended-adapters-for-windows-mixed-reality-capable-pcs.md)** 性 - 在 10 分钟内设置并启动。 沉浸式头戴显示设备使用内出跟踪来跟踪运动和运动控制器，具有六个自由度。 无需外部相机或灯泡标记！
* **[支持更广泛的电脑](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)**- Windows Mixed Reality将允许更多人体验桌面 VR，支持从 499 美元开始选择集成图形卡和电脑。
* **[Windows Mixed Reality](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)** 主页 - 全球第一个空间操作系统为 2D 应用的多任务处理、启动 VR 游戏和应用以及放置装饰性全息影像提供了熟悉的家庭环境。
* Microsoft Store 中的令人惊叹的 **[VR](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** 游戏和应用 - 从沉浸式娱乐（如 Hulu VR 和 360 视频）到长篇故事（如 SUPERHOT VR 和亚利桑那州）中，Microsoft Store 在 Windows Mixed Reality 中提供了一系列可体验的内容。
* **[SteamVR 早期](./using-steamvr-with-windows-mixed-reality.md)** 访问 - Windows 10 Fall Creators Update 支持将 SteamVR 标题与 Windows Mixed Reality 头戴显示设备和控制器一起播放，使 VR 标题的最大目录可供 Windows Mixed Reality 用户使用。

## <a name="known-issues"></a>已知问题

我们一直努力提供出色的Windows Mixed Reality体验，但仍在跟踪一些已知问题。 如果发现其他人， [请提供反馈](/windows/mixed-reality/give-us-feedback)。

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>桌面应用Windows Mixed Reality主页
* 截图工具桌面应用不起作用。
* 重新启动时，桌面应用不会保留设置。
* 如果在桌面上使用混合现实门户预览版，在 Windows Mixed Reality 中打开桌面应用时，可能会注意到无限镜像效果。 
* 运行桌面应用可能会导致非超级计算机电脑Windows Mixed Reality问题;不建议这样做。  
* 桌面应用可能会自动启动，因为桌面上不可见的窗口具有焦点。 
* 桌面用户帐户控制提示会使头戴显示设备显示为黑色，直到提示完成。

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality设置
* 在Windows头戴显示设备时，电脑监视器可能会空白。 拔下头戴显示设备以启用电脑监视器的输出，以完成Windows设置。
* 创建边界时，跟踪可能会失败。 如果是，请重试，因为系统将随着时间的推移了解有关空间的更多信息。
* 如果在安装Cortana启用或Windows Mixed Reality，此更改将应用于桌面Cortana设置。
* 如果未连接耳机，首次访问家庭Windows Mixed Reality小费。
* 蓝牙可能会干扰运动控制器。 我们建议在会话期间蓝牙或Windows Mixed Reality控制器。

### <a name="games-and-apps-from-windows-store"></a>来自 Windows Store 的游戏和应用
* 某些图形密集型游戏（如 Forza Gamesports 6）在游戏内部播放时，可能会导致性能较低Windows Mixed Reality。

### <a name="audio"></a>音频
* 如上所述，蓝牙音频外围设备无法很好地处理Windows Mixed Reality和空间音效体验。 它们还可能会对运动控制器体验产生负面影响。 不建议将音频头戴显示蓝牙与音频设备Windows Mixed Reality。
* 当设备未 (时，) 头戴显示设备进行音频播放。 如果只有一个音频头戴显示设备，可能需要将音频头戴显示设备连接到主机电脑而不是头戴显示设备。 如果是这样，则必须在混合现实音频和语音 中设置"切换到头戴显示设备  >    >  **音频"。**
* 某些应用程序（包括许多通过 SteamVR 启动的应用程序）在启动或停止音频设备时，可能会丢失音频或挂起混合现实门户。 打开应用后，请重启混合现实门户以更正此错误。
* 如果在Cortana头戴显示设备之前在主机上启用了Windows Mixed Reality，则可能会丢失应用于你放在Windows Mixed Reality应用的空间声音模拟。 解决方案是在连接到电脑的所有音频设备上启用"用于耳机的 Windows Sonic"，即使是连接头戴显示设备的音频设备：
   1. 在桌面任务栏上左键单击扬声器图标，然后从音频设备列表中选择。
   2. 右键单击桌面任务栏上的扬声器图标，然后选择"说话人设置用于耳机的 Windows Sonic菜单中的"扬声器"。
   3. 针对所有音频设备重复这些步骤 (终结点) 。
>[!NOTE]
> - 由于连接到头戴显示设备的耳机/扬声器不会显示，除非你正在穿戴它，所以你必须在 Windows Mixed Reality 主页的桌面应用窗口中进行此操作，以将此设置应用于连接到头戴显示设备 (或集成到头戴显示设备) 的音频设备。
> - 另一种选择是在启动 Windows Mixed Reality 之前，在桌面上设置Cortana"让 Cortana 响应Hey  >   Cortana"。

* 当另一个多媒体 USB 设备 (例如 Web cam) 与 Windows Mixed Reality 头戴显示设备共享同一 USB 集线器 (（外部或电脑) 内部）时，在极少数情况下，头戴显示设备的音频千万头戴显示设备可能会发出响声或没有任何音频。 可以通过头戴显示设备将其修复为不与其他设备共享同一集线器的 USB 端口，或者断开/禁用其他 USB 多媒体设备。
* 在极少数情况下，主机电脑的 USB 集线器无法为 Windows Mixed Reality 头戴显示设备提供足够电源，你可能会注意到连接到头戴显示设备的设备出现干扰。

### <a name="speech"></a>语音
* Cortana可能无法播放用于侦听/思考和命令的音频响应的音频提示。
* Cortana日本市场的文本在使用期间不会正确显示在Cortana下方。
* Cortana第一次在活动会话中调用她时，混合现实门户速度。 可以通过确保在启用"与 Cortana 聊天"下Cortana"设置Cortana"Cortana"。   >    >  
* Cortana在未运行 PC 的 PC 上运行Windows Mixed Reality Ultra速度。
* 当系统键盘设置为与 Windows Mixed Reality 中的 UI 语言不同的语言时，使用 Windows Mixed Reality 中的键盘听写将导致有关听写因没有 Wi-Fi 连接而失败的错误对话框。 若要解决此问题，请确保系统键盘语言与 Windows Mixed Reality UI 语言匹配。
* 西班牙未正确被识别为为用户启用语音的市场Windows Mixed Reality。

### <a name="holograms"></a>全息影像
* 如果已将大量全息影像放置在Windows Mixed Reality，则当你四处查看时，某些全息影像可能会消失并再次出现。 若要避免这种情况，请删除主Windows Mixed Reality区域中的一些全息影像。

### <a name="motion-controllers"></a>运动控制器
* 有时，如果在 Edge 中选择网页，内容将缩放而不是单击。
* 有时，当你在 Edge 中选择链接时，选择将不起作用。

## <a name="prior-release-notes"></a>以前的发行说明
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另请参阅
* [沉浸式头戴显示设备 (外部链接) ](./troubleshooting-windows-mixed-reality.md)
* [HoloLens 已知问题](/windows/mixed-reality/hololens-known-issues)
* [安装工具](/windows/mixed-reality/develop/install-the-tools)
* [给我们提供反馈](/windows/mixed-reality/give-us-feedback)