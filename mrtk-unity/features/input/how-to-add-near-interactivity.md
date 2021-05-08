---
title: HowToAddNearInteractivity
description: MRTK 中有关近交互的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，近交互，
ms.openlocfilehash: fc6fbb33e5a8e9aa6930f56f292f8ded51c53ff0
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644843"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a>如何在 MRTK 中添加近乎交互

近交互采用触摸和获取的形式。 触控和抓取事件分别由 [PokePointer](pointers.md#pokepointer) 和 [SpherePointer](pointers.md#spherepointer)的指针事件引发。

需要使用三个关键步骤来侦听特定 GameObject 上的触摸和/或获取输入事件。

1. 确保在主 [MRTK 配置文件](../../configuration/mixed-reality-configuration-guide.md)中注册相关指针。
1. 确保所需的 GameObject 具有适当的 [获取](#add-grab-interactions) 或 [触摸](#add-touch-interactions) 脚本组件和 [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) 。
1. 将附加脚本上的输入处理程序接口实现到所需的 GameObject 以侦听 [抓取](#grab-code-example) 或 [触摸](#touch-code-example) 事件。

## <a name="add-grab-interactions"></a>添加抓取交互

1. 确保在 *MRTK 指针配置文件* 中注册了 [SpherePointer](pointers.md#spherepointer) 。

    默认的 MRTK 配置文件和默认的 HoloLens 2 配置文件已包含一个 *SpherePointer*。 可以通过选择 MRTK 配置文件并导航到 **输入**  >  **指针**  >  **指针选项** 来确认将创建的 SpherePointer。 默认的 `GrabPointer` prefab (资产/MRTK/SDK/功能/UX/prototyping/指针) 应列在 *控制器类型* 中。  只要实现了类，就可以使用自定义 prefab [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) 。

    ![抓取指针配置文件示例](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    默认的抓取指针将在抓取点周围的锥形中查询附近的对象，以匹配默认的 Hololens 2 接口。

    ![圆锥抓取指针](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. 在应为 grabbable 的 GameObject 上，添加一个 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) ，以及一个碰撞器。

    确保 GameObject 的层位于 grabbable 层上。 默认情况下，所有层（ *空间感知* 和 *忽略 Raycasts* ）都是 grabbable。 检查 *GrabPointer* prefab 中的 *抓取层掩码*，查看哪些层是 grabbable 的。

1. 在 GameObject 或其任一上级上，添加一个实现接口的脚本组件 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 。 对象的任何上级 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 都将能够接收指针事件。

### <a name="grab-code-example"></a>获取代码示例

下面的脚本将在事件为触摸或抓取时打印。 在相关的 *IMixedRealityPointerHandler* 接口函数中，可以查看通过触发该事件的指针类型 [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) 。 如果指针是 *SpherePointer*，则交互是一个捕获。

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

## <a name="add-touch-interactions"></a>添加触控交互

在 UnityUI 元素上添加触控交互的过程不同于 vanilla 3D Gameobject。 可以跳到以下部分（ *UNITY ui*）来启用 Unity ui 组件。

不过，对于 **这两种** 类型的 UX 元素，请确保在 *MRTK 指针配置文件* 中注册了 [PokePointer](pointers.md#pokepointer) 。

默认的 MRTK 配置文件和默认的 HoloLens 2 配置文件已包含一个 *PokePointer*。 可以通过选择 MRTK 配置文件并导航到 "**输入**  >  **指针**  >  **指针" 选项** 来确认将创建的 PokePointer。 默认 `PokePointer` (资产/MRTK/SDK/功能/UX/prototyping/指针) prefab 应列在 *控制器类型* 中。  只要实现了类，就可以使用自定义 prefab [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 。

!["文件" 指针配置文件示例](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>三维 Gameobject

可以通过两种不同的方式向 3D Gameobject 添加触摸交互，具体取决于你的3d 对象应仅具有单个可触摸平面，还是应基于其整个碰撞器进行可触摸。
第一种方法通常是在具有 BoxColliders 的对象上，只需将碰撞器的单个面用于触控事件。 另一种是对于需要根据其碰撞器从任何方向可触摸的对象。

### <a name="single-face-touch"></a>单一面部触控

这对于启用只有单个人脸需要可触摸的情况非常有用。 此选项假设游戏对象具有 BoxCollider。 可以将它与非 BoxCollider 对象一起使用，在这种情况下，"边界" 和 "本地中心" 属性很大程度上是手动设置的，以便配置可触摸平面 (即应将界限设置为非零零值) 。

1. 在应为可触摸的 GameObject 上，添加 BoxCollider 和 [ `NearInteractionTouchable` ] (x： MixedReality) 组件。

    1. *如果* 在下面的组件脚本中使用 [] (x： MixedReality) 接口，请设置要 **接收的事件** `IMixedRealityTouchHandler` 。

    1. 单击 "**修复边界** 和 **修复中心**"

    ![NearInteractionTouchable 安装程序](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. 在该对象或其上级之一上，添加一个实现的脚本组件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   交互. 具有 [ `NearInteractionTouchable` ] (x： MixedReality. NearInteractionTouchable) 的对象的任何上级也将能够接收指针事件。

> [!NOTE]
> 在选择了 *NearInteractionTouchable* GameObject 的编辑器场景视图中，请注意一个白色的边框正方形和箭头。 箭头指向可触摸的 "front"。 Collidable 将仅从该方向可触摸。 若要使碰撞器可触摸所有方向，请参阅 [任意碰撞器触摸](#arbitrary-collider-touch)的部分。
> ![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>任意碰撞器触控

这对于启用游戏对象需要沿其整个碰撞面可触摸的情况非常有用。 例如，这可用于为具有 SphereCollider 的对象启用触摸交互，在这种情况下，整个碰撞器都需要为可触摸。

1. 在应可触摸的 GameObject 上，添加一个碰撞器和 [ `NearInteractionTouchableVolume` ] (x： MixedReality) 组件。

    1. *如果* 在下面的组件脚本中使用 [] (x： MixedReality) 接口，请设置要 **接收的事件** `IMixedRealityTouchHandler` 。

1. 在该对象或其上级之一上，添加一个实现的脚本组件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   交互. 具有 [ `NearInteractionTouchable` ] (x： MixedReality. NearInteractionTouchable) 的对象的任何上级也将能够接收指针事件。

### <a name="unity-ui"></a>Unity UI

1. 添加/确保场景中有一个 [UnityUI 画布](https://docs.unity3d.com/Manual/UICanvas.html) 。

1. 在可触摸的 GameObject 上，添加一个 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 组件。  

    1. *如果在* 下面的组件脚本中使用接口，请设置要 **接收的事件** [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。

1. 在该对象或其上级之一上，添加一个实现接口的脚本组件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。 对象的任何上级 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 都将能够接收指针事件。

> [!IMPORTANT]
> 如果对象位于重叠画布对象上，则对象的行为可能不符合预期。 为了确保行为一致，不会在场景中重叠画布对象。

> [!IMPORTANT]
> 在 `NearInteractionTouchable` 脚本组件中， *要接收* 的属性事件有两个选项： *指针* 和 *触摸*。 设置要接收到 *指针* 的 *事件*（如果使用 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 接口，并将其设置为 "*触摸*"，前提是 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 在组件脚本中使用响应/处理输入事件的接口。

#### <a name="touch-code-example"></a>触控代码示例

下面的代码演示了一个 MonoBehaviour，它可以附加到具有 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 变体组件并响应触控输入事件的 GameObject。

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

此示例创建一个多维数据集，使其可触摸，并更改触控上的颜色。

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

### <a name="grab-events"></a>获取事件

下面的示例演示如何使 GameObject 可拖动。 假定游戏对象上有一个碰撞器。

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
