---
title: Unity 中的空间映射
description: 了解如何在 Unity 混合现实应用中使用和管理与你的真实世界几何之间的渲染和冲突。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，空间映射，呈现器，碰撞器，网格，扫描，组件，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实 Toolkit
ms.openlocfilehash: 62e4c4fad725dbe58773035b0bb47f1911098217
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905705"
---
# <a name="spatial-mapping-in-unity"></a>Unity 中的空间映射

使用[空间映射](../../design/spatial-mapping.md)可以检索表示世界上的表面的三角形网格，这些网格围绕 HoloLens 设备。 你可以使用 "位置"、"封闭" 和 "房间" 分析的 surface data，为 Unity 项目提供浸入式的额外剂量。

Unity 包含对空间映射的完全支持，可通过以下方式向开发人员公开：

1. MixedRealityToolkit 中提供了空间映射组件，可为空间映射入门提供方便快捷的路径
2. 较低级别的空间映射 Api，提供完全控制并实现更复杂的特定于应用程序的自定义

若要在应用中使用空间映射，需要在 Appxmanifest.xml 中设置 SpatialPerception 功能。

## <a name="device-support"></a>设备支持

| 特征 | [第一代 (HoloLens) ](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hololens2-hardware) | [沉浸式头戴显示设备](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| 空间映射 | ✔️ | ✔️ | ❌ |

## <a name="setting-the-spatialperception-capability"></a>设置 SpatialPerception 功能

为了使应用程序能够使用空间映射数据，必须启用 SpatialPerception 功能。

如何启用 SpatialPerception 功能：

1. 在 Unity 编辑器中，打开 **"Player 设置"** 窗格 (编辑 > Project 设置 > 播放机) 
2. 选择 **"Windows 存储"** 选项卡
3. 展开 **"发布设置"** ，然后检查 **"功能"** 列表中的 **"SpatialPerception"** 功能

> [!NOTE]
> 如果已将 Unity 项目导出到 Visual Studio 解决方案，则需要导出到新文件夹或在[Visual Studio 的 appxmanifest.xml 中手动设置此功能](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

空间映射还需要至少10.0.10586.0 的 MaxVersionTested：

1. 在 Visual Studio 中，右键单击解决方案资源管理器中的 **appxmanifest.xml** ，然后选择 "**查看代码**"
2. 查找指定 **y** 的行，并将 **MaxVersionTested = "10.0.10240.0"** 更改为 **MaxVersionTested = "10.0.10586.0"**
3. **保存** appxmanifest.xml。

## <a name="how-to-add-mapping-in-unity"></a>如何在 Unity 中添加映射

[!INCLUDE[](includes/unity-spatial-mapping.md)]

## <a name="higher-level-mesh-analysis-spatial-understanding"></a>更高级别的网格分析：空间理解

> [!CAUTION]
> 空间理解已弃用，以支持 [场景理解](../../design/scene-understanding.md)。

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是一系列实用工具代码，适用于基于 Unity 的全息 api 构建的全息开发。

### <a name="spatial-understanding"></a>空间理解

在物理环境中放置全息影像时，通常需要超越空间映射的网格和面平面。 过程放置完成后，需要更高级别的环境理解。 这通常需要作出有关楼层、天花板和墙壁的决策。 您还可以根据一组放置约束进行优化，以确定全息对象的最佳物理位置。

在 Conker 和片段的开发过程中，Asobo 工作室通过开发房间规划求解来面对此问题。 其中每个游戏都有特定于游戏的需求，但它们共享了核心空间理解技术。 HoloToolkit SpatialUnderstanding 库封装了这一技术，使你能够快速找到墙上的空白空间，将对象放置在天花板上，识别出要放置的字符，以及其他大量的空间理解查询。

所有源代码都包含在内，使你可以根据需要对其进行自定义，并与社区分享你的改进。 C + + 求解器的代码已包装到 UWP dll 中，并通过包含在 MixedRealityToolkit 中的 prefab 向 Unity 公开。

### <a name="understanding-modules"></a>了解模块

模块公开了三个主要接口：用于简单的图面和空间查询的拓扑、用于对象检测的形状，以及用于基于约束的对象集放置的对象放置规划求解。 下面介绍上述每种方式。 除了三个主要模块接口外，ray 强制转换接口还可用于检索标记的表面类型，并可将自定义 watertight playspace 网格复制出来。

### <a name="ray-casting"></a>Ray 转换

完成房间扫描后，会在内部生成标签，如地面、天花板和墙。 此 `PlayspaceRaycast` 函数采用一条射线，如果该射线与已知表面冲突，则返回; 如果是，则返回有关该图面的形式的信息 `RaycastResult` 。

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology,
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface,
                    //  but vertical surface that looks like a
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

在内部，raycast 是根据 playspace 的计算出的 8 cm 立方 voxel 表示形式计算出来的。 每个 voxel 都包含一组具有已处理拓扑数据的 surface 元素 (亦即 surfels) 。 将比较交叉 voxel 单元中包含的 surfels 和用于查找拓扑信息的最佳匹配项。 此拓扑数据包含以 "SurfaceTypes" 枚举形式返回的标签，以及相交表面的外围应用。

在 Unity 示例中，游标将每个帧都转换为射线。 首先，针对 Unity 的 colliders。 其次，针对 "了解模块" 的世界表示。 最后又是一个 UI 元素。 在此应用程序中，UI 获得优先级，接下来是理解结果，最后是 Unity colliders。 SurfaceType 将报告为光标旁边的文本。

![曲面类型在光标旁边标记](images/su-raycastresults-300px.jpg)<br>
*曲面类型在光标旁边标记*

### <a name="topology-queries"></a>拓扑查询

在 DLL 中，拓扑管理器处理环境的标记。 如上所述，很多数据存储在 surfels 中，包含在 voxel 卷中。 此外，"PlaySpaceInfos" 结构用于存储有关 playspace 的信息，其中包括世界对齐 (下面) 、楼层和天花板高度的详细信息。 试探法用于确定地面、天花板和墙。 例如，具有大于 1-m2 的图面区域的最大和最低水平曲面被视为楼层。

> [!NOTE]
> 在此过程中也使用了扫描过程中的照相机路径。

拓扑管理器公开的查询子集通过 dll 公开。 公开的拓扑查询如下所示。

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

每个查询都具有一组特定于查询类型的参数。 在下面的示例中，用户指定了所需的卷的最小高度 & 宽度、地面上的最小位置高度以及卷前面的最小间隙量。 所有度量都以米为单位。

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

其中每个查询都使用 "TopologyResult" 结构的预分配数组。 "LocationCount" 参数指定传入数组的长度。 返回值报告返回的位置的数量。 此数字绝不会大于 "locationCount" 参数中传递的值。

"TopologyResult" 包含返回的卷的中心位置，方向 (如 normal) ，以及所找到空间的尺寸。

```cpp
struct TopologyResult
{
    DirectX::XMFLOAT3 position;
    DirectX::XMFLOAT3 normal;
    float width;
    float length;
};
```

> [!NOTE]
> 在 Unity 示例中，其中每个查询都链接到 "虚拟 UI" 面板中的某个按钮。 示例将每个查询的参数硬编码为合理的值。 有关更多示例，请参阅示例代码中的 SpaceVisualizer。

### <a name="shape-queries"></a>形状查询

在 dll 中，形状分析器 ( "ShapeAnalyzer_W" ) 使用拓扑分析器与用户定义的自定义形状相匹配。 Unity 示例定义一组形状，并通过 "应用内查询" 菜单在 "形状" 选项卡中公开结果。其目的在于，用户可以根据应用程序的需要定义自己的对象形状查询并使用这些查询。

形状分析仅适用于水平曲面。 例如，沙发由平面座位表面和沙发顶部的扁平顶部定义。 形状查询查找特定大小、高度和方位范围的两个图面，两个图面对齐并连接起来。 使用 Api 术语，沙发座位和后端是形状组件，对齐要求是形状组件约束。

"Sittable" 对象在 Unity 示例 () ShapeDefinition 中定义的示例查询如下所示。

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

每个形状查询都由一组形状组件定义，每个形状组件都具有一组组件约束和一组形状约束，它们列出组件之间的依赖关系。 此示例在单个组件定义中包含三个约束，组件之间没有任何形状约束 (因为只有一个组件) 。

与此相反，沙发形状具有两个形状组件和四个形状约束。 组件由其在用户的组件列表中的索引标识，在此示例中 (0 和 1) 。

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

在 Unity 模块中提供包装函数以便于创建自定义形状定义。 可以在 "ShapeComponentConstraint" 和 "ShapeConstraint" 结构内的 "SpatialUnderstandingDll" 中找到组件和形状约束的完整列表。

![在此图面上找到矩形形状](images/su-shapequery-300px.jpg)<br>
*在此图面上找到矩形形状*

### <a name="object-placement-solver"></a>对象放置规划求解

对象放置规划求解可用于确定放置对象的物理空间中的理想位置。 在给定对象规则和约束的情况下，求解器将找到最适合的位置。 此外，对象查询会一直保留，直到删除了带 "Solver_RemoveObject" 或 "Solver_RemoveAllObjects" 调用的对象，从而允许约束的多对象位置。 对象放置查询由三个部分组成：具有参数的放置类型、规则列表和约束列表。 若要运行查询，请使用以下 API。

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

此函数采用对象名称、位置定义和规则和约束列表。 C # 包装提供构造 helper 函数，使规则和约束构造变得简单。 放置定义包含查询类型，即以下其中一项。

```cpp
public enum PlacementType
{
    Place_OnFloor,
    Place_OnWall,
    Place_OnCeiling,
    Place_OnShape,
    Place_OnEdge,
    Place_OnFloorAndCeiling,
    Place_RandomInAir,
    Place_InMidAir,
    Place_UnderFurnitureEdge,
};
```

每个放置类型都具有一组特定于该类型的参数。 "ObjectPlacementDefinition" 结构包含一组静态 helper 函数，用于创建这些定义。 例如，若要查找在楼层上放置对象的位置，可以使用以下函数。 public static ObjectPlacementDefinition Create_OnFloor (System.numerics.vector2 halfDims) 除了放置类型之外，还可以提供一组规则和约束。 不能违反规则。 然后，将根据一组约束优化满足类型和规则的可能放置位置，以便选择最佳放置位置。 每个规则和约束都可以通过提供的静态创建函数来创建。 下面提供了一个示例规则和约束构造函数。

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

以下对象放置查询正在寻找一个位置，用于将半米式立方体放置在表面的边缘，远离其他以前放置的对象，靠近房间的中心。

```cs
List<ObjectPlacementRule> rules =
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints =
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f),
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

如果成功，则返回包含放置位置、尺寸和方向的 "ObjectPlacementResult" 结构。 此外，放置将添加到 dll 的已放置对象的内部列表中。 后续的放置查询会将此对象考虑在内。 Unity 示例中的 "LevelSolver" 文件包含更多示例查询。

![对象放置的结果](images/su-objectplacement-1000px.jpg)<br>
*图3：从三个位置对地面查询产生的结果与相机位置规则的结果的蓝色方框*

当对级别或应用程序方案所需的多个对象的放置位置进行求解时，首先要解决不必要的对象和大型对象，以便最大程度地提高空间。 放置顺序很重要。 如果找不到对象位置，请尝试减少不受约束的配置。 具有一组后备配置对于跨许多房间配置支持功能至关重要。

### <a name="room-scanning-process"></a>房间扫描过程

虽然 HoloLens 提供的空间映射解决方案设计为能够满足整个范围的问题空间的一般需求，但却构建了空间理解模块来支持两个特定游戏的需求。 其解决方案是围绕特定过程和假设集构造的，如下所示。

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

用户驱动的 playspace "painting" –在扫描阶段，用户移动并浏览重头戏，并有效地绘制应包括的区域。 在此阶段，生成的网格非常重要，可提供用户反馈。 室内家庭或办公设置–查询函数围绕平整表面和墙壁围绕直角设计。 这是一个软限制。 但是，在扫描阶段，将完成主轴分析以按主要轴和次要轴优化网格分割。 包含的 SpatialUnderstanding 文件管理扫描阶段过程。 它调用以下函数。

```txt
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan –
    Called each frame to update the scanning process. The camera position and
    orientation is passed in and is used for the playspace painting process,
    described above.

GeneratePlayspace_RequestFinish –
    Called to finalize the playspace. This will use the areas “painted” during
    the scan phase to define and lock the playspace. The application can query
    statistics during the scanning phase as well as query the custom mesh for
    providing user feedback.

Import_UnderstandingMesh –
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by
    the module and placed on the understanding prefab will periodically query the
    custom mesh generated by the process. In addition, this is done once more
    after scanning has been finalized.
```

由 "SpatialUnderstanding" 行为驱动的扫描流将调用 InitScan，然后 UpdateScan 每个帧。 当统计信息查询报告合理的范围时，允许用户 airtap 调用 RequestFinish 以指示扫描阶段结束。 继续调用 UpdateScan，直到其返回值指示 dll 已完成处理。

### <a name="understanding-mesh"></a>了解网格

理解 dll 在内部将 playspace 存储为 8 cm 大小的 voxel 多维数据集的网格。 在扫描的初始部分中，将完成主要组件分析以确定房间的轴。 在内部，它存储其 voxel 空间与这些轴对齐。 大约每秒生成一次网格，方法是从 voxel 卷中提取等值面。

![从 voxel 卷生成的生成的网格](images/su-custommesh.jpg)<br>
*从 voxel 卷生成的生成的网格*

## <a name="troubleshooting"></a>疑难解答

* 确保已设置 [SpatialPerception](#setting-the-spatialperception-capability) 功能
* 跟踪丢失时，下一个 OnSurfaceChanged 事件将删除所有网格。

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>混合现实中的空间映射 Toolkit

有关在混合现实 Toolkit 中使用空间映射的详细信息，请参阅 MRTK 文档的[空间感知部分](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started)。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [文本](text-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>请参阅

* [坐标系统](../../design/coordinate-systems.md)
* [Unity 中的坐标系统](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine</a>
