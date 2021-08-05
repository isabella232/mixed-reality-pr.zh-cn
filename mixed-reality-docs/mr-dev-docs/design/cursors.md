---
title: 游标
description: 光标（或目标向量的指示器）为用户提供持续反馈，让用户了解用户HoloLens他们的意图。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (第一代) 、HoloLens 2、混合现实、光标、目标、凝视、手势、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、MRTK、混合现实 Toolkit、射线、输入
ms.openlocfilehash: 46e570328451078586109448bce28a7074bc9c2f791c15a284c85b845441fabe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187043"
---
# <a name="cursors"></a>游标

![游标](images/UX_Hero_Cursor.jpg)

光标根据头戴显示设备认为用户当前焦点处于给定时间的位置提供持续反馈。 光标反馈包括虚拟环境中响应输入的区域、全息影像或点。 即使光标是设备理解用户注意位置的数字表示形式，也与确定用户的意图不同。 游标反馈还让用户了解预期系统响应。 可以使用反馈将意图传达给设备，这会增加用户置信度。

有 3 种类型的光标：**手指、光线****和头部凝视**。 这些指针光标在设备、HoloLens和沉浸式头戴显示设备HoloLens 2输入形式。 下面是有关每种头戴显示设备类型和交互模型使用的游标类型的指南。 在混合现实Toolkit (MRTK) 中，我们创建了拖放游标模块来帮助你构建正确的指向体验。

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
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>手指光标</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>光线光标</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>头部凝视光标</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>手指光标

手指光标仅可用于HoloLens 2以增强"直接[操作与手](direct-manipulation.md)部"交互模式。 我们已将环连接到两个索引指的提示，以更好地了解手指指向何处。 环大小基于手指与 UI 图面的邻近度，当手指触摸 UI 时，该图面缩小为小点。 手指越近，环越小。 <br>

![手指光标](images/finger-cursor.png)<br>
手指光标 1 **的视觉反馈** 状态：环收缩为点。 2：环与表面对齐。 3：环与手指矢量垂直。 4：无环。

## <a name="ray-cursor"></a>光线光标

光线光标附加到远向射线的末尾，以允许操作手部无法到达的对象。 在沉浸式头戴显示设备中，射线从运动控制器中反射，以点光标结尾。 在HoloLens 2中，我们应用这些运动控制器射线的思维模型，并设计出源自手部、以环形光标结尾、与直接操作中使用的手指光标一致的手部射线。 <br>
:::row:::
    :::column:::
        ![光线光标控制器](images/ray-cursor-controller.png)<br>
        **运动控制器的光线光标**<br>
    :::column-end:::
    :::column:::
        ![光线光标手](images/ray-cursor-hand.png)<br>
        **手部射线光标**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>头部凝视光标

头部凝视光标是附加到不可见头部凝视向量末尾的点，该向量使用头部的位置和旋转进行指向。 若要执行操作，此指向光标与各种提交输入（如点击声、语音命令、停留和按下按钮）配对。 在HoloLens 2中，头部凝视最好与任何非空敲击的提交输入配对，因为空敲击和远手射线之间会存在交互冲突。 <br>
:::row:::
    :::column:::
        ![头部凝视光标手](images/head-gaze-cursor-hand.png)<br>
        **头部凝视光标和手势**<br>
    :::column-end:::
    :::column:::
        ![头部凝视光标语音](images/head-gaze-cursor-voice.png)<br>
        **使用语音命令头部凝视光标**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>游标自定义建议

若要自定义游标反馈行为和外观，下面是一些设计建议：

### <a name="cursor-scale"></a>游标刻度

* 光标不应大于可用目标，使用户能够轻松与 交互并查看内容。
* 根据你创建的体验，在用户四处查看时缩放光标也是一个重要的考虑因素。 例如，随着用户在你的体验中进一步查看，光标不应变得太小，因此会丢失。
* 缩放光标时，请考虑在缩放时向光标应用软动画，以赋予其自然感觉。
* 避免妨碍内容。 全息影像使体验令人记忆，并且光标不应从这些体验中消失。

### <a name="directionless-cursor-shape"></a>无向光标形状

* 虽然没有一个右光标形状，但建议使用无方向形状，如圆条。 以某种方向指向的游标 (例如，传统的箭头光标) 可能会让用户困惑始终如此。
* 这种情况的一个例外是，使用游标向用户传达交互指令时。 例如，在混合现实 OS 中缩放全息影像时，光标暂时包含箭头，指示用户如何移动手来缩放全息影像。

### <a name="look-and-feel"></a>外观

* 圆环图或圆环图形状的光标适用于许多应用程序。
* 选择最适合你正在创建的体验的颜色和形状。
* 游标特别容易进行 [颜色分离](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)。
* 具有均衡不透明度的小游标可保持信息性，而不会控制视觉对象层次结构。
* 请避免在光标后面使用阴影或突出显示，因为它们可能会干扰内容，并分散用户对当前任务注意力。
* 光标应与应用中的图面对齐并浮出。 用户有一种感觉，即系统可以看到他们正在查看何处，但系统也了解其周围的环境。 例如，混合现实 OS 中的光标与用户世界表面对齐，即使用户不直接查看全息影像，也产生感知世界感。
* 当光标靠近用户时，以磁方式将光标锁定到交互元素，有助于增强用户在使用选择操作时与该元素交互的置信度。

### <a name="visual-cues"></a>视觉提示

* 如果你的体验侧重于单个全息影像，则光标应仅对齐该全息影像，当你离开该全息影像时，会更改形状。 这可让用户了解全息影像是可操作且可以与之交互的。
* 如果应用程序使用空间映射，则光标可以对齐并放大它看到的每一个图面。 这会向用户提供反馈，HoloLens应用程序可以看到其空间。 这强化了全息影像在现实世界中真实性的事实，并有助于缩小真实与虚拟之间的差距。
* 了解当视图中没有全息影像或表面时光标应执行什么操作。 将其置于用户前面预先确定的距离是一种选择。

### <a name="possible-actions"></a>可能的操作

* 光标可以通过不同的图标表示，以传达全息影像可以执行的操作，例如缩放或旋转。
* 仅在游标上添加额外信息（如果它对于用户具有某种影响）。 否则，用户可能不会注意到状态更改或被光标混淆。

### <a name="input-state"></a>输入状态

* 我们可以使用光标显示用户的输入状态或意向。 例如，我们可以显示一个图标，告知用户系统可以看到其手部状态，并且应用程序知道他们已准备好采取措施。
* 我们还可使用光标向用户显示系统通过暂时的颜色更改听到的语音命令

* 可通过不同方式实现以下游标状态。 通过建模游标（如状态机）来实现这些不同的状态。 例如：
    * 空闲状态是显示默认游标的位置。
    * 就绪状态是检测到用户手处于就绪位置时的状态。
    * 交互状态是用户执行特定交互时的状态。
    * "可能的操作"状态或悬停状态是传达可在全息影像上执行的操作时。

还可以在检测不同状态时，以一种外观可显示不同艺术资产的方式实现这些状态。

<br>

---

## <a name="going-cursor-free"></a>进入"无游标"

当沉浸感是体验的关键组成部分，并且通过凝视和手势 (交互时，建议在无需) 时进行设计。 系统仍然需要满足游标的正常要求：为用户提供有关系统理解其指向的连续反馈，并帮助他们向系统传达其意图。 这可以通过其他明显的状态更改实现。

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>适用于 Unity 的混合现实 (MRTK Toolkit) 光标

默认情况下 [，MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) 为 [DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors) (游标预制) 其视觉状态与 shell 的系统游标相同。 它分配在 MRTK 的输入配置文件的“指针”下。 可以根据自己的体验替换/自定义此游标。 为了体验眼动跟踪输入，MRTK 还提供 EyeGazeCursor，它具有细微的视觉效果，可最大程度地减少干扰。

* [MRTK - 指针配置文件](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [MRTK - 输入系统](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [MRTK - 指针](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a>另请参阅

* [笔势](gaze-and-commit.md#composite-gestures)
* [头部凝视并提交](gaze-and-commit.md)