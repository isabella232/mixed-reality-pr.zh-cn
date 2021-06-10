---
title: 选择 Unity 版本和 XR 插件
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity 和 XR 插件建议。
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit， mixedrealitytoolkit-unity， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity
ms.openlocfilehash: da171db41e508fe556d8645b23f12f6f437446a1
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908230"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>选择 Unity 版本和 XR 插件

虽然我们 **目前建议安装 Unity 2019.4 LTS，** 以及使用旧版内置 XR 进行混合现实开发，但也可使用其他 Unity 配置生成应用。

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (建议) 

Microsoft 当前推荐的用于 HoloLens 2 和 Windows Mixed Reality 的 Unity 配置是使用旧版内置 XR 支持的 **Unity 2019.4 LTS。**

安装和管理 Unity 的最佳方式是通过 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>。 安装后，打开 Unity 中心：

1. 选择" **安装"选项卡** ，然后选择" **添加"**
2. 选择"Unity 2019.4 LTS"，然后单击"下一 **步"**

![Unity 中心安装新版本](images/unity-hub-img-01.png)

3. 检查"平台" **下的以下组件**
    * **通用 Windows 平台生成支持** 
    * **Windows 生成支持 (IL2CPP)**

![Unity 通用 Windows 平台生成支持选项](../images/Unity_Install_Option_UWP.png)

4. 如果在未安装这些选项的情况下安装了 Unity，可以通过 Unity 中心的"添加模块 **"菜单** 添加它们：

![Unity Windows 生成支持选项](../images/Unity_Install_Option_UWP2.png)

若要开始使用 Unity 2019.4 LTS 中的旧版内置 XR，请单击此处：

> [!div class="nextstepaction"]
> [设置旧版内置 XR](legacy-xr-support.md)

> [!NOTE]
> 自 Unity 2019 起，Unity 已弃用其旧版内置 XR 支持。  虽然 Unity 2019 确实提供了新的 XR 插件框架，但由于 Azure 空间定位点与 AR Foundation 2 不兼容，Microsoft 当前不建议在 Unity 2019 中提供该路径。  在 Unity 2020 中，XR 插件框架支持 Azure 空间定位点。

如果要为 HoloLens (第一代) 开发应用，这些头戴显示设备在具有旧版内置 XR 的 Unity 2019 LTS 中仍受支持，以在 Unity 2019 LTS 的整个生命周期中到 2022 年年中。

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

如果使用 **Unity 2020.3 LTS，** 可以使用 **Windows XR** 插件开发HoloLens 2和Windows Mixed Reality应用程序。

但是，存在一些已知问题，这些问题会影响全息影像的稳定性和其他HoloLens 2： 

* 使用生成目标通用 Windows 平台全息应用远程处理应用程序无法工作。
* Unity 图形作业系统默认为打开状态，即使它与 HoloLens 项目不兼容。

如果选择在 Unity 2020 中立即开始新项目，请务必在交付应用之前，跟进后续几个月的更新 Unity 版本和 Windows XR 插件生成。  这将确保用户获得适当的全息影像稳定性。

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