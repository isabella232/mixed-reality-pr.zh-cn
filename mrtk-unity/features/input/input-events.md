---
title: 输入事件
description: MRTK 中的大于文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，事件，
ms.openlocfilehash: 25ac5bd4a4f5d5678a80ec362512ce7daac791a17e93944aa4832d9d09c02ee2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208329"
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
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 输入已更改 | 对给定类型的输入进行更改时引发。 **T** 可以采用以下值： <br/> - *float* (例如返回模拟触发器) <br/> - *Vector2.y* (例如，返回游戏杆操纵杆方向)  <br/> - *System.numerics.vector2* (例如，返回跟踪设备的位置)  <br/> - *四元数* (例如返回所跟踪设备的方向) <br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (例如，返回完全跟踪的设备)  |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | Speech 关键字已识别 | 在识别 *语音命令配置文件* 中配置的其中一个关键字时引发。 |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | 听写<br/> 假设 <br/> 结果 <br/> 完成 <br/> 错误 | 由听写系统引发，用于报告听写会话的结果。 |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | 笔势事件： <br/> Started <br/> 已更新 <br/> 已完成 <br/> 已取消 | 手势检测时引发。 |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 已更新/已完成笔势 | 检测包含给定类型的其他数据的笔势时引发。 有关 **T** 的可能值的详细信息，请参阅 [**笔势事件**](gestures.md#gesture-events)。 |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | 手动更新的接头 | 在更新手动接头时由明确表述的手势控制器引发。 |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | 已更新手动网格 | 当手写网格更新时由明确表述的手势控制器引发。 |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | 操作开始/结束 | 引发以指示映射到操作的输入的操作开始和结束。 |

## <a name="input-events-in-action"></a>操作中的输入事件

在脚本级别，可以通过实现上表中所示的某个事件处理程序接口来使用输入事件。 当通过用户交互引发输入事件时，会发生以下情况：

1. MRTK 输入系统可识别输入事件已发生。
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

若要创建侦听全局输入事件的组件，而不考虑可能的 GameObject，组件必须向输入系统自行注册。 注册之后，此 MonoBehaviour 的任何实例都将接收输入事件，以及任何 GameObject () 当前焦点和其他全局注册侦听器。

如果输入事件 [标记为](#how-to-stop-input-events)"已使用"，则全局注册的处理程序仍将接收回拨。 但是，没有任何焦点 Gameobject 会接收到该事件。

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

回退输入处理程序与注册的全局输入处理程序类似，但被视为最后一种用于输入事件处理的手段。 仅当找不到全局输入处理程序且焦点不 Gameobject 时，才会利用回退输入处理程序。

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

每个输入事件接口提供一个 [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) 数据对象作为接口上每个函数的参数。 此事件数据对象从 Unity 自己的扩展 [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) 。

若要阻止输入事件通过其执行（ [如所述](#input-events-in-action)）进行传播，组件可以调用 [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) 来将事件标记为 "已使用"。 这会阻止任何其他 Gameobject 接收当前输入事件，全局输入处理程序除外。

> [!NOTE]
> 调用方法的组件 `Use()` 会阻止其他 gameobject 接收它。 但是，当前 GameObject 上的其他组件仍将接收输入事件，并激发任何相关的接口函数。

## <a name="see-also"></a>另请参阅

- [指针](pointers.md)
- [语音](speech.md)
- [输入状态](input-state.md)
