---
title: Windows Mixed Reality PC 检查应用
description: 在购买 Windows Mixed Reality 耳机之前，如何查找并使用 Windows Mixed Reality PC 检查应用来测试 PC 的兼容性。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，兼容，兼容性，PC，系统要求
appliesto:
- Windows 10
ms.openlocfilehash: 5cf84768984691c253a557f6576685e89fb61078
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677239"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality PC 检查应用

**[Windows Mixed REALITY PC 检查](windows-mixed-reality-pc-check-app.md)** 应用是确保您的 PC 准备好运行 Windows mixed reality 的最佳方式。 

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

运行应用后，会收到以下消息之一：
* **准备好了。** 你的电脑具有运行 Windows Mixed Reality 所需要的功能。
* **就是这样。** 这台电脑或许能够运行 Windows Mixed Reality，但某些功能可能会受到限制。
* **无法运行混合现实。** 这台电脑不满足运行 Windows Mixed Reality 所需的最低要求。

然后，你将针对所需的硬件、驱动程序和操作系统分析你的 PC。
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

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>获取有关 Windows Mixed Reality PC 检查结果的帮助

当你在计算机上设置 Windows Mixed Reality 或运行 Windows Mixed Reality PC 检查应用时，你会收到一份报告，指出你的电脑是否已准备好运行。 下面是你可能会看到的一些详细信息。 

### <a name="youre-good-to-go"></a>![准备就绪](images/glyph-succeeded.png)

好消息-你的电脑可以运行 Windows Mixed Reality。 但请记住，计算机硬件和配置之间仍存在差异，因此每台电脑上的混合现实体验可能不相同。 

>[!NOTE]
>如果看到一条消息，指出： "此硬件配置可能与 Windows Mixed Reality 一起工作，但尚未对其进行测试"，则在长时间运行 Windows Mixed Reality 时可能会遇到一些性能问题。


### <a name="youre-nearly-there"></a>![您差不多](images/glyph-warning.png)

你的电脑应能够运行 Windows Mixed Reality，但可能无法提供最佳体验。 图形可能会滞后，某些应用程序和游戏可能性能不佳，并且某些应用程序可能根本无法运行。 

下面是你可能会看到的消息，以及如何处理它们：

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>这台电脑的集成显卡包含单声道 RAM。

集成图形卡将在具有双通道 RAM 的 Pc 上提供最佳的 Windows Mixed Reality 体验。 如果遇到性能问题，请尝试以下操作之一：

* 安装 [兼容的单独图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)。
* 安装其他 RAM 杆以创建双通道 RAM。 
* 切换到 [兼容的 PC](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices)。

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>这台电脑的混合图形配置具有不兼容的 PCIe 链接。

PCIe 代表 *外围组件互连 Express* 。 这是电脑用来与图形卡通信的连接。 您的配置可能会正常运行，但如果遇到问题，则需要切换到兼容的 [PC](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices)。

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>对于 Windows Mixed Reality，这台电脑的图形驱动程序可能无法正常工作。

如果遇到问题，请尝试使用 Windows 更新下载新的图形驱动程序 ( **启动 > 设置 > 更新 & 安全 > 检查更新** ) ，或访问电脑制造商或图形卡制造商的网站。 

如果这不起作用，则需要添加兼容的 [图形卡](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 或切换到兼容的 [PC](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices)。

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>这台电脑的处理器可能无法与 Windows Mixed Reality 很好地配合工作。

这台电脑的处理器可能无法与 Windows Mixed Reality 很好地配合工作，因为它没有足够的核心。 如果 Windows Mixed Reality 运行不正常，请将处理器替换为 [兼容](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 的处理器，或切换到 [兼容的 PC](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices)。

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>这台电脑可能没有兼容的 USB 配置。

如果遇到运行 Windows Mixed Reality 的问题，请尝试以下操作：
* 将耳机插入到其他 USB 端口（如果可用）。
* 如果这不起作用，请卸载您的 PC 的当前 USB 驱动程序，然后重新安装 Microsoft 驱动程序：
1. 选择 " **开始** "，然后在搜索框中键入 **"设备管理器"** 。
1. 从结果中选择 " **设备管理器** "。
1. 展开 "通用串行总线控制器" 类别，查看列出的设备并卸载所有不兼容的驱动程序。 
 * 如果该列表包含的 "可扩展主机控制器" 项在设备名称的末尾没有 "Microsoft"，则该驱动程序与 Windows Mixed Reality 不兼容。 需要将其卸载。 若要卸载某个驱动程序，请在列表中右键单击该设备，然后选择 " **卸载设备** "。 选中 " **删除此设备的驱动程序软件** " 复选框，然后选择 " **卸载** "。
 * 如果该列表包含名称中包含 "Etron" 的 "可扩展主机控制器" 项，该 USB 控制器与 Windows Mixed Reality 不兼容。 需要在电脑上使用不同的 USB 端口，或购买不同的 USB 3.0 主机控制器。
1. 重启你的电脑。 
1. 返回到设备管理器并再次查找可扩展的主机控制器项。 如果你现在在设备名称的末尾看到 "Microsoft"，你就可以开始了。 如果没有，请重复执行卸载步骤来删除任何其他非 Microsoft 驱动程序版本。
* 如果仍然不起作用，请将 PCIe USB 卡添加到 PC。

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>这台电脑没有适用于控制器的蓝牙4.0。

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>这台电脑没有自供电 USB 端口。

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>这台电脑应该可以正常工作，但您可以使用高性能的 Intel®处理器获得最佳体验。

### <a name="cant-run-mixed-reality"></a>![无法运行混合现实](images/glyph-error.png)

 [获取有关 Windows Mixed Reality PC 检查结果的帮助](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
