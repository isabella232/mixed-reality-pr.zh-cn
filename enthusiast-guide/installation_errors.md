---
title: 安装错误
description: 高级 Windows Mixed Reality 安装错误疑难解答，超出了标准使用者支持文档的范围。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，安装
appliesto:
- Windows 10
ms.openlocfilehash: 6837824346ce2390437daef0bc8eeab447f9e1f4
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677686"
---
# <a name="installation-errors"></a>安装错误

## <a name="your-pc-cant-run-windows-mixed-reality"></a>"你的电脑无法运行 Windows Mixed Reality"

你的电脑不满足运行 Windows Mixed Reality 所需的 [最低要求](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 。 这可能是因为计算机的硬件设置与 Windows Mixed Reality 不兼容，或者你需要 [更新到最新版本的 windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq)。 

请注意，Windows Mixed Reality 需要至少支持 WDDM 2.2 的图形卡驱动程序，因此请确保具有制造商提供的最新驱动程序更新。 如果 Windows Mixed Reality 安装程序显示您的图形卡无法满足要求，而您认为图形卡有问题，请确保将您的耳机插入正确的卡。

## <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"您差不多，这台电脑不满足运行 Windows Mixed Reality 所需的最低要求"

你的 PC 不满足 Windows Mixed Reality 中最佳体验所需的 [最低要求](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 。 你的电脑可能能够运行沉浸式耳机，但可能无法运行某些应用程序，或者可能存在性能问题。

请注意，Windows Mixed Reality 需要至少支持 WDDM 2.2 的图形卡驱动程序，因此请确保具有制造商提供的最新驱动程序更新。 如果 Windows Mixed Reality 安装程序显示您的图形卡无法满足要求，而您认为图形卡有问题，请确保将您的耳机插入正确的卡。

## <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"在可以设置 Windows Mixed Reality 之前，管理员将需要为你的组织启用它。 了解更多 "

你可能在使用企业托管网络，而你的组织正在使用 Windows Server Update Services (WSUS) 或具有可能会阻止下载的其他策略。 请联系组织的 IT 部门或系统管理员，以 [启用 Windows Mixed Reality](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable)。

## <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"我们无法下载混合现实软件" 或 "在我们进行一些下载时挂起"

* 有时挂起的更新可能会阻止混合现实软件下载。 请参阅 " **设置" > 更新 & 安全 > Windows 更新** ，并确保 Windows 更新已启用。 然后下载并安装任何等待更新。 如果收到 Windows 更新错误，请 [在此处](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)获取帮助。
* 请确保你的电脑已连接到 internet，并且至少有2GB 的可用存储空间。 检查网络状态： **设置 > 网络 & Internet > 状态** 。 如果无法连接到 internet，请 [在此处](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues)获取帮助。  
* 重启电脑，然后重试。 

如果这些解决方案不起作用，请尝试执行以下操作：
* 如果 Wi-fi 网络连接设置为 " [按流量计费](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq)"，请将其更改为 "不按流量"。 若要关闭按流量计费的连接，请转到： " **设置" > 网络 & Internet > 状态 > "更改连接属性" > 设置为按流量计费的连接** ，然后选择 "关闭"。  
* 如果最近安装了更新，则可能会导致问题。 建议您不要删除任何已安装的更新，尤其是安全更新，使您的 PC 保持安全，但有时删除最新的更新可帮助确定问题的根源。 要执行此操作： 
    * 请参阅 " **设置" > 更新 & 安全 > 查看已安装的更新历史记录 > 卸载更新**
    * 选择上次安装的更新，然后选择 "卸载"。
    * 出现 "是否确实要卸载此更新？" 提示时 回答 "是"。 如果在尝试执行这些步骤时收到错误，请转到 [此处](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors)。 
    * 重启电脑，然后重试。 
    * 如果 Windows Mixed Reality 安装正确，请在 "设置" **> Windows 更新 > 检查更新** ，并查看 Windows mixed reality 是否继续运行。 如果未正确安装，请重新安装更新，并与 Windows 支持部门联系。 

## <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"出现错误，无法启动 Windows Mixed Reality"
若要获取有关特定错误代码的详细信息，请查看 [此处](error-codes.md)。 你还可以尝试：

* 从电脑拔出耳机电缆。
* 重启电脑。
* 转到 " **设置" > 更新 & 安全 > Windows 更新** ，并确保已打开 "Windows 更新"。 下载并安装任何等待更新。
* 将耳机重新连接到电脑，然后重试安装。

如果这些步骤不起作用，请卸载并重新安装 Windows Mixed Reality：
* **> Mixed reality** 中转到 "设置" > 卸载，然后选择 "卸载"。 
* 重启你的电脑。 
* 若要再次开始安装过程，只需将耳机插入 PC 即可。
