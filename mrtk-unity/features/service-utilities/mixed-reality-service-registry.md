---
title: 混合现实服务注册表
description: MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar 上的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 061e4233d61de817b1aaed7faaa6d461427d6f07
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176707"
---
# <a name="mixed-reality-service-registry"></a>混合现实服务注册表

混合现实 Toolkit 有两个非常相似的命名组件，它们执行相关任务： MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar。

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)是包含每个注册服务的实例的组件， (核心系统和扩展服务) 。

> [!NOTE]
> MixedRealityServiceRegistry 包含实现 [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 接口的对象的实例，包括 [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)。
>
>实现 [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (IMixedRealityService) 子类的对象在 MixedRealityServiceRegistry 中显式未注册。 这些对象由各个服务管理 (例如：空间感知) 。

MixedRealityServiceRegistry 作为静态 c # 类实现，是用于在应用程序代码中获取服务实例的建议模式。

以下代码片段演示如何获取 IMixedRealityInputSystem 实例。

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)是定义由组件实现的功能的接口，这些组件管理一个或多个服务的注册。 实现 IMixedRealityServiceRegistrar 的组件负责在 MixedRealityServiceRegistry 中添加和删除数据。 [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)对象是一个组件。

可在 MRTK/SDK/实验/功能文件夹中找到其他注册机构。 这些组件可用于向应用程序添加单个服务 (例如：空间感知) 支持。 下面列出了这些单一服务管理器。

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

上述每个组件（InputSystemManager 除外）都负责管理一种服务类型的注册和状态。 InputSystem 需要一些额外的支持服务 (例如： FocusProvider) ，这些服务也由 InputSystemManager 进行管理。

通常，由服务管理组件在内部调用 IMixedRealityServiceRegistrar 定义的方法，或由需要其他服务组件来正常工作的服务调用。 通常情况下，应用程序代码不会调用这些方法，因为这样做可能会导致应用程序的行为不能预料 (例如：缓存服务实例可能会) 无效。

## <a name="see-also"></a>另请参阅

- [IMixedRealityServiceRegistrar API 文档](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [MixedRealityServiceRegistry API 文档](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
