---
title: 全息远程处理
description: 文档全息远程处理 MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 637f68e5ad5f360aea4b5c0603a682d61d152a89
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144583"
---
# <a name="holographic-remoting"></a>全息远程处理

全息远程处理通过使用 Wi-Fi 或 USB 电缆连接，将电脑中的全息内容实时流式处理到你的 Microsoft HoloLens。 当开发混合现实应用程序时，此功能可以显著提高开发人员的工作效率。

下面所述的 XR SDK 是 unity [2019.3 和更高版本中的 unity 新 XR 管道](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。 有关将 XR SDK 与 MRTK 配合使用的详细信息，请参阅 [此处](../../configuration/getting-started-with-mrtk-and-xrsdk.md) 。 旧 XR 是指 Unity 2018 中包含的现有 XR 管道，在 Unity 2019.3 中已弃用，并已在 Unity 2020 中删除。

## <a name="initial-setup"></a>初始设置

若要启用到 HoloLens 的远程处理，确保项目使用的是最新的远程处理组件非常重要。

1. **> 包管理器打开窗口**
    - 如果使用旧版 XR：验证是否安装了最新版本的 **Windows Mixed Reality** 包。
    - 如果使用 XR SDK：验证是否安装了最新版本的 **WINDOWS XR 插件** 包。
1. 通过 Microsoft Store 确保在 HoloLens 上安装了最新的全息远程处理应用程序。

请继续阅读 [旧版 XR 安装说明](#legacy-xr-setup-instructions) 或 [XR SDK 安装说明](#xr-sdk-setup-instructions) ，具体取决于项目中使用的管道。

## <a name="legacy-xr-setup-instructions"></a>旧版 XR 安装说明

以下说明仅适用于使用 HoloLens 2 的远程处理。 如果仅通过 HoloLens (第一代) 执行远程处理，请跳到 [通过 Wi-fi 连接到 hololens](#connecting-to-the-hololens-with-wi-fi)。

使用 HoloLens 2 时，已向 MRTK 中添加了对远程处理表述的手势和眼睛跟踪数据的支持。 若要启用这些功能，请按照将 [DotNetWinRT 导入到项目](#import-dotnetwinrt-into-the-project)中所述的步骤进行操作。

导入后，下一步是选择 **混合现实工具包**  >  **实用工具**  >  **Windows mixed reality**  >  **检查配置**。 此步骤添加启用 DotNetWinRT 依赖关系的脚本定义。

> [!NOTE]
> 使用 Unity 2019.4 和更高版本时，无需运行检查配置实用程序。

若要启用手部眼部跟踪和眼动跟踪，请遵循调试HoloLens 2 **Unity** 包导入和相关部分进行远程处理的步骤。

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>调试HoloLens 2 Unity 包导入进行远程处理

如果HoloLens 2和眼动跟踪无法通过远程处理工作，则存在一些常见的潜在问题。 下面按应检查的顺序列出它们。

在 **Unity 2019.3** 或更高版本上运行时，这些问题尤其相关。

#### <a name="import-dotnetwinrt-into-the-project"></a>将 DotNetWinRT 导入项目

1. 下载 [混合现实功能工具](https://aka.ms/MRFeatureTool)

1. 在" **发现功能"视图中** ，选择" *混合现实 WinRT 投影"*

    ![选择 DotNetWinRT 包](../images/tools/remoting/SelectDotNetWinRT.png)

1. 单击 **"获取功能** "并继续 [导入包](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages)。

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT定义写入播放器设置

> [!NOTE]
> 使用 Unity 2019.4 及更高版本时，DOTNETWINRT_PRESENT定义包含在相应的 .asmdef 文件中，而不是 Unity Player 设置中。 "检查配置"步骤不是必需的。

从 MRTK 版本 2.5.0 开始，出于性能原因，#define自动设置此版本。 若要启用此标志，请使用"混合现实工具包实用工具  >    >  **"Windows Mixed Reality"**  >  **检查配置"** 菜单项。

> [!Note]
> "检查配置"项不显示确认。 若要确认已设置定义，请导航到 Unity 播放器设置。 在"UWP"选项卡下，选中"脚本定义符号的其他设置"下。 请确保DOTNETWINRT_PRESENT正确写入该列表。 如果存在，则此步骤成功。

![DotNetWinRT 存在](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>删除HoloLens 2远程处理支持

如果由于存在 DotNetWinRT 适配器而发生冲突或其他问题，请访问我们的帮助资源 之 [一](../../index.md#getting-help)。

## <a name="xr-sdk-setup-instructions"></a>XR SDK 安装说明

按照 [Windows Mixed Reality MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) 和 XR SDK 入门"页上的说明进行操作，并确保执行编辑器中 HoloLens 远程处理所需的步骤。

## <a name="connecting-to-the-hololens-with-wi-fi"></a>使用设备连接到 HoloLens Wi-Fi

配置项目后，可以与 HoloLens 建立连接。

1. 在 **">生成设置**"中，确保项目生成类型 **设置为通用 Windows 平台**
1. 在 HoloLens 上，启动 **全息远程处理** 应用程序。
1. 在 Unity 中，如果使用的是旧版 **XR) /Windows XR** 插件远程处理 (，请选择"Windows > XR > 全息仿真 ("（如果使用 XR SDK) ）。

    ![启动全息仿真](../images/tools/remoting/StartHolographicEmulation.png)

1. 将 **仿真模式设置为****"远程"到"设备"。**

    ![设置仿真模式](../images/tools/remoting/SelectEmulationMode.png)

1.  (**_仅适用于旧版 XR)_** 选择 **设备版本**。

    ![选择"设备版本"](../images/tools/remoting/SelectDeviceVersion.png)

1. 使用全息远程处理播放器应用程序显示的 IP 地址，设置" **远程计算机"** 字段。

    ![输入 IP 地址](../images/tools/remoting/EnterIPAddress.png)

1. 单击“连接”  。

> [!NOTE]
> 如果无法连接，请确保HoloLens 2连接到电脑并重启 Unity。

## <a name="connecting-to-the-hololens-with-usb-cable"></a>使用 USB 电缆连接到 HoloLens

USB 电缆连接提供更好的渲染质量和稳定性。 若要使用 USB 电缆连接，请从 HoloLens 设置Wi-Fi HoloLens 中的 HoloLens 断开连接，并启动全息远程播放器应用。 它将显示以 169 开头的 IP 地址。 在 Unity 的全息仿真设置中使用此 IP 地址进行连接。 识别 USB 电缆的 IP 地址后，可以安全地将 HoloLens 连接到Wi-Fi连接。

## <a name="starting-a-remoting-session"></a>启动远程处理会话

将 Unity 连接到 HoloLens 后，在编辑器中进入播放模式。

会话完成后，退出播放模式。

> [!NOTE]
> 某些版本的 Unity 存在一个已知问题，即编辑器在远程处理会话期间进入播放模式时可能会挂起。 加载项目时，如果全息窗口已打开，则可能会显示此问题。 若要确保此问题不会发生，请始终在退出 Unity 之前关闭全息对话。

## <a name="see-also"></a>另请参阅

- [全息远程处理故障排除和限制](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Microsoft 全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)