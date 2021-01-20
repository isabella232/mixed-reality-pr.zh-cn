---
title: 分发应用程序
description: 针对各种受支持的平台和发布存储区的不同分发选项的概述。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens，混合现实，沉浸式耳机，应用，uwp，提交，提交，筛选器，元数据，系统要求，关键字，wack，证书，包，appx，销售情况
ms.openlocfilehash: eb06ff46be6fbe6e480f9b43fa7f23ee47982192
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582857"
---
# <a name="distributing-your-apps"></a>分发应用程序

![WMR 主页中的 Floaty 鸟3D 应用 lancher](images/distribute-hero-image.png)

将你的应用程序交给你的用户或在世界中，这是一项开发工作的最重要的 painstaking。 我们已将该过程简化为一组资源，这些资源依赖于最适合你或你的团队的分发和部署方案。

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>分布选项

> [!IMPORTANT]
> * 如果你要与另一方共享你的应用，则需要构建并提供 appx 文件。 
>     * 如果使用的是应用程序安装程序，还需要与用户共享证书。
> 
> * 如果与组织共享，则需要使用工作或学校帐户，并访问组织的 [MDM (移动设备管理) ](/hololens/hololens-enroll-mdm) 基础结构。  
>    * 如果你是共享参与方，则需要是租户中的管理员，并使用 [Microsoft 终结点管理器管理中心](/mem/intune/apps/apps-deploy) 使应用程序可用。 另一种方法是与最终用户共享 appx 文件和应用程序依赖项。
>    * 如果你是最终用户，则在你向共享组织的租户注册后，应用将自动下载或可供下载。 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>方案</strong></td>
    <td><strong>本地设备安装</strong></td>
    <td><strong>与任何人共享</strong></td>
    <td><strong>与组织共享</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>应用安装程序</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-app-installer"><strong>MDM-公司门户</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-intune"><strong>MDM-必需的应用安装</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-store-business"><strong>适用于企业的 Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="/hololens/app-deploy-provisioning-package"><strong>预配包</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="#other-scenarios"><strong>自定义 Win32 部署</strong></a> (不适用于 HoloLens 设备-请参阅下面的) </td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> 应用安装程序当前不可用于托管设备或 HoloLens (第一代) 设备。

## <a name="other-scenarios"></a>其他方案

* 您可以生成一个 Win32。用于 Win32 应用程序部署的基于 Unity 的 PC 独立生成目标的 EXE 文件，包括流和游戏通过。 获得。EXE，你可以将应用程序正常提交到所选平台。 

* 如果你需要在离线时安装 HoloLens 2 应用程序，请参阅 [脱机安全 HoloLens 2](/hololens/hololens-common-scenarios-offline-secure) 说明或通过预配包安装应用，而无需启用开发人员模式。

* 你还可以将生成部署到设备，并将其与通过 [使用 Visual Studio 部署和调试](../develop/platform-capabilities-and-apis/using-visual-studio.md) 或 [使用设备门户安装应用程序包](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications)来启用开发人员模式的其他开发人员共享。

## <a name="see-also"></a>另请参阅
* [从 Microsoft Store 查找、安装和卸载应用程序](/hololens/holographic-store-apps)