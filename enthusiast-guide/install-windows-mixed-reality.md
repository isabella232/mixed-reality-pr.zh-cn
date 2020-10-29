---
title: 安装 Windows Mixed Reality 软件
description: 插入 Windows Mixed Reality 耳机后，请使用混合现实门户应用开始使用并下载 Windows Mixed Reality 功能。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，入门，安装，混合现实门户
appliesto:
- Windows 10
ms.openlocfilehash: 5e04f29f834b2220f51f1748aa59e4188d8ad38d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677763"
---
# <a name="install-windows-mixed-reality-software"></a>安装 Windows Mixed Reality 软件

## <a name="launch-mixed-reality-portal"></a>启动混合现实门户

插入 Windows Mixed Reality 耳机并成功安装驱动程序后，会在你的桌面上自动启动混合现实门户 (MRP) 。 如果此操作未自动发生，你始终可以从 "开始" 菜单启动 "混合现实门户" ( **> 混合现实门户) 启动** 。 启动门户后，单击 " **入门** "

![欢迎使用混合现实](images/1050px-mixedrealityportal.png)

在混合现实门户中，你可以：

* 在耳机中显示 livestream 的视图， (仅限超小型) 的 Windows Mixed Reality。 若要打开和关闭此功能，请选择 "停止预览" 或 "开始预览"。  (你还可以从 "混合现实开始" 菜单打开和关闭预览版。 ) 
* 查看耳机和控制器的状态。 选择 "菜单" 以查看所有信息。
* 设置新控制器。 选择 **菜单 > 设置控制器** 。
* 打开或关闭边界。 选择 **菜单 > "边界开/关"** 。  (如果将其关闭，则需要在一个位置保持安全。 ) 
* 创建新边界。 选择 **菜单 > 运行安装程序** 。
* 转到混合现实照片。 选择 **菜单 > 查看混合现实照片** 。
* 获取混合现实应用和游戏。 选择 **菜单 > 获取混合现实应用** 。

## <a name="download-windows-mixed-reality"></a>下载 Windows Mixed Reality

Windows Mixed Reality 大小约为1GB，下载时间取决于你的 internet 连接。 如果遇到 "我们无法下载混合现实软件" 的消息，请查看 [故障排除步骤](installation_errors.md#we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading)。

## <a name="general-troubleshooting"></a>常规故障排除

如果遇到问题或在使用混合现实门户时收到错误消息，请尝试这些解决方案。

**重启 Windows Mixed Reality**

1. 断开耳机与电脑的连接 (两个电缆) 。
2. 重新启动计算机，然后重新连接耳机。

**确保你的电脑能识别你的耳机**

如果重新启动不起作用，请确保电脑能够识别你的耳机。 选择 "开始"，在搜索框中键入 "设备管理器"，然后在列表中选择它。 展开 Mixed reality 设备，查看是否列出了你的耳机。 

如果未列出，请尝试以下操作：
* 将耳机插入电脑上的不同端口（如果可用）。
* 查看 [Windows 更新](https://support.microsoft.com/help/12373)中的最新软件更新。
* 卸载并重新安装 Windows Mixed Reality：
    1. 断开耳机与电脑的连接 (两个电缆) 。
    2. 选择 " **设置" > 混合现实 > 卸载** "。
    3. 取消配对运动控制器：选择 " **设置" > 设备 > 蓝牙 & 其他设备** 。 选择每个控制器，然后选择 " **删除设备** "。
    4. 若要重新安装 Windows Mixed Reality，请将你的耳机插回你的电脑。

## <a name="common-error-messages"></a>常见错误消息

下面是你可能会看到的 [错误消息](error-codes.md) 的一些注意事项。

| 如果看到此消息 | 尝试此操作 |
| --- | --- |
| 检查 USB 电缆 | 将耳机连接到不同的 USB 端口 (，并确保它是 SuperSpeed USB 3.0) 。 同时，尝试删除耳机与计算机之间的所有扩展器或集线器。 |
| 检查显示电缆 | 请尝试以下做法： <ul><li>将耳机连接到 DisplayPort 1.2 或更高版本，1.4 或者连接到或更高版本。 确保端口与电脑上最先进的图形卡相对应。</li><li>如果使用的是适配器，请确保它支持4K</li><li>尝试使用不同的 HDMI 端口</li><li>如果将外部监视器连接到 HDMI 端口，请尝试将其插入 DisplayPort，并将 HDMI 端口用于耳机</li></ul> |
| 出现问题 | 遵循上述一般故障排除步骤。 |

## <a name="review-and-accept-terms-and-conditions"></a>查看并接受条款和条件

若要继续安装，你的电脑上必须有2GB 可用空间。 查看并按 **我同意** 条款和条件继续操作

![接受条款和条件](images/1050px-mixedrealityportalpage2.png)

## <a name="compatibility-check"></a>兼容性检查

下一步是兼容的检查。 混合现实门户将进行检查，以确认你的电脑是否与混合现实兼容。 **绿色** 检查表示您的 PC 已通过所需的项目！ **橙色** 三角形表示你的计算机可能存在给定要求的问题。 如果遇到问题，可能需要对 PC 进行故障排除或升级。 **红色** X 表示您的 PC 不满足指定项目的要求。

![兼容检查](images/1050px-compatcheck.png)

## <a name="getting-ready"></a>做好准备

你将在屏幕上看到 "已准备好设置你" 的消息，并提供旋转图标。 这只需几分钟的时间：

![准备好设置](images/1050px-gettingsetup.png)

## <a name="see-also"></a>请参阅
* [询问社区](https://answers.microsoft.com)
* [联系我们以获取支持](https://support.microsoft.com/contactus/)
* [安装疑难解答](installation_errors.md)
* [安装疑难解答](set-up-questions.md)
* [设置 Windows Mixed Reality](set-up-windows-mixed-reality.md)
