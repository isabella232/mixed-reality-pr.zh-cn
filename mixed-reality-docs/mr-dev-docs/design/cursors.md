---
title: 游标
description: 对于目标向量，光标或指示器可为用户提供持续的反馈，以了解 HoloLens 对其意图的了解情况。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (第一代) ，HoloLens 2，Mixed Reality，光标，目标，注视，手势，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，射线，输入
ms.openlocfilehash: 0525bb9b30dfe71fba7b8ebf2afd2c87a8c97a27
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582404"
---
# <a name="cursors"></a><span data-ttu-id="f927f-104">游标</span><span class="sxs-lookup"><span data-stu-id="f927f-104">Cursors</span></span>

![游标](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="f927f-106">光标提供持续的反馈，其中基于耳机认为用户当前焦点在给定时间的位置。</span><span class="sxs-lookup"><span data-stu-id="f927f-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="f927f-107">光标反馈包括虚拟环境中的哪些区域、全息图或点对输入的响应。</span><span class="sxs-lookup"><span data-stu-id="f927f-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="f927f-108">尽管光标是设备理解用户注意的数字表示形式，但这与确定用户的意图并不相同。</span><span class="sxs-lookup"><span data-stu-id="f927f-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="f927f-109">光标反馈还允许用户了解系统对预期的响应。</span><span class="sxs-lookup"><span data-stu-id="f927f-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="f927f-110">你可以使用反馈将其意图传达给设备，从而提高用户信心。</span><span class="sxs-lookup"><span data-stu-id="f927f-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="f927f-111">有三种类型的游标： **手指、光线** 和 **打印头**。</span><span class="sxs-lookup"><span data-stu-id="f927f-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="f927f-112">这些指针在 HoloLens、HoloLens 2 和沉浸式耳机上使用不同的输入情态。</span><span class="sxs-lookup"><span data-stu-id="f927f-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="f927f-113">下面是针对每种类型的耳机和交互模型使用哪种类型的游标的指导。</span><span class="sxs-lookup"><span data-stu-id="f927f-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="f927f-114">在混合现实工具包中 (MRTK) ，我们已创建了拖放游标模块，以帮助你生成正确的指针体验。</span><span class="sxs-lookup"><span data-stu-id="f927f-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="f927f-115">设备支持</span><span class="sxs-lookup"><span data-stu-id="f927f-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f927f-116"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="f927f-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f927f-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="f927f-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f927f-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f927f-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f927f-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="f927f-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f927f-120">手指光标</span><span class="sxs-lookup"><span data-stu-id="f927f-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="f927f-121">✔️</span><span class="sxs-lookup"><span data-stu-id="f927f-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="f927f-122">Ray 光标</span><span class="sxs-lookup"><span data-stu-id="f927f-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="f927f-123">✔️</span><span class="sxs-lookup"><span data-stu-id="f927f-123">✔️</span></span></td>
        <td><span data-ttu-id="f927f-124">✔️</span><span class="sxs-lookup"><span data-stu-id="f927f-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="f927f-125">打印头光标</span><span class="sxs-lookup"><span data-stu-id="f927f-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="f927f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="f927f-126">✔️</span></span></td>
        <td><span data-ttu-id="f927f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="f927f-127">✔️</span></span></td>
        <td><span data-ttu-id="f927f-128">✔️</span><span class="sxs-lookup"><span data-stu-id="f927f-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="f927f-129">手指光标</span><span class="sxs-lookup"><span data-stu-id="f927f-129">Finger cursor</span></span>

<span data-ttu-id="f927f-130">Finger 游标仅在 HoloLens 2 上提供，用于增强 "[直接操作](direct-manipulation.md)" 交互模式。</span><span class="sxs-lookup"><span data-stu-id="f927f-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="f927f-131">我们已将振铃连接到两个食指，以更好地了解手指指向的位置。</span><span class="sxs-lookup"><span data-stu-id="f927f-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="f927f-132">环形大小基于向 UI 表面显示的手指的邻近点，当手指接触 UI 时，该大小将缩小为小点。</span><span class="sxs-lookup"><span data-stu-id="f927f-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="f927f-133">手指越接近，环越小。</span><span class="sxs-lookup"><span data-stu-id="f927f-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="f927f-134">![手指光标](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="f927f-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="f927f-135">**Finger cursor 1 的视觉反馈状态** ：环形收缩为点。</span><span class="sxs-lookup"><span data-stu-id="f927f-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="f927f-136">2：环形与图面对齐。</span><span class="sxs-lookup"><span data-stu-id="f927f-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="f927f-137">3：环与 finger 矢量垂直。</span><span class="sxs-lookup"><span data-stu-id="f927f-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="f927f-138">4：无环。</span><span class="sxs-lookup"><span data-stu-id="f927f-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="f927f-139">Ray 光标</span><span class="sxs-lookup"><span data-stu-id="f927f-139">Ray cursor</span></span>

<span data-ttu-id="f927f-140">Ray 光标连接到最靠近的光线的末尾，以允许对不是手接触的对象进行操作。</span><span class="sxs-lookup"><span data-stu-id="f927f-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="f927f-141">在沉浸式耳机中，从运动控制器开始，并以点光标结束。</span><span class="sxs-lookup"><span data-stu-id="f927f-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="f927f-142">在 HoloLens 2 中，我们应用了这些运动控制器光线的心理模型，并在与直接操作中使用的 finger 光标保持一致的不要和结尾处，为其设计的手写光线。</span><span class="sxs-lookup"><span data-stu-id="f927f-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="f927f-143">![Ray cursor 控制器](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="f927f-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="f927f-144">**运动控制器的光线光标**</span><span class="sxs-lookup"><span data-stu-id="f927f-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f927f-145">![Ray 光标手](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="f927f-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="f927f-146">**免提的光线光标**</span><span class="sxs-lookup"><span data-stu-id="f927f-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="f927f-147">打印头光标</span><span class="sxs-lookup"><span data-stu-id="f927f-147">Head-gaze cursor</span></span>

<span data-ttu-id="f927f-148">打印头光标是一个点，用于连接到使用点的位置和旋转点的不可见的端面向量。</span><span class="sxs-lookup"><span data-stu-id="f927f-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="f927f-149">若要执行操作，请将指针光标与各种提交输入（如分流、语音命令、停留和按钮按下）配对。</span><span class="sxs-lookup"><span data-stu-id="f927f-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="f927f-150">在 HoloLens 2 中，打印头最适用于不是点击的任何提交输入，因为这会在空中分流和远手光线之间发生交互冲突。</span><span class="sxs-lookup"><span data-stu-id="f927f-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="f927f-151">![打印头的光标手](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="f927f-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="f927f-152">**带有手动手势的打印头**</span><span class="sxs-lookup"><span data-stu-id="f927f-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f927f-153">![打印头光标声音](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="f927f-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="f927f-154">**带有声音命令的头盔光标**</span><span class="sxs-lookup"><span data-stu-id="f927f-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="f927f-155">游标自定义建议</span><span class="sxs-lookup"><span data-stu-id="f927f-155">Cursor customization recommendations</span></span>

<span data-ttu-id="f927f-156">如果要自定义游标反馈行为和外观，以下是一些设计建议：</span><span class="sxs-lookup"><span data-stu-id="f927f-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="f927f-157">游标刻度</span><span class="sxs-lookup"><span data-stu-id="f927f-157">Cursor scale</span></span>

* <span data-ttu-id="f927f-158">光标不应大于可用目标，从而使用户可以轻松地与内容交互并查看内容。</span><span class="sxs-lookup"><span data-stu-id="f927f-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="f927f-159">根据您创建的体验，在用户看起来时缩放光标也是一个重要的考虑因素。</span><span class="sxs-lookup"><span data-stu-id="f927f-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="f927f-160">例如，当用户看到你的体验时，光标不应太小以致丢失。</span><span class="sxs-lookup"><span data-stu-id="f927f-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="f927f-161">缩放光标时，请考虑将软动画应用到它，因为它会进行缩放以使其成为一种有机感觉。</span><span class="sxs-lookup"><span data-stu-id="f927f-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="f927f-162">避免阻碍内容。</span><span class="sxs-lookup"><span data-stu-id="f927f-162">Avoid obstructing content.</span></span> <span data-ttu-id="f927f-163">全息影像使体验更加容易，并且光标不应从它们中消失。</span><span class="sxs-lookup"><span data-stu-id="f927f-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="f927f-164">Directionless 光标形状</span><span class="sxs-lookup"><span data-stu-id="f927f-164">Directionless cursor shape</span></span>

* <span data-ttu-id="f927f-165">尽管没有一个右光标形状，但建议使用 directionless 形状（如圆环图）。</span><span class="sxs-lookup"><span data-stu-id="f927f-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="f927f-166">在某些方向上指向 (例如，传统的箭头光标) 的游标可能会使用户感到困惑。</span><span class="sxs-lookup"><span data-stu-id="f927f-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="f927f-167">当使用游标向用户传达交互指令时，会出现这种情况的例外情况。</span><span class="sxs-lookup"><span data-stu-id="f927f-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="f927f-168">例如，在混合现实操作系统中缩放全息影像时，光标暂时会包括一些箭头，指导用户如何移动其手来缩放全息影像。</span><span class="sxs-lookup"><span data-stu-id="f927f-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="f927f-169">外观</span><span class="sxs-lookup"><span data-stu-id="f927f-169">Look and feel</span></span>

* <span data-ttu-id="f927f-170">环形或圆环图游标适用于许多应用程序。</span><span class="sxs-lookup"><span data-stu-id="f927f-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="f927f-171">选择最能代表您正在创建的体验的颜色和形状。</span><span class="sxs-lookup"><span data-stu-id="f927f-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="f927f-172">游标特别容易出现 [颜色分离](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)。</span><span class="sxs-lookup"><span data-stu-id="f927f-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="f927f-173">具有均衡不透明度的小游标将使其具有信息性，而无需占据视觉层次结构。</span><span class="sxs-lookup"><span data-stu-id="f927f-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="f927f-174">请 cognizant 在游标后面使用阴影或突出显示，因为它们可能会妨碍内容和对任务的注意力。</span><span class="sxs-lookup"><span data-stu-id="f927f-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="f927f-175">光标应与应用中的表面对齐并向其展示。</span><span class="sxs-lookup"><span data-stu-id="f927f-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="f927f-176">用户会感觉到系统可以看到的位置，但系统也知道其周围的位置。</span><span class="sxs-lookup"><span data-stu-id="f927f-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="f927f-177">例如，混合现实操作系统中的光标与用户世界的表面保持一致，即使用户没有直接在全息图上查看，也可以感觉到世界的认知。</span><span class="sxs-lookup"><span data-stu-id="f927f-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="f927f-178">将光标移到靠近用户的位置时，会将光标锁定到交互元素，从而有助于提高用户在使用选择操作时与该元素交互的置信度。</span><span class="sxs-lookup"><span data-stu-id="f927f-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="f927f-179">视觉提示</span><span class="sxs-lookup"><span data-stu-id="f927f-179">Visual cues</span></span>

* <span data-ttu-id="f927f-180">如果你的体验侧重于单个全息图，则当你看起来远离该全息图时，光标应该只与全息图和改变形状对齐。</span><span class="sxs-lookup"><span data-stu-id="f927f-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="f927f-181">这可以向用户传达全息影像是可操作的，并且可以与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="f927f-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="f927f-182">如果你的应用程序使用空间映射，则光标可能会对齐并向其看到的每个表面显示。</span><span class="sxs-lookup"><span data-stu-id="f927f-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="f927f-183">这会向 HoloLens 和你的应用程序可以看到其空间的用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="f927f-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="f927f-184">这就是一个事实，那就是全息影像非常真实，并可帮助您弥补现实和虚拟之间的差距。</span><span class="sxs-lookup"><span data-stu-id="f927f-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="f927f-185">在视图中没有全息影像或曲面时，了解光标应执行的操作。</span><span class="sxs-lookup"><span data-stu-id="f927f-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="f927f-186">将其放置在用户前面预先确定的距离上是一种选择。</span><span class="sxs-lookup"><span data-stu-id="f927f-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="f927f-187">可能的操作</span><span class="sxs-lookup"><span data-stu-id="f927f-187">Possible actions</span></span>

* <span data-ttu-id="f927f-188">光标可由不同的图标表示，以传达全息图可以执行的操作，例如缩放或旋转。</span><span class="sxs-lookup"><span data-stu-id="f927f-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="f927f-189">仅在游标中添加了其他内容时，才添加其他信息。</span><span class="sxs-lookup"><span data-stu-id="f927f-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="f927f-190">否则，用户可能不会注意到状态发生更改，也可能会使光标混淆。</span><span class="sxs-lookup"><span data-stu-id="f927f-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="f927f-191">输入状态</span><span class="sxs-lookup"><span data-stu-id="f927f-191">Input state</span></span>

* <span data-ttu-id="f927f-192">可以使用光标显示用户的输入状态或意向。</span><span class="sxs-lookup"><span data-stu-id="f927f-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="f927f-193">例如，我们可以显示一个图标，告诉用户系统看到其手状态，并且应用程序知道他们已准备好采取措施。</span><span class="sxs-lookup"><span data-stu-id="f927f-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="f927f-194">我们还可以使用光标向用户显示系统通过暂时颜色更改发出声音命令</span><span class="sxs-lookup"><span data-stu-id="f927f-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="f927f-195">可以通过不同的方式实现以下游标状态。</span><span class="sxs-lookup"><span data-stu-id="f927f-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="f927f-196">您可以通过对游标（如状态机）进行建模来实现这些不同的状态。</span><span class="sxs-lookup"><span data-stu-id="f927f-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="f927f-197">例如：</span><span class="sxs-lookup"><span data-stu-id="f927f-197">For example:</span></span>
    * <span data-ttu-id="f927f-198">空闲状态是显示默认光标的位置。</span><span class="sxs-lookup"><span data-stu-id="f927f-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="f927f-199">"就绪" 状态是指检测到用户在准备就绪的位置。</span><span class="sxs-lookup"><span data-stu-id="f927f-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="f927f-200">交互状态是指用户正在执行特定交互。</span><span class="sxs-lookup"><span data-stu-id="f927f-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="f927f-201">当你传达可以在全息图上执行的可能操作时，可能的操作状态或悬停状态。</span><span class="sxs-lookup"><span data-stu-id="f927f-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="f927f-202">你还可以在检测到不同状态时，以一种可实现外观的方式实现这些状态以显示不同的图片资产。</span><span class="sxs-lookup"><span data-stu-id="f927f-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="f927f-203">转到 "无游标"</span><span class="sxs-lookup"><span data-stu-id="f927f-203">Going "cursor-free"</span></span>

<span data-ttu-id="f927f-204">如果浸入式是体验的关键组件，并且 (在通过注视和手势) 不需要很高的精度时，建议不使用游标进行设计。</span><span class="sxs-lookup"><span data-stu-id="f927f-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="f927f-205">系统仍然需要满足游标的一般要求：向用户提供对系统对其指向的了解的持续反馈，并帮助他们将他们的意图传达给系统。</span><span class="sxs-lookup"><span data-stu-id="f927f-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="f927f-206">这可以通过其他明显的状态更改实现。</span><span class="sxs-lookup"><span data-stu-id="f927f-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f927f-207">MRTK 中的光标 (混合现实工具包) 适用于 Unity</span><span class="sxs-lookup"><span data-stu-id="f927f-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="f927f-208">默认情况下， [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供与 shell 的系统游标具有相同可视状态的 Prefab ([DefaultCursor) prefab。](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)</span><span class="sxs-lookup"><span data-stu-id="f927f-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="f927f-209">它分配在 MRTK 的输入配置文件的“指针”下。</span><span class="sxs-lookup"><span data-stu-id="f927f-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="f927f-210">您可以根据自己的经验来替换/自定义此光标。</span><span class="sxs-lookup"><span data-stu-id="f927f-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="f927f-211">对于目视跟踪输入经验，MRTK 还提供了 EyeGazeCursor，它具有微妙的视觉对象，可将干扰降到最低。</span><span class="sxs-lookup"><span data-stu-id="f927f-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="f927f-212">MRTK - 指针配置文件</span><span class="sxs-lookup"><span data-stu-id="f927f-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="f927f-213">MRTK - 输入系统</span><span class="sxs-lookup"><span data-stu-id="f927f-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="f927f-214">MRTK - 指针</span><span class="sxs-lookup"><span data-stu-id="f927f-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="f927f-215">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f927f-215">See also</span></span>

* [<span data-ttu-id="f927f-216">笔势</span><span class="sxs-lookup"><span data-stu-id="f927f-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="f927f-217">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="f927f-217">Head-gaze and commit</span></span>](gaze-and-commit.md)