---
title: Windows Mixed Reality电脑兼容性指南
description: 概述图表，其中概述了与设备兼容的最低电脑系统Windows Mixed Reality。
author: qianw211
ms.author: v-qianwen
ms.date: 09/22/2021
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 超级， 兼容， 兼容性， 系统要求， PC
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: af3228e76bc9ce54ef877b67e8e85a3bde25e140
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436726"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality电脑硬件兼容性指南

![电脑兼容性英雄图像](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>功能和体验

Windows 10和 Windows 11 Windows Mixed Reality各种电脑硬件上的各种头戴显示设备。  电脑功能将决定你可以拥有的体验。
使用高端电脑时，你可获取一些额外的功能和功能：

* 更简洁的视觉对象和更高的刷新率。
* 更多应用和体验，包括图形密集型游戏。
* 桌面上的"镜像"窗口，显示你在混合现实中所看到的内容。
* 录制和共享混合现实体验的视频和照片。

## <a name="minimum-pc-hardware-guidelines"></a>电脑硬件最低要求指南

查看以下硬件准则并运行 Windows Mixed Reality 应用，了解电脑能否[混合现实门户运行。](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)

请记住，性能因具体设置而异。 还需要确保电脑具有适用于你使用的Windows Mixed Reality沉浸式头[](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)戴显示设备所需的正确端口。

>[!NOTE]
>开发电脑的准则高于运行混合现实应用的使用者电脑的准则。 如果你是混合现实开发人员， [请参阅推荐的开发电脑规格](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)。

## <a name="mixed-reality-portal-app"></a>混合现实门户应用

[混合现实门户](https://www.microsoft.com/store/productid/9ng1h8b3zc7m)是确保电脑已准备好运行Windows Mixed Reality。

运行应用后，你可收到以下消息之一：

* **你可继续。**  电脑已准备好运行混合现实游戏和体验。
* **支持某些功能。** 电脑可以运行一些混合现实体验。
* **无法运行混合现实。** 此电脑不满足运行此电脑所需的最低Windows Mixed Reality。

然后，你将根据所需的硬件、驱动程序和操作系统对电脑进行分析。
![Windows Mixed Reality电脑检查的屏幕截图](images/screenshot-mr-pc-check.jpg)

| 图标 | 含义 |
| --- | --- |
| <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /> | 电脑会传递所需的项。 |
| <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /> | 根据给定的要求，电脑可能有问题。 如果遇到问题，可能需要对电脑进行故障排除或升级。 
| <img alt="Error" width="30" height="30" src="images/glyph-error.png" /> | 电脑不满足指定项的要求。 |

 [获取有关结果混合现实门户的帮助](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>兼容性准则

> [!IMPORTANT]
> 我们将更新，对电脑兼容性指南进行补充Windows Mixed Reality修订。 请定期回来查看最新准则和要求。

### <a name="high-resolution-headset-requirements"></a>高分辨率头戴显示设备要求

由于分辨率更高，以下要求适用于 HP Reverb G1、G2 和 Omnicept 产品系列，以确保最佳的 90 Hz 全分辨率体验：

- Intel Core i5、i7、Intel Xeon E3-1240 v5，等效或更好。 AMD Ryzen 5 等效或更佳。  
- NVIDIA GeForce GTX 1080、AMD Radeon RX 5700，等效或更好  
- 内存：8 GB RAM 或更多  
- 1x 显示端口 1.3  
- 1x USB 3.0 Type-C，带电源 (或包含的电源适配器)  
- Windows 102019 年 5 月更新或更高版本  
 
**所有其他与 WMR 兼容的头戴显示设备** <br>
对于所有其他 HMD，请参阅以下要求：

| | Windows Mixed Reality 90Hz 电脑 | Windows Mixed Reality 60Hz 电脑 |
| --- | --- | --- |
| 操作系统 | Windows 10 Fall Creators Update (RS3) 或更高版本 - 家庭、Pro、商业、教育。 <br/>     (<b>注意</b>：S 模式下的 N Windows 10 专业版 版本或版本不支持)  |
| 处理器 | Intel Core i5 4590 (第 4 代) 、四核 (或更好的)  <br> AMD Ryzen 5 1400 3.4Ghz (桌面) 、四核 (或)  | Intel Core i5 7200U (第 7 代移动) ，双核，已启用 Intel Hyper-Threading Technology (或)  <br> AMD Ryzen 5 1400 3.4Ghz (桌面) 、四核 (或)  |
| RAM | 8 GB DDR3 (或更好的)  | 8 GB DDR3 双通道 (或更好的)  |
| 可用磁盘空间 | 至少 10 GB | 至少 10 GB |
| 显卡| <ul> <li>NVIDIA GTX 1060 (或) 支持 DX12 的离散 GPU </li> <li>AMD RX 470/570 (或) 支持 DX12 的离散 GPU </li> </ul> <br> <b>注意：</b> GPU 必须托管在 PCIe 3.0 x4+ 链接槽中 |  <ul>  <li>集成 Intel HD Graphics 620 (或) 支持 DX12 的集成 GPU <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units"> (</a>检查模型是否更) </li> <li>NVIDIA MX150 (或) 离散 GPU</li> <li>Nvidia GeForce GTX 1050 离散 GPU</li> <li>Nvidia 965M 离散 GPU</li> <li>AMD Radeon RX 460/560</li> </ul> <b>注意：</b> 不支持较旧的 Intel GPU，例如 HD Graphics 4xx、5xx、2xxx、3xxx、4xxx、5xxx 和 6xxx。 |
| 图形驱动程序 | Windows显示驱动程序模型 (WDDM) 2.2 |  |
| [图形显示端口](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | 2.0 或 DisplayPort 1.2 | 1.4 或 DisplayPort 1.2 |
| 显示 | 连接的外部或集成 VGA (800x600) 显示 (或更好的)  | 
| [USB 连接](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | USB 3.0 | |
| 蓝牙控制器 (连接[连接](controllers-in-wmr.md) | 蓝牙 4.0 | |
| 预期的头戴显示设备帧速率 | 90 Hz | 60 Hz |
| 强力 | USB 3.0 端口 | USB 3.0 端口 |

**其他信息：**

* 屏幕至少为 15" 的较大笔记本电脑效果最佳。
* 混合图形配置仅与 Windows Mixed Reality 90Hz 兼容。 任何混合配置中的离散图形适配器必须满足离散图形适配器Windows Mixed Reality指南中列出的所有要求。
* 如果离散图形卡应运行 Windows Mixed Reality 90Hz，但默认为每秒 60Hz (60 帧) 刷新速率，请使用全尺寸 DisplayPort toMI 2.0 适配器插入头戴显示设备并启用 90Hz 刷新速率。
* 不同的头戴显示设备可能需要不同的硬件端口，因此请确保电脑具有正确的端口或所需的适配器[](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md)来连接到头戴显示设备。

>[!NOTE]
>不满足最低确认规格的离散和集成图形硬件尚未测试、确认或优化Windows Mixed Reality并且可能无法正常工作或完全无法正常工作。

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality和 Surface

为了在 Surface 设备上获得Windows Mixed Reality体验，我们建议使用配置了至少 NVIDIA GeForce GTX 1060 GB 和 16 GB RAM 的最新 SurfaceBook (15") 。  此配置支持Windows Mixed Reality功能，并且已经过测试，Windows Mixed Reality。  最新的 Surface Book (13.5") 、Surface Studio、Surface Laptop 和 Surface Pro (2017) 在配置 Intel Core i5 CPU (或更好的) 和至少 8 GB RAM 时，将支持某些 Windows Mixed Reality 功能。

**要求：**

* Surface 产品要求驱动程序更新与 Windows Mixed Reality。 若要在 Surface 上安装这些驱动程序，可以设置 >更新和安全>**检查更新。**
* Surface[产品需要视频](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md)端口中的适配器 (微型 DisplayPort 或 USB-C，具体取决于 Surface PC) 2.0，Windows Mixed Reality头戴显示设备。 最新版本的 Surface Mini-DisplayPort 与适用于 Mini-DisplayPort AV 适配器兼容，但 (版本未安装) 。 同样 <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">，Surface USB-C 到MIC 适配器</a> 也兼容到MIC 2.0。

## <a name="see-also"></a>请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们获得支持](https://support.microsoft.com/contactus/)
* [推荐用于Windows Mixed Reality电脑的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
