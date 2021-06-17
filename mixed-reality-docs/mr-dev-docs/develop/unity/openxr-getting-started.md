---
title: 使用混合现实 OpenXR 插件
description: 了解如何为 Unity 项目启用混合现实 OpenXR 插件。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr， unity， hololens， hololens 2， 混合现实， MRTK， 混合现实工具包， 增强现实， 虚拟现实， 混合现实头戴显示设备， 学习， 教程， 入门
ms.openlocfilehash: ffec0cbe2ea9fd87cbb5f38010dad2d64e2e82ee
ms.sourcegitcommit: adbe3baa6b1c284ed1c4fd796d8b5612c3ca3f42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2021
ms.locfileid: "112270432"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a>使用混合现实 OpenXR 插件

面向面向 Unity 2020 的开发人员HoloLens 2或混合现实应用程序，可以使用 OpenXR 插件而不是 WindowsXR 插件，以更好地实现跨平台兼容性。  混合现实 OpenXR 插件还适用于最新的 [混合现实功能工具](welcome-to-mr-feature-tool.md)。

## <a name="prerequisites"></a>先决条件

* 最新的 Unity 2020.3 LTS，推荐 2020.3.6f1 或以上版本。
* 最新的 Unity OpenXR 插件，推荐 1.2 或更高版本
* 用于 [开发HoloLens 2工具](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* 最新 MRTK (可选) ，推荐版本 2.6 或更高版本
* 最新的混合现实 OpenXR 插件，推荐版本 0.9.5 或更高版本

> [!NOTE]
> 如果要在 Windows 电脑上生成 VR 应用程序，则混合现实 OpenXR 插件不一定是必需的。 但是，如果要为 HP Reverb G2 控制器自定义控制器映射，或构建适用于 HOLOLENS 2 和 VR 头戴显示设备的应用，需要安装插件。

## <a name="setting-up-your-project-with-mrtk"></a>使用 MRTK 设置项目

用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。

> [!div class="nextstepaction"]
> [使用 MRTK 设置项目](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。

## <a name="manual-setup-without-mrtk"></a>不带 MRTK 的手动设置

使用新的混合现实功能工具应用程序安装 OpenXR 插件。 按照安装和 [使用说明操作，](welcome-to-mr-feature-tool.md) 在"混合现实工具包"类别中选择"混合现实 **OpenXR** 插件"包：

![混合现实功能工具包窗口，突出显示了打开的 xr 插件](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>设置生成目标

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：

1. 选择 **"文件>生成设置..."**
2. 在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**
3. 将“体系结构”设置为“ARM 64” 
4. 将“目标设备”设置为“HoloLens” 
5. 将“生成类型”设置为“D3D” 
6. 将“UWP SDK”设置为“最近安装的版本” 

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>为 OpenXR 配置 XR 插件管理

若要在 Unity 中将 OpenXR 设置为运行时，请执行以下操作：

1. 在 Unity 编辑器中，导航到 **"编辑>项目设置"**
2. 在"设置"列表中，选择 **"XR 插件管理"**
3. 选中"**启动时初始化 XR"和****"OpenXR"** 框
4. 如果以HoloLens 2为目标，请确保你位于 UWP 平台上，然后选择"Microsoft HoloLens **功能集"**

![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-img-05.png)

## <a name="optimization"></a>优化

如果要针对 HoloLens 2 进行开发，请导航到"混合现实> **OpenXR >应用** 针对 HoloLens 2 的建议项目设置，以获得更好的应用性能。

![已选中 OpenXR 的混合现实菜单项的屏幕截图](images/openxr-img-08.png)

> [!IMPORTANT]
> 如果在 **OpenXR** 插件旁边看到红色警告图标，请单击该图标并选择" **全部修复** "，然后再继续。 Unity 编辑器可能需要自动重启以使更改生效。

![OpenXR 项目验证窗口的屏幕截图](images/openxr-img-06.png)

现在，你已准备好在 Unity 中开始使用 OpenXR 进行开发！  继续学习下一部分，了解如何使用 OpenXR 示例。

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>OpenXR 和 HoloLens 2 的 Unity 示例项目

请查看 [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 示例存储库，了解示例 Unity 项目，了解如何使用混合现实 OpenXR 插件为 HoloLens 2 或混合现实头戴显示设备生成 Unity 应用程序。

## <a name="using-mrtk-with-openxr-support"></a>使用具有 OpenXR 支持的 MRTK

MRTK-Unity 2.5.3 版开始，支持混合现实 OpenXR 插件。

1. 再次 [打开混合现实功能工具](welcome-to-mr-feature-tool.md) 以安装混合现实工具包（如果尚未安装）。 OpenXR 支持位于 **Foundation 包** 中。
2. 转到检查器中的 MixedReality Toolkit 组件脚本，并切换到 **DefaultOpenXRConfigurationProfile** 配置文件：

    ![在检查器中切换混合现实工具包组件中的 MRTK 配置的屏幕截图](images/openxr-img-11.png)

    1. 有关迁移到 OpenXR 的更深入的信息，请参阅 [MRTK 文档](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)。

> [!NOTE]
> 从以前版本的 MRTK 升级时，请确保以下行位于 **Assets/MixedRealityToolkit.Generated/link.xml** 文件中：
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 如果从 MRTK 2.5.4 或更高版本开始，则默认情况下将添加此行。

## <a name="next-steps"></a>后续步骤

为 OpenXR 配置项目并有权访问示例后，请查看 OpenXR 插件中[](openxr-supported-features.md)当前支持的功能。

## <a name="have-feedback"></a>有反馈？

OpenXR 仍处于试验阶段，因此，我们感谢你提供的任何反馈来帮助改进它。 使用 [](https://aka.ms/unityforums)**Microsoft**  +  **OpenXR** 标记你的论坛帖子，并HoloLens 2或 Windows Mixed Reality。 

## <a name="see-also"></a>另请参阅

* [配置项目时不使用 MRTK](configure-unity-project.md)
* [建议用于 Unity 的设置](recommended-settings-for-unity.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md#how-to-profile-with-unity)