---
title: 头部凝视和提交
description: 开始处理打印头和提交输入模型，包括目标大小、位置和稳定。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality，注视，注视目标，交互，设计，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，目标，焦点，平滑
ms.openlocfilehash: 13a040a8309d084fcfdbfa91cbd9d63b595b004a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009447"
---
# <a name="head-gaze-and-commit"></a>头部凝视和提交

"[注视](gaze-and-commit.md)" 和 "提交" 输入 _模型是一_ 种特殊情况，涉及到对象以用户头方向为目标。 您可以使用辅助输入来操作目标，例如，手型手势和 "选择" 语音命令。 

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
        <td>头部凝视和提交</td>
        <td>✔️ 推荐</td>
        <td>✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</td>
        <td>➕ 备用选项</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>目标大小调整和反馈

一直看着头注视向量，可用于精细定位，但通常最适用于毛目标-获取更大的目标。 1度到1.5 度的最小目标大小允许成功的用户操作在大多数情况下，尽管目标为3度，但通常允许更高的速度。 用户的目标大小实际上是一个二维区域，即使对于3D 元素也是如此。 提供一些突出的提示，指出某个元素处于 "活动" 状态， (用户为其设定目标) 很有用。 这可能包括处理方式（如可见的 "悬停" 效果、音频突出显示或单击），或通过元素清晰显示光标。

![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)<br>
*最佳目标大小，以2米到远处*

<br>

![突出显示凝视目标对象的示例](images/gazetargeting-highlighting-940px.jpg)<br>
*突出显示凝视目标对象的示例*

## <a name="target-placement"></a>目标位置

用户经常无法在其视图字段中找到太高或较低的 UI 元素。 其中的大多数关注点在其主要关注点的周围，这大致在目视。 将大多数目标放在视平线位置附近的某个合理范围内可能有所帮助。 在任何时候，用户都可以专注于一个相对较小的视觉区域 (在视觉上，) 将视觉对象组合在一起，将 UI 元素分组到它们在概念上的相关程度，可以在用户将其看起来通过某个区域时，使用从项目到项目的 attentional。 在设计 UI 时，请注意 HoloLens 和沉浸式头戴显示设备之间视野的巨大差异。

![在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例](images/gazetargeting-grouping-1000px.jpg)<br>
*在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例*

## <a name="improving-targeting-behaviors"></a>改进目标设定行为

如果用户意向面向某个对象，则可以确定或将其视为非常近似，这有助于接受接近的未命中交互尝试，就好像它们的目标是正确的一样。 下面是一些可在混合现实体验中结合使用的成功方法：

### <a name="head-gaze-stabilization-gravity-wells"></a>头部凝视防抖动（“重力井”）

这应该是最多或全部开启。 此方法可删除用户可能出于移动原因而移动的自然头和抖动。

### <a name="closest-link-algorithms"></a>最邻近链接算法

这些算法最适用于具有稀疏交互式内容的区域。 如果很有可能确定用户尝试与之交互的概率很高，则可以通过假定某些级别来补充其目标功能。

### <a name="backdating-and-postdating-actions"></a>Backdating 和 postdating 操作

此机制非常适合需要快速完成的任务。 当用户在一系列目标和激活设法使其的同时进行时，可以采用某种目的。 这对于在早期测试) 生效之前/之后（ (50 ms 之前/之后），允许缺少的步骤对用户具有特别关注的目标有很大的作用。

### <a name="smoothing"></a>平滑处理

这种机制对于路径移动非常有用，因为自然的移动特征会降低轻微的抖动和 wobbles。 对路径运动进行平滑处理时，按移动的大小和距离而不是一段时间来平滑。

### <a name="magnetism"></a>磁吸

此机制可被视为最近的链接算法的更通用版本，即根据目标绘制游标，或者只是直观或不增加 hitboxes，因为用户通过使用一些交互式布局了解来更好地利用用户意图来实现目标。 这对于小型目标可能非常强大。

### <a name="focus-stickiness"></a>焦点粘性

确定要为其提供哪些邻近的交互式元素时，焦点到，焦点将为当前聚焦的元素提供偏移。 当在两个元素之间的中间点处浮动时，这有助于减少不稳定的焦点切换行为。

## <a name="see-also"></a>另请参阅

* [基于眼睛的交互](eye-gaze-interaction.md)
* [凝视和停留](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手势](gaze-and-commit.md#composite-gestures)
* [手 - 指向并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)



