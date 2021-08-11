---
title: 发行说明 - 2018 年 10 月
description: 随时了解 2018 HoloLens Windows Mixed Reality 2018/RS5 更新Windows 10和发行说明。
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: 发行说明， 版本， windows 10， 内部版本， rs5， os
ms.openlocfilehash: e046025ff4952a6e8779545374ec59d9f49c907ad3174b188474ae040cb28ac7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219961"
---
# <a name="release-notes---october-2018"></a>发行说明 - 2018 年 10 月

**[Windows 10 2018 年 10 月更新 (](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** RS5) 包括适用于连接到电脑的HoloLens Windows Mixed Reality头戴显示设备新功能。 

若要更新到 HoloLens 或 PC (for Windows Mixed Reality 沉浸式 (VR) 头戴显示设备) 的最新版本，请打开 **设置** 应用，转到"更新 &**安全性**"，然后选择"**检查更新**"按钮。 在Windows 10电脑上，还可使用 Windows 10 2018 年 10 月更新 媒体创建工具 手动[Windows安装程序](https://www.microsoft.com/software-download/windows10)。

**桌面版最新版本：Windows 10 2018 年 10 月更新 (** **10.0.17763.107)**<br>
**最新版本的 HoloLens：Windows 10 2018 年 10 月更新 (** **10.0.17763.134**) <br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>沉浸式头戴显示Windows Mixed Reality的新功能

本Windows 10 2018 年 10 月更新包括对将沉浸式 Windows Mixed Reality VR () 桌面电脑使用的许多改进。

### <a name="for-everyone"></a>针对所有人

* **混合现实闪光灯** - 在现实世界中打开一个门户以查找键盘、查看附近的某人，或在不删除头戴显示设备的情况下查看周围的环境！ 可以通过在运动控制器上按 "开始"菜单 + 抓取Windows或说"打开/关闭"来打开混合现实闪光灯。 将控制器指向想要看到的方向，例如，在暗处使用闪光灯。

    ![混合现实闪光灯](images/mr-flashlight.png)

* **新应用中启动内容的混合现实主页**
    * 如果对 SteamVR 使用 Windows Mixed Reality，[则你的 SteamVR](./using-steamvr-with-windows-mixed-reality.md)标题现在会显示在 "开始"菜单 中，每个应用启动器可以放置在混合现实主页。
    
        ![SteamVR 应用启动器](images/steamvr-launchers.png)
        
    * 新的 *360 视频* 应用，用于发现定期精选的 360 度视频。
    * 新的 *WebVR 展示* 应用，用于发现定期精选的 WebVR 体验选择。
    * 首次Windows Mixed Reality客户将输入 悬崖小屋，并发现其中预先填充了一些我们最喜欢的沉浸式应用和游戏的 3D 应用Microsoft Store。
    * Microsoft Edge窗口现在包含"共享 *"* 按钮。
* **快速操作菜单**- 在沉浸式混合现实应用中，可以按 Windows 按钮访问新的快速操作菜单，轻松访问 *SteamVR* 菜单、*照片/视频捕获*、闪光灯和 *主页*。 
* **支持台式电脑**- Windows Mixed Reality完成 (后) 无需显示仿真器即可在台式电脑上运行的沉浸式 VR 头戴显示设备。
* 新的 **音频** 功能 - 现在可以将音频从 Windows Mixed Reality 体验镜像到头戴显示设备中的音频 (或耳机) 和连接到电脑的音频设备 (如外部扬声器) 。 我们还在头戴显示设备中添加了音量级别的可视指示器。
* **其他改进**
    * 混合现实门户更新现在通过 Microsoft Store 提供，从而在主要版本和版本Windows更新。 请注意，这仅适用于桌面应用，Windows Mixed Reality头戴显示设备体验仍通过 OS 进行更新。 
    * 当头戴显示设备进入睡眠状态时，Windows Mixed Reality应用将挂起而不是 (，直到混合现实门户关闭) 。
    
### <a name="for-developers"></a>面向开发人员

* **[QR](/windows/mixed-reality/develop/platform-capabilities-and-apis/qr-code-tracking)** 码跟踪 - 在混合现实应用中启用 QR 码跟踪，允许 Windows Mixed Reality沉浸式 (VR) 头戴显示设备扫描 QR 码，并报告回感兴趣的应用。
* 沉浸式应用的硬件 **DRM** 支持 - 开发人员现在可以请求受硬件保护的反缓冲纹理（如果受显示硬件支持），从而允许应用程序使用来自 PlayReady 等源的硬件保护内容。
* **[将混合现实捕获 UI](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** 集成到沉浸式应用中 - 开发人员只需几行代码，就可以使用内置的 Windows 相机捕获 [UI](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)将混合现实捕获集成到其应用中。

## <a name="new-features-for-hololens"></a>HoloLens

此Windows 10 2018 年 10 月更新可供所有客户HoloLens，并包括许多改进，例如：

### <a name="for-everyone"></a>针对所有人

* **快速操作菜单**- 在沉浸式混合现实应用中，可以按 Windows 按钮访问新的快速操作菜单，轻松访问"开始录制视频"、拍照、混合现实主页、调节音量和 *连接。* 
* **从"开始**"或"快速操作"菜单启动/停止视频捕获 - 如果从""开始"菜单"或"快速操作"菜单启动视频捕获，你将能够从同一位置停止录制。  (，也始终可以使用语音命令来) 
* **Project** 已启用 Miracast 的设备 - Project HoloLens内容到附近的 Surface 设备或电视/监视器（如果使用已启用 Miracast 的显示器或适配器）。
* **新通知**- 在电脑上查看HoloLens响应通知，就像在电脑上查看和响应通知一样。  
* **沉浸式混合** 现实应用中的有用覆盖 - 使用沉浸式混合现实应用时，现在会看到键盘、对话框、文件选取器等覆盖。
* **音量更改的** 可视指示器 - 在设备上使用音量增加/关闭按钮时HoloLens头戴显示设备中音量级别的可视指示器。
* **设备启动的新视觉对象** - 在启动过程中添加了加载指示器，以提供系统正在加载的可视反馈。
* **附近共享**- Windows共享体验允许与附近的设备共享Windows捕获。  
* **从Microsoft Edge** 共享 - Microsoft Edge现在包含"*共享"* 按钮。 

### <a name="for-developers"></a>面向开发人员

* **[将混合现实捕获 UI](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** 集成到沉浸式应用中 - 开发人员只需几行代码，就可以使用内置的 Windows 相机捕获 [UI](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)将混合现实捕获集成到其应用中。

### <a name="for-commercial-customers"></a>适用于商业客户

* **启用设置后预配**- 现在随时都可以使用 设置。
* **使用组分配Azure AD** - 现在可以使用Azure AD组来配置Windows分配的访问权限，以设置单应用或多应用展台配置。
* **从登录屏幕进行配置文件** 切换的 PIN 登录 - PIN 登录现在可用于登录屏幕上的"其他用户"。 
* **通过 MDM 读取设备硬件信息**- IT 管理员可以查看和跟踪HoloLens MDM 控制台中的设备序列号进行跟踪。
* **通过HoloLens MDM** 设置设备名称 (重命名) - IT 管理员可以在 MDM 控制台HoloLens和重命名设备。

### <a name="for-international-customers"></a>适用于国际客户

现在可以将 HoloLens 与简体中文或日语的本地化用户界面一起使用，包括本地化的 Pinyin 键盘、听写、文本到语音 (TTS) 和语音命令。

## <a name="known-issues"></a>已知问题

我们一直努力提供出色的Windows Mixed Reality体验，但仍在跟踪一些已知问题。 如果发现其他人， [请提供反馈](/windows/mixed-reality/give-us-feedback)。

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>更新后
在应用程序上使用 Windows 10 2018 年 10 月更新 时，HoloLens：
* **从通知启动** 应用时，应用最终可能会以登录循环结束 – 某些需要登录的应用在从通知启动时最终可能会以无限登录循环结束。 例如，从安装中心安装 Microsoft 公司门户应用，然后从安装完成通知Microsoft Store启动后，可能会发生这种情况。
* 应用 **登录** 页可以使用空白页完成 - 在某些情况下，当应用程序上显示登录提示时，登录页不会关闭，而是显示一个空白的 (黑色) 页。 可以关闭空白页或将其移动，以在下方发现应用程序。 例如，在从应用注册 MDM 期间登录时设置发生这种情况。 

## <a name="provide-feedback-and-report-issues"></a>提供反馈并报告问题

请使用 反馈中心 或 HoloLens 电脑上的[Windows 10 应用](/windows/mixed-reality/give-us-feedback)提供反馈并报告问题。 使用 反馈中心可确保包含所有必要的诊断信息，以帮助我们的工程师快速调试和解决问题。

>[!NOTE]
>请务必接受提示，询问你是否希望反馈中心 Documents 文件夹， (系统提示时选择"是) 。 

## <a name="prior-release-notes"></a>以前的发行说明

* [发行说明 - 2018 年 4 月](release-notes-april-2018.md)
* [发行说明 - 2017 年 10 月](release-notes-october-2017.md)
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另请参阅
* [沉浸式头戴显示设备 (外部链接) ](./troubleshooting-windows-mixed-reality.md)
* [HoloLens外部 (支持) ](https://support.microsoft.com/products/hololens)
* [安装工具](/windows/mixed-reality/develop/install-the-tools)
* [给我们提供反馈](/windows/mixed-reality/give-us-feedback)