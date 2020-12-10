---
ms.openlocfilehash: 50b56f6f081f682c3f3655e81aa492d84d254314
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002643"
---
# <a name="425"></a>[<span data-ttu-id="4d137-101">4.25</span><span class="sxs-lookup"><span data-stu-id="4d137-101">4.25</span></span>](#tab/425)

<span data-ttu-id="4d137-102">您可以在 " **Windows Mixed Reality 空间输入**" 下查找蓝图函数，并通过 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 在调用代码文件中添加来查找 c + + 函数。</span><span class="sxs-lookup"><span data-stu-id="4d137-102">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![捕获手势](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="4d137-104">枚举</span><span class="sxs-lookup"><span data-stu-id="4d137-104">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="4d137-105">建立</span><span class="sxs-lookup"><span data-stu-id="4d137-105">Blueprint:</span></span>

![手势类型](../images/unreal/gesture-type.png)

<span data-ttu-id="4d137-107">C++：</span><span class="sxs-lookup"><span data-stu-id="4d137-107">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="4d137-108">函数</span><span class="sxs-lookup"><span data-stu-id="4d137-108">Function</span></span>
<span data-ttu-id="4d137-109">您可以使用函数启用和禁用手势捕获 `CaptureGestures` 。</span><span class="sxs-lookup"><span data-stu-id="4d137-109">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="4d137-110">当启用的笔势激发输入事件时， `true` 如果手势捕获成功，则函数返回 `false` ; 如果出现错误，则返回。</span><span class="sxs-lookup"><span data-stu-id="4d137-110">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="4d137-111">建立</span><span class="sxs-lookup"><span data-stu-id="4d137-111">Blueprint:</span></span>

![捕获手势最佳实践](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="4d137-113">C++：</span><span class="sxs-lookup"><span data-stu-id="4d137-113">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="4d137-114">下面是关键事件，可在蓝图和 c + +： ![ 键事件中找到](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="4d137-114">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

![关键事件2](../images/unreal/key-events2.png)
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

# <a name="426"></a>[<span data-ttu-id="4d137-116">4.26</span><span class="sxs-lookup"><span data-stu-id="4d137-116">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="4d137-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4d137-117">Windows Mixed Reality</span></span>

![已连接到 "配置笔势" 功能的事件开始播放蓝图](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="4d137-119">然后，你应该添加代码以订阅以下事件：</span><span class="sxs-lookup"><span data-stu-id="4d137-119">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="4d137-120">![Windows 空间输入保留、点击和左操作笔势的蓝图 ](../images/unreal/key-events.png)
 ![ "详细信息" 面板中的 windows 空间输入点击手势选项的屏幕截图](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="4d137-120">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="4d137-121">OpenXR</span><span class="sxs-lookup"><span data-stu-id="4d137-121">OpenXR</span></span>

<span data-ttu-id="4d137-122">在 OpenXR 中，通过输入管道跟踪笔势事件。</span><span class="sxs-lookup"><span data-stu-id="4d137-122">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="4d137-123">使用手动交互，设备可以自动识别分流和保持手势，而不能识别其他手势。</span><span class="sxs-lookup"><span data-stu-id="4d137-123">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="4d137-124">它们被命名为 OpenXRMsftHandInteraction Select 并抓住映射。</span><span class="sxs-lookup"><span data-stu-id="4d137-124">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="4d137-125">不需要启用订阅，你应该在项目设置/引擎/输入中声明事件，就像下面这样：</span><span class="sxs-lookup"><span data-stu-id="4d137-125">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![OpenXR 操作映射的屏幕截图](../images/unreal-hand-tracking-img-12.png)
