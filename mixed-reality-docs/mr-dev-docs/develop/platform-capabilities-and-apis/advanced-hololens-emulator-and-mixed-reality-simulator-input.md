---
title: 高级 HoloLens Emulator 和混合现实模拟器
description: 有关使用键盘、鼠标和 Xbox 控制器来模拟 HoloLens Emulator 和 Windows Mixed Reality 模拟器输入的详细说明。
author: pbarnettms
ms.author: pbarnett
ms.date: 06/8/2020
ms.topic: article
keywords: HoloLens，Emulator，模拟，Windows Mixed Reality，混合现实耳机，Windows Mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: a4e66b2738d5f89949b14fd6f901e2b30dc38cd9e02072f640345d374b9eb9fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217123"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>高级 HoloLens 仿真器和混合现实模拟器输入

大多数模拟器用户只需使用[HoloLens Emulator](using-the-hololens-emulator.md#basic-emulator-input)或[Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md#basic-simulator-input)的基本输入控件。 下面的详细信息适用于已发现需要模拟更复杂输入的高级用户。

## <a name="concepts"></a>概念

若要开始控制 HoloLens 的虚拟输入 Emulator 和 Windows Mixed Reality 模拟器，你应该首先了解一些概念。

动作指的是控制和更改场景中某个对象的位置和方向。 对于目标可控对象，运动由旋转和平移进行控制， (移动) 三个轴。
* **偏航**：向左或向右旋转。
* **音调**：打开或关闭。
* **滚**：并排滚动。
* **X**：向左或向右移动。
* **Y**：向上或向下移动。
* **Z**：向前或向后移动。

手势和运动控制器输入紧密映射到物理设备：
* **操作**：模拟按食指捏的操作，或在控制器上拉取操作按钮。 例如，操作输入可用于模拟攻攻敲击手势，滚动查看内容，以及按下并保持。
* **[布隆](../../design/system-gesture.md#bloom)/System 手势或 home**：使用 HoloLens 布隆/系统手势或控制器的 "主页" 按钮返回到 shell 并激发系统操作。

在 HoloLens 2 中，双手具有丰富的表示形式。  除了被跟踪/未跟踪，并可用于驾驶手势外，现在，我们还提供了一个可供用户使用的有表述的主干模型，并向开发人员公开。  骨架模型每个都有26个跟踪点。  
* **接点**：在三维空间中具有关联点的给定跟踪位置的20个跟踪位置之一。
* **姿势**：所有接头的完整集合，共26个联接。 

当前不会通过模拟器公开各个接点位置的直接控制，但你可以通过模拟 API 来设置它们。 我们有一组有用的代表，模拟器使你可以在之间切换。

你还可以控制模拟传感器输入的状态：
* **Reset**：返回所有模拟传感器的默认值。  从 HoloLens 2 Emulator 开始，可以将重置范围限定为 one 或 both。 使用修改键 (s) 使用修改键 (s) 或按钮 ()  (左和/或右 Alt，或游戏板) 上的左和/或右缓冲器。
* **跟踪**：循环浏览位置跟踪模式，其中包括：
  * **默认值**： OS 根据系统发出的请求选择最佳跟踪模式。
   * **方向**：强制仅限方向跟踪，无论系统请求。
   * **位置**：强制进行位置跟踪，不管系统请求。

## <a name="types-of-input"></a>输入类型

下表显示了每种类型的输入如何映射到键盘、鼠标和 Xbox 控制器。 每种类型都有不同的映射，具体取决于输入控件的模式。 您可以在本文档的后面部分找到有关输入控制模式的详细信息。

| 输入 |  Keyboard |  鼠标 |  Xbox 控制器 | 
|----------|----------|----------|----------|
|  Yaw |  左/右箭头 |  向左/向右拖动 |  向右控制杆左/右 | 
|  音调 |  向上/向下箭头 |  向上/向下拖动 |  右操纵杆向上/向下 | 
|  Roll |  Q/E |  |  DPad 左/右 | 
|  X |  A/D |  |  左操纵杆向左/向右 | 
|  Y |  Page up/page down |  |  DPad | 
|  Z |  W/S |  |  向左/向下移动操纵杆 | 
|  操作 |  Enter 或 space |  向右按钮 |  按钮或触发器 | 
|  布隆/系统 |  F2 或 Windows 键 |  |  B 按钮 | 
|  控制器手柄按钮/手型抓住 |  G  |  |  | 
|  控制器菜单按钮 |  M  |  |  | 
|  控制器触摸板触控 |  U  |  |  | 
|  控制器触摸板按压 |  P  |  |  | 
|  控制器操纵杆按下 |  K  |  |  | 
|  左控制器跟踪状态 |  F9 |  |  | 
|  右控制器跟踪状态 |  F10 |  |  | 
|  手动 "闭合" 姿势 | 7 |  |  |
|  "打开" (默认)  | 8 |  |  |
|  手型点姿势 | 9 |  |  |
|  手型姿势 | 0 |  |  |
|  重置 |  转义键 |  |  “开始”按钮 | 
|  跟踪 |  T 或 F3 |  |  X 按钮 | 


注意：控制器按钮可以针对一个手型/控制器或使用手形目标修饰符。

## <a name="targeting"></a>目标设定 

以上一些输入概念彼此独立。  "操作"、"布隆"/"系统"、"重置" 和 "跟踪" 是完整的概念、不需要和不受的任何其他修饰符的影响。  其余概念可以应用于多个目标之一。 我们引入了一些方法，用于指定应将命令应用于哪个目标目标。  在所有情况下，都可以通过 UI 或通过键盘按指定的对象来指定。  在某些情况下，也可以直接与 xbox 控制器一起指定。 

下表描述了针对的选项，以及每个选项的激活方式。

| 对象 | 键盘修饰符 | 控制器修饰符 | EmulatorUI 修饰符 |
|----------|----------|----------|----------|
| 正文 | （默认值） | （默认值） | （默认值） |
| 头 | 保持 H | （不可用） | （不可用） |
| 左侧/控制器 | 按住左 Alt 按钮 | 保持左侧肩按钮 | Left-Hand 图钉 | 
| 右手/控制器 | 按住右 Alt 按钮 | 保留适当的肩按钮 | Right-Hand 图钉 |
| 泄漏 | 保持 Y | （不可用） | 眼睛图钉 |
  
下表显示了每个目标修饰符如何映射每个核心移动输入概念

| 输入 | 默认 (正文)  |  手动/控制器 (按住 Alt、按住游戏板肩按钮或切换 UI 图钉)  |  Head (保持 H)   |  眼睛 (保持 Y 或切换 UI 图钉)  |
|----------|----------|----------|----------|----------|
|  Yaw |  向左/向右翻转正文 |  向左或向右移动 |  向左/右旋转 | 眼睛向左或向右看 |
|  音调 |  开启/关闭头 |  上移/下移 |  开启/关闭头 | 眼睛查看/关闭 | 
|  Roll |  向左/右滚动 |  |  向左/右滚动 | 不 (操作)  |
|  X |  向左/向右滑动 |  向左/向右移动右手/控制器 |  向左/右旋转 | 不 (操作)  |
|  Y |  上移/下移正文 |  向上/向下移动手动/控制器 |  开启/关闭头 | 不 (操作)  |
|  Z |  向后移动正文 |  向前/向后移动手动/控制器 |  开启/关闭头 | 不 (操作)  |
 
 
## <a name="controlling-an-app"></a>控制应用

建议为日常使用以下一组控件：

|  Operation |  键盘和鼠标 |  控制器 | 
|----------|----------|----------|
|  正文 X |  A/D |  左操纵杆向左/向右 | 
|  正文 Y |  Page up/page down |  DPad | 
|  正文 Z |  W/S |  向左/向下移动操纵杆 | 
|  正文偏航 |  向左/向右拖动鼠标 |  向右控制杆左/右 | 
|  头偏航 |  H + 向左/向右拖动鼠标 |  H (键盘) + 向右控制杆向左/向右 | 
|  打印头间距 |  向上/向下拖动鼠标 |  右操纵杆向上/向下 | 
|  打印头 |  Q/E |  DPad 左/右 | 
|  手动/控制器 X |  Alt + A/D |  肩 + 左操纵杆向左/右 | 
|  手动/控制器 Y |  Alt + Page up/page down |  肩 + DPad 向上/向下 | 
|  手动/控制器 Z |  Alt + W/S |  单指 + 左滚动块向上/向下 | 
|  手/控制器 Yaw |  Alt + 向左/向右拖动鼠标 |  手部 + 右滚动块左/右 | 
|  手部/控制器间距 |  Alt + 向上/向下拖动鼠标 |  双指 + 右指向上/向下滚动 | 
|  手/控制器滚动 |  Alt + Q/E |  手部 + DPad 左侧/右侧 | 
|  操作 |  鼠标右键 |  触发器 | 
|  Bloom/System/Home |  F2 或Windows键 |  B 按钮 | 
|  重置 |  Escape |  “开始”按钮 | 
|  跟踪 |  T |  X 按钮 | 
|  滚动 |  Alt + 鼠标右键 + 向上/向下拖动鼠标 |  单手 + 触发器 + 右滚动/向下滚动 | 
|  更快地移动/旋转 | 向左或向右 Shift 键 | 按并按住右 thumbstick |
|  移动/旋转缓慢 | 向左或向右 Ctrl 键 | 按并按住左 thumbstick |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>将 Windows Mixed Reality 沉浸式头戴显示设备和运动控制器与 HoloLens 2 仿真器配合使用

将沉浸式Windows Mixed Reality头戴显示设备与HoloLens 2 Emulator时，运动和旋转会自动映射到头戴显示设备移动和旋转。  运动控制器位置和方向自动映射到仿真器中的手部位置和方向。  下表列出了使用运动控制器时可用的其他操作。

> [!NOTE]
> 使用头戴显示设备时，将自动忽略标准键盘、鼠标和游戏板控件。

|  操作 |  操作 |  备注 | 
|----------|----------|----------|
|  正文 X |  Thumbstick 左/右 |   | 
|  正文 Z |  Thumbstick Forward/Back |   | 
|  正文 Y |  键盘页向上/向下 | 确保Windows Mixed Reality焦点。  如果焦点位于桌面桌面上，请按 Win+Y Windows将焦点返回到Windows Mixed Reality。 |
|  眼睛向左/向右看 |  DPad 左侧/右侧 | |
|  眼睛向上/向下查找 | DPad 向上/向下 | |
|  点击 | 触发器 | |
|  收缩/抓取 | 手柄按钮 | |
|  系统笔势 | “菜单”按钮 | |
|  重置位置 | 滚动更新单击 | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>感知模拟控制面板键盘快捷方式

可以使用以下键盘快捷方式访问"感知模拟"控制面板，并启用或禁用电脑输入设备。

| Operation | 快捷键 | 说明/说明 |
|-----------|----------|-------------|
| 切换"使用键盘进行模拟" | F4 | 关闭后，键盘输入将转到HoloLens或Windows Mixed Reality应用程序。 |
| 切换"使用鼠标进行模拟" | F5 | 关闭后，鼠标输入将转到混合现实环境 (Windows Mixed Reality仅)  |
| 切换"使用游戏板进行模拟" | F6 | 关闭后，模拟将忽略游戏板输入 |
| 显示或隐藏控制面板 | F7 | |
| 将键盘焦点设置为控制面板 | F8 | 如果面板当前不可见，它将首先显示。 |
| 将面板停靠或取消停靠到模拟器或混合现实门户窗口 | F9 | 如果窗口在取消停靠时关闭，它将停靠并隐藏。 |

## <a name="see-also"></a>另请参阅
* [安装工具](../install-the-tools.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [使用 Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)
