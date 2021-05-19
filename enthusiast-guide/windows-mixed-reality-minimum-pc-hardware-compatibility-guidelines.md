---
title: Windows Mixed Reality PC 兼容性指南
description: 概述图表，其中概述了与 Windows Mixed Reality 兼容的最小 PC 系统要求。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，Ultra，兼容，兼容性，系统要求，PC
appliesto:
- Windows 10
ms.openlocfilehash: e73b00dcf8d6974f06c22c3b0ab0771a8e1a5969
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143315"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality 最小电脑硬件兼容性指南

## <a name="features-and-experiences"></a>功能和体验

Windows 10 在一组不同的 PC 硬件上使用各种耳机来实现 Windows Mixed Reality。  您的 PC 的强大功能将决定您可以获得的体验。
对于更高端的 Pc，你将获得一些额外的功能和功能：

* 更锐利的视觉对象和更高的刷新频率。
* 更多应用和体验，包括大多数图形密集型游戏。
* 桌面上显示了在混合现实中看到的内容的 "镜像" 窗口。
* 记录和共享混合现实体验的视频和照片。

## <a name="minimum-pc-hardware-guidelines"></a>电脑硬件最低要求指南

查看以下硬件准则并运行 [混合现实门户](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) 应用，了解你的电脑是否可以运行 Windows Mixed reality。

请记住，根据确切的设置，性能会有所不同。 你还需要确保你的电脑具有适用于你正在使用的 Windows Mixed Reality 沉浸式耳机的 [正确端口](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 。

>[!NOTE]
>开发 Pc 的准则高于运行混合现实应用的使用者电脑的指导原则。 如果你是混合现实开发人员， [请参阅建议的开发 PC 规范](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)。

## <a name="mixed-reality-portal-app"></a>混合现实门户应用

[混合现实门户](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) 是确保您的 PC 准备好运行 Windows Mixed reality 的最佳方式。

运行应用后，会收到以下消息之一：

* **你可继续。**  电脑已准备好运行混合现实游戏和体验。
* **支持某些功能。** 电脑可以运行一些混合现实体验。
* **无法运行混合现实。** 此电脑不满足运行此电脑所需的最低Windows Mixed Reality。

然后，你将根据所需的硬件、驱动程序和操作系统对电脑进行分析。
![屏幕截图Windows Mixed Reality 电脑检查](images/screenshot-mr-pc-check.jpg)

<table>
<tr>
<th>图标</th><th>含义</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">电脑会传递所需的项。</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">根据给定的要求，电脑可能有问题。 如果遇到问题，可能需要对电脑进行故障排除或升级。</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">电脑不满足指定项的要求。</td>
</tr>
</table>

 [获取有关结果混合现实门户的帮助](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>兼容性准则

> [!IMPORTANT]
> 我们将更新，对电脑兼容性指南进行补充Windows Mixed Reality修订。 请定期回来查看最新准则和要求。

### <a name="high-resolution-headset-requirements"></a>高分辨率头戴显示设备要求

由于分辨率更高，以下要求适用于 HP Reverb G1、G2 和 Omnicept 产品系列，以确保最佳的 90 Hz 全分辨率体验：

<ul>
<li> Intel Core i5、i7、Intel Xenon E3-1240 v5，等效或更好。 AMD Ryzen 5 等效或更佳。 </li>
<li> NVIDIA GeForce GTX 1080、AMD Radeon RX 5700、等效或更好 </li>
<li> 内存： 8 GB RAM 或更多 </li>
<li> 1x 显示端口1。3 </li>
<li> 1x USB 3.0 类型-C 与电源传送 (或随附的电源适配器) </li>
<li> Windows 10 可能会2019更新或更高版本 </li>
</ul>

**所有其他 WMR 兼容耳机** <br>
对于所有其他 HMDs，请参阅以下要求：

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 90Hz 电脑</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 60Hz Pc</th>
</tr><tr>
    <td style="vertical-align: middle">操作系统</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 秋季创意者更新 (RS3) 或更高版本、专业版、商业版和教育版。<br/>     (<b>注意</b>：在 N 版或 Windows 10 专业版的 S 模式下不受支持) </td>
</tr><tr>
    <td style="vertical-align: middle">处理器</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (第四代) ，四核 (或更好的)  <br>AMD Ryzen 5 1400 3.4 Ghz (桌面) 、四核 (或更好的) </td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (第7代移动) 、支持 Intel Hyper-Threading 技术的双核 (或更好的)  <br>AMD Ryzen 5 1400 3.4 Ghz (桌面) 、四核 (或更好的) </td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (或更好) </td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 双通道 (或更好) </td>
</tr><tr>
    <td style="vertical-align: middle">可用磁盘空间</td>
    <td style="vertical-align: middle; text-align: center;">至少 10 GB</td>
    <td style="vertical-align: middle; text-align: center;">至少 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">图形卡</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul>
            <li>NVIDIA GTX 1060 (或) 支持 DX12 的离散 GPU</li>
            <li>AMD RX 470/570 (或) 支持 DX12 的离散 GPU </li>
            </ul>
            <b>注意：</b> GPU 必须托管在 PCIe 3.0 x4+ 链接槽中 </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>集成 Intel HD Graphics 620 (或) 支持 DX12 的集成 GPU (检查模型是否更 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">) </a></li>
        <li>NVIDIA MX150 (或) 离散 GPU</li>
        <li>Nvidia GeForce GTX 1050 离散 GPU</li>
        <li>Nvidia 965M 离散 GPU</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>注意：</b> 不支持较旧的 Intel GPU，例如 HD Graphics 4xx、5xx、2xxx、3xxx、4xxx、5xxx 和 6xxx。
    </td>
</tr><tr>
    <td style="vertical-align: middle">图形驱动程序</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows Display Driver Model (WDDM) 2.2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">图形显示端口</a></td>
    <td style="vertical-align: middle; text-align: center;">2.0 或 DisplayPort 1.2</td>
    <td style="vertical-align: middle; text-align: center;">1.4 或 DisplayPort 1.2</td>
</tr><tr>
    <td style="vertical-align: middle">显示</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">连接的外部或集成 VGA (800x600) 显示 (或更好的) </td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">USB 连接</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 </td>
</tr><tr>
    <td style="vertical-align: middle">运动控制器 (<a href="controllers-in-wmr.md">蓝牙连接) </a></td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">蓝牙 4.0</td>
</tr><tr>
    <td style="vertical-align: middle">预期的头戴显示设备帧速率</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">强力</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 端口</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 端口</td>
</tr>
</table>

**其他信息：**

* 具有至少15个屏幕的更大的便携式计算机的效果最佳。
* 混合图形配置仅与 Windows Mixed Reality 90Hz 兼容。 任何混合配置中的离散图形适配器都必须满足针对离散图形适配器的 Windows Mixed Reality 准则中列出的所有要求。
* 如果你有一个应运行 Windows Mixed Reality 90Hz 的离散图形卡，但默认情况下为每秒 60Hz (60 帧) 刷新率，请使用全尺寸 DisplayPort 到 HDMI 2.0 适配器，插入你的耳机并启用90Hz 的刷新频率。
* 不同的耳机可能需要不同的硬件端口，因此请确保您的计算机具有正确的端口或 [必要的适配器](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) 以连接到您的耳机。

>[!NOTE]
>不符合最低确认规格的离散和集成图形硬件尚未针对 Windows Mixed Reality 进行测试、确认或优化，可能无法正常工作。

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality 和 Surface

若要在 Surface 设备上获得最佳的 Windows Mixed Reality 体验，建议使用最新的 SurfaceBook (15 ") 至少配置 NVIDIA GeForce GTX 1060 GB 和 16 GB RAM。  此配置支持所有 Windows Mixed Reality 功能，并且已针对 Windows Mixed Reality 进行了测试。  最新的 Surface Book (13.5 ") 、Surface Studio、Surface 膝上机和 Surface Pro (2017) 将在配置有 Intel Core i5 CPU 的情况下，支持一些 Windows Mixed Reality 功能， (或更好的) 和至少 8 GB 的 RAM。

**要求：**

* Surface products 需要驱动程序更新才能与 Windows Mixed Reality 兼容。 可以通过转到 " **设置" > 更新和安全 > 检查更新，** 将这些驱动程序安装在你的图面上。
* Surface 产品需要来自视频端口 (微型 DisplayPort 或 USB 的 [适配器](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) ，具体取决于 Surface PC) 到 HDMI 2.0 For Windows Mixed Reality 耳机。 最新版本的 Surface Mini-DisplayPort与适用于 Mini-DisplayPort AV 适配器兼容，但 (版本未安装) 。 同样 <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">，Surface USB-C 到MIMI 适配器</a> 也与MIC 2.0 兼容。

## <a name="see-also"></a>另请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们获得支持](https://support.microsoft.com/contactus/)
* [推荐用于Windows Mixed Reality电脑的适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
