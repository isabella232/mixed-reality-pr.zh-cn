---
title: 显示进度
description: 了解进度控制如何为用户提供反馈，指出混合现实应用中正在进行长时间运行的操作。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、设计、控件、ui、ux、进度指示器、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、MRTK、混合现实Toolkit
ms.openlocfilehash: 8d397f627b55409d640ac6925a72d6bf169e207c27cb2a90bcee990c7a8d7683
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207869"
---
# <a name="progress-indicator"></a>进度指示器

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

进度控件提供反馈，指出长时间运行的操作正在进行。 当进度指示器可见时，用户可以查看等待时间，并且无法与应用交互。

<br>

---

## <a name="types-of-progress"></a>进度类型

向用户提供有关发生的情况的信息非常重要。 在混合现实中，如果应用没有良好的视觉反馈，用户很容易被物理环境或对象分散注意力。 对于需要几秒钟的时间的情况，例如加载数据或场景正在更新时，显示可视指示器是一个好办法。 有两个选项可让用户了解操作正在进行 - 进度 **栏** 或 **进度环**。

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>进度条<br>
        进度栏显示任务的完成百分比。 应在操作期间使用，该操作的持续时间 (确定) ，但其进度不应阻止用户与应用的交互。<br>
        <br>
        *图像：进度栏示例HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![中的进度栏HoloLens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>进度环<br>
        "进度环"仅具有不确定状态，应在用户交互被阻止时使用，直到操作完成。<br>
        <br>
        *图像：进度环示例HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![设备上的进度环HoloLens示例](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>自定义对象的进度<br>
        可以通过使用自己的自定义 2D/3D 对象自定义 Progress 控件来添加应用的个性化和品牌标识。<br>
        <br>
        *图像：自定义网格示例在HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![中自定义网格示例HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>最佳实践

* 将 [广告板或标记](billboarding-and-tag-along.md) 紧密耦合到进度显示，因为用户可以轻松地将其头部移动到空白区域并丢失上下文。 如果用户看不到任何内容，应用可能看起来已崩溃。 "进度"预制板中内置了广告板和标记。
* 始终向用户提供有关发生的情况的状态信息。 "进度"预制条提供了各种视觉样式，Windows提供状态的标准环类型进度。 如果希望进度样式与应用的品牌保持一致，还可以将自定义网格与动画一起使用。

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>适用于 Unity 的混合现实 (MRTK Toolkit) 进度指示器

* [MRTK - 进度指示器预制](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK - 场景转换服务](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


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