---
title: Windows Mixed Reality电脑兼容性指南
description: 概述图表，其中概述了与设备兼容的最低电脑系统Windows Mixed Reality。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 超级， 兼容， 兼容性， 系统要求， 电脑
appliesto:
- Windows 10
ms.openlocfilehash: ed9113c5aa54d74678fcd6f888fa96007533d0d27e921f91aa6feeda459d11b7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187842"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality电脑硬件兼容性指南

![电脑兼容性英雄图像](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>功能和体验

Windows 10为Windows Mixed Reality各种电脑硬件上的头戴显示设备提供支持。  电脑功能将决定你可以拥有的体验。
使用高端电脑时，你可获取一些额外的功能和功能：

* 更简洁的视觉对象和更高的刷新率。
* 更多应用和体验，包括图形密集型游戏。
* 桌面上的"镜像"窗口，显示你在混合现实中所看到的内容。
* 录制和共享混合现实体验的视频和照片。

## <a name="minimum-pc-hardware-guidelines"></a>电脑硬件最低要求指南

查看以下硬件准则并运行 Windows Mixed Reality 应用，了解电脑[能否](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)混合现实门户运行。

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
<li> Intel Core i5、i7、Intel Xeon E3-1240 v5，等效或更好。 AMD Ryzen 5 等效或更佳。 </li>
<li> NVIDIA GeForce GTX 1080、AMD Radeon RX 5700，等效或更好 </li>
<li> 内存：8 GB RAM 或更多 </li>
<li> 1x 显示端口 1.3 </li>
<li> 1x USB 3.0 Type-C，带电源 (或包含的电源适配器) </li>
<li> Windows 102019 年 5 月更新或更高版本 </li>
</ul>

**所有其他与 WMR 兼容的头戴显示设备** <br>
对于所有其他 HMD，请参阅以下要求：

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 90Hz 电脑</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 60Hz 电脑</th>
</tr><tr>
    <td style="vertical-align: middle">操作系统</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) 或更高版本 - 家庭、Pro、商业、教育。<br/>     (<b>注意</b>：在 S 模式下的 N Windows 10 专业版 版本或版本上) </td>
</tr><tr>
    <td style="vertical-align: middle">处理器</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (第 4 代) 、四核 (或更好的)  <br>AMD Ryzen 5 1400 3.4Ghz (桌面) 、四核 (或更好的) </td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (第 7 代移动) ，双核，已启用 Intel Hyper-Threading Technology (或)  <br>AMD Ryzen 5 1400 3.4Ghz (桌面) 、四核 (或更好的) </td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (或更佳) </td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 双通道 (或更好的) </td>
</tr><tr>
    <td style="vertical-align: middle">可用磁盘空间</td>
    <td style="vertical-align: middle; text-align: center;">至少 10 GB</td>
    <td style="vertical-align: middle; text-align: center;">至少 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">显卡</td>
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
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows显示驱动程序模型 (WDDM) 2.2</td>
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
    <td style="vertical-align: middle">蓝牙运动<a href="controllers-in-wmr.md"> (的</a>) </td>
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

* 屏幕至少为 15"的较大笔记本电脑效果最佳。
* 混合图形配置仅与 Windows Mixed Reality 90Hz 兼容。 任何混合配置中的离散图形适配器必须满足离散图形适配器Windows Mixed Reality指南中列出的所有要求。
* 如果离散图形卡应运行 Windows Mixed Reality 90Hz，但默认为 60Hz (60 帧/秒) 刷新速率，请使用全尺寸 DisplayPort toMI 2.0 适配器插入头戴显示设备并启用 90Hz 刷新速率。
* 不同的头戴显示设备可能需要不同的硬件端口，因此请确保电脑具有正确的端口或所需的适配器[](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md)来连接到头戴显示设备。

>[!NOTE]
>不符合最低确认规格的离散和集成图形硬件尚未针对 Windows Mixed Reality 测试、确认或优化，它们可能无法正常运行。

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality 和图面

若要在 Surface 设备上获得最佳 Windows Mixed Reality 体验，建议使用最新的 SurfaceBook (15 ") 至少配置 NVIDIA GeForce GTX 1060 GB 和 16 gb RAM。  此配置支持所有 Windows Mixed Reality 功能，并且已经过 Windows Mixed Reality 测试。  最新的 Surface Book (13.5 ") 、Surface Studio、Surface Laptop 和 Surface Pro (2017) 在配置了 Intel Core i5 CPU Windows Mixed Reality 或更好的 (和至少 8 GB 的 RAM 时，它们都支持某些) 功能。

**要求：**

* Surface products 需要驱动程序更新才能与 Windows Mixed Reality 兼容。 可以通过转到 **设置 > 更新和安全 > 检查更新** 来安装这些驱动程序。
* surface 产品需要来自视频端口 (微型 DisplayPort 或 USB）的[适配器](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md)，具体取决于 Windows Mixed Reality 耳机) 到 HDMI 2.0 的 surface PC。 最新版本的 Surface Mini-DisplayPort 到 HDMI AV 适配器与 HDMI 2.0 兼容 (不) 旧版本。 同样， <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB 到 Hdmi 适配器</a> 也与 hdmi 2.0 兼容。

## <a name="see-also"></a>另请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)
* [适用于 Windows Mixed Reality 功能的电脑的推荐适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
