---
title: MRTK 2.6 发行说明
description: MRTK 版本 2.6 的发行说明
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 4ac82f7e07135e840886fef810844ff00ef1ac1e
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647195"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Microsoft Mixed Reality Toolkit 2.6 发行说明

> [!IMPORTANT]
> 存在一个已知的编译器问题，该问题会影响使用 ARM64 为 Microsoft HoloLens 2 构建的应用程序。 此问题通过更新 2019 Visual Studio版本 16.8 或更高版本来修复。 如果无法更新Visual Studio，请 `com.microsoft.mixedreality.toolkit.tools` 导入包以应用解决方法。

## <a name="whats-new-in-262"></a>2.6.2 中的新增功能

### <a name="corrects-parenting-of-the-spatial-mesh"></a>更正空间网格的父级设置

修复了 [在](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) 移动混合现实 Playspace 对象后空间网格未正确定位的问题 (例如：通过远程端口) 。

## <a name="whats-new-in-261"></a>2.6.1 中的新增功能

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>修复了 OpenXR 未在 HoloLens 2/UWP 上运行的问题

修复了阻止 MRTK 的 OpenXR 支持在 UWP 上运行的回归。

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>修复了 Leap Motion ObjectManipulator 不旋转的问题

修复了 ObjectManipulator 脚本未考虑闰运动手旋转的回归。

### <a name="sample-scene-updates"></a>示例场景更新

更新场景理解示例场景，以正确反映 Unity 插件的已发货状态。 此外，将示例更新为不再依赖于正在导入的空间感知示例场景。 在更新到 2.6.1 之前，应删除导入的场景理解和空间感知示例（如果它们存在于项目中）以避免可能出现的冲突。 如果未删除这些示例，并且确实在控制台中看到了与这些示例相关的冲突，请删除示例 (或文件夹) ，然后 `Assets/Samples/Mixed Reality Toolkit Examples` 重试导入。

更新对话示例场景以正确描述当前对话方案。

## <a name="whats-new-in-260"></a>2.6.0 中的新增功能
<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>添加对 OpenXR 的支持

添加了对 Unity 的 OpenXR 预览包和 Microsoft 的混合现实 OpenXR 包的初始支持。 有关详细信息 [，请参阅 MRTK/XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)入门页 [、Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)论坛文章或 [Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) 文档。

> [!IMPORTANT]
> Unity 中的 OpenXR 仅在 Unity 2020.2 及更高版本上受支持。
>
> 目前，它还仅支持 x64 和 ARM64 生成。

### <a name="asset-swap-utility"></a>资产交换实用工具

使用新的资产交换实用工具 交换 Unity 场景中 [的多个资产](../features/tools/asset-swap-utility.md)。

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>MRTK 现在支持 HP 运动控制器

HP Reverb G2 的控制器现在本机与 MRTK 一起工作。

### <a name="experimental-interactive-element--state-visualizer"></a>实验交互式元素 + 状态可视化工具

Interactive 元素是 MRTK 输入系统的简化集中入口点。 它包含状态管理方法、事件管理和核心交互状态的状态设置逻辑。 有关详细信息，请参阅 [Interactive 元素文档](../features/experimental/interactive-element.md)。

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

状态可视化工具是依赖于 Interactive 元素的动画组件。  此组件创建动画剪辑、设置关键帧并生成动画器状态机。 有关详细信息，请参阅 [状态可视化工具文档](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>所有平台上现在都支持使用远程端口手势进行远程传送

用户现在可以使用远程端口手势跨所有平台移动其播放空间。 若要在具有默认配置的 MR 设备上通过控制器进行远程传送，请使用指纹。 若要使用可表达的手进行远程传送，请用手指朝上手势，同时将索引和滚动块朝外，通过卷起手指完成视区。 若要使用输入模拟进行远程传送，请参阅更新 [后的输入模拟服务文档](../features/input-simulation/input-simulation-service.md)。

  ![远程端口手势](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>场景理解现在以实验性空间感知观察器的身份在 MRTK 中提供

MRTK 2.6 [中引入了](/windows/mixed-reality/scene-understanding) 对场景理解的实验性支持。 用户可以在基于 MRTK 的项目中HoloLens 2空间感知观察器，将场景理解功能合并到一起。 有关详细信息， [请阅读场景理解](../features/spatial-awareness/scene-understanding.md) 文档。

> [!IMPORTANT]
> 场景理解仅在 HoloLens 2 Unity 2019.4 及更高版本上受支持。
>
> 此功能需要场景理解包，该包现在可通过混合现实 [功能工具 获得](https://aka.ms/MRFeatureTool)。
> 使用混合现实功能工具或通过 UPM 导入时，请在导入实验性 - 场景了解示例之前导入 Demos - SpatialAwareness 示例，因为存在依赖项问题。 有关详细信息 [，请参阅此 GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 问题。

  ![场景理解](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>运行时配置文件切换支持

MRTK 现在允许在 MRTK 实例初始化之前（即 MRT (K 初始化配置文件开关) 之前）和在配置文件处于活动状态后（即活动配置文件开关) ）之前进行配置文件切换 (。 前一个开关可用于基于硬件的功能启用选择组件，而后者可用于在用户输入应用程序的子部分时修改体验。 有关详细信息和 [代码示例，请阅读](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) 有关配置文件切换的文档。

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>方向指示器和关注从实验阶段中学习的求解器

两个新的求解器已准备好与主线 MRTK 一起使用。

  ![方向指示器求解器](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>手部教练从实验阶段中训练

手部指导功能现已准备好与主线 MRTK 一起使用。
  ![手部教练示例](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>从实验性中开始的对话控件

对话框控件现已准备好与主线 MRTK 一起使用。

  ![对话框控件](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>从实验性中培养的脉冲着色器

脉冲着色器脚本从实验阶段开始。 有关详细信息，请参阅： [脉冲着色器文档](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>输入录制服务改进

`InputRecordingService` 和 `InputPlaybackService` 现在可以录制和播放眼睛凝视输入。 录制经过优化，可确保在录制整个录制期间保持一致的帧速率，同时将文件大小和节省时间减少约 50%。 现在，可以异步执行录制文件的保存和加载。 请注意，此 MRTK 版本中记录的文件格式已更改，有关新版本 1.1 规范详细信息，请参阅此处。 [](../features/input-simulation/input-animation-file-format.md)

### <a name="reading-mode"></a>读取模式

添加了对读取[模式的支持，HoloLens 2。](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) 读取模式可减少系统的视场，但消除了 Unity 输出的缩放。 Unity 呈现的像素将对应于项目上HoloLens 2。 应用程序作者应该对多个人员进行测试，以确保这是他们希望在应用中进行权衡。

  ![Windows Mixed Reality读取模式](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>支持 UWP 上的 3D 应用启动器

添加了为 UWP 设置 [3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 应用启动器的能力。 此设置在"MRTK 生成窗口"和"MRTK 项目设置"下的"生成设置"中公开。 在 Unity 中生成期间，它会自动写入项目。

  ![生成设置](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>中断性变更

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>导入的 GLTF 对象的某些字段现已大写

由于反序列化相关问题，导入的 GLTF 对象的某些字段现在以大写字母开始。 受影响的字段 (名称中 `ComponentType`) ：、、 `Path` `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` 。

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>输入动画二进制文件具有更新版本 1.1 格式

和 使用的输入动画二进制文件现在具有更新的文件格式，以启用对这两个 `InputRecordingService` `InputPlaybackService` 服务的优化。 有关 [新版本](../features/input-simulation/input-animation-file-format.md) 1.1 规范的信息，请参阅此处。

### <a name="msbuild-for-unity-support"></a>MSBuild for Unity 支持

从 2.5.2 版开始，已移除对适用于 Unity 的 MSBuild 的支持，以与 Unity 的新包 [指南保持一致](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)。

## <a name="known-issues"></a>已知问题

### <a name="openxr"></a>OpenXR

全息远程处理和 OpenXR 当前存在一个已知问题，其中手部无法一致地可用。
此外，眼动跟踪示例场景当前不兼容，尽管眼动跟踪 *确实* 可以正常工作。

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>某些混合现实工具包标准着色器功能需要 Foundation 包

通过 Unity 程序包管理器 导入时，MRTK 标准着色器实用工具脚本 (例如：HoverLight.cs) 不会与标准资产包中的着色器共存。 若要访问此功能，应用程序需要导入 Foundation 包。

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache 可能在关闭时创建新的相机

在某些情况下 (例如，在 Unity 编辑器) 中使用 LeapMotion 提供程序时，CameraCache 可能会关闭时重新创建 MainCamera。 有关详细信息 [，请参阅](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 此问题。

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>通过 Unity 代码导入示例时，FileNotFoundException 程序包管理器

根据项目路径的长度，通过 Unity 命令导入示例程序包管理器 Unity 控制台中生成 FileNotFoundException 消息。 原因是"缺少"文件的路径超过 256 个字符MAX_PATH (256 个字符) 。 若要解决此问题，请缩短项目路径的长度。

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>未指定空间化程序。 应用程序将不支持空间声音

如果未配置音频空间化程序，则会出现"未指定空间化程序"警告。 如果未安装 XR 包，则可能会发生这种情况，因为 Unity 在这些包中包含空间化程序。

若要解决此问题，请确保：

- **窗口**  > **程序包管理器** 已安装一个或多个 XR 包
- **混合现实工具包**  > **实用工具**  > **配置 Unity 项目**，并针对音频空间 **化程序进行选择**

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

在面向独立平台 时，当前存在将 [Oculus XR 插件与 一起使用的已知问题](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)。  有关更新，请查看 Oculus bug 跟踪器/论坛/发行说明。

此 bug 由以下 3 个错误集表示：

![Oculus XR 插件错误](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI 和 TextMeshPro

较新版本的 TextMeshPro (1.5.0+ 或 2.1.1+) 存在已知问题，其中下拉列表的默认字号和粗体字体字符间距已更改。

![TMP 映像](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

可以通过降级到早期版本的 TextMeshPro 来这样做。 有关详细信息 [，#8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) 问题说明。