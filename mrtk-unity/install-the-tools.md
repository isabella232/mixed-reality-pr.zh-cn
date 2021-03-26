---
title: 安装工具
description: MRTK-Unity，安装工具文档页
author: polar-kev
ms.author: kesemple
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK, 混合现实工具包, 安装,最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器
ms.openlocfilehash: a22a032261f3734167b229618f40db112b43c0f7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "102236958"
---
# <a name="install-the-tools"></a>安装工具

获取为 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备生成应用程序所需的工具。 Windows Mixed Reality 开发没有单独的 SDK；将使用 Visual Studio 和 Windows 10 SDK。

没有混合现实设备？ 可以安装 [HoloLens 仿真器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)来测试混合现实应用的某些功能，而无需使用 HoloLens。 还可以使用 [Windows Mixed Reality 模拟器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)来测试用于沉浸式头戴显示设备的混合现实应用。

此页面将引导你完成将 MRTK 与 Unity 结合使用所需的工具。 如果有兴趣探索其他混合现实开发平台，请查看[混合现实开发简介](https://docs.microsoft.com/windows/mixed-reality/develop/development?tabs=unity)页面。

可以使用 [Unity 的混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)的输入模拟来测试各种类型的输入交互，例如手势跟踪和眼动跟踪。

|提示：将此页面添加为书签并定期检查，以便及时了解推荐用于混合现实开发的每种工具的最新版本。|
|---|

## <a name="installation-checklist"></a>安装清单

| 工具 | 注释 |
|---------|---------|
| ![Windows 徽标](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**（手动安装链接）</a><br><br>安装最新版本的 Windows 10，以便电脑的操作系统与正在为其生成混合现实应用程序的平台匹配。  | **安装 Windows 10** <br> 可以通过“设置”中的“Windows 更新”，或者使用左栏中的链接创建安装媒体，来安装最新版本的 Windows 10。 <br><br>有关每个 Windows 10 版本提供的最新混合现实功能的信息，请参阅[当前发行说明](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)。 通过“设置”>“更新和安全”>“对于开发人员”在电脑上启用开发人员模式。 <br><br> **企业和公司管理电脑的注意事项**<br>如果你的电脑由组织的 IT 部门管理，可能需要与他们联系才能进行更新。 <br><br> **Windows 的“N”版本**<br> Windows 的“N”版本不支持 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备。 |
| ![Visual Studio 徽标图像](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019（16.8 或更高版本）** （安装链接）</a> <br><br>适用于 Windows 等的功能齐全的集成开发环境 (IDE)。 将使用 Visual Studio 来编写代码、调试、测试和部署。 | **安装 Visual Studio 2019** <br> 请确保安装以下工作负载： <br><br>*● 使用 C++ 的桌面开发*<br>*● 通用 Windows 平台 (UWP) 开发*<br><br>在 UWP 工作负载内，如果要针对 HoloLens 进行开发，请务必选中以下可选组件：<br><br>*● USB 设备连接*<br><br>**有关 Unity 的注意事项**<br>除非你出于特定目的有意尝试安装较新（非 LTS）版本的 Unity，否则我们建议不要将 Unity 工作负载作为 Visual Studio 安装的一部分进行安装，而是安装下文所述的 Unity 2019 LTS 流。<br><br>**已知问题**<br>在 Visual Studio 2019 版本16.0 中调试混合现实应用时存在一些已知问题。  请确保更新到 Visual Studio 2019 版本 16.8 或更高版本。 |
| ![Windows 徽标](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** （手动安装链接）</a> <br><br>提供用于在 HoloLens 2 上生成 Windows 10 应用的最新标头、库、元数据和工具。 | **要生成 HoloLens 2 应用，必须安装 Windows SDK 内部版本 18362 或更高版本。**<br> <br> 如果仅针对桌面 Windows Mixed Reality 头戴显示设备或 HoloLens（第 1 代）开发应用程序，则可以使用 Visual Studio 2019 安装的 Windows SDK。 |
| ![Visual Studio 徽标](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2154784" target="_blank">HoloLens 2 仿真器（Windows Holographic 版本 20H2，2021 年 2 月更新）（安装链接：10.0.19041.1134）</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens（第一代）仿真器**（安装链接：10.0.17763.134）</a> <br><br>使用仿真器可在没有 HoloLens 的情况下在 HoloLens 虚拟机映像上运行应用程序。<br> <br> | 有关如何开始使用仿真器的详细信息，请参阅[使用 HoloLens 仿真器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)。<br> <br> 系统必须支持 Hyper-V 才能成功安装仿真器。 有关详细信息，请参阅下面的“系统要求”部分。 <br> <br> HoloLens（第一代）仿真器的说明 <br>. 若要使用 Visual Studio 2019 安装 HoloLens（第一代）仿真器，则需要取消选择 VS 模板，然后[从 Visual Studio Marketplace 进行安装](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)。 |

## <a name="unity"></a>Unity

现在你已准备好 Windows 10、Visual Studio 和 Windows 10 SDK，可使用 Unity 作为引擎用进行构建。

### <a name="1-download-the-latest-version"></a>1.下载最新版本

建议使用 [Unity LTS（长期支持）](https://unity3d.com/unity/qa/lts-releases)流作为启动新项目时使用的最佳版本，更新到最新版本可获得最新的稳定修补程序。

* 当前文档将使用 [Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)。 也支持 Unity 2018.4 LTS。
* 如果要将 [混合现实 OpenXR](https://docs.microsoft.com/windows/mixed-reality/develop/unity/openxr-getting-started) 预览功能用于 MRTK，需要使用 Unity 2020.2 或更高版本。
* 如果由于特定原因需要使用其他版本的 Unity，Unity 支持并行安装不同的版本。

### <a name="2-install-the-mixed-reality-feature-tool"></a>2.安装混合现实功能工具

[混合现实功能工具](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)是开发人员发现混合现实功能包并将其添加到 Unity 项目中的一种新方式。

你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。 验证所需的包后，混合现实功能工具会将它们下载到所选的 Unity 项目中。

#### <a name="importing-the-mixed-reality-toolkit"></a>导入混合现实工具包

可遵循下面的[安装和使用说明](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#system-requirements)，选择“混合现实工具包基础”包，下载混合现实工具包。

如果想要从 Github 手动下载 MRTK 包，请访问发布页面（[Mixed Reality Toolkit-Unity (GitHub)](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)）。

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3.设置电脑来进行混合现实开发

Windows 10 SDK 在 Windows 10 操作系统上效果最佳。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。 请注意，并非所有工具都在较早的操作系统上受支持。

| 备注：可针对 HoloLens 和/或 VR 沉浸式头戴显示设备开发和部署应用。 确保满足以下要求（具体由你的需求而定）。 |
|---|

#### <a name="for-hololens-development"></a>对于 HoloLens 开发

在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 [Unity](https://docs.unity3d.com/Manual/system-requirements.html) 和 Visual Studio 的系统要求。 如果想要在 HoloLens 设备上运行应用，需要按照 [Windows 设备门户设置说明](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal)进行操作。 如果打算使用 [HoloLens 仿真器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)，还需要确保电脑满足 [HoloLens 仿真器系统要求](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#hololens-emulator-system-requirements)。

若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)。

如果你打算针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。

### <a name="hololens-troubleshooting"></a>HoloLens 故障排除

“开发人员模式”设置呈灰显

如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](https://docs.microsoft.com/hololens/security-adminless-os)。 在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。 但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](https://docs.microsoft.com/hololens/hololens2-compliance)。

可能的解决方案包括：

* 要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式
* 建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。
此策略可通过[预配包](https://docs.microsoft.com/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure)来进行设置
* 使用[高级恢复助理 (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)

| 备注：有关设备管理的详细信息，可参阅 HoloLens 设备管理概述。|
|---|

我无法通过 USB 进行部署

如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02#building-your-application-to-your-hololens-2)操作。

沉浸式 (VR) 头戴显示设备要求

| 备注：以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新。|
|---|

| 警告：不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范。|
|---|

如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。

某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。

. | 最小值 | 建议
--- |--- |---
处理器 | 笔记本：Intel 移动 Core i5 第 7 代 CPU，双核超线程 桌面：Intel 桌面 i5 第 6 代 CPU，双核超线程或 AMD FX4350 4.2Ghz 四核等效 CPU| 桌面：Intel 桌面 i7 第 6 代（6 核）或 AMD Ryzen 5 1600（6 核，12 线程）GPU | 笔记本：NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU 桌面：NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU | 桌面：NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU
GPU 驱动程序 WDDM 版本 | WDDM 2.2 驱动程序
散热设计功耗 | 15W 或更高
图形显示端口 | 1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）
显示器分辨率 | 分辨率：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色
内存 | 8 GB 或更大的 RAM | 16 GB 或更高的 RAM
存储 | 大于 10 GB 的额外可用空间
USB 端口 | 1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) 注意：USB 必须提供至少 900mA
Bluetooth | 蓝牙 4.0（用于连接配件）

## <a name="next-development-checkpoint"></a>下一个开发检查点

现在你已安装这些工具，建议学习 MRTK HoloLens 2 教程系列。
> [!div class="nextstepaction"]
> [HoloLens 2 教程系列](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)