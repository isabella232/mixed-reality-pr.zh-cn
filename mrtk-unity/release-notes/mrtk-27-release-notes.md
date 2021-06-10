---
title: MRTK 2.7 发行说明
description: MRTK 版本 2.7 发行说明
author: RogPodge
ms.author: roliu
ms.date: 05/27/2021
ms.localizationpriority: medium
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， XRSDK， 旧版 XR， Leap Motion， Ultraleap
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 92c8705c70a2a6c1e25f1ed6b1f87eac1e5726e0
ms.sourcegitcommit: 11d5d7c3fdd59c1ebcfca34dbb6d84c05b481e5f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111897400"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Microsoft Mixed Reality Toolkit 2.7 发行说明

## <a name="whats-new-in-270"></a>2.7.0 中的新增功能

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>MRTK 中现已正式支持 OpenXR

随着新的 OpenXR 插件变得越来越成熟，MRTK 现在正式支持 OpenXR。 与以前的版本相比，我们使用 OpenXR 向项目添加了以下功能：

- [支持系统提供的动作控制器模型](#support-for-the-system-provided-motion-controller-model-on-openxr)
- 支持 WinMR 手势 (选择、按住、[操作和导航](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)) #9843
- [支持控制器触点](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [支持在手动网格上进行HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- 支持在 HoloLens 2 #9567[上#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567) [](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- 支持对场景进行场景 [HoloLens 2#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>旧式 XR 和 XR SDK 数据提供程序现在可以在同一配置文件中使用

现在，只有在选择了适当的管道时，才加载数据提供程序，从而允许旧式 XR 和 XR SDK 数据提供程序共存于同一配置文件中。 为了适应这种情况，旧版 XR 和 XR SDK 数据提供程序现在组织在配置文件视图中的不同选项卡下，帮助用户确定其目标 XR 管道是否具有正确的配置文件。

![旧式和 XR SDK 数据提供程序现在可以在单个配置文件下统一](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

为了适应这种情况，现在不再加载 null 数据提供程序并显示在配置文件检查器中。 用户可以在" `Show null data providers in the profile inspector` 编辑 **"->"项目设置"->混合现实工具包** "下切换，以调试缺少数据提供程序的意外行为。

![现在默认隐藏 Null 数据提供程序 在配置文件检查器中 ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ 切换显示 null 数据提供程序](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>添加了体验设置和关联的混合现实场景内容行为

用户现在可以配置["体验设置"，](../features/experience-settings/experience-settings.md)这将允许 MRTK[](../features/experience-settings/scene-content.md)根据目标体验适当地显示混合现实场景内容。

如果用户以前的体验缩放设置与新的体验设置配置文件不匹配，系统会在检查器中提示他们更正它

![体验缩放迁移](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>重新设计的配置器现在引导用户完成安装过程

新的 MRTK 配置器为用户提供分步指南，以正确配置项目以用于 XR 开发并用于 MRTK。 其中介绍了 XR 管道的选择、获取特定于平台的插件、导入 TextMeshPro、显示使用 UPM) 时的示例 (以及以前为项目提供的其他建议设置。

![显示管道列表的 Configurator](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>已伸缩的 Teleport 热点

新的 [远程端口热点组件](../features/teleport-system/teleport-hotspot.md) 已经过专业。 可以将远程端口热点添加到 GameObject，以确保用户在远程传送到该位置时处于特定位置和方向。

![Teleport 热点示例](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>已分居

停留特征和示例现已从实验阶段开始。 示例场景中包含HoloLens 2样式按钮的新示例。

![停留英雄](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>添加了对 Leap Motion Unity 模块版本 4.6.0、4.7.0、4.7.1 和 4.8.0 的支持

对最新版本的 Leap Motion [Unity 模块](https://developer.leapmotion.com/unity) 的支持现在与 MRTK 2.7.0 兼容。  有关详细信息[，请参阅如何为 Leap Motion 配置 MRTK。](../supported-devices/leap-motion-mrtk.md)

感谢贡献 @jackyangzzh 新的 LeapMotionOrientationExample 场景！

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>引发的目标语音事件不再局限于凝视指针

以前，只能在使用凝视指针聚焦的对象上引发目标语音事件。 现在，如果对象通过任何指针聚焦，则它们可以接收语音事件。

![具有远点指针的语音事件](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>从 HTK 移植到 MRTK 的 TextToSpeech

现在，MRTK 中最终提供了一个纯文本 TextToSpeech 脚本，可帮助你使用 从 UWP 平台上的文本生成语音 [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) 。 还添加了一个示例场景来演示该功能。

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>在 OpenXR 上支持系统提供的动作控制器模型

添加了对 OpenXR 上系统提供的动作控制器模型的支持（在编辑器中和运行时）。

![显示两个运动控制器模型的编辑器窗口](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>支持在 OpenXR HoloLens 2手部网格

![MRTK 示例场景中在设备上运行手动网格](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>支持跨旧版 WMR、Windows XR 插件和 OpenXR 的控制器触角

添加了对跨旧版 WMR、Windows XR 插件和 OpenXR 的控制器触角的支持。 [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>支持在 Windows XR 插件上进行眼动跟踪

添加了在使用 Windows XR 插件最低版本 2.7.0 (Unity 2019) 、4.4.2 (Unity 2020) 和 5.2.2 (Unity 2021) 时对眼睛凝视的支持。 [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>值得注意的 Bug 修复和更改

- 收缩检测更流畅。 现在更难意外删除收缩手势。 [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- 设置 标志时，具有对象操控器组件的对象现在一致地保持发布速度。 [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Back-strafing 现在会检查楼层，帮助防止相机卡入环境或用户将鼠标悬停在空白区域的情况。[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject 现在是一个虚拟属性，在扩展球体或圆球指针时允许更灵活。 [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- 现在，当显示可用的语音命令时，按钮会显示正确的关键字。 [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Oculus 控制器现在使用自己的独立可视化工具，防止 MRTK 可视化效果与 Oculus 集成包的可视化效果冲突。 [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- 与键盘相关的脚本已更改，以与最新 Unity 版本 (2019.4.25+ & 2020.3.2+) 中的行为保持一致。 自发布起，仍有一个自动完成 bug 和 TMP 输入字段 bug (在 MRTK 外部) 影响 HoloLens。 有关详细信息，请参阅[#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056)和[#9724。](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724)
- 改进了滚动对象集合的性能。 还修复了在复制时导致集合中的 GameObject 丢失材料的问题。 [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813) [、#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- 在"场景理解"演示脚本中，添加了 `GetSceneObjectsOfType` 用于检索所有观察到的某种类型的场景对象的 函数。 [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524) [、#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- 在命令行生成工具中，只有 或 标志指定的场景 (存在任何标志时) 将 `sceneList` `sceneListFile` 包含在生成中。 [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- 在生成工具中，有一个新选项指定的路径，并使用它来执行包还原，而不是使用 (`nuget.exe` `msbuild` 默认) 。 [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- 修复了使用 Windows XR 插件可能会导致手部连接过时和手部网格双倍的问题。 [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- 修复了使用 Windows XR 插件的自动远程处理功能导致缺少输入和交互的问题。 [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- 修复了 BuildDeployWindow 尝试查询路径的无效 reg 键Windows SDK的问题。 [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- MRTK 的 glTF 导入程序现在是可选的。 如果存在多个 glTF 导入程序，则可以通过将 添加到自定义脚本定义符号来禁用 `MRTK_GLTF_IMPORTER_OFF` MRTK。 [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- 修复了未正确检测到 OpenVR 上的 Knuckles 控制器的问题。 [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- 在可视化手部网格网格时减少每帧分配 [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- 添加了一个菜单项以在 Unity (中启动 MRTK 示例包程序包管理器) 以便更轻松地将示例导入 [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- 减少了使用 Unity 2020.3 时出现加载时警告的数量。
- 添加了生成窗口功能文档 [：请访问页面](/windows/mixed-reality/mrtk-unity/features/tools/build-window)

## <a name="known-issues"></a>已知问题

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>音频演示缺少 (UPM 包的 asmdef 文件) 

通过混合现实功能工具导入 MRTK 时，示例和演示将使用 Unity 包管理器 UI 添加到项目。 导入音频演示后， `WindowsMicrophoneStreamDemo.unity` 场景将无法正常运行。 这是示例缺少 asmdef 文件的结果。

若要解决此 [问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)，请执行以下步骤：

- Copy Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@ [...]/MRTK.示例 asmdef 到 "资产/示例/混合现实工具包示例" 文件夹
- 将复制的文件重命名为示例
- 打开示例文件
- 在 "名称" 框中，将内容替换为示例
- 单击“应用”
- 生成并部署

此问题将在即将发布的 MRTK 版本中解决。

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>MRTK 生成窗口触发 Unity 2020.3 中的 "导入资产" 对话框

Unity 2020.3 上的 MRTK 生成窗口存在一个已知 [问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) ，在成功执行 UWP 生成后，"导入资产" 对话框不会完成。 与 Unity 的合作调查中正在调查此问题。

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Unity 2020 中的文本网格 Pro 画布呈现器警告

使用 Unity 2020 时，大多数 MRTK 示例场景中都记录了以下警告：

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

[TextMeshPro 版本 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3)中添加了画布呈现器警告。  这些警告不会影响 MRTK 的示例场景，可以从控制台中清除。 有关更多详细信息，请参阅 [问题 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) 。
