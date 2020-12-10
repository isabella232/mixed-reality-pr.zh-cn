---
ms.openlocfilehash: 23bba22801f61f6b4814991c8b3bde68d2c5f6b7
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002653"
---
# <a name="425"></a>[4.25](#tab/425)

若要在蓝图中使用现货，请在 **Windows Mixed REALITY HMD** 下搜索任何操作：

![手动射线最佳实践](../images/unreal/hand-rays-bp.png)

若要在 c + + 中访问它们，请将添加 `WindowsMixedRealityFunctionLibrary.h` 到调用代码文件的顶部。

### <a name="enum"></a>枚举

你还可以访问 **EHMDInputControllerButtons** 下的输入事例，它们可在蓝图中使用：

![输入控制器按钮](../images/unreal/input-controller-buttons.png)

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
    * 通过使用 "选择" （启用 [语音输入](../unreal-voice-input.md) ）在 HoloLens 2 中触发。
* **抓住** 用户触发的抓住事件。
    * 在 HoloLens 2 中通过将用户的手指关闭到全息图上触发。

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

可以通过蓝图访问 PointerPoseInfo 结构，如下所示：

![指针姿势信息最佳实践](../images/unreal/pointer-pose-info-bp.png)

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

![获取指针姿势信息](../images/unreal/get-pointer-pose-info.png)

C++：
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. 如果指针在当前帧中 Grasped，**则为 Grasped** 返回 true。

建立

![是 Grasped 的最佳实践](../images/unreal/is-grasped-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. 如果用户在当前帧中触发了 Select，**则选择 "按下" 将** 返回 true。

建立

![选择按下的 BP](../images/unreal/is-select-pressed-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. 如果在当前帧中触发事件或按钮，**则单击 "是" 按钮** 返回 true。

建立

![按钮是否已单击 BP](../images/unreal/is-button-clicked-bp.png)

C++：
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **获取控制器跟踪状态** 返回当前帧中的跟踪状态。

建立

![获取控制器跟踪状态 BP](../images/unreal/get-controller-tracking-status-bp.png)

C++：
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
# <a name="426"></a>[4.26](#tab/426)

若要获取手写片的数据，应使用上一节中的 Get 运动控制器数据函数。 返回的结构包含两个参数，您可以使用这些参数创建一个手型， **瞄准位置** 和 **aim 旋转**。 这些参数构成弯头线。 您应该获取它们并查找指向的全息影像。

下面是一个示例，该示例确定手 ray 是否击中小组件并设置自定义命中结果：

![获取运动控制器数据函数的蓝图](../images/unreal-hand-tracking-img-04.png) 