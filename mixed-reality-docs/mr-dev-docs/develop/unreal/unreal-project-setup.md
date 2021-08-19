---
title: 设置 Unreal 项目
description: 了解如何使用最新版 Unreal Engine 和混合现实功能工具设置项目。
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, 混合现实, 开发, 功能, 新项目, 仿真器文档, 指南, 全息影像, 游戏开发, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 最新, 工具, 开始使用, 基本, unreal, 工具包, 中心, 安装, Windows, HoloLens, openxr, mrtk
ms.openlocfilehash: fee0e9a9deb92dffca742e19ebe27d2dd4cb53c0
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905557"
---
# <a name="setting-up-your-unreal-project"></a>设置 Unreal 项目

建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。

转到 Epic Games Launcher 的“库”选项卡，选择“启动”旁的下拉箭头，然后单击“选项”。   在“目标平台”下，选择“HoloLens 2”，然后单击“应用”。
![Unreal 安装选项 HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>导入 Unreal 的混合现实工具包

![MRTK](../../design/images/MRTK_UX_Hero.png)

混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。

如果还没有混合现实项目，请按照 [HoloLens 2 入门教程](tutorials/unreal-uxt-ch1.md)的前 3 个部分准备好项目供 MRTK 使用。

### <a name="introducing-the-mrtk-hub-for-unreal"></a>适用于 Unreal 的 MRTK 中心简介

建议使用 MRTK 中心获取 MRTK 插件。 这是开发人员发现和更新 Microsoft Mixed Reality 插件并将其添加到 Unreal 项目的一种新方式。 无需退出 Unreal 编辑器，即可查看插件、了解其依赖项并将其安装到你的项目中。

- 发现新的 Microsoft Mixed Reality 插件，并将其依赖项安装到你的 Unreal 项目中。
- 将 Microsoft Mixed Reality 插件保持在最新状态。
- 如果不再需要 Microsoft Mixed Reality 插件，请将其从项目中删除。

> [!NOTE]
> 适用于 Unreal 的 MRTK 中心仅可用于 Unreal Engine 4.26 及更高版本。 对于 Unreal Engine 4.25，可从 Unreal Engine 市场或 GitHub 获取 MRTK 插件，如[入门部分](unreal-development-overview.md#1-getting-started)所述。

#### <a name="installing-the-mrtk-hub"></a>安装 MRTK 中心

从 [Unreal Engine 市场](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-toolkit-hub)下载插件，打开你的项目，然后从“插件”菜单的“混合现实”部分启用插件 。 出现提示时，重启编辑器。

![启用 MRTK 中心插件](images/hub-enable-plugin.png)

为项目启用插件后，可通过工具栏按钮访问中心。

![打开 MRTK 中心窗口](images/hub-toolbar.png)

#### <a name="installing-mixed-reality-plugins"></a>安装混合现实插件

若要使用中心安装插件，请选择要添加到项目的插件，然后按“安装”按钮。 若要下载插件，请验证“问题”框中是否没有冲突，然后按“确认” 。 下载插件后，系统会提示你重启编辑器。 遗憾的是，我们无法为你自动重启编辑器。有时在安装完成之前，新的编辑器实例会启动。

![使用 MRTK 中心安装插件](images/hub-download.png)

关闭编辑器后，你将看到一个命令提示符，附带有一个进度栏，用于解压缩下载的插件。 将针对要安装的每个插件显示一个命令提示符。 完成解压缩后，可重新打开编辑器，然后继续你的[混合现实开发之旅](unreal-quickstart.md)。

![MRTK 中心通过命令提示符解压缩插件](images/hub-unpack.png)

> [!IMPORTANT]
> 安装插件后，必须将它签入到源代码管理，例如任何其他项目级别的插件。

#### <a name="updating-mixed-reality-plugins"></a>更新混合现实插件

若要使用中心更新插件，请从列表中选择要更新的插件，然后按“安装”按钮。 若要下载更新后的插件，请验证“问题”框中是否没有冲突，然后按“确认” 。 系统将提示你重启编辑器来完成更新。 插件更新在编辑器启动期间完成，因此在重新打开编辑器之前，无需等待任何解压缩完成。

![通过 MRTK 中心更新插件](images/hub-update.png)

#### <a name="removing-mixed-reality-plugins"></a>删除混合现实插件

若要使用中心卸载插件，请选择要删除的插件，然后从下拉列表中选择已安装的版本。 若要删除插件，请验证“问题”框中是否没有冲突，然后按“确认” 。 系统将提示你重启编辑器来完成删除。

![通过 MRTK 中心删除插件](images/hub-remove.png)

#### <a name="reviewing-changes-and-detecting-incompatibilities"></a>查看更改并检测不兼容的情况

可在中心窗口底部查看将对项目进行的确切更改。 在这里，可看到将在项目中添加或删除的插件，以及进行更改时可能导致问题的任何潜在不兼容性。

> [!NOTE]
> 问题列表将在 Unreal 引擎版本和插件依赖项版本中显示不兼容，但它不会自动修复问题，也不会自动提出问题修复建议。

![尝试安装不兼容的插件](images/hub-issues.png)

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unreal 徽标图像](../images/MRTK-Unreal-Banner.png)<br>**混合现实工具包 - Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。