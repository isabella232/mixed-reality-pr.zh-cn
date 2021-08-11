---
title: 软件概述和发布历史记录
description: 概述适用于设备、沉浸式头戴显示设备Windows Mixed Reality的主要软件组件及其发行历史记录。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、混合现实、虚拟现实、VR、MR、软件组件、发行历史记录、发行说明、版本历史记录
appliesto:
- Windows 10
ms.openlocfilehash: 51c13326d2ad8aebe164e64d0bfc380923a91d1be02cea840cec4addd062533f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219723"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Mixed Reality 软件概述和版本历史记录

## <a name="introduction-to-mixed-reality-software"></a>混合现实软件简介

Windows Mixed Reality由以下主要软件组件组成：

1. **混合现实门户**，它提供主要Windows Mixed Reality体验
    * 在 Windows 10 版本 1709 和 1803 中，混合现实门户 是通过 Windows 更新更新的 Windows 10 操作系统的关键组件。
    * 在 Windows 10 1809 及更高版本中，混合现实门户应用更新Microsoft Store更新。
2. 混合 **现实按需功能** 包 (FOD) ，在 混合现实门户 首次运行时自动下载并安装。 有关 FOD 包的信息，请参阅 [此处](/windows/application-management/manage-windows-mixed-reality)
3. 混合 **现实头戴显示** 设备驱动程序和运动控制器驱动程序（也称为 HoloLens 传感器驱动程序）是使 Windows Mixed Reality 头戴显示设备能够与 Windows Mixed Reality。 第一次插入混合现实头戴显示设备时，会自动通过 Windows Update 下载并安装它，并定期通过 Windows 更新
4. 混合现实运动控制器模型驱动程序包含混合现实运动控制器的 3D 模型和第三方混合现实体验所需的模型。 首次将混合现实运动控制器配对到电脑时，Windows更新自动下载并安装此控制器，并可通过 Windows 更新
5. **Windows 10版本 1709** (Fall Creator 的 Update) 或更高版本包含支持更新Windows Mixed Reality

在 SteamVR Windows Mixed Reality应用程序需要以下软件：

6. **SteamVR，** 由流泵公司开发和维护，可在 Steam 上启用虚拟现实应用和游戏。 可在[此处](https://go.microsoft.com/fwlink/?linkid=862788)找到详细信息。
7. 适用于 **Windows Mixed Reality的流式** 处理组件，用于将 SteamVR 与 Windows Mixed Reality。 有关此组件的信息，请参阅适用于[SteamVR Windows Mixed Reality页](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

管理 Windows Mixed Reality头戴显示设备：

8. 设备 **助理应用**（由每个头戴显示设备制造商开发和维护）提供对头戴显示设备Windows Mixed Reality简介。 在具有内置配对功能蓝牙头戴显示设备上，设备助理应用支持将运动控制器还原到其蓝牙配对。 某些头戴显示 (如 Samsung Odyssey 和 Samsung Odyssey+) 还使用设备助理应用提供头戴显示设备制造商提供的头戴显示设备固件更新。 第一次插入头戴显示设备时，会自动下载此应用，可在"开始Windows菜单中找到。

## <a name="windows-10-release-notes---may-2020"></a>Windows 10发行说明 - 2020 年 5 月

Windows 10 **2020 年 5 月更新 (v2004)** 包含 Windows Mixed Reality (VR) 头戴显示设备新功能，例如能够在 混合现实主页 中启动 Win32 应用程序。 HoloLens (第一代) LTS (长期服务) ，每月发布一次服务更新。

升级到沉浸式 WINDOWS MIXED REALITY (VR) 头戴显示设备的最新电脑版本，打开 设置 > Update **& Security** 并选择"检查 **更新"。** 在 Windows 10 电脑上，还可使用 Windows 10 媒体创建工具 手动安装 Windows 10 **202 Windows 0** 年 5 月 [更新](https://www.microsoft.com/software-download/windows10)。

**桌面版 ：Windows 10** v2004 (10.0.19041.264) 

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>适用于沉Windows Mixed Reality头戴显示设备的更新

#### <a name="introducing-the-new-microsoft-edge"></a>新版 Microsoft Edge 简介

如前所述[，](/windows/mixed-reality/new-microsoft-edge)我们进行了更新，以更好地支持在 Windows Mixed Reality 中使用新的 Microsoft Edge 浏览器。 新的Microsoft Edge采用Chromium开放源代码项目，以为客户提供更好的 Web 兼容性，减少所有 Web 开发人员的 Web 碎片。 它还支持 WebXR，WebXR 是一种用于为 VR 头戴显示设备创建沉浸式 Web 体验的新标准，用于代理 WebVR。

#### <a name="improved-settings-for-wmr"></a>改进了 WMR 设置

感谢你的反馈，我们在头戴显示页上添加了并阐明设置：

* **我的家的视觉质量** - 更改这些设置只会影响混合现实主页环境 (悬崖小屋 Skyloft) ：

* **调整图像中效果的详细** 级别混合现实主页 - 这会更改一些呈现效果，从而影响我们在主页中使用的效果。 具体而言，将此设置从低 (更改为高时，) 材料（如 (等）的视觉质量会进行缩放。

* **更改应用窗口分辨率** - 默认情况下，在主页中启动大多数 2D 窗口都以 720 p 分辨率启动。 虽然可以在垂直方向上手动调整&大小，但也可以选择将它们全部以 1080p 启动。 以前，此选项在"视觉质量"下 (") beta 版本"选项。 我们现在已适当地将拆分为单独的设置。

* **体验选项** - 这些选项调整混合现实体验，以减少硬件可能难以与不受限制的 90 fps 保持一致的系统负载。 可以显式启用或禁用这些附加设置，或选择"让Windows决定，让启发式方法继续决定何时启用和禁用这些设置。

* **分辨率** - 如果你有像 HP Reverb 这样的高分辨率头戴显示设备，我们支持以本机分辨率运行它，或者出于性能原因以降低分辨率运行它。 早期的头戴显示设备（如 Samsung Odyssey 和 Odyssey+）仅支持单个分辨率，因此不能在这些头戴显示设备上更改此设置。

* **帧** 速率 - 现在可以手动设置头戴显示设备帧速率，或继续让 Windows 使用其启发来确定 60 Hz 或 90 Hz 是否更合适。

* **校准** - 与之前一样，可以调整 IPD (（如果头戴显示设备) 支持）。

* **输入切换** - 将输入焦点切换 (Win+Y) 行为切换为 (状态传感器反馈或手动) 自动切换。

#### <a name="new-cortana-app"></a>新建Cortana应用

此更新Windows包括最新版本的 Cortana 应用，该应用目前仅适用于美国英语，不再支持某些混合现实特定命令，例如"拍照"和"观看视频"。 可以使用新的Cortana来启动应用，它还支持以工作效率为中心的新命令，例如"下一个会议何时进行？" 或"向 <name> 我延迟运行的电子邮件发送"。
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>19041.546 版中提供的其他更新 (2020 年 10 月发布) 

此桌面每月服务更新包括以下针对设备Windows Mixed Reality更改： 
* 减少 HMD 显示器Windows Mixed Reality HMD 显示器中的 (和) 。 
* 添加了对即将推出的 HP Windows Mixed Reality的支持。 
* 在某些情况下，如果无法达到 90 Hz，Windows Mixed Reality 中 90-Hz 刷新速率设置的行为将无法再自动切换回 60 Hz。 

#### <a name="help-us-improve"></a>帮助我们改进！

我们不断寻求改进兼容性。  如果发现收藏的经典 Win32 应用程序在运行期间行为Windows Mixed Reality，请通过我们的[反馈中心。](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)

### <a name="prior-release-notes"></a>以前的发行说明

* [发行说明 - 2019 年 5 月](release-notes-may-2019.md)
* [发行说明 - 2018 年 10 月](release-notes-october-2018.md)
* [发行说明 - 2018 年 4 月](release-notes-april-2018.md)
* [发行说明 - 2017 年 10 月](release-notes-october-2017.md)
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>混合现实头戴显示设备与运动控制器驱动程序发行历史记录 ###

此驱动程序通过 Windows 更新自动下载和安装，但下载链接是内联提供的：

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 2004 (2020 年 5 月更新)  ####

   | 版本          | 发布日期          | 主要更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 2021 年 3 月 23 日  | 与 Windows 10 版本 1903 及更高版本兼容。<br/><ul><li>更新 HP Reverb G2 的隐藏区域网格的排序顺序，以便与其他头戴显示设备保持一致。</li><li>HP Reverb G2 头戴显示设备视觉对象质量改进。</li><li>Windows Mixed Reality头戴显示设备平台和可靠性改进。</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 2020 年 12 月 10 日  | 与 Windows 10 版本 1903 及更高版本兼容。<br/><ul><li>HP 控制器的新控制器固件，用于解决某些控制器具有无法正常工作的触发器的问题。</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 2020 年 10 月 8 日  | 与 Windows 10 版本 1903 及更高版本兼容。<br/><ul><li>对 HP Reverb G2、HP Omnicept 和新的 HP 控制器的官方支持。</li><li>对 HP Reverb 和 Samsung Odyssey+ 头戴显示设备进行次要显示更正。  (OS [内部版本 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) 或更高版本或 OS 内部版本 [18362.1110 和 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) 或更高版本) 。</li><li>改进了计算机电源状态从睡眠状态转换，以减少 SWW 1-4 错误。</li><li>Windows Mixed Reality头戴显示设备平台的次要修复和可靠性改进。|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 2020 年 5 月 7 日      | 与 Windows 10 版本 1903 及更高版本兼容。<br/><ul><li>Windows Mixed Reality 耳机平台辅助修补程序和可靠性改进。</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10，版本 1903 (2019 更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 2019 年 10 月 14 日      | 与 Windows 10 版本1809和更高版本兼容。<br/><ul><li>Windows Mixed Reality 耳机平台辅助修补程序。</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 2019 年 6 月 24 日      | 与 Windows 10 版本1809和更高版本兼容。<br/><ul><li>围绕睡眠计算机和电源状态转换 Windows Mixed Reality 耳机平台和可靠性改进。</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 2019 年 5 月 1 日      | 与 Windows 10 版本1809和更高版本兼容。<br/><ul><li>包含 2017 Acer，Asus，Dell，Fujitsu，HP，联想和 Medion Windows Mixed Reality 耳机的固件更新。 此固件更新通过某些图形适配器或图形驱动程序提高耳机显示的兼容性和可靠性。</li><li>Windows Mixed Reality 耳机平台和可靠性改进</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10，版本 1803 (2018 更新) ，版本 1809 (10 月2018更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2019年1月2日      | 与 Windows 10 版本1803和更高版本兼容。<br/><ul><li>耳机跟踪抖动和断断续续修补程序</li><li>闪光灯模式可靠性修补程序</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 2018年10月1日      | Windows 10 版本1809的驱动程序的初始公开发行版。<br/>与 Windows 10 版本1803和更高版本兼容。<br/><ul><li>启用 Windows 10 版本1809中的新 Windows Mixed Reality 功能，如闪光灯模式</li><li>耳机跟踪和可靠性改进</li><li>动作控制器跟踪和性能改进</li><li>USB 性能和改进</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 2018 年 4 月 27 日      | 版本1803的 Windows 10 的驱动程序的初始公共版本<br/> <ul><li>耳机跟踪和可靠性改进</li><li>动作控制器跟踪和性能改进</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10，版本 1709 (秋季创建者更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 2018年2月6日    | <ul><li>官方支持 3Glasses Blubur S2 Mixed Reality 耳机</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 2017 年 12 月 19 日   | <ul><li>解决了 *导致某些电脑上出现错误代码* 2181038087-7 的 HID 问题</li><li>各种稳定性和可靠性修补程序</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 2017 年 12 月 5 日    | <ul><li>改善了耳机跟踪</li><li>动作控制器触摸板响应能力改进</li><li>解决驱动程序安装有时可能会失败的问题</li><li>各种稳定性和可靠性修补程序</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 2017年11月21日   | <ul><li>解决了在使用期间导致耳机显示出现黑色的问题</li><li>解决了有时会导致运动控制器消失的问题</li><li>为 Dell 面板耳机显示传感器性能改进</li><li>各种稳定性和可靠性修补程序</li></ul> |
   | 10.0.16299.1036  | 2017年11月7日    | <ul><li>运动控制器引发 mechanic 改进：<ul><li>当位置准确性为近似值时，速度现在会正确报告，因此你现在可以在你的打印头后面进行操作！</li><li>可在 [此处](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)的 "ThrowingStarter" unity 包中找到引发的示例代码。 打开引发场景，开始工作</li></ul></li><li>改善了运动控制器电池报告</li><li>各种稳定性和可靠性修补程序</li></ul> |
   | 10.0.16299.1012  | 2017 年 10 月 17 日    | 驱动程序的初始公共版本                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>混合现实运动控制器型号驱动程序发行历史记录 ###

此驱动程序还会通过 Windows 更新自动下载和安装，但会以内联方式提供下载链接：

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10，版本 2004 (2020 更新) 

| 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 2020年9月16日      | 新 HP 运动控制器的驱动程序的初始公开发行版。 与 Windows 10 版本1903和更高版本兼容。 此驱动程序只与新的 HP 运动控制器兼容。  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10，版本 1803 (2018 更新) ，版本 1809 (10 月2018更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 2018年10月1日      | Windows 10 版本1809的驱动程序的初始公开发行版。 与 Windows 10 版本1803和更高版本兼容。  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 2018 年 4 月 17 日      | 版本1803的 Windows 10 的驱动程序的初始公开发行版。  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10，版本 1709 (秋季创建者更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 2017 年 10 月 17 日    | 驱动程序的初始公共版本                          |

### <a name="mixed-reality-portal-release-history"></a>混合现实门户版本历史记录 ###

在 Windows 10 版本1809和更高版本中，[混合现实门户](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)通过 Microsoft Store 应用进行更新。

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10 版本1809和更高版本 ####

   | 版本            | 发布日期          | 重大更改                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 2021 年 6 月 8 日          | <ul><li>为常见耳机错误添加到获取帮助应用的故障排除链接。</li><li>解决了在初始安装过程中可能会跳过耳机设备辅助应用的问题。</li><li>更新 "系统要求" 页，其中包含高分辨率耳机的其他信息。</li><li>用新视觉对象更新初始屏幕和登录页。</li></ul>  |
   | 2000.21041.1051.0  | 2021年4月26日        | <ul><li>更新混合现实门户的应用图标。</li></ul>  |
   | 2000.20111.1381.0  | 2020年12月10日     | <ul><li>更新混合现实门户的登录页。</li><li>减少固件更新过程中的耳机连接错误。 </li></ul>  |
   | 2000.20071.1133.0  | 2020 年 8 月 5 日        | <ul><li>支持 [OpenXR](/windows/mixed-reality/openxr) 以暂停预览窗口。</li></ul>  | 
   | 2000.20041.1212.0  | 2020 年 5 月 11 日          | <ul><li>解决导致15-5 错误的计时问题。</li><li>改进了对不通过 internet 连接运行 Windows Mixed Reality 的支持。</li><li>通过 **安装控制器** 改进了对配对运动控制器的支持。</li></ul>  | 
   | 2000.20031.1202.0  | 2020 年 4 月 14 日        | <ul><li>支持注册 Windows Mixed Reality 的信息、提示和产品/服务。</li></ul>  | 
   | 2000.20011.1312.0  | 2020 年 2 月 11 日     | <ul><li>改进了对使用 [OpenXR](/windows/mixed-reality/openxr) 在设备上使用的应用程序的支持，可能为2019更新。</li><li>解决辅助功能和键盘焦点问题</li></ul>  | 
   | 2000.19101.1211.0  | 2019 年 11 月 11 日     | <ul><li>解决了阻止你切换空间边界视觉对象的问题。</li><li>解决了在设置空间边界期间阻止你中心戴显示的问题。</li></ul>  | 
   | 2000.19081.1301.0  | 2019 年 9 月 23 日    | <ul><li>解决了出现硬件问题的耳机显示错误消息的问题。 在以前的版本上收到1-4 错误代码的用户现在可能会收到有关其设备状态的更具体的错误代码。</li></ul>  |
   | 2000.19071.1302.0  | 2019 年 8 月 13 日     | <ul><li>支持在具有 5 2019 更新的设备上使用 [OpenXR](/windows/mixed-reality/openxr) 的应用程序。</li></ul>  | 
   | 2000.19061.1011.0  | 2019 年 7 月 16 日         | <ul><li>支持 JSON 配置选项以自定义应用行为。 有关详细信息，请参阅 https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup 。</li></ul>  | 

### <a name="steamvr-release-history"></a>SteamVR 发行历史记录 ###

可在此处找到 SteamVR 的阀门发行说明： [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>SteamVR 发行历史记录的 Windows Mixed Reality ###

SteamVR 组件 Windows Mixed Reality 的发行说明可在此处找到：[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
