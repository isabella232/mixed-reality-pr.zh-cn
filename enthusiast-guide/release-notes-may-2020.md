---
title: 发行说明 - 2020 年 5 月
description: 随时了解 2020 Windows Mixed Reality 2020 年 5 月更新Windows 10发行说明。
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: 发行说明， 版本， windows 10， 内部版本， 19h1， os， 2020 年 5 月
ms.openlocfilehash: 462fcbfa10cfff8df23c970fd54ee0754a4d9472
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439158"
---
# <a name="windows-10-release-notes---may-2020"></a>Windows 10发行说明 - 2020 年 5 月

Windows 10 **2020 年 5 月更新 (v2004)** 包括 Windows Mixed Reality (VR) 头戴显示设备新功能，例如能够在 混合现实主页 中启动 Win32 应用程序。 HoloLens (第一代) LTS (长期服务) ，每月发布一次服务更新。

升级到沉浸式 WINDOWS MIXED REALITY (VR) 头戴显示设备的最新电脑版本，打开 设置 > Update **& Security** 并选择"检查 **更新"。** 在 Windows 10 电脑上，还可使用 Windows 媒体创建工具 手动安装 Windows 10 **2020** 年 5 月 [更新](https://www.microsoft.com/software-download/windows10)。

**桌面版 ：Windows 10** v2004 (10.0.19041.264) 

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>适用于沉Windows Mixed Reality头戴显示设备的更新

### <a name="introducing-the-new-microsoft-edge"></a>新版 Microsoft Edge 简介

如前所述[，](/windows/mixed-reality/new-microsoft-edge)我们进行了更新，以更好地支持在 Windows Mixed Reality 中使用新的 Microsoft Edge 浏览器。 新的Microsoft Edge采用 Chromium 开放源代码项目，以为客户提供更好的 Web 兼容性，减少所有 Web 开发人员的 Web 碎片。 它还支持 WebXR，WebXR 是一种用于为 VR 头戴显示设备创建沉浸式 Web 体验的新标准，用于代理 WebVR。

### <a name="improved-settings-for-wmr"></a>改进了 WMR 设置

感谢你的反馈，我们在头戴显示页上添加了并阐明设置：

* **我的家的视觉质量** - 更改这些设置只会影响混合现实主页环境 (悬崖小屋和 Skyloft) ：

* **调整图像中效果的详细** 级别混合现实主页 - 这更改了一些呈现效果，会影响我们在主页中使用的效果。 具体而言，将此设置从低 (更改为高时，) 材料（如 (、具体等）的视觉质量会进行缩放。

* **更改应用窗口分辨率** - 默认情况下，在主页中启动大多数 2D 窗口都以 720 p 分辨率启动。 虽然可以在垂直方向上手动调整&大小，但也可以选择将它们全部以 1080p 启动。 以前，此选项在"视觉质量"下 (") ""非常高的 beta 版本"选项。 我们现在已适当地将拆分为单独的设置。

* **体验选项** - 这些选项调整混合现实体验，以减少硬件可能难以与不受限制的 90 fps 保持一致的系统负载。 可以显式启用或禁用这些附加设置，或选择"让Windows决定，让启发式方法继续决定何时启用和禁用这些设置。

* **分辨率** - 如果你有像 HP Reverb 这样的高分辨率头戴显示设备，我们支持以本机分辨率运行它，或出于性能原因以降低分辨率运行它。 早期的头戴显示设备（如 Samsung Odyssey 和 Odyssey+）仅支持单个分辨率，因此不能在这些头戴显示设备上更改此设置。

* **帧** 速率 - 现在可以手动设置头戴显示设备显示帧速率，或继续让 Windows 使用其启发来确定 60 Hz 或 90 Hz 是否更合适。

* **校准** - 与之前一样，如果头戴显示设备 (，) 设备之间的间距调整 IPD。

* **输入切换** - 将输入焦点切换 (Win+Y) 行为切换为 (状态传感器反馈或手动) 自动切换。

### <a name="new-cortana-app"></a>新建Cortana应用

此更新Windows包括最新版本的 Cortana 应用，该应用目前仅适用于美国英语，不再支持某些混合现实特定命令，例如"拍照"和"观看视频"。 可以使用新的Cortana启动应用，它还支持以工作效率为中心的新命令，例如"下一个会议何时进行？" 或"向 \< name \> 我延迟运行的电子邮件发送"。
    
### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>19041.546 版中提供的其他更新 (2020 年 10 月发布) 

此桌面每月服务更新包括以下针对Windows Mixed Reality更改： 
* 减少 HMD 显示器Windows Mixed Reality HMD 显示器中的 (和) 。 
* 添加了对即将推出的 HP Windows Mixed Reality的支持。 
* 在某些情况下，如果无法达到 90 Hz，Windows Mixed Reality 中 90-Hz 刷新速率设置的行为将无法再自动切换回 60 Hz。 

### <a name="help-us-improve"></a>帮助我们改进！

我们不断寻求改进兼容性。  如果发现收藏的经典 Win32 应用程序在运行期间行为Windows Mixed Reality，请通过我们的[反馈中心。](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)

## <a name="prior-release-notes"></a>以前的发行说明

* [发行说明 - 2019 年 5 月](release-notes-may-2019.md)
* [发行说明 - 2018 年 10 月](release-notes-october-2018.md)
* [发行说明 - 2018 年 4 月](release-notes-april-2018.md)
* [发行说明 - 2017 年 10 月](release-notes-october-2017.md)
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>请参阅
* [沉浸式头戴显示设备 (外部链接) ](./troubleshooting-windows-mixed-reality.md)
* [HoloLens外部 (支持) ](https://support.microsoft.com/products/hololens)
* [安装工具](/windows/mixed-reality/develop/install-the-tools)
* [给我们提供反馈](/windows/mixed-reality/give-us-feedback)