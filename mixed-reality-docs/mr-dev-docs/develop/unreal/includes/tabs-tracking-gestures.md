---
ms.openlocfilehash: 6b9223481ed909961dbb88d03e4b55ef68448525
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717737"
---
# <a name="426"></a>[<span data-ttu-id="08a93-101">4.26</span><span class="sxs-lookup"><span data-stu-id="08a93-101">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="08a93-102">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="08a93-102">Windows Mixed Reality</span></span>

![已连接到 "配置笔势" 功能的事件开始播放蓝图](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="08a93-104">然后，你应该添加代码以订阅以下事件：</span><span class="sxs-lookup"><span data-stu-id="08a93-104">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="08a93-105">![Windows 空间输入保留、点击和左操作笔势的蓝图 ](../images/unreal/key-events.png)
 ![ "详细信息" 面板中的 windows 空间输入点击手势选项的屏幕截图](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="08a93-105">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="08a93-106">OpenXR</span><span class="sxs-lookup"><span data-stu-id="08a93-106">OpenXR</span></span>

<span data-ttu-id="08a93-107">在 OpenXR 中，通过输入管道跟踪笔势事件。</span><span class="sxs-lookup"><span data-stu-id="08a93-107">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="08a93-108">使用手动交互，设备可以自动识别分流和保持手势，而不能识别其他手势。</span><span class="sxs-lookup"><span data-stu-id="08a93-108">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="08a93-109">它们被命名为 OpenXRMsftHandInteraction Select 并抓住映射。</span><span class="sxs-lookup"><span data-stu-id="08a93-109">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="08a93-110">不需要启用订阅，你应该在项目设置/引擎/输入中声明事件，就像下面这样：</span><span class="sxs-lookup"><span data-stu-id="08a93-110">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![OpenXR 操作映射的屏幕截图](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[<span data-ttu-id="08a93-112">4.25</span><span class="sxs-lookup"><span data-stu-id="08a93-112">4.25</span></span>](#tab/425)

<span data-ttu-id="08a93-113">您可以在 " **Windows Mixed Reality 空间输入**" 下查找蓝图函数，并通过 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 在调用代码文件中添加来查找 c + + 函数。</span><span class="sxs-lookup"><span data-stu-id="08a93-113">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![捕获手势](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="08a93-115">枚举</span><span class="sxs-lookup"><span data-stu-id="08a93-115">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="08a93-116">建立</span><span class="sxs-lookup"><span data-stu-id="08a93-116">Blueprint:</span></span>

![手势类型](../images/unreal/gesture-type.png)

<span data-ttu-id="08a93-118">C++：</span><span class="sxs-lookup"><span data-stu-id="08a93-118">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="08a93-119">函数</span><span class="sxs-lookup"><span data-stu-id="08a93-119">Function</span></span>
<span data-ttu-id="08a93-120">您可以使用函数启用和禁用手势捕获 `CaptureGestures` 。</span><span class="sxs-lookup"><span data-stu-id="08a93-120">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="08a93-121">当启用的笔势激发输入事件时， `true` 如果手势捕获成功，则函数返回 `false` ; 如果出现错误，则返回。</span><span class="sxs-lookup"><span data-stu-id="08a93-121">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="08a93-122">建立</span><span class="sxs-lookup"><span data-stu-id="08a93-122">Blueprint:</span></span>

![捕获手势最佳实践](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="08a93-124">C++：</span><span class="sxs-lookup"><span data-stu-id="08a93-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="08a93-125">下面是关键事件，可在蓝图和 c + +： ![ 键事件中找到](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="08a93-125">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

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

