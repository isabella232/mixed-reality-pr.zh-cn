---
title: 场景理解
description: 介绍 MRTK 中的场景理解
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity， HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 场景理解
ms.openlocfilehash: 1ed6f93216fc90e7c6332f2b9c40911d25d96d2a
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743557"
---
# <a name="scene-understanding"></a>场景理解

[场景理解](/windows/mixed-reality/scene-understanding)返回场景实体的语义表示形式及其HoloLens 2 (HoloLens  1 Gen 不支持) 。

此技术的一些预期用例包括：
* 将对象放在某种类型的最近表面上 (例如墙和地板) 
* 为平台样式游戏构造导航网格
* 提供物理引擎友好几何图形作为四边形
* 通过避免编写类似的算法来加速开发

场景理解是 MRTK 2.6 中的实验性功能。  它作为名为 的空间观察器集成到[](spatial-awareness-getting-started.md#register-observers)MRTK [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 中。 场景理解适用于旧版 XR 管道和 XR SDK 管道 (OpenXR (从 MRTK 2.7) 和 Windows XR 插件) 开始。 在这两种情况下都 `WindowsSceneUnderstandingObserver` 使用 。

> [!NOTE] 
> 不支持在远程处理中使用场景理解。

## <a name="observer-overview"></a>观察者概述

当系统询问时， [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 将返回 [SpatialAwarenessSceneObject，](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) 其属性对应用程序了解其周围的环境很有用。 观察频率、返回的对象类型 (例如墙、) 和其他观察者行为取决于通过配置文件对观察者的配置。 例如，如果需要遮挡掩码，则必须将观察程序配置为生成四边形。 观察到的场景可以保存为序列化文件，稍后可以加载该文件以在编辑器播放模式下重新创建场景。

## <a name="setup"></a>设置

> [!IMPORTANT]
> 场景理解仅在 HoloLens 2 Unity 2019.4 及更高版本上受支持。

1. 确保在生成设置中将平台设置为 UWP。
1. 通过混合现实功能工具 [获取场景理解包](https://aka.ms/MRFeatureTool)。

## <a name="using-scene-understanding"></a>使用场景理解

开始使用场景理解的最快方法就是查看示例场景。

### <a name="scene-understanding-sample-scene"></a>场景理解示例场景

在 Unity 中，使用项目资源管理器打开 中的场景文件 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` 并按 play！

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> 仅适用于 MRTK 2.6.0 - 使用混合现实功能工具或通过 UPM 导入时，请在导入实验性 - 场景了解示例之前导入 Demos - SpatialAwareness 示例，因为存在依赖项问题。 有关详细信息 [，请参阅此 GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 问题。

::: moniker-end
场景演示了以下内容：

* 在应用程序 UI 中通过 可视化观察场景对象来配置观察程序
* 演示如何 `DemoSceneUnderstandingController` 更改观察者设置并侦听相关事件的示例脚本
* 将场景数据保存至设备进行脱机开发
* 将以前保存的场景数据 (.bytes 文件) 以支持编辑器内开发工作流

> [!IMPORTANT]
> 默认情况下， `ShouldLoadFromFile` 观察者的 属性设置为 false。 若要查看序列化示例房间的可视化效果，请参阅下面的配置观察程序 [服务](#configuring-the-observer-service) 部分，在编辑器中将 属性设置为 true。
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> 示例场景基于旧版 XR 管道。 如果使用 XR SDK 管道，应相应地修改配置文件。 提供的场景理解空间感知系统配置文件 () 和场景理解观察器配置文件 (`DemoSceneUnderstandingSystemProfile` `DefaultSceneUnderstandingObserverProfile` 和) `DemoSceneUnderstandingObserverProfile` 都适用于这两个管道。
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> 由于初始化/线程执行 `There is no active AsyncCoroutineRunner when an action is posted.` 顺序，示例场景在某些情况下记录警告。 如果可以确认组件已附加到"演示控制器 `AsyncCoroutineRunner` "GameObject，并且组件/GameObject 在场景中保持启用/活动状态 (默认) ，可以放心忽略警告。
::: moniker-end

#### <a name="configuring-the-observer-service"></a>配置观察程序服务

选择"MixedRealityToolkit"游戏对象并检查检查器。

![场景了解层次结构中的位置](../images/spatial-awareness/MRTKHierarchy.png)

![检查器中的 MRTK 位置](../images/spatial-awareness/MRTKLocation.png)

这些选项将允许配置 `WindowsSceneUnderstandingObserver` 。

### <a name="example-script"></a>示例脚本

示例脚本 _DemoSceneUnderunderunderController.cs_ 演示了使用场景理解服务时的主要概念。

* 订阅场景理解事件
* 处理场景理解事件
* 在运行时 `WindowsSceneUnderstandingObserver` 配置

场景中面板上的切换通过调用此示例脚本的公共函数来更改场景理解观察器的行为。

打开 *实例化预制件*，将演示如何创建大小适合自身以适应所有 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)的对象，这些对象在父对象下完全收集。

![演示控制器选项](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>生成应用说明

以标准方式生成并部署到 HoloLens。 运行后，应会显示多个按钮以使用这些功能。

请注意，向观察器进行查询时存在一些问题。 提取请求配置错误会导致事件有效负载不包含预期数据。 例如，如果用户不请求四边形，则不存在遮挡掩码纹理。 与明智一样，如果观察程序未配置为请求网格，则不会出现任何世界网格。 `DemoSceneUnderstandingController`该脚本负责处理其中一些依赖项，但并非所有依赖项。

可以通过 设备门户访问保存的 [场景](/windows/mixed-reality/using-the-windows-device-portal) 文件 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 。 可以通过在检查器中的观察程序配置文件中指定这些场景文件，在编辑器中使用这些场景文件。

![设备门户字节文件的位置](../images/spatial-awareness/BytesInDevicePortal.png)

![观察程序中的序列化场景字节数](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>另请参阅

* [场景理解概述](/windows/mixed-reality/scene-understanding)
* [场景理解 SDK 概述](/windows/mixed-reality/scene-understanding-sdk)