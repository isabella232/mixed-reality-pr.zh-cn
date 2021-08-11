---
title: Controllers
description: 如何在 MRTK 中使用控制器
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 控制器，
ms.openlocfilehash: bc6aea1abda85567ab1b0db2616b529a92b4165e9b9cbcbc4b8b3cecd8a34c9f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224747"
---
# <a name="controllers"></a>Controllers

控制器由输入提供程序 自动创建 [**和销毁**](input-providers.md)。 每个控制器类型都有一些由轴类型定义的物理输入，告诉我们输入值 (（数字、单轴、双轴、六 Dof、...) ）的数据类型，以及描述输入来源的输入类型 *(* Button Press、Trigger、Thumb Stick、Spatial Pointer...) 。 物理输入通过"控制器输入映射配置文件"中的 "混合现实" 组件中的"输入系统配置文件" Toolkit操作。 

![控制器输入映射](../images/input/ControllerInputMapping.png)
