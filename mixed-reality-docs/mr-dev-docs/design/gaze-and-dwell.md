---
title: 注视和停留
description: " (眼/head) 注视和停留输入模型的一般概述"
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合现实，注视，停留，交互，设计，眼睛跟踪，头跟踪
ms.openlocfilehash: ee8b6487079a071fe84606949314f2dd315df45f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677875"
---
# <a name="gaze-and-dwell"></a>注视和停留

手拿工具和零件，手势可能是没有意义或无法实现。
在某些上下文中，语音命令也可能不可靠，例如在过大的情况下。
注视和停留提供了一种熟悉且易于掌握的机制，用于在 HoloLens 上完成工作和无人参与。
此外，注视和停留在操作环境中与干扰干扰或静默约束无关。
我们区分 _注视和停留_ 区的两个变体： [打印头和](gaze-and-dwell-head.md) 停留区， [注视眼睛和停留](gaze-and-dwell-eyes.md)区。

## <a name="scenarios"></a>方案

注视和停留在某个人的 transact-sql 与其他任务繁忙的情况下，以及因环境或社交限制而导致的语音不是100%。
一个很好的例子是穿戴 HoloLens 的人在修理汽车发动机时获取参考信息。
倚靠在发动机舱内时，他们的手拿着工具或支撑着身体。
车库空间很大，工具不断敲打声和嘈杂声，难以使用语音命令。
注视和停留允许使用 HoloLens 的人员自信地浏览其参考材料，而不会中断工作流。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>输入模型</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>头部凝视和停留</td>
        <td>✔️ 推荐</td>
        <td>✔️ 推荐</td>
        <td>✔️ 推荐</td>
    </tr>
     <tr>
        <td>眼睛凝视和停留</td>
        <td>❌ 不可用</td>
        <td>✔️ 推荐</td>
        <td>❌ 不可用</td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a>请参阅
* [基于眼睛的交互](eye-gaze-interaction.md)
* [HoloLens 2 中的眼动跟踪](eye-tracking.md)
* [凝视和提交](gaze-and-commit.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手势](gaze-and-commit.md#composite-gestures)
* [手 - 指向并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)
