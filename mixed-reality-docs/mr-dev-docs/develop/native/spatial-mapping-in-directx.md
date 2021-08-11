---
title: DirectX 中的空间映射
description: 了解如何在 DirectX 应用中实现空间映射，以及如何在通用云平台 SDK Windows示例应用程序。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows混合现实， 空间映射， 环境， 交互， directx， winrt， api， 示例代码， UWP， SDK， 演练
ms.openlocfilehash: e7f0735ea28703d3a9f18198901ffa5f06676f78b7b8962bf20824e05f793061
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198843"
---
# <a name="spatial-mapping-in-directx"></a>DirectX 中的空间映射

> [!NOTE]
> 本文与旧版 WinRT 本机 API 相关。  对于新的本机应用项目，建议使用 **[OpenXR API](openxr-getting-started.md)**。

本主题介绍如何在 DirectX[](../../design/spatial-mapping.md)应用中实现空间映射，包括随 Universal Windows Platform SDK 一起打包的空间映射示例应用程序的详细说明。

本主题使用 [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 代码示例中的代码。

>[!NOTE]
>本文中的代码片段当前演示如何使用 C++/CX，而不是 C++17 兼容的 C++/WinRT，如 [C++](creating-a-holographic-directx-project.md)全息项目模板 中使用的。  这些概念等效于 C++/WinRT 项目，但需要转换代码。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>空间映射</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>DirectX 开发概述

空间映射的本机应用程序开发使用[Windows。Perception.Spatial](/uwp/api/Windows.Perception.Spatial)命名空间。 这些 API 提供对空间映射功能的完全控制，其方式与 Unity 公开空间映射 [API 的方式相同](../unity/spatial-mapping-in-unity.md)。

### <a name="perception-apis"></a>感知 API

为空间映射开发提供的主要类型如下：
* [SpatialSurfaceObserver](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) 以 SpatialSurfaceInfo 对象的形式提供有关用户附近应用程序指定空间区域内表面的信息。
* [SpatialSurfaceInfo](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo) 描述单个外部空间图面，包括唯一 ID、边界量和上次更改时间。 它将在请求时异步提供 SpatialSurfaceMesh。
* [SpatialSurfaceMeshOptions](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshOptions) 包含用于自定义从 SpatialSurfaceInfo 请求的 SpatialSurfaceMesh 对象的参数。
* [SpatialSurfaceMesh](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) 表示单个空间图面的网格数据。 顶点位置、顶点法线和三角形索引的数据包含在成员 SpatialSurfaceMeshBuffer 对象中。
* [SpatialSurfaceMeshBuffer](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMeshBuffer) 包装一种类型的网格数据。

使用这些 API 开发应用程序时，基本程序流将如下所示 (如以下示例应用程序中所述的示例) ：
- **设置 SpatialSurfaceObserver**
  - 调用 [RequestAccessAsync](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver)，以确保用户已授予应用程序使用设备的空间映射功能的权限。
  - 实例化 SpatialSurfaceObserver 对象。
  - 调用 [SetBoundingVolumes](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) 以指定需要空间图面相关信息的空间区域。 将来可以再次调用此函数来修改这些区域。 使用 [SpatialBoundingVolume 指定每个区域](/uwp/api/Windows.Perception.Spatial.SpatialBoundingVolume)。
  - 注册 [ObservedSurfacesChanged](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) 事件，每当有关于指定空间区域的空间图面的新信息可用时，该事件就会发生。
- **处理 ObservedSurfacesChanged 事件**
  - 在事件处理程序中，调用 [GetObservedSurfaces](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) 以接收 SpatialSurfaceInfo 对象的地图。 使用此地图，可以更新用户环境中存在哪些空间 [图面的记录](../../design/spatial-mapping.md#mesh-caching)。
  - 对于每个 SpatialSurfaceInfo 对象，可以查询[TryGetBounds](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo)以确定图面的空间范围（以你选择的空间坐标系[](../../design/coordinate-systems.md)表示）。
  - 如果决定请求空间图面的网格，请调用 [TryComputeLatestMeshAsync](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo)。 可以提供指定三角形密度以及返回的网格数据的格式的选项。
- **接收和处理网格**
  - 每次调用 TryComputeLatestMeshAsync 都会异步返回一个 SpatialSurfaceMesh 对象。
  - 在此对象中，可以访问包含的 SpatialSurfaceMeshBuffer 对象，这样，就可以访问网格的三角形索引、顶点位置和顶点法线（如果请求它们）。 此数据的格式与用于呈现网格的 [Direct3D 11](/windows/win32/api/d3d11/nf-d3d11-id3d11device-createbuffer) API 直接兼容。
  - 在这里，应用程序可以选择分析或 [处理](../../design/spatial-mapping.md#mesh-processing) 网格数据，并使用它来呈现 [和](../../design/spatial-mapping.md#rendering) 物理光线 [广播和冲突](../../design/spatial-mapping.md#raycasting-and-collision)。
  - 要注意的一个重要详细信息是，必须将刻度应用于网格顶点位置 (例如，在用于呈现网格) 的顶点着色器中，将它们从缓冲区中存储的优化整数单位转换为米。 可以通过调用 [VertexPositionScale](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh)来检索此刻度。

### <a name="troubleshooting"></a>疑难解答
* 不要忘记使用[SpatialSurfaceMesh.VertexPositionScale](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh)返回的刻度缩放顶点着色器中的网格顶点位置

## <a name="spatial-mapping-code-sample-walkthrough"></a>空间映射代码示例演练

全息 [空间映射](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 代码示例包括可用于开始将表面网格加载到应用的代码，包括用于管理和呈现图面网格的基础结构。

现在，我们将演练如何将图面映射功能添加到 DirectX 应用。 可以将此代码添加到[holographic](creating-a-holographic-directx-project.md) Windows模板项目中，也可以浏览上述代码示例。 此代码示例基于 Windows应用模板。

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>将应用设置为使用 spatialPerception 功能

应用可以使用空间映射功能。 这是必需的，因为空间网格是用户环境的表示形式，这可被视为私有数据。 在应用的 package.appxmanifest 文件中声明此功能。 下面的示例说明：

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

此功能来自 **uap2** 命名空间。 若要在清单中访问此命名空间，请作为 *xlmns* 属性包括在 Package &lt;> 元素中。 下面的示例说明：

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>检查空间映射功能支持

Windows Mixed Reality支持各种设备，包括不支持空间映射的设备。 如果应用可以使用空间映射或必须使用空间映射来提供功能，则应用应检查以确保在尝试使用空间映射之前支持空间映射。 例如，如果混合现实应用需要空间映射，如果用户尝试在没有空间映射的设备上运行空间映射，则它应显示一条有关该效果的消息。 或者，应用可以呈现自己的虚拟环境来表示用户的环境，从而提供类似于空间映射可用时发生的情况的体验。 在任何情况下，此 API 都允许应用了解何时不会获取空间映射数据，并做出适当的响应。

若要检查当前设备是否支持空间映射，首先请确保 UWP 协定处于级别 4 或更高，然后调用 SpatialSurfaceObserver：：IsSupported () 。 下面是如何在全息空间映射代码示例的 [上下文中](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 这样做的。 在请求访问权限之前，会检查支持。

SpatialSurfaceObserver：：IsSupported () API 从 SDK 版本 15063 开始提供。 如有必要，在使用此 API 之前，将项目重定目标到平台版本 15063。

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

当 UWP 协定小于级别 4 时，应用应继续，就像设备能够执行空间映射一样。

### <a name="request-access-to-spatial-mapping-data"></a>请求访问空间映射数据

在尝试创建任何图面观察程序之前，应用需要请求访问空间映射数据的权限。 下面是基于 Surface Mapping 代码示例的示例，本页稍后提供了更多详细信息：

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>创建图面观察器

**Windows：:P erception：：Spatial：：Surfaces** 命名空间包括 [SpatialSurfaceObserver](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver)类，该类观察 [你在 SpatialCoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem)中指定的一个或多个卷。 使用 [SpatialSurfaceObserver](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceObserver) 实例实时访问图面网格数据。

从 **AppMain.h**：

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

如上一部分所述，必须先请求访问空间映射数据，然后应用才能使用它。 此访问权限在应用程序上自动HoloLens。

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

接下来，需要配置图面观察器以观察特定的边界卷。 在这里，我们观察到一个 20x20x5 米的框，以坐标系原点为中心。

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

可以改为设置多个边界卷。

*这是伪代码：*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

还可使用其他边界形状，例如视图边线或未对齐轴的边界框。

*这是伪代码：*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

如果应用需要在图面映射数据不可用时执行任何不同操作，可以编写代码来响应不允许[SpatialPerceptionAccessStatus](/uwp/api/Windows.Perception.Spatial.SpatialPerceptionAccessStatus)的情况 - 例如，在附加沉浸式设备的 PC 上不允许它，因为这些设备没有用于空间映射的硬件。 对于这些设备，应改为依赖空间阶段来了解用户的环境和设备配置。

### <a name="initialize-and-update-the-surface-mesh-collection"></a>初始化和更新图面网格集合

如果已成功创建图面观察器，我们可以继续初始化图面网格集合。 在这里，我们使用拉取模型 API 来获取当前观测到的一组表面：

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

还有一个推送模型可用于获取图面网格数据。 可以选择将应用设计为仅使用拉取模型，在这种情况下，你将经常轮询数据（例如，每帧一次）或特定时间段（例如，在游戏设置期间）。 如果是这样，则需要用到上述代码。

在我们的代码示例中，我们选择了使用这两种模型来实现除教学之外目的。 在这里，我们将订阅事件，以便在系统识别更改时接收最新的 surface 网格数据。

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

我们的代码示例还配置为响应这些事件。 我们来看看如何实现此目的。

**注意：** 这可能不是你的应用程序处理网格数据的最有效方法。 此代码为清楚起见而编写，未经过优化。

在存储使用[Platform：： guid](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)作为键值的[SpatialSurfaceInfo](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceInfo)对象的只读映射中提供了 surface 网格数据。

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

为了处理此数据，我们首先查找集合中不是的键值。 本主题稍后将介绍如何将数据存储在示例应用中的详细信息。

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

我们还必须删除 surface 网格集合中的表面网格，但不再存在于系统集合中。 为此，我们需要执行类似于我们刚刚为添加和更新网格而显示的内容的操作;我们会循环访问应用的集合，并查看系统集合中是否存在 **Guid** 。 如果不在系统集合中，我们会将其删除。

通过 AppMain 中的事件处理程序：

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

RealtimeSurfaceMeshRenderer 中的网格修剪实现：

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>获取和使用 surface 网格数据缓冲区

获取 surface 网格信息非常简单，只需将数据收集和处理更新到该集合。 现在，我们将详细介绍如何使用数据。

在我们的代码示例中，我们选择使用 surface 网格进行呈现。 这是在真实表面上 occluding 全息影像的常见方案。 你还可以呈现网格，或呈现这些网格的已处理版本，以便在开始提供应用或游戏功能之前向用户显示房间的扫描区域。

当从我们在上一节中介绍的事件处理程序接收 surface 网格更新时，代码示例将启动进程。 此函数中的重要代码行是更新 surface *网格* 的调用：这次，我们已经处理了网格信息，我们即将获取用于显示的顶点和索引数据。

从 RealtimeSurfaceMeshRenderer：

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

我们的示例代码旨在使数据类 **SurfaceMesh** 处理网格数据处理和呈现。 这些网格是 **RealtimeSurfaceMeshRenderer** 实际保存地图的内容。 每个用户都引用了它所来自的 SpatialSurfaceMesh，因此，你可以随时使用它来访问网格顶点或索引缓冲区，或者获取网格转换。 现在，我们将网格标记为需要更新。

从 SurfaceMesh：

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

下一次要求网格绘制自身时，它将首先检查标志。 如果需要更新，则会在 GPU 上更新顶点和索引缓冲区。

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

首先，我们获取原始数据缓冲区：

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

然后，使用 HoloLens 提供的网格数据创建 Direct3D 设备缓冲区：

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**注意：** 有关上一代码片段中使用的 CreateDirectXBuffer helper 函数，请参阅 Surface 映射代码示例： SurfaceMesh、GetDataFromIBuffer。 现在，设备资源创建已完成，并且网格被视为已加载并准备好进行更新和呈现。

### <a name="update-and-render-surface-meshes"></a>更新和呈现 surface 网格

我们的 SurfaceMesh 类具有专用的更新函数。 每个 [SpatialSurfaceMesh](/uwp/api/Windows.Perception.Spatial.Surfaces.SpatialSurfaceMesh) 都有其自己的转换，我们的示例使用 **SpatialStationaryReferenceFrame** 的当前坐标系统来获取转换。 然后，它会更新 GPU 上的模型常量缓冲区。

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

当需要呈现 surface 网格时，请在呈现集合之前做一些准备工作。 我们为当前呈现配置设置着色器管道，并设置 "输入组装器" 阶段。 全息相机帮助器类 **CameraResources** 现在已经设置了视图/投影常量缓冲区。

From **RealtimeSurfaceMeshRenderer：： Render**：

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

完成此操作后，我们将在网格上循环，并告诉每个网格自行绘制。 **注意：** 此示例代码未经过优化，无法使用任何种类的截锥剔除，但你应在应用程序中包括此功能。

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

单个网格负责设置顶点和索引缓冲区、步幅和模型转换常量缓冲区。 与 Windows 全息应用程序模板中的旋转多维数据集一样，我们使用实例化来 stereoscopic 缓冲区。

From **SurfaceMesh：:D raw**：

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>用图面映射呈现选项

外围应用程序代码示例提供了用于封闭呈现 surface 网格数据的代码，以及用于在屏幕上呈现 surface 网格数据的代码。 选择的路径（或两者）取决于应用程序。 我们将在本文档中逐步介绍这两种配置。

**呈现全息效果的封闭缓冲区**

首先，清除当前虚拟摄像机的呈现目标视图。

从 AppMain：

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

这是一个 "预渲染" 阶段。 在这里，我们将通过请求网格呈现器来仅呈现深度来创建封闭缓冲区。 在此配置中，我们不会附加 "呈现目标" 视图，并且网格呈现器会将 "像素着色器" 阶段设置为 **nullptr** ，以便 GPU 不必消耗像素。 几何将栅格化到深度缓冲区，图形管道将停止。

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

我们可以使用针对图面映射封闭缓冲区的额外深度测试来绘制全息影像。 在此代码示例中，如果多维数据集位于图面后面，则将其呈现为不同的颜色。

从 AppMain：

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

基于 SpecialEffectPixelShader 中的代码。 hlsl：

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**注意：** 对于我们的 **GatherDepthLess** 例程，请参阅 Surface Mapping 代码示例： SpecialEffectPixelShader. hlsl。

**向显示器呈现 surface 网格数据**

我们还可以将表面网格绘制到立体声显示缓冲区。 我们选择使用光照绘制完全面，但可以自由地绘制线框，在渲染前处理网格，应用纹理地图等。

在这里，我们的代码示例告诉网格呈现器绘制集合。 这次我们不指定仅深度传递，它会附加像素着色器并使用为当前虚拟摄像机指定的目标完成呈现管道。

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>另请参阅
* [创建全息 DirectX 项目](creating-a-holographic-directx-project.md)
* [Windows。感知。空间 API](/uwp/api/Windows.Perception.Spatial)