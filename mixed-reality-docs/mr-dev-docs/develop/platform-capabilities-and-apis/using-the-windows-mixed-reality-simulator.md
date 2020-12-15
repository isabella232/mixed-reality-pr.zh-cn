---
title: 使用 Windows Mixed Reality 模拟器
description: 使用 Windows Mixed Reality 模拟器，无需 Windows Mixed Reality 沉浸式耳机即可在电脑上测试混合现实应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality，模拟器，测试
ms.openlocfilehash: 4ed3355df242f1df35c009e53149d834ea113e1f
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530295"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>使用 Windows Mixed Reality 模拟器

使用 Windows Mixed Reality 模拟器，无需 Windows Mixed Reality 沉浸式耳机即可在电脑上测试混合现实应用。 Windows 10 创意者更新中提供了模拟器。 模拟器与 [HoloLens 模拟器](using-the-hololens-emulator.md)类似，但模拟器不使用虚拟机。 模拟应用在 Windows 10 桌面用户会话中运行，就像使用沉浸式耳机一样。 沉浸式耳机上传感器读取的人工和环境输入使用键盘、鼠标或 Xbox 控制器进行模拟。 应用不需要任何修改即可在模拟器中运行，并且不知道它们不在沉浸式耳机上运行。

## <a name="enabling-the-windows-mixed-reality-simulator"></a>启用 Windows Mixed Reality 模拟器

1. **启用** 开发人员模式-> 更新和安全性-为开发人员 >
2. 从桌面启动 **混合现实门户**
3. 如果这是你第一次启动门户，则需要完成安装体验
   1. 选择 **入门**
   2. 选择 " **我同意** 接受协议"
   3. 对于开发人员，请选择 " **设置" 进行模拟 ()** 在不使用物理设备的情况下继续进行安装
   4. 选择 " **设置** " 以确认你的选择
4. 选择混合现实门户左侧的 " **开发人员** " 按钮
5. 将模拟切换开关切换到 **打开**
   * 默认情况下，启用模拟将安装并启用左模拟的 DOF 控制器。  在 Windows 10 可能2019更新之前，安装模拟 6 DOF 控制器需要管理员权限。  接受 "用户帐户控制" 对话框（如果有）。

现在，你应该已运行模拟！

如果要在 "设置" 中禁用开发人员模式，则应首先在混合现实门户的 "**开发人员**" 部分中将模拟切换开关设置为 "**关闭**"。

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>将应用部署到混合现实模拟器

由于模拟器在没有虚拟机的情况下在本地 PC 上运行，因此你可以在调试时将通用 Windows 应用程序部署到 **本地计算机** 。

## <a name="basic-simulator-input"></a>基本模拟器输入

控制模拟器类似于许多常见的3D 视频游戏和 [HoloLens 模拟器](using-the-hololens-emulator.md)。 可以使用键盘、鼠标或 Xbox 控制器提供输入。

可以通过定向模拟用户的操作，戴上沉浸式耳机来控制模拟器。 你的操作将移动模拟用户，并与应用进行交互，使其与沉浸式耳机上的响应相同。
* **前后左右走动** - 使用键盘上的 WASD 键，或 Xbox 控制器上的左摇杆。
* **查找、向下、向左** 、向右选择并拖动鼠标、使用键盘上的箭头键或 Xbox 控制器上的右摇杆。
* **操作按钮按下控制器** -右键单击鼠标，按键盘上的 enter 键，或使用 Xbox 控制器上的按钮。
* **"主页" 按钮按下控制器** -按键盘上的 Windows 键或 F2 键，或按 Xbox 控制器上的 B 按钮。
* **用于滚动的控制器移动** -按住 Alt 键和鼠标右键，然后向上或向下拖动鼠标。 在 Xbox 控制器中，按住右触发器和按钮，并将右摇杆向下和向下移动。

## <a name="tracked-controllers"></a>跟踪控制器

混合现实模拟器最多可以模拟两个手持跟踪的运动控制器。 在混合现实门户中使用切换开关启用它们。 每个模拟控制器都有：
* 位置和方向（空间）
* “主页”按钮
* “菜单”按钮
* 手柄按钮
* 触摸板
* 控制
* 电池电量水平

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unity 开发检查点历程，则你就处于部署阶段之中。 在这里，你可以继续下一 [主题](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) 或直接跳转到添加高级服务。

> [!div class="nextstepaction"]
> [高级服务](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>另请参阅
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [高级混合现实模拟器输入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Unity 中的空间映射](../../develop/unity/spatial-mapping-in-unity.md)
* [DirectX 中的空间映射](../../develop/native/spatial-mapping-in-directx.md)
