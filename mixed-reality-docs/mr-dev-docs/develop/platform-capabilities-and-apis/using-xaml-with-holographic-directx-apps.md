---
title: 将 XAML 与全息 DirectX 应用配合使用
description: 说明在 DirectX 应用中在 2D XAML 视图和沉浸式视图之间切换的影响，以及如何有效使用 XAML 视图和沉浸式视图。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: windows 混合现实， UWP， 应用视图管理， xaml， 键盘， 演练， DirectX
ms.openlocfilehash: 3c7edfdf4ff2ed629699dca0514efabc9ce7241cb1781e4b9c914ad4bff1f900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220943"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>将 XAML 与全息 DirectX 应用配合使用

> [!NOTE]
> 本文与旧版 WinRT 本机 API 相关。  对于新的本机应用项目，建议使用 **[OpenXR API](../native/openxr-getting-started.md)**。

本主题介绍在 DirectX 应用中 [在 2D XAML](../../design/app-views.md) 视图和沉浸式视图之间切换的影响，以及如何有效使用 XAML 视图和沉浸式视图。

## <a name="xaml-view-switching-overview"></a>XAML 视图切换概述

在 HoloLens，稍后可能会显示 2D XAML 视图的沉浸式应用需要先初始化该 XAML 视图，然后立即从该视图切换到沉浸式视图。 XAML 将在应用执行任何操作之前加载，这会增加启动时间。 XAML 将继续占用应用进程中的内存空间，而它仍保留在后台。 启动延迟和内存使用量取决于应用在切换到本机视图之前对 XAML 执行哪些操作。 如果一开始在 XAML 启动代码中不执行任何操作，但启动沉浸式视图除外，则影响应该很小。 此外，由于全息渲染是直接到沉浸式视图进行，因此你将避免该渲染上任何与 XAML 相关的限制。

CPU 和 GPU 的内存使用量计数。 Direct3D 11 可以交换虚拟图形内存，但它可能无法交换掉部分或所有 XAML GPU 资源，并且可能会显著影响性能。 无论哪种方式，不加载任何不需要的 XAML 功能都会为应用留下更多空间，并提供更好的体验。

## <a name="xaml-view-switching-workflow"></a>XAML 视图切换工作流

从 XAML 直接进入沉浸式模式的应用的工作流如下所示：
* 应用在 2D XAML 视图中启动。
* 应用的 XAML 启动序列检测当前系统是否支持全息渲染：
* 如果是这样，应用会创建沉浸式视图，并将其引入前台。 对于设备上不需要的任何内容，将跳过 XAML 加载Windows Mixed Reality包括 XAML 视图中的任何呈现类和资产加载。 如果应用使用 XAML 进行键盘输入，则仍应创建该输入页。
* 如果没有，XAML 视图可以像平时一样继续处理业务。

## <a name="tip-for-rendering-graphics-across-both-views"></a>跨两个视图呈现图形的提示

如果应用需要在 DirectX 中为 Windows Mixed Reality 中的 XAML 视图实现一定的渲染，则最好创建一个可以同时使用这两个视图的呈现器。 呈现器应该是一个可以从这两个视图访问的实例，并且应在 2D 和全息渲染之间切换。 这样，GPU 资产只需加载一次，这可减少切换视图时加载时间、内存影响和交换资源量。
