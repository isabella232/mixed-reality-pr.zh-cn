---
title: 安装适用于 HoloLens 2 的 PIX
description: 了解如何安装适用于 HoloLens 2 设备的 PIX。
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens，HoloLens 2，PIX，捕获，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 5dfc16f97790b47af3c24ca44c060a9a2495a320
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530448"
---
# <a name="installing-pix-for-hololens-2"></a>安装适用于 HoloLens 2 的 PIX

[PIX](https://devblogs.microsoft.com/pix) 是适用于 Windows 上的 DirectX 12 应用程序的性能优化和调试工具。 

## <a name="setup"></a>设置

1. 从主机 PC 获取最新的 PIX [版本]( https://devblogs.microsoft.com/pix/download) ，并通过 USB 电缆将您的 HoloLens 2 连接到您的 PC。

2. 如果你的 HoloLens 2 在 [Windows 有问必答版本](https://insider.windows.com) 上，或具有用于中断 PIX 的配置，则  [刷新你的设备](https://docs.microsoft.com/hololens/hololens-recovery) 以清除所有数据。

3. 启用 **开发人员模式** 和 **设备门户**：

* 从 Shell 打开 **设置** ：

![突出显示 "设置" 按钮的 HoloLens 菜单的屏幕截图](images/pix-img-01.jpg)

* 选择 " **更新" & 安全**：

![突出显示了 "更新和安全" 按钮的 "设置" 窗口的屏幕截图](images/pix-img-02.jpg)

* **为开发人员** 选择：

!["安全和更新" 窗口的屏幕截图，其中突出显示了 "开发人员" 按钮](images/pix-img-03.jpg)

* 启用 **使用开发人员功能** 并 **启用设备门户**

!["开发人员" 窗口的屏幕截图在 "启用设备门户" 按钮的 "设置" 中打开](images/pix-img-04.jpg)

!["开发人员" 窗口的屏幕截图在 "设置" 中打开 "使用开发功能" 切换突出显示](images/pix-img-05.jpg)

* 如果设备仍处于连接状态、处于唤醒状态，并且用户已登录，则启动 Visual Studio。

> [!IMPORTANT]
> 请确保设备不处于待机模式或睡眠状态。 如果在此步骤中遇到问题，请参阅 [Windows 设备门户说明](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)。

## <a name="preparing-for-deployment"></a>准备部署

1. 在 Visual Studio 中，将 " **ARM64** " 设置为 "平台" 和 " **设备** " 作为设备：

![突出显示了平台和设备设置的 visual studio 解决方案屏幕截图](images/pix-img-06.png)

2. 当 Visual Studio 提示你输入来自设备的 **PIN** 时：

![Visual studio 弹出窗口的屏幕截图要求提供 PIN](images/pix-img-07.png)

* 从 Shell 选择 **设置**
* 选择 **更新 & 安全性**
* **为开发人员** 选择，并在 **设备发现** 下按对 

!["开发人员" 窗口的屏幕截图在 "设置" 中打开，并突出显示设备发现](images/pix-img-08.jpg)

![突出显示注册代码的付费设备弹出窗口屏幕截图](images/pix-img-09.jpg)

* 在 Visual Studio 中输入生成的 PIN 号

3. Visual Studio 会将应用部署到连接的 HoloLens 2，这可能需要几分钟的时间，具体取决于应用程序。

## <a name="launching-pix"></a>启动 PIX

首先，使用设备门户验证应用未在 HoloLens 2 上运行。 然后，启动 PIX，连接到你的设备，然后选择 **Home**：

![PIX 应用程序主屏幕的屏幕截图](images/pix-img-10.png)

* 从左侧菜单中选择 " **连接** "：

![突出显示了 "连接" 按钮的 PIX 应用程序左侧菜单的屏幕截图](images/pix-img-11.png)

2. 从 " **计算机** " 选项卡中，选择 " **添加**"，然后输入以下凭据：
    * 别名：由用户决定
    * 主机名或 IP 地址：127.0.0。1

3. 在 "**计算机**" 选项卡的右下方选择 "**连接**"：

![已突出显示 "别名"、"主机名"、"IP 地址" 和 "添加" 按钮的 PIX 应用连接窗口屏幕截图](images/pix-img-12.png)

> [!NOTE]
> 第一次连接始终较慢，因为正在复制二进制文件。

4. 当 PIX 连接到 HoloLens 2 时，请在 "启动 UWP" 选项卡的 " **选择目标进程** " 部分找到你的应用，然后选择 " **启动**"：

![选择 "目标进程" 窗口并突出显示 "启动" 按钮时 PIX 应用程序的屏幕截图](images/pix-img-13.png)

## <a name="gpu-captured"></a>捕获的 GPU

1. 在 **Gpu 捕获** 部分中单击 "**照片**"，启动 gpu 捕获：

![显示了 "电脑连接" 面板的 PIX 应用程序屏幕截图，其中突出显示了 GPU 捕获](images/pix-img-14.png)

2. 单击 **GPU 捕获** 面板中生成的屏幕快照，打开捕获以进行分析：

![带有 gpu 捕获部分打开的 PIX 应用程序的屏幕截图，其中突出显示了 GPU 捕获面板](images/pix-img-15.png)

3. 按 " **开始** " 以开始分析：

!["启动" 按钮突出显示的 PIX 应用程序的屏幕截图](images/pix-img-16.png)

> [!IMPORTANT]
> 如果在拍摄 GPU 捕获后收集计时数据，则需要重新启动耳机。 这是一次重新启动设备，并且是计时数据收集所必需的。

PIX 现在可以使用！

## <a name="see-also"></a>另请参阅
* [PIX 主页](https://devblogs.microsoft.com/pix)