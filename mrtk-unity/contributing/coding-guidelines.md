---
title: 编码指导原则
description: 编写 MRTK 时要遵循的编码原则和约定。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: 'Unity、HoloLens、HoloLens 2、混合现实、开发、MRTK、c #、'
ms.openlocfilehash: 8887e248bd550bdd7a59f19c16df1ec3647ceff7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145247"
---
# <a name="coding-guidelines"></a>编码准则

本文档概述了在 MRTK 时要遵循的编码原则和约定。

---

## <a name="philosophy"></a>理念

### <a name="be-concise-and-strive-for-simplicity"></a>简单易用

最简单的解决方案通常是最好的做法。 这是这些准则的替代目标，应是所有编码活动的目标。 很简单的部分非常简单，并且与现有代码保持一致。 尝试使代码简单。

读者应该只会遇到提供有用信息的项目。 例如，重述的注释会不提供额外的信息，也不会对信号比率增加干扰。

使代码逻辑保持简单。 请注意，这不是有关使用最少行数的语句，最大限度地减少标识符名称或大括号样式的大小，但要减少概念数量并通过熟悉的模式最大程度地实现这些概念的可见性。

### <a name="produce-consistent-readable-code"></a>生成一致、可读的代码

代码可读性与低缺陷率相关。 努力创建易于阅读的代码。 努力创建具有简单逻辑的代码，并重新使用现有组件，因为它还有助于确保正确性。

您生成的代码的所有详细信息，从正确性的最基本细节到一致的样式和格式设置。 使编码样式与已存在的内容保持一致，即使它不符合您的偏好。 这会提高总体代码库的可读性。

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>支持在编辑器和运行时配置组件

MRTK 支持一组不同的用户 - 喜欢在 Unity 编辑器中配置组件和加载预制件的用户，以及需要实例化并配置运行时对象的用户。

所有代码都应通过向已保存场景中的 GameObject 添加组件，以及通过代码实例化该组件来工作。 测试应包括一个测试用例，用于实例化预制件和实例化，并在运行时配置组件。

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>"在编辑器中播放"是首个和主要目标平台

"在编辑器中播放"是在 Unity 中进行访问的最快方法。 为客户提供快速进行访问的方法可以让他们更快开发解决方案并尝试更多想法。 换句话说，最大化迭代速度可帮助客户实现更多目标。

使一切在编辑器中正常工作，然后使其在任何其他平台上运行。 在编辑器中保持工作。 将新平台添加到编辑器中很容易。 如果应用仅在设备上工作，则很难让"播放编辑器"正常工作。

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>谨慎添加新的公共字段、属性、方法和序列化私有字段

每次添加公共方法、字段、属性时，它都会成为 MRTK 的公共 API 图面的一部分。 标有 的私有 `[SerializeField]` 字段还会向编辑器公开字段，这些字段是公共 API 图面的一部分。 其他人可能会使用该公共方法，使用公共字段配置自定义预制项，并依赖于它。

应仔细检查新的公共成员。 将来需要维护任何公共字段。 请记住，如果公共字段的类型 (序列化的私有字段) MonoBehaviour 更改或删除，则可能会破坏其他人。 首先需要为发布弃用 字段，并且需要提供代码来迁移已采用依赖项的人的更改。

### <a name="prioritize-writing-tests"></a>优先编写测试

MRTK 是一个社区项目，由不同的一系列参与者修改。 这些参与者可能不知道 bug 修复/功能的详细信息，并且意外中断了功能。 MRTK 在完成每个拉取请求之前[运行持续集成测试](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16)。 无法签入中断测试的更改。 因此，测试是确保其他人不会中断您的功能的最佳方式。

修复 bug 后，编写测试，以确保它不会在将来回退。 如果添加功能，请编写验证功能的测试。 这对于所有 UX 功能（实验功能除外）都是必需的。

## <a name="c-coding-conventions"></a>C # 编码约定

### <a name="script-license-information-headers"></a>脚本许可证信息标头

所有发布新文件的 Microsoft 员工应该在任何新文件的顶部添加以下标准许可证标头，如下所示：

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>函数/方法摘要标头

应将发布到 MRTK 的所有公共类、结构、枚举、函数、属性和字段描述为其用途和用法，如下所示：

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

这可确保正确生成文档并传送所有类、方法和属性。

将拒绝不带适当摘要标记提交的任何脚本文件。

### <a name="mrtk-namespace-rules"></a>MRTK 命名空间规则

混合现实工具包使用基于功能的命名空间模型，所有基础命名空间以 "MixedReality" 开头。 通常，你不需要在命名空间中指定工具包层 (例如： Core、Providers、Services) 。

当前定义的命名空间是：

- MixedReality 工具包
- MixedReality。
- MixedReality 诊断
- MixedReality。
- MixedReality。输入
- MixedReality. SpatialAwareness
- MixedReality。
- MixedReality。

对于具有大量类型的命名空间，可以创建有限数量的子命名空间，以帮助范围使用。

省略接口、类或数据类型的命名空间将导致更改被阻止。

### <a name="adding-new-monobehaviour-scripts"></a>添加新的 MonoBehaviour 脚本

使用拉取请求添加新的 MonoBehaviour 脚本时，请确保将该 [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) 属性应用于所有适用的文件。 这可确保在编辑器中的 " *添加组件* " 按钮下容易发现组件。 如果组件不能在编辑器（如抽象类）中显示，则不需要使用属性标志。

在下面的示例中，应在 *此处填写包* 的包位置。 如果将项放入 *MRTK/SDK* 文件夹，包将为 *SDK*。

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>添加新的 Unity 检查器脚本

一般情况下，请尽量避免为 MRTK 组件创建自定义检查器脚本。 它添加了可由 Unity 引擎处理的基本代码的额外开销和管理。

如果检查器类是必需的，请尝试使用 Unity 的 [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) 。 这再次简化了检查器类，将大部分工作保留给 Unity。

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

如果检查器类中需要自定义呈现，请尝试使用 [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) 和 [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) 。 这将确保 Unity 正确处理呈现嵌套预制和修改后的值。

如果 [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) 由于自定义逻辑中的要求无法使用 ，请确保所有用法都包装在 周围 [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) 。 这将确保 Unity 为具有给定属性的嵌套预制和已修改值正确呈现检查器。

此外，请尝试使用 修饰自定义检查器类 [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) 。 此标记可确保一起选择和修改场景中具有此组件的多个对象。 任何新的检查器类都应测试其代码在场景中的此情况下是否正常工作。

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

### <a name="adding-new-scriptableobjects"></a>添加新的 ScriptableObjects

添加新的 ScriptableObject 脚本时，请确保将 属性 [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) 应用于所有适用的文件。 这可确保通过资产创建菜单在编辑器中轻松发现组件。 如果组件无法在编辑器（如抽象类）中显示，则不需要特性标志。

在下面的示例中， *子文件夹* 应填充 MRTK 子文件夹（如果适用）。 如果将项放在 *MRTK/Providers* 文件夹中，则包将为 *提供程序*。 如果将项放在 *MRTK/Core* 文件夹中，请将其设置为"配置文件"。

在下面的示例中 *，MyNewService |如果适用* ，应用新类的名称填充 MyNewProvider。 如果将项放在 *MixedRealityToolkit* 文件夹中，请保留此字符串。

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>Logging

添加新功能或更新现有功能时，请考虑将 DebugUtilities.LogVerbose 日志添加到对将来调试有用的有趣代码。 此处在添加日志记录和添加的干扰与没有足够的日志记录之间做出权衡 (这会使诊断难以) 。

一个有趣的示例，其中日志记录对 (以及相关的负载) 很有用：

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

这种类型的日志记录有助于捕获类似的问题 [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) ，这是由于检测到的源不匹配和源丢失事件引起的。

避免为每个帧上发生的数据和事件添加日志-理想的日志记录应涵盖由不同用户输入驱动的 "有趣的" 事件， (例如，用户的 "单击" 事件和来自的一组更改和事件，这些事件对于记录) 很感兴趣。 记录的 "用户仍在保持手势" 状态，每个帧都不感兴趣，并且日志会严重影响日志。

请注意，默认情况下不启用此详细日志记录 (必须在 [诊断系统设置](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging) 中启用该日志记录) 

### <a name="spaces-vs-tabs"></a>空格与制表符

参与此项目时，请务必使用4个空格而不是选项卡。

### <a name="spacing"></a>间距

不要在方括号和圆括号之间添加其他空格：

#### <a name="dont"></a>不要

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a>要

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a>命名约定

始终 `PascalCase` 对属性使用。 `camelCase`对于大多数字段，使用 `PascalCase` `static readonly` 和 `const` 字段除外。 这种情况的唯一例外是对于需要通过序列化字段的数据结构 `JsonUtility` 。

#### <a name="dont"></a>不要

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a>要

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a>访问修饰符

始终为所有字段、属性和方法声明一个访问修饰符。

- 所有 Unity API 方法应 `private` 默认为默认值，除非需要在派生类中重写这些方法。 在这种情况下， `protected` 应该使用。

- 字段应始终为 `private` ，具有 `public` 或 `protected` 属性访问器。

- 尽可能使用[expression expression-bodied 成员](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members)和[auto 属性](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements)

#### <a name="dont"></a>不要

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a>要

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a>使用大括号

每个语句块后始终使用大括号，并将它们放在下一行。

#### <a name="dont"></a>禁止事项

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a>不要

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a>要

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

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>公共类、结构和枚举应全部位于各自的文件中

如果类、结构或枚举可以设为私有，则可以将其包含在同一文件中。  这样可以避免 Unity 的编译问题，并确保发生正确的代码抽象，还减少了代码需要更改时的冲突和中断性变更。

#### <a name="dont"></a>不要

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a>要

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a>应做事项

MyStruct.cs

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

MyEnumType.cs

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

MyClass.cs

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a>初始化枚举

为了确保从 0 开始正确初始化所有枚举，.NET 提供了一个整洁的快捷方式，只需将第一个 (起始值) 枚举。  (值 1 = 0 剩余值不是必需的) 

#### <a name="dont"></a>不要

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a>要

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a>相应扩展的订单枚举

如果将来可能会扩展枚举，以便对枚举顶部的默认值排序，这可以确保枚举索引不受新增功能的影响，这一点至关重要。

#### <a name="dont"></a>不要

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

#### <a name="do"></a>要

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

### <a name="review-enum-use-for-bitfields"></a>查看位域的枚举用途

如果枚举可能需要多个状态作为值，例如，"手部 = 左&右"。 然后，需使用 BitFlag 正确修饰枚举，才能正确使用枚举

Handedness.cs 文件对此有一个具体实现

### <a name="dont"></a>不要

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a>要

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

### <a name="hard-coded-file-paths"></a>硬编码的文件路径

生成字符串文件路径（尤其是编写硬编码的字符串路径）时，执行以下操作：

1. 尽可能使用[ `Path` C# 的 API，](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8)例如 `Path.Combine` 或 `Path.GetFullPath` 。
1. 使用 / 或 [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) ，而不是 \ 或 \\ \\ 。

这些步骤可确保 MRTK 在基于 Windows 和 Unix 的系统上均有效。

### <a name="dont"></a>不要

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a>要

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a>最佳做法，包括 Unity 建议

此项目的一些目标平台需要考虑性能。 考虑到这一点，在严格更新循环或算法中频繁调用的代码中，通常会小心地分配内存。

### <a name="encapsulation"></a>封装

如果需要从类或结构外部访问字段，请始终使用私有字段和公共属性。  请确保归置私有字段和公共属性。 这样一来，就可以更轻松地查看属性的作用，以及该字段可通过脚本进行修改。

> [!NOTE]
> 这种情况的唯一例外是，对于需要对这些字段进行序列化的数据结构 `JsonUtility` ，需要一个数据类以使序列化的所有公共字段都能正常工作。

#### <a name="dont"></a>不要

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

#### <a name="do"></a>要

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

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>尽可能缓存值并将其序列化到场景/prefab 中

考虑到 HoloLens，最佳做法是在场景或 prefab 中优化性能和缓存引用，以限制运行时内存分配。

#### <a name="dont"></a>不要

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a>要

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

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>缓存对材料的引用，请勿每次都调用 "材料"

每次使用 "材料" 时，Unity 都将创建新的材料，这会导致内存泄漏（如果未正确清理）。

#### <a name="dont"></a>不要

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

#### <a name="do"></a>要

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
> 或者，使用 Unity 的 "SharedMaterial" 属性，该属性在每次引用它时不会创建新的材料。

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>使用 [平台依赖编译](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) 来确保工具包不会将生成在另一个平台上中断

- 使用 `WINDOWS_UWP` 来使用 UWP 特定的非 Unity api。 这会阻止它们尝试在编辑器中或不受支持的平台上运行。 这等效于 `UNITY_WSA && !UNITY_EDITOR` 并且应使用来取代。
- 使用 `UNITY_WSA` 可以使用 UWP 特定的 Unity api，如 `UnityEngine.XR.WSA` 命名空间。 当平台设置为 UWP 时，以及在生成的 UWP 应用中，这将在编辑器中运行。

此图表可帮助你根据 `#if` 自己的用例和所需的生成设置来决定要使用哪个版本。

|平台 | UWP IL2CPP | UWP .NET | 编辑器 |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | False | False | True |
| `UNITY_WSA` | True | True | True |
| `WINDOWS_UWP` | True | True | False |
| `UNITY_WSA && !UNITY_EDITOR` | True | True | False |
| `ENABLE_WINMD_SUPPORT` | True | True | False |
| `NETFX_CORE` | False | True | False |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>优先使用日期时间 UtcNow。当前

DateTime.UtcNow 比 DateTime.Now 更快。 在以前的性能调查中，我们发现使用 DateTime.Now 会增加大量开销，尤其是在 Update () 循环中。 [另一些则出现相同的问题](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)。

首选使用 DateTime.UtcNow，除非实际需要本地化时间 (原因可能是你想要在用户的时区显示当前时间) 。 如果要处理相对时间 (即某些上次更新和现在) 之间的增量，则最好使用 DateTime.UtcNow 以避免执行时区转换的开销。

## <a name="powershell-coding-conventions"></a>PowerShell 编码约定

MRTK 代码库的子集将 PowerShell 用于管道基础结构和各种脚本和实用程序。 新的 PowerShell 代码应遵循 [PoshCode 样式](https://poshcode.gitbooks.io/powershell-practice-and-style/)。

## <a name="see-also"></a>另请参阅

 [MSDN 中的 C# 编码约定](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)