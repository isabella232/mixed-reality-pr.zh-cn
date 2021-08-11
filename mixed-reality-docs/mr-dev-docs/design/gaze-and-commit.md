---
title: 凝视并提交
description: 了解注视和提交输入模型，包括两种类型的眼睛 (眼睛和眼睛眼睛) ，以及各种类型的提交。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: mixed reality，注视，注视目标，交互，设计，眼睛跟踪，打印头跟踪，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实 Toolkit
ms.openlocfilehash: 98f2ac9d26fc02c969520fff9083152b77bf66a2f864d5fdb15b1ee781d5d7cb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201882"
---
# <a name="gaze-and-commit"></a>凝视并提交

"_注视" 和 "提交_" 是一种基本的输入模型，与使用鼠标的计算机进行交互的方式密切相关：_点 & 单击_。 在此页上，我们将介绍两种类型的目视输入 (打印头和眼睛眼睛) 以及不同类型的提交操作。 _注视和提交_ 被视为具有间接操作的最大输入模型。 它最适用于与不在世界各地的全息内容交互。

混合现实耳机可以使用用户头部的位置和方向来确定其头向量。 将看起来像是直接从用户的眼睛之间直接的一种激光。 这可粗略呈现出用户正查看的位置。 您的应用程序可以将此射线与虚拟或现实对象交叉，并在该位置绘制光标，以使用户了解其目标。

除了眼睛眼睛外，某些混合现实耳机（如 HoloLens 2）包含产生眼睛眼睛矢量的眼睛跟踪系统。 这可精细测量用户正在查看的位置。 在这两种情况下，注视都表示用户意向的重要信号。 系统更好地解释并预测用户的预期操作，提高了用户的满意度和性能。

下面是一些示例，说明混合现实开发人员如何从打印头或眼睛中获益：
* 您的应用程序可以在场景中与全息影像交叉，以确定用户的注意力 (更精确地利用眼睛) 。
* 您的应用程序可以基于用户的 "注视" 通道手势和控制器按下，这样用户就可以无缝选择、激活、抓取、滚动或以其他方式与全息影像交互。
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

## <a name="head-and-eye-tracking-design-concepts-demo"></a>头部和眼动跟踪设计概念演示

若要了解头部和眼动跟踪设计概念的运行情况，请查看下面的“设计全息影像 - 头部跟踪和眼动跟踪”视频演示。 完成后，请继续详细了解特定主题。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

此视频来自于“设计全息影像”HoloLens 2 应用。在[此处](https://aka.ms/dhapp)下载并享受完整体验。

## <a name="gaze"></a>凝视

### <a name="eye--or-head-gaze"></a>眼后看好了吗？
当面对问题时，有几个注意事项需要考虑是否应使用 "眼睛和提交" 或 "良好和提交" 输入模型。 如果要针对沉浸式耳机进行开发，或 (第一代) 的 HoloLens，则选择非常简单：机头和提交。 如果要为 HoloLens 2 进行开发，则选择会稍微难些。 务必要了解每种方法所附带的优点和挑战。
在下表中，我们编译了一些广泛的专业人员和职业，以对比眼睛和眼睛的目标。 这从很大程度上来看，我们建议在此处了解各种混合现实中的眼睛目标：
* [HoloLens 2 上的目视跟踪](eye-tracking.md)：在 HoloLens 2 包括某些开发人员指南的同时，提供新的眼睛跟踪功能。 
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
        <td>低工作量 (几乎不需要任何正文变动) </td>
        <td>可能是 fatiguing 的 discomfort (例如，颈部紧张) </td>
    </tr>
    <tr>
        <td>不需要游标，但建议使用微妙的反馈</td>
        <td>需要显示游标</td>
    </tr>
    <tr>
        <td>无平滑的眼睛运动-例如，不适合绘图</td>
        <td>更多受控和显式</td>
    </tr>
    <tr>
        <td>对于小型目标 (很难，如小按钮或 weblinks) </td>
        <td>非常! 好的回退！</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

无论您使用的是眼睛还是目视，都可以使用看起来和提交输入模型，每个都有不同的设计约束集。 它们分别介绍了 [眼睛和提交](gaze-and-commit-eyes.md) 和 [提交](gaze-and-commit-head.md) 文章。

<br>

---

### <a name="cursor"></a>游标

:::row:::
    :::column:::
        对于 "注视"，大多数应用程序都应该使用 [游标](cursors.md) 或其他听觉/视觉指示来让用户信任他们要与之交互的内容。 通常将此光标置于世界上，其中其打印头看起来先与一个对象（可能是全息图或真实表面）相交。<br>
        <br>
        对于眼睛，我们通常建议 *不要* 显示游标，因为这可能会使用户迅速变得杂乱。 相反，突出强调视觉对象目标，或使用模糊的光标来自信用户要与之交互的对象。 有关详细信息，请查看 HoloLens 2 上[基于目视的输入的设计指南](eye-tracking.md)。
    :::column-end:::
        :::column:::
       ![用于显示注视的视觉对象示例](images/cursor.jpg)<br>
       *图像：显示注视的视觉对象光标示例*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>提交
_在谈论看一看目标_ 的不同方法之后，让我们更深入地谈谈 "注视" 和 "_提交_" 中的 _提交_ 部分。
以对象或 UI 元素为目标后，用户可以使用辅助输入交互或单击此元素。 这被称为输入模型的提交步骤。 

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


HoloLens 2 上也提供了空中点击。 它已从原始版本中宽松。 几乎所有类型的 pinches 现在都受支持，只要手直立并且仍保持。 这样，用户就可以更轻松地学习和使用手势。 这一新的 "air&quot; 将通过相同的 API 替换旧的，因此，在为 HoloLens 2 重新编译后，现有应用程序将自动具有新行为。

<br>

---

### <a name=&quot;gaze-and-select-voice-command&quot;></a>注视并单击 &quot;选择&quot; 语音命令
语音命令是混合现实中的主要交互方法之一。 它提供强大的免提机制来控制系统。 有不同类型的语音交互模型：

- 使用单击传动或提交作为辅助输入的泛型 &quot;Select&quot; 命令。
- 对象命令 (例如，&quot;关闭&quot; 或 &quot;使其变大" ) 将操作作为辅助输入执行并提交到操作。
- 全局 (，例如"转到开始") 不需要目标。
- 聊天用户界面或实体（如 Cortana具有 AI 自然语言功能。
- 自定义语音命令

若要详细了解详细信息和可用语音命令的综合列表及其使用方法，请查看语音 [命令指南](../out-of-scope/voice-design.md) 。

<br>

---


### <a name="gaze-and-hololens-clicker"></a>凝视HoloLens单击器

:::row:::
    :::column:::
        HoloLens Clicker 是专为 HoloLens 而构建的第一个外围设备。 它包含在第一代 HoloLens (Development Edition) 中。 单击HoloLens用户只需最小手部运动即可单击，并提交为辅助输入。 HoloLens Clicker 使用 HoloLens (HOLOLENS (BTLE) 或 HoloLens 2 蓝牙连接到第一代 () 。<br>
        <br>
        [对设备进行配对的更多信息和说明](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *图像：HoloLens单击器*
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


### <a name="gaze-and-xbox-adaptive-controller"></a>凝视和 Xbox 自适应控制器
Xbox 自适应控制器主要用于满足具有有限移动性的游戏者的需求，是一个统一的设备中心，可帮助使混合现实更易于访问。

Xbox 自适应控制器使用"A"按钮执行点击作为辅助输入。 设备映射到有助于导航和控制系统的默认操作集。 如果要自定义控制器，请使用 Xbox Accessories 应用程序来配置 Xbox 自适应控制器。

![Xbox 自适应控制器](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox 自适应控制器*

连接交换机、按钮、装载和手柄等外部设备，以创建唯一的自定义控制器体验。 按钮、指纹和触发器输入由通过 3.5 mm 千头和 USB 端口连接的辅助设备控制。

![Xbox 自适应控制器端口](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox 自适应控制器端口*

[设备配对说明](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 网站上提供了更多信息</a>

<br>

---

## <a name="composite-gestures"></a>复合手势

### <a name="air-tap"></a>隔空敲击
空敲击 (和下面的其他手势) 只对特定点击做出反应。 若要检测其他点击（如菜单或抓取功能），应用程序必须直接使用上述两个关键组件手势部分中描述的较低级别的交互。

### <a name="tap-and-hold"></a>点击并按住
按住是指保持隔空敲击手指向下的位置。 组合使用敲击和按住，可以在与手部移动结合使用时进行各种更复杂的"点击和拖动"交互，例如选取对象，而不是激活该对象或鼠标下移辅助交互，如显示上下文菜单。
但是，在设计此手势时，应小心，因为在任何扩展手势期间，用户都容易放宽其手势。

### <a name="manipulation"></a>操作
当希望全息影像对用户手部运动做出 1：1 响应时，可以使用操作手势移动、调整全息影像大小或旋转全息影像。 此类 1:1 运动可让用户进行实际绘制或绘画。
操作手势的初始定位应通过凝视或指向来完成。 点击和按住开始后，任何对象操作都由手部移动处理，这可让用户在操作时四处查看。

### <a name="navigation"></a>导航
导航手势就像一个虚拟游戏杆，可用于导航 UI 小组件（如径向菜单）。 点击并按住以开始手势，然后在标准化 3D 立方体中以初始按压位置为中心移动手部。 可以将手沿 X、Y 或 Z 轴从值 -1 移动到 1，以 0 作为起点。
导航可用于生成基于速度的连续滚动或缩放手势，类似于通过单击鼠标按钮然后上下移动鼠标来滚动 2D UI。

使用导轨导航是指识别特定轴中的移动，直到达到该轴上的特定阈值。 这仅在开发人员在应用程序中启用多个轴的移动时有用，例如，如果应用程序配置为识别跨 X、Y 轴的导航手势，但还指定了带导轨的 X 轴。 在这种情况下，系统将识别跨 X 轴的手动运动，只要它们保留在 X 轴上的虚导轨 () （如果手部运动也发生在 Y 轴上）。

在 2D 应用中，用户可以使用垂直导航手势在应用内进行滚动、缩放或拖动。 这会向应用注入虚拟手指触摸，以模拟相同类型的触摸手势。 用户可以通过在应用程序上方的栏上的工具之间切换来选择执行哪些操作，只需选择按钮或说"<滚动/拖动/缩放>工具"即可。

[有关复合手势的详细信息](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>手势识别器

使用手势识别的一个好处是，只能为当前目标全息影像可以接受的手势配置手势识别器。 平台仅在必要时进行区分，以区分这些特定的受支持手势。 这样一来，仅支持敲击的全息影像可以接受按下和松开之间的任意时长，而支持点击和按住的全息影像可以在保持时间阈值后将点击提升为保持。

## <a name="hand-recognition"></a>手部识别
HoloLens 通过跟踪设备可识别的一只手或双手的位置来识别手势。 当手处于就绪状态（手背朝向自己，食指向上）或按下状态（手背朝向自己，食指向下）时，HoloLens 可检测到手部。 当手在其他姿势中时，HoloLens忽略它们。
对于检测到HoloLens手，无需方向和按下状态即可访问其位置。 当手接近手势范围的边缘时，可看到一个方向向量，可向用户显示该方向向量，以便他们知道如何将手移回 HoloLens 可检测的范围。

## <a name="gesture-frame"></a>手势范围
对于HoloLens手势，手必须位于手势框架内，其范围是手势测量相机可以适当看到的范围，从眼睛到眼睛，以及手部之间。 用户需要针对此识别领域进行训练，以便成功操作和获得自己的舒适感。 许多用户最初会假设手势框架必须在其视图中通过HoloLens，并令人不解地保持其手部以进行交互。 使用HoloLens单击器时，手不需要位于手势范围内。

具体而言，对于连续手势，用户在移动全息对象时，在手势中将手移动到手势框架之外存在一些风险，并丢失预期结果。

应考虑以下三个事项：

- 用户对手势框架的存在和近似边界进行教育。 这是在安装过程中HoloLens的。

- 当用户的手势接近或中断应用程序中的手势帧边界时，通知用户丢失手势会导致不预期的结果。 研究表明此类通知系统的关键质量。 命令行HoloLens在中心光标处提供了此类通知的一个很好的示例，指示边界跨越发生的方向。

- 应尽可能避免穿过手势范围的边界。 一般情况下，这意味着手势的结果应在边界停止，而不是反转。 例如，如果用户在房间中移动某个全息对象，则移动应在手势框架被破坏时停止，并且不会返回到起点。 用户可能会遇到一些沮丧，但可能会更快了解边界，并且无需每次重启其全部预期操作。



## <a name="see-also"></a>另请参阅
* [基于眼睛的交互](eye-gaze-interaction.md)
* [HoloLens 2 中的眼动跟踪](eye-tracking.md)
* [凝视和停留](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手势](gaze-and-commit.md#composite-gestures)
* [手 - 指向并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)