---
title: 手部和运动控制器
description: 了解手部和运动控制器交互模型，这些模型可以删除虚拟和物理之间的边界。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合现实、手部、运动控制器、交互、设计、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、MRTK、混合现实Toolkit
ms.openlocfilehash: 3a54d707260a3e5aebd83a53b62098504c86c9fea7b2ecbb49d3dbd8b72400dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213684"
---
# <a name="hands-and-motion-controllers"></a>手部和运动控制器

## <a name="scenarios"></a>方案

阅读交互 [概述 后](interaction-fundamentals.md)，选择手部和运动控制器交互模型。 这意味着你要开发一个应用程序，该应用程序要求用户使用两只手与全息世界交互。 应用程序将实现删除虚拟和物理之间的边界的目标。

一些特定方案可能是：
* 为信息工作者提供包含 UI 的 2D 虚拟屏幕来显示和控制内容
* 为工厂装配线提供一线工作人员教程和指南
* 开发用于协助和教育医疗专业人员的专业工具  
* 使用 3D 虚拟对象来装饰现实世界，或创建第二世界 
* 以现实世界为背景创建基于位置的服务和游戏

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>手部和运动控制器形式

:::row:::
    :::column:::
       [![用手直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[使用手直接操作](direct-manipulation.md)<br>
       以形式应用用户可用于触摸和操作全息影像的手部功能。 通过使用每日生活体验和提供适当的视觉元素，用户可以使用相同的方式操作现实世界的对象，以与虚拟对象交互。
    :::column-end:::
    :::column:::
       [![使用手指向和提交](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[使用手指向和提交](point-and-commit.md)<br>
        这种形式使用户能够在一段距离内与全息影像交互。 它使用户能够充分利用周围的环境。 用户可以将全息影像放在任何位置，但仍可以从任何距离访问它们。 用于控制和操作 2D 和 3D 全息影像的思维模型和手势与直接操作的高度同步。
    :::column-end:::
    :::column:::
       [![运动控制器](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[运动控制器](motion-controllers.md)<br>
       运动控制器通过跨一系列距离的精确交互来扩展用户的物理功能，同时使用一只或两只手。 这些硬件附件提供了许多常用交互的快捷方式，并为各种操作提供有条不减的、可操作的反馈。 目前，运动控制器仅适用于 WINDOWS MIXED REALITY (WMR) 方案。 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>另请参阅
* [头部凝视并提交](gaze-and-commit.md)
* [头部凝视和停留](gaze-and-dwell.md)
* [使用手直接操作](direct-manipulation.md)
* [使用手指向和提交](point-and-commit.md)
* [免动手操作](hands-free.md)
