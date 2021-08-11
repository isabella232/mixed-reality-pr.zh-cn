---
title: 使用 Windows Mixed Reality 模拟器
description: 使用Windows Mixed Reality模拟器，无需使用沉浸式头戴显示设备即可在电脑上Windows Mixed Reality现实应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality，模拟器，测试
ms.openlocfilehash: 0a6ff0cb0cd893c40e354c0590437201fb97e75c67421a638e47897b19a8f688
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220926"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>使用 Windows Mixed Reality 模拟器

使用Windows Mixed Reality模拟器，无需使用沉浸式头戴显示设备即可在电脑上Windows Mixed Reality现实应用。 模拟器可用于Windows 10 创意者更新。 模拟器类似于[HoloLens Emulator，但](using-the-hololens-emulator.md)模拟器不使用虚拟机。 模拟应用在桌面Windows 10会话中运行，就像使用沉浸式头戴显示设备一样。 沉浸式头戴显示设备上的传感器读取的人类和环境输入改为使用键盘、鼠标或 Xbox 控制器进行模拟。 应用无需任何修改，无需在模拟器中运行，并且不知道它们未在沉浸式头戴显示设备上运行。

## <a name="enabling-the-windows-mixed-reality-simulator"></a>启用 Windows Mixed Reality 模拟器

1. **从 -设置**-> 更新和安全性 -> 开发人员启用开发人员模式
2. 从 **混合现实门户** 启动应用程序
3. 如果这是首次启动门户，则需要完成安装体验
   1. 选择 **"入门"**
   2. 选择 **"我同意** 接受协议"
   3. 选择 **"设置模拟 (让开发人员)** 在没有物理设备的情况下继续完成设置
   4. 选择 **"设置** "以确认选择
4. 选择 **应用程序左侧** 的"开发人员混合现实门户
5. 将"模拟"切换开关切换到 **"打开"**
   * 默认情况下，启用模拟将安装并启用左侧模拟的 6 DOF 控制器。  在 Windows 10 2019 年 5 月更新之前，安装模拟的 6 DOF 控制器需要管理员权限。  如果显示"用户帐户控制"对话框，则接受该对话框。

现在应运行模拟！

如果要在"开发人员"模式下禁用"开发人员设置，应首先在"开发人员"部分中将"模拟"切换开关混合现实门户。 

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>将应用部署到混合现实模拟器

由于模拟器在没有虚拟机的情况下在本地电脑上运行，因此可以在调试时将通用Windows **应用部署到本地** 计算机。

## <a name="basic-simulator-input"></a>基本模拟器输入

控制模拟器类似于许多常见的 3D 电子游戏和HoloLens[模拟器](using-the-hololens-emulator.md)。 可以使用键盘、鼠标或 Xbox 控制器提供输入。

通过指导模拟用户使用沉浸式头戴显示设备的操作来控制模拟器。 操作会移动模拟用户，并会导致与响应方式与沉浸式头戴显示设备上的应用交互。
* **前后左右走动** - 使用键盘上的 WASD 键，或 Xbox 控制器上的左摇杆。
* **向上、向下、向左** 和向右查找 - 选择并拖动鼠标、使用键盘上的箭头键或 Xbox 控制器上的右键。
* **按控制器上的操作** 按钮 - 右键单击鼠标，按键盘上的 Enter 键，或使用 Xbox 控制器上的 A 按钮。
* **主按钮按控制器**- 按键盘Windows键或 F2 键，或按 Xbox 控制器上的 B 按钮。
* **用于滚动的控制器移动** - 按住 Alt 键和鼠标右键，然后向上/向下拖动鼠标。 在 Xbox 控制器中按住右扳机键和 A 按钮的同时向上和向下移动右摇杆。

## <a name="tracked-controllers"></a>跟踪的控制器

混合现实模拟器可模拟最多两个手动跟踪运动控制器。 使用设备中的切换开关启用混合现实门户。 每个模拟控制器都有：
* 空间中的位置和方向
* “主页”按钮
* “菜单”按钮
* 手柄按钮
* 触摸板
* Thumbstick
* 电池剩余电量

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unity 开发检查点历程，则你就处于部署阶段之中。 在这里，可以继续学习 [下一个主题](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) ，也可以直接跳转到添加高级服务。

> [!div class="nextstepaction"]
> [高级服务](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>另请参阅
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [高级混合现实模拟器输入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Unity 中的空间映射](../../develop/unity/spatial-mapping-in-unity.md)
* [DirectX 中的空间映射](../../develop/native/spatial-mapping-in-directx.md)
