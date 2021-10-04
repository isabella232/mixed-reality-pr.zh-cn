---
title: 软件概述和发布历史记录
description: 概述适用于设备、沉浸式头戴显示设备Windows Mixed Reality的主要软件组件及其发行历史记录。
author: qianw211
ms.author: v-qianwen
ms.date: 09/30/2021
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 软件组件， 发行历史记录， 发行说明， 版本历史记录
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: e20b2075e45620a7533dbb2d369d00e73b98f9c7
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436625"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Mixed Reality 软件概述和版本历史记录

## <a name="introduction-to-mixed-reality-software"></a>混合现实软件简介

Windows Mixed Reality由以下主要软件组件组成：

1. **混合现实门户**，它提供主要Windows Mixed Reality体验
    * 在 Windows 10 版本 1709 和 1803 中，混合现实门户 是通过 Windows 更新更新的 Windows 10 操作系统的关键组件。
    * 在 Windows 10 1809 及更高版本中，混合现实门户应用更新Microsoft Store更新。
    * 在 Windows 11 版本 21H2 中。
2. 混合 **现实按需功能** 包 (FOD) ，在 混合现实门户 首次运行时自动下载并安装。 有关 FOD 包的信息，请参阅 [此处](/windows/application-management/manage-windows-mixed-reality)
3. 混合 **现实头戴显示** 设备驱动程序和运动控制器驱动程序（也称为 HoloLens 传感器驱动程序）是使 Windows Mixed Reality 头戴显示设备能够与 Windows Mixed Reality。 首次插入混合现实头戴显示设备时，Windows更新会自动下载并安装此设备，并定期通过 Windows 更新
4. 混合现实运动控制器模型驱动程序包含混合现实运动控制器的 3D 模型和第三方混合现实体验所需的模型。 首次将混合现实运动控制器配对到电脑时，系统会自动下载并Windows"更新"，然后通过 Windows 更新
5. **Windows 10版本 1709** (Fall Creator 的 Update) 或更高版本包含支持更新的关键 OS 组件Windows Mixed Reality

在 SteamVR Windows Mixed Reality应用程序需要以下软件：

6. **SteamVR，** 由流泵公司开发和维护，可在 Steam 上启用虚拟现实应用和游戏。 可在[此处](https://go.microsoft.com/fwlink/?linkid=862788)找到详细信息。
7. SteamVR **Windows Mixed Reality，** 用于将 SteamVR 与 Windows Mixed Reality。 有关此组件的信息，请参阅适用于[SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) Windows Mixed Reality页

管理 Windows Mixed Reality头戴显示设备：

8. 设备 **助理应用**（由每个头戴显示设备制造商开发和维护）提供对头戴显示设备Windows Mixed Reality简介。 在具有内置 蓝牙 功能的设备头戴显示设备上，设备助理应用支持将运动控制器还原到其工厂蓝牙配对。 某些头戴显示 (如 Samsung Odyssey 和 Samsung Odyssey+) 还使用设备助理应用提供头戴显示设备制造商提供的头戴显示设备固件更新。 第一次插入头戴显示设备时，会自动下载此应用，可在"开始Windows菜单中找到。

## <a name="windows-11-release-notes---october-2021"></a>Windows 11 发行说明 - 2021 年 10 月

### <a name="infinite-expanse"></a>Infinite Expanse

<img src="images\infinite-expanse-win11.png" alt="The Infinite Explanse environment">

<br>

* 新的虚拟家庭环境Windows Mixed Reality设备，其范围和大小显著缩减，简化为单阶段，而不是功能更丰富的House。 
* Infinite Expanse 旨在解决客户对资源消耗较少的虚拟家庭环境的长期请求，使客户能够利用其游戏和体验获得最佳性能。 
* 可在"位置"菜单中的"固定面板"中 **找到** 此新的虚拟 **主页** 环境。 

### <a name="steamvr-boot-with-mixed-reality-portal-launch"></a>带启动的 SteamVR 混合现实门户启动

* 新设置可用于在 WMR 启动时自动启动 SteamVR，从而绕过 WMR 主空间并直接跳转到 SteamVR。
   * 此新设置可在"混合现实"设置"启动和桌面">自动启动"下的 >**应用中找到**。 
    
### <a name="new-startup-experience-settings"></a>新的启动体验设置

* 新设置可用于通过提高对启动时间的控制级别来更好地配置混合现实门户体验。
* 现在，可以控制设备混合现实门户激活状态传感器时是否启动虚拟桌面应用，以及虚拟桌面应用的打开方式。
* 可以在"混合现实""启动设置桌面"下的 >**应用中找到这些新设置**
    * 切换以在 HMD 插件上启动 MRP。
    * 在检测到存在时切换以启动 MRP。
    * 在桌面应用焦点上切换"打开桌面应用"。

### <a name="prior-release-notes"></a>以前的发行说明

* [发行说明 - 2020 年 5 月](release-notes-may-2020.md)
* [发行说明 - 2019 年 5 月](release-notes-may-2019.md)
* [发行说明 - 2018 年 10 月](release-notes-october-2018.md)
* [发行说明 - 2018 年 4 月](release-notes-april-2018.md)
* [发行说明 - 2017 年 10 月](release-notes-october-2017.md)
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>混合现实头戴显示设备与运动控制器驱动程序发行历史记录 ###

此驱动程序通过更新自动下载Windows安装，但下载链接是内联提供的：

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 2004 (2020 年 5 月更新)  ####

   | 版本          | 发布日期          | 主要更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 2021 年 3 月 23 日  | 与 Windows 10 版本 1903 及更高版本兼容。<br/><ul><li>更新 HP Reverb G2 的隐藏区域网格的安装顺序，以便与其他头戴显示设备保持一致。</li><li>HP Reverb G2 头戴显示设备视觉对象质量改进。</li><li>Windows Mixed Reality头戴显示设备平台和可靠性改进。</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 2020 年 12 月 10 日  | 与 Windows 10 版本 1903 及更高版本兼容。<br/><ul><li>HP 控制器的新控制器固件，用于解决某些控制器具有无法正常工作的触发器的问题。</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 2020 年 10 月 8 日  | 与 Windows 10 版本 1903 及更高版本兼容。<br/><ul><li>对 HP Reverb G2、HP Omnicept 和新的 HP 控制器的官方支持。</li><li>对 HP Reverb 和 Samsung Odyssey+ 头戴显示设备进行次要显示更正。  (OS 内部版本 [19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) 或更高版本或 OS 内部版本 [18362.1110 和 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) 或更高版本) 。</li><li>改进了计算机电源状态从睡眠状态转换，以减少 SWW 1-4 错误。</li><li>Windows Mixed Reality头戴显示设备平台的次要修复和可靠性改进。|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 2020 年 5 月 7 日      | 与 Windows 10 版本 1903 及更高版本兼容。<br/><ul><li>Windows Mixed Reality头戴显示设备平台的次要修复和可靠性改进。</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10版本 1903 (2019 年 5 月更新)  ####

   | 版本          | 发布日期          | 主要更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 2019 年 10 月 14 日      | 与 Windows 10 版本 1809 及更高版本兼容。<br/><ul><li>Windows Mixed Reality头戴显示设备平台次要修复。</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 2019 年 6 月 24 日      | 与 Windows 10 版本 1809 及更高版本兼容。<br/><ul><li>Windows Mixed Reality睡眠计算机和电源状态转换方面改进头戴显示设备平台和可靠性。</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 2019 年 5 月 1 日      | 与 Windows 10 版本 1809 及更高版本兼容。<br/><ul><li>包含适用于 2017 Acer、Asus、Dell、且 Hp、Lenovo 和 Medion Windows Mixed Reality更新。 此固件更新提高了头戴显示与某些图形适配器或图形驱动程序的兼容性和可靠性。</li><li>Windows Mixed Reality头戴显示设备平台和可靠性改进</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10版本 1803 (2018 年 4 月更新) 和版本 1809 (2018 年 10 月更新)  ####

   | 版本          | 发布日期          | 主要更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2019 年 1 月 2 日      | 与 Windows 10 1803 及更高版本兼容。<br/><ul><li>头戴显示设备跟踪抖动和抖动修复</li><li>闪光灯模式可靠性修复</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 2018 年 10 月 1 日      | 适用于 Windows 10 版本 1809 的驱动程序的初始公共Windows 10 版本 1809。<br/>与 Windows 10 1803 及更高版本兼容。<br/><ul><li>在Windows Mixed Reality中启用新功能，例如Windows 10 版本 1809</li><li>头戴显示设备跟踪和可靠性改进</li><li>运动控制器跟踪和性能改进</li><li>USB 性能和改进</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 2018 年 4 月 27 日      | 适用于 Windows 10 版本 1803 的驱动程序的初始公共版本<br/> <ul><li>头戴显示设备跟踪和可靠性改进</li><li>运动控制器跟踪和性能改进</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10版本 1709 (Fall Creators Update)  ####

   | 版本          | 发布日期          | 主要更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 2018 年 2 月 6 日    | <ul><li>正式支持 3Glasses 的中微 S2 混合现实头戴显示设备</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 2017 年 12 月 19 日   | <ul><li>解决导致某些电脑出现问题 *的* HID 问题错误代码 2181038087-7</li><li>各种稳定性和可靠性修复</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 2017 年 12 月 5 日    | <ul><li>改进了头戴显示设备跟踪</li><li>运动控制器触摸板响应能力改进</li><li>解决驱动程序安装有时可能失败的问题</li><li>各种稳定性和可靠性修复</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 2017 年 11 月 21 日   | <ul><li>解决了使用期间导致头戴显示有时呈黑色的问题</li><li>解决了有时导致运动控制器消失的问题</li><li>Dell Visor 头戴显示设备的存在传感器性能改进</li><li>各种稳定性和可靠性修复</li></ul> |
   | 10.0.16299.1036  | 2017 年 11 月 7 日    | <ul><li>运动控制器引发运动改进：<ul><li>现在，当位置准确度为近似值时，将正确报告速度，因此现在可以在头部后面抛出！</li><li>有关引发的示例代码，可在此处的"ThrowingStarter"unity [包中找到](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)。 打开引发场景以开始</li></ul></li><li>改进了运动控制器电池报告</li><li>各种稳定性和可靠性修复</li></ul> |
   | 10.0.16299.1012  | 2017 年 10 月 17 日    | 驱动程序的初始公共版本                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>混合现实运动控制器模型驱动程序发布历史记录 ###

此驱动程序也会自动下载并安装Windows更新，但下载链接是内联提供的：

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 2004 (2020 年 5 月更新) 

| 版本          | 发布日期          | 主要更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 2020 年 9 月 16 日      | 新的 HP 运动控制器驱动程序的初始公共版本。 与 Windows 10 版本 1903 及更高版本兼容。 此驱动程序仅与新的 HP 运动控制器兼容。  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10版本 1803 (2018 年 4 月更新) 和版本 1809 (2018 年 10 月更新)  ####

   | 版本          | 发布日期          | 主要更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 2018 年 10 月 1 日      | 适用于 Windows 10 版本 1809 的驱动程序的初始公共Windows 10 版本 1809。 与 Windows 10 1803 及更高版本兼容。  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 2018 年 4 月 17 日      | 适用于 Windows 10 版本 1803 的驱动程序的初始公共版本。  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10版本 1709 (Fall Creators Update)  ####

   | 版本          | 发布日期          | 主要更改                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 2017 年 10 月 17 日    | 驱动程序的初始公共版本                          |

### <a name="mixed-reality-portal-release-history"></a>混合现实门户发布历史记录 ###

在 Windows 10 版本 1809 及更高版本中[，混合现实门户](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)应用更新Microsoft Store更新。

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10 版本 1809及更高版本 ####

   | 版本            | 发布日期          | 主要更改                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 2021 年 6 月 8 日          | <ul><li>为常见头戴显示设备错误获取帮助应用添加故障排除链接。</li><li>解决了在初始设置过程中可能会跳过头戴显示设备配套应用的问题。</li><li>使用高分辨率头戴显示设备的其他信息更新系统要求页。</li><li>使用新视觉对象更新初始屏幕和登陆页面。</li></ul>  |
   | 2000.21041.1051.0  | 2021 年 4 月 26 日        | <ul><li>更新应用程序的应用混合现实门户。</li></ul>  |
   | 2000.20111.1381.0  | 2020 年 12 月 10 日     | <ul><li>更新 混合现实门户 的登陆混合现实门户。</li><li>减少固件更新期间出现头戴显示设备连接错误。 </li></ul>  |
   | 2000.20071.1133.0  | 2020 年 8 月 5 日        | <ul><li>支持 [OpenXR](/windows/mixed-reality/openxr) 暂停预览窗口。</li></ul>  | 
   | 2000.20041.1212.0  | 2020 年 5 月 11 日          | <ul><li>解决导致 15-5 错误不一致的计时问题。</li><li>改进了对运行Windows Mixed Reality Internet 连接的支持。</li><li>改进了对通过安装程序控制器 配对 **运动控制器的支持**。</li></ul>  | 
   | 2000.20031.1202.0  | 2020 年 4 月 14 日        | <ul><li>支持注册有关此服务的信息、提示Windows Mixed Reality。</li></ul>  | 
   | 2000.20011.1312.0  | 2020 年 2 月 11 日     | <ul><li>通过 2019 年 5 月更新改进了对在设备上使用 [OpenXR](/windows/mixed-reality/openxr) 的应用程序的支持。</li><li>解决辅助功能和键盘焦点问题</li></ul>  | 
   | 2000.19101.1211.0  | 2019 年 11 月 11 日     | <ul><li>解决阻止切换房间边界视觉对象的问题。</li><li>解决了在房间边界设置过程中阻止你将头戴显示设备居中的问题。</li></ul>  | 
   | 2000.19081.1301.0  | 2019 年 9 月 23 日    | <ul><li>解决了出现硬件问题的头戴显示设备显示错误错误消息的问题。 以前版本上收到 1-4 错误代码的用户现在可能会收到更具体的设备状态错误代码。</li></ul>  |
   | 2000.19071.1302.0  | 2019 年 8 月 13 日     | <ul><li>支持在具有 2019 年 5 月更新的设备上使用 [OpenXR](/windows/mixed-reality/openxr) 的应用程序。</li></ul>  | 
   | 2000.19061.1011.0  | 2019 年 7 月 16 日         | <ul><li>支持使用 JSON 配置选项自定义应用行为。 有关详细信息，请参阅使用 Windows Mixed Reality[进行基于位置的娱乐](/windows/mixed-reality/location-based-experiences#setup)设置。</li></ul>  | 

### <a name="steamvr-release-history"></a>SteamVR 发行历史记录 ###

可在此处找到 SteamVR 的便笺： [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality SteamVR 发行历史记录 ###

有关 SteamVR 组件Windows Mixed Reality发行说明，可在此处找到：[http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
