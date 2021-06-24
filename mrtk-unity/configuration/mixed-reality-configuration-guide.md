---
title: 混合现实配置指南
description: 用于将 MRTK 配置为 Unity 的文档。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，
ms.openlocfilehash: a8aca05b4a4bc154061d6f7594e5128ab91d5f0e
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588867"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a>混合现实工具包配置文件配置指南

混合现实工具包将尽可能多的配置用于管理工具包， (除了真正的运行时 "内容" ) 。

本指南是一个简单的演练，适用于当前适用于该工具包的每个配置文件屏蔽。

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>主要混合现实工具包配置文件

主配置文件（附加到场景中的 *MixedRealityToolkit* GameObject）提供项目中工具包的主入口点。

> [!NOTE]
> 混合现实工具包 "锁定" 默认配置屏幕以确保你始终具有项目的一个公共起点，并且建议在项目演变后开始定义自己的设置。 在播放模式下，不能编辑 MRTK 配置。

![MRTK 配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

混合现实工具包的所有 "默认" 配置文件均可在 SDK 项目中的文件夹 "资产/MRTK/SDK/配置文件" 中找到。

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile 针对 HoloLens 2 进行了优化。 有关详细信息，请参阅 [配置文件](../features/profiles/profiles.md) 。

打开主混合现实工具包配置文件时，检查器中会显示以下屏幕：

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

如果在场景中选择不包含 MixedRealityToolkit 的 MixedRealityToolkitConfigurationProfile 资产，则会询问你是否希望 MRTK 自动为你安装场景。 这是可选的，但是，场景中必须有一个活动的 MixedRealityToolkit 对象才能访问所有配置屏幕。

这会承载项目的当前活动运行时配置。

从这里，你可以导航到 MRTK 的所有配置文件，包括：

- [混合现实工具包配置文件配置指南](#mixed-reality-toolkit-profile-configuration-guide)
  - [主要混合现实工具包配置文件](#the-main-mixed-reality-toolkit-configuration-profile)
  - [体验设置](#experience-settings)
  - [相机设置](#camera-settings)
  - [输入系统设置](#input-system-settings)
  - [边界可视化设置](#boundary-visualization-settings)
  - [Teleportation 系统选择](#teleportation-system-selection)
  - [空间感知设置](#spatial-awareness-settings)
  - [诊断设置](#diagnostics-settings)
  - [场景系统设置](#scene-system-settings)
  - [其他服务设置](#additional-services-settings)
  - [输入操作设置](#input-actions-settings)
  - [输入操作规则](#input-actions-rules)
  - [指针配置](#pointer-configuration)
  - [手势配置](#gestures-configuration)
  - [语音命令](#speech-commands)
  - [控制器映射配置](#controller-mapping-configuration)
  - [控制器可视化设置](#controller-visualization-settings)
  - [编辑器实用工具](#editor-utilities)
    - [服务检查器](#service-inspectors)
    - [深度缓冲区呈现器](#depth-buffer-renderer)
  - [在运行时更改配置文件](#changing-profiles-at-runtime)
    - [预 MRTK 初始化配置文件开关](#pre-mrtk-initialization-profile-switch)
    - [活动配置文件开关](#active-profile-switch)
  - [另请参阅](#see-also)

下面详细介绍了这些配置文件：

---
<a name="experience"></a>

## <a name="experience-settings"></a>体验设置

位于 "主混合现实工具包配置" 页上，此设置定义项目的 [混合现实环境规模](/windows/mixed-reality/coordinate-systems-in-unity) 的默认操作。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>相机设置

相机设置定义如何为混合现实项目设置照相机，定义一般剪辑、质量和透明度设置。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>输入系统设置

混合现实项目提供了一个功能强大的经过训练的输入系统，用于路由默认情况下选择的项目的所有输入事件。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

MRTK 提供的输入系统后面是多个其他系统，它们有助于推动和管理复杂的 weavings，以抽象出多平台/混合现实框架的复杂性。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

下面详细介绍了每个配置文件：

- 焦点设置
- [输入操作设置](#input-actions-settings)
- [输入操作规则](#input-actions-rules)
- [指针配置](#pointer-configuration)
- [手势配置](#gestures-configuration)
- [语音命令](#speech-commands)
- [控制器映射配置](#controller-mapping-configuration)
- [控制器可视化设置](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>边界可视化设置

边界系统会转换由基础平台边界/监护人系统报告的感知边界。 边界可视化工具配置使你能够根据用户的位置自动显示场景中记录的边界。边界还会根据用户在场景中 teleports 的位置做出反应/更新。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Teleportation 系统选择

混合现实项目提供了一个功能完备的 Teleportation 系统，用于管理项目中的 Teleportation 事件，默认情况下处于选中状态。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>空间感知设置

混合现实项目提供重建的空间感知系统，用于在默认情况下选择的项目中使用空间扫描系统。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

混合现实工具包的空间感知配置使你能够定制系统的启动方式，无论应用程序是在应用程序启动时自动启动还是在以后以编程方式设置，还可以为视图字段设置范围。

它还允许您配置网格和图面设置，进一步自定义您的项目如何理解您的环境。

这仅适用于可提供扫描环境的设备。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>诊断设置

MRTK 的可选但非常有用的功能是插件诊断功能。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

诊断配置文件提供了几个简单的系统，可以在项目运行时进行监视，包括便捷的 On/Off 开关，用于在场景中启用/禁用显示面板。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>场景系统设置

MRTK 提供了此可选的服务，可帮助管理复杂的加法场景加载/卸载。 若要确定场景系统是否适合你的项目，请阅读 [场景系统入门指南。](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>其他服务设置

混合现实工具包的更高级的领域之一是其 [服务定位器模式](https://en.wikipedia.org/wiki/Service_locator_pattern) 实现，该实现允许向框架注册任何 "服务"。 这样，就可以轻松地使用新功能/系统扩展框架，还可以利用这些功能来注册自己的运行时组件。

任何注册的服务仍能充分利用所有 Unity 事件，而无需执行 MonoBehaviour 或笨单一实例模式的开销和成本。 这就允许在运行前台和后台进程（例如，生成系统、运行时游戏逻辑或几乎任何其他操作）时不具有场景开销的纯 c # 组件。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>输入操作设置

输入操作提供了一种方法，用于从运行时项目抽象任何物理交互和输入。 所有物理输入 (从控制器/手/鼠标/等) 转换为逻辑输入操作，以便在运行时项目中使用。 这可确保无论输入来自何处，项目只是在幕后将这些操作作为 "要执行的操作" 或 "交互" 来实现。

若要创建新的输入操作，只需单击 "添加新操作" 按钮并为其表示的内容输入友好文本名称即可。 然后，只需选择一个轴 (操作要传达的数据类型) ，或在物理控制器的情况下，它可以附加到的物理输入类型，例如：

| 轴约束 | 数据类型 | 描述 | 用法示例 |
| :--- | :--- | :--- | :--- |
| 无 | 无数据 | 用于空操作或事件 | 事件触发器 |
| 原始 (保留)  | object | 保留以供将来使用 | 空值 |
| 数码 | bool | 打开或关闭类型数据的布尔值 | 控制器按钮 |
| 单轴 | FLOAT | 单个精度数据值 | 范围输入，例如触发器 |
| 双轴 | Vector2 | 多个轴的双浮点类型日期 | Dpad 或 Thumbstick |
| 三个 Dof 位置 | Vector3 | 具有 3 个浮点轴的 中的位置类型数据 | 仅 3D 位置样式控制器 |
| 三个 Dof 旋转 | 四元 | 具有 4 个浮点轴的仅旋转输入 | 三度样式控制器，例如 Oculus Go 控制器 |
| 六个 Dof | 混合现实姿势 (Vector3、四元数)  | 包含 Vector3 和四元数组件的位置和旋转样式输入 | 运动控制器或指针 |

利用输入操作的事件不限于物理控制器，仍可在项目中使用，使运行时效果生成新操作。

> [!NOTE]
> 输入操作是在运行时无法编辑的少数组件之一，它们只是设计时配置。 在项目运行时，不应交换此配置文件，因为框架 (并且项目) 每个操作生成的 ID 的依赖关系。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>输入操作规则

输入操作规则提供了一种自动将中针对一个输入操作引发的事件转换为基于其数据值的不同操作的方法。 这些在框架中无缝管理，不会产生任何性能成本。

例如，将单个双轴输入事件从 中的 DPad 转换为 4 个对应的"Dpad Up"/"DPad 向下"/"Dpad 左侧"/"Dpad 右侧"操作 (如下图) 所示。

这也可在你自己的代码中完成。 但是，由于这是一种非常常见的模式，框架提供了一种机制来"开箱使用"

可以针对任何可用的输入轴配置输入操作规则。 但是，一个轴类型的输入操作可以转换为同一轴类型的另一个输入操作。 可以将双轴操作映射到另一个双轴操作，但不能映射到数字或无操作。

![输入操作规则配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>指针配置

指针用于驱动来自任何输入设备的场景中的交互性，从而对场景中的任何对象提供方向和命中测试 (该对象附加了碰撞体或是 UI 组件) 。 默认情况下，会自动为控制器、头戴显示设备配置 (/焦点) 和鼠标/触摸输入。

此外，还可使用混合现实工具包提供的众多行组件之一在活动场景中可视化指针，如果它们实现 MRTK IMixedRealityPointer 接口，也可以可视化自己的任何一个。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- 指向范围：确定所有指针（包括凝视）的全局指向范围。
- 指向光线广播层掩码：确定指针将针对哪些层进行光线广播。
- 调试绘制指向射线：用于可视化用于光线广播的射线的调试帮助程序。
- 调试绘制指向射线颜色：用于可视化的一组颜色。
- 凝视光标预制件：可轻松指定任何场景的全局凝视光标。

有一个附加的帮助器按钮，可根据需要快速跳转到凝视提供程序，以替代凝视的一些特定值。

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>笔势配置

手势是一种特定于系统的实现，允许将输入操作分配给各种 SDK 提供的各种"笔势"输入 (例如 HoloLens) 。

> [!NOTE]
> 当前的笔势实现仅适用于 HoloLens，并且将针对其他系统进行增强，因为将来这些系统将添加到工具包 (尚未) 。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>语音命令

与笔势一样，某些运行时平台语音转文本智能"命令"功能，能够生成 Unity 项目可以接收的命令。 此配置文件允许配置以下各项：

1. 常规设置 - 设置为"自动启动"或"手动启动"的"启动行为"确定是初始化输入系统启动时的 KeywordRecognizer，还是让项目决定何时初始化 KeywordRecognizer。 "识别置信度"用于初始化 Unity 的 [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)
2. 语音命令 - 注册"单词"，并将其转换为项目可以接收的输入操作。 如果需要，还可以将键盘操作附加到键盘操作。

> [!IMPORTANT]
> 系统目前仅在 Windows 10 平台（例如 HoloLens 和 Windows 10 桌面）上运行时支持语音，并且将针对其他系统进行增强，因为将来会添加到 MRTK 中 (尚未) 。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>控制器映射配置

混合现实工具包的核心配置屏幕之一是能够配置和映射项目可以使用的各种类型的控制器。

下面的配置屏幕允许配置工具包当前识别的任何控制器。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

MRTK 为以下控制器/系统提供默认配置：

- 鼠标 (包括三维空间鼠标支持) 
- 触摸屏手机
- Xbox 控制器
- Windows Mixed Reality控制器
- HoloLens 笔势
- 用于 WANVive Wand 控制器的
- Oculus Touch 控制器
- Oculus 远程控制器
- 通用 OpenVR 设备 (高级用户) 

单击任何预建控制器系统的"映像"，可以针对其所有相应输入配置单个输入操作，例如，请参阅下面的 Oculus Touch 控制器配置屏幕：

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

还有一个高级屏幕，用于配置上面未标识的其他 OpenVR 或 Unity 输入控制器。

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>控制器可视化设置

除了控制器映射，还提供了单独的配置文件来自定义控制器在场景中的显示方式。

可以在控制器的所有实例的"全局" (配置此配置，) 或特定于单个控制器类型/手部。

MRTK 还支持适用于 Windows Mixed Reality OpenVR 的本机 SDK 控制器模型。 这些对象作为 GameObjects 加载到场景中，使用平台的控制器跟踪进行定位。

如果场景中的控制器表示形式需要与物理控制器位置偏移，则只需针对控制器模型的预制项设置该偏移量 (例如，使用偏移位置) 设置控制器预制的转换位置。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>编辑器实用工具

以下实用工具仅在编辑器中工作，可用于提高开发效率。

![MRTK 编辑器配置实用工具](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>服务检查器

服务检查器是一项仅编辑器功能，可生成表示活动服务的场景中对象。 选择这些对象将显示检查器，这些检查器提供文档链接、控制编辑器可视化效果和深入了解服务状态。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

可以通过在配置文件的"编辑器设置"下选中"使用服务 *检查* 器" *来* 启用服务检查器。

### <a name="depth-buffer-renderer"></a>深度缓冲区呈现器

与一些混合现实平台共享深度缓冲区可以提高 [全息影像稳定性](../performance/hologram-stabilization.md)。 例如，Windows Mixed Reality平台可以修改每个像素呈现的场景，以考虑呈现帧所花时间的细微头部运动。 但是，这些技术需要使用具有准确数据的深度缓冲区来了解几何图形与用户的位置和距离。

为了确保场景将所有必要的数据呈现到深度缓冲区，开发人员可以在配置文件中的"编辑器设置"下切换"呈现深度缓冲区"功能。 这会采用当前深度缓冲区，通过向主相机应用后处理效果，以颜色呈现给 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) 场景视图。

![渲染深度缓冲区实用工具 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>场景中的蓝色柱形具有 ZWrite 关闭的材料，因此不会写入深度数据</sup>

## <a name="changing-profiles-at-runtime"></a>在运行时更改配置文件

可以在运行时更新配置文件，通常有两种不同的方案和时间，这很有帮助：

1. **MRTK** 初始化配置文件开关：在启动时，在 MRTK 初始化和配置文件变为活动状态之前，替换尚未使用的配置文件，以基于设备功能启用/禁用不同的功能。 例如，如果体验在没有空间映射硬件的 VR 中运行，则启用空间映射组件可能没有意义。
1. **活动配置文件切换**：启动后，在 MRTK 初始化且配置文件变为活动状态后，交换当前使用的配置文件以更改某些功能的行为方式。 例如，应用程序中可能有特定的子体验需要完全删除远手指针。

### <a name="pre-mrtk-initialization-profile-switch"></a>PRE MRTK 初始化配置文件开关

为此，可将下面的 MonoBehaviour (示例附加到 MRTK 初始化之前运行的) ， (即唤醒 () ) 。 请注意，脚本 (例如，对 `SetProfileBeforeInitialization`) 的调用必须早于脚本执行 `MixedRealityToolkit` ，这可以通过设置 [脚本执行顺序设置](https://docs.unity3d.com/Manual/class-MonoManager.html)来实现。

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

 (例如，一组适用于特定平台的任意配置文件，而不是 "profileToUse"，例如，一个用于 VR，一个用于 VR 2，等等) 。 可以使用各种其他指标 (例如 https://docs.unity3d.com/ScriptReference/SystemInfo.html ，或照相机是否为不透明/透明) ，以确定要加载的配置文件。

### <a name="active-profile-switch"></a>活动配置文件开关

可以通过将 `MixedRealityToolkit.Instance.ActiveProfile` 属性设置为替换活动配置文件的新配置文件来完成此操作。

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

注意当在 `ActiveProfile` 运行时进行设置时，当前正在运行的服务将在所有服务的最后一个 behaviour () 之后发生，并且与新配置文件关联的服务的实例化和初始化将发生在所有服务的第一次更新 () 之前。

在此过程中可能会出现明显的应用程序毫不迟疑。 此外，任何优先级高于脚本的脚本 `MixedRealityToolkit` 都可以在正确设置新的配置文件之前输入其更新。 有关脚本优先级的详细信息，请参阅 [脚本执行顺序设置](https://docs.unity3d.com/Manual/class-MonoManager.html) 。

在配置文件切换过程中，现有的 UI 照相机会保持不变，确保在开关后需要画布的 Unity UI 组件仍可正常工作。

## <a name="see-also"></a>另请参阅

- [全息影像稳定化](../performance/hologram-stabilization.md)