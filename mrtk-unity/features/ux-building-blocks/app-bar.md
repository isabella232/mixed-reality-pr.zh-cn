---
title: 应用栏
description: MRTK 中的应用栏概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 应用栏，
ms.openlocfilehash: 1ecb43d25a4353ff4c3bd8350efaab877900a5b979cd42d2c8d1cb91ce32ae0c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198262"
---
# <a name="app-bar"></a>应用栏

![应用栏](../images/app-bar/MRTK_AppBar_Main.png)

应用栏是一个 UI 组件，与 [边界控件脚本一起](bounds-control.md) 使用。 它将按钮控件添加到对象，并意图对其进行操作。 使用"调整"按钮，可以取消/激活对象的边界控制接口。 "删除"按钮应从场景中删除对象。

## <a name="how-to-use-app-bar"></a>如何使用应用栏

将 `AppBar` " (assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) 拖放到场景层次结构中。 在组件的检查器面板中，分配具有边界控件的任何对象作为目标 *边界框* ，以将应用栏添加到其中。

**重要提示：** 目标对象的边界控制激活选项应为"手动激活"。

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
