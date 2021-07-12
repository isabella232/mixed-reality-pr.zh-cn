---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603701"
---
# <a name="openxr"></a>[<span data-ttu-id="170b4-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="170b4-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="170b4-102">混合现实 OpenXR 插件 **是 Microsoft** 针对 **Unity 2020 LTS 或** 更高版本的建议。</span><span class="sxs-lookup"><span data-stu-id="170b4-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for **Unity 2020 LTS** or later.</span></span> <span data-ttu-id="170b4-103">随着将来开发新功能，它们只会包含在混合现实 OpenXR 插件中。</span><span class="sxs-lookup"><span data-stu-id="170b4-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="170b4-104">混合现实 OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。</span><span class="sxs-lookup"><span data-stu-id="170b4-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="170b4-105">这样，你可以编写一次光线广播代码，该代码HoloLens 2 ARCore/ARKit 手机和平板电脑。</span><span class="sxs-lookup"><span data-stu-id="170b4-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="170b4-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="170b4-106">Prerequisites</span></span> 

* <span data-ttu-id="170b4-107">用于[开发HoloLens 2工具](../../../install-the-tools.md?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="170b4-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="170b4-108">最新 Unity 2020.3 LTS：版本 2020.3.8f1 或更高版本</span><span class="sxs-lookup"><span data-stu-id="170b4-108">Latest Unity 2020.3 LTS: version 2020.3.8f1 or later</span></span>

### <a name="recommended-package-versions"></a><span data-ttu-id="170b4-109">建议的包版本</span><span class="sxs-lookup"><span data-stu-id="170b4-109">Recommended package versions</span></span>

<span data-ttu-id="170b4-110">本页中的说明将设置核心 Unity OpenXR 包，这些包HoloLens 2或Windows Mixed Reality应用：</span><span class="sxs-lookup"><span data-stu-id="170b4-110">The instructions in this page will set you up with the core Unity OpenXR packages required to deploy HoloLens 2 or Windows Mixed Reality apps:</span></span>

* <span data-ttu-id="170b4-111">Unity OpenXR 插件：版本 1.2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="170b4-111">Unity OpenXR plugin: version 1.2 or later</span></span>
* <span data-ttu-id="170b4-112">混合现实 OpenXR 插件：版本 1.0.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="170b4-112">Mixed Reality OpenXR plugin: version 1.0.0 or later</span></span>

<span data-ttu-id="170b4-113">如果在项目中使用以下包，则需要确保至少使用下面列出的最低版本：</span><span class="sxs-lookup"><span data-stu-id="170b4-113">If you use the following packages in your project, you will need to ensure that you use at least the minimum versions listed below:</span></span>

* <span data-ttu-id="170b4-114">MRTK：版本 2.7.2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="170b4-114">MRTK: version 2.7.2 or later</span></span>
* <span data-ttu-id="170b4-115">AR Foundation：版本 4.1.1 或更高版本</span><span class="sxs-lookup"><span data-stu-id="170b4-115">AR Foundation: version 4.1.1 or later</span></span>
* <span data-ttu-id="170b4-116">URP (通用) 管道：版本 10.5.1 或更高版本</span><span class="sxs-lookup"><span data-stu-id="170b4-116">Universal Render Pipeline (URP): version 10.5.1 or later</span></span>
* <span data-ttu-id="170b4-117">Azure 空间定位点：版本 2.10 或更高版本</span><span class="sxs-lookup"><span data-stu-id="170b4-117">Azure Spatial Anchors: version 2.10 or later</span></span>
* <span data-ttu-id="170b4-118">Azure 远程渲染：版本 1.0.15 或更高版本</span><span class="sxs-lookup"><span data-stu-id="170b4-118">Azure Remote Rendering: version 1.0.15 or later</span></span>

> [!NOTE]
> <span data-ttu-id="170b4-119">如果要在电脑上生成 VR Windows，则不严格要求使用混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="170b4-119">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not strictly required.</span></span> <span data-ttu-id="170b4-120">但是，如果要为 HP Reverb G2 控制器设置输入绑定，或构建在 HOLOLENS 2 和 VR 头戴显示设备上运行的应用，需要安装插件。</span><span class="sxs-lookup"><span data-stu-id="170b4-120">However, you'll want to install the plugin if you're setting up input bindings for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="170b4-121">WindowsXR</span><span class="sxs-lookup"><span data-stu-id="170b4-121">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="170b4-122">Microsoft 不建议将 Windows XR 插件用于 Unity 2020 中的任何新项目。</span><span class="sxs-lookup"><span data-stu-id="170b4-122">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>  <span data-ttu-id="170b4-123">应改为使用混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="170b4-123">Instead, you should use the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="170b4-124">但是，如果使用的是 Unity 2019，并且需要 AR Foundation 2.0 来与 ARCore/ARKit 设备兼容，则此插件会启用该支持。</span><span class="sxs-lookup"><span data-stu-id="170b4-124">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="170b4-125">在 Unity 2019 中使用此插件与 Azure 空间定位点不兼容。</span><span class="sxs-lookup"><span data-stu-id="170b4-125">Using this plugin in Unity 2019 is not compatible with Azure Spatial Anchors.</span></span>

# <a name="legacy-xr"></a>[<span data-ttu-id="170b4-126">旧版 XR</span><span class="sxs-lookup"><span data-stu-id="170b4-126">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="170b4-127">如果你仍在使用 Unity **2019** 或更早版本，Microsoft 建议使用旧版 **内置 XR 支持**。</span><span class="sxs-lookup"><span data-stu-id="170b4-127">If you're still on **Unity 2019** or earlier, Microsoft recommends using the **Legacy Built-in XR support**.</span></span>

<span data-ttu-id="170b4-128">虽然 Windows XR 插件在 Unity 2019 上正常运行，但不建议这样做，因为此插件与 Unity 2019 上的 Azure 空间定位点不兼容。</span><span class="sxs-lookup"><span data-stu-id="170b4-128">While the Windows XR plugin is functional on Unity 2019, it's not recommended because this plugin is not compatible with Azure Spatial Anchors on Unity 2019.</span></span>

<span data-ttu-id="170b4-129">如果要启动新项目，建议改为安装 [Unity 2020，](../../choosing-unity-version.md) 然后使用混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="170b4-129">If you're starting a new project, we recommend [installing Unity 2020 instead](../../choosing-unity-version.md) and using the Mixed Reality OpenXR plugin.</span></span>