---
title: 配置混合现实功能工具
description: 了解如何从面向 HoloLens 和 VR 开发的混合现实功能工具中下载并安装混合现实工具包 Unity。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731934"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="901da-104">配置混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="901da-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="901da-105">使用混合现实功能工具时，你可以访问三个不同的设置类别并可随意自定义这些类别：</span><span class="sxs-lookup"><span data-stu-id="901da-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="901da-106">下载设置</span><span class="sxs-lookup"><span data-stu-id="901da-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="901da-107">功能设置</span><span class="sxs-lookup"><span data-stu-id="901da-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="901da-108">导入设置</span><span class="sxs-lookup"><span data-stu-id="901da-108">Import settings</span></span>](#import-settings)

## <a name="download-settings"></a><span data-ttu-id="901da-109">下载设置</span><span class="sxs-lookup"><span data-stu-id="901da-109">Download settings</span></span>

![下载设置](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="901da-111">覆盖现有包文件</span><span class="sxs-lookup"><span data-stu-id="901da-111">Overwrite existing package files</span></span>

<span data-ttu-id="901da-112">如果启用此设置，则每次获取包文件时都会下载包文件。</span><span class="sxs-lookup"><span data-stu-id="901da-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 

* <span data-ttu-id="901da-113">**建议将此选项保留为禁用状态以减少网络带宽使用量**</span><span class="sxs-lookup"><span data-stu-id="901da-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="901da-114">默认情况下，不会重新下载以前获取的包文件</span><span class="sxs-lookup"><span data-stu-id="901da-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="901da-115">包缓存</span><span class="sxs-lookup"><span data-stu-id="901da-115">Package cache</span></span>

<span data-ttu-id="901da-116">更改此设置可更新下载功能包的位置。</span><span class="sxs-lookup"><span data-stu-id="901da-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="901da-117">该设置在此版本中是只读的。</span><span class="sxs-lookup"><span data-stu-id="901da-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="901da-118">将来的版本允许配置此设置。</span><span class="sxs-lookup"><span data-stu-id="901da-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="901da-119">功能设置</span><span class="sxs-lookup"><span data-stu-id="901da-119">Feature settings</span></span>

![功能设置](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a><span data-ttu-id="901da-121">显示预览版本</span><span class="sxs-lookup"><span data-stu-id="901da-121">Show preview releases</span></span>

<span data-ttu-id="901da-122">启用此设置可获取预览版本。</span><span class="sxs-lookup"><span data-stu-id="901da-122">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="901da-123">默认情况下，不会在混合现实功能工具中显示预览版本</span><span class="sxs-lookup"><span data-stu-id="901da-123">By default, preview releases are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="901da-124">预览版本定义为在包版本中包含“-preview”指定。</span><span class="sxs-lookup"><span data-stu-id="901da-124">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

### <a name="show-early-access-program-features"></a><span data-ttu-id="901da-125">显示抢先访问计划功能</span><span class="sxs-lookup"><span data-stu-id="901da-125">Show early access program features</span></span>

<span data-ttu-id="901da-126">启用此设置可从注册的抢先访问计划版本中获取功能。</span><span class="sxs-lookup"><span data-stu-id="901da-126">Enable this setting to acquire features from registered early access programs releases.</span></span>

* <span data-ttu-id="901da-127">默认情况下，不会在混合现实功能工具中显示抢先访问功能</span><span class="sxs-lookup"><span data-stu-id="901da-127">By default, early access features are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="901da-128">如果在没有`Show preview releases`的情况下启用`Show early access program features`，可能导致发现中不显示抢先访问包。</span><span class="sxs-lookup"><span data-stu-id="901da-128">Enabling `Show early access program features` without `Show preview releases` may result in eary access packages not appearing in Discovery.</span></span>

## <a name="import-settings"></a><span data-ttu-id="901da-129">导入设置</span><span class="sxs-lookup"><span data-stu-id="901da-129">Import settings</span></span>

![导入设置](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a><span data-ttu-id="901da-131">替换现有包文件</span><span class="sxs-lookup"><span data-stu-id="901da-131">Replace existing package files</span></span>

<span data-ttu-id="901da-132">默认情况下，混合现实功能工具会删除正在导入的包的以前副本，以减少文件大小和不必要的计算。</span><span class="sxs-lookup"><span data-stu-id="901da-132">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 

* <span data-ttu-id="901da-133">取消选中此设置可保留所有版本</span><span class="sxs-lookup"><span data-stu-id="901da-133">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="901da-134">项目的相对导入路径</span><span class="sxs-lookup"><span data-stu-id="901da-134">Project relative import path</span></span>

<span data-ttu-id="901da-135">更改此设置可更新导入时复制功能包的项目文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="901da-135">Change this setting to update project folder path where feature packages are copied on import.</span></span> 

* <span data-ttu-id="901da-136">例如，如果项目文件夹是 C:\GalaxyExplorer，则完全限定的导入路径将为 C:\GalaxyExplorer\Packages\MixedReality 。</span><span class="sxs-lookup"><span data-stu-id="901da-136">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="901da-137">该设置在此版本中是只读的。</span><span class="sxs-lookup"><span data-stu-id="901da-137">This setting is **read-only** in this release.</span></span> <span data-ttu-id="901da-138">将来的版本允许配置此设置。</span><span class="sxs-lookup"><span data-stu-id="901da-138">Future releases may make this setting configurable.</span></span>

## <a name="early-access-settings"></a><span data-ttu-id="901da-139">抢先访问设置</span><span class="sxs-lookup"><span data-stu-id="901da-139">Early Access settings</span></span>

![抢先访问设置](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a><span data-ttu-id="901da-141">在删除抢先访问计划之前要求确认</span><span class="sxs-lookup"><span data-stu-id="901da-141">Ask for confirmation before removing an early access program</span></span>

<span data-ttu-id="901da-142">此设置确定在每次删除抢先访问计划时是否显示提示。</span><span class="sxs-lookup"><span data-stu-id="901da-142">This setting determines if a prompt will be displayed each time an early access program is removed.</span></span>

### <a name="my-previews"></a><span data-ttu-id="901da-143">我的预览</span><span class="sxs-lookup"><span data-stu-id="901da-143">My previews</span></span>

<span data-ttu-id="901da-144">已注册的抢先访问计划的列表。</span><span class="sxs-lookup"><span data-stu-id="901da-144">The list of registered early access programs.</span></span> <span data-ttu-id="901da-145">使用`Add`、`Edit`和`Remove`来管理已注册的计划的集合。</span><span class="sxs-lookup"><span data-stu-id="901da-145">Use the `Add`, `Edit` and `Remove` to manage the collection of registered programs.</span></span>

## <a name="diagnostic-settings"></a><span data-ttu-id="901da-146">诊断设置</span><span class="sxs-lookup"><span data-stu-id="901da-146">Diagnostic settings</span></span>

![诊断设置](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a><span data-ttu-id="901da-148">日志文件</span><span class="sxs-lookup"><span data-stu-id="901da-148">Log file</span></span>

<span data-ttu-id="901da-149">显示诊断日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="901da-149">Displays the path to the diagnostic log file.</span></span>

## <a name="see-also"></a><span data-ttu-id="901da-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="901da-150">See also</span></span>

- [<span data-ttu-id="901da-151">欢迎使用混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="901da-151">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)