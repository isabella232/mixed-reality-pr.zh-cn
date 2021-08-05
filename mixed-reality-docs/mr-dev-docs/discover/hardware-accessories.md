---
title: 硬件配件
description: 介绍可用于 Windows Mixed Reality 的附件类型，以及如何设置它们。
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: 操作方法， 附件， 蓝牙， bt， 控制器， 游戏板， 点击器， xbox， 硬件， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， 运动控制器
ms.openlocfilehash: a6776df9374fce3f1399de944be06c93ff6fdcb3e6f4a38dcc92453556857376
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188448"
---
# <a name="hardware-accessories"></a>硬件配件

Windows Mixed Reality设备支持附件。 可以使用手机蓝牙 USB 端口将支持的附件与电脑中的沉浸式头戴显示设备配对。

有关将 蓝牙 附件与 HoloLens 的信息，连接 蓝牙 和[USB-C 设备。](/hololens/hololens-connect-devices)

Windows Mixed Reality沉浸式头戴显示设备需要附件进行除凝[视和](../design/gaze-and-commit.md)语音 之外的[输入](../design/voice-input.md)。 支持的附件包括 **键盘和鼠标**、**游戏板****[和运动控制器](../design/motion-controllers.md)**。

## <a name="pairing-bluetooth-accessories"></a>配对蓝牙附件

将蓝牙头戴显示设备与沉浸式头戴显示设备配对蓝牙设备与Windows 10设备配对：

1. 在"开始"菜单中 **，打开设置** 应用
2. 转到 **"设备"**
3. 如果蓝牙开关关闭，请打开单选按钮
4. 将设备蓝牙配对模式。 此过程因设备而异，但在大多数设备上蓝牙按住一个或多个按钮。
5. 等待设备的名称显示在设备蓝牙列表中。 选择设备后，选择"配对 **"** 按钮。 如果附近有许多蓝牙设备，可能需要滚动到 蓝牙 设备列表的底部，以查看尝试配对的设备。
6. 将蓝牙外围设备与输入功能 (例如：蓝牙键盘) ，可能会显示 6 位或 8 位引脚。 请确保在外围设备上键入该引脚，然后按 Enter 完成与头戴显示设备的配对。

## <a name="motion-controllers"></a>运动控制器

Windows Mixed Reality[沉浸](../design/motion-controllers.md)式头戴显示设备支持运动控制器，但不支持HoloLens。 这些控制器在视场中提供精确的响应式移动跟踪。 沉浸式头戴显示设备中的传感器执行跟踪，这意味着无需在空间的墙上安装硬件。 每个控制器具有多种输入方法。

![Windows Mixed Reality运动控制器](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>蓝牙键盘

英语键盘蓝牙键盘可以配对，并可在任何可以使用全息键盘的地方使用。 获取质量键盘会有所不同，因此我们建议使用 Microsoft[通用](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001)可折叠键盘或[Microsoft Designer 蓝牙 Desktop。](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)

## <a name="bluetooth-gamepads"></a>蓝牙游戏板

可以将控制器与专门启用游戏板支持的应用和游戏一同使用。 游戏板不能用于控制HoloLens用户界面。

Xbox 无线控制器与 Xbox One S 或作为附件销售，Xbox One S功能蓝牙连接，因此可以将它们与HoloLens头戴显示设备一起使用。 必须先更新 Xbox[无线控制器](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)，然后才能与 HoloLens。

其他品牌蓝牙游戏板可能Windows Mixed Reality设备，但支持因应用程序而异。

## <a name="other-bluetooth-accessories"></a>其他蓝牙附件

只要外围设备支持 HID 蓝牙 GATT 配置文件，就可以与 HOLOLENS。 除蓝牙、鼠标和单击器外的其他 HID 和 GATT HoloLens可能需要在设备上安装一个Microsoft HoloLens应用程序，以完全正常运行。

不支持的外围设备包括：

* 不支持蓝牙配置文件中的外围设备。
* 蓝牙音频设备（如扬声器和头戴显示设备）在 设置 应用中可用，但不支持将 Microsoft HoloLens 作为音频终结点。
* 蓝牙手机和电脑不支持配对和文件传输。

## <a name="unpairing-a-bluetooth-peripheral"></a>与外围设备蓝牙连接

1. 在"开始"菜单中 **，打开设置** 应用
2. 转到 **"设备"**
3. 打开蓝牙（如果已关闭）
4. 在可用设备列表中查找蓝牙设备
5. 从列表中选择设备，然后选择"删除 **"** 按钮