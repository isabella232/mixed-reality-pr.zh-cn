---
title: 针对 Unity 的性能建议
description: 了解 Unity 特定的提示，利用混合现实应用中的项目设置、分析和内存管理来提高性能。
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2019
ms.topic: article
keywords: 图形, cpu, gpu, 渲染, 垃圾回收, hololens
ms.localizationpriority: high
ms.openlocfilehash: f8757e5a5f5c9163dc70d8c8d0e93848c49a6694
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "101759723"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="5307e-104">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="5307e-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="5307e-105">本文基于[针对混合现实的性能建议](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)，但重点介绍特定于 Unity 的改进。</span><span class="sxs-lookup"><span data-stu-id="5307e-105">This article builds on the [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on Unity-specific improvements.</span></span>

## <a name="use-recommended-unity-project-settings"></a><span data-ttu-id="5307e-106">使用建议的 Unity 项目设置</span><span class="sxs-lookup"><span data-stu-id="5307e-106">Use recommended Unity project settings</span></span>

<span data-ttu-id="5307e-107">在 Unity 中优化混合现实应用的性能时，最重要的第一步是确保使用[建议用于 Unity 的环境设置](recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="5307e-107">The most important first step when optimizing performance of mixed reality apps in Unity is to be sure you're using the [recommended environment settings for Unity](recommended-settings-for-unity.md).</span></span> <span data-ttu-id="5307e-108">该文中的内容涉及到一些对于生成高性能混合现实应用至关重要的场景配置。</span><span class="sxs-lookup"><span data-stu-id="5307e-108">That article contains content with some of the most important scene configurations for building performant Mixed Reality apps.</span></span> <span data-ttu-id="5307e-109">本文也强调了其中建议的一些设置。</span><span class="sxs-lookup"><span data-stu-id="5307e-109">Some of these recommended settings are highlighted below, as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="5307e-110">如何使用 Unity 进行探查</span><span class="sxs-lookup"><span data-stu-id="5307e-110">How to profile with Unity</span></span>

<span data-ttu-id="5307e-111">Unity 提供内置的 **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** ，它是一个极佳的资源，可以收集特定应用的重要性能见解。</span><span class="sxs-lookup"><span data-stu-id="5307e-111">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in, which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="5307e-112">尽管你可以在编辑器中运行该探查器，但这些指标并不代表真正的运行时环境，因此应该慎用其结果。</span><span class="sxs-lookup"><span data-stu-id="5307e-112">Although you can run the profiler in-editor, these metrics don't represent the true runtime environment so results should be used cautiously.</span></span> <span data-ttu-id="5307e-113">建议在设备上运行应用程序时远程对其进行探查，以获得最准确且可对其采取措施的见解。</span><span class="sxs-lookup"><span data-stu-id="5307e-113">We recommended remotely profiling your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="5307e-114">此外，Unity 的 [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) 也是一个可供使用的强大见解工具。</span><span class="sxs-lookup"><span data-stu-id="5307e-114">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) is also a powerful and insight tool to use.</span></span>

<span data-ttu-id="5307e-115">Unity 提供了以下方面的详尽文档：</span><span class="sxs-lookup"><span data-stu-id="5307e-115">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="5307e-116">如何[将 Unity Profiler 远程连接到 UWP 应用程序](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="5307e-116">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="5307e-117">如何有效[使用 Unity Profiler 诊断性能问题](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="5307e-117">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="5307e-118">在连接 Unity Profiler 并添加 GPU 探查器后（查看右上角的“添加探查器”），可以在探查器的中间分别查看花费在 CPU 和 GPU 上的时间。</span><span class="sxs-lookup"><span data-stu-id="5307e-118">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="5307e-119">这样，开发人员很快就能大致了解其应用程序是受 CPU 还是 GPU 的约束。</span><span class="sxs-lookup"><span data-stu-id="5307e-119">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 与 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="5307e-121">CPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="5307e-121">CPU performance recommendations</span></span>

<span data-ttu-id="5307e-122">以下内容涵盖更深入的性能做法，特别适合在 Unity 和 C# 开发中采用。</span><span class="sxs-lookup"><span data-stu-id="5307e-122">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="5307e-123">缓存引用</span><span class="sxs-lookup"><span data-stu-id="5307e-123">Cache references</span></span>

<span data-ttu-id="5307e-124">建议在初始化时缓存对所有相关组件和 GameObject 的引用，因为重复函数调用（如 [GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html) 和 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)）相对于存储指针的内存成本更昂贵。</span><span class="sxs-lookup"><span data-stu-id="5307e-124">We recommend caching references to all relevant components and GameObjects at initialization because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* and [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html) are more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="5307e-125">.</span><span class="sxs-lookup"><span data-stu-id="5307e-125">.</span></span> <span data-ttu-id="5307e-126">*Camera.main* 仅在后台使用 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，但而它会以很高的开销在场景图中搜索具有“MainCamera”标记的 camera 对象。</span><span class="sxs-lookup"><span data-stu-id="5307e-126">*Camera.main* just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath, which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> <span data-ttu-id="5307e-127">避免 GetComponent(string)</span><span class="sxs-lookup"><span data-stu-id="5307e-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="5307e-128">使用 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 时，会产生少量不同的重载。</span><span class="sxs-lookup"><span data-stu-id="5307e-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="5307e-129">必须始终使用基于类型的实现，切勿使用基于字符串的搜索重载。</span><span class="sxs-lookup"><span data-stu-id="5307e-129">It is important to always use the Type-based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="5307e-130">在场景中按字符串进行搜索，比按类型进行搜索的开销要高得多。</span><span class="sxs-lookup"><span data-stu-id="5307e-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="5307e-131">（正确）Component GetComponent(Type type)</span><span class="sxs-lookup"><span data-stu-id="5307e-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="5307e-132">（正确）T GetComponent\<T>()</span><span class="sxs-lookup"><span data-stu-id="5307e-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="5307e-133">（错误）Component GetComponent(string)></span><span class="sxs-lookup"><span data-stu-id="5307e-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="5307e-134">避免高开销的操作</span><span class="sxs-lookup"><span data-stu-id="5307e-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="5307e-135">**避免使用 [LINQ](/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="5307e-135">**Avoid use of [LINQ](/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="5307e-136">尽管 LINQ 很容易读写，但与比手动编写算法相比，使用 LINQ 通常需要更多的计算和内存。</span><span class="sxs-lookup"><span data-stu-id="5307e-136">Although LINQ can be clean and easy to read and write, it generally requires more computation and memory than if you wrote the algorithm manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="5307e-137">**通用 Unity API**</span><span class="sxs-lookup"><span data-stu-id="5307e-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="5307e-138">某些 Unity API 虽然很有用，但其执行开销可能很高。</span><span class="sxs-lookup"><span data-stu-id="5307e-138">Certain Unity APIs, although useful, can be expensive to execute.</span></span> <span data-ttu-id="5307e-139">其中的大部分 API 都涉及到在整个场景图中搜索 GameObject 的匹配列表。</span><span class="sxs-lookup"><span data-stu-id="5307e-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="5307e-140">一般情况下，若要避免这些操作，可以缓存引用，或者实现 GameObject 的管理器组件，以在运行时跟踪引用。</span><span class="sxs-lookup"><span data-stu-id="5307e-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects to track the references at runtime.</span></span>

    ```csharp
        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()
    ```

>[!NOTE]
> <span data-ttu-id="5307e-141">应该消除 *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 的所有开销。</span><span class="sxs-lookup"><span data-stu-id="5307e-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="5307e-142">与直接函数调用相比，这些函数可能要慢上若干千倍。</span><span class="sxs-lookup"><span data-stu-id="5307e-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="5307e-143">**注意装箱**</span><span class="sxs-lookup"><span data-stu-id="5307e-143">**Beware of boxing**</span></span>

    <span data-ttu-id="5307e-144">[装箱](/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是 C# 语言和运行时的核心概念。</span><span class="sxs-lookup"><span data-stu-id="5307e-144">[Boxing](/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="5307e-145">它是将值类型化变量（例如 `char`、`int` 和 `bool` 等）包装到引用类型化变量中的过程。</span><span class="sxs-lookup"><span data-stu-id="5307e-145">It's the process of wrapping value-typed variables such as `char`, `int`, `bool`, etc. into reference-typed variables.</span></span> <span data-ttu-id="5307e-146">将值类型化变量“装箱”后，该变量将包装在 `System.Object` 内，后者存储在托管堆上。</span><span class="sxs-lookup"><span data-stu-id="5307e-146">When a value-typed variable is "boxed", it's wrapped in a `System.Object`, which is stored on the managed heap.</span></span> <span data-ttu-id="5307e-147">需要分配内存，并在最终释放内存后，由垃圾回收器处理内存。</span><span class="sxs-lookup"><span data-stu-id="5307e-147">Memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="5307e-148">这种分配和解除分配会损害性能，且在许多情况下是不必要的，或者可以由开销更低的替代做法轻松取代。</span><span class="sxs-lookup"><span data-stu-id="5307e-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

    <span data-ttu-id="5307e-149">若要避免装箱，请务必将用于存储数值类型和结构（包括 `Nullable<T>`）的变量、字段和属性强类型化为特定类型（例如 `int`、`float?` 或 `MyStruct`），而不是使用对象。</span><span class="sxs-lookup"><span data-stu-id="5307e-149">To avoid boxing, be sure that the variables, fields, and properties in which you store numeric types and structs (including `Nullable<T>`) are strongly typed as specific types such as `int`, `float?` or `MyStruct`, instead of using object.</span></span>  <span data-ttu-id="5307e-150">如果将这些对象放入列表中，请确保使用强类型列表（例如 `List<int>`），而不是 `List<object>` 或 `ArrayList`。</span><span class="sxs-lookup"><span data-stu-id="5307e-150">If putting these objects into a list, be sure to use a strongly typed list such as `List<int>` rather than `List<object>` or `ArrayList`.</span></span>

    <span data-ttu-id="5307e-151">**C# 中的装箱示例**</span><span class="sxs-lookup"><span data-stu-id="5307e-151">**Example of boxing in C#**</span></span>

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

#### <a name="repeating-code-paths"></a><span data-ttu-id="5307e-152">重复代码路径</span><span class="sxs-lookup"><span data-stu-id="5307e-152">Repeating code paths</span></span>

<span data-ttu-id="5307e-153">应该精心编写每秒要执行多次的任何</span><span class="sxs-lookup"><span data-stu-id="5307e-153">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="5307e-154">重复性 Unity 回调函数（例如 Update）和/或帧。</span><span class="sxs-lookup"><span data-stu-id="5307e-154">Update) that are executed many times per second and/or frame should be written carefully.</span></span> <span data-ttu-id="5307e-155">此处发生的任何高开销操作都会对性能持续造成巨大影响。</span><span class="sxs-lookup"><span data-stu-id="5307e-155">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="5307e-156">**空回调函数**</span><span class="sxs-lookup"><span data-stu-id="5307e-156">**Empty callback functions**</span></span>

    <span data-ttu-id="5307e-157">在应用程序中保留以下代码看似没有妨碍，尤其是因为每个 Unity 脚本都要通过此 Update 方法自动初始化，但这些空回调的开销可能非常高。</span><span class="sxs-lookup"><span data-stu-id="5307e-157">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with an Update method, these empty callbacks can become expensive.</span></span> <span data-ttu-id="5307e-158">Unity 在 UnityEngine 代码与应用程序代码之间的非托管和托管代码边界之间来回操作。</span><span class="sxs-lookup"><span data-stu-id="5307e-158">Unity operates back and forth between an unmanaged and managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="5307e-159">通过此桥梁进行上下文切换会产生相当高的开销，即使没有要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="5307e-159">Context switching over this bridge is fairly expensive, even if there's nothing to execute.</span></span> <span data-ttu-id="5307e-160">如果应用具有数百个 GameObject 以及包含空重复性 Unity 回调的组件，则此操作特别容易造成问题。</span><span class="sxs-lookup"><span data-stu-id="5307e-160">This becomes especially problematic if your app has 100s of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="5307e-161">Update() 最容易造成此性能问题，但如下所列的其他重复性 Unity 回调可能也好不到哪里去，甚至更糟：FixedUpdate()、LateUpdate()、OnPostRender"、OnPreRender()、OnRenderImage() 等。</span><span class="sxs-lookup"><span data-stu-id="5307e-161">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks, such as the following can be equally as bad, if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="5307e-162">**偏向于对每帧运行一次的操作**</span><span class="sxs-lookup"><span data-stu-id="5307e-162">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="5307e-163">以下 Unity API 是许多全息应用的常用操作。</span><span class="sxs-lookup"><span data-stu-id="5307e-163">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="5307e-164">尽管并非总是可行，但这些函数的结果往往只计算一次，然后在整个应用程序中对给定的帧重新利用结果。</span><span class="sxs-lookup"><span data-stu-id="5307e-164">Although not always possible, the results from these functions can commonly be computed once and the results reutilized across the application for a given frame.</span></span>

    <span data-ttu-id="5307e-165">a) 最好是通过一个专用的单一实例类或服务来处理投影到场景中的视线，然后在所有其他场景组件中重复使用此结果，而无需由每个组件执行重复性的、相同的光投影操作。</span><span class="sxs-lookup"><span data-stu-id="5307e-165">a) It's good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then reuse this result in all other scene components, instead of making repeated and identical Raycast operations by each component.</span></span> <span data-ttu-id="5307e-166">某些应用程序可能要求从不同的原点投射光线，或者针对不同的[图层遮罩](https://docs.unity3d.com/ScriptReference/LayerMask.html)投射光线。</span><span class="sxs-lookup"><span data-stu-id="5307e-166">Some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>
    
    ```csharp
        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()
    ```

    <span data-ttu-id="5307e-167">b) 通过在 Start()或 Awake() 中[缓存引用](#cache-references)，来避免重复性 Unity 回调（例如 Update()）中的 GetComponent() 操作</span><span class="sxs-lookup"><span data-stu-id="5307e-167">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>
    
    ```csharp
        UnityEngine.Object.GetComponent()
    ```

    <span data-ttu-id="5307e-168">c) 如果可能，最好是在初始化时实例化所有对象，并使用[对象池](#object-pooling)在应用程序的整个运行时中回收并重复使用 GameObject</span><span class="sxs-lookup"><span data-stu-id="5307e-168">c) It's good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and reuse GameObjects throughout runtime of your application</span></span>

    ```csharp
        UnityEngine.Object.Instantiate()
    ```

3) <span data-ttu-id="5307e-169">**避免接口和虚拟构造**</span><span class="sxs-lookup"><span data-stu-id="5307e-169">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="5307e-170">与利用直接构造或直接函数调用相比，通过接口与直接对象调用函数或调用虚拟函数往往会造成高得多的开销。</span><span class="sxs-lookup"><span data-stu-id="5307e-170">Invoking function calls through interfaces vs direct objects or calling virtual functions can often be much more expensive than using direct constructs or direct function calls.</span></span> <span data-ttu-id="5307e-171">如果不需要虚拟函数或接口，应将其删除。</span><span class="sxs-lookup"><span data-stu-id="5307e-171">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="5307e-172">但是，如果利用它们能够简化开发协作、改善代码的易读性和代码可维护性，则这些做法造成的性能下降是值得的。</span><span class="sxs-lookup"><span data-stu-id="5307e-172">However, the performance hit for these approaches is worth the trade-off if using them simplifies development collaboration, code readability, and code maintainability.</span></span>

    <span data-ttu-id="5307e-173">一般情况下，不建议将字段和函数标记为虚拟，除非明确要求覆盖此成员。</span><span class="sxs-lookup"><span data-stu-id="5307e-173">Generally, the recommendation is to not mark fields and functions as virtual unless there's a clear expectation that this member needs to be overwritten.</span></span> <span data-ttu-id="5307e-174">应特别注意要对每个帧调用多次（甚至对每个帧调用一次，例如 `UpdateUI()` 方法）的高频代码路径。</span><span class="sxs-lookup"><span data-stu-id="5307e-174">One should be especially careful around high-frequency code paths that are called many times per frame or even once per frame such as an `UpdateUI()` method.</span></span>

4) <span data-ttu-id="5307e-175">**避免按值传递结构**</span><span class="sxs-lookup"><span data-stu-id="5307e-175">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="5307e-176">与类不同，结构是值类型，将其直接传递给函数时，其内容将复制到新建的实例。</span><span class="sxs-lookup"><span data-stu-id="5307e-176">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="5307e-177">这种复制增加了 CPU 开销以及堆栈上的附加内存。</span><span class="sxs-lookup"><span data-stu-id="5307e-177">This copy adds CPU cost, as well as additional memory on the stack.</span></span> <span data-ttu-id="5307e-178">对于小型结构，这种影响可以忽略不计，因此是可接受的。</span><span class="sxs-lookup"><span data-stu-id="5307e-178">For small structs, the effect is minimal and thus acceptable.</span></span> <span data-ttu-id="5307e-179">但是，对于要对每个帧重复调用的函数，以及采用大型结构的函数，如果可能，请修改函数定义以按引用传递。</span><span class="sxs-lookup"><span data-stu-id="5307e-179">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="5307e-180">在此处了解详细信息</span><span class="sxs-lookup"><span data-stu-id="5307e-180">Learn more here</span></span>](/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="5307e-181">杂项</span><span class="sxs-lookup"><span data-stu-id="5307e-181">Miscellaneous</span></span>

1) <span data-ttu-id="5307e-182">**物理学**</span><span class="sxs-lookup"><span data-stu-id="5307e-182">**Physics**</span></span>

    <span data-ttu-id="5307e-183">a) 一般情况下，改善物理学的最简单方法是限制花费在物理学上的时间或每秒迭代次数。</span><span class="sxs-lookup"><span data-stu-id="5307e-183">a) Generally, the easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="5307e-184">这会降低模拟准确度。</span><span class="sxs-lookup"><span data-stu-id="5307e-184">This will reduce simulation accuracy.</span></span> <span data-ttu-id="5307e-185">参阅 Unity 中的 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)</span><span class="sxs-lookup"><span data-stu-id="5307e-185">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="5307e-186">b) Unity 中的碰撞体类型具有广泛不同的性能特征。</span><span class="sxs-lookup"><span data-stu-id="5307e-186">b) The types of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="5307e-187">下面从左到右按顺序列出了性能最高到性能最低的碰撞体。</span><span class="sxs-lookup"><span data-stu-id="5307e-187">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="5307e-188">重要的是避免网格碰撞体，其开销要比基元碰撞体高出太多。</span><span class="sxs-lookup"><span data-stu-id="5307e-188">It's important to avoid Mesh Colliders, which are substantially more expensive than the primitive colliders.</span></span>

    <span data-ttu-id="5307e-189">球体 < 胶囊 < 箱体 <<< 网格（凸） < 网格（非凸）</span><span class="sxs-lookup"><span data-stu-id="5307e-189">Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)</span></span>

    <span data-ttu-id="5307e-190">有关详细信息，请参阅 [Unity 物理学最佳做法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="5307e-190">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="5307e-191">**动画**</span><span class="sxs-lookup"><span data-stu-id="5307e-191">**Animations**</span></span>

    <span data-ttu-id="5307e-192">通过禁用动画程序组件来禁用空闲动画（禁用游戏对象不会产生相同的效果）。</span><span class="sxs-lookup"><span data-stu-id="5307e-192">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="5307e-193">避免其动画程序循环将某个值设置为相同内容的设计模式。</span><span class="sxs-lookup"><span data-stu-id="5307e-193">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="5307e-194">此方法会产生相当大的开销，但对应用程序没有影响。</span><span class="sxs-lookup"><span data-stu-id="5307e-194">There's considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="5307e-195">在此处了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="5307e-195">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="5307e-196">**复杂算法**</span><span class="sxs-lookup"><span data-stu-id="5307e-196">**Complex algorithms**</span></span>

    <span data-ttu-id="5307e-197">如果应用程序使用复杂算法，例如逆向运动、路径查找等，请努力找到更简单的方法，或调整其性能相关的设置</span><span class="sxs-lookup"><span data-stu-id="5307e-197">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="5307e-198">CPU-GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="5307e-198">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="5307e-199">一般情况下，CPU-GPU 性能归根结底与提交到显卡的 **绘制调用** 相关。</span><span class="sxs-lookup"><span data-stu-id="5307e-199">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="5307e-200">为了改善性能，需要战略性地 **减少** 绘制调用，或 **重新构建** 绘制调用以获得最佳结果。</span><span class="sxs-lookup"><span data-stu-id="5307e-200">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="5307e-201">由于绘制调用本身是资源密集型的，减少此类调用可以减少所需的总体工作量。</span><span class="sxs-lookup"><span data-stu-id="5307e-201">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="5307e-202">此外，绘制调用之间的状态更改需要在图形驱动程序中执行高开销的验证和转换步骤，因此，重新构建应用程序的绘制调用来限制状态更改（例如</span><span class="sxs-lookup"><span data-stu-id="5307e-202">Further, state changes between draw calls require costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes (i.e</span></span> <span data-ttu-id="5307e-203">不同的材料等）可以大幅提高性能。</span><span class="sxs-lookup"><span data-stu-id="5307e-203">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="5307e-204">Unity 通过一篇详尽的文章概述并深入探讨了如何根据其平台批处理绘制调用。</span><span class="sxs-lookup"><span data-stu-id="5307e-204">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="5307e-205">Unity 绘制调用批处理</span><span class="sxs-lookup"><span data-stu-id="5307e-205">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="5307e-206">单通道实例化渲染</span><span class="sxs-lookup"><span data-stu-id="5307e-206">Single pass instanced rendering</span></span>

<span data-ttu-id="5307e-207">Unity 中的单通道实例化渲染使针对每只眼睛的绘制调用缩减为一个实例化绘制调用。</span><span class="sxs-lookup"><span data-stu-id="5307e-207">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="5307e-208">由于两个绘制调用之间的缓存内聚性，GPU 的性能也能得到一定的改善。</span><span class="sxs-lookup"><span data-stu-id="5307e-208">Because of cache coherency between two draw calls, there's also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="5307e-209">在 Unity 项目中启用此功能</span><span class="sxs-lookup"><span data-stu-id="5307e-209">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="5307e-210">打开“播放器 XR 设置”（转到“编辑” > “项目设置” > “播放器” > “XR 设置”）    </span><span class="sxs-lookup"><span data-stu-id="5307e-210">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="5307e-211">从“立体渲染方法”下拉菜单中选择“单通道实例化”（必须选中“支持虚拟现实”复选框）  </span><span class="sxs-lookup"><span data-stu-id="5307e-211">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="5307e-212">有关此渲染方法的详细信息，请阅读 Unity 的以下文章。</span><span class="sxs-lookup"><span data-stu-id="5307e-212">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="5307e-213">如何使用高级立体渲染最大化 AR 和 VR 的性能</span><span class="sxs-lookup"><span data-stu-id="5307e-213">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="5307e-214">单通道实例化</span><span class="sxs-lookup"><span data-stu-id="5307e-214">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="5307e-215">如果开发人员的现有自定义着色器不是针对实例化编写的，则单通道实例化渲染会发生一个常见问题。</span><span class="sxs-lookup"><span data-stu-id="5307e-215">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="5307e-216">启用此功能后，开发人员可能会注意到，某些 GameObject 只在一只眼睛中呈现。</span><span class="sxs-lookup"><span data-stu-id="5307e-216">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="5307e-217">这是因为，关联的自定义着色器没有与实例化相关的适当属性。</span><span class="sxs-lookup"><span data-stu-id="5307e-217">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="5307e-218">请参阅 Unity 文章 [HoloLens 的 单通道立体渲染](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)来了解如何解决此问题</span><span class="sxs-lookup"><span data-stu-id="5307e-218">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="5307e-219">静态批处理</span><span class="sxs-lookup"><span data-stu-id="5307e-219">Static batching</span></span>

<span data-ttu-id="5307e-220">Unity 能够批处理许多静态对象，以减少对 GPU 的绘制调用。</span><span class="sxs-lookup"><span data-stu-id="5307e-220">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="5307e-221">静态批处理适用于 Unity 中具有以下特征的大多数[渲染器](https://docs.unity3d.com/ScriptReference/Renderer.html)：1) 共享相同的材料；2) 全部标记为 Static（在 Unity 中选择一个对象，然后选择检查器右上角的复选框） 。</span><span class="sxs-lookup"><span data-stu-id="5307e-221">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and select the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="5307e-222">标记为 *Static* 的 GameObject 无法在应用程序的整个运行时中移动。</span><span class="sxs-lookup"><span data-stu-id="5307e-222">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="5307e-223">因此，在几乎每个对象都需要进行定位、移动、缩放等操作的 HoloLens 上，可能很难利用静态批处理。对于沉浸式头戴显示设备，静态批处理可以大幅减少绘制调用，从而改善性能。</span><span class="sxs-lookup"><span data-stu-id="5307e-223">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="5307e-224">有关更多详细信息，请阅读 [Unity 中的绘制调用批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)下的“静态批处理”。</span><span class="sxs-lookup"><span data-stu-id="5307e-224">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="5307e-225">动态批处理</span><span class="sxs-lookup"><span data-stu-id="5307e-225">Dynamic batching</span></span>

<span data-ttu-id="5307e-226">由于在 HoloLens 开发中将对象标记为 Static 会造成问题，动态批处理可能是弥补这项短缺功能的极佳手段。</span><span class="sxs-lookup"><span data-stu-id="5307e-226">Since it's problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="5307e-227">它也可用于沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="5307e-227">It can also be useful on immersive headsets, as well.</span></span> <span data-ttu-id="5307e-228">不过，Unity 中的动态批处理可能很难启用，原因是 GameObject 必须 **a) 共享相同的材料**；**b) 符合其他很多条件**。</span><span class="sxs-lookup"><span data-stu-id="5307e-228">However, dynamic batching in Unity can be difficult to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="5307e-229">有关条件的完整列表，请阅读[Unity 中的绘制调用批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)下的“动态批处理”。</span><span class="sxs-lookup"><span data-stu-id="5307e-229">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="5307e-230">最常见的情况是，由于关联的网格数据不能超过 300 个顶点，因此 GameObject 无效，无法对其进行动态批处理。</span><span class="sxs-lookup"><span data-stu-id="5307e-230">Most commonly, GameObjects become invalid to be batched dynamically, because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="5307e-231">其他技术</span><span class="sxs-lookup"><span data-stu-id="5307e-231">Other techniques</span></span>

<span data-ttu-id="5307e-232">仅当多个 GameObject 能够共享同一材料时，才会发生批处理。</span><span class="sxs-lookup"><span data-stu-id="5307e-232">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="5307e-233">通常，批处理受阻的原因是 GameObject 需要对其各自的材料使用独特的纹理。</span><span class="sxs-lookup"><span data-stu-id="5307e-233">Typically, this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="5307e-234">开发人员往往将纹理合并成一个大纹理，此方法称为[纹理集合](https://en.wikipedia.org/wiki/Texture_atlas)。</span><span class="sxs-lookup"><span data-stu-id="5307e-234">It's common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="5307e-235">此外，在可能且合理的情况下，他们倾向于将网格合并成一个 GameObject。</span><span class="sxs-lookup"><span data-stu-id="5307e-235">Furthermore, it's preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="5307e-236">Unity 中的每个渲染器具有自身关联的绘制调用，而不是通过一个渲染器提交合并的网格。</span><span class="sxs-lookup"><span data-stu-id="5307e-236">Each Renderer in Unity will have its associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span>

>[!NOTE]
> <span data-ttu-id="5307e-237">在运行时修改 Renderer.material 属性会创建材料的副本，因此可能会中断批处理。</span><span class="sxs-lookup"><span data-stu-id="5307e-237">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="5307e-238">使用 Renderer.sharedMaterial 可以修改各个 GameObject 的共享材料属性。</span><span class="sxs-lookup"><span data-stu-id="5307e-238">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="5307e-239">GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="5307e-239">GPU performance recommendations</span></span>

<span data-ttu-id="5307e-240">详细了解[如何在 Unity 中优化图形渲染](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span><span class="sxs-lookup"><span data-stu-id="5307e-240">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="5307e-241">优化深度缓冲区共享</span><span class="sxs-lookup"><span data-stu-id="5307e-241">Optimize depth buffer sharing</span></span>

<span data-ttu-id="5307e-242">建议在“播放器 XR 设置”下启用“深度缓冲区共享”，以优化[全息影像稳定性](../platform-capabilities-and-apis/Hologram-stability.md)。 </span><span class="sxs-lookup"><span data-stu-id="5307e-242">It's recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](../platform-capabilities-and-apis/Hologram-stability.md).</span></span> <span data-ttu-id="5307e-243">但是，在使用此设置的情况下启用基于深度的后期阶段重新投影时，建议选择“16 位深度格式”而不是“24 位深度格式” 。</span><span class="sxs-lookup"><span data-stu-id="5307e-243">When enabling depth-based late-stage reprojection with this setting however, it's recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="5307e-244">16 位深度缓冲区可以大幅减少与深度缓冲区流量相关的带宽（以及电量消耗）。</span><span class="sxs-lookup"><span data-stu-id="5307e-244">The 16-bit depth buffers will drastically reduce the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="5307e-245">这可能会给节能和性能提升带来很大的好处。</span><span class="sxs-lookup"><span data-stu-id="5307e-245">This can be a big win both in power reduction and performance improvement.</span></span> <span data-ttu-id="5307e-246">但是，使用 *16 位深度格式* 可能会造成两种负面影响。</span><span class="sxs-lookup"><span data-stu-id="5307e-246">However, there are two possible negative outcomes by using *16-bit depth format*.</span></span>

<span data-ttu-id="5307e-247">**Z 冲突**</span><span class="sxs-lookup"><span data-stu-id="5307e-247">**Z-Fighting**</span></span>

<span data-ttu-id="5307e-248">与 24 位相比，16 位的更低深度范围保真度更容易发生 [Z 冲突](https://en.wikipedia.org/wiki/Z-fighting)。</span><span class="sxs-lookup"><span data-stu-id="5307e-248">The reduced depth range fidelity makes [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) more likely to occur with 16 bit than 24-bit.</span></span> <span data-ttu-id="5307e-249">若要避免这种假象，请修改 [Unity 相机](https://docs.unity3d.com/Manual/class-Camera.html)的近距/远距剪裁平面，以采用更低的精度。</span><span class="sxs-lookup"><span data-stu-id="5307e-249">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="5307e-250">对于基于 HoloLens 的应用程序，50 米（而不是 Unity 的默认 1000 米）的远距剪裁平面通常可以消除任何 Z 冲突。</span><span class="sxs-lookup"><span data-stu-id="5307e-250">For HoloLens-based applications, a far clip plane of 50 m instead of the Unity default 1000 m can generally eliminate any z-fighting.</span></span>

<span data-ttu-id="5307e-251">**已禁用模具缓冲区**</span><span class="sxs-lookup"><span data-stu-id="5307e-251">**Disabled Stencil Buffer**</span></span>

<span data-ttu-id="5307e-252">当 Unity 创建 [16 位深度的渲染纹理](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)时，不会创建模具缓冲区。</span><span class="sxs-lookup"><span data-stu-id="5307e-252">When Unity creates a [Render Texture with 16-bit depth](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), there's no stencil buffer created.</span></span> <span data-ttu-id="5307e-253">选择 24 位深度格式后，每个 Unity 文档将创建一个 24 位 Z 缓冲区和一个 [8 位模具缓冲区] (https://docs.unity3d.com/Manual/SL-Stencil.html) （如果 32 位在设备上适用，通常在 HoloLens 等设备上适用）。</span><span class="sxs-lookup"><span data-stu-id="5307e-253">Selecting 24-bit depth format, per Unity documentation, will create a 24-bit z-buffer, as well as an [8-bit stencil buffer] (https://docs.unity3d.com/Manual/SL-Stencil.html) (if 32-bit is applicable on a device, which is generally the case such as HoloLens).</span></span>

### <a name="avoid-full-screen-effects"></a><span data-ttu-id="5307e-254">避免全屏效果</span><span class="sxs-lookup"><span data-stu-id="5307e-254">Avoid full-screen effects</span></span>

<span data-ttu-id="5307e-255">全屏运行的技术可能会产生相当高的开销，因为它们的数量级是每帧数百万次操作。</span><span class="sxs-lookup"><span data-stu-id="5307e-255">Techniques that operate on the full screen can be expensive since their order of magnitude is millions of operations every frame.</span></span> <span data-ttu-id="5307e-256">建议避免抗锯齿、开花等[后处理](https://docs.unity3d.com/Manual/PostProcessingOverview.html)效果。</span><span class="sxs-lookup"><span data-stu-id="5307e-256">It's recommended to avoid [post-processing effects](https://docs.unity3d.com/Manual/PostProcessingOverview.html) such as anti-aliasing, bloom, and more.</span></span>

### <a name="optimal-lighting-settings"></a><span data-ttu-id="5307e-257">最佳照明设置</span><span class="sxs-lookup"><span data-stu-id="5307e-257">Optimal lighting settings</span></span>

<span data-ttu-id="5307e-258">Unity 中的[实时全局照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供杰出的视觉效果，但涉及到开销很高的照明计算。</span><span class="sxs-lookup"><span data-stu-id="5307e-258">[Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide outstanding visual results but involves expensive lighting calculations.</span></span> <span data-ttu-id="5307e-259">建议通过“窗口” > “渲染” > “照明设置”> 取消选中“实时全局照明”，为每个 Unity 场景文件禁用“实时全局照明”   。</span><span class="sxs-lookup"><span data-stu-id="5307e-259">We recommended disabling real-time Global Illumination for every Unity scene file via **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination**.</span></span>

<span data-ttu-id="5307e-260">此外，建议禁用所有阴影投射，因为这也会将高开销的 GPU 通道添加到 Unity 场景中。</span><span class="sxs-lookup"><span data-stu-id="5307e-260">Furthermore, it's recommended to disable all shadow casting as these also add expensive GPU passes onto a Unity scene.</span></span> <span data-ttu-id="5307e-261">可以按光源禁用阴影，但也可以通过“质量”设置对其进行整体控制。</span><span class="sxs-lookup"><span data-stu-id="5307e-261">Shadows can be disable per light but can also be controlled holistically via Quality settings.</span></span>

<span data-ttu-id="5307e-262">转到“编辑” > “项目设置”，然后选择“质量”类别 > 为“UWP 平台”选择“低质量”。   </span><span class="sxs-lookup"><span data-stu-id="5307e-262">**Edit** > **Project Settings**, then select the **Quality** category > Select **Low Quality** for the UWP Platform.</span></span> <span data-ttu-id="5307e-263">还可以直接将“阴影”属性设置为“禁用阴影”。 </span><span class="sxs-lookup"><span data-stu-id="5307e-263">One can also just set the **Shadows** property to **Disable Shadows**.</span></span>

<span data-ttu-id="5307e-264">建议在 Unity 中将烘焙光照用于你的模型。</span><span class="sxs-lookup"><span data-stu-id="5307e-264">We recommended that you use baked lighting with your models in Unity.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="5307e-265">减少多边形计数</span><span class="sxs-lookup"><span data-stu-id="5307e-265">Reduce poly count</span></span>

<span data-ttu-id="5307e-266">可通过以下方式减少多边形计数</span><span class="sxs-lookup"><span data-stu-id="5307e-266">Polygon count is reduced by either</span></span>
1) <span data-ttu-id="5307e-267">从场景中删除对象</span><span class="sxs-lookup"><span data-stu-id="5307e-267">Removing objects from a scene</span></span>
2) <span data-ttu-id="5307e-268">抽离资产，以减少给定网格的多边形数目</span><span class="sxs-lookup"><span data-stu-id="5307e-268">Asset decimation, which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="5307e-269">在应用程序中实施[详细级别 (LOD) 系统](https://docs.unity3d.com/Manual/LevelOfDetail.html)，以通过同一几何结构的较小多边形版本渲染远距离对象</span><span class="sxs-lookup"><span data-stu-id="5307e-269">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application, which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="5307e-270">了解 Unity 中的着色器</span><span class="sxs-lookup"><span data-stu-id="5307e-270">Understanding shaders in Unity</span></span>

<span data-ttu-id="5307e-271">若要大致比较着色器的性能，一种简单方法是识别每个着色器在运行时执行的平均操作数目。</span><span class="sxs-lookup"><span data-stu-id="5307e-271">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="5307e-272">可在 Unity 中轻松实现此目的。</span><span class="sxs-lookup"><span data-stu-id="5307e-272">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="5307e-273">选择着色器资产或选择材料，然后在检查器窗口的右上角选择齿轮图标，然后选择“选择着色器”</span><span class="sxs-lookup"><span data-stu-id="5307e-273">Select your shader asset or select a material, then in the top-right corner of the inspector window, select the gear icon followed by **"Select Shader"**</span></span>

    ![在 Unity 中选择着色器](images/Select-shader-unity.png)
2) <span data-ttu-id="5307e-275">选择着色器资产后，选择检查器窗口下的“编译并显示代码”按钮</span><span class="sxs-lookup"><span data-stu-id="5307e-275">With the shader asset selected, select the **"Compile and show code"** button under the inspector window</span></span>

    ![在 Unity 中编译着色器代码](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="5307e-277">编译后，查看结果中的统计信息部分，其中包含针对顶点和像素着色器（注意：像素着色器通常也称为段着色器）执行的不同操作数目</span><span class="sxs-lookup"><span data-stu-id="5307e-277">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 标准着色器操作](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a><span data-ttu-id="5307e-279">优化像素着色器</span><span class="sxs-lookup"><span data-stu-id="5307e-279">Optimize pixel shaders</span></span>

<span data-ttu-id="5307e-280">使用上述方法查看编译的统计信息结果时可以看到，[段着色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)执行的平均操作数目通常比[顶点着色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)更多。</span><span class="sxs-lookup"><span data-stu-id="5307e-280">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders), on average.</span></span> <span data-ttu-id="5307e-281">段着色器（也称为像素着色器）是按屏幕输出中的像素执行的，而顶点着色器只是按屏幕上绘制的所有网格的每个顶点执行的。</span><span class="sxs-lookup"><span data-stu-id="5307e-281">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span> 

<span data-ttu-id="5307e-282">因此，段着色器不仅仅是指令数比顶点着色器更多（因为要执行所有照明计算），而且段着色器几乎总是针对较大数据集执行的。</span><span class="sxs-lookup"><span data-stu-id="5307e-282">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="5307e-283">例如，如果屏幕输出为 2,000 x 2,000 图像，则段着色器可能会执行 2,000\*2,000 = 4,000,000 次。</span><span class="sxs-lookup"><span data-stu-id="5307e-283">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="5307e-284">如果渲染两只眼睛，此数字将会翻倍，因为有两个屏幕。</span><span class="sxs-lookup"><span data-stu-id="5307e-284">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="5307e-285">如果混合现实应用程序使用多个通道、全屏后处理效果或以相同的像素渲染多个网格，则此数字会大幅提高。</span><span class="sxs-lookup"><span data-stu-id="5307e-285">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span> 

<span data-ttu-id="5307e-286">因此，在段着色器中减少操作数目所带来的性能增益，通常远远好过在顶点着色器中进行优化。</span><span class="sxs-lookup"><span data-stu-id="5307e-286">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="5307e-287">Unity 标准着色器替代技术</span><span class="sxs-lookup"><span data-stu-id="5307e-287">Unity Standard shader alternatives</span></span>

<span data-ttu-id="5307e-288">不要使用基于物理学的渲染 (PBR) 或其他优质着色器，而是寻求利用更高性能且更经济的着色器。</span><span class="sxs-lookup"><span data-stu-id="5307e-288">Instead of using a physically based rendering (PBR) or another high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="5307e-289">[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供针对混合现实项目进行优化的 [MRTK 标准着色器](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mrtk-standard-shader.md)。</span><span class="sxs-lookup"><span data-stu-id="5307e-289">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mrtk-standard-shader.md) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="5307e-290">与 Unity 标准着色器相比，Unity 还提供不发光、顶点发亮、漫射和其他简化的着色器选项。</span><span class="sxs-lookup"><span data-stu-id="5307e-290">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="5307e-291">有关更多详细信息，请参阅[内置着色器的用法和性能](https://docs.unity3d.com/Manual/shader-Performance.html)。</span><span class="sxs-lookup"><span data-stu-id="5307e-291">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="5307e-292">着色器预加载</span><span class="sxs-lookup"><span data-stu-id="5307e-292">Shader preloading</span></span>

<span data-ttu-id="5307e-293">使用着色器预加载和其他技巧优化[着色器加载时间](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)。</span><span class="sxs-lookup"><span data-stu-id="5307e-293">Use *Shader preloading* and other tricks to optimize [shader load time](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="5307e-294">具体而言，着色器预加载意味着不会看到运行时着色器编译造成的任何帧聚结情况。</span><span class="sxs-lookup"><span data-stu-id="5307e-294">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="5307e-295">限制过度绘制</span><span class="sxs-lookup"><span data-stu-id="5307e-295">Limit overdraw</span></span>

<span data-ttu-id="5307e-296">在 Unity 中，可以通过在“场景”视图的左上角切换 [**绘制模式菜单**](https://docs.unity3d.com/Manual/ViewModes.html)并选择“过度绘制”，来显示其场景的过度绘制。 </span><span class="sxs-lookup"><span data-stu-id="5307e-296">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top-left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="5307e-297">一般情况下，在将对象发送到 GPU 之前提前剔除对象可以缓解过度绘制。</span><span class="sxs-lookup"><span data-stu-id="5307e-297">Generally, overdraw can be mitigated by culling objects ahead of time before they're sent to the GPU.</span></span> <span data-ttu-id="5307e-298">Unity 提供了有关为其引擎实现[遮挡剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5307e-298">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="5307e-299">内存建议</span><span class="sxs-lookup"><span data-stu-id="5307e-299">Memory recommendations</span></span>

<span data-ttu-id="5307e-300">过多的内存分配和解除分配操作可能对全息应用程序产生负面影响，导致性能不稳定、帧冻结和其他不利行为。</span><span class="sxs-lookup"><span data-stu-id="5307e-300">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application, resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="5307e-301">在 Unity 中进行开发时，了解内存注意事项特别重要，因为内存管理由垃圾回收器进行控制。</span><span class="sxs-lookup"><span data-stu-id="5307e-301">It's especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="5307e-302">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="5307e-302">Garbage collection</span></span>

<span data-ttu-id="5307e-303">在执行期间激活垃圾回收器 (GC) 来分析不再处于范围内的对象时，如果需要释放对象的内存以便可供重复使用，则全息应用会将处理计算时间损失在 GC 上。</span><span class="sxs-lookup"><span data-stu-id="5307e-303">Holographic apps will lose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released, so it can be made available for reuse.</span></span> <span data-ttu-id="5307e-304">连续的分配和解除分配通常需要垃圾回收器更频繁地运行，因此会损害性能和用户体验。</span><span class="sxs-lookup"><span data-stu-id="5307e-304">Constant allocations and de-allocations will generally require the garbage collector to run more frequently, thus hurting performance and user experience.</span></span>

<span data-ttu-id="5307e-305">Unity 在一个很好的网页中详细说明了垃圾回收器的工作原理，并提供了有关如何为内存管理编写更高效代码的提示。</span><span class="sxs-lookup"><span data-stu-id="5307e-305">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="5307e-306">优化 Unity 游戏中的垃圾回收</span><span class="sxs-lookup"><span data-stu-id="5307e-306">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="5307e-307">导致过度垃圾回收的最常见原因之一是在 Unity 开发中不缓存对组件和类的引用。</span><span class="sxs-lookup"><span data-stu-id="5307e-307">One of the most common practices that leads to excessive garbage collection isn't caching references to components and classes in Unity development.</span></span> <span data-ttu-id="5307e-308">应在运行 Start() 或 Awake() 期间捕获所有引用，并在以后运行 Update() 或 LateUpdate() 等函数期间重复使用这些引用。</span><span class="sxs-lookup"><span data-stu-id="5307e-308">Any references should be captured during Start() or Awake() and reused in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="5307e-309">其他快速提示：</span><span class="sxs-lookup"><span data-stu-id="5307e-309">Other quick tips:</span></span>
- <span data-ttu-id="5307e-310">在运行时使用 [StringBuilder](/dotnet/api/system.text.stringbuilder) C# 类动态生成复杂字符串</span><span class="sxs-lookup"><span data-stu-id="5307e-310">Use the [StringBuilder](/dotnet/api/system.text.stringbuilder) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="5307e-311">删除不再需要的 Debug.Log() 调用，因为它们仍会在应用的所有生成版本中执行</span><span class="sxs-lookup"><span data-stu-id="5307e-311">Remove calls to Debug.Log() when no longer needed, as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="5307e-312">如果全息应用通常需要大量的内存，请考虑在加载阶段（例如，在演示加载或过渡屏幕时）调用 [_**System.GC.Collect()**_](/dotnet/api/system.gc.collect)</span><span class="sxs-lookup"><span data-stu-id="5307e-312">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](/dotnet/api/system.gc.collect) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="5307e-313">对象池</span><span class="sxs-lookup"><span data-stu-id="5307e-313">Object pooling</span></span>

<span data-ttu-id="5307e-314">对象池是一种热门技术，可以降低连续对象分配和解除分配所造成的开销。</span><span class="sxs-lookup"><span data-stu-id="5307e-314">Object pooling is a popular technique for reducing the cost of continuous object allocation and deallocations.</span></span> <span data-ttu-id="5307e-315">此技术是通过以下方式实现的：分配一个由相同对象构成的较大池并重复使用此池中非活动的可用实例，而不是在各个时间内不断生成和销毁对象。</span><span class="sxs-lookup"><span data-stu-id="5307e-315">This is done by allocating a large pool of identical objects and reusing inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="5307e-316">对象池非常适合应用中生存期可变的可重用组件。</span><span class="sxs-lookup"><span data-stu-id="5307e-316">Object pools are great for reuseable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="5307e-317">Unity 中的对象池教程</span><span class="sxs-lookup"><span data-stu-id="5307e-317">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="5307e-318">启动性能</span><span class="sxs-lookup"><span data-stu-id="5307e-318">Startup performance</span></span>

<span data-ttu-id="5307e-319">请考虑使用较小的场景启动应用，然后使用 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 加载场景的剩余部分。</span><span class="sxs-lookup"><span data-stu-id="5307e-319">Consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="5307e-320">这样，应用就可以尽快进入交互状态。</span><span class="sxs-lookup"><span data-stu-id="5307e-320">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="5307e-321">在激活新场景时，可能会出现较大的 CPU 峰值，并且渲染的任何内容可能会出现断连或聚结。</span><span class="sxs-lookup"><span data-stu-id="5307e-321">There may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="5307e-322">解决此问题的方法之一是，在所要加载的场景中将 AsyncOperation.allowSceneActivation 属性设置为“false”，等待场景加载完成，将屏幕清理为黑屏，然后将此属性重新设置为“true”以完成场景激活。</span><span class="sxs-lookup"><span data-stu-id="5307e-322">One way to work around this is to set the AsyncOperation.allowSceneActivation property to "false" on the scene being loaded, wait for the scene to load, clear the screen too black, and then set it back to "true" to complete the scene activation.</span></span>

<span data-ttu-id="5307e-323">请记住，在加载启动场景时，会向用户显示全息初始屏幕。</span><span class="sxs-lookup"><span data-stu-id="5307e-323">Remember that while the startup scene is loading, the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="5307e-324">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5307e-324">See also</span></span>
- [<span data-ttu-id="5307e-325">优化 Unity 游戏中的图形渲染</span><span class="sxs-lookup"><span data-stu-id="5307e-325">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="5307e-326">优化 Unity 游戏中的垃圾回收</span><span class="sxs-lookup"><span data-stu-id="5307e-326">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="5307e-327">[物理学最佳做法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="5307e-327">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="5307e-328">[优化脚本 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="5307e-328">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>