---
title: 手动菜单
description: 手部菜单允许用户为常用函数快速启动手动附加的 UI。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手、菜单、按钮、快速访问、布局、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、MRTK、混合现实Toolkit
ms.openlocfilehash: 76338f75250054c531560dc0b6cb18aa7130c09fe30a49b4afc3fd409f88fdc0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201964"
---
# <a name="hand-menu"></a>手动菜单

![Ulnar 手部位置](images/UX_Hero_HandMenu.jpg)

手部菜单是其中最独特的 UX 模式之HoloLens 2。 它允许你快速启动手动附加的 UI。 由于它可以随时访问，并且可以轻松显示和隐藏，因此它适用于快速操作。

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

你将在下面的列表找到有关使用手部菜单的建议最佳做法。 还可以在 [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)中查找演示手部菜单的示例场景。

<br>

---

## <a name="best-practices"></a>最佳实践

**使按钮数保持较小** 

由于手部锁定菜单和眼睛之间的距离非常近，并且用户随时都倾向于将焦点放在相对较小的可视区域 (因此视觉的注意圆锥大约是 10 度) ，因此建议将按钮数保持较小。 根据我们的探索，包含三个按钮的一列可以很好地将所有内容保留到 (FOV) 即使用户将手移到 FOV 中心。 

**使用手部菜单快速操作** 

引发一个手部并维持该位置很容易导致手部感到。 对需要短时间交互的菜单使用手动锁定方法。 如果菜单很复杂，并且需要延长交互时间，请考虑改为使用世界锁定或正文锁定。 

**按钮/面板角度**

菜单应向头部的相反中央和中间显示广告：这样，可以自然地移动手部，以与另一手交互，并避免触摸按钮时手部位置出现任何麻烦或手部姿势。 

**考虑支持单手或免手操作**

不要假定用户两手都始终可用。 当一只或两只手不可用时，请考虑各种上下文，并确保设计考虑到这些情况。 若要支持单手菜单，可以尝试在手部翻转时将菜单位置从手动锁定 (世界锁定) 。 对于免手方案，请考虑使用语音命令调用手部菜单。

**避免在系统主页按钮 (附近添加按钮)**

如果手部菜单按钮放置得离主按钮太近，则与手部菜单交互时可能会意外触发。

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>包含大型复杂 UI 控件的手动菜单

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
建议限制手动附加菜单上的按钮或 UI 控件的数量。 这是因为与大量 UI 元素的扩展交互可能会导致手部受累。 如果你的体验需要一个大型菜单，则为用户提供一种简单的方式来锁定菜单。 我们建议的一种技术是在手掉手或翻转离开用户时进行世界锁定，然后进行菜单控制。 第二种技术是允许用户使用另一手直接抓取菜单。 当用户释放菜单时，菜单应进行世界锁定。 这样一来，用户可以在一段长时间内轻松、自信地与各种 UI 元素进行交互。 

当菜单被世界锁定时，请确保提供一种移动菜单的方法，并关闭不再需要的菜单。 在菜单的两侧或顶部提供控点，使菜单可移动。 添加关闭按钮以允许菜单关闭。 允许用户在用户手部面向用户时将菜单重新附加在手上。 我们还建议要求用户凝视其手以防止误报 (请参阅下面的) 。

**显示可用性问题的大型菜单**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**手动放置的"世界锁定"菜单**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**手动抓取&拉取到世界锁定菜单**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>如何防止误报

如果只是使用"手部"作为事件来触发手部菜单，则当不需要手动菜单时，它可能会意外出现 (误报) ，因为人们有意移动手部 (以用于通信和对象操作) 和无意。 若要减少误报，请添加除"手部启动"事件外的额外步骤，以调用手部菜单 (例如完全打开手指或用户有意在手部) 。

**需要平面手部**

通过要求使用平面打开的手势，可以防止在用户操作对象或手势时在环境中通信时发生误报。 

**需要凝视**

通过要求用户使用眼睛凝视或头部凝视 (来凝视其手部) ，它可以防止误报，因为用户必须将焦点作为辅助激活步骤 (将焦点引导到手部，并设置可调整的距离阈值，以允许用户舒适) 。  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>手部菜单放置最佳做法

在人类剖析中，ulnar 下部是一种在 ulna 中附近运行的神经。 ulna 是在前群中发现的一个长根，从下部拉伸到最小手指。

下面是基于探索的两个建议位置：

:::row:::
    :::column:::
        ![Ulnar 手部在手部位置](images/UlnarSideHandMenu.gif)<br>
        **A.ulnar 在手心内**<br>
        此位置是可靠的，因为手不会相互重叠。 这对准确的手部检测和跟踪至关重要。
    :::column-end:::
    :::column:::
        ![上手的 Ulnar 手部位置](images/UlnarAboveHandMenu.gif)<br>
        **B.上面的 Ulnar**<br>
        此位置对于用户来说很舒适，因为他们无需过多地提升手部即可与手部菜单交互。 建议将菜单放在 **手心上方 13 cm** 的位置，并对齐 ulnar 树中的按钮。 [详细了解最佳按钮大小](interactable-object.md)<br>
        <br>
        出于技术原因，建议使用一个必需的实现来设置此位置：用户相反的手接近与之交互时，开发人员需要冻结菜单。 这样可以避免手部重叠时出现抖动，还可以更快地确定按钮的目标。<br>
        <br>
        HoloLens 2相机在手彼此分离时准确识别手部。 任何重叠的手都可能导致手部菜单离开定位点位置。<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>不建议的菜单位置

我们使用不同的菜单布局和位置完成了用户研究，不建议使用以下菜单位置，找到以下每项研究缺点：

:::row:::
    :::column:::
        ![arm 上方](images/AboveArm.gif)<br>
        **在 arm 上方**<br>
        1 - 难以维护良好的手部跟踪<br>
        2 - 由于位置不自然，导致用户感到不自然
    :::column-end:::
    :::column:::
        ![手指上方](images/AboveFingers.gif)<br>
        **手指上方**<br>
        1 - 手部因为长时间按住手部而感到手部减轻<br>
        2 - 手部跟踪索引和中指问题
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![中心上方的线心](images/handCenter.gif)<br>
        **上居中线**<br>
        1 - 手部跟踪问题，因为手重叠<br>
        2 - 手部因为长时间按住手与菜单交互而感到手部减轻
    :::column-end:::
    :::column:::
        ![顶部指 ](images/TopFingerTip.gif) **指顶部手部**<br>
        1 - 手部跟踪问题<br>
        2 - 手部远离正常姿势<br>
        3 - 由于手指之间的空间有限，意外地用其他手指按下按钮时问题
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Arm 的背面](images/BackOfTheArm.gif)<br>
        **手部背面**<br>
        1 - 可能会意外触发主页按钮<br>
        2 - 不是自然或舒适位置
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>适用于 Unity 的 MrTK (Mixed Reality Toolkit) 中的手动菜单

**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为手部菜单提供脚本和示例场景。 HandConstraintPalmUp 求解器脚本允许使用各种可配置选项将任何对象附加到手。 MRTK 的手动菜单示例包括一些有用的选项，例如平面手部和防止误报的凝视要求。

* [手部菜单文档](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [手部菜单示例场景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

可以使用 MRTK 示例中心应用HoloLens 2手动菜单示例。

* [MRTK 示例中心中的手动菜单场景](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

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