---
title: 输入模拟服务
description: 有关 MRTK 中的输入模拟服务的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f329cceded5e510d3d4fc1a1c13b5a504f1f3669ad408b733267595e77dd15a6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227571"
---
# <a name="input-simulation-service"></a>输入模拟服务

![MRTK 输入模拟](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

借助 MRTK 的输入模拟，你可以在 Unity 编辑器中测试各种类型的交互，而无需生成并部署到设备。 这使你可以在设计和开发过程中快速迭代你的想法。 使用键盘和鼠标组合来控制模拟输入。

输入模拟服务模拟 Unity 编辑器中可能不可用的设备和平台的行为。 示例包括：

* HoloLens或 VR 设备头跟踪
* HoloLens手势
* HoloLens 2手部跟踪
* HoloLens 2眼动跟踪
* VR 设备控制器

> [!WARNING]
> 在仿真模式下使用 Unity 的 XR 全息仿真 = "在编辑器中>模拟时，这不起作用。 Unity 的编辑器内模拟将控制 MRTK 的输入模拟。 若要使用 MRTK 输入模拟服务，需要将 XR 全息仿真设置为仿真模式 = *"None"*

## <a name="how-to-use-mrtk-input-simulation"></a>如何使用 MRTK 输入模拟 

在 MRTK 的配置文件中，默认启用输入模拟。 只需单击"播放 **"** 按钮即可运行支持输入模拟的场景。

* 按 W、A、S、D、Q、E 键可移动摄像头。
* 在按住鼠标右键的同时移动鼠标可以四处浏览。
* 按空格键（右手）或左 Shift 键（左手）以显示模拟的双手 
* 按 T 或 Y 键以将模拟的双手保持在视野中 
* 若要旋转模拟手部，请按住 **Ctrl 键** 并移动鼠标

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a>在编辑器输入模拟备忘单中

在 HandInteractionExamples 场景中按 **左 Ctrl + H，** 显示具有输入模拟控件的备忘单。

> ![MRTK 输入模拟备忘单](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a>启用输入模拟服务

在"输入系统数据提供程序"配置下，可以使用以下内容配置输入模拟服务。

* **类型** 必须为 *Microsoft.MixedReality.Toolkit。Input > SimulationService*。
* **受支持的平台 (默认)** 包括所有 *编辑器* 平台，因为服务使用键盘和鼠标输入。

> [!NOTE]
> 输入模拟服务可以在其他平台终结点（例如独立）上使用， (支持的平台) **属性以** 包含所需的目标。
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a>相机控件

输入模拟服务可以模拟头部运动。

### <a name="rotating-the-camera"></a>旋转相机

1. 将鼠标悬停在视区编辑器窗口上。
    *如果按钮按下不起作用，可能需要单击窗口以赋予其输入焦点。*
1. 按并按住鼠标 **"查找 (** 按钮"默认按钮：右键) 。
1. 在视区窗口中移动鼠标以旋转照相机。
1. 使用滚轮在视图方向周围滚动照相机。

可以通过更改输入模拟配置文件中的鼠标查找 **速度** 设置来配置相机旋转速度。

或者，使用"水平查找垂直"轴将相机旋转为默认 /  (：游戏控制器右滚动) 。

### <a name="moving-the-camera"></a>移动摄像头

使用"**移动水平** / **移动垂直** 轴"将相机 (默认值：WASD 键或游戏控制器左滚动) 。

还可以在工具窗口中显式设置相机位置和旋转角度。 可以使用"重置"按钮将相机重置为 **默认值** 。

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>控制器模拟

输入模拟支持模拟控制器设备 (即运动控制器和手部) 。 这些虚拟控制器可以与支持常规控制器的任何对象（如按钮或可抓取对象）交互。

### <a name="controller-simulation-mode"></a>控制器模拟模式

在输入 [模拟工具窗口中，](#input-simulation-tools-window)**默认控制器模拟模式** 设置在三个不同的输入模型之间切换。 还可以在输入模拟配置文件中设置此默认模式。

* *手部*：模拟具有联合位置数据的完全铰接式手部设备。

   模拟HoloLens 2模型。

   可以在此模式下模拟基于手部精确定位或使用触摸的交互。

* *手势：* 使用敲击和基本手势模拟简化的手势模型。

   模拟[HoloLens模型](/windows/mixed-reality/gestures)。

   焦点使用凝视指针进行控制。 Air *Tap* 手势用于与按钮交互。

* *运动控制器*：模拟与 VR 头戴显示设备一同使用的动作控制器，其工作方式类似于与手部远部交互。

   使用控制器交互模型模拟 VR 头戴显示设备。

   触发器、抓取键和菜单键通过键盘和鼠标输入进行模拟。

### <a name="simulating-controller-movement"></a>模拟控制器移动

按并按住"**左/** 右控制器操作 (键"：左控制器的左移和右控制器) 空格键以获得对任一控制器的控制。 按下操作键时，控制器将显示在视区中。 释放操作密钥后，控制器会在控制器隐藏超时 **短后消失**。

控制器可以相对于输入模拟工具窗口中的相机进行切换和冻结，[](#input-simulation-tools-window)或者按"左/右切换控制器 **键" (** 默认值 *：T* 表示左侧 *，Y* 表示右键) 。 再次按切换键以再次隐藏控制器。 若要操作控制器，需要保留 **左/** 右控制器操作键。 双击" **左/右控制器操作键"** 还可以打开/关闭控制器。

鼠标移动将在视图平面中移动控制器。 控制器可以使用鼠标滚轮 进一步或更靠近 **相机**。

若要使用鼠标旋转控制器，请按住左 **/** 右控制器操作键 (*左* 移或空格键) 和控制器旋转按钮 **(** 默认值：*左 Ctrl* 按钮) ，然后移动鼠标以旋转控制器。 可以通过更改输入模拟配置文件中的"鼠标控制器旋转 **速度** "设置来配置控制器旋转速度。

还可以在输入模拟工具窗口中更改所有[](#input-simulation-tools-window)手部放置，包括将手重置为默认值。

### <a name="additional-profile-settings"></a>其他配置文件设置

* **控制器深度乘数** 控制鼠标滚轮深度移动的敏感度。 较大的数字将加快控制器缩放。
* **默认控制器距离** 是控制器与相机的初始距离。 单击" **重置** "按钮控制器也会在此距离放置控制器。
* **控制器抖动量** 向控制器添加随机运动。 此功能可用于模拟设备上不准确的控制器跟踪，并确保交互能够很好地处理干扰输入。

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>手势

还可以模拟手势，例如收缩、抓取、抓取等。

1. 使用左移/右控制器 **操作** 键或左移 (*空格**键启用手动*) 

2. 操作时，按住鼠标按钮以执行手势。

每个鼠标按钮都可以进行映射，以使用鼠标手势的左 */中/右* 手势设置将手部形状转换为不同的手势。 " *默认手势"* 是在未按下任何按钮时手的形状。

> [!NOTE]
> 收缩 *手势* 是此时执行"选择"操作的唯一手势。

### <a name="one-hand-manipulation"></a>单手操作

1. 按住左 **移/右控制器操作** 键 (*左移**或空格键)*
2. 指向对象
3. 按住鼠标按钮进行收缩
4. 使用鼠标移动对象
5. 释放鼠标按钮以停止交互

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>双手操作

对于同时使用两只手操作对象，建议使用持久性手模式。

1. 按切换键按 *"T/Y"* 按钮 (两手) 。
1. 一次操作一次：
    1. 按住 **空间** 以控制右手
    1. 将指针移到要抓取对象的位置
    1. 按 **鼠标左键** 以激活 *挤压* 手势。
    1. 释放 **空间** 以停止控制右手。 手型会被冻结并锁定到 *挤压* 手势，因为它不再被操作。
1. 用另一种方式重复此过程，在第二个位置抓取相同的对象。
1. 由于这两个指针都抓取了同一个对象，因此可以移动其中的任何一个对象来执行双向操作。

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>GGV (注视、手势和语音) 交互

默认情况下，当场景中不存在任何已表述的手时，将在编辑器中启用 GGV 交互。

1. 旋转相机，将注视光标指向种不可交互对象 (鼠标右键) 
1. 单击并按住 **鼠标左键** 以进行交互
1. 再次旋转相机以操纵对象

你可以关闭此功能，方法是在输入模拟配置文件中切换 " *启用手动免费输入* " 选项。

此外，还可以使用模拟指针进行 GGV 交互

1. 通过将 **手形模拟模式** 切换到 [输入模拟配置文件](#enabling-the-input-simulation-service)中的 *手势* 来启用 GGV 模拟
1. 旋转相机，将注视光标指向种不可交互对象 (鼠标右键) 
1. 按住 **空间** 以控制右手
1. 单击并按住 **鼠标左键** 以进行交互
1. 使用鼠标移动对象
1. 释放鼠标按钮以停止交互

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a>引发传送事件

若要在输入模拟中引发传送事件，请在输入模拟配置文件中配置手手势设置，使其中一个执行 **传送开始** 手势，而另一个执行 **传送结束** 手势。 传送 **开始** 手势将显示传送指针，而 **传送结束** gesure 将完成传送操作并移动用户。

生成的传送的 y 位置取决于沿 y 轴的摄像机置换。 在编辑器中，默认情况下此值为0，因此使用 **Q** 和 **E** 键将其调整为适当的高度。

![输入模拟传送设置](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>运动控制器交互

模拟的运动控制器的操作方式与所表述的操作方式相同。 当触发器、抓取和菜单键分别映射到 *鼠标左键*、 *G* 和 *M* 键时，交互模型类似于清晰的手写内容交互。

### <a name="eye-tracking"></a>眼动跟踪

可以通过检查 [输入模拟配置文件](#enabling-the-input-simulation-service)中的 "**模拟眼睛位置**" 选项来启用 [目视跟踪模拟](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor)。 这不应与 GGV 或运动控制器样式交互一起使用 (因此请确保将 **默认控制器模拟模式** 设置为 "带) 的 *手写* "。

## <a name="input-simulation-tools-window"></a>"输入模拟工具" 窗口

从 **混合现实**  >  **Toolkit**  >  **实用程序**  >  **输入模拟** 菜单启用 "输入模拟工具" 窗口。 此窗口提供在播放模式下对输入模拟状态的访问。

## <a name="viewport-buttons-optional"></a>视区按钮 (可选) 

可在输入模拟配置文件中的 " **指示器 prefab**" 下指定用于控制基本手布局的 prefab。 这是一个可选的实用工具，可以在 " [输入模拟工具" 窗口](#input-simulation-tools-window)中访问相同的功能。

> [!NOTE]
> 默认情况下，视区指示器处于禁用状态，因为它们目前可能会干扰 Unity UI 交互。 请参阅问题 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)。 若要启用，请将 InputSimulationIndicators prefab 添加到 **指示器 prefab**。

手动图标显示模拟手的状态：

* ![未跟踪的手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) 不跟踪。 单击 "启用&quot;。
* ![跟踪的手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;跟踪的手形图标") 只跟踪该手型，而不是由用户控制。 单击以隐藏手。
* ![受控手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "受控手形图标") 由用户跟踪和控制。 单击以隐藏手。
* ![重置手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "重置手形图标") 单击可将手形重置为默认位置。


## <a name="see-also"></a>另请参阅

* [输入系统配置文件](../input/input-providers.md)。
