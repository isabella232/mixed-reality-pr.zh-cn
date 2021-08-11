---
title: DirectX 中的坐标系统
description: 了解 DirectX 和混合现实中具有空间定位符、引用帧和空间定位点的坐标系。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: 混合现实， 空间定位器， 空间参考框架， 空间坐标系， 空间阶段， 示例代码， 图像稳定， 空间定位点， 空间定位点存储， 跟踪丢失， 演练， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: 5da521568ef15f0c512984c96846939bd30063d3485709d4b6568dc9b155052a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196436"
---
# <a name="coordinate-systems-in-directx"></a>DirectX 中的坐标系统

> [!NOTE]
> 本文与旧版 WinRT 本机 API 相关。  对于新的本机应用项目，建议使用 **[OpenXR API](openxr-getting-started.md)**。

[坐标系统](../../design/coordinate-systems.md)构成了由数据 API 提供的空间Windows Mixed Reality的基础。

如今的固定 VR 或单房间 VR 设备为跟踪空间建立一个主要坐标系。 混合现实设备（如 HoloLens）专为大型未定义环境而设计，设备在用户四处移动时发现和了解其环境。 设备可适应不断改进有关用户房间的知识，但会导致坐标系统在应用生存期内相互更改关系。 Windows Mixed Reality支持各种设备，范围从沉浸式头戴显示设备到世界附加参考帧。

>[!NOTE]
>本文中的代码片段当前演示如何使用 C++/CX，而不是 C++17 兼容的 C++/WinRT，如 [C++](creating-a-holographic-directx-project.md)全息项目模板 中使用的。  这些概念等效于 C++/WinRT 项目，但需要转换代码。

## <a name="spatial-coordinate-systems-in-windows"></a>空间坐标系统Windows

用于推理中实际坐标系的核心类型Windows <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>。 此类型的实例表示任意坐标系，提供一种方法用于获取转换矩阵数据，可用于在两个坐标系之间转换，而无需了解每个坐标系统的详细信息。

返回空间信息的方法将接受 SpatialCoordinateSystem 参数，使你可以决定返回这些坐标最有用的坐标系。 空间信息表示为用户周围的点、射线或音量，这些坐标的单位将始终以米为单位。

SpatialCoordinateSystem 与其他坐标系（包括表示设备位置的坐标系）具有动态关系。 在任何时间点，设备都可以找到一些坐标系，而不是其他坐标系。 对于大多数坐标系，应用必须准备好处理它们找不到的时间段。

应用程序不应直接创建 SpatialCoordinateSystems ，而应该通过 Perception API 使用它们。 感知 API 中坐标系统有三个主要来源，每个源映射到"坐标系统"页上 [描述的概](../../design/coordinate-systems.md) 念：
* 若要获取固定的参考框架，请创建 <a href="/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference，</a> 或者从当前 <a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference 获取一个</a>。
* 若要获取空间定位点，请创建 <a href="/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>。
* 若要获取附加的引用框架，请创建 <a href="/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>。

这些对象返回的所有坐标系都是右移的，+y 向上、+x 向右和 +z 向后。 可以通过将左侧或右侧手指指向正 x 方向，将手指指向正 y 方向来记住正 z 轴指向哪个方向。 你的拇指指向的方向（无论指向你还是相反方向）就是正 z 轴为坐标系统所指的方向。 下面的图例显示了这两个坐标系统。

![左侧和右侧坐标系](images/left-hand-right-hand.gif)<br>
*左侧和右侧坐标系*

使用<a href="/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>类创建附加或固定的引用框架，以基于位置启动到 SpatialCoordinateSystem HoloLens。 请继续阅读下一部分，详细了解此过程。

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>使用空间阶段将全息影像放在世界

使用静态<a href="/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference：：Current</a> Windows Mixed Reality头戴显示设备访问不透明头戴显示设备坐标系。 此 API 提供：

* 坐标系统
* 有关玩家是球员是球员还是移动玩家的信息
* 如果玩家是移动的，则用于四处移动的安全区域的边界
* 指示头戴显示设备是否是定向的。 
* 用于更新空间阶段的事件处理程序。

首先，获取空间阶段并订阅其更新： 

空间 **阶段初始化的代码**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

在 OnCurrentChanged 方法中，应用应检查空间阶段并更新播放器体验。 本示例提供阶段边界和用户指定的起始位置以及阶段视图范围和移动属性范围的可视化效果。 当无法提供阶段时，我们还回退到自己的固定坐标系。


空间阶段 **更新代码**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

定义阶段边界的顶点集按顺时针顺序提供。 用户Windows Mixed Reality Shell 在边界处绘制围栏，但出于自己的目的，你可能想要将可演练区域三角形化。 以下算法可用于将阶段三角形化。


空间阶段 **三角形化代码**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>使用固定参考框架将全息影像放在世界

[SpatialStationaryFrameOfReference](/uwp/api/Windows.Perception.Spatial.SpatialStationaryFrameOfReference)类表示在用户四处移动[](../../design/coordinate-systems.md#stationary-frame-of-reference)时相对于用户周围保持固定的引用框架。 此参考框架优先使坐标在设备附近保持稳定。 SpatialStationaryFrameOfReference 的一个关键用途是在呈现全息影像时充当渲染引擎中的基础世界坐标系。

若要获取 SpatialStationaryFrameOfReference，请使用 [SpatialLocator](/uwp/api/Windows.Perception.Spatial.SpatialLocator) 类并调用 [CreateStationaryFrameOfReferenceAtCurrentLocation](/uwp/api/Windows.Perception.Spatial.SpatialLocator)。

从Windows全息应用模板代码：

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* 固定参考框架旨在提供相对于整体空间的最佳拟合位置。 允许该引用帧中的单个位置略微偏移。 这是正常的，因为设备会详细了解环境。
* 当需要单个全息影像的精确位置时，应使用 SpatialAnchor 将单个全息影像定位到现实世界中的位置，例如，用户指示特别感兴趣的点。 定位点位置不会偏移，但可以更正;定位点将使用更正后下一帧中的已更正位置。

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>使用空间定位点将全息影像放在世界

[空间定位](../../design/coordinate-systems.md#spatial-anchors) 点是一种将全息影像放在现实世界中特定位置的不错方法，系统可确保定位点在一段时间保持不变。 本主题说明如何创建和使用定位点，以及如何使用定位点数据。

可以在选择的 SpatialCoordinateSystem 内的任何位置和方向创建 SpatialAnchor。 设备目前必须能够找到该坐标系，并且系统不得已达到其空间定位点的限制。

定义后，SpatialAnchor 的坐标系会不断调整，以保持其初始位置的精确位置和方向。 然后，可以使用此 SpatialAnchor 来呈现全息影像，这些全息影像将在此确切位置的用户周围显示固定。

当与定位点的距离增加时，使定位点保持就位的调整效果会放大。 应避免呈现相对于该定位点原点大约 3 米以上的定位点的内容。

[CoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor)属性获取一个坐标系统，用于相对于定位点放置内容，当设备调整定位点的精确位置时，将应用缓动。

使用 [RawCoordinateSystem](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) 属性和相应的 [RawCoordinateSystemAdjusted](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) 事件自己管理这些调整。

### <a name="persist-and-share-spatial-anchors"></a>持久保存和共享空间定位点

可以使用 SpatialAnchorStore 类在本地保留[SpatialAnchor，](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)然后在相同设备的未来应用会话中HoloLens它。

通过使用<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>，可以从本地 SpatialAnchor 创建持久云定位点，然后应用可以在多个 HoloLens、iOS 和 Android 设备上找到该定位点。  通过在多个设备上共享公共空间定位点，每个用户都可以实时查看相对于该定位点在同一物理位置呈现的内容。 

还可以将<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间定位</a>点用于跨设备、iOS HoloLens Android 设备的异步全息影像持久性。  通过共享持久云空间定位点，多个设备可以观察一段时间相同的持久全息影像，即使这些设备不同时存在于一起。

若要开始在 HoloLens 应用中构建共享体验，请尝试使用 5 分钟的 Azure 空间定位点HoloLens<a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">快速入门</a>。

使用 Azure 空间定位点启动并运行后，可以在<a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens。</a>  演练还适用于 Android 和 <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">iOS，</a> 使你可以在所有设备上共享相同的定位点。

### <a name="create-spatialanchors-for-holographic-content"></a>为全息内容创建 SpatialAnchors

对于此代码示例，我们修改了 holographic Windows模板，以在检测到按下的手势 **时** 创建定位点。 然后，在呈现过程中将多维数据集放置在定位点。

由于帮助程序类支持多个定位点，因此我们可以放置要使用此代码示例的多维数据集数量！

> [!NOTE]
> 定位点的 ID 是应用中控制的位置。 本示例创建了一个命名方案，该命名方案基于应用定位点集合中当前存储的定位点数进行顺序命名。

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>异步加载和缓存 SpatialAnchorStore

让我们看看如何编写 SampleSpatialAnchorHelper 类来帮助处理此持久性，包括：
* 存储由 Platform：：String 键编制索引的内存中定位点的集合。
* 从系统的 SpatialAnchorStore 加载定位点，该存储与本地内存中集合分开。
* 当应用选择这样做时，将定位点的本地内存中集合保存至 SpatialAnchorStore。

下面将了解如何在 [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) 中保存 [SpatialAnchor 对象](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)。

当 类启动时，我们将异步请求 SpatialAnchorStore。 这涉及到系统 I/O，因为 API 加载定位点存储，并且此 API 是异步的，因此 I/O 是非阻塞的。

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

你将获得一个 SpatialAnchorStore，可用于保存定位点。 这是一个 IMapView，用于将作为字符串的键值与 SpatialAnchors 的数据值关联。 在示例代码中，我们将它存储在私有类成员变量中，该变量可通过帮助程序类的公共函数访问。

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>别忘了挂钩暂停/恢复事件，保存并加载定位点存储。

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>将内容保存到定位点存储

当系统挂起应用时，需要将空间锚点保存到锚存储。 你还可以选择在其他时间将定位点保存到定位点存储区，就像你在应用的实现时所需要的那样。

准备尝试将内存中的定位标记保存到 SpatialAnchorStore 时，可以循环遍历集合并尝试保存每个定位点。

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>在应用恢复时从定位点存储加载内容

你可以还原 AnchorStore 中保存的定位点，方法是在你的应用程序恢复或随时恢复时将其从定位点存储区的 IMapView 传输到你自己的内存中数据库。

若要从 SpatialAnchorStore 还原定位点，请将你感兴趣的每个定位点还原到自己的内存中集合。

需要 SpatialAnchors 的内存中数据库，才能将字符串与所创建的 SpatialAnchors 相关联。 在我们的示例代码中，我们选择使用 Windows：： Foundation：：集合：： IMap 来存储定位点，这使得为 SpatialAnchorStore 使用相同的密钥和数据值变得简单。

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>可能无法立即定位还原的定位点。 例如，它可能是位于单独房间或不同建筑物中的定位点。 在使用从 AnchorStore 检索到的定位点之前应对其进行测试。

<br>

>[!NOTE]
>在此示例代码中，我们将从 AnchorStore 检索所有定位点。 这不是必需的;您的应用程序也可以选择使用对您的实现有意义的字符串键值，并选择某个定位点。

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>如果需要，请清除锚定存储

有时，您需要清除应用状态并写入新数据。 下面是如何通过 [SpatialAnchorStore](/uwp/api/Windows.Perception.Spatial.SpatialAnchorStore)执行此操作的方法。

使用我们的帮助器类，几乎不需要包装 Clear 函数。 我们选择在示例实现中执行此操作，因为我们的帮助器类被赋予了拥有 SpatialAnchorStore 实例的责任。

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>示例：将定位坐标系与固定引用帧坐标系统相关联

假设你有一个定位点，并且想要将定位点坐标系统中的某些内容关联到其他内容所使用的 SpatialStationaryReferenceFrame。 您可以使用 [TryGetTransformTo](/uwp/api/Windows.Perception.Spatial.SpatialCoordinateSystem) 从定位点的坐标系统获取转换为固定参考帧的转换：

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

此过程可通过两种方式来实现：
1. 它告诉你是否可以彼此理解两个引用框架，以及
2. 如果是这样，它将提供一个转换，以便直接从一个坐标系转换到另一个坐标系统。

使用此信息，您可以了解两个引用帧之间对象之间的空间关系。

对于呈现，通常可以根据对象的原始参考框架或锚点对它们进行分组，从而获得更好的结果。 为每个组执行单独的绘图处理。 对于具有最初使用同一坐标系统创建的模型转换的对象，视图矩阵更准确。

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>使用设备附加的参考框架创建全息影像

有时，你想要呈现已 [附加](../../design/coordinate-systems.md#attached-frame-of-reference) 到设备位置的全息影像，例如，当设备只能确定其方向而不能确定其在空间中的位置时，包含调试信息或信息性消息的面板。 为此，我们使用附加的参考框架。

SpatialLocatorAttachedFrameOfReference 类定义了相对于设备而不是实际的坐标系统。 此框架的固定标题相对于用户在创建引用框架时面向的方向的用户环境。 接下来，这一帧参考中的所有方向都是相对于该固定标题的，即使用户要旋转设备也是如此。

对于 HoloLens，此帧坐标系统的原点位于用户头旋转中心，因此其位置不受 head 旋转的影响。 您的应用程序可以指定与此点相对的偏移量，以将全息影像置于用户的前端。

若要获取 SpatialLocatorAttachedFrameOfReference，请使用 SpatialLocator 类并调用 CreateAttachedFrameOfReferenceAtCurrentHeading。

这适用于整个 Windows Mixed Reality 设备范围。

### <a name="use-a-reference-frame-attached-to-the-device"></a>使用附加到设备的引用框架

这些部分讨论了在 "Windows 全息" 应用模板中所做的更改，以使用此 API 启用设备附加的参考框架。 此 "附加" 的全息图将与固定或定位全息影像一起工作，并且在设备暂时无法找到其在世界各地的位置时也可能会用到它。

首先，我们将模板更改为存储 SpatialLocatorAttachedFrameOfReference 而不是 SpatialStationaryFrameOfReference：

从 **HolographicTagAlongSampleMain**：

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

从 **HolographicTagAlongSampleMain**：

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

在更新过程中，我们会在从帧预测获得的时间戳处获取坐标系统。

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>获取空间指针姿势，并遵循用户的注视

我们希望我们的示例全息图跟随用户的 [注视](../../design/gaze-and-commit.md)，这与全息 shell 可以遵循用户的注视方式类似。 为此，我们需要从相同的时间戳中获取 SpatialPointerPose。

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

此 SpatialPointerPose 包含根据 [用户的当前标题](gaze-in-directx.md)放置全息影像所需的信息。

为了用户舒适，我们使用线性内插 ( "lerp" ) 在一段时间内使更改位置平滑。 这比将全息图锁定到其注视的用户更适合。 Lerping 的标记，还可以通过抑制移动来使全息影像稳定。 如果未执行此抑制，用户将看到全息影像抖动，因为通常会将其视为让的用户。

From **StationaryQuadRenderer：:P ositionhologram**：

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>对于调试面板，您可以选择将全息图从一边重定位到一边，使其不会妨碍您的视图。 下面是有关如何执行此操作的示例。

对于 **StationaryQuadRenderer：:P ositionhologram**：

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>旋转全息图以面对相机

不能定位全息图（在本例中为四部分），还必须旋转对象，使其面向用户。 这种旋转发生在世界空间中，因为这种类型的 billboarding 允许全息图保留在用户的环境中。 由于全息图锁定为显示方向，因此，billboarding 不是很舒适：在这种情况下，你还必须在左视图和右视图矩阵之间进行插值，才能获得不会干扰立体声呈现的视图空间布告栏转换。 在这里，我们将旋转 X 和 Z 轴以面对用户。

From **StationaryQuadRenderer：： Update**：

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>呈现附加全息图

在此示例中，我们还会选择在 SpatialLocatorAttachedReferenceFrame 的坐标系统中呈现全息影像，这是我们放置全息图的位置。  (如果我们决定使用另一个坐标系统进行呈现，则需要从设备附加的参考框架的坐标系统到该坐标系统获取转换。 ) 

From **HolographicTagAlongSampleMain：： Render**：

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

就这么简单！ 现在，全息图将 "跟踪" 在用户看看方向上为2米的位置。

>[!NOTE]
>此示例还会加载其他内容-请参阅 StationaryQuadRenderer。

## <a name="handling-tracking-loss"></a>处理跟踪丢失

当设备在世界各地找不到自己时，应用程序会遇到 "跟踪丢失" 的情况。 Windows Mixed Reality 应用应能够应对位置跟踪系统的此类中断。 通过使用默认 SpatialLocator 上的 LocatabilityChanged 事件，可以观察到这些中断，并创建响应。

From **AppMain：： SetHolographicSpace：**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

当你的应用收到 LocatabilityChanged 事件时，它可以根据需要更改行为。 例如，在 PositionalTrackingInhibited 状态下，你的应用程序可以暂停正常操作，并呈现显示一条警告消息的 [标记](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) 。

Windows 全息应用模板附带了一个已为你创建的 LocatabilityChanged 处理程序。 默认情况下，当位置跟踪不可用时，它将在调试控制台中显示警告。 可以向此处理程序添加代码，以根据需要从应用程序中提供响应。

从 **AppMain：**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>空间映射

[空间映射](spatial-mapping-in-directx.md)api 使用坐标系统获取 surface 网格的模型转换。

## <a name="see-also"></a>另请参阅
* [坐标系统](../../design/coordinate-systems.md)
* [空间定位点](../../design/spatial-anchors.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的空间映射](spatial-mapping-in-directx.md)