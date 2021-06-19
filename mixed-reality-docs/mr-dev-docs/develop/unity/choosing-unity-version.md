---
title: 选择 Unity 版本和 XR 插件
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity 和 XR 插件建议。
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit， mixedrealitytoolkit-unity， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity
ms.openlocfilehash: 452692b1be98459cc242833149b1cfd91f0f4d4a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394404"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>选择 Unity 版本和 XR 插件

虽然我们 **目前建议安装 Unity 2019.4 LTS，** 以及使用旧版内置 XR 进行混合现实开发，但也可使用其他 Unity 配置生成应用。

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (建议) 

Microsoft 当前推荐的用于 HoloLens 2 和 Windows Mixed Reality 的 Unity 配置是使用旧版内置 XR 支持的 **Unity 2019.4 LTS。**

安装和管理 Unity 的最佳方式是通过 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>。 安装后，打开 Unity 中心：

1. 选择" **安装"选项卡** ，然后选择" **添加"**
2. 选择"Unity 2019.4 LTS"，然后单击"下一 **步"**

![Unity 中心安装新版本](images/unity-hub-img-2019.png)

3. 检查"平台" **下的以下组件**
    * **通用 Windows 平台生成支持** 
    * **Windows 生成支持 (IL2CPP)**

![Unity 通用 Windows 平台生成支持选项](images/Unity_Install_Option_UWP_2019.png)

4. 如果在未安装这些选项的情况下安装了 Unity，可以通过 Unity 中心的"添加模块 **"菜单** 添加它们：

![Unity Windows 生成支持选项](images/Unity_Install_Option_UWP2_2019.png)

若要开始使用 Unity 2019.4 LTS 中的旧版内置 XR，请单击此处：

> [!div class="nextstepaction"]
> [设置旧版内置 XR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> 自 Unity 2019 起，Unity 已弃用其旧版内置 XR 支持。  虽然 Unity 2019 确实提供了新的 XR 插件框架，但由于 Azure 空间定位点与 AR Foundation 2 不兼容，Microsoft 当前不建议在 Unity 2019 中提供该路径。  在 Unity 2020 中，XR 插件框架支持 Azure 空间定位点。

如果要为 HoloLens (第一代) 开发应用，这些头戴显示设备在具有旧版内置 XR 的 Unity 2019 LTS 中仍受支持，以在 Unity 2019 LTS 的整个生命周期中到 2022 年年中。

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

如果使用的是 Unity **2020.3 LTS，Microsoft** 的当前建议是最新的 **混合现实 OpenXR 插件**。 必须使用 Unity 修补程序版本 2020.3.8f1 或更高版本，以避免 2020.3 早期版本的已知性能问题。

混合现实 OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。 这样，你可以编写命中测试代码一次，该代码HoloLens 2 ARCore/ARKit 手机和平板电脑。

但是，有一些已知问题会影响 Unity 2020 LTS 项目：

* URP (URP) 10.5.0 或HoloLens 2性能下降。

如果选择在 Unity 2020 中立即开始新项目，请务必在交付应用之前，跟进未来几周更新的 Unity 生成和 URP 包。  这将确保用户获得适当的全息影像稳定性。

> [!div class="nextstepaction"]
> [使用 OpenXR 插件](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

## <a name="unity-20211"></a>Unity 2021.1

如果要尝试早期 Unity **2021.1** 版本，应前进到 **OpenXR** 插件，因为 Windows XR 插件已弃用。  从 Unity 2021.2 开始，OpenXR 插件将是混合现实开发的唯一路径，因为将不再支持 Windows XR 插件。

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

如果已有一个使用 Unity 2018.4 LTS 的项目，则 Unity 引擎在发布后将继续受支持 2 年。  Unity 2018 LTS 将于 2021 年春季终止服务。