---
title: 安装 Windows Mixed Reality 软件
description: 插入头戴显示设备Windows Mixed Reality，使用 混合现实门户 应用开始并下载Windows Mixed Reality功能。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 入门， 设置， 混合现实门户
appliesto:
- Windows 10
ms.openlocfilehash: 1ac7ab79b6d28a44636fc16859456eb7af329a215e2d6718d0190b86281d0b67
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186931"
---
# <a name="install-windows-mixed-reality-software"></a>安装 Windows Mixed Reality 软件

> [!div class="nextstepaction"]
> [获取混合现实门户](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab)

## <a name="launch-mixed-reality-portal"></a>启动混合现实门户

将头戴显示设备Windows Mixed Reality驱动程序成功安装后，混合现实门户 (MRP) 会自动在桌面上启动。 如果门户未启动，始终可以从"开始"或"开始"打开混合 **现实> 混合现实门户。** 门户启动后，选择 **"入门**

![欢迎使用混合现实](images/1050px-mixedrealityportal.png)

在混合现实门户中，可以：

* 选择"停止预览"或 (Windows Mixed Reality Ultra预览) 在头戴显示设备中显示视图的实时流。 还可以从混合现实应用启用和关闭"开始"菜单。
* 查看头戴显示设备和控制器的状态。 选择"菜单"以查看所有信息。
* 设置新控制器。 选择 **"菜单>设置控制器"。**
* 打开或关闭边界。 选择 **"菜单>边界打开/关闭"。**  (如果将其关闭，则需要在一个位置保持安全。) 
* 创建新边界。 选择 **"菜单>运行安装程序"。**
* 访问混合现实照片。 选择 **"菜单>查看混合现实照片"。**
* 获取混合现实应用和游戏。 选择 **"菜单>获取混合现实应用"。**

## <a name="download-windows-mixed-reality"></a>下载Windows Mixed Reality

Windows Mixed Reality大小为 1 GB，下载时间因 Internet 连接而异。 如果收到一条显示"无法下载混合现实软件"的消息，请看这些 [故障排除步骤](installation_errors.md#we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading)。

## <a name="general-troubleshooting"></a>常规故障排除

如果在使用解决方案时遇到问题或收到混合现实门户，请尝试这些解决方案。

**重启Windows Mixed Reality**

1. 将头戴显示设备与电脑断开连接 (两根电缆) 。
2. 重启电脑，然后重新连接头戴显示设备。

**确保电脑可识别头戴显示设备**

如果重启不起作用，请确保电脑已识别头戴显示设备。 选择"开始"，在搜索框中键入设备管理器，然后在列表中选择它。 展开"混合现实设备"，查看是否列出了头戴显示设备。

如果未列出，请尝试以下操作：

* 将头戴显示设备插入电脑上的不同端口（如果可用）。
* 检查更新 中Windows[软件更新](https://support.microsoft.com/help/12373)。
* 卸载并重新安装Windows Mixed Reality：
    1. 将头戴显示设备与电脑断开连接 (两根电缆) 。
    2. 选择 **"设置 >混合现实>卸载"。**
    3. 将运动控制器配对：选择 **"设置 >设备> 蓝牙 &设备"。** 选择每个控制器，然后选择"**删除设备"。**
    4. 若要重新安装Windows Mixed Reality，请将头戴显示设备插入电脑。

## <a name="common-error-messages"></a>常见错误消息

下面是尝试查看错误消息 [的](error-codes.md) 一些操作。

| 如果看到此消息 | 尝试此服务 |
| --- | --- |
| 检查 USB 电缆 | 连接头戴显示设备连接到不同的 USB 端口 (并确保它是超速 USB 3.0) 。 此外，请尝试删除头戴显示设备与计算机之间的任何扩展程序或集线器。 |
| 检查显示电缆 | 请尝试以下步骤： <ul><li>连接头戴显示设备连接到 DisplayPort 1.2 或更高版本，或将头戴显示设备连接到 1.4 或更高版本。 请确保端口与电脑上的最先进的图形卡相对应。</li><li>如果使用的是适配器，请确保其支持 4K</li><li>尝试使用另一个MIDMI 端口</li><li>如果已将外部监视器插入了一个适用于该端口的外部监视器，请尝试改为将其插入 DisplayPort，然后使用头戴显示设备使用的适用于你的头戴显示设备</li></ul> |
| 出现问题 | 按照上述常规故障排除步骤操作。 |

## <a name="review-and-accept-terms-and-conditions"></a>查看并接受条款和条件

若要继续安装，电脑上必须有 2 GB 的可用空间。 查看并 **按"我同意** 条款和条件"继续

![接受条款和条件](images/1050px-mixedrealityportalpage2.png)

## <a name="compatibility-check"></a>兼容性检查

接下来是兼容的检查。 混合现实门户检查以确认电脑与混合现实兼容。 **绿色** 检查表示电脑通过了所需的项！ **橙色** 三角形表示根据给定的要求，电脑可能有问题。 如果发现任何问题，可能需要对电脑进行故障排除或升级。 **红色** X 表示电脑不满足指定项的要求。

![Compat 检查](images/1050px-compatcheck.png)

## <a name="getting-ready"></a>做好准备

屏幕上会显示一条"正在准备设置"消息，其中显示旋转图标，只需几分钟时间：

![准备设置](images/1050px-gettingsetup.png)

## <a name="see-also"></a>另请参阅

* [询问社区](https://answers.microsoft.com)
* [联系我们获得支持](https://support.microsoft.com/contactus/)
* [安装疑难解答](installation_errors.md)
* [安装程序疑难解答](wmr-setup-faq.yml)
* [设置 Windows Mixed Reality](set-up-windows-mixed-reality.md)
