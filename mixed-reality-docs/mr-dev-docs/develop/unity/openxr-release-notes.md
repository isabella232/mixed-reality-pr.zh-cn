---
title: 混合现实 OpenXR 插件发行说明
description: 及时了解最新的发行说明，并升级到混合现实 OpenXR 插件。
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: 568d5f25eceed385a1331cd2cf5fe6e3adb6f8228e85d6d2d316749fc2ee431c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187618"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a>混合现实 OpenXR 插件发行说明

## <a name="100---current-release"></a>1.0.0 - 最新版本

* 修复了一个错误：无论是不是 ARAnchorManager，应用启动时 XRAnchorSubsystem 总是启动。
* 修复了重新投射模式不能正常工作的错误。

## <a name="100-preview2---2021-06-14"></a>1.0.0-preview.2 - 2021-06-14

* 依赖于 Unity 的 1.2.2 OpenXR 插件。
* 将全息远程处理功能更改到各个功能组中。
* 修复了“应用 HoloLens 2 项目设置”会更改项目颜色空间的错误。 Unity OpenXR 1.2.0 插件后不再需要此功能。
* 修复了错误：输入设备连接后，在应用程序挂起和恢复后，设备输入不会断开连接。
* 添加了支持：通过 ARSession 检测插件和当前跟踪状态。
* 修复了“AR 默认平面”ARFoundation 预设不可见的错误。

## <a name="100-preview1---2021-06-02"></a>1.0.0-preview.1 - 2021-06-02

* 支持 OpenXR 场景了解 MSFT 扩展，而不是预览扩展。
* HoloLens 2 上的平面检测不再需要混合现实 OpenXR 运行时的预览版本。

## <a name="095---2021-05-21"></a>0.9.5 - 2021-05-21

* 依赖于 Unity 的 1.2.0 OpenXR 插件
* 适应新的功能 UI（在 OpenXR 插件 1.2.0 中）进行配置。
* 修复了可定位相机提供程序未正确取消注册的错误。
* 清理了一些额外使用的 [Preserve]。
* 更新输入系统 UI 中的“HP Reverb G2 控制器 (OpenXR)”名称。

## <a name="094---2021-05-20"></a>0.9.4 - 2021-05-20

* 依赖于 Unity 的 1.2.0 OpenXR 插件。
* 添加了新的 C# API，用于获取运动控制器 glTF 模型。
* 添加了新的 C# API，用于获取启用的视图配置并设置重新投射设置。
* 添加了新的 C# API，用于通过 XRMeshSubsystem 为计算网格设置其他设置。
* 添加了新的 C# API 来配置和订阅手势识别事件。
* 添加了“Windows->XR->编辑器远程处理”设置对话框。
* 添加了对 HoloLens UWP 应用程序的 ARM 支持。

## <a name="093---2021-04-29"></a>0.9.3 - 2021-04-29

* 修复了全息远程处理连接不可靠的错误
* 修复了错误：在升级到 Unity 的 1.1.1 OpenXR 插件后，VR 渲染性能为不理想。

## <a name="092---2021-04-21"></a>0.9.2 - 2021-04-21

* 插件版本 0.9.1 中 HoloLens 2 平面检测将适用于 105 版本的混合现实 OpenXR 预览版运行时。
* 插件版本 0.9.2 中 HoloLens 2 平面检测将适用于 106 版本的混合现实 OpenXR 预览版运行时。
* 从 InputProvider 中删除了一些未使用的回调，以防止 XRInputSubsystem.* GetTrackingOriginMode 等调用（不是由我们的输入系统管理）返回具有误导性值的成功。
* 将 XRAnchorStore 的弃用版本拆分到其专有文件，以防止 Unity 控制台发出警告。

## <a name="091---2021-04-20"></a>0.9.1 - 2021-04-20

* 依赖于 Unity 的 1.1.1 OpenXR 插件。
* 添加了对 UWP 平台的全息远程处理应用程序的支持。
* 修复了 XRAnchorStore 尝试在主线程之外获取设置实例的 UnityException。

## <a name="090---2021-03-29"></a>0.9.0 - 2021-03-29

* 添加了支持：通过 XRMeshSubsystem 和 ARMeshManager 进行空间映射。
* 添加了新的 C# API，用于获取 OpenXR 句柄，以支持其他 Unity 包使用 OpenXR 扩展。
* 添加了新的 C# API，用于与 Windows.Perception API 互操作，以支持其他 Unity 包使用 Perception WinRT API。
* 从 Windows Mixed Reality 功能集的所需功能中删除了交互配置文件，以便开发人员可以选择他们测试用的运动控制器。
* 添加了全息编辑器远程处理功能验证程序，以帮助用户正确设置编辑器远程处理。
* 修复了在连接失败后退出全息编辑器远程处理模式时，Unity 编辑器崩溃的错误。
* 修复了 unpremultipled alpha 纹理导致 HoloLens 2 性能欠佳的错误。
* 修复了场景原点处于地面级别时未正确找到手部跟踪的错误。
* 修复了在离开并加载新场景后手部网格跟踪消失的错误。
* 修复了可定位相机提供程序未正确清理的错误。
* 将 XRAnchorStore API 的命名空间修改为 Microsoft.MixedReality.OpenXR。