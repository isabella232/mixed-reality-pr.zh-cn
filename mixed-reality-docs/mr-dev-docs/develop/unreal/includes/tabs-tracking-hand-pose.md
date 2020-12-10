---
ms.openlocfilehash: 9fdcbdfe115fa859081c28b768f9c213ac241d13
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002648"
---
# <a name="425"></a>[4.25](#tab/425)

`EWMRHandKeypoint`枚举描述手形的骨骼层次结构。 可以在蓝图中找到每个 keypoint：

![手动 Keypoint 最佳实践](../images/hand-keypoint-bp.png)

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

您可以在 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 表中找到每个枚举用例的数值。

### <a name="supporting-hand-tracking"></a>支持手动跟踪

可以通过在 **Windows Mixed Reality > 手动** 跟踪中添加 **支持手动** 跟踪，在蓝图中使用手动跟踪：

![手动跟踪最佳实践](../images/unreal/hand-tracking-bp.png)

`true`如果设备上是否支持手动跟踪，则此函数返回， `false` 如果手动跟踪不可用，则返回。

![支持手动跟踪最佳实践](../images/unreal/supports-hand-tracking-bp.png)

C++：

添加 `WindowsMixedRealityHandTrackingFunctionLibrary.h`。

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>正在获取手动跟踪

您可以使用 **GetHandJointTransform** 从手返回空间数据。 数据将每帧更新一次，但如果在框架中，则会缓存返回值。 出于性能方面的考虑，不建议在此函数中使用繁重的逻辑。

![获取手动联合转换](../images/unreal/get-hand-joint-transform.png)

C++：
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

下面是 GetHandJointTransform 函数参数的细目：

* **手型** –用户可以是向左或向右。
* **Keypoint** –手型的骨骼。
* **转换** –骨骼基的坐标和方向。 你可以请求下一个骨骼的基，以获取骨骼末尾的转换数据。 特殊的 Tip 骨骼提供 distal 的结尾。
* * * 半径-骨骼基的半径。
* * * 返回值-如果该骨骼跟踪此帧，则为 true; 如果未跟踪该骨骼，则为 false。


# <a name="426"></a>[4.26](#tab/426)

该层次结构由 `EHandKeypoint` enum 描述：

![Keypoint 蓝图选项的图像](../images/hand-keypoint-bp.png)

您可以使用 **获取运动控制器数据** 函数从用户的手获取所有这些数据。 该函数返回 **XRMotionControllerData** 结构。 下面是一个示例蓝图脚本，它分析 XRMotionControllerData 结构以获取现有的接点位置，并在每个接合位置绘制一个调试坐标系。

![通过信道函数连接到行跟踪的 "获取注视" 数据函数蓝图](../images/unreal-hand-tracking-img-03.png)

务必要检查该结构是否有效以及它是否为手形。 否则，在访问位置、旋转和半径数组时，可能会获得未定义的行为。
