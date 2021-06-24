---
title: 输入模拟服务
description: 有关 MRTK 中的输入模拟服务的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 5420f3f2d20d07585007a58f5cf70d8e2027efc6
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588842"
---
# <a name="input-simulation-service"></a>输入模拟服务

![MRTK 输入模拟](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

借助 MRTK 的输入模拟，你可以在 Unity 编辑器中测试各种类型的交互，而无需生成并部署到设备。 这使你可以在设计和开发过程中快速循环你的想法。 使用键盘和鼠标组合来控制模拟输入。

输入模拟服务模拟可能在 Unity 编辑器中不可用的设备和平台的行为。 示例包括：

* HoloLens 或 VR 设备标题跟踪
* HoloLens 手势
* HoloLens 2 已表述的手动跟踪
* HoloLens 2 目视跟踪
* VR 设备控制器

> [!WARNING]
> 当使用 Unity 的 XR 全息模拟 > 模拟模式 = "在编辑器中模拟" 时，此操作不起作用。 Unity 的编辑器内模拟将从 MRTK 的输入模拟中控制。 若要使用 MRTK 输入模拟服务，需要将 XR 全息仿真设置为仿真模式 = *"无"*

## <a name="how-to-use-mrtk-input-simulation"></a>如何使用 MRTK 输入模拟 

默认情况下，在 MRTK 附带的配置文件中启用输入模拟。 只需单击 " **播放** " 按钮即可运行具有输入模拟支持的场景。

* 按 **W、A、S、D、Q、E** 键移动相机。
* 按住鼠标 **右键** ，并移动鼠标以进行浏览。
* 若要启动模拟手势，请按 **空格键 (向右)** 或 **向左 Shift 键 (左手)**
* 若要在视图中保持模拟，请按 **T** 或 **Y** 键
* 要旋转模拟手，请按住 **Ctrl 键** 并移动鼠标

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a>在编辑器输入模拟工作表中

在 HandInteractionExamples 场景中按 **左 Ctrl + H** ，以显示包含输入模拟控件的 "工作表"。

> ![MRTK 输入模拟备忘单](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a>启用输入模拟服务

在输入系统数据提供程序配置下，可通过以下方式配置输入模拟服务。

* **类型** 必须是 *MixedReality > InputSimulationService*。
* 默认情况下，**支持的平台 ()** 包含所有 *编辑器* 平台，因为该服务使用键盘和鼠标输入。

> [!NOTE]
> 可以通过将 **支持的平台 (s)** 属性更改为包含所需的目标，在其他平台终结点（如独立）上使用输入模拟服务。
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a>照相机控件

头移动可由输入模拟服务模拟。

### <a name="rotating-the-camera"></a>旋转相机

1. 将鼠标悬停在视区编辑器窗口之上。
    *如果按钮按下不起作用，则您可能需要单击窗口以使其输入焦点。*
1. 按住鼠标的 " **查找" 按钮** (默认：鼠标右键) 。
1. 在视区窗口中移动鼠标，旋转相机。
1. 使用滚轮按视图方向滚动相机。

可以通过更改输入模拟配置文件中的 " **鼠标外观速度** " 设置来配置照相机旋转速度。

另外，还可以使用 "**横向**" / **外观垂直** 轴旋转相机 (默认：游戏控制器右操纵杆) 。

### <a name="moving-the-camera"></a>移动摄像头

使用 "**移动水平** / **移动垂直** 轴" (默认值： WASD 键或游戏控制器左操纵杆) 移动相机。

还可以在 "工具" 窗口中显式设置相机位置和旋转角度。 可以使用 " **重置** " 按钮将相机重置为其默认值。

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>控制器模拟

输入模拟支持 (模拟控制器设备，如运动控制器和) 。 这些虚拟控制器可以与支持常规控制器的任何对象（如按钮或 grabbable 对象）进行交互。

### <a name="controller-simulation-mode"></a>控制器模拟模式

在 " [输入模拟工具" 窗口](#input-simulation-tools-window) 中， **默认的控制器模拟模式** 设置在三个不同的输入模型之间切换。 此默认模式也可以在输入模拟配置文件中进行设置。

* 明确 *说明：模拟* 带有联合位置数据的一个完全表述的手形设备。

   模拟 HoloLens 2 交互模型。

   可以在此模式下模拟基于手或使用触摸的精确定位的交互。

* *手势：通过* 使用 "分流" 和 "基本" 手势模拟简化的手模型。

   模拟 [HoloLens 交互模型](/windows/mixed-reality/gestures)。

   使用注视指针控制焦点。 *Air 攻丝* 笔势用于与按钮交互。

* *运动控制器*：模拟与 VR 耳机一起使用的运动控制器，其工作方式类似于与清晰的手势交互。

   模拟 VR 耳机与控制器交互模型。

   通过键盘和鼠标输入模拟触发器、抓取和菜单键。

### <a name="simulating-controller-movement"></a>模拟控制器移动

按住 **左/右控制器操作键** (默认值：左侧控制器的 *左移* 和右控制器的 *空间*) 以获得控制器的控制。 按下操作键时，控制器将显示在视区中。 释放操作密钥后，控制器将在短 **控制器隐藏超时** 后消失。

控制器可以在 " [输入模拟工具" 窗口](#input-simulation-tools-window) 中的相机之间切换，也可以通过按 " **切换左/右" 控制器键** (默认值 *： "* 左" 和 " *Y* " 右) 。 再次按切换键，以再次隐藏控制器。 若要操作控制器，需要保留 **左/右控制器操作密钥** 。 双击 **左/右控制器操作键** 还可以开启/关闭控制器。

鼠标移动将在视图平面移动控制器。 可以使用 **鼠标滚轮** 将控制器进一步或更接近相机。

若要使用鼠标旋转控制器，请将 **左/右控制器操作键** (*左移* 或 *空间*) *，* **控制器旋转按钮** (默认：左按 *Ctrl* 按钮) ，然后移动鼠标来旋转控制器。 可以通过更改输入模拟配置文件中的 " **鼠标控制器旋转速度** " 设置来配置控制器旋转速度。

也可以在 " [输入模拟工具" 窗口](#input-simulation-tools-window)中更改所有位置，包括将指针重置为默认值。

### <a name="additional-profile-settings"></a>其他配置文件设置

* **控制器深度乘数** 控制鼠标滚轮深度移动的灵敏度。 数字越大，控制器缩放就会提高。
* **默认控制器距离** 是控制器与照相机的初始距离。 单击 " **重置** " 按钮控制器也会将控制器置于此距离。
* **控制器抖动量** 将随机运动添加到控制器。 此功能可用于在设备上模拟不准确的控制器跟踪，并确保交互工作非常适合于输入。

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>手势

也可以模拟手写手势，如收缩、抓取、闲逛等。

1. 使用 **左/右控制器操作键** 启用手动控制 (*左移* 或 *空间*) 

2. 进行操作时，按住鼠标按钮以执行手动手势。

每个鼠标按钮都可以映射，使用 *鼠标左键或中键笔势* 设置将手形形状转换为不同的笔势。 当没有按下任何按钮时， *默认的手势* 将为手形形状。

> [!NOTE]
> 此时，只会执行 "选择" 操作的 "选中 *" 的笔势* 。

### <a name="one-hand-manipulation"></a>一次操作

1. 按住左 **/右控制器操作键** (*左移* 或 *空间*) 
2. 指向对象
3. 按住鼠标按钮进行挤压
4. 使用鼠标移动对象
5. 释放鼠标按钮以停止交互

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>双重操作

若要同时处理两个对象，建议使用永久性的手动模式。

1. 按下切换键 (*T/Y*) 切换。
1. 一次操作一只手：
    1. 按住 **空格** 可控制右侧
    1. 将手移到要抓取对象的地方
    1. 按 **鼠标左键***激活收缩手势*。
    1. 释放 **空间** 以停止控制右侧。 手将就地冻结并锁定到收缩手势中，因为它不再被操作。
1. 另一方面重复此过程，在另一个位置抓取同一个对象。
1. 现在，两只手都抓取同一个对象，可以移动其中一个，以执行两手操作。

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>GGV (凝视、手势和语音) 交互

默认情况下，GGV 交互在编辑器中启用，而场景中没有可表达的手。

1. 旋转相机，将凝视光标指向可交互 (鼠标按钮) 
1. 单击并按住 **鼠标左键** 进行交互
1. 再次旋转相机以操作对象

可以通过在输入模拟配置文件中切换"启用 *无手输入"* 选项来关闭此选项。

此外，可以使用模拟手进行 GGV 交互

1. 通过切换输入模拟配置文件 **中的手势模拟模式***来* 启用 GGV [模拟](#enabling-the-input-simulation-service)
1. 旋转相机，将凝视光标指向可交互 (鼠标按钮) 
1. 按住 **空格** 可控制右侧
1. 单击并按住 **鼠标左键** 进行交互
1. 使用鼠标移动对象
1. 释放鼠标按钮以停止交互

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a>引发 Teleport 事件

若要在输入模拟中引发远程端口事件，请配置输入模拟配置文件中的手势设置，以便一个执行 **远程** 端口启动手势，而另一个执行 **远程端口结束** 手势。 **Teleport 开始** 手势将启动 Teleport 指针，而 **Teleport End** gesure 将完成远程端口操作并移动用户。

生成的远程端口的 y 位置取决于相机沿 y 轴的位移。 在编辑器中，默认为 0，因此请使用 **Q** 和 **E** 键调整到适当的高度。

![输入模拟远程端口设置](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>运动控制器交互

模拟运动控制器的操控方式与定手操作方式相同。 交互模型类似于手部远部交互，而触发器、抓取键和菜单键分别映射到 *鼠标* 左键 *、G* 键 *和 M* 键。

### <a name="eye-tracking"></a>眼动跟踪

[可以通过检查](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) 输入模拟配置文件 中的 **"模拟眼睛位置** "选项来 [启用眼动跟踪模拟](#enabling-the-input-simulation-service)。 这不应与 GGV 或运动控制器样式交互 (因此请确保将"默认控制器模拟模式"设置为"定点手部) 。

## <a name="input-simulation-tools-window"></a>输入模拟工具窗口

从"混合现实工具包实用工具""输入模拟"菜单中  >    >    >  **启用输入模拟工具** 窗口。 此窗口提供对播放模式期间输入模拟状态的访问。

## <a name="viewport-buttons-optional"></a>视区按钮 (可选) 

可在"指示器预制"下的输入模拟配置文件中指定用于控制基本手部放置的编辑器中按钮 **的预制。** 这是一个可选实用工具，可以在输入模拟工具窗口中访问 [相同的功能](#input-simulation-tools-window)。

> [!NOTE]
> 视区指示器默认处于禁用状态，因为它们当前有时会干扰 Unity UI 交互。 请参阅问题[#6106。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106) 若要启用，将 InputSimulationIndicators 预制添加到 **指示器预制。**

手部图标显示模拟手的状态：

* ![未跟踪手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) 手未跟踪。 单击以启用手部。
* ![跟踪手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "跟踪手形图标") 手被跟踪，但不由用户控制。 单击可隐藏手部。
* ![受控手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "受控手形图标") 手由用户跟踪和控制。 单击可隐藏手部。
* ![重置手形图标](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "重置手形图标") 单击以将手重置为默认位置。


## <a name="see-also"></a>另请参阅

* [输入系统配置文件](../input/input-providers.md)。