---
title: 使用 Unity 包管理器
description: 在 Unity 程序包管理器中使用 MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK 包，
ms.openlocfilehash: 524783c48b82722aec26648ea54477a6c7bcd4ae
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177320"
---
# <a name="using-the-unity-package-manager"></a><span data-ttu-id="c2d37-104">使用 Unity 包管理器</span><span class="sxs-lookup"><span data-stu-id="c2d37-104">Using the Unity Package Manager</span></span>

<span data-ttu-id="c2d37-105">从版本2.5.0 开始，使用[混合现实功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)，在使用 unity 2019.4 和更高版本时，Microsoft Mixed reality Toolkit 与 unity 程序包管理器 (UPM) 集成。</span><span class="sxs-lookup"><span data-stu-id="c2d37-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="c2d37-106">使用混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="c2d37-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="c2d37-107">如欢迎使用 [混合现实功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 中所述，你可以使用 [此链接](https://aka.ms/MRFeatureTool)下载该工具。</span><span class="sxs-lookup"><span data-stu-id="c2d37-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2d37-108">如果项目的清单 `Microsoft Mixed Reality` 在部分中有一个条目 `scopedRegistries` ，则建议将其删除。</span><span class="sxs-lookup"><span data-stu-id="c2d37-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="c2d37-109">若要删除已配置的作用域注册表，请使用 `Edit`  >  `Project Settings`  >  `Package Manager` 。</span><span class="sxs-lookup"><span data-stu-id="c2d37-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![删除作用域内注册表](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="c2d37-111">查找功能时，MRTK 包会显示在 `Mixed Reality Toolkit` 标题下方。</span><span class="sxs-lookup"><span data-stu-id="c2d37-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![发现功能](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="c2d37-113">选择功能时，不需要考虑所需的依赖项，该工具会自动下载并将其集成到项目中。</span><span class="sxs-lookup"><span data-stu-id="c2d37-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![必需的依赖项](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="c2d37-115">通过 Unity 程序包管理器管理混合现实功能</span><span class="sxs-lookup"><span data-stu-id="c2d37-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="c2d37-116">一旦将混合现实 Toolkit 程序包添加到了包清单中，就可以使用 Unity 程序包管理器用户界面对其进行管理。</span><span class="sxs-lookup"><span data-stu-id="c2d37-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![MRTK Foundation UPM 包](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="c2d37-118">如果使用 Unity 程序包管理器删除混合现实 Toolkit 包，则必须使用[前面介绍的步骤](#using-the-mixed-reality-feature-tool)重新添加此包。</span><span class="sxs-lookup"><span data-stu-id="c2d37-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="c2d37-119">使用混合现实 Toolkit 示例</span><span class="sxs-lookup"><span data-stu-id="c2d37-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="c2d37-120">与使用资产包时 () 文件不同， `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` 不会自动导入示例场景和资产。</span><span class="sxs-lookup"><span data-stu-id="c2d37-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="c2d37-121">若要利用一个或多个示例，请使用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="c2d37-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="c2d37-122">在 Unity 编辑器中，导航到 `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="c2d37-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="c2d37-123">在包列表中，选择 `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="c2d37-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="c2d37-124">在列表中找到所需的示例 (s) `Samples`</span><span class="sxs-lookup"><span data-stu-id="c2d37-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="c2d37-125">单击 `Import into Project`</span><span class="sxs-lookup"><span data-stu-id="c2d37-125">Click `Import into Project`</span></span>

![导入示例](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="c2d37-127">更新示例包时，Unity 提供了更新导入的示例的选项。</span><span class="sxs-lookup"><span data-stu-id="c2d37-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="c2d37-128">更新导入的示例将覆盖对该示例和关联的资产所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="c2d37-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2d37-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2d37-129">See Also</span></span>

- [<span data-ttu-id="c2d37-130">混合现实 Toolkit 包</span><span class="sxs-lookup"><span data-stu-id="c2d37-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)
