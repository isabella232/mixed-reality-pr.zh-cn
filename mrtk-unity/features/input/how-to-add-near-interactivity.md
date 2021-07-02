---
title: 如何添加近乎交互
description: MRTK 中有关近交互的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，近交互，
ms.openlocfilehash: 241425f0c158d684cad6dad8c88c8d692cbec42f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176876"
---
# <a name="how-to-add-near-interactivity"></a><span data-ttu-id="45232-104">如何添加近乎交互</span><span class="sxs-lookup"><span data-stu-id="45232-104">How to add near interactivity</span></span>

<span data-ttu-id="45232-105">近交互采用触摸和获取的形式。</span><span class="sxs-lookup"><span data-stu-id="45232-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="45232-106">触控和抓取事件分别由 [PokePointer](pointers.md#pokepointer) 和 [SpherePointer](pointers.md#spherepointer)的指针事件引发。</span><span class="sxs-lookup"><span data-stu-id="45232-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="45232-107">需要使用三个关键步骤来侦听特定 GameObject 上的触摸和/或获取输入事件。</span><span class="sxs-lookup"><span data-stu-id="45232-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="45232-108">确保在主 [MRTK 配置文件](../../configuration/mixed-reality-configuration-guide.md)中注册相关指针。</span><span class="sxs-lookup"><span data-stu-id="45232-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="45232-109">确保所需的 GameObject 具有适当的 [获取](#add-grab-interactions) 或 [触摸](#add-touch-interactions) 脚本组件和 [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) 。</span><span class="sxs-lookup"><span data-stu-id="45232-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="45232-110">将附加脚本上的输入处理程序接口实现到所需的 GameObject 以侦听 [抓取](#grab-code-example) 或 [触摸](#touch-code-example) 事件。</span><span class="sxs-lookup"><span data-stu-id="45232-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="45232-111">添加抓取交互</span><span class="sxs-lookup"><span data-stu-id="45232-111">Add grab interactions</span></span>

1. <span data-ttu-id="45232-112">确保在 *MRTK 指针配置文件* 中注册了 [SpherePointer](pointers.md#spherepointer) 。</span><span class="sxs-lookup"><span data-stu-id="45232-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="45232-113">默认的 MRTK 配置文件和默认 HoloLens 2 配置文件已经包含一个 *SpherePointer*。</span><span class="sxs-lookup"><span data-stu-id="45232-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="45232-114">可以通过选择 MRTK 配置文件并导航到 **输入**  >  **指针**  >  **指针选项** 来确认将创建的 SpherePointer。</span><span class="sxs-lookup"><span data-stu-id="45232-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="45232-115">默认的 `GrabPointer` prefab (资产/MRTK/SDK/功能/UX/prototyping/指针) 应列在 *控制器类型* 中。 </span><span class="sxs-lookup"><span data-stu-id="45232-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="45232-116">只要实现了类，就可以使用自定义 prefab [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) 。</span><span class="sxs-lookup"><span data-stu-id="45232-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![抓取指针配置文件示例](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="45232-118">默认的抓取指针将在抓取点周围的锥形中查询附近的对象，以匹配默认的 Hololens 2 接口。</span><span class="sxs-lookup"><span data-stu-id="45232-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![圆锥抓取指针](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="45232-120">在应为 grabbable 的 GameObject 上，添加一个 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) ，以及一个碰撞器。</span><span class="sxs-lookup"><span data-stu-id="45232-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="45232-121">确保 GameObject 的层位于 grabbable 层上。</span><span class="sxs-lookup"><span data-stu-id="45232-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="45232-122">默认情况下，所有层（ *空间感知* 和 *忽略 Raycasts* ）都是 grabbable。</span><span class="sxs-lookup"><span data-stu-id="45232-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="45232-123">检查 *GrabPointer* prefab 中的 *抓取层掩码*，查看哪些层是 grabbable 的。</span><span class="sxs-lookup"><span data-stu-id="45232-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="45232-124">在 GameObject 或其任一上级上，添加一个实现接口的脚本组件 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 。</span><span class="sxs-lookup"><span data-stu-id="45232-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="45232-125">对象的任何上级 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 都将能够接收指针事件。</span><span class="sxs-lookup"><span data-stu-id="45232-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="45232-126">获取代码示例</span><span class="sxs-lookup"><span data-stu-id="45232-126">Grab code example</span></span>

<span data-ttu-id="45232-127">下面的脚本将在事件为触摸或抓取时打印。</span><span class="sxs-lookup"><span data-stu-id="45232-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="45232-128">在相关的 *IMixedRealityPointerHandler* 接口函数中，可以查看通过触发该事件的指针类型 [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) 。</span><span class="sxs-lookup"><span data-stu-id="45232-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="45232-129">如果指针是 *SpherePointer*，则交互是一个捕获。</span><span class="sxs-lookup"><span data-stu-id="45232-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

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

## <a name="add-touch-interactions"></a><span data-ttu-id="45232-130">添加触控交互</span><span class="sxs-lookup"><span data-stu-id="45232-130">Add touch interactions</span></span>

<span data-ttu-id="45232-131">在 UnityUI 元素上添加触控交互的过程不同于 vanilla 3D Gameobject。</span><span class="sxs-lookup"><span data-stu-id="45232-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="45232-132">可以跳到以下部分（ *UNITY ui*）来启用 Unity ui 组件。</span><span class="sxs-lookup"><span data-stu-id="45232-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="45232-133">不过，对于 **这两种** 类型的 UX 元素，请确保在 *MRTK 指针配置文件* 中注册了 [PokePointer](pointers.md#pokepointer) 。</span><span class="sxs-lookup"><span data-stu-id="45232-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="45232-134">默认的 MRTK 配置文件和默认 HoloLens 2 配置文件已经包含一个 *PokePointer*。</span><span class="sxs-lookup"><span data-stu-id="45232-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="45232-135">可以通过选择 MRTK 配置文件并导航到 "**输入**  >  **指针**  >  **指针" 选项** 来确认将创建的 PokePointer。</span><span class="sxs-lookup"><span data-stu-id="45232-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="45232-136">默认 `PokePointer` (资产/MRTK/SDK/功能/UX/prototyping/指针) prefab 应列在 *控制器类型* 中。 </span><span class="sxs-lookup"><span data-stu-id="45232-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="45232-137">只要实现了类，就可以使用自定义 prefab [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 。</span><span class="sxs-lookup"><span data-stu-id="45232-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

!["文件" 指针配置文件示例](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="45232-139">三维 Gameobject</span><span class="sxs-lookup"><span data-stu-id="45232-139">3D GameObjects</span></span>

<span data-ttu-id="45232-140">可以通过两种不同的方式向 3D Gameobject 添加触摸交互，具体取决于你的3d 对象应仅具有单个可触摸平面，还是应基于其整个碰撞器进行可触摸。</span><span class="sxs-lookup"><span data-stu-id="45232-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="45232-141">第一种方法通常是在具有 BoxColliders 的对象上，只需将碰撞器的单个面用于触控事件。</span><span class="sxs-lookup"><span data-stu-id="45232-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="45232-142">另一种是对于需要根据其碰撞器从任何方向可触摸的对象。</span><span class="sxs-lookup"><span data-stu-id="45232-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="45232-143">单一面部触控</span><span class="sxs-lookup"><span data-stu-id="45232-143">Single face touch</span></span>

<span data-ttu-id="45232-144">这对于启用只有单个人脸需要可触摸的情况非常有用。</span><span class="sxs-lookup"><span data-stu-id="45232-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="45232-145">此选项假设游戏对象具有 BoxCollider。</span><span class="sxs-lookup"><span data-stu-id="45232-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="45232-146">可以将它与非 BoxCollider 对象一起使用，在这种情况下，"边界" 和 "本地中心" 属性很大程度上是手动设置的，以便配置可触摸平面 (即应将界限设置为非零零值) 。</span><span class="sxs-lookup"><span data-stu-id="45232-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="45232-147">在可触摸的 GameObject 中，添加 BoxCollider 和 [ `NearInteractionTouchable` ] (x： Toolkit MixedReality。NearInteractionTouchable) 组件。</span><span class="sxs-lookup"><span data-stu-id="45232-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="45232-148">如果使用 [] (x： Toolkit MixedReality，*请设置要* 接收的事件 `IMixedRealityTouchHandler` 。IMixedRealityTouchHandler 在以下组件脚本中) 接口。</span><span class="sxs-lookup"><span data-stu-id="45232-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="45232-149">单击 "**修复边界** 和 **修复中心**"</span><span class="sxs-lookup"><span data-stu-id="45232-149">Click **Fix bounds** and **Fix center**</span></span>

    ![NearInteractionTouchable 安装程序](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="45232-151">在该对象或其上级之一上，添加一个实现的脚本组件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="45232-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="45232-152">交互.</span><span class="sxs-lookup"><span data-stu-id="45232-152">interface.</span></span> <span data-ttu-id="45232-153">具有 [ `NearInteractionTouchable` ] (x： Toolkit MixedReality 的对象的任何上级。NearInteractionTouchable) 也可以接收指针事件。</span><span class="sxs-lookup"><span data-stu-id="45232-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="45232-154">在选择了 *NearInteractionTouchable* GameObject 的编辑器场景视图中，请注意一个白色的边框正方形和箭头。</span><span class="sxs-lookup"><span data-stu-id="45232-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="45232-155">箭头指向可触摸的 "front"。</span><span class="sxs-lookup"><span data-stu-id="45232-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="45232-156">Collidable 将仅从该方向可触摸。</span><span class="sxs-lookup"><span data-stu-id="45232-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="45232-157">若要使碰撞器可触摸所有方向，请参阅 [任意碰撞器触摸](#arbitrary-collider-touch)的部分。</span><span class="sxs-lookup"><span data-stu-id="45232-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="45232-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="45232-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="45232-159">任意碰撞器触控</span><span class="sxs-lookup"><span data-stu-id="45232-159">Arbitrary collider touch</span></span>

<span data-ttu-id="45232-160">这对于启用游戏对象需要沿其整个碰撞面可触摸的情况非常有用。</span><span class="sxs-lookup"><span data-stu-id="45232-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="45232-161">例如，这可用于为具有 SphereCollider 的对象启用触摸交互，在这种情况下，整个碰撞器都需要为可触摸。</span><span class="sxs-lookup"><span data-stu-id="45232-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="45232-162">在应可触摸的 GameObject 上，添加一个碰撞器和 [ `NearInteractionTouchableVolume` ] (x： Toolkit MixedReality。NearInteractionTouchableVolume) 组件。</span><span class="sxs-lookup"><span data-stu-id="45232-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="45232-163">如果使用 [] (x： Toolkit MixedReality，*请设置要* 接收的事件 `IMixedRealityTouchHandler` 。IMixedRealityTouchHandler 在以下组件脚本中) 接口。</span><span class="sxs-lookup"><span data-stu-id="45232-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="45232-164">在该对象或其上级之一上，添加一个实现的脚本组件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="45232-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="45232-165">交互.</span><span class="sxs-lookup"><span data-stu-id="45232-165">interface.</span></span> <span data-ttu-id="45232-166">具有 [ `NearInteractionTouchable` ] (x： Toolkit MixedReality 的对象的任何上级。NearInteractionTouchable) 也可以接收指针事件。</span><span class="sxs-lookup"><span data-stu-id="45232-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="45232-167">Unity UI</span><span class="sxs-lookup"><span data-stu-id="45232-167">Unity UI</span></span>

1. <span data-ttu-id="45232-168">添加/确保场景中有一个 [UnityUI 画布](https://docs.unity3d.com/Manual/UICanvas.html) 。</span><span class="sxs-lookup"><span data-stu-id="45232-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="45232-169">在可触摸的 GameObject 上，添加一个 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 组件。</span><span class="sxs-lookup"><span data-stu-id="45232-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="45232-170">*如果在* 下面的组件脚本中使用接口，请设置要 **接收的事件** [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。</span><span class="sxs-lookup"><span data-stu-id="45232-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="45232-171">在该对象或其上级之一上，添加一个实现接口的脚本组件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。</span><span class="sxs-lookup"><span data-stu-id="45232-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="45232-172">对象的任何上级 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 都将能够接收指针事件。</span><span class="sxs-lookup"><span data-stu-id="45232-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45232-173">如果对象位于重叠画布对象上，则对象的行为可能不符合预期。</span><span class="sxs-lookup"><span data-stu-id="45232-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="45232-174">为了确保行为一致，不会在场景中重叠画布对象。</span><span class="sxs-lookup"><span data-stu-id="45232-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45232-175">在 `NearInteractionTouchable` 脚本组件中， *要接收* 的属性事件有两个选项： *指针* 和 *触摸*。</span><span class="sxs-lookup"><span data-stu-id="45232-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="45232-176">设置要接收到 *指针* 的 *事件*（如果使用 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 接口，并将其设置为 "*触摸*"，前提是 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 在组件脚本中使用响应/处理输入事件的接口。</span><span class="sxs-lookup"><span data-stu-id="45232-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="45232-177">触控代码示例</span><span class="sxs-lookup"><span data-stu-id="45232-177">Touch code example</span></span>

<span data-ttu-id="45232-178">下面的代码演示了一个 MonoBehaviour，它可以附加到具有 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 变体组件并响应触控输入事件的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="45232-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

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

## <a name="near-interaction-script-examples"></a><span data-ttu-id="45232-179">近交互脚本示例</span><span class="sxs-lookup"><span data-stu-id="45232-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="45232-180">触摸事件</span><span class="sxs-lookup"><span data-stu-id="45232-180">Touch events</span></span>

<span data-ttu-id="45232-181">此示例创建一个多维数据集，使其可触摸，并更改触控上的颜色。</span><span class="sxs-lookup"><span data-stu-id="45232-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

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

### <a name="grab-events"></a><span data-ttu-id="45232-182">获取事件</span><span class="sxs-lookup"><span data-stu-id="45232-182">Grab events</span></span>

<span data-ttu-id="45232-183">下面的示例演示如何使 GameObject 可拖动。</span><span class="sxs-lookup"><span data-stu-id="45232-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="45232-184">假定游戏对象上有一个碰撞器。</span><span class="sxs-lookup"><span data-stu-id="45232-184">Assumes that the game object has a collider on it.</span></span>

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

## <a name="useful-apis"></a><span data-ttu-id="45232-185">有用的 API</span><span class="sxs-lookup"><span data-stu-id="45232-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="45232-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45232-186">See also</span></span>

* [<span data-ttu-id="45232-187">输入概述</span><span class="sxs-lookup"><span data-stu-id="45232-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="45232-188">指针</span><span class="sxs-lookup"><span data-stu-id="45232-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="45232-189">输入事件数</span><span class="sxs-lookup"><span data-stu-id="45232-189">Input Events</span></span>](input-events.md)
