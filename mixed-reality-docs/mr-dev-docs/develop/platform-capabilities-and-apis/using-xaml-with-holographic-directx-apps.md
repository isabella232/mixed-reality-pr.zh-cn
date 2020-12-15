---
title: 将 XAML 与全息 DirectX 应用配合使用
description: 说明在 DirectX 应用中切换 2D XAML 视图和沉浸式视图的影响，以及如何有效地利用 XAML 视图和沉浸式视图。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: windows mixed reality，UWP，应用视图管理，xaml，键盘，演练，DirectX
ms.openlocfilehash: b062efadca9ccfe2e2caeb054f662becc0807b50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530278"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>将 XAML 与全息 DirectX 应用配合使用

> [!NOTE]
> 本文与旧版 WinRT 本机 Api 相关。  对于新的本机应用项目，建议使用 **[OPENXR API](../native/openxr-getting-started.md)**。

本主题介绍在 DirectX 应用中切换 [2D XAML 视图和沉浸式视图](../../design/app-views.md) 的影响，以及如何有效地利用 XAML 视图和沉浸式视图。

## <a name="xaml-view-switching-overview"></a>XAML 视图切换概述

在 HoloLens 上，可以在以后显示 2D XAML 视图的沉浸式应用程序需要首先初始化该 XAML 视图，并从该处立即切换到沉浸式视图。 XAML 将在你的应用程序可以执行任何操作之前加载，这增加了启动时间的短暂增长。 XAML 将继续占用应用进程中的内存空间，同时保留在后台。 启动延迟量和内存使用情况取决于应用程序在切换到本机视图之前对 XAML 执行的操作。 如果首先在 XAML 启动代码中执行任何操作，但启动沉浸式视图除外，则影响应该很小。 此外，由于全息呈现直接在沉浸式视图中完成，因此你将避免对该呈现进行任何与 XAML 相关的限制。

CPU 和 GPU 的内存使用量。 Direct3D 11 可以交换虚拟图形内存，但它可能无法调换部分或全部 XAML GPU 资源，而且可能会显著降低性能。 无论采用哪种方式，不加载任何不需要的 XAML 功能都将为应用程序留出更多空间，并提供更好的体验。

## <a name="xaml-view-switching-workflow"></a>XAML 视图切换工作流

直接从 XAML 进入沉浸式模式的应用的工作流如下所示：
* 应用程序在 2D XAML 视图中启动。
* 应用的 XAML 启动序列检测当前系统是否支持全息呈现：
* 如果是这样，该应用程序会创建沉浸式视图，并立即将其放到前台。 对于 Windows Mixed Reality 设备上不需要的任何内容（包括在 XAML 视图中呈现类和资产加载），将跳过 XAML 加载。 如果应用使用 XAML 进行键盘输入，则仍应创建该输入页。
* 如果不是，则 XAML 视图可以像平常一样继续工作。

## <a name="tip-for-rendering-graphics-across-both-views"></a>用于跨两个视图呈现图形的提示

如果你的应用程序需要在 Windows Mixed Reality 中为 XAML 视图实现某种数量的应用程序，最佳做法是创建一个可同时使用这两个视图的呈现器。 呈现器应是可以从这两个视图访问的一个实例，并且应在二维和全息呈现之间切换。 这样一来，GPU 资产仅加载一次，这会减少加载时间、内存影响以及切换视图时交换的资源量。
