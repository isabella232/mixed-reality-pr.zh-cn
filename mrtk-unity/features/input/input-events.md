---
title: 输入事件数
description: MRTK 中的大于文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，事件，
ms.openlocfilehash: 450c6dbbed8fc9bbb1a648b7a22f0de66747cbaf
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145223"
---
# <a name="input-events"></a>输入事件

下面的列表概述了要由自定义 MonoBehaviour 组件实现的所有可用输入事件接口。 这些接口将由 MRTK 输入系统调用，以根据用户输入交互处理自定义应用逻辑。 与以下标准输入事件类型相比，[指针输入事件](pointers.md#pointer-event-interfaces)的处理方式略有不同。

> [!IMPORTANT]
> 默认情况下，仅当脚本是焦点中某个 GameObject 的指针或父级的 GameObject 时，该脚本才会接收到输入事件。

| Handler | 事件 | 说明 |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | 检测到源/丢失源 | 在检测到/丢失输入源时引发，如检测到的已表述手势或丢失跟踪。 |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | 源姿势已更改 | 在源姿势发生更改时引发。 源姿势表示输入源的一般姿势。 可以通过获取在六个 DOF 控制器中的特定姿势，如手柄或指针 `IMixedRealityInputHandler<MixedRealityPose>` 。 |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | 输入关闭/向上 | 对二进制输入（如按钮）的更改引发。 |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 输入已更改 | 对给定类型的输入进行更改时引发。 **T** 可以采用以下值： <br/> - *float* (例如返回模拟触发器) <br/> - *Vector2.y* (例如，返回游戏杆操纵杆方向)  <br/> - *System.numerics.vector2* (例如，返回跟踪设备的位置)  <br/> - *四元* (，例如返回所跟踪设备) <br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (例如，返回完全跟踪的设备)  |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | 已识别语音关键字 | 在识别语音命令配置文件 中配置的关键字之 *一时引发*。 |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | 听写<br/> 假设 <br/> 结果 <br/> 完成 <br/> 错误 | 由听写系统引发，以报告听写会话的结果。 |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | 上的笔势事件： <br/> Started <br/> 已更新 <br/> 已完成 <br/> 已取消 | 在手势检测时引发。 |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 手势已更新/已完成 | 在检测包含给定类型的其他数据的笔势时引发。 有关 [**T 的可能**](gestures.md#gesture-events) 值的详细信息，请参阅笔势 **事件**。 |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | 已更新手部 | 在更新手部时由铰接式手部控制器引发。 |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | 手动网格已更新 | 由手部网格更新时由铰接式手部控制器引发。 |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | 操作已启动/已结束 | 引发 以指示映射到操作的输入的操作开始和结束。 |

## <a name="input-events-in-action"></a>操作中的输入事件

在脚本级别，可以通过实现上表中所示的事件处理程序接口之一来使用输入事件。 通过用户交互触发输入事件时，将发生以下情况：

1. MRTK 输入系统识别已发生输入事件。
1. MRTK 输入系统向所有[已注册的全局输入处理程序](#register-for-global-input-events)激发输入事件的相关接口函数
1. 对于注册到输入系统的每个活动指针：
    1. 输入系统确定当前指针的焦点是哪个 GameObject。
    1. 输入系统利用 [Unity 的事件系统](https://docs.unity3d.com/Manual/EventSystem.html) 为重点 GameObject 上的所有匹配组件激发相关的接口函数。
    1. 如果任何时候输入事件已 [标记为](#how-to-stop-input-events)"已使用"，该进程将结束，并且不会再进一步 gameobject 接收回调。
        - 示例：在 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 识别语音命令时，将搜索实现接口的组件。
        - 注意：如果在当前 GameObject 上找不到与所需接口匹配的组件，则 Unity 事件系统将向上冒泡以搜索父 GameObject。
1. 如果未注册任何全局输入处理程序，并且找不到具有匹配的组件/接口的 GameObject，则输入系统将调用每个回退注册的输入处理程序

> [!NOTE]
> 与上面列出的输入事件接口相比，[指针输入事件](pointers.md#pointer-event-interfaces)的处理方式略有不同。 特别是，指针输入事件仅由触发输入事件的指针以及任何全局输入处理程序的 GameObject 处理。 对于所有活动指针，常规输入事件由 Gameobject 处理。

### <a name="input-event-interface-example"></a>输入事件接口示例

下面的代码演示如何使用 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 接口。 如果用户在使用此类 GameObject 时显示 "更小" 或 "更大" 字样 `ShowHideSpeechHandler` ，则 GameObject 会将其自身缩放一半或两倍。

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 输入事件要求在 [MRTK 语音命令配置文件](speech.md)中预先注册所需的关键字。

## <a name="register-for-global-input-events"></a>注册全局输入事件

若要创建侦听全局输入事件的组件，而不考虑可能的 GameObject，组件必须向输入系统自行注册。 注册后，此 MonoBehaviour 的任何实例都将接收输入事件，以及当前 (焦点和其他全局注册侦听器) GameObject 事件。

如果输入事件已 [标记为已用](#how-to-stop-input-events)，则全局注册处理程序仍将接收回调。 但是，没有焦点 GameObjects 将接收事件。

### <a name="global-input-registration-example"></a>全局输入注册示例

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a>注册回退输入事件

回退输入处理程序类似于已注册的全局输入处理程序，但被视为处理输入事件的最后手段。 只有在未找到全局输入处理程序且没有 GameObject 焦点时，才使用回退输入处理程序。

### <a name="fallback-input-handler-example"></a>回退输入处理程序示例

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a>如何停止输入事件

每个输入事件接口都提供 [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) 一个数据对象作为接口上每个函数的参数。 此事件数据对象从 Unity 自己的 扩展 [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) 。

为了阻止输入事件按所述传播其执行，组件可以调用[](#input-events-in-action)以 [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) 将事件标记为已用。 这将阻止任何其他 GameObject 接收当前输入事件，全局输入处理程序除外。

> [!NOTE]
> 调用 方法的组件 `Use()` 将阻止其他 GameObject 接收它。 但是，当前 GameObject 上的其他组件仍将接收输入事件并调用任何相关的接口函数。

## <a name="see-also"></a>另请参阅

- [指针](pointers.md)
- [语音](speech.md)
- [输入状态](input-state.md)
