---
title: 入门教程 - 3. 配置 MRTK 配置文件
description: 本教程介绍如何配置混合现实工具包 (MRTK) 配置文件。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 空间感知
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300452"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3.配置 MRTK 配置文件

## <a name="overview"></a>概述

在本教程中，你将学习如何自定义和配置 MRTK 配置文件。

<a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK 配置文件</a>是一个嵌套配置文件树，它们构成了应如何初始化 MRTK 系统和功能的配置信息。 顶级配置文件（即“配置”配置文件）包含每个主要核心系统的嵌套配置文件。 每个嵌套的配置文件都设计为配置其对应系统的行为。

此特定示例将演示如何通过更改空间网格观察程序的设置来隐藏空间感知网格。 但是，可以按照相同的原则来自定义 MRTK 配置文件中的任何设置或值。

正如你在[上一教程](mr-learning-base-02.md#congratulations)期间将项目部署到 HoloLens 2 时遇到的一样，<a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">空间感知</a>网格是一系列表示环境几何图形的网格。 这是一种有用的可视化效果，一开始就能看到，但通常也可将它关闭，以避免用它后产生视觉干扰和额外的性能影响。

## <a name="objectives"></a>目标

* 了解如何自定义和配置 MRTK 配置文件
* 隐藏空间感知网格

## <a name="changing-the-spatial-awareness-display-option"></a>更改空间感知显示选项

隐藏空间感知网格所要执行的主要步骤如下：

1. 克隆默认的配置配置文件
2. 启用空间感知系统
3. 克隆默认的空间感知系统配置文件
4. 克隆默认的空间感知网格观察程序配置文件
5. 更改空间感知网格的可见性

> [!NOTE]
> 默认情况下，MRTK 配置文件不可编辑。 这是一些默认的配置文件模板，必须先克隆它们，然后才能对其进行编辑。 配置文件有多个嵌套层。 因此，在配置一个或多个设置时，常见的做法是克隆然后编辑多个配置文件。

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何克隆、自定义和配置 MRTK 配置文件和设置。

> [!div class="nextstepaction"]
> [下一教程：4.定位场景中的对象](mr-learning-base-04.md)