---
title: Windows Mixed RealityPC 检查应用
description: 如何在购买 Windows Mixed Reality 耳机之前查找并使用 Windows Mixed Reality pc 检查应用来测试 PC 的兼容性。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality，Mixed reality，虚拟现实，VR，先生，兼容，兼容性，PC，系统要求
appliesto:
- Windows 10
ms.openlocfilehash: 463e7dfc2c95ed9efc70a87ebbb0dac08b134251401a1114f3b9a364aa197073
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188038"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed RealityPC 检查应用

**[Windows Mixed Reality pc 检查](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** 应用是确保你的电脑准备好运行 Windows Mixed Reality 的最佳方式。 Windows Mixed Reality pc 检查应用仅适用于至少安装了 Windows 10 版本1607的电脑。 若要查看 Windows 的版本，请在搜索栏中键入 "winver"，并运行命令。 对于早于1607的 Windows 10 版本，应用仍会显示在存储中，但当你尝试安装时，会收到错误。

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

运行应用后，会收到以下消息之一：

* **准备好了。** 你的电脑 Windows Mixed Reality 运行所需要的。
* **就是这样。** 这台电脑可以 Windows Mixed Reality 运行，但某些功能可能会受到限制。
* **无法运行混合现实。** 这台电脑不满足 Windows Mixed Reality 运行所需的最低要求。

然后，将针对所需的硬件、驱动程序和操作系统分析你的 PC。
![Windows Mixed Reality PC 检查的屏幕截图](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>图标</th><th>含义</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">你的电脑传递所需的项目。</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">你的计算机可能存在特定要求的问题。 如果遇到任何问题，可能需要对 PC 进行故障排除或升级。</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">你的电脑不满足指定项目的要求。</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>获取 Windows Mixed Reality PC 检查结果的帮助

在计算机上设置 Windows Mixed Reality 或运行 Windows Mixed Reality PC 检查应用时，会收到兼容性报告。 下面是你可能会看到的一些详细信息。

### <a name="youre-good-to-go"></a>![准备就绪](images/glyph-succeeded.png)

好消息-你的电脑可以 Windows Mixed Reality 运行。 请记住，计算机硬件和配置之间仍有差异。 混合现实体验在每台电脑上可能不相同。

>[!NOTE]
>如果看到一条消息，指出 "此硬件配置可能与 Windows Mixed Reality 一起使用，但尚未对其进行测试，则在长时间运行 Windows Mixed Reality 时可能会遇到一些性能问题。

### <a name="youre-nearly-there"></a>![您差不多](images/glyph-warning.png)

你的电脑应能 Windows Mixed Reality 运行，但可能无法提供最佳体验。 图形可能会滞后，某些应用程序和游戏可能运行不正常，某些应用程序可能根本无法运行。

下面是你可能会看到的消息，以及如何处理它们：

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>这台电脑的集成显卡包含单声道 RAM

集成图形卡将在具有双通道 RAM 的 pc 上提供最佳 Windows Mixed Reality 体验。 如果遇到性能问题：

* 安装 [兼容的单独图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。
* 安装其他 RAM 杆以创建双通道 RAM。
* 切换到 [兼容的 PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)。

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>这台电脑的混合图形配置具有不兼容的 PCIe 链接

PCIe 代表 *外围组件互连 Express*。 这是电脑用来与图形卡通信的连接。 您的配置可能会正常运行，但如果遇到问题，则需要切换到兼容的 [PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)。

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>这台电脑的图形驱动程序可能无法正常工作 Windows Mixed Reality

如果遇到问题，请尝试使用 Windows 更新下载新的图形驱动程序 ("**启动 >" 设置 > "更新**&" > ") " "" 更新 "" 更新 "，或者访问电脑制造商或图形卡制造商的网站。

如果这不起作用，则需要添加兼容的 [图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 或切换到兼容的 [PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)。

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>这台电脑的处理器可能无法正常运行 Windows Mixed Reality

这台电脑的处理器可能无法与 Windows Mixed Reality 正常工作，因为它没有足够的核心。 如果 Windows Mixed Reality 不能正常运行，请更新为[兼容](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)的 PC 或切换到[兼容的 PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)。

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>这台电脑可能没有兼容的 USB 配置

如果遇到运行 Windows Mixed Reality 的问题：

* 将耳机插入到其他 USB 端口（如果可用）。
* 如果这不起作用，请卸载您的 PC 的当前 USB 驱动程序，然后重新安装 Microsoft 驱动程序：

1. 选择 " **开始**"，然后在搜索框中键入 **"设备管理器"** 。
1. 从结果中选择 " **Device Manager** "。
1. 展开 "通用串行总线控制器" 类别，查看列出的设备并卸载所有不兼容的驱动程序。 
 * 如果该列表在设备名称的末尾包含 "可扩展主机控制器" 项目而不包含 "Microsoft"，则驱动程序与 Windows Mixed Reality 不兼容。 需要将其卸载。 若要卸载某个驱动程序，请在列表中右键单击该设备，然后选择 " **卸载设备**"。 选中 " **删除此设备的驱动程序软件** " 复选框，然后选择 " **卸载**"。
 * 如果该列表包含名称中包含 "Etron" 的 "可扩展主机控制器" 项，该 USB 控制器与 Windows Mixed Reality 不兼容。 需要在电脑上使用不同的 USB 端口，或购买不同的 USB 3.0 主机控制器。
1. 重启你的电脑。 
1. 返回到 Device Manager 并再次查找可扩展的主机控制器项。 如果你现在在设备名称的末尾看到 "Microsoft"，你就可以开始了。 如果没有，请重复执行卸载步骤来删除任何其他非 Microsoft 驱动程序版本。
* 如果仍然不起作用，请将 PCIe USB 卡添加到 PC。

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>对于控制器，这台电脑没有4.0 蓝牙。

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>这台电脑没有自供电 USB 端口。

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>这台电脑应该可以正常工作，但您可以使用高性能的 Intel®处理器获得最佳体验。

### <a name="cant-run-mixed-reality"></a>![无法运行混合现实](images/glyph-error.png)

 [获取 Windows Mixed Reality PC 检查结果的帮助](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
