---
title: DirectX 中的手和运动控制器
description: 开始在本机 DirectX 应用中使用手动跟踪和运动控制器的开发人员指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: 双手，运动控制器，directx，输入，全息影像，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 13988df80052ef85662dcf9834406baa91d48f7c0b70242d1c904548c2707105
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210950"
---
# <a name="hands-and-motion-controllers-in-directx"></a>DirectX 中的手和运动控制器

> [!NOTE]
> 本文与旧版 WinRT 本机 Api 相关。  对于新的本机应用项目，建议使用 **[OPENXR API](openxr-getting-started.md)**。

在 Windows Mixed Reality 中，手动和[运动控制器](../../design/motion-controllers.md)输入都是通过空间输入 api （在 Windows 中找到）来处理的[。无.输入。](/uwp/api/windows.ui.input.spatial)空间命名空间。 这使您能够轻松地处理常见的操作，例如在双手和运动控制器中 **选择** "按相同方式"。

## <a name="getting-started"></a>入门

若要访问 Windows Mixed Reality 中的空间输入，请从 SpatialInteractionManager 接口开始。  可以通过调用  [SpatialInteractionManager：： GetForCurrentView](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)访问此接口，通常在应用启动期间进行。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager 的作业是提供对 [SpatialInteractionSources](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)（表示输入源）的访问权限。  系统中提供了三种 SpatialInteractionSources。
* **手型** 表示用户检测到的手。 现有的源根据设备提供不同的功能，范围从 HoloLens 的基本手势到 HoloLens 2 上完全表述的手动跟踪。 
* **控制器** 表示配对的运动控制器。 运动控制器可以提供不同的功能，例如，选择触发器、菜单按钮、"抓住按钮"、"触摸板" 和 "thumbsticks"。
* **语音** 表示用户在系统中检测到的语音关键字。 例如，每当用户显示 "选择" 时，此源都会注入一个选择按下和释放。

源的每帧数据由  [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 接口表示。 可以通过两种不同的方式来访问此数据，这取决于您是要在应用程序中使用基于事件驱动或基于轮询的模型。

### <a name="event-driven-input"></a>事件驱动的输入
SpatialInteractionManager 提供了多个应用可以侦听的事件。  一些示例包括   [SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、[SourceReleased 和 [SourceUpdated](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)。

例如，下面的代码将名为 MyApp：： OnSourcePressed 的事件处理程序挂接到 SourcePressed 事件。  这允许你的应用检测任何类型的交互源的按下操作。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

此按下的事件将在按下时与相应的 SpatialInteractionSourceState 一起异步发送到您的应用程序。 您的应用程序或游戏引擎可能想要立即开始处理，或在输入处理例程中排队事件数据。 下面是 SourcePressed 事件的事件处理程序函数，用于检查是否已按下 "选择" 按钮。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

上述代码仅检查 "Select" 按下，它对应于设备上的主要操作。 示例包括对 HoloLens 执行 AirTap 或在运动控制器上拉取触发器。  "选择" 按下表示用户激活其目标全息图的意图。  将为多个不同的按钮和手势触发 SourcePressed 事件，您可以检查 SpatialInteractionSource 上的其他属性，以测试这些情况。

### <a name="polling-based-input"></a>基于轮询的输入
还可以使用 SpatialInteractionManager 轮询每个帧的当前输入状态。  为此，请在每个帧上调用 [GetDetectedSourcesAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 。  此函数返回一个数组，其中包含每个活动[SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)的一个[SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 。 这意味着每个活动的运动控制器有一个，每次被跟踪，一个用于语音，另一个用于语音。 然后，你可以检查每个 SpatialInteractionSourceState 上的属性以将输入驱动到你的应用程序中。 

下面的示例演示如何使用轮询方法检查 "select" 操作。 *预测* 变量表示可从 [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)中获取的 [HolographicFramePrediction](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)对象。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

每个 SpatialInteractionSource 都有一个 ID，可用于标识新源并将现有源从帧关联到帧。  每次离开并进入 FOV 时，都可以获得新的 ID，但在会话期间，控制器 Id 会保持静态。  您可以使用 SpatialInteractionManager （如 [SourceDetected](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) 和 [SourceLost](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)）上的事件来做出手动输入或离开设备的视图，或者当动作控制器开启/关闭或配对/不成对时做出反应。

### <a name="predicted-vs-historical-poses"></a>预测与历史记录
GetDetectedSourcesAtTimestamp 具有 timestamp 参数。 这使您可以请求状态并引发预测或历史数据，从而使您可以将空间交互与其他输入源关联起来。 例如，在呈现当前帧中的位置时，可以传入由 [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)提供的预测时间戳。 这样一来，系统就可以向前预测该位置，使其与呈现的帧输出保持一致，从而最大程度地减少感觉滞后时间。

但是，这种预测的姿势并不会生成适合于交互源的最佳定点光线。 例如，按下运动控制器按钮时，该事件最多需要20毫秒才能向上蓝牙到操作系统。 同样，在用户执行手型手势后，在系统检测到该笔势之前一定会经历一定的时间，然后应用程序会轮询该手势。 当应用程序轮询状态更改时，使用的是过去发生的这种交互的头和手。 如果目标是将当前 HolographicFrame 的时间戳传递给 GetDetectedSourcesAtTimestamp，则会在显示帧时将姿势预测到目标射线，这可能会在将来的 20 ms 以上。 这种未来的理由适用于 *渲染* 交互源，但会因为用户在过去发生的目标问题而为 *交互提供了* 时间问题。

幸运的是， [SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、[SourceReleased 和 [SourceUpdated](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) 事件提供与每个输入事件关联的历史 [状态](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 。  这直接包括通过 [TryGetPointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)提供的历史头和手中的内容，以及可传递给其他 api 以与此事件关联的历史 [时间戳](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) 。

这会在每个帧呈现和定位时提供以下最佳做法：
* 对于呈现每个帧的 **手动/控制器** ，应用应按照当前帧的 photon 时间 **轮询** 每个交互源的 **前预测** 姿势。  可以通过调用每个帧的 [GetDetectedSourcesAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 来轮询所有交互源，并传入 [HolographicFrame：： CurrentPrediction](/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)提供的预测时间戳。
* 对于在按下或释放时的 **手动/控制器目标** ，你的应用程序应处理按下/已释放的 **事件**，raycasting **基于该事件的打印头或** 手。 可以通过以下方式获取此目标射线：处理 [SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) 或 [SourceReleased](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) 事件，从事件参数获取 [状态](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 属性，然后调用其 [TryGetPointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 方法。

## <a name="cross-device-input-properties"></a>跨设备输入属性
SpatialInteractionSource API 支持使用各种功能的控制器和手动跟踪系统。 许多这些功能在设备类型之间是通用的。 例如，手动跟踪和运动控制器都提供 "选择" 操作和三维位置。 只要有可能，API 就会将这些常见功能映射到 SpatialInteractionSource 上的相同属性。  这使应用程序能够更轻松地支持各种输入类型。 下表介绍了支持的属性，以及它们如何跨输入类型进行比较。

| 属性 | 说明 | HoloLens 第一代) 手势 ( | 运动控制器 | 明确表述|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource：：**左右手使用习惯**](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Right 或 left 右手/controller。 | 不支持 | 支持 | 支持 |
| [SpatialInteractionSourceState：：**IsSelectPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 主要按钮的当前状态。 | Air | 触发器 | 宽松 (直立的喷)  |
| [SpatialInteractionSourceState：：**IsGrasped**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | 抓取按钮的当前状态。 | 不受支持 | 抓取按钮 | 挤压或合上 |
| [SpatialInteractionSourceState：：**IsMenuPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | 菜单按钮的当前状态。    | 不受支持 | 菜单按钮 | 不受支持 |
| [SpatialInteractionSourceLocation：：**Position**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | 控制器上的抓手或抓握位置的 XYZ 位置。 | 掌上位置 | 抓握姿势位置 | 掌上位置 |
| [SpatialInteractionSourceLocation：：**取向**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | 四元数，表示控制器上手部或手柄姿势的方向。 | 不受支持 | 手柄姿势方向 | 手部方向 |
| [SpatialPointerInteractionSourcePose：：**位置**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | 指向射线的原点。 | 不支持 | 支持 | 支持 |
| [SpatialPointerInteractionSourcePose：：**ForwardDirection**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | 指向射线的方向。 | 不支持 | 支持 | 支持 |

上述某些属性并非在所有设备上都可用，API 提供了对此进行测试的方法。 例如，可以检查 [SpatialInteractionSource：：IsGraspSupported](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) 属性，以确定源是否提供抓取操作。

### <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指向姿势

Windows Mixed Reality支持不同外形系数的动作控制器。  它还支持明确的手部跟踪系统。  所有这些系统在手部位置与应用应该用于指向或呈现用户手部对象的自然"向前"方向之间具有不同的关系。  为了支持所有这些操作，为手部跟踪和运动控制器提供了两种类型的 3D 姿势。  第一种是手柄姿势，表示用户手部位置。  第二种是指向姿势，它表示源自用户手或控制器的指向射线。 因此，如果要呈现用户手或用户手中持有的对象（如手部或手部），请使用手柄姿势。 如果要从控制器或手进行光线转换，例如当用户指向 UI 时，请使用指向姿势。

可以通过[SpatialInteractionSourceState：:P roperties：：TryGetLocation (...) 访问手柄姿势](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_)。 定义如下：
* 手柄 **位置**：自然按住控制器时，通过向左或向右调整以将手柄中的位置居中时，手心中心。
* 手柄 **方向的** 右轴：完全打开手形成平面 5 指姿势时，与手部正常的射线从左 (向前，从右手心向后) 
* 手柄方向 **的** 向前轴：当你部分关闭手部 (就像按住控制器) 一样，指向"向前"的射线通过由非滚动手指组成的管道。
* 手柄 **方向的上轴**：右侧和向前定义隐含的向上轴。

可以通过[SpatialInteractionSourceState：:P roperties：：TryGetLocation (...) ：：SourcePointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或[SpatialInteractionSourceState：：TryGetPointerPose (...) ：：TryGetInteractionSourcePose](/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)访问指针姿势。 

## <a name="controller-specific-input-properties"></a>控制器特定的输入属性
对于控制器，SpatialInteractionSource 具有具有附加功能的 Controller 属性。
* **HasThumbstick：** 如果为 true，则控制器具有指纹。 检查 SpatialInteractionSourceState 的 [ControllerProperties](/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) 属性以获取 thumbstick x 和 y 值 (ThumbstickX 和 ThumbstickY) ，以及其按下状态 (IsThumbstickPressed) 。
* **HasTouchpad：** 如果为 true，则控制器具有触摸板。 检查 SpatialInteractionSourceState 的 ControllerProperties 属性以获取触摸板 x 和 y 值 (TouchpadX 和 TouchpadY) ，并知道用户是否触摸了触摸板 (IsTouchpadTouched) 以及是否按下触摸板 (IsTouchpadPressed) 。
* **SimpleHapticsController：** 通过控制器的 SimpleHapticsController API，可以检查控制器的视区功能，还可控制视区反馈。

对于从下到上以及从左到右方向 (轴，触摸板和 thumbstick 的范围为 -1 到 1) 。 使用 SpatialInteractionSourceState：：SelectPressedValue 属性访问的模拟触发器的范围为 0 到 1。 值为 1 与 IsSelectPressed 等于 true 相关联;任何其他值与 IsSelectPressed 等于 false 相关联。

## <a name="articulated-hand-tracking"></a>表达式手部跟踪
Windows Mixed Reality API 完全支持手部跟踪，例如，在HoloLens 2。 手部跟踪可用于在应用程序中实现直接操作和点和提交输入模型。 它还可用于创作完全自定义交互。

### <a name="hand-skeleton"></a>手部框架
表达式手部跟踪提供一个 25 个联合框架，可实现许多不同类型的交互。  该主干为索引/中/环/小手指提供五个连接点，为滚动块提供四个连接点，并提供一个手部连接。  下部作为层次结构的基础。 下图演示了框架的布局。

![手部框架](images/hand-skeleton.png)

在大多数情况下，每个联合都基于它表示的命名。  由于每个联合有两个块，因此我们使用一个约定，基于该位置的子类命名每个联合。  子类被定义为距离更远的。  例如，"Index Proximal"联合包含索引代理下部开始位置，以及该下部的方向。  它不包含的结束位置。  如果需要，你可以从层次结构中的下一个联合（即"索引中间"联合）获取它。

除了 25 个分层连接外，系统还提供一个手部连接。  通常不会将手心视为手部结构的一部分。 它仅作为获取手部整体位置和方向的简便方法提供。

下面提供了每个联合的以下信息：

| 名称 | 说明 |
|--- |--- |
|位置 | 联合的 3D 位置，可在任何请求的坐标系中提供。 |
|方向 | 任何请求的坐标系中提供的三维方向。 |
|半径 | 与连接位置上外观表面的距离。 用于优化依赖于手指宽度的直接交互或可视化效果。 |
|精确度 | 提供一个提示，说明系统对此联合信息具有怎样的自信。 |

可以通过 [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)上的函数访问手部主干数据。  该函数称为 [TryGetHandPose，](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)它返回名为 [HandPose 的对象](/uwp/api/windows.perception.people.handpose)。  如果源不支持铰接手，则此函数将返回 null。  拥有 HandPose 后，可以通过调用 [TryGetJoint](/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)获取当前联合数据，并指定你感兴趣的联合的名称。  数据作为 [JointPose 结构](/uwp/api/windows.perception.people.jointpose) 返回。  以下代码获取索引指提示的位置。 变量 *currentState* 表示 [SpatialInteractionSourceState 的实例](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>手部网格

通过表达式手部跟踪 API，可以完全实现三角形手部网格。  此网格可以与手部框架一起实时进行扭曲，并且可用于可视化和高级物理技术。  若要访问手部网格，首先需要在[SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource)上调用[TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)来创建[HandMeshObserver](/uwp/api/windows.perception.people.handmeshobserver)对象。  这只需要每个源完成一次，通常是首次看到它。  这意味着每当手进入 FOV 时，都会调用此函数来创建 HandMeshObserver 对象。  这是一个异步函数，因此必须在此处处理一些并发。  可用后，可以通过调用 [GetTriangleIndices](/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)向 HandMeshObserver 对象请求三角形索引缓冲区。  索引不会在帧上更改帧，因此可以获取一次，在源生存期内缓存它们。  索引按顺时针方向的逆时针顺序提供。

以下代码启动分离的 std：：thread 以创建网格观察程序，在网格观察程序可用后提取索引缓冲区。  它从名为 *currentState 的变量开始*，该变量是 [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 的实例，表示跟踪手。

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
启动分离线程只是处理异步调用的一个选项。  或者，可以使用 [C++/WinRT co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) 新功能。

拥有 HandMeshObserver 对象后，应在其相应 SpatialInteractionSource 处于活动状态的持续时间内保留该对象。  然后，可以通过调用 [GetVertexStateForPose](/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) 并传递表示要顶点的姿势 [的 HandPose](/uwp/api/windows.perception.people.handpose) 实例，来请求它提供表示手的最新顶点缓冲区。  缓冲区中的每个顶点都有一个位置和一个普通顶点。  以下示例演示了如何获取手部网格的当前顶点集。  与以前一样 *，currentState* 变量表示 [SpatialInteractionSourceState 的实例](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

与主干连接相比，手部网格 API 不允许为顶点指定坐标系。  相反 [，HandMeshVertexState](/uwp/api/windows.perception.people.handmeshvertexstate) 指定提供顶点的坐标系。  然后，可以通过调用 [TryGetTransformTo](/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) 并指定你需要的坐标系统，获取网格转换。  每当使用顶点时，都需要使用此网格转换。  此方法可减少 CPU 开销，尤其是在仅将网格用于呈现目的时。

## <a name="gaze-and-commit-composite-gestures"></a>凝视和提交复合手势
对于使用凝视和提交输入模型的应用程序，尤其是在 HoloLens (第一代) 上，空间输入 API 提供了可选的[SpatialGestureRecognizer，](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer)可用于启用基于"select"事件构建的复合手势。  通过将交互从 SpatialInteractionManager 路由到全息影像的 SpatialGestureRecognizer，应用可以跨手、语音和空间输入设备统一检测点击、按住、操作和导航事件，而无需手动处理按下和释放。

SpatialGestureRecognizer 仅对请求的一组手势进行最小区分。 例如，如果只请求 Tap，则只要用户愿意，用户就会按住手指，并且仍然会出现点击。 如果同时请求点击和按住，在按住手指大约一秒后，手势将提升为"按住"，并且不再发生点击。

若要使用 SpatialGestureRecognizer，请处理 SpatialInteractionManager 的 [InteractionDetected](/uwp/api/Windows.UI.Input.Spatial.SpatialInteractionManager) 事件，并抓取在那里公开的 SpatialPointerPose。 使用此姿势中的用户头部凝视射线与用户周围的全息影像和表面网格相交，以确定用户打算与哪些对象交互。 然后，使用其 CaptureInteraction 方法将事件参数中的 SpatialInteraction 路由到目标全息影像的 SpatialGestureRecognizer。 [](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) 这将开始根据创建时该识别器上设置的 [SpatialGestureSettings](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureSettings) 或 [TrySetGestureSettings 解释该交互](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer)。

在HoloLens (第一代) ，交互和手势应从用户的头部凝视派生其目标，而不是在手的位置呈现或交互。 启动交互后，手的相对运动可用于控制手势，就像操作或导航手势一样。

## <a name="see-also"></a>另请参阅
* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [直接操作输入模型](../../design/direct-manipulation.md)
* [点和提交输入模型](../../design/point-and-commit.md)
* [凝视和提交输入模型](../../design/gaze-and-commit.md)
* [运动控制器](../../design/motion-controllers.md)