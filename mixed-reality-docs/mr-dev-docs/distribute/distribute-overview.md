---
title: 分发应用程序
description: 针对各种受支持的平台和发布存储区的不同分发选项的概述。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens，混合现实，沉浸式耳机，应用，uwp，提交，提交，筛选器，元数据，系统要求，关键字，wack，证书，包，appx，销售情况
ms.openlocfilehash: 5c7a1d6e00610a4046bd71b07ca5184399c9e335
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925773"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="e15f9-104">分发应用程序</span><span class="sxs-lookup"><span data-stu-id="e15f9-104">Distributing your apps</span></span>

![WMR 主页中的 Floaty 鸟3D 应用 lancher](images/distribute-hero-image.png)

<span data-ttu-id="e15f9-106">将你的应用程序交给你的用户或在世界中，这是一项开发工作的最重要的 painstaking。</span><span class="sxs-lookup"><span data-stu-id="e15f9-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="e15f9-107">我们简化了下面列出的一组资源的过程，所有这些资源都依赖于最适合你或你的团队的分发和部署方案。</span><span class="sxs-lookup"><span data-stu-id="e15f9-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="e15f9-108">分布选项</span><span class="sxs-lookup"><span data-stu-id="e15f9-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="e15f9-109">如果你要与另一方共享你的应用，则需要构建并提供 appx 文件。</span><span class="sxs-lookup"><span data-stu-id="e15f9-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="e15f9-110">如果使用的是应用程序安装程序，还需要与用户共享证书。</span><span class="sxs-lookup"><span data-stu-id="e15f9-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="e15f9-111">如果与组织共享，则需要使用工作或学校帐户，并访问组织的 [MDM (移动设备管理) ](https://docs.microsoft.com/hololens/hololens-enroll-mdm) 基础结构。</span><span class="sxs-lookup"><span data-stu-id="e15f9-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="e15f9-112">如果你是共享参与方，则需要是租户中的管理员，并使用 [Microsoft 终结点管理器管理中心](https://docs.microsoft.com/mem/intune/apps/apps-deploy) 使应用程序可用。</span><span class="sxs-lookup"><span data-stu-id="e15f9-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="e15f9-113">另一种方法是与最终用户共享 appx 文件和应用程序依赖项。</span><span class="sxs-lookup"><span data-stu-id="e15f9-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="e15f9-114">如果你是最终用户，则在你向共享组织的租户注册后，应用将自动下载或可供下载。</span><span class="sxs-lookup"><span data-stu-id="e15f9-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="e15f9-115"><strong>方案</strong></span><span class="sxs-lookup"><span data-stu-id="e15f9-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="e15f9-116"><strong>本地设备安装</strong></span><span class="sxs-lookup"><span data-stu-id="e15f9-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="e15f9-117"><strong>与任何人共享</strong></span><span class="sxs-lookup"><span data-stu-id="e15f9-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="e15f9-118"><strong>与组织共享</strong></span><span class="sxs-lookup"><span data-stu-id="e15f9-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e15f9-119">通过<a href="https://docs.microsoft.com/hololens/hololens-insider">Windows 内幕构建</a> (<a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>应用安装程序</strong></a>) </span><span class="sxs-lookup"><span data-stu-id="e15f9-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></a> (through <a href="https://docs.microsoft.com/hololens/hololens-insider">Windows Insider builds</a>)</span></span></td>
    <td><span data-ttu-id="e15f9-120">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-120">✔️</span></span></td>
    <td><span data-ttu-id="e15f9-121">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="e15f9-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-公司门户</strong></a></span><span class="sxs-lookup"><span data-stu-id="e15f9-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="e15f9-123">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e15f9-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-必需的应用安装</strong></a></span><span class="sxs-lookup"><span data-stu-id="e15f9-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="e15f9-125">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e15f9-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="e15f9-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="e15f9-127">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-127">✔️</span></span></td>
    <td><span data-ttu-id="e15f9-128">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e15f9-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>适用于企业的 Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="e15f9-129"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="e15f9-130">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e15f9-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>预配包</strong></a></span><span class="sxs-lookup"><span data-stu-id="e15f9-131"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="e15f9-132">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-132">✔️</span></span></td>
    <td><span data-ttu-id="e15f9-133">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-133">✔️</span></span></td>
    <td><span data-ttu-id="e15f9-134">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="e15f9-135"><a href="#additional-scenarios"><strong>自定义 Win32 部署</strong></a> (不适用于 HoloLens 设备-请参阅下面的) </span><span class="sxs-lookup"><span data-stu-id="e15f9-135"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="e15f9-136">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-136">✔️</span></span></td>
    <td><span data-ttu-id="e15f9-137">✔️</span><span class="sxs-lookup"><span data-stu-id="e15f9-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="e15f9-138">应用安装程序当前不可用于托管设备或 HoloLens (第一代) 设备。</span><span class="sxs-lookup"><span data-stu-id="e15f9-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="e15f9-139">其他方案</span><span class="sxs-lookup"><span data-stu-id="e15f9-139">Additional scenarios</span></span>

* <span data-ttu-id="e15f9-140">对于 Win32 应用程序部署，包括流和游戏通过，您可以生成一个 Win32。EXE 文件，使用 Unity 中的 PC 独立生成目标并将应用程序正常提交到所选平台。</span><span class="sxs-lookup"><span data-stu-id="e15f9-140">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="e15f9-141">如果你需要在离线时安装 HoloLens 2 应用程序，请参阅 [脱机安全 HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) 说明或通过预配包安装应用，而无需启用开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="e15f9-141">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="e15f9-142">你还可以将生成部署到设备，并将其与通过 [使用 Visual Studio 部署和调试](../develop/platform-capabilities-and-apis/using-visual-studio.md) 或 [使用设备门户安装应用程序包](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal)来启用开发人员模式的其他开发人员共享。</span><span class="sxs-lookup"><span data-stu-id="e15f9-142">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="e15f9-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e15f9-143">See also</span></span>
* [<span data-ttu-id="e15f9-144">从 Microsoft Store 查找、安装和卸载应用程序</span><span class="sxs-lookup"><span data-stu-id="e15f9-144">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

<!-- ## Submitting to the Microsoft Store

You've finally made it to the last step on your distribution journey, actually getting your app into the Microsoft Store! Our [submission guidelines](submitting-an-app-to-the-microsoft-store.md) article will take you through: 

* Partner Center registration 
* Asset preparation
* App packaging
* Testing
* Final submission process

You can even give out free trials to get future consumers excited about your new immersive experience. Once your app is listed on the Microsoft Store you can sit back, engage with your expanding user community, and think about all the new features you want to add! -->
