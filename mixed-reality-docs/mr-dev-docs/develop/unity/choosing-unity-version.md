---
title: 选择 Unity 版本和 XR 插件
description: 随时了解适用于 HoloLens 应用程序开发的最新 Unity 和 XR 插件建议。
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938101"
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
    * **Windows Build 支持 (IL2CPP)**

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

但是，有一些已知问题会影响全息影像稳定性和 HoloLens 2 上的其他功能： 

* 深度缓冲区提交在最近的 Unity 2020 生成中回归，这会导致严重的全息影像不稳定。
* 使用通用 Windows 平台生成目标的全息应用远程处理应用程序无法正常工作。
* Unity 图形作业系统在默认情况下是打开的，即使它与 HoloLens 项目不兼容。

如果你现在选择在 Unity 2020 中启动一个新项目，请务必在交付应用之前，在未来几个月内跟进更新后的 Unity 生成和 Windows XR 插件版本。  这将确保用户体验到适当的全息影像稳定性。

> [!div class="nextstepaction"]
> [使用 Windows XR 插件](windows-xr-plugin.md)

### <a name="using-openxr"></a>使用 OpenXR

Unity 2020.3 LTS 还支持 **混合现实 OpenXR** 插件的公共预览版。

Mixed Reality OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。 这样一来，你就可以编写命中测试代码一次，然后跨 HoloLens 2 和 ARCore/ARKit 手机和平板电脑。 

今年晚些时候， **具有 OpenXR 插件的 unity 2020.3 LTS** 将成为推荐的 unity 配置，并且 unity 中的未来 HoloLens 2 功能将仅通过此插件公开。  你现在可以在此处启动你的项目-但是，如果你的项目面向 HoloLens 2，则当前会遇到 Unity 2020 全息图稳定性以及上面列出的其他问题。  在交付您的应用程序之前，请务必回来查看更新后的 Unity 生成和 OpenXR 插件版本。  这将确保用户体验到适当的全息影像稳定性。 

> [!div class="nextstepaction"]
> [使用 OpenXR 插件](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021。1

如果你正在试用早期 **Unity 2021.1** 生成，则应前进到 **OpenXR 插件**，因为 Windows XR 插件已在此处弃用。  从 Unity 2021.2 开始，OpenXR 插件将成为混合现实开发的唯一路径，因为 Windows XR 插件将不再受支持。

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

如果你已有使用 Unity 2018.4 LTS 的项目，则 Unity 引擎在发布后将继续受到2年的支持。  Unity 2018 LTS 将在2021春季接通服务结束。
