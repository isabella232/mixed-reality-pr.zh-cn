---
title: 表面
description: 了解如何在 Surfaces 示例应用中使用视觉对象、音频和表达式手部跟踪创建触手跟踪。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality， 设计， 示例应用， 控件， MRTK， 混合现实工具包， Unity， 示例应用， 示例应用， 开源， Microsoft Store， HoloLens， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: 28f8bc1e1f30573936067a83b1ad26133c23c5b8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743391"
---
# <a name="surfaces"></a><span data-ttu-id="5b80f-104">表面</span><span class="sxs-lookup"><span data-stu-id="5b80f-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="5b80f-105">本文讨论我们在混合现实设计实验室中创建的探索示例，我们在该实验室[](https://github.com/Microsoft/MRDesignLabs_Unity)中分享有关混合现实应用开发的学习和建议。</span><span class="sxs-lookup"><span data-stu-id="5b80f-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="5b80f-106">随着我们进行新的发现，与设计相关的文章和代码将不断发展。</span><span class="sxs-lookup"><span data-stu-id="5b80f-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="5b80f-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  是 Microsoft 混合现实设计实验室提供的开源示例应用。</span><span class="sxs-lookup"><span data-stu-id="5b80f-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="5b80f-108">它探索了如何使用视觉对象、音频和完全表达的手动跟踪创建触手部。</span><span class="sxs-lookup"><span data-stu-id="5b80f-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![表面](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="5b80f-110">演示视频</span><span class="sxs-lookup"><span data-stu-id="5b80f-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="5b80f-111">使用 HoloLens 2 记录混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="5b80f-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="5b80f-112">关于应用</span><span class="sxs-lookup"><span data-stu-id="5b80f-112">About the app</span></span>

<span data-ttu-id="5b80f-113">Surfaces 演示如何使用混合现实工具包 (MRTK) 输入系统和构建基块来创建适用于 HoloLens 2 的应用体验。</span><span class="sxs-lookup"><span data-stu-id="5b80f-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="5b80f-114">在此项目中，可以找到以下示例：</span><span class="sxs-lookup"><span data-stu-id="5b80f-114">In this project, you can find the examples of:</span></span>

- <span data-ttu-id="5b80f-115">使用 MRTK 的 [输入系统](/windows/mixed-reality/mrtk-unity/features/input/overview)，特别是手部/联合跟踪。</span><span class="sxs-lookup"><span data-stu-id="5b80f-115">Use MRTK's [Input System](/windows/mixed-reality/mrtk-unity/features/input/overview), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="5b80f-116">使用 MRTK 的标准 [着色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) 进行性能图形处理。</span><span class="sxs-lookup"><span data-stu-id="5b80f-116">Use MRTK's [Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) for performant graphics.</span></span>

<span data-ttu-id="5b80f-117">可以使用此项目的组件创建自己的混合现实应用体验。</span><span class="sxs-lookup"><span data-stu-id="5b80f-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="5b80f-118">MR Dev Days 2020 - 从 MR Surfaces 应用学习</span><span class="sxs-lookup"><span data-stu-id="5b80f-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="5b80f-119">从 MR Surfaces 应用学习</span><span class="sxs-lookup"><span data-stu-id="5b80f-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="5b80f-120">MRDL Surfaces 应用背后的高级设计人员 Lars Simkins 讨论应用的设计故事和技术亮点。</span><span class="sxs-lookup"><span data-stu-id="5b80f-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="5b80f-121">GitHub 上的项目存储库</span><span class="sxs-lookup"><span data-stu-id="5b80f-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="5b80f-122">从 Microsoft Store HoloLens 2 下载应用</span><span class="sxs-lookup"><span data-stu-id="5b80f-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="5b80f-123"> (应用仅在 HoloLens 2) </span><span class="sxs-lookup"><span data-stu-id="5b80f-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="5b80f-124">关于作者</span><span class="sxs-lookup"><span data-stu-id="5b80f-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="5b80f-125"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="5b80f-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="5b80f-126">用户体验设计师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="5b80f-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="5b80f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b80f-127">See also</span></span>

* <span data-ttu-id="5b80f-128">[MRTK 示例中心](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="5b80f-128">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="5b80f-129">[表面](sampleapp-surfaces.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="5b80f-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="5b80f-130">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="5b80f-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="5b80f-131">星系探索者 2.0</span><span class="sxs-lookup"><span data-stu-id="5b80f-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)