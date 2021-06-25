---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906935"
---
# <a name="openxr"></a>[<span data-ttu-id="5fd50-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="5fd50-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="5fd50-102">Mixed Reality OpenXR 插件是 Microsoft 针对 Unity 2020 LTS 或更高版本的 **建议** 。</span><span class="sxs-lookup"><span data-stu-id="5fd50-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="5fd50-103">随着将来开发新功能，这些新功能将仅包括在混合现实 OpenXR 插件中。</span><span class="sxs-lookup"><span data-stu-id="5fd50-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="5fd50-104">Mixed Reality OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。</span><span class="sxs-lookup"><span data-stu-id="5fd50-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="5fd50-105">这样一来，你就可以编写 raycasting 代码一次，然后跨 HoloLens 2 和 ARCore/ARKit 手机和平板电脑。</span><span class="sxs-lookup"><span data-stu-id="5fd50-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5fd50-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="5fd50-106">Prerequisites</span></span> 

* <span data-ttu-id="5fd50-107">[适用于 HoloLens 2 开发的](../../../install-the-tools.md?tabs=unity#installation-checklist)最新工具</span><span class="sxs-lookup"><span data-stu-id="5fd50-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="5fd50-108">最新 Unity 2020.3 LTS， (建议 2020.3.8 f1 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="5fd50-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="5fd50-109">最低版本</span><span class="sxs-lookup"><span data-stu-id="5fd50-109">Minimum versions</span></span>

<span data-ttu-id="5fd50-110">此页中的说明将设置以下列出的最新和最大 Unity 和 OpenXR 要求：</span><span class="sxs-lookup"><span data-stu-id="5fd50-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="5fd50-111">最新 Unity OpenXR 插件 (建议1.2 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="5fd50-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="5fd50-112">最新混合现实 OpenXR 插件， (建议1.0.0 版或更高版本) </span><span class="sxs-lookup"><span data-stu-id="5fd50-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="5fd50-113">**(可选)** 最新 MRTK， (建议2.7 版或更高版本) </span><span class="sxs-lookup"><span data-stu-id="5fd50-113">**(Optional)** Latest MRTK, (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="5fd50-114">**(可选)** 最新的通用呈现管道包， (建议10.5.1 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="5fd50-114">**(Optional)** Latest Universal Render Pipeline package, (we recommend version 10.5.1 or later)</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="5fd50-115">如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="5fd50-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="5fd50-116">但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。</span><span class="sxs-lookup"><span data-stu-id="5fd50-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="5fd50-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="5fd50-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="5fd50-118">Microsoft 不建议对 Unity 2020 中的任何新项目使用 Windows XR 插件。</span><span class="sxs-lookup"><span data-stu-id="5fd50-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="5fd50-119">但是，如果你使用的是 Unity 2019，并且需要 AR Foundation 2.0 才能兼容 ARCore/ARKit 设备，此插件会启用该支持。</span><span class="sxs-lookup"><span data-stu-id="5fd50-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fd50-120">在 Unity 2019 中使用此插件不支持 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="5fd50-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="5fd50-121">旧版 XR</span><span class="sxs-lookup"><span data-stu-id="5fd50-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="5fd50-122">如果你仍在 Unity 2019 或更早版本，Microsoft 建议使用旧的内置 XR 支持。</span><span class="sxs-lookup"><span data-stu-id="5fd50-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="5fd50-123">尽管 Windows XR 插件在 Unity 2019 上正常运行，但不建议这样做，因为不支持 Azure 空间锚。</span><span class="sxs-lookup"><span data-stu-id="5fd50-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>