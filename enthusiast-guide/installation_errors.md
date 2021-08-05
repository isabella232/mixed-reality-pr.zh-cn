---
title: 安装错误
description: 高级Windows Mixed Reality安装错误故障排除，超出了标准使用者支持文档。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 故障排除， 错误， 帮助， 支持， 安装
appliesto:
- Windows 10
ms.openlocfilehash: 702e38196ea3fda5cc7595decfeef4c6305ae2274ce6e5740af60c511447506b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213185"
---
# <a name="installation-errors"></a>安装错误

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"电脑无法运行Windows Mixed Reality"

电脑不满足运行[计算机所需的](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)最低Windows Mixed Reality。 计算机的硬件设置可能与 Windows Mixed Reality不兼容，或者可能需要更新到最新版本[的 Windows。](https://support.microsoft.com/help/12373/windows-update-faq) 

Windows Mixed Reality至少支持 WDDM 2.2 的图形卡驱动程序。 请确保获得制造商提供的最新驱动程序更新。 如果Windows Mixed Reality显示图形卡不符合要求，并且你认为它符合要求，请确保将头戴显示设备插入正确的卡中。

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"你近在万里-此电脑不满足运行此电脑所需的最低Windows Mixed Reality"

电脑不满足获得最佳[体验](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)所需的最低要求Windows Mixed Reality。 电脑可能能够运行沉浸式头戴显示设备，但可能会遇到性能问题，并且无法运行某些应用程序。

Windows Mixed Reality至少支持 WDDM 2.2 的图形卡驱动程序。 请确保获得制造商提供的最新驱动程序更新。 如果Windows Mixed Reality显示图形卡不符合要求，并且你认为它符合要求，请确保将头戴显示设备插入正确的卡中。

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"在设置Windows Mixed Reality之前，管理员需要为组织启用它。 了解更多"

你可能位于企业托管网络上，并且你的组织正在使用 WSUS Windows Server Update Services (WSUS) 。 可能会阻止下载的这些策略和其他策略。 请联系组织的 IT 部门或系统管理员以[启用Windows Mixed Reality。](/windows/application-management/manage-windows-mixed-reality#enable)

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"我们无法下载混合现实软件"或"执行一些下载时挂起"

* 有时，挂起的更新可能会阻止混合现实软件下载。 转到 **"设置 >更新&安全性> Windows更新"，Windows** 更新已打开。 然后下载并安装任何正在等待的更新。 如果收到"更新Windows，请在此处[获取帮助](https://support.microsoft.com/help/10164/fix-windows-update-errors)。
* 确保电脑已连接到 Internet，并且至少有 2 GB 的可用存储空间。 检查网络状态，位置：设置 >**网络& Internet >状态**。 如果无法连接到 Internet，请在此处 [获取帮助](https://support.microsoft.com/help/10741/windows-10-fix-network-connection-issues)。  
* 重启电脑，然后重试。 

如果这些解决方案不起作用，请尝试：
* 如果Wi-Fi网络连接设置为按流量 [计费](https://support.microsoft.com//help/17452/windows-metered-internet-connections-faq)，请更改为"未计量"。 若要关闭按流量计费的连接，请转到：设置 > **Network & Internet** > Status > 将连接属性>设置为按流量计费的连接，然后选择"关闭"。  
* 如果最近安装了更新，则可能会导致问题。 建议不要删除任何已安装的更新，尤其是保护电脑安全的安全更新。 但是，有时删除最新更新可以帮助确定问题的原因： 
    * 转到 **"设置 >更新&安全性>查看已安装的更新历史记录>卸载更新**
    * 选择安装的最后一个更新，然后选择"卸载"。
    * 当系统提示"确定是否要卸载此更新？" 回答"是"。 如果在尝试这些步骤时收到错误，请获取有关如何解决 [Windows 更新错误的更多详细信息](https://support.microsoft.com//help/10164/fix-windows-update-errors)。 
    * 重启电脑，然后重试。 
    * 如果Windows Mixed Reality正确安装，请在"更新设置 > Windows下重新安装>**检查** 更新，并查看Windows Mixed Reality是否继续工作。 如果未正确安装，请重新安装更新，并联系Windows支持人员。 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"出现问题，无法开始Windows Mixed Reality"
若要获取有关特定错误代码的详细信息，请参阅 [此处](error-codes.md)。 还可以尝试：

* 从电脑拔下两根头戴显示设备电缆。
* 重启电脑。
* 转到 **设置 >更新&更新> Windows，** 并确保Windows更新" 。 下载并安装任何正在等待的更新。
* 将头戴显示设备重新连接到电脑，然后重试设置。

如果这些步骤不起作用，请卸载并重新安装Windows Mixed Reality：
* 转到 **"设置 >混合现实>"，** 然后选择"卸载"。 
* 重启你的电脑。 
* 若要再次启动安装过程，只需将头戴显示设备插入电脑。