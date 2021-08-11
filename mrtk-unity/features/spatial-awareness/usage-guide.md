---
title: UsingGuide
description: 描述用于以编程方式配置空间感知系统的关键机制和 Api
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 3a4b6ce17b87dba6155a9e020e41c800fd8ab86bc1b507e77e680fe9ec9a6687
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204119"
---
# <a name="configuring-mesh-observers-via-code"></a>通过代码配置网格观察器

本文将讨论一些用于以编程方式配置 [空间感知系统](spatial-awareness-getting-started.md) 和相关 *网格观察* 程序数据提供程序的关键机制和 api。

## <a name="accessing-mesh-observers"></a>访问网格观察器

实现接口的网格观察器类向 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 空间感知系统提供平台特定的网格数据。 可以在空间识别配置文件中配置多个观察者。

访问空间感知系统的数据提供程序与任何其他 Mixed Reality Toolkit 服务大致相同。 空间感知服务必须强制转换到 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 接口，才能通过 `GetDataProvider<T>` api 访问，然后可以使用这些 api 在运行时直接访问网格观察程序对象。

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

`CoreServices.GetSpatialAwarenessSystemDataProvider<T>()`帮助器简化了此访问模式，如下所示。

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>启动和停止网格观察

处理空间感知系统时，最常见的任务之一是在运行时动态关闭/启用此功能。 这是通过和 api 每个观察者完成的 [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) 。

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

通过空间感知系统直接访问，还可以简化此代码功能。

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>启动和停止所有网格观察

在应用程序中启动/停止所有网格观察通常是非常方便的。 这可以通过有用的空间感知系统 Api 和来实现 [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) 。

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>枚举和访问网格

可以按观察程序来完成访问网格，然后通过 API 通过该网格观察程序识别的网格进行枚举 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 。

如果在编辑器中运行，可以使用将 [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) `Mesh` 对象保存到资产文件中。

如果在设备上运行，可以使用很多社区和存储插件将数据序列化为 `MeshFilter` 模型文件类型 ([OBJ 示例](http://wiki.unity3d.com/index.php/ObjExporter)) 。

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Loop through all known Meshes
foreach (SpatialAwarenessMeshObject meshObject in observer.Meshes.Values)
{
    Mesh mesh = meshObject.Filter.mesh;
    // Do something with the Mesh object
}
```

## <a name="showing-and-hiding-the-spatial-mesh"></a>显示和隐藏空间网格

可以使用以下示例代码以编程方式隐藏/显示网格：

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>注册网格观察事件

组件可以实现 `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` 并注册空间感知系统以接收网格观察事件。

`DemoSpatialMeshHandler` (资产/MRTK/示例/演示/SpatialAwareness/脚本) 脚本是一种很有用的示例，也是侦听网格观察器事件的起点。

这是 *DemoSpatialMeshHandler* 脚本和网格观察事件侦听的简化示例。

```c#
// Simplify type
using SpatialAwarenessHandler = IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>;

public class MyMeshObservationExample : MonoBehaviour, SpatialAwarenessHandler
{
    private void OnEnable()
    {
        // Register component to listen for Mesh Observation events, typically done in OnEnable()
        CoreServices.SpatialAwarenessSystem.RegisterHandler<SpatialAwarenessHandler>(this);
    }

    private void OnDisable()
    {
        // Unregister component from Mesh Observation events, typically done in OnDisable()
        CoreServices.SpatialAwarenessSystem.UnregisterHandler<SpatialAwarenessHandler>(this);
    }

    public virtual void OnObservationAdded(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationUpdated(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationRemoved(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }
}
```

## <a name="see-also"></a>另请参阅

- [空间感知入门](spatial-awareness-getting-started.md)
- [配置空间感知网格观察程序](configuring-spatial-awareness-mesh-observer.md)
- [空间感知 API 文档](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
