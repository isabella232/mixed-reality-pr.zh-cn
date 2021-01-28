---
title: 用于 Unity 的 MRTK 简介
description: 首先了解跨平台混合现实工具包提供给新的混合现实开发人员的各项内容。
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 测试, 混合现实工具包, MRTK 版本 2, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 跨平台
ms.openlocfilehash: 4c013f1fa50518404f899b4181e7c07b9e4e0e56
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581703"
---
# <a name="introducing-mrtk-for-unity"></a>用于 Unity 的 MRTK 简介

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>混合现实工具包 (MRTK) 是什么？

MRTK 是一个很棒的开源工具包，自 HoloLens 首次发布以来就有了它。 该工具包现在的优秀，归功于我们开发人员社区的努力贡献。 在过去 3 年里，我们听取了开发人员社区的反馈，在构建 MRTK v2 时考虑到了大家最关注的一些事项。  

MRTK for Unity 是一款面向混合现实应用程序的开源跨平台开发工具包。 该工具包提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。 该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

查看 [GitHub 上的 MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)，并通过[安装指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)开始使用。

## <a name="new-with-mrtk-v2"></a>MRTK v2 新增功能

我们想要强调一下我们对这些平台工具的承诺。  事实上，我们使用 MRTK 第 2 版开发了我们的内置体验，例如开箱即用的设置体验 (OOBE) 和混合现实提示应用程序。 另外，你还会看到首先通过 MRTK 公开的全新 HoloLens 2 功能，因为我们认为这是在我们的平台上进行开发的最佳方式。 

### <a name="modular"></a>模块化

构建它时，我们采用了模块化方式，因此，你不需要将此工具包的所有组件都放到项目中。  实际上，这样做有一些好处。  缩小你的项目，使之更易于管理。  另外，由于我们在构建它时使用了可脚本化的对象，并且它是接口驱动型的，因此你也可以将它附带的组件替换为你自己的，这样就可以支持其他服务、系统和平台。

### <a name="cross-platform"></a>跨平台

说到其他平台，必须指出的是，它提供跨平台支持。  虽然这并不意味着我们会对每个平台提供支持，但我们可以保证：当你将生成目标切换到其他平台时，工具包代码的任何部分都不会崩溃。  模块化设计稳定可靠且具有可扩展性，因此能够支持多个平台，例如 ARCore、ARKit 和 OpenVR。

### <a name="performant"></a>高性能

由于要使用移动平台，因此我们在构建它时必须时时刻刻考虑到性能。  这相当重要，我们需要确保这些工具不会给你造成麻烦。

## <a name="see-also"></a>另请参阅

* [安装工具](../install-the-tools.md)
* [使用适用于 Unity 的 MRTK 进行开发](unity-development-overview.md)
* [MRTK - 安装指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK - 文档主页 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [从 HoloToolkit/MRTK 移植到 MRTK 版本 2 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
