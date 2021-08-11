---
title: DirectX 中的头部和眼部凝视
description: 了解如何在本机 DirectX 应用中使用打印头和眼睛跟踪来请求、使用和解包 raycasting 数据。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: 眼睛，眼睛，打印头，打印头跟踪，眼睛跟踪，directx，输入，全息影像，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 0e32c9f24b56d938b5c6f9cbdf28e9959b190abc22591a26d1dfcfa0af2f5f4d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193200"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>DirectX 中的头盔和眼睛眼睛输入

> [!NOTE]
> 本文与旧版 WinRT 本机 Api 相关。  对于新的本机应用项目，建议使用 **[OPENXR API](openxr-getting-started.md)**。

在 Windows Mixed Reality 中，眼睛和头盔输入用于确定用户正在查看的内容。 您可以使用这些数据来驱动主要的输入模型，如 [头看和提交](../../design/gaze-and-commit.md)，并为不同的交互类型提供上下文。 通过 API 可以使用两种类型的目视矢量：打印头-注视和眼睛。  两者都作为具有原点和方向的三维射线提供。 然后，应用程序可以 raycast 到其幕后或现实世界，确定用户的目标。

**打印头** 表示用户的头指向的方向。 将头看看作设备本身的位置和前进方向，并将其位置作为两个显示器之间的中心点。 打印头在所有混合现实设备上都可用。

**眼睛** 表示用户眼睛正在寻找的方向。 原点位于用户的眼睛之间。  它在包含目视跟踪系统的混合现实设备上可用。

打印头和眼睛都可通过  [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API 进行访问。 调用 [SpatialPointerPose：： TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 以在指定的时间戳和 [坐标系统](coordinate-systems-in-directx.md)接收新的 SpatialPointerPose 对象。 此 SpatialPointerPose 包含一个头部和方向。 它还包含目视的原点和方向（如果眼睛跟踪可用）。

### <a name="device-support"></a>设备支持

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>功能</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
</tr>
<tr>
     <td>头部凝视</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>眼睛-注视</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>使用打印头

若要访问 head，请首先调用  [SpatialPointerPose：： TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 以接收新的 SpatialPointerPose 对象。 传递以下参数。
 - 一个 [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) ，它表示要用于打印头的坐标系。 这由以下代码中的 *坐标系* 变量表示。 有关详细信息，请访问我们的 [坐标系统](coordinate-systems-in-directx.md) 开发人员指南。
 - 表示请求的头姿势的确切时间的 [时间戳](/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) 。  通常，您将使用与当前帧的显示时间对应的时间戳。 可以从  [HolographicFramePrediction](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 对象获取此预测的显示时间戳，该对象可通过当前 [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)访问。  此 HolographicFramePrediction 对象由下面代码中的 *预测* 变量表示。

 获得有效的 SpatialPointerPose 后，头位置和正向方向可作为属性进行访问。  下面的代码演示如何访问它们。

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>使用红眼

要使用户使用目视输入，每个用户首次使用设备时，必须通过 [目视跟踪用户校准](/hololens/hololens-calibration) 。 眼睛良好的 API 类似于打印头。
它使用相同的 [SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API，该 API 提供了一个射线原点和方向，你可以根据场景进行 raycast。  唯一的区别是，在使用之前，需要显式启用目视跟踪：
1. 请求用户在应用中使用目视跟踪的权限。
2. 启用包清单中的 "注视输入" 功能。

### <a name="requesting-access-to-eye-gaze-input"></a>正在请求访问目视输入

当你的应用程序启动时，调用 [EyesPose：： RequestAccessAsync](/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) 以请求访问目视跟踪。 系统将在需要时提示用户，并在授予访问权限后返回 [GazeInputAccessStatus：：允许](/uwp/api/windows.ui.input.gazeinputaccessstatus) 。 这是一个异步调用，因此需要进行一些额外的管理。 下面的示例旋转分离的 std：： thread 以等待结果，并将其存储到名为 *m_isEyeTrackingEnabled* 的成员变量。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
启动分离的线程只是一种用于处理异步调用的选项。 你还可以使用 c + +/WinRT. 支持的新 [co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) 功能
下面是要求用户提供权限的另一个示例：
-   EyesPose：： IsSupported () 允许应用程序仅在有目视跟踪器时才触发权限对话框。
-   GazeInputAccessStatus m_gazeInputAccessStatus;这是为了防止反复弹出权限提示。

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a>声明 *注视输入* 功能

双击 *解决方案资源管理器* 中的 appxmanifest.xml 文件。  然后导航到 " *功能* " 部分，并检查 " *注视输入* " 功能。 

![注视输入能力](images/gaze-input-capability.png)

这会将以下行添加到 appxmanifest.xml 文件的 *Package* 节：
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>获取眼睛眼睛

一旦您收到了 ET 的访问权限，就可以自由地抓住每个帧的眼睛。
与 head 一样，通过使用所需的时间戳和坐标系统调用[SpatialPointerPose：： TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)获取[SpatialPointerPose](/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 。 SpatialPointerPose 包含通过[眼睛](/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)属性的[EyesPose](/uwp/api/windows.perception.people.eyespose)对象。 只有启用了目视跟踪，此值才为非 null。 在该处，可以通过调用 [EyesPose：： IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)检查设备中的用户是否具有目视跟踪校准。  接下来，使用 " [注视](/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) " 属性获取包含眼睛位置和方向的 [SpatialRay](/uwp/api/windows.perception.spatial.spatialray) 。 "注视" 属性有时可以为 null，因此请务必检查此值。 如果校准的用户暂时关闭了眼睛，就会发生这种情况。

下面的代码演示如何访问眼睛眼睛。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a>当目视跟踪不可用时回退

如我们的 [目视跟踪设计文档](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available)中所述，设计人员和开发人员都应该知道目视跟踪数据可能不可用的情况。

数据不可用的原因有多种：
* 用户未校准
* 用户已拒绝应用访问其目视跟踪数据
* 临时 interferences，例如 HoloLens 面板上的污迹或用户眼睛 occluding 的头发。 

虽然本文档中已提到了某些 Api，但在下面的部分中，我们提供了有关如何检测目视跟踪是否可用作快速参考的摘要： 

* 检查系统是否完全支持目视跟踪。 调用以下 *方法*： [Windows。EyesPose. IsSupported ()](/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* 检查是否校准了用户。 调用以下 *属性*： [Windows。EyesPose. IsCalibrationValid](/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)   

* 检查用户是否已授予你的应用程序权限以使用其目视跟踪数据：检索当前的 _"GazeInputAccessStatus"_。 有关如何执行此操作的示例，请参阅 [请求访问注视输入](/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)。 

还可能想要检查眼睛跟踪数据是否过时，方法是在接收到的眼睛跟踪数据更新之间添加超时，否则回退到下面所述的打印头。   
有关详细信息，请访问我们的 [回退设计注意事项](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) 。

<br>

## <a name="correlating-gaze-with-other-inputs"></a>将注视与其他输入关联

有时，你可能会发现需要与过去的事件对应的 [SpatialPointerPose](/uwp/api/windows.ui.input.spatial.spatialpointerpose) 。 例如，如果用户进行一次点击，你的应用可能想要知道他们正在查看的内容。 出于此目的，只需将 [SpatialPointerPose：： TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 与预测帧时间结合使用，因为系统输入处理和显示时间之间存在延迟。 此外，如果使用目视看来确定目标，则在完成提交操作之前，我们的眼睛往往会继续。 这不是简单地点击的问题，而是将长的语音命令与快速的目视运动组合在一起，这一点更重要。 处理这种情况的一种方法是，使用对应于输入事件的历史时间戳对  [SpatialPointerPose：： TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)进行其他调用。  

但对于通过 SpatialInteractionManager 进行路由的输入，有一种更简单的方法。 [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)有其自己的[TryGetAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函数。 调用 将提供完全相关的 [SpatialPointerPose，](/uwp/api/windows.ui.input.spatial.spatialpointerpose) 而无需猜测。 有关使用 SpatialInteractionSourceStates 的信息，请参阅 DirectX 文档中的 [手部和](hands-and-motion-controllers-in-directx.md) 运动控制器。

<br>

## <a name="calibration"></a>校准

若要准确运行眼动跟踪，每个用户都需要进行眼动 [跟踪用户校准](/hololens/hololens-calibration)。 这样，设备可以调整系统，为用户提供更舒适、更高质量的观看体验，并确保同时进行准确的眼动跟踪。 开发人员无需在自己端执行任何操作来管理用户校准。 系统将确保在下列情况下提示用户校准设备：
* 用户首次使用设备
* 用户之前选择退出校准过程
* 用户上次使用设备时校准过程不成功

开发人员应确保为可能不可用眼动跟踪数据的用户提供足够的支持。 若要详细了解回退解决方案的注意事项，请通过"眼[动跟踪"了解HoloLens 2。](../../design/eye-tracking.md)

<br>

## <a name="see-also"></a>另请参阅

* [校准](/hololens/hololens-calibration)
* [DirectX 中的坐标系统](coordinate-systems-in-directx.md)
* [眼睛凝视HoloLens 2](../../design/eye-tracking.md)
* [凝视和提交输入模型](../../design/gaze-and-commit.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的语音输入](voice-input-in-directx.md)