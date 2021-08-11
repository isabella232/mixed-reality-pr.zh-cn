---
title: OpenXR
description: 使用可移植的 OpenXR API 标准生成引擎，并部署到 Windows Mixed Reality HoloLens 2头戴显示设备。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR， 路线图， 扩展， Khronos， BasicXRApp， DirectX， 本机， 本机应用， 自定义引擎， 中间件
ms.openlocfilehash: 66ef972e09617e596a7d1d097073183943037e29b462ed3070d4defac91ca6b6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193735"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR 是 <a href="https://www.khronos.org/" target="_blank">Khronos</a>的开放免版税 API 标准，为引擎提供对混合现实范围内一系列设备的 [本机访问权限](../../discover/mixed-reality.md)。

可以在桌面上使用 OpenXR 进行开发HoloLens 2或Windows Mixed Reality沉浸式 VR 头戴显示设备。  如果无法访问头戴显示设备，可以改为使用 HoloLens 2 Emulator 或 Windows Mixed Reality 模拟器。

## <a name="why-openxr"></a>为何使用 OpenXR？

使用 OpenXR，可以生成面向全息设备（如 HoloLens 2）和沉浸式 VR 设备（例如桌面电脑的 Windows Mixed Reality 头戴显示设备）的引擎。 OpenXR 允许你编写代码一次，然后可跨各种硬件平台移植该代码。

OpenXR API 使用加载程序将应用程序直接连接到头戴显示设备本机平台支持。 最终用户无论使用的是手机还是任何其他头戴显示设备，都Windows Mixed Reality和最小延迟。

## <a name="what-is-openxr"></a>什么是 OpenXR？

OpenXR API 提供核心姿势预测、帧计时和空间输入功能，你需要构建一个面向全息和沉浸式设备的引擎。

若要了解 OpenXR API，请查看 OpenXR 1.0<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank"></a>规范<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">、API 参考</a>和<a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速参考指南</a>。  有关详细信息，请参阅 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 页</a>。

若要面向 HoloLens 2 的完整功能集，还将使用跨供应商和特定于供应商的 OpenXR 扩展，这些扩展可实现 OpenXR 1.0 核心之外的其他功能，例如明确手部跟踪、眼动跟踪、空间映射和空间定位点。 有关详细信息，请参阅下面的 [路线图](#roadmap) 部分，了解今年稍后将介绍的扩展。

OpenXR 本身不是混合现实引擎。  相反，OpenXR 使 Unity 和 Unreal 等引擎能够编写可移植代码一次，然后，无论供应商如何构建该平台，都可以访问用户的全息或沉浸式设备的本机平台功能。

## <a name="roadmap"></a>路线图

OpenXR 规范定义了一种扩展机制，该机制使运行时实现者能够公开除基础[](#what-is-openxr)<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0</a>规范 中定义的核心功能之外的其他功能。

有三种类型的 OpenXR 扩展：
* **供应商扩展 (例如 `MSFT` ，) ：** 启用硬件或软件功能中的按供应商创新。  任何运行时供应商都可以随时引入和提供供应商扩展。
  * **试验性供应商扩展 (例如 `MSFT_preview` ，) ：** 正在预览以收集反馈的实验性供应商扩展。  `MSFT_preview` 扩展仅适用于开发人员设备，在提供实际扩展时将被删除。  若要试验它们，可以在 [开发人员设备上启用预览扩展](openxr-getting-started.md#using-preview-extensions)。
* **跨供应商 `EXT` 扩展：** 多个公司定义和实现跨供应商扩展。  感兴趣的公司组随时都可以引入 EXT 扩展。
* **官方 `KHR` 扩展：** 官方 Khronos 扩展，作为核心规范发行版的一部分提供。  KHR 扩展由与核心规范本身相同的许可证涵盖。

OpenXR Windows Mixed Reality支持一组 和 扩展，这些扩展将完整的 HoloLens 2 `MSFT` `EXT` 功能引入 OpenXR 应用程序：

| 功能区域 | 扩展可用性 |
|--------------|------------------------|
| 系统 + 会话 | **OpenXR 1.0 核心规格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [引用空间 (视图、本地、阶段) ](../../design/coordinate-systems.md) | **OpenXR 1.0 核心规格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| 查看单 (立体声)  | **OpenXR 1.0 核心规格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [交换链](../platform-capabilities-and-apis/rendering.md)  + [帧计时](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1.0 核心规格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| 组合层<br /> (投影、四边形)  | **OpenXR 1.0 核心规格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [输入和触点](../../design/interaction-fundamentals.md) | **OpenXR 1.0 核心规格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 集成 | **正式 `KHR` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12 集成 | **正式 `KHR` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [无限制的引用空间 <br /> (世界规模的体验) ](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [空间定位点](../../design/spatial-anchors.md) | <p>**`MSFT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code></p><p>**`MSFT_preview` 预览版 [运行时 107 中的扩展](openxr-getting-started.md#using-preview-extensions)：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_anchor_persistence_preview">XR_MSFT_spatial_anchor_persistence_preview</a></code></p> |
| [手部 <br /> (手柄/目标姿势、敲击、抓取) ](../../design/hands-and-tools.md)<p>*HoloLens 2*</p> | **`MSFT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [手部铰接 + 手部网格](../../design/hands-and-tools.md)<p>*HoloLens 2*</p> | <p>**`EXT` 扩展已发布：**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [眼睛凝视](../../design/eye-tracking.md)<p>*HoloLens 2*</p> | **`EXT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| [混合现实捕获 (<br /> PV 相机设备的第三个) ](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*HoloLens 2*</p> | **`MSFT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| 与其他混合现实 SDK 互操作<br /> (例如 [QR](../platform-capabilities-and-apis/qr-code-tracking.md))  | <p>**`MSFT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` 运行时 105 中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| 与 UWP CoreWindow API 互操作<br /> (，例如键盘/鼠标)  | **`MSFT` 运行时 103 中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| 运动控制器交互配置文件<br /> (Samsung Odyssey 和 HP Reverb G2)  | **`MSFT` 运行时 103 中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [运动控制器呈现模型](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` 运行时 104 中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [场景理解 (平面、网格) ](../../design/scene-understanding.md)<p>*HoloLens 2*</p> | <p>**`MSFT` 运行时 106 中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding">XR_MSFT_scene_understanding</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_scene_understanding_serialization">XR_MSFT_scene_understanding_serialization</a></code></p> |
| [组合层重新 (自动平面或仅方向重新 <br />) ](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT` 运行时 106 中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_composition_layer_reprojection">XR_MSFT_composition_layer_reprojection</a></code> |
| 其他跨供应商扩展 | <p>**正式 `KHR` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code></p><p>**`EXT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code></p> |

虽然其中一些扩展可能作为供应商特定的扩展开始，但 Microsoft 和其他 OpenXR 运行时供应商正在共同为其中许多功能领域设计跨供应商或 `MSFT` `EXT` `KHR` 扩展。 跨供应商扩展会使你为这些功能编写的代码可跨运行时供应商移植，就像核心规范一样。

## <a name="getting-started-with-openxr"></a>OpenXR 入门

![用户我的世界混合现实头戴显示设备播放的屏幕截图](images/openxr-minecraft.jpg)

*我的世界新的 RenderDragon 引擎已使用 OpenXR 构建其桌面 VR 支持！*

Microsoft 一直在与 Unity 和长篇故事游戏合作，以确保混合现实的未来是开放的，不仅适用于 HoloLens 2，还适用于整个 PC VR，包括 HP 的新[Reverb G2](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)头戴显示设备。  OpenXR 为目前主要标题交付的跨供应商 VR 支持提供支持，例如 我的世界 和 Microsoft Flight Simulator！  有关针对第一代 HoloLens (进行) ，请参阅[发行说明](/hololens/hololens1-release-notes)。

若要了解如何在 Unity、Unreal Engine 或你自己的引擎中开始使用 OpenXR，请继续阅读！

### <a name="openxr-in-unity"></a>Unity 中的 OpenXR

Microsoft 当前推荐的用于 HoloLens 2 和 Windows Mixed Reality 的 Unity 配置是具有最新混合现实 OpenXR 插件的 **Unity 2020.3 LTS。**  此插件包括对 OpenXR 扩展的支持，这些扩展可启动 HoloLens 2 和[Windows Mixed Reality](#roadmap)头戴显示设备的完整功能，包括手部/眼动跟踪、空间定位点和 HP Reverb G2 控制器。  MRTK-Unity [MRTK 2.7](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)起支持 OpenXR。  有关 Unity 2020 和 OpenXR 入门详细信息，请参阅 [选择 Unity 版本](../unity/choosing-unity-version.md)。

如果要针对第一代 HoloLens (进行开发) ，则需要继续将 **Unity 2019.4 LTS** 与旧版 WinRT API 后端一起使用。  如果要在 Unity 2019 应用中面向新的 HP Reverb G2 控制器，请参阅 [HP Reverb G2 输入文档](../unity/unity-reverb-g2-controllers.md)。

从 **Unity 2021.2** 开始，OpenXR 将是面向头戴显示设备HoloLens 2 Windows Mixed Reality Unity 后端。

### <a name="openxr-in-unreal-engine"></a>Unreal 引擎中的 OpenXR

Unreal Engine 4.23 是推出 OpenXR 1.0 预览版支持的第一个主要游戏引擎版本！  现在 **，在 Unreal Engine 4.26** 中，可以通过 Unreal Engine 的内置 OpenXR 支持获得对 HoloLens 2、Windows Mixed Reality 和其他桌面 VR 头戴显示设备的支持。  Unreal Engine 4.26 还支持[Microsoft 的 OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal)扩展插件，支持手部交互和 HP Reverb G2 控制器支持，为 HoloLens 2 和 Windows Mixed Reality 头戴显示[设备](#roadmap)提供完整的功能集。  Unreal Engine 4.26 目前适用于[长](https://www.unrealengine.com/download/creators)篇故事Launcher，MRTK-Unreal 0.12 支持 OpenXR 项目。

### <a name="openxr-for-native-development"></a>用于本机开发的 OpenXR

可以在桌面上使用 OpenXR 进行开发HoloLens 2或Windows Mixed Reality沉浸式 VR 头戴显示设备。  如果无法访问头戴显示设备，可以改为使用 HoloLens 2 Emulator 或 Windows Mixed Reality 模拟器。

若要开始开发 OpenXR 应用程序HoloLens 2或 Windows Mixed Reality VR 头戴显示设备，请参阅如何[开始使用 OpenXR 开发](openxr-getting-started.md)。

有关 OpenXR API 所有主要组件的教程，以及当前使用 OpenXR 的实际应用程序示例，请查看此 60 分钟的演练视频：

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>另请参阅

* <a href="https://www.khronos.org/openxr/" target="_blank">有关 OpenXR 详细信息</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 参考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速参考指南</a>