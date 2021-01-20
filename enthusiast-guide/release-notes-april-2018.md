---
title: 发行说明-2018 年4月
description: 对于 Windows 10 4 月 2018/RS4 更新，请随时了解 HoloLens 和 Windows Mixed Reality 发行说明。
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: 发行说明、版本、windows 10、build、rs4、os
ms.openlocfilehash: cdaed2b653faeac81b539422aba6f6e0c7f6c064
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581621"
---
# <a name="release-notes---april-2018"></a>发行说明-2018 年4月

**[Windows 10 2018 年4月更新](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (也称为 RS4) 包含适用于 HoloLens 和 Windows Mixed Reality 的新功能（连接到电脑）。 

若要更新任一设备类型的最新版本，请打开 " **设置** " 应用，中转到 " **更新" & 安全**"，然后选择" **检查更新** "按钮。 在 Windows 10 电脑上，你还可以使用 [windows media 创建工具](https://www.microsoft.com/software-download/windows10)手动安装 windows 10 2018 年4月版更新。

**最新版本的桌面：** Windows 10 2018 年4月更新 (**10.0.17134.1**) <br>
**最新版本的 HoloLens：** Windows 10 2018 年4月更新 (**10.0.17134.80**) <br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*2018年4月更新中的 Alex Kipman 的消息和新的混合现实功能概述*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>适用于 Windows Mixed Reality 沉浸式耳机的新功能

Windows 10 2018 年4月的更新包括对使用 Windows Mixed Reality 沉浸式 (VR) 耳机和台式计算机的许多改进，例如： 

* **混合现实的新环境** -通过选择 "开始" 菜单上的 " **位置** "，在 Cliff 房子和新的 Skyloft 环境之间进行选择。 我们还添加 [了一个试验性功能](/windows/mixed-reality/design/add-custom-home-environments) ，可让你使用已创建的自定义环境。
* **快速访问混合现实捕获** -使用跨环境和应用的运动控制器进行混合现实照片，但不捕获受 DRM 保护的内容。 按住 Windows 按钮，然后点击触发器。 .
* **用于启动和调整内容大小的新选项** -在从 "开始" 菜单启动应用程序时，这些应用程序将自动放置在您前面。 你现在还可以通过拖动窗口的边缘和角来调整2D 应用的大小。
* 通过 gazing 内容并说 "传送"，**可以轻松地通过 "传送" 语音命令快速转到内容**。
* **混合现实主页的 [动画3d 应用启动器](/windows/mixed-reality/distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home#animation-guidelines)和 [装饰性3d 对象](/windows/mixed-reality/distribute/enable-placement-of-3d-models-in-the-home)**。 你现在可以将动画添加到3D 应用启动器，并允许用户将装饰性3D 模型从网页或2D 应用放置到 Windows Mixed Reality 主页中。
* 对 **[SteamVR 的 Windows mixed](/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)** Reality 的改进-SteamVR 的 Windows mixed reality 是全新升级的 "早期访问"，其中包括：使用运动控制器时的 haptic 反馈，提高了性能和可靠性，并改进了 SteamVR 中的运动控制器外观。
* **其他改进** -更新的自动性能设置提供更好的体验 (你可以 [手动覆盖](#visual-quality) 此设置) 。 安装程序现在提供了有关 USB 3.0 控制器和图形卡的常见兼容性问题的更多详细信息。

## <a name="new-features-for-hololens"></a>HoloLens 的新功能

2018年4月版更新已到达所有 HoloLens 客户！ 自 [8 月2016年8月](release-notes-august-2016.md)发行的自上次主要发行版软件以来，此更新已打包。

### <a name="for-everyone"></a>适用于每个人

<table>
  <tr>
    <th>功能</th><th>详细信息</th><th>说明</th>
  </tr>
  <tr>
    <td>启动时自动放置2D 和3D 内容</td><td>2D 应用程序启动器或 2D UWP 应用在世界上自动放置，并在启动时获得最佳大小和距离，而不需要用户进行设置。 如果 <a href="/windows/mixed-reality/design/app-views">沉浸式应用</a> 程序使用的是2d 应用程序启动器而不是 <a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3d 应用程序启动器</a>，则沉浸式应用程序将从2d 应用程序启动器中自动启动，与在 RS1 中一样。<br><br>"开始" 菜单中的3D 应用启动器也会自动置于世界各地。 用户随后可以单击启动器启动沉浸式应用，而不是自动启动应用。 从全息影像应用和边缘中打开的3D 内容也会自动置于世界各地。</td><td>从 "开始" 菜单打开应用时，系统不会要求你将其置于世界中。<br><br>如果2D 应用/<a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">三维应用启动器</a> 放置不是最佳的，你可以使用下面所述的新的流体应用操作轻松移动它们。 还可以通过口述 "移动此内容"，然后使用 "注视" 重定位内容来重定位2D 应用启动器/3D 内容。</td>
  </tr>
  <tr>
    <td>流体应用操作</td><td>移动、调整二维和3D 内容并进行旋转，无需进入 "调整" 模式。</td><td>若要移动 2D UWP 应用或2D 应用启动器，只需在其应用栏上查看，然后使用点击 + 按住并拖动手势。 可以通过 gazing 对象上的任何位置移动3D 内容，然后使用点击 + 按住并拖动。<br><br>若要调整二维内容的大小，请将其置于其一角。 注视光标将变为调整大小光标，然后可以点击 + 按住并拖动鼠标来调整大小。 还可以通过查看边缘并拖动使其高度或更宽。<br><br>若要调整三维内容大小，请将双手抬起到手势帧，并将其放在就绪位置。 你会看到光标变成了两个小手的状态。 用双手敲击并保持手势。 将您的手移动到更近或更远的距离会更改对象的大小。 向后移动手动和向后移动会旋转对象。 还可以通过这种方式调整或旋转二维内容。</td>
  </tr>
  <tr>
    <td>2D 应用程序水平调整大小和重排</td><td>使二维 UWP 应用在纵横比中更宽，以查看更多的应用内容。 例如，使邮件应用宽度足以显示预览窗格。</td><td>只需注视 2D UWP 应用的左右边缘即可查看调整大小光标，然后使用点击 + 按住并拖动手势调整大小。</td>
  </tr>
  <tr>
    <td>扩展的语音命令支持</td><td>您可以更轻松地使用语音。</td><td>尝试以下语音命令：<ul><li>"转到开始"-打开 "开始" 菜单或退出 <a href="/windows/mixed-reality/design/app-views">沉浸式应用</a>。</li><li>"移动此项"-允许移动对象。</li></ul></td>
  </tr>
  <tr>
    <td>更新的全息影像和照片应用</td><td>更新了具有新全息影像的全息影像应用。 更新了照片应用。</td><td>你会注意到全息影像和照片应用的更新外观。 全息影像应用包括几个新的全息影像和标签 maker，便于创建文本。</td>
  </tr>
  <tr>
    <td>改善了混合现实捕获</td><td>硬件快捷方式启动和结束 MRC 视频。</td><td>保持音量向上 + 向下，3秒钟后即可开始录制 MRC 视频。 再次点击，或使用布隆手势结束。</td>
  </tr>
  <tr>
    <td>合并空间</td><td>简化对全息影像的空间管理，使其进入单个空间。</td><td>HoloLens 自动查找你的空间，不再需要你管理或选择空间。 如果你围绕你的全息影像出现问题，你可以使用 " <b>设置" > 系统 > 全息影像 > 删除附近的全息影像</b>。 如果需要，还可以选择 " <b>删除所有全息影像</b>"。</td>
  </tr>
  <tr>
    <td>改进的音频浸入式</td><td>现在，你可以在干扰环境中更好地听到 HoloLens，并从应用程序获得更逼真的声音，因为声音由设备检测到的真实背景。</td><td>无需执行任何操作即可获得改进的空间音质。</td>
  </tr>
  <tr>
    <td>文件资源浏览器</td><td>在 HoloLens 内移动和删除文件。</td><td>您可以使用 <b>文件资源管理器</b> 应用程序在 HoloLens 内移动和删除文件。<br><br><b>提示：</b> 如果看不到任何文件，则 "最近的" 筛选器可能处于活动状态 (时钟图标在左窗格中突出显示) "。 若要解决此问题，请 </b> 在左窗格中选择 "此设备文档" 图标 (时钟图标) 下，或打开菜单并选择 " <b>此设备</b>"。
</td>
  </tr>
  <tr>
    <td>MTP (媒体传输协议) 支持</td><td>使您的台式计算机能够访问您的库 (在 HoloLens 上) 的照片、视频、文档，以便轻松地进行传输。</td><td>类似于其他移动设备，将你的 HoloLens 连接到电脑，使 <b>文件资源管理器</b> 能够访问你的 hololens 库 (照片、视频、文档) 以便轻松传输。<br><br><b>提示：</b><ul><li>如果看不到任何文件，请确保登录到 HoloLens 以启用对数据的访问。</li><li>在电脑上的 <b>文件资源管理器</b> 中，可以选择 " <b>设备属性</b> " 以查看 Windows 全息 OS 版本号 (固件版本) 和设备序列号。</li></ul><b>已知问题：</b> 在电脑上通过 <b>文件资源管理器</b> 重命名 HoloLens 时未启用。</td>
  </tr>
  <tr>
    <td>在安装过程中捕获门户网络支持</td><td>现在，你可以在旅馆、会议中心、零售商店或使用捕获门户的企业中设置你的 HoloLens。</td><td>在安装过程中，选择网络，选中 "自动连接"，并在出现提示时输入网络信息。</td>
  </tr>
  <tr>
    <td>通过 OneDrive 应用进行的照片和视频同步</td><td>HoloLens 中的照片和视频现在会通过 Microsoft Store 而不是照片应用从 OneDrive 应用同步。</td><td>若要进行此设置，请从应用商店下载并启动 OneDrive 应用。 首次运行时，系统将提示您自动将照片上传到 OneDrive。 如果未显示此提示，你可以在应用设置中找到该选项。</td>
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
    <td>基于深度缓冲区自动选择关注点</td><td>将深度缓冲区提交给 Windows 后，HoloLens 就可以自动选择一个重点点来优化全息影像稳定性。</td><td>在 Unity 中，参阅 <b>> Player > 通用 Windows 平台选项卡上的 > "编辑 > 项目设置" 选项卡</b>，展开 " <b>WINDOWS Mixed Reality SDK</b> " 项，并选中 " <b>启用深度缓冲区共享</b>"。 这将自动检查新项目。<br><br>对于 DirectX 应用，请确保在<b>HolographicRenderingParameters</b>每个帧上调用<a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a>方法，以向 Windows 提供深度缓冲区。
</td>
  </tr>
  <tr>
    <td>全息 reprojection 模式</td><td>你现在可以在 HoloLens 上禁用位置 reprojection，以改善严格的正文锁定内容（如360度视频）的全息影像稳定性。</td><td>在 Unity 中，当视图中的所有内容严格地被锁定时，将<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">ReprojectionMode</a>设置为<a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode。</a><br><br>对于 DirectX 应用，当视图中的所有内容都是严格的正文锁定时，将<a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">ReprojectionMode</a>设置为<a href="/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode。</a></td>
  </tr>
  <tr>
    <td>应用定制 Api</td><td>Windows Api 详细了解你的应用程序的运行位置，例如设备的显示是否是透明的 (HoloLens) 或不透明 (沉浸式耳机) ，以及 UWP 应用的2D 视图是否显示在全息 shell 中。</td><td>Unity 先前手动公开了 <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings</a> ，但在此生成之前仍可正常使用。<br><br>对于 DirectX 应用，你现在可以访问现有 Api，例如 <a href="/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay. adaptivesourcemanager.getdefault ( # A1。IsOpaque</a> 和 <a href="/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview IsCurrentViewPresentedOnHolographicDisplay</a> 。
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
    <td>在单个设备上使用多个 Azure Active Directory 的用户帐户</td><td>与多个 Azure AD 用户共享 HoloLens，每个用户都有自己的用户设置和设备上的用户数据。</td><td><a href="/hololens/hololens-multiple-users">IT 专业人员中心：与多人共享 HoloLens</a></td>
  </tr>
  <tr>
    <td>登录时更改 Wi-Fi 网络</td><td>在登录前更改 Wi-Fi 网络，使其他用户首次登录到其 Azure AD 的用户帐户，允许用户在不同位置和作业站点共享设备。</td><td>在登录屏幕上，可以使用 "密码" 字段下面的 "网络" 图标来连接到网络。 当你首次登录到设备时，这非常有用。</td>
  </tr>
  <tr>
    <td>统一注册</td><td>现在，使用个人 Microsoft 帐户将设备设置为使用个人来添加工作帐户 (Azure AD) 并将设备加入其 MDM 服务器，这很容易。</td><td>使用 Azure AD 帐户登录，并自动进行注册。</td>
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
    <td>新的 "Windows 全息 for Business" OS 名称</td><td>清除版本命名，以便在 HoloLens 上启用商用套件功能时减少版本升级许可证应用程序上的混淆。</td><td>你可以在 " <b>设置" > 系统 ></b>的 "设置" 中查看设备上的 Windows 全息版本。 如果已应用版本更新以启用商业套件功能，则将显示 "Windows 全息 for Business"。 了解如何 <a href="/hololens/hololens-upgrade-enterprise">解锁 Windows 全息版功能</a>。</td>
  </tr>
  <tr>
  <td>Windows 配置设计器 (WCD) </td><td>创建和编辑预配包，以通过已更新的 WCD 应用配置 HoloLens。 用于版本更新、可配置的 OOBE、区域/时区、批量 Azure AD 令牌、网络和开发人员 CSP 的简单 HoloLens 向导。 高级编辑器筛选为 HoloLens 支持的选项，包括分配的访问权限和帐户管理 Csp。</td><td><a href="/hololens/hololens-provisioning">IT 专业人员中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
    <td>可配置的安装程序 (OOBE) </td><td>在安装过程中隐藏校准、手势/注视定型和 Wi-Fi 配置屏幕。</td><td><a href="/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT 专业人员中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
    <td>批量 Azure AD 令牌支持</td><td>将设备预注册到 Azure AD directory 租户，以加快用户安装流。</td><td><a href="/hololens/hololens-provisioning">IT 专业人员中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup 云解决方案提供商</td><td>部署配置文件以在开发人员模式下设置 HoloLens。 适用于开发和演示设备。</td><td><a href="/hololens/hololens-provisioning">IT 专业人员中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
  <td>AccountManagement 云解决方案提供商</td><td>共享 HoloLens 设备并在注销或处于非活动/存储阈值后删除用户数据，以供临时使用。 支持 Azure AD 帐户。</td><td><a href="/hololens/hololens-provisioning">IT 专业人员中心：使用预配包配置 HoloLens</a></td>
  </tr>
  <tr>
  <td>已分配的访问权限</td><td>对第一行辅助角色或演示的 Windows 分配的访问权限。 单个或多个应用锁定。 无需开发人员解锁。</td><td><a href="/hololens/hololens-kiosk">IT 专业人员中心：在展台模式下设置 HoloLens</a></td>
  </tr>
  <tr>
  <td>展台设备的来宾访问</td><td>使用无密码的来宾帐户对 Windows 分配的访问权限来演示。 单个或多个应用锁定。 无需开发人员解锁。</td><td><a href="/hololens/hololens-kiosk#guest">IT 专业人员中心：在展台模式下设置 HoloLens</a></td>
  </tr>
  <tr>
    <td>设置 (OOBE) 诊断</td><td>从 HoloLens 获取诊断日志，以便在反馈中心对登录失败) 的用户可用之前， (Azure AD 登录失败进行故障排除。</td><td>当安装或登录失败时，选择 "新 <b>收集信息</b> " 选项以获取诊断日志进行故障排除。</td>
  </tr>
  <tr>
    <td>本地帐户的无限密码过期</td><td>如果本地帐户密码过期，则删除设备重置中断。</td><td>预配本地帐户时，将不再需要在 " <b>设置</b>" 中每42天更改密码，因为帐户密码不再过期。</td>
  </tr>
  <tr>
    <td>MDM 同步状态和详细信息</td><td>标准 Windows 功能，可了解 HoloLens 中的 MDM 同步状态和详细信息。</td><td>可以 <b>> 访问工作或学校 > 信息，在设置 > 帐户</b>中检查设备的 MDM 同步状态。 在 " <b> 设备同步状态" <b> 部分中，可以开始同步、查看由 MDM 管理的区域，以及创建和导出高级诊断报告。</td>
  </tr>
</table>

## <a name="known-issues"></a>已知问题

我们一直在努力提供强大的 Windows Mixed Reality 体验，但我们仍在跟踪一些已知问题。 如果发现其他人，请 [向我们提供反馈](/windows/mixed-reality/give-us-feedback)。

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>更新后

从 RS1 更新到 RS4 上的后，你可能会发现以下问题：
* **Pin 重置** -固定到 "开始" 菜单的3x3 应用将在更新后重置为默认值。 
* **应用和放置的全息影像重置** -在更新后将删除位于你的世界中的应用，并将需要在你的整个空间中将其重新放置。 
* **反馈中心可能不会立即启动** -更新后，将需要几分钟时间才能启动某些收件箱应用，如反馈中心，而这些应用会自行更新。 
* **需要重新同步企业 Wi-Fi 证书** -我们正在调查的问题需要将 HoloLens 连接到不同的网络，以便企业证书重新同步到设备，然后才能使用证书重新连接到公司网络。 
* **HEVC 视频播放不起作用** -尝试播放 h-p 视频的应用程序将收到一条错误消息。 解决方法是 [访问 Windows 设备门户](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)，在左侧导航栏上选择 " **应用** "，并 **删除** HEVC 应用程序。 然后，从 Microsoft Store 安装最新的 [HEVC 视频扩展](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 。 我们正在调查此问题。 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>对于开发人员：为运行 Windows 10 2018 年4月更新的设备更新 HoloLens 应用

除了更好的 [新功能](#new-features-for-hololens)列表，Windows 10 2018 年4月更新 (RS4) 为 HoloLens 强制实施一些代码行为，而以前的版本不会：
* 在 RS4 上 **使用敏感资源 (照相机、麦克风) 等的权限请求** 将对用于访问敏感资源（如相机或麦克风）的应用强制执行权限请求。 RS1 on HoloLens 未强制执行这些提示，因此，如果应用程序假定立即访问这些资源，则即使用户向请求的资源) 授予权限，也可能会在 RS4 (崩溃。 有关详细信息，请参阅相关 [UWP 应用功能声明一文](/windows/uwp/packaging/app-capability-declarations) 。
* 在 HoloLens 上，对 RS4 的 **应用的调用** 将强制正确使用 [ *Windows.System。*](/uwp/api/Windows.System.Launcher)发起程序类，用于启动自己的其他应用。 例如，我们发现Windows.System 的应用程序存在问题 *。LaunchUriForResultsAsync* 从非 ASTA (UI) 线程。 这会在 RS1 上成功进行，但 RS4 需要在 UI 线程上执行调用。

### <a name="windows-mixed-reality-on-desktop"></a>桌面上的 Windows Mixed Reality

#### <a name="visual-quality"></a>视觉质量

* 如果在 Windows 10 四月2018更新之后，图形比之前更模糊，或视图的字段在你的耳机上看起来更小，则自动性能设置可能已更改为在不太强大的图形卡 (（例如 Nvidia 1050) ）上保持足够的帧速率。 如果你选择) ，你可以通过导航到 "设置" **> 混合现实 > 耳机显示 > 体验选项 >** "自动" 更改为 "90 Hz" 来手动替代此 (。 你还可以尝试在同一设置页上更改 **视觉质量** () "高"。

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality 安装

* 当使用连接的耳机设置 Windows 时，电脑监视器可能会留空。 拔出耳机，使计算机监视器能够完成 Windows 安装程序的输出。
* 如果尚未连接耳机，则首次访问 Windows Mixed Reality 主页时可能会错过提示。
* 其他蓝牙设备可能会干扰运动控制器。 如果运动控制器具有连接/配对/跟踪问题，请确保蓝牙无线电 (如果外部转换器) 插到无障碍的位置，而不是紧挨着另一台蓝牙转换器。 同时，在 Windows Mixed Reality 会话期间尝试关闭其他蓝牙外围设备，查看其是否有帮助。

#### <a name="games-and-apps-from-the-microsoft-store"></a>Microsoft Store 中的游戏和应用

* 在 Windows Mixed Reality 内播放时，某些以图形方式密集型的游戏（如 Forza Motorsport 7）可能会导致不支持的电脑出现性能问题。

#### <a name="audio"></a>音频

* 如果在使用 Windows Mixed Reality 耳机之前在主机 PC 上启用 Cortana，则可能会丢失适用于你在 Windows Mixed Reality 主页上放置的应用的空间音效模拟。 
   * 解决方法是在连接到电脑的所有音频设备上启用 "Windows Sonic，耳机"，甚至在手机连接音频设备上启用：
      1. 在桌面任务栏上左键单击扬声器图标，然后从音频设备列表中选择。
      2. 右键单击桌面任务栏上的扬声器图标，然后在 "扬声器设置" 菜单中选择 "Windows Sonic 用于耳机"。
      3. 为所有音频设备重复以下步骤， (终结点) 。
   * 在  >  启动 Windows Mixed Reality 之前，另一个选项是在桌面上的 "设置 **cortana** " 中关闭 "让 cortana 响应你好 cortana"。
* 当另一台多媒体 USB 设备 (（例如 web cam）) 使用 Windows Mixed Reality 耳机共享同一 USB 集线器 (外部计算机或 PC 内) ，在极少数情况下，耳机的音频插孔/耳机可能有蜂鸣声或根本没有音频。 你可以将耳机修复为与其他设备共享同一集线器的 USB 端口，或者断开连接/禁用其他 USB 多媒体设备。
* 在极少数情况下，主机 PC 的 USB 集线器无法为 Windows Mixed Reality 耳机提供足够的电量，你可能会注意到耳机突然出现噪音激增。

#### <a name="holograms"></a>全息影像

* 如果你在 Windows Mixed Reality 主页中放置了大量全息影像，则某些影像可能会消失，并在你查找时重新出现。 若要避免出现这种情况，请删除 Windows Mixed Reality 主页的部分全息影像。

#### <a name="motion-controllers"></a>运动控制器

* 如果未将输入路由到耳机，则当运动控制器位于房间边界旁边时，它会短暂消失。 按 Win + Y 以确保桌面监视器上出现蓝色横幅可以解决此问题。 
* 有时，当你在 Microsoft Edge 中单击网页时，内容将缩放，而不是单击。

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 主页中的桌面应用

* 截图工具不适用于桌面应用。
* 桌面应用在重新启动时不会保留设置。
* 如果你在桌面上使用混合现实门户预览，则在 Windows Mixed Reality 主页中打开桌面应用时，你可能会注意到无限镜像效果。 
* 运行桌面应用可能会导致非超 Windows Mixed Reality 电脑上出现性能问题;不建议使用此方法。  
* 桌面应用可能会自动启动，因为桌面上不可见的窗口有焦点。 
* 桌面用户帐户控制提示会使耳机显示黑色，直到完成提示。

#### <a name="windows-mixed-reality-for-steamvr"></a>适用于 SteamVR 的 Windows Mixed Reality

* 你可能需要在更新后启动混合现实门户，以确保 Windows 10 2018 年4月更新的必需软件更新在启动 SteamVR 之前已完成。 
* 你必须在最新版本的 Windows Mixed Reality 上才能使 SteamVR 保持与 Windows 10 2018 年4月版更新兼容。 请确保为 SteamVR 的 Windows Mixed Reality 启用了自动更新，此功能位于流中库的 "软件" 部分。  

#### <a name="other-issues"></a>其他问题

>[!IMPORTANT]
>推送到内部版本的 Windows 10 4 月2018更新的早期版本 (版本 17134.5) 缺少运行 Windows Mixed Reality 所需的软件。 如果使用 Windows Mixed Reality，建议避免使用此版本。 

在此更新的初始版本中使用 Surface Book 2 时，我们发现了性能回归 (10.0.17134.1) 我们在即将推出的更新修补程序中进行修复。 建议你等待，直到手动更新或等待更新正常推出。

## <a name="provide-feedback-and-report-issues"></a>提供反馈和报告问题

使用 [HoloLens 或 Windows 10 电脑上的反馈中心应用](/windows/mixed-reality/give-us-feedback) 提供反馈和报告问题。 使用反馈中心可确保包括所有必要的诊断信息，以帮助我们的工程师快速调试和解决问题。

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