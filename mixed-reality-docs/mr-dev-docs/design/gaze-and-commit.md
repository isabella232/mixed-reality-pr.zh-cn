---
title: 凝视并提交
description: 了解凝视和提交输入模型，包括两种类型的凝视 (头部凝视和凝视) 以及各种类型的提交。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合现实， 凝视， 凝视目标， 交互， 设计， 眼动跟踪， 头部跟踪， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196562"
---
# <a name="gaze-and-commit"></a>凝视并提交

_凝视和_ 提交是一个基本的输入模型，它与我们使用鼠标与计算机交互的方式密切相关：单击 _"&"。_ 在此页上，我们引入了两种类型的凝视输入 (头部和眼睛凝视) 以及不同类型的提交操作。 _凝视和提交_ 被视为具有间接操作的远端输入模型。 它最适合用于与无法访问的全息内容进行交互。

混合现实头戴显示设备可以使用用户头部的位置和方向来确定其头部方向向量。 将凝视视为直接从用户眼睛之间的方向直接指向的箭头。 这可粗略呈现出用户正查看的位置。 应用程序可以将此射线与虚拟或真实对象相交，并绘制该位置的光标，让用户知道目标对象。

除了头部凝视之外，一些混合现实头戴显示设备（HoloLens 2）还包括生成眼睛凝视矢量的眼动跟踪系统。 这可精细测量用户正在查看的位置。 在这两种情况下，凝视都表示用户意向的重要信号。 系统可以解释和预测用户预期操作越好，用户满意度和性能就越好。

下面是一些示例，说明混合现实开发人员如何从头部或眼睛凝视中获益：
* 应用可以将凝视与场景中的全息影像相交，以确定用户注意力的 (通过眼睛凝视) 。
* 应用可以基于用户的凝视来通道手势和控制器按下，这样用户就可以无缝选择、激活、抓取、滚动或与其全息影像交互。
* 您的应用程序可让用户在实际的表面上放置全息影像，方法是将其表面与空间映射网格进行交叉处理。
* 您的应用程序可以知道用户不会看到重要对象的方向，这会使您的应用程序能够通过视觉对象和音频提示来转向该对象。

<br>

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
         <tr>
        <td>眼睛凝视和提交</td>
        <td>❌ 不可用</td>
        <td>✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</td>
        <td>❌ 不可用</td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>标题和眼睛跟踪设计概念演示

若要查看标题和目视跟踪的设计概念，请参阅下面的 **设计全息影像-打印头跟踪和眼睛跟踪** 视频演示。 完成后，请继续详细了解特定主题。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*此视频取自 "设计全息影像" HoloLens 2 应用。下载并在 [此处](https://aka.ms/dhapp)享受完全体验。*

## <a name="gaze"></a>凝视

### <a name="eye--or-head-gaze"></a>眼后看好了吗？
当面对问题时，有几个注意事项需要考虑是否应使用 "眼睛和提交" 或 "良好和提交" 输入模型。 如果你正在开发沉浸式耳机或用于 HoloLens (第一代) ，则选择简单：打印头，并提交。 如果你正在开发 HoloLens 2，则选择会稍微难些。 务必要了解每种方法所附带的优点和挑战。
在下表中，我们编译了一些广泛的专业人员和职业，以对比眼睛和眼睛的目标。 这从很大程度上来看，我们建议在此处了解各种混合现实中的眼睛目标：
* [Hololens 2 上的目视跟踪](eye-tracking.md)：在 hololens 2 上提供新的目视跟踪功能（包括一些开发人员指南）。 
* [目视的交互](eye-gaze-interaction.md)：计划使用目视跟踪作为输入时的设计注意事项和建议。

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>目视瞄准目标</strong></td>
        <td><strong>头部凝视目标设定</strong></td>
    </tr>
    <tr>
        <td>Fast!</td>
        <td>比较</td>
    </tr>
    <tr>
        <td>低 (几乎不需要任何人体运动) </td>
        <td>可能很难受 - 可能 (，例如，) </td>
    </tr>
    <tr>
        <td>不需要光标，但建议提供细微的反馈</td>
        <td>需要显示游标</td>
    </tr>
    <tr>
        <td>没有平滑的眼部运动 - 例如，不适合绘制</td>
        <td>更受控且更显式</td>
    </tr>
    <tr>
        <td>对于小型目标 (例如，小型按钮或 Web 链接) </td>
        <td>可靠！ 出色的回退！</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

无论对凝视和提交输入模型使用头部凝视还是眼睛凝视，每个模型都附带不同的设计约束集。 这些分别在眼睛凝视、[提交、](gaze-and-commit-eyes.md)[头部凝视和提交文章中](gaze-and-commit-head.md)介绍。

<br>

---

### <a name="cursor"></a>游标

:::row:::
    :::column:::
        对于头部凝视，大多数应用都应使用[](cursors.md)光标或其他审核/视觉指示，让用户对要与之交互的方面具有置信度。 通常在此光标位于其头部凝视射线首先与对象相交（可能是全息影像或真实表面）的地方。<br>
        <br>
        对于眼睛凝视 *，我们通常* 建议不要显示光标，因为这可能会快速成为用户的干扰和麻烦。 而是以小方式突出显示视觉对象目标，或使用眼睛光标来表示用户要与之交互的置信度。 有关详细信息，请查看我们的设计指南 [，了解](eye-tracking.md) 基于眼睛的输入HoloLens 2。
    :::column-end:::
        :::column:::
       ![显示凝视的示例视觉光标](images/cursor.jpg)<br>
       *图像：用于显示凝视的示例视觉光标*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>提交
在讨论对目标 _进行_ 凝视的不同方法后，让我们再讨论一下凝 _视和提交_ 中的提交 _部分_。
以对象或 UI 元素为目标后，用户可以使用辅助输入与之交互或单击它。 这被称为输入模型的提交步骤。 

支持以下提交方法：
- 空中攻指的手势 (就是，在您自己的前方抬起，并将食指和拇指) 
- 说 _"选择"_ 或一个目标语音命令
- 在[HoloLens Clicker](/hololens/hololens1-clicker)上按单个按钮
- 按下 Xbox 游戏板上的 "A" 按钮
- 按 Xbox 自适应控制器上的 "A" 按钮

### <a name="gaze-and-air-tap-gesture"></a>注视和气攻敲击手势
隔空敲击是一种手部直立的点击手势。 若要使用空中点击，请将您的食指向准备就绪，然后将其放在拇指上，并将您的食指向上提升到释放。 在 HoloLens (第一代) 上，点击是最常见的辅助输入。


:::row:::
    :::column:::
       ![手指处于就绪位置](images/readyandpress-ready.jpg)<br>
       **手指处于就绪位置**<br>
    :::column-end:::
    :::column:::
       ![按下手指点击或单击](images/readyandpress-press.jpg)<br>
        **按下手指点击或单击**<br>
    :::column-end:::
:::row-end:::


HoloLens 2 上也提供了空中点击。 它已从原始版本中宽松。 几乎所有类型的 pinches 现在都受支持，只要手直立并且仍保持。 这样，用户就可以更轻松地学习和使用手势。 这种新的 "air&quot; 将通过相同的 API 替换旧的，因此，在重新编译 HoloLens 2 后，现有应用程序将自动具有新行为。

<br>

---

### <a name=&quot;gaze-and-select-voice-command&quot;></a>注视并单击 &quot;选择&quot; 语音命令
语音命令是混合现实中的主要交互方法之一。 它提供强大的免提机制来控制系统。 有不同类型的语音交互模型：

- 使用单击提示或提交作为辅助输入的通用&quot;Select&quot;命令。
- 对象命令 (例如，&quot;关闭&quot;或&quot;放大") 作为辅助输入执行并提交到某个操作。
- 全局 (，例如"转到开始") 不需要目标。
- 聊天用户界面或 Cortana 等实体具有 AI 自然语言功能。
- 自定义语音命令

若要详细了解详细信息和可用语音命令的综合列表及其使用方法，请查看语音 [命令指南](../out-of-scope/voice-design.md) 。

<br>

---


### <a name="gaze-and-hololens-clicker"></a>凝视和 HoloLens Clicker

:::row:::
    :::column:::
        HoloLens Clicker 是专为 HoloLens 构建的第一个外围设备。 它包含在 HoloLens (第一代) Development Edition 中。 HoloLens Clicker 允许用户以最少的手部运动进行单击，并提交作为辅助输入。 HoloLens Clicker 使用 (BTLE) 或 HoloLens 2 连接到 HoloLens 蓝牙低功耗 (第一代) 。<br>
        <br>
        [对设备进行配对的更多信息和说明](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *图像：HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens 遥控器](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>凝视和 Xbox 无线控制器

:::row:::
    :::column:::
        Xbox 无线控制器使用"A"按钮执行点击作为辅助输入。 设备映射到有助于导航和控制系统的默认操作集。 如果要自定义控制器，请使用 Xbox Accessories 应用程序配置 Xbox 无线控制器。<br>
        <br>
        [如何将 Xbox 控制器与电脑配对](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *图像：Xbox 无线控制器*
    :::column-end:::
        :::column:::
       ![Xbox 无线控制器](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>注视和 Xbox 自适应控制器
Xbox 自适应控制器主要用于满足移动性有限的游戏玩家的需求，是一种统一的设备，有助于使混合现实更易于访问。

Xbox 自适应控制器使用 "A" 按钮执行单击传动作为辅助输入。 设备映射到一组可帮助导航和控制系统的默认操作。 如果要自定义控制器，请使用 Xbox 附件应用程序来配置 Xbox 自适应控制器。

![Xbox 自适应控制器](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox 自适应控制器*

连接外部设备，如交换机、按钮、装入和操纵杆，以创建唯一的自定义控制器体验。 按钮、操纵杆和触发器输入由通过 3.5 mm 插座和 USB 端口连接的辅助设备控制。

![Xbox 自适应控制器端口](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox 自适应控制器端口*

[设备配对说明](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 网站上提供了更多信息</a>

<br>

---

## <a name="composite-gestures"></a>复合手势

### <a name="air-tap"></a>隔空敲击
"Air" 手势 (和下面的其他手势) 只会对特定点击做出反应。 若要检测其他点击，如菜单或抓住，你的应用程序必须直接使用上面两个关键组件手势部分中所述的低级交互。

### <a name="tap-and-hold"></a>点击并按住
按住是指保持隔空敲击手指向下的位置。 与 arm 移动（例如，选取对象，而不是激活对象）或 mousedown 辅助交互（如显示上下文菜单）结合使用时，点击和保持的组合允许使用各种更复杂的 "单击并拖动" 交互。
请注意，在为此手势设计时应谨慎，因为用户在任何扩展手势期间都容易使其 postures。

### <a name="manipulation"></a>操作
当您想让全息图对用户的手的变动做出回应1:1 时，可以使用操作手势移动、调整或旋转全息图。 此类 1:1 运动可让用户进行实际绘制或绘画。
操作手势的初始定位应通过凝视或指向来完成。 点击并保持开始后，任何对象操作都将由手动移动处理，从而使用户能够在操作时进行浏览。

### <a name="navigation"></a>导航
导航手势就像一个虚拟游戏杆，可用于导航 UI 小组件（如径向菜单）。 点击并按住以开始手势，然后在标准化 3D 立方体中以初始按压位置为中心移动手部。 您可以沿 X、Y 或 Z 轴将您的手移动到值1到1之间，0是起点。
导航可用于生成基于速度的连续滚动或缩放手势，类似于通过单击鼠标按钮然后上下移动鼠标来滚动 2D UI。

使用 rails 导航，是指在该轴上达到特定阈值之前识别特定轴中的运动的能力。 这仅在开发人员在应用程序中启用多个轴的移动时有用，例如，如果应用程序配置为识别跨 X、Y 轴的导航手势，但还指定了带导轨的 X 轴。 在这种情况下，系统将识别跨 X 轴的手动运动，只要它们保留在 X 轴上的虚导轨 () （如果手部运动也发生在 Y 轴上）。

在 2D 应用中，用户可以使用垂直导航手势在应用内进行滚动、缩放或拖动。 这会向应用注入虚拟手指触摸，以模拟相同类型的触摸手势。 用户可以通过在应用程序上方的栏上的工具之间切换来选择执行哪些操作，只需选择按钮或说"<滚动/拖动/缩放>工具"即可。

[有关复合手势的详细信息](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>手势识别器

使用手势识别的一个好处是，只能为当前目标全息影像可以接受的手势配置手势识别器。 平台仅在必要时进行区分，以区分这些特定的受支持手势。 这样一来，仅支持敲击的全息影像可以接受按下和松开之间的任意时长，而支持点击和按住的全息影像可以在保持时间阈值后将点击提升为保持。

## <a name="hand-recognition"></a>手部识别
HoloLens 通过跟踪设备可识别的一只手或双手的位置来识别手势。 当手处于就绪状态（手背朝向自己，食指向上）或按下状态（手背朝向自己，食指向下）时，HoloLens 可检测到手部。 当手部有其他姿势时，HoloLens 会忽略它们。
对于 HoloLens 检测到的每手，无需方向和按下状态即可访问其位置。 当手接近手势范围的边缘时，可看到一个方向向量，可向用户显示该方向向量，以便他们知道如何将手移回 HoloLens 可检测的范围。

## <a name="gesture-frame"></a>手势范围
对于 HoloLens 上的手势，手必须位于手势帧中，其范围是手势测量相机可以适当看到的范围，从手部到手部以及手部之间。 用户需要针对此识别领域进行训练，以便成功操作和获得自己的舒适感。 许多用户最初会假设手势框架必须通过 HoloLens 位于其视图中，并且要保持其手部以不解的方式进行交互。 使用 HoloLens Clicker 时，手不需要位于手势范围内。

具体而言，对于连续手势，用户在移动全息对象时，在手势中将手移动到手势框架之外存在一些风险，并丢失预期结果。

应考虑以下三个事项：

- 手势帧存在和大致边界的用户教育。 这会在安装 HoloLens 期间进行。

- 当用户的手势接近或中断应用程序内的手势帧边界时，通知用户，使丢失的手势导致意外的结果。 研究显示了此类通知系统的重要质量。 在中心游标上，HoloLens shell 提供此类通知的很好的示例，指示边界交叉的发生方向。

- 应尽可能避免穿过手势范围的边界。 通常，这意味着应在边界停止笔势的结果，而不是反转。 例如，如果用户在房间内移动某个全息对象，则在该笔势帧被破坏时，移动应停止，并且不会返回到开始点。 用户可能会遇到一些挫折，但可能会更快地了解边界，无需每次都重新启动其全部预期操作。



## <a name="see-also"></a>另请参阅
* [基于眼睛的交互](eye-gaze-interaction.md)
* [HoloLens 2 中的眼动跟踪](eye-tracking.md)
* [凝视和停留](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手势](gaze-and-commit.md#composite-gestures)
* [手 - 指向并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)