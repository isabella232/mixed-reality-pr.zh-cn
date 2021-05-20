---
title: 凝视并提交
description: 了解凝视和提交输入模型，包括两种类型的凝视 (头部凝视和凝视) 以及各种类型的提交。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合现实， 凝视， 凝视目标， 交互， 设计， 眼动跟踪， 头部跟踪， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196562"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="3509d-104">凝视并提交</span><span class="sxs-lookup"><span data-stu-id="3509d-104">Gaze and commit</span></span>

<span data-ttu-id="3509d-105">_凝视和_ 提交是一个基本的输入模型，它与我们使用鼠标与计算机交互的方式密切相关：单击 _"&"。_</span><span class="sxs-lookup"><span data-stu-id="3509d-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="3509d-106">在此页上，我们引入了两种类型的凝视输入 (头部和眼睛凝视) 以及不同类型的提交操作。</span><span class="sxs-lookup"><span data-stu-id="3509d-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="3509d-107">_凝视和提交_ 被视为具有间接操作的远端输入模型。</span><span class="sxs-lookup"><span data-stu-id="3509d-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="3509d-108">它最适合用于与无法访问的全息内容进行交互。</span><span class="sxs-lookup"><span data-stu-id="3509d-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="3509d-109">混合现实头戴显示设备可以使用用户头部的位置和方向来确定其头部方向向量。</span><span class="sxs-lookup"><span data-stu-id="3509d-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="3509d-110">将凝视视为直接从用户眼睛之间的方向直接指向的箭头。</span><span class="sxs-lookup"><span data-stu-id="3509d-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="3509d-111">这可粗略呈现出用户正查看的位置。</span><span class="sxs-lookup"><span data-stu-id="3509d-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="3509d-112">应用程序可以将此射线与虚拟或真实对象相交，并绘制该位置的光标，让用户知道目标对象。</span><span class="sxs-lookup"><span data-stu-id="3509d-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="3509d-113">除了头部凝视之外，一些混合现实头戴显示设备（HoloLens 2）还包括生成眼睛凝视矢量的眼动跟踪系统。</span><span class="sxs-lookup"><span data-stu-id="3509d-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="3509d-114">这可精细测量用户正在查看的位置。</span><span class="sxs-lookup"><span data-stu-id="3509d-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="3509d-115">在这两种情况下，凝视都表示用户意向的重要信号。</span><span class="sxs-lookup"><span data-stu-id="3509d-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="3509d-116">系统可以解释和预测用户预期操作越好，用户满意度和性能就越好。</span><span class="sxs-lookup"><span data-stu-id="3509d-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="3509d-117">下面是一些示例，说明混合现实开发人员如何从头部或眼睛凝视中获益：</span><span class="sxs-lookup"><span data-stu-id="3509d-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="3509d-118">应用可以将凝视与场景中的全息影像相交，以确定用户注意力的 (通过眼睛凝视) 。</span><span class="sxs-lookup"><span data-stu-id="3509d-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="3509d-119">应用可以基于用户的凝视来通道手势和控制器按下，这样用户就可以无缝选择、激活、抓取、滚动或与其全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="3509d-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="3509d-120">您的应用程序可让用户在实际的表面上放置全息影像，方法是将其表面与空间映射网格进行交叉处理。</span><span class="sxs-lookup"><span data-stu-id="3509d-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="3509d-121">您的应用程序可以知道用户不会看到重要对象的方向，这会使您的应用程序能够通过视觉对象和音频提示来转向该对象。</span><span class="sxs-lookup"><span data-stu-id="3509d-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="3509d-122">设备支持</span><span class="sxs-lookup"><span data-stu-id="3509d-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3509d-123"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="3509d-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="3509d-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="3509d-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3509d-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3509d-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3509d-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="3509d-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3509d-127">头部凝视和提交</span><span class="sxs-lookup"><span data-stu-id="3509d-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="3509d-128">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="3509d-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="3509d-129">✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</span><span class="sxs-lookup"><span data-stu-id="3509d-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="3509d-130">➕ 备用选项</span><span class="sxs-lookup"><span data-stu-id="3509d-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="3509d-131">眼睛凝视和提交</span><span class="sxs-lookup"><span data-stu-id="3509d-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="3509d-132">❌ 不可用</span><span class="sxs-lookup"><span data-stu-id="3509d-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="3509d-133">✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</span><span class="sxs-lookup"><span data-stu-id="3509d-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="3509d-134">❌ 不可用</span><span class="sxs-lookup"><span data-stu-id="3509d-134">❌ Not available</span></span></td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="3509d-135">标题和眼睛跟踪设计概念演示</span><span class="sxs-lookup"><span data-stu-id="3509d-135">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="3509d-136">若要查看标题和目视跟踪的设计概念，请参阅下面的 **设计全息影像-打印头跟踪和眼睛跟踪** 视频演示。</span><span class="sxs-lookup"><span data-stu-id="3509d-136">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="3509d-137">完成后，请继续详细了解特定主题。</span><span class="sxs-lookup"><span data-stu-id="3509d-137">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="3509d-138">*此视频取自 "设计全息影像" HoloLens 2 应用。下载并在 [此处](https://aka.ms/dhapp)享受完全体验。*</span><span class="sxs-lookup"><span data-stu-id="3509d-138">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="gaze"></a><span data-ttu-id="3509d-139">凝视</span><span class="sxs-lookup"><span data-stu-id="3509d-139">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="3509d-140">眼后看好了吗？</span><span class="sxs-lookup"><span data-stu-id="3509d-140">Eye- or head-gaze?</span></span>
<span data-ttu-id="3509d-141">当面对问题时，有几个注意事项需要考虑是否应使用 "眼睛和提交" 或 "良好和提交" 输入模型。</span><span class="sxs-lookup"><span data-stu-id="3509d-141">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="3509d-142">如果你正在开发沉浸式耳机或用于 HoloLens (第一代) ，则选择简单：打印头，并提交。</span><span class="sxs-lookup"><span data-stu-id="3509d-142">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="3509d-143">如果你正在开发 HoloLens 2，则选择会稍微难些。</span><span class="sxs-lookup"><span data-stu-id="3509d-143">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="3509d-144">务必要了解每种方法所附带的优点和挑战。</span><span class="sxs-lookup"><span data-stu-id="3509d-144">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="3509d-145">在下表中，我们编译了一些广泛的专业人员和职业，以对比眼睛和眼睛的目标。</span><span class="sxs-lookup"><span data-stu-id="3509d-145">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="3509d-146">这从很大程度上来看，我们建议在此处了解各种混合现实中的眼睛目标：</span><span class="sxs-lookup"><span data-stu-id="3509d-146">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="3509d-147">[Hololens 2 上的目视跟踪](eye-tracking.md)：在 hololens 2 上提供新的目视跟踪功能（包括一些开发人员指南）。</span><span class="sxs-lookup"><span data-stu-id="3509d-147">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="3509d-148">[目视的交互](eye-gaze-interaction.md)：计划使用目视跟踪作为输入时的设计注意事项和建议。</span><span class="sxs-lookup"><span data-stu-id="3509d-148">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="3509d-149"><strong>目视瞄准目标</strong></span><span class="sxs-lookup"><span data-stu-id="3509d-149"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="3509d-150"><strong>头部凝视目标设定</strong></span><span class="sxs-lookup"><span data-stu-id="3509d-150"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3509d-151">Fast!</span><span class="sxs-lookup"><span data-stu-id="3509d-151">Fast!</span></span></td>
        <td><span data-ttu-id="3509d-152">比较</span><span class="sxs-lookup"><span data-stu-id="3509d-152">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3509d-153">低 (几乎不需要任何人体运动) </span><span class="sxs-lookup"><span data-stu-id="3509d-153">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="3509d-154">可能很难受 - 可能 (，例如，) </span><span class="sxs-lookup"><span data-stu-id="3509d-154">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3509d-155">不需要光标，但建议提供细微的反馈</span><span class="sxs-lookup"><span data-stu-id="3509d-155">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="3509d-156">需要显示游标</span><span class="sxs-lookup"><span data-stu-id="3509d-156">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3509d-157">没有平滑的眼部运动 - 例如，不适合绘制</span><span class="sxs-lookup"><span data-stu-id="3509d-157">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="3509d-158">更受控且更显式</span><span class="sxs-lookup"><span data-stu-id="3509d-158">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3509d-159">对于小型目标 (例如，小型按钮或 Web 链接) </span><span class="sxs-lookup"><span data-stu-id="3509d-159">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="3509d-160">可靠！</span><span class="sxs-lookup"><span data-stu-id="3509d-160">Reliable!</span></span> <span data-ttu-id="3509d-161">出色的回退！</span><span class="sxs-lookup"><span data-stu-id="3509d-161">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3509d-162">...</span><span class="sxs-lookup"><span data-stu-id="3509d-162">...</span></span></td>
        <td><span data-ttu-id="3509d-163">...</span><span class="sxs-lookup"><span data-stu-id="3509d-163">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="3509d-164">无论对凝视和提交输入模型使用头部凝视还是眼睛凝视，每个模型都附带不同的设计约束集。</span><span class="sxs-lookup"><span data-stu-id="3509d-164">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="3509d-165">这些分别在眼睛凝视、[提交、](gaze-and-commit-eyes.md)[头部凝视和提交文章中](gaze-and-commit-head.md)介绍。</span><span class="sxs-lookup"><span data-stu-id="3509d-165">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="3509d-166">游标</span><span class="sxs-lookup"><span data-stu-id="3509d-166">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3509d-167">对于头部凝视，大多数应用都应使用[](cursors.md)光标或其他审核/视觉指示，让用户对要与之交互的方面具有置信度。</span><span class="sxs-lookup"><span data-stu-id="3509d-167">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="3509d-168">通常在此光标位于其头部凝视射线首先与对象相交（可能是全息影像或真实表面）的地方。</span><span class="sxs-lookup"><span data-stu-id="3509d-168">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="3509d-169">对于眼睛凝视 *，我们通常* 建议不要显示光标，因为这可能会快速成为用户的干扰和麻烦。</span><span class="sxs-lookup"><span data-stu-id="3509d-169">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="3509d-170">而是以小方式突出显示视觉对象目标，或使用眼睛光标来表示用户要与之交互的置信度。</span><span class="sxs-lookup"><span data-stu-id="3509d-170">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="3509d-171">有关详细信息，请查看我们的设计指南 [，了解](eye-tracking.md) 基于眼睛的输入HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="3509d-171">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="3509d-172">![显示凝视的示例视觉光标](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="3509d-172">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="3509d-173">*图像：用于显示凝视的示例视觉光标*</span><span class="sxs-lookup"><span data-stu-id="3509d-173">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="3509d-174">提交</span><span class="sxs-lookup"><span data-stu-id="3509d-174">Commit</span></span>
<span data-ttu-id="3509d-175">在讨论对目标 _进行_ 凝视的不同方法后，让我们再讨论一下凝 _视和提交_ 中的提交 _部分_。</span><span class="sxs-lookup"><span data-stu-id="3509d-175">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="3509d-176">以对象或 UI 元素为目标后，用户可以使用辅助输入与之交互或单击它。</span><span class="sxs-lookup"><span data-stu-id="3509d-176">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="3509d-177">这被称为输入模型的提交步骤。</span><span class="sxs-lookup"><span data-stu-id="3509d-177">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="3509d-178">支持以下提交方法：</span><span class="sxs-lookup"><span data-stu-id="3509d-178">The following commit methods are supported:</span></span>
- <span data-ttu-id="3509d-179">空中攻指的手势 (就是，在您自己的前方抬起，并将食指和拇指) </span><span class="sxs-lookup"><span data-stu-id="3509d-179">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="3509d-180">说 _"选择"_ 或一个目标语音命令</span><span class="sxs-lookup"><span data-stu-id="3509d-180">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="3509d-181">在[HoloLens Clicker](/hololens/hololens1-clicker)上按单个按钮</span><span class="sxs-lookup"><span data-stu-id="3509d-181">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="3509d-182">按下 Xbox 游戏板上的 "A" 按钮</span><span class="sxs-lookup"><span data-stu-id="3509d-182">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="3509d-183">按 Xbox 自适应控制器上的 "A" 按钮</span><span class="sxs-lookup"><span data-stu-id="3509d-183">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="3509d-184">注视和气攻敲击手势</span><span class="sxs-lookup"><span data-stu-id="3509d-184">Gaze and air tap gesture</span></span>
<span data-ttu-id="3509d-185">隔空敲击是一种手部直立的点击手势。</span><span class="sxs-lookup"><span data-stu-id="3509d-185">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="3509d-186">若要使用空中点击，请将您的食指向准备就绪，然后将其放在拇指上，并将您的食指向上提升到释放。</span><span class="sxs-lookup"><span data-stu-id="3509d-186">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="3509d-187">在 HoloLens (第一代) 上，点击是最常见的辅助输入。</span><span class="sxs-lookup"><span data-stu-id="3509d-187">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="3509d-188">![手指处于就绪位置](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="3509d-188">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="3509d-189">**手指处于就绪位置**</span><span class="sxs-lookup"><span data-stu-id="3509d-189">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3509d-190">![按下手指点击或单击](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="3509d-190">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="3509d-191&quot;>**按下手指点击或单击**</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-191&quot;>**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id=&quot;3509d-192&quot;>HoloLens 2 上也提供了空中点击。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-192&quot;>Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id=&quot;3509d-193&quot;>它已从原始版本中宽松。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-193&quot;>It has been relaxed from the original version.</span></span> <span data-ttu-id=&quot;3509d-194&quot;>几乎所有类型的 pinches 现在都受支持，只要手直立并且仍保持。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-194&quot;>Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id=&quot;3509d-195&quot;>这样，用户就可以更轻松地学习和使用手势。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-195&quot;>This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id=&quot;3509d-196&quot;>这种新的 &quot;air&quot; 将通过相同的 API 替换旧的，因此，在重新编译 HoloLens 2 后，现有应用程序将自动具有新行为。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-196&quot;>This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name=&quot;gaze-and-select-voice-command&quot;></a><span data-ttu-id=&quot;3509d-197&quot;>注视并单击 &quot;选择&quot; 语音命令</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-197&quot;>Gaze and &quot;Select&quot; voice command</span></span>
<span data-ttu-id=&quot;3509d-198&quot;>语音命令是混合现实中的主要交互方法之一。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-198&quot;>Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id=&quot;3509d-199&quot;>它提供强大的免提机制来控制系统。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-199&quot;>It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id=&quot;3509d-200&quot;>有不同类型的语音交互模型：</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-200&quot;>There are different types of voice interaction models:</span></span>

- <span data-ttu-id=&quot;3509d-201&quot;>使用单击提示或提交作为辅助输入的通用&quot;Select&quot;命令。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;3509d-201&quot;>The generic &quot;Select&quot; command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id=&quot;3509d-202&quot;>对象命令 (例如，&quot;关闭&quot;或&quot;放大") 作为辅助输入执行并提交到某个操作。</span><span class="sxs-lookup"><span data-stu-id="3509d-202">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="3509d-203">全局 (，例如"转到开始") 不需要目标。</span><span class="sxs-lookup"><span data-stu-id="3509d-203">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="3509d-204">聊天用户界面或 Cortana 等实体具有 AI 自然语言功能。</span><span class="sxs-lookup"><span data-stu-id="3509d-204">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="3509d-205">自定义语音命令</span><span class="sxs-lookup"><span data-stu-id="3509d-205">Custom voice commands</span></span>

<span data-ttu-id="3509d-206">若要详细了解详细信息和可用语音命令的综合列表及其使用方法，请查看语音 [命令指南](../out-of-scope/voice-design.md) 。</span><span class="sxs-lookup"><span data-stu-id="3509d-206">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="3509d-207">凝视和 HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="3509d-207">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3509d-208">HoloLens Clicker 是专为 HoloLens 构建的第一个外围设备。</span><span class="sxs-lookup"><span data-stu-id="3509d-208">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="3509d-209">它包含在 HoloLens (第一代) Development Edition 中。</span><span class="sxs-lookup"><span data-stu-id="3509d-209">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="3509d-210">HoloLens Clicker 允许用户以最少的手部运动进行单击，并提交作为辅助输入。</span><span class="sxs-lookup"><span data-stu-id="3509d-210">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="3509d-211">HoloLens Clicker 使用 (BTLE) 或 HoloLens 2 连接到 HoloLens 蓝牙低功耗 (第一代) 。</span><span class="sxs-lookup"><span data-stu-id="3509d-211">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="3509d-212">对设备进行配对的更多信息和说明</span><span class="sxs-lookup"><span data-stu-id="3509d-212">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="3509d-213">*图像：HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="3509d-213">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens 遥控器](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="3509d-215">凝视和 Xbox 无线控制器</span><span class="sxs-lookup"><span data-stu-id="3509d-215">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3509d-216">Xbox 无线控制器使用"A"按钮执行点击作为辅助输入。</span><span class="sxs-lookup"><span data-stu-id="3509d-216">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="3509d-217">设备映射到有助于导航和控制系统的默认操作集。</span><span class="sxs-lookup"><span data-stu-id="3509d-217">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="3509d-218">如果要自定义控制器，请使用 Xbox Accessories 应用程序配置 Xbox 无线控制器。</span><span class="sxs-lookup"><span data-stu-id="3509d-218">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="3509d-219">如何将 Xbox 控制器与电脑配对</span><span class="sxs-lookup"><span data-stu-id="3509d-219">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="3509d-220">*图像：Xbox 无线控制器*</span><span class="sxs-lookup"><span data-stu-id="3509d-220">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox 无线控制器](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="3509d-222">注视和 Xbox 自适应控制器</span><span class="sxs-lookup"><span data-stu-id="3509d-222">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="3509d-223">Xbox 自适应控制器主要用于满足移动性有限的游戏玩家的需求，是一种统一的设备，有助于使混合现实更易于访问。</span><span class="sxs-lookup"><span data-stu-id="3509d-223">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="3509d-224">Xbox 自适应控制器使用 "A" 按钮执行单击传动作为辅助输入。</span><span class="sxs-lookup"><span data-stu-id="3509d-224">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="3509d-225">设备映射到一组可帮助导航和控制系统的默认操作。</span><span class="sxs-lookup"><span data-stu-id="3509d-225">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="3509d-226">如果要自定义控制器，请使用 Xbox 附件应用程序来配置 Xbox 自适应控制器。</span><span class="sxs-lookup"><span data-stu-id="3509d-226">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="3509d-227">![Xbox 自适应控制器](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="3509d-227">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="3509d-228">*Xbox 自适应控制器*</span><span class="sxs-lookup"><span data-stu-id="3509d-228">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="3509d-229">连接外部设备，如交换机、按钮、装入和操纵杆，以创建唯一的自定义控制器体验。</span><span class="sxs-lookup"><span data-stu-id="3509d-229">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="3509d-230">按钮、操纵杆和触发器输入由通过 3.5 mm 插座和 USB 端口连接的辅助设备控制。</span><span class="sxs-lookup"><span data-stu-id="3509d-230">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="3509d-231">![Xbox 自适应控制器端口](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="3509d-231">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="3509d-232">*Xbox 自适应控制器端口*</span><span class="sxs-lookup"><span data-stu-id="3509d-232">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="3509d-233">设备配对说明</span><span class="sxs-lookup"><span data-stu-id="3509d-233">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="3509d-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 网站上提供了更多信息</a></span><span class="sxs-lookup"><span data-stu-id="3509d-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="3509d-235">复合手势</span><span class="sxs-lookup"><span data-stu-id="3509d-235">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="3509d-236">隔空敲击</span><span class="sxs-lookup"><span data-stu-id="3509d-236">Air tap</span></span>
<span data-ttu-id="3509d-237">"Air" 手势 (和下面的其他手势) 只会对特定点击做出反应。</span><span class="sxs-lookup"><span data-stu-id="3509d-237">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="3509d-238">若要检测其他点击，如菜单或抓住，你的应用程序必须直接使用上面两个关键组件手势部分中所述的低级交互。</span><span class="sxs-lookup"><span data-stu-id="3509d-238">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="3509d-239">点击并按住</span><span class="sxs-lookup"><span data-stu-id="3509d-239">Tap and hold</span></span>
<span data-ttu-id="3509d-240">按住是指保持隔空敲击手指向下的位置。</span><span class="sxs-lookup"><span data-stu-id="3509d-240">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="3509d-241">与 arm 移动（例如，选取对象，而不是激活对象）或 mousedown 辅助交互（如显示上下文菜单）结合使用时，点击和保持的组合允许使用各种更复杂的 "单击并拖动" 交互。</span><span class="sxs-lookup"><span data-stu-id="3509d-241">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="3509d-242">请注意，在为此手势设计时应谨慎，因为用户在任何扩展手势期间都容易使其 postures。</span><span class="sxs-lookup"><span data-stu-id="3509d-242">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="3509d-243">操作</span><span class="sxs-lookup"><span data-stu-id="3509d-243">Manipulation</span></span>
<span data-ttu-id="3509d-244">当您想让全息图对用户的手的变动做出回应1:1 时，可以使用操作手势移动、调整或旋转全息图。</span><span class="sxs-lookup"><span data-stu-id="3509d-244">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="3509d-245">此类 1:1 运动可让用户进行实际绘制或绘画。</span><span class="sxs-lookup"><span data-stu-id="3509d-245">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="3509d-246">操作手势的初始定位应通过凝视或指向来完成。</span><span class="sxs-lookup"><span data-stu-id="3509d-246">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="3509d-247">点击并保持开始后，任何对象操作都将由手动移动处理，从而使用户能够在操作时进行浏览。</span><span class="sxs-lookup"><span data-stu-id="3509d-247">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="3509d-248">导航</span><span class="sxs-lookup"><span data-stu-id="3509d-248">Navigation</span></span>
<span data-ttu-id="3509d-249">导航手势就像一个虚拟游戏杆，可用于导航 UI 小组件（如径向菜单）。</span><span class="sxs-lookup"><span data-stu-id="3509d-249">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="3509d-250">点击并按住以开始手势，然后在标准化 3D 立方体中以初始按压位置为中心移动手部。</span><span class="sxs-lookup"><span data-stu-id="3509d-250">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="3509d-251">您可以沿 X、Y 或 Z 轴将您的手移动到值1到1之间，0是起点。</span><span class="sxs-lookup"><span data-stu-id="3509d-251">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="3509d-252">导航可用于生成基于速度的连续滚动或缩放手势，类似于通过单击鼠标按钮然后上下移动鼠标来滚动 2D UI。</span><span class="sxs-lookup"><span data-stu-id="3509d-252">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="3509d-253">使用 rails 导航，是指在该轴上达到特定阈值之前识别特定轴中的运动的能力。</span><span class="sxs-lookup"><span data-stu-id="3509d-253">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="3509d-254">这仅在开发人员在应用程序中启用多个轴的移动时有用，例如，如果应用程序配置为识别跨 X、Y 轴的导航手势，但还指定了带导轨的 X 轴。</span><span class="sxs-lookup"><span data-stu-id="3509d-254">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="3509d-255">在这种情况下，系统将识别跨 X 轴的手动运动，只要它们保留在 X 轴上的虚导轨 () （如果手部运动也发生在 Y 轴上）。</span><span class="sxs-lookup"><span data-stu-id="3509d-255">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="3509d-256">在 2D 应用中，用户可以使用垂直导航手势在应用内进行滚动、缩放或拖动。</span><span class="sxs-lookup"><span data-stu-id="3509d-256">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="3509d-257">这会向应用注入虚拟手指触摸，以模拟相同类型的触摸手势。</span><span class="sxs-lookup"><span data-stu-id="3509d-257">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="3509d-258">用户可以通过在应用程序上方的栏上的工具之间切换来选择执行哪些操作，只需选择按钮或说"<滚动/拖动/缩放>工具"即可。</span><span class="sxs-lookup"><span data-stu-id="3509d-258">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="3509d-259">有关复合手势的详细信息</span><span class="sxs-lookup"><span data-stu-id="3509d-259">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="3509d-260">手势识别器</span><span class="sxs-lookup"><span data-stu-id="3509d-260">Gesture recognizers</span></span>

<span data-ttu-id="3509d-261">使用手势识别的一个好处是，只能为当前目标全息影像可以接受的手势配置手势识别器。</span><span class="sxs-lookup"><span data-stu-id="3509d-261">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="3509d-262">平台仅在必要时进行区分，以区分这些特定的受支持手势。</span><span class="sxs-lookup"><span data-stu-id="3509d-262">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="3509d-263">这样一来，仅支持敲击的全息影像可以接受按下和松开之间的任意时长，而支持点击和按住的全息影像可以在保持时间阈值后将点击提升为保持。</span><span class="sxs-lookup"><span data-stu-id="3509d-263">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="3509d-264">手部识别</span><span class="sxs-lookup"><span data-stu-id="3509d-264">Hand recognition</span></span>
<span data-ttu-id="3509d-265">HoloLens 通过跟踪设备可识别的一只手或双手的位置来识别手势。</span><span class="sxs-lookup"><span data-stu-id="3509d-265">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="3509d-266">当手处于就绪状态（手背朝向自己，食指向上）或按下状态（手背朝向自己，食指向下）时，HoloLens 可检测到手部。</span><span class="sxs-lookup"><span data-stu-id="3509d-266">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="3509d-267">当手部有其他姿势时，HoloLens 会忽略它们。</span><span class="sxs-lookup"><span data-stu-id="3509d-267">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="3509d-268">对于 HoloLens 检测到的每手，无需方向和按下状态即可访问其位置。</span><span class="sxs-lookup"><span data-stu-id="3509d-268">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="3509d-269">当手接近手势范围的边缘时，可看到一个方向向量，可向用户显示该方向向量，以便他们知道如何将手移回 HoloLens 可检测的范围。</span><span class="sxs-lookup"><span data-stu-id="3509d-269">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="3509d-270">手势范围</span><span class="sxs-lookup"><span data-stu-id="3509d-270">Gesture frame</span></span>
<span data-ttu-id="3509d-271">对于 HoloLens 上的手势，手必须位于手势帧中，其范围是手势测量相机可以适当看到的范围，从手部到手部以及手部之间。</span><span class="sxs-lookup"><span data-stu-id="3509d-271">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="3509d-272">用户需要针对此识别领域进行训练，以便成功操作和获得自己的舒适感。</span><span class="sxs-lookup"><span data-stu-id="3509d-272">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="3509d-273">许多用户最初会假设手势框架必须通过 HoloLens 位于其视图中，并且要保持其手部以不解的方式进行交互。</span><span class="sxs-lookup"><span data-stu-id="3509d-273">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="3509d-274">使用 HoloLens Clicker 时，手不需要位于手势范围内。</span><span class="sxs-lookup"><span data-stu-id="3509d-274">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="3509d-275">具体而言，对于连续手势，用户在移动全息对象时，在手势中将手移动到手势框架之外存在一些风险，并丢失预期结果。</span><span class="sxs-lookup"><span data-stu-id="3509d-275">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="3509d-276">应考虑以下三个事项：</span><span class="sxs-lookup"><span data-stu-id="3509d-276">There are three things that you should consider:</span></span>

- <span data-ttu-id="3509d-277">手势帧存在和大致边界的用户教育。</span><span class="sxs-lookup"><span data-stu-id="3509d-277">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="3509d-278">这会在安装 HoloLens 期间进行。</span><span class="sxs-lookup"><span data-stu-id="3509d-278">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="3509d-279">当用户的手势接近或中断应用程序内的手势帧边界时，通知用户，使丢失的手势导致意外的结果。</span><span class="sxs-lookup"><span data-stu-id="3509d-279">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="3509d-280">研究显示了此类通知系统的重要质量。</span><span class="sxs-lookup"><span data-stu-id="3509d-280">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="3509d-281">在中心游标上，HoloLens shell 提供此类通知的很好的示例，指示边界交叉的发生方向。</span><span class="sxs-lookup"><span data-stu-id="3509d-281">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="3509d-282">应尽可能避免穿过手势范围的边界。</span><span class="sxs-lookup"><span data-stu-id="3509d-282">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="3509d-283">通常，这意味着应在边界停止笔势的结果，而不是反转。</span><span class="sxs-lookup"><span data-stu-id="3509d-283">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="3509d-284">例如，如果用户在房间内移动某个全息对象，则在该笔势帧被破坏时，移动应停止，并且不会返回到开始点。</span><span class="sxs-lookup"><span data-stu-id="3509d-284">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="3509d-285">用户可能会遇到一些挫折，但可能会更快地了解边界，无需每次都重新启动其全部预期操作。</span><span class="sxs-lookup"><span data-stu-id="3509d-285">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="3509d-286">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3509d-286">See also</span></span>
* [<span data-ttu-id="3509d-287">基于眼睛的交互</span><span class="sxs-lookup"><span data-stu-id="3509d-287">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="3509d-288">HoloLens 2 中的眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="3509d-288">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="3509d-289">凝视和停留</span><span class="sxs-lookup"><span data-stu-id="3509d-289">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="3509d-290">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="3509d-290">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3509d-291">手 - 手势</span><span class="sxs-lookup"><span data-stu-id="3509d-291">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="3509d-292">手 - 指向并提交</span><span class="sxs-lookup"><span data-stu-id="3509d-292">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="3509d-293">本能交互</span><span class="sxs-lookup"><span data-stu-id="3509d-293">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="3509d-294">语音输入</span><span class="sxs-lookup"><span data-stu-id="3509d-294">Voice input</span></span>](voice-input.md)