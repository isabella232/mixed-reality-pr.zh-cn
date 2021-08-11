---
title: 发行说明 - 2018 年 4 月
description: 随时了解 2018 HoloLens Windows Mixed Reality 2018/RS4 更新Windows 10发行说明。
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: 发行说明， 版本， windows 10， 内部版本， rs4， os
ms.openlocfilehash: 27f80d659c63362191a80eeae973111ca342090901c243772868d1a7c11e24d3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202429"
---
# <a name="release-notes---april-2018"></a>发行说明 - 2018 年 4 月

Windows 10 **[2018](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** 年 4 月更新 (也称为 RS4) 包括连接到电脑的 HoloLens 和 Windows Mixed Reality 沉浸式头戴显示设备新功能。 

若要更新到任一设备类型的最新版本，请打开 设置 **应用，** 转到"更新&**安全性**"，然后选择"检查 **更新"** 按钮。 在 Windows 10 电脑上，还可使用 Windows 媒体创建工具 手动安装 Windows 10 2018[年](https://www.microsoft.com/software-download/windows10)4 月更新。

**桌面的最新版本：Windows 10** 2018 年 4 月更新 (**10.0.17134.1**) <br>
**最新版本的 HoloLens：Windows 10** 2018 年 4 月更新 (**10.0.17134.80**) <br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Alex Kipman 提供的消息，并概述了 2018 年 4 月更新Windows 10混合现实功能*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>沉浸式头戴显示Windows Mixed Reality的新功能

2018 Windows 10 2018 年 4 月更新包含许多有关将沉浸式 Windows Mixed Reality (VR) 头戴显示设备与桌面电脑一同使用的改进，例如： 

* **新环境混合现实主页**- 选择"悬崖小屋位置"，在 悬崖小屋 环境与新 Skyloft 环境之间"开始"菜单。 我们还添加了一 [项实验](/windows/mixed-reality/design/add-custom-home-environments) 性功能，可让你使用已创建的自定义环境。
* **快速访问混合现实捕获** - 跨环境和应用使用运动控制器拍摄混合现实照片，但不捕获受 DRM 保护的内容。 按住Windows按钮，然后点击触发器。 .
* **用于启动和调整内容大小的新** 选项 - 现在，当你从应用程序启动应用时，应用会自动"开始"菜单。 现在，通过拖动窗口的边缘和角，还可以调整 2D 应用的大小。
* **使用"teleport"** 语音命令轻松跳转到内容 - 通过Windows Mixed Reality内容并说"teleport"，快速在用户主页中的内容前进行远程传送。
* **[动画的 3D 应用启动器和](/windows/mixed-reality/distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home#animation-guidelines)装饰 [性 3D](/windows/mixed-reality/distribute/enable-placement-of-3d-models-in-the-home)混合现实主页。** 现在可以将动画添加到 3D 应用启动器，并允许用户将装饰性 3D 模型从网页或 2D 应用放入 Windows Mixed Reality主页。
* **[针对 SteamVR](/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)** Windows Mixed Reality 的改进 - 适用于 SteamVR 的 Windows Mixed Reality 已退出新升级的"早期访问"，包括：使用运动控制器时出现动作反馈、提高性能和可靠性，以及改进 SteamVR 中运动控制器的外观。
* **其他改进** - 更新的自动性能设置提供了更优化的体验 [ (可以手动](#visual-quality) 替代此设置) 。 安装程序现在提供有关 USB 3.0 控制器和图形卡的常见兼容性问题的更多详细信息。

## <a name="new-features-for-hololens"></a>HoloLens

2018 Windows 10 2018 年 4 月更新已到达所有HoloLens客户！ 此更新包含自[2016](release-notes-august-2016.md)年 8 月发布 HoloLens主要版本以来引入的改进。

### <a name="for-everyone"></a>针对所有人

<table>
  <tr>
    <th>功能</th><th>详细信息</th><th>说明</th>
  </tr>
  <tr>
    <td>启动时自动放置 2D 和 3D 内容</td><td>2D 应用启动器或 2D UWP 应用在启动时自动放置于世界的最佳大小和距离，而不是要求用户放置它。 如果 <a href="/windows/mixed-reality/design/app-views">沉浸</a> 式应用使用 2D 应用启动器而不是 <a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3D</a>应用启动器，沉浸式应用将像在 RS1 中一样从 2D 应用启动器自动启动。<br><br>来自 "开始"菜单 的 3D 应用启动器也自动设置在世界上。 用户可以单击启动器以启动沉浸式应用，而不是自动启动应用。 从 全息影像 应用和 Edge 打开的 3D 内容也自动位于全球。</td><td>从 "开始"菜单 打开应用时，系统不会要求你将应用放在世界上。<br><br>如果 2D 应用<a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">/3D</a> 应用启动器放置不是最佳位置，可以使用下面所述的新流畅应用操作轻松移动它们。 还可通过说"移动此项"重新定位 2D 应用启动器/3D 内容，然后使用凝视重新定位内容。</td>
  </tr>
  <tr>
    <td>流畅的应用操作</td><td>无需进入"调整"模式即可移动、调整和旋转 2D 和 3D 内容。</td><td>若要移动 2D UWP 应用或 2D 应用启动器，只需凝视其应用栏，然后使用点击 + 按住 + 拖动手势。 可以通过在对象上的任意位置进行点击，然后使用点击 +按住 + 拖动来移动 3D 内容。<br><br>若要调整 2D 内容的大小，请凝视其一角。 凝视光标将变为调整大小的光标，然后点击"+ 按住 + 拖动"以调整大小。 通过查看 2D 内容的边缘和拖动，还可以使 2D 内容更高或更宽。<br><br>若要重设 3D 内容的大小，请两手向上提升手势框架，将手指向上指向就绪位置。 你将看到光标变为一个状态，只需两只小手。 用双手点击并按住手势。 将手移得更近或更远会更改对象的大小。 相互向前和向后移动手会旋转对象。 还可以按此方式调整/旋转 2D 内容。</td>
  </tr>
  <tr>
    <td>通过重排水平调整 2D 应用大小</td><td>在纵横比方面使 2D UWP 应用更宽，以查看更多应用内容。 例如，使邮件应用足够宽以显示"预览"窗格。</td><td>只需凝视 2D UWP 应用的左边缘或右边缘即可查看调整大小光标，然后使用点击 + 按住 + 拖动手势调整大小。</td>
  </tr>
  <tr>
    <td>扩展的语音命令支持</td><td>可以更简单地使用语音。</td><td>请尝试以下语音命令：<ul><li>"去开始菜单"- 启动"开始"菜单或退出<a href="/windows/mixed-reality/design/app-views">沉浸式应用</a>。</li><li>"移动此项"- 允许移动对象。</li></ul></td>
  </tr>
  <tr>
    <td>更新全息影像和照片应用</td><td>更新全息影像全息影像的应用。 更新了照片应用。</td><td>你会注意到，应用和照片全息影像更新的外观。 该全息影像应用包括多个全息影像和一个标签制造商，以便更轻松地创建文本。</td>
  </tr>
  <tr>
    <td>改进了混合现实捕获</td><td>硬件快捷方式 MRC 视频的开始和结束。</td><td>按住音量向上 + 向下 3 秒，开始录制 MRC 视频。 再次点击这两者，或使用"布满"手势结束。</td>
  </tr>
  <tr>
    <td>合并空格</td><td>将全息影像的空间管理简化为单个空间。</td><td>HoloLens自动查找空间，并且不再需要管理或选择空间。 如果周围的全息影像出现问题，可以转到"系统设置 >删除> 全息影像 ><b>全息影像"。</b> 如果需要，还可以选择"<b>删除所有全息影像"。</b></td>
  </tr>
  <tr>
    <td>改进了音频沉浸式</td><td>现在，你可以更好地HoloLens环境中的声音，并体验来自应用程序的更真实的声音，因为声音被设备检测到的真实墙所遮盖。</td><td>你不必执行任何工作来享受改进的空间音效。</td>
  </tr>
  <tr>
    <td>文件资源浏览器</td><td>从文件内移动和删除HoloLens。</td><td>可以使用<b>应用文件资源管理器移动</b>和删除文件HoloLens。<br><br><b>提示：</b> 如果看不到任何文件，则"最近"筛选器可能处于活动状态， (左窗格中突出显示时钟) 。 若要修复，请在左侧窗格中选择"此设备"文档 (位于时钟图标下方，) 菜单并选择" </b> <b>此设备"。</b>
</td>
  </tr>
  <tr>
    <td>MTP (媒体传输协议) 支持</td><td>使桌面电脑能够访问库， (照片、视频、文档) 上HoloLens轻松传输。</td><td>与其他移动设备类似，将 HoloLens 连接到电脑以启动<b>文件资源管理器</b>以访问 HoloLens 库 (照片、视频、文档) 轻松传输。<br><br><b>提示：</b><ul><li>如果看不到任何文件，请确保登录到HoloLens以启用对数据的访问。</li><li>在<b>文件资源管理器，</b>可以选择"设备属性"，Windows全息<b></b>OS 版本号 (固件) 和设备序列号。</li></ul><b>已知问题：</b>未HoloLens通过<b>文件资源管理器</b>重命名帐户。</td>
  </tr>
  <tr>
    <td>设置期间强制网络门户网络支持</td><td>现在，可以在酒店、HoloLens、零售商店或使用强制网络门户的企业的来宾网络上设置客户网络。</td><td>在安装过程中，选择网络，选中"自动连接"，并按提示输入网络信息。</td>
  </tr>
  <tr>
    <td>通过应用同步OneDrive视频</td><td>现在，来自 HoloLens 的OneDrive应用将Microsoft Store照片应用进行同步。</td><td>若要进行设置，请从应用商店下载OneDrive启动应用。 首次运行时，系统会提示你自动将照片上传到OneDrive。 如果未显示此提示，可以在应用设置中查找选项。</td>
  </tr>
</table>

### <a name="for-developers"></a>面向开发人员

<table>
  <tr>
    <th>功能</th><th>详细信息</th><th>说明</th>
  </tr>
  <tr>
    <td>空间映射改进</td><td>质量、简化和性能改进。</td><td>空间映射网格将显示为 "整洁" –表示相同的详细信息级别需要较少的三角形。 你可能会注意到场景中的三角形密度发生了变化。</td>
  </tr>
  <tr>
    <td>基于深度缓冲区自动选择关注点</td><td>将深度缓冲区提交到 Windows 允许 HoloLens 自动选择焦点以优化全息影像稳定性。</td><td>在 Unity 中，请参阅<b>"编辑 >" Project 设置 > 播放机 > 通用 Windows 平台 > 设置 XR Windows Mixed Reality</b>，展开<b>SDK</b>项，并选中 "<b>启用深度缓冲区共享</b>"。 这将自动检查新项目。<br><br>对于 DirectX 应用，请确保在<b>HolographicRenderingParameters</b>每个帧上调用<a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a>方法，以提供 Windows 的深度缓冲区。
</td>
  </tr>
  <tr>
    <td>全息 reprojection 模式</td><td>你现在可以在 HoloLens 上禁用位置 reprojection，以改善严格的正文锁定内容（如360度视频）的全息影像稳定性。</td><td>在 Unity 中，当视图中的所有内容严格地被锁定时，将<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">ReprojectionMode</a>设置为<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode。</a><br><br>对于 DirectX 应用，当视图中的所有内容都是严格的正文锁定时，将<a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">ReprojectionMode</a>设置为<a href="/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode。</a></td>
  </tr>
  <tr>
    <td>应用定制 Api</td><td>Windowsapi 详细了解你的应用程序的运行位置，如设备的显示是否透明 (HoloLens) 或不透明 (沉浸式耳机) ，以及 UWP 应用的2d 视图是否显示在全息 shell 中。</td><td>Unity 先前手动公开了 <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings</a> ，但在此生成之前仍可正常使用。<br><br>对于 DirectX 应用，你现在可以访问现有 Api，例如<a href="/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay. adaptivesourcemanager.getdefault () 。</a>HoloLens 上的 IsOpaque 和<a href="/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview</a> 。
</td>
  </tr>
  <tr>
      <td>研究模式</td><td>允许开发人员在构建学术和工业应用程序时访问密钥 HoloLens 传感器，以测试计算机视觉和机器人领域的新想法，包括：<ul><li>四个环境跟踪相机</li><li>深度映射相机数据的两个版本</li><li>反射率流的两个版本</li></ul></td><td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/research-mode">研究模式文档</a><br><a href="https://github.com/Microsoft/HoloLensForCV">研究模式示例应用</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>面向商业客户

<table>
  <tr>
    <th>功能</th><th>详细信息</th><th>说明</th>
  </tr>
  <tr>
    <td>在单个设备上使用多个 Azure Active Directory 的用户帐户</td><td>共享包含多个 Azure AD 用户的 HoloLens，每个用户都有自己的用户设置和设备上的用户数据。</td><td><a href="/hololens/hololens-multiple-users">IT Pro 中心：与多人共享 HoloLens</a></td>
  </tr>
  <tr>
    <td>登录时更改 Wi-Fi 网络</td><td>在登录前更改 Wi-Fi 网络，使其他用户首次登录到其 Azure AD 的用户帐户，允许用户在不同位置和作业站点共享设备。</td><td>在登录屏幕上，可以使用 "密码" 字段下面的 "网络" 图标来连接到网络。 当你首次登录到设备时，这非常有用。</td>
  </tr>
  <tr>
    <td>统一注册</td><td>现在可以轻松地将设备设置为个人 Microsoft 帐户 HoloLens 用户添加工作帐户 (Azure AD) 并将设备加入其 MDM 服务器。</td><td>使用 Azure AD 帐户登录，并自动进行注册。</td>
  </tr>
  <tr>
    <td>无 MDM 注册的邮件同步</td><td>支持 Exchange Active Sync (EAS) 邮件同步，无需 MDM 注册。</td><td>你现在可以在不注册 MDM 的情况下同步电子邮件。 您可以使用 Microsoft 帐户设置设备，下载并安装邮件应用程序，并直接添加工作电子邮件帐户。</td>
  </tr>
</table>

### <a name="for-it-pros"></a>适用于 IT 专业人员

<table>
  <tr>
    <th>功能</th><th>详细信息</th><th>说明</th>
  </tr>
  <tr>
    <td>新的 "Windows Holographic for Business" OS 名称</td><td>清除版本命名，以便在 HoloLens 上启用商用套件功能时减少版本升级许可证应用程序上的混淆。</td><td>可在<b>设置 > 系统 ></b>中查看设备上 Windows 全息的版本。 如果已应用版本更新以启用商业套件功能，则将显示 "Windows Holographic for Business"。 了解如何<a href="/hololens/hololens-upgrade-enterprise">解锁 Windows Holographic for Business 功能</a>。</td>
  </tr>
  <tr>
  <td>Windows配置设计器 (WCD) </td><td>创建和编辑预配包，以通过更新的 WCD 应用配置 HoloLens。 用于版本更新的简单 HoloLens 向导、可配置的 OOBE、区域/时区、批量 Azure AD 令牌、网络和开发人员 CSP。 将高级编辑器筛选为 HoloLens 支持的选项，包括已分配的访问权限和帐户管理 csp。</td><td><a href="/hololens/hololens-provisioning">IT Pro 中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
    <td>可配置的安装程序 (OOBE) </td><td>在安装过程中隐藏校准、手势/注视定型和 Wi-Fi 配置屏幕。</td><td><a href="/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro 中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
    <td>批量 Azure AD 令牌支持</td><td>将设备预注册到 Azure AD directory 租户，以加快用户安装流。</td><td><a href="/hololens/hololens-provisioning">IT Pro 中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup 云解决方案提供商</td><td>部署配置文件以在开发人员模式下设置 HoloLens。 适用于开发和演示设备。</td><td><a href="/hololens/hololens-provisioning">IT Pro 中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
  <td>AccountManagement 云解决方案提供商</td><td>共享 HoloLens 设备并在注销或处于非活动/存储阈值后删除用户数据，以供临时使用。 支持 Azure AD 帐户。</td><td><a href="/hololens/hololens-provisioning">IT Pro 中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
  <td>已分配的访问权限</td><td>为第一行工作人员或演示 Windows 分配的访问权限。 单个或多个应用锁定。 无需开发人员解锁。</td><td><a href="/hololens/hololens-kiosk">IT Pro 中心：在展台模式下设置 HoloLens</a></td>
  </tr>
  <tr>
  <td>展台设备的来宾访问</td><td>使用无密码的来宾帐户 Windows 分配的访问权限来进行演示。 单个或多个应用锁定。 无需开发人员解锁。</td><td><a href="/hololens/hololens-kiosk#guest">IT Pro 中心：在展台模式下设置 HoloLens</a></td>
  </tr>
  <tr>
    <td>设置 (OOBE) 诊断</td><td>从 HoloLens 获取诊断日志，以便您可以对 Azure AD 登录失败进行故障排除， (在反馈中心对登录失败的用户可用) 。</td><td>当安装或登录失败时，选择 "新 <b>收集信息</b> " 选项以获取诊断日志进行故障排除。</td>
  </tr>
  <tr>
    <td>本地帐户的无限密码过期</td><td>如果本地帐户密码过期，则删除设备重置中断。</td><td>预配本地帐户时，不再需要在<b>设置</b>中每42天更改密码，因为帐户密码不再过期。</td>
  </tr>
  <tr>
    <td>MDM 同步状态和详细信息</td><td>标准 Windows 功能，用于从 HoloLens 中了解 MDM 同步状态和详细信息。</td><td>可以<b>> 访问工作或学校 > 信息，查看设置 > 帐户</b>中的设备的 MDM 同步状态。 在 " <b> 设备同步状态" <b> 部分中，可以开始同步、查看由 MDM 管理的区域，以及创建和导出高级诊断报告。</td>
  </tr>
</table>

## <a name="known-issues"></a>已知问题

我们一直在努力提供出色的 Windows Mixed Reality 体验，但我们仍在跟踪一些已知问题。 如果发现其他人，请 [向我们提供反馈](/windows/mixed-reality/give-us-feedback)。

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>更新后

在您的 HoloLens 上从 RS1 升级到 RS4 后，您可能会发现以下问题：
* **pin 重置**-固定到 "开始"菜单的3x3 应用将在更新后重置为默认值。 
* **应用和放置的全息影像重置** -在更新后将删除位于你的世界中的应用，并将需要在你的整个空间中将其重新放置。 
* **反馈中心可能不会立即启动** -更新后，将需要几分钟时间才能启动某些收件箱应用，如反馈中心，而这些应用会自行更新。 
* **需要重新同步企业 Wi-Fi 证书**-我们正在调查的问题需要将 HoloLens 连接到不同的网络，以便企业证书重新同步到设备，然后才能使用证书重新连接到公司网络。 
* **HEVC 视频播放不起作用** -尝试播放 h-p 视频的应用程序将收到一条错误消息。 解决方法是 [访问 Windows 设备门户](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)，在左侧导航栏上选择 "**应用**"，并 **删除** HEVC 应用程序。 然后，从 Microsoft Store 安装最新[HEVC 视频扩展](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7)。 我们正在调查此问题。 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>对于开发人员：为运行 Windows 10 2018 年4月更新的设备更新 HoloLens 应用

除了更好的[新功能](#new-features-for-hololens)列表外，Windows 10 2018 年4月的更新 (RS4) HoloLens 强制执行以前版本不会执行的某些代码行为：
* **使用敏感资源的权限请求 (照相机、麦克风等** HoloLens 上的) -RS4 将强制实施权限请求，以访问敏感资源，如相机或麦克风。 HoloLens 上的 RS1 未强制执行这些提示，因此，如果你的应用程序假定立即访问这些资源， (RS4 中可能会崩溃，即使用户向请求的资源) 授予了权限也是如此。 有关详细信息，请参阅相关 [UWP 应用功能声明一文](/windows/uwp/packaging/app-capability-declarations) 。
* 对 HoloLens 上 **你自己** 的 RS4 外部的应用的调用将强制正确使用 [ *Windows.System Launcher* 类](/uwp/api/Windows.System.Launcher)来启动你自己的其他应用。 例如，我们发现了 LauncherWindows.Sys的应用的问题 *。LaunchUriForResultsAsync* 从非 ASTA (UI) 线程。 这会在 HoloLens 的 RS1 中成功，但 RS4 要求在 UI 线程上执行调用。

### <a name="windows-mixed-reality-on-desktop"></a>在桌面上 Windows Mixed Reality

#### <a name="visual-quality"></a>视觉质量

* 如果你在 Windows 10 2018 年4月更新该图形比之前更模糊，或视图的字段在你的耳机上看起来更小，则自动性能设置可能已更改为在不太强大的图形卡上保持足够的帧速率 (例如 Nvidia 1050) 。 如果你选择) ，你可以通过导航到 **设置 > 混合现实 > "耳机显示 > 体验" 选项**> "自动" 改为 "90 Hz" 来手动替代此 (。 你还可以尝试在同一设置页面上更改 **视觉质量** () "高"。

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality 安装程序

* 设置与耳机连接的 Windows 时，您的 PC 监视器可能会留空。 拔出耳机，使其能够输出到电脑监视器，以完成 Windows 设置。
* 如果尚未连接耳机，则首次访问 Windows Mixed Reality 时可能会错过提示。
* 其他蓝牙设备可能会导致运动控制器干扰。 如果运动控制器具有连接/配对/跟踪问题，请确保蓝牙无线电 (如果外部转换器) 插到无障碍的位置，而不是紧挨着另一蓝牙转换器。 同时，尝试在 Windows Mixed Reality 会话过程中关闭其他蓝牙外围设备，以查看是否有帮助。

#### <a name="games-and-apps-from-the-microsoft-store"></a>Microsoft Store 中的游戏和应用

* 某些图形密集型游戏（如 Forza Motorsport 7）可能会导致在 Windows Mixed Reality 内播放时不太强大的 Pc 上出现性能问题。

#### <a name="audio"></a>音频

* 如果你在使用 Windows Mixed Reality 耳机之前在你的主机 PC 上启用了 Cortana，则可能会丢失适用于你围绕 Windows Mixed Reality home 的应用的空间声音模拟。 
   * 解决方法是在连接到电脑的所有音频设备上启用 "用于耳机的 Windows Sonic"，甚至在手机连接音频设备上启用：
      1. 在桌面任务栏上左键单击扬声器图标，然后从音频设备列表中选择。
      2. 右键单击桌面任务栏上的扬声器图标，然后在 "扬声器设置" 菜单中选择 "用于耳机的 Windows Sonic"。
      3. 为所有音频设备重复以下步骤， (终结点) 。
   * 另一个选项是在启动 Windows Mixed Reality 之前，禁用桌面上 **设置** Cortana 中的 "让 Cortana 响应嗨 Cortana"  >   。
* 当另一台多媒体 USB 设备 (（例如 web cam）) 使用 Windows Mixed Reality 耳机共享同一 USB 集线器 (外部或 PC 内) ，在极少数情况下，耳机的音频插孔/耳机可能会有蜂鸣声或根本没有音频。 你可以将耳机修复为与其他设备共享同一集线器的 USB 端口，或者断开连接/禁用其他 USB 多媒体设备。
* 在极少数情况下，主机 PC 的 USB 集线器无法为 Windows Mixed Reality 耳机提供足够的电源，你可能会注意到耳机突然出现噪音激增。

#### <a name="holograms"></a>全息影像

* 如果你在 Windows Mixed Reality home 中放置了大量全息影像，则某些影像可能会消失，并在你查找时重新出现。 为避免出现这种情况，请在 Windows Mixed Reality home 的那一区域中删除一些全息影像。

#### <a name="motion-controllers"></a>运动控制器

* 如果未将输入路由到耳机，则当运动控制器位于房间边界旁边时，它会短暂消失。 按 Win + Y 以确保桌面监视器上出现蓝色横幅可以解决此问题。 
* 有时，当你在 Microsoft Edge 中单击网页时，内容将缩放，而不是单击。

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality home 中的桌面应用

* 截图工具不适用于桌面应用。
* 桌面应用在重新启动时不会保留设置。
* 如果你在桌面上使用混合现实门户预览，则在 Windows Mixed Reality home 中打开桌面应用时，你可能会注意到无限镜像效果。 
* 运行桌面应用可能会导致非超 Windows Mixed Reality 电脑上出现性能问题;不建议使用此方法。  
* 桌面应用可能会自动启动，因为桌面上不可见的窗口有焦点。 
* 桌面用户帐户控制提示会使耳机显示黑色，直到完成提示。

#### <a name="windows-mixed-reality-for-steamvr"></a>SteamVR 的 Windows Mixed Reality

* 你可能需要在更新后启动混合现实门户，以确保 Windows 10 2018 年4月版更新所必需的软件更新在启动 SteamVR 之前已完成。 
* 必须使用最新版本的 SteamVR Windows Mixed Reality，才能保持 Windows 10 与2018年4月版更新保持兼容。 请确保已 Windows Mixed Reality 打开 SteamVR 的 "自动更新"，它位于流中库的 "软件" 部分。  

#### <a name="other-issues"></a>其他问题

>[!IMPORTANT]
>Windows 10 2018 年4月更新的早期版本推送到内部版本 (版本 17134.5) 缺少运行 Windows Mixed Reality 所需的软件。 如果使用 Windows Mixed Reality，则建议避免使用此版本。 

在此更新的初始版本中使用 Surface Book 2 时，我们发现性能退化 (10.0.17134.1) 我们在即将推出的更新修补程序中进行修复。 建议你等待，直到手动更新或等待更新正常推出。

## <a name="provide-feedback-and-report-issues"></a>提供反馈和报告问题

使用[HoloLens 或 Windows 10 PC 上的反馈中心应用](/windows/mixed-reality/give-us-feedback)提供反馈和报告问题。 使用反馈中心可确保包括所有必要的诊断信息，以帮助我们的工程师快速调试和解决问题。

>[!NOTE]
>请确保接受提示，询问你是否想要反馈中心访问文档文件夹 (在出现) 提示时选择 **"是"** 。

## <a name="prior-release-notes"></a>以前的发行说明

* [发行说明 - 2017 年 10 月](release-notes-october-2017.md)
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另请参阅
* [沉浸式耳机支持 (外部链接) ](./troubleshooting-windows-mixed-reality.md)
* [HoloLens 支持 (外部链接) ](https://support.microsoft.com/products/hololens)
* [安装工具](/windows/mixed-reality/develop/install-the-tools)
* [给我们提供反馈](/windows/mixed-reality/give-us-feedback)