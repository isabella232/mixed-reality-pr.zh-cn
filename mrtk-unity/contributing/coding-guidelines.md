---
title: 编码准则
description: 参与 MRTK 时应遵循的编码原则和约定。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， C#，
ms.openlocfilehash: 122c51962c55796c037302c7b79cc4df643a47b7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121435"
---
# <a name="coding-guidelines"></a><span data-ttu-id="45e98-104">编码准则</span><span class="sxs-lookup"><span data-stu-id="45e98-104">Coding guidelines</span></span>

<span data-ttu-id="45e98-105">本文档概述了参与 MRTK 时应遵循的编码原则和约定。</span><span class="sxs-lookup"><span data-stu-id="45e98-105">This document outlines coding principles and conventions to follow when contributing to MRTK.</span></span>

---

## <a name="philosophy"></a><span data-ttu-id="45e98-106">哲学</span><span class="sxs-lookup"><span data-stu-id="45e98-106">Philosophy</span></span>

### <a name="be-concise-and-strive-for-simplicity"></a><span data-ttu-id="45e98-107">简洁明了，为简单起见而努力</span><span class="sxs-lookup"><span data-stu-id="45e98-107">Be concise and strive for simplicity</span></span>

<span data-ttu-id="45e98-108">最简单的解决方案通常是最佳解决方案。</span><span class="sxs-lookup"><span data-stu-id="45e98-108">The simplest solution is often the best.</span></span> <span data-ttu-id="45e98-109">这是这些指南的一个首要目标，应成为所有编码活动的目标。</span><span class="sxs-lookup"><span data-stu-id="45e98-109">This is an overriding aim of these guidelines and should be the goal of all coding activity.</span></span> <span data-ttu-id="45e98-110">简单一部分是简洁，并且与现有代码一致。</span><span class="sxs-lookup"><span data-stu-id="45e98-110">Part of being simple is being concise, and consistent with existing code.</span></span> <span data-ttu-id="45e98-111">尝试使代码保持简单。</span><span class="sxs-lookup"><span data-stu-id="45e98-111">Try to keep your code simple.</span></span>

<span data-ttu-id="45e98-112">读者只应遇到提供有用信息的项目。</span><span class="sxs-lookup"><span data-stu-id="45e98-112">Readers should only encounter artifacts that provide useful information.</span></span> <span data-ttu-id="45e98-113">例如，重新陈述明显情况的评论不会提供额外的信息，并增加干扰与信号比率。</span><span class="sxs-lookup"><span data-stu-id="45e98-113">For example, comments that restate what is obvious provide no extra information and increase the noise to signal ratio.</span></span>

<span data-ttu-id="45e98-114">使代码逻辑保持简单。</span><span class="sxs-lookup"><span data-stu-id="45e98-114">Keep code logic simple.</span></span> <span data-ttu-id="45e98-115">请注意，这不是有关使用最小行数、最小化标识符名称或大括号样式大小的语句，而是关于减少概念数量并通过熟悉的模式最大化这些概念的可见性的语句。</span><span class="sxs-lookup"><span data-stu-id="45e98-115">Note that this is not a statement about using the fewest number of lines, minimizing the size of identifier names or brace style, but about reducing the number of concepts and maximizing the visibility of those through familiar patterns.</span></span>

### <a name="produce-consistent-readable-code"></a><span data-ttu-id="45e98-116">生成一致的可读代码</span><span class="sxs-lookup"><span data-stu-id="45e98-116">Produce consistent, readable code</span></span>

<span data-ttu-id="45e98-117">代码可读性与低缺陷率相关。</span><span class="sxs-lookup"><span data-stu-id="45e98-117">Code readability is correlated with low defect rates.</span></span> <span data-ttu-id="45e98-118">努力创建易于阅读的代码。</span><span class="sxs-lookup"><span data-stu-id="45e98-118">Strive to create code that is easy to read.</span></span> <span data-ttu-id="45e98-119">努力创建具有简单逻辑的代码，并重新使用现有组件，因为它还有助于确保正确性。</span><span class="sxs-lookup"><span data-stu-id="45e98-119">Strive to create code that has simple logic and re-uses existing components as it will also help ensure correctness.</span></span>

<span data-ttu-id="45e98-120">从正确性的最基本细节到一致的样式和格式设置，所生成代码的所有详细信息都很重要。</span><span class="sxs-lookup"><span data-stu-id="45e98-120">All details of the code you produce matter, from the most basic detail of correctness to consistent style and formatting.</span></span> <span data-ttu-id="45e98-121">保持编码样式与已存在的样式一致，即使它不符合你的偏好。</span><span class="sxs-lookup"><span data-stu-id="45e98-121">Keep your coding style consistent with what already exists, even if it is not matching your preference.</span></span> <span data-ttu-id="45e98-122">这提高了整体代码库的可读性。</span><span class="sxs-lookup"><span data-stu-id="45e98-122">This increases the readability of the overall codebase.</span></span>

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a><span data-ttu-id="45e98-123">支持在编辑器和运行时配置组件</span><span class="sxs-lookup"><span data-stu-id="45e98-123">Support configuring components both in editor and at run-time</span></span>

<span data-ttu-id="45e98-124">MRTK 支持一组不同的用户 - 喜欢在 Unity 编辑器中配置组件和加载预制件的用户，以及需要实例化并配置运行时对象的用户。</span><span class="sxs-lookup"><span data-stu-id="45e98-124">MRTK supports a diverse set of users – people who prefer to configure components in the Unity editor and load prefabs, and people who need to instantiate and configure objects at run-time.</span></span>

<span data-ttu-id="45e98-125">所有代码都应通过向已保存场景中的 GameObject 添加组件，以及通过代码实例化该组件来工作。</span><span class="sxs-lookup"><span data-stu-id="45e98-125">All your code should work by BOTH adding a component to a GameObject in a saved scene, and by instantiating that component in code.</span></span> <span data-ttu-id="45e98-126">测试应包括一个测试用例，用于实例化预制件和实例化，并在运行时配置组件。</span><span class="sxs-lookup"><span data-stu-id="45e98-126">Tests should include a test case both for instantiating prefabs and instantiating, configuring the component at runtime.</span></span>

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a><span data-ttu-id="45e98-127">"在编辑器中播放"是首个和主要目标平台</span><span class="sxs-lookup"><span data-stu-id="45e98-127">Play-in-editor is your first and primary target platform</span></span>

<span data-ttu-id="45e98-128">"在编辑器中播放"是在 Unity 中进行访问的最快方法。</span><span class="sxs-lookup"><span data-stu-id="45e98-128">Play-In-Editor is the fastest way to iterate in Unity.</span></span> <span data-ttu-id="45e98-129">为客户提供快速进行访问的方法可以让他们更快开发解决方案并尝试更多想法。</span><span class="sxs-lookup"><span data-stu-id="45e98-129">Providing ways for our customers to iterate quickly allows them to both develop solutions more quickly and try out more ideas.</span></span> <span data-ttu-id="45e98-130">换句话说，最大化迭代速度可帮助客户实现更多目标。</span><span class="sxs-lookup"><span data-stu-id="45e98-130">In other words, maximizing the speed of iteration empowers our customers to achieve more.</span></span>

<span data-ttu-id="45e98-131">使一切在编辑器中正常工作，然后使其在任何其他平台上运行。</span><span class="sxs-lookup"><span data-stu-id="45e98-131">Make everything work in editor, then make it work on any other platform.</span></span> <span data-ttu-id="45e98-132">在编辑器中保持工作。</span><span class="sxs-lookup"><span data-stu-id="45e98-132">Keep it working in the editor.</span></span> <span data-ttu-id="45e98-133">将新平台添加到编辑器中很容易。</span><span class="sxs-lookup"><span data-stu-id="45e98-133">It is easy to add a new platform to Play-In-Editor.</span></span> <span data-ttu-id="45e98-134">如果应用仅在设备上工作，则很难让"播放编辑器"正常工作。</span><span class="sxs-lookup"><span data-stu-id="45e98-134">It is very difficult to get Play-In-Editor working if your app only works on a device.</span></span>

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a><span data-ttu-id="45e98-135">谨慎添加新的公共字段、属性、方法和序列化私有字段</span><span class="sxs-lookup"><span data-stu-id="45e98-135">Add new public fields, properties, methods and serialized private fields with care</span></span>

<span data-ttu-id="45e98-136">每次添加公共方法、字段、属性时，它都会成为 MRTK 的公共 API 图面的一部分。</span><span class="sxs-lookup"><span data-stu-id="45e98-136">Every time you add a public method, field, property, it becomes part of MRTK’s public API surface.</span></span> <span data-ttu-id="45e98-137">标有 的私有 `[SerializeField]` 字段还会向编辑器公开字段，这些字段是公共 API 图面的一部分。</span><span class="sxs-lookup"><span data-stu-id="45e98-137">Private fields marked with `[SerializeField]` also expose fields to the editor and are part of the public API surface.</span></span> <span data-ttu-id="45e98-138">其他人可能会使用该公共方法，使用公共字段配置自定义预制项，并依赖于它。</span><span class="sxs-lookup"><span data-stu-id="45e98-138">Other people might use that public method, configure custom prefabs with your public field, and take a dependency on it.</span></span>

<span data-ttu-id="45e98-139">应仔细检查新的公共成员。</span><span class="sxs-lookup"><span data-stu-id="45e98-139">New public members should be carefully examined.</span></span> <span data-ttu-id="45e98-140">将来需要维护任何公共字段。</span><span class="sxs-lookup"><span data-stu-id="45e98-140">Any public field will need to be maintained in the future.</span></span> <span data-ttu-id="45e98-141">请记住，如果公共字段的类型 (序列化的私有字段) MonoBehaviour 更改或删除，则可能会破坏其他人。</span><span class="sxs-lookup"><span data-stu-id="45e98-141">Remember that if the type of a public field (or serialized private field) changes or gets removed from a MonoBehaviour, that could break other people.</span></span> <span data-ttu-id="45e98-142">首先需要为发布弃用 字段，并且需要提供代码来迁移已采用依赖项的人的更改。</span><span class="sxs-lookup"><span data-stu-id="45e98-142">The field will need to first be deprecated for a release, and code to migrate changes for people that have taken dependencies would need to be provided.</span></span>

### <a name="prioritize-writing-tests"></a><span data-ttu-id="45e98-143">优先编写测试</span><span class="sxs-lookup"><span data-stu-id="45e98-143">Prioritize writing tests</span></span>

<span data-ttu-id="45e98-144">MRTK 是一个社区项目，由各种参与者修改。</span><span class="sxs-lookup"><span data-stu-id="45e98-144">MRTK is a community project, modified by a diverse range of contributors.</span></span> <span data-ttu-id="45e98-145">这些参与者可能不知道 bug 修复/功能的详细信息，并意外中断了你的功能。</span><span class="sxs-lookup"><span data-stu-id="45e98-145">These contributors may not know the details of your bug fix / feature, and accidentally break your feature.</span></span> <span data-ttu-id="45e98-146">[MRTK 在完成每个拉取请求](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) 之前运行持续集成测试。</span><span class="sxs-lookup"><span data-stu-id="45e98-146">[MRTK runs continuous integration tests](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) before completing every pull request.</span></span> <span data-ttu-id="45e98-147">无法签入中断测试的更改。</span><span class="sxs-lookup"><span data-stu-id="45e98-147">Changes that break tests cannot be checked in.</span></span> <span data-ttu-id="45e98-148">因此，测试是确保其他人不会破坏你的功能的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="45e98-148">Therefore, tests are the best way to ensure that other people do not break your feature.</span></span>

<span data-ttu-id="45e98-149">修复 bug 时，编写测试以确保它将来不会回归。</span><span class="sxs-lookup"><span data-stu-id="45e98-149">When you fix a bug, write a test to ensure it does not regress in the future.</span></span> <span data-ttu-id="45e98-150">如果添加功能，请编写验证功能是否正常工作的测试。</span><span class="sxs-lookup"><span data-stu-id="45e98-150">If adding a feature, write tests that verify your feature works.</span></span> <span data-ttu-id="45e98-151">这是除实验性功能之外的所有 UX 功能所必需。</span><span class="sxs-lookup"><span data-stu-id="45e98-151">This is required for all UX features except experimental features.</span></span>

## <a name="c-coding-conventions"></a><span data-ttu-id="45e98-152">C# 编码约定</span><span class="sxs-lookup"><span data-stu-id="45e98-152">C# Coding conventions</span></span>

### <a name="script-license-information-headers"></a><span data-ttu-id="45e98-153">脚本许可证信息标头</span><span class="sxs-lookup"><span data-stu-id="45e98-153">Script license information headers</span></span>

<span data-ttu-id="45e98-154">所有提供新文件的 Microsoft 员工都应在任何新文件的顶部添加以下标准许可证标头，如下所示：</span><span class="sxs-lookup"><span data-stu-id="45e98-154">All Microsoft employees contributing new files should add the following standard License header at the top of any new files, exactly as shown below:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a><span data-ttu-id="45e98-155">函数/方法摘要标头</span><span class="sxs-lookup"><span data-stu-id="45e98-155">Function / method summary headers</span></span>

<span data-ttu-id="45e98-156">发布给 MRTK 的所有公共类、结构、枚举、函数、属性、字段都应描述为其用途和使用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="45e98-156">All public classes, structs, enums, functions, properties, fields posted to the MRTK should be described as to its purpose and use, exactly as shown below:</span></span>

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

<span data-ttu-id="45e98-157">这可确保正确生成文档，并针对所有类、方法和属性分发文档。</span><span class="sxs-lookup"><span data-stu-id="45e98-157">This ensures documentation is properly generated and disseminated for all all classes, methods, and properties.</span></span>

<span data-ttu-id="45e98-158">任何在没有正确摘要标记的情况下提交的脚本文件都将被拒绝。</span><span class="sxs-lookup"><span data-stu-id="45e98-158">Any script files submitted without proper summary tags will be rejected.</span></span>

### <a name="mrtk-namespace-rules"></a><span data-ttu-id="45e98-159">MRTK 命名空间规则</span><span class="sxs-lookup"><span data-stu-id="45e98-159">MRTK namespace rules</span></span>

<span data-ttu-id="45e98-160">混合现实工具包使用基于特征的命名空间模型，其中所有基础命名空间以"Microsoft.MixedReality.Toolkit"开头。</span><span class="sxs-lookup"><span data-stu-id="45e98-160">The Mixed Reality Toolkit uses a feature based namespace model, where all foundational namespaces begin with "Microsoft.MixedReality.Toolkit".</span></span> <span data-ttu-id="45e98-161">一般情况下，无需指定工具包层 (例如：命名空间中的 Core、提供程序) 服务层。</span><span class="sxs-lookup"><span data-stu-id="45e98-161">In general, you need not specify the toolkit layer (ex: Core, Providers, Services) in your namespaces.</span></span>

<span data-ttu-id="45e98-162">当前定义的命名空间包括：</span><span class="sxs-lookup"><span data-stu-id="45e98-162">The currently defined namespaces are:</span></span>

- <span data-ttu-id="45e98-163">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="45e98-163">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="45e98-164">Microsoft.MixedReality.Toolkit.Boundary</span><span class="sxs-lookup"><span data-stu-id="45e98-164">Microsoft.MixedReality.Toolkit.Boundary</span></span>
- <span data-ttu-id="45e98-165">Microsoft.MixedReality.Toolkit.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="45e98-165">Microsoft.MixedReality.Toolkit.Diagnostics</span></span>
- <span data-ttu-id="45e98-166">Microsoft.MixedReality.Toolkit.Editor</span><span class="sxs-lookup"><span data-stu-id="45e98-166">Microsoft.MixedReality.Toolkit.Editor</span></span>
- <span data-ttu-id="45e98-167">Microsoft.MixedReality.Toolkit.Input</span><span class="sxs-lookup"><span data-stu-id="45e98-167">Microsoft.MixedReality.Toolkit.Input</span></span>
- <span data-ttu-id="45e98-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span><span class="sxs-lookup"><span data-stu-id="45e98-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span></span>
- <span data-ttu-id="45e98-169">Microsoft.MixedReality.Toolkit.Teleport</span><span class="sxs-lookup"><span data-stu-id="45e98-169">Microsoft.MixedReality.Toolkit.Teleport</span></span>
- <span data-ttu-id="45e98-170">Microsoft.MixedReality.Toolkit.Utilities</span><span class="sxs-lookup"><span data-stu-id="45e98-170">Microsoft.MixedReality.Toolkit.Utilities</span></span>

<span data-ttu-id="45e98-171">对于具有大量类型的命名空间，可以创建有限数量的子命名空间，帮助确定使用范围。</span><span class="sxs-lookup"><span data-stu-id="45e98-171">For namespaces with a large amount of types, it is acceptable to create a limited number of sub-namespaces to aid in scoping usage.</span></span>

<span data-ttu-id="45e98-172">省略接口、类或数据类型的命名空间将导致更改被阻止。</span><span class="sxs-lookup"><span data-stu-id="45e98-172">Omitting the namespace for an interface, class or data type will cause your change to be blocked.</span></span>

### <a name="adding-new-monobehaviour-scripts"></a><span data-ttu-id="45e98-173">添加新的 MonoBehaviour 脚本</span><span class="sxs-lookup"><span data-stu-id="45e98-173">Adding new MonoBehaviour scripts</span></span>

<span data-ttu-id="45e98-174">使用拉取请求添加新的 MonoBehaviour 脚本时，请确保将 属性 [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) 应用于所有适用的文件。</span><span class="sxs-lookup"><span data-stu-id="45e98-174">When adding new MonoBehaviour scripts with a pull request, ensure the [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="45e98-175">这可确保组件在编辑器中的"添加组件"按钮下 *易于* 发现。</span><span class="sxs-lookup"><span data-stu-id="45e98-175">This ensures the component is easily discoverable in the editor under the *Add Component* button.</span></span> <span data-ttu-id="45e98-176">如果组件无法在编辑器（如抽象类）中显示，则不需要特性标志。</span><span class="sxs-lookup"><span data-stu-id="45e98-176">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="45e98-177">在下面的示例中， *此处的"包* "应填充组件的包位置。</span><span class="sxs-lookup"><span data-stu-id="45e98-177">In the example below, the *Package here* should be filled with the package location of the component.</span></span> <span data-ttu-id="45e98-178">如果将项放在 *MRTK/SDK* 文件夹中，则包将为 *SDK*。</span><span class="sxs-lookup"><span data-stu-id="45e98-178">If placing an item in *MRTK/SDK* folder, then the package will be *SDK*.</span></span>

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a><span data-ttu-id="45e98-179">添加新的 Unity 检查器脚本</span><span class="sxs-lookup"><span data-stu-id="45e98-179">Adding new Unity inspector scripts</span></span>

<span data-ttu-id="45e98-180">通常，请尝试避免为 MRTK 组件创建自定义检查器脚本。</span><span class="sxs-lookup"><span data-stu-id="45e98-180">In general, try to avoid creating custom inspector scripts for MRTK components.</span></span> <span data-ttu-id="45e98-181">这会增加 Unity 引擎可以处理的代码库的额外开销和管理。</span><span class="sxs-lookup"><span data-stu-id="45e98-181">It adds additional overhead and management of the codebase that could be handled by the Unity engine.</span></span>

<span data-ttu-id="45e98-182">如果需要检查器类，请尝试使用 Unity 的 [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) 。</span><span class="sxs-lookup"><span data-stu-id="45e98-182">If an inspector class is necessary, try to use Unity's [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html).</span></span> <span data-ttu-id="45e98-183">这再次简化了检查器类，将大部分工作保留给 Unity。</span><span class="sxs-lookup"><span data-stu-id="45e98-183">This again simplifies the inspector class and leaves much of the work to Unity.</span></span>

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

<span data-ttu-id="45e98-184">如果检查器类中需要自定义呈现，请尝试使用 [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) 和 [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) 。</span><span class="sxs-lookup"><span data-stu-id="45e98-184">If custom rendering is required in the inspector class, try to utilize [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) and [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html).</span></span> <span data-ttu-id="45e98-185">这将确保 Unity 正确处理呈现嵌套预制和修改后的值。</span><span class="sxs-lookup"><span data-stu-id="45e98-185">This will ensure Unity correctly handles rendering nested prefabs and modified values.</span></span>

<span data-ttu-id="45e98-186">如果 [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) 由于自定义逻辑中的要求无法使用 ，请确保所有用法都包装在 周围 [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) 。</span><span class="sxs-lookup"><span data-stu-id="45e98-186">If [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) cannot be used due to a requirement in custom logic, ensure all usage is wrapped around a [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html).</span></span> <span data-ttu-id="45e98-187">这将确保 Unity 为具有给定属性的嵌套预制和已修改值正确呈现检查器。</span><span class="sxs-lookup"><span data-stu-id="45e98-187">This will ensure Unity renders the inspector correctly for nested prefabs and modified values with the given property.</span></span>

<span data-ttu-id="45e98-188">此外，请尝试使用 修饰自定义检查器类 [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) 。</span><span class="sxs-lookup"><span data-stu-id="45e98-188">Furthermore, try to decorate the custom inspector class with a [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html).</span></span> <span data-ttu-id="45e98-189">此标记可确保一起选择和修改场景中具有此组件的多个对象。</span><span class="sxs-lookup"><span data-stu-id="45e98-189">This tag ensure multiple objects with this component in the scene can be selected and modified together.</span></span> <span data-ttu-id="45e98-190">任何新的检查器类都应测试其代码在场景中的此情况下是否正常工作。</span><span class="sxs-lookup"><span data-stu-id="45e98-190">Any new inspector classes should test that their code works in this situation in the scene.</span></span>

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a><span data-ttu-id="45e98-191">添加新的 ScriptableObjects</span><span class="sxs-lookup"><span data-stu-id="45e98-191">Adding new ScriptableObjects</span></span>

<span data-ttu-id="45e98-192">添加新的 ScriptableObject 脚本时，请确保将 属性 [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) 应用于所有适用的文件。</span><span class="sxs-lookup"><span data-stu-id="45e98-192">When adding new ScriptableObject scripts, ensure the [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="45e98-193">这可确保通过资产创建菜单在编辑器中轻松发现组件。</span><span class="sxs-lookup"><span data-stu-id="45e98-193">This ensures the component is easily discoverable in the editor via the asset creation menus.</span></span> <span data-ttu-id="45e98-194">如果组件无法在编辑器（如抽象类）中显示，则不需要特性标志。</span><span class="sxs-lookup"><span data-stu-id="45e98-194">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="45e98-195">在下面的示例中， *子文件夹* 应填充 MRTK 子文件夹（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="45e98-195">In the example below, the *Subfolder* should be filled with the MRTK subfolder, if applicable.</span></span> <span data-ttu-id="45e98-196">如果将项放在 *MRTK/Providers* 文件夹中，则包将为 *提供程序*。</span><span class="sxs-lookup"><span data-stu-id="45e98-196">If placing an item in *MRTK/Providers* folder, then the package will be *Providers*.</span></span> <span data-ttu-id="45e98-197">如果将项放在 *MRTK/Core* 文件夹中，请将其设置为"配置文件"。</span><span class="sxs-lookup"><span data-stu-id="45e98-197">If placing an item in the *MRTK/Core* folder, set this to "Profiles".</span></span>

<span data-ttu-id="45e98-198">在下面的示例中 *，MyNewService |如果适用* ，应用新类的名称填充 MyNewProvider。</span><span class="sxs-lookup"><span data-stu-id="45e98-198">In the example below, the *MyNewService | MyNewProvider* should be filled with the your new class' name, if applicable.</span></span> <span data-ttu-id="45e98-199">如果将项放在 *MixedRealityToolkit* 文件夹中，请保留此字符串。</span><span class="sxs-lookup"><span data-stu-id="45e98-199">If placing an item in the *MixedRealityToolkit* folder, leave this string out.</span></span>

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a><span data-ttu-id="45e98-200">Logging</span><span class="sxs-lookup"><span data-stu-id="45e98-200">Logging</span></span>

<span data-ttu-id="45e98-201">添加新功能或更新现有功能时，请考虑将 DebugUtilities.LogVerbose 日志添加到对将来调试有用的有趣代码。</span><span class="sxs-lookup"><span data-stu-id="45e98-201">When adding new features or updating existing features, consider adding DebugUtilities.LogVerbose logs to interesting code that may be useful for future debugging.</span></span> <span data-ttu-id="45e98-202">此处在添加日志记录和添加的干扰与没有足够的日志记录之间做出权衡 (这会使诊断难以) 。</span><span class="sxs-lookup"><span data-stu-id="45e98-202">There's a tradeoff here between adding logging and the added noise and not enough logging (which makes diagnosis difficult).</span></span>

<span data-ttu-id="45e98-203">一个有趣的示例，其中日志记录对 (有效负载和有效负载) ：</span><span class="sxs-lookup"><span data-stu-id="45e98-203">An interesting example where having logging is useful (along with interesting payload):</span></span>

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

<span data-ttu-id="45e98-204">这种类型的日志记录可以帮助捕获问题，如 ，这些问题是由检测到不匹配的源和 [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) 源丢失事件引起的。</span><span class="sxs-lookup"><span data-stu-id="45e98-204">This type of logging can help catch issues like [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016), which were caused by mismatched source detected and source lost events.</span></span>

<span data-ttu-id="45e98-205">避免添加每个帧上发生的数据和事件的日志 - 理想情况下，日志记录应涵盖由不同用户输入驱动的"有趣的"事件 (即用户"单击"，以及记录) 的来自的更改和事件集。</span><span class="sxs-lookup"><span data-stu-id="45e98-205">Avoid adding logs for data and events that are occurring on every frame - ideally logging should cover "interesting" events driven by distinct user inputs (i.e. a "click" by a user and the set of changes and events that come from that are interesting to log).</span></span> <span data-ttu-id="45e98-206">每帧记录的"用户仍在按住手势"的状态并不有趣，并且会使日志重负。</span><span class="sxs-lookup"><span data-stu-id="45e98-206">The ongoing state of "user is still holding a gesture" logged every frame is not interesting and will overwhelm the logs.</span></span>

<span data-ttu-id="45e98-207">请注意，默认情况下不会启用此详细日志记录 (必须在诊断系统设置设置中启用) [](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)</span><span class="sxs-lookup"><span data-stu-id="45e98-207">Note that this verbose logging is not turned on by default (it must be enabled in the [Diagnostic System settings](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging))</span></span>

### <a name="spaces-vs-tabs"></a><span data-ttu-id="45e98-208">空格与制表符</span><span class="sxs-lookup"><span data-stu-id="45e98-208">Spaces vs tabs</span></span>

<span data-ttu-id="45e98-209">参与此项目时，请务必使用 4 个空格而不是制表符。</span><span class="sxs-lookup"><span data-stu-id="45e98-209">Please be sure to use 4 spaces instead of tabs when contributing to this project.</span></span>

### <a name="spacing"></a><span data-ttu-id="45e98-210">间距</span><span class="sxs-lookup"><span data-stu-id="45e98-210">Spacing</span></span>

<span data-ttu-id="45e98-211">请勿在方括号和括号之间添加其他空格：</span><span class="sxs-lookup"><span data-stu-id="45e98-211">Do not to add additional spaces between square brackets and parenthesis:</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-212">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-212">Don't</span></span>

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a><span data-ttu-id="45e98-213">要</span><span class="sxs-lookup"><span data-stu-id="45e98-213">Do</span></span>

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a><span data-ttu-id="45e98-214">命名约定</span><span class="sxs-lookup"><span data-stu-id="45e98-214">Naming conventions</span></span>

<span data-ttu-id="45e98-215">始终对 `PascalCase` 属性使用 。</span><span class="sxs-lookup"><span data-stu-id="45e98-215">Always use `PascalCase` for properties.</span></span> <span data-ttu-id="45e98-216">用于 `camelCase` 大多数字段，但 `PascalCase` 和 `static readonly` 字段 `const` 除外。</span><span class="sxs-lookup"><span data-stu-id="45e98-216">Use `camelCase` for most fields, except use `PascalCase` for `static readonly` and `const` fields.</span></span> <span data-ttu-id="45e98-217">唯一的例外是要求字段由 序列化的数据结构 `JsonUtility` 。</span><span class="sxs-lookup"><span data-stu-id="45e98-217">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`.</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-218">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-218">Don't</span></span>

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a><span data-ttu-id="45e98-219">要</span><span class="sxs-lookup"><span data-stu-id="45e98-219">Do</span></span>

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a><span data-ttu-id="45e98-220">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="45e98-220">Access modifiers</span></span>

<span data-ttu-id="45e98-221">始终声明所有字段、属性和方法的访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="45e98-221">Always declare an access modifier for all fields, properties and methods.</span></span>

- <span data-ttu-id="45e98-222">除非需要在派生类中重写所有 Unity API 方法，否则默认情况下所有 Unity API 方法 `private` 都应为 。</span><span class="sxs-lookup"><span data-stu-id="45e98-222">All Unity API Methods should be `private` by default, unless you need to override them in a derived class.</span></span> <span data-ttu-id="45e98-223">在这种情况下， `protected` 应使用 。</span><span class="sxs-lookup"><span data-stu-id="45e98-223">In this case `protected` should be used.</span></span>

- <span data-ttu-id="45e98-224">字段应始终为 `private` ，具有 `public` 或 `protected` 属性访问器。</span><span class="sxs-lookup"><span data-stu-id="45e98-224">Fields should always be `private`, with `public` or `protected` property accessors.</span></span>

- <span data-ttu-id="45e98-225">尽可能 [使用 expression-bodied](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) [成员和](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) 自动属性</span><span class="sxs-lookup"><span data-stu-id="45e98-225">Use [expression-bodied members](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) and [auto properties](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) where possible</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-226">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-226">Don't</span></span>

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a><span data-ttu-id="45e98-227">要</span><span class="sxs-lookup"><span data-stu-id="45e98-227">Do</span></span>

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a><span data-ttu-id="45e98-228">使用大括号</span><span class="sxs-lookup"><span data-stu-id="45e98-228">Use braces</span></span>

<span data-ttu-id="45e98-229">请始终在每个语句块后使用大括号，将其放在下一行。</span><span class="sxs-lookup"><span data-stu-id="45e98-229">Always use braces after each statement block, and place them on the next line.</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-230">禁止事项</span><span class="sxs-lookup"><span data-stu-id="45e98-230">Don't</span></span>

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a><span data-ttu-id="45e98-231">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-231">Don't</span></span>

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a><span data-ttu-id="45e98-232">要</span><span class="sxs-lookup"><span data-stu-id="45e98-232">Do</span></span>

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a><span data-ttu-id="45e98-233">公共类、结构以及枚举都应进入其自己的文件中</span><span class="sxs-lookup"><span data-stu-id="45e98-233">Public classes, structs, and enums should all go in their own files</span></span>

<span data-ttu-id="45e98-234">如果类、结构或枚举可成为私有的，则可以包括在同一文件中。</span><span class="sxs-lookup"><span data-stu-id="45e98-234">If the class, struct, or enum can be made private then it's okay to be included in the same file.</span></span>  <span data-ttu-id="45e98-235">这样可以避免 Unity 的编译问题，并确保发生正确的代码抽象，还减少了代码需要更改时的冲突和中断性变更。</span><span class="sxs-lookup"><span data-stu-id="45e98-235">This avoids compilations issues with Unity and ensure that proper code abstraction occurs, it also reduces conflicts and breaking changes when code needs to change.</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-236">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-236">Don't</span></span>

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="45e98-237">要</span><span class="sxs-lookup"><span data-stu-id="45e98-237">Do</span></span>

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="45e98-238">应做事项</span><span class="sxs-lookup"><span data-stu-id="45e98-238">Do</span></span>

<span data-ttu-id="45e98-239">MyStruct.cs</span><span class="sxs-lookup"><span data-stu-id="45e98-239">MyStruct.cs</span></span>

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

<span data-ttu-id="45e98-240">MyEnumType.cs</span><span class="sxs-lookup"><span data-stu-id="45e98-240">MyEnumType.cs</span></span>

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

<span data-ttu-id="45e98-241">MyClass.cs</span><span class="sxs-lookup"><span data-stu-id="45e98-241">MyClass.cs</span></span>

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a><span data-ttu-id="45e98-242">初始化枚举</span><span class="sxs-lookup"><span data-stu-id="45e98-242">Initialize enums</span></span>

<span data-ttu-id="45e98-243">为了确保从 0 开始正确初始化所有枚举，.NET 提供了一个整洁的快捷方式，只需将第一个 (起始值) 枚举。</span><span class="sxs-lookup"><span data-stu-id="45e98-243">To ensure all enums are initialized correctly starting at 0, .NET gives you a tidy shortcut to automatically initialize the enum by just adding the first (starter) value.</span></span> <span data-ttu-id="45e98-244"> (值 1 = 0 剩余值不是必需的) </span><span class="sxs-lookup"><span data-stu-id="45e98-244">(e.g Value 1 = 0 Remaining values are not required)</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-245">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-245">Don't</span></span>

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a><span data-ttu-id="45e98-246">要</span><span class="sxs-lookup"><span data-stu-id="45e98-246">Do</span></span>

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a><span data-ttu-id="45e98-247">相应扩展的订单枚举</span><span class="sxs-lookup"><span data-stu-id="45e98-247">Order enums for appropriate extension</span></span>

<span data-ttu-id="45e98-248">如果将来可能会扩展枚举，以便对枚举顶部的默认值排序，这可以确保枚举索引不受新增功能的影响，这一点至关重要。</span><span class="sxs-lookup"><span data-stu-id="45e98-248">It is critical that if an Enum is likely to be extended in the future, to order defaults at the top of the Enum, this ensures Enum indexes are not affected with new additions.</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-249">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-249">Don't</span></span>

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a><span data-ttu-id="45e98-250">要</span><span class="sxs-lookup"><span data-stu-id="45e98-250">Do</span></span>

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a><span data-ttu-id="45e98-251">查看位域的枚举用途</span><span class="sxs-lookup"><span data-stu-id="45e98-251">Review enum use for bitfields</span></span>

<span data-ttu-id="45e98-252">如果枚举可能需要多个状态作为值，例如，"手部 = 左&右"。</span><span class="sxs-lookup"><span data-stu-id="45e98-252">If there is a possibility for an enum to require multiple states as a value, e.g. Handedness = Left & Right.</span></span> <span data-ttu-id="45e98-253">然后，需使用 BitFlag 正确修饰枚举，才能正确使用枚举</span><span class="sxs-lookup"><span data-stu-id="45e98-253">Then the Enum needs to be decorated correctly with BitFlags to enable it to be used correctly</span></span>

<span data-ttu-id="45e98-254">Handedness.cs 文件对此有一个具体实现</span><span class="sxs-lookup"><span data-stu-id="45e98-254">The Handedness.cs file has a concrete implementation for this</span></span>

### <a name="dont"></a><span data-ttu-id="45e98-255">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-255">Don't</span></span>

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a><span data-ttu-id="45e98-256">要</span><span class="sxs-lookup"><span data-stu-id="45e98-256">Do</span></span>

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a><span data-ttu-id="45e98-257">硬编码的文件路径</span><span class="sxs-lookup"><span data-stu-id="45e98-257">Hard-coded file paths</span></span>

<span data-ttu-id="45e98-258">生成字符串文件路径（尤其是编写硬编码的字符串路径）时，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="45e98-258">When generating string file paths, and in particular writing hard-coded string paths, do the following:</span></span>

1. <span data-ttu-id="45e98-259">尽可能使用[ `Path` C# 的 API，](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8)例如 `Path.Combine` 或 `Path.GetFullPath` 。</span><span class="sxs-lookup"><span data-stu-id="45e98-259">Use C#'s [`Path` APIs](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) whenever possible such as `Path.Combine` or `Path.GetFullPath`.</span></span>
1. <span data-ttu-id="45e98-260">使用 / 或 [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) ，而不是 \ 或 \\ \\ 。</span><span class="sxs-lookup"><span data-stu-id="45e98-260">Use / or [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) instead of \ or \\\\.</span></span>

<span data-ttu-id="45e98-261">这些步骤可确保 MRTK 在基于 Windows 和 Unix 的系统上均有效。</span><span class="sxs-lookup"><span data-stu-id="45e98-261">These steps ensure that MRTK works on both Windows and Unix-based systems.</span></span>

### <a name="dont"></a><span data-ttu-id="45e98-262">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-262">Don't</span></span>

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a><span data-ttu-id="45e98-263">要</span><span class="sxs-lookup"><span data-stu-id="45e98-263">Do</span></span>

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a><span data-ttu-id="45e98-264">最佳做法，包括 Unity 建议</span><span class="sxs-lookup"><span data-stu-id="45e98-264">Best practices, including Unity recommendations</span></span>

<span data-ttu-id="45e98-265">此项目的一些目标平台需要考虑性能。</span><span class="sxs-lookup"><span data-stu-id="45e98-265">Some of the target platforms of this project require to take performance into consideration.</span></span> <span data-ttu-id="45e98-266">请记住，在紧密更新循环或算法中频繁调用的代码中分配内存时，请始终小心。</span><span class="sxs-lookup"><span data-stu-id="45e98-266">With this in mind always be careful when allocating memory in frequently called code in tight update loops or algorithms.</span></span>

### <a name="encapsulation"></a><span data-ttu-id="45e98-267">封装</span><span class="sxs-lookup"><span data-stu-id="45e98-267">Encapsulation</span></span>

<span data-ttu-id="45e98-268">如果需要从类或结构外部访问字段，请始终使用私有字段和公共属性。</span><span class="sxs-lookup"><span data-stu-id="45e98-268">Always use private fields and public properties if access to the field is needed from outside the class or struct.</span></span>  <span data-ttu-id="45e98-269">请确保共定位私有字段和公共属性。</span><span class="sxs-lookup"><span data-stu-id="45e98-269">Be sure to co-locate the private field and the public property.</span></span> <span data-ttu-id="45e98-270">这样一来，可以更轻松地一目了然地查看支持 属性和字段是否由脚本修改。</span><span class="sxs-lookup"><span data-stu-id="45e98-270">This makes it easier to see, at a glance, what backs the property and that the field is modifiable by script.</span></span>

> [!NOTE]
> <span data-ttu-id="45e98-271">唯一的例外是要求字段由 序列化的数据结构，其中数据类需要具有所有公共字段才能使序列化 `JsonUtility` 正常工作。</span><span class="sxs-lookup"><span data-stu-id="45e98-271">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`, where a data class is required to have all public fields for the serialization to work.</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-272">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-272">Don't</span></span>

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a><span data-ttu-id="45e98-273">要</span><span class="sxs-lookup"><span data-stu-id="45e98-273">Do</span></span>

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a><span data-ttu-id="45e98-274">缓存值，并尽可能在场景/预制中序列化这些值</span><span class="sxs-lookup"><span data-stu-id="45e98-274">Cache values and serialize them in the scene/prefab whenever possible</span></span>

<span data-ttu-id="45e98-275">考虑 HoloLens 后，最好优化场景中的性能和缓存引用，或预先设置以限制运行时内存分配。</span><span class="sxs-lookup"><span data-stu-id="45e98-275">With the HoloLens in mind, it's best to optimize for performance and cache references in the scene or prefab to limit runtime memory allocations.</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-276">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-276">Don't</span></span>

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a><span data-ttu-id="45e98-277">要</span><span class="sxs-lookup"><span data-stu-id="45e98-277">Do</span></span>

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a><span data-ttu-id="45e98-278">缓存对材料的引用，不要每次调用".material"</span><span class="sxs-lookup"><span data-stu-id="45e98-278">Cache references to materials, do not call the ".material" each time</span></span>

<span data-ttu-id="45e98-279">每次使用".material"时，Unity 都会创建新材料，如果未正确清理，则会导致内存泄漏。</span><span class="sxs-lookup"><span data-stu-id="45e98-279">Unity will create a new material each time you use ".material", which will cause a memory leak if not cleaned up properly.</span></span>

#### <a name="dont"></a><span data-ttu-id="45e98-280">不要</span><span class="sxs-lookup"><span data-stu-id="45e98-280">Don't</span></span>

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a><span data-ttu-id="45e98-281">要</span><span class="sxs-lookup"><span data-stu-id="45e98-281">Do</span></span>

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> <span data-ttu-id="45e98-282">或者，使用 Unity 的"SharedMaterial"属性，该属性不会每次引用材料时都创建新材料。</span><span class="sxs-lookup"><span data-stu-id="45e98-282">Alternatively, use Unity's "SharedMaterial" property which does not create a new material each time it is referenced.</span></span>

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a><span data-ttu-id="45e98-283">使用 [平台相关](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) 编译来确保工具包不会中断另一个平台上的生成</span><span class="sxs-lookup"><span data-stu-id="45e98-283">Use [platform dependent compilation](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) to ensure the Toolkit won't break the build on another platform</span></span>

- <span data-ttu-id="45e98-284">使用 `WINDOWS_UWP` 以使用特定于 UWP 的非 Unity API。</span><span class="sxs-lookup"><span data-stu-id="45e98-284">Use `WINDOWS_UWP` in order to use UWP-specific, non-Unity APIs.</span></span> <span data-ttu-id="45e98-285">这会阻止它们尝试在编辑器中或不受支持的平台中运行。</span><span class="sxs-lookup"><span data-stu-id="45e98-285">This will prevent them from trying to run in the Editor or on unsupported platforms.</span></span> <span data-ttu-id="45e98-286">这等效于 `UNITY_WSA && !UNITY_EDITOR` ，应该用于支持 。</span><span class="sxs-lookup"><span data-stu-id="45e98-286">This is equivalent to `UNITY_WSA && !UNITY_EDITOR` and should be used in favor of.</span></span>
- <span data-ttu-id="45e98-287">使用 `UNITY_WSA` 使用特定于 UWP 的 Unity API，例如 `UnityEngine.XR.WSA` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="45e98-287">Use `UNITY_WSA` to use UWP-specific Unity APIs, such as the `UnityEngine.XR.WSA` namespace.</span></span> <span data-ttu-id="45e98-288">当平台设置为 UWP 时，这将在编辑器中运行，在内置 UWP 应用中运行。</span><span class="sxs-lookup"><span data-stu-id="45e98-288">This will run in the Editor when the platform is set to UWP, as well as in built UWP apps.</span></span>

<span data-ttu-id="45e98-289">此图表可帮助你根据用例和预期生成设置决定 `#if` 使用哪个。</span><span class="sxs-lookup"><span data-stu-id="45e98-289">This chart can help you decide which `#if` to use, depending on your use cases and the build settings you expect.</span></span>

|<span data-ttu-id="45e98-290">平台</span><span class="sxs-lookup"><span data-stu-id="45e98-290">Platform</span></span> | <span data-ttu-id="45e98-291">UWP IL2CPP</span><span class="sxs-lookup"><span data-stu-id="45e98-291">UWP IL2CPP</span></span> | <span data-ttu-id="45e98-292">UWP .NET</span><span class="sxs-lookup"><span data-stu-id="45e98-292">UWP .NET</span></span> | <span data-ttu-id="45e98-293">编辑器</span><span class="sxs-lookup"><span data-stu-id="45e98-293">Editor</span></span> |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | <span data-ttu-id="45e98-294">错误</span><span class="sxs-lookup"><span data-stu-id="45e98-294">False</span></span> | <span data-ttu-id="45e98-295">False</span><span class="sxs-lookup"><span data-stu-id="45e98-295">False</span></span> | <span data-ttu-id="45e98-296">True</span><span class="sxs-lookup"><span data-stu-id="45e98-296">True</span></span> |
| `UNITY_WSA` | <span data-ttu-id="45e98-297">True</span><span class="sxs-lookup"><span data-stu-id="45e98-297">True</span></span> | <span data-ttu-id="45e98-298">True</span><span class="sxs-lookup"><span data-stu-id="45e98-298">True</span></span> | <span data-ttu-id="45e98-299">True</span><span class="sxs-lookup"><span data-stu-id="45e98-299">True</span></span> |
| `WINDOWS_UWP` | <span data-ttu-id="45e98-300">True</span><span class="sxs-lookup"><span data-stu-id="45e98-300">True</span></span> | <span data-ttu-id="45e98-301">True</span><span class="sxs-lookup"><span data-stu-id="45e98-301">True</span></span> | <span data-ttu-id="45e98-302">False</span><span class="sxs-lookup"><span data-stu-id="45e98-302">False</span></span> |
| `UNITY_WSA && !UNITY_EDITOR` | <span data-ttu-id="45e98-303">True</span><span class="sxs-lookup"><span data-stu-id="45e98-303">True</span></span> | <span data-ttu-id="45e98-304">True</span><span class="sxs-lookup"><span data-stu-id="45e98-304">True</span></span> | <span data-ttu-id="45e98-305">False</span><span class="sxs-lookup"><span data-stu-id="45e98-305">False</span></span> |
| `ENABLE_WINMD_SUPPORT` | <span data-ttu-id="45e98-306">True</span><span class="sxs-lookup"><span data-stu-id="45e98-306">True</span></span> | <span data-ttu-id="45e98-307">True</span><span class="sxs-lookup"><span data-stu-id="45e98-307">True</span></span> | <span data-ttu-id="45e98-308">错误</span><span class="sxs-lookup"><span data-stu-id="45e98-308">False</span></span> |
| `NETFX_CORE` | <span data-ttu-id="45e98-309">False</span><span class="sxs-lookup"><span data-stu-id="45e98-309">False</span></span> | <span data-ttu-id="45e98-310">True</span><span class="sxs-lookup"><span data-stu-id="45e98-310">True</span></span> | <span data-ttu-id="45e98-311">错误</span><span class="sxs-lookup"><span data-stu-id="45e98-311">False</span></span> |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a><span data-ttu-id="45e98-312">优先使用日期时间 UtcNow。当前</span><span class="sxs-lookup"><span data-stu-id="45e98-312">Prefer DateTime.UtcNow over DateTime.Now</span></span>

<span data-ttu-id="45e98-313">UtcNow 的速度比日期时间快。</span><span class="sxs-lookup"><span data-stu-id="45e98-313">DateTime.UtcNow is faster than DateTime.Now.</span></span> <span data-ttu-id="45e98-314">在之前的性能调查中，我们发现使用日期时间。现在增加了大量开销，尤其是在更新 () 循环中使用时。</span><span class="sxs-lookup"><span data-stu-id="45e98-314">In previous performance investigations we've found that using DateTime.Now adds significant overhead especially when used in the Update() loop.</span></span> <span data-ttu-id="45e98-315">[其他人遇到了相同的问题](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)。</span><span class="sxs-lookup"><span data-stu-id="45e98-315">[Others have hit the same issue](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span></span>

<span data-ttu-id="45e98-316">首选使用 UtcNow，除非你实际需要本地化时间 (合理的原因可能是你想要在用户的时区) 中显示当前时间。</span><span class="sxs-lookup"><span data-stu-id="45e98-316">Prefer using DateTime.UtcNow unless you actually need the localized times (a legitimate reason may be you wanting to show the current time in the user's time zone).</span></span> <span data-ttu-id="45e98-317">如果您处理的是相对时间 (即，一些最后一个更新与现在) 之间的差异，则最好使用 UtcNow 来避免执行时区转换的开销。</span><span class="sxs-lookup"><span data-stu-id="45e98-317">If you are dealing with relative times (i.e. the delta between some last update and now), it's best to use DateTime.UtcNow to avoid the overhead of doing timezone conversions.</span></span>

## <a name="powershell-coding-conventions"></a><span data-ttu-id="45e98-318">PowerShell 编码约定</span><span class="sxs-lookup"><span data-stu-id="45e98-318">PowerShell coding conventions</span></span>

<span data-ttu-id="45e98-319">MRTK 基本代码的子集为管道基础结构和各种脚本和实用工具使用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45e98-319">A subset of the MRTK codebase uses PowerShell for pipeline infrastructure and various scripts and utilities.</span></span> <span data-ttu-id="45e98-320">新 PowerShell 代码应遵循 [PoshCode 样式](https://poshcode.gitbooks.io/powershell-practice-and-style/)。</span><span class="sxs-lookup"><span data-stu-id="45e98-320">New PowerShell code should follow the [PoshCode style](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span></span>

## <a name="see-also"></a><span data-ttu-id="45e98-321">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45e98-321">See also</span></span>

 [<span data-ttu-id="45e98-322">MSDN 中的 c # 编码约定</span><span class="sxs-lookup"><span data-stu-id="45e98-322">C# coding conventions from MSDN</span></span>](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)