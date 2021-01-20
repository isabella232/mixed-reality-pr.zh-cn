---
title: 硬件配件
description: 介绍可用于 Windows Mixed Reality 的附件类型，以及如何对其进行设置。
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: 操作说明，附件，蓝牙，bt，控制器，游戏板，clicker，xbox，硬件，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，运动控制器
ms.openlocfilehash: b9a58a34a88de01d1d2351ff0a5efbe4f99298db
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583322"
---
# <a name="hardware-accessories"></a>硬件配件

Windows Mixed Reality 设备支持附件。 可以使用蓝牙或 USB 端口将支持的附件与电脑上的沉浸式耳机配对。

有关将蓝牙附件与 HoloLens 配合使用的信息，请参阅 [连接到蓝牙和 USB-C 设备](/hololens/hololens-connect-devices)。

Windows Mixed Reality 沉浸式耳机需要用于输入的 [附件，看](../design/gaze-and-commit.md) 看看不到 [声音](../design/voice-input.md)。 支持的附件包括 **键盘和鼠标**、 **游戏板** 和 **[运动控制器](../design/motion-controllers.md)**。

## <a name="pairing-bluetooth-accessories"></a>配对蓝牙附件

使用沉浸式耳机配对蓝牙外围设备类似于将蓝牙外围设备与 Windows 10 桌面或移动设备配对：

1. 从 "开始" 菜单中打开 " **设置** " 应用
2. 中转到 **设备**
3. 如果蓝牙无线电设备使用滑块开关，则将其打开
4. 将蓝牙设备置于配对模式下。 此过程因设备而异，但在大多数 Bluetooth 设备上，按住一个或多个按钮。
5. 等待设备的名称显示在蓝牙设备列表中。 完成后，选择设备，然后选择 " **对** " 按钮。 如果你有多个附近的蓝牙设备，则可能需要滚动到蓝牙设备列表的底部，才能看到你要尝试配对的设备。
6. 当将蓝牙外围设备与输入功能配对 (例如：蓝牙键盘) 时，可能会显示一个6位数或8位数的 pin。 请确保在外围设备上输入该 pin，并按 enter 键完成与耳机的配对。

## <a name="motion-controllers"></a>运动控制器

沉浸式耳机支持 Windows Mixed Reality [运动控制器](../design/motion-controllers.md) ，但不支持 HoloLens。 这些控制器在你的视图的字段中提供精确的响应性移动跟踪。 沉浸式耳机中的传感器进行跟踪，这意味着无需在空间中的墙壁上安装硬件。 每个控制器都具有几个输入方法。

![Windows Mixed Reality 运动控制器](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>蓝牙键盘

使用简体中文的蓝牙键盘可以在任何可使用全息键盘的地方配对和使用。 获取质量键盘会产生差别，因此建议使用 [Microsoft 通用折叠键盘](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) 或 [Microsoft Designer 蓝牙桌面](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)。

## <a name="bluetooth-gamepads"></a>蓝牙 gamepads

可以将控制器与专门启用游戏板支持的应用和游戏配合使用。 Gamepads 不能用于控制 HoloLens 用户界面。

Xbox one 随附的 xbox 无线控制器，或者作为 Xbox One 功能的 "蓝牙连接" 的附件售出，因此可将其用于 HoloLens 和沉浸式耳机。 [必须先更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)Xbox 无线控制器，然后才能将其与 HoloLens 配合使用。

其他品牌的蓝牙 gamepads 可能适用于 Windows Mixed Reality 设备，但支持会因应用程序而异。

## <a name="other-bluetooth-accessories"></a>其他蓝牙附件

只要外围设备支持蓝牙 HID 或 GATT 配置文件，它就可以与 HoloLens 配对。 除键盘、鼠标和 HoloLens Clicker 以外的其他蓝牙 HID 和 GATT 设备可能需要 Microsoft HoloLens 上的配套应用程序才能完全正常运行。

不受支持的外设包括：

* 蓝牙音频配置文件中的外围设备不受支持。
* 可以在 "设置" 应用中使用 "扬声器和耳机" 等蓝牙音频设备，但不支持将 Microsoft HoloLens 作为音频终结点。
* 启用 Bluetooth 的手机和电脑不支持配对和文件传输。

## <a name="unpairing-a-bluetooth-peripheral"></a>取消配对蓝牙外围设备

1. 从 "开始" 菜单中打开 " **设置** " 应用
2. 中转到 **设备**
3. 如果蓝牙无线电已关闭，请打开它
4. 在可用的蓝牙设备列表中找到你的设备
5. 从列表中选择你的设备，然后选择 " **删除** " 按钮