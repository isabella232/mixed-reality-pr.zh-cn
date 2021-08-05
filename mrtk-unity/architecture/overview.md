---
title: 体系结构概述
description: MRTK 的体系结构概述。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK 体系结构，
ms.openlocfilehash: 7113ee68a3d8bae016236996725a879c95e31f410cb273184ddcc255ae7a0685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186594"
---
# <a name="architecture-overview"></a>体系结构概述

若要全面了解 MRTK 的内容，本文档中包含的体系结构信息将帮助你了解以下内容：

- 大量 MRTK 及其连接方式
- MRTK 引入的概念，在 vanilla Unity 中可能不存在
- 一些较大的系统如何 (输入) 工作

本部分并不旨在指导你如何执行任务，而是指导如何构造此类任务及其原因。

## <a name="many-audiences-one-toolkit"></a>许多受众，一个工具包

MRTK 没有单个统一的受众。 它用于支持从首次黑客攻击到为企业构建复杂共享体验的个人等用例。 某些代码和 API 可能已针对其他代码和 API 进行了多个优化 (即，MRTK 的某些部分似乎更适用于"一键配置") ，但必须注意，其中一些代码和 API 更适用于历史和资源。 随着 MRTK 的发展，构建的功能应设计为可缩放以支持各种用例。

MRTK 还需要在 VR 和 AR 体验之间正常缩放。 在 HoloLens 2 或 HoloLens 1 上部署时，应可以轻松生成可正常回退行为的应用程序，并且应该可以轻松生成面向 OpenVR 和 WMR (以及其他平台) 的应用程序。 虽然有时团队可能会专注于特定系统或平台的特定迭代，但长期目标是为构建混合现实体验的任何位置构建广泛的支持。

## <a name="high-level-breakdown"></a>高级细分

MRTK 既是一组工具，用于快速获得混合现实 (MR) 体验，也是一个应用程序框架，对其自身的运行时、扩展方式以及配置方式有意见。

从较高层面来说，可以按以下方式细分 MRTK：

![体系结构概述关系图](../features/images/architecture/MRTK_Architecture.png)

MRTK 还包含另一组抓取包实用工具，它们几乎不依赖于 MRTK (的其余部分，以列出一些内容：生成工具、求解器、音频影响因素、平滑实用程序和线条呈现器) 

从框架和运行时开始，体系结构文档的其余部分会从下到上生成，并不断前进到更有趣、更复杂的系统，例如输入。 请参阅目录以继续体系结构概述。
