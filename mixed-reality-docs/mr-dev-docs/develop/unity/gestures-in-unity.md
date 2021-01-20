---
title: Unity 中的手势
description: 了解如何使用 XR 和通用按钮和轴 Api 在 Unity 中使用手动手势输入来执行操作。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 手势，unity，注视，输入，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: 44c42abdd4628cacd6af334a916fb725da8bb022
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583893"
---
# <a name="gestures-in-unity"></a>Unity 中的手势

您可以通过两种主要方式在您的 [HMD 中进行](gaze-in-unity.md)操作，在 HoloLens 和沉浸式的中的 [手势](../../design/gaze-and-commit.md#composite-gestures) 和 [运动控制器](../../design/motion-controllers.md) 。 可以通过 Unity 中的相同 Api 访问空间输入的两个源的数据。

Unity 提供了两种主要方法来访问 Windows Mixed Reality 的空间输入数据。 常见的 *GetButton/GetAxis* api 跨多个 Unity XR sdk 工作，而特定于 Windows Mixed Reality 的 *InteractionManager/GestureRecognizer* api 会公开一组完整的空间输入数据。

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高级别复合手势 Api (GestureRecognizer) 

**命名空间：** *UnityEngine. XR*<br>
**类型**： *GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*

您的应用程序还可以识别空间输入源、点击、保持、操作和导航笔势的更高级复合手势。 您可以使用 GestureRecognizer 在 [手](../../design/gaze-and-commit.md#composite-gestures) 和 [运动控制器](../../design/motion-controllers.md) 中识别这些组合手势。

GestureRecognizer 上的每个手势事件都提供输入的 SourceKind，以及事件发生时的目标 head 射线。 某些事件提供其他特定于上下文的信息。

使用手势识别器捕获手势只需几个步骤：
1. 创建新的手势识别器
2. 指定要监视的手势
3. 订阅这些手势的事件
4. 开始捕获手势

### <a name="create-a-new-gesture-recognizer"></a>创建新的手势识别器

若要使用 *GestureRecognizer*，必须创建 *GestureRecognizer*：

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>指定要监视的手势

通过 SetRecognizableGestures 指定你对其感兴趣的手势 *( # B1*：

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>订阅这些手势的事件

订阅你感兴趣的手势的事件。

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
>导航和操作手势在 *GestureRecognizer* 的实例上互相排斥。

### <a name="start-capturing-gestures"></a>开始捕获手势

默认情况下，在调用 *StartCapturingGestures ( # B1* 之前， *GestureRecognizer* 不监视输入。 如果在处理 *StopCapturingGestures ( # B3* 的帧之前执行了输入，则可能会在 *StopCapturingGestures ( # B1* 之后生成笔势事件。 *GestureRecognizer* 将记得在上一帧实际发生的情况下，它是处于打开还是关闭状态，因此，根据此帧的注视目标启动和停止手势监视是可靠的。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>停止捕获手势

停止手势识别：

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>删除手势识别器

请记住，在销毁 *GestureRecognizer* 对象之前，取消订阅已订阅的事件。

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

![运动控制器模型和 teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*运动控制器模型和 teleportation*

若要在应用中渲染与用户所持有的物理控制器相匹配的运动控制器，并在按下各种按钮时进行解释，可以在 [混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/)中使用 **MotionController prefab** 。  此 prefab 从系统的已安装运动控制器驱动程序在运行时动态加载正确的 glTF 模型。  必须动态加载这些模型，而不是在编辑器中手动导入它们，以便您的应用程序能够显示您的用户可能拥有的任何当前和未来控制器的物理上准确的3D 模型。

1. 按照 [入门](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 说明下载混合现实工具包，并将其添加到 Unity 项目。
2. 如果在入门步骤中将相机替换为 *MixedRealityCameraParent* prefab，则准备就绪！  该 prefab 包括运动控制器呈现。  否则，请从 "项目" 窗格中将 *资产/HoloToolkit/Input/prototyping/MotionControllers* 添加到场景中。  你需要将该 prefab 添加为你用来移动相机的任何父对象的子对象，以使该用户在场景中 teleports 时，使控制器与用户一起工作。  如果应用不涉及 teleporting，只需在场景的根目录中添加 prefab。

## <a name="throwing-objects"></a>引发对象

在虚拟现实中引发对象比最初可能更难。 与大多数基于物理的交互一样，当游戏中的抛出意外时，它会立即出现，并打破浸入式。 我们花了一些时间来了解如何表示物理上正确的引发行为，并通过我们的平台的更新启用了一些准则，我们想要与你共享。

可在 [此处](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到如何实现引发的示例。 此示例遵循以下四个准则：
* **使用控制器的 *速度* （而不是位置**）。 在11月的 Windows 更新中，我们引入了 ["近似" 位置跟踪状态](../../design/motion-controllers.md#controller-tracking-state)下的行为更改。 处于此状态时，将继续报告有关控制器的速率信息，前提是我们相信它的高准确性，这通常比位置长。
* **合并控制器的 *角度速度***。 此逻辑全部包含在 `throwing.cs` 文件中的静态方法中，该文件位于 `GetThrownObjectVelAngVel` 以上链接的包中：
   1. 在角度速度 conserved 时，引发的对象必须保持与抛出时相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. 由于引发的对象很大范围可能不会成为手柄姿势的源，因此它的速度可能比用户引用框架中控制器的速度不同。 以这种方式提供的对象速度的部分是围绕控制器原点的已抛出对象的质量的瞬间相切速度。 此相切速度是控制器角度速度的叉积，向量表示控制器原点与所引发对象的质量中心之间的距离。

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. 引发的对象的总速度是控制器的速度与此相切速度的总和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* 密切 **关注我们应用速度的 *时间***。 按下按钮时，该事件最多可能需要 20 ms 才能通过蓝牙向上向上冒泡到操作系统。 这意味着，如果你将控制器状态更改从按下状态更改为未按下或其他方式，则控制器会提供你获取的信息。 接下来，轮询 API 所提供的控制器可能是向前预测的，它会在帧显示时反映可能的情况，这可能会在未来超过 20 ms。 这适用于 *呈现* 已保存的对象，但会在计算用户释放引发的时间轨迹时，为 *目标* 对象提供时间问题。 幸运的是，在11月更新中，当发送 Unity 事件（如 *InteractionSourcePressed* 或 *InteractionSourceReleased* ）时，当按下或释放该按钮时，该状态包含来自后端的历史记录数据。  若要在引发期间获得最准确的控制器呈现和控制器目标，则必须根据需要正确使用轮询和事件：
   * 对于每个帧的 **控制器呈现** ，你的应用程序应将控制器的 *GameObject* 放在前预测的控制器上，为当前帧的 photon 时间提供。  可以从 XR 等 Unity 轮询 Api 获取此数据 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。WSA.InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。
   * 对于 **控制器** 针对按下或释放的目标，应用程序应基于该按下或释放事件的历史控制器提出的 raycast 和计算轨迹。  可以从 Unity 事件 Api 获取此数据，如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。
* **使用手柄姿势**。 相对于手柄姿势报告角度速度和速度，而不是指针姿势。

在将来的 Windows 更新中，引发将继续改进，你可以在此处找到详细信息。

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>MRTK v2 中的手势和运动控制器

可以从输入管理器访问笔势和运动控制器。
* [MRTK v2 中的手势](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [MRTK v2 中的运动控制器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>按照教程进行操作

混合现实学院中提供了更详细的自定义示例的分步教程：

- [MR 输入 211：手势](tutorials/holograms-211.md)
- [MR 输入 213：运动控制器](../../deprecated/mixed-reality-213.md)

[![MR 输入 213-运动控制器](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*MR 输入 213-运动控制器*

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [手部和眼部跟踪](./hand-eye-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅

* [头部凝视并提交](../../design/gaze-and-commit.md)
* [运动控制器](../../design/motion-controllers.md)