---
title: 设置 XR 配置
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity XR 配置建议。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394561"
---
# <a name="setting-up-your-xr-configuration"></a>设置 XR 配置

启动新的 Unity 项目时，可以使用三个不同的选项来处理 XR 需求： 
* OpenXR 插件
* Windows XR 插件
* 旧 XR 插件

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>用 MRTK 设置项目

用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。

> [!div class="nextstepaction"]
> [试用我们的 MRTK 教程](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。

### <a name="using-mrtk-with-openxr-support"></a>结合使用 MRTK 与 OpenXR 支持

MRTK-Unity 2.7 版本为混合现实 OpenXR 插件提供更好的支持。

再次打开 [混合现实功能工具](welcome-to-mr-feature-tool.md) 以安装混合现实工具包（如果尚未安装）。 OpenXR 支持在 **基础** 包中提供。

有关 [迁移到 OpenXR 的更深入信息](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，请参阅 MRTK 文档。

> [!NOTE]
> 从早于 **2.5.3** 的 MRTK 的早期版本进行升级时，请确保 **资产/MixedRealityToolkit 和 link.xml** 文件中有以下行：
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 如果开始使用 MRTK 2.5.4 或更高版本，则默认情况下会添加此行。

## <a name="manual-setup-without-mrtk"></a>无 MRTK 的手动设置

尽管 Microsoft 和社区创建了开源工具，例如 [混合现实工具包 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 将自动设置 WMR 环境，但许多开发人员希望从根本上构建他们的经验。

[!INCLUDE[](includes/xr/manual-setup.md)]
