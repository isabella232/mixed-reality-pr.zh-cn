---
title: 使用 Windows XR 插件
description: 了解如何使用 Windows XR 支持在具有和没有 MRTK 的情况下设置 Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity， 混合现实， 开发， 入门， 新项目， Windows Mixed Reality， UWP， XR， 性能， 旧版， mrtk， 窗口
ms.openlocfilehash: 44de6b418995b75d9e199f03922f89016b76c5cd
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743646"
---
# <a name="using-windows-xr-plugin"></a>使用 Windows XR 插件

对于面向 Unity 2020 的开发人员，Windows XR 插件允许访问 HoloLens 2 和 Windows Mixed Reality 头戴显示设备上的混合现实功能。  Unity 2019 也支持此插件，尽管在此版本上使用此插件时，Azure 空间定位点存在一些已知的不兼容。

虽然 Microsoft 和社区已创建开源工具（如混合现实工具包 [ (MRTK) ） ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 来自动设置 WMR 环境，但许多开发人员希望从头构建自己的体验。  以下文档将演示如何正确设置混合现实开发项目，无论你是否使用 MRTK。  需要更改的设置分为两类：每项目设置和按场景设置。

## <a name="setting-up-your-project-with-mrtk"></a>使用 MRTK 设置项目

用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。

> [!div class="nextstepaction"]
> [试用我们的 MRTK 教程](./tutorials/mr-learning-base-02.md?tabs=winxr)

有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。

## <a name="manual-setup-without-mrtk"></a>不带 MRTK 的手动设置

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：

1.  选择 **"文件>生成设置..."**
2.  在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**
3.  将“体系结构”设置为“ARM 64” 
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D” 
6.  将“UWP SDK”设置为“最近安装的版本” 
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出时创建[](../../design/app-views.md)沉浸式视图而不是 2D 视图：

1. 在 Unity 编辑器中，导航到"编辑 **>项目设置"，然后选择****"XR 插件管理"**

2. 选择 **"安装 XR 插件管理"**

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-5.png)

3. 选择 **"启动时初始化 XR"，****然后选择Windows Mixed Reality**

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-7.png)

4. 展开 **"XR 插件管理"部分，** 然后选择 **"Univeral Windows 平台设置"** 选项卡
5. 如果使用的是 Unity 2020 或更高版本，则会看到用于检查 **OpenXR** 或 **Windows Mixed Reality。** 
    * 可以选择任一运行时。  如果你专门针对 HoloLens 2 或 HP Reverb G2 进行开发，并决定试用 **OpenXR，** 请选择 OpenXR 框，查看使用适用于 Unity 的混合现实 [OpenXR](openxr-getting-started.md) 插件指南，在返回到本教程之前，请正确设置这些设备

> [!NOTE]
> 从 Unity 2020 LTS 开始，Microsoft 将采用 OpenXR 开发。  迁移到此路径时，在 Unity 2021.1 中，Windows XR 插件将在 2021.2 中弃用并删除，使 OpenXR 成为唯一受支持的路径。 有关详细信息，请参阅 [使用混合现实 OpenXR 插件](openxr-getting-started.md)。

6. 如果决定选择"深度提交 **Windows Mixed Reality，** 请选中所有框，将"深度提交模式"设置为"深度 **16 位"**

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中Windows Mixed Reality部分](images/wmr-config-img-8.png)