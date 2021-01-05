---
title: 免手动
description: 了解用户可能会遇到的有关动手和控制器接口的问题，以及各种免提备选方案。
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: 混合现实，无人参与，注视，注视目标，交互，设计，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，语音输入，可用性
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847684"
---
# <a name="hands-free"></a>免手动

## <a name="scenarios"></a>方案

如 [交互模型概述](interaction-fundamentals.md)中所述，一旦确定了用户及其目标，就可以在工作完成任务时询问自己面临的环境或环境挑战。 例如，许多用户都需要使用他们的手来实现其真实目标，并且它们会很难与基于手工控制器的界面进行交互。

一些具体方案包括： 
* 在用户双手被占用时引导用户完成任务
* 在用户双手被占用时参考材料
* 手部疲劳
* 无法跟踪手套
* 手里拿着东西
* 使用大手手势时的社交 awkwardness
* 狭小空间

## <a name="hands-free-modalities"></a>无人参与情态

### <a name="voice-input"></a>[语音输入](voice-input.md)

使用语音执行命令和控制接口提供了一种便捷的方式来操作，并使用快捷方式跳过多个步骤（如果需要）。 使用语音输入时，用户可以将任何按钮的名称大声激活， _( "查看它，说它" )_ ，并与可以完成任务的数字代理进行联系。

### <a name="gaze-and-dwell"></a>[凝视和停留](gaze-and-dwell.md)

在某些免提情况下，使用你的声音并不理想，甚至不可能。 很大的工厂环境、隐私或社会规范都可以进行限制。 使用 "注视 + 停留" 模型，用户无需任何额外的眼睛即可在应用中导航，而只需在目标位置) 的 gazing (，并在一段时间内 lingers。 若要详细了解注视和停留的各个设计注意事项，请查看 [眼睛和停留和眼睛](gaze-and-dwell-eyes.md) [+ 停留](gaze-and-dwell-head.md)。

## <a name="transitioning-in-and-out-of-hands-free"></a>转换为无干预

在这些情况下，让你可以轻松地与用于命令和导航的全息影像进行交互，范围可能是对应用程序的绝对要求，即端到端的应用程序的绝对要求。 

如果应用程序要求始终使用免提，无论是通过使用停留、自定义语音命令还是单个语音命令，"选择"，都请确保在用户界面中设置合适的便利。 

如果目标用户需要自行从手切换到无人参与，则必须考虑以下原则。

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>假设用户已处于要切换到的模式
例如，如果用户在工厂地面上，观看其 HoloLens 上的视频参考，并决定提起扳手开始工作，则她很可能会开始免费工作，而无需将扳手按下按钮。 她可以使用语音命令调用语音会话，停留在已可见的 UI 上，开始停留，或说 "select" 一词。

用户可以： 
* 在无人参与的情况下切换到无人参与
* 用双手切换
* 使用控制器切换到控制器 

### <a name="create-redundant-ways-to-switch-modes"></a>创建冗余方式来切换模式

第一个原则就是访问，另一个原则就是可用性。 不应该只是一种方法可以在模式中进行转换。 

以下是一些示例： 
* 用于开始语音交互的按钮
* 用于转换到的语音命令，使用打印头和停留

### <a name="add-a-dash-of-drama"></a>添加 drama 的短划线

模式切换是一件很大的作用。 在这些转换发生时，这一点很重要，因为这种转换是一个明显的交换机，让用户知道发生了什么情况。 

## <a name="usability-checklist"></a>可用性清单

**用户可以执行所有操作，也可以从端到端免费完成，**
* 每个种不可交互应可随时访问
* 确保所有自定义手势（如调整大小、放置、swipes、点击等）都有替换。
* 确保用户能够自信地控制 UI 的存在、位置和详细程度
    * 正在获取 UI
    * 对 (FOV) 的视图以外的 UI 进行寻址
    * 我看到了多少，

**与正确的实用一起教授和加强的交互的机制是什么？**

用户了解 .。。
* ...它们处于哪种模式？
* ...在此模式下可以执行哪些操作？
* ...什么是当前状态？
* ...如何转换？
    
**UI 是否经过优化，无人参与？**   

* 示例：停留实用并非内置于典型的2D 模式
* 示例：语音目标更适合对象突出显示
* 示例：对于需要打开的标题，语音交互更好

## <a name="see-also"></a>另请参阅

* [HoloLens 2 中的眼动跟踪](eye-tracking.md)
* [凝视和提交](gaze-and-commit.md)
* [凝视和停留](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手势](gaze-and-commit.md#composite-gestures)
* [手 - 指向并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)
