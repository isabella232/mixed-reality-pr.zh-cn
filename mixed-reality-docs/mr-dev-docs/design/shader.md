---
title: 着色器
description: 了解混合现实工具包标准着色器如何提供各种类型的视觉效果，这些效果可用于混合现实应用中的全息影像。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合现实，控件，交互，ui，ux，着色器，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，视觉效果
ms.openlocfilehash: 9a60c5065ddb5bcf410bb43b318575da50f7ccf8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600176"
---
# <a name="shader"></a>着色器

![着色器](images/UX_Hero_StandardShader.jpg)

由于全息对象与真实环境中的物理对象混合在一起，因此向用户提供视觉提示非常重要。 混合现实工具包标准着色器提供各种类型的视觉效果，可与全息影像一起使用。 着色系统使用单个灵活的着色器来实现类似于 Unity 的标准着色器的视觉对象。 着色器实现了 [熟知的设计系统原则](https://www.microsoft.com/design/fluent/#/) ，并在混合现实设备上保持高性能。
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a>使用 MRTK (混合现实工具包的视觉效果示例) 标准着色器 
:::row:::
    :::column:::
       ![移动](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **邻近感应**<br>
    :::column-end:::
    :::column:::
       ![旋转](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **边框细**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a>MRTK for Unity 中的标准着色器

* [MRTK-标准着色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

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
* [公告和尾随](billboarding-and-tag-along.md)
* [显示进度](progress.md)
* [表面磁吸](surface-magnetism.md)