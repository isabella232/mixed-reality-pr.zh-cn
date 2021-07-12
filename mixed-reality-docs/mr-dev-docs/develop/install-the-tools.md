---
title: 安装工具
description: 从这里开始，了解最新版本的 Unity、Visual Studio，以及推荐用于 HoloLens 和 VR 开发的工具。
author: thetuvix
ms.author: alexturn
ms.date: 05/11/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: 1317d37fede9c714cebdbe7eb9b0c334f1e5fd1a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394351"
---
# <a name="install-the-tools"></a>安装工具

获取为 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备生成应用程序所需的工具。 Windows Mixed Reality 开发没有单独的 SDK；将使用 Visual Studio 和 Windows 10 SDK。

没有混合现实设备？ 可以安装 [HoloLens 仿真器](platform-capabilities-and-apis/using-the-hololens-emulator.md)来测试混合现实应用的某些功能，而无需使用 HoloLens。 还可以使用 [Windows Mixed Reality 模拟器](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)来测试用于沉浸式头戴显示设备的混合现实应用。

建议安装 Unity 或 Unreal 游戏引擎，这是开始创建混合现实应用的最简单方法。 不过，如果你想要使用自定义引擎，则也可以针对 DirectX 生成应用。

如果你使用的是 Unity，则可以使用 [Unity 的混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)的输入模拟来测试各种类型的输入交互，例如手势跟踪和眼动跟踪输入。 对于 Unreal 项目，使用 [UX 工具插件](https://github.com/microsoft/MixedReality-UXTools-Unreal)来测试常见的输入交互和用户体验功能。

>[!TIP]
>将此页面添加为书签并定期检查，以便及时了解推荐用于混合现实开发的每种工具的最新版本。

<br>

## <a name="installation-checklist"></a>安装清单

| 工具 | 注释 |
|---------|---------|
| ![Windows 徽标](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**（手动安装链接）</a><br><br>安装最新版本的 Windows 10，以便电脑的操作系统与正在为其生成混合现实应用程序的平台匹配。  | **安装 Windows 10** <br> 可以通过“设置”中的“Windows 更新”，或者使用左栏中的链接创建安装媒体，来安装最新版本的 Windows 10。 <br><br>有关每个 Windows 10 版本提供的最新混合现实功能的信息，请参阅[当前发行说明](/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md)。 通过“设置”>“更新和安全”>“对于开发人员”在电脑上启用开发人员模式。 <br><br> **企业和公司管理电脑的注意事项**<br>如果你的电脑由组织的 IT 部门管理，可能需要与他们联系才能进行更新。 <br><br> **Windows 的“N”版本**<br> Windows 的“N”版本不支持 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备。 |
| ![Visual Studio 徽标图像](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019（16.8 或更高版本）** （安装链接）</a> <br><br>适用于 Windows 等的功能齐全的集成开发环境 (IDE)。 将使用 Visual Studio 来编写代码、调试、测试和部署。 | **安装 Visual Studio 2019** <br> 请确保安装以下工作负载： <br><br>*● 使用 C++ 的桌面开发*<br>*● 通用 Windows 平台 (UWP) 开发*<br>●使用 Unity 进行游戏开发（如果计划使用 Unity）<br><br>在 UWP 工作负荷中，请确保包含以下组件以便安装：<br><br>● Windows 10 SDK 版本 10.0.19041.0 或 10.0.18362.0<br>● USB 设备连接（通过 USB 进行 HoloLens 部署/调试所需）<br>● C++ (v142) 通用 Windows 平台工具（使用 Unity 时必需）<br><br>有关 HoloLens（第一代）和桌面 Windows Mixed Reality 头戴显示设备的说明<br>如果仅针对桌面 Windows Mixed Reality 头戴显示设备或 HoloLens（第 1 代）开发应用程序，则可以使用 Visual Studio 2017 和它安装的 Windows SDK。<br><br>**已知问题**<br>在 Visual Studio 2019 版本16.0 中调试混合现实应用时存在一些已知问题。  请确保更新到 Visual Studio 2019 版本 16.8 或更高版本。 |
| ![Visual Studio 徽标](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2165258" target="_blank">HoloLens 2 仿真器（Windows 全息版 21H1，2021 年 6 月更新）（安装链接：10.0.20348.1007）</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens（第一代）仿真器**（安装链接：10.0.17763.134）</a> <br><br>使用可选仿真器可在没有 HoloLens 的情况下在 HoloLens 虚拟机映像上运行应用程序。<br> <br> | 有关如何开始使用可选仿真器的详细信息，请参阅[使用 HoloLens 仿真器](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md)。<br> <br> 系统必须支持 Hyper-V 才能成功安装仿真器。 有关详细信息，请参阅下面的“系统要求”部分。 <br> <br> HoloLens（第一代）仿真器的说明 <br>  若要成功完成安装，需要 Visual Studio 2017。 若要使用 Visual Studio 2019 安装 HoloLens（第一代）仿真器，则需要取消选择 VS 模板，然后[从 Visual Studio Marketplace 进行安装](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)。 |

## <a name="install-your-engine-of-choice"></a>安装你选择的引擎

现在，你已准备好 Windows 10、Visual Studio 和 Windows 10 SDK，可安装并设置你选择的引擎。

> [!div class="nextstepaction"]
> [选择引擎](choosing-an-engine.md)

## <a name="troubleshooting"></a>疑难解答

### <a name="setting-developer-mode-is-grayed-out"></a>“开发人员模式”设置呈灰显

如果你在设备上启用开发人员模式时遇到问题，则你可能不是[设备所有者](/hololens/security-adminless-os)。 在多用户模式下，最先使用设备的用户就是设备所有者，后续的任何用户都没有必需的权限来启用开发人员模式或其他配置更改。 但存在一个例外，在 Autopilot 环境中，第一个用户可能不是设备所有者；有关详细信息，可参阅 [HoloLens 安全文档](/hololens/security-adminless-os#device-owner)。

可能的解决方案包括：

* 要求设备所有者在将设备递给其他用户或开发人员之前启用开发人员模式
* 建议你的 IT/MDM 管理员为特定设备或开发人员设备组启用 [ApplicationManagement/AllowDeveloperUnlock 策略](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。
    * 此策略可通过[预配包](/hololens/hololens-provisioning)或[适合 HoloLens 设备的 MDM](/hololens/hololens-mdm-configure)来进行设置
* 使用[高级恢复助理 (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> 有关设备管理的详细信息，可参阅 [HoloLens 设备管理](/hololens/hololens-csp-policy-overview)概述。

#### <a name="i-cant-deploy-over-usb"></a>我无法通过 USB 进行部署

如果你没法通过 USB 直接部署应用程序，请确保你满足了上述所有安全要求，并按照我们的[分步教程](unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)操作。
