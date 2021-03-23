---
title: 授权项目更改
description: 了解如何授权对面向 HoloLens 和 VR 开发的混合现实功能工具进行项目更改。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230753"
---
# <a name="authorizing-project-changes"></a><span data-ttu-id="b2b59-104">授权项目更改</span><span class="sxs-lookup"><span data-stu-id="b2b59-104">Authorizing project changes</span></span>

<span data-ttu-id="b2b59-105">在修改 Unity 项目之前，需要查看和批准对清单和项目文件所做的更改：</span><span class="sxs-lookup"><span data-stu-id="b2b59-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![请求授权](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="b2b59-107">file:///</span><span class="sxs-lookup"><span data-stu-id="b2b59-107">Manifest</span></span>

<span data-ttu-id="b2b59-108">可以在左侧的“清单”列中查看建议的清单更改。</span><span class="sxs-lookup"><span data-stu-id="b2b59-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="b2b59-109">该内容与将写入项目清单 (Packages/manifest.json) 的内容完全相同：</span><span class="sxs-lookup"><span data-stu-id="b2b59-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![清单预览](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="b2b59-111">要复制到项目中的文件</span><span class="sxs-lookup"><span data-stu-id="b2b59-111">Files to be copied into the project</span></span>

<span data-ttu-id="b2b59-112">右侧的“要复制到项目中的文件”部分列出了将复制到 Unity 项目中的特定功能包文件：</span><span class="sxs-lookup"><span data-stu-id="b2b59-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![包含要复制的文件的清单预览](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="b2b59-114">比较清单</span><span class="sxs-lookup"><span data-stu-id="b2b59-114">Compare manifests</span></span>

<span data-ttu-id="b2b59-115">可通过选择“比较”来查看所有建议更改的详细并排比较：</span><span class="sxs-lookup"><span data-stu-id="b2b59-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![比较清单](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="b2b59-117">批准更改</span><span class="sxs-lookup"><span data-stu-id="b2b59-117">Approving changes</span></span>

<span data-ttu-id="b2b59-118">建议的更改获得批准后，所列文件将被复制到 Unity 项目中，并将更新清单，使其包含对这些文件的引用。</span><span class="sxs-lookup"><span data-stu-id="b2b59-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="b2b59-119">应将功能包 (\*.tgz) 文件添加到源代码管理。</span><span class="sxs-lookup"><span data-stu-id="b2b59-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="b2b59-120">它们使用相对路径进行引用，使开发团队能够轻松共享功能和清单更改。</span><span class="sxs-lookup"><span data-stu-id="b2b59-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="b2b59-121">在修改过程中，将对当前 manifest.json 文件进行备份。</span><span class="sxs-lookup"><span data-stu-id="b2b59-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2b59-122">查看清单备份时，最早的备份将称为 manifest.json.backup。</span><span class="sxs-lookup"><span data-stu-id="b2b59-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="b2b59-123">后续的新备份将使用从零 (0) 开始的数字值进行批注。</span><span class="sxs-lookup"><span data-stu-id="b2b59-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="b2b59-124">返回到上一步骤</span><span class="sxs-lookup"><span data-stu-id="b2b59-124">Going back to the previous step</span></span>

<span data-ttu-id="b2b59-125">如需对功能选择进行更改，请单击“返回”，返回到[导入](importing-features.md)步骤。</span><span class="sxs-lookup"><span data-stu-id="b2b59-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2b59-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2b59-126">See also</span></span>

- [<span data-ttu-id="b2b59-127">欢迎使用混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="b2b59-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="b2b59-128">导入选定包</span><span class="sxs-lookup"><span data-stu-id="b2b59-128">Importing selected packages</span></span>](importing-features.md)
