---
title: 手部跟踪
description: 有关如何在 MRTK 中使用 HandTracking 的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，手动跟踪
ms.openlocfilehash: 6cd55bc76d9fba42640954bcbf50e62f66454a94
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143357"
---
# <a name="hand-tracking"></a>手部跟踪

## <a name="hand-tracking-profile"></a>手动跟踪配置文件

_手动跟踪配置文件_ 位于 _输入系统配置文件_ 下。 它包含用于自定义手动表示形式的设置。

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>联合 prototyping

联合 prototyping 使用简单的 prototyping 进行可视化。 _掌_ 形和 _食指_ 是特别重要的，拥有自己的 prefab，而所有其他接头共享同一 prefab。

默认情况下，手型 prototyping 是简单的几何基元。 如果需要，可以将其替换。 如果根本没有指定 prefab，则改为创建空 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 。

> [!WARNING]
> 避免在联合 prototyping 中使用复杂的脚本或消耗大量的资源，因为联合对象会在每个帧上转换，并且可能会产生极高的性能开销！

默认手动接点表示 |  接点标签
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>手动网格 prefab

如果手动跟踪设备提供了完全定义的网格数据，则使用手写网格。 Prefab 中的网格呈现被设备中的数据替换，因此虚拟网格（如多维数据集）就足够了。 Prefab 的材料用于手写网格。

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

手动网格显示可能会对性能产生显著影响，因此，可通过取消选中 " **启用手写显示可视化效果** " 选项来完全禁用它。

## <a name="hand-visualization-settings"></a>手动可视化设置

手动网格和手部联合可视化效果可以分别通过"手部网格可视化模式"设置和"手部联合可视化模式"来关闭 *或* 打开。 这些设置特定于应用程序模式，这意味着在编辑器 (中查看与编辑器内模拟的连接时，可以打开某些功能，例如) 同时在播放器内部版本) 中部署到设备 (时关闭相同的功能。

请注意，通常建议在编辑器 (中启用手部联合可视化效果，以便编辑器内模拟显示手部连接位置) ，在播放器 (中同时关闭手部联合可视化效果和手部网格可视化效果，因为它们会导致性能下降) 。

## <a name="scripting"></a>脚本编写

可以从输入系统请求每个手部作为 的位置和旋转 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 。

或者，系统允许访问跟随联合的[GameObject。](https://docs.unity3d.com/ScriptReference/GameObject.html) 如果另一个 GameObject 应持续跟踪联合，这非常有用。

枚举中列出了可用 [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) 联合。

> [!NOTE]
> 手部跟踪丢失时，会销毁联合对象！ 请确保使用联合对象的任何脚本都妥善处理 `null` 案例以避免错误！

### <a name="accessing-a-given-hand-controller"></a>访问给定的手部控制器

特定的手部控制器通常可用，例如处理输入事件时。 在这种情况下，可以使用 接口直接从设备请求联合 [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 数据。

#### <a name="polling-joint-pose-from-controller"></a>从控制器轮询联合姿势

如果 [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) 请求 `false` 的联合因某种原因不可用，则函数返回 。 在这种情况下，生成的姿势将为 [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) 。

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a>从手部可视化工具进行联合转换

可以从控制器可视化工具 请求 [联合对象](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)。

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a>简化的联合数据访问

如果未提供特定控制器，则提供实用工具类，方便访问手部联合数据。 这些函数从当前跟踪的第一个可用手部设备请求联合数据。

#### <a name="polling-joint-pose-from-handjointutils"></a>轮询来自 HandJointUtils 的接头姿势

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) 是一个静态类，用于查询第一个活动的设备。

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>从手联合服务的联合转换

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) 为跟踪接头保留一组持久的 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 。

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>手动跟踪事件

如果不需要直接从控制器轮询数据，则输入系统还会提供事件。

#### <a name="joint-events"></a>联合事件

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) 处理接点位置的更新。

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a>网格事件

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) 处理所表述的手写网格的更改。

请注意，默认情况下不启用手头网格。

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a>已知问题

### <a name="net-native"></a>.NET Native

使用 .NET 后端时，主版本目前有一个已知问题。 在 .NET Native 中， `IInspectable` 无法使用将指针从本机封送到托管代码 `Marshal.GetObjectForIUnknown` 。 MRTK 使用此来获取，以便 `SpatialCoordinateSystem` 从平台接收手写数据。

在 [本机混合现实工具包](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)存储库中，我们提供了 DLL 源作为此问题的解决方法。 请按照自述文件中的说明进行操作，并将生成的二进制文件复制到 Unity 资产的插件文件夹中。 之后，MRTK 中提供的 WindowsMixedRealityUtilities 脚本将解决此问题。

如果要创建自己的 DLL 或在现有 DLL 中包含此解决方法，解决方法的核心是：

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

在 c # Unity 代码中使用它：

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```
