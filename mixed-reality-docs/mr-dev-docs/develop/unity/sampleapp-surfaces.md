---
title: 表面
description: 了解如何在表面示例应用中创建 tactile sensations，并在视觉对象、音频和有表述的手写跟踪中进行演示。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality，设计，示例应用，控件，MRTK，混合现实工具包，Unity，示例应用，示例应用，开源，Microsoft Store，HoloLens，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: bd4ecabda749d4a2760fe0225caf7c53966a1b98
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759713"
---
# <a name="surfaces"></a><span data-ttu-id="6a54b-104">表面</span><span class="sxs-lookup"><span data-stu-id="6a54b-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="6a54b-105">本文讨论了我们在 [混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)中创建的探索示例，这是我们与混合现实应用开发的知识和建议。</span><span class="sxs-lookup"><span data-stu-id="6a54b-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="6a54b-106">我们设计相关的文章和代码将随着我们的新发现而发展。</span><span class="sxs-lookup"><span data-stu-id="6a54b-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="6a54b-107">[表面](https://github.com/microsoft/MRDL_Unity_Surfaces)  是 Microsoft 混合现实设计实验室的开源示例应用。</span><span class="sxs-lookup"><span data-stu-id="6a54b-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="6a54b-108">本文探讨了如何使用视觉、音频和完全清晰的手写跟踪来创建 tactile 成名。</span><span class="sxs-lookup"><span data-stu-id="6a54b-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![表面](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="6a54b-110">演示视频</span><span class="sxs-lookup"><span data-stu-id="6a54b-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="6a54b-111">使用混合现实捕获记录了 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6a54b-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="6a54b-112">关于应用</span><span class="sxs-lookup"><span data-stu-id="6a54b-112">About the app</span></span>

<span data-ttu-id="6a54b-113">图面演示了如何使用混合现实工具包 (MRTK) 的输入系统和构建基块，为 HoloLens 2 创建应用体验。</span><span class="sxs-lookup"><span data-stu-id="6a54b-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="6a54b-114">在此项目中，可以找到以下示例：</span><span class="sxs-lookup"><span data-stu-id="6a54b-114">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="6a54b-115">使用 MRTK 的 [输入系统](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)，尤其是手动/联合跟踪。</span><span class="sxs-lookup"><span data-stu-id="6a54b-115">Use MRTK's [Input System](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="6a54b-116">使用 MRTK 的 [标准着色器](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mrtk-standard-shader.md) 来实现高性能图形。</span><span class="sxs-lookup"><span data-stu-id="6a54b-116">Use MRTK's [Standard Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mrtk-standard-shader.md) for performant graphics.</span></span>

<span data-ttu-id="6a54b-117">可以使用此项目的组件来创建自己的混合现实应用体验。</span><span class="sxs-lookup"><span data-stu-id="6a54b-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="6a54b-118">MR 开发人员 2020-知识</span><span class="sxs-lookup"><span data-stu-id="6a54b-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="6a54b-119">从 MR 表面应用知识</span><span class="sxs-lookup"><span data-stu-id="6a54b-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="6a54b-120">Lars Simkins，MRDL surface 应用后的高级设计人员将讨论应用的设计故事和技术要点。</span><span class="sxs-lookup"><span data-stu-id="6a54b-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="6a54b-121">GitHub 上的项目存储库</span><span class="sxs-lookup"><span data-stu-id="6a54b-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="6a54b-122">从 HoloLens 2 Microsoft Store 下载应用</span><span class="sxs-lookup"><span data-stu-id="6a54b-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="6a54b-123"> (应用仅在 HoloLens 2 上可用) </span><span class="sxs-lookup"><span data-stu-id="6a54b-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="6a54b-124">关于作者</span><span class="sxs-lookup"><span data-stu-id="6a54b-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="6a54b-125"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="6a54b-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="6a54b-126">用户体验设计师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="6a54b-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="6a54b-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a54b-127">See also</span></span>

* <span data-ttu-id="6a54b-128">[MRTK 示例中心](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/example-hub.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="6a54b-128">[MRTK Examples Hub](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/example-hub.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="6a54b-129">[表面](sampleapp-surfaces.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="6a54b-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="6a54b-130">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="6a54b-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="6a54b-131">星系探索者 2.0</span><span class="sxs-lookup"><span data-stu-id="6a54b-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
