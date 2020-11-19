---
title: 关于 Maquette
description: Maquette 及其功能简介。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality，Maquette，原型设计，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935414"
---
# <a name="about-maquette"></a><span data-ttu-id="dbbed-104">关于 Maquette</span><span class="sxs-lookup"><span data-stu-id="dbbed-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="dbbed-105">![徽标 ](../images/MaquetteIcon.png) MaquetteScript 简介</span><span class="sxs-lookup"><span data-stu-id="dbbed-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="dbbed-106">Maquette 集成了标准 ECMA 5.1 Javascript，实现 Maquette 场景和对象（可在 VSCode 中进行编辑和执行）的交互。</span><span class="sxs-lookup"><span data-stu-id="dbbed-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="dbbed-107">对象的属性是从脚本、调用的对象方法以及对象和系统事件现场中读取和设置公开的。</span><span class="sxs-lookup"><span data-stu-id="dbbed-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="dbbed-108">脚本还可以通过脚本访问的系统对象与 Maquette 本身交互。</span><span class="sxs-lookup"><span data-stu-id="dbbed-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="dbbed-109">用户可与之交互的各种 UI 控件都是系统的一部分。</span><span class="sxs-lookup"><span data-stu-id="dbbed-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="dbbed-110">当在 Maquette 中创作或从脚本内创建和管理时，可添加这些项。</span><span class="sxs-lookup"><span data-stu-id="dbbed-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="dbbed-111">具有这些元素的用户交互事件 (数据输入、点击等) 也会公开给作为事件编写脚本。</span><span class="sxs-lookup"><span data-stu-id="dbbed-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="dbbed-112">通过这些新增功能，可以构建简单易用的场景，从试验到数据可视化，到探索的混合现实用户方案，到在 AR 或 VR 中充分认识到的体验。</span><span class="sxs-lookup"><span data-stu-id="dbbed-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="dbbed-113">60 second'ish 视频</span><span class="sxs-lookup"><span data-stu-id="dbbed-113">60 second'ish video</span></span>
* <span data-ttu-id="dbbed-114">输入标题卡</span><span class="sxs-lookup"><span data-stu-id="dbbed-114">Entry Title Card</span></span>
  * <span data-ttu-id="dbbed-115">在 Maquette 中创建交互式混合现实内容</span><span class="sxs-lookup"><span data-stu-id="dbbed-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="dbbed-116">脚本/交互/UI 系统</span><span class="sxs-lookup"><span data-stu-id="dbbed-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="dbbed-117">欢迎按团队或视频标题进行欢迎？</span><span class="sxs-lookup"><span data-stu-id="dbbed-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="dbbed-118">说明</span><span class="sxs-lookup"><span data-stu-id="dbbed-118">explaining:</span></span>
  * <span data-ttu-id="dbbed-119">通过编写脚本来支持创建交互式 MR 内容的推理</span><span class="sxs-lookup"><span data-stu-id="dbbed-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="dbbed-120">了解如何在广泛的画笔笔划中使用它</span><span class="sxs-lookup"><span data-stu-id="dbbed-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="dbbed-121">编写 vingette 的操作脚本</span><span class="sxs-lookup"><span data-stu-id="dbbed-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="dbbed-122">组合对话框</span><span class="sxs-lookup"><span data-stu-id="dbbed-122">Composing dialog box</span></span>
  * <span data-ttu-id="dbbed-123">构建大纲 (的应用程序演示) </span><span class="sxs-lookup"><span data-stu-id="dbbed-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="dbbed-124">在 photogrammetry 模型中撰写</span><span class="sxs-lookup"><span data-stu-id="dbbed-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="dbbed-125">与故障排除指南交互</span><span class="sxs-lookup"><span data-stu-id="dbbed-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="dbbed-126">在 VSCode 中调试脚本的屏幕视图</span><span class="sxs-lookup"><span data-stu-id="dbbed-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="dbbed-127">从场景中的对象获取脚本的访问权限</span><span class="sxs-lookup"><span data-stu-id="dbbed-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="dbbed-128">等等 .。。</span><span class="sxs-lookup"><span data-stu-id="dbbed-128">Etc...</span></span>
* <span data-ttu-id="dbbed-129">结束时的摘要卡</span><span class="sxs-lookup"><span data-stu-id="dbbed-129">Summary Title card at end</span></span>
  * <span data-ttu-id="dbbed-130">链接到 Maquette</span><span class="sxs-lookup"><span data-stu-id="dbbed-130">Link to Maquette</span></span>
  * <span data-ttu-id="dbbed-131">在何处开始编写脚本</span><span class="sxs-lookup"><span data-stu-id="dbbed-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="dbbed-132">公告/状态/社区</span><span class="sxs-lookup"><span data-stu-id="dbbed-132">Announcements/status/community</span></span>
  * <span data-ttu-id="dbbed-133">期待查看可以执行/提交 ( 操作的内容 ) </span><span class="sxs-lookup"><span data-stu-id="dbbed-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="dbbed-134">反馈和我们如何更好地为你提供服务</span><span class="sxs-lookup"><span data-stu-id="dbbed-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="dbbed-135">入门</span><span class="sxs-lookup"><span data-stu-id="dbbed-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="dbbed-136">示例和示例应用</span><span class="sxs-lookup"><span data-stu-id="dbbed-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="dbbed-137">支持</span><span class="sxs-lookup"><span data-stu-id="dbbed-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="dbbed-138">向我们发送反馈</span><span class="sxs-lookup"><span data-stu-id="dbbed-138">Send us feedback</span></span>

<span data-ttu-id="dbbed-139">我们期待收到你的体验和结果。</span><span class="sxs-lookup"><span data-stu-id="dbbed-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="dbbed-140">反馈、建议和 bug 报告始终欢迎使用！</span><span class="sxs-lookup"><span data-stu-id="dbbed-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="dbbed-141"><链接？ ></span><span class="sxs-lookup"><span data-stu-id="dbbed-141"><Link?></span></span>