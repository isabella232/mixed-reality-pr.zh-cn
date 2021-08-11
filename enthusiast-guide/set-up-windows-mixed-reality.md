---
title: 设置 Windows Mixed Reality
description: 如何设置运动控制器Windows Mixed Reality语音和音频，并定义安全播放空间的空间边界。
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 入门， 设置， 运动控制器， 控制器， 语音， 音频， 固定， 站， 边界， 图形驱动程序， Microsoft Edge， chromium
ms.openlocfilehash: 436818ee662f9beb1c445ea5b22c5d168bb4142a7b49a116a4f5fa138e3a5595
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221040"
---
# <a name="set-up-windows-mixed-reality"></a>设置 Windows Mixed Reality

## <a name="get-ready"></a>准备工作

若要Windows Mixed Reality，需要：

* 兼容的混合现实沉浸式头戴显示设备。 [了解详细信息](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* 一[Windows Mixed Reality](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)头戴显示设备正确端口的已就绪电脑
* 运动 [控制器](controllers-in-wmr.md)、Xbox 控制器或鼠标和键盘
* 如果头戴显示设备没有内置麦克风 (麦克风的耳机) 
* 一个大型的开放空间

## <a name="get-set"></a>获取集

准备空间 (包括开销空间) 。 请确保将使用的区域中没有障碍、危险或易损坏的项。 请勿在风扇顶部或超低的上限风扇下设置 。 从该区域中删除任何断点或障碍，并确保所有头戴显示设备用户阅读并了解安全准则。

空间准备就绪后，请插入头戴显示设备，但不要将其打开 -首先，我们需要在电脑上进行一些设置。 我们将运行电脑检查、下载一些软件、连接控制器，并创建边界来帮助你避免[](boundary-questions.md)障碍。

然后是有趣的部分- 放在头戴显示设备上，进入混合世界。 Cortana等待你浏览。 玩得愉快！

## <a name="go"></a>开始！

空间准备就绪后，请插入头戴显示设备，但不要将其打开 -首先，我们需要在电脑上进行一些设置。 我们将运行电脑检查、下载一些软件、连接控制器，并创建边界来帮助你避免[](boundary-questions.md)障碍。

然后是有趣的部分- 放在头戴显示设备上，进入混合世界。 Cortana等待你浏览。 玩得愉快！

## <a name="get-familiar-with-your-motion-controllers"></a>熟悉运动控制器

如果头戴显示设备具有内置无线电，则头戴显示设备随头戴显示设备一起在工厂中配对。 首次打开新控制器和头戴显示设备时，它们已配对。

如果头戴显示设备没有内置无线电，必须将其与电脑配对来设置运动控制器。 大多数在 2018 年之后生产的头戴显示设备都内置了无线电。

如果仅计划使用 Xbox 游戏板或键盘和鼠标，则无需对控制器进行配对。  如果计划使用控制器，应将其配对。

**注意**：Windows Mixed Reality运动控制器需要 蓝牙 4.0。 如果电脑没有内置 蓝牙，则需要插入支持 蓝牙 4.0 的 USB 蓝牙 适配器，以启用运动控制器。 无需使用 蓝牙适配器来使用头戴显示设备中的内置无线电。

![熟悉运动控制器](images/get_to_know_controllers.png)

如果需要配对运动控制器，请查看本文[中的](controllers-in-wmr.md)Windows Mixed Reality控制器。

## <a name="set-up-your-room-boundary"></a>设置房间边界

选择房间规模或桌面规模体验：

**选项 1：** 为我设置 (也称为房间缩放) 让你能够四处移动房间，是最沉浸式混合现实体验。 建议至少清除 5 英尺 x 7 英尺 (1.5 米 x 2 米) 混合现实空间。

**选项 2：为我** 设置 (台式) 台式办公体验。 如果空间不大，这是一个不错的选择。 这也意味着你将使用没有边界的头戴显示设备。 你需要停留在一处，因为没有任何边界来帮助避免物理障碍。 某些应用和游戏并非旨在成为边界体验，因此它们可能无法如预期工作。

![选择设置](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a>如果选择"针对所有体验设置我"

很快，你的房间将成为一个虚拟世界，你可以在这里四处移动和交互！ 站起并清除房间中的一些空间，以运行混合现实。 建议至少清除 5 英尺 x 7 英尺（1.5 米 x 2 米）的空间，用于混合现实。

![确保空间清晰](images/1050px-createaboundary.png)

请确保空间清晰。

![将头戴显示设备居中](images/1050px-createaboundary-2.png)

将头戴显示设备居中。

![跟踪边界](images/1050px-createaboundary-3.png)

跟踪边界。

![保持指向电脑](images/1050px-createaboundary-4.png)

将头戴显示设备指向电脑。

![下面是边界](images/1050px-createaboundary-5.png)

下面是边界。

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a>如果选择"设置我以说话和站位"

如果选择此选项，则无需执行额外的步骤。

## <a name="what-is-the-maximum-size-of-the-boundary"></a>边界的最大大小是什么？

Windows Mixed Reality 中支持的最大边界大小为 18x18ft (5.7x5.7m) 或 13 ft ( (4 m) 半径。 边界大小取决于定位点以及距离定位点有多远，才能面临边界稳定性的风险。  Windows Mixed Reality构建在阶段抽象上，而阶段是移动的空间。 该阶段依赖于单个定位点，几乎每个应用也假设这一点 - Vive 和 Oculus 也使用其单一坐标系。  这一点很重要，因为使用内出跟踪时，当你从定位点进一步离开时，头戴显示设备跟踪在保持边界稳定方面是可靠的。  如果边界旨在帮助避免物理障碍，那么从你离开的中心越远，问题就更多了。  有关最大边界大小的决策有两个因素。 头戴显示设备Windows Mixed Reality提供最佳房间刻度体验的最大距离和头戴显示设备电缆的长度，对于大多数 Windows Mixed Reality 头戴显示设备来说，最大距离为 10 (3 米) 。

## <a name="set-up-speech"></a>设置语音

可以在混合Cortana启用语音命令，从而使用语音命令来远程传送和打开应用。 你将在操作说明一章中[了解混合现实操作。](learn-mixed-reality.md)

![混合现实比语音更好](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a>设置音频头戴显示设备

除非购买了带集成 AKG 耳机和双麦克风阵列的 Samsung HMD Odyssey，否则需要获取一个同时具有麦克风和耳机的音频头戴显示设备，并插入头戴显示设备 3.5 毫米音频插口。 头戴显示设备 3.5 毫米音频插口位于头戴显示设备视口的下面或连接到头戴显示设备视口的短音频电缆的末尾，具体取决于头戴显示设备型号。

## <a name="adjusting-your-headsets-display-settings"></a>调整头戴显示设备显示设置

Windows Mixed Reality根据电脑的硬件配置自动选择平衡质量和性能的显示设置。 若要调整这些设置，请转到"设置 >**混合现实>头戴显示"。**

### <a name="visuals"></a>视觉对象

此设置控制混合现实主页的视觉质量。 默认值为"Automatic"。

### <a name="resolution"></a>解决方法

此处显示了头戴显示设备本机分辨率。

如果将分辨率更高的头戴显示设备连接到电脑，例如显示 4320x2160 的头戴显示设备，则会看到用于调整混合现实显示分辨率的设置。

* 此设置为 Windows Mixed Reality 组合堆栈提供了以本机方式呈现 (（例如，在 4320x2160) ）或使组合堆栈以较低的分辨率和向上缩放呈现的选项 (例如，以 2880x1440 呈现，将比例向上缩放到 4320x2160) 。
* 默认设置以本机方式呈现 (例如 **，4320 x 2160 (最佳** 质量) 选项) ，以便从头戴显示设备提供最佳视觉质量。
* 如果存在 **以下情况，** 请使用 (自动) 优化"选项：
    * 电脑不符合显示器分辨率更高的头戴显示设备的最低图形硬件要求
    * 你看到了图形性能问题

此设置适用于 Windows 10 1903 或更高版本。

### <a name="calibration"></a>校准

此设置用于调整支持软件 IPD 的头戴显示设备 IPD 校准。

### <a name="experience-options"></a>体验选项

此高级设置将替代默认头戴显示刷新速率体验。

* **自动 (默认) ：** 根据电脑的硬件配置自动选择 60 Hz 或 90-Hz 体验。
* **60 Hz**
* **90 Hz**

>[!Note]
>首次设置 HP Reverb G2 头戴显示设备时，体验将更改为 90Hz，以确保获得最佳体验。  如果需要，可更改回"自动"。

### <a name="input-switching"></a>输入切换

此设置控制设备Windows Mixed Reality头戴显示传感器的响应：

* 使用头戴显示传感器自动切换 (默认) ：Windows每当头戴显示设备 (时，) 会自动将输入Windows Mixed Reality键盘、鼠标...Windows Mixed Reality。 你随时可以使用 Win + Y 重写此 。
* **手动切换Windows** 徽标键 + Y：Windows不会使用头戴显示设备状态传感器来检测何时头戴显示设备。 你需要使用 Win + Y 在电脑桌面和电脑设备之间Windows Mixed Reality。

此设置适用于 Windows 10 1903 或更高版本。

## <a name="installing-microsoft-edge"></a>安装Microsoft Edge 

若要在 Windows Mixed Reality 主页Microsoft Edge使用基于 Chromium 的新 Microsoft Edge，请升级到 Windows 10 版本 1903 或更高版本，以本机支持 Win32 应用程序 (如 Windows Mixed Reality 主页中的新 Microsoft Edge) 。 检查Windows更新[或手动安装最新版本Windows 10。](https://www.microsoft.com/software-download/windows10)

>[!IMPORTANT]
>新Microsoft Edge WebXR（为 VR 头戴显示设备创建沉浸式 Web 体验的新标准）启动。 如果安装了新应用，Microsoft Edge中无法再播放 WebVR Microsoft Edge。

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a>中新Microsoft Edge的问题Windows Mixed Reality

**版本 1903 或更高版本的 2020-01 Windows 10 累积更新解决的已知 (问题)**

- 启动任何 Win32 应用（包括Microsoft Edge）会导致头戴显示短暂冻结。
- "Microsoft Edge磁贴从"Windows Mixed Reality "开始"菜单 ("文件夹中消失，可在"经典应用"文件夹中找到) 。
- Windows上一个Microsoft Edge仍放置在混合现实主页周围，但不能使用。 尝试激活这些窗口会启动桌面应用中的 Edge。
- 选择窗口中的超链接混合现实主页在桌面上启动 Web 浏览器，而不是混合现实主页。
- WebVR 展示应用存在于 混合现实主页，尽管不再支持 WebVR。
- 对键盘启动和视觉对象的常规改进。

**其他已知问题**

- 在 Windows Mixed Reality 中打开的网站将在关闭混合现实门户丢失，尽管Microsoft Edge窗口将保留它们放置在混合现实主页。
- 来自Microsoft Edge的音频未进行空间化。
- 在 360 查看器扩展版本 2.3.8 中修复：在 Windows Mixed Reality 中打开 YouTube 中的 360 视频可能会导致视频在头戴显示设备中扭曲。 重启 Edge 时，应以不公开方式更新 360 查看器扩展来解决此问题。 可以通过在地址栏中输入 并选择"扩展"旁边的"展开"按钮来确认扩展 `edge://system/` 的版本。
- 在Windows Mixed Reality会话期间，虚拟监视器将在 System 设置 > Display 中显示为>**监视器**。

## <a name="launching-mixed-reality-after-the-first-time"></a>首次后启动混合现实

再次进入混合现实就像将头戴显示设备连接到电脑时重新打开一样简单。 也可通过从混合现实门户打开应用程序来手动启动"开始"菜单。 输入和音频会在你打开头戴显示设备时自动路由到头戴显示设备，或者可以通过在键盘上按 Windows **+ Y 来** 手动触发此操作。

## <a name="see-also"></a>另请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们获得支持](https://support.microsoft.com/contactus/)
* [排查安装问题](installation_errors.md)
* [设置疑难解答](wmr-setup-faq.yml)
* [了解 Mixed Reality](learn-mixed-reality.md)
* [运动控制器](controllers-in-wmr.md)
* [由内而外跟踪的工作原理](tracking-system.md)
