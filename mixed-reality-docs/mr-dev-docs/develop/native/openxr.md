---
title: OpenXR
description: 使用可移植 OpenXR API 标准构建引擎，并将其部署到 Windows Mixed Reality 和 HoloLens 2 耳机。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR，路线图，扩展，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件
ms.openlocfilehash: 98b75f8b6059e6537d4cb4a10ecf8d057ad19a07
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2021
ms.locfileid: "110711536"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR 是来自 <a href="https://www.khronos.org/" target="_blank">Khronos</a>的免费版税 API 标准，为引擎提供跨 [混合现实](../../discover/mixed-reality.md)范围内的一系列设备的本机访问权限。

你可在桌面上的 HoloLens 2 或 Windows Mixed Reality 沉浸式头戴显示设备上使用 OpenXR 进行开发。  如果你无权访问耳机，则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。

## <a name="why-openxr"></a>为什么要 OpenXR？

借助 OpenXR，你可以构建面向全息设备（如 HoloLens 2）和沉浸式设备（如台式计算机的 Windows Mixed Reality 耳机）的引擎。 OpenXR 可让你编写代码，然后在各种硬件平台上对其进行迁移。

OpenXR API 使用加载程序将应用程序直接连接到头戴显示器的本机平台支持。 最终用户可以获得最大性能和最小延迟，无论他们使用的是 Windows Mixed Reality 还是任何其他耳机。

## <a name="what-is-openxr"></a>什么是 OpenXR？

OpenXR API 提供核心姿势预测、帧计时和空间输入功能，你需要构建一个可面向全息和沉浸式设备的引擎。

若要了解有关 OpenXR API 的信息，请参阅 OpenXR 1.0 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">规范</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 参考</a>和 <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速参考指南</a>。  有关详细信息，请参阅 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 页</a>。

若要面向一组完整的 HoloLens 2 功能，还将使用跨供应商和供应商特定的 OpenXR 扩展，这些扩展启用 OpenXR 1.0 核心之外的其他功能，例如已表述的手动跟踪、目视跟踪、空间映射和空间锚。 有关详细信息，请参阅本年度今后的扩展中的 " [路线图" 部分](#roadmap) 。

OpenXR 本身并不是一个混合现实引擎。  相反，OpenXR 使 Unity 和 Unreal 等引擎能够编写可移植代码一次，然后就可以访问用户的全息或沉浸式设备的本机平台功能，无论构建该平台的供应商是什么。

## <a name="roadmap"></a>路线图

OpenXR 规范定义了一种扩展机制，它使运行时实现程序能够公开超出<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">基本 OpenXR 1.0 规范</a>中定义的[核心功能](#what-is-openxr)的其他功能。

有三种类型的 OpenXR 扩展：
* **供应商扩展 (例如 `MSFT`) ：** 启用硬件或软件功能中的每个供应商创新。  任何运行时供应商随时都可以引入和交付供应商扩展。
  * **实验性供应商扩展 (例如 `MSFT_preview`) ：** 正在预览的实验性供应商扩展以收集反馈。  `MSFT_preview` 扩展仅适用于开发人员设备，并将在真正的扩展交付时删除。  若要对其进行试验，可以 [在开发人员设备上启用预览版扩展](openxr-getting-started.md#using-preview-extensions)。
* **跨供应商 `EXT` 扩展：** 多个公司定义和实现的跨供应商扩展。  一组感兴趣的公司随时可以引入扩展扩展。
* **官方 `KHR` 扩展：** 正式 Khronos 扩展作为核心规范版本的一部分而被批准。  KHR 扩展与核心规范本身具有相同的许可证。

Windows Mixed Reality OpenXR 运行时支持一组 `MSFT` 和 `EXT` 扩展，这些扩展将一组完整的 HoloLens 2 功能引入 OpenXR 应用程序：

| 功能区域 | 扩展可用性 |
|--------------|------------------------|
| 系统 + 会话 | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [引用空间 (视图、本地、阶段) ](../../design/coordinate-systems.md) | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| 查看 (mono、立体声) 的配置 | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [交换链](../platform-capabilities-and-apis/rendering.md)  + [帧计时](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| 组合层<br /> (投影，四)  | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [输入和 haptics](../../design/interaction-fundamentals.md) | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 集成 | **正式 `KHR` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12 集成 | **正式 `KHR` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [无限的参考空间 <br /> (世界规模的体验) ](../../design/coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [空间定位点](../../design/spatial-anchors.md) | **`MSFT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [手动交互 <br /> (手柄/aim 姿势、分流、抓住) ](../../design/hands-and-tools.md)<p>*仅 HoloLens 2*</p> | **`MSFT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [手型 articulation + 手写网格](../../design/hands-and-tools.md)<p>*仅 HoloLens 2*</p> | <p>**`EXT` 在运行时102中发布的扩展：**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT` 在运行时102中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [眼睛凝视](../../design/eye-tracking.md)<p>*仅 HoloLens 2*</p> | **`EXT` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| 与其他 HoloLens Sdk 互操作<br /> (例如， [QR](../platform-capabilities-and-apis/qr-code-tracking.md)) <p>*仅 HoloLens 2*</p> | <p>**`MSFT` 在运行时102中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code></p><p>**`MSFT` 运行时105中的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_perception_anchor_interop">XR_MSFT_perception_anchor_interop</a></code></p> |
| [混合现实捕获 <br /> 从 PV 相机 (第三个渲染) ](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*仅 HoloLens 2*</p> | **`MSFT` 在运行时102中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| 与 UWP CoreWindow API 互操作<br />例如，对于键盘/鼠标)  ( | **`MSFT` 在运行时103中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_holographic_window_attachment">XR_MSFT_holographic_window_attachment</a></code>
| 运动控制器交互配置文件<br /> (Samsung 太空和 HP 回音 G2)  | **`MSFT` 在运行时103中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_samsung_odyssey_controller">XR_EXT_samsung_odyssey_controller</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hp_mixed_reality_controller">XR_EXT_hp_mixed_reality_controller</a></code> |
| [运动控制器呈现模型](../../design/motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT` 在运行时104中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_controller_model">XR_MSFT_controller_model</a></code> |
| [了解 (平面、网格) 的场景 ](../../design/scene-understanding.md)<p>*仅 HoloLens 2*</p> | <p>**从运行时102：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code>与[场景理解 SDK](../platform-capabilities-and-apis/scene-understanding-sdk.md)一起使用</p><p>**`MSFT`[预览版运行时 105](openxr-getting-started.md#using-preview-extensions)中的扩展：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_preview2">XR_MSFT_scene_understanding_preview2</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_scene_understanding_serialization_preview">XR_MSFT_scene_understanding_serialization_preview</a></code></p> |
| [复合层 reprojection 模式 <br /> (自动平面或仅限方向的 reprojection) ](../platform-capabilities-and-apis/hologram-stability.md#reprojection) | **`MSFT`[预览版运行时 105](openxr-getting-started.md#using-preview-extensions)中的扩展：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_composition_layer_reprojection_preview">XR_MSFT_composition_layer_reprojection_preview</a></code> |
| 其他跨供应商扩展 | <p>**正式 `KHR` 扩展已发布：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_color_scale_bias" target="_blank">XR_KHR_composition_layer_color_scale_bias</a></code><p>**`EXT` 已发布的扩展：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

尽管其中一些扩展可能会作为特定于供应商的 `MSFT` 扩展开始，但 Microsoft 和其他 OpenXR 运行时供应商正在协同工作，以便为 `EXT` 其中许多功能领域设计跨供应商或 `KHR` 扩展。 跨供应商扩展会使你为在运行时供应商提供的这些功能编写的代码与核心规范相同。

## <a name="getting-started-with-openxr"></a>OpenXR 入门

![戴上混合现实耳机的用户正在播放的 Minecraft 屏幕截图](images/openxr-minecraft.jpg)

*Minecraft 的新 RenderDragon 引擎已使用 OpenXR 构建了其 desktop VR 支持！*

Microsoft 一直在使用 Unity 和长篇故事来确保未来混合现实处于打开状态，而不仅仅是针对 HoloLens 2，而是在所有的 PC VR 范围内（包括 [HP 的新的回响 G2 耳机](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)）。  OpenXR 为当前交付的主要职位（如 Minecraft 和 Microsoft 航班模拟器）提供跨供应商 VR 支持。  有关为 HoloLens (第一代) 进行开发的详细信息，请参阅 [发行说明](/hololens/hololens1-release-notes)。

若要了解如何在 Unity、Unreal 引擎或你自己的引擎中开始处理 OpenXR，请阅读！

### <a name="openxr-in-unity"></a>Unity 中的 OpenXR

如今，为 HoloLens 2、HoloLens (第一代) 和 Windows Mixed Reality 耳机支持的 Unity 开发路径是与现有 WinRT API 后端的 **unity 2019 LTS** 。  可以 [通过 Unity](../unity/openxr-getting-started.md)跳转到 OpenXR;如果要以 Unity 2019 应用中的新 HP 回音 G2 控制器为目标，请参阅 [HP 回音 g2 输入文档](../unity/unity-reverb-g2-controllers.md)。

从 **unity 2020 LTS** 开始， [unity 附带了一个 OpenXR 后端，该后端](https://forum.unity.com/threads/unitys-plans-for-openxr.993225/) 支持 HoloLens 2 和 Windows Mixed Reality 耳机。  这包括对安装 [HoloLens 2 和 Windows Mixed Reality 耳机的全部功能](#roadmap)的 OpenXR 扩展的支持，包括手写/眼睛跟踪、空间锚定和 HP 回音 G2 控制器。  MRTK-Unity 支持从 [MRTK 2.7](../unity/tutorials/mr-learning-base-02.md?tabs=openxr#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)到的 OpenXR。  若要详细了解适用于当前的 Unity 2020 LTS 支持，请参阅 [选择 unity 版本](../unity/choosing-unity-version.md)。

从 **Unity 2021** 开始，OpenXR 将毕业为面向 HoloLens 2 和 Windows Mixed Reality 耳机的唯一受支持的 Unity 后端。

### <a name="openxr-in-unreal-engine"></a>Unreal 引擎中的 OpenXR

截至 **Unreal 引擎 4.23**，完全支持 HoloLens 2 和 Windows mixed reality 耳机通过 Windows mixed Reality (WinRT) 插件提供。

Unreal 引擎4.23 也是发布预览版支持的第一个重要游戏引擎版本 OpenXR 1.0！  现在，在 **Unreal engine 4.26** 中，支持 HoloLens 2、Windows Mixed Reality 和其他 desktop VR 耳机通过 Unreal 引擎的内置 OpenXR 支持获得。  Unreal 引擎4.26 还支持 [Microsoft 的 OpenXR 扩展插件](https://github.com/microsoft/Microsoft-OpenXR-Unreal)、启用手动交互和 HP 回音 G2 控制器支持， [并使 HoloLens 2 和 Windows Mixed Reality 耳机](#roadmap)上的功能保持最新。  Unreal 引擎4.26 现已在 [长篇故事游戏启动器](https://www.unrealengine.com/download/creators)中提供，并在4月晚些时候推出 MRTK-Unreal 支持。


### <a name="openxr-for-native-development"></a>用于本机开发的 OpenXR

你可在桌面上的 HoloLens 2 或 Windows Mixed Reality 沉浸式头戴显示设备上使用 OpenXR 进行开发。  如果你无权访问耳机，则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。

若要开始为 HoloLens 2 或沉浸式 Windows Mixed Reality 耳机开发 OpenXR 应用程序，请参阅 [如何开始 OpenXR 开发](openxr-getting-started.md)。

有关 OpenXR API 的所有主要组件的教程，以及目前使用 OpenXR 的实际应用程序的示例，请查看此60分钟演练视频：

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="see-also"></a>另请参阅

* <a href="https://www.khronos.org/openxr/" target="_blank">有关 OpenXR 的详细信息</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 参考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速参考指南</a>