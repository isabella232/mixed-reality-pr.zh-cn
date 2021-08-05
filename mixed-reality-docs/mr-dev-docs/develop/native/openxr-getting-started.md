---
title: OpenXR 入门
description: 开始在 Windows Mixed Reality 和 HoloLens 2 耳机上使用便携 OpenXR API 标准版。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，Windows Mixed Reality，OpenXR 开发人员工具，DirectX，本机，本机应用，自定义引擎，中间件，入门，101，预览版扩展，OpenXR 运行时版本，系统状态
ms.openlocfilehash: 6d334b491d231ab5987dd1bc6a3eb43f5e0fe30a82c6525bca1935fbf1cd83bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189140"
---
# <a name="getting-started-with-openxr"></a>OpenXR 入门

你可在桌面上的 HoloLens 2 或 Windows Mixed Reality 沉浸式头戴显示设备上使用 OpenXR 进行开发。  如果无权访问耳机，可以改为使用 HoloLens 2 Emulator 或 Windows Mixed Reality 模拟器。

## <a name="getting-started-with-openxr-for-hololens-2"></a>HoloLens 2 的 OpenXR 入门

开始开发 HoloLens 2 的 OpenXR 应用程序：

1. 设置 HoloLens 2 或按照说明[安装 HoloLens 2 模拟器的最新版本](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。 如果你使用的是最新的仿真程序映像，或者设备已更新其 OS，你应该已准备好 OpenXR 1.0。
2. 请确保已获得最新的 OpenXR 运行时，并在设备或模拟器中启动 **应用商店** 应用程序，并提供所有 [扩展](openxr.md#roadmap)。
    * 在右上方打开菜单，选择 " **下载和更新**"，然后选择 " **获取更新**"。  

> [!NOTE]
> 如果使用的是模拟器，则每次启动仿真程序时都会重置该仿真程序映像，因此最好的做法是确保使用[最新版本的 HoloLens 2 模拟器映像](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Windows Mixed Reality 耳机入门（OpenXR）

开始为沉浸式 Windows Mixed Reality 耳机开发 OpenXR 应用程序：

1. 请确保至少运行 Windows 10 2019 年5月更新 (1903) ，这是 Windows Mixed Reality 最终用户运行 OpenXR 应用程序的最低要求。  如果使用的是早期版本的 Windows 10，则可以通过使用<a href="https://www.microsoft.com/software-download/windows10" target="_blank">Windows 10 更新助手</a>进行升级。
2. 设置 Windows Mixed Reality 耳机，或按照说明[启用 Windows Mixed Reality 模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)。

就这么简单！  安装 Windows Mixed Reality OpenXR 运行时，并为所有 Windows Mixed Reality 用户自动激活运行时。  然后 Microsoft Store 会使运行时保持最新状态。

若要再次激活 Windows Mixed Reality OpenXR 运行时，请从 "开始"菜单启动混合现实门户，并在窗口顶部选择 "修复"。  如果缺少该按钮，则 OpenXR 运行时已处于活动状态。<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>获取 Windows Mixed Reality 的 OpenXR 开发人员工具

若要试用 Windows Mixed Reality OpenXR 运行时，可以<a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">为 Windows Mixed Reality 应用安装 OpenXR 开发人员工具</a>。  此应用提供了各种 OpenXR 功能的演示，同时提供了一个系统状态页，其中包含有关活动运行时和当前耳机的关键信息。

使用 HoloLens 2 模拟器时，为 Windows Mixed Reality 安装 OpenXR 开发人员工具的最简单方法是通过[Windows 设备门户](../platform-capabilities-and-apis/using-the-windows-device-portal.md)。 导航到 "OpenXR" 页，然后单击 "开发人员功能" 下的 "安装" 按钮，此操作也可在物理 HoloLens 2 设备上运行。

![Windows Mixed Reality 应用的 OpenXR 开发人员工具](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>生成示例 OpenXR 应用

如果尚未安装，请务必安装 OpenXR 开发所需 [的工具](../install-the-tools.md) 。

<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>项目显示了一个简单的 OpenXR 示例，其中包含 Win32 和 UWP HoloLens 2 项目文件在 Visual Studio 中。 由于解决方案包含 HoloLens UWP 项目，因此需要在 Visual Studio 中安装[通用 Windows 平台开发工作负载](../install-the-tools.md#installation-checklist)才能完全打开它。

虽然 Win32 和 UWP 项目文件是独立的，因为打包和部署的不同之处在于每个项目中的应用代码几乎完全相同！

生成 OpenXR Win32 desktop .EXE 后，可以将其与任何支持 OpenXR 的 desktop VR 平台上的 VR 耳机一起使用，无论是哪种耳机类型。

生成 OpenXR UWP 应用包后，可以将[该包部署](../platform-capabilities-and-apis/using-visual-studio.md)到 HoloLens 2 设备或 HoloLens 2 Emulator。

## <a name="learning-the-openxr-api"></a>Learning OpenXR API

有关 OpenXR API 的教程，请查看 Visual Studio 中的<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>示例的60分钟视频。  该视频演示了如何在您自己的引擎中使用 OpenXR API 的每个主要组件，同时还演示了一些在 OpenXR 上构建的应用程序。

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>将 OpenXR 加载程序集成到项目中

若要开始在现有项目中使用 OpenXR，你将包含 OpenXR 加载程序。  加载程序在设备上发现活动的 OpenXR 运行时，并提供对它实现的核心函数和扩展函数的访问权限。

可以从 Visual Studio 项目中[引用官方 OpenXR NuGet 包](#reference-official-openxr-nuget-package)，也可以在 Khronos GitHub 存储库中[包含官方 OpenXR 加载器源](#include-official-openxr-loader-source)。  这两种方法都可让你访问 OpenXR 1.0 核心功能，以及发布 `KHR` `EXT` 和 `MSFT` 扩展。

如果你有兴趣试用 `MSFT_preview` 扩展，可以在混合现实 GitHub 存储库[中复制预览版 OpenXR 标头](#using-preview-extensions)。

### <a name="reference-official-openxr-nuget-package"></a>引用官方 OpenXR NuGet 包

NuGet <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR** 包</a>是在 Visual Studio c + + 解决方案中引用预生成的 OpenXR 加载程序 .DLL 的最简单方法。  这样，你就可以访问 OpenXR 1.0 核心功能，还可以 `KHR` 发布 `EXT` 和 `MSFT` 扩展。

向 Visual Studio c + + 解决方案添加 OpenXR NuGet 包引用：
1. 在 **解决方案资源管理器** 中，右键单击将使用 OpenXR 的项目，然后选择 "**管理 NuGet 包 ...**"。
2. 切换到 " **浏览** " 选项卡并搜索 **OpenXR**。
3. 选择 **OpenXR** 包，然后在右侧的详细信息窗格中选择 "安装"。
4. 选择 "确定" 以接受对项目所做的更改。
5. 添加 `#include <openxr/openxr.h>` 到源文件，开始使用 OPENXR API。

若要查看 OpenXR API 的运行示例，请查看 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 示例应用。

### <a name="include-official-openxr-loader-source"></a>包括官方 OpenXR 加载程序源

如果你想要自己生成加载程序（例如，为了避免 .DLL 额外的加载程序），则可以将官方的 Khronos OpenXR 加载程序源提取到你的项目中。  这样，你就可以访问 OpenXR 1.0 核心功能，还可以 `KHR` 发布 `EXT` 和 `MSFT` 扩展。

若要开始操作，请按照<a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">GitHub 上的 Khronos OpenXR-SDK</a>存储库中的说明进行操作。  项目设置为使用 CMake 进行生成-如果你使用 MSBuild，则需要将代码复制到你自己的项目中。

## <a name="using-preview-extensions"></a>使用预览扩展

`MSFT_preview`[扩展路线图](openxr.md#roadmap)中列出的扩展是为了收集反馈而预览的实验性供应商扩展。  这些扩展仅适用于开发人员设备，并将在真正的扩展交付时删除。

如果你有兴趣试用可用 `MSFT_preview` 扩展，请执行以下步骤来更新你的项目：
1. 按照上述任一方法将 OpenXR 加载程序集成到项目中。
2. 将项目中的标准 OpenXR 标头替换为<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">GitHub 上混合现实 OpenXR</a>存储库中的预览标头。

若要在目标 HoloLens 2 或台式计算机上激活预览版扩展支持：
  1. 若要确保已获得最新的 OpenXR 运行时并提供所有 [扩展](openxr.md#roadmap) ，请从目标设备或模拟器中启动 **应用商店** 应用，打开右上方的菜单，选择 " **下载和更新** "，然后选择 " **获取更新**"。
  2. 从 Microsoft Store 将<a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">Windows Mixed Reality 应用的 OpenXR 开发人员工具</a>安装到目标设备上并运行它。
  3. 导航到 "**开发人员设置**" 选项卡，并启用 "**使用最新预览版 OpenXR 运行时**"。  这将在你的设备上启用预览版扩展，并激活预览扩展。
     ![Windows Mixed Reality 应用开发人员设置选项卡的 OpenXR 开发人员工具](images/mixed-reality-openxr-developer-tools-settings.png)
  4. 确认 OpenXR 开发人员工具的 "**系统状态**" 选项卡上显示的 **运行时版本** [Windows Mixed Reality 是否](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality)与计划尝试的预览扩展插件所需的版本相匹配。  如果是这样，则应在 " **扩展** " 列表中看到该扩展。  稳定扩展可用后，将删除其预览扩展。<br />
     ![Windows Mixed Reality 应用系统状态选项卡的 OpenXR 开发人员工具](images/mixed-reality-openxr-developer-tools-status.png)

请参阅 <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">混合现实 OpenXR</a> 存储库，以了解这些预览版扩展的文档以及如何使用它们的示例。

## <a name="troubleshooting"></a>疑难解答

如果在使用 OpenXR 开发时遇到问题，请查看 [故障排除提示](openxr-troubleshooting.md)。