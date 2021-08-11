---
title: 眼睛凝视和停留
description: 首先概要了解眼睛凝视和停留输入模型，包括交互模型、设计准则和独特挑战。
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: 眼动跟踪, 混合现实, 输入, 眼睛凝视, 视线定位, HoloLens 2, 视线选择, 停留, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, HoloLens, MRTK, 混合现实工具包, 设计
ms.openlocfilehash: dfe74ee1fe304cc63bb0c547d01ebadeb0469b171caa806671887817c17f92ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201826"
---
# <a name="eye-gaze-and-dwell"></a>眼睛凝视和停留

“眼睛凝视和停留”交互模型  是[眼睛凝视和提交](gaze-and-commit.md)交互模型的特例：
1. 注视目标和 
2. 要确认选择目标，请使用辅助显式输入：只是一直看着要选择的目标。

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a>“眼睛凝视和停留”交互模型的优势 

如果你正在用手执行某个任务，或者手中拿了工具，则可能无法用手与全息影像交互。
选择全息影像时，一种解放双手的替代性交互方式是“眼睛凝视和停留”，换言之，“盯着看”。  通过这种方式，即使是行动严重受限的无法完全转动其头部或身体的用户（例如，在空间严重受限的工作环境中的用户），也可以与全息影像交互。
用户只需一直看着要选择的目标，系统就会显示不同的停留反馈来指示过程。

## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a>“眼睛凝视和停留”交互模型的难点

通常情况下，建议只在语音输入和手动输入都不可用的情况下使用基于停留的激活。 原因在于不易选择合适的停留时间。 新手用户可以使用较长的停留时间，专家用户则希望快速且高效地浏览其整个体验。 因此，难点在于如何根据用户的具体需求调整停留时间。
如果停留时间太短，则会因为全息影像一直在对用户的眼睛凝视进行响应而导致用户感到不适。 如果停留时间太长，则会给用户造成体验太慢且易中断的感觉，因为用户必须长时间盯着目标。

## <a name="design-recommendations"></a>设计建议

建议对停留反馈使用双状态方法：
1. 初动延迟  ：当用户开始看着目标时，系统不应立即响应，否则可能会给用户带来不愉快的体验，导致用户感到不适。 此时应启动一个计时器，用于检测用户是在有意盯着该目标，还是仅仅扫了它一眼。
在设定好临近度（即用户在注视而不是瞟着某个大型目标）的情况下，建议将初动时间设置为 150-250 毫秒。  
2. 启动停留反馈：  在确定用户是在有意盯着该目标以后，请开始显示停留反馈，通知用户停留激活正在启动。 
3. 持续反馈：  当用户持续看着目标时，显示一个连续进度指示器，这样用户就知道自己必须始终看着目标。 具体说来，对于眼睛凝视输入，建议一开始显示一个较大的圆圈或球体，然后将其缩小，通过这种方式吸引用户的视觉注意力。  显示一个表示最终状态的指示器（小圆圈）是为了告知用户停留将何时结束。 示例图如下所示。 
4. 完成：  如果用户一直注视该目标（又注视了 650-850 毫秒），则完成停留激活，选择被用户注视的目标。

![停留状态](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a>另请参阅

* [眼动跟踪](eye-tracking.md)
* [眼睛凝视和提交](gaze-and-commit-eyes.md)
* [凝视和提交](gaze-and-commit.md)
* [凝视和停留](gaze-and-dwell.md)
* [语音输入](../out-of-scope/voice-design.md)
