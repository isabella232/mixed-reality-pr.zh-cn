---
title: 发行说明 - 2016 年 8 月
description: 随时了解 2016 年HoloLens日周年Windows 10发行说明。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、发行说明、os、平台、功能、商业套件
ms.openlocfilehash: 2cb6153877b27ce0e1260696447bd4c5c851c6f00a20a7889b855c5646e8871f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202451"
---
# <a name="release-notes---august-2016"></a>发行说明 - 2016 年 8 月

HoloLens团队正在倾听开发人员的反馈，Windows 会员计划确定工作优先级。 请[继续通过 反馈中心、](/windows/mixed-reality/give-us-feedback)开发人员[论坛](https://forums.hololens.com)和[Twitter 提供反馈 @HoloLens ](https://twitter.com/hololens)。 随着Windows 10周年更新，HoloLens团队很高兴为全息体验提供进一步改进。 在此更新中，我们侧重于企业请求的主要修复、改进和引入功能，这些功能在 Microsoft HoloLens Commercial Suite。

**最新版本：Windows** Holographic 2016 年 8 月更新 (**10.0.14393.0，Windows 10** 周年) 

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

若要 [更新到当前版本](/windows/mixed-reality/updating-hololens)，请打开 设置 *应用，* 转到"更新&*安全性*"，然后选择"检查 *更新"* 按钮。

## <a name="new-features"></a>新增功能

**附加到进程调试HoloLens** 现在支持附加到进程调试。 可以使用 Visual Studio 2015 Update 3 连接到正在运行的应用，HoloLens[开始调试它](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app)。 此操作无需从项目部署，Visual Studio部署。

**更新HoloLens Emulator** 我们还发布了最新版本的 HoloLens Emulator。

**游戏板支持** 现在可以将游戏板与 蓝牙 配对并使用HoloLens！ 新发布的 Xbox 无线控制器 S 蓝牙功能，可用于播放你最喜爱的支持游戏板的游戏和应用。 必须先[应用](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)控制器更新，然后才能将 Xbox 无线控制器 S 与 HoloLens。 [XInput](/windows/win32/xinput/xinput-game-controller-apis-portal)和 Windows 支持 Xbox[无线控制器 S。Gaming.Input](/uwp/api/Windows.Gaming.Input) API。 可以通过蓝牙访问更多控制器[Windows。Gaming.Input](/uwp/api/Windows.Gaming.Input) API。

## <a name="improvements-and-fixes"></a>改进和修复

我们正在与 Windows 10 周年更新的其余部分同步，因此，除了 HoloLens 特定修补程序之外，你还从 Windows 更新中收到所有良好信息，以提高平台可靠性和性能。 你的反馈受到高度重视，并优先处理版本中的修复。

我们改进了以下体验：
* 登录体验。
* 工作区加入。
* 设备电源状态转换的电源效率。
* 混合现实捕获的稳定性。
* 蓝牙可靠性
* 多应用方案中的全息影像持久性。

我们修复了以下问题：
* Visual Studio探查器与图形调试器无法连接。
* 设备&文件资源管理器中不会显示文档照片。
* 当光标置于应用栏上方时，应用栏可能会闪烁，同时处于"调整"模式。
* 在"调整"模式下，眼睛凝视点光标会逐渐变为 4 箭头光标。
* "你好Cortana播放音乐"不会启动Groove。
* 在上一次更新后，显示"转到主页"无法正确显示图钉面板。

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Microsoft HoloLens Commercial Suite

该Microsoft HoloLens Commercial Suite已准备好进行企业部署。 我们添加了一些来自早期业务合作伙伴 [的高度](/windows/mixed-reality/commercial-features) 请求的商业功能。

请联系本地Microsoft 帐户管理员购买Microsoft HoloLens Commercial Suite。

### <a name="key-commercial-features"></a>主要商业功能 

* 展台模式。 使用HoloLens展台模式，可以限制要运行的应用以启用演示或展示体验。<br>
  ![使用展台HoloLens，设备将直接启动到你选择的应用。](images/201608-kioskmode-400px.png)
* 适用于 HoloLens 的移动设备管理 (MDM)。 IT 部门可以使用 HoloLens 等解决方案同时管理多个 Microsoft Intune。 可以管理设置，选择要安装的应用，并设置根据组织需求定制的安全配置。<br>
  ![设备管理移动HoloLens跨多个设备提供企业级设备管理。](images/201608-enterprisemanagement-400px.png)
* 适用于企业的 Windows 更新。 对设备进行受控的操作系统更新，并支持长期服务分支。
* 数据安全。 在 HoloLens 上启用 BitLocker 数据加密，从而提供与任何其他 Windows 设备相同的安全保护级别。
* 工作访问。 组织中任何人都可以通过虚拟网络上的虚拟专用网络远程连接到HoloLens。 HoloLens 还可以访问需要凭据的 Wi-Fi 网络。
* 适用于企业的 Microsoft Store。 IT 部门还可以设置一个企业专用商店，其中仅包含公司的应用，用于HoloLens使用情况。 安全地将企业软件分发给选定的企业用户组。

### <a name="development-edition-vs-commercial-suite"></a>Development Edition 与 Commercial Suite

<table>
<tr>
<th>功能</th><th>Development Edition</th><th>商业套件</th>
</tr><tr>
<td>设备加密 (Bitlocker) </td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>虚拟专用网络 (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">展台模式</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 管理和部署</th>
</tr><tr>
<td>移动设备管理 (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>阻止取消注册的功能</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>基于证书的公司Wi-Fi访问</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store（消费者）</td><td style="text-align: center;">使用者</td><td style="text-align: center;">通过 MDM 进行筛选</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">企业应用商店门户</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 安全性和标识</th>
</tr><tr>
<td>使用 AAD Azure Active Directory (登录) </td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>使用 Microsoft 帐户登录 (MSA) </td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>带 PIN 解锁密钥的下一代凭据</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">安全启动</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 服务和支持</th>
</tr><tr>
<td>当更新可用时自动更新系统</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Long Term Servicing Branch</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>以前的发行说明
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另请参阅
* [HoloLens 已知问题](/windows/mixed-reality/hololens-known-issues)
* [商业功能](/windows/mixed-reality/commercial-features)
* [安装工具](/windows/mixed-reality/develop/install-the-tools)
* [使用 HoloLens 仿真器](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)