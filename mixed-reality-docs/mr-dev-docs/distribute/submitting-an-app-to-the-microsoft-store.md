---
title: 将应用提交到 Microsoft Store
description: 探讨将混合现实应用打包、测试和提交到 Microsoft Store 的过程。
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store，HoloLens，沉浸式耳机，应用，uwp，提交，提交，筛选器，元数据，系统要求，关键字，wack，证书，包，appx，销售，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 7b1953fe0244b06f019f0e28432b7f9be9c21081
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98031973"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a><span data-ttu-id="1ec5c-104">将应用提交到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="1ec5c-104">Submitting an app to the Microsoft Store</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ec5c-105">如果要提交 Unreal 应用程序，请确保在继续操作之前遵循 **[发布说明](../develop/unreal/unreal-publishing-to-store.md)** 。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-105">If you're submitting an Unreal application, make sure you follow the **[publishing instructions](../develop/unreal/unreal-publishing-to-store.md)** before continuing.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ec5c-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="1ec5c-106">Prerequisites</span></span>

<span data-ttu-id="1ec5c-107">[HoloLens](../hololens-hardware-details.md)和 WINDOWS 10 PC 均支持[沉浸式耳机](../discover/immersive-headset-hardware-details.md)运行通用 Windows 平台应用。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-107">Both [HoloLens](../hololens-hardware-details.md) and the Windows 10 PC powering your [immersive headset](../discover/immersive-headset-hardware-details.md) run Universal Windows Platform apps.</span></span> <span data-ttu-id="1ec5c-108">无论是提交支持 HoloLens、PC 还是同时提交这两种应用，都可以通过 [合作伙伴中心](https://partner.microsoft.com/dashboard)进行应用提交。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-108">Whether you're submitting an app that supports HoloLens, PC, or both, app submission goes through the [Partner Center](https://partner.microsoft.com/dashboard).</span></span>

<span data-ttu-id="1ec5c-109">如果还没有合作伙伴中心开发人员帐户，请在继续之前 [注册](https://developer.microsoft.com/store/register) 一个。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-109">If you don't already have a Partner Center developer account, [sign up](https://developer.microsoft.com/store/register) for one before moving on.</span></span> <span data-ttu-id="1ec5c-110">可在此 [应用提交文章](https://docs.microsoft.com/windows/uwp/publish/app-submissions)中找到有关提交指南和清单的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-110">You can find more information about submission guidelines and checklists in this [app submissions article](https://docs.microsoft.com/windows/uwp/publish/app-submissions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ec5c-111">如果合作伙伴中心开发人员帐户未能通过雇用验证检查，则无法将任何应用程序提交到 Microsoft Store。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-111">You won't be able to submit any applications to the Microsoft Store if your Partner Center developer account fails the employment verification check.</span></span> <span data-ttu-id="1ec5c-112">请联系合作伙伴中心 [支持团队](https://developer.microsoft.com/windows/support) 了解更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-112">Please contact the Partner Center [support team](https://developer.microsoft.com/windows/support) for more details.</span></span>

## <a name="packaging-a-mixed-reality-app"></a><span data-ttu-id="1ec5c-113">打包混合现实应用</span><span class="sxs-lookup"><span data-stu-id="1ec5c-113">Packaging a Mixed Reality app</span></span>

<span data-ttu-id="1ec5c-114">打包混合现实应用程序的步骤包括：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-114">There are several steps to packaging a Mixed Reality application, including:</span></span>

* <span data-ttu-id="1ec5c-115">正确准备所有映像资产</span><span class="sxs-lookup"><span data-stu-id="1ec5c-115">Correctly preparing all image assets</span></span>
* <span data-ttu-id="1ec5c-116">选择在 "HoloLens 开始" 菜单中显示的磁贴图像</span><span class="sxs-lookup"><span data-stu-id="1ec5c-116">Choosing the tile image displayed in the HoloLens Start menu</span></span>
* <span data-ttu-id="1ec5c-117">设置应用的目标和最低 Windows 版本</span><span class="sxs-lookup"><span data-stu-id="1ec5c-117">Setting the target and minimum Windows version for the app</span></span>
* <span data-ttu-id="1ec5c-118">在应用程序依赖项中设置目标设备系列</span><span class="sxs-lookup"><span data-stu-id="1ec5c-118">Setting the target device families in the app dependencies</span></span>
* <span data-ttu-id="1ec5c-119">添加元数据以将应用与 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="1ec5c-119">Adding metadata to associate the app with the Microsoft Store</span></span>
* <span data-ttu-id="1ec5c-120">创建上传包</span><span class="sxs-lookup"><span data-stu-id="1ec5c-120">Creating an upload package</span></span>

<span data-ttu-id="1ec5c-121">以下每个提交阶段都包含在下面的部分中，我们建议你在第一次提交尝试时不留下任何内容。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-121">Each of these submission stages is covered in its own section below - we recommend going through them sequentially you don't leave any out on your first submission attempt.</span></span>

### <a name="prepare-image-assets-included-in-the-appx"></a><span data-ttu-id="1ec5c-122">准备包含在 appx 中的映像资产</span><span class="sxs-lookup"><span data-stu-id="1ec5c-122">Prepare image assets included in the appx</span></span>

<span data-ttu-id="1ec5c-123">Appx 构建工具需要以下图像资产，以便将应用程序构建到 appx 包中，这对于提交到 Microsoft Store 是必需的。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-123">The following image assets are required for the appx building tools to build your application into an appx package, which is required for submission to the Microsoft Store.</span></span> <span data-ttu-id="1ec5c-124">你可以在 MSDN 上详细了解 [磁贴和图标资产的准则](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-124">You can learn more about [guidelines for tile and icon assets](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) on MSDN.</span></span>

| <span data-ttu-id="1ec5c-125">所需资产</span><span class="sxs-lookup"><span data-stu-id="1ec5c-125">Required Asset</span></span> | <span data-ttu-id="1ec5c-126">建议的缩放</span><span class="sxs-lookup"><span data-stu-id="1ec5c-126">Recommended Scale</span></span> | <span data-ttu-id="1ec5c-127">图像格式</span><span class="sxs-lookup"><span data-stu-id="1ec5c-127">Image Format</span></span> | <span data-ttu-id="1ec5c-128">资产显示在哪个位置？</span><span class="sxs-lookup"><span data-stu-id="1ec5c-128">Where is the asset displayed?</span></span> | 
|----------|----------|----------|------------------|
| <span data-ttu-id="1ec5c-129">方块字71x71 徽标</span><span class="sxs-lookup"><span data-stu-id="1ec5c-129">Square 71x71 Logo</span></span> | <span data-ttu-id="1ec5c-130">任意</span><span class="sxs-lookup"><span data-stu-id="1ec5c-130">Any</span></span> |  <span data-ttu-id="1ec5c-131">PNG</span><span class="sxs-lookup"><span data-stu-id="1ec5c-131">PNG</span></span> | <span data-ttu-id="1ec5c-132">不适用</span><span class="sxs-lookup"><span data-stu-id="1ec5c-132">N/A</span></span> | 
| <span data-ttu-id="1ec5c-133">方块字150x150 徽标</span><span class="sxs-lookup"><span data-stu-id="1ec5c-133">Square 150x150 Logo</span></span> | <span data-ttu-id="1ec5c-134">150x150 (100% 规模) 或 225x225 (150% 规模) </span><span class="sxs-lookup"><span data-stu-id="1ec5c-134">150x150 (100% scale) or 225x225 (150% scale)</span></span> | <span data-ttu-id="1ec5c-135">PNG</span><span class="sxs-lookup"><span data-stu-id="1ec5c-135">PNG</span></span> | <span data-ttu-id="1ec5c-136">如果未提供310x310，则启动 pin 和所有应用 () ，存储搜索建议，商店列表页，商店浏览，存储搜索</span><span class="sxs-lookup"><span data-stu-id="1ec5c-136">Start pins and All Apps (if 310x310 isn't provided), Store Search Suggestions, Store Listing Page, Store Browse, Store Search</span></span> | 
|  <span data-ttu-id="1ec5c-137">宽310x150 徽标</span><span class="sxs-lookup"><span data-stu-id="1ec5c-137">Wide 310x150 Logo</span></span> |  <span data-ttu-id="1ec5c-138">任意</span><span class="sxs-lookup"><span data-stu-id="1ec5c-138">Any</span></span>  |  <span data-ttu-id="1ec5c-139">PNG</span><span class="sxs-lookup"><span data-stu-id="1ec5c-139">PNG</span></span>  |  <span data-ttu-id="1ec5c-140">不适用</span><span class="sxs-lookup"><span data-stu-id="1ec5c-140">N/A</span></span> | 
|  <span data-ttu-id="1ec5c-141">应用商店徽标</span><span class="sxs-lookup"><span data-stu-id="1ec5c-141">Store Logo</span></span> |  <span data-ttu-id="1ec5c-142">75x75 (150% 规模) </span><span class="sxs-lookup"><span data-stu-id="1ec5c-142">75x75 (150% scale)</span></span>  |  <span data-ttu-id="1ec5c-143">PNG</span><span class="sxs-lookup"><span data-stu-id="1ec5c-143">PNG</span></span>  |  <span data-ttu-id="1ec5c-144">合作伙伴中心，报表应用，编写评审，我的媒体库</span><span class="sxs-lookup"><span data-stu-id="1ec5c-144">Partner Center, Report App, Write a Review, My Library</span></span> | 
|  <span data-ttu-id="1ec5c-145">初始屏幕</span><span class="sxs-lookup"><span data-stu-id="1ec5c-145">Splash Screen</span></span> |  <span data-ttu-id="1ec5c-146">930x450 (150% 规模) </span><span class="sxs-lookup"><span data-stu-id="1ec5c-146">930x450 (150% scale)</span></span>  |  <span data-ttu-id="1ec5c-147">PNG</span><span class="sxs-lookup"><span data-stu-id="1ec5c-147">PNG</span></span>  |  <span data-ttu-id="1ec5c-148">2D 应用启动器 (盖板) </span><span class="sxs-lookup"><span data-stu-id="1ec5c-148">2D app launcher (slate)</span></span> | 

<span data-ttu-id="1ec5c-149">如果正在开发 HoloLens，还可以利用其他建议的资产：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-149">If you're developing for HoloLens, there are other recommended assets that you can take advantage of:</span></span>

| <span data-ttu-id="1ec5c-150">推荐的资产</span><span class="sxs-lookup"><span data-stu-id="1ec5c-150">Recommended Assets</span></span> | <span data-ttu-id="1ec5c-151">建议的缩放</span><span class="sxs-lookup"><span data-stu-id="1ec5c-151">Recommended Scale</span></span> | <span data-ttu-id="1ec5c-152">资产显示在哪个位置？</span><span class="sxs-lookup"><span data-stu-id="1ec5c-152">Where is the asset displayed?</span></span> | 
|----------|----------|----------|
|  <span data-ttu-id="1ec5c-153">方块字310x310 徽标</span><span class="sxs-lookup"><span data-stu-id="1ec5c-153">Square 310x310 Logo</span></span> |  <span data-ttu-id="1ec5c-154">310x310 (150% 规模) </span><span class="sxs-lookup"><span data-stu-id="1ec5c-154">310x310 (150% scale)</span></span> |  <span data-ttu-id="1ec5c-155">启动 pin 和所有应用</span><span class="sxs-lookup"><span data-stu-id="1ec5c-155">Start pins and All Apps</span></span> | 

### <a name="live-tile-requirements"></a><span data-ttu-id="1ec5c-156">动态磁贴要求</span><span class="sxs-lookup"><span data-stu-id="1ec5c-156">Live Tile requirements</span></span>

<span data-ttu-id="1ec5c-157">默认情况下，HoloLens 上的 "开始" 菜单将使用最大的包含正方形磁贴图像。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-157">The Start menu on HoloLens will use the largest included square tile image by default.</span></span> <span data-ttu-id="1ec5c-158">Microsoft 发布的应用具有可选的3D 启动器，你可以按照 [3d 应用启动器实现](implementing-3d-app-launchers.md) 说明将其添加到应用。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-158">Apps published by Microsoft have an optional 3D launcher, which you can add to your app by following the [3D app launcher implementation](implementing-3d-app-launchers.md) instructions.</span></span>

### <a name="specifying-target-and-minimum-version-of-windows"></a><span data-ttu-id="1ec5c-159">指定 Windows 的目标和最低版本</span><span class="sxs-lookup"><span data-stu-id="1ec5c-159">Specifying target and minimum version of Windows</span></span>

<span data-ttu-id="1ec5c-160">如果混合现实应用包含特定于 Windows 版本的功能，则必须指定支持的目标和最低平台版本。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-160">If your Mixed Reality app includes features that are specific to a Windows version, it's important to specify the supported target and minimum platform versions.</span></span>

<span data-ttu-id="1ec5c-161">**对于面向 [Windows Mixed Reality 沉浸式耳机](../discover/immersive-headset-hardware-details.md)的应用，请特别注意，这需要至少 Windows 10 秋季创意者更新 (10.0;生成 16299) 可以正常工作。**</span><span class="sxs-lookup"><span data-stu-id="1ec5c-161">**Pay special attention for apps targeting [Windows Mixed Reality immersive headsets](../discover/immersive-headset-hardware-details.md), which require at least the Windows 10 Fall Creators Update (10.0; Build 16299) to function properly.**</span></span>

<span data-ttu-id="1ec5c-162">当你在 Visual Studio 中创建新的通用 Windows 项目时，系统将提示你设置 Windows 的目标和最低版本。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-162">You'll be prompted to set the target and minimum version of Windows when you create a new Universal Windows Project in Visual Studio.</span></span> <span data-ttu-id="1ec5c-163">对于现有项目，可以在 " **项目** " 菜单中选择 " **<您的应用程序名称** 在下拉菜单底部的> 属性。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-163">For existing projects, you can change this setting in the **Project** menu by selecting the **<Your app name's> Properties** at the bottom of the drop-down menu.</span></span>

<span data-ttu-id="1ec5c-164">![在 Visual Studio 2019 中设置最低和目标平台版本](images/visual-studio-min-version-500px.png)</span><span class="sxs-lookup"><span data-stu-id="1ec5c-164">![Setting minimum and target platform versions in Visual Studio 2019](images/visual-studio-min-version-500px.png)</span></span><br>
<span data-ttu-id="1ec5c-165">*在 Visual Studio 中设置最低平台版本和目标平台版本*</span><span class="sxs-lookup"><span data-stu-id="1ec5c-165">*Setting minimum and target platform versions in Visual Studio*</span></span>

### <a name="specifying-target-device-families"></a><span data-ttu-id="1ec5c-166">指定目标设备系列</span><span class="sxs-lookup"><span data-stu-id="1ec5c-166">Specifying target device families</span></span>

<span data-ttu-id="1ec5c-167">适用于 [hololens](../hololens-hardware-details.md)和 [沉浸式耳机](../discover/immersive-headset-hardware-details.md)) 的 Windows Mixed Reality 应用程序 (是通用 Windows 平台的一部分，因此具有 **Windows 通用**[目标设备系列](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)的任何应用包都可以通过沉浸式耳机在 HoloLens 或 windows 10 电脑上运行。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-167">Windows Mixed Reality applications (for both [HoloLens](../hololens-hardware-details.md) and [immersive headsets](../discover/immersive-headset-hardware-details.md)) are part of the Universal Windows Platform, so any app package with a **Windows.Universal** [target device family](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) can run on HoloLens or Windows 10 PCs with immersive headsets.</span></span> <span data-ttu-id="1ec5c-168">如果未在应用程序清单中指定目标设备系列，可能会无意中打开应用程序，使其不会出现意外的 Windows 10 设备。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-168">If you don't specify a target device family in your app manifest, you may inadvertently open your app up to unintended Windows 10 devices.</span></span> <span data-ttu-id="1ec5c-169">按照以下步骤指定所需的 Windows 10 设备系列，然后在 [将应用包上传到 Microsoft Store 提交时，请仔细检查是否设置了正确的设备系列。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)</span><span class="sxs-lookup"><span data-stu-id="1ec5c-169">Follow the steps below to specify the intended Windows 10 device family, then [double-check you've set the correct device families when you upload your app package in Partner Center for Microsoft Store submission.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)</span></span>

* <span data-ttu-id="1ec5c-170">若要在 Visual Studio 中设置此字段，请右键单击 **appxmanifest.xml** 并选择 " **查看代码**"，然后找到 " **y 名称** " 字段。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-170">To set this field in Visual Studio, right-click on the **Package.appxmanifest** and select **View Code**, then find the **TargetDeviceFamily Name** field.</span></span> <span data-ttu-id="1ec5c-171">默认情况下，它应类似于以下条目：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-171">By default, it should look like the following entry:</span></span>

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* <span data-ttu-id="1ec5c-172">如果创建的是 **hololens** 应用，则可以通过将目标设备系列设置为 Windows，确保它仅在 HoloLens 上安装 **。全息** 版：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-172">If you're creating a **HoloLens** app, you can make sure it's only installed on HoloLens by setting the target device family to **Windows.Holographic**:</span></span> 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* <span data-ttu-id="1ec5c-173">如果你的应用需要 **HoloLens 2** 功能，如目视或手动跟踪，则可以通过将目标设备系列 **设置为适用于 windows 版本** 18362 或更高 **版本的 10.0.18362.0** ，确保它面向 windows 版本或更高版本：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-173">If your app requires **HoloLens 2** functionality, like eye or hand-tracking, you can make sure it's targeted to Windows versions 18362 or greater by setting the target device family to **Windows.Holographic** with a **MinVersion** of 10.0.18362.0:</span></span>

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* <span data-ttu-id="1ec5c-174">如果你的应用是为 **Windows Mixed reality 沉浸式耳机** 创建的，则可以确保它仅安装在 Windows 10 计算机上，并通过 Windows 10 秋季创意者更新 (Windows Mixed Reality) **通过将目标** 设备系列 **设置为 10.0.16299.0** ：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-174">If your app is created for **Windows Mixed Reality immersive headsets**, you can make sure it's only installed on Windows 10 PCs with the Windows 10 Fall Creators Update (necessary for Windows Mixed Reality) by setting the target device family to **Windows.Desktop** with a **MinVersion** of 10.0.16299.0:</span></span>

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* <span data-ttu-id="1ec5c-175">最后，如果你的应用程序应在 **HoloLens** 和 **Windows Mixed Reality 沉浸式耳机** 上运行，你可以确保此应用仅适用于这两个设备家族，同时确保每个目标都具有正确的最低 Windows 版本，方法是为每个目标设备系列包含其各自的 MinVersion：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-175">Finally, if your app is intended to run on both **HoloLens** and **Windows Mixed Reality immersive headsets**, you can make sure the app is only available to those two device families and simultaneously ensure that each target has the correct minimum Windows version by including a line for each target device family with its respective MinVersion:</span></span>

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

<span data-ttu-id="1ec5c-176">若要了解有关面向设备家族的详细信息，请阅读 [y UWP 文档](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-176">You can learn more about targeting device families by reading the [TargetDeviceFamily UWP documentation](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).</span></span>

### <a name="associate-app-with-the-store"></a><span data-ttu-id="1ec5c-177">将应用与应用商店关联</span><span class="sxs-lookup"><span data-stu-id="1ec5c-177">Associate app with the Store</span></span>

<span data-ttu-id="1ec5c-178">当你将应用程序与 Microsoft Store 相关联时，以下值将下载到当前项目本地应用程序清单文件中：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-178">When you associate your app with the Microsoft Store, the following values are downloaded to the current projects local app manifest file:</span></span>

* <span data-ttu-id="1ec5c-179">包显示名称</span><span class="sxs-lookup"><span data-stu-id="1ec5c-179">Package Display Name</span></span>
* <span data-ttu-id="1ec5c-180">包名称</span><span class="sxs-lookup"><span data-stu-id="1ec5c-180">Package Name</span></span>
* <span data-ttu-id="1ec5c-181">发布者 ID</span><span class="sxs-lookup"><span data-stu-id="1ec5c-181">Publisher ID</span></span>
* <span data-ttu-id="1ec5c-182">发行者显示名称</span><span class="sxs-lookup"><span data-stu-id="1ec5c-182">Publisher Display Name</span></span>
* <span data-ttu-id="1ec5c-183">版本</span><span class="sxs-lookup"><span data-stu-id="1ec5c-183">Version</span></span>

<span data-ttu-id="1ec5c-184">如果用自己的自定义 .xml 文件覆盖默认的 appxmanifest.xml 文件，则不能将应用程序与 Microsoft Store 相关联。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-184">If you're overriding the default package.appxmanifest file with your own custom .xml file, you can’t associate your app with the Microsoft Store.</span></span> <span data-ttu-id="1ec5c-185">将自定义清单文件与应用商店关联将导致错误消息。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-185">Associating a custom manifest file with the Store will result in an error message.</span></span>

<span data-ttu-id="1ec5c-186">你还可以通过转到 Visual Studio 解决方案并选择 " **Project > Store > 将应用与应用商店关联** 来测试购买和通知方案。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-186">You can also test purchase and notification scenarios by going to your Visual Studio solution and selecting **Project > Store > Associate App with the Store**.</span></span>

### <a name="creating-an-upload-package"></a><span data-ttu-id="1ec5c-187">创建上传包</span><span class="sxs-lookup"><span data-stu-id="1ec5c-187">Creating an upload package</span></span>

<span data-ttu-id="1ec5c-188">按照 [打包适用于 windows 10 的通用 windows 应用程序中的](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)准则。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-188">Follow guidelines at [Packaging Universal Windows apps for Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).</span></span>

<span data-ttu-id="1ec5c-189">创建上传包的最后一步是使用 [Windows 应用认证](#windows-app-certification-kit)包验证包。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-189">The final step of creating an upload package is validating the package using the [Windows App Certification Kit](#windows-app-certification-kit).</span></span>

<span data-ttu-id="1ec5c-190">如果要将特定于 HoloLens 的包添加到其他 Windows 10 设备家族上可用的现有产品，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-190">If you're adding a HoloLens-specific package to an existing product that's available on other Windows 10 device families, pay attention to:</span></span> 

* [<span data-ttu-id="1ec5c-191">版本号可能如何影响向特定客户发送的包</span><span class="sxs-lookup"><span data-stu-id="1ec5c-191">How version numbers may impact which packages are delivered to specific customers</span></span>](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)
* [<span data-ttu-id="1ec5c-192">如何将包分发到不同的操作系统</span><span class="sxs-lookup"><span data-stu-id="1ec5c-192">How packages are distributed to different operating systems</span></span>](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)

<span data-ttu-id="1ec5c-193">一般指导原则是，设备中版本号最高的包是存储区分发的包。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-193">The general guidance is that the package with the highest version number for a device is the one distributed by the Store.</span></span>

<span data-ttu-id="1ec5c-194">在出现 **Windows 通用** 包和 **windows 全息** 包的情况下，如果 windows 通用包具有较高的版本号，则 HoloLens 用户将下载较高的版本号 windows 通用包而不是 windows 全息包。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-194">In a scenario where there's a **Windows.Universal** package and a **Windows.Holographic** package, and the Windows.Universal package has a higher version number, a HoloLens user will download the higher version number Windows.Universal package instead of the Windows.Holographic package.</span></span> 

<span data-ttu-id="1ec5c-195">如果上述方案不是你要寻找的结果，则可以使用以下几种解决方案：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-195">In cases where the above scenario isn't the outcome you're looking for, there are several available solutions:</span></span>

* <span data-ttu-id="1ec5c-196">确保特定于平台的包（如 Windows. 全息）的版本号比平台无关包（如 Windows 通用）的版本号更高。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-196">Ensure your platform-specific packages, such as Windows.Holographic, always have a higher version number than your platform agnostic packages like Windows.Universal</span></span>
* <span data-ttu-id="1ec5c-197">不要将应用打包为 Windows。如果你还具有特定于平台的包，请将 Windows 通用包打包为你要在其上可用的特定平台</span><span class="sxs-lookup"><span data-stu-id="1ec5c-197">Don't package apps as Windows.Universal if you also have platform-specific packages - instead package the Windows.Universal package for the specific platforms you want it available on</span></span>
* <span data-ttu-id="1ec5c-198">创建跨所有平台工作的单个 Windows 通用包。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-198">Create a single Windows.Universal package that works across all platforms.</span></span> <span data-ttu-id="1ec5c-199">目前尚不支持此选项，因此建议使用上述解决方案。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-199">Support for this option isn't great right now so the above solutions are recommended.</span></span>

>[!NOTE]
> <span data-ttu-id="1ec5c-200">若要在 HoloLens (第一代) 和 HoloLen 2 上支持你的应用，你需要上传两个应用包;一个包含 x86 for HoloLens (第一代) ，一个包含 ARM 或 ARM64 （适用于 HoloLens 2）。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-200">To support your app on both HoloLens (1st Gen) and HoloLen 2, you need to upload two app packages; one containing x86 for HoloLens (1st Gen) and one containing ARM or ARM64 for HoloLens 2.</span></span> 
> 
> <span data-ttu-id="1ec5c-201">如果在包中同时包含 ARM 和 ARM64，则 ARM64 版本将是在 HoloLens 2 上使用的版本。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-201">If you include both ARM and ARM64 in your package, the ARM64 version will be the one used on HoloLens 2.</span></span> 

>[!NOTE]
> <span data-ttu-id="1ec5c-202">可以声明单个包，使其适用于多个目标设备系列</span><span class="sxs-lookup"><span data-stu-id="1ec5c-202">You can declare a single package to be applicable to multiple target device families</span></span>

## <a name="testing-your-app"></a><span data-ttu-id="1ec5c-203">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="1ec5c-203">Testing your app</span></span>

### <a name="windows-app-certification-kit"></a><span data-ttu-id="1ec5c-204">Windows 应用认证工具包</span><span class="sxs-lookup"><span data-stu-id="1ec5c-204">Windows App Certification Kit</span></span>

<span data-ttu-id="1ec5c-205">通过 Visual Studio 创建要提交到合作伙伴中心的应用包时，"创建应用程序包" 向导会提示你针对创建的包运行 Windows 应用认证工具包。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-205">When you create app packages to submit to Partner Center through Visual Studio, the Create App Packages wizard prompts you to run the Windows App Certification Kit against the packages that get created.</span></span> <span data-ttu-id="1ec5c-206">若要对应用程序进行平滑提交，最好先验证应用的本地副本是否通过 [Windows 应用认证包测试](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) ，然后再将其提交到应用商店。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-206">To have a smooth submission process to the Store, it's best to verify that the local copy of your app passes the [Windows App Certification Kit tests](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) before submitting them to the Store.</span></span> <span data-ttu-id="1ec5c-207">当前不支持在远程 HoloLens 上运行 Windows 应用程序认证包。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-207">Running the Windows App Certification Kit on a remote HoloLens isn't currently supported.</span></span>

### <a name="run-on-all-targeted-device-families"></a><span data-ttu-id="1ec5c-208">在所有目标设备系列上运行</span><span class="sxs-lookup"><span data-stu-id="1ec5c-208">Run on all targeted device families</span></span>

<span data-ttu-id="1ec5c-209">使用 Windows 通用平台，您可以创建跨所有 Windows 10 设备系列运行的单一应用程序。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-209">The Windows Universal Platform allows you to create a single application that runs across all of the Windows 10 device families.</span></span> <span data-ttu-id="1ec5c-210">但是，它并不保证通用 Windows 应用程序将只在所有设备家族上工作。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-210">However, it doesn't guarantee that Universal Windows apps will just work on all device families.</span></span> <span data-ttu-id="1ec5c-211">在所选的每个设备家族上 [测试您的应用程序](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) 很重要，以确保获得良好的体验。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-211">It's important to [test your app](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) on each of your chosen device families to ensure a good experience.</span></span>

## <a name="submitting-your-mixed-reality-app-to-the-store"></a><span data-ttu-id="1ec5c-212">将混合现实应用提交到应用商店</span><span class="sxs-lookup"><span data-stu-id="1ec5c-212">Submitting your Mixed Reality app to the Store</span></span>

<span data-ttu-id="1ec5c-213">如果要提交基于 Unity 项目的混合现实应用，请先参阅此 [视频](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) 。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-213">If you're submitting a Mixed Reality app that is based on a Unity project, see this [video](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) first.</span></span>

<span data-ttu-id="1ec5c-214">通常，提交在 HoloLens 或沉浸式耳机上运行的 Windows Mixed Reality 应用就像将任何 UWP 应用提交到 Microsoft Store。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-214">In general, submitting a Windows Mixed Reality app that works on HoloLens or immersive headsets is just like submitting any UWP app to the Microsoft Store.</span></span> <span data-ttu-id="1ec5c-215">[通过保留应用名称创建应用](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)后，请遵循[UWP 提交清单](https://docs.microsoft.com/windows/uwp/publish/app-submissions)。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-215">Once you've [created your app by reserving its name](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), follow the [UWP submission checklist](https://docs.microsoft.com/windows/uwp/publish/app-submissions).</span></span>

<span data-ttu-id="1ec5c-216">你要做的第一项工作就是为混合现实体验 [选择一个类别和子](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) 类别。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-216">One of the first things you'll do is [select a category and subcategory](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) for your Mixed Reality experience.</span></span> <span data-ttu-id="1ec5c-217">**请务必为应用选择最准确的类别**。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-217">It's important that you **choose the most accurate category for your app**.</span></span> <span data-ttu-id="1ec5c-218">类别可帮助将应用程序商品置于正确的存储类别中，并确保它使用相关搜索查询显示。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-218">Categories help merchandise your application in the right Store categories and ensure it shows up using relevant search queries.</span></span> <span data-ttu-id="1ec5c-219">将 **您的 VR 标题列为游戏不会导致您的应用程序的曝光更好，** 可能会阻止其显示在更具可容纳性和更少的类别中。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-219">**Listing your VR title as a game won't result in better exposure for your app,** and may prevent it from showing up in categories that are more fitting and less crowded.</span></span>

<span data-ttu-id="1ec5c-220">但在提交过程中，有四个重要方面需要进行特定于现实的特定选择：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-220">However, there are four key areas in the submission process where you'll want to make Mixed Reality-specific selections:</span></span>
1. <span data-ttu-id="1ec5c-221">在 "[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)" 下的 "**[产品声明](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)**" 部分。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-221">In the **[Product declarations](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** section under [Properties](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).</span></span>
2. <span data-ttu-id="1ec5c-222">在 "[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)" 下的 "**[系统要求](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)**" 部分。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-222">In the **[System requirements](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** section under [Properties](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).</span></span>
3. <span data-ttu-id="1ec5c-223">"[包](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)" 下的 "**[设备系列可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)**" 部分。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-223">In the **[Device family availability](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** section under [Packages](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).</span></span>
4. <span data-ttu-id="1ec5c-224">几个 **[商店列表页](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 字段。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-224">In several of the **[Store listing page](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** fields.</span></span>

### <a name="mixed-reality-product-declarations"></a><span data-ttu-id="1ec5c-225">混合现实产品声明</span><span class="sxs-lookup"><span data-stu-id="1ec5c-225">Mixed Reality product declarations</span></span>

<span data-ttu-id="1ec5c-226">在应用提交过程的 " **[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** " 页上，可以在 " **[产品声明](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** " 部分中找到几个与混合现实相关的选项。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-226">On the **[Properties](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** page of the app submission process, you'll find several options related to Mixed Reality in the **[Product declarations](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** section.</span></span>

<span data-ttu-id="1ec5c-227">![混合现实产品声明](images/product-declarations-900px.png)</span><span class="sxs-lookup"><span data-stu-id="1ec5c-227">![Mixed Reality product declarations](images/product-declarations-900px.png)</span></span><br>
<span data-ttu-id="1ec5c-228">混合现实产品声明</span><span class="sxs-lookup"><span data-stu-id="1ec5c-228">Mixed Reality product declarations</span></span>

<span data-ttu-id="1ec5c-229">首先，需要确定应用为其提供混合现实体验的设备类型。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-229">First, you need to identify the device types for which your app offers a Mixed Reality experience.</span></span> <span data-ttu-id="1ec5c-230">标识设备类型可确保应用包含在应用商店中的 Windows Mixed Reality 集合中。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-230">Identifying device types ensures that your app is included in Windows Mixed Reality collections in the Store.</span></span>

<span data-ttu-id="1ec5c-231">"这一体验是针对 Windows Mixed Reality 设计的："</span><span class="sxs-lookup"><span data-stu-id="1ec5c-231">Next to "This experience is designed for Windows Mixed Reality on:"</span></span>
* <span data-ttu-id="1ec5c-232">如果你的应用程序在沉浸式耳机连接到用户的 PC 时提供了 VR 体验，请选中 " **电脑** " 框。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-232">Check the **PC** box if your app offers a VR experience when an immersive headset is connected to the user's PC.</span></span> <span data-ttu-id="1ec5c-233">建议选中此框，无论你的应用程序设置为在沉浸式耳机上以独占方式运行，还是在连接耳机时提供混合现实模式或附赠内容。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-233">We recommend checking this box whether your app is set to run exclusively on an immersive headset or if it's a standard PC game or app offering a Mixed Reality mode or bonus content when a headset is connected.</span></span>
* <span data-ttu-id="1ec5c-234">仅当你的应用程序在 HoloLens 上运行时提供了全息体验时，才检查 **hololens** 框。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-234">Check the **HoloLens** box only if your app offers a holographic experience when it's run on HoloLens.</span></span>
* <span data-ttu-id="1ec5c-235">如果你的应用在这两个设备类型上都提供混合现实体验，请选中 **这两个** 框。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-235">Check **both** boxes if your app offers a Mixed Reality experience on both device types.</span></span>

<span data-ttu-id="1ec5c-236">如果选择上述 "PC"，则需要将 "混合现实设置" (活动级别) 。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-236">If you selected "PC" above, you'll want to set the "Mixed Reality setup" (activity level).</span></span> <span data-ttu-id="1ec5c-237">这仅适用于在连接到沉浸式头设备的 Pc 上运行的混合现实体验，因为 HoloLens 上的混合现实应用是全球规模的，用户在安装过程中未定义边界。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-237">This only applies to Mixed Reality experiences that run on PCs connected to immersive headsets, as Mixed Reality apps on HoloLens are world-scale and the user doesn't define a boundary during setup.</span></span>
* <span data-ttu-id="1ec5c-238">如果你设计的应用程序位于同一位置，请选择 " **固定 +** 上"。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-238">Choose **Seated + standing** if you designed your app to have the user stay in one position.</span></span> <span data-ttu-id="1ec5c-239">例如，在你掌控飞机考核中心的游戏中。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-239">For example, in a game where you're in control of an aircraft cockpit.</span></span>
* <span data-ttu-id="1ec5c-240">如果你的应用程序的设计目的是让用户在安装过程中定义的集边界内进行浏览，则选择 " **所有体验** "。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-240">Choose **All experiences** if your app is designed with the intention that the user walks around within a set boundary defined during setup.</span></span> <span data-ttu-id="1ec5c-241">例如，可能是一项游戏，你可以在其中进行逐步操作并对减减减攻击。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-241">For example, might be a game where you side-step and duck to dodge attacks.</span></span>

### <a name="mixed-reality-system-requirements"></a><span data-ttu-id="1ec5c-242">混合现实系统要求</span><span class="sxs-lookup"><span data-stu-id="1ec5c-242">Mixed Reality system requirements</span></span>

<span data-ttu-id="1ec5c-243">在应用提交过程的 " **[属性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** " 页上，可以在 " **[系统要求](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** " 部分中找到几个与混合现实相关的选项。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-243">On the **[Properties](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** page of the app submission process, you'll find several options related to Mixed Reality in the **[System requirements](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** section.</span></span>

<span data-ttu-id="1ec5c-244">![系统要求](images/system-reqs-800px.png)</span><span class="sxs-lookup"><span data-stu-id="1ec5c-244">![System requirements](images/system-reqs-800px.png)</span></span><br>
<span data-ttu-id="1ec5c-245">系统要求</span><span class="sxs-lookup"><span data-stu-id="1ec5c-245">System requirements</span></span>

<span data-ttu-id="1ec5c-246">在本部分中，你将确定) 硬件所需的最小 (，以及建议用于混合现实应用的 (可选) 硬件。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-246">In this section, you'll identify minimum (required) hardware and recommended (optional) hardware for your Mixed Reality app.</span></span>

<span data-ttu-id="1ec5c-247">**输入硬件：**</span><span class="sxs-lookup"><span data-stu-id="1ec5c-247">**Input hardware:**</span></span>

<span data-ttu-id="1ec5c-248">如果应用支持 [语音输入](../design/voice-input.md)) 、 **[Xbox 控制器或游戏板](../discover/hardware-accessories.md#bluetooth-gamepads)** 或 **[Windows Mixed Reality 运动控制器](../design/motion-controllers.md)** 的 **麦克风**，请使用复选框来告知潜在客户。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-248">Use the checkboxes to tell potential customers if your app supports **microphone** for [voice input](../design/voice-input.md)), **[Xbox controller or gamepad](../discover/hardware-accessories.md#bluetooth-gamepads)**, or **[Windows Mixed Reality motion controllers](../design/motion-controllers.md)**.</span></span> <span data-ttu-id="1ec5c-249">此信息将显示在应用商店中的应用的 "产品详细信息" 页上，可帮助你的应用包含在适当的应用/游戏集合中。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-249">This information will be surfaced on your app's product detail page in the Store and will help your app get included in the appropriate app/game collections.</span></span> <span data-ttu-id="1ec5c-250">例如，对于支持运动控制器的所有游戏，都可能存在一个集合。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-250">For example, a collection may exist for all games that support motion controllers.</span></span>

<span data-ttu-id="1ec5c-251">为输入类型选择 "最低硬件" 或 "推荐的硬件" 复选框。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-251">Be thoughtful about selecting checkboxes for "minimum hardware" or "recommended hardware" for input types.</span></span> 

<span data-ttu-id="1ec5c-252">例如：</span><span class="sxs-lookup"><span data-stu-id="1ec5c-252">For example:</span></span> 
* <span data-ttu-id="1ec5c-253">如果游戏需要运动控制器，但通过麦克风接受语音输入，请选择 "Windows Mixed Reality 运动控制器" 旁边的 "最小硬件" 复选框，但 "麦克风" 旁边的 "推荐的硬件" 复选框。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-253">If your game requires motion controllers, but accepts voice input via microphone, select the "minimum hardware" checkbox next to "Windows Mixed Reality motion controllers," but the "recommended hardware" checkbox next to "Microphone."</span></span> 
* <span data-ttu-id="1ec5c-254">如果可以使用 Xbox 控制器、游戏板或运动控制器播放游戏，则可以选择 "Xbox 控制器或游戏板" 旁边的 "最小硬件" 复选框，并选择 "Windows Mixed Reality 运动控制器" 旁边的 "推荐的硬件" 复选框，因为运动控制器可能会在游戏板上提供一个步骤。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-254">If your game can be played with either an Xbox controller, gamepad, or motion controllers, you might select the "minimum hardware" checkbox next to "Xbox controller or gamepad" and select the "recommended hardware" checkbox next to "Windows Mixed Reality motion controllers" as motion controllers will likely offer a step-up in experience from the gamepad.</span></span>

<span data-ttu-id="1ec5c-255">**Windows Mixed Reality 沉浸式耳机：**</span><span class="sxs-lookup"><span data-stu-id="1ec5c-255">**Windows Mixed Reality immersive headset:**</span></span>

<span data-ttu-id="1ec5c-256">指示是否需要沉浸式耳机来使用你的应用，或是否可选，这对于客户满意度和教育至关重要。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-256">Indicating whether an immersive headset is required to use your app, or is optional, is critical to customer satisfaction and education.</span></span>

<span data-ttu-id="1ec5c-257">如果你的应用 *只能* 通过沉浸式耳机使用，请选择 "Windows Mixed Reality 沉浸式耳机" 旁边的 "最小硬件" 复选框。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-257">If your app can *only* be used through an immersive headset, select the "minimum hardware" checkbox next to "Windows Mixed Reality immersive headset."</span></span> <span data-ttu-id="1ec5c-258">这会显示在应用程序中应用程序的产品详细信息页上，在 "购买" 按钮上显示为警告，因此客户不会认为他们购买的应用程序将在其电脑上运行，如传统桌面应用程序。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-258">This will be surfaced on your app's product detail page in Store as a warning above the purchase button so customers don't think they're purchasing an app that will function on their PC like a traditional desktop app.</span></span>

<span data-ttu-id="1ec5c-259">如果你的应用程序在桌面上运行，如传统的 PC 应用程序，但在连接沉浸式头戴式耳机时提供了 VR 体验 (你的应用的完整内容是否可用，或者仅) 部分，请选中 "Windows Mixed Reality 沉浸式耳机" 旁边的 "推荐的硬件" 复选框。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-259">If your app runs on the desktop like a traditional PC app, but offers a VR experience when an immersive headset is connected (whether the full content of your app is available, or only a portion), select the "recommended hardware" checkbox next to "Windows Mixed Reality immersive headset."</span></span> <span data-ttu-id="1ec5c-260">如果你的应用程序在未连接沉浸式头戴式的情况下作为传统桌面应用程序运行，则不会出现任何警告。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-260">No warning will be surfaced above the purchase button on your app's product detail page if your app functions as a traditional desktop app without an immersive headset connected.</span></span>

<span data-ttu-id="1ec5c-261">**PC 规范：**</span><span class="sxs-lookup"><span data-stu-id="1ec5c-261">**PC specifications:**</span></span>

<span data-ttu-id="1ec5c-262">如果你希望你的应用程序尽可能多地访问 Windows Mixed reality 沉浸式耳机用户，请将适用于[Windows Mixed Reality 电脑](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的 PC 规格作为集成图形[定位](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-262">If you want your app to reach as many Windows Mixed Reality immersive headset users as possible, [target](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) the PC specifications for [Windows Mixed Reality PCs with integrated graphics](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).</span></span>

<span data-ttu-id="1ec5c-263">无论你的混合现实应用程序是以最低的 Windows Mixed Reality PC 需求为目标还是需要特定的 PC 配置（如 [Windows Mixed Reality 超 PC] (的专用 GPU https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines ），都应该在 "最低硬件" 列中添加相关的 pc 规范。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-263">Whether your Mixed Reality app targets the minimum Windows Mixed Reality PC requirements, or needs a specific PC configuration like the dedicated GPU of a [Windows Mixed Reality Ultra PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines, you should add the relevant PC specifications in the "minimum hardware" column.</span></span>

<span data-ttu-id="1ec5c-264">如果混合现实应用旨在提供更好的性能，或在特定 PC 配置或图形卡上提供更高分辨率的图形，则应在 "推荐的硬件" 列中包含相关的 PC 规范。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-264">If your Mixed Reality app is designed for better performance or offers higher-resolution graphics on a particular PC configuration or graphics card, you should include the relevant PC specifications in the "recommended hardware" column.</span></span>

<span data-ttu-id="1ec5c-265">仅当混合现实应用使用连接到电脑的沉浸式头戴式耳机时，此情况才适用。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-265">This only applies if your Mixed Reality app uses an immersive headset connected to a PC.</span></span> <span data-ttu-id="1ec5c-266">如果混合现实应用仅在 HoloLens 上运行，则无需指示 PC 规范，因为 HoloLens 只有一个硬件配置。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-266">If your Mixed Reality app only runs on HoloLens, you won't need to indicate PC specifications as HoloLens has only one hardware configuration.</span></span>

### <a name="device-family-availability"></a><span data-ttu-id="1ec5c-267">设备系列可用性</span><span class="sxs-lookup"><span data-stu-id="1ec5c-267">Device family availability</span></span>

<span data-ttu-id="1ec5c-268">如果已在 Visual Studio 中 [正确打包了应用](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) ，则在 "包" 页上上传该应用时，应生成包含可用设备系列的表。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-268">If you've [packaged your app correctly](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) in Visual Studio, uploading it on the Packages page should produce a table with the available device families.</span></span>

<span data-ttu-id="1ec5c-269">![设备家族可用性表](images/device-family-table-900px.png)</span><span class="sxs-lookup"><span data-stu-id="1ec5c-269">![Device family availability table](images/device-family-table-900px.png)</span></span><br>
<span data-ttu-id="1ec5c-270">设备家族可用性表</span><span class="sxs-lookup"><span data-stu-id="1ec5c-270">Device family availability table</span></span>

<span data-ttu-id="1ec5c-271">如果混合现实应用适用于沉浸式耳机，则应在表中选择至少 "Windows 10 桌面"。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-271">If your Mixed Reality app works on immersive headsets, then at least "Windows 10 Desktop" should be selected in the table.</span></span> <span data-ttu-id="1ec5c-272">如果你的混合现实应用在 HoloLens 上工作，则应至少选择 "Windows 10 全息版"。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-272">If your Mixed Reality app works on HoloLens, then at least "Windows 10 Holographic" should be selected.</span></span> <span data-ttu-id="1ec5c-273">如果你的应用在两个 Windows Mixed Reality 耳机类型上运行，则应选择 "Windows 10 桌面" 和 "Windows 10 全息版"。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-273">If your app runs on both Windows Mixed Reality headset types, both "Windows 10 Desktop" and "Windows 10 Holographic" should be selected.</span></span>

>[!TIP]
><span data-ttu-id="1ec5c-274">许多开发人员在上载其应用包时出现错误，这些错误与 "合作伙伴中心" 中的包清单与你的应用/发布者帐户信息的不匹配相关。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-274">Many developers run into errors when uploading their app's package related to mismatches between the package manifest and your app/publisher account information in Partner Center.</span></span> <span data-ttu-id="1ec5c-275">使用与您的 Windows 开发人员帐户关联的同一帐户登录到 Visual Studio （ (用于登录到合作伙伴中心) 的帐户）通常可以避免这些错误。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-275">These errors can often be avoided by signing into Visual Studio with the same account associated with your Windows developer account (the one you use to sign into Partner Center).</span></span> <span data-ttu-id="1ec5c-276">如果你使用相同的帐户，则在打包应用程序之前，你可以将应用与其在 Microsoft Store 中的标识相关联。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-276">If you use the same account, you'll be able to associate your app with its identity in the Microsoft Store before you package it.</span></span>

<span data-ttu-id="1ec5c-277">![将你的应用与 Microsoft Store](images/associate-your-app-700px.png)</span><span class="sxs-lookup"><span data-stu-id="1ec5c-277">![Associate your app with the Microsoft Store](images/associate-your-app-700px.png)</span></span><br>
<span data-ttu-id="1ec5c-278">在 Visual Studio 中将应用与 Microsoft Store 相关联</span><span class="sxs-lookup"><span data-stu-id="1ec5c-278">Associate your app with the Microsoft Store in Visual Studio</span></span>

### <a name="store-listing-page"></a><span data-ttu-id="1ec5c-279">商店列表页</span><span class="sxs-lookup"><span data-stu-id="1ec5c-279">Store listing page</span></span>

<span data-ttu-id="1ec5c-280">在应用提交过程的 "应用 [商店列表](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) " 页上，可以添加有关混合现实应用的有用信息。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-280">On the [Store listing](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) page of the app submission process, there are several places you can add useful information about your Mixed Reality app.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1ec5c-281">若要确保应用程序正确地分类了应用程序并将其视为 Windows Mixed Reality 客户，应将 **"Windows Mixed Reality"** 添加为应用的 "搜索词"， (可以通过展开 "共享字段" 部分) 来查找搜索词。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-281">To ensure your app is correctly categorized by the Store and made discoverable to Windows Mixed Reality customers, you should add **"Windows Mixed Reality"** as one of your "Search terms" for the app (you can find search terms by expanding the "Shared fields" section).</span></span>

<span data-ttu-id="1ec5c-282">![将 Windows Mixed Reality 添加到搜索词](images/search-terms-800px.png)</span><span class="sxs-lookup"><span data-stu-id="1ec5c-282">![Add Windows Mixed Reality to search terms](images/search-terms-800px.png)</span></span><br>
<span data-ttu-id="1ec5c-283">向搜索词添加 "Windows Mixed Reality"</span><span class="sxs-lookup"><span data-stu-id="1ec5c-283">Add "Windows Mixed Reality" to search terms</span></span>

## <a name="offering-a-free-trial-for-your-game-or-app"></a><span data-ttu-id="1ec5c-284">为游戏或应用提供免费试用版</span><span class="sxs-lookup"><span data-stu-id="1ec5c-284">Offering a free trial for your game or app</span></span>

<span data-ttu-id="1ec5c-285">在许多情况下，使用者在购买 Windows Mixed Reality 沉浸式耳机之前，将不会受到虚拟现实的经验限制。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-285">In many cases, your consumers will have limited to no experience with virtual reality before they buy a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="1ec5c-286">他们可能不知道从重要游戏中获得的内容，或者在沉浸式体验中熟悉自己的舒适阈值。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-286">They may not know what to expect from intense games or be familiar with their own comfort threshold in immersive experiences.</span></span> <span data-ttu-id="1ec5c-287">许多客户还可能会尝试在未徽章为 [Windows Mixed Reality pc](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的电脑上使用 Windows mixed reality 沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-287">Many customers may also try a Windows Mixed Reality immersive headset on PCs that aren't badged as [Windows Mixed Reality PCs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).</span></span> <span data-ttu-id="1ec5c-288">出于上述考虑，强烈建议您考虑为付费混合现实应用或游戏提供 [免费试用版](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) 。</span><span class="sxs-lookup"><span data-stu-id="1ec5c-288">Because of these considerations, we strongly recommend you consider offering a [free trial](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) for your paid Mixed Reality app or game.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ec5c-289">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ec5c-289">See also</span></span>
* [<span data-ttu-id="1ec5c-290">什么是混合现实？</span><span class="sxs-lookup"><span data-stu-id="1ec5c-290">What is Mixed Reality?</span></span>](../discover/mixed-reality.md)
* [<span data-ttu-id="1ec5c-291">开发概述</span><span class="sxs-lookup"><span data-stu-id="1ec5c-291">Development overview</span></span>](../develop/development.md)
* [<span data-ttu-id="1ec5c-292">应用视图</span><span class="sxs-lookup"><span data-stu-id="1ec5c-292">App views</span></span>](../design/app-views.md)
* [<span data-ttu-id="1ec5c-293">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="1ec5c-293">Understanding Performance for Mixed Reality</span></span>](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="1ec5c-294">Unity 性能建议</span><span class="sxs-lookup"><span data-stu-id="1ec5c-294">Performance Recommendations for Unity</span></span>](../develop/unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="1ec5c-295">在 HoloLens 上测试应用</span><span class="sxs-lookup"><span data-stu-id="1ec5c-295">Testing your app on HoloLens</span></span>](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [<span data-ttu-id="1ec5c-296">Windows Mixed Reality 最小电脑硬件兼容性指南</span><span class="sxs-lookup"><span data-stu-id="1ec5c-296">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
