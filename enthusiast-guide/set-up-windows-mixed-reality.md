---
title: 设置 Windows Mixed Reality
description: 如何设置 Windows Mixed Reality 运动控制器、语音和音频，并为安全播放空间定义房间边界。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，入门，安装，运动控制器，控制器，语音，音频，固定，下，边界，图形驱动程序，Microsoft Edge，chromium
ms.openlocfilehash: cd59fd34dd00edc98d209681cc1239895c36ada2
ms.sourcegitcommit: 55a6a0b481238e7a2e3278a51583b6bda0eb259a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434631"
---
# <a name="set-up-windows-mixed-reality"></a>设置 Windows Mixed Reality

## <a name="get-ready"></a>准备工作

若要运行 Windows Mixed Reality，你将需要：

* 兼容混合现实沉浸式耳机。 [了解详细信息](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* 适用于你的耳机的 [Windows Mixed Reality 就绪 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ，其中包含正确的端口
* 运动 [控制器](controllers-in-wmr.md)、Xbox 控制器或鼠标和键盘
* 如果耳机上没有内置麦克风，请 (耳机) 
* 大的开放空间

## <a name="get-set"></a>获取集

准备空间 (包括) 的开销空间。 请确保要使用的区域中没有障碍物、危险或脆弱的项目。 请勿在楼梯的顶部或在超低天花板风扇下进行设置。 从区域中删除 breakables 和障碍，并确保你和使用你的耳机的任何人都阅读并了解 [安全指导原则](https://support.microsoft.com/help/4039969)。

## <a name="go"></a>开始！

空间准备就绪后，请插入耳机，但不要将其放置在一起，首先我们需要在你的电脑上进行一些设置。 我们将运行电脑检查、下载某些软件、连接控制器，并创建 [边界](boundary-questions.md) 来帮助避免障碍。

然后，将其放在您的耳机上，并进入 mixed world。 Cortana 将等待为你演示。 玩得愉快！

## <a name="get-familiar-with-your-motion-controllers"></a>熟悉运动控制器

如果耳机有内置收音机，则与耳机一起提供的控制器会在工厂中配对。 首次打开新控制器和耳机时，它们已配对。

如果有不带内置收音机的耳机，则必须通过将运动控制器配对到电脑 (在2018内置无线电) 后制造的大多数耳机。

如果只计划使用 Xbox 游戏板或键盘和鼠标，则无需配对控制器。  如果你计划使用控制器，你应该将它们配对。

**注意**： Windows Mixed Reality 运动控制器需要蓝牙4.0。 如果你的电脑没有内置蓝牙，你将需要插入支持蓝牙4.0 的 USB 蓝牙适配器，才能启用运动控制器。 如果你使用的是耳机中的内置广播，则不需要蓝牙适配器。

![熟悉运动控制器](images/get_to_know_controllers.png)

如果需要配对运动控制器，请查看 [Windows Mixed Reality](controllers-in-wmr.md) 一文中的 "控制器"。

## <a name="set-up-your-room-boundary"></a>设置房间边界

选择会议室或书桌规模体验：

**选项1：设置) 的所有体验 (也称为 "空间缩放" ** 使你可以浏览房间，并且是最能沉浸的混合现实体验。 建议在混合现实中清除至少5英尺 x 7 英尺 (1.5 米 x 2 米) 空间。

**选项2：设置 " (" （也称为 "桌面"）) ** 体验在你的办公桌上工作。 如果空间中没有很多空间，则这是一个不错的选择。 这也意味着你将在没有边界的情况下使用耳机。 你需要保留在一个位置，因为你没有边界来帮助你避免物理障碍。 此外，某些应用和游戏可能设计为与边界一起使用，因此它们可能无法按预期工作。

![选择安装](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a>如果选择 "设置为所有体验"，

不久，你的聊天室就会成为一个虚拟世界，你可以在其中进行浏览和交互！ 在空间中，为运行混合现实 (（例如，清除一些楼层空间，并将椅子移到房间) 的一侧，就可以清楚地了解空间。 建议在混合现实中清除至少5英尺 x 7 英尺 (1.5 米 x 2 米) 空间。

![确保空间清晰](images/1050px-createaboundary.png)

请确保您的空间清晰。

![使耳机居中](images/1050px-createaboundary-2.png)

将耳机居中。

![跟踪边界](images/1050px-createaboundary-3.png)

跟踪边界。

![一直指向 PC](images/1050px-createaboundary-4.png)

使你的头戴显示在你的电脑上。

![下面是边界](images/1050px-createaboundary-5.png)

下面是边界。

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a>如果选择 "设置为已安装并运行"

如果选择此选项，则无需执行其他步骤。

## <a name="what-is-the-maximum-size-of-the-boundary"></a>边界的最大大小是多少？

Windows Mixed Reality 中当前支持的最大边界大小为 18x18ft (5.7 x 5.7 m) 或 13ft (4 分钟) radius （中心）。  边界大小取决于锚点，以及从锚点到该点之间的距离，你可以在风险的稳定性之前进行移动。  Windows Mixed Reality 建立在平台中的一个阶段抽象基础之上，这一阶段就是您在其中移动的空间，而此阶段依赖于单个定位点 (每个应用程序也会假设，这也是 Naopak 和 Oculus 的工作方式，因为它们只有单个坐标系统) 。  这一点很重要的原因是，使用内部跟踪，因为从锚点中进一步移动时，耳机跟踪在保持边界稳定时是可靠的。  如果边界旨在帮助避免物理障碍，就会越来越多地从中心开始更多问题。  两个因素决定了最大边界大小;Windows Mixed Reality 耳机可提供最佳房间缩放体验的最大距离（对于大多数 Windows Mixed Reality 耳机，最大限度地减少了头戴式耳机线）的 (10ft) 。

## <a name="set-up-speech"></a>设置语音

可以在混合现实内启用 Cortana 命令。 这样，便可以使用混合现实中的语音命令传送、打开应用和执行其他操作。 你将在 " [了解混合现实](learn-mixed-reality.md) " 一章中了解有关此情况的详细信息。

![语音的混合现实效果更佳](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a>设置音频耳机

除非购买的是附带 AKG 耳机和集成双重麦克风阵列) 的 Samsung HMD 太空 (，否则，将需要获得同时具有麦克风和) 耳机的音频耳机 (，并将其插入耳机的 3.5 mm 音频插孔。 用于耳机的 3.5 mm 音频插孔将取决于耳机型号-位于耳机面板的底部，或位于耳机式面板的短音频电缆的末尾。

## <a name="adjusting-your-headsets-display-settings"></a>调整头戴显示设备的显示设置

Windows Mixed Reality 根据你的电脑的硬件配置，自动选择用于平衡质量和性能的显示设置。 若要调整这些设置，请参阅 " **设置" > 混合现实 > 耳机显示**。

### <a name="visuals"></a>视觉对象

此设置控制混合现实主页的视觉质量。 默认值为 "自动"。

### <a name="resolution"></a>解决方法

此处显示了头戴显示的分辨率。

如果连接带有较高分辨率的耳机 (例如，使用4320x2160 的耳机显示 PC) ，你将看到一个调整混合现实显示分辨率的设置。

* 此设置为 Windows Mixed Reality 组合堆栈提供选项，以在 4320x2160) 的情况下呈现本机 (例如，在上呈现组合堆栈，或在较低的分辨率和 upscale 上呈现组合堆栈 (例如，在2880x1440 和 upscale 呈现为 4320x2160) 。
* 默认设置为以本机方式呈现 (例如， **4320 x 2160 (最佳质量) ** 选项) 以提供可从耳机获得最佳视觉质量。
* 如果你的电脑不满足具有更高分辨率显示器的头戴显示设备的最低图形硬件要求，并且/或者如果你看到图形性能问题，则可以尝试使用选择 " **自动增加 (最佳性能) ** " 选项。

此设置在 Windows 10 版本1903或更高版本上可用。

### <a name="calibration"></a>校准

此设置是为了为带有软件 IPD 支持的耳机调整 IPD 校准。

### <a name="experience-options"></a>体验选项

此高级设置将覆盖默认的耳机显示刷新频率体验。

* **自动 (默认) **：根据电脑的硬件配置，自动选择60Hz 或90Hz 体验。
* **60Hz**
* **90Hz**

>[!Note]
>第一次设置 HP 回音 G2 耳机时，体验将更改为90Hz，以确保获得最佳体验。  如果需要，可以将其更改回 "自动"。

### <a name="input-switching"></a>输入切换

此设置控制 Windows Mixed Reality 为响应头戴显示传感器的行为：

* **使用耳机状态传感器自动切换** (默认) ：在戴上耳机时，windows 将自动将输入 (键盘、鼠标 ... ) 到 Windows Mixed Reality。 可以通过 Win + Y 随时替代此情况。
* **使用 Windows 徽标键 + Y 手动切换**： windows 不会使用耳机状态传感器来检测戴戴显示设备。 需要使用 Win + Y 在 PC 桌面和 Windows Mixed Reality 之间切换输入。

此设置在 Windows 10 版本1903或更高版本上可用。

## <a name="installing-microsoft-edge"></a>正在安装 Microsoft Edge 

若要在 Windows Mixed Reality 主页中使用新的基于 Chromium 的 Microsoft Edge，请升级到 Windows 10 1903 版或更高版本，以便对 Win32 应用程序的本机支持 (例如 Windows Mixed Reality 主页中新的 Microsoft Edge) 。 请检查 Windows 更新或 [手动安装最新版本的 Windows 10](https://www.microsoft.com/software-download/windows10)。

>[!IMPORTANT]
>新的 Microsoft Edge 启动时支持 WebXR，这是创建用于 VR 耳机的沉浸式 web 体验的新标准。 如果安装新的 Microsoft Edge，你将无法再在 Microsoft Edge 中播放 WebVR 体验。

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a>Windows Mixed Reality 中新的 Microsoft Edge 的问题

**2020-01 (或更高1903版本的 Windows 10 累积更新解决了已知问题) **

- 启动任何 Win32 应用程序（包括新的 Microsoft Edge）都会导致耳机显示暂时冻结。
- Microsoft Edge 磁贴从 Windows Mixed Reality 开始菜单中消失 (你可以在) 的 "经典应用" 文件夹中找到它。
- 以前的 Microsoft Edge 中的 Windows 仍位于混合现实主页，但无法使用。 尝试激活桌面应用内的 windows 启动边缘。
- 选择混合现实中的超链接时，将在桌面上而不是混合现实主页上启动 web 浏览器。
- 尽管不再支持 WebVR，但 WebVR 展示应用存在于混合现实主页中。
- 键盘启动和视觉对象的一般改进。

**其他已知问题**

- 当混合现实门户关闭时，在 Windows Mixed Reality 中打开的网站将会丢失，但 Microsoft Edge 窗口仍会保留在混合现实中的位置。
- Microsoft Edge windows 中的音频未 spatialized。
- 修复了360查看器扩展版本2.3.8：在 Windows Mixed Reality 中从 YouTube 打开360视频可能会导致耳机上出现视频失真。 重启边缘应在不可见的情况下更新360查看器扩展以解决此问题。 您可以通过 `edge://system/` 在地址栏中输入，然后选择 "扩展" 旁边的 "展开" 按钮，确认您所拥有的扩展版本。
- 在 Windows Mixed Reality 会话期间，虚拟监视器将在 " **设置" > 系统 > 显示**中显示为一般物理监视器。

## <a name="launching-mixed-reality-after-the-first-time"></a>首次启动混合现实

第二次输入混合的实际情况非常简单，就像将头戴显示在连接到您的 PC 上一样简单。 还可以通过从 "开始" 菜单打开混合现实门户应用程序，手动启动该应用程序。 当你将输入和音频置于耳机上时，它会自动将其路由到耳机，你也可以通过按键盘上的 **Windows + Y** 来手动触发。

## <a name="see-also"></a>另请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)
* [排查安装问题](installation_errors.md)
* [安装疑难解答](set-up-questions.md)
* [了解 Mixed Reality](learn-mixed-reality.md)
* [运动控制器](controllers-in-wmr.md)
* [由内而外跟踪的工作原理](tracking-system.md)
