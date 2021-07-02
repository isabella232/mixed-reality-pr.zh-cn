---
title: MRTK 配置文件配置指南
description: 将 MRTK 配置为 Unity 的文档。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity， HoloLens， HoloLens 2， 混合现实， 开发， MRTK，
ms.openlocfilehash: b7ec8d9ca2213ff998f94a6a2d029900ff886a2f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176409"
---
# <a name="mrtk-profile-configuration-guide"></a>MRTK 配置文件配置指南

混合现实Toolkit集中管理工具包所需的尽可能多的配置， (真正的运行时"操作") 。

本指南是当前可用于工具包的每个配置文件屏幕的简单演练。

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>主要混合现实Toolkit配置文件

附加到场景中 *的 MixedRealityToolkit* GameObject 的主配置文件为项目中的 Toolkit提供了主入口点。

> [!NOTE]
> 混合现实Toolkit"锁定"默认配置屏幕，以确保始终有项目的共同起点，建议随着项目的发展开始定义自己的设置。 在播放模式下，MRTK 配置不可编辑。

![MRTK 配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

混合现实应用的所有"默认"配置文件Toolkit资产/MRTK/SDK/Profiles 文件夹中的 SDK 项目中。

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile 已针对 HoloLens 2。 有关详细信息 [，](../features/profiles/profiles.md) 请参阅配置文件。

打开"混合现实"Toolkit配置文件"时，检查器中将看到以下屏幕：

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

如果在场景中选择没有 MixedRealityToolkitConfigurationProfile 资产的 MixedRealityToolkit，它会询问是否希望 MRTK 自动设置场景。 这是可选的，但是，场景中必须有一个活动的 MixedRealityToolkit 对象来访问所有配置屏幕。

这保存项目的当前活动运行时配置。

可在此处导航到 MRTK 的所有配置文件，包括：

- [混合现实Toolkit配置文件配置指南](#mrtk-profile-configuration-guide)
  - [主要混合现实Toolkit配置文件](#the-main-mixed-reality-toolkit-configuration-profile)
  - [体验设置](#experience-settings)
  - [相机设置](#camera-settings)
  - [输入系统设置](#input-system-settings)
  - [边界可视化设置](#boundary-visualization-settings)
  - [远程传送系统选择](#teleportation-system-selection)
  - [空间感知设置](#spatial-awareness-settings)
  - [诊断设置](#diagnostics-settings)
  - [场景系统设置](#scene-system-settings)
  - [其他服务设置](#additional-services-settings)
  - [输入操作设置](#input-actions-settings)
  - [输入操作规则](#input-actions-rules)
  - [指针配置](#pointer-configuration)
  - [笔势配置](#gestures-configuration)
  - [语音命令](#speech-commands)
  - [控制器映射配置](#controller-mapping-configuration)
  - [控制器可视化设置](#controller-visualization-settings)
  - [编辑器实用工具](#editor-utilities)
    - [服务检查器](#service-inspectors)
    - [深度缓冲区呈现器](#depth-buffer-renderer)
  - [在运行时更改配置文件](#changing-profiles-at-runtime)
    - [PRE MRTK 初始化配置文件开关](#pre-mrtk-initialization-profile-switch)
    - [活动配置文件开关](#active-profile-switch)
  - [另请参阅](#see-also)

以下相关部分详细介绍了这些配置文件：

---
<a name="experience"></a>

## <a name="experience-settings"></a>体验设置

此设置位于混合现实Toolkit配置页上，为项目定义[混合现实环境规模](/windows/mixed-reality/coordinate-systems-in-unity)的默认操作。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>相机设置

相机设置定义如何为混合现实项目设置相机，并定义通用剪辑、质量和透明度设置。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>输入系统设置

混合现实Project提供了一个可靠且经过良好训练的输入系统，用于路由默认选择的项目周围的所有输入事件。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

MRTK 提供的输入系统后面是其他几个系统，这些系统有助于推动和管理抽象出多平台/混合现实框架的复杂性所需的复杂互操作。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

下面详细介绍了每个配置文件：

- 焦点设置
- [输入操作设置](#input-actions-settings)
- [输入操作规则](#input-actions-rules)
- [指针配置](#pointer-configuration)
- [笔势配置](#gestures-configuration)
- [语音命令](#speech-commands)
- [控制器映射配置](#controller-mapping-configuration)
- [控制器可视化设置](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>边界可视化设置

边界系统转换基础平台边界/保护者系统报告的感知边界。 边界可视化工具配置使你可以自动显示场景中相对于用户位置的记录边界。边界还会根据用户在场景中的远程端口位置做出反应/更新。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>远程传送系统选择

混合现实Project提供了一个功能齐全的远程传送系统，用于管理项目中默认选择的远程传送事件。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>空间感知设置

混合现实Project提供了一个重新生成的空间感知系统，用于处理项目中默认选择的空间扫描系统。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

混合现实Toolkit空间感知配置可让你定制系统的启动方式，无论系统是在应用程序启动时自动启动还是稍后以编程方式启动，以及设置视场的区。

它还允许你配置网格和图面设置，进一步自定义项目如何理解你周围的环境。

这仅适用于可以提供扫描环境的设备。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>诊断设置

MRTK 的一个可选但非常有用的功能是插件诊断功能。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

诊断配置文件提供了多个在项目运行时监视的简单系统，包括一个方便的打开/关闭开关，用于启用/禁用场景中的显示面板。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>场景系统设置

MRTK 提供此可选服务，可帮助你管理复杂的附加场景加载/卸载。 若要确定场景系统是否适合你的项目，请阅读场景 [系统入门指南。](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>其他服务设置

混合现实平台的一个更高级Toolkit是它的服务定位器模式实现[](https://en.wikipedia.org/wiki/Service_locator_pattern)，它允许向框架注册任何"服务"。 这样，框架就可以轻松地通过新功能/系统进行扩展，但还允许项目利用这些功能来注册自己的运行时组件。

任何已注册的服务仍可充分利用所有 Unity 事件，无需开销和成本即可实现 MonoBehaviour 或 clunky 单一模式。 这样，纯 C# 组件就无需场景开销来同时运行前台进程和后台进程，例如生成系统、运行时游戏逻辑，或者几乎不需要任何其他内容。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>输入操作设置

输入操作提供了一种从运行时项目中抽象任何物理交互和输入的方法。 控制器/ (/鼠标/等) 输入的所有物理输入将转换为逻辑输入操作，以用于运行时项目。 这可确保无论输入来自何处，项目都只是在后台将这些操作实现为"要执行的操作"或"交互"。

若要创建新的输入操作，只需单击"添加新操作"按钮，并输入其表示的友好文本名称。 然后，只需选择 (数据类型的轴) 用于传达操作，或者对于物理控制器，它可附加到的物理输入类型，例如：

| 轴约束 | 数据类型 | 说明 | 用法示例 |
| :--- | :--- | :--- | :--- |
| 无 | 无数据 | 用于空操作或事件 | 事件触发器 |
| 原始 (预留)  | object | 保留以供将来使用 | 空值 |
| 数码 | bool | 类型数据上的布尔值 | 控制器按钮 |
| 单轴 | float | 单个精度数据值 | 范围输入，例如触发器 |
| 双轴 | Vector2 | 多轴的双浮点类型日期 | Dpad 或操纵杆 |
| 三个 Dof 位置 | Vector3 | 具有3个浮点轴的位置类型数据 | 仅限3D 位置样式控制器 |
| 三个 Dof 旋转 | 四元 | 仅旋转4浮点轴的输入 | 三度样式的控制器，例如 Oculus 控制器 |
| 6 Dof | 混合现实姿势 (System.numerics.vector2，四元数)  | 使用 System.numerics.vector2 和四元数分量的位置和旋转样式输入 | 运动控制器或指针 |

使用输入操作的事件并不限于物理控制器，仍可在项目中使用，以使运行时效果生成新的操作。

> [!NOTE]
> 输入操作是无法在运行时编辑的几个组件之一，它们只是设计时配置。 由于框架 (，不应将此配置文件换出，且项目) 依赖于为每个操作生成的 ID。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>输入操作规则

输入操作规则提供了一种方法，用于根据其数据值将对中的一个输入操作引发的事件自动转换为不同的操作。 它们在框架内无缝管理，不会产生任何性能开销。

例如，将单个双轴输入事件从中的 DPad 转换为4对应的 "Dpad Up"/"DPad 向下"/"Dpad 左"/"Dpad Right" 操作 (如下图所示) 。

也可以在自己的代码中完成此操作。 不过，由于这是一种非常常见的模式，因此框架提供了一种机制来实现这种 "现成"

可以为任何可用输入轴配置输入操作规则。 但是，可以将一个轴类型的输入操作转换为同一轴类型的另一个输入操作。 可以将双轴操作映射到另一个双轴操作，但不能映射到数字或无操作。

![输入操作规则配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>指针配置

指针用于驱动来自任何输入设备的场景中的交互性，同时为场景 (中附加了碰撞器或) 的 UI 组件提供方向和命中测试。 默认情况下，指针是自动配置的控制器、耳机 (注视/聚焦) 和鼠标/触控输入。

还可以使用混合现实 Toolkit 所提供的众多线条组件中的一个，或在实现 MRTK IMixedRealityPointer 接口时使用的任意行组件来在活动场景中进行可视化。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- 指向区区：确定所有指针的全局指向范围，包括 "注视"。
- 指向 Raycast 层掩码：确定将 Raycast 哪些层指针。
- 调试绘图指向射线：用于可视化用于 raycasting 的光线的调试帮助程序。
- 调试绘图指向射线颜色：用于可视化的一组颜色。
- 注视 cursor prefab：可轻松地为任何场景指定全局注视光标。

还有一个附加帮助器按钮，可快速跳转到注视提供商，以便在需要时重写某些特定值。

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>手势配置

手势是一种系统特定的实现，可用于将输入操作分配给各种 sdk (（例如 HoloLens) ）提供的各种 "手势" 输入方法。

> [!NOTE]
> 当前的手势实现仅适用于 HoloLens，并将在将来添加到 Toolkit 的其他系统中进行增强， (尚未) 任何日期。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>语音命令

与手势相似，某些运行时平台还提供智能的 "语音到文本" 功能，能够生成可由 Unity 项目接收的命令。 此配置文件允许你配置以下内容：

1. 常规设置-"启动行为" 设置为 "自动启动" 或 "手动启动" 确定是在输入系统启动时初始化 KeywordRecognizer，还是让项目决定何时初始化 KeywordRecognizer。 "识别置信度" 用于初始化 Unity 的 [KEYWORDRECOGNIZER API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)
2. 语音命令-注册 "单词" 并将其转换为可由您的项目接收的输入操作。 如果需要，还可以将它们附加到键盘操作。

> [!IMPORTANT]
> 在 Windows 10 平台上运行时，系统当前仅支持语音，例如 HoloLens 和 Windows 10 桌面，并将在将来添加到 MRTK 时，对其他系统进行增强， (尚未) 任何日期。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>控制器映射配置

混合现实 Toolkit 的核心配置屏幕之一是能够配置和映射项目可使用的各种类型的控制器。

使用下面的配置屏幕，可以配置该工具包当前识别的任何控制器。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

MRTK 为以下控制器/系统提供默认配置：

- 鼠标 (包括3D 空间鼠标支持) 
- 触摸屏手机
- Xbox 控制器
- Windows Mixed Reality 控制器
- HoloLens笔势
- HTC Naopak 杆控制器
- Oculus 触摸控制器
- Oculus 远程控制器
- 一般 OpenVR 设备 (高级用户仅) 

单击任意预建控制器系统的映像可为其所有相应输入配置单个输入操作，例如，请参阅下面的 Oculus Touch 控制器配置屏幕：

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

还提供了一个高级屏幕，用于配置上面未标识的其他 OpenVR 或 Unity 输入控制器。

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>控制器可视化设置

除了控制器映射外，还提供了一个单独的配置文件，用于自定义控制器在幕后中的呈现方式。

此配置可以在 "全局" (某个特定手) 控制器的所有实例，或特定于单个控制器类型/手。

MRTK 还支持 Windows Mixed Reality 和 OpenVR 的本机 SDK 控制器型号。 这些在场景中作为 Gameobject 加载，并使用平台的控制器跟踪进行定位。

如果场景中的控制器表示形式需要与物理控制器位置偏移，只需将该偏移量设置为与控制器模型的 prefab (例如，将控制器 prefab 的转换位置设置为偏移位置) 。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>编辑器实用工具

以下实用工具仅适用于编辑器，有助于提高开发工作效率。

![MRTK 编辑器配置实用工具](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>服务检查器

服务检查器是一项仅限编辑器的功能，用于生成代表活动服务的场景中对象。 选择这些对象将显示检查器，这些检查器提供文档链接、控制编辑器可视化对象和了解服务的状态。

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

可以通过在配置文件中选中 "*编辑器设置* 下的"*使用服务检查* 器 "来启用服务检查器。

### <a name="depth-buffer-renderer"></a>深度缓冲区呈现器

与一些混合现实平台共享深度缓冲区可以改善 [全息影像的稳定性](../performance/hologram-stabilization.md)。 例如，Windows Mixed Reality 平台可以修改呈现的场景每个像素，以在呈现帧所花的时间内进行微妙的打印头运动。 不过，这些技术需要具有准确数据的深度缓冲区来了解几何图形在用户中的位置和距离。

若要确保场景将所有所需数据呈现给深度缓冲区，开发人员可以在配置文件中的 *编辑器设置* 下切换 *呈现深度缓冲区* 功能。 这将采用当前深度缓冲区，并通过对主相机应用后处理效果，将其呈现为场景视图的颜色 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) 。

![呈现深度缓冲区实用程序 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>场景中的蓝色圆柱体的材料具有 ZWrite off，因此不会写入深度数据</sup>

## <a name="changing-profiles-at-runtime"></a>在运行时更改配置文件

在运行时可以更新配置文件，但在这种情况下，通常有两种不同的方案和时间：

1. **预 MRTK 初始化配置文件开关**：在启动时，在初始化 MRTK 之前，并将配置文件变为活动状态，替换不使用的配置文件，根据设备功能启用/禁用不同的功能。 例如，如果在不具有空间映射硬件的 VR 中运行体验，则启用空间映射组件可能没有意义。
1. **活动配置文件切换**：启动后，在初始化 MRTK 并激活配置文件后，交换当前正在使用的配置文件，以更改特定功能的行为方式。 例如，应用程序中可能有特定的子体验，需要完全删除最多的指针。

### <a name="pre-mrtk-initialization-profile-switch"></a>预 MRTK 初始化配置文件开关

为此，可以附加下面的 MonoBehaviour (示例) 该示例在 MRTK 初始化之前运行 (即唤醒 () ) 。 请注意， (脚本，即，) 的调用必须早于脚本执行，这可以通过设置脚本执行顺序 `SetProfileBeforeInitialization` `MixedRealityToolkit` 设置 [实现](https://docs.unity3d.com/Manual/class-MonoManager.html)。

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

除了"profileToUse"，还有一组适用于特定平台的任意配置文件（例如 (一个适用于 HoloLens 1、一个适用于 VR、一个适用于 HoloLens 2 等) 。 可以使用各种其他指示器（例如 (，或者相机是否不透明/透明) ，以确定要加载的 https://docs.unity3d.com/ScriptReference/SystemInfo.html 配置文件。

### <a name="active-profile-switch"></a>活动配置文件开关

可以通过将 属性设置为替换活动配置文件 `MixedRealityToolkit.Instance.ActiveProfile` 的新配置文件来完成此操作。

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

请注意，在运行时进行设置时，当前正在运行的服务的销毁将在所有服务的最后一个 LateUpdate () 之后发生，并且与新配置文件关联的服务实例化和初始化将在所有服务的第一个更新 () 之前发生。 `ActiveProfile`

此过程期间可能会出现明显的应用程序异常。 此外，优先级高于该脚本的任何脚本都可以在正确设置新配置文件之前输入 `MixedRealityToolkit` 其更新。 有关 [脚本优先级详细信息，](https://docs.unity3d.com/Manual/class-MonoManager.html) 请参阅脚本执行顺序设置。

在配置文件切换过程中，现有 UI 相机将保持不变，确保需要画布的 Unity UI 组件在切换后仍可正常工作。

## <a name="see-also"></a>另请参阅

- [全息影像稳定化](../performance/hologram-stabilization.md)
