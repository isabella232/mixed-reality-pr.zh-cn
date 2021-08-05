---
title: 凝视和停留
description: 大致了解混合现实应用程序的眼睛和头部凝视和停留输入模型。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合现实， 凝视， 停留， 交互， 设计， 眼动跟踪， 头部跟踪， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实 Toolkit
ms.openlocfilehash: c65c13b06df70ed5471b283ad349dd72e1575018a98913177983d7a13571d666
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213671"
---
# <a name="gaze-and-dwell"></a>凝视和停留

手拿工具和零件，手势可能是没有意义或无法实现。
在某些上下文中，语音命令也不可靠，例如，在过于朗读的情况下。
凝视和停留提供了一种熟悉且易于掌握的机制，用于进行头部启动和HoloLens。
此外，凝视和停留是一种很好的回退，与操作环境中干扰或静音约束无关。
我们区分凝视和停留的两种 _变体_： [头部凝](gaze-and-dwell-head.md) 视和停留 [以及眼睛凝视和停留](gaze-and-dwell-eyes.md)。

## <a name="scenarios"></a>方案

在一个人手正忙于执行其他任务，并且由于环境或社会约束，语音并非 100% 可靠或可用的情况下，凝视和停留功能非常出色。
一个很好的例子是穿戴 HoloLens 的人在修理汽车发动机时获取参考信息。
倚靠在发动机舱内时，他们的手拿着工具或支撑着身体。
车库空间很大，工具不断敲打声和嘈杂声，难以使用语音命令。
凝视和停留可让使用HoloLens人员自信地导航其参考资料，而不会中断其工作流。

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></td>
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

 ## <a name="see-also"></a>另请参阅

* [基于眼睛的交互](eye-gaze-interaction.md)
* [HoloLens 2 中的眼动跟踪](eye-tracking.md)
* [凝视和提交](gaze-and-commit.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手势](gaze-and-commit.md#composite-gestures)
* [手 - 指向并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)