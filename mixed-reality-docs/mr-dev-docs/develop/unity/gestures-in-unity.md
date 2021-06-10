---
title: Unity 中的笔势
description: 了解如何使用 XR 和常用按钮和轴 API 通过手势输入在 Unity 中对凝视采取措施。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 手势， unity， 凝视， 输入， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， MRTK， 混合现实工具包
ms.openlocfilehash: 87666c120686547b1a07f6da41519219d4a47720
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600636"
---
# <a name="gestures-in-unity"></a>Unity 中的笔势

在 Unity 中，有两种对凝视采取措施的关键[](../../design/gaze-and-commit.md#composite-gestures)方法[：HoloLens](gaze-in-unity.md)和沉浸式 HMD 中的手势和运动控制器。 [](../../design/motion-controllers.md) 可以通过 Unity 中的相同 API 访问两个空间输入源的数据。

Unity 提供两种主要方法来访问空间输入数据Windows Mixed Reality。 常见的 *Input.GetButton/Input.GetAxis* API 可跨多个 Unity XR SDK 工作，而特定于 Windows Mixed Reality 的 *InteractionManager/GestureRecognizer* API 则公开一组完整的空间输入数据。

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高级复合手势 API (GestureRecognizer) 

**命名空间***：UnityEngine.XR.WSA.Input*<br>
**类型**：GestureRecognizer、GestureSettings、InteractionSourceKind   

应用还可以识别空间输入源、点击、按住、操作和导航手势的更高级别复合手势。 可以使用 GestureRecognizer 在手[](../../design/gaze-and-commit.md#composite-gestures)部和运动[控制器](../../design/motion-controllers.md)上识别这些复合手势。

GestureRecognizer 上的每个笔势事件都提供输入的 SourceKind，以及事件发生时的目标头射线。 某些事件提供其他上下文特定信息。

使用手势识别器捕获手势只需几个步骤：
1. 创建新的手势识别器
2. 指定要监视的手势
3. 订阅这些手势的事件
4. 开始捕获手势

### <a name="create-a-new-gesture-recognizer"></a>创建新的手势识别器

若要使用 *GestureRecognizer，* 必须已创建 *GestureRecognizer*：

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>指定要监视的手势

通过 *SetRecognizableGestures* () ：

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>订阅这些手势的事件

订阅事件，了解你感兴趣的手势。

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>导航和操作手势在 *GestureRecognizer* 的实例上互斥。

### <a name="start-capturing-gestures"></a>开始捕获手势

默认情况下，在调用 *StartCapturingGestures* 之前 *，GestureRecognizer* () 监视输入。 如果在 *处理 StopCapturingGestures* 的帧之前执行了输入，则调用 *StopCapturingGestures ()* 后，可能会生成笔势 () 事件。 *GestureRecognizer* 将记住它在上一帧中是打开还是关闭，而该帧实际发生手势，因此，根据此帧的凝视目标启动和停止手势监视是可靠的。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>停止捕获手势

停止手势识别：

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>删除手势识别器

在销毁 GestureRecognizer 对象之前，请 *记得取消订阅已订阅* 的事件。

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>在 Unity 中呈现运动控制器模型

![运动控制器模型和远程传送](images/motioncontrollertest-teleport-1000px.png)<br>
*运动控制器模型和远程传送*

若要在应用中呈现与用户持有的物理控制器匹配的运动控制器，并按各种按钮时进行阐明，可以使用混合现实工具包 中的 **MotionController** [预制项](https://github.com/Microsoft/MixedRealityToolkit-Unity/)。  此预制件在运行时从系统安装的动态控制器驱动程序动态加载正确的 glTF 模型。  必须动态加载这些模型，而不是在编辑器中手动导入这些模型，这样应用就会为用户可能拥有的任何当前和未来控制器显示物理上准确的 3D 模型。

1. 按照 [入门](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 说明下载混合现实工具包，并将其添加到 Unity 项目。
2. 如果在安装步骤中将相机替换为 *MixedRealityCameraParent* 预制件入门，则你可以继续操作！  该预制包括运动控制器呈现。  否则，请从" *项目"窗格将 Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* 添加到场景中。  需要添加该预制组件作为任何父对象的子级，当用户在场景中进行远程传送时，你使用它来移动照相机，以便控制器与用户一起移动。  如果应用不涉及远程传送，只需在场景的根目录下添加预制。

## <a name="throwing-objects"></a>引发对象

在虚拟现实中引发对象比最初看起来更困难。 与大多数基于物理的交互一样，在游戏中以意外方式引发时，它将立即明显并中断沉浸式。 我们花费了一些时间来深入思考如何表示物理上正确的引发行为，并制定了一些指南，通过更新我们的平台来启用，我们希望与大家分享。

可在此处找到建议实现 引发 [的示例](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)。 此示例遵循以下四个准则：
* **使用控制器的速度 *，而不是* 位置**。 在 Windows 的 11 月更新中，我们引入了在处于"近似"位置跟踪状态 [时的行为更改](../../design/motion-controllers.md#controller-tracking-state)。 处于此状态时，只要我们认为控制器的准确度较高（通常比位置长）保持高精度，就会继续报告有关控制器的速度信息。
* **合并 *控制器 的* 角速度**。 此逻辑全部包含在静态 方法的 文件中， `throwing.cs` `GetThrownObjectVelAngVel` 位于上面链接的包中：
   1. 由于角速度被放大，所引发的对象必须保持与引发时相同的角速度： `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. 由于所引发对象的质量中心可能不在手柄姿势的原点，因此在用户参考框架中，其速度可能不同于控制器的速度。 通过此方式提供的对象速度部分是控制器原点周围所引发对象质量中心的即时正切速度。 此正切速度是控制器角度速度的交叉乘积，向量表示控制器原点与所引发对象的质量中心之间的距离。

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. 所引发对象的总速度是控制器的速度和此正切速度之和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **请密切注意 *应用* 速度 的时间**。 按下按钮时，该事件可能需要 20 毫秒才能通过蓝牙向上冒泡到操作系统。 这意味着，如果轮询控制器状态是否从按下状态更改为未按下状态，则控制器会提供你通过它获得的信息，实际上会提前进行此状态更改。 此外，轮询 API 呈现的控制器姿势会向前预测，以反映显示帧时可能超过 20 毫秒的姿势。 这适用于 *呈现* 持有的对象，但在我们计算用户释放引发的时间时，会进一步解决以对象为目标的时间问题。 幸运的是，在 11 月更新中，当发送 *InteractionSourcePressed* 或 *InteractionSourceReleased* 等 Unity 事件时，状态包括按下或释放按钮时从返回的历史姿势数据。  若要在引发期间获取最准确的控制器呈现和控制器目标，必须正确使用轮询和事件处理（如果适用）：
   * 对于 **呈现每个** 帧的控制器，应用应在当前帧的光子时间将控制器 *的 GameObject* 定位到向前预测的控制器姿势。  从 Unity 轮询 API（如 *[XR）获取此数据。InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。Wsa。Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。
   * 对于 **面向按下或** 释放的控制器，应用应基于该按下或释放事件的历史控制器姿势进行光线广播和计算轨迹。  从 Unity 事件 API（如 *[InteractionManager.InteractionSourcePressed）获取此数据](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。
* **使用手柄姿势**。 相对于手柄姿势（而不是指针姿势）报告角速度和速度。

引发将继续随将来的 Windows 更新而改进，你可以在此处找到有关它的信息。

## <a name="gesture-and-motion-controllers-in-mrtk"></a>MRTK 中的手势和运动控制器

可以从输入管理器访问手势和运动控制器。

* [MRTK 中的笔势](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [MRTK 中的运动控制器](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a>按照教程进行操作

混合现实学院中提供了分步教程和更详细的自定义示例：

- [MR 输入 211：手势](tutorials/holograms-211.md)
- [MR 输入 213：运动控制器](../../deprecated/mixed-reality-213.md)

[![MR 输入 213 - 运动控制器](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*MR 输入 213 - 运动控制器*

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发旅程，则你正在探索 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [手部和眼部跟踪](./hand-eye-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅

* [头部凝视并提交](../../design/gaze-and-commit.md)
* [运动控制器](../../design/motion-controllers.md)