---
title: 手部跟踪
description: 有关如何在 MRTK 中使用 HandTracking 的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 手部跟踪，
ms.openlocfilehash: f9d3b6b0f83a513b849aa27d464595ec8543bc30b64314c9a6e341cd6cb3a519
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189481"
---
# <a name="hand-tracking"></a>手部跟踪

## <a name="hand-tracking-profile"></a>手部跟踪配置文件

手 _部跟踪配置文件_ 位于输入系统 _配置文件 下_。 它包含用于自定义手部表示形式的设置。

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>联合预制

使用简单的预制项可视化联合预制。 _"手_ 心"和"_索引_ 手指"的连接点非常重要，并且具有自己的预制项，而其他所有连接都具有相同的预制。

默认情况下，手部联合预制是简单的几何基元。 如果需要，可以替换它们。 如果完全未指定预制，则改为创建空[GameObject。](https://docs.unity3d.com/ScriptReference/GameObject.html)

> [!WARNING]
> 避免在联合预制件中使用复杂的脚本或成本高昂的渲染，因为联合对象会基于每个帧进行转换，并且可能会显著降低性能成本！

默认手部联合表示形式 |  联合标签
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>手部网格预制

如果手部跟踪设备提供了完全定义的网格数据，则使用手部网格。 预制件中可呈现的网格被设备的数据替换，因此，一个虚拟网格（如多维数据集）已足够。 预制材料用于手部网格。

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

手部网格显示可能会显著影响性能，因此，可以通过取消选中"启用手部网格可视化"选项完全 **禁用** 它。

## <a name="hand-visualization-settings"></a>手部可视化设置

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

#### <a name="polling-joint-pose-from-handjointutils"></a>从 HandJointUtils 轮询联合姿势

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) 是查询第一个活动手部设备的静态类。

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>从手部联合服务进行联合转换

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService)保留一组用于跟踪联合的[永久 GameObject。](https://docs.unity3d.com/ScriptReference/GameObject.html)

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>手部跟踪事件

如果不需要直接从控制器轮询数据，则输入系统也提供事件。

#### <a name="joint-events"></a>联合活动

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) 处理联合位置的更新。

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

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) 处理已表达手部网格的更改。

请注意，手动网格默认未启用。

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

目前，使用 .NET 后端的主版本存在一个已知问题。 在 .NET Native 中，不能使用 将指针从本机 `IInspectable` 封送到托管代码 `Marshal.GetObjectForIUnknown` 。 MRTK 使用此来获取 `SpatialCoordinateSystem` ，以便从平台接收手部和眼睛数据。

我们已在本机混合现实存储库 中提供了 DLL 源作为[此问题的Toolkit解决方法](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)。 请按照自述文件中的说明进行操作，将生成的二进制文件复制到 Unity 资产的 Plugins 文件夹中。 之后，MRTK 中提供的 WindowsMixedRealityUtilities 脚本将解决你的解决方法。

如果要创建自己的 DLL 或将此解决方法纳入现有 DLL，解决方法的核心是：

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

及其在 C# Unity 代码中的使用：

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
