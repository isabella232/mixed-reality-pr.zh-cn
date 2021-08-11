---
title: 关于 Maquette
description: Maquette 及其功能简介。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality，Maquette， 原型制作， 混合现实， 虚拟现实， VR， MR， 反馈， 反馈中心， bug
ms.openlocfilehash: 81c09bf22ea531a76156c9264e127593b6302ad5d0bcb248de9518bfb647717b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197882"
---
# <a name="about-maquette"></a>关于 Maquette

<!-- TODO(Harrison): Need consolidated logo with text -->
![徽标 ](../images/MaquetteIcon.png) Maquescript 简介

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
Maquette 集成了标准 ECMA 5.1 Javascript，支持在 Maquette 场景和对象（可以从 VSCode 中编辑和执行）中投资交互性。 公开对象的属性，用于从脚本、调用的对象方法以及字段化的对象和系统事件中读取和设置。 脚本还可通过可通过脚本访问的系统对象与 Maquette 本身进行交互。 用户可以与之交互的各种 UI 控件是系统的一部分。 在 Maquette 中创作时，可以添加这些脚本，也可以从脚本中创建和管理这些脚本。 具有这些元素的用户交互事件 (数据输入、单击等) 也会作为事件向脚本公开。 通过这些新增功能，可以构建简单到复杂的场景，从试验到数据可视化，到混合现实用户方案的探索，到 AR 或 VR 中完全实现的体验。

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
60 秒"ish 视频
* 条目标题卡
  * 在 Maquette 中创建交互式混合现实内容
  * 脚本编写/交互/UI 系统
* 团队或视频字幕欢迎使用 VO？  解释：
  * 脚本背后的推理，以启用交互式 MR 内容的创建
  * 了解如何在非常广泛的画笔笔划中使用
* 脚本编写 vingette 的运行
  * "撰写"对话框
  * 从大纲生成应用 (应用演示) 
  * 在照片测量模型中撰写
  * 与故障排除指南交互
  * VSCode 中调试脚本的屏幕视图
  * 从场景中的对象获取对脚本的访问权限
  * 等。。。
* 末尾的摘要标题卡
  * Maquette 链接
  * 编写脚本的入门位置
  * 公告/状态/社区
  * 请期待查看你可以执行哪些工作/提交 (？) 
  * 反馈以及我们可如何提供更好的服务

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [入门](installation.md)
* [示例和示例应用](../samples/overview.md)
* [支持](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a>向我们发送反馈

我们希望了解你的体验和结果。 始终欢迎提供反馈、建议和 bug 报告！
<链接？>