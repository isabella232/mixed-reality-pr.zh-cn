---
title: 开始手势
description: 启动笔势以调用 "开始" 菜单。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实，手势，交互，设计，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，布隆
ms.openlocfilehash: 1994b38341dfdb2ef1cdb326cf7747c0af5f9c34
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703263"
---
# <a name="start-gesture"></a>开始手势

开始手势是用于调用 "开始" 菜单的笔势。 它相当于按键盘上的 Windows 键、Xbox 控制器上的 Xbox 按钮或沉浸式耳机运动控制器上的 Windows 按钮。 务必要了解在每个混合现实设备上为系统保留了哪些手势，以防止在设计交互时出现冲突。

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
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
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
        <td>手腕按钮</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>眼睛和掌上手掌</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>开花
为了在 HoloLens (第一代) 中打开 "开始" 菜单，我们设计了 "布隆"，这是一个模拟花开花的符号手势。 这是 surefooted 交互的独特之处，易于执行，并可快速回调。 若要在 HoloLens (第一代) 上执行布隆手势，请将掌托在一起，并将其放在一起，然后将手指分散在一起。

:::row:::
    :::column:::
        ![布隆关闭](images/bloom-close.png)<br>
        **步骤1：将手掌集中到一起**<br>
    :::column-end:::
    :::column:::
        ![布隆打开](images/bloom-open.png)<br>
        **步骤2：掌上手掌**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>开始手势
在 HoloLens 2 中，我们将布隆手势替换为虚拟手腕按钮，该按钮允许更多的 instinctual 交互，无需其他教学。 通过向用户显示手腕上的按钮，用户可以以直观的方式进行访问，并将其与他人一起使用。

:::row:::
    :::column:::
        ![手腕按钮就绪](images/wrist-button-ready.png)<br>
        **步骤1：掌上以显示 "手腕" 按钮**<br>
    :::column-end:::
    :::column:::
        ![手腕按钮按下](images/wrist-button-press.png)<br>
        **步骤2：按 "手腕" 按钮**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a>单向开始手势

> [!IMPORTANT]
> 对于要运行的单移交开始手势：
>
> 1. 您必须更新到2019年11月更新 (生成 18363.1039) 或更高版本。
> 1. 您的眼睛必须在设备上校准，以便目视跟踪能够正常工作。 查看 "开始" 图标时，如果看不到轨道点，则不会在设备上校准眼睛。

您还可以只用一只手执行开始手势。 为此，请在你的掌上，为你的掌上，查看内部手腕上的 " **开始" 图标** 。 **保持您的眼睛，同时** 将您的拇指和食指汇聚在一起。<br>
:::row:::
    :::column:::
        ![手腕按钮就绪](images/wrist-button-ready.png)<br>
        **步骤1：掌上以显示 "手腕" 按钮**<br>
    :::column-end:::
    :::column:::
        ![手腕按钮挤压](images/wrist-button-pinch.png)<br>
        **步骤2：目视看着按钮，然后捏紧**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>另请参阅

* [本能交互](interaction-fundamentals.md)
* [眼睛-注视](eye-tracking.md)
* [语音输入](voice-input.md)
