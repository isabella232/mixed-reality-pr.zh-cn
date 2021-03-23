---
title: 配置混合现实功能工具
description: 了解如何从面向 HoloLens 和 VR 开发的混合现实功能工具中下载并安装混合现实工具包 Unity。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "99243886"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="6b3c3-104">配置混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="6b3c3-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="6b3c3-105">使用混合现实功能工具时，你可以访问三个不同的设置类别并可随意自定义这些类别：</span><span class="sxs-lookup"><span data-stu-id="6b3c3-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="6b3c3-106">下载设置</span><span class="sxs-lookup"><span data-stu-id="6b3c3-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="6b3c3-107">功能设置</span><span class="sxs-lookup"><span data-stu-id="6b3c3-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="6b3c3-108">导入设置</span><span class="sxs-lookup"><span data-stu-id="6b3c3-108">Import settings</span></span>](#import-settings)

![设置](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="6b3c3-110">下载设置</span><span class="sxs-lookup"><span data-stu-id="6b3c3-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="6b3c3-111">覆盖现有包文件</span><span class="sxs-lookup"><span data-stu-id="6b3c3-111">Overwrite existing package files</span></span>

<span data-ttu-id="6b3c3-112">如果启用此设置，则每次获取包文件时都会下载包文件。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="6b3c3-113">**建议将此选项保留为禁用状态以减少网络带宽使用量**</span><span class="sxs-lookup"><span data-stu-id="6b3c3-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="6b3c3-114">默认情况下，不会重新下载以前获取的包文件</span><span class="sxs-lookup"><span data-stu-id="6b3c3-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="6b3c3-115">包缓存</span><span class="sxs-lookup"><span data-stu-id="6b3c3-115">Package cache</span></span>

<span data-ttu-id="6b3c3-116">更改此设置可更新下载功能包的位置。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="6b3c3-117">该设置在此版本中是只读的。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="6b3c3-118">将来的版本允许配置此设置。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="6b3c3-119">功能设置</span><span class="sxs-lookup"><span data-stu-id="6b3c3-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="6b3c3-120">包括预览版本</span><span class="sxs-lookup"><span data-stu-id="6b3c3-120">Include preview releases</span></span>

<span data-ttu-id="6b3c3-121">启用此设置可获取预览版本。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="6b3c3-122">默认情况下，不会在混合现实功能工具中显示预览版本</span><span class="sxs-lookup"><span data-stu-id="6b3c3-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="6b3c3-123">预览版本定义为在包版本中包含“-preview”指定。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="6b3c3-124">导入设置</span><span class="sxs-lookup"><span data-stu-id="6b3c3-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="6b3c3-125">替换现有包文件</span><span class="sxs-lookup"><span data-stu-id="6b3c3-125">Replace existing package files</span></span>

<span data-ttu-id="6b3c3-126">默认情况下，混合现实功能工具会删除正在导入的包的以前副本，以减少文件大小和不必要的计算。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="6b3c3-127">取消选中此设置可保留所有版本</span><span class="sxs-lookup"><span data-stu-id="6b3c3-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="6b3c3-128">项目的相对导入路径</span><span class="sxs-lookup"><span data-stu-id="6b3c3-128">Project relative import path</span></span>

<span data-ttu-id="6b3c3-129">更改此设置可更新导入时复制功能包的项目文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="6b3c3-130">例如，如果项目文件夹是 C:\GalaxyExplorer，则完全限定的导入路径将为 C:\GalaxyExplorer\Packages\MixedReality 。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="6b3c3-131">该设置在此版本中是只读的。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="6b3c3-132">将来的版本允许配置此设置。</span><span class="sxs-lookup"><span data-stu-id="6b3c3-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b3c3-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b3c3-133">See also</span></span>

- [<span data-ttu-id="6b3c3-134">欢迎使用混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="6b3c3-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)