---
title: 关于 Maquette
description: Maquette 及其功能简介。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality，Maquette，原型设计，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935414"
---
# <a name="about-maquette"></a>关于 Maquette

<!-- TODO(Harrison): Need consolidated logo with text -->
![徽标 ](../images/MaquetteIcon.png) MaquetteScript 简介

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
Maquette 集成了标准 ECMA 5.1 Javascript，实现 Maquette 场景和对象（可在 VSCode 中进行编辑和执行）的交互。 对象的属性是从脚本、调用的对象方法以及对象和系统事件现场中读取和设置公开的。 脚本还可以通过脚本访问的系统对象与 Maquette 本身交互。 用户可与之交互的各种 UI 控件都是系统的一部分。 当在 Maquette 中创作或从脚本内创建和管理时，可添加这些项。 具有这些元素的用户交互事件 (数据输入、点击等) 也会公开给作为事件编写脚本。 通过这些新增功能，可以构建简单易用的场景，从试验到数据可视化，到探索的混合现实用户方案，到在 AR 或 VR 中充分认识到的体验。

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
60 second'ish 视频
* 输入标题卡
  * 在 Maquette 中创建交互式混合现实内容
  * 脚本/交互/UI 系统
* 欢迎按团队或视频标题进行欢迎？  说明
  * 通过编写脚本来支持创建交互式 MR 内容的推理
  * 了解如何在广泛的画笔笔划中使用它
* 编写 vingette 的操作脚本
  * 组合对话框
  * 构建大纲 (的应用程序演示) 
  * 在 photogrammetry 模型中撰写
  * 与故障排除指南交互
  * 在 VSCode 中调试脚本的屏幕视图
  * 从场景中的对象获取脚本的访问权限
  * 等等 .。。
* 结束时的摘要卡
  * 链接到 Maquette
  * 在何处开始编写脚本
  * 公告/状态/社区
  * 期待查看可以执行/提交 ( 操作的内容 ) 
  * 反馈和我们如何更好地为你提供服务

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [入门](installation.md)
* [示例和示例应用](../samples/overview.md)
* [支持](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a>向我们发送反馈

我们期待收到你的体验和结果。 反馈、建议和 bug 报告始终欢迎使用！
<链接？ >