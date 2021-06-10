---
title: 使用旧的内置 XR 支持
description: 了解如何使用旧版内置 XR 支持设置具有和不带 MRTK 的 Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity， 混合现实， 开发， 入门， 新项目， Windows Mixed Reality， UWP， XR， 性能， 旧版， mrtk
ms.openlocfilehash: b5faa48ec913c5095b12361318729b6f14276f30
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743501"
---
# <a name="using-legacy-built-in-xr-support"></a>使用旧版内置 XR 支持

## <a name="setting-up-your-project-with-mrtk"></a>使用 MRTK 设置项目

用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。

> [!div class="nextstepaction"]
> [试用我们的 MRTK 教程](./tutorials/mr-learning-base-02.md?tabs=wsa)

有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。

## <a name="manual-setup-without-mrtk"></a>不带 MRTK 的手动设置

如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](images/wmr-config-img-3.png)

如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：

1.  选择 **"文件>生成设置..."**
2.  在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**
3.  将“体系结构”设置为“ARM 64” 
4.  将“目标设备”设置为“HoloLens” 
5.  将“生成类型”设置为“D3D” 
6.  将“UWP SDK”设置为“最近安装的版本” 
7.  将“生成配置”设置为“发布”，因为调试存在已知的性能问题 

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

设置平台后，需要让 Unity 知道在导出时创建[](../../design/app-views.md)沉浸式视图而不是 2D 视图。

> [!CAUTION]
> 旧版 XR 在 Unity 2019 中已弃用，在 Unity 2020 中已删除。

1. 从 **"生成设置..."** 打开" **播放器设置..."。窗口** 并展开 **"XR 设置"** 组
2. 在 **"XR 设置"** 部分中 **，选择"** 支持的虚拟现实"以添加"虚拟现实设备"列表
3. 将 **深度格式设置为** **16 位深度** 并启用 **深度缓冲区共享**
4. 将 **立体声渲染模式设置为****单通道实例**
5. 如果要 **使用全息远程处理** ，请选择"支持的 WSA 全息远程处理" 

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了"播放器设置"部分](images/wmr-config-img-9.png)