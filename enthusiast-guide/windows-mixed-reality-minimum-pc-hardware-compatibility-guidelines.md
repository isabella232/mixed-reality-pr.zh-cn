---
title: Windows Mixed Reality 最小电脑硬件兼容性指南
description: 显示与 Windows Mixed Reality 兼容的最小 PC 系统要求的图表。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，Ultra，兼容，兼容性，系统要求，PC
appliesto:
- Windows 10
ms.openlocfilehash: bd287e2089056be56330c2c2e8e9af2c079009ac
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725658"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality 最小电脑硬件兼容性指南

## <a name="features-and-experiences"></a>功能和体验

Windows 10 同时为 Windows Mixed Reality 和 Windows Mixed Reality 供电。 您所遇到的版本取决于您的 PC 硬件。

借助 Windows Mixed Reality，你可以获得一些额外的功能和功能：

* 更锐利的视觉对象和更高的刷新频率 (每秒90帧) 。
* 更多应用和体验，包括大多数图形密集型游戏。
* 桌面上显示了在混合现实中看到的内容的 "镜像" 窗口。
* 记录和共享混合现实体验的视频和照片。

## <a name="minimum-pc-hardware-guidelines"></a>电脑硬件最低要求指南

为了获得 Windows Mixed Reality 的最佳体验，请从新的适用于 windows [Mixed reality 的 pc](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 或 Windows mixed reality 兼容的电脑开始，从而提供 Windows Mixed reality 超体验。 Windows Mixed Reality 在更高的刷新率下提供了更多的更多的视觉对象、更多应用体验，包括大多数图形密集型游戏、在桌面上镜像 Windows Mixed Reality 体验，以及记录和共享 (照片和视频) 你的体验。 

查看以下硬件准则并运行 [混合现实门户应用](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M)，了解你的电脑是否可以运行 Windows Mixed reality。

请记住，根据确切的设置，性能会有所不同。 你还需要确保你的电脑具有适用于你正在使用的 Windows Mixed Reality 沉浸式耳机的 [正确端口](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) 。

>[!NOTE]
>开发 Pc 的准则高于运行混合现实应用的使用者电脑的指导原则。 如果你是混合现实开发人员， [请参阅建议的开发 PC 规范](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)。


## <a name="mixed-reality-portal-app"></a>混合现实门户应用

混合现实门户是确保您的 PC 准备好运行 Windows Mixed Reality 的最佳方式。 

<a href="https://www.microsoft.com/store/productid/9ng1h8b3zc7m"><img alt="Download Mixed Reality Portal" src="images/WMR-PC-Check-app.png"/></a>

运行应用后，会收到以下消息之一：
* **准备好了。** 你的电脑具有运行 Windows Mixed Reality 所需要的功能。
* **支持某些功能。** 这台电脑可以运行 Windows Mixed Reality，但某些功能可能会受到限制。
* **无法运行混合现实。** 这台电脑不满足运行 Windows Mixed Reality 所需的最低要求。

然后，将针对所需的硬件、驱动程序和操作系统分析你的 PC。
![Windows Mixed Reality PC 检查的屏幕截图](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>图标</th><th>含义</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">你的电脑传递所需的项目。</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">你的计算机可能存在特定要求的问题。 如果遇到问题，可能需要对 PC 进行故障排除或升级。</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">你的电脑不满足指定项目的要求。</td>
</tr>
</table>

 [获取混合现实门户结果的帮助](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

## <a name="compatibility-guidelines"></a>兼容性指南
> [!IMPORTANT]
> 我们将更新，并将其添加到中，并可能会修改这些 Windows Mixed Reality PC 兼容性指南。 请定期查看以了解最新的指导原则和要求。

**HP 回音兼容规范**<br>
由于分辨率较高，以下要求适用于 HP 回音 G1 & G2 产品线，以确保最佳 90 Hz，并获得完整的分辨率体验： 

<ul>
<li> Intel Core i5，i7，Intel Xenon E3-1240 v5，等效或更好。 AMD Ryzen 5 等效或更好。 </li>
<li> NVIDIA GeForce GTX 1080、AMD Radeon RX 5700、等效或更好 </li> 
<li> 内存： 8 GB 或更大 RAM </li> 
<li> 1x 显示端口1。3 </li> 
<li> 1x USB 3.0 类型-C 与电源传送 (或随附的电源适配器) </li>
<li> Windows 10 可能会2019更新或更高版本 </li>
</ul>

**所有其他 WMR 兼容耳机** <br>
对于所有其他 HMDs，请参阅以下要求： 

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality 超 Pc</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality Pc</th>
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
    <td colspan="3" style="vertical-align: middle; text-align: center;">至少 10 GB</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">至少 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">图形卡</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul> 
            <li>NVIDIA GTX 1060 (或更高) DX12 的离散 GPU</li>
            <li>AMD RX 470/570 (或更高) 支持 DX12 的离散 GPU </li>
            </ul>     
            <b>注意：</b> GPU 必须托管在 PCIe 3.0 x4 + 链接槽中 </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>集成的 Intel HD Graphics 620 (或更高) 支持 DX12 的集成 GPU <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units"> (检查模型是否更高) </a></li>
        <li>NVIDIA MX150 (或更高) 离散 GPU</li>
        <li>Nvidia GeForce GTX 1050 离散 GPU</li>
        <li>Nvidia 965M 离散 GPU</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>注意：</b> 不支持较旧的 Intel Gpu，如 HD Graphics 4xx、5xx、2xxx、3xxx、4xxx、5xxx 和6xxx。
    </td>
</tr><tr>
    <td style="vertical-align: middle">图形驱动程序</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows 显示器驱动程序模型 (WDDM) 2。2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">图形显示端口</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2.0 或 DisplayPort 1。2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1.4 或 DisplayPort 1。2</td>
</tr><tr>
    <td style="vertical-align: middle">显示</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">连接的外部或集成 VGA (800x600) 显示 (或更好的) </td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">USB 连接</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 类型-A </td>
</tr><tr>
    <td style="vertical-align: middle"><a href="controllers-in-wmr.md">动作控制器</a>的蓝牙连接性 () </td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">蓝牙4。0</td>
</tr><tr>
    <td style="vertical-align: middle">预期头戴式帧速率</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">强力</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 (键入) 端口</td>
    <td style="vertical-align: middle; text-align: center;">USB 3.0 (键入) 端口</td>
</tr>
</table>



**其他信息：**
* 具有至少15个屏幕的更大的便携式计算机的效果最佳。
* 为获得最佳体验，我们建议使用第8代 Intel®核心™或第7代 intel® Core™ i5 处理器。
* 混合图形配置仅与 Windows Mixed Reality 兼容。 任何混合配置中的离散图形适配器都必须满足针对离散图形适配器的 Windows Mixed Reality 准则中列出的所有要求。
* 如果你有一个应运行 Windows Mixed Reality 的独立显卡，但默认为 60 Hz (每秒60帧数) 刷新率，请使用全尺寸 DisplayPort 到 HDMI 2.0 适配器，将耳机插入到你的耳机，启用 90 Hz 的刷新频率。
* 不同的耳机可能需要不同的硬件端口，因此请确保您的计算机具有正确的端口或 [必要的适配器](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) 以连接到您的耳机。

>[!NOTE]
>不符合最低确认规格的离散和集成图形硬件尚未针对 Windows Mixed Reality 进行测试、确认或优化，可能无法正常工作。

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality 和 Surface

若要在 Surface 设备上获得最佳的 Windows Mixed Reality 体验，建议使用 NVIDIA GeForce GTX 1060 GB 和 16 GB RAM 配置 SurfaceBook 2 (15 ") 。  此配置支持所有 Windows Mixed Reality 功能 @ 90 Hz，并对 Windows Mixed Reality 进行了测试和徽章。  Surface Book 2 (13 ") 、Surface Studio、Surface 膝上机和 Surface Pro (2017) 将在配置有 Intel Core i5 CPU 的情况下，支持一些 Windows Mixed Reality 功能， (或更好的) 和至少 8 GB 的 RAM。

**要求：**
* Surface products 需要驱动程序更新才能与 Windows Mixed Reality 兼容。 可以通过转到 " **设置" > 更新和安全 > 检查更新，** 将这些驱动程序安装在你的图面上。
* Surface 产品需要来自视频端口 (微型 DisplayPort 或 USB 的 [适配器](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) ，具体取决于 Surface PC) 到 HDMI 2.0 For Windows Mixed Reality 耳机。 最新版本的 Surface Mini-DisplayPort 到 HDMI AV 适配器与 HDMI 2.0 兼容 (不) 旧版本。 同样， <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB 到 Hdmi 适配器</a> 也与 hdmi 2.0 兼容。

>[!WARNING]
>并非所有微型 DisplayPort 或 USB 到 HDMI 适配器都支持 HDMI 2.0。 请考虑在任何适配器上检查显式 "HDMI 2.0" 兼容性或 "4K" 兼容性。

下表提供了有关与 Windows Mixed Reality 提供的表面兼容性的详细信息：

<table>
    <tr>
        <th> Surface 设备 </th><th> Windows Mixed Reality 功能支持？ </th><th> 建议配置 </th><th> 说明</th>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (原始) /Surface Pro 2 </td><td style="vertical-align: middle"> 无 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro 3 </td><td style="vertical-align: middle"> 无 </td><td> </td><td></td>
    </tr>
 (安装了 Windows 10 专业版)  <tr>
        <td style="vertical-align: middle"> Surface Pro 4 </td><td style="vertical-align: middle"> 无 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface 3 </td><td style="vertical-align: middle"> 无 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book </td><td style="vertical-align: middle"> 无 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> 具有性能基准的 Surface Book </td><td style="vertical-align: middle"> 无 </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Go </td><td style="vertical-align: middle"> 无 </td><td> </td><td></td>
    </tr>
<tr>
        <td style="vertical-align: middle"> Surface Book 2 (15 &quot;)  </td><td style="vertical-align: middle"> 完全 </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1060/16 GB 内存 </td>
        <td>
            <ul>
                <li><b>建议</b>：在 Surface 设备上获得最佳 Windows Mixed Reality 体验时，我们建议使用 NVIDIA GeForce GTX 1060 gb 和 16 gb RAM 配置 SurfaceBook 2 15。  此配置经过测试并徽章 Windows Mixed Reality，因此将支持所有 Windows Mixed Reality 功能，并允许你享受最大的兼容应用和游戏阵列。</li>
                <li>NVIDIA GeForce GTX 1060 离散 GPU 提供 Windows Mixed Reality 超高 @ 90-Hz 体验</li><br/>                <li>为了获得最佳性能，请使用为 Surface Book 2 发布的 Nvidia 图形驱动程序。 新版驱动程序可在 Nvidia&#39;的网站上提供，但未经测试。</li><br/>                <li>需要 <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB 到 HDMI 适配器</a> (其他适配器可能会正常运行，但未经测试) </li>
                <li><b>图面停靠上的注意</b>：由于外围设备的电源限制，Windows Mixed Reality 不支持将 surface dock 用于 surface Book 2。</li><br/>                <li><b>请注意，在 windows 10 版本1803上</b>：如果&#39;重新运行 Windows 10 版本1803，请确保&#39;在操作系统版本17134.137 或更高版本上通过 KB4284848) 安装 (，以确保具有最新的性能修复程序。 有关详细信息，请参阅 <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>的发行说明。</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book 2 (13.5 &quot;)  </td><td style="vertical-align: middle"> 部分 </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1050/16 GB 内存 </td>
        <td>
            <ul>
                <li><b>注意</b>： Surface Book 2 (13 ") 不适用于 Windows mixed reality，但将支持一些 Windows Mixed reality 功能，使你可以使用有限数量的兼容应用和游戏。  性能将取决于你的配置。</li>
                <li>使用 Intel Core i5/Intel HD Graphics 620 集成 GPU 的配置将提供 Windows Mixed Reality @ 60-Hz 体验</li>
                <li>使用 Intel Core i7/NVIDIA GeForce GTX 1050 离散 GPU 的配置将提供 Windows Mixed Reality @ 90-Hz 体验</li>                       <li>为了获得最佳性能，请使用为 Surface Book 2 发布的 Nvidia 图形驱动程序。 新版驱动程序可在 Nvidia&#39;的网站上提供，但未经测试。</li>
                <li>需要 <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">SURFACE USB 到 HDMI 适配器</a> (其他适配器可能会正常运行，但未经测试) </li>
                <li><b>图面停靠上的注意</b>：由于外围设备的电源限制，Windows Mixed Reality 不支持将 surface dock 用于 surface Book 2。</li>
                <li><b>请注意，在 windows 10 版本1803上</b>：如果&#39;重新运行 Windows 10 版本1803，请确保&#39;在操作系统版本17134.137 或更高版本上通过 KB4284848) 安装 (，以确保具有最新的性能修复程序。 有关详细信息，请参阅 <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>的发行说明。</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Studio </td><td style="vertical-align: middle"> 部分 </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GeForce GTX 980m/16 GB RAM </td>
        <td>
            <ul>
                <li><b>注意</b>： Surface Studio 不适用于 Windows mixed reality，但将支持一些 Windows Mixed reality 功能，使你可以使用有限数量的兼容应用和游戏。  性能将取决于你的配置。</li>
                <li>带有 NVIDIA GeForce GTX 965 m 的配置将提供 Windows Mixed Reality @ 60-Hz 体验。</li>
                <li>带有 NVIDIA GeForce GTX 980 m 的配置将提供 Windows Mixed Reality @ 90-Hz 体验。</li>
                <li>Surface 微型 DisplayPort 到 HDMI 2.0 适配器 (其他适配器可能运行，但未经测试) </li>
                <li>Windows Mixed Reality 耳机必须连接到带 "+" 符号的 USB 端口</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro (2017)  </td><td style="vertical-align: middle"> 部分 </td><td style="vertical-align: middle"> Intel Core i7/Intel® Iris™加上图形 640/16 GB 内存 </td>
        <td>
            <ul>
                <li><b>注意</b>： Surface Pro (2017) 不适用于 Windows mixed reality，但将支持一些 Windows Mixed reality 功能，使你可以使用有限数量的兼容应用和游戏。  性能将取决于你的配置。</li>
                <li><b>不支持</b>使用 Intel Core M3/Intel HD Graphics 615 集成 GPU 的配置</li>
                <li>使用 Intel Core i5/Intel HD Graphics 620 集成 GPU 的配置将提供 Windows Mixed Reality @ 60-Hz 体验</li>
                <li>带有 Intel Core i7/Intel® Iris™和图形640集成 GPU 的配置将提供 Windows Mixed Reality @ 60-Hz 体验</li><br/><li>需要 Surface 微型 DisplayPort 到 HDMI 2.0 适配器 (其他适配器可能运行，但未经测试) </li>
                <li>使用期间，需要将 <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">性能滑块</a> 设置为 "最佳性能"</li>
            </ul>
        </td>
    </tr><br/>    <tr>
        <td style="vertical-align: middle"> Surface Laptop </td><td style="vertical-align: middle"> 部分 </td><td style="vertical-align: middle"> Intel Core i7/Intel® Iris™加上图形 640/16 GB 内存 </td>
        <td>
            <ul>
                <li><b>注意</b>： Surface 膝上机并非徽章 Windows mixed reality，但将支持一些 Windows Mixed reality 功能，使你可以使用有限数量的兼容应用和游戏。  性能将取决于你的配置。</li>
                <li><b>不支持</b>使用 Intel Core M3/Intel HD Graphics 615 集成 GPU 的配置</li>
                <li>使用 Intel Core i5/Intel HD Graphics 620 集成 GPU 的配置将提供 Windows Mixed Reality @ 60-Hz 体验</li>
                <li>带有 Intel Core i7/Intel® Iris™和图形640集成 GPU 的配置将提供 Windows Mixed Reality @ 60-Hz 体验</li><br/><li>需要 Surface 微型 DisplayPort 到 HDMI 2.0 适配器 (其他适配器可能运行，但未经测试) </li>
                <li>使用期间，需要将 <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">性能滑块</a> 设置为 "最佳性能"</li>
            </ul>
        </td>
    </tr>
</table>

## <a name="see-also"></a>另请参阅
* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)
* [适用于 Windows Mixed Reality 的电脑的推荐适配器](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
