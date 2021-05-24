---
title: 选择 Unity 版本和 XR 插件
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity 和 XR 插件建议。
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: febeb46972935a02d9c945e2a0cafabebedd0715
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333379"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>选择 Unity 版本和 XR 插件

尽管我们目前 **建议安装 Unity 2019.4 LTS 并使用旧式内置 XR** 进行混合现实开发，但也可以使用其他 Unity 配置来构建应用。

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (建议) 

Microsoft 当前推荐用于 HoloLens 2 和 Windows Mixed Reality 开发的 Unity 配置是 **使用旧内置 XR 支持的 unity 2019.4 LTS** 。

安装和管理 Unity 的最佳方式是通过 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity 中心]</a>进行。 安装后，打开 Unity 中心：

1. 选择 "**安装**" 选项卡，然后选择 "**添加**"
2. 选择 Unity 2019.4 LTS，并单击 "**下一步**"

![Unity 中心安装新版本](images/unity-hub-img-01.png)

3. 检查 **"平台" 下的** 以下组件
    * **通用 Windows 平台生成支持** 
    * **Windows 生成支持 (IL2CPP)**

![Unity 通用 Windows 平台生成支持选项](../images/Unity_Install_Option_UWP.png)

4. 如果不使用这些选项安装 Unity，可以通过 Unity 中心中 **的 "添加模块"** 菜单添加它们：

![Unity Windows 生成支持选项](../images/Unity_Install_Option_UWP2.png)

若要开始处理 Unity 2019.4 LTS 中的旧内置 XR，请单击此处：

> [!div class="nextstepaction"]
> [设置旧版内置 XR](legacy-xr-support.md)

> [!NOTE]
> Unity 已弃用了它在 Unity 2019 中的旧内置 XR 支持。  虽然 Unity 2019 提供了新的 XR 插件框架，但 Microsoft 目前并未建议使用 Unity 2019 中的路径，因为 Azure 空间锚与 AR Foundation 2 不兼容。  在 Unity 2020 中，XR 插件框架支持 Azure 空间锚。

如果正在开发适用于 HoloLens (第一代) 的应用，则在 Unity 2019 LTS 中，这些耳机仍受支持，其中内置 XR 用于 Unity 2019 LTS 2022 到的完整生命周期。

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

如果使用的是 **Unity 2020.3 LTS**，则可以使用 **Windows XR 插件** 开发 HoloLens 2 和 Windows Mixed Reality 应用程序。

但是，存在一些已知问题，这些问题会影响全息影像的稳定性和其他HoloLens 2： 

* 使用生成目标通用 Windows 平台全息应用远程处理应用程序无法工作。
* Unity 图形作业系统默认为打开状态，即使它与 HoloLens 项目不兼容。

如果选择使用 Unity 2020，请务必升级到 Unity 2020.3.6f1 或更高版本，以确保用户体验适当的全息影像稳定性。

> [!div class="nextstepaction"]
> [使用 Windows XR 插件](windows-xr-plugin.md)

### <a name="using-openxr"></a>使用 OpenXR

Unity 2020.3 LTS 还支持混合 **现实 OpenXR** 插件的公共预览版。

混合现实 OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。 这样，你可以编写命中测试代码一次，该代码HoloLens 2 ARCore/ARKit 手机和平板电脑。 

今年稍后，具有 OpenXR 插件的 **Unity 2020.3 LTS** 将成为推荐的 Unity 配置，并且 Unity 中未来的 HoloLens 2 功能将仅通过此插件公开。

> [!div class="nextstepaction"]
> [使用 OpenXR 插件](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021.1

如果要尝试早期 Unity **2021.1** 版本，应前进到 **OpenXR** 插件，因为 Windows XR 插件已弃用。  从 Unity 2021.2 开始，OpenXR 插件将是混合现实开发的唯一路径，因为将不再支持 Windows XR 插件。

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

如果已有一个使用 Unity 2018.4 LTS 的项目，则 Unity 引擎在发布后将继续受支持 2 年。  Unity 2018 LTS 将于 2021 年春季终止服务。
