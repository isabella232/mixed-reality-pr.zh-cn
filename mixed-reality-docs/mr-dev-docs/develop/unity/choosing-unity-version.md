---
title: 选择 Unity 版本和 XR 插件
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity 和 XR 插件建议。
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit， mixedrealitytoolkit-unity， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity
ms.openlocfilehash: 646a0ec3b3b332b038509cba39caa085c1590c1a
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112921418"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>选择 Unity 版本和 XR 插件

虽然我们目前建议安装具有用于混合现实开发的最新混合现实 OpenXR 插件的 **Unity 2020.3 LTS，** 但也可使用其他 Unity 配置生成应用。

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (建议) 

Microsoft 当前推荐的用于 HoloLens 2 Windows Mixed Reality 的 Unity 配置是具有最新混合现实 OpenXR 插件 的 **Unity 2020.3 LTS。** 必须使用 Unity 修补程序版本 2020.3.8f1 或更高版本，以避免 2020.3 早期版本的已知性能问题。

> [!IMPORTANT]
> Unity 2020 不支持将 HoloLens (第一代) 。 在 Unity 2019 LTS 的整个生命周期（到 2022 年年中）中，具有旧版内置 XR 的 **[Unity 2019 LTS](#unity-20194-lts)** 仍支持这些头戴显示设备。
>
> [!NOTE]
> 某些包尚不与 Unity 2020 LTS 中的混合现实项目兼容：
> 
> * URP (URP) 10.5.0 或更旧版本的 URP 在设备上HoloLens 2性能问题。 _(URP 版本中修复了)_
> * Azure 远程渲染尚未发布支持 Unity 2020 的更新版本。
>
> 如果 Unity 项目使用通用呈现管道或Azure 远程渲染，建议在更新的包可用之前，继续将项目升级到 Unity 2020。

最好通过 Unity Hub 安装和管理 Unity。 安装后，打开 Unity 中心：

1. 选择" **安装"选项卡** ，然后选择" **添加"**
2. 选择 Unity 2020.3 LTS，然后单击"下一 **步"**

![Unity 中心安装新版本](images/unity-hub-img-01.png)

3. 检查"平台" **下的以下组件**
    * **通用 Windows 平台生成支持**
    * **Windows 生成支持 (IL2CPP)**

![Unity 通用 Windows 平台生成支持选项](../images/Unity_Install_Option_UWP.png)

4. 如果在未安装这些选项的情况下安装了 Unity，可以通过 Unity 中心的"添加模块 **"菜单** 添加它们：

![Unity Windows 生成支持选项](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [使用 OpenXR 插件](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> 虽然我们建议将 OpenXR 用于所有新项目，但 Unity 2020.3 LTS 也支持 [Windows XR 插件](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)。 虽然此插件不会获得 AR Foundation 4.0 支持等新功能，但完全受支持。

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

如果需要使用 Unity 2019，可以将 Unity **2019 LTS 与旧版内置 XR 一起使用**。 若要开始使用 Unity 2019.4 LTS 中的旧版内置 XR，请单击此处：

> [!div class="nextstepaction"]
> [设置旧版内置 XR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> 自 Unity 2019 起，Unity 已弃用其旧版内置 XR 支持。  虽然 Unity 2019 确实提供了新的 XR 插件框架，但由于 Azure 空间定位点与 AR Foundation 2 不兼容，Microsoft 当前不建议在 Unity 2019 中提供该路径。  在 Unity 2020 中，XR 插件框架支持 Azure 空间定位点。

如果要为 HoloLens (第一代) 开发应用，这些头戴显示设备在具有旧版内置 XR 的 Unity 2019 LTS 中仍受支持，以在 Unity 2019 LTS 的整个生命周期中到 2022 年年中。

## <a name="unity-20211"></a>Unity 2021.1

如果要尝试早期 Unity **2021.1** 版本，应前进到 **OpenXR** 插件，因为 Windows XR 插件已弃用。  从 Unity 2021.2 开始，OpenXR 插件将是混合现实开发的唯一路径，因为将不再支持 Windows XR 插件。

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

如果已有一个使用 Unity 2018.4 LTS 的项目，则 Unity 引擎在发布后将继续受支持 2 年。  Unity 2018 LTS 将于 2021 年春季终止服务。
