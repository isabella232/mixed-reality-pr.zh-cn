---
title: 目视跟踪目标选择
description: 如何访问眼睛数据和目视注视特定事件，以在 MRTK 中选择目标
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，EyeTracking，
ms.openlocfilehash: aab2f35259db183f4f3edb4fffc2b3e7a066bccf9c69e492c90ee193388b8b7a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189585"
---
# <a name="eye-supported-target-selection"></a>目视支持的目标选择

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

本页讨论用于访问眼睛数据的不同选项，以及用于在 MRTK 中选择目标的目视特定事件。 使用目视跟踪，可以通过与用户正在查看的信息以及有关 _手动跟踪_ 和 _语音命令_ 等其他输入的信息组合来进行快速轻松的目标选择：

- 查找 & 说 _"选择"_ (默认的语音命令) 
- 查找 (自定义语音命令 & 说 _"分解"_ 或 _"Pop"_) 
- 查看 & 蓝牙按钮
- 看看 & 挤压 (例如，在你的前方，将拇指和食指置于一起) 
  - 请注意，要使其正常工作， [需要禁用手写片](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)

若要使用眼睛来选择全息内容，有几个选项可供选择：

[**1. 使用主要焦点指针：**](#1-use-generic-focus-and-pointer-handlers)

这可以理解为优先顺序的游标。
默认情况下，如果手处于视图状态，则这将是手动光线。
如果没有任何指针在视图中，则优先顺序的指针将为 head 或眼睛。
因此，请注意，如果使用的是手写光线，则会将基于当前设计头或眼睛的眼睛禁止为光标输入。

例如：

用户需要选择一个 "远处" 的全息按钮。
作为开发人员，您希望提供一个灵活的解决方案，使用户能够在各种情况下实现此任务：

- 转到按钮并浏览
- 从远处观看，说 "选择"
- 在这种情况下，使用手 ray 定位按钮并执行挤压，最灵活的解决方案是使用主焦点处理程序，因为当当前优先级优先顺序指针触发事件时，它会通知你。 请注意，如果启用了 "手写" 光线，则一旦进入查看，就会立即禁用 head 或眼睛视觉焦点指针。

> [!IMPORTANT]
> 请注意，如果启用了 "手写" 光线，则一旦进入查看，就会立即禁用 head 或眼睛视觉焦点指针。 如果要支持 [ _"外观和挤压"_ 交互，则需要禁用该手型](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)。 在我们的眼睛跟踪示例场景中，我们已禁用了 "手动" 光线，以允许使用眼睛 + 手动作展示更丰富的交互-请参阅示例 [目视支持的定位](eye-tracking-eyes-and-hands.md)。

[**2. 同时使用目视关注和手中光线：**](#2-independent-eye-gaze-specific-eyetrackingtarget)

在某些情况下，你可能想要更具体地了解哪种类型的焦点指针可以触发某些事件，并允许同时使用多个远交互技术。

例如：在您的应用程序中，用户可以使用 "far" 光线来操纵一些全息机械设置-例如，抓住并保存一些较远的全息引擎部件，并将其固定到位。 这样做时，用户必须通过一系列说明，并通过标记一些复选框来记录她/他的进度。 如果用户的工作 _不忙_，只需触摸复选框或使用手 instinctual 选择它。 但是，如果用户有她/他的工作繁忙，则在我们的示例中，您需要让用户使用其眼睛无缝滚动说明，只需查看一个复选框，然后说 "检查！"。

若要启用此项，需要使用独立于 core MRTK FocusHandlers 的眼睛特定的 EyeTrackingTarget 脚本，稍后将对此进行讨论。

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. 使用一般焦点和指针处理程序

如果正确设置了目视跟踪 (参阅 [基本 MRTK 安装程序以使用目视跟踪](eye-tracking-basic-setup.md)) ，使用户可以使用眼睛来选择全息影像，这与任何其他焦点输入 (例如，打印头或手 ray) 相同。这使你可以通过在 MRTK 输入指针配置文件中定义主焦点类型（这取决于用户的需求）来灵活地与全息影像交互，同时使代码保持不变。 这允许在打印头或眼睛眼睛之间切换，而无需更改代码行或将手形光线替换为远交互的目视目标。

### <a name="focusing-on-a-hologram"></a>专注于全息图

若要检测全息影像的聚焦情况，请使用 _"IMixedRealityFocusHandler"_ 接口，该接口提供两个接口成员： _OnFocusEnter_ 和 _OnFocusExit_。

下面是 [ColorTap](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) 中的一个简单示例，用于在查看时更改全息图的颜色。

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a>选择重点全息图

若要选择具有焦点的全息图，请使用 _PointerHandler_ 侦听输入事件以确认所做的选择。
例如，添加 _IMixedRealityPointerHandler_ 会使它们对简单指针输入做出反应。
_IMixedRealityPointerHandler_ 接口需要实现以下三个接口成员： _OnPointerUp_、 _OnPointerDown_ 和 _OnPointerClicked_。

在下面的示例中，我们通过查看并收缩或说 "select" 来更改全息图的颜色。
触发事件所需的操作的定义是， `eventData.MixedRealityInputAction == selectAction` 我们可以 `selectAction` 在 Unity 编辑器中设置的类型-默认情况下，它是 "选择" 操作。 可以通过 [](../input-actions.md) _MRTK 配置文件_  ->  _输入_  ->  _输入操作_ 在 MRTK 配置文件中配置可用 MixedRealityInputActions 的类型。

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a>眼睛特定的 BaseEyeFocusHandler

如果眼睛看起来可能与其他指针输入非常不同，则你可能想要确保只在 _视觉_ 上输入时做出反应，并确保它当前是主输入指针。
出于此目的，你将使用 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) 特定于目视跟踪的，以及从派生的 [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) 。
如前文所述，它仅在目视注视目标为主指针输入 (即，没有手) 处于活动状态时才触发。 有关详细信息，请参阅 [如何支持眼睛眼睛 + 手势](eye-tracking-eyes-and-hands.md)。

下面是 `EyeTrackingDemo-03-Navigation` (资产/MRTK/示例/演示/EyeTracking/场景) 的示例。
在此演示中，有两个将根据对象的哪个部分进行检查的3D 全息影像：如果用户查看全息图的左侧，则该部件将慢慢地向正面朝用户方向移动。
如果查看了右侧，那部分会慢慢地移至前面。
这是一种可能不希望在任何时候都处于活动状态的行为，也可能不希望手中出现意外触发的情况。
附加后 [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) ，GameObject 将在查看时旋转。

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

有关可用事件的完整列表，请参阅 API 文档 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) ：

- **OnEyeFocusStart：** 眼睛眼睛与此目标的碰撞 *器相交后* 触发。
- **OnEyeFocusStay：** 眼睛眼睛与此目标的碰撞器相交 *时* 触发。
- **OnEyeFocusStop：** 眼睛眼睛 *停止* 与此目标的碰撞器相交后触发。
- **OnEyeFocusDwell：** 眼睛在指定的时间段内与此目标的碰撞器相交后触发。

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. 独立的眼睛-注视特定的 EyeTrackingTarget

最后，我们为您提供了一个解决方案，让您通过脚本将基于目视的输入完全独立于其他焦点指针 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。

这有三大 _优点_：

- 可以确保只对用户的眼睛进行反应。
- 这与当前活动的主输入无关。 因此，可以一次处理多个输入，例如，将快速目视定位与手势结合起来。
- 已经设置了几个 Unity 事件，使您能够快速轻松地处理和重用 Unity 编辑器内或通过代码中的现有行为。

还有一些 _缺点：_

- 分别处理单独的输入的工作量。
- 不优雅地降低：它仅支持目视目标。 如果目视跟踪不起作用，则需要额外的回退。

与 _BaseFocusHandler_ 类似， _EyeTrackingTarget_ 已准备好几个眼睛特定的 unity 事件，你可以通过 Unity 编辑器轻松地侦听这些事件 (参见下面的示例) 或通过在代码中使用 _AddListener ()_ ：

- OnLookAtStart () 
- WhileLookingAtTarget () 
- OnLookAway () 
- OnDwell () 
- OnSelected () 

在下面的示例中，我们将逐步介绍如何使用 _EyeTrackingTarget_。

### <a name="example-1-eye-supported-smart-notifications"></a>示例 #1：目视支持的智能通知

在 `EyeTrackingDemo-02-TargetSelection` (资产/MRTK/示例/演示/EyeTracking/场景) 中，可以找到反应眼睛的 _"智能留心通知"_ 的示例。
这些是可放置在场景中的3D 文本框，当查看这些文本框以便于辨认时，它们会平稳地放大并向用户翻。 当用户阅读通知时，信息始终显示清晰清晰。 阅读并查看通知后，将自动消除通知并将其淡出。为实现所有这一切，有几个根本不特定于目视跟踪的通用行为脚本，例如：

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

此方法的优点是可以通过各种事件重用相同的脚本。 例如，全息图可能会根据声音命令或在按虚拟按钮后开始面向用户。 若要触发这些事件，只需引用应在附加到 GameObject 的脚本中执行的方法 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。

对于 _"智能留心通知"_ 示例，会发生以下情况：

- **OnLookAtStart ()**：通知开始到 .。。
  - *FaceUser：* .。。向用户转。
  - *ChangeSize：* .。。大小增加 _(最大为指定的最大刻度)_。
  - *BlendOut：* .。。开始在更 _微妙的空闲状态) 之后_ 混合更多 (。  

- **OnDwell ()**：通知 _BlendOut_ 脚本已充分查看通知。

- **OnLookAway ()**：通知开始到 .。。
  - *FaceUser：* .。。返回到其原始方向。
  - *ChangeSize：* .。。减小到其原始大小。
  - *BlendOut：* .。。开始进行 blend-如果触发了 _OnDwell ()_ ，请完全和销毁，并将其恢复到其空闲状态。

**设计注意事项：** 这种体验的关键是要认真调整任何这些行为的速度，以避免通过对用户的眼睛反应太快来导致 discomfort。
否则，这很快就会让人感到难以承受。

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>示例#2：全息 gem 在查看时缓慢旋转

与示例 #1 类似，我们可以轻松地为 (Assets/MRTK/Examples/Demos/EyeTracking/Scene) 场景中的全息 gem 创建悬停反馈，该场景在查看时以恒定方向和恒定速度 (缓慢旋转 (与上面) 中的旋转示例相反。 `EyeTrackingDemo-02-TargetSelection` 只需从 EyeTrackingTarget 的 _WhileLookingAtTarget_ 事件触发全息 () 旋转。  下面是一些更多详细信息：

1. 创建包含公共函数的通用脚本，以轮换它附加到的 GameObject。 下面是 _RotateWithConstSpeedDir.cs_ 中的示例，可在其中从 Unity 编辑器调整旋转方向和速度。

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. 将 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 脚本添加到目标 GameObject， () UnityEvent 触发器中 _引用 RotateTarget_ () 函数，如以下屏幕截图所示：

    ![EyeTrackingTarget 示例](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>示例#3：弹出这些 gem（也名多模式 _眼睛凝视支持的目标选择）_

在上一示例中，我们演示了检测是否查看目标以及触发对此的反应是多么容易。 接下来，让我们使用 中的 _OnSelected_ () 事件使 gem 分解 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。 有趣的部分是 *如何* 触发选择。 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)允许快速分配调用所选内容的不同方法：

- _收缩手势_：将"选择操作"设置为"Select"使用默认手势来触发选择。
这意味着，用户只需举手，将手指和手指合在一起以确认选择。

- 说 _"选择"：_ 使用默认语音命令 _"选择"_ 来选择全息影像。

- 说 _"分解"_ 或 _"Pop"：_ 若要使用自定义语音命令，需要执行两个步骤：
    1. 设置自定义操作，例如 _"DestroyTarget"_
        - 导航到 _MRTK ->输入 ->输入操作_
        - 单击"添加新操作"

    2. 设置触发此操作的语音命令，例如" _分解"_ 或 _"Pop"_
        - 导航到 _MRTK ->输入 ->语音_
        - 单击"添加新的语音命令"
            - 关联刚刚创建的操作
            - 分配 _KeyCode_ 以允许通过按下按钮触发操作

![语音命令 EyeTrackingTarget 示例](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

选择 gem 后，它会分解，发出声音并消失。 这由脚本 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) 处理。 可以使用两个选项：

- **在 Unity 编辑器中：** 只需将附加到每个 gem 模板的脚本链接到 Unity 编辑器中的 OnSelected () Unity 事件。
- **在代码中：** 如果不想四处拖放 GameObject，还可以直接将事件侦听器添加到脚本。  
下面是我们在脚本中执行它 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) 的示例：

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>示例#4：将手部射线和眼睛凝视输入一起使用

手部射线优先于头部和眼睛凝视目标。 这意味着，如果启用手部射线，当手进入视图时，手部射线将充当主指针。
但是，在某些情况下，你可能想要在仍然检测用户是否正在查看某个全息影像的同时使用手部射线。 简单！ 实质上，需要执行两个步骤：

**1.启用手部射线：** 若要启用手部射线，请转到混合现实Toolkit _->输入 ->指针_。
在所有眼动跟踪演示场景配置混合现实 Toolkit 的 _EyeTrackingDemo-00-RootScene_ 中，应会看到 _EyeTrackingDemoPointerProfile_。
可以从头开始 _创建新的输入配置文件_ ，也可以调整当前眼动跟踪配置文件：

- **从头开始：** 在"_指针"_ 选项卡中，从上下文菜单中选择 _DefaultMixedRealityInputPointerProfile。_
这是已启用手部射线的默认指针配置文件！
若要更改默认光标 (不透明的白色) ，只需克隆配置文件并创建自己的自定义指针配置文件。
然后将 _DefaultCursor_ 替换为"凝视光标预制"下的 _EyeGazeCursor。_   
- **基于现有的 _EyeTrackingDemoPointerProfile：_** 双击 _EyeTrackingDemoPointerProfile，_ 在"指针选项"下 _添加以下条目_：
  - **控制器类型：**"表达手部"，"Windows Mixed Reality"
  - **手部：** 任何
  - **指针预制：** DefaultControllerPointer

**2.检测** 是否正在查看全息影像：使用脚本启用检测是否正在查看全息影像 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) ，如上所述。 还可以查看示例脚本以寻找灵感，因为此脚本在眼睛凝视后显示全息影像 (例如，光标) 是否启用手部射线。 `FollowEyeGaze`

现在，启动眼动跟踪演示场景时，应该会看到来自手部的射线。
例如，在眼动跟踪目标选择演示中，半透明圆圈仍在关注眼睛凝视，gem 会响应它们是否被查看，而顶部场景菜单按钮则使用主输入指针 (指针) 。

---
[返回到"MixedRealityToolkit 中的眼动跟踪"](eye-tracking-main.md)
