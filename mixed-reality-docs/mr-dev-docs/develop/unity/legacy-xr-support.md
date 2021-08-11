---
title: 使用旧的内置 XR 支持
description: 了解如何使用旧内置 XR 支持设置具有和没有 MRTK 的 Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目，Windows Mixed Reality，UWP，XR，性能，旧，mrtk
ms.openlocfilehash: 534df0b9c4efbe62b00af6cccb74f4203c1557e9479b2101320bab3bbdb5e565
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192044"
---
# <a name="using-legacy-built-in-xr-support"></a>使用旧的内置 XR 支持

## <a name="setting-up-your-project-with-mrtk"></a>用 MRTK 设置项目

用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。

> [!div class="nextstepaction"]
> [试用我们的 MRTK 教程](./tutorials/mr-learning-base-02.md?tabs=wsa)

有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。

## <a name="manual-setup-without-mrtk"></a>无 MRTK 的手动设置

如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

如果以 HoloLens 2 为目标，则需要切换到通用 Windows 平台：

1.  选择 **文件 > 生成设置 ...**
2.  选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"
3.  将“体系结构”设置为“ARM 64” 
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D” 
6.  将“UWP SDK”设置为“最近安装的版本” 
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，并突出显示通用 Windows 平台](images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../design/app-views.md) 而不是2d 视图。

> [!CAUTION]
> 旧版 XR 在 Unity 2019 中已弃用，并已在 Unity 2020 中删除。

1. 从生成设置打开 **播放机设置**... **窗口** 并展开 **XR 设置** 组
2. 在 " **XR 设置**" 部分中，选择 "**支持的虚拟现实**" 以添加虚拟现实设备列表
3. 将 **深度格式** 设置为 **16 位深度** 并启用 **深度缓冲共享**
4. 将 **立体声渲染模式** 设置为 **单一传递实例**
5. 如果要使用全息远程处理，请选择 " **支持 WSA 全息远程处理** " 

![突出显示了 "播放机设置" 部分的 "Project 设置" 窗口的屏幕截图](images/wmr-config-img-9.png)