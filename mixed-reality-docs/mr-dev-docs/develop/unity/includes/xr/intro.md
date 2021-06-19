---
ms.openlocfilehash: ca3589364fb27c3f8087572113f09e48d30e087e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394571"
---
# <a name="openxr"></a>[<span data-ttu-id="78683-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="78683-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="78683-102">混合现实 OpenXR 插件 **是 Microsoft** 针对 Unity 2020 LTS 或更高版本的建议。</span><span class="sxs-lookup"><span data-stu-id="78683-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="78683-103">随着将来开发新功能，它们只会包含在混合现实 OpenXR 插件中。</span><span class="sxs-lookup"><span data-stu-id="78683-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="78683-104">混合现实 OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。</span><span class="sxs-lookup"><span data-stu-id="78683-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="78683-105">这样，你可以编写一次光线广播代码，该代码HoloLens 2 ARCore/ARKit 手机和平板电脑。</span><span class="sxs-lookup"><span data-stu-id="78683-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="78683-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="78683-106">Prerequisites</span></span> 

* <span data-ttu-id="78683-107">用于 [开发HoloLens 2工具](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="78683-107">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="78683-108">最新的 Unity 2020.3 LTS， (2020.3.8f1 或) </span><span class="sxs-lookup"><span data-stu-id="78683-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="78683-109">最低版本</span><span class="sxs-lookup"><span data-stu-id="78683-109">Minimum versions</span></span>

<span data-ttu-id="78683-110">本页中的说明将设置下面列出的最新、最大的 Unity 和 OpenXR 要求：</span><span class="sxs-lookup"><span data-stu-id="78683-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="78683-111">最新的 Unity OpenXR 插件， (1.2 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="78683-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="78683-112">最新的混合现实 OpenXR 插件， (版本 1.0.0 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="78683-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="78683-113">**(可选)** 建议使用最新的 MRTK (2.7 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="78683-113">**(Optional)** Latest MRTK, (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="78683-114">**(可选)** 最新的通用呈现管道包， (版本 10.5.1 或更高版本) </span><span class="sxs-lookup"><span data-stu-id="78683-114">**(Optional)** Latest Universal Render Pipeline package, (we recommend version 10.5.1 or later)</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="78683-115">如果要在 Windows 电脑上生成 VR 应用程序，则混合现实 OpenXR 插件不一定是必需的。</span><span class="sxs-lookup"><span data-stu-id="78683-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="78683-116">但是，如果要为 HP Reverb G2 控制器自定义控制器映射，或构建适用于 HOLOLENS 2 和 VR 头戴显示设备的应用，需要安装插件。</span><span class="sxs-lookup"><span data-stu-id="78683-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="78683-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="78683-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="78683-118">Microsoft 不建议将 Windows XR 插件用于 Unity 2020 中任何新项目。</span><span class="sxs-lookup"><span data-stu-id="78683-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="78683-119">但是，如果使用的是 Unity 2019，并且需要 AR Foundation 2.0 来与 ARCore/ARKit 设备兼容，则此插件会启用该支持。</span><span class="sxs-lookup"><span data-stu-id="78683-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78683-120">在 Unity 2019 中使用此插件不支持 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="78683-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="78683-121">旧版 XR</span><span class="sxs-lookup"><span data-stu-id="78683-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="78683-122">如果你仍在使用 Unity 2019 或更早版本，Microsoft 建议使用旧版内置 XR 支持。</span><span class="sxs-lookup"><span data-stu-id="78683-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="78683-123">虽然 Windows XR 插件在 Unity 2019 上正常运行，但不建议这样做，因为不支持 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="78683-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>