---
title: 开始手势
description: 了解如何使用启动手势在沉浸式头戴显示设备上HoloLens Windows Mixed Reality菜单。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实， 手势， 交互， 设计， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实 Toolkit， bloom
ms.openlocfilehash: f3ad9309c7232f20a25060b1d98d7374272ceea00f24be18d7263b8ec7002fb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213726"
---
# <a name="start-gesture"></a>开始手势

"开始"手势是一种用于调用"开始"菜单的手势。 这相当于在键盘上按Windows键、Xbox 控制器上的 Xbox 按钮或沉浸式头戴显示设备运动控制器上的Windows按钮。 请特别注意每个混合现实设备上保留的系统手势，以防止在设计交互时发生冲突。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>开花</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>"开始"按钮</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>眼睛凝视和手指向上收缩</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>开花

我们设计了"Bloom"来打开第一代HoloLens (中的) 菜单，这是一种模拟花店的符号手势。 它特别适合确保交互、易于使用和快速召回。 若要使用手势，请用手指向上和手指按住手，然后通过分散手指来打开手。

:::row:::
    :::column:::
        ![Bloom close](images/bloom-close.png)<br>
        **步骤 1：用手指将手指放在一起**<br>
    :::column-end:::
    :::column:::
        ![Bloom open](images/bloom-open.png)<br>
        **步骤 2：手部分散在一起**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>开始手势

在HoloLens 2中，我们将 Bloom 手势替换为虚拟手部按钮，这更符合用户的需求。 通过向用户显示上的按钮，他们可以直观地接触并按住另一手。

:::row:::
    :::column:::
        ![已准备就绪的"开始"按钮](images/wrist-button-ready.png)<br>
        **步骤 1：可向上键显示""按钮**<br>
    :::column-end:::
    :::column:::
        ![按下"开始"按钮](images/wrist-button-press.png)<br>
        **步骤 2：按按钮**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a>单只手的开始手势

> [!IMPORTANT]
> 为了让单只手的开始手势发挥作用，请执行以下操作：
>
> 1. 必须更新到 2019 年 11 月更新（版本 18363.1039）或更高版本。
> 1. 必须在设备上校准你的眼睛，使目视跟踪功能正常运行。 如果在注视“开始”图标时未看到其周围的环行点，则表明未在设备上校准你的眼睛。

也可以只用一只手使用"开始"手势。 将手与面向你的手放在一起，并查看内部包上的 **"** 开始"图标。 注视图标时，请将拇指和食指捏在一起。<br>
:::row:::
    :::column:::
        ![已准备就绪的"开始"按钮](images/wrist-button-ready.png)<br>
        **步骤 1：可向上键显示""按钮**<br>
    :::column-end:::
    :::column:::
        ![收缩按钮收缩](images/wrist-button-pinch.png)<br>
        **步骤 2：眼睛凝视按钮，然后收缩**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>另请参阅

* [本能交互](interaction-fundamentals.md)
* [眼睛凝视](eye-tracking.md)
* [语音输入](voice-input.md)