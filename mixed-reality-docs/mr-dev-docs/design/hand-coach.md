---
title: 手部指导
description: 了解当系统未检测到要帮助帮助的用户时，如何使用手型指导触发3D 手势。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality，设计，手型指导，沉浸式耳机，MRTK，双手，帮助双手，混合现实耳机，windows Mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: ec302cecb106b339828adf1c8777c2ea7ec7fa30
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300042"
---
# <a name="hand-coach"></a><span data-ttu-id="ed8fd-104">手部指导</span><span class="sxs-lookup"><span data-stu-id="ed8fd-104">Hand coach</span></span>

![示例：手型指导](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="ed8fd-106">当系统未检测到用户的手时，手动指导会触发3D 建模。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-106">Hand coach triggers 3D modeled hands when the system doesn't detect the user’s hands.</span></span> <span data-ttu-id="ed8fd-107">此功能是一个 "教学" 组件，可帮助用户在未教授手势时引导用户。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-107">This feature is a “teaching” component that helps guide the user when the gesture hasn't been taught.</span></span> <span data-ttu-id="ed8fd-108">如果用户没有在某个时间段完成指定的手势，则会循环一段时间。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-108">If users haven't done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="ed8fd-109">手型指导可用于表示按下按钮或选取全息图标。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="ed8fd-110">手写指导</span><span class="sxs-lookup"><span data-stu-id="ed8fd-110">Hand coach provided</span></span>

<span data-ttu-id="ed8fd-111">当前交互模型表示各种手势控件，例如滚动、远选和点击显示。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="ed8fd-112">下面是<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>中提供的现有手型手势的完整列表：</span><span class="sxs-lookup"><span data-stu-id="ed8fd-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="ed8fd-113">![接近选择的示例](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="ed8fd-114">**接近选择使用的示例显示如何选择按钮或关闭种不可交互对象**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed8fd-115">![空中点击的示例](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="ed8fd-116">**空中点击的示例-用于显示如何选择远距离的对象**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed8fd-117">![移动示例](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="ed8fd-118">**将对象移动到空间的示例-用于显示如何在空间中移动全息图**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed8fd-119">![旋转示例](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="ed8fd-120">**演示如何旋转全息影像或对象的 Rotate-Used 示例**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="ed8fd-121">![缩放示例](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="ed8fd-122">**缩放示例-用于显示如何操作更大或更小的全息影像**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed8fd-123">![手掌的示例](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="ed8fd-124">**掌上-建议使用的示例，用于引入手菜单**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed8fd-125">![HandFlip 的示例](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="ed8fd-126">**示例-用于打开手形菜单的另一种方式**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ed8fd-127">![滚动示例](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="ed8fd-128">**滚动示例–用于滚动列表或长文档**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="ed8fd-129">设计概念</span><span class="sxs-lookup"><span data-stu-id="ed8fd-129">Design concepts</span></span>

<span data-ttu-id="ed8fd-130">对于 Hololens2，我们基于 instinctual 和自然手势设计出了手动交互。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="ed8fd-131">我们认为这对于大多数用户来说是直观的，因此我们不会创建专用的手势学习时间。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-131">We believe these to be intuitive to most users, so we didn't create dedicated gesture learning moments.</span></span> <span data-ttu-id="ed8fd-132">相反，我们创建了手形指导，帮助用户了解有关这些手势的问题，或者不熟悉全息图交互。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-132">Instead, we created the hand coach to help users learn about these gestures if they get stuck or are unfamiliar with hologram interactions.</span></span> <span data-ttu-id="ed8fd-133">如果没有学习，我们认为向用户展示如何执行操作，这是最佳选择。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="ed8fd-134">我们发现用户能够找出手势，但需要一些指导。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-134">We found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="ed8fd-135">如果检测到用户不能在某个时间段内与对象交互，则会触发一则手指导，演示正确的抓手和 finger 位置。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-135">If we detect a user doesn't interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="ed8fd-136">直观</span><span class="sxs-lookup"><span data-stu-id="ed8fd-136">Intuitive</span></span>

<span data-ttu-id="ed8fd-137">动画处理时，应该很明显，不会造成任何混淆。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-137">When animating hands, it should be obvious and shouldn't cause any confusion.</span></span> <span data-ttu-id="ed8fd-138">手型动画是尝试提示用户理解的手势的表示形式。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-138">The hand animation is a representation of the gesture you're trying to prompt the user to understand.</span></span> 

<span data-ttu-id="ed8fd-139">例如，如果希望用户按下某个按钮，则会触发按下按钮的一只手。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="ed8fd-140">![示例：点击点击](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="ed8fd-141">*演示附近点击 Gem 的指导*</span><span class="sxs-lookup"><span data-stu-id="ed8fd-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="ed8fd-142">手动缩放</span><span class="sxs-lookup"><span data-stu-id="ed8fd-142">Hand scale</span></span>

<span data-ttu-id="ed8fd-143">我们使用 UI 菜单测试了各种手大小，并感觉到，如果想要调整规模，就会 menacing。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling.</span></span> <span data-ttu-id="ed8fd-144">如果它们太小，则很难查看和理解手势。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-144">If they were too small, it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="ed8fd-145">**语音和手**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-145">**Voice over and hands**</span></span>

<span data-ttu-id="ed8fd-146">不要指望用户可以通过语音来侦听一组说明，并通过手动指导观看不同说明。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="ed8fd-147">序列化说明，帮助用户专注于争用，从而减少传感器的过载。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="ed8fd-148">我能创建自己的吗？</span><span class="sxs-lookup"><span data-stu-id="ed8fd-148">Can I create my own?</span></span>

<span data-ttu-id="ed8fd-149">可以！</span><span class="sxs-lookup"><span data-stu-id="ed8fd-149">Yes!</span></span> <span data-ttu-id="ed8fd-150">我们鼓励你为游戏创建自己的独特手势，并向社区提供反馈！</span><span class="sxs-lookup"><span data-stu-id="ed8fd-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="ed8fd-151">我们提供了一个可用于你的应用的 Rigged 的 Maya 文件，可在此处下载 <a href="files/HandCoach_MRTK.zip"> HandCoach_MRTK.zip </a></span><span class="sxs-lookup"><span data-stu-id="ed8fd-151">We've provided a Maya file of a Rigged hand that can be used for your app, which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip </a></span></span>

<span data-ttu-id="ed8fd-152">![在 Maya 中进行动画处理的示例](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="ed8fd-153">*Maya 中闲逛的动画手形的示例*</span><span class="sxs-lookup"><span data-stu-id="ed8fd-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="ed8fd-154">**推荐的创作工具**</span><span class="sxs-lookup"><span data-stu-id="ed8fd-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="ed8fd-155">在三维音乐家之间，很多选择使用 [Autodesk 的 Maya，它可以使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 来转换资产的创建方式。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-155">Among 3D artists, many choose to use [Autodesk’s Maya, which can use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="ed8fd-156">提供的免提文件是一个 Maya 二进制文件，因此建议使用 Maya 来动画和导出手。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-156">The hands file provided is a Maya Binary File, so it's recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="ed8fd-157">如果希望使用其他三维程序，请参阅 <b>。FBX</b>： <a href="files/HandCoachMRTK_FBX.zip"> 下载 HandCoachMRTK_FBX.zip </a> 来创建自己的控制器设置。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-157">If you prefer to use another 3D program, here's a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Download HandCoachMRTK_FBX.zip </a> to create your own controller setup.</span></span> 

<span data-ttu-id="ed8fd-158">如果使用提供的可下载 maya 手型文件，则建议将 unity 向下扩展到0.6。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-158">If using the downloadable maya Hand File provided, it's suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="ed8fd-159">![示例： Maya 中的手型指导远程测试机组](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="ed8fd-160">*Rigged*</span><span class="sxs-lookup"><span data-stu-id="ed8fd-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="ed8fd-161">技术规格</span><span class="sxs-lookup"><span data-stu-id="ed8fd-161">Technical Specs</span></span>

*   <span data-ttu-id="ed8fd-162">Maya Ascii 格式提供两个文件</span><span class="sxs-lookup"><span data-stu-id="ed8fd-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="ed8fd-163">Right 和左手提供 Maya 二进制格式</span><span class="sxs-lookup"><span data-stu-id="ed8fd-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="ed8fd-164">将 Maya 文件设置为 24 FPS</span><span class="sxs-lookup"><span data-stu-id="ed8fd-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="ed8fd-165">在该文件中，有一个左手的右手，可用于两个右手或单面手势。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-165">Within the file, there's a left and right hand, which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="ed8fd-166">仅在默认情况下，才会显示右手。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="ed8fd-167">建议在开始和结束时留出大约10帧的缓冲区来淡化</span><span class="sxs-lookup"><span data-stu-id="ed8fd-167">It's suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="ed8fd-168">如果对具有指定目标的对象进行动画处理，则其最佳方案为动态到默认框或 Null。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-168">If animating an object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="ed8fd-169">如果要对物理对象（例如 box）进行动画处理，最佳做法是不在 Maya 中对转换进行动画处理，而是等待在 Unity 中或代码中对其进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="ed8fd-170">对于要传达的任何有意义的信息，可见动画应为1.5 秒</span><span class="sxs-lookup"><span data-stu-id="ed8fd-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="ed8fd-171">如果你对动画感到满意：</span><span class="sxs-lookup"><span data-stu-id="ed8fd-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="ed8fd-172">选择所有接头和制作关键帧</span><span class="sxs-lookup"><span data-stu-id="ed8fd-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="ed8fd-173">删除控制器，选择接头和网格，并将其导出为 FBX</span><span class="sxs-lookup"><span data-stu-id="ed8fd-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="ed8fd-174">如果有多个动画，可以使用 Maya 的内置游戏导出程序： https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="ed8fd-174">If there are Multiple Animations, you can use Maya’s built-in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="ed8fd-175">从 Maya 导出</span><span class="sxs-lookup"><span data-stu-id="ed8fd-175">Exporting from Maya</span></span>

<span data-ttu-id="ed8fd-176">对动画满意后</span><span class="sxs-lookup"><span data-stu-id="ed8fd-176">After you're satisfied with your animation</span></span>
* <span data-ttu-id="ed8fd-177">选择所有接头：选择 > 层次结构</span><span class="sxs-lookup"><span data-stu-id="ed8fd-177">Select all joints: Select > Hierarchy</span></span>

     ![示例：菜单中的层次结构](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="ed8fd-179">制作动画：切换到动画 > 键 > 制作动画</span><span class="sxs-lookup"><span data-stu-id="ed8fd-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![示例：制作动画菜单位置](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="ed8fd-181">删除控制器远程测试机组： Outliner > MainR_Grp 或 MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="ed8fd-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![示例：控制器 Rig 菜单位置](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="ed8fd-183">导出为 FBX：选择 .JNT + 网格： File > 导出所选内容 (选项框) > 导出选定内容</span><span class="sxs-lookup"><span data-stu-id="ed8fd-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![示例：导出选择菜单位置](images/HandCoach/OptionBox.png)<br>

     ![示例：菜单位置](images/HandCoach/SelectionExport.png)<br>

     ![示例：导出选项菜单位置](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="ed8fd-187">导出为 FBX 并将其放入 Unity 时，将指针向下缩放到0.6。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-187">When exporting as an FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="ed8fd-188">我们发现这非常适合显示手。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="ed8fd-189">![示例： Unity 设置](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="ed8fd-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="ed8fd-190">*在 MRTK 中找到 HandCoach_R prefab 的 Unity 设置*</span><span class="sxs-lookup"><span data-stu-id="ed8fd-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="ed8fd-191">实现对 Unity 项目的动手</span><span class="sxs-lookup"><span data-stu-id="ed8fd-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="ed8fd-192">最佳做法</span><span class="sxs-lookup"><span data-stu-id="ed8fd-192">Best practices</span></span>

* <span data-ttu-id="ed8fd-193">建议将 unity 向下扩展到0。6</span><span class="sxs-lookup"><span data-stu-id="ed8fd-193">It's suggested to scale down the hands in unity to 0.6</span></span>
* <span data-ttu-id="ed8fd-194">应播放两次，如果未完成，则连续循环，直到手势完成。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="ed8fd-195">应循环访问两次，以确保用户有时间注册并查看手势。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="ed8fd-196">指针应在循环之间淡入和淡出。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="ed8fd-197">如果用户的手在 HL2 摄像头中可见，但用户不会进行所需的交互，则会在10秒后出现。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-197">If user’s hands are visible by HL2 cameras but users aren't doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="ed8fd-198">如果 HL2 照相机看不到用户的手，则会在5秒后出现指针。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="ed8fd-199">如果动画中间的 HL2 相机明显跟踪用户的手，动画将完成并淡出。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="ed8fd-200">如果要包括语音，则建议将其对应于手的手势。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-200">If you're including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="ed8fd-201">如果你至少已经教授了一次，则只会在其检测到用户停滞时重复手势。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-201">If you've taught the hands at least once, only repeat the gesture if it's detected that the user is stuck.</span></span>
*   <span data-ttu-id="ed8fd-202">如果特定的 finger 位置是关键的，请确保用户可以清楚地查看动画中的这些差异。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="ed8fd-203">尝试右倾，以清楚地显示最重要的部分。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="ed8fd-204">如果你注意到了手上的扭曲，则需要中转到 Unity 的质量设置以增加骨骼数量。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the number of bones.</span></span> 
 <span data-ttu-id="ed8fd-205">请参阅 Unity 的编辑 > 项目设置 > Quality > 其他 > Blend 权重。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="ed8fd-206">请确保选择 "4 骨骼" 以查看平滑联接。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span>

   ![示例： "项目设置" 窗口](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a><span data-ttu-id="ed8fd-208">要避免的内容</span><span class="sxs-lookup"><span data-stu-id="ed8fd-208">What to avoid</span></span>

* <span data-ttu-id="ed8fd-209">将指针放大太大</span><span class="sxs-lookup"><span data-stu-id="ed8fd-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="ed8fd-210">将指针放在靠近用户的附近</span><span class="sxs-lookup"><span data-stu-id="ed8fd-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="ed8fd-211">只需教授一次。</span><span class="sxs-lookup"><span data-stu-id="ed8fd-211">Hands should only be taught once.</span></span> <span data-ttu-id="ed8fd-212">优于教授会导致混淆和麻烦</span><span class="sxs-lookup"><span data-stu-id="ed8fd-212">Over teaching can cause confusion and messiness</span></span>
* <span data-ttu-id="ed8fd-213">将它引入 Unity，在此处下载最新的 MRTK： https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="ed8fd-213">Bringing it into Unity, download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
  * <span data-ttu-id="ed8fd-214">材料： Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="ed8fd-214">Material: Teaching_Hand2</span></span>
  * <span data-ttu-id="ed8fd-215">脚本：请参阅<a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach">MRTK 手型指导</a>的 MRTK 准则</span><span class="sxs-lookup"><span data-stu-id="ed8fd-215">Scripts: Refer to MRTK guidelines for <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> MRTK hand coach </a></span></span>
  * <span data-ttu-id="ed8fd-216">每项目设置</span><span class="sxs-lookup"><span data-stu-id="ed8fd-216">Per- project setting</span></span>
    * <span data-ttu-id="ed8fd-217">场景设置为 UWP：可在 [配置 Unity 项目](../develop/unity/Configure-Unity-Project.md) 中找到 Windows Mixed Reality 的说明</span><span class="sxs-lookup"><span data-stu-id="ed8fd-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](../develop/unity/Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="ed8fd-218">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed8fd-218">See also</span></span>

* [<span data-ttu-id="ed8fd-219">交互-基础</span><span class="sxs-lookup"><span data-stu-id="ed8fd-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="ed8fd-220">资产创建过程</span><span class="sxs-lookup"><span data-stu-id="ed8fd-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="ed8fd-221">笔势</span><span class="sxs-lookup"><span data-stu-id="ed8fd-221">Gestures</span></span>](./interaction-fundamentals.md)
* [<span data-ttu-id="ed8fd-222">安装工具</span><span class="sxs-lookup"><span data-stu-id="ed8fd-222">Install the Tools</span></span>](../develop/install-the-tools.md)
* [<span data-ttu-id="ed8fd-223">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="ed8fd-223">Configure Unity Project</span></span>](../develop/unity/Configure-Unity-Project.md)
* [<span data-ttu-id="ed8fd-224">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="ed8fd-224">Unity development overview</span></span>](../develop/unity/unity-development-overview.md)
* [<span data-ttu-id="ed8fd-225">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="ed8fd-225">MRTK 101</span></span>](../out-of-scope/mrtk-101.md)