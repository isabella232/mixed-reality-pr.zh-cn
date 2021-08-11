---
title: MRTK 2.7 发行说明
description: MRTK 版本 2.7 发行说明
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK, XRSDK, 旧版 XR, Leap Motion, Ultraleap, OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 921cdb4d9643e55841bc7c979066c276f5fd80998ad97d19332c528cebe05c37
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203477"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Microsoft 混合现实工具包 2.7 发行说明

## <a name="whats-new-in-272"></a>2\.7.2 中的新增功能

### <a name="fixed-a-upm-package-dependency-issue"></a>修复了一个 UPM 包依赖关系问题

MRTK 2.7.1 UPM 包中存在一个未正确设置依赖关系的问题。 该问题会导致混合现实功能工具无法正确导入 MRTK 2.7.1 包。 该问题现已在 2.7.2 中得到解决。 与 2.7.1 相比，此版本中的代码未有更改。


## <a name="whats-new-in-271"></a>2\.7.1 中的新增功能

### <a name="show-version"></a>显示版本

`Mixed Reality` > `Toolkit` 菜单现在包含一个 `Show version...` 项，该项可用于检查混合现实工具包基础包，以确定项目所使用的 MRTK 版本。

![显示版本菜单](images/ShowVersionMenu.png)

![MRTK 版本对话框](images/VersionDialog.png)

> [!NOTE]
> 如果 MRTK 是从 [GitHub 存储库](https://aka.ms/mrtk)克隆的，则不会设置版本信息。
>
> ![无法确定版本](images/CannotDetermineVersion.png)

### <a name="authors-list"></a>作者列表

从 MRTK 2.7.1 开始，混合现实工具包基础包中包含了作者列表文件。

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a>在配置器设置流中集成了 OpenXR 项目设置

从 MRTK 2.7.1 开始，混合现实 OpenXR 插件的用户将收到有关如何通过 MRTK 设置该插件的说明。 有一个选项可供以 HoloLens 2 为目标的用户自动应用建议的设置。

![包含 OpenXR 设置说明的配置器窗口](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a>值得注意的 Bug 修复和更改

- 已将 Unity Joystick Manager 标记为在 XR SDK 管道上受支持 [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954)、[#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)
- 添加了对可交互检查器代码的检查，以防止出现 null 错误 [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)
- 在脉冲着色器示例场景中添加了 OpenXR 网格提供程序 [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)
- 在示例场景中还原了手部物理特性配置文件 [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)
- 对 HandConstraint* 脚本做了一些清理 [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)
- 修复了一些会影响创建和克隆配置文件的 bug [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)


## <a name="whats-new-in-270"></a>2\.7.0 中的新增功能

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR 现已在 MRTK 中正式受支持

随着新的 OpenXR 插件变得越来越成熟，MRTK 现已正式支持 OpenXR。 与以前的版本相比，我们在使用 OpenXR 的项目中添加了以下功能：

- [支持系统提供的运动控制器模型](#support-for-the-system-provided-motion-controller-model-on-openxr)
- 支持 WinMR 手势（选择、保持、操控和导航）[#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [支持控制器触觉](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [支持 HoloLens 2 上的铰接式手部网格](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- 支持 HoloLens 2 上的空间映射 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567)、[#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- 支持 HoloLens 2 上的场景理解 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

如果你通过 OpenXR 将 HoloLens 2 或 Windows Mixed Reality 头戴显示设备用作目标，请确保通过[混合现实功能工具](https://aka.ms/MRFeatureTool)安装/更新到混合现实 OpenXR 插件版本 0.9.5 或更高版本，否则你可能会错过上述某些改进。

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>现在可以在同一配置文件中使用旧版 XR 和 XR SDK 数据提供程序

现在，仅当选择了相应的管道时，才会加载数据提供程序，使得旧版 XR 和 XR SDK 数据提供程序可共存于同一个配置文件中。 为了适应这种变化，旧版 XR 和 XR SDK 数据提供程序现已组织在配置文件视图中的不同选项卡下，帮助用户确定他们是否对其目标 XR 管道使用了正确的配置文件。

![旧版数据提供程序和 XR SDK 数据提供程序现在可在单个配置文件下统一](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

为了适应这种变化，null 数据提供程序现在不再会加载并显示在配置文件检查器中。 用户可以在“编辑”->“项目设置”->“混合现实工具包”下切换 `Show null data providers in the profile inspector`，以调试在缺少数据提供程序时发生的意外行为。

![Null 数据提供程序现在默认已隐藏](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![切换“在配置文件检查器中显示 null 数据提供程序”设置](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>添加了体验设置和一个关联的混合现实场景内容行为

用户现在可以配置[体验设置](../features/experience-settings/experience-settings.md)，使得 MRTK 能够根据目标体验适当显示[混合现实场景内容](../features/experience-settings/scene-content.md)。

如果用户以前的“体验规模”设置与新的体验设置配置文件不匹配，系统会提示他们在检查器中进行更正

![体验规模迁移](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>重新设计的配置器现在会指导用户完成设置过程

新的 MRTK 配置器为用户提供分步指导，使他们能够正确配置项目以进行 XR 开发，并将其与 MRTK 配合使用。 在该配置器中可以选择 XR 管道、获取特定于平台的插件、导入 TextMeshPro，并显示示例（在使用 UPM 时）以及以前包含的为项目建议的设置。

![显示管道列表的配置器](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>正式推出了传送热点

已正式推出一个新的[传送热点组件](../features/teleport-system/teleport-hotspot.md)。 你可以将传送热点添加到 GameObject，以确保用户在传送到特定位置时处于该特定位置和方位。

![传送热点示例](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>正式推出了停留功能

在经过试验后，停留功能和示例现已正式推出。 示例场景中包含容积型 HoloLens 2 样式按钮的新示例。

![停留功能主图](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>添加了对 Leap Motion Unity 模块版本 4.6.0、4.7.0、4.7.1 和 4.8.0 的支持

对最新版 [Leap Motion Unity 模块](https://developer.leapmotion.com/unity)的支持现在与 MRTK 2.7.0 兼容。 有关详细信息，请参阅[如何为 Leap Motion 配置 MRTK](../supported-devices/leap-motion-mrtk.md)。

非常感谢 @jackyangzzh 为新的 LeapMotionOrientationExample 场景所做的贡献！

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>引发的目标语音事件不再局限于凝视指针

以前，只能对通过凝视指针聚焦的对象引发目标语音事件。 现在，通过任何指针聚焦的对象都可以接收语音事件。

![通过远端指针引发的语音事件](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>已将 TextToSpeech 从 HTK 移植到 MRTK

广受欢迎的 TextToSpeech 脚本现在终于可在 MRTK 中使用，以便帮助你在 UWP 平台上使用 [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) 从文本生成语音。 此外还添加了一个示例场景来演示该功能。

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>OpenXR 上支持系统提供的运动控制器模型

在 OpenXR 上添加了对系统提供的运动控制器模型的支持（在编辑器中以及在运行时）。

![显示两个运动控制器模型的编辑器窗口](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>OpenXR 上支持 HoloLens 2 铰接式手部网格

![MRTK 示例场景中在设备上运行的手部网格](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>旧版 WMR、Windows XR 插件和 OpenXR 均支持控制器触觉

添加了旧版 WMR、Windows XR 插件和 OpenXR 对控制器触觉的支持。 [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Windows XR 插件支持眼动跟踪

添加了在使用 Windows XR 插件最低版本 2.7.0 (Unity 2019)、4.4.2 (Unity 2020) 和 5.2.2 (Unity 2021) 时的眼睛凝视支持。 [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>值得注意的 Bug 修复和更改

- 捏合检测变得更顺利。 现在更不容易出现意外中断捏合手势的情况。 [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- 现在，在设置标志后，具有对象操控器组件的对象在释放时会持续保持速度。 [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- 向后扫射现在会查找地面，帮助防止摄像头固定到环境中或用户将光标悬停在空白空间上的情况。[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject 现在是一个虚拟属性，可让用户更灵活地展开球体或戳击指针。 [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- 在显示可用的语音命令时，按钮现在会显示正确的关键字。 [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Oculus 控制器现在使用自身的独立可视化工具，防止 MRTK 可视化效果与 Oculus 集成包的可视化效果相冲突。 [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- 与键盘相关的脚本已更改，以便与最新 Unity 版本（2019.4.25+ 和 2020.3.2+）的行为相一致。 在该版本中，仍然存在会影响 HoloLens 的自动完成 bug 和 TMP 输入字段 bug（这两个 bug 都出现在 MRTK 的外部）。 有关详细信息，请参阅 [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) 和 [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724)。
- 改进了滚动对象集合的性能。 此外，还修复了一个导致集合中的 GameObject 在复制后丢失材料的问题。 [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813)、[#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- 在场景理解演示脚本中，添加了 `GetSceneObjectsOfType` 函数以检索特定种类的所有已观测到的场景对象。 [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524)、[#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- 在命令行生成工具中，只会将 `sceneList` 或 `sceneListFile` 标志（如果存在任一标志）指定的场景包含在生成中。 [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- 在生成工具中，有一个新选项可用于指定 `nuget.exe` 的路径，并使用该路径执行包还原，而无需使用 `msbuild`（默认选项）。 [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- 修复了使用 Windows XR 插件可能会导致手关节僵硬和手部网格数翻倍的问题。 [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- 修复了使用 Windows XR 插件的自动远程控制功能导致丢失输入和交互的问题。 [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- 修复了 BuildDeployWindow 尝试在无效注册表项中查询 Windows SDK 路径的问题。 [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- MRTK 的 glTF 导入器现在是可选的。 如果存在多个 glTF 导入器，可以通过将 `MRTK_GLTF_IMPORTER_OFF` 添加到自定义脚本定义符号来禁用 MRTK 的导入器。 [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- 修复了无法正常检测 OpenVR 上的指节控制器的问题。 [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- 减少了可视化手部网格时的每帧分配数 [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- 添加了一个菜单项用于启动 MRTK 示例包（在 Unity 包管理器中），以便更轻松地导入示例 [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- 减少了使用 Unity 2020.3 时显示的加载时间警告数。
- 添加了生成窗口功能文档：[访问页面](../features/tools/build-window.md)

## <a name="known-issues"></a>已知问题

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>音频演示缺少 asmdef 文件（UPM 包）

通过混合现实功能工具导入 MRTK 时，会使用 Unity 包管理器 UI 将示例和演示添加到项目。 导入音频演示后，`WindowsMicrophoneStreamDemo.unity` 场景的行为将不正常。 这是由于示例缺少 .asmdef 文件所致。

若要解决此[问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)，请执行以下步骤：

- 将 Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef 复制到“Assets/Samples/Mixed Reality Toolkit Examples”文件夹中
- 将复制的文件重命名为 Examples
- 打开 Examples 文件
- 在“名称”框中，将内容替换为 Examples
- 单击“应用”
- 生成并部署

将来的 MRTK 版本将修复此问题。

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>MRTK 生成窗口在 Unity 2020.3 中不停地触发“正在导入资产”对话框

Unity 2020.3 上的 MRTK 生成窗口存在一个已知[问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723)：在成功执行 UWP 生成后，“正在导入资产”对话框不会完成。 我们正在配合 Unity 调查此问题。

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Unity 2020 中出现 Text Mesh Pro 画布渲染器警告

使用 Unity 2020 时，大部分 MRTK 示例场景中都会记录以下警告：

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

[TextMeshPro 版本 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3) 中添加了画布渲染器警告。 这些警告不会影响 MRTK 的示例场景，可以从控制台中清除。 有关更多详细信息，请参阅[问题 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811)。