---
title: 运动控制器
description: 了解如何在应用程序中使用混合现实运动控制器设置、配对和管理器输入交互。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 控制器、运动控制器、配对、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、滚动、手柄、状态
ms.openlocfilehash: bced0115eee5e753ef01d129ae10910acdca2b7b91020117f53b2ebf8833a130
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224870"
---
# <a name="motion-controllers"></a>运动控制器

:::row:::
    :::column:::
        运动控制器 [是允许用户](../discover/hardware-accessories.md) 在混合现实中采取措施的硬件附件。 运动 [控制器比手势](gaze-and-commit.md#composite-gestures) 的优点是控制器在空间中具有精确的位置，允许与数字对象进行精细交互。 对于Windows Mixed Reality沉浸式头戴显示设备，运动控制器是用户在自己世界内采取操作的主要方式。<br>
        <br>
        *图像：Windows Mixed Reality运动控制器*
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality运动控制器](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

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
     <td>运动控制器</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>硬件详细信息

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Windows Mixed Reality运动控制器使用沉浸式头戴显示设备中的传感器在视场中提供精确的响应式移动跟踪。 无需在空间的墙上安装硬件。 这些运动控制器提供与沉浸式头戴显示设备相同的易于设置Windows Mixed Reality可移植性。 我们的设备合作伙伴计划在此假日在零售架上销售这些控制器。

![了解控制器](images/controllerimage-750px.png)<br>
*了解控制器*

**功能：**
* 光学跟踪
* 触发器
* "抓取"按钮
* Thumbstick
* 触摸板

## <a name="setup"></a>设置

### <a name="before-you-begin"></a>在开始之前

需要的软件：
* 一组两个运动控制器。
* 四个 AA 电池。
* 支持 4.0 蓝牙电脑。

**检查Windows、Unity 和驱动程序更新**
* 若要[进行混合现实](../develop/install-the-tools.md)开发，请访问安装适用于 Windows Unity 等的首选版本的工具。
* 确保拥有最新的头戴显示设备 [驱动程序和运动控制器驱动程序](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)。

### <a name="pairing-controllers"></a>配对控制器

运动控制器可以使用与任何其他设备一样Windows设置与主机电脑蓝牙连接。

1. 将两个 AA 电池插入控制器的背面。 将电池盖保持关闭状态。
2. 如果使用的是外部 USB 蓝牙 适配器，而不是内置 蓝牙，请查看蓝牙[最佳做法](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)，然后再继续。 对于具有内置无线电的桌面配置，请确保天线已连接。
3. 打开 **Windows 设置"** 添加蓝牙或其他设备蓝牙并删除"运动控制器 – 右侧"和"运动控制器  ->    ->    ->  – 左"的任何早期版本实例。 另请查看列表底部的"其他设备"类别。
4. 选择 **"蓝牙或其他设备"，** 并看到它开始发现蓝牙设备。
5. 按住控制器的按钮Windows打开控制器，一旦它发出声，松开它。
6. 按住电池隔离舱 (选项卡上的配对按钮) LED 开始脉冲。

:::row:::
    :::column:::
7. 等待"运动控制器 - 左"或"运动控制器 - 右侧"显示在列表底部。 选择以配对。 控制器在连接时将振动一次。<br>
        <br>
        *图像：选择要配对的"运动控制器";如果有多个实例，请从列表底部选择一个实例*
    :::column-end:::
        :::column:::
       ![选择"运动控制器"进行配对，如果多个实例从列表底部选择一个实例](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. 你将看到控制器显示在"鼠标、键盘蓝牙笔"类别下的"已连接&**设置****中**。 此时，可能会获得固件更新 – 请参阅下 [一部分](motion-controllers.md#updating-controller-firmware)。
9. 重新附加电池盖。
10. 为第二个控制器重复步骤 1-9。

<br>

:::row:::
    :::column:::
        成功配对两个控制器后，设置应如下所示，在"鼠标、键盘 **&笔"类别下** <br>
        <br>
        *图像：已连接运动控制器*
    :::column-end:::
        :::column:::
       ![已连接运动控制器](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

如果控制器在配对后关闭，则其状态将显示为"配对"。 对于永久位于"其他设备"类别的控制器，配对可能只部分完成。 在这种情况下，请再次运行配对步骤，使控制器正常运行。

### <a name="updating-controller-firmware"></a>更新控制器固件

* 如果使用新的控制器固件将沉浸式头戴显示设备连接到电脑，则固件将在下次打开时自动推送到运动控制器。 控制器固件更新由循环运动中亮起 LED 象限的模式指示，需要 1-2 分钟。


:::row:::
    :::column:::
* 固件更新完成后，控制器将重新启动并重新连接。 现在应连接两个控制器。 <br>
        <br>
        *图像：在设置中蓝牙控制器*
    :::column-end:::
        :::column:::
       ![已连接的控制器](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* 验证控制器是否正常工作：
    1. 启动 **混合现实门户** 并输入混合现实主页。
    2. 移动控制器并验证跟踪、测试按钮，并验证 [远程传送是否](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 正常工作。 如果没有，请查看运动 [控制器故障排除](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)。

## <a name="gazing-and-pointing"></a>凝视和指向

Windows Mixed Reality两个关键模型进行交互;**凝视和提交** 以及 **指向和提交**：
* 通过 **凝视和** 提交，用户通过凝视将对象作为 [目标，然后](gaze-and-commit.md)使用手势敲击、游戏板、点击器或语音选择对象。
* 借助 **点和** 提交，用户可以将支持指向的动作控制器指向目标对象，然后使用控制器的触发器选择对象。

支持使用运动控制器指向的应用还应在可能的情况下启用凝视驱动交互，为用户提供使用哪些输入设备的选择。

### <a name="managing-recoil-when-pointing"></a>在指向时管理重新处理

使用运动控制器进行指向和提交时，用户将使用该控制器通过拉取其触发器来定向和交互。 意外拉取触发器的用户最终可能在触发器拉取结束时将控制器定目标到比预期更高的目标。

若要管理用户拉取触发器时可能会发生的任何此类重新扫描，应用可以在触发器的模拟轴值高于 0.0 时对齐其目标射线。 然后，可以在触发器值达到 1.0 后，使用该目标射线操作几帧，只要在短时间范围内发生最终按下。 使用更高级别的复合点击[手势](gaze-and-commit.md#composite-gestures)时，Windows将管理此目标射线捕获和超时。

## <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指向姿势

Windows Mixed Reality支持不同外形因素的动作控制器，每个控制器的设计在用户手部位置与应用在呈现控制器时应该用于指向的自然"向前"方向之间的关系有所不同。

为了更好地表示这些控制器，可以针对每个交互源调查两种类型的姿势：手柄 **姿势和****指针姿势**。

### <a name="grip-pose"></a>手柄姿势

手柄 **姿势** 表示手部由手部检测到的HoloLens或持有运动控制器的手部的位置。

在沉浸式头戴显示设备中，手柄姿势最适合用于呈现用户手部或用户手部中持有的对象，例如手部或手部。 在可视化运动控制器时，也使用手柄姿势，因为运动控制器的Windows 提供的可呈现模型使用手柄姿势作为旋转的原点和中心。

手柄姿势的定义具体如下：
* 手柄 **位置**：自然按住控制器时，通过向左或向右调整以将手柄中的位置居中时，手心中心。 在Windows Mixed Reality控制器上，此位置通常与"抓取"按钮对齐。
* 手柄 **方向的** 右轴：完全打开手形成平面五指姿势时，与手部正常的射线从左 (向前，从右手心向后) 
* 手柄方向 **的** 向前轴：当你部分关闭手部 (就像按住控制器) 一样，指向"向前"的射线通过由非滚动手指组成的管道。
* 手柄 **方向的上轴**：右侧和向前定义隐含的向上轴。

### <a name="pointer-pose"></a>指针姿势

指针 **姿势** 表示指向向前的控制器的提示。

在呈现控制器模型本身时，系统提供的指针姿势最适合用于 **光线广播**。 如果要呈现一些其他虚拟对象（例如虚拟照片）来更换控制器，则应该指向该虚拟对象最自然的射线，例如沿应用定义的"手形"模型群移动的射线。 由于用户可以看到虚拟对象，而不是物理控制器，因此使用应用的用户可能更自然地指向虚拟对象。

## <a name="controller-tracking-state"></a>控制器跟踪状态

与头戴显示设备Windows Mixed Reality，运动控制器不需要设置外部跟踪传感器。 相反，控制器由头戴显示设备本身的传感器进行跟踪。

如果用户将控制器移到头戴显示设备视场外，在大多数情况下，Windows继续推断控制器位置，并将它们提供给应用。 当控制器丢失视觉跟踪的时间足够长时，控制器的位置将下降至近似准确性位置。

此时，系统会将控制器进行正文锁定，跟踪用户移动时的位置，同时仍使用其内部方向传感器公开控制器的真实方向。 许多使用控制器指向和激活 UI 元素的应用都可以正常运行，同时大致准确无误，而无需用户通知。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>有关显式跟踪状态的原因

希望根据跟踪状态以不同方式处理位置的应用可能会进一步检查控制器状态的属性，例如 SourceLossRisk 和 PositionAccuracy：

<table>
<tr>
<th> 跟踪状态 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>准确度高</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> 是</td>
</tr><tr>
<td> <b>高准确度 (有丢失数据) </b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> 是</td>
</tr><tr>
<td> <b>近似准确度</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: green; color: white"> 是</td>
</tr><tr>
<td> <b>无位置</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 近似 </td><td style="background-color: orange"> false</td>
</tr>
</table>

这些运动控制器跟踪状态的定义如下：
* **高精度：** 虽然运动控制器位于头戴显示设备视场内，但它通常基于视觉跟踪提供高精度位置。 暂时离开视场或被头戴显示设备传感器短暂遮盖（例如 (由用户另一手遮挡）的移动控制器) 将基于控制器本身的惯性跟踪，在短时间内继续返回高精度姿势。
* **高准确度 (有丢失数据) ：** 当用户将运动控制器移到头戴显示设备视场的边缘之后，头戴显示设备很快就会无法直观地跟踪控制器的位置。 应用通过看到 **SourceLossRisk** 达到 1.0，知道控制器何时到达此 FOV 边界。 此时，应用可以选择暂停需要稳定高质量手势流的控制器手势。
* **近似准确度：** 当控制器丢失视觉跟踪的时间足够长时，控制器的位置将下降至近似准确性位置。 此时，系统会将控制器进行正文锁定，跟踪用户移动时的位置，同时仍使用其内部方向传感器公开控制器的真实方向。 许多使用控制器指向和激活 UI 元素的应用可以正常运行，同时大致准确，无需用户通知。 具有较重输入要求的应用可以选择通过检查 **PositionAccuracy** 属性来检测从"高准确度"到"近似准确度"的下降，例如，在此期间，在屏幕外目标上为用户提供更丰富的命中框。  
* **无位置：** 虽然控制器可以长时间以近似精度运行，但有时系统知道，即使是人体锁定的位置目前也无意义。 例如，打开的控制器可能从未在视觉上观察到，或者用户可能会关闭随后由其他人选取的控制器。 此时，系统不会向应用提供任何位置 **，TryGetPosition** 将返回 false。

## <a name="interactions-low-level-spatial-input"></a>交互：低级别空间输入

手部和运动控制器之间的核心交互包括 **选择**、菜单、**抓取**、**触摸板****、Thumbstick** 和 **Home。**
* **选择** 是激活全息影像的主要交互，包括按后发布。 对于运动控制器，使用控制器的触发器执行"按 Select"。 执行"选择"的其他方法有：说 [语音命令"选择](voice-input.md) "。 可以在任何应用中使用相同的选择交互。 将"选择"视为鼠标单击的等效项;一个通用操作，可学习一次，然后应用于所有应用。
* **菜单** 是作用于 对象的辅助交互，用于拉取上下文菜单或执行其他一些辅助操作。 使用运动控制器，可以使用控制器的菜单按钮执行 *菜单* 操作。  (，即包含汉堡"菜单"图标的按钮) 
* **掌握** 是用户直接对手下的对象采取措施来操作它们的方法。 使用运动控制器，可以通过紧密地抓取手部执行抓取操作。 运动控制器可能会检测到抓取按钮、手部触发器或其他传感器的抓取。
* **触摸板** 允许用户沿运动控制器触摸板的图面调整两个维度的操作，通过单击触摸板向下提交操作。 触摸板提供按下状态、触摸状态和规范化 XY 坐标。 X 和 Y 在圆形触摸板范围内的范围为 -1 到 1，中心 (0，0) 。 对于 X，-1 在左侧，1 在右侧。 对于 Y，-1 位于底部，1 位于顶部。
* **Thumbstick** 允许用户通过移动运动控制器的滚动块在其循环范围内来调整两个维度中的操作，通过单击滚动块来提交操作。 指纹还提供按下状态和规范化 XY 坐标。 X 和 Y 在圆形触摸板范围内的范围为 -1 到 1，中心 (0，0) 。 对于 X，-1 在左侧，1 在右侧。 对于 Y，-1 位于底部，1 位于顶部。
* **"** 主页"是一个特殊的系统操作，用于返回到"开始"菜单。 这类似于按键盘上的Windows或 Xbox 控制器上的 Xbox 按钮。 可以通过按运动控制器上的Windows按钮转到"主页"。 请注意，始终可以返回"你好，Cortana，开始"。 应用无法专门对"主页"操作做出反应，因为操作由系统处理。

## <a name="composite-gestures-high-level-spatial-input"></a>复合手势：高级空间输入

[可以随着时间的推移跟踪](gaze-and-commit.md#composite-gestures)手势和运动控制器，以检测一组常见的高级 **[复合手势](gaze-and-commit.md#composite-gestures)**。 这使应用能够检测高级别 **点击、按住**、操作和 **导航** 手势，无论用户最终是使用手还是控制器。

## <a name="rendering-the-motion-controller-model"></a>呈现运动控制器模型

**3D 控制器Windows** 为应用提供系统中当前处于活动状态的每个运动控制器的可呈现模型。 通过在运行时让应用动态加载并阐明这些系统提供的控制器模型，可以确保应用向前兼容任何将来的控制器设计。

我们建议在控制器手柄姿势处呈现所有可呈现模型，因为模型的来源与物理世界中的此点对齐。 如果要渲染控制器模型，则你可能希望从指针姿势 **（表示** 用户自然希望沿其指向的射线，给定该控制器的物理设计）将光线广播到场景中。

若要详细了解如何在 Unity 中动态加载控制器模型，请参阅在 Unity 中呈现 [运动控制器](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity) 模型部分。

**2D 控制器线条图** 虽然我们建议将应用内控制器提示和命令附加到应用内控制器模型本身，但某些开发人员可能想要在平面"教程"或"操作说明"UI 中使用运动控制器的 2D 线条艺术表示形式。 对于这些开发人员，我们.png右键单击鼠标右键以保存运动控制器线条图 (，以保存) 。

![运动控制器线条图条预览](images/motioncontrollers-black-preview-300px.png)

["'white'"中的全分辨率运动控制器线条图](images/motioncontrollers-white.png)
 
["'black'"中的全分辨率运动控制器线条图](images/motioncontrollers-black.png)

## <a name="faq"></a>常见问题解答

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>能否将运动控制器与多个电脑配对？

运动控制器支持与单个电脑配对。 按照运动控制器 [设置的说明对](motion-controllers.md#setup) 控制器进行配对。

### <a name="how-do-i-update-motion-controller-firmware"></a>如何实现更新运动控制器固件？

运动控制器固件是头戴显示设备驱动程序的一部分，必要时会在连接时自动更新。 固件更新通常需要 1-2 分钟，具体取决于蓝牙和链接质量。 在极少数情况下，控制器固件更新最多可能需要 10 分钟，这可能表示连接蓝牙或无线电干扰。 请参阅[蓝牙指南中的最佳实践来](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)排查连接问题。 固件更新后，控制器将重新启动并重新连接到主机电脑 (你可能会注意到 LED 亮，用于跟踪) 。 如果固件更新因 (例如控制器断电而中断) ，则下次打开控制器时将再次尝试更新。

### <a name="how-i-can-check-battery-level"></a>如何检查电池电量？

在[Windows Mixed Reality中](../discover/navigating-the-windows-mixed-reality-home.md)，可以打开控制器，在虚拟模型的另一侧查看其电池电量。 没有物理电池电量指示器。

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>能否在没有头戴显示设备的情况下使用这些控制器？ 只是为了进行游戏/触发器/等输入？

不用于通用Windows应用程序。

## <a name="troubleshooting"></a>疑难解答

请参阅 [《友元指南》](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) 中的运动控制器故障排除。

## <a name="filing-motion-controller-feedbackbugs"></a>提交运动控制器反馈/bug

[使用"混合](/hololens/hololens-feedback) 现实 ->输入"类别，在 反馈中心 中提供反馈。

## <a name="see-also"></a>另请参阅

* [Unity 中的运动控制器](../develop/unity/motion-controllers-in-unity.md)
* [DirectX 中的手和运动控制器](../develop/native/hands-and-motion-controllers-in-directx.md)
* [笔势](gaze-and-commit.md#composite-gestures)
* [友元指南：Windows Mixed Reality主页](/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [友元指南：在&应用中使用Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [由内而外跟踪的工作原理](/windows/mixed-reality/enthusiast-guide/tracking-system)