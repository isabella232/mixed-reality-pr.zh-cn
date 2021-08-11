---
title: 头部凝视和提交
description: 开始使用头部凝视和提交输入模型，包括目标大小调整、放置和稳定。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: 混合现实， 凝视， 凝视目标， 交互， 设计， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实 Toolkit， 目标， 焦点， 平滑
ms.openlocfilehash: 641e403df23b2559429ca80aa06f384c4845ee347518adca2cfde1b3dbe874dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223649"
---
# <a name="head-gaze-and-commit"></a>头部凝视和提交

_头部凝视和提交_ 是凝视和提交输入 [](gaze-and-commit.md)模型的一种特殊情况，涉及以具有用户头部方向的对象为目标。 可以使用辅助输入（例如手势敲击或"选择"语音命令）对目标操作。 

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
        <td>头部凝视和提交</td>
        <td>✔️ 推荐</td>
        <td>✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</td>
        <td>➕ 备用选项</td>
    </tr>
</table>

---

## <a name="head-and-eye-tracking-design-concepts-demo"></a>头部和眼动跟踪设计概念演示

若要了解头部和眼动跟踪设计概念的运行情况，请查看下面的“设计全息影像 - 头部跟踪和眼动跟踪”视频演示。 完成后，请继续详细了解特定主题。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

此视频来自于“设计全息影像”HoloLens 2 应用。在[此处](https://aka.ms/dhapp)下载并享受完整体验。

## <a name="target-sizing-and-feedback"></a>目标大小调整和反馈

头部凝视向量已反复显示，可用于精细定位，但通常最适合用于总目标 -获取更大的目标。 1 度到 1.5 度的最小目标大小允许在大多数情况下成功执行用户操作，尽管目标 3 度通常允许更高的速度。 用户的目标大小实际上是 2D 区域，即使对于 3D 元素，无论面向 3D 元素的投影都应是目标区域。 提供一些突出的提示，指出某个元素是 ("活动"的提示，) 有用。 这可能包括可见"悬停"效果、音频突出显示或单击或光标与元素的清晰对齐等处理。

![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)<br>
*2 米距离的最佳目标大小*

<br>

![突出显示凝视目标对象的示例](images/gazetargeting-highlighting-940px.jpg)<br>
*突出显示凝视目标对象的示例*

## <a name="target-placement"></a>目标位置

用户通常找不到其视场中过高或低的 UI 元素。 他们大部分注意力都集中在主要焦点周围的区域，这大约在眼睛级别。 将大多数目标放在视平线位置附近的某个合理范围内可能有所帮助。 考虑到用户往往随时专注于相对较小的可视区域 (视觉的注意圆环大约是 10 度) ，在概念上将 UI 元素分组到相关程度后，当用户将视线移到某个区域时，可以使用从项到项的注意链接行为。 在设计 UI 时，请注意 HoloLens 和沉浸式头戴显示设备之间视野的巨大差异。

![在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例](images/gazetargeting-grouping-1000px.jpg)<br>
*在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例*

## <a name="improving-targeting-behaviors"></a>改进目标设定行为

如果可以确定或近似地确定用户目标目标，则接受近乎错过的交互尝试会很有帮助，就像它们的目标正确一样。 下面是一些可以合并到混合现实体验中的成功方法：

### <a name="head-gaze-stabilization-gravity-wells"></a>头部凝视防抖动（“重力井”）

这应该会在大多数或所有时间打开。 此方法可消除用户可能由于查找和说话行为而移动的自然头部和头部抖动。

### <a name="closest-link-algorithms"></a>最邻近链接算法

这些算法最适合具有稀疏交互式内容的区域。 如果确定用户尝试与之交互的可能性很高，则可以通过假设一定的意向级别来补充其目标能力。

### <a name="backdating-and-postdating-actions"></a>备份和发布操作

此机制非常适合需要快速完成的任务。 当用户快速完成一系列目标定位和激活操作时，假设一些意向会很有用。 此外，允许遗漏的步骤针对用户在点击之前或经过 (50 毫秒之前或之后稍稍聚焦的目标（在 50 毫秒之前/之后）有效，这一点也很有用) 。

### <a name="smoothing"></a>平滑处理

此机制可用于路径移动，减少由于自然头部移动特征而出现轻微抖动和抖动。 对路径运动进行平滑处理时，按运动的大小和距离（而不是一段时间）平滑。

### <a name="magnetism"></a>磁吸

此机制可视为更常规的最近链接算法版本-将光标绘制到目标，或只是增加命中框（不管是否可见）。因为用户通过使用交互布局的一些知识来更好地接近用户意向来接近可能的目标。 对于小型目标，这非常强大。

### <a name="focus-stickiness"></a>焦点粘性

在确定要向哪个附近交互元素提供焦点时，焦点粘性会向当前聚焦的元素提供偏差。 当在具有自然干扰的两个元素之间的中点浮动时，这有助于减少不稳定的焦点切换行为。

## <a name="see-also"></a>另请参阅

* [基于眼睛的交互](eye-gaze-interaction.md)
* [凝视和停留](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手势](gaze-and-commit.md#composite-gestures)
* [手 - 指向并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)