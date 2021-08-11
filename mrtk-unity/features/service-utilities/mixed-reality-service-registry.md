---
title: 混合现实服务注册表
description: 有关 MixedRealityServiceRegistry 和 IMixedRealityServiceRegistmix 的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 16aea46890297dab209c13b6776a0a571b1e05bf5021a5795a33dc88366ee9b1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217425"
---
# <a name="mixed-reality-service-registry"></a>混合现实服务注册表

混合现实Toolkit有两个名称类似的组件，用于执行相关任务：MixedRealityServiceRegistry 和 IMixedRealityServiceRegist分。

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)是包含每个已注册服务的实例的组件， (核心系统和扩展服务) 。

> [!NOTE]
> MixedRealityServiceRegistry 包含实现 [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 接口的对象的实例，包括 [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)。
>
>实现 [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (IMixedRealityService) 子类的对象未显式注册到 MixedRealityServiceRegistry 中。 这些对象由单个服务管理 (例如：空间感知) 。

MixedRealityServiceRegistry 作为静态 C# 类实现，是建议用于获取应用程序代码中的服务实例的模式。

以下代码片段演示如何获取 IMixedRealityInputSystem 实例。

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistmix

[IMixedRealityServiceRegist以](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)接口定义由管理一个或多个服务的注册的组件实现的功能。 实现 IMixedRealityServiceRegist且负责添加和删除 MixedRealityServiceRegistry 内的数据的组件。 [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)对象是此类组件之一。

可以在 MRTK/SDK/Experimental/Features 文件夹中找到其他注册机构。 这些组件可用于添加单个服务 (例如：空间感知) 应用程序支持。 下面列出了这些单一服务管理器。

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

上述每个组件（InputSystemManager 除外）负责管理单个服务类型的注册和状态。 InputSystem 需要一些额外的支持服务 (例如：FocusProvider) 由 InputSystemManager 管理。

一般情况下，由 IMixedRealityServiceRegist分定义的方法由服务管理组件在内部调用，或者由需要其他服务组件正常运行的服务调用。 通常，应用程序代码不应调用这些方法，因为这样做可能会导致应用程序的行为不 (例如：缓存的服务实例可能会变得) 。

## <a name="see-also"></a>另请参阅

- [IMixedRealityServiceRegistmix API 文档](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [MixedRealityServiceRegistry API 文档](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
