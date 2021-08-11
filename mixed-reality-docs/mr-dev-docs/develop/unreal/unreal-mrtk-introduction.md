---
title: 适用于 Unreal 的 MRTK 简介
description: 首先了解适用于 Unreal 的混合现实工具包提供给新的混合现实开发人员的各项内容。
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 测试, 混合现实工具包, MRTK 版本 2, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 跨平台
ms.openlocfilehash: 06eacac245c80f16ab48dbda4b5aca740ffdfd66a0266beafac5e46b39a9d109
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221827"
---
# <a name="introducing-mrtk-for-unreal"></a>适用于 Unreal 的 MRTK 简介

![MRTK 横幅图像](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>混合现实工具包 (MRTK) 是什么？

MRTK 是一个很棒的开源工具包，自 HoloLens 首次发布以来就有了它。 该工具包现在的优秀，归功于我们开发人员社区的努力贡献。 

适用于 Unreal 的混合现实工具包 (MRTK-Unreal) 是一组组件，包含插件、示例和文档，旨在为使用 Unreal Engine 开发混合现实应用程序提供帮助。 目前，该工具包包含：
* [适用于 Unreal 的 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)，可提供代码、蓝图和示例，用于实现 Hololens 2 应用程序的 UX 功能。
* [适用于 Unreal 的 Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal)，有助于优化混合现实应用程序的视觉保真，同时不超出性能预算。

查看 [GitHub 上的 MRTK 文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)，并通过 [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) 或 [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) 安装指南入门。

### <a name="modular"></a>模块化

构建 MRTK Unreal 时，我们采用了模块化方式，因此，你不需要将此工具包的所有组件都放到项目中。 可以选择所需的插件并根据需要进行添加或删除。 使用此方法可缩小你的项目，使之更易于管理。  

### <a name="performant"></a>高性能

由于要使用移动平台，因此我们在构建 MRTK Unreal 时必须时时刻刻考虑到性能。 这相当重要，我们需要确保这些工具不会给你造成麻烦。

## <a name="project-setup"></a>项目设置

> [!div class="nextstepaction"]
> [下载 Unreal Engine 和 MRTK](unreal-project-setup.md)

## <a name="see-also"></a>另请参阅

* [安装工具](../install-the-tools.md)
* [使用适用于 Unreal 的 MRTK 进行开发](unreal-development-overview.md)
* [UX Tools - 安装指南 (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [UX Tools - 文档主页 (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [Graphics Tools - 安装指南 (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [Graphics Tools - 文档主页 (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)