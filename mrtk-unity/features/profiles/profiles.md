---
title: 配置文件
description: MRTK 中的文档配置文件
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，配置文件，
ms.openlocfilehash: 785d402e924a534627dfd1d742d2019d9ce9dd5a
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908240"
---
# <a name="profiles"></a>配置文件

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

配置 MRTK 的主要方法之一是通过基础包中提供的配置文件。 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)场景中的主对象将具有活动配置文件，这是一个 ScriptableObject。 顶级 MRTK 配置文件包含主要核心系统每个核心的子配置文件数据，其中每个核心系统都设计为配置其对应子系统的行为。 此外，这些子配置文件也是 ScriptableObjects 的，因此可以在其下包含一个级别的其他配置文件对象的引用。 实质上是一个完整的连接配置文件树，它们构成了有关如何初始化 MRTK 子系统和功能的配置信息。

例如，输入系统的行为由输入系统配置文件控制，如 `DefaultMixedRealityInputSystemProfile` (资产/MRTK/SDK/配置文件) 。

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>分析检查器</sup>

## <a name="background"></a>背景

配置文件主要用于支持跨多个设备的特定方案，这些设备通过数据提供程序进行处理。 通过这种方式，可以将应用设计为设备 agnosticly，并让 MRTK 和配置文件的数据提供程序处理跨平台支持。

还会围绕特定设备的输入功能构建一些配置文件，例如，默认为 GGV-样式交互的 HoloLens 1 配置文件。

## <a name="xr-sdk"></a>XR SDK

::: moniker range=">= mrtkunity-2021-05"
使用所有默认的 MRTK 配置文件，这些配置文件都是跨 Unity 的 XR 管道配置的。 以前的 "DefaultOpenXRConfigurationProfile" 和 "DefaultXRSDKConfigurationProfile" 现在标记为已过时。
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
目前提供了两个配置文件用于 XR SDK `DefaultXRSDKConfigurationProfile` 和 `DefaultHoloLens2XRSDKConfigurationProfile` 。 因此，并不是所有的示例场景都受到完全支持，因为存在场景和方案特定的配置。 使用和的任何 `DefaultMixedRealityToolkitConfigurationProfile` 样本 `DefaultHoloLens2ConfigurationProfile` _都可以_ 交换到其对应的 XR SDK 配置文件。 如果将 OpenXR 与 XR SDK 配合使用，请改用 `DefaultOpenXRConfigurationProfile` 。

还需要执行其他工作来简化配置并支持所有的示例场景，同时可以并行配置旧的 XR 和 XR SDK。 请参阅问题 [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) 跟踪。
::: moniker-end

有关在旧 XR 和 XR SDK 之间转换配置文件的详细信息，请参阅为 [XR SDK 管道配置 MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) 。

## <a name="default-profile"></a>默认配置文件

MRTK 提供了一组默认配置文件，涵盖了 MRTK 支持的大多数平台和方案。 例如，当你选择 " `DefaultMixedRealityToolkitConfigurationProfile` (资产/MRTK/SDK/配置文件" 时) 你将能够在 "VR (OpenVR、WMR) 和 HoloLens (1" 和 "2) 上尝试方案。

请注意，由于这是一个常规的使用配置文件，因此不会针对任何特定用例进行优化。 如果希望具有更适合其他平台的高性能/特定设置，请参阅下面的其他配置文件，这些配置文件在各自的平台上稍微调整更好。

## <a name="hololens-2-profile"></a>HoloLens 2 配置文件

MRTK 还提供了一个默认配置文件，该配置文件在 HoloLens 2： `DefaultHoloLens2ConfigurationProfile` (资产/MRTK/SDK/profile/HoloLens2) 上经过优化，可用于部署和测试。

当系统提示选择 MixedRealityToolkit 对象的配置文件时，请使用此配置文件而不是默认的所选配置文件。

HoloLens2 配置文件与默认配置文件之间的主要区别是：

**禁用** 的功能：

- [边界系统](../boundary/boundary-system-getting-started.md)
- [传送系统](../teleport-system/teleport-system.md)
- [空间感知系统](../spatial-awareness/spatial-awareness-getting-started.md)
- 由于性能开销) ，[手动网格可视化](../input/hand-tracking.md) (

**已启用** 的系统：

- [目视跟踪提供程序](../input/eye-tracking/eye-tracking-main.md)
- 目视输入模拟

照相机配置文件设置将设置为 "匹配"，以便编辑器质量和播放器质量相同。 这不同于默认照相机配置文件，其中不透明显示设置为较高的质量。 此更改意味着编辑器内的质量会降低，这将与设备上呈现的内容更匹配。

> [!NOTE]
> 默认情况下，基于客户端反馈关闭空间感知系统-它是一种有趣的可视化效果，通常是关闭的，但通常是关闭的，以避免视觉干扰，并使其在其上出现额外性能下降。 可以按照 [此处的说明](../spatial-awareness/spatial-awareness-getting-started.md)重新启用系统。
