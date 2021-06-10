---
title: 显示进度
description: 了解进度控件如何向用户提供在混合现实应用中运行长时间运行的操作的反馈。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，控件，ui，ux，进度指示器，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: 01f032efb887ecfc6f8d66683fb954cd0574a4f3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600546"
---
# <a name="progress-indicator"></a>进度指示器

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

进度控件提供长时间运行的操作的反馈。 当进度指示器可见时，用户可以看到等待时间并且无法与应用进行交互。

<br>

---

## <a name="types-of-progress"></a>进度类型

向用户提供有关发生的情况的信息非常重要。 在混合现实中，如果你的应用程序不具备良好的视觉反馈，则可以轻松地在物理环境或对象上对用户进行工作。 对于需要几秒钟，如加载数据或场景正在更新的情况，最好是显示可视指示器。 有两个选项可用于向用户显示操作正在进行– **进度栏** 或 **进度环**。

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>进度栏<br>
        进度栏显示任务完成的百分比。 它应在其持续时间已知 (确定性) 的操作过程中使用，但其进度不应阻止用户与应用程序交互。<br>
        <br>
        *图像： HoloLens 中的进度栏示例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 中的进度栏示例](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>进度环<br>
        进度环仅具有不确定状态，并且在操作完成之前阻止用户交互时使用。<br>
        <br>
        *图像： HoloLens 中的进度环形示例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 设备上的进度环示例](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>自定义对象的进度<br>
        你可以通过使用你自己的自定义 2D/3D 对象自定义进度控件来添加到应用的个性和品牌标识。<br>
        <br>
        *Image：自定义网格示例（HoloLens）的进度*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 中的自定义网格示例的进度](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>最佳实践

* 将 [billboarding 或标记一起](billboarding-and-tag-along.md) 紧密地转换为进度的显示，因为用户可以轻松地将其标头移到空空间，并丢失上下文。 如果用户无法看到任何内容，你的应用可能看起来好像已崩溃。 Billboarding 和标记一起内置于 prefab 中。
* 提供有关用户发生的情况的状态信息始终是好的。 进度 prefab 提供了各种视觉样式，包括用于提供状态的 Windows 标准环形类型进度。 如果希望进度的样式与应用的品牌保持一致，还可以将自定义网格与动画一起使用。

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK 中的进度指示器 (适用于 Unity 的混合现实工具包) 

* [MRTK-进度指示器 prototyping](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK-场景转换服务](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


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