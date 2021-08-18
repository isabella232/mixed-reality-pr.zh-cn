---
ms.openlocfilehash: 271116683c94e051f61b78c0db3974ee843afdbd
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905706"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="spatial-awareness-system"></a>空间感知系统

在 MRTK 中，查看 [空间感知入门](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 指南，了解有关设置各种空间网格观察器的信息。

有关设备观察程序的信息，请参阅 [配置适用于设备的网格观察](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/configuring-spatial-awareness-mesh-observer) 器指南。

有关场景理解观察程序的信息，请查看 [场景了解观察](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) 程序指南。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="armeshmanager"></a>ARMeshManager

Unity 的 ARFoundation 为空间网格的内置可视化提供了 ARMeshManager 组件。 有关使用情况的详细信息，请参阅 [Unity 的文档](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/mesh-manager.html) 。

## <a name="xrmeshsubsystem"></a>XRMeshSubsystem

如果你想要直接使用 Unity 的 [XRMeshSubsystem](https://docs.unity3d.com/ScriptReference/XR.XRMeshSubsystem.html) ，请参阅 [Unity 的文档](https://docs.unity3d.com/Manual/xrsdk-meshing.html) ，以了解有关使用情况的详细信息。

## <a name="windows-xr-plugin"></a>WindowsXR 插件

WindowsXR 插件提供了一些额外的扩展方法用于配置 XRMeshSubsystem，例如设置边界球体或访问基础平台网格表示形式。 所有其他扩展都可以 [在 Unity 的文档中](https://docs.unity3d.com/Packages/com.unity.xr.windowsmr@5.3/api/UnityEngine.XR.WindowsMR.WindowsMRExtensions.html)找到。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Unity 内置空间映射组件入门

Unity 提供了两个组件，可以轻松地将空间映射添加到应用、 **空间映射呈现** 器和 **空间映射碰撞** 器。

### <a name="spatial-mapping-renderer"></a>空间映射呈现器

空间映射呈现器允许对空间映射网格进行可视化。

![Unity 中的空间映射呈现器](../images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>空间映射碰撞器

空间映射碰撞器允许在空间映射网格中 (或字符) 交互（如物理学）的全息内容。

![Unity 中的空间映射碰撞器](../images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>使用内置的空间映射组件

如果要可视化和与物理表面交互，则可以将这两个组件添加到应用中。

在 Unity 应用中使用这两个组件：

1. 在要检测空间图面网格的区域的中心选择一个 GameObject。
2. 在检查器窗口中，**添加组件**  >  **XR**  >  **空间映射碰撞** 器   或 **空间映射呈现** 器。

有关如何在 <a href="https://docs.unity3d.com/2018.4/Documentation/Manual/SpatialMappingComponents.html" target="_blank">Unity 文档网站</a>上使用这些组件的详细信息，请参阅。

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>超越内置的空间映射组件

利用这些组件，您可以轻松地开始进行空间映射。 若要进一步了解，需要了解两个主要的路径：

* 若要执行自己的低级网格处理，请参阅下面有关低级别空间映射脚本 API 的部分。
* 若要执行更高级别的网格分析，请参阅以下部分，了解 [MixedRealityToolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/SpatialUnderstanding)中的 SpatialUnderstanding 库。

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>使用低级别 Unity 空间映射 API

如果需要更多的控制，而不是空间映射呈现器和空间映射碰撞器组件产品/服务，请使用低级别空间映射 Api。

**命名空间：** *UnityEngine. XR*<br>
**类型**： *SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*

我们概括了使用以下部分中的空间映射 Api 的应用程序的建议流。

### <a name="set-up-the-surfaceobservers"></a>设置 SurfaceObserver (s) 

为需要空间映射数据的每个应用程序定义的空间区域实例化一个 SurfaceObserver 对象。

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

通过调用 SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox 或 SetVolumeAsFrustum，指定每个 SurfaceObserver 对象为其提供数据的空间区域。 您可以重新定义将来的空间区域，方法是再次调用其中一种方法。

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

调用 SurfaceObserver () 时，必须为空间映射系统包含其新信息的 SurfaceObserver 区域中的每个空间图面提供一个处理程序。 对于一个空间图面，处理程序接收：

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>处理表面更改

有几个用来处理的主要用例：添加和更新，可以使用相同的代码路径，并将其删除。

* 在添加和更新的情况下，我们将从字典中添加或获取表示此网格的 GameObject。 我们将使用必要的组件创建 SurfaceData 结构，然后调用 RequestMeshDataAsync 来使用网格数据填充 GameObject，然后将其放置在场景中。
* 在已删除的示例中，我们从字典中删除表示此网格的 GameObject 并销毁它。

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a>处理数据准备就绪

OnDataReady 处理程序接收 SurfaceData 对象。 "WorldAnchor"、"MeshFilter" 和 " (" （可选）) 其包含的 MeshCollider 对象反映关联空间图面的最新状态。 （可选）通过访问 MeshFilter 对象的网格成员来分析和/或 [处理](../../../design/spatial-mapping.md#mesh-processing) 网格数据。 使用最新网格呈现空间图面，并 (（可选）) 将其用于物理学冲突和 raycasts。 务必确认 SurfaceData 的内容不为空。

### <a name="start-processing-on-updates"></a>开始处理更新

SurfaceObserver 应延迟，而不是每个帧调用更新 () 。

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while (true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```
