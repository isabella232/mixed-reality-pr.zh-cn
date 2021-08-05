---
title: 如何添加靠近交互
description: 有关 MRTK 中的近交互的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 近交互，
ms.openlocfilehash: 174623ebf340e800848c15e22dc2299aaf997b484a1329d67c28540acd79515a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212581"
---
# <a name="how-to-add-near-interactivity"></a>如何添加靠近交互

近处交互以触摸和抓取的形式提供。 Touch 和 grab 事件分别由数据线和[SpherePointer](pointers.md#pokepointer)引发[](pointers.md#spherepointer)为指针事件。

若要侦听特定 GameObject 上的触摸和/或抓取输入事件，需要执行三个关键步骤。

1. 确保在主 [MRTK](../../configuration/mixed-reality-configuration-guide.md)配置文件 中注册相关指针。
1. 确保所需的 GameObject 具有适当的[抓取或](#add-grab-interactions)[触摸](#add-touch-interactions)脚本组件 和 [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) 。
1. 在附加到所需 GameObject 的脚本上实现输入处理程序接口，以侦听 [抓取](#grab-code-example) 或 [触摸](#touch-code-example) 事件。

## <a name="add-grab-interactions"></a>添加抓取交互

1. 确保在 *MRTK* 指针配置文件 中注册 [SpherePointer。](pointers.md#spherepointer)

    默认 MRTK 配置文件和默认 HoloLens 2配置文件已包含 *SpherePointer*。 可以通过选择 MRTK 配置文件并导航到"输入指针指针选项"来确认将创建  >    >  **SpherePointer。** 应列出默认预制 `GrabPointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) ，其控制器类型应为"表达手 *"。*  只要自定义预制项实现 类，就可以使用 [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) 自定义预制。

    ![抓取指针配置文件示例](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    默认抓取指针查询抓取点周围圆环中的附近对象，以匹配默认的 Hololens 2 接口。

    ![圆条抓取指针](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. 在应可抓取的 GameObject 上，添加 以及 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 碰撞体。

    确保 GameObject 的层位于可抓取层上。 默认情况下，除空间感知和 *忽略光线广播* 外的所有层都是可抓取的。 通过检查 *GrabPointer* 预制中的抓取层 *掩码*，查看哪些层可抓取。

1. 在 GameObject 或它的上级之一上，添加实现 接口的脚本 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 组件。 具有 的对象的任何上级 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 也将能够接收指针事件。

### <a name="grab-code-example"></a>抓取代码示例

下面是在事件是触摸或抓取时将打印的脚本。 在相关的 *IMixedRealityPointerHandler* 接口函数中，可以查看通过 触发该事件的指针类型 [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) 。 如果指针是 *SpherePointer，* 则交互是抓取。

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a>添加触摸交互

在 UnityUI 元素上添加触摸交互的过程不同于普通 3D GameObject。 可以跳到下一部分 *Unity UI，* 以启用 Unity UI 组件。

但是 **，** 对于这两种类型的 UX 元素，请确保 *MrTK* 指针配置文件 中注册 [了一个一个数据](pointers.md#pokepointer)点器。

默认 MRTK 配置文件和默认 HoloLens 2配置文件已包含 *一个为 的一个。* 可以通过选择 MRTK 配置文件并导航到"输入指针指针""指针选项"来确认将创建一个将创建一个一  >    >  **个一体机**。 默认 `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) 预制器应列出控制器类型为"定点手 *"。*  只要自定义预制项实现 类，就可以使用 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 自定义预制。

![分型指针配置文件示例](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>3D GameObjects

有两种不同的方法向 3D GameObject 添加触摸交互，具体取决于你的 3d 对象应只具有一个可触摸平面，还是应基于其整个碰撞体来触摸它。
第一种方式通常是使用 BoxColliders 的对象，其中只需要碰撞体的单面对触摸事件做出反应。 另一种是适用于需要根据碰撞体从任何方向接触的对象。

### <a name="single-face-touch"></a>单面触摸

这可用于启用只需要接触单个人脸的情况。 此选项假定游戏对象具有 BoxCollider。 可以将其与非 BoxCollider 对象一起使用，在这种情况下，需要手动设置"边界"和"本地中心"属性来配置可触摸平面 (即边界应设置为非零零值) 。

1. 在应可触摸的 GameObject 上，添加 BoxCollider 和 [ `NearInteractionTouchable` ] (xref：Microsoft.MixedReality.Toolkit。Input.NearInteractionTouchable) 组件。

    1. 如果使用 **[** ]  `IMixedRealityTouchHandler` xref：Microsoft.MixedReality. (，将"接收事件"设置为"touch Toolkit。Input.IMixedRealityTouchHandler) 组件脚本中的接口。

    1. 单击 **"修复边界"和****"修复中心"**

    ![NearInteractionTouchable 安装程序](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. 在该对象或它的上级之一上，添加实现 的脚本组件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   接口。 具有 [ ] 的对象的任何上级 (`NearInteractionTouchable` xref：Microsoft.MixedReality.Toolkit。Input.NearInteractionTouchable) 还能够接收指针事件。

> [!NOTE]
> 在选择了 *NearInteractionTouchable* GameObject 的编辑器场景视图中，请注意白色边框正方形和箭头。 箭头指向可触摸的"正面"。 只能从该方向接触可碰撞对象。 若要使碰撞体从所有方向接触，请参阅有关任意碰撞体触摸 [的部分](#arbitrary-collider-touch)。
> ![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>任意碰撞体触摸

这可用于启用需要沿着整个碰撞体人脸接触游戏对象的情况。 例如，这可用于为具有 SphereCollider 的对象启用触摸交互，其中整个碰撞体需要可触摸。

1. 在应可触摸的 GameObject 上，添加碰撞体和 [ ] (`NearInteractionTouchableVolume` xref：Microsoft.MixedReality.Toolkit。Input.NearInteractionTouchableVolume) 组件。

    1. 如果使用 **[** ]  `IMixedRealityTouchHandler` xref：Microsoft.MixedReality. (，将"接收事件"设置为"touch Toolkit。Input.IMixedRealityTouchHandler) 组件脚本中的接口。

1. 在该对象或它的上级之一上，添加实现 的脚本组件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   接口。 具有 [ ] 的对象的任何上级 (`NearInteractionTouchable` xref：Microsoft.MixedReality.Toolkit。Input.NearInteractionTouchable) 还能够接收指针事件。

### <a name="unity-ui"></a>Unity UI

1. 添加/确保场景中有 [UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) 画布。

1. 在应可触摸的 GameObject 上，添加 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 组件。  

    1. 如果在 **下面的组件脚本***中使用该* 接口，将"事件"设置为" [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 接收到触摸"。

1. 在该对象或它的上级之一上，添加实现 接口的脚本 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 组件。 具有 的对象的任何上级 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 也将能够接收指针事件。

> [!IMPORTANT]
> 如果对象位于重叠的画布对象上，则它们的行为可能未按预期方式进行。 若要确保行为一致，切勿在场景中重叠画布对象。

> [!IMPORTANT]
> 在脚本 `NearInteractionTouchable` 组件上，对于属性 *"要接收的事件"，* 有两个选项："*指针*"和"*触摸"。* 如果使用 *接口，* 将"事件"设置为"接收到指针";如果在响应/处理输入事件的组件脚本中使用该接口，将 设置为 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) *Touch。* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

#### <a name="touch-code-example"></a>触控代码示例

下面的代码演示了一个 MonoBehaviour，该 MonoBehaviour 可以附加到包含变体组件的 GameObject 并 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 响应触摸输入事件。

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a>近交互脚本示例

### <a name="touch-events"></a>触摸事件

此示例创建一个立方体，使其可触摸，并更改触摸时的颜色。

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a>抓取事件

下面的示例演示如何使 GameObject 可拖动。 假设游戏对象上具有碰撞体。

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a>有用的 API

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a>另请参阅

* [输入概述](overview.md)
* [指针](pointers.md)
* [输入事件数](input-events.md)
