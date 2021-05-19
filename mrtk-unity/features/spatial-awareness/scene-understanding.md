---
title: 场景理解
description: 介绍 MRTK 中的场景理解
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，场景理解
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143887"
---
# <a name="scene-understanding"></a>场景理解

[场景理解](/windows/mixed-reality/scene-understanding) 返回场景实体的语义表示形式，并在 __HoloLens 2__ (hololens 第一代上，不支持) 。

此技术的一些预期用例如下：
* 将对象置于特定类型的最近图面上 (例如墙壁和地面) 
* 构造平台样式游戏的导航网格
* 提供物理引擎友好几何作为四边形
* 通过避免编写类似的算法来加速开发

从 MRTK 2.6 开始，场景理解作为 __实验__ 性功能提供。 它集成到 MRTK 中，作为名为的 [空间观察](spatial-awareness-getting-started.md#register-observers) 程序 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 。 场景理解既适用于旧的 XR 管道，也适用于 XR SDK 管道。 在这两种情况下， `WindowsSceneUnderstandingObserver` 都使用。

## <a name="observer-overview"></a>观察程序概述

当系统询问时， [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 将返回 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) ，其属性对应用程序有用，以了解其环境。 观察频率、返回的对象类型 (例如墙壁、楼层) 和其他观察者行为取决于观察者通过配置文件的配置。 例如，如果需要封闭掩码，则必须将观察程序配置为生成四边形。 观察到的场景可以保存为序列化文件，稍后可以将其加载以便在编辑器播放模式下重新创建场景。

## <a name="setup"></a>设置

> [!IMPORTANT]
> 仅在 HoloLens 2 和 Unity 2019.4 及更高版本上支持场景理解。

1. 确保在生成设置中将平台设置为 UWP。
1. 通过混合现实功能工具 [获取场景理解包](https://aka.ms/MRFeatureTool)。

## <a name="using-scene-understanding"></a>使用场景理解

开始使用场景理解的最快方法就是查看示例场景。

### <a name="scene-understanding-sample-scene"></a>场景理解示例场景

在 Unity 中，使用项目资源管理器打开 中的场景文件 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` 并按 play！

> [!IMPORTANT]
> 使用混合现实功能工具或通过 UPM 导入时，请在导入实验性 - 场景了解示例之前导入 Demos - SpatialAwareness 示例，因为存在依赖项问题。 有关详细信息 [，请参阅此 GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 问题。

场景演示了以下内容：

* 在应用程序 UI 中通过 可视化观察场景对象来配置观察程序
* 演示如何 `DemoSceneUnderstandingController` 更改观察者设置并侦听相关事件的示例脚本
* 将场景数据保存至设备进行脱机开发
* 将以前保存的场景数据 (.bytes 文件) 以支持编辑器内开发工作流

> [!NOTE] 
> 示例场景基于旧版 XR 管道。 如果使用 XR SDK 管道，应相应地修改配置文件。 提供的场景理解空间感知系统配置文件 () 和场景理解观察器配置文件 (`DemoSceneUnderstandingSystemProfile` `DefaultSceneUnderstandingObserverProfile` 和) `DemoSceneUnderstandingObserverProfile` 都适用于这两个管道。

#### <a name="configuring-the-observer-service"></a>配置观察程序服务

选择"MixedRealityToolkit"游戏对象并检查检查器。

![场景了解层次结构中的位置](../images/spatial-awareness/MRTKHierarchy.png)

![检查器中的 MRTK 位置](../images/spatial-awareness/MRTKLocation.png)

这些选项允许配置 `WindowsSceneUnderstandingObserver` 。

### <a name="example-script"></a>示例脚本

示例脚本 _DemoSceneUnderstandingController_ 演示了使用场景理解服务的主要概念。

* 订阅场景理解事件
* 处理场景理解事件
* `WindowsSceneUnderstandingObserver`在运行时配置

屏幕上面板上的切换通过调用此示例脚本的公共函数，更改场景理解观察程序的行为。

打开 *实例化 prototyping*，将演示如何创建适合所有 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)的大小的对象，并在父对象下进行整齐收集。

![演示控制器选项](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>生成的应用说明

采用标准方式生成并部署到 HoloLens。 运行后，将出现一些按钮，这些按钮可用于功能。

请注意，有一些 pit 正在向观察者发出查询。 错误配置请求导致事件负载中不包含预期数据。 例如，如果一个没有请求四边形，则不会显示任何封闭掩码纹理。 类似地，如果未将观察者配置为请求网格，则不会显示世界网格。 此 `DemoSceneUnderstandingController` 脚本负责处理其中的某些依赖项，但并非全部。

可以通过中的 [设备门户](/windows/mixed-reality/using-the-windows-device-portal) 访问已保存的场景文件 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 。 可以通过在 "检查器" 中找到的观察程序配置文件中指定这些场景文件，在编辑器中使用这些文件。

![字节文件的设备门户位置](../images/spatial-awareness/BytesInDevicePortal.png)

![观察程序中的序列化场景字节](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>另请参阅

* [空间映射概述 WMR](/windows/mixed-reality/scene-understanding)
* [空间映射概述 WMR](/windows/mixed-reality/scene-understanding-sdk)