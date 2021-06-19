---
title: 使用混合现实 OpenXR 插件
description: 了解如何为 Unity 项目启用混合现实 OpenXR 插件。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: ffec0cbe2ea9fd87cbb5f38010dad2d64e2e82ee
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392675"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a>使用混合现实 OpenXR 插件

对于面向 Unity 2020 的开发人员构建 HoloLens 2 或混合现实应用程序，可以使用 OpenXR 插件代替 WindowsXR 插件，以实现更好的跨平台兼容性。  混合现实 OpenXR 插件还适用于最新的 [混合现实功能工具](welcome-to-mr-feature-tool.md)。

## <a name="prerequisites"></a>先决条件

* 最新 Unity 2020.3 LTS，建议 2020.3.6 f1 或更高版本。
* 最新 Unity OpenXR 插件，建议1.2 或更高版本
* [适用于 HoloLens 2 开发的](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)最新工具
* 最新 MRTK (可选) ，建议版本2.6 或更高版本
* 最新混合现实 OpenXR 插件，建议版本0.9.5 或更高版本

> [!NOTE]
> 如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。 但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。

## <a name="setting-up-your-project-with-mrtk"></a>用 MRTK 设置项目

用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。

> [!div class="nextstepaction"]
> [使用 MRTK 设置项目](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。

## <a name="manual-setup-without-mrtk"></a>无 MRTK 的手动设置

安装具有新的混合现实功能工具应用程序的 OpenXR 插件。 按照 [安装和使用说明](welcome-to-mr-feature-tool.md) ，在混合现实工具包类别中选择 **混合现实 OpenXR 插件** 包：

![突出显示了 "打开 xr" 插件的混合现实功能工具包窗口](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>设置生成目标

如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：

1. 选择 **文件 > 生成设置 ...**
2. 选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"
3. 将“体系结构”设置为“ARM 64” 
4. 将“目标设备”设置为“HoloLens” 
5. 将“生成类型”设置为“D3D” 
6. 将“UWP SDK”设置为“最近安装的版本” 

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>为 OpenXR 配置 XR 插件管理

若要将 OpenXR 设置为 Unity 中的运行时：

1. 在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"
2. 在设置列表中，选择 " **XR 插件管理**"
3. 选中 " **在启动时初始化 XR"** 和 " **OpenXR** " 框
4. 如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 " **Microsoft HoloLens 功能集**"

![在 Unity 编辑器中打开的 "项目设置" 面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-img-05.png)

## <a name="optimization"></a>优化

如果你正在开发 HoloLens 2，请导航到 **混合现实> OpenXR > 应用适用于 hololens 2 的推荐项目设置** ，以获得更好的应用性能。

![所选 OpenXR 打开的混合现实菜单项的屏幕截图](images/openxr-img-08.png)

> [!IMPORTANT]
> 如果在 " **OpenXR" 插件** 旁出现一个红色警告图标，请单击该图标，然后选择 " **全部修复** "，然后继续。 Unity 编辑器可能需要自动重启以使更改生效。

![OpenXR 项目验证窗口的屏幕截图](images/openxr-img-06.png)

你现在已准备好开始通过 Unity 中的 OpenXR 进行开发！  继续阅读下一节，了解如何使用 OpenXR 示例。

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>适用于 OpenXR 和 HoloLens 2 的 Unity 示例项目

查看示例 unity 项目的 [OpenXR 混合现实示例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 存储库展示如何使用混合现实 OpenXR 插件为 HoloLens 2 或混合现实耳机构建 unity 应用程序。

## <a name="using-mrtk-with-openxr-support"></a>结合使用 MRTK 与 OpenXR 支持

从2.5.3 版本开始，MRTK-Unity 支持混合现实 OpenXR 插件。

1. 再次打开 [混合现实功能工具](welcome-to-mr-feature-tool.md) 以安装混合现实工具包（如果尚未安装）。 OpenXR 支持在 **基础** 包中提供。
2. 转到检查器中的 MixedReality 工具包组件脚本，并切换到 **DefaultOpenXRConfigurationProfile** 配置文件：

    ![在检查器的混合现实工具包组件中切换 MRTK 配置的屏幕截图](images/openxr-img-11.png)

    1. 有关 [迁移到 OpenXR 的更深入信息](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，请参阅 MRTK 文档。

> [!NOTE]
> 从 MRTK 的早期版本进行升级时，请确保以下行位于 **资产/MixedRealityToolkit/link.xml** 文件中：
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 如果开始使用 MRTK 2.5.4 或更高版本，则默认情况下会添加此行。

## <a name="next-steps"></a>后续步骤

现在，你已为 OpenXR 配置了项目并有权访问示例，请查看我们的 OpenXR 插件当前支持的 [功能](openxr-supported-features.md) 。

## <a name="have-feedback"></a>是否有反馈？

OpenXR 仍是实验性的，因此我们非常感谢你的反馈，你可以向我们提供更好的帮助。 你将在 [Unity 论坛](https://aka.ms/unityforums)上查找我们，方法是使用 **Microsoft**  +  **OpenXR** 和 **HoloLens 2** 或 **Windows Mixed Reality** 标记论坛帖子。

## <a name="see-also"></a>另请参阅

* [配置项目时不使用 MRTK](configure-unity-project.md)
* [建议用于 Unity 的设置](recommended-settings-for-unity.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md#how-to-profile-with-unity)