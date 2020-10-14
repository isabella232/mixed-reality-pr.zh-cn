---
title: Mixed Reality 软件概述和版本历史记录
description: 概述 Windows Mixed Reality 的主要软件组件及其发行历史记录
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，软件组件，发布历史记录，发行说明，版本历史记录
appliesto:
- Windows 10
ms.openlocfilehash: 76a913ae5890c908dda4e25d5b5c21554fdae7f0
ms.sourcegitcommit: 9c88703a832fb8ca8476e808499d06239ea5d2cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "92011428"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Mixed Reality 软件概述和版本历史记录

## <a name="introduction-to-mixed-reality-software"></a>混合现实软件简介

Windows Mixed Reality 包含以下主要软件组件：

1. **混合现实门户**，提供主要的 Windows Mixed reality 体验
    * 在 Windows 10 中，版本1709和1803，混合现实门户是 Windows 10 操作系统的关键组件，并通过 Windows 更新更新。
    * 在 Windows 10 中，1809和更高版本的混合现实门户都通过 Microsoft Store 应用进行更新。
2. **混合现实功能点播包** (FOD) ，在混合现实门户首次运行期间自动下载和安装。 可在[此处](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)找到有关 FOD 包的详细信息
3. **混合现实耳机和运动控制器驱动**程序（也称为 HoloLens 传感器驱动程序）是允许 Windows mixed reality 耳机使用 Windows mixed reality 的关键驱动程序包。 这会在首次连接混合现实耳机时通过 Windows 更新自动下载和安装，并通过 Windows 更新定期更新
4. **混合现实运动控制器型号驱动程序**包含混合现实运动控制器的3d 模型，以及第三方混合现实体验所需的模型。 这会在你首次将混合现实运动控制器配对到电脑时通过 Windows 更新自动下载和安装，并通过 Windows 更新进行更新。
5. **Windows 10 版本 1709 (秋季创建者的更新) 或更新版本** 包含支持 Windows Mixed Reality 的关键操作系统组件和技术

此外，在 SteamVR 中使用 Windows Mixed Reality 需要以下软件：

6. **SteamVR**，由阀门公司开发和维护，可在流上启用虚拟现实应用和游戏。 可在[此处](https://go.microsoft.com/fwlink/?linkid=862788)找到详细信息。
7. SteamVR 组件的 **Windows Mixed reality** ，它将 SteamVR 与 Windows mixed reality 桥接。 有关此组件的详细信息，请参阅 [Windows Mixed Reality For SteamVR 页。](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

管理 Windows Mixed Reality 耳机：

8. 每个耳机制造商开发和维护的 **设备附属应用程序**提供了 Windows Mixed Reality 耳机简介。 在带有内置蓝牙功能的耳机上，设备辅助应用允许将运动控制器还原到工厂的蓝牙配对。 某些耳机 (例如 Samsung 太空和 Samsung 太空 +) 还使用设备配套应用从耳机制造商提供耳机固件更新。 首次连接耳机时，会自动下载此应用，并且可在 Windows "开始" 菜单中找到。

## <a name="windows-10-release-notes---may-2020"></a>Windows 10 发行说明-5 月2020

**Windows 10 可能2020更新 (v2004) **包含 Windows mixed REALITY (VR) 耳机的新功能，例如在混合现实总部启动 Win32 应用程序的功能。 HoloLens (第一代) 提供 (LTS) 的长期服务，每月发布服务更新。

若要更新到适用于 Windows Mixed Reality 的 PC 上的最新版本沉浸式 (VR) 耳机，请打开 " **设置** " 应用，中转到 " **更新 & 安全性**"，然后选择 " **检查更新** " 按钮。 在 Windows 10 电脑上，你还可以使用[windows media 创建工具](https://www.microsoft.com/software-download/windows10)手动安装**Windows 10 2020 更新**。

**最新版本的桌面**： Windows 10 v2004 (10.0.19041.264) 

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沉浸式耳机更新

#### <a name="introducing-the-new-microsoft-edge"></a>推出新的 Microsoft Edge
如前所述 [，我们](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge)已在 Windows Mixed Reality 中使用新的 Microsoft Edge 浏览器进行了更好的支持。 新的 Microsoft Edge 采用 Chromium 开源项目为客户创建更好的 web 兼容性，并为所有 web 开发人员创建更少的 web 兼容性。 它还支持 WebXR，这是用于创建用于 VR 耳机的沉浸式 web 体验的新标准，而不是 WebVR。

#### <a name="improved-settings-for-wmr"></a>改进的 WMR 设置
感谢你的反馈，我们已添加并阐明了耳机显示页面上的设置：

* 更改这些设置的**视觉质量**只会影响 (Cliff 房子和 Skyloft) 的混合现实家用环境：

* **调整混合现实中的详细程度和质量质量** -这将更改我们在本主页中使用的一些渲染影响。 特别是，当你将此设置从 "低" 更改为 "高" 时，不同材料 (木材、具体 ) 的视觉质量将会缩放。

* **更改应用程序窗口分辨率** -默认情况下，在主启动的大多数2d 窗口均以720p 分辨率启动。 尽管可以在垂直方向上手动 & 调整其大小，但你也可以选择让它们全都以1080p 的方式启动。 以前，此选项在视觉质量下作为非常高的 (beta) 选项提供。 我们已将其正确地拆分为单独的设置。

* **体验选项** -这些选项调整了混合现实体验，降低了硬件可能会因硬件而不受限制的 90 fps 而降低的负载。 您可以选择显式启用或禁用这些附加设置，或者选择 "让 Windows 决定" 并让试探法继续决定何时切换这些设置。

* **解决方法** ：如果你有高分辨率的耳机（如 HP 回音），我们支持以其本机分辨率运行，或者出于性能原因，降低分辨率。 先前的耳机（如 Samsung 太空和太空 +）仅支持单一分辨率，因此你将无法在这些耳机上更改此设置。

* **帧速率** -你现在可以手动设置耳机显示的帧速率，或继续允许 Windows 使用其试探法来确定是否更适合 60 hz 或 90 Hz。

* **校准** -与之前一样，你可以调整 IPD (interpupillary 距离) 如果你的耳机支持。

* **输入切换** -切换输入焦点切换 (Win + Y) 行为自动 (基于状态传感器反馈) 还是手动。

#### <a name="new-cortana-app"></a>新建 Cortana 应用
Windows 的这一更新包括最新版本的 Cortana 应用程序，该应用程序目前仅提供英语版本，不再支持某些特定于混合现实的命令，例如 "拍摄照片" 和 "拍摄视频"。 你仍可以使用新 Cortana 来启动应用，并且它还支持新的工作效率重点命令，如 "我的下一会议是什么时候？" 或 "发送一封电子邮件到 <name> 我的最晚运行。"
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>19041.546 年 10 2020 月发布的 (中提供了其他更新) 
此桌面每月服务更新包括适用于 Windows Mixed Reality 设备的下列更改： 
* 在 Windows Mixed Reality (HMD) 中减少扭曲和 aberrations。 
* 添加了对即将推出的 HP Windows Mixed Reality 运动控制器的支持。 
* 在某些情况下，如果无法实现90Hz，则将 Windows Mixed Reality 中90Hz 刷新速率设置的行为更改为不再自动切换回60Hz。 

#### <a name="please-help-us-improve"></a>请帮助我们改进！
我们会不断改进兼容性。  如果在 Windows Mixed Reality 中发现你最喜欢的经典 Win32 应用程序不能正常工作，请通过我们的 [反馈中心](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)提交反馈。

### <a name="prior-release-notes"></a>以前的发行说明

* [发行说明-5 月2019](release-notes-may-2019.md)
* [发行说明 - 2018 年 10 月](release-notes-october-2018.md)
* [发行说明-2018 年4月](release-notes-april-2018.md)
* [发行说明 - 2017 年 10 月](release-notes-october-2017.md)
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>混合现实耳机和运动控制器驱动程序发行历史记录 ###

此驱动程序通过 Windows 更新自动下载和安装，但会以内联方式提供下载链接：

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 版本 2004 (2020 更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 2020年10月8日  | 与 Windows 10 版本1903和更高版本兼容。<br/><ul><li>HP 回音 G2、HP Omnicept 和新 HP 控制器的官方支持。</li><li>HP 回音和 Samsung 太空 + 耳机的轻微显示更正。  (要求 [Os 版本 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) 或更高版本 [，或者操作系统版本18362.1110 和 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) 或更高版本) 。</li><li>改善计算机电源状态从睡眠转换到减少 SWW 1-4 错误。</li><li>Windows Mixed Reality 耳机平台辅助修补程序和可靠性改进。|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 5月7日，2020      | 与 Windows 10 版本1903和更高版本兼容。<br/><ul><li>Windows Mixed Reality 耳机平台辅助修补程序和可靠性改进。</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10 版本 1903 (2019 更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 2019年10月14日      | 与 Windows 10 版本1809和更高版本兼容。<br/><ul><li>Windows Mixed Reality 耳机平台次要修补程序。</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 6月24日，2019      | 与 Windows 10 版本1809和更高版本兼容。<br/><ul><li>Windows Mixed Reality 耳机平台和有关睡眠计算机和电源状态转换的可靠性改进。</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 2019 年 5 月 1 日      | 与 Windows 10 版本1809和更高版本兼容。<br/><ul><li>包含 2017 Acer，Asus，Dell，Fujitsu，HP，联想和 Medion Windows Mixed Reality 耳机的固件更新。 此固件更新通过某些图形适配器和/或图形驱动程序提高耳机显示的兼容性和可靠性。</li><li>Windows Mixed Reality 耳机平台和可靠性改进</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10 版本 1803 (2018 更新) 和版本 1809 (10 月2018更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2019年1月2日      | 与 Windows 10 版本1803和更高版本兼容。<br/><ul><li>耳机跟踪抖动和断断续续修补程序</li><li>闪光灯模式可靠性修补程序</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 10月1日，2018      | 适用于 Windows 10 版本1809的驱动程序的初始公开发行版。<br/>与 Windows 10 版本1803和更高版本兼容。<br/><ul><li>启用 Windows 10 版本1809中的新 Windows Mixed Reality 功能，如闪光灯模式</li><li>耳机跟踪和可靠性改进</li><li>动作控制器跟踪和性能改进</li><li>USB 性能和改进</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 4月27日，2018      | 适用于 Windows 10 版本1803的驱动程序的初始公共版本<br/> <ul><li>耳机跟踪和可靠性改进</li><li>动作控制器跟踪和性能改进</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10 版本 1709 (秋季创意者更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 2018年2月6日    | <ul><li>官方支持 3Glasses Blubur S2 Mixed Reality 耳机</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 2017年12月19日   | <ul><li>解决了 *导致某些电脑上出现错误代码* 2181038087-7 的 HID 问题</li><li>各种稳定性和可靠性修补程序</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 2017年12月5日    | <ul><li>改善了耳机跟踪</li><li>动作控制器触摸板响应能力改进</li><li>解决驱动程序安装有时可能会失败的问题</li><li>各种稳定性和可靠性修补程序</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 2017年11月21日   | <ul><li>解决了在使用期间导致耳机显示出现黑色的问题</li><li>解决了有时会导致运动控制器消失的问题</li><li>为 Dell 面板耳机显示传感器性能改进</li><li>各种稳定性和可靠性修补程序</li></ul> |
   | 10.0.16299.1036  | 2017年11月7日    | <ul><li>运动控制器引发 mechanic 改进：<ul><li>当位置准确性为近似值时，速度现在会正确报告，因此你现在可以在你的打印头后面进行操作！</li><li>可在 [此处](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)的 "ThrowingStarter" unity 包中找到引发的示例代码。 打开引发场景，开始工作</li></ul></li><li>改善了运动控制器电池报告</li><li>各种稳定性和可靠性修补程序</li></ul> |
   | 10.0.16299.1012  | 2017年10月17日    | 驱动程序的初始公共版本                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>混合现实运动控制器型号驱动程序发行历史记录 ###

此驱动程序还会通过 Windows 更新自动下载和安装，但会以内联方式提供下载链接：

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 版本 2004 (2020 更新) 

| 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 2020年9月16日      | 新 HP 运动控制器的驱动程序的初始公开发行版。 与 Windows 10 版本1903和更高版本兼容。 此驱动程序只与新的 HP 运动控制器兼容。  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10 版本 1803 (2018 更新) 和版本 1809 (10 月2018更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 10月1日，2018      | 适用于 Windows 10 版本1809的驱动程序的初始公开发行版。 与 Windows 10 版本1803和更高版本兼容。  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 2018年4月17日      | 适用于 Windows 10 版本1803的驱动程序的初始公开发行版。  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10 版本 1709 (秋季创意者更新)  ####

   | 版本          | 发布日期          | 重大更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 2017年10月17日    | 驱动程序的初始公共版本                          |

### <a name="mixed-reality-portal-release-history"></a>混合现实门户版本历史记录 ###

在 Windows 10 中，1809和更高版本的 [混合现实门户](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) 都通过 Microsoft Store 应用进行更新。

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10 版本1809及更高版本 ####

   | 版本            | 发布日期          | 重大更改                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.20071.1133.0  | 2020 年 8 月 5 日        | <ul><li>支持 [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) 以暂停预览窗口。</li></ul>  | 
   | 2000.20041.1212.0  | 2020 年 5 月 11 日          | <ul><li>解决导致15-5 错误的计时问题。</li><li>改进了对运行 Windows Mixed Reality 而无 internet 连接的支持。</li><li>通过 **设置控制器**改进了对配对运动控制器的支持。</li></ul>  | 
   | 2000.20031.1202.0  | 2020 年 4 月 14 日        | <ul><li>支持注册有关 Windows Mixed Reality 的信息、提示和产品。</li></ul>  | 
   | 2000.20011.1312.0  | 2020 年 2 月 11 日     | <ul><li>改进了对使用 [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) 在设备上使用的应用程序的支持，可能为2019更新。</li><li>解决辅助功能和键盘焦点问题</li></ul>  | 
   | 2000.19101.1211.0  | 2019 年 11 月 11 日     | <ul><li>解决了阻止你切换空间边界视觉对象的问题。</li><li>解决了在设置空间边界期间阻止你中心戴显示的问题。</li></ul>  | 
   | 2000.19081.1301.0  | 2019 年 9 月 23 日    | <ul><li>解决了耳机遇到硬件问题的问题显示了错误消息。 在以前的版本上收到1-4 错误代码的用户现在可能会收到有关其设备状态的更具体的错误代码。</li></ul>  |
   | 2000.19071.1302.0  | 2019年8月13日     | <ul><li>支持在具有 5 2019 更新的设备上使用 [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) 的应用程序。</li></ul>  | 
   | 2000.19061.1011.0  | 2019 年 7 月 16 日         | <ul><li>支持 JSON 配置选项以自定义应用行为。 有关详细信息，请参阅 https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup 。</li></ul>  | 

### <a name="steamvr-release-history"></a>SteamVR 发行历史记录 ###

可在此处找到 SteamVR 的阀门发行说明： [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>SteamVR 发行历史记录的 Windows Mixed Reality ###

可在此处找到 Windows Mixed Reality for SteamVR 组件的发行说明： [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
