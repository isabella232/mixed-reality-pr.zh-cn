---
title: 系统、扩展服务和数据提供程序
description: MRTK 扩展和数据提供程序
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，系统扩展，
ms.openlocfilehash: 347c4b7603c58a09c98bce738beff02a751a3e47549154109bd2b661ba13e9a6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211521"
---
# <a name="systems-extension-services-and-data-providers"></a>系统、扩展服务和数据提供程序

在混合现实 Toolkit 中，许多功能都以服务的形式提供。 服务分为三个主要类别：系统、扩展服务和数据访问接口。

## <a name="systems"></a>系统

系统是提供混合现实 Toolkit 核心功能的服务。 所有系统都是接口的实现 [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 。

- [BoundarySystem](../features/boundary/boundary-system-getting-started.md)
- [CameraSystem](../features/camera-system/camera-system-overview.md)
- [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md)
- [InputSystem](../features/input/overview.md)
- [SceneSystem](../features/scene-system/scene-system-getting-started.md)
- [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [TeleportSystem](../features/teleport-system/teleport-system.md)

列出的每个系统都出现在 MixedRealityToolkit 组件的配置 [文件](../features/profiles/profiles.md)中。

## <a name="extensions"></a>Extensions

扩展服务是用于扩展混合现实 Toolkit 功能的组件。 所有扩展服务必须指定它们实现 [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) 接口。

有关创建扩展服务的信息，请参阅 [扩展服务](../features/extensions/extension-services.md) 一文。

为了可以 MRTK，可使用 MixedRealityToolkit 组件的配置文件的 Extensions 部分注册和配置扩展服务。

![配置扩展服务](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>数据提供程序

数据访问接口是根据其名称将数据提供给混合现实 Toolkit 服务的组件。 所有数据访问接口都必须指定它们实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 接口。

> [!NOTE]
> 并非所有服务都需要数据访问接口。 在混合现实 Toolkit 的系统中，输入和空间感知系统是使用数据访问接口的唯一服务。

为了能够访问特定的 MRTK 服务，数据访问接口在服务的配置文件中注册。

应用程序代码通过接口访问数据提供程序 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 。 若要简化访问，还可以通过 helper 类检索数据访问接口 `CoreServices` 。

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> 尽管 `IMixedRealityDataProvider` 继承自 `IMixedRealityService` ，但数据提供程序未注册到 `MixedRealityServiceRegistry` 。 若要访问数据提供程序，应用程序代码必须查询为其注册的服务实例 (例如：输入系统) 。

### <a name="input"></a>输入

MRTK 输入系统只利用实现的数据访问接口 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 。

![输入系统数据提供程序](../features/images/input/RegisteredServiceProviders.PNG)

下面的示例演示如何访问输入模拟提供程序并切换 SmoothEyeTracking 属性。

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

通过使用 helper 类，还可以简化访问核心输入系统的数据提供程序 `CoreServices` 。

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> 输入系统只返回运行应用程序的平台支持的数据访问接口。

有关为 MRTK 输入系统编写数据提供程序的信息，请参阅 [创建输入系统数据提供程序](../features/input/create-data-provider.md)。

### <a name="spatial-awareness"></a>空间感知

MRTK 空间感知系统只利用实现接口的数据访问 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 接口。

![空间感知系统数据提供程序](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

下面的示例演示如何访问已注册的空间网格数据提供程序和更改网格的可见性。

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

通过使用 helper 类，还可以简化访问核心空间感知系统的数据提供程序 `CoreServices` 。

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> 空间感知系统仅返回运行应用程序的平台支持的数据访问接口。

有关为 MRTK 空间感知系统编写数据提供程序的信息，请参阅 [创建空间感知系统数据提供程序](../features/spatial-awareness/create-data-provider.md)。

## <a name="see-also"></a>另请参阅

- [扩展服务](../features/extensions/extension-services.md)
- [创建输入系统数据提供程序](../features/input/create-data-provider.md)
- [创建空间感知系统系统数据提供程序](../features/spatial-awareness/create-data-provider.md)
- [IMixedRealityService 接口](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [IMixedRealityDataProvider 接口](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [IMixedRealityExtensionService 接口](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
