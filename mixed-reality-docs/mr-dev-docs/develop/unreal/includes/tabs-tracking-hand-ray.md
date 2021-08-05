---
ms.openlocfilehash: fb8b5b509ef83e2a4f9d978dbf0faebbf3e0be1d10d6697f16cfb9366d7a2edb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187263"
---
# <a name="426"></a>[4.26](#tab/426)

若要获取手部射线的数据，应使用上一部分中的"获取运动控制器数据"函数。 返回的结构包含两个参数，可用于创建手部射线 – **目标位置** 和 **目标旋转**。 这些参数形成由你的定向的射线。 应接受它们，并找到所指向的全息影像。

下面是一个示例，用于确定手部射线是否命中小组件并设置自定义命中结果：

![获取运动控制器数据函数的蓝图](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[4.25](#tab/425)

若要在蓝图中使用手部射线，请搜索 **HMD** 下Windows Mixed Reality操作：

![手部射线 BP](../images/unreal/hand-rays-bp.png)

若要在 C++ 中访问它们， `WindowsMixedRealityFunctionLibrary.h` 请包含调用代码文件顶部的 。

### <a name="enum"></a>枚举

还可以访问 **EHMDInputControllerButtons** 下的输入事例，可在蓝图中使用：

![输入控制器按钮](../images/unreal/input-controller-buttons.png)

为了在 C++ 中访问，请使用 `EHMDInputControllerButtons` enum 类：
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

下面是两个适用枚举事例的细分：

* **选择** - 用户触发的 Select 事件。
    * 通过HoloLens 2、凝视和提交，或在启用语音输入时说"选择"[来](../unreal-voice-input.md)触发。
* **抓取** - 用户触发的"抓取"事件。
    * 在全息HoloLens 2上关闭用户手指，在图像中触发。

可以通过如下所示的枚举，在 C++ 中访问手部网格 `EHMDTrackingStatus` 的跟踪状态：

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

下面是两个适用枚举事例的细分：

* **NotTracked** - 手不可见
* **已** 跟踪 - 手完全被跟踪

### <a name="struct"></a>结构

PointerPoseInfo 结构可以提供有关以下手部数据的信息：

* **原** 点 – 手的原点
* **方向** – 手的方向
* **Up** – 手的向上矢量
* **方向** - 方向四元数
* **跟踪状态** - 当前跟踪状态

可以通过蓝图访问 PointerPoseInfo 结构，如下所示：

![指针姿势信息 BP](../images/unreal/pointer-pose-info-bp.png)

或者使用 C++：

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

可以在每个帧上调用下面列出的所有函数，从而允许持续监视。

1. **获取指针姿势信息** 返回有关当前帧中手部射线方向的完整信息。

蓝图：

![获取指针姿势信息](../images/unreal/get-pointer-pose-info.png)

C++：
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **如果手在当前** 帧中抓取，则"被抓取"返回 true。

蓝图：

![已掌握 BP](../images/unreal/is-grasped-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **如果用户在当前帧中** 触发了 Select，则 Select Pressed 返回 true。

蓝图：

![选择"按下的 BP"](../images/unreal/is-select-pressed-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. **如果事件或按钮** 在当前帧中触发，则单击的按钮将返回 true。

蓝图：

![按钮单击的 BP](../images/unreal/is-button-clicked-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **获取控制器跟踪状态** 返回当前帧中的跟踪状态。

蓝图：

![获取控制器跟踪状态 BP](../images/unreal/get-controller-tracking-status-bp.png)

C++：
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```