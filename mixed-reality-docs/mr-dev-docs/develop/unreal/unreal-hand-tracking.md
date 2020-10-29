---
title: Unreal 中的手部跟踪
description: 说明如何在 Unreal 中使用手动跟踪
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，手动跟踪，Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，混合现实，开发，功能，文档，指南，全息影像，游戏开发
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675877"
---
# <a name="hand-tracking-in-unreal"></a>Unreal 中的手部跟踪

## <a name="overview"></a>概述

手写跟踪系统使用用户的不要和手指作为输入。 您可以获取每个手指的位置和旋转、整个手掌甚至是在代码中使用的手势。 

## <a name="hand-pose"></a>举手

使用举手功能，你可以跟踪活动用户的手和手指，并将其用作输入，你可以通过蓝图和 c + + 进行访问。 可以在 Unreal 的 [HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API 中找到更多技术详细信息。 Unreal API 以坐标系统的形式发送数据，并使用 Unreal 引擎同步刻度。

### <a name="understanding-the-bone-hierarchy"></a>了解骨骼层次结构

`EWMRHandKeypoint`枚举描述手形的骨骼层次结构。 可以在蓝图中找到每个 keypoint：

![手动 Keypoint 最佳实践](images/hand-keypoint-bp.png)

完整的 c + + 枚举如下所示：
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

您可以在 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 表中找到每个枚举用例的数值。 下图显示了具有匹配枚举事例的整个手型布局：

![手写框架](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>支持手动跟踪

可以通过在 **Windows Mixed Reality > 手动** 跟踪中添加 **支持手动** 跟踪，在蓝图中使用手动跟踪：

![手动跟踪最佳实践](images/unreal/hand-tracking-bp.png)

`true`如果设备上是否支持手动跟踪，则此函数返回， `false` 如果未提供手动跟踪，则返回。

![支持手动跟踪最佳实践](images/unreal/supports-hand-tracking-bp.png)

C++： 

添加 `WindowsMixedRealityHandTrackingFunctionLibrary.h`。

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>正在获取手动跟踪
您可以使用 **GetHandJointTransform** 从手返回空间数据。 数据将每帧更新一次，但如果在框架中，则会缓存返回值。 出于性能方面的考虑，不建议在此函数中使用繁重的逻辑。 

![获取手动联合转换](images/unreal/get-hand-joint-transform.png)
 
C++：
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

函数参数细目：

* **手型** –是用户的左侧或右侧
* **Keypoint** –手型的骨骼。 
* **转换** –骨骼基的坐标和方向。 你可以请求下一个骨骼的基，以获取骨骼末尾的转换数据。 特殊的 Tip 骨骼提供 distal 的结尾。 
* **半径** -骨骼基的半径。
* **返回值** -如果在此帧中跟踪了骨骼，则为 true; 如果未跟踪骨骼，则为 false。

## <a name="hand-live-link-animation"></a>手动实时链接动画
使用 [实时链接插件](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)向动画显示手姿势。

如果启用了 Windows Mixed Reality 和 Live Link 插件： 
1. 选择 " **窗口 >" 实时链接** "，打开" 实时链接编辑器 "窗口。 
2. 单击 " **源** " 并启用 **Windows Mixed Reality 手动跟踪源**

![实时链接源](images/unreal/live-link-source.png)
 
启用源并打开动画资产后，展开 " **预览场景** " 选项卡中的 " **动画** " 部分会显示其他选项 (详细信息显示在 Unreal 的实时链接文档中-由于插件已在 beta 中，因此该过程稍后可能会更改) 。

![实时链接动画](images/unreal/live-link-animation.png)
 
手型动画层次结构与在中相同 `EWMRHandKeypoint` 。 动画可以使用 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 重定向：

![实时链接动画2](images/unreal/live-link-animation2.png)
 
还可以在编辑器中将它作为子类：

![实时链接重新映射](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>访问手写网格数据

![手写网格](images/unreal/hand-mesh.png)

在可以访问手写网格数据之前，你需要：
- 选择 **ARSessionConfig** 资产，展开 " **AR 设置->** " "世界" 映射设置，然后选中 " **根据跟踪的几何生成网格数据** "。 

下面是默认的网格参数：

1.  将网格数据用于封闭
2.  为网格数据生成冲突
3.  为网格数据生成导航网格
4.  以线框–用于显示生成的网格的 debug 参数呈现网格数据

这些参数值用作空间映射网格和手写网格默认值。 你可以在任何网格的蓝图或代码中随时对其进行更改。

### <a name="c-api-reference"></a>C + + API 参考 
用于 `EEARObjectClassification` 查找所有以可跟踪对象中的手写网格值。
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

当系统检测到任何以可跟踪对象（包括手写网格）时，将调用以下委托。 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

请确保委托处理程序遵循下面的函数签名：

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

可以通过以下操作访问网格数据  `UARTrackedGeometry::GetUnderlyingMesh` ：

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a>蓝图 API 参考

若要在蓝图中使用手写网格：
1. 将 **ARTrackableNotify** 组件添加到蓝图参与者

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
2. 请参阅 " **详细信息** " 面板，展开 " **事件** " 部分。 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
3. 添加/更新/删除跟踪的几何图形时覆盖事件图中的以下节点：

![在 ARTrackable 通知上](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>手写光线

您可以在 c + + 和蓝图中使用一种手写作为指针设备，这会公开 [SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API。

必须指出的是，由于所有函数的结果都更改每个帧，因此它们都是可调用的。 有关纯函数和非纯函数或可调用函数的详细信息，请参阅蓝图用户 guid on [函数](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

若要在蓝图中使用现货，请在 **Windows Mixed REALITY HMD** 下搜索任何操作：

![手动射线最佳实践](images/unreal/hand-rays-bp.png)
 
若要在 c + + 中访问它们，请将添加 `WindowsMixedRealityFunctionLibrary.h` 到调用代码文件的顶部。

### <a name="enum"></a>枚举
你还可以访问 **EHMDInputControllerButtons** 下的输入事例，它们可在蓝图中使用：

![输入控制器按钮](images/unreal/input-controller-buttons.png)

若要在 c + + 中访问，请使用 `EHMDInputControllerButtons` enum 类：
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

下面是两个适用的枚举事例的细目：
* **选择** -用户触发的 Select 事件。 
    * 通过使用 "选择" 并启用 [语音输入](unreal-voice-input.md) ，可以在 HoloLens 2 中触发事件。 
* **抓住** 用户触发的抓住事件。 
    * 可以通过将用户的手指置于全息图上，在 HoloLens 2 中触发此事件。 

可以通过下面所示的枚举来访问 c + + 中手写网格的跟踪状态 `EHMDTrackingStatus` ：

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

下面是两个适用的枚举事例的细目：
* **NotTracked** –手写不可见
* **跟踪** –完全跟踪

### <a name="struct"></a>结构
PointerPoseInfo 结构可为你带来以下手数据信息：
* **源** –现有的原点
* **方向** –手型方向
* **向上** –向上向量
* **方向** -方向四元数 
* **跟踪状态** -当前跟踪状态

可以通过蓝图访问此内容，如下所示：

![指针姿势信息最佳实践](images/unreal/pointer-pose-info-bp.png)

或带有 c + +：

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>函数

可以在每个帧上调用下面列出的所有函数，这允许持续监视。 

1. **获取指针姿势信息** 返回有关当前帧中的现货方向的完整信息。 

建立

![获取指针姿势信息](images/unreal/get-pointer-pose-info.png)

C++： 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. 如果指针在当前帧中 Grasped， **则为 Grasped** 返回 true。

建立

![是 Grasped 的最佳实践](images/unreal/is-grasped-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. 如果用户在当前帧中触发了 Select， **则选择 "按下" 将** 返回 true。

建立

![选择按下的 BP](images/unreal/is-select-pressed-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. 如果在当前帧中触发事件或按钮， **则单击 "是" 按钮** 返回 true。

建立

![按钮是否已单击 BP](images/unreal/is-button-clicked-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **获取控制器跟踪状态** 返回当前帧中的跟踪状态。

建立

![获取控制器跟踪状态 BP](images/unreal/get-controller-tracking-status-bp.png)

C++：
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>笔势

Hololens 2 可以跟踪空间手势，这意味着您可以将这些手势捕获为输入。 可以在 [HoloLens 2 基本使用](https://docs.microsoft.com/hololens/hololens2-basic-usage) 文档中找到有关手势的更多详细信息。

您可以在 " **Windows Mixed Reality 空间输入** " 下查找蓝图函数，并通过 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 在调用代码文件中添加来查找 c + + 函数。

![捕获手势](images/unreal/capture-gestures.png)

### <a name="enum"></a>枚举
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
建立 

![手势类型](images/unreal/gesture-type.png)

C++：
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>函数
您可以使用函数启用和禁用手势捕获 `CaptureGestures` 。 当启用的笔势激发输入事件时， `true` 如果手势捕获成功，则函数返回 `false` ; 如果出现错误，则返回。

建立

![捕获手势最佳实践](images/unreal/capture-gestures-bp.png)

C++：
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

下面是关键事件，可在蓝图和 c + +： ![ 键事件中找到](images/unreal/key-events.png)

![关键事件2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所 Unreal 的开发检查点旅程，就是在探索 MRTK 核心构建基块。 在这里，你可以继续执行下一个构建基块： 

> [!div class="nextstepaction"]
> [本地空间定位点](unreal-spatial-anchors.md)

或跳转到混合现实平台功能和 Api：

> [!div class="nextstepaction"]
> [HoloLens 摄像头](unreal-hololens-camera.md)

随时可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks) 。