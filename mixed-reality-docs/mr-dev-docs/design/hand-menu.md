---
title: 手动菜单
description: 手动菜单允许用户快速为常用函数获取手动连接的 UI。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手型，菜单，按钮，快速访问，布局，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: e222d792d883ccacc71b177fbde21979c8dfcc77
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299912"
---
# <a name="hand-menu"></a>手动菜单

![Ulnar 端位置](images/UX_Hero_HandMenu.jpg)

"手形" 菜单是 HoloLens 2 中最独特的 UX 模式之一。 它可让你快速打开手动连接的 UI。 由于可以随时访问它，并且可以轻松地显示和隐藏，因此对于快速操作非常有用。

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

你将在下面的列表中找到建议使用的最佳实践。 你还可以在 [MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)中找到演示菜单的示例场景。

<br>

---

## <a name="best-practices"></a>最佳做法

**使按钮数保持较小** 

由于手锁定菜单和眼睛之间的距离接近，用户在任何时候都专注于相对较小的视觉区域 (attentional 的视觉效果约为10度) ，我们建议将按钮数保持为小。 基于我们的探索，一列包含三个按钮的工作非常好，因为即使在用户将其) FOV 移动到 FOV 的中心时，也可以通过将视图的所有内容保留在 " (视图" 字段中。 

**使用 "快速操作" 菜单** 

提起 arm 并维持位置可能很容易导致 arm 疲劳。 对需要短交互的菜单使用手锁定的方法。 如果菜单非常复杂并且需要延长交互时间，请考虑改用世界锁定或正文锁定。 

**按钮/面板角度**

菜单应以与之相对的肩和中间的方式为布告栏：这允许自然的手移动与菜单之间的交互，并在触摸按钮时避免任何难或令人不安的位置。 

**考虑支持单向或无需操作**

不要假设用户的手始终可用。 如果一项或两次操作都不可用，请考虑使用各种上下文，并确保你的设计帐户适用于这种情况。 若要支持右手菜单，可以尝试将菜单位置从 "手动锁定" 切换到 "全局锁定" （当手型翻转 (向下) 。 对于无需人工使用的方案，请考虑使用语音命令调用手形菜单。

**避免在手腕 (系统 "主页按钮附近添加按钮)**

如果将 "手形" 菜单按钮置于 "主页" 按钮附近，则可能会在与 "手形" 菜单交互时意外触发。

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>包含大型和复杂 UI 控件的菜单

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
建议限制手动附加菜单上的按钮或 UI 控件的数目。 这是因为，与大量 UI 元素的扩展交互可能会导致 arm 疲劳。 如果你的体验需要大菜单，请为用户提供一种简单的方式来锁定菜单。 我们建议的一种方法是在离开或离开用户时，进行全球锁定后菜单。 第二种方法是允许用户直接抓住菜单。 当用户释放菜单时，菜单应为 "全局锁定"。 这样一来，用户就可以在很长一段时间内轻松且自信地与各种 UI 元素交互。 

当菜单处于全局锁定状态时，请确保提供移动菜单的方法，并在不再需要菜单时关闭菜单。 通过在菜单边或顶部提供控点，使菜单可移动。 添加 "关闭" 按钮以允许菜单关闭。 允许菜单在用户正面正面向用户重新附加。 此外，我们还建议要求用户随时注视，以防止错误激活 (参见下面) 。

**显示可用性问题的大菜单**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**现有的全球锁定菜单**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**手动抓取 & 拉取到世界上-锁定菜单**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>如何防止错误激活

如果使用 "上滑作为事件来触发" 手形菜单，则在不需要它时可能会意外出现 (误报) ，因为人们会有意 (进行通信和对象操作) 。 若要减少错误激活，请添加除手掌事件外的附加步骤，以调用 (的手形菜单，如完全打开的手指或用户有意 gazing 的) 。

**需要单层掌**

通过要求平整的张开手，可以防止在用户在环境中进行通信的过程中操作对象或手势时出现错误激活。 

**需要注视**

通过要求用户通过眼睛眼睛或眼睛) 来 (注视，这会阻止错误激活，因为用户必须将其注意力视为辅助激活步骤 (，并使用可用于允许用户舒适) 的可调距离阈值。  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>手动菜单布局最佳实践

在人剖析中，ulnar 勇气是在 ulna 骨骼附近运行的勇气。 Ulna 是在 forearm 中找到的一个长骨骼，该骨骼从弯头拉伸到最小手指。

下面是基于探索的两个建议位置：

:::row:::
    :::column:::
        ![手掌内的 Ulnar 端位置](images/UlnarSideHandMenu.gif)<br>
        **手掌内的 Ulnar**<br>
        此位置是可靠的，因为不会相互重叠。 这对于准确的手动检测和跟踪至关重要。
    :::column-end:::
    :::column:::
        ![Ulnar 右侧位置](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar 以上的手势**<br>
        此位置对用户非常熟悉，因为他们不需要将其扶手提高到与手形菜单的交互。 建议将菜单 **13 厘米** 置于掌上，并对齐 ulnar 掌中的按钮。 [阅读有关最佳按钮大小的详细信息](interactable-object.md)<br>
        <br>
        出于技术原因，我们建议将此位置用于一个必需实现：一旦用户与之交互，开发人员将需要冻结该菜单。 这将避免 jitteriness 与指针重叠，还允许更快地定位按钮。<br>
        <br>
        HoloLens 2 相机在彼此分开时可以精确地识别。 任何重叠的手势都可以导致手形菜单远离定位点位置。<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>不建议的菜单位置

我们使用不同的菜单布局和位置完成了用户研究， **不建议** 使用以下菜单位置，查找下面每个研究的缺点：

:::row:::
    :::column:::
        ![上方 arm](images/AboveArm.gif)<br>
        **Arm 之上**<br>
        1-难以维护良好的手写跟踪<br>
        2-由于非自然位置导致用户疲劳
    :::column-end:::
    :::column:::
        ![上手指](images/AboveFingers.gif)<br>
        **上手指**<br>
        1-疲劳，因为要长时间持有<br>
        2-手动跟踪索引和中间指的问题
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![上方中心掌](images/handCenter.gif)<br>
        **上方-中心掌托**<br>
        1-由于指针重叠而发生的手动跟踪问题<br>
        疲劳，因为需要长时间来与菜单交互
    :::column-end:::
    :::column:::
        ![Top 手指 ](images/TopFingerTip.gif) **top 手指**<br>
        1-手写跟踪问题<br>
        2-疲劳在正常情况上保持手动<br>
        3-由于手指间的空间有限，出现意外的按下按钮的问题
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Arm 背面](images/BackOfTheArm.gif)<br>
        **Arm 背面**<br>
        1-可以意外触发主按钮<br>
        2-不是自然或舒适的位置
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK 中的菜单 (混合现实工具包) 适用于 Unity

**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为手形菜单提供脚本和示例场景。 HandConstraintPalmUp 求解器脚本允许您将任何对象附加到各种可配置选项。 MRTK 的手形菜单示例包含有用的选项，例如，用于防止错误激活的平面掌和注视要求。

* [手动菜单文档](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [手型菜单示例场景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

可以在 HoloLens 2 中试用带有 MRTK 示例中心应用的菜单示例。

* [MRTK 示例中心中的手形菜单场景](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a>另请参阅

* [光标](cursors.md)
* [手部射线](point-and-commit.md)
* [Button](button.md)
* [可交互对象](interactable-object.md)
* [边界框和应用栏](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手动菜单](hand-menu.md)
* [追踪菜单](near-menu.md)
* [对象集合](object-collection.md)
* [语音命令](voice-input.md)
* [键盘](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑块](slider.md)
* [着色器](shader.md)
* [公告和尾随](billboarding-and-tag-along.md)
* [显示进度](progress.md)
* [表面磁吸](surface-magnetism.md)
