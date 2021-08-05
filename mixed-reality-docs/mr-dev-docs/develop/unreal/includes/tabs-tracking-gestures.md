---
ms.openlocfilehash: fa21b1a5c3c89cf3c1c63c7ed8ebbdc3d8547661443853987ee3713e50c50e5c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187259"
---
# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![连接到配置笔势函数的事件开始播放的蓝图](../images/unreal-hand-tracking-img-09.png)

然后，应添加代码以订阅以下事件：

![空间Windows按住、点击和左操作手势的蓝图 详细信息面板Windows空间输入 ](../images/unreal/key-events.png)
 ![ 点击手势选项的屏幕截图](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

在 OpenXR 中，手势事件通过输入管道进行跟踪。 使用手势交互，设备可以自动识别点击和按住手势，但不能识别其他手势。 它们命名为 OpenXRMsftHandInteraction Select 和手柄映射。 无需启用订阅，应在 Project 设置/Engine/Input 中声明事件，如下所示：

![OpenXR 操作映射的屏幕截图](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[4.25](#tab/425)

可以通过在调用代码文件中添加 ，在 Windows Mixed Reality **输入** 和 C++ 函数下 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 找到 Blueprint 函数。

![捕获手势](../images/unreal/capture-gestures.png)

### <a name="enum"></a>枚举
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
蓝图：

![笔势类型](../images/unreal/gesture-type.png)

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
可以使用 函数启用和禁用笔势 `CaptureGestures` 捕获。 当启用的笔势触发输入事件时，如果笔势捕获成功，并且出现错误，则函数 `true` `false` 将返回 。

蓝图：

![捕获手势 BP](../images/unreal/capture-gestures-bp.png)

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

以下是可在蓝图和 C++ 中查找的关键事件： ![ 密钥事件](../images/unreal/key-events.png)

![关键事件 2](../images/unreal/key-events2.png)
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

