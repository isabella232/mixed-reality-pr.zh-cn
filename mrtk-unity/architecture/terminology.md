---
title: 术语
description: MRTK 中的不同输入系统术语。
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 输入，
ms.openlocfilehash: 33f423fba286e9e85e6d0bedac82bff0b7aae81f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121455"
---
# <a name="input-system"></a><span data-ttu-id="92e64-104">输入系统</span><span class="sxs-lookup"><span data-stu-id="92e64-104">Input system</span></span>

<span data-ttu-id="92e64-105">输入系统是 MRTK 提供的所有功能中最大的系统之一。</span><span class="sxs-lookup"><span data-stu-id="92e64-105">The input system is one of the largest systems out of all features offered by the MRTK.</span></span>
<span data-ttu-id="92e64-106">工具包中基于它构建的许多内容 (指针、焦点、预制件) 。</span><span class="sxs-lookup"><span data-stu-id="92e64-106">So many things within the toolkit build on top of it (pointers, focus, prefabs).</span></span> <span data-ttu-id="92e64-107">输入系统内的代码允许自然交互，例如跨平台抓取和旋转。</span><span class="sxs-lookup"><span data-stu-id="92e64-107">The code within the input system is what allows for natural interactions like grab and rotate across platforms.</span></span>

<span data-ttu-id="92e64-108">输入系统有一些值得定义的术语：</span><span class="sxs-lookup"><span data-stu-id="92e64-108">The input system has some of its own terminology that are worth defining:</span></span>

- <span data-ttu-id="92e64-109">**数据提供程序**</span><span class="sxs-lookup"><span data-stu-id="92e64-109">**Data providers**</span></span>

    <span data-ttu-id="92e64-110">输入配置文件中的输入设置具有对称为数据访问提供程序的实体的引用 - 另一个描述这些实体的单词是设备管理器。</span><span class="sxs-lookup"><span data-stu-id="92e64-110">The input settings in the input profile have references to entities known as data providers - another word that describes these are device managers.</span></span> <span data-ttu-id="92e64-111">这些组件的工作是通过使用特定的基础系统进行连接来扩展 MRTK 输入系统。</span><span class="sxs-lookup"><span data-stu-id="92e64-111">These are components whose job is to extend the MRTK input system by interfacing with a specific underlying system.</span></span> <span data-ttu-id="92e64-112">提供程序的一个示例是 Windows Mixed Reality 提供程序，其作业是与基础 Windows Mixed Reality API 对话，然后将这些 API 的数据转换为下面特定于 MRTK 的输入概念。</span><span class="sxs-lookup"><span data-stu-id="92e64-112">An example of a provider is the Windows Mixed Reality provider, whose job it is to talk with the underlying Windows Mixed Reality APIs and then translate the data from those APIs into MRTK-specific input concepts below.</span></span> <span data-ttu-id="92e64-113">另一个示例是 OpenVR 提供程序 (，其作业是与 Unity 抽象版本的 OpenVR API 对话，然后将该数据转换为 MRTK 输入概念) 。</span><span class="sxs-lookup"><span data-stu-id="92e64-113">Another example would be the OpenVR provider (whose job it is to talk to Unity-abstracted version of OpenVR APIs and then translate that data into MRTK input concepts).</span></span>

- <span data-ttu-id="92e64-114">**控制器**</span><span class="sxs-lookup"><span data-stu-id="92e64-114">**Controller**</span></span>

    <span data-ttu-id="92e64-115">物理控制器的表示形式 (无论它是 6 度自由控制器、具有手势支持的 HoloLens 1 样式手、完全表达的手势、闰运动控制器等) 。</span><span class="sxs-lookup"><span data-stu-id="92e64-115">A representation of a physical controller (whether it's a 6-degree-of-freedom controller, a HoloLens 1-style hand with gesture support, a fully articulated hand, a leap motion controller, etc.).</span></span> <span data-ttu-id="92e64-116">控制器由设备管理器生成 (，即 WMR 设备管理器将生成一个控制器，并管理其生存期，当它看到一个明确手) 。</span><span class="sxs-lookup"><span data-stu-id="92e64-116">Controllers are spawned by device managers (i.e. the WMR device manager will spawn a controller and manage its lifetime when it sees an articulated hand coming into existence).</span></span>

- <span data-ttu-id="92e64-117">**指针**</span><span class="sxs-lookup"><span data-stu-id="92e64-117">**Pointer**</span></span>

    <span data-ttu-id="92e64-118">控制器使用指针与游戏对象交互。</span><span class="sxs-lookup"><span data-stu-id="92e64-118">Controllers use pointers to interact with game objects.</span></span> <span data-ttu-id="92e64-119">例如，近交互指针负责检测手部（ (控制器）何时) 将自身播发为支持"近交互"的对象。</span><span class="sxs-lookup"><span data-stu-id="92e64-119">For example, the near interaction pointer is responsible for detecting when the hand (which is a controller) is close to objects that advertise themselves as supporting 'near interaction'.</span></span> <span data-ttu-id="92e64-120">指针的其他示例包括远程传送或远距指针 (即 shell 手部射线指针) ，它使用远距光线广播来与用户发送的长于手部长度的内容交互。</span><span class="sxs-lookup"><span data-stu-id="92e64-120">Other examples for pointers are teleportation or far pointers (i.e. the shell hand ray pointer) that use far raycasts to engage with content that is longer than arms-length from the user.</span></span>

    <span data-ttu-id="92e64-121">指针由设备管理器创建，然后附加到输入源。</span><span class="sxs-lookup"><span data-stu-id="92e64-121">Pointers are created by the device manager and then attached to an input source.</span></span> <span data-ttu-id="92e64-122">若要获取控制器的所有指针，请执行以下操作： `controller.InputSource.Pointers`</span><span class="sxs-lookup"><span data-stu-id="92e64-122">To get all of the pointers for a controller, do: `controller.InputSource.Pointers`</span></span>

    <span data-ttu-id="92e64-123">请注意，控制器可以同时与许多不同的指针关联。</span><span class="sxs-lookup"><span data-stu-id="92e64-123">Note that a controller can be associated with many different pointers at the same time.</span></span> <span data-ttu-id="92e64-124">为了确保这不会进入混沌状态，有一个指针转换器控制允许哪些指针处于活动状态 (例如，当检测到近交互时，该) 。</span><span class="sxs-lookup"><span data-stu-id="92e64-124">In order to ensure that this doesn't devolve into chaos, there is a pointer mediator which controls which pointers are allowed to be active (for example, the mediator will disable far interaction pointers when near interaction is detected).</span></span>

- <span data-ttu-id="92e64-125">**重点**</span><span class="sxs-lookup"><span data-stu-id="92e64-125">**Focus**</span></span>

    <span data-ttu-id="92e64-126">指针事件将发送到焦点 **中的对象**。</span><span class="sxs-lookup"><span data-stu-id="92e64-126">Pointer events are sent to objects in **focus**.</span></span> <span data-ttu-id="92e64-127">焦点选择因指针类型而异;手部射线指针将使用光线广播，而手部指针将使用球体广播。</span><span class="sxs-lookup"><span data-stu-id="92e64-127">Focus selection will vary by pointer type; a hand ray pointer will use raycasts, while a poke pointer will use spherecasts.</span></span> <span data-ttu-id="92e64-128">对象必须实现 IMixedRealityFocusHandler 以接收焦点。</span><span class="sxs-lookup"><span data-stu-id="92e64-128">An object must implement IMixedRealityFocusHandler to receive focus.</span></span> <span data-ttu-id="92e64-129">可以全局注册对象以接收未筛选的指针事件，但不建议此方法。</span><span class="sxs-lookup"><span data-stu-id="92e64-129">It's possible to globally register an object to receive unfiltered pointer events, but this approach is not recommended.</span></span>

    <span data-ttu-id="92e64-130">更新焦点对象的组件是 [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)</span><span class="sxs-lookup"><span data-stu-id="92e64-130">The component that updates which objects are in focus is the [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)</span></span>

- <span data-ttu-id="92e64-131">**游标**</span><span class="sxs-lookup"><span data-stu-id="92e64-131">**Cursor**</span></span>

    <span data-ttu-id="92e64-132">与指针关联的实体，该指针围绕指针交互提供其他视觉提示。</span><span class="sxs-lookup"><span data-stu-id="92e64-132">An entity associated with a pointer that gives additional visual cues around pointer interaction.</span></span> <span data-ttu-id="92e64-133">例如，FingerCursor 将围绕手指呈现一个环，并且当手指接近"近可交互"对象时，可能会旋转该环。</span><span class="sxs-lookup"><span data-stu-id="92e64-133">For example, the FingerCursor will render a ring around your finger and may rotate that ring when your finger is close to 'near interactable' objects.</span></span> <span data-ttu-id="92e64-134">指针可以一次与单个游标相关联。</span><span class="sxs-lookup"><span data-stu-id="92e64-134">A pointer can be associated with a single cursor at time.</span></span>

- <span data-ttu-id="92e64-135">**交互和操作**</span><span class="sxs-lookup"><span data-stu-id="92e64-135">**Interaction and Manipulation**</span></span>

    <span data-ttu-id="92e64-136">可以使用交互或操作脚本标记对象。</span><span class="sxs-lookup"><span data-stu-id="92e64-136">Objects can be tagged with an interaction or manipulation script.</span></span> <span data-ttu-id="92e64-137">这可以通过 或 [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 类似 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。</span><span class="sxs-lookup"><span data-stu-id="92e64-137">This may be via a [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable), or something like [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)/[`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

    <span data-ttu-id="92e64-138">例如，NearInteractionGrabbable 和 NearInteractionTouchable 允许某些指针 (尤其是近) 交互指针，以知道可以聚焦哪些对象。</span><span class="sxs-lookup"><span data-stu-id="92e64-138">For example, NearInteractionGrabbable and NearInteractionTouchable allow for certain pointers (especially   near interaction pointers) to know which objects can be focused on.</span></span>

    <span data-ttu-id="92e64-139">可交互和 ManipulationHandler 是侦听指针事件以修改 UI 视觉对象或移动/缩放/旋转游戏对象的组件示例。</span><span class="sxs-lookup"><span data-stu-id="92e64-139">Interactable and ManipulationHandler are examples of components that listen to pointer events to modify   UI visuals or move/scale/rotate game objects.</span></span>

<span data-ttu-id="92e64-140">下图从 MRTK 输入堆栈 (从下到) 捕获高级生成：</span><span class="sxs-lookup"><span data-stu-id="92e64-140">The image below captures the high level build up (from bottom up) of the MRTK input stack:</span></span>

![输入系统关系图](../features/images/input/MRTK_InputSystem.png)
