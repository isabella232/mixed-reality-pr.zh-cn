---
title: Unity 的输入移植指南
description: 了解如何在 Unity 中处理 Windows Mixed Reality 的输入。
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 输入、unity、移植
ms.openlocfilehash: d6bef0f10cf1fc20d5067ac77a126bb793385f59
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192645"
---
# <a name="input-porting-guide-for-unity"></a><span data-ttu-id="bad3c-104">Unity 的输入移植指南</span><span class="sxs-lookup"><span data-stu-id="bad3c-104">Input porting guide for Unity</span></span>

<span data-ttu-id="bad3c-105">你可以使用以下两种方法之一将输入逻辑移植到 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="bad3c-105">You can port your input logic to Windows Mixed Reality using one of two approaches.</span></span> <span data-ttu-id="bad3c-106">第一种是使用 Unity 的通用 GetButton/GetAxis Api 跨多个平台。</span><span class="sxs-lookup"><span data-stu-id="bad3c-106">The first is to use Unity's general Input.GetButton/GetAxis APIs that span across multiple platforms.</span></span> <span data-ttu-id="bad3c-107">第二个是特定于 Windows 的 XR。WSA.输入 Api，为运动控制器和 HoloLens 手提供了更丰富的数据。</span><span class="sxs-lookup"><span data-stu-id="bad3c-107">The second is the Windows-specific XR.WSA.Input APIs, which offer richer data specifically for motion controllers and HoloLens hands.</span></span>

## <a name="general-inputgetbuttongetaxis-apis"></a><span data-ttu-id="bad3c-108">General GetButton/GetAxis Api</span><span class="sxs-lookup"><span data-stu-id="bad3c-108">General Input.GetButton/GetAxis APIs</span></span>

<span data-ttu-id="bad3c-109">Unity 目前使用其常规输入. GetButton/GetAxis Api 来公开 [OCULUS SDK](https://docs.unity3d.com/Manual/OculusControllers.html) 和 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)的输入。</span><span class="sxs-lookup"><span data-stu-id="bad3c-109">Unity currently uses its general Input.GetButton/Input.GetAxis APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) and [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html).</span></span> <span data-ttu-id="bad3c-110">如果你的应用程序已在使用这些 Api 进行输入，则 GetButton/GetAxis Api 是支持 Windows Mixed Reality 中的运动控制器的最简单路径。</span><span class="sxs-lookup"><span data-stu-id="bad3c-110">If your apps are already using these APIs for input, the Input.GetButton/Input.GetAxis APIs are the easiest paths for supporting motion controllers in Windows Mixed Reality.</span></span> <span data-ttu-id="bad3c-111">只需在输入管理器中重新映射按钮和轴。</span><span class="sxs-lookup"><span data-stu-id="bad3c-111">You'll only need to remap buttons and axes in the Input Manager.</span></span>

<span data-ttu-id="bad3c-112">有关详细信息，请参阅 [Unity 按钮/轴映射表](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 和 [常见 Unity api 的概述](../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。</span><span class="sxs-lookup"><span data-stu-id="bad3c-112">For more information, see the [Unity button/axis mapping table](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) and the [overview of the common Unity APIs](../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).</span></span>

## <a name="windows-specific-xrwsainput-apis"></a><span data-ttu-id="bad3c-113">Windows 特定的 XR。WSA.输入 Api</span><span class="sxs-lookup"><span data-stu-id="bad3c-113">Windows-specific XR.WSA.Input APIs</span></span>

<span data-ttu-id="bad3c-114">如果你的应用程序已为每个平台构建自定义输入逻辑，则可以在 **UnityEngine** 命名空间中使用特定于 Windows 的空间输入 api。</span><span class="sxs-lookup"><span data-stu-id="bad3c-114">If your app already builds custom input logic for each platform, you can use the Windows-specific spatial input APIs in the **UnityEngine.XR.WSA.Input** namespace.</span></span> <span data-ttu-id="bad3c-115">在这里，你可以访问其他信息（如位置准确性或源类型），从而让你可以在 HoloLens 上区分双手和控制器。</span><span class="sxs-lookup"><span data-stu-id="bad3c-115">From there, you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart on HoloLens.</span></span>

<span data-ttu-id="bad3c-116">有关详细信息，请参阅 [UNITYENGINE XR api 概述](../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。</span><span class="sxs-lookup"><span data-stu-id="bad3c-116">For more information, see the [overview of the UnityEngine.XR.WSA.Input APIs](../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="bad3c-117">手柄姿势与指针姿势</span><span class="sxs-lookup"><span data-stu-id="bad3c-117">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="bad3c-118">Windows Mixed Reality 支持采用不同外形规格的运动控制器。</span><span class="sxs-lookup"><span data-stu-id="bad3c-118">Windows Mixed Reality supports motion controllers in different form factors.</span></span> <span data-ttu-id="bad3c-119">每个控制器的设计不同于用户的位置与应用在呈现控制器时使用的自然 "转发" 方向之间的关系。</span><span class="sxs-lookup"><span data-stu-id="bad3c-119">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="bad3c-120">为了更好地表示这些控制器，可以针对每个交互源调查以下两种类型：</span><span class="sxs-lookup"><span data-stu-id="bad3c-120">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>

* <span data-ttu-id="bad3c-121">**手柄姿势**，表示由 HoloLens 检测到的掌托的位置，或包含运动控制器的掌托的位置。</span><span class="sxs-lookup"><span data-stu-id="bad3c-121">The **grip pose**, which represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="bad3c-122">在沉浸式耳机上，这种姿势最适合用于呈现 **用户的手** 或 **持有用户的对象**，例如剑或机枪。</span><span class="sxs-lookup"><span data-stu-id="bad3c-122">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="bad3c-123">**手柄位置**：在固定控制器时，掌上质心，向左或向右调整以使其在手柄内居中。</span><span class="sxs-lookup"><span data-stu-id="bad3c-123">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="bad3c-124">**手柄方向的右轴**：当你完全打开手形成一个平面的5指形姿势时，与你的掌上的光线 (从右手掌向后) </span><span class="sxs-lookup"><span data-stu-id="bad3c-124">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="bad3c-125">**抓握方向的前向轴**：当部分合上时，就如同按住控制器一样，通过由您的非拇指指的电子管来指向 "转发" 的射线。</span><span class="sxs-lookup"><span data-stu-id="bad3c-125">The **grip orientation's Forward axis**: When you close your hand partially, as if holding the controller, the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="bad3c-126">**手柄方向的上轴**：向右和向后定义隐含的上轴。</span><span class="sxs-lookup"><span data-stu-id="bad3c-126">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="bad3c-127">可以通过 Unity 的跨供应商输入 API (XR 来访问抓握姿势 **[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/旋转**) 或通过特定于 Windows 的 API (**sourcePose TryGetPosition/旋转**，) 请求手柄姿势。</span><span class="sxs-lookup"><span data-stu-id="bad3c-127">You can access the grip pose through either Unity's cross-vendor input API (**[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation**) or through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Grip pose).</span></span>
* <span data-ttu-id="bad3c-128">**指针姿势**，表示控制器的末端。</span><span class="sxs-lookup"><span data-stu-id="bad3c-128">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="bad3c-129">当你呈现控制器模型本身时，最好使用这种 raycast 来指示 **UI** 。</span><span class="sxs-lookup"><span data-stu-id="bad3c-129">This pose is best used to raycast when **pointing at UI** when you're rendering the controller model itself.</span></span>
    * <span data-ttu-id="bad3c-130">目前，指针姿势仅可通过特定于 Windows 的 API (**TryGetPosition/旋转**，请求指针) 。</span><span class="sxs-lookup"><span data-stu-id="bad3c-130">Currently, the pointer pose is available only through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Pointer pose).</span></span>

<span data-ttu-id="bad3c-131">这些姿势坐标全部用 Unity 世界坐标表示。</span><span class="sxs-lookup"><span data-stu-id="bad3c-131">These pose coordinates are all expressed in Unity world coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="bad3c-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bad3c-132">See also</span></span>
* <span data-ttu-id="bad3c-133">[运动控制器]().。。/../design/motion-controllers.md) </span><span class="sxs-lookup"><span data-stu-id="bad3c-133">[Motion controllers]()../../design/motion-controllers.md)</span></span>
* [<span data-ttu-id="bad3c-134">Unity 中的运动控制器</span><span class="sxs-lookup"><span data-stu-id="bad3c-134">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="bad3c-135">UnityEngine. XR</span><span class="sxs-lookup"><span data-stu-id="bad3c-135">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="bad3c-136">UnityEngine. XR. InputTracking</span><span class="sxs-lookup"><span data-stu-id="bad3c-136">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="bad3c-137">移植指南</span><span class="sxs-lookup"><span data-stu-id="bad3c-137">Porting guides</span></span>](porting-guides.md)
