---
title: 使用 Windows XR 插件
description: 了解如何使用 Windows XR 支持设置具有和没有 MRTK 的 Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目，Windows Mixed Reality，UWP，XR，性能，旧，mrtk，Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938097"
---
# <a name="using-windows-xr-plugin"></a>使用 Windows XR 插件

对于面向 Unity 2020 的开发人员，Windows XR 插件允许在 HoloLens 2 和 Windows Mixed Reality 耳机上访问混合现实功能。  此插件在 Unity 2019 上也受支持，但在该版本上使用此插件时，Azure 空间锚有一些已知的不兼容性。

尽管 Microsoft 和社区创建了开源工具，例如 [混合现实工具包 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 将自动设置 WMR 环境，但许多开发人员希望从根本上构建他们的经验。  如果你使用的是 MRTK，则以下文档将演示如何正确设置用于混合现实开发的项目。  需要更改的设置分为两类：每个项目的设置和每场景设置。

## <a name="setting-up-your-project-with-mrtk"></a>用 MRTK 设置项目

用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。

> [!div class="nextstepaction"]
> [试用我们的 MRTK 教程](tutorials/mr-learning-base-01.md)

有关更多功能的详细信息，请参阅 [MRTK 的文档](/windows/mixed-reality/mrtk-unity) 。

## <a name="manual-setup-without-mrtk"></a>无 MRTK 的手动设置

如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：

1.  选择 **文件 > 生成设置 ...**
2.  选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"
3.  将 **体系结构** 设置为 **ARM 64**
4.  将 **目标设备** 设置为 **HoloLens**
5.  将 **生成类型** 设置为 **D3D**
6.  将 **UWP SDK** 设置为 **安装的最新版本**
7.  将 **生成配置** 设置为 **发布** ，因为调试存在已知的性能问题

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../design/app-views.md) 而不是2d 视图：

1. 在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"，然后选择 " **XR 插件管理**"

2. 选择 "**安装 XR 插件管理**"

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-5.png)

3. 选择 **"启动时初始化 XR" 和 "** **Windows Mixed Reality** "

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-7.png)

4. 展开 " **XR 插件管理** " 部分，并选择 " **通用 Windows 平台设置** " 选项卡
5. 如果使用的是 Unity 2020 或更高版本，则会看到用于检查 **OpenXR** 或 **Windows Mixed Reality** 的选项。 
    * 您可以选择 "运行时"。  如果你要专门针对 HoloLens 2 或 HP 回音 G2 进行开发，并决定尝试 **OpenXR**，请选择 "OpenXR" 框，并查看本指南，以 [了解如何使用适用于 Unity 的 Mixed Reality OpenXR 插件](openxr-getting-started.md) 为这些设备正确设置，然后再返回到本教程

> [!NOTE]
> 从 Unity 2020 LTS 开始，Microsoft 正在接纳 OpenXR 的开发。  随着我们迁移到此路径，在 Unity 2021.1 中，Windows XR 插件将被弃用并在2021.2 中删除，从而使 OpenXR 成为唯一支持的路径。 可以在 [使用混合现实 OpenXR 插件](openxr-getting-started.md)中找到详细信息。

6. 如果决定选择 **Windows Mixed Reality** 插件，请选中所有复选框，并将 **深度提交模式** 设置为 **深度16位**

![突出显示了 Windows Mixed Reality 部分的 "项目设置" 窗口的屏幕截图已在 unity 编辑器中打开](images/wmr-config-img-8.png)
