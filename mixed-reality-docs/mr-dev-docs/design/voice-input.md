---
title: 语音输入
description: 语音输入是适用于 HoloLens 和 Windows Mixed Reality 沉浸式耳机的核心输入。 语音可用于命令、听写、Cortana 等。
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv，语音，cortana，语音，输入，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，注视
ms.openlocfilehash: 6773bb71da7d98b1dd00d2246084d469e5e7c6ba
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600576"
---
# <a name="voice-input"></a><span data-ttu-id="01d18-105">语音输入</span><span class="sxs-lookup"><span data-stu-id="01d18-105">Voice input</span></span>

![语音输入](images/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="01d18-107">在 HoloLens 上，语音是重要输入形式之一。</span><span class="sxs-lookup"><span data-stu-id="01d18-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="01d18-108">它使你可以直接在无需使用 [手型手势](gaze-and-commit.md#composite-gestures)的情况下直接执行命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="01d18-109">可以将语音输入作为一种传达意图的自然方式。</span><span class="sxs-lookup"><span data-stu-id="01d18-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="01d18-110">语音在遍历复杂接口时特别有用，因为它允许用户通过一个命令剪切嵌套菜单。</span><span class="sxs-lookup"><span data-stu-id="01d18-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="01d18-111">语音输入由支持所有 _通用 Windows 应用_ 中的语音的 [同一引擎](/windows/uwp/design/input/speech-recognition)提供支持。</span><span class="sxs-lookup"><span data-stu-id="01d18-111">Voice input is powered by the [same engine](/windows/uwp/design/input/speech-recognition) that supports speech in all _Universal Windows Apps_.</span></span> <span data-ttu-id="01d18-112">在 HoloLens 上，语音识别将始终在设备设置中配置的 Windows 显示语言中工作。</span><span class="sxs-lookup"><span data-stu-id="01d18-112">On HoloLens, speech recognition will always function in the Windows display language configured in your device Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="01d18-113">语音和注视</span><span class="sxs-lookup"><span data-stu-id="01d18-113">Voice and gaze</span></span>

<span data-ttu-id="01d18-114">使用语音命令时，head 或眼睛看起来是典型的目标机制，无论是使用光标 "选择" 还是将命令通道到你要查看的应用程序。</span><span class="sxs-lookup"><span data-stu-id="01d18-114">When you're using voice commands, head or eye gaze is the typical targeting mechanism, whether with a cursor to "select" or to channel your command to an application you're looking at.</span></span> <span data-ttu-id="01d18-115">可能甚至不需要显示任何看起来光标 _( "查看它" )_。</span><span class="sxs-lookup"><span data-stu-id="01d18-115">It may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="01d18-116">某些语音命令根本不需要目标，如 "开始" 或 "你好 Cortana"。</span><span class="sxs-lookup"><span data-stu-id="01d18-116">Some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="01d18-117">设备支持</span><span class="sxs-lookup"><span data-stu-id="01d18-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="01d18-118"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="01d18-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="01d18-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="01d18-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="01d18-120"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="01d18-120"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="01d18-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="01d18-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="01d18-122">语音输入</span><span class="sxs-lookup"><span data-stu-id="01d18-122">Voice input</span></span></td>
        <td><span data-ttu-id="01d18-123">✔️</span><span class="sxs-lookup"><span data-stu-id="01d18-123">✔️</span></span></td>
        <td><span data-ttu-id="01d18-124">✔️</span><span class="sxs-lookup"><span data-stu-id="01d18-124">✔️</span></span></td>
        <td><span data-ttu-id="01d18-125">用麦克风) ✔️ (</span><span class="sxs-lookup"><span data-stu-id="01d18-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="01d18-126">"Select" 命令</span><span class="sxs-lookup"><span data-stu-id="01d18-126">The "select" command</span></span>

<span data-ttu-id="01d18-127">**HoloLens（第一代）**</span><span class="sxs-lookup"><span data-stu-id="01d18-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="01d18-128">即使不将语音支持专门添加到应用，用户也可以通过口述系统语音命令 "select" 来激活全息影像。</span><span class="sxs-lookup"><span data-stu-id="01d18-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="01d18-129">此行为与在 HoloLens 上的 [点击](gaze-and-commit.md#composite-gestures) ，按下 [hololens clicker](/hololens/hololens1-clicker)上的 "选择" 按钮或在 [Windows Mixed Reality 运动控制器](motion-controllers.md)上按下触发器的行为相同。</span><span class="sxs-lookup"><span data-stu-id="01d18-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="01d18-130">听到声音，并看到带有 "select" 的工具提示显示为确认。</span><span class="sxs-lookup"><span data-stu-id="01d18-130">You'll hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="01d18-131">"选择" 由低功率关键字检测算法启用，这意味着您可以在任何时间使用最小的电池寿命。</span><span class="sxs-lookup"><span data-stu-id="01d18-131">"Select" is enabled by a low-power keyword detection algorithm, which means you can say it anytime with minimal battery life impact.</span></span> <span data-ttu-id="01d18-132">你甚至可以在一边说 "选择"。</span><span class="sxs-lookup"><span data-stu-id="01d18-132">You can even say "select" with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="01d18-133">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="01d18-133">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="01d18-134">若要在 HoloLens 2 中使用 "选择" 语音命令，首先需要打开 "注视" 光标作为指针。</span><span class="sxs-lookup"><span data-stu-id="01d18-134">To use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="01d18-135">让它变得更容易记住，只需说 "选择"。</span><span class="sxs-lookup"><span data-stu-id="01d18-135">The command to bring it up is easy to remember--just say, "select".</span></span><br><br>
        <span data-ttu-id="01d18-136">若要退出此模式，请通过空中攻指再次使用鼠标，使用手指接近按钮，或使用系统手势。</span><span class="sxs-lookup"><span data-stu-id="01d18-136">To exit the mode, use your hands again by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br> 
        <span data-ttu-id="01d18-137">*图像：说 "选择" 以使用声音命令进行选择*</span><span class="sxs-lookup"><span data-stu-id="01d18-137">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![用户可以将 "选择" 用于所选的语音命令。](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a><span data-ttu-id="01d18-139">你好小娜</span><span class="sxs-lookup"><span data-stu-id="01d18-139">Hey Cortana</span></span>

<span data-ttu-id="01d18-140">你可以随时说 "你好 Cortana" 来打开 Cortana。</span><span class="sxs-lookup"><span data-stu-id="01d18-140">You can say "Hey Cortana" to bring up Cortana at any time.</span></span> <span data-ttu-id="01d18-141">无需等待她就会继续询问她的问题或向她提供一条指导。</span><span class="sxs-lookup"><span data-stu-id="01d18-141">You don't have to wait for her to appear to continue asking her your question or giving her an instruction.</span></span> <span data-ttu-id="01d18-142">例如，尝试说 "你好 Cortana，天气是什么？"。</span><span class="sxs-lookup"><span data-stu-id="01d18-142">For example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="01d18-143">作为单个句子。</span><span class="sxs-lookup"><span data-stu-id="01d18-143">as a single sentence.</span></span> <span data-ttu-id="01d18-144">有关 Cortana 和你可以执行的操作的详细信息，请询问她！</span><span class="sxs-lookup"><span data-stu-id="01d18-144">For more information about Cortana and what you can do, ask her!</span></span> <span data-ttu-id="01d18-145">说 "你好 Cortana，我该怎么办？"</span><span class="sxs-lookup"><span data-stu-id="01d18-145">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="01d18-146">然后，她将获取工作和建议命令的列表。</span><span class="sxs-lookup"><span data-stu-id="01d18-146">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="01d18-147">如果已在 Cortana 应用中，请选择 **？**</span><span class="sxs-lookup"><span data-stu-id="01d18-147">If you're already in the Cortana app, select the **?**</span></span> <span data-ttu-id="01d18-148">图标，提取此相同的菜单。</span><span class="sxs-lookup"><span data-stu-id="01d18-148">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="01d18-149">**HoloLens 特定的命令**</span><span class="sxs-lookup"><span data-stu-id="01d18-149">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="01d18-150">“我可以说什么？”</span><span class="sxs-lookup"><span data-stu-id="01d18-150">"What can I say?"</span></span>
* <span data-ttu-id="01d18-151">"转到开始"-而不是 [布隆](system-gesture.md#bloom) 转到 " [开始" 菜单](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="01d18-151">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="01d18-152">"启动 <app> "</span><span class="sxs-lookup"><span data-stu-id="01d18-152">"Launch <app>"</span></span>
* <span data-ttu-id="01d18-153">"移动到 <app> 此处"</span><span class="sxs-lookup"><span data-stu-id="01d18-153">"Move <app> here"</span></span>
* <span data-ttu-id="01d18-154">"拍摄照片"</span><span class="sxs-lookup"><span data-stu-id="01d18-154">"Take a picture"</span></span>
* <span data-ttu-id="01d18-155">"开始录制"</span><span class="sxs-lookup"><span data-stu-id="01d18-155">"Start recording"</span></span>
* <span data-ttu-id="01d18-156">"停止录制"</span><span class="sxs-lookup"><span data-stu-id="01d18-156">"Stop recording"</span></span>
* <span data-ttu-id="01d18-157">"显示现有的光线"</span><span class="sxs-lookup"><span data-stu-id="01d18-157">"Show hand ray"</span></span>
* <span data-ttu-id="01d18-158">"隐藏现有的光线"</span><span class="sxs-lookup"><span data-stu-id="01d18-158">"Hide hand ray"</span></span>
* <span data-ttu-id="01d18-159">"增加亮度"</span><span class="sxs-lookup"><span data-stu-id="01d18-159">"Increase the brightness"</span></span>
* <span data-ttu-id="01d18-160">"降低亮度"</span><span class="sxs-lookup"><span data-stu-id="01d18-160">"Decrease the brightness"</span></span>
* <span data-ttu-id="01d18-161">"增加音量"</span><span class="sxs-lookup"><span data-stu-id="01d18-161">"Increase the volume"</span></span>
* <span data-ttu-id="01d18-162">"降低音量"</span><span class="sxs-lookup"><span data-stu-id="01d18-162">"Decrease the volume"</span></span>
* <span data-ttu-id="01d18-163">"静音" 或 "取消静音"</span><span class="sxs-lookup"><span data-stu-id="01d18-163">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="01d18-164">"关闭设备"</span><span class="sxs-lookup"><span data-stu-id="01d18-164">"Shut down the device"</span></span>
* <span data-ttu-id="01d18-165">"重新启动设备"</span><span class="sxs-lookup"><span data-stu-id="01d18-165">"Restart the device"</span></span>
* <span data-ttu-id="01d18-166">"进入睡眠状态"</span><span class="sxs-lookup"><span data-stu-id="01d18-166">"Go to sleep"</span></span>
* <span data-ttu-id="01d18-167">"它是什么时间？"</span><span class="sxs-lookup"><span data-stu-id="01d18-167">"What time is it?"</span></span>
* <span data-ttu-id="01d18-168">"我有多少电池剩余电量？"</span><span class="sxs-lookup"><span data-stu-id="01d18-168">"How much battery do I have left?"</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="01d18-169">"看，说它"</span><span class="sxs-lookup"><span data-stu-id="01d18-169">"See It, Say It"</span></span><br>
        <span data-ttu-id="01d18-170">HoloLens 为语音输入提供了一个 "查看 it，假设 it" 模型，其中按钮上的标签告诉用户他们可以表达的语音命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-170">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="01d18-171">例如，在使用 HoloLens (第一代) 中查看应用窗口时，用户可以说 "调整" 命令来调整应用在世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="01d18-171">For example, when looking at an app window in HoloLens (1st gen), a user can say "Adjust" command to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="01d18-172">*图像：用户可以说 "调整" 命令，该命令显示在应用程序栏中以调整应用程序的位置*</span><span class="sxs-lookup"><span data-stu-id="01d18-172">*Image: A user can say the "Adjust" command, which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="01d18-173">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="01d18-173">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="01d18-174">![查看应用程序窗口或全息图时，用户可以说 "调整" 命令，该命令显示在应用程序栏中，用于调整应用在世界中的位置。](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="01d18-174">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="01d18-175">当应用遵循此规则时，用户可以轻松地了解要控制系统的内容。</span><span class="sxs-lookup"><span data-stu-id="01d18-175">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="01d18-176">Gazing 在 HoloLens (第一代) 中的某个按钮上，你会看到一个 "声音停留" 工具提示，该工具提示在一秒钟后出现，如果按钮已启用语音，并显示 "按" 的命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-176">While gazing at a button in HoloLens (1st gen), you'll see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="01d18-177">若要在 HoloLens 2 中显示语音工具提示，请通过说 "选择" 或 "我可以说什么" 来显示语音光标 (查看图像) 。</span><span class="sxs-lookup"><span data-stu-id="01d18-177">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="01d18-178">*图像： "查看它，假设" 命令显示在按钮下方*</span><span class="sxs-lookup"><span data-stu-id="01d18-178">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![查看它，假设 "](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="01d18-180">用于快速全息影像操作的语音命令</span><span class="sxs-lookup"><span data-stu-id="01d18-180">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="01d18-181">在 gazing 时，可以使用许多语音命令来快速执行操作任务。</span><span class="sxs-lookup"><span data-stu-id="01d18-181">There are many voice commands you can say while gazing at a hologram to quickly do manipulation tasks.</span></span> <span data-ttu-id="01d18-182">这些语音命令适用于你放置在世界中的应用程序窗口和3D 对象。</span><span class="sxs-lookup"><span data-stu-id="01d18-182">These voice commands work on app windows and 3D objects you've placed in the world.</span></span>

<span data-ttu-id="01d18-183">**全息图操作命令**</span><span class="sxs-lookup"><span data-stu-id="01d18-183">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="01d18-184">面部</span><span class="sxs-lookup"><span data-stu-id="01d18-184">Face me</span></span>
* <span data-ttu-id="01d18-185">更大 |完善</span><span class="sxs-lookup"><span data-stu-id="01d18-185">Bigger | Enhance</span></span>
* <span data-ttu-id="01d18-186">较小</span><span class="sxs-lookup"><span data-stu-id="01d18-186">Smaller</span></span>

<span data-ttu-id="01d18-187">在 HoloLens 2 上，你还可以结合眼睛创建更自然的交互，从而隐式地提供有关所引用内容的上下文信息。</span><span class="sxs-lookup"><span data-stu-id="01d18-187">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze, which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="01d18-188">例如，您可以查看全息图，说 "放置 _此_ 内容"，然后在要放置它的位置上进行查看，并显示 "在 _此处_"。</span><span class="sxs-lookup"><span data-stu-id="01d18-188">For example, you could look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="01d18-189">您也可以在复杂的计算机上查看全息部分，并说： "向我介绍有关 _此_ 的详细信息"。</span><span class="sxs-lookup"><span data-stu-id="01d18-189">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>

## <a name="discovering-voice-commands"></a><span data-ttu-id="01d18-190">发现语音命令</span><span class="sxs-lookup"><span data-stu-id="01d18-190">Discovering voice commands</span></span>

<span data-ttu-id="01d18-191">某些命令（如上面用于快速操作的命令）可以隐藏。</span><span class="sxs-lookup"><span data-stu-id="01d18-191">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="01d18-192">若要了解可以使用的命令，请看一看对象并说 "我可以说什么？"。</span><span class="sxs-lookup"><span data-stu-id="01d18-192">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="01d18-193">将弹出的可能命令的列表。</span><span class="sxs-lookup"><span data-stu-id="01d18-193">A list of possible commands pops up.</span></span> <span data-ttu-id="01d18-194">你还可以使用打印头的光标来浏览并显示你前面每个按钮的语音工具提示。</span><span class="sxs-lookup"><span data-stu-id="01d18-194">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="01d18-195">如果需要完整的列表，请随时说 "显示所有命令"。</span><span class="sxs-lookup"><span data-stu-id="01d18-195">If you want a complete list, just say, "Show all commands" anytime.</span></span> 

## <a name="dictation"></a><span data-ttu-id="01d18-196">听写</span><span class="sxs-lookup"><span data-stu-id="01d18-196">Dictation</span></span>

<span data-ttu-id="01d18-197">语音听写可以更高效地向应用程序中输入文本，而不是使用 [空中点击](gaze-and-commit.md#composite-gestures)。</span><span class="sxs-lookup"><span data-stu-id="01d18-197">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="01d18-198">这可以极大地加快用户的输入。</span><span class="sxs-lookup"><span data-stu-id="01d18-198">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="01d18-199">![语音听写开始，选择 "麦克风" 按钮](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="01d18-199">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="01d18-200">*语音听写开始于选择键盘上的麦克风按钮*</span><span class="sxs-lookup"><span data-stu-id="01d18-200">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="01d18-201">只要全息键盘处于活动状态，就可以切换到听写模式，而不是键入。</span><span class="sxs-lookup"><span data-stu-id="01d18-201">Anytime the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="01d18-202">选择文本输入框一侧的麦克风以开始使用。</span><span class="sxs-lookup"><span data-stu-id="01d18-202">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="01d18-203">向应用添加语音命令</span><span class="sxs-lookup"><span data-stu-id="01d18-203">Adding voice commands to your app</span></span>

<span data-ttu-id="01d18-204">考虑为生成的任何体验添加语音命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-204">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="01d18-205">语音是控制系统和应用的强大方式。</span><span class="sxs-lookup"><span data-stu-id="01d18-205">Voice is a powerful way control the system and apps.</span></span> <span data-ttu-id="01d18-206">由于用户使用不同类型的方言和重音说话，因此正确选择语音关键字会确保明确解释用户的命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-206">Because users speak with different kinds of dialects and accents, proper choice of speech keywords will make sure your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="01d18-207">最佳实践</span><span class="sxs-lookup"><span data-stu-id="01d18-207">Best practices</span></span>

<span data-ttu-id="01d18-208">以下是一些有助于流畅语音识别的做法。</span><span class="sxs-lookup"><span data-stu-id="01d18-208">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="01d18-209">**使用简明命令** - 如果可能的话，选择两个或更多音节的关键词。</span><span class="sxs-lookup"><span data-stu-id="01d18-209">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="01d18-210">不同口音的人说单音节词时倾向于使用不同的元音。</span><span class="sxs-lookup"><span data-stu-id="01d18-210">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="01d18-211">示例："播放视频"优于"播放当前选定的视频"</span><span class="sxs-lookup"><span data-stu-id="01d18-211">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="01d18-212">**使用简单的词汇** - 示例："显示笔记"优于"显示图块"</span><span class="sxs-lookup"><span data-stu-id="01d18-212">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="01d18-213">**确保命令是非** 破坏性的 - 确保任何语音命令操作都是非破坏性的，并且很容易在用户附近说话的另一个人意外触发命令时撤消。</span><span class="sxs-lookup"><span data-stu-id="01d18-213">**Make sure commands are non-destructive** - Make sure any speech command actions are non-destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="01d18-214">**避免类似的声音命令** - 避免注册多个声音相似的语音命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-214">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound similar.</span></span> <span data-ttu-id="01d18-215">示例："显示更多"和"显示商店"可能类似。</span><span class="sxs-lookup"><span data-stu-id="01d18-215">Example: "Show more" and "Show store" can be similar sounding.</span></span>
* <span data-ttu-id="01d18-216">在应用未使用时取消注册应用 **-** 当应用未位于特定语音命令有效的状态时，请考虑取消注册应用，以便其他命令不会混淆该命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-216">**Unregister your app when not it uses** - When your app isn't in a state in which a particular speech command is valid, consider unregistering it so that other commands aren't confused for that one.</span></span>
* <span data-ttu-id="01d18-217">**使用不同的口音进行测试** - 由具有不同口音的用户测试应用。</span><span class="sxs-lookup"><span data-stu-id="01d18-217">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="01d18-218">**保持语音命令一致性** - 如果“返回”可转到上一页，请在应用程序中保持此行为。</span><span class="sxs-lookup"><span data-stu-id="01d18-218">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="01d18-219">**避免使用系统** 命令 - 为系统保留以下语音命令，因此请避免在应用程序中使用它们：</span><span class="sxs-lookup"><span data-stu-id="01d18-219">**Avoid using system commands** - The following voice commands are reserved for the system, so avoid using them in your applications:</span></span>
   * <span data-ttu-id="01d18-220">“你好小娜”</span><span class="sxs-lookup"><span data-stu-id="01d18-220">"Hey Cortana"</span></span>
   * <span data-ttu-id="01d18-221">“选择”</span><span class="sxs-lookup"><span data-stu-id="01d18-221">"Select"</span></span>
   * <span data-ttu-id="01d18-222">"转到开始"</span><span class="sxs-lookup"><span data-stu-id="01d18-222">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="01d18-223">语音输入的优点</span><span class="sxs-lookup"><span data-stu-id="01d18-223">Advantages of voice input</span></span>

<span data-ttu-id="01d18-224">语音输入是传达我们意图的自然方式。</span><span class="sxs-lookup"><span data-stu-id="01d18-224">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="01d18-225">语音特别适用于接口 **遍历** ，因为它可以帮助用户完成接口的多个步骤。</span><span class="sxs-lookup"><span data-stu-id="01d18-225">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface.</span></span> <span data-ttu-id="01d18-226">用户在查看网页时可能会说"返回"，而不必向上键并点击应用中的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="01d18-226">A user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app.</span></span> <span data-ttu-id="01d18-227">这种小的时间 **节省对用户** 对体验的认知具有强大的情感影响，并为用户提供了少量的视觉障碍。</span><span class="sxs-lookup"><span data-stu-id="01d18-227">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="01d18-228">当我们忙得不可开交或同时处理多项任务时，使用语音也是一种方便的输入方法。</span><span class="sxs-lookup"><span data-stu-id="01d18-228">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="01d18-229">在难以在键盘上键入的设备上，语音听写可能是输入文本的一种有效替代方法。</span><span class="sxs-lookup"><span data-stu-id="01d18-229">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="01d18-230">最后，在某些情况下，当凝视和手势的准确性范围受到限制时，语音有助于解除用户意向的混乱。</span><span class="sxs-lookup"><span data-stu-id="01d18-230">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="01d18-231">**语音的使用如何让用户受益**</span><span class="sxs-lookup"><span data-stu-id="01d18-231">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="01d18-232">省时 - 它应该使最终目标更高效。</span><span class="sxs-lookup"><span data-stu-id="01d18-232">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="01d18-233">最大限度地减少工作量 - 它应该使任务更加流畅和轻松。</span><span class="sxs-lookup"><span data-stu-id="01d18-233">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="01d18-234">减少认知压力 - 它是直观的，易于学习和记忆。</span><span class="sxs-lookup"><span data-stu-id="01d18-234">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="01d18-235">这是在社交上可接受的 - 它应符合社会行为规范。</span><span class="sxs-lookup"><span data-stu-id="01d18-235">It's socially acceptable - it should fit in with societal norms of behavior.</span></span>
* <span data-ttu-id="01d18-236">它是常规的 - 语音很容易成为一种习惯行为。</span><span class="sxs-lookup"><span data-stu-id="01d18-236">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="01d18-237">语音输入的挑战</span><span class="sxs-lookup"><span data-stu-id="01d18-237">Challenges for voice input</span></span>

<span data-ttu-id="01d18-238">虽然语音输入非常适用于许多不同的应用程序，但它也面临一些挑战。</span><span class="sxs-lookup"><span data-stu-id="01d18-238">While voice input is great for many different applications, it also faces several challenges.</span></span> <span data-ttu-id="01d18-239">了解语音输入的优点和难题使应用开发人员能够更智能地选择语音输入的使用方式和时间，并为用户提供出色的体验。</span><span class="sxs-lookup"><span data-stu-id="01d18-239">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="01d18-240">**连续输入控件的语音输入** 精细控制就是其中之一。</span><span class="sxs-lookup"><span data-stu-id="01d18-240">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="01d18-241">例如，用户可能需要更改其音乐应用中的音量。</span><span class="sxs-lookup"><span data-stu-id="01d18-241">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="01d18-242">她可能会说"声音更响"，但不清楚系统应该如何放大音量。</span><span class="sxs-lookup"><span data-stu-id="01d18-242">She can say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="01d18-243">用户可以说："稍微大一点"，但"一点"很难量化。</span><span class="sxs-lookup"><span data-stu-id="01d18-243">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="01d18-244">使用语音移动或缩放全息影像同样困难。</span><span class="sxs-lookup"><span data-stu-id="01d18-244">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="01d18-245">**语音输入检测的可靠性** 虽然语音输入系统变得越来越好，但有时它们可能会错误地听到和解释语音命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-245">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="01d18-246">关键在于应对应用程序中的挑战。</span><span class="sxs-lookup"><span data-stu-id="01d18-246">The key is to address the challenge in your application.</span></span> <span data-ttu-id="01d18-247">当系统正在侦听时，向用户提供反馈，系统所理解内容阐明了理解用户语音的潜在问题。</span><span class="sxs-lookup"><span data-stu-id="01d18-247">Provide feedback to your users when the system is listening and what the system understood clarifies potential issues understanding the users' speech.</span></span>  

<span data-ttu-id="01d18-248">**共享空间中的语音输入** 在与他人共享的空间内，语音在社交上可能不可接受。</span><span class="sxs-lookup"><span data-stu-id="01d18-248">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="01d18-249">以下是一些示例：</span><span class="sxs-lookup"><span data-stu-id="01d18-249">Here are a few examples:</span></span>
* <span data-ttu-id="01d18-250">用户可能不希望干扰其他人 (例如，在静默的库或共享办公) </span><span class="sxs-lookup"><span data-stu-id="01d18-250">The user may not want to disturb others (for example, in a quiet library or shared office)</span></span>
* <span data-ttu-id="01d18-251">在公共场合与自己交谈时，用户可能会感到困难，</span><span class="sxs-lookup"><span data-stu-id="01d18-251">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="01d18-252">用户可能会觉得听写个人或机密 (包括密码) 其他人正在侦听</span><span class="sxs-lookup"><span data-stu-id="01d18-252">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="01d18-253">**唯一或未知单词的语音输入** 当用户听写系统可能未知的字词（如昵称、某些语言字词或缩写）时，也难以进行语音输入。</span><span class="sxs-lookup"><span data-stu-id="01d18-253">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words, or abbreviations.</span></span> 

<span data-ttu-id="01d18-254">**学习语音命令** 虽然最终目标是自然地与系统进行交谈，但应用通常仍依赖于特定的预定义语音命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-254">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="01d18-255">与一组重要的语音命令相关的一项挑战是如何在不重载用户的情况下教授它们，以及如何帮助用户保留它们。</span><span class="sxs-lookup"><span data-stu-id="01d18-255">A challenge associated with a significant set of voice commands is how to teach them without overloading the user and how to help the user to keep them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="01d18-256">语音反馈状态</span><span class="sxs-lookup"><span data-stu-id="01d18-256">Voice feedback states</span></span>

<span data-ttu-id="01d18-257">当语音应用正确时，用户了解他们能说什么，并得到清晰的反馈 - 系统正确地听到了用户说的话。</span><span class="sxs-lookup"><span data-stu-id="01d18-257">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="01d18-258">这两个信号使用户在使用语音作为主要输入方法时充满自信。</span><span class="sxs-lookup"><span data-stu-id="01d18-258">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="01d18-259">下面的图表显示了识别语音输入时光标发生的情况以及它是如何将信息传达给用户的。</span><span class="sxs-lookup"><span data-stu-id="01d18-259">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="01d18-260">![1.常规游标状态](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="01d18-260">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="01d18-261">**1.常规游标状态**</span><span class="sxs-lookup"><span data-stu-id="01d18-261">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01d18-262">![2.传达语音反馈，然后消失](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="01d18-262">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="01d18-263">**2.传达语音反馈，然后消失**</span><span class="sxs-lookup"><span data-stu-id="01d18-263">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01d18-264">![\*3.</span><span class="sxs-lookup"><span data-stu-id="01d18-264">![\*3.</span></span> <span data-ttu-id="01d18-265">常规游标状态](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="01d18-265">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="01d18-266">**3.返回到常规游标状态**</span><span class="sxs-lookup"><span data-stu-id="01d18-266">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="01d18-267">在混合现实中，用户应该知道的关于“语音”的重要事项</span><span class="sxs-lookup"><span data-stu-id="01d18-267">Top things users should know about "speech" in mixed reality</span></span>

* <span data-ttu-id="01d18-268">在 **以按钮** 为目标时说" ("，可以在任意位置使用它来选择按钮) 。</span><span class="sxs-lookup"><span data-stu-id="01d18-268">Say **"Select"** while targeting a button (you can use this anywhere to select a button).</span></span>
* <span data-ttu-id="01d18-269">可以在某些应用中通过说出应用栏按钮的标签名称来执行操作。</span><span class="sxs-lookup"><span data-stu-id="01d18-269">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="01d18-270">例如，在查看应用时，用户可以说"删除"命令从世界中删除应用 (这样可以节省时间，无需手动选择) 。</span><span class="sxs-lookup"><span data-stu-id="01d18-270">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to select it with your hand).</span></span>
* <span data-ttu-id="01d18-271">可以通过说" **你好 Cortana"来启动 Cortana 侦听。**</span><span class="sxs-lookup"><span data-stu-id="01d18-271">You can start Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="01d18-272">你可以向她提问（“你好小娜，埃菲尔铁塔有多高”），告诉她打开应用（“你好小娜，打开 Netflix”），或告诉她调出“开始”菜单（“你好小娜，带我回家”）等等。</span><span class="sxs-lookup"><span data-stu-id="01d18-272">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="01d18-273">用户对语音的常见问题和关注点</span><span class="sxs-lookup"><span data-stu-id="01d18-273">Common questions and concerns users have about voice</span></span>

* <span data-ttu-id="01d18-274">我可以说什么？</span><span class="sxs-lookup"><span data-stu-id="01d18-274">What can I say?</span></span>
* <span data-ttu-id="01d18-275">我如何知道系统正确听到了我说的话？</span><span class="sxs-lookup"><span data-stu-id="01d18-275">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="01d18-276">系统总是理解错误我的语音命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-276">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="01d18-277">当我发出语音命令时，系统不会做出反应。</span><span class="sxs-lookup"><span data-stu-id="01d18-277">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="01d18-278">当我发出语音命令时，系统的反应是错误的。</span><span class="sxs-lookup"><span data-stu-id="01d18-278">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="01d18-279">我如何将我的语音定向到一个特定的应用或应用命令？</span><span class="sxs-lookup"><span data-stu-id="01d18-279">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="01d18-280">我可以使用语音来对 HoloLens 上的全息帧执行命令吗？</span><span class="sxs-lookup"><span data-stu-id="01d18-280">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="01d18-281">通信</span><span class="sxs-lookup"><span data-stu-id="01d18-281">Communication</span></span>

<span data-ttu-id="01d18-282">对于想要利用 HoloLens 提供的自定义音频输入处理选项的应用程序，了解应用可以使用的各种音频流类别非常重要。 [](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category)</span><span class="sxs-lookup"><span data-stu-id="01d18-282">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it's important to understand the various [audio stream categories](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) your app can consume.</span></span> <span data-ttu-id="01d18-283">Windows 10 支持多个不同的流类别，HoloLens 利用这三种类别来启用自定义处理，以优化为语音、通信和其他而定制的麦克风音频质量，这些音频质量可用于环境音频捕获 (即"camcorder") 方案。</span><span class="sxs-lookup"><span data-stu-id="01d18-283">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication, and other, which can be used for ambient environment audio capture (that is, "camcorder") scenarios.</span></span>
* <span data-ttu-id="01d18-284">"AudioCategory_Communications流"类别针对通话质量和旁白方案进行自定义，为客户端提供用户语音的 16 kHz 24 位单声道音频流</span><span class="sxs-lookup"><span data-stu-id="01d18-284">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16-kHz 24-bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="01d18-285">AudioCategory_Speech流类别是针对 HoloLens (Windows) 语音引擎自定义的，并提供用户语音的 16 kHz 24 位单声道流。</span><span class="sxs-lookup"><span data-stu-id="01d18-285">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16-kHz 24-bit mono stream of the user's voice.</span></span> <span data-ttu-id="01d18-286">如果需要，第三方语音引擎可以使用此类别。</span><span class="sxs-lookup"><span data-stu-id="01d18-286">This category can be used by third-party speech engines if needed.</span></span>
* <span data-ttu-id="01d18-287">流AudioCategory_Other环境音频录制自定义的流类别，为客户端提供 48 kHz 24 位立体声音频流。</span><span class="sxs-lookup"><span data-stu-id="01d18-287">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48-kHz 24-bit stereo audio stream.</span></span>

<span data-ttu-id="01d18-288">所有这些音频处理都是硬件加速的，这意味着与在 HoloLens CPU 上执行相同的处理相比，功能消耗的功率要少得多。</span><span class="sxs-lookup"><span data-stu-id="01d18-288">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="01d18-289">避免在 CPU 上运行其他音频输入处理，以最大化系统电池使用时间，并充分利用内置的卸载音频输入处理。</span><span class="sxs-lookup"><span data-stu-id="01d18-289">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built-in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="01d18-290">语言</span><span class="sxs-lookup"><span data-stu-id="01d18-290">Languages</span></span>

<span data-ttu-id="01d18-291">HoloLens 2 [支持多种语言](/hololens/hololens2-language-support)。</span><span class="sxs-lookup"><span data-stu-id="01d18-291">HoloLens 2 [supports multiple languages](/hololens/hololens2-language-support).</span></span> <span data-ttu-id="01d18-292">请记住，即使安装了多个键盘，或者应用尝试使用不同的语言创建语音识别器，语音命令也始终以系统的显示语言运行。</span><span class="sxs-lookup"><span data-stu-id="01d18-292">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="01d18-293">疑难解答</span><span class="sxs-lookup"><span data-stu-id="01d18-293">Troubleshooting</span></span>

<span data-ttu-id="01d18-294">如果在使用"select"和"Hey Cortana"时遇到任何问题，请尝试移动到更静默的空间、远离干扰源，或者更响一点。</span><span class="sxs-lookup"><span data-stu-id="01d18-294">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="01d18-295">目前，HoloLens 上的所有语音识别都专门针对英语的本机美国优化。</span><span class="sxs-lookup"><span data-stu-id="01d18-295">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="01d18-296">对于 Windows Mixed Reality Developer Edition 2017，在初始 HMD 连接后注销并返回到电脑桌面后 (音频终结点管理逻辑) 永久正常工作。</span><span class="sxs-lookup"><span data-stu-id="01d18-296">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="01d18-297">在通过 WMR OOBE 后首次注销/登录事件之前，用户可能会遇到各种音频功能问题，从无音频到无音频切换，具体取决于首次连接 HMD 之前系统设置方式。</span><span class="sxs-lookup"><span data-stu-id="01d18-297">Before that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up before connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="01d18-298">适用于 Unity 的混合现实工具包 (MRTK) 语音输入</span><span class="sxs-lookup"><span data-stu-id="01d18-298">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="01d18-299">使用 **[MRTK，](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 可以轻松地在任何对象上分配语音命令。</span><span class="sxs-lookup"><span data-stu-id="01d18-299">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="01d18-300">使用 MRTK 的 **语音输入配置文件** 定义关键字。</span><span class="sxs-lookup"><span data-stu-id="01d18-300">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="01d18-301">通过分配 **SpeechInputHandler** 脚本，你可以使任何对象响应语音输入配置文件中定义的关键字。</span><span class="sxs-lookup"><span data-stu-id="01d18-301">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="01d18-302">SpeechInputHandler 还提供了语音确认标签以提高用户信心。</span><span class="sxs-lookup"><span data-stu-id="01d18-302">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="01d18-303">MRTK-语音命令</span><span class="sxs-lookup"><span data-stu-id="01d18-303">MRTK - Voice command</span></span>](/windows/mixed-reality/mrtk-unity/features/input/speech)

---

## <a name="see-also"></a><span data-ttu-id="01d18-304">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01d18-304">See also</span></span>

* [<span data-ttu-id="01d18-305">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="01d18-305">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="01d18-306">本能交互</span><span class="sxs-lookup"><span data-stu-id="01d18-306">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="01d18-307">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="01d18-307">Voice input in DirectX</span></span>](../develop/native/voice-input-in-directx.md)
* [<span data-ttu-id="01d18-308">Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="01d18-308">Voice input in Unity</span></span>](../develop/unity/voice-input-in-unity.md)