---
title: 开始设计和原型制作
description: 如果已做好创建方面的准备工作，请了解开始设计和原型制作所需的基本概念。
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 发现, 分发, 索引, 登陆页, 设计, 开发, 教程, 示例应用, 基础知识, 案例研究, 资源, HoloLens 操作指南, 开源项目, 核心概念, 交互, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, HoloLens, MRTK, 混合现实工具包
ms.openlocfilehash: c4d9f9b4c4be1c5012ac8dc84fb55e6c5fa9eaee
ms.sourcegitcommit: 85ba3af69ec2a9056f759bab7b66f79f09a016b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2021
ms.locfileid: "111454760"
---
# <a name="start-designing-and-prototyping"></a><span data-ttu-id="742a9-104">开始设计和原型制作</span><span class="sxs-lookup"><span data-stu-id="742a9-104">Start designing and prototyping</span></span>

![混合现实设计摘要](images/design-hero-image.png)

<span data-ttu-id="742a9-106">混合现实应用程序与当今世界上任何其他应用程序都不同，设计它们是一项很难的工作。</span><span class="sxs-lookup"><span data-stu-id="742a9-106">Mixed Reality applications are unlike anything else in the world today, and designing them is hard work.</span></span> <span data-ttu-id="742a9-107">你不仅要考虑到正在创建的真实世界和虚拟世界的新组合，还必须考虑它们提供的新型用户体验。</span><span class="sxs-lookup"><span data-stu-id="742a9-107">Not only do you have to account for the new combinations of real and virtual worlds you're creating, but also the new user experiences they afford.</span></span> <span data-ttu-id="742a9-108">由于混合现实很大，因此我们在其设计范围内选择了要点，并在下面将它们布置为一系列检查点。</span><span class="sxs-lookup"><span data-stu-id="742a9-108">Since Mixed Reality is a big place, we've selected important points along its design spectrum and laid them out below as a series of checkpoints.</span></span> <span data-ttu-id="742a9-109">这些检查点应该是连续的，但如果你已经有了一定的了解，则可以随时跳转到以下任何部分。</span><span class="sxs-lookup"><span data-stu-id="742a9-109">These are meant to be sequential, but if you've already dipped your feet in feel free to jump to any of the following sections.</span></span> 

<span data-ttu-id="742a9-110">请查看我们的设备概述视频开始入门：</span><span class="sxs-lookup"><span data-stu-id="742a9-110">Take a look at our design overview video to get started:</span></span>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a><span data-ttu-id="742a9-111">设计检查点</span><span class="sxs-lookup"><span data-stu-id="742a9-111">Design checkpoints</span></span>

<span data-ttu-id="742a9-112">使用以下检查点将应用程序创意和概念带入混合现实的世界。</span><span class="sxs-lookup"><span data-stu-id="742a9-112">Use the following checkpoints to bring your application ideas and concepts into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="742a9-113">1.入门</span><span class="sxs-lookup"><span data-stu-id="742a9-113">1. Getting started</span></span>

<span data-ttu-id="742a9-114">与所有历程一样，设计混合现实应用程序的冒险之旅从基础开始。</span><span class="sxs-lookup"><span data-stu-id="742a9-114">Like all journeys, your adventure into designing Mixed Reality applications starts with the basics.</span></span> <span data-ttu-id="742a9-115">我们建议你自行熟悉[什么是混合现实](../discover/mixed-reality.md)以及[什么是全息影像？](../discover/hologram.md)文章，让大脑为沉浸式设计做好准备。</span><span class="sxs-lookup"><span data-stu-id="742a9-115">We recommend familiarizing yourself with the [What is Mixed Reality](../discover/mixed-reality.md) and [What is a hologram?](../discover/hologram.md) articles to get your mind primed for immersive design.</span></span> <span data-ttu-id="742a9-116">完成通读后，你就可以开始混合现实设计历程了！</span><span class="sxs-lookup"><span data-stu-id="742a9-116">Once you've completed your read-through, you'll be ready to start your Mixed Reality design journey!</span></span>

![来自“设计全息影像”应用的入门 GIF](images/HandTracking2.gif)

|  <span data-ttu-id="742a9-118">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="742a9-118">Checkpoint</span></span>  |  <span data-ttu-id="742a9-119">业务成效</span><span class="sxs-lookup"><span data-stu-id="742a9-119">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="742a9-120">扩展设计过程</span><span class="sxs-lookup"><span data-stu-id="742a9-120">Expand your design process</span></span>](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | <span data-ttu-id="742a9-121">亲眼见证从 Microsoft 内外的设计师处收集的混合现实设计过程</span><span class="sxs-lookup"><span data-stu-id="742a9-121">Get a first-hand look at design process for Mixed Reality, gathered from designers inside and outside of Microsoft</span></span> |
| [<span data-ttu-id="742a9-122">混合现实应用的类型</span><span class="sxs-lookup"><span data-stu-id="742a9-122">Types of Mixed Reality apps</span></span>](types-of-mixed-reality-apps.md) | <span data-ttu-id="742a9-123">确定你的应用体验在混合现实范围内的位置</span><span class="sxs-lookup"><span data-stu-id="742a9-123">Decide where your app experience will live on the Mixed Reality spectrum</span></span> |
| [<span data-ttu-id="742a9-124">“设计全息影像”应用</span><span class="sxs-lookup"><span data-stu-id="742a9-124">Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | <span data-ttu-id="742a9-125">了解混合现实 UX 设计的基础知识，只需体验创建出色 HoloLens 应用相关的行为、提示和建议即可（可在 HoloLens 2 中从 Microsoft Store 下载）</span><span class="sxs-lookup"><span data-stu-id="742a9-125">Learn the fundamentals of Mixed Reality UX Design by experiencing with behaviors, tips, and recommendations for creating amazing HoloLens apps (available for download from Microsoft Store in HoloLens 2)</span></span> |
| [<span data-ttu-id="742a9-126">MRTK 中心示例</span><span class="sxs-lookup"><span data-stu-id="742a9-126">MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | <span data-ttu-id="742a9-127">体验混合现实的常见空间交互和 UX 构建基块（可从 HoloLens 2 中的 Microsoft Store 下载）</span><span class="sxs-lookup"><span data-stu-id="742a9-127">Experience common spatial interactions and UX building blocks for Mixed Reality (available for download from Microsoft Store in HoloLens 2)</span></span> |
| <span data-ttu-id="742a9-128">（可选）[下载 Figma 工具包](figma-toolkit.md)</span><span class="sxs-lookup"><span data-stu-id="742a9-128">**Optional** [Download the Figma Toolkit](figma-toolkit.md)</span></span> | <span data-ttu-id="742a9-129">Figma 工具包提供了一些资产，你可以使用它们根据 MRTK 中的可用组件来草拟和布置 UI</span><span class="sxs-lookup"><span data-stu-id="742a9-129">The Figma Toolkit provides assets for you to use for sketching and laying out UI based on the components available in MRTK</span></span> |

### <a name="2-core-concepts"></a><span data-ttu-id="742a9-130">2.核心概念</span><span class="sxs-lookup"><span data-stu-id="742a9-130">2. Core concepts</span></span>

<span data-ttu-id="742a9-131">无论是针对 VR 还是 AR 进行开发，都有几个核心概念适用于设计流畅的沉浸式体验。</span><span class="sxs-lookup"><span data-stu-id="742a9-131">Whether you're developing for VR or AR, there are several core concepts that apply to designing fluid immersive experiences.</span></span> <span data-ttu-id="742a9-132">了解用户的观点、定位对象并确保每个人都舒适安全是你在历程的这一阶段的头等大事。</span><span class="sxs-lookup"><span data-stu-id="742a9-132">Understanding the users point of view, positioning objects, and ensuring everyone is comfortable and safe are your top priorities at this stage of your journey.</span></span> <span data-ttu-id="742a9-133">本部分结束时，你将有一个坚实的基础来进行交互设计。</span><span class="sxs-lookup"><span data-stu-id="742a9-133">By the end of this section you'll have a solid foundation to carry through into interaction design.</span></span>

![核心概念示例图像](images/fragments-750px.jpg)

|  <span data-ttu-id="742a9-135">概念</span><span class="sxs-lookup"><span data-stu-id="742a9-135">Concept</span></span>  |  <span data-ttu-id="742a9-136">业务成效</span><span class="sxs-lookup"><span data-stu-id="742a9-136">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="742a9-137">全息帧</span><span class="sxs-lookup"><span data-stu-id="742a9-137">Holographic frame</span></span>](holographic-frame.md) | <span data-ttu-id="742a9-138">了解用户佩戴着其头戴显示设备时如何看到覆盖到现实世界的内容</span><span class="sxs-lookup"><span data-stu-id="742a9-138">Understand how users see your content overlaid onto the real world when wearing their headsets</span></span> |
| [<span data-ttu-id="742a9-139">坐标系统</span><span class="sxs-lookup"><span data-stu-id="742a9-139">Coordinate systems</span></span>](coordinate-systems.md) | <span data-ttu-id="742a9-140">了解如何将全息影像置于世界上有意义的各个位置，该位置可能是实际空间，也可能是你创建的某个虚拟领域</span><span class="sxs-lookup"><span data-stu-id="742a9-140">Learn how to position holograms in meaningful places in the world, whether it's their physical room or a virtual realm you've created</span></span> |
| [<span data-ttu-id="742a9-141">空间映射</span><span class="sxs-lookup"><span data-stu-id="742a9-141">Spatial mapping</span></span>](spatial-mapping.md) | <span data-ttu-id="742a9-142">在用户的世界中锚定对象，并利用真实世界的物理表面</span><span class="sxs-lookup"><span data-stu-id="742a9-142">Anchor objects in the user's world and take advantage of real world's physical surfaces</span></span> |
| [<span data-ttu-id="742a9-143">舒适感注意事项</span><span class="sxs-lookup"><span data-stu-id="742a9-143">Comfort considerations</span></span>](comfort.md) | <span data-ttu-id="742a9-144">通过以模仿自然世界的方式创建和呈现沉浸式内容，确保用户的舒适感和安全性</span><span class="sxs-lookup"><span data-stu-id="742a9-144">Ensure user comfort and safety by creating and presenting immersive content in a way that mimics the natural world</span></span> |

### <a name="3-interaction-design"></a><span data-ttu-id="742a9-145">3.交互设计</span><span class="sxs-lookup"><span data-stu-id="742a9-145">3. Interaction design</span></span>

<span data-ttu-id="742a9-146">无论虚拟体验有多漂亮和拟真，如果不能进行交互，也都是没有用的。</span><span class="sxs-lookup"><span data-stu-id="742a9-146">No matter how beautiful and immersive a virtual experience is, it's useless without interaction.</span></span> <span data-ttu-id="742a9-147">本部分将向你介绍基本交互模型、手势和运动控制器、语音输入以及收集用户的眼部跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="742a9-147">This section will walk you through basic interaction models, hand and motion controllers, voice input, and gathering eye tracking data from your users.</span></span> <span data-ttu-id="742a9-148">本部分结束后，你便已准备好处理设计历程中的最后一个大主题：用户体验。</span><span class="sxs-lookup"><span data-stu-id="742a9-148">By the end of this section you'll be ready to tackle the last big topic on your design journey: user experience.</span></span>

![交互设计因素](images/UX_Hero_Manipulation.jpg)

|  <span data-ttu-id="742a9-150">概念</span><span class="sxs-lookup"><span data-stu-id="742a9-150">Concept</span></span>  |  <span data-ttu-id="742a9-151">业务成效</span><span class="sxs-lookup"><span data-stu-id="742a9-151">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="742a9-152">交互模型</span><span class="sxs-lookup"><span data-stu-id="742a9-152">Interaction models</span></span>](interaction-fundamentals.md) | <span data-ttu-id="742a9-153">通过手部、眼部和语音输入向用户提供本能交互</span><span class="sxs-lookup"><span data-stu-id="742a9-153">Provide your users with instinctual interactions through hand, eye, and voice input</span></span> |
| [<span data-ttu-id="742a9-154">手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="742a9-154">Hands and motion controllers</span></span>](hands-and-tools.md) | <span data-ttu-id="742a9-155">了解如何在靠近用户手的位置或者通过精确的交互在远距离与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="742a9-155">Learn how to interact with holograms at close range with a user' hands or at long range with precise interactions</span></span> |
| [<span data-ttu-id="742a9-156">语音输入</span><span class="sxs-lookup"><span data-stu-id="742a9-156">Voice input</span></span>](voice-input.md) | <span data-ttu-id="742a9-157">在沉浸式应用中使用语音命令作为输入来控制周围的全息影像和环境</span><span class="sxs-lookup"><span data-stu-id="742a9-157">Use voice commands as input in your immersive apps to control surrounding holograms and environments</span></span>  |
| [<span data-ttu-id="742a9-158">眼部跟踪</span><span class="sxs-lookup"><span data-stu-id="742a9-158">Eye Tracking</span></span>](eye-tracking.md) | <span data-ttu-id="742a9-159">使用有关用户正在查看的内容的信息，在全息体验中增加一个新层次的上下文和人工理解</span><span class="sxs-lookup"><span data-stu-id="742a9-159">Add a new level of context and human understanding in a holographic experience by using information about what your users are looking at</span></span> |

### <a name="4-user-experience-elements"></a><span data-ttu-id="742a9-160">4.用户体验元素</span><span class="sxs-lookup"><span data-stu-id="742a9-160">4. User experience elements</span></span>

<span data-ttu-id="742a9-161">现在你已经掌握了基本的交互，你可以专注于用户体验元素的更细微之处，以及如何使它们适应混合现实的独特环境。</span><span class="sxs-lookup"><span data-stu-id="742a9-161">Now that you've mastered basic interactions, you can focus on the finer points of user experience elements and how to adapt them for Mixed Reality's unique environments.</span></span> <span data-ttu-id="742a9-162">你将了解常见的行为、资产设计、对象缩放和版式，同时为用户提供直观的体验。</span><span class="sxs-lookup"><span data-stu-id="742a9-162">You'll cover common behaviors, asset design, object scaling, and typography, while making the experience intuitive for your users.</span></span> <span data-ttu-id="742a9-163">本部分标志着混合现实官方设计历程的结束，但在[后续步骤？](#whats-next)部分中还有更多资源供你继续了解。</span><span class="sxs-lookup"><span data-stu-id="742a9-163">This section marks the end of the official Mixed Reality design journey, but there are more resources in the [What's next?](#whats-next) section to keep you going.</span></span>

![UX 元素](images/UX_Hero_BoundingBox.jpg)

|  <span data-ttu-id="742a9-165">概念</span><span class="sxs-lookup"><span data-stu-id="742a9-165">Concept</span></span>  |  <span data-ttu-id="742a9-166">业务成效</span><span class="sxs-lookup"><span data-stu-id="742a9-166">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="742a9-167">常用控件和行为</span><span class="sxs-lookup"><span data-stu-id="742a9-167">Common controls and behaviors</span></span>](app-patterns-landingpage.md) | <span data-ttu-id="742a9-168">了解常用空间交互和 UI 构建基块</span><span class="sxs-lookup"><span data-stu-id="742a9-168">Learn about frequently used spatial interactions and UI building blocks</span></span> |
| [<span data-ttu-id="742a9-169">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="742a9-169">Color, light, and materials</span></span>](color-light-and-materials.md) | <span data-ttu-id="742a9-170">设计适用于混合现实的质量资产，其考虑了颜色、照明和材料</span><span class="sxs-lookup"><span data-stu-id="742a9-170">Design quality assets for Mixed Reality that take color, lighting, and materials into account</span></span> |
| [<span data-ttu-id="742a9-171">对象规模</span><span class="sxs-lookup"><span data-stu-id="742a9-171">Object scale</span></span>](scale.md) | <span data-ttu-id="742a9-172">整合尽可能多的现实世界视觉提示给我们，帮助你的用户了解对象的位置、大小以及组成部分</span><span class="sxs-lookup"><span data-stu-id="742a9-172">Incorporate as many real-world visual cues as possible to us help your users understand where objects are, how big they are, and what they’re made of</span></span> |
| [<span data-ttu-id="742a9-173">版式</span><span class="sxs-lookup"><span data-stu-id="742a9-173">Typography</span></span>](typography.md) | <span data-ttu-id="742a9-174">在三维空间中使用清晰可读的文本，为用户提供所需的重要信息</span><span class="sxs-lookup"><span data-stu-id="742a9-174">Use clear, readable text in three-dimensional space to give your users the important information they need</span></span> |

## <a name="whats-next"></a><span data-ttu-id="742a9-175">下一步操作</span><span class="sxs-lookup"><span data-stu-id="742a9-175">What's next?</span></span>

<span data-ttu-id="742a9-176">设计师的工作一直在更新，尤其是在学习以新的范式创建沉浸式体验时。</span><span class="sxs-lookup"><span data-stu-id="742a9-176">A designer's job is never done, especially when learning to create immersive experiences in a new paradigm.</span></span> <span data-ttu-id="742a9-177">以下各部分将带你跨越已完成的初学者级别设计材料并进入混合现实开发的世界。</span><span class="sxs-lookup"><span data-stu-id="742a9-177">The following sections will take you beyond the beginner level design material you've already completed and into the world of Mixed Reality development.</span></span> <span data-ttu-id="742a9-178">这些主题和资源不按任何顺序排列，因此可随意探索！</span><span class="sxs-lookup"><span data-stu-id="742a9-178">These topics and resources aren't in any sequential order, so feel free to explore!</span></span>

### <a name="choose-a-prototyping-option"></a><span data-ttu-id="742a9-179">选择原型制作选项</span><span class="sxs-lookup"><span data-stu-id="742a9-179">Choose a prototyping option</span></span>  

:::row:::   
    :::column:::    
        <span data-ttu-id="742a9-180">[![MRTK Figma 工具包](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="742a9-180">[![MRTK Figma Toolkit](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span></span><br>
        <span data-ttu-id="742a9-181">**[Figma 工具包](figma-toolkit.md)**</span><span class="sxs-lookup"><span data-stu-id="742a9-181">**[Figma Toolkit](figma-toolkit.md)**</span></span><br>   
        <span data-ttu-id="742a9-182">Figma 工具包提供可用于 UI 构造和布局的资产。</span><span class="sxs-lookup"><span data-stu-id="742a9-182">Figma Toolkit provides the assets that can be used for sketching and laying out UI.</span></span> <span data-ttu-id="742a9-183">所有 UI 控件都基于 MRTK 中可用的组件。</span><span class="sxs-lookup"><span data-stu-id="742a9-183">All UI controls are based on the components available in MRTK.</span></span>
    :::column-end:::        
    :::column:::    
       <span data-ttu-id="742a9-184">[![了解 Unity](../images/Final_unity_logo.png)](https://learn.unity.com/)</span><span class="sxs-lookup"><span data-stu-id="742a9-184">[![Learn Unity](../images/Final_unity_logo.png)](https://learn.unity.com/)</span></span><br>
        <span data-ttu-id="742a9-185">**[了解 Unity](https://learn.unity.com/)**</span><span class="sxs-lookup"><span data-stu-id="742a9-185">**[Learn Unity](https://learn.unity.com/)**</span></span><br>
        <span data-ttu-id="742a9-186">了解如何使用 Unity 创建交互式体验。</span><span class="sxs-lookup"><span data-stu-id="742a9-186">Learn how to create interactive experiences with Unity.</span></span> <span data-ttu-id="742a9-187">从头至尾从实践中学习。</span><span class="sxs-lookup"><span data-stu-id="742a9-187">Learn by doing, from start to finish.</span></span>
    :::column-end:::    
    :::column:::    
        <span data-ttu-id="742a9-188">[![混合现实工具包 (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span><span class="sxs-lookup"><span data-stu-id="742a9-188">[![Mixed Reality Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span></span><br>
        <span data-ttu-id="742a9-189">**[混合现实工具包 (MRTK)](/windows/mixed-reality/mrtk-unity/)**</span><span class="sxs-lookup"><span data-stu-id="742a9-189">**[Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/)**</span></span><br>  
        <span data-ttu-id="742a9-190">使用空间交互和 UI 构建基块，通过 Unity 立即开始混合现实设计和开发。</span><span class="sxs-lookup"><span data-stu-id="742a9-190">With spatial interaction and UI building blocks, jump-start your mixed reality design and development with Unity.</span></span>   
    :::column-end:::
    :::column:::    
        <span data-ttu-id="742a9-191">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span><span class="sxs-lookup"><span data-stu-id="742a9-191">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span></span><br>
        <span data-ttu-id="742a9-192">**[Microsoft Maquette](https://www.maquette.ms/)**</span><span class="sxs-lookup"><span data-stu-id="742a9-192">**[Microsoft Maquette](https://www.maquette.ms/)**</span></span><br>  
        <span data-ttu-id="742a9-193">为 VR 而设计。</span><span class="sxs-lookup"><span data-stu-id="742a9-193">Design for VR.</span></span> <span data-ttu-id="742a9-194">可以使用 Microsoft Maquette 快速便捷地进行沉浸式空间原型制作。</span><span class="sxs-lookup"><span data-stu-id="742a9-194">Microsoft Maquette makes spatial prototyping easy, quick, and immersive.</span></span> 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a><span data-ttu-id="742a9-195">其他资源</span><span class="sxs-lookup"><span data-stu-id="742a9-195">Other resources</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="742a9-196">[![了解基础知识](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span><span class="sxs-lookup"><span data-stu-id="742a9-196">[![Understand the basics](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span></span><br>
        <span data-ttu-id="742a9-197">**[了解基础知识](../discover/get-started-with-mr.md#understand-the-basics)**</span><span class="sxs-lookup"><span data-stu-id="742a9-197">**[Understand the basics](../discover/get-started-with-mr.md#understand-the-basics)**</span></span><br>
        <span data-ttu-id="742a9-198">更好地了解是什么定义了混合现实，以及如何使用混合现实。</span><span class="sxs-lookup"><span data-stu-id="742a9-198">Get a better understanding of what defines mixed reality and how it’s being used.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="742a9-199">[![参加活动](images/74-16.png)](../whats-new/sf-academy-events.md)</span><span class="sxs-lookup"><span data-stu-id="742a9-199">[![Come to an event](images/74-16.png)](../whats-new/sf-academy-events.md)</span></span><br>
         <span data-ttu-id="742a9-200">**[参加活动](../whats-new/sf-academy-events.md)**</span><span class="sxs-lookup"><span data-stu-id="742a9-200">**[Come to an event](../whats-new/sf-academy-events.md)**</span></span><br>
        <span data-ttu-id="742a9-201">查看硬件并获取动手教程，以便创建第一个 HoloLens 2 应用程序。</span><span class="sxs-lookup"><span data-stu-id="742a9-201">See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="742a9-202">[![安装工具](images/74-17.png)](../develop/install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="742a9-202">[![Install the tools](images/74-17.png)](../develop/install-the-tools.md)</span></span><br>
         <span data-ttu-id="742a9-203">**[安装工具](../develop/install-the-tools.md)**</span><span class="sxs-lookup"><span data-stu-id="742a9-203">**[Install the tools](../develop/install-the-tools.md)**</span></span><br>
        <span data-ttu-id="742a9-204">使用安装清单获取为 HoloLens 和混合现实构建应用所需的工具。</span><span class="sxs-lookup"><span data-stu-id="742a9-204">Use the installation checklist to get the tools you need to build apps for HoloLens and mixed reality.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="742a9-205">[![开始开发](images/74-18.png)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="742a9-205">[![Start developing](images/74-18.png)](../develop/development.md)</span></span><br>
        <span data-ttu-id="742a9-206">**[开始开发](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="742a9-206">**[Start developing](../develop/development.md)**</span></span><br>
        <span data-ttu-id="742a9-207">根据技能水平、工作风格或平台兴趣选择开发路径。</span><span class="sxs-lookup"><span data-stu-id="742a9-207">Choose a development path based on your skill level, work style, or platform interest.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>
