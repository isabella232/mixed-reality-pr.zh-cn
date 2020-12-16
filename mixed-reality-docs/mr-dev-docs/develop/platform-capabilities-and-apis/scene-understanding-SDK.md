---
title: 场景理解 SDK
description: 场景理解 SDK 的编程指南
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: 场景了解，空间映射，Windows Mixed Reality，Unity
ms.openlocfilehash: 1ec29d09ab52abae9a9111a6441523c8aa7720f7
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530344"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="0cb0f-104">场景理解 SDK 概述</span><span class="sxs-lookup"><span data-stu-id="0cb0f-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="0cb0f-105">场景理解转换混合现实设备捕获的非结构化环境传感器数据，并将其转换为强大的抽象表示形式。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="0cb0f-106">SDK 充当应用程序和场景了解运行时之间的通信层。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="0cb0f-107">它旨在模拟现有的标准构造，如3D 表示形式的三维场景图形，以及2D 应用程序的2D 矩形和面板。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="0cb0f-108">尽管构造场景了解模拟会映射到具体框架，但通常情况下，SceneUnderstanding 是框架不可知的，这使得与它交互的可变框架之间具有互操作性。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="0cb0f-109">随着场景理解演变，SDK 的作用是确保新的表示形式和功能继续在统一框架内公开。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="0cb0f-110">在本文档中，我们将首先介绍高级概念，这些概念将帮助你熟悉开发环境/用法，并为特定的类和构造提供更详细的文档。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="0cb0f-111">在何处获取 SDK？</span><span class="sxs-lookup"><span data-stu-id="0cb0f-111">Where do I get the SDK?</span></span>

<span data-ttu-id="0cb0f-112">SceneUnderstanding SDK 可通过 NuGet 下载。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="0cb0f-113">SceneUnderstanding SDK</span><span class="sxs-lookup"><span data-stu-id="0cb0f-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="0cb0f-114">**注意：** 最新版本依赖于预览包，你需要启用预发布包才能查看。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-114">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="0cb0f-115">对于版本 0.5.2022-rc 和更高版本，场景理解支持适用于 c # 和 c + + 的语言投影，使应用程序可以为 Win32 或 UWP 平台开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-115">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="0cb0f-116">在此版本中，SceneUnderstanding 支持 unity 的编辑器中的支持，该支持仅用于与 HoloLens2 通信。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="0cb0f-117">SceneUnderstanding 需要 Windows SDK 版本18362或更高版本。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="0cb0f-118">如果你使用的是 Unity 项目中的 SDK，则使用 [NuGet For Unity](https://github.com/GlitchEnzo/NuGetForUnity) 将包安装到你的项目中。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-118">If you're using the SDK in a Unity project, use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="0cb0f-119">概念概述</span><span class="sxs-lookup"><span data-stu-id="0cb0f-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="0cb0f-120">场景</span><span class="sxs-lookup"><span data-stu-id="0cb0f-120">The Scene</span></span>

<span data-ttu-id="0cb0f-121">混合现实设备会不断集成有关它在你的环境中看到的内容的信息。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="0cb0f-122">场景了解漏斗图所有这些数据源，并生成一个统一的抽象抽象。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="0cb0f-123">场景理解会生成场景，这些场景是 [SceneObjects](scene-understanding-SDK.md#sceneobjects) 的组成部分，表示单个事物的实例 (，如墙壁/天花板/楼层。 ) 场景对象本身是 [SceneComponents 的组合，表示构成此 SceneObject 的更精细的部分。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-123">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="0cb0f-124">组件的示例包括四边形和网格，但将来可能表示边界框、冲突网格、元数据等。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="0cb0f-125">将原始传感器数据转换为场景的过程是一项可能消耗大量资源的操作， (~ 10x10m) 到几分钟用于大空间 (~ 50x50m) ，因此没有应用程序请求的设备不会进行计算。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="0cb0f-126">相反，应用程序会按需触发场景生成。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="0cb0f-127">SceneObserver 类具有可计算或反序列化场景的静态方法，然后可以使用该场景进行枚举/交互。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="0cb0f-128">"计算" 操作按需执行并在 CPU 上执行，但在单独的进程中 (混合现实驱动程序) 。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="0cb0f-129">但是，虽然我们在另一个进程中进行计算，但生成的场景数据会存储在应用程序的场景对象中并进行维护。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="0cb0f-130">下面的关系图演示了此流程，并显示了两个应用程序与场景理解运行时交互的示例。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![流程图](images/SU-ProcessFlow.png)

<span data-ttu-id="0cb0f-132">左侧是混合现实运行时的关系图，它在自己的进程中始终处于打开和运行状态。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-132">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="0cb0f-133">此运行时负责执行设备跟踪、空间映射和其他操作，场景了解使用它来理解和解决世界的相关原因。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="0cb0f-134">在关系图的右侧，我们将显示两个使用场景理解的理论应用程序。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="0cb0f-135">第一个使用 MRTK 的应用程序接口，该应用程序在内部使用场景理解 SDK，第二个应用程序计算并使用两个单独的场景实例。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-135">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="0cb0f-136">此关系图中的所有三个场景都生成不同场景的不同实例，驱动程序无法跟踪在一个场景中的应用程序和场景对象之间共享的全局状态。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-136">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="0cb0f-137">场景理解确实提供了一种在一段时间内进行跟踪的机制，但这是使用 SDK 实现的。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="0cb0f-138">跟踪代码已在应用程序的进程中的 SDK 中运行。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-138">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="0cb0f-139">由于每个场景会将其数据存储在应用程序的内存空间中，因此，你可以假定场景对象的所有功能或它的内部数据始终在应用程序的进程中执行。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-139">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="0cb0f-140">Layout</span><span class="sxs-lookup"><span data-stu-id="0cb0f-140">Layout</span></span>

<span data-ttu-id="0cb0f-141">若要使用场景理解，了解并了解运行时如何以逻辑方式和物理方式表示组件可能会很有价值。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-141">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="0cb0f-142">场景表示具有特定布局的数据，其中选择了简单的布局，同时保持基础结构 pliable，而无需进行重大修改。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-142">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="0cb0f-143">场景将通过以下方式实现此目标：将所有组件存储在简单列表中) 的所有场景对象 (构建基块，并通过引用（其中特定组件引用其他组件）定义层次结构和组合。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-143">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="0cb0f-144">下面的示例展示了结构的平面和逻辑形式。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-144">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="0cb0f-145">逻辑布局</span><span class="sxs-lookup"><span data-stu-id="0cb0f-145">Logical Layout</span></span></th><th><span data-ttu-id="0cb0f-146">物理布局</span><span class="sxs-lookup"><span data-stu-id="0cb0f-146">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="0cb0f-147">场景</span><span class="sxs-lookup"><span data-stu-id="0cb0f-147">Scene</span></span>
  <ul>
  <li><span data-ttu-id="0cb0f-148">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="0cb0f-148">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="0cb0f-149">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="0cb0f-149">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="0cb0f-150">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="0cb0f-150">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="0cb0f-151">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="0cb0f-151">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="0cb0f-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="0cb0f-152">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="0cb0f-153">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="0cb0f-153">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="0cb0f-154">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="0cb0f-154">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="0cb0f-155">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="0cb0f-155">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="0cb0f-156">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="0cb0f-156">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="0cb0f-157">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="0cb0f-157">SceneObject_1</span></span></li>
  <li><span data-ttu-id="0cb0f-158">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="0cb0f-158">SceneObject_2</span></span></li>
  <li><span data-ttu-id="0cb0f-159">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="0cb0f-159">SceneObject_3</span></span></li>
  <li><span data-ttu-id="0cb0f-160">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="0cb0f-160">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="0cb0f-161">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="0cb0f-161">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="0cb0f-162">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="0cb0f-162">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="0cb0f-163">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="0cb0f-163">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="0cb0f-164">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="0cb0f-164">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="0cb0f-165">此图重点介绍场景的物理布局和逻辑布局之间的差异。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-165">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="0cb0f-166">在左侧，我们将看到您的应用程序在枚举场景时看到的数据的分层布局。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-166">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="0cb0f-167">在右侧，我们看到场景由12个不同的组件组成，如有必要，可单独访问。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-167">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="0cb0f-168">处理新场景时，我们希望应用程序以逻辑方式对此层次结构进行遍历，但当在场景更新之间进行跟踪时，某些应用程序可能只对在两个场景之间共享的特定组件感兴趣。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-168">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="0cb0f-169">API 概述</span><span class="sxs-lookup"><span data-stu-id="0cb0f-169">API overview</span></span>

<span data-ttu-id="0cb0f-170">以下部分提供对场景理解中的构造的高级概述。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-170">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="0cb0f-171">阅读本部分后，你将了解如何表达场景以及各种组件的用途/用途。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-171">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="0cb0f-172">下一节将提供具体的代码示例以及在本概述中 glossed 的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-172">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="0cb0f-173">下面所述的所有类型都驻留在 `Microsoft.MixedReality.SceneUnderstanding` 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-173">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="0cb0f-174">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="0cb0f-174">SceneComponents</span></span>

<span data-ttu-id="0cb0f-175">现在，您已经了解了幕后的逻辑布局，接下来可以展示 SceneComponents 的概念，以及如何使用它们来组成层次结构。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-175">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="0cb0f-176">SceneComponents 是 SceneUnderstanding 中最精细的分解，表示单个核心事物，例如，一个网格或四个边界框。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-176">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="0cb0f-177">SceneComponents 是可以独立更新并可由其他 SceneComponents 引用的项，因此，它们具有一个唯一 ID 的单一全局属性，该属性允许此类跟踪/引用机制。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-177">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="0cb0f-178">Id 用于场景层次结构的逻辑组合以及对象持久性 (相对于另一场景更新一个场景的操作。 ) </span><span class="sxs-lookup"><span data-stu-id="0cb0f-178">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="0cb0f-179">如果要将每个新计算的场景视为不同的场景，只需枚举其中的所有数据，Id 就会对您很有透明度。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-179">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="0cb0f-180">但是，如果你打算跟踪多个更新上的组件，则将使用 Id 在场景对象之间建立索引和查找 SceneComponents。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-180">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="0cb0f-181">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="0cb0f-181">SceneObjects</span></span>

<span data-ttu-id="0cb0f-182">SceneObject 是一个 SceneComponent，它表示 "事物" 的实例，例如墙壁、楼层、天花板等。用其 Kind 属性表示。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-182">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="0cb0f-183">SceneObjects 是几何，因此具有在空间中表示其位置的函数和属性，但不包含任何几何或逻辑结构。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-183">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="0cb0f-184">相反，SceneObjects 引用其他 SceneComponents，特别是 SceneQuads 和 SceneMeshes，它们提供系统支持的各种表示形式。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-184">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="0cb0f-185">计算新场景时，应用程序很可能会枚举场景的 SceneObjects，以处理其感兴趣的内容。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-185">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="0cb0f-186">SceneObjects 可以包含以下任一项：</span><span class="sxs-lookup"><span data-stu-id="0cb0f-186">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="0cb0f-187">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="0cb0f-187">SceneObjectKind</span></span></th> <th><span data-ttu-id="0cb0f-188">说明</span><span class="sxs-lookup"><span data-stu-id="0cb0f-188">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="0cb0f-189">背景</span><span class="sxs-lookup"><span data-stu-id="0cb0f-189">Background</span></span></td><td><span data-ttu-id="0cb0f-190">已知 SceneObject <b>不</b> 是其他已识别的场景对象类型之一。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-190">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="0cb0f-191">此类不应与 Unknown 混淆，其中背景已知不是墙壁/楼层/天花板，等等 .。。虽然未知还未分类。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-191">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="0cb0f-192">壁</span><span class="sxs-lookup"><span data-stu-id="0cb0f-192">Wall</span></span></td><td><span data-ttu-id="0cb0f-193">物理墙。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-193">A physical wall.</span></span> <span data-ttu-id="0cb0f-194">墙壁被认为是可移动的环境结构。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-194">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="0cb0f-195">Floor</span><span class="sxs-lookup"><span data-stu-id="0cb0f-195">Floor</span></span></td><td><span data-ttu-id="0cb0f-196">楼层是可以进行审核的任何表面。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-196">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="0cb0f-197">注意：楼梯不是楼层。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-197">Note: stairs aren't floors.</span></span> <span data-ttu-id="0cb0f-198">另请注意，该楼层假设有任何不可表面，因此没有明确的假设。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-198">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="0cb0f-199">多层结构，斜坡等 .。。应将所有分类为楼层。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-199">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="0cb0f-200">Ceiling</span><span class="sxs-lookup"><span data-stu-id="0cb0f-200">Ceiling</span></span></td><td><span data-ttu-id="0cb0f-201">房间的上部面。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-201">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="0cb0f-202">平台</span><span class="sxs-lookup"><span data-stu-id="0cb0f-202">Platform</span></span></td><td><span data-ttu-id="0cb0f-203">一个大平面，可以在其上放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-203">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="0cb0f-204">它们倾向于表示表、countertops 和其他大型水平曲面。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-204">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="0cb0f-205">World</span><span class="sxs-lookup"><span data-stu-id="0cb0f-205">World</span></span></td><td><span data-ttu-id="0cb0f-206">标记不可知的几何数据的保留标签。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-206">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="0cb0f-207">通过设置 EnableWorldMesh 更新标志生成的网格将归为 "世界"。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-207">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="0cb0f-208">Unknown</span><span class="sxs-lookup"><span data-stu-id="0cb0f-208">Unknown</span></span></td><td><span data-ttu-id="0cb0f-209">尚未对此场景对象进行分类并为其分配一种类型。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-209">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="0cb0f-210">这不应与背景混淆，因为此对象可能是任何内容，而系统刚刚没有提供足够强大的分类。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-210">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="0cb0f-211">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="0cb0f-211">SceneMesh</span></span>

<span data-ttu-id="0cb0f-212">SceneMesh 是一种 SceneComponent，它使用三角形列表来模拟任意几何对象的几何。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-212">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="0cb0f-213">SceneMeshes 用于多个不同的上下文中，它们可以表示 watertight 单元结构的组件或作为 WorldMesh，这表示与场景关联的未绑定空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-213">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="0cb0f-214">每个网格提供的索引和顶点数据使用与用于在所有新式渲染 Api 中呈现三角形网格的 [顶点和索引缓冲区](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) 相同的熟悉布局。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-214">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="0cb0f-215">在场景理解中，网格使用32位索引，可能需要分解为某些呈现引擎的块。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-215">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="0cb0f-216">缠绕顺序和坐标系统</span><span class="sxs-lookup"><span data-stu-id="0cb0f-216">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="0cb0f-217">场景理解生成的所有网格都应该使用顺时针缠绕顺序返回 Right-Handed 坐标系中的网格。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-217">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="0cb0f-218">注意：版本之前的操作系统版本。191105可能会有一个已知 bug，其中 "World" 网格以 Counter-Clockwise 缠绕顺序返回，后者随后已修复。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-218">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="0cb0f-219">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="0cb0f-219">SceneQuad</span></span>

<span data-ttu-id="0cb0f-220">SceneQuad 是一个 SceneComponent，它表示占据三维世界的2d 面。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-220">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="0cb0f-221">SceneQuads 可以与 ARKit ARPlaneAnchor 或 ARCore 平面相似，但它们提供了更高级别的功能，如要由平面应用程序使用的2d 画布或更高的 UX。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-221">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="0cb0f-222">为四边形提供了2D 特定的 Api，使放置和布局简单易用，并开发 (但使用四边形渲染) 应感觉比使用3d 网格更类似于2d 画布。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-222">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="0cb0f-223">SceneQuad 形状</span><span class="sxs-lookup"><span data-stu-id="0cb0f-223">SceneQuad shape</span></span>

<span data-ttu-id="0cb0f-224">SceneQuads 在2d 中定义边界矩形图面。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-224">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="0cb0f-225">但是，SceneQuads 表示具有任意和可能复杂的形状的图面 (例如，环形形状的表。 ) 表示四个部分的复杂形状，可以使用 GetSurfaceMask API 将图面上的形状呈现到提供的图像缓冲区。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-225">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="0cb0f-226">如果具有四部分的 SceneObject 还具有网格，则网格三角形应等效于此呈现的图像，它们都表示图面的实面（以2d 或3d 坐标表示）。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-226">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="0cb0f-227">场景理解 SDK 详细信息和参考</span><span class="sxs-lookup"><span data-stu-id="0cb0f-227">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="0cb0f-228">以下部分将帮助你熟悉 SceneUnderstanding 的基础知识。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="0cb0f-229">本部分应为你提供基础知识，此时你应该具有足够的上下文来浏览示例应用程序，以了解如何整体使用 SceneUnderstanding。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="0cb0f-230">初始化</span><span class="sxs-lookup"><span data-stu-id="0cb0f-230">Initialization</span></span>

<span data-ttu-id="0cb0f-231">使用 SceneUnderstanding 的第一步是让应用程序获取对场景对象的引用。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="0cb0f-232">可以通过以下两种方式之一完成此操作：可以通过驱动程序计算场景，也可以反序列化过去计算的现有场景。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="0cb0f-233">后者可用于在开发期间使用 SceneUnderstanding，在这种情况下，应用程序和体验可以在没有混合现实设备的情况下快速建立原型。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="0cb0f-234">使用 SceneObserver 计算场景。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="0cb0f-235">在创建场景之前，应用程序应查询你的设备以确保它支持 SceneUnderstanding，并请求用户访问以获取 SceneUnderstanding 所需的信息。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="0cb0f-236">如果未调用 RequestAccessAsync ( # A1，则计算新场景将会失败。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="0cb0f-237">接下来，我们将计算一个以混合现实耳机为根的新场景，其半径为10米。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="0cb0f-238">从数据的初始化 (也称为。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="0cb0f-239">PC 路径) </span><span class="sxs-lookup"><span data-stu-id="0cb0f-239">the PC Path)</span></span>

<span data-ttu-id="0cb0f-240">尽管可以计算用于直接使用的场景，但也可以使用序列化形式计算，以便以后使用。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="0cb0f-241">此功能经过证明可用于开发，因为它允许开发人员在无需设备的情况下使用和测试场景理解。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="0cb0f-242">序列化场景的操作与计算场景几乎完全相同，数据将返回到应用程序，而不是由 SDK 在本地反序列化。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="0cb0f-243">然后，你可以自行反序列化它或将其保存以供将来使用。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-243">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="0cb0f-244">SceneObject 枚举</span><span class="sxs-lookup"><span data-stu-id="0cb0f-244">SceneObject Enumeration</span></span>

<span data-ttu-id="0cb0f-245">现在，你的应用程序有场景，你的应用程序将查看和与 SceneObjects 交互。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="0cb0f-246">这可以通过访问 **SceneObjects** 属性来完成：</span><span class="sxs-lookup"><span data-stu-id="0cb0f-246">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="0cb0f-247">组件更新和 refinding 组件</span><span class="sxs-lookup"><span data-stu-id="0cb0f-247">Component update and refinding components</span></span>

<span data-ttu-id="0cb0f-248">还有另一个函数，用于在场景（称为 \**_FindComponent_* _）中检索组件。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-248">There's another function that retrieves components in the Scene called \**_FindComponent_* _.</span></span> <span data-ttu-id="0cb0f-249">当更新跟踪对象并在以后的场景中查找这些对象时，此函数很有用。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="0cb0f-250">下面的代码将计算一个相对于以前场景的新场景，然后在新场景中查找楼层。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="0cb0f-251">从场景对象访问网格和四边形</span><span class="sxs-lookup"><span data-stu-id="0cb0f-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="0cb0f-252">找到 SceneObjects 后，你的应用程序很可能需要访问由组成的四边形/网格中包含的数据。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="0cb0f-253">可以通过 _\*_四边形_\*_ 和 _\*_网格_\*_ 属性访问此数据。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-253">This data is accessed with the _*_Quads_*_ and _*_Meshes_*_ properties.</span></span> <span data-ttu-id="0cb0f-254">下面的代码将枚举地面对象的所有四边形和网格。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="0cb0f-255">请注意，它是相对于场景原点的转换的 SceneObject。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="0cb0f-256">这是因为，SceneObject 表示 "事物" 的实例，在空间中可定位，四边形和网格表示相对于其父级转换的几何图形。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="0cb0f-257">单独的 SceneObjects 可以引用相同的 SceneMesh/SceneQuad SceneComponents，也可能是 SceneObject 有多个 SceneMesh/SceneQuad。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="0cb0f-258">处理转换</span><span class="sxs-lookup"><span data-stu-id="0cb0f-258">Dealing with Transforms</span></span>

<span data-ttu-id="0cb0f-259">在处理转换时，场景理解已精心尝试与传统的三维场景表示。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="0cb0f-260">因此，每个场景都局限于一个坐标系统，这与大多数常见的3D 环境表示形式非常类似。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="0cb0f-261">每个 SceneObjects 都提供它们相对于该坐标系统的位置。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="0cb0f-262">如果你的应用程序正在处理的场景会延伸到单个源所提供的限制，则可以将 SceneObjects 定位到 SpatialAnchors，或生成多个场景并将它们合并在一起，但为了简单起见，我们假定 watertight 场景位于其自身的源中，而该已由由场景 OriginSpatialGraphNodeId 定义的一个本地化。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="0cb0f-263">例如，以下 Unity 代码演示了如何使用 Windows 感知和 Unity Api 来协调坐标系。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="0cb0f-264">有关获取与 Unity 世界原点相对应的 SpatialCoordinateSystem 的详细信息，请参阅 [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) 和 [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) ，了解有关 Windows 感知 api 的详细信息，以及 [Unity 中混合现实本机对象](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-264">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

<span data-ttu-id="0cb0f-265">每个 `SceneObject` 都有一个转换，然后将其应用到该对象。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="0cb0f-266">在 Unity 中，我们转换为右手坐标坐标，并按如下所示分配本地转换：</span><span class="sxs-lookup"><span data-stu-id="0cb0f-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a><span data-ttu-id="0cb0f-267">十字</span><span class="sxs-lookup"><span data-stu-id="0cb0f-267">Quad</span></span>

<span data-ttu-id="0cb0f-268">四边形旨在帮助2D 布局方案，并应被视为2D 画布 UX 元素的扩展。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="0cb0f-269">尽管四边形是 SceneObjects 的组件并且可以在3D 中呈现，但四个 Api 本身假设四边形是2D 结构。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="0cb0f-270">它们提供了信息（如区、形状），并提供了用于放置的 Api。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="0cb0f-271">四边形具有矩形区，但它们表示任意形状的2D 图面。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="0cb0f-272">若要在与3D 环境四边形的图面上实现放置，使此交互成为可能。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="0cb0f-273">当前场景理解提供了两个此类函数： _ *FindCentermostPlacement*\* 和 **GetSurfaceMask**。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-273">Currently Scene Understanding provides two such functions, _ *FindCentermostPlacement*\* and **GetSurfaceMask**.</span></span> <span data-ttu-id="0cb0f-274">FindCentermostPlacement 是一个高级别 API，它在四个位置上定位一个对象，并尝试查找您的对象的最佳位置，以确保您提供的边界框保持在底层的表面上。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="0cb0f-275">输出的坐标是相对于 "四个空间" 中的四个部分的，其中左上角是 (x = 0，y = 0) ，就像对其他 windows Rect 类型一样。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="0cb0f-276">在使用自己的对象的源时，请务必考虑这一点。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="0cb0f-277">下面的示例演示如何查找 centermost 可放置位置并将全息图定位到四个部分。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="0cb0f-278">步骤1-4 依赖于特定的框架/实现，但主题应类似。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="0cb0f-279">请注意，四个部分只表示在空间中进行了本地化的界限2D 平面。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="0cb0f-280">通过让引擎/框架知道四个部分，并相对于四个部分定位对象，您的全息影像会正确地定位到现实世界。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="0cb0f-281">网格</span><span class="sxs-lookup"><span data-stu-id="0cb0f-281">Mesh</span></span>

<span data-ttu-id="0cb0f-282">网格表示对象或环境的几何表示形式。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="0cb0f-283">与每个空间 surface 网格一起提供的 [空间映射](../../design/spatial-mapping.md)、网格索引和顶点数据非常类似于在所有新式渲染 api 中用于呈现三角形网格的顶点和索引缓冲区。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="0cb0f-284">顶点位置在的坐标系统中提供 `Scene` 。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="0cb0f-285">用于引用此数据的特定 Api 如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cb0f-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="0cb0f-286">下面的代码提供了一个示例，说明如何从网格结构生成三角形列表：</span><span class="sxs-lookup"><span data-stu-id="0cb0f-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="0cb0f-287">索引/顶点缓冲区必须 >= 索引/顶点计数，但也可以任意调整大小以允许有效地重用内存。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="0cb0f-288">ColliderMesh</span><span class="sxs-lookup"><span data-stu-id="0cb0f-288">ColliderMesh</span></span>

<span data-ttu-id="0cb0f-289">场景对象通过 "网格" 和 "ColliderMeshes" 属性提供对网格和碰撞器网格数据的访问。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="0cb0f-290">这些网格将始终匹配，这意味着网格属性的 i'th 索引与 ColliderMeshes 属性的 i'th 索引表示相同的几何。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="0cb0f-291">如果运行时/对象支持碰撞器网格，则可保证获得最小多边形，最高序位，并在应用程序使用 colliders 的任何位置使用 ColliderMeshes。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="0cb0f-292">如果系统不支持 colliders，则在 ColliderMeshes 中返回的网格对象将与网格减少内存约束的对象相同。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="0cb0f-293">通过场景理解进行开发</span><span class="sxs-lookup"><span data-stu-id="0cb0f-293">Developing with scene understanding</span></span>

<span data-ttu-id="0cb0f-294">此时，你应了解场景的核心构建基块了解运行时和 SDK。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="0cb0f-295">大容量和复杂性在于访问模式、与3D 框架的交互，以及可以在这些 Api 基础上编写的工具来执行更高级的任务，例如空间规划、房间分析、导航、物理学等。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="0cb0f-296">我们想要在示例中捕获这些示例，这些示例应指导您正确地指导您的场景。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="0cb0f-297">如果有不能解决的示例或方案，请告知我们，我们将尝试记录/原型所需的内容。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="0cb0f-298">在哪里可以获取示例代码？</span><span class="sxs-lookup"><span data-stu-id="0cb0f-298">Where can I get sample code?</span></span>

<span data-ttu-id="0cb0f-299">可在 [Unity 示例页](https://github.com/sceneunderstanding-microsoft/unitysample) 页面上了解 unity 的示例代码。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="0cb0f-300">此应用程序将允许你与设备进行通信并呈现各种场景对象，或者，它允许你将序列化场景加载到电脑上，并允许你在不使用设备的情况下体验场景。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="0cb0f-301">在哪里可以获取示例场景？</span><span class="sxs-lookup"><span data-stu-id="0cb0f-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="0cb0f-302">如果你有 HoloLens2，则可以通过将 ComputeSerializedAsync 的输出保存到文件，并在方便时反序列化，来保存已捕获的任何场景。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="0cb0f-303">如果你没有 HoloLens2 设备，但想要在场景理解下播放，则需要下载预捕获的场景。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="0cb0f-304">场景理解示例当前附带了序列化场景，可以在方便的时候下载和使用。</span><span class="sxs-lookup"><span data-stu-id="0cb0f-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="0cb0f-305">可在此处找到它们：</span><span class="sxs-lookup"><span data-stu-id="0cb0f-305">You can find them here:</span></span>

[<span data-ttu-id="0cb0f-306">场景了解示例场景</span><span class="sxs-lookup"><span data-stu-id="0cb0f-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="0cb0f-307">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cb0f-307">See also</span></span>

* [<span data-ttu-id="0cb0f-308">空间映射</span><span class="sxs-lookup"><span data-stu-id="0cb0f-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="0cb0f-309">场景理解</span><span class="sxs-lookup"><span data-stu-id="0cb0f-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="0cb0f-310">Unity 示例</span><span class="sxs-lookup"><span data-stu-id="0cb0f-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
