---
title: 选择 Unity 版本和 XR 插件
description: 随时了解最新的 Unity 和 XR 插件建议 HoloLens 应用程序开发。
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603678"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>选择 Unity 版本和 XR 插件

尽管我们目前 **建议安装 Unity 2020.3 LTS 以及用于混合现实开发的最新混合现实 OpenXR 插件** ，但你也可以通过其他 Unity 配置来构建应用。

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (建议) 

Microsoft 针对 HoloLens 2 和 Windows Mixed Reality 开发的当前推荐 unity 配置是 **具有最新混合现实 OpenXR 插件的 unity 2020.3 LTS**。 **必须** 使用 Unity patch release 2020.3.8 f1 或更高版本，以避免在早期的2020.3 版本中出现已知的性能问题。

> [!IMPORTANT]
> Unity 2020 不支持 (第一代) HoloLens 目标。 在 **[unity 2019 LTS](#unity-20194-lts)** 中，这些耳机仍受支持，其中内置内置 XR 用于 UNITY 2019 LTS 2022 到的完整生命周期。

安装和管理 Unity 的最佳方式是通过 **Unity 中心**：

1. 安装 <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity 中心**</a>。
2. 选择 " **安装** " 选项卡，然后选择 " **添加**"。
3. 选择 " **Unity 2020.3 LTS** "，然后单击 " **下一步**"。

![Unity 中心安装新版本](images/unity-hub-img-01.png)

4. 检查 **"平台"** 下的以下组件：
    * **通用 Windows 平台生成支持**
    * **Windows 生成支持 (IL2CPP)**

![Unity 通用 Windows 平台生成支持选项](../images/Unity_Install_Option_UWP.png)

5. 如果你以前安装了 Unity 但没有这些选项，则可以通过 Unity 中心中 **的 "添加模块"** 菜单添加它们：

![Unity Windows 生成支持选项](../images/Unity_Install_Option_UWP2.png)

安装 Unity 2020.3 后，开始使用混合现实 OpenXR 插件创建项目或升级现有项目：

> [!div class="nextstepaction"]
> [用 OpenXR 插件设置项目](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> 尽管我们建议为所有新项目使用 OpenXR，但 Unity 2020.3 LTS 还支持[Windows XR 插件](xr-project-setup.md?tabs=windowsxr)。 此插件完全受支持，但它不会收到 AR Foundation 4.0 支持等新功能。

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

如果需要使用 Unity 2019，可将 **unity 2019 LTS 与旧内置 XR 结合** 使用。 若要开始处理 Unity 2019.4 LTS 中的旧内置 XR，请单击此处：

> [!div class="nextstepaction"]
> [设置具有旧内置 XR 的项目](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity 已弃用了它在 Unity 2019 中的旧内置 XR 支持。  虽然 Unity 2019 提供了新的 XR 插件框架，但 Microsoft 目前并未建议使用 Unity 2019 中的路径，因为 Azure 空间锚与 AR Foundation 2 不兼容。  在 Unity 2020 中，XR 插件框架支持 Azure 空间锚。

如果要为 HoloLens (第一代) 开发应用程序，则在 unity 2019 LTS 中，这些耳机仍受支持，其中内置 XR 用于 unity 2019 LTS 2022 到的完整生命周期。

## <a name="unity-20212"></a>Unity 2021。2

如果你正在试用早期 **Unity 2021.2** 生成，请开始处理 [**Mixed Reality OpenXR 插件**](xr-project-setup.md?tabs=openxr)。 OpenXR 插件是 unity 2021.2 和更高版本中混合现实开发的唯一路径，作为支持 Windows XR 插件的最终 Unity 版本是 Unity 2021.1。

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS 已到达 Unity 的两年 Long-Term 支持窗口的末尾，不再接收来自 Unity 的更新，但你的项目将继续运行。

如果你有一个 Unity 2018 项目，则应考虑计划迁移到 Unity 2020.3 LTS 和 Mixed Reality OpenXR 插件。