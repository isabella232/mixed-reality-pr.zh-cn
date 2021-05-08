---
title: 场景理解 SDK
description: 了解如何在混合现实应用中安装和使用场景理解 SDK （包括组件、网格和对象）。
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: 场景了解，空间映射，Windows Mixed Reality，Unity
ms.openlocfilehash: 2f6e0c9d0370caed2b2bc01399b9e4fc00836556
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644833"
---
# <a name="scene-understanding-sdk-overview"></a>场景理解 SDK 概述

场景理解转换混合现实设备捕获的非结构化环境传感器数据，并将其转换为强大的抽象表示形式。 SDK 充当应用程序和场景了解运行时之间的通信层。 它旨在模拟现有的标准构造，如3D 表示形式的三维场景图形，以及2D 应用程序的2D 矩形和面板。 尽管构造场景了解模拟会映射到具体框架，但通常情况下，SceneUnderstanding 是框架不可知的，这使得与它交互的可变框架之间具有互操作性。 随着场景理解演变，SDK 的作用是确保新的表示形式和功能继续在统一框架内公开。 在本文档中，我们将首先介绍高级概念，这些概念将帮助你熟悉开发环境/用法，并为特定的类和构造提供更详细的文档。

## <a name="where-do-i-get-the-sdk"></a>在何处获取 SDK？

SceneUnderstanding SDK 可通过 [混合现实功能工具](../unity/welcome-to-mr-feature-tool.md)下载。

**注意：** 最新版本依赖于预览包，你需要启用预发布包才能查看。

对于版本 0.5.2022-rc 和更高版本，场景理解支持适用于 c # 和 c + + 的语言投影，使应用程序可以为 Win32 或 UWP 平台开发应用程序。 在此版本中，SceneUnderstanding 支持 unity 的编辑器中的支持，该支持仅用于与 HoloLens2 通信。 

SceneUnderstanding 需要 Windows SDK 版本18362或更高版本。 

## <a name="conceptual-overview"></a>概念概述

### <a name="the-scene"></a>场景

混合现实设备会不断集成有关它在你的环境中看到的内容的信息。 场景了解漏斗图所有这些数据源，并生成一个统一的抽象抽象。 场景理解会生成场景，这些场景是 [SceneObjects](scene-understanding-SDK.md#sceneobjects) 的组成部分，表示单个事物的实例 (，如墙壁/天花板/楼层。 ) 场景对象本身是 [SceneComponents 的组合，表示构成此 SceneObject 的更精细的部分。 组件的示例包括四边形和网格，但将来可能表示边界框、冲突网格、元数据等。

将原始传感器数据转换为场景的过程是一项可能消耗大量资源的操作， (~ 10x10m) 到几分钟用于大空间 (~ 50x50m) ，因此没有应用程序请求的设备不会进行计算。 相反，应用程序会按需触发场景生成。 SceneObserver 类具有可计算或反序列化场景的静态方法，然后可以使用该场景进行枚举/交互。 "计算" 操作按需执行并在 CPU 上执行，但在单独的进程中 (混合现实驱动程序) 。 但是，虽然我们在另一个进程中进行计算，但生成的场景数据会存储在应用程序的场景对象中并进行维护。 

下面的关系图演示了此流程，并显示了两个应用程序与场景理解运行时交互的示例。 

![流程图](images/SU-ProcessFlow.png)

左侧是混合现实运行时的关系图，它在自己的进程中始终处于打开和运行状态。 此运行时负责执行设备跟踪、空间映射和其他操作，场景了解使用它来理解和解决世界的相关原因。 在关系图的右侧，我们将显示两个使用场景理解的理论应用程序。 第一个使用 MRTK 的应用程序接口，该应用程序在内部使用场景理解 SDK，第二个应用程序计算并使用两个单独的场景实例。 此关系图中的所有三个场景都生成不同场景的不同实例，驱动程序无法跟踪在一个场景中的应用程序和场景对象之间共享的全局状态。 场景理解确实提供了一种在一段时间内进行跟踪的机制，但这是使用 SDK 实现的。 跟踪代码已在应用程序的进程中的 SDK 中运行。

由于每个场景会将其数据存储在应用程序的内存空间中，因此，你可以假定场景对象的所有功能或它的内部数据始终在应用程序的进程中执行。

### <a name="layout"></a>Layout

若要使用场景理解，了解并了解运行时如何以逻辑方式和物理方式表示组件可能会很有价值。 场景表示具有特定布局的数据，其中选择了简单的布局，同时保持基础结构 pliable，而无需进行重大修改。 场景将通过以下方式实现此目标：将所有组件存储在简单列表中) 的所有场景对象 (构建基块，并通过引用（其中特定组件引用其他组件）定义层次结构和组合。

下面的示例展示了结构的平面和逻辑形式。

<table>
<tr><th>逻辑布局</th><th>物理布局</th></tr>
<tr>
<td>
<ul>
  场景
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

此图重点介绍场景的物理布局和逻辑布局之间的差异。 在左侧，我们将看到您的应用程序在枚举场景时看到的数据的分层布局。 在右侧，我们看到场景由12个不同的组件组成，如有必要，可单独访问。 处理新场景时，我们希望应用程序以逻辑方式对此层次结构进行遍历，但当在场景更新之间进行跟踪时，某些应用程序可能只对在两个场景之间共享的特定组件感兴趣。

## <a name="api-overview"></a>API 概述

以下部分提供对场景理解中的构造的高级概述。 阅读本部分后，你将了解如何表达场景以及各种组件的用途/用途。 下一节将提供具体的代码示例以及在本概述中 glossed 的其他详细信息。

下面所述的所有类型都驻留在 `Microsoft.MixedReality.SceneUnderstanding` 命名空间中。

### <a name="scenecomponents"></a>SceneComponents

现在，您已经了解了幕后的逻辑布局，接下来可以展示 SceneComponents 的概念，以及如何使用它们来组成层次结构。 SceneComponents 是 SceneUnderstanding 中最精细的分解，表示单个核心事物，例如，一个网格或四个边界框。 SceneComponents 是可以独立更新并可由其他 SceneComponents 引用的项，因此，它们具有一个唯一 ID 的单一全局属性，该属性允许此类跟踪/引用机制。 Id 用于场景层次结构的逻辑组合以及对象持久性 (相对于另一场景更新一个场景的操作。 )  

如果要将每个新计算的场景视为不同的场景，只需枚举其中的所有数据，Id 就会对您很有透明度。 但是，如果你打算跟踪多个更新上的组件，则将使用 Id 在场景对象之间建立索引和查找 SceneComponents。

### <a name="sceneobjects"></a>SceneObjects

SceneObject 是一个 SceneComponent，它表示 "事物" 的实例，例如墙壁、楼层、天花板等。用其 Kind 属性表示。 SceneObjects 是几何，因此具有在空间中表示其位置的函数和属性，但不包含任何几何或逻辑结构。 相反，SceneObjects 引用其他 SceneComponents，特别是 SceneQuads 和 SceneMeshes，它们提供系统支持的各种表示形式。 计算新场景时，应用程序很可能会枚举场景的 SceneObjects，以处理其感兴趣的内容。

SceneObjects 可以包含以下任一项：

<table>
<tr>
<th>SceneObjectKind</th> <th>说明</th>
</tr>
<tr><td>背景</td><td>已知 SceneObject <b>不</b> 是其他已识别的场景对象类型之一。 此类不应与 Unknown 混淆，其中背景已知不是墙壁/楼层/天花板，等等 .。。虽然未知还未分类。</b></td></tr>
<tr><td>壁</td><td>物理墙。 墙壁被认为是可移动的环境结构。</td></tr>
<tr><td>Floor</td><td>楼层是可以进行审核的任何表面。 注意：楼梯不是楼层。 另请注意，该楼层假设有任何不可表面，因此没有明确的假设。 多层结构，斜坡等 .。。应将所有分类为楼层。</td></tr>
<tr><td>Ceiling</td><td>房间的上部面。</td></tr>
<tr><td>平台</td><td>一个大平面，可以在其上放置全息影像。 它们倾向于表示表、countertops 和其他大型水平曲面。</td></tr>
<tr><td>World</td><td>标记不可知的几何数据的保留标签。 通过设置 EnableWorldMesh 更新标志生成的网格将归为 "世界"。</td></tr>
<tr><td>Unknown</td><td>尚未对此场景对象进行分类并为其分配一种类型。 这不应与背景混淆，因为此对象可能是任何内容，而系统刚刚没有提供足够强大的分类。</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

SceneMesh 是一种 SceneComponent，它使用三角形列表来模拟任意几何对象的几何。 SceneMeshes 用于多个不同的上下文中，它们可以表示 watertight 单元结构的组件或作为 WorldMesh，这表示与场景关联的未绑定空间映射网格。 每个网格提供的索引和顶点数据使用与用于在所有新式渲染 Api 中呈现三角形网格的 [顶点和索引缓冲区](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) 相同的熟悉布局。 在场景理解中，网格使用32位索引，可能需要分解为某些呈现引擎的块。

#### <a name="winding-order-and-coordinate-systems"></a>缠绕顺序和坐标系统

场景理解生成的所有网格都应该使用顺时针缠绕顺序返回 Right-Handed 坐标系中的网格。 

注意：版本之前的操作系统版本。191105可能会有一个已知 bug，其中 "World" 网格以 Counter-Clockwise 缠绕顺序返回，后者随后已修复。

### <a name="scenequad"></a>SceneQuad

SceneQuad 是一个 SceneComponent，它表示占据三维世界的2d 面。 SceneQuads 可以与 ARKit ARPlaneAnchor 或 ARCore 平面相似，但它们提供了更高级别的功能，如要由平面应用程序使用的2d 画布或更高的 UX。 为四边形提供了2D 特定的 Api，使放置和布局简单易用，并开发 (但使用四边形渲染) 应感觉比使用3d 网格更类似于2d 画布。

#### <a name="scenequad-shape"></a>SceneQuad 形状

SceneQuads 在2d 中定义边界矩形图面。 但是，SceneQuads 表示具有任意和可能复杂的形状的图面 (例如，环形形状的表。 ) 表示四个部分的复杂形状，可以使用 GetSurfaceMask API 将图面上的形状呈现到提供的图像缓冲区。 如果具有四部分的 SceneObject 还具有网格，则网格三角形应等效于此呈现的图像，它们都表示图面的实面（以2d 或3d 坐标表示）。

## <a name="scene-understanding-sdk-details-and-reference"></a>场景理解 SDK 详细信息和参考

以下部分将帮助你熟悉 SceneUnderstanding 的基础知识。 本部分应为你提供基础知识，此时你应该具有足够的上下文来浏览示例应用程序，以了解如何整体使用 SceneUnderstanding。

### <a name="initialization"></a>初始化

使用 SceneUnderstanding 的第一步是让应用程序获取对场景对象的引用。 可以通过以下两种方式之一完成此操作：可以通过驱动程序计算场景，也可以反序列化过去计算的现有场景。 后者可用于在开发期间使用 SceneUnderstanding，在这种情况下，应用程序和体验可以在没有混合现实设备的情况下快速建立原型。

使用 SceneObserver 计算场景。 在创建场景之前，应用程序应查询你的设备以确保它支持 SceneUnderstanding，并请求用户访问以获取 SceneUnderstanding 所需的信息。

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

如果未调用 RequestAccessAsync () ，则计算新场景将会失败。 接下来，我们将计算一个以混合现实耳机为根的新场景，其半径为10米。

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>从数据的初始化 (也称为。 PC 路径) 

尽管可以计算用于直接使用的场景，但也可以使用序列化形式计算，以便以后使用。 此功能经过证明可用于开发，因为它允许开发人员在无需设备的情况下使用和测试场景理解。 序列化场景的操作与计算场景几乎完全相同，数据将返回到应用程序，而不是由 SDK 在本地反序列化。 然后，你可以自行反序列化它或将其保存以供将来使用。

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a>SceneObject 枚举

现在，你的应用程序有场景，你的应用程序将查看和与 SceneObjects 交互。 这可以通过访问 **SceneObjects** 属性来完成：

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a>组件更新和 refinding 组件

还有另一个函数，可检索场景中名为 ***FindComponent*** 的组件。 当更新跟踪对象并在以后的场景中查找这些对象时，此函数很有用。 下面的代码将计算一个相对于以前场景的新场景，然后在新场景中查找楼层。

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>从场景对象访问网格和四边形

找到 SceneObjects 后，你的应用程序很可能需要访问由组成的四边形/网格中包含的数据。 可以通过 ***四边形** _ 和 _ *_网格_** 属性访问此数据。 下面的代码将枚举地面对象的所有四边形和网格。

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

请注意，它是相对于场景原点的转换的 SceneObject。 这是因为，SceneObject 表示 "事物" 的实例，在空间中可定位，四边形和网格表示相对于其父级转换的几何图形。 单独的 SceneObjects 可以引用相同的 SceneMesh/SceneQuad SceneComponents，也可能是 SceneObject 有多个 SceneMesh/SceneQuad。

### <a name="dealing-with-transforms"></a>处理转换

在处理转换时，场景理解已精心尝试与传统的三维场景表示。 因此，每个场景都局限于一个坐标系统，这与大多数常见的3D 环境表示形式非常类似。 每个 SceneObjects 都提供它们相对于该坐标系统的位置。 如果你的应用程序正在处理的场景会延伸到单个源所提供的限制，则可以将 SceneObjects 定位到 SpatialAnchors，或生成多个场景并将它们合并在一起，但为了简单起见，我们假定 watertight 场景位于其自身的源中，而该已由由场景 OriginSpatialGraphNodeId 定义的一个本地化。

例如，以下 Unity 代码演示了如何使用 Windows 感知和 Unity Api 来协调坐标系。 有关获取与 Unity 世界原点相对应的 SpatialCoordinateSystem 的详细信息，请参阅 [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 和 [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) ，了解有关 Windows 感知 api 的详细信息，以及 [Unity 中混合现实本机对象](/windows/mixed-reality/unity-xrdevice-advanced) 的详细信息。

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

每个 `SceneObject` 都有一个转换，然后将其应用到该对象。 在 Unity 中，我们转换为右手坐标坐标，并按如下所示分配本地转换：

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a>十字

四边形旨在帮助2D 布局方案，并应被视为2D 画布 UX 元素的扩展。 尽管四边形是 SceneObjects 的组件并且可以在3D 中呈现，但四个 Api 本身假设四边形是2D 结构。 它们提供了信息（如区、形状），并提供了用于放置的 Api。

四边形具有矩形区，但它们表示任意形状的2D 图面。 若要在与3D 环境四边形的图面上实现放置，使此交互成为可能。 当前场景理解提供了两个此类函数： **FindCentermostPlacement** 和 **GetSurfaceMask**。 FindCentermostPlacement 是一个高级别 API，它在四个位置上定位一个对象，并尝试查找您的对象的最佳位置，以确保您提供的边界框保持在底层的表面上。

> [!NOTE]
> 输出的坐标是相对于 "四个空间" 中的四个部分的，其中左上角是 (x = 0，y = 0) ，就像对其他 windows Rect 类型一样。 在使用自己的对象的源时，请务必考虑这一点。 

下面的示例演示如何查找 centermost 可放置位置并将全息图定位到四个部分。

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

步骤1-4 依赖于特定的框架/实现，但主题应类似。 请注意，四个部分只表示在空间中进行了本地化的界限2D 平面。 通过让引擎/框架知道四个部分，并相对于四个部分定位对象，您的全息影像会正确地定位到现实世界。 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>网格

网格表示对象或环境的几何表示形式。 与每个空间 surface 网格一起提供的 [空间映射](../../design/spatial-mapping.md)、网格索引和顶点数据非常类似于在所有新式渲染 api 中用于呈现三角形网格的顶点和索引缓冲区。 顶点位置在的坐标系统中提供 `Scene` 。 用于引用此数据的特定 Api 如下所示：

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

下面的代码提供了一个示例，说明如何从网格结构生成三角形列表：

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

索引/顶点缓冲区必须 >= 索引/顶点计数，但也可以任意调整大小以允许有效地重用内存。

### <a name="collidermesh"></a>ColliderMesh

场景对象通过 "网格" 和 "ColliderMeshes" 属性提供对网格和碰撞器网格数据的访问。 这些网格将始终匹配，这意味着网格属性的 i'th 索引与 ColliderMeshes 属性的 i'th 索引表示相同的几何。 如果运行时/对象支持碰撞器网格，则可保证获得最小多边形，最高序位，并在应用程序使用 colliders 的任何位置使用 ColliderMeshes。 如果系统不支持 colliders，则在 ColliderMeshes 中返回的网格对象将与网格减少内存约束的对象相同。

## <a name="developing-with-scene-understanding"></a>通过场景理解进行开发

此时，你应了解场景的核心构建基块了解运行时和 SDK。 大容量和复杂性在于访问模式、与3D 框架的交互，以及可以在这些 Api 基础上编写的工具来执行更高级的任务，例如空间规划、房间分析、导航、物理学等。 我们想要在示例中捕获这些示例，这些示例应指导您正确地指导您的场景。 如果有不能解决的示例或方案，请告知我们，我们将尝试记录/原型所需的内容。

### <a name="where-can-i-get-sample-code"></a>在哪里可以获取示例代码？

可在 [Unity 示例页](https://github.com/sceneunderstanding-microsoft/unitysample) 页面上了解 unity 的示例代码。 此应用程序将允许你与设备进行通信并呈现各种场景对象，或者，它允许你将序列化场景加载到电脑上，并允许你在不使用设备的情况下体验场景。

### <a name="where-can-i-get-sample-scenes"></a>在哪里可以获取示例场景？

如果你有 HoloLens2，则可以通过将 ComputeSerializedAsync 的输出保存到文件，并在方便时反序列化，来保存已捕获的任何场景。 

如果你没有 HoloLens2 设备，但想要在场景理解下播放，则需要下载预捕获的场景。 场景理解示例当前附带了序列化场景，可以在方便的时候下载和使用。 可在此处找到它们：

[场景了解示例场景](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>另请参阅

* [空间映射](../../design/spatial-mapping.md)
* [场景理解](../../design/scene-understanding.md)
* [Unity 示例](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)