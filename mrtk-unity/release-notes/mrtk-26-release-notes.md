---
title: MRTK 2.6 发行说明
description: MRTK 版本2.6 的发行说明
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，
ms.openlocfilehash: 452f0f352443620dea70b1680859bab4e2b3a0818de5f130accdb84c2798cfe0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206689"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Microsoft Mixed Reality Toolkit 2.6 发行说明

> [!IMPORTANT]
> 存在一个已知的编译器问题，它会影响使用 ARM64 为 Microsoft HoloLens 2 生成的应用程序。 此问题的解决方法是将 Visual Studio 2019 更新为16.8 或更高版本。 如果无法更新 Visual Studio，请导入 `com.microsoft.mixedreality.toolkit.tools` 包以应用解决方法。

## <a name="whats-new-in-262"></a>2.6.2 中的新增功能

### <a name="corrects-parenting-of-the-spatial-mesh"></a>纠正空间网格的父级

修复了在将混合现实 Playspace 对象移 (（例如：通过中转) ）移动后空间网格无法正确定位的 [问题](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) 。

## <a name="whats-new-in-261"></a>2.6.1 中的新增功能

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>修复 HoloLens 2/UWP 上未运行的 OpenXR

修复了一个回归，使 MRTK 的 OpenXR 支持无法在 UWP 上运行。

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>修复 Leap 运动 ObjectManipulator 不旋转

修复了 ObjectManipulator 脚本未考虑闰运动手旋转的回归。

### <a name="sample-scene-updates"></a>示例场景更新

更新场景了解示例场景，以正确反映 Unity 插件的已发布状态。 还将更新示例，使其不再依赖于要导入的空间感知示例场景。 更新到2.6.1 之前，应删除已导入的场景了解和空间感知示例（如果它们存在于你的项目中）以避免可能的冲突。 如果你未删除这些示例，并且看不到与控制台中的这些示例相关的冲突，请)  (或文件夹中删除示例， `Assets/Samples/Mixed Reality Toolkit Examples` 然后重试导入。

更新对话框示例场景，以正确描述当前的对话框方案。

## <a name="whats-new-in-260"></a>2.6.0 中的新增功能

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>添加对 OpenXR 的支持

添加了对 Unity 的 OpenXR 预览版包和 Microsoft Mixed Reality OpenXR 包的初始支持。 有关详细信息，请参阅 [MRTK/XRSDK 入门页](../configuration/getting-started-with-mrtk-and-xrsdk.md)、 [Unity 的论坛文章](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)或 [Microsoft 的文档](/windows/mixed-reality/develop/unity/openxr-getting-started) 。

> [!IMPORTANT]
> Unity 中的 OpenXR 仅在 Unity 2020.2 和更高版本上受支持。
>
> 目前，它还仅支持 x64 和 ARM64 生成。

### <a name="asset-swap-utility"></a>资产交换实用工具

使用新的 [资产交换实用工具](../features/tools/asset-swap-utility.md)在 Unity 场景中交换多个资产。

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>现在 MRTK 支持 HP 运动控制器

HP 回音 G2 的控制器现在可以使用 MRTK 在本机上运行。

### <a name="experimental-interactive-element--state-visualizer"></a>试验式交互式元素 + 状态可视化工具

Interactive 元素是 MRTK 输入系统的简化集中入口点。 它包含状态管理方法、事件管理和核心交互状态的状态设置逻辑。 有关详细信息，请参阅 [交互式元素文档](../features/experimental/interactive-element.md)。

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

状态可视化工具是依赖于交互式元素的动画组件。 此组件创建动画剪辑，设置关键帧并生成 Animator 状态机。 有关详细信息，请参阅 [状态可视化工具文档](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>现在，在所有平台上都支持带有传送手势的 Teleportation

用户现在可以使用 "传送" 手势在所有平台上四处移动其播放空间。 若要在具有默认配置的 MR 设备上传送控制器，请使用操纵杆。 若要传送有清晰的手势，请在掌上朝上，使用索引并拇指向外，通过运行食指完成传送。 若要传送输入模拟，请参阅更新的 [输入模拟服务文档](../features/input-simulation/input-simulation-service.md)。

![传送手势](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>场景理解现在可在 MRTK 中作为实验性空间识别观察程序提供

MRTK 2.6 中引入了对 [场景理解](/windows/mixed-reality/scene-understanding) 的实验性支持。 用户可以将 HoloLens 2 的场景理解功能合并为基于 MRTK 的项目中的空间感知观察程序。 有关详细信息，请阅读 [场景了解文档](../features/spatial-awareness/scene-understanding.md) 。

> [!IMPORTANT]
> 仅 HoloLens 2 和 Unity 2019.4 及更高版本支持场景理解。
>
> 此功能需要主题理解包，现可通过 [混合现实功能工具](https://aka.ms/MRFeatureTool)获得。
> 使用混合现实功能工具或通过 UPM 导入时，请导入 SpatialAwareness 示例，然后导入 SceneUnderstanding 示例，因为存在依赖关系问题。 有关详细信息，请参阅[此 GitHub 问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)。

![场景理解](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>运行时配置文件切换支持

MRTK 现在允许在初始化 MRTK 实例之前进行配置文件切换 (即，预 MRTK 初始化配置文件开关) ，并在配置文件处于活动状态后， (例如活动配置文件开关) 。 前者可用于基于硬件功能启用选择组件，而后者可用于在用户输入应用程序的细则时修改体验。 有关详细信息和代码示例，请阅读 [有关配置文件切换的文档](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) 。

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>方向指示器并遵循实验性的 solvers

两个新的 solvers 可以与主线 MRTK 一起使用。

![定向指示器求解器](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>从实验过渡的手势

"手形指导" 功能现已准备好用于主线 MRTK。

![手动指导示例](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>从实验渐变的对话框控件

对话框控件现在可与主线 MRTK 一起使用。

![对话框控件](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>从实验渐变的脉冲着色器

脉冲着色器脚本已从实验渐变。 有关详细信息，请参阅： [脉冲着色器文档](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>输入记录服务改进

`InputRecordingService``InputPlaybackService`现在，可以录制和播放眼睛眼睛输入。 记录已进行了优化，以确保在整个记录期间保持一致的帧速率，同时还会减少大约50% 的记录文件大小和节省时间。 现在可以异步执行记录文件的保存和加载。 注意此 MRTK 版本中记录的文件格式已更改，请参阅 [此处](../features/input-simulation/input-animation-file-format.md) ，了解有关新版1.1 规范的详细信息。

### <a name="reading-mode"></a>读取模式

添加了对 HoloLens 2 上[读取模式](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality)的支持。 读取模式缩小了系统的视图，但消除了 Unity 输出的缩放。 由 Unity 呈现的像素将与 HoloLens 2 上的投影像素相对应。 应用程序作者应该与多个用户进行测试，以确保在其应用中这一折衷。

![Windows Mixed Reality 读取模式](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>对 UWP 上的3D 应用启动器的支持

添加了设置适用于 UWP 的 [3d 应用程序启动器](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 的功能。 此设置在 "生成设置" 下的 "MRTK 生成" 窗口和 "MRTK Project" 设置中公开。 在 Unity 中生成的过程中，会自动将其写入项目。

![生成设置](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>中断性变更

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>导入的 GLTF 对象的某些字段现在为大写形式

由于与反序列化相关的问题，导入的 GLTF 对象的某些字段现在以大写字母开头。 受影响的字段在其新名称中 () ： `ComponentType` 、 `Path` 、 `Interpolation` 、 `Target` 、 `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` 、、、、和。

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>输入动画二进制文件具有更新版本1.1 格式

使用和提供的输入动画二进制 `InputRecordingService` 文件 `InputPlaybackService` 现在具有更新的文件格式，以启用对这两个服务的优化。 有关新版1.1 规范的详细信息，请参阅 [此处](../features/input-simulation/input-animation-file-format.md) 。

### <a name="msbuild-for-unity-support"></a>MSBuild 支持 Unity

2.5.2 版本已删除对 unity 的 MSBuild 支持，以与[Unity 的新包指南](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)保持一致。

## <a name="known-issues"></a>已知问题

### <a name="openxr"></a>OpenXR

目前存在一个与全息远程处理和 OpenXR 有关的已知问题，其中的手形并不一致。
此外，眼动跟踪示例场景当前不兼容，尽管眼动跟踪 _确实_ 可以正常工作。

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>某些混合现实Toolkit标准着色器功能需要 Foundation 包

通过 Unity 程序包管理器 导入时，MRTK 标准着色器实用工具脚本 (例如：HoverLight.cs) 不会与标准资产包中的着色器共存。 若要访问此功能，应用程序需要导入 Foundation 包。

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache 可能在关闭时创建新的相机

在某些情况下 (例如，在 Unity 编辑器) 中使用 LeapMotion 提供程序时，CameraCache 可能会关闭时重新创建 MainCamera。 有关详细信息 [，请参阅](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 此问题。

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>通过 Unity 代码导入示例时发生 FileNotFoundException 程序包管理器

根据项目路径的长度，通过 Unity 命令导入示例程序包管理器 Unity 控制台中生成 FileNotFoundException 消息。 原因是"缺少"文件的路径超过 256 个字符MAX_PATH (256 个字符) 。 若要解决此问题，请缩短项目路径的长度。

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>未指定空间化程序。 应用程序将不支持空间声音

如果未配置音频空间化程序，则会出现"未指定空间化程序"警告。 如果未安装 XR 包，则可能会发生这种情况，因为 Unity 在这些包中包含空间化程序。

若要解决此问题，请确保：

- **窗口**  > **程序包管理器** 已安装一个或多个 XR 包
- **混合现实Toolkit**  > **实用工具**  > **配置 Unity Project，** 并针对音频空间 **化程序进行选择**

  ![选择"音频空间化程序"](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException：对象引用未设置为实例化 (SceneTransitionService.Ini实例) 

在某些情况下，打开 `EyeTrackingDemo-00-RootScene` 可能会导致 SceneTransitionService 类的 Initialize 方法中出现 NullReferenceException。
此错误是由于未设置场景转换服务的配置文件。 若要解决此问题，请使用以下步骤：

- 导航到 `MixedRealityToolkit` 层次结构中的 对象
- 在"检查器"窗口中，选择 `Extensions`
- 如果未展开，则展开 `Scene Transition Service`
- 将 的值设置为 `Configuration Profile` **MRTKExamplesHubSceneTransitionServiceProfile**

![修复场景转换配置文件](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

在面向独立平台 时，当前存在将 [Oculus XR 插件与 一起使用的已知问题](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)。 有关更新，请查看 Oculus bug 跟踪器/论坛/发行说明。

此 bug 由以下 3 个错误集表示：

![Oculus XR 插件错误](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI 和 TextMeshPro

较新版本的 TextMeshPro (1.5.0+ 或 2.1.1+) 存在已知问题，其中下拉列表的默认字号和粗体字体字符间距已更改。

![TMP 映像](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

可以通过降级到早期版本的 TextMeshPro 来这样做。 有关详细信息 [，#8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 问题说明。
