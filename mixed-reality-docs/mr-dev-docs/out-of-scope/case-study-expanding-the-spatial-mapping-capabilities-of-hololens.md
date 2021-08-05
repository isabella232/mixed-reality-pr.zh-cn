---
title: 案例研究 - 扩展应用程序的空间映射HoloLens
description: 创建第一个Microsoft HoloLens应用时，我们想知道我们可以在设备上推送空间映射的边界。
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、空间映射
ms.openlocfilehash: f0438990c39570f9188e2e150a8cbe7907d72f7e2be260c72e41646565b8d89e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210432"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>案例研究 - 扩展应用程序的空间映射HoloLens

创建第一个Microsoft HoloLens应用时，我们想知道我们可以在设备上推送空间映射的边界。 Microsoft Studios 的软件工程师 Jeff Evertt 介绍了如何开发新技术，无需对全息影像如何在用户的实际环境中进行更多控制。

> [!NOTE]
> HoloLens 2实现新的场景理解运行时[，它为](../design/scene-understanding.md)混合现实开发人员提供了结构化的高级别环境表示形式，旨在直观地为环境感知应用程序进行开发。 

## <a name="watch-the-video"></a>观看视频

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>超出空间映射范围

当我们处理片段和[](https://www.microsoft.com/p/fragments/9nblggh5ggm8)[Young Conker（HoloLens](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)的第一个游戏之一）时，我们发现，当我们在物理世界执行全息影像过程放置时，我们需要更高级别地了解用户的环境。 每个游戏都有其自己的特定放置需求：例如，在片段中，我们希望能够区分不同的表面（如楼层或表）以将线索放在相关位置。 我们还希望能够识别生命大小的全息字符可以位于的图面上，例如一个长相或一张长条。 在 Young Conker 中，我们希望 Conker 及其手下能够将球员房间中的凸面用作平台。

[我们的游戏开发合作伙伴 Asobo Studios](https://www.asobostudio.com/index.html)解决了此问题，并创建了一种扩展游戏空间映射功能的技术HoloLens。 使用这种方法，我们可以分析球员房间并识别表面，例如墙、表、地板和楼层。 它还使我们能够针对一组约束进行优化，以确定全息对象的最佳位置。

## <a name="the-spatial-understanding-code"></a>空间理解代码

我们采用 Asobo 的原始代码并创建了一个封装此技术的库。 Microsoft 和 Asobo 现已开放源代码此代码，并可在 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) 上使用它，供你用于自己的项目。 所有源代码都包含在一起，可让你根据需要对其进行自定义，并与社区共享改进。 C++ 求解器的代码已包装到 UWP DLL 中，并公开给 Unity，其中包含 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)中包含的下拉预制。

Unity 示例中包含许多有用的查询，可用于在墙上查找空格、将对象放在顶上或放在楼层上的大空间上、识别字符的放置位置，以及大量其他空间理解查询。

尽管 HoloLens 提供的空间映射解决方案设计为足够通用，足以满足整个问题空间的需求，但构建空间理解模块是为了支持两个特定游戏的需求。 因此，其解决方案是围绕特定过程和一组假设构建的：
* **固定大小 playspace：** 用户指定 init 调用中的最大 playspace 大小。
* **一次扫描过程**：该过程需要一个离散的扫描阶段，用户可在这里四处浏览，定义 playspace。 在扫描完成之前，查询函数将无法正常工作。
* **用户驱动的播放空间"绘制**"：在扫描阶段，用户移动并查看 playspace，有效地绘制应包含的区域。 生成的网格对于在此阶段提供用户反馈非常重要。
* **室内家庭或办公室设置**：查询函数围绕直角的平面和墙进行设计。 这是软限制。 但是，在扫描阶段，完成主轴分析以优化主轴和次轴的网格分面。

### <a name="room-scanning-process"></a>房间扫描过程

加载空间理解模块时，要做的第一件事就是扫描空间，以便标识和标记所有可用表面（如楼层、上限和墙）。 在扫描过程中，查看房间并"绘制"扫描中应包含的区域。

在此阶段看到的网格是一项重要的视觉反馈，可让用户知道正在扫描房间的哪些部分。 空间理解模块的 DLL 在内部将 playspace 存储为大小为 8cm 的体xel 立方体网格。 在扫描的初始部分，将完成主要组件分析以确定房间的轴。 在内部，它存储与这些轴对齐的体xel 空间。 大约每秒通过从体xel 卷中提取等值面来生成网格。

![以白色表示的空间映射网格，并理解绿色中的 playspace 网格](images/spatial-mapping-500px.png)

以白色表示的空间映射网格，并理解绿色中的 playspace 网格



包含的 SpatialUnderunder.cs 文件管理扫描阶段过程。 它调用以下函数：
* **SpatialUnderstanding_Init：** 在开始时调用一次。
* **GeneratePlayspace_InitScan：** 指示扫描阶段应开始。
* **GeneratePlayspace_UpdateScan_DynamicScan：** 调用每个帧以更新扫描过程。 相机位置和方向传入，用于播放空间绘制过程，如上所述。
* **GeneratePlayspace_RequestFinish：** 调用 以完成 playspace。 这将在扫描阶段使用"绘制"区域来定义和锁定 playspace。 应用程序可以在扫描阶段查询统计信息，并查询自定义网格以提供用户反馈。
* **Import_UnderstandingMesh：** 在扫描期间，模块提供的、放置在理解预制项上的 **SpatialUnderstandingCustomMesh** 行为将定期查询进程生成的自定义网格。 此外，在扫描完成之后，会再次完成此操作。

由 **SpatialUnderunder** 行为驱动的扫描流调用 **InitScan**，然后 **更新Scan 每个** 帧。 当统计信息查询报告合理的覆盖范围时，用户可以通过 airtap 调用 **RequestFinish** 来指示扫描阶段结束。 **UpdateScan** 将继续调用，直到其返回值指示 DLL 已完成处理。

## <a name="the-queries"></a>查询

扫描完成后，你将能够访问 接口中的三种不同类型的查询：
* **拓扑查询**：这些查询是基于扫描房间的拓扑的快速查询。
* **形状查询**：这些查询利用拓扑查询的结果来查找与定义的自定义形状非常匹配的水平图面。
* **对象放置查询**：这些是更复杂的查询，这些查询根据对象的一组规则和约束查找最佳位置。

除了三个主要查询外，还有一个光线广播接口，可用于检索标记的图面类型，并可以复制自定义 watertight 房间网格。

### <a name="topology-queries"></a>拓扑查询

在 DLL 中，拓扑管理器处理环境的标签。 如上所述，大部分数据存储在体量体中。 此外 **，PlaySpaceInfos** 结构用于存储有关播放空间的信息，包括世界对齐方式 (下面列出了有关) 、楼层和上限高度的详细信息。

启发法用于确定楼层、上限和墙。 例如，最大和最低水平图面大于 1 m2 的图面被视为地面。 请注意，扫描过程中也使用照相机路径。

拓扑管理器公开的一部分查询通过 DLL 公开。 公开的拓扑查询如下所示：
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

每个查询都有一组特定于查询类型的参数。 在下面的示例中，用户指定所需&的最小高度、最低放置高度（位于楼层上方）和卷前面的最小排空量。 所有度量以米为单位。




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

每个查询采用预分配的 **TopologyResult** 结构数组。 **locationCount** 参数指定传入数组的长度。 返回值报告返回的位置数。 此数字永远不会大于传入 **的 locationCount** 参数。

**TopologyResult** 包含返回的卷的中心位置、 (方向（即正常) 和找到空间的尺寸）。




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

请注意，在 Unity 示例中，每个查询都链接到虚拟 UI 面板中的按钮。 示例将每个查询的参数硬编码为合理的值。 有关更多示例，请参阅示例代码中的 *SpaceVisualizer.cs。*

### <a name="shape-queries"></a>形状查询

在 DLL 中，形状分析器 **(ShapeAnalyzer_W)** 拓扑分析器来匹配用户定义的自定义形状。 Unity 示例在形状选项卡上具有一组预定义的形状，这些形状显示在查询菜单中。

请注意，形状分析仅适用于水平图面。 例如，一个长子由平底的席位表面和靠后的平顶定义。 形状查询查找特定大小、高度和纵横范围的两个图面，两个图面对齐并连接。 使用 API 术语时，长套式席位和靠背是形状组件，对齐要求是形状组件约束。

在 Unity 示例 (**ShapeDefinition.cs**) 中为"sittable"对象定义的示例查询如下所示：




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

每个形状查询由一组形状组件定义，每个组件具有一组组件约束和一组形状约束，这些约束列出组件之间的依赖关系。 此示例在单个组件定义中包含三个约束，并且组件之间没有形状约束 (因为只有一个组件) 。

相比之下，长相形状有两个形状组件和四个形状约束。 请注意，组件由用户组件列表中的索引标识， (0 和 1 作为) 。




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Unity 模块中提供了包装函数，方便创建自定义形状定义。 可以在 **ShapeComponentConstraint** 和 **ShapeConstraint** 结构内的 **SpatialUnderunderdll.cs** 中找到组件和形状约束的完整列表。

![蓝色矩形突出显示了长方形查询的结果。](images/chair-shape-query-500px.png)

蓝色矩形突出显示了长方形查询的结果。



### <a name="object-placement-solver"></a>对象放置求解器

对象放置查询可用于识别物理房间中放置对象的理想位置。 求解器将查找给定对象规则和约束的最佳位置。 此外，对象查询将一直存在，直到通过Solver_RemoveObject或Solver_RemoveAllObjects删除对象，从而允许受约束的多对象放置。

对象放置查询由三部分组成：具有参数的放置类型、规则列表和约束列表。 若要运行查询，请使用以下 API：




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
此函数采用对象名称、放置定义以及规则和约束的列表。 C# 包装器提供构造帮助程序函数，使规则与约束构造变得简单。 放置定义包含查询类型，即以下类型之一：




```
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

每个放置类型都有一组类型唯一的参数。 **ObjectPlacementDefinition** 结构包含一组用于创建这些定义的静态帮助程序函数。 例如，若要查找将对象放在楼层的位置，可以使用以下函数： 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

除了放置类型之外，还可以提供一组规则和约束。 不能违反规则。 然后，根据约束集优化满足类型和规则的可能放置位置，以选择最佳放置位置。 每个规则和约束都可以由提供的静态创建函数创建。 下面提供了一个示例规则与约束构造函数。




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

下面的对象放置查询正在查找一个在表面边缘放置半米立方体的位置，远离其他以前放置的对象和靠近房间中心的位置。




```
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

如果成功，则返回包含放置位置、维度和方向的 **ObjectPlacementResult** 结构。 此外，放置将添加到 DLL 的已放置对象的内部列表中。 后续放置查询将考虑此对象。 Unity **示例中的 LevelSolver.cs** 文件包含更多示例查询。

![蓝色框显示三个"放置到楼层"查询的结果，这些查询具有"离开相机位置"规则。](images/away-from-camera-position-500px.png)

蓝色框显示三个"放置到楼层"查询的结果，这些查询具有"离开相机位置"规则。


**提示：**
* 在解决级别或应用程序方案所需的多个对象的放置位置时，首先解决空对象和大型对象，以最大程度地提高找到空间的概率。
* 放置顺序非常重要。 如果找不到对象放置，请尝试约束较少的配置。 拥有一组回退配置对于支持多个房间配置中的功能至关重要。

### <a name="ray-casting"></a>光线投射

除了这三个主要查询外，光线投射接口还可用于检索标记表面类型，自定义 watertight playspace 网格可以在房间扫描和终结后，内部为楼层、上限和墙等表面生成标签。 **PlayspaceRaycast** 函数采用射线，如果射线与已知表面碰撞，则返回有关该图面的信息（如果为 **RaycastResult）。** 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

在内部，光线广播是根据 playspace 的计算 8cm 立方体体xel 表示形式计算的。 每个体素都包含一组图面元素，其中包含已处理的拓扑 (也称为 surfaceels) 。 比较相交体xel 单元格中包含的图面，以及用于查找拓扑信息的最佳匹配项。 此拓扑数据包含以 **SurfaceTypes** 枚举形式返回的标签，以及相交表面表面。

在 Unity 示例中，光标将每帧投射一条射线。 首先，针对 Unity 的碰撞体;其次，针对了解模块的世界表示形式;最后，针对 UI 元素。 在此应用程序中，UI 获取优先级，然后获取理解结果，最后获取 Unity 的碰撞体。 **SurfaceType** 报告为光标旁边的文本。

![光线广播结果报告与楼层的交集。](images/raycast-result-500px.jpg)

光线广播结果报告与楼层的交集。


## <a name="get-the-code"></a>获取代码

开放源代码在 [MixedRealityToolkit 中提供](https://github.com/Microsoft/MixedRealityToolkit-Unity)。 如果在项目中使用[HoloLens，](https://forums.hololens.com/)请通过开发人员论坛告诉我们。 我们等不及看到你使用它做什么！

## <a name="about-the-author"></a>关于作者

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b>是一位软件工程主管，从HoloLens到体验开发，他一直致力于开发。 在HoloLens之前，他Kinect Xbox 应用和游戏行业工作过各种平台和游戏。 Jeff 对机器人、图形和具有闪烁的灯可发出声的一切充满爱。 他喜欢学习新知识并处理软件、硬件，尤其是在两者相交的空间。</td>
</tr>
</table>



## <a name="see-also"></a>另请参阅
* [空间映射](../design/spatial-mapping.md)
* [场景理解](../design/scene-understanding.md)
* [房间扫描可视化](../design/room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio：从开发一线HoloLens课程](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
