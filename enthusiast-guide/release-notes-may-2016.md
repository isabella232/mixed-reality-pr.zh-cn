---
title: 发行说明 - 2016 年 5 月
description: 了解 Windows 全息2016更新的 HoloLens 发行说明。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，发行说明，操作系统，功能，生成，平台
ms.openlocfilehash: fe93890300d46dc12041f198a772671c79c97af0d6be2fc959937932a1d108c3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202522"
---
# <a name="release-notes---may-2016"></a>发行说明 - 2016 年 5 月

HoloLens 团队致力于通过 Windows 有问必答计划为你提供最新的功能更新和主要修复。 感谢你的所有建议，我们会将你的反馈反馈给你。 通过反馈中心、[开发人员论坛](https://forums.hololens.com) [ @HoloLens 和 Twitter](https://twitter.com/hololens)继续向[我们提供反馈](/windows/mixed-reality/give-us-feedback)。

**发行版：** Windows 全息 2016) 更新 (**10.0.14342.1016**

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

若要更新到当前版本，请打开 *设置* 应用，请参阅 *更新 & 安全*"，然后选择"*检查更新*"按钮。

## <a name="new-features"></a>新增功能

* 你现在可以 **同时在2d 视图中运行最多三个应用**，这可为 HoloLens 中的多任务提供无限用例。 浏览此航班上的新功能时，将新的反馈中心与知识探寻点列表打开。

  ![HoloLens 可以同时运行三个应用](images/img-3625-400px.jpg)<br>
  同时在2D 视图中运行最多三个应用

* 我们添加了新的 **语音命令**：
   * 尝试查看全息图并通过 "面部我" 来旋转
   * 使用 "更大" 或 "小" 来更改其大小
   * 通过说 "你好 Cortana，将 *应用名称* 移动到此处" 移动应用。
* 我们 **HoloLens 更轻松地进行开发**。 现在，你可以通过[Windows 设备门户](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)浏览、上传和下载文件。 你可以通过 Visual Studio 访问你的任何一侧加载或部署的应用程序的 "文档" 文件夹、"图片" 文件夹和 "本地存储"。
* **模拟器现在支持使用 Microsoft 帐户登录**，就像你在实际 HoloLens 上一样，你可以从 "其他工具" 菜单的 ">>" 启用。
* **二维应用现在会在观看视频全屏时隐藏应用栏和光标** 以避免干扰。 你的视频观看体验将更有乐趣地 HoloLens。
* 你还可以在 **没有应用栏的情况下固定照片** 。

  ![对于诸如照片的2D 应用，可以隐藏应用栏](images/img-3626-400px.jpg)<br>
  对于具有2D 视图的应用（如照片），可以隐藏应用栏

* **文件选取器** 的工作方式与 HoloLens 上的预期一样。
* 更新了 **Edge 浏览器** ，以通过桌面和电话映射统一的用户体验。 已启用浏览器的多个实例，自定义 HoloLens 新的选项卡页，选项卡查看，并在新窗口中打开，以及电源 & 性能改进。
* **Groove 音乐** 应用现在为 HoloLens。 访问应用商店进行下载，并尝试在后台播放。
* 您可以轻松地自定义应用在您的世界中的排列方式。 通过只需单击并拖动中间垂直线框中的圆圈，尝试在调整模式下 **旋转全息影像** 。 你可能会注意到，全息影像具有更 **严格的拟合边界框** ，以确保最大化交互。 你还可以将所有平面应用垂直调整 (除了照片和全息影像应用) 。

  ![将全息影像放置在世界中后可以旋转](images/img-3627-400px.jpg)<br>
  将全息影像置于世界中后旋转

* 我们在此航班中进行了多项 **输入改进** 。 可以将常规蓝牙鼠标连接到 HoloLens。 已对 clicker 进行了微调，以便 & 通过 clicker 移动全息影像。 键盘的运行效果也比以往更好。
* 现在，可以通过按向上键和向下键同时按下的方式来获取 **混合现实图片** 。 你还可以共享混合现实 & 视频到 Facebook、Twitter 和 YouTube 的已捕获照片。
* **混合现实视频** 的最大记录长度已增加到五分钟。
* **照片应用** 现在可从 OneDrive 流式传输视频，而无需在播放前下载整个视频。
* 我们已改进了你 **离开全息影像的** 方式。 你还将看到重新连接到 Wi-Fi 的选项，如果 HoloLens 无法检测到这些位置，请重试。
* 键盘提供了一个 **用于输入电子邮件地址的布局** ，其中的密钥允许您通过单击即可输入最受欢迎的电子邮件域。
* 在 OOBE 期间加快 **应用注册** 和时区的 **自动检测** ，为你提供最佳的第一个用户体验。
* **存储意义** 允许您在 "设置" 应用程序中查看系统和应用程序的剩余和已用磁盘空间。
* 我们已将反馈应用和内部集线器聚合到单个应用 **反馈中心**，这是一个用于向 **我们提供** 有关你喜欢的功能、需要改进的功能以及你可以执行哪些操作的反馈的工具。 加入有问必答计划后，你可以随时 **获取最新的内幕资讯**、 **评级版本** ，并从反馈中心 **知识探寻点反馈** 。
* 我们还[发布了 Emulator 版本的更新 HoloLens](/windows/mixed-reality/develop/install-the-tools) 。
* 由于自动 **视频抖动**，混合现实视频现在看起来更好。

## <a name="major-fixes"></a>主要修补程序

我们修复了全息图空间的问题，其中的空间速度较慢或检测不正确。 修复了关机问题，此问题可能会继续尝试在关闭过程中启动 shell。

解决了问题
* 这会阻止恢复 XAML 应用程序的功能。
* 出现故障时，会导致黑屏和一些锯齿线条。
* 使用某些应用时，滚动有时会出现错误的方向。
* 当设备仍处于打开状态时，电源 Led 可能指示为关闭状态。
* 从待机状态恢复后，WiFi 可能会关闭。
* Xbox 标识提供程序提供玩家代号设置，并停滞在循环中。
* 在 OneDrive 文件选取器中选择下载的文件时，外壳有时会崩溃。
* 按住链接有时会打开一个新的、断开的选项卡并打开上下文菜单。
* windows 设备门户不允许从50到80的 IPD 调整

修复了照片问题
* 图像有时会显示旋转，因为忽略 EXIF 方向属性被忽略。
* 在启动固定照片时，它可能会崩溃。
* 视频会在暂停后重新启动，而不会从上次暂停的位置继续。
* 如果共享视频是在播放时共享的，则可能会阻止其重播。
* 混合现实捕获记录将从仅音频源的 0.5-1 秒开始。
* "同步" 按钮在初始 OneDrive 同步过程中消失。

已解决设置问题，其中
* 环境更改时需要进行刷新。
* 键盘上的 "Enter" 不像单击某些对话框中的 "下一步"。
* 很难知道 clicker 失败的配对。
* 它可能会因为 WiFi 断开连接和连接而无法响应。

修复了 Cortana 的问题
* 它可能会停滞显示侦听 UI。
* 如果你回答 "是" 或 "否" 以退出应用程序的请求，请在 "独占模式" 应用中询问 "你好 Cortana"。
* 如果请求 Cortana 进入睡眠状态，然后再继续，Cortana 侦听 UI 将无法正确恢复。
* 查询 "我连接到哪些网络？" "我已连接"。 当第一个网络配置文件返回无连接时，可能会失败。
* 用户界面冻结 "正在侦听"，但在退出应用程序后，将立即开始执行语音识别。
* 如果从 Cortana 应用注销，则在重新启动之前，不会让你重新登录。
* 当混合现实捕获 UI 处于活动状态时，它不会启动。

修复了 Visual Studio 的问题
* 后台任务调试不起作用。
* 图形调试器中的帧分析不起作用。
* 除非将项目的 TargetPlatformVersion 设置为10240，否则不会在 Visual Studio 的下拉列表中显示 HoloLens Emulator。

## <a name="changes-from-previous-release"></a>以前版本中的更改
* Cortana 命令 **嗨 Cortana，重新启动设备** 不起作用。 用户可能会说 **Cortana，重新启动，** 或者 **嘿 Cortana，重新启动设备**。
* 已从产品中删除展台模式。

## <a name="prior-release-notes"></a>以前的发行说明
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另请参阅
* [HoloLens 已知问题](/windows/mixed-reality/hololens-known-issues)
* [安装工具](/windows/mixed-reality/develop/install-the-tools)
* [Shell](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)
* [更新混合现实的 2D UWP 应用](/windows/mixed-reality/develop/porting-apps/building-2d-apps)
* [硬件配件](/windows/mixed-reality/discover/hardware-accessories)
* [混合现实捕获](/windows/mixed-reality/mixed-reality-capture)
* [语音输入](/windows/mixed-reality/design/voice-input)
* [将应用提交到 Windows 存储](/windows/mixed-reality/distribute/submitting-an-app-to-the-microsoft-store)
* [使用 HoloLens 仿真器](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)