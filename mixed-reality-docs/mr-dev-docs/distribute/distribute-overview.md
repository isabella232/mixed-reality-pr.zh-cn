---
title: 分发应用程序
description: 针对各种受支持的平台和发布存储区的不同分发选项的概述。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens，混合现实，沉浸式耳机，应用，uwp，提交，提交，筛选器，元数据，系统要求，关键字，wack，证书，包，appx，销售情况
ms.openlocfilehash: b4b82557ba274852ebb3f97058017fa2e5db1c02
ms.sourcegitcommit: 9e9d58de4513655c7daa71ff4b5b2c2b115ab959
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97034578"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="c91ac-104">分发应用程序</span><span class="sxs-lookup"><span data-stu-id="c91ac-104">Distributing your apps</span></span>

![WMR 主页中的 Floaty 鸟3D 应用 lancher](images/distribute-hero-image.png)

<span data-ttu-id="c91ac-106">将你的应用程序交给你的用户或在世界中，这是一项开发工作的最重要的 painstaking。</span><span class="sxs-lookup"><span data-stu-id="c91ac-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="c91ac-107">我们简化了下面列出的一组资源的过程，所有这些资源都依赖于最适合你或你的团队的分发和部署方案。</span><span class="sxs-lookup"><span data-stu-id="c91ac-107">We've simplified process into a set of resources listed below, all of which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="c91ac-108">分布选项</span><span class="sxs-lookup"><span data-stu-id="c91ac-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="c91ac-109">如果你要与另一方共享你的应用，则需要构建并提供 appx 文件。</span><span class="sxs-lookup"><span data-stu-id="c91ac-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="c91ac-110">如果使用的是应用程序安装程序，还需要与用户共享证书。</span><span class="sxs-lookup"><span data-stu-id="c91ac-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="c91ac-111">如果与组织共享，则需要使用工作或学校帐户，并访问组织的 [MDM (移动设备管理) ](https://docs.microsoft.com/hololens/hololens-enroll-mdm) 基础结构。</span><span class="sxs-lookup"><span data-stu-id="c91ac-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](https://docs.microsoft.com/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="c91ac-112">如果你是共享参与方，则需要是租户中的管理员，并使用 [Microsoft 终结点管理器管理中心](https://docs.microsoft.com/mem/intune/apps/apps-deploy) 使应用程序可用。</span><span class="sxs-lookup"><span data-stu-id="c91ac-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](https://docs.microsoft.com/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="c91ac-113">另一种方法是与最终用户共享 appx 文件和应用程序依赖项。</span><span class="sxs-lookup"><span data-stu-id="c91ac-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="c91ac-114">如果你是最终用户，则在你向共享组织的租户注册后，应用将自动下载或可供下载。</span><span class="sxs-lookup"><span data-stu-id="c91ac-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="c91ac-115"><strong>方案</strong></span><span class="sxs-lookup"><span data-stu-id="c91ac-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="c91ac-116"><strong>本地设备安装</strong></span><span class="sxs-lookup"><span data-stu-id="c91ac-116"><strong>Local device install</strong></span></span></td>
    <td><span data-ttu-id="c91ac-117"><strong>与任何人共享</strong></span><span class="sxs-lookup"><span data-stu-id="c91ac-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="c91ac-118"><strong>与组织共享</strong></span><span class="sxs-lookup"><span data-stu-id="c91ac-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c91ac-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>应用安装程序</strong></span><span class="sxs-lookup"><span data-stu-id="c91ac-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="c91ac-120">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-120">✔️</span></span></td>
    <td><span data-ttu-id="c91ac-121">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="c91ac-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-公司门户</strong></a></span><span class="sxs-lookup"><span data-stu-id="c91ac-122"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="c91ac-123">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c91ac-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-必需的应用安装</strong></a></span><span class="sxs-lookup"><span data-stu-id="c91ac-124"><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="c91ac-125">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c91ac-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="c91ac-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="c91ac-127">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-127">✔️</span></span></td>
    <td><span data-ttu-id="c91ac-128">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-128">✔️</span></span></td><span data-ttu-id="c91ac-129">s</span><span class="sxs-lookup"><span data-stu-id="c91ac-129">s</span></span>
</tr>
<tr>
    <td><span data-ttu-id="c91ac-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>适用于企业的 Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="c91ac-130"><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="c91ac-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-131">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c91ac-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>预配包</strong></a></span><span class="sxs-lookup"><span data-stu-id="c91ac-132"><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="c91ac-133">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-133">✔️</span></span></td>
    <td><span data-ttu-id="c91ac-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-134">✔️</span></span></td>
    <td><span data-ttu-id="c91ac-135">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-135">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="c91ac-136"><a href="#additional-scenarios"><strong>自定义 Win32 部署</strong></a> (不适用于 HoloLens 设备-请参阅下面的) </span><span class="sxs-lookup"><span data-stu-id="c91ac-136"><a href="#additional-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="c91ac-137">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-137">✔️</span></span></td>
    <td><span data-ttu-id="c91ac-138">✔️</span><span class="sxs-lookup"><span data-stu-id="c91ac-138">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="c91ac-139">应用安装程序当前不可用于托管设备或 HoloLens (第一代) 设备。</span><span class="sxs-lookup"><span data-stu-id="c91ac-139">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="additional-scenarios"></a><span data-ttu-id="c91ac-140">其他方案</span><span class="sxs-lookup"><span data-stu-id="c91ac-140">Additional scenarios</span></span>

* <span data-ttu-id="c91ac-141">对于 Win32 应用程序部署，包括流和游戏通过，您可以生成一个 Win32。EXE 文件，使用 Unity 中的 PC 独立生成目标并将应用程序正常提交到所选平台。</span><span class="sxs-lookup"><span data-stu-id="c91ac-141">For Win32 application deployment, including Steam and Game Pass, you can produce a Win32 .EXE file using the PC Standalone build target from Unity and submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="c91ac-142">如果你需要在离线时安装 HoloLens 2 应用程序，请参阅 [脱机安全 HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) 说明或通过预配包安装应用，而无需启用开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="c91ac-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) instructions or instal the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="c91ac-143">你还可以将生成部署到设备，并将其与通过 [使用 Visual Studio 部署和调试](../develop/platform-capabilities-and-apis/using-visual-studio.md) 或 [使用设备门户安装应用程序包](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal)来启用开发人员模式的其他开发人员共享。</span><span class="sxs-lookup"><span data-stu-id="c91ac-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](https://docs.microsoft.com/hololens/holographic-custom-apps#installing-an-application-package-with-the-device-portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="c91ac-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c91ac-144">See also</span></span>
* [<span data-ttu-id="c91ac-145">从 Microsoft Store 查找、安装和卸载应用程序</span><span class="sxs-lookup"><span data-stu-id="c91ac-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](https://docs.microsoft.com/hololens/holographic-store-apps)

