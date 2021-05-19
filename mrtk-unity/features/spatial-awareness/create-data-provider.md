---
title: 创建空间感知数据提供程序
description: 介绍如何在 MRTK 中创建自定义数据提供程序
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145149"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a><span data-ttu-id="923dd-104">创建空间感知系统数据提供程序</span><span class="sxs-lookup"><span data-stu-id="923dd-104">Creating a spatial awareness system data provider</span></span>

<span data-ttu-id="923dd-105">空间感知系统是一个可扩展的系统，用于向应用程序提供有关实际环境的数据。</span><span class="sxs-lookup"><span data-stu-id="923dd-105">The Spatial Awareness system is an extensible system for providing applications with data about real world environments.</span></span> <span data-ttu-id="923dd-106">若要添加对新硬件平台或新形式的空间感知数据的支持，可能需要自定义数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="923dd-106">To add support for a new hardware platform or a new form of Spatial Awareness data, a custom data provider may be required.</span></span>

<span data-ttu-id="923dd-107">本文介绍如何 [为空间感知](../../architecture/systems-extensions-providers.md)系统创建自定义数据提供程序（也称为空间观察器）。</span><span class="sxs-lookup"><span data-stu-id="923dd-107">This article describes how to create [custom data providers](../../architecture/systems-extensions-providers.md), also called Spatial Observers, for the Spatial Awareness system.</span></span> <span data-ttu-id="923dd-108">此处显示的示例代码来自 类实现，该类实现可用于在编辑器中加载 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [3D 网格数据](spatial-object-mesh-observer.md)。</span><span class="sxs-lookup"><span data-stu-id="923dd-108">The example code shown here is from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class implementation which is [useful for loading 3D mesh data in-editor](spatial-object-mesh-observer.md).</span></span>

> [!NOTE]
> <span data-ttu-id="923dd-109">可以在 文件夹中找到此示例中使用的完整 `Assets/MRTK/Providers/ObjectMeshObserver` 源代码。</span><span class="sxs-lookup"><span data-stu-id="923dd-109">The complete source code used in this example can be found in the `Assets/MRTK/Providers/ObjectMeshObserver` folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="923dd-110">命名空间和文件夹结构</span><span class="sxs-lookup"><span data-stu-id="923dd-110">Namespace and folder structure</span></span>

<span data-ttu-id="923dd-111">可通过两种方式之一分发数据提供程序：</span><span class="sxs-lookup"><span data-stu-id="923dd-111">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="923dd-112">第三方加载项</span><span class="sxs-lookup"><span data-stu-id="923dd-112">Third party add-ons</span></span>
1. <span data-ttu-id="923dd-113">Microsoft Mixed Reality Toolkit 的一部分</span><span class="sxs-lookup"><span data-stu-id="923dd-113">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="923dd-114">向 MRTK 提交新数据提供程序的审批过程将因情况而异，将在初始建议时传达。</span><span class="sxs-lookup"><span data-stu-id="923dd-114">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="923dd-115">可以通过创建新的功能请求类型问题 [*来提交* 建议](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)。</span><span class="sxs-lookup"><span data-stu-id="923dd-115">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-on"></a><span data-ttu-id="923dd-116">第三方加载项</span><span class="sxs-lookup"><span data-stu-id="923dd-116">Third party add-on</span></span>

<span data-ttu-id="923dd-117">**命名空间**</span><span class="sxs-lookup"><span data-stu-id="923dd-117">**Namespace**</span></span>

<span data-ttu-id="923dd-118">数据提供程序需要具有命名空间来缓解潜在的名称冲突。</span><span class="sxs-lookup"><span data-stu-id="923dd-118">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="923dd-119">建议命名空间包含以下组件。</span><span class="sxs-lookup"><span data-stu-id="923dd-119">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="923dd-120">生成加载项的公司名称</span><span class="sxs-lookup"><span data-stu-id="923dd-120">Company name producing the add-on</span></span>
- <span data-ttu-id="923dd-121">功能区域</span><span class="sxs-lookup"><span data-stu-id="923dd-121">Feature area</span></span>

<span data-ttu-id="923dd-122">例如，Contoso 公司创建和交付的空间感知数据提供程序可能是 *"Contoso.MixedReality.Toolkit.SpatialAwareness"。*</span><span class="sxs-lookup"><span data-stu-id="923dd-122">For example, a Spatial Awareness data provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.SpatialAwareness"*.</span></span>

<span data-ttu-id="923dd-123">**文件夹结构**</span><span class="sxs-lookup"><span data-stu-id="923dd-123">**Folder structure**</span></span>

<span data-ttu-id="923dd-124">建议将数据提供程序的源代码布局在文件夹层次结构中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="923dd-124">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![文件夹结构示例](../images/spatial-awareness/ExampleProviderFolderStructure.png)

<span data-ttu-id="923dd-126">其中， *ContosoSpatialAwareness* 文件夹包含数据提供程序的实现， *Editor* 文件夹包含检查器 (和任何其他特定于 Unity 编辑器的代码) ，而 profile *文件夹包含* 一个或多个预生成的配置文件可脚本化对象。</span><span class="sxs-lookup"><span data-stu-id="923dd-126">Where the *ContosoSpatialAwareness* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="923dd-127">MRTK 提交</span><span class="sxs-lookup"><span data-stu-id="923dd-127">MRTK submission</span></span>

<span data-ttu-id="923dd-128">**命名空间**</span><span class="sxs-lookup"><span data-stu-id="923dd-128">**Namespace**</span></span>

<span data-ttu-id="923dd-129">如果将空间感知系统数据提供程序提交到 [混合现实工具包存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，命名空间 **必须** 以 MixedReality 开头 (例如： *SpatialObjectMeshObserver*) </span><span class="sxs-lookup"><span data-stu-id="923dd-129">If a spatial awareness system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span></span>

 <span data-ttu-id="923dd-130">代码应位于 MRTK/Providers 下的文件夹中 (例如： *MRTK/providers/ObjectMeshObserver*) 。</span><span class="sxs-lookup"><span data-stu-id="923dd-130">and the code should be located in a folder beneath MRTK/Providers (ex: *MRTK/Providers/ObjectMeshObserver*).</span></span>

<span data-ttu-id="923dd-131">**文件夹结构**</span><span class="sxs-lookup"><span data-stu-id="923dd-131">**Folder structure**</span></span>

<span data-ttu-id="923dd-132">所有代码都应位于 MRTK/Providers 下的文件夹中 (例如： MRTK/Providers/ObjectMeshObserver) 。</span><span class="sxs-lookup"><span data-stu-id="923dd-132">All code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/ObjectMeshObserver).</span></span>

## <a name="define-the-spatial-data-object"></a><span data-ttu-id="923dd-133">定义空间数据对象</span><span class="sxs-lookup"><span data-stu-id="923dd-133">Define the spatial data object</span></span>

<span data-ttu-id="923dd-134">创建空间感知数据提供程序的第一步是确定数据类型 (例如：网格或平面将提供给应用程序) 。</span><span class="sxs-lookup"><span data-stu-id="923dd-134">The first step in creating a Spatial Awareness data provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="923dd-135">所有空间数据对象必须实现 [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) 接口。</span><span class="sxs-lookup"><span data-stu-id="923dd-135">All spatial data objects must implement the [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span></span>

<span data-ttu-id="923dd-136">混合现实工具包基础提供了以下可以在新的数据提供程序中使用或扩展的空间对象。</span><span class="sxs-lookup"><span data-stu-id="923dd-136">The Mixed Reality Toolkit foundation provides the following spatial objects that can be used or extended in new data providers.</span></span>

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a><span data-ttu-id="923dd-137">实现数据访问接口</span><span class="sxs-lookup"><span data-stu-id="923dd-137">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="923dd-138">指定接口和/或基类继承</span><span class="sxs-lookup"><span data-stu-id="923dd-138">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="923dd-139">所有空间感知数据提供程序必须实现 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 接口，该接口指定空间感知系统所需的最小功能。</span><span class="sxs-lookup"><span data-stu-id="923dd-139">All Spatial Awareness data providers must implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, which specifies the minimum functionality required by the Spatial Awareness system.</span></span> <span data-ttu-id="923dd-140">MRTK foundation 包含 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 类，该类提供此所需功能的默认实现。</span><span class="sxs-lookup"><span data-stu-id="923dd-140">The MRTK foundation includes the [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class which provides a default implementation of this required functionality.</span></span>

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> <span data-ttu-id="923dd-141">[`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)接口由 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 类用来指示它提供对 SpatialAwarenessMesh 功能的支持。</span><span class="sxs-lookup"><span data-stu-id="923dd-141">The [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface is used by the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class to indicate that it provides support for the SpatialAwarenessMesh capability.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="923dd-142">应用 MixedRealityDataProvider 特性</span><span class="sxs-lookup"><span data-stu-id="923dd-142">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="923dd-143">创建空间感知数据提供程序的一个关键步骤是将属性应用于 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 类。</span><span class="sxs-lookup"><span data-stu-id="923dd-143">A key step in creating a Spatial Awareness data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="923dd-144">此步骤可用于设置数据提供程序的默认配置文件和平台 () ，以及在空间感知配置文件中选择的配置文件和平台，以及名称、文件夹路径等。</span><span class="sxs-lookup"><span data-stu-id="923dd-144">This step enables setting the default profile and platform(s) for the data provider, when selected in the Spatial Awareness profile as well as Name, folder path, and more.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="923dd-145">实现 IMixedRealityDataProvider 方法</span><span class="sxs-lookup"><span data-stu-id="923dd-145">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="923dd-146">一旦定义了类，下一步就是提供接口的实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="923dd-146">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="923dd-147">[`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)类通过 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 类只为方法提供空实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="923dd-147">The [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides only an empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="923dd-148">这些方法的详细信息通常是特定于数据访问接口的。</span><span class="sxs-lookup"><span data-stu-id="923dd-148">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="923dd-149">应由数据提供程序实现的方法如下：</span><span class="sxs-lookup"><span data-stu-id="923dd-149">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="923dd-150">实现数据访问接口逻辑</span><span class="sxs-lookup"><span data-stu-id="923dd-150">Implement the data provider logic</span></span>

<span data-ttu-id="923dd-151">下一步是通过实现特定的数据提供程序接口来添加数据提供程序的逻辑，例如 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 。</span><span class="sxs-lookup"><span data-stu-id="923dd-151">The next step is to add the logic of the data provider by implementing the specific data provider interface, for example [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver).</span></span> <span data-ttu-id="923dd-152">数据访问接口的此部分通常是特定于平台的。</span><span class="sxs-lookup"><span data-stu-id="923dd-152">This portion of the data provider will typically be platform specific.</span></span>

### <a name="observation-change-notifications"></a><span data-ttu-id="923dd-153">观察更改通知</span><span class="sxs-lookup"><span data-stu-id="923dd-153">Observation change notifications</span></span>

<span data-ttu-id="923dd-154">为了使应用程序能够响应设备对环境的了解更改，数据访问接口会引发接口中定义的通知事件 [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) 。</span><span class="sxs-lookup"><span data-stu-id="923dd-154">To allow applications to respond to changes in the device's understanding of the environment, the data provider raises notification events as defined in the [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span></span>

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 <span data-ttu-id="923dd-155">示例中的以下代码 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 演示了添加网格数据时的引发和事件。</span><span class="sxs-lookup"><span data-stu-id="923dd-155">The following code from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) examples demonstrates raising and event when mesh data is added.</span></span>

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> <span data-ttu-id="923dd-156">[`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver)类不会引发 `OnObservationUpdated` 事件，因为3d 模型仅加载一次。</span><span class="sxs-lookup"><span data-stu-id="923dd-156">The [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class does not raise `OnObservationUpdated` events since the 3D model is only loaded once.</span></span> <span data-ttu-id="923dd-157">类中的实现 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 提供了为 `OnObservationUpdated` 观察到的网格引发事件的示例。</span><span class="sxs-lookup"><span data-stu-id="923dd-157">The implementation in the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class provides an example of raising an `OnObservationUpdated` event for an observed mesh.</span></span>

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="923dd-158">添加 Unity 探查器检测</span><span class="sxs-lookup"><span data-stu-id="923dd-158">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="923dd-159">性能在混合现实应用程序中非常重要。</span><span class="sxs-lookup"><span data-stu-id="923dd-159">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="923dd-160">每个组件都增加了应用程序必须考虑的一些开销。</span><span class="sxs-lookup"><span data-stu-id="923dd-160">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="923dd-161">为此，在内部循环中包含 Unity 探查器检测和经常使用的代码路径，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="923dd-161">To this end, it is important that all spatial awareness data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="923dd-162">建议在检测自定义提供程序时实现 MRTK 使用的模式。</span><span class="sxs-lookup"><span data-stu-id="923dd-162">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="923dd-163">用于标识探查器标记的名称是任意的。</span><span class="sxs-lookup"><span data-stu-id="923dd-163">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="923dd-164">MRTK 使用以下模式。</span><span class="sxs-lookup"><span data-stu-id="923dd-164">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="923dd-165">"[product] className. 方法名称-可选注释"</span><span class="sxs-lookup"><span data-stu-id="923dd-165">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="923dd-166">建议自定义数据访问接口遵循类似的模式，以帮助在分析跟踪时简化特定组件和方法的标识。</span><span class="sxs-lookup"><span data-stu-id="923dd-166">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="923dd-167">创建配置文件和检查器</span><span class="sxs-lookup"><span data-stu-id="923dd-167">Create the profile and inspector</span></span>

<span data-ttu-id="923dd-168">在混合现实工具包中，数据访问接口是使用 [配置文件](../profiles/profiles.md)配置的。</span><span class="sxs-lookup"><span data-stu-id="923dd-168">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="923dd-169">定义配置文件</span><span class="sxs-lookup"><span data-stu-id="923dd-169">Define the profile</span></span>

<span data-ttu-id="923dd-170">配置文件内容应镜像数据提供程序的可访问属性， (例如：更新间隔) 。</span><span class="sxs-lookup"><span data-stu-id="923dd-170">Profile contents should mirror the accessible properties of the data provider (ex: update interval).</span></span> <span data-ttu-id="923dd-171">每个接口中定义的所有用户可配置属性都应包含在配置文件中。</span><span class="sxs-lookup"><span data-stu-id="923dd-171">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

<span data-ttu-id="923dd-172">如果新的数据提供程序扩展了现有的提供程序，则鼓励使用基类。</span><span class="sxs-lookup"><span data-stu-id="923dd-172">Base classes are encouraged if a new data provider extends an existing provider.</span></span> <span data-ttu-id="923dd-173">例如， [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) 扩展 [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) 以使客户能够提供将用作环境数据的三维模型。</span><span class="sxs-lookup"><span data-stu-id="923dd-173">For example, the [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) extends the [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) to enable customers to provide a 3D model to be used as the environment data.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

<span data-ttu-id="923dd-174">`CreateAssetMenu`特性可应用到配置文件类，使客户能够使用 "**创建**  >  **资产**  >  **混合现实工具包**  >  **配置文件**" 菜单创建配置文件实例。</span><span class="sxs-lookup"><span data-stu-id="923dd-174">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="923dd-175">实现检查器</span><span class="sxs-lookup"><span data-stu-id="923dd-175">Implement the inspector</span></span>

<span data-ttu-id="923dd-176">配置文件检查器是用于配置和查看配置文件内容的用户界面。</span><span class="sxs-lookup"><span data-stu-id="923dd-176">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="923dd-177">每个配置文件检查器应扩展此 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 类。</span><span class="sxs-lookup"><span data-stu-id="923dd-177">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="923dd-178">`CustomEditor`属性向 Unity 通知该检查器应用到的资产类型。</span><span class="sxs-lookup"><span data-stu-id="923dd-178">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="923dd-179">创建 () 的程序集定义</span><span class="sxs-lookup"><span data-stu-id="923dd-179">Create assembly definition(s)</span></span>

<span data-ttu-id="923dd-180">混合现实工具包使用程序集 [定义 () ](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html) 文件来指定组件之间的依赖关系，并协助 Unity 减少编译时间。</span><span class="sxs-lookup"><span data-stu-id="923dd-180">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="923dd-181">建议为所有数据访问接口及其编辑器组件创建程序集定义文件。</span><span class="sxs-lookup"><span data-stu-id="923dd-181">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="923dd-182">使用前面示例中的 [文件夹结构](#namespace-and-folder-structure) ，ContosoSpatialAwareness 数据提供程序有两个 asmdef 文件。</span><span class="sxs-lookup"><span data-stu-id="923dd-182">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoSpatialAwareness data provider.</span></span>

<span data-ttu-id="923dd-183">第一个程序集定义适用于数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="923dd-183">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="923dd-184">对于此示例，它将称为 ContosoSpatialAwareness，将位于示例的 *ContosoSpatialAwareness* 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="923dd-184">For this example, it will be called ContosoSpatialAwareness and will be located in the example's *ContosoSpatialAwareness* folder.</span></span> <span data-ttu-id="923dd-185">此程序集定义必须指定对 Microsoft.MixedReality.Toolkit 及其依赖的其他任何程序集的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="923dd-185">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="923dd-186">ContosoInputEditor 程序集定义将指定配置文件检查器以及任何特定于编辑器的代码。</span><span class="sxs-lookup"><span data-stu-id="923dd-186">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="923dd-187">此文件必须位于编辑器代码的根文件夹中。</span><span class="sxs-lookup"><span data-stu-id="923dd-187">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="923dd-188">此示例中的文件将位于 *ContosoSpatialAwareness\Editor* 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="923dd-188">In this example, the file will be located in the *ContosoSpatialAwareness\Editor* folder.</span></span> <span data-ttu-id="923dd-189">此程序集定义将包含对 ContosoSpatialAwareness 程序集的引用，以及：</span><span class="sxs-lookup"><span data-stu-id="923dd-189">This assembly definition will contain a reference to the ContosoSpatialAwareness assembly as well as:</span></span>

- <span data-ttu-id="923dd-190">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="923dd-190">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="923dd-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="923dd-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="923dd-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="923dd-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="923dd-193">注册数据提供程序</span><span class="sxs-lookup"><span data-stu-id="923dd-193">Register the data provider</span></span>

<span data-ttu-id="923dd-194">创建后，可以将数据提供程序注册到空间感知系统，以在应用程序中使用。</span><span class="sxs-lookup"><span data-stu-id="923dd-194">Once created, the data provider can be registered with the Spatial Awareness system to be used in the application.</span></span>

![选择空间对象网格观察程序](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="923dd-196">打包和分发</span><span class="sxs-lookup"><span data-stu-id="923dd-196">Packaging and distribution</span></span>

<span data-ttu-id="923dd-197">作为第三方组件分发的数据提供程序具有开发人员偏好的打包和分发的特定详细信息。</span><span class="sxs-lookup"><span data-stu-id="923dd-197">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="923dd-198">最常见的解决方案可能是生成 .unitypackage，然后通过 Unity 资产存储进行分发。</span><span class="sxs-lookup"><span data-stu-id="923dd-198">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="923dd-199">如果提交数据提供程序并将其作为 Microsoft Mixed Reality Toolkit 包的一部分接受，Microsoft MRTK 团队将打包并分发它作为 MRTK 产品/服务一部分。</span><span class="sxs-lookup"><span data-stu-id="923dd-199">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="923dd-200">另请参阅</span><span class="sxs-lookup"><span data-stu-id="923dd-200">See also</span></span>

- [<span data-ttu-id="923dd-201">空间感知系统</span><span class="sxs-lookup"><span data-stu-id="923dd-201">Spatial awareness system</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="923dd-202">`IMixedRealitySpatialAwarenessObject` 接口</span><span class="sxs-lookup"><span data-stu-id="923dd-202">`IMixedRealitySpatialAwarenessObject` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [<span data-ttu-id="923dd-203">`BaseSpatialAwarenessObject` 类</span><span class="sxs-lookup"><span data-stu-id="923dd-203">`BaseSpatialAwarenessObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [<span data-ttu-id="923dd-204">`SpatialAwarenessMeshObject` 类</span><span class="sxs-lookup"><span data-stu-id="923dd-204">`SpatialAwarenessMeshObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [<span data-ttu-id="923dd-205">`SpatialAwarenessPlanarObject` 类</span><span class="sxs-lookup"><span data-stu-id="923dd-205">`SpatialAwarenessPlanarObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [<span data-ttu-id="923dd-206">`IMixedRealitySpatialAwarenessObserver` 接口</span><span class="sxs-lookup"><span data-stu-id="923dd-206">`IMixedRealitySpatialAwarenessObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [<span data-ttu-id="923dd-207">`BaseSpatialObserver` 类</span><span class="sxs-lookup"><span data-stu-id="923dd-207">`BaseSpatialObserver` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [<span data-ttu-id="923dd-208">`IMixedRealitySpatialAwarenessMeshObserver` 接口</span><span class="sxs-lookup"><span data-stu-id="923dd-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [<span data-ttu-id="923dd-209">`IMixedRealityDataProvider` 交互</span><span class="sxs-lookup"><span data-stu-id="923dd-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="923dd-210">`IMixedRealityCapabilityCheck` 交互</span><span class="sxs-lookup"><span data-stu-id="923dd-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
