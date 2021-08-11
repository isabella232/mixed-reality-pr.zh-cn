---
title: 选择引擎
description: 介绍可用于 HoloLens 和 VR 的混合现实开发的引擎选项。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: 14235852f8c90e7ccc4f105f2938ce514ae2933973469db9a0e01bd03d2c1b6d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227545"
---
# <a name="choosing-your-engine"></a>选择引擎

我们的文档中有几种开发途径供你采用。 首先是找到适合你的技术。 如果你已经有了想法，请继续操作，直接跳到下面其相应的选项卡。 如果你还在观望或者刚刚起步，请查看每一种途径，了解它们提供的内容、可用的平台和工具，然后开始创建吧！

> [!IMPORTANT]
> 如果你有现成的项目想要引入到 HoloLens 2 或沉浸式 VR 头戴显示设备（例如 Reverb G2）中，请查看我们的[移植指南概述](porting-apps/porting-overview.md)。 对于使用 HTK、MRTK v1、SteamVR 或针对沉浸式头戴显示设备开发的项目（例如 Oculus Rift 或 HTC Vive），我们有一些指导。

## <a name="engine-overview"></a>引擎概述

* **Unity** 是市场上领先的实时开发平台之一，其中包含以 c + + 编写的基本运行时代码，所有开发脚本都是以 c # 编写的。 无论你是想创建游戏、电影和动画，还是想在虚拟世界中呈现建筑或工程概念，Unity 都有提供支持的基础结构。

* **Unreal Engine 4** 是一个功能强大的开源创建引擎，可在 c + + 和蓝图中完全支持混合现实。 从 Unreal Engine 4.25 开始，HoloLens 提供完备的支持，且已准备好投入生产。 借助灵活的 Blueprints Visual Scripting 系统等功能，设计师可直观地使用全套概念和功能，而这些内容通常仅适用于编程人员。 跨多个行业的创建者可利用自由操作和掌控力来提供前沿内容、交互式体验和沉浸式虚拟世界。

* 具有编写自己的三维呈现器经验的 **本机** 开发人员可以使用 OpenXR 生成自定义引擎。 OpenXR 是来自 Khronos 的开放式免版税 API 标准，它对供应商提供的涵盖广泛的混合现实的各种设备提供引擎本机访问。 你可在桌面上的 HoloLens 2 或 Windows Mixed Reality 沉浸式头戴显示设备上使用 OpenXR 进行开发。

* 创建引人注目的跨浏览器 AR/VR web 体验的 **Web** 开发人员可以使用 **WebXR**。

    > [!NOTE]
    > HoloLens 开发 **Babylon.js** 当前正在进行。 查看 [最新新闻并与社区联系](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)！

<!-- Babylon is a Javascript-based, open source, 3D graphics engine capable of powering 3D scenes in a web browser. Babylon.js 4.2+ includes support for WebXR. With Babylon React Native, you can even build cross-platform native     applications for PC, mobile, and mixed reality devices. -->

## <a name="features-and-devices"></a>功能和设备

<br>

| 物流 | Unity | Unreal | JavaScript | 自定义引擎 <br>使用 OpenXR)  ( |
|---|---|---|---|---|
| 语言 | C# | C++ | JavaScript | C/C++ |
| 定价 | [Unity 定价](https://store.unity.com/#plans-individual) | [Unreal 定价](https://www.unrealengine.com/download) | 免费 | 免费 |

<br>

| 设备功能 | Unity | Unreal | JavaScript | 自定义引擎 <br>使用 OpenXR)  ( |
|---|---|---|---|---|
| 设备/显示器跟踪 | ✔️ | ✔️ | ✔️ | ✔️ |
| 手动输入 | ✔️ | ✔️ | ✔️ | ✔️ |
| 目视输入 | ✔️ | ✔️ | ❌ | ✔️ |
| 语音输入 | ✔️ | ✔️ | ✔️ | ✔️ |
| 运动控制器 | ✔️ | ✔️ | ✔️ | ✔️ |
| 平面/网格命中测试 | ✔️ | ✔️ | ✔️ | ✔️ |
| 场景理解 | ✔️ | ✔️ | ❌ | ✔️ |
| 空间音效 | ✔️ | ✔️ | ✔️ | ✔️ |
| QR 码检测 | ✔️ | ✔️ | ❌ | ✔️ |

<br>

| 硬件 | Unity | Unreal | JavaScript | 自定义引擎 <br>使用 OpenXR)  ( |
|---|---|---|---|---|
| HoloLens 2 | ✔️ | ✔️ | ✔️ | ✔️ |
| HoloLens（第 1 代） | ✔️ | ✔️ | ❌ | WinRT (旧版)  |
| [Windows Mixed Reality 头戴显示设备](../discover/immersive-headset-hardware-details.md) | ✔️ | ✔️ | ✔️ | ✔️ |
| SteamVR 头戴显示设备 | ✔️ | ✔️ | ✔️ | ✔️ |
| Oculus Quest/Rift | ✔️ | ✔️ | ✔️ | ✔️ |
| 移动 (ARCore/ARKit)  | ✔️ | ✔️ | ✔️ | ❌ |

<br>

| 工具 | Unity | Unreal | JavaScript | 自定义引擎 <br> (OpenXR)  |
|---|---|---|---|---|
| 混合现实工具包 | ✔️ | ✔️ | ❌  | ❌ |
| 世界锁定工具 | ✔️ | ❌ | ❌  | ❌ |
<!-- | 网格 | ❌ | ❌ | ❌ | ❌ | -->

<br>

| 云服务 | Unity | Unreal | JavaScript | 自定义引擎 <br> (OpenXR)  |
|---|---|---|---|---|
| Azure 空间定位点 | ✔️ | ✔️ | ❌ | ✔️ |
| Azure Object Anchors | ✔️ | ❌ | ❌ | ✔️ |
| Azure 远程渲染 | ✔️ * | ❌ | ❌ | ✔️ * |

> [!NOTE]
> * Azure 远程渲染 Unity) 中，使用旧版 WinRT API 和 XR 插件的应用 (Windows支持) 。 即将推出对 OpenXR 应用的 ARR 支持。

## <a name="next-steps"></a>后续步骤

[!INCLUDE[](includes/tools-next-steps.md)]