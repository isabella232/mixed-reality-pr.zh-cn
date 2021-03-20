---
title: HoloLens (第一代) 输入 211-手势
description: 按照以下编码演练操作，使用 Unity、Visual Studio 和 HoloLens 来了解手势概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，学院，教程，手势，HoloLens，混合现实学院，unity，混合现实耳机，windows Mixed reality 耳机，虚拟现实耳机，Windows 10
ms.openlocfilehash: fe5d3d736c3ad460feeb7aaf66597344618bc1cb
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730454"
---
# <a name="hololens-1st-gen-input-211-gesture"></a><span data-ttu-id="56fbb-104">HoloLens (第一代) 输入211：手势</span><span class="sxs-lookup"><span data-stu-id="56fbb-104">HoloLens (1st gen) Input 211: Gesture</span></span>

>[!NOTE]
><span data-ttu-id="56fbb-105">混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="56fbb-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="56fbb-106">因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。</span><span class="sxs-lookup"><span data-stu-id="56fbb-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="56fbb-107">我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。</span><span class="sxs-lookup"><span data-stu-id="56fbb-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="56fbb-108">我们将维护这些教程，使之持续适用于支持的设备。</span><span class="sxs-lookup"><span data-stu-id="56fbb-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="56fbb-109">已经为 HoloLens 2 发布了[一系列新教程](./mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="56fbb-109">[A new series of tutorials](./mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="56fbb-110">[手势](../../../design/gaze-and-commit.md#composite-gestures) 会使用户意向变为操作。</span><span class="sxs-lookup"><span data-stu-id="56fbb-110">[Gestures](../../../design/gaze-and-commit.md#composite-gestures) turn user intention into action.</span></span> <span data-ttu-id="56fbb-111">用户可以使用手势来与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="56fbb-111">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="56fbb-112">在本课程中，我们将了解如何跟踪用户的动手，响应用户输入，并根据手头状态和位置向用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="56fbb-112">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="56fbb-113">在 [先生/女士 101](../../../develop/unity/tutorials/holograms-101.md)中，我们使用了一种简单的点击手势来与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="56fbb-113">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="56fbb-114">现在，我们将转到轻攻攻攻，并探索新的概念：</span><span class="sxs-lookup"><span data-stu-id="56fbb-114">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="56fbb-115">检测何时跟踪用户的手并向用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="56fbb-115">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="56fbb-116">使用导航手势旋转全息影像。</span><span class="sxs-lookup"><span data-stu-id="56fbb-116">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="56fbb-117">请在用户即将退出查看时提供反馈。</span><span class="sxs-lookup"><span data-stu-id="56fbb-117">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="56fbb-118">使用操作事件可允许用户使用其手移动全息影像。</span><span class="sxs-lookup"><span data-stu-id="56fbb-118">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="56fbb-119">在本课程中，我们将重新访问 Unity 项目 **模型资源管理器，该资源管理器** 是在 [MR Input 210](holograms-210.md)中生成的。</span><span class="sxs-lookup"><span data-stu-id="56fbb-119">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="56fbb-120">我们 astronaut 的朋友会回来，帮助我们探索这些新的手势概念。</span><span class="sxs-lookup"><span data-stu-id="56fbb-120">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="56fbb-121">以下各章中嵌入的视频使用较旧版本的 Unity 和混合现实工具包记录。</span><span class="sxs-lookup"><span data-stu-id="56fbb-121">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="56fbb-122">虽然分步说明准确且最新，但你可能会看到处于过期状态的相应视频中的脚本和视觉对象。</span><span class="sxs-lookup"><span data-stu-id="56fbb-122">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="56fbb-123">视频仍包含在 posterity 中，因为涵盖的概念仍适用。</span><span class="sxs-lookup"><span data-stu-id="56fbb-123">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="56fbb-124">设备支持</span><span class="sxs-lookup"><span data-stu-id="56fbb-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="56fbb-125">课程</span><span class="sxs-lookup"><span data-stu-id="56fbb-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="56fbb-126"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="56fbb-126"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="56fbb-127"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="56fbb-127"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="56fbb-128">MR 输入 211：手势</span><span class="sxs-lookup"><span data-stu-id="56fbb-128">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="56fbb-129">✔️</span><span class="sxs-lookup"><span data-stu-id="56fbb-129">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="56fbb-130">✔️</span><span class="sxs-lookup"><span data-stu-id="56fbb-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="56fbb-131">准备工作</span><span class="sxs-lookup"><span data-stu-id="56fbb-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="56fbb-132">必备条件</span><span class="sxs-lookup"><span data-stu-id="56fbb-132">Prerequisites</span></span>

* <span data-ttu-id="56fbb-133">配置了正确 [工具](../../../develop/install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="56fbb-133">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="56fbb-134">一些基本 c # 编程能力。</span><span class="sxs-lookup"><span data-stu-id="56fbb-134">Some basic C# programming ability.</span></span>
* <span data-ttu-id="56fbb-135">应已完成 [尊敬的基本知识 101](../../../develop/unity/tutorials/holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="56fbb-135">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="56fbb-136">应已完成 [MR 输入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="56fbb-136">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="56fbb-137">[为开发配置](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="56fbb-137">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="56fbb-138">项目文件</span><span class="sxs-lookup"><span data-stu-id="56fbb-138">Project files</span></span>

* <span data-ttu-id="56fbb-139">下载项目所需的 [文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) 。</span><span class="sxs-lookup"><span data-stu-id="56fbb-139">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span> <span data-ttu-id="56fbb-140">需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="56fbb-140">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="56fbb-141">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="56fbb-141">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="56fbb-142">如果要在下载之前查看源代码， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)找到。</span><span class="sxs-lookup"><span data-stu-id="56fbb-142">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="56fbb-143">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="56fbb-143">Errata and Notes</span></span>

* <span data-ttu-id="56fbb-144">需要在 Visual Studio 的 "工具"-">选项->调试" 中禁用 "启用仅我的代码" (*取消选中*) ，以便在代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="56fbb-144">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="56fbb-145">第0章-Unity 设置</span><span class="sxs-lookup"><span data-stu-id="56fbb-145">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="56fbb-146">说明</span><span class="sxs-lookup"><span data-stu-id="56fbb-146">Instructions</span></span>

1. <span data-ttu-id="56fbb-147">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="56fbb-147">Start Unity.</span></span>
2. <span data-ttu-id="56fbb-148">选择“打开”。</span><span class="sxs-lookup"><span data-stu-id="56fbb-148">Select **Open**.</span></span>
3. <span data-ttu-id="56fbb-149">导航到之前未存档的 **手势** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="56fbb-149">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="56fbb-150">查找并选择 "**启动** / **模型资源管理器**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="56fbb-150">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="56fbb-151">单击 " **选择文件夹** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="56fbb-151">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="56fbb-152">在 " **项目** " 面板中，展开 " **场景** " 文件夹。</span><span class="sxs-lookup"><span data-stu-id="56fbb-152">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="56fbb-153">双击 " **ModelExplorer** 场景" 将其加载到 Unity。</span><span class="sxs-lookup"><span data-stu-id="56fbb-153">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="56fbb-154">生成</span><span class="sxs-lookup"><span data-stu-id="56fbb-154">Building</span></span>

1. <span data-ttu-id="56fbb-155">在 Unity 中，选择 " **文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-155">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="56fbb-156">如果场景 **/ModelExplorer** 未列在 " **生成**" 中，请单击 " **添加打开的场景** " 添加场景。</span><span class="sxs-lookup"><span data-stu-id="56fbb-156">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="56fbb-157">如果要专门针对 HoloLens 进行开发，请将 " **目标设备** " 设置为 " **hololens**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-157">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="56fbb-158">否则，请将其留在 **任何设备** 上。</span><span class="sxs-lookup"><span data-stu-id="56fbb-158">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="56fbb-159">确保将 " **生成类型** " 设置为 " **D3D** "，并将 " **Sdk** " 设置为 " **最新安装** 的 (，这应是 SDK 16299 或更高) 版本</span><span class="sxs-lookup"><span data-stu-id="56fbb-159">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="56fbb-160">单击“生成”。</span><span class="sxs-lookup"><span data-stu-id="56fbb-160">Click **Build**.</span></span>
6. <span data-ttu-id="56fbb-161">创建名为 "App" 的 **新文件夹** 。</span><span class="sxs-lookup"><span data-stu-id="56fbb-161">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="56fbb-162">单击 **应用** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="56fbb-162">Single click the **App** folder.</span></span>
8. <span data-ttu-id="56fbb-163">按 **选择文件夹** ，Unity 将开始为 Visual Studio 生成项目。</span><span class="sxs-lookup"><span data-stu-id="56fbb-163">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="56fbb-164">当 Unity 完成后，将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="56fbb-164">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="56fbb-165">打开 **应用程序** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="56fbb-165">Open the **App** folder.</span></span>
2. <span data-ttu-id="56fbb-166">打开 **ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-166">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="56fbb-167">如果部署到 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="56fbb-167">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="56fbb-168">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 " **发布** "，将 "从 ARM" 更改为 " **x86**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-168">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="56fbb-169">单击 "本地计算机" 按钮旁的下拉箭头，然后选择 " **远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-169">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="56fbb-170">输入 **HoloLens 设备 IP 地址** ，并将身份验证模式设置为 **通用 (未加密协议)**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-170">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="56fbb-171">单击“选择”  。</span><span class="sxs-lookup"><span data-stu-id="56fbb-171">Click **Select**.</span></span> <span data-ttu-id="56fbb-172">如果你不知道设备 IP 地址，请在 "设置" 中查找 " **> 网络 & Internet > 高级选项**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-172">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="56fbb-173">在顶部菜单栏中，单击 " **调试-> 启动而不调试** " 或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-173">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="56fbb-174">如果这是首次部署到设备，则需要将 [其与 Visual Studio 配对](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="56fbb-174">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="56fbb-175">当应用程序已部署后，使用 **选择手势** 关闭 **Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="56fbb-175">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="56fbb-176">如果要部署到沉浸式耳机：</span><span class="sxs-lookup"><span data-stu-id="56fbb-176">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="56fbb-177">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 " **发布** "，将 "从 ARM" 更改为 " **x64**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-177">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="56fbb-178">确保将部署目标设置为 " **本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-178">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="56fbb-179">在顶部菜单栏中，单击 " **调试-> 启动而不调试** " 或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="56fbb-180">当应用程序已部署后，通过将触发器拖到运动控制器上来关闭 **Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="56fbb-180">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="56fbb-181">你可能会注意到 Visual Studio 错误面板中出现一些红色错误。</span><span class="sxs-lookup"><span data-stu-id="56fbb-181">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="56fbb-182">可以放心地忽略它们。</span><span class="sxs-lookup"><span data-stu-id="56fbb-182">It is safe to ignore them.</span></span> <span data-ttu-id="56fbb-183">切换到 "输出" 面板以查看实际的生成进度。</span><span class="sxs-lookup"><span data-stu-id="56fbb-183">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="56fbb-184">"输出" 面板中的错误将要求您进行修补 (最常见的原因是脚本) 出错。</span><span class="sxs-lookup"><span data-stu-id="56fbb-184">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="56fbb-185">第1章-手动检测的反馈</span><span class="sxs-lookup"><span data-stu-id="56fbb-185">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="56fbb-186">目标</span><span class="sxs-lookup"><span data-stu-id="56fbb-186">Objectives</span></span>

* <span data-ttu-id="56fbb-187">订阅手动跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="56fbb-187">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="56fbb-188">使用光标反馈向用户显示要跟踪的用户。</span><span class="sxs-lookup"><span data-stu-id="56fbb-188">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="56fbb-189">在 HoloLens 2 上，只要指针可见，就会触发指针 (而不是指手指向上) 。</span><span class="sxs-lookup"><span data-stu-id="56fbb-189">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="56fbb-190">说明</span><span class="sxs-lookup"><span data-stu-id="56fbb-190">Instructions</span></span>

* <span data-ttu-id="56fbb-191">在 " **层次结构** " 面板中，展开 " **InputManager** " 对象。</span><span class="sxs-lookup"><span data-stu-id="56fbb-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="56fbb-192">查找并选择 " **GesturesInput** " 对象。</span><span class="sxs-lookup"><span data-stu-id="56fbb-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="56fbb-193">**InteractionInputSource** 脚本将执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="56fbb-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="56fbb-194">订阅 InteractionSourceDetected 和 InteractionSourceLost 事件。</span><span class="sxs-lookup"><span data-stu-id="56fbb-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="56fbb-195">设置 HandDetected 状态。</span><span class="sxs-lookup"><span data-stu-id="56fbb-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="56fbb-196">取消订阅 InteractionSourceDetected 和 InteractionSourceLost 事件。</span><span class="sxs-lookup"><span data-stu-id="56fbb-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="56fbb-197">接下来，我们将根据用户的操作，将游标从 [MR 输入 210](holograms-210.md) 升级到显示反馈的游标。</span><span class="sxs-lookup"><span data-stu-id="56fbb-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="56fbb-198">在 " **层次结构** " 面板中，选择 **光标** 对象并将其删除。</span><span class="sxs-lookup"><span data-stu-id="56fbb-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="56fbb-199">在 " **项目** " 面板中，搜索 " **CursorWithFeedback** " 并将其拖到 " **层次结构** " 面板中。</span><span class="sxs-lookup"><span data-stu-id="56fbb-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="56fbb-200">在 "**层次结构**" 面板中单击 " **InputManager** "，然后将 **CursorWithFeedback** 对象从 **层次结构** 中拖放到 **检查器** 底部的 InputManager **SimpleSinglePointerSelector** 的 "**游标**" 字段。</span><span class="sxs-lookup"><span data-stu-id="56fbb-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="56fbb-201">在 **层次结构** 中单击 " **CursorWithFeedback** "。</span><span class="sxs-lookup"><span data-stu-id="56fbb-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="56fbb-202">在 "**检查器**" 面板中，展开 **对象游标** 脚本上的 "**游标状态数据**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="56fbb-203">**游标状态数据** 的工作方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="56fbb-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="56fbb-204">任何 **观察** 状态都意味着未检测到任何手形，用户只需查看。</span><span class="sxs-lookup"><span data-stu-id="56fbb-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="56fbb-205">任何 **交互** 状态都表示检测到手型或控制器。</span><span class="sxs-lookup"><span data-stu-id="56fbb-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="56fbb-206">任何 **悬停** 状态都意味着用户正在查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="56fbb-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="56fbb-207">生成和部署</span><span class="sxs-lookup"><span data-stu-id="56fbb-207">Build and Deploy</span></span>

* <span data-ttu-id="56fbb-208">在 Unity 中，使用 **File > 生成设置** 重新生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="56fbb-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="56fbb-209">打开 **应用程序** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="56fbb-209">Open the **App** folder.</span></span>
* <span data-ttu-id="56fbb-210">如果它尚未打开，请打开 **ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="56fbb-211"> (如果在安装过程中已经在 Visual Studio 中生成了/部署了此项目，则可以打开 VS 的实例，并在出现) 提示时单击 "全部重新加载"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="56fbb-212">在 Visual Studio 中，单击 " **调试"-> "无调试开始** " 或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="56fbb-213">在应用程序部署到 HoloLens 后，请使用 "轻攻攻" 手势关闭 fitbox。</span><span class="sxs-lookup"><span data-stu-id="56fbb-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="56fbb-214">将您的手转到视图，并将您的索引手指指向天空，开始进行手动跟踪。</span><span class="sxs-lookup"><span data-stu-id="56fbb-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="56fbb-215">向左、向右、向下和向下移动。</span><span class="sxs-lookup"><span data-stu-id="56fbb-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="56fbb-216">监视在检测到您的手形后光标发生变化的方式，并从视图中丢失。</span><span class="sxs-lookup"><span data-stu-id="56fbb-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="56fbb-217">如果你使用的是沉浸式耳机，则必须连接并断开控制器的连接。</span><span class="sxs-lookup"><span data-stu-id="56fbb-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="56fbb-218">此反馈在沉浸式设备上变得不太感兴趣，因为连接的控制器始终为 "可用"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="56fbb-219">第2章-导航</span><span class="sxs-lookup"><span data-stu-id="56fbb-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="56fbb-220">目标</span><span class="sxs-lookup"><span data-stu-id="56fbb-220">Objectives</span></span>

* <span data-ttu-id="56fbb-221">使用导航手势事件来轮换 astronaut。</span><span class="sxs-lookup"><span data-stu-id="56fbb-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="56fbb-222">说明</span><span class="sxs-lookup"><span data-stu-id="56fbb-222">Instructions</span></span>

<span data-ttu-id="56fbb-223">若要在应用中使用导航笔势，我们将在导航手势发生时编辑 **GestureAction** 来旋转对象。</span><span class="sxs-lookup"><span data-stu-id="56fbb-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="56fbb-224">此外，我们还会将反馈添加到要在导航可用时显示的光标。</span><span class="sxs-lookup"><span data-stu-id="56fbb-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="56fbb-225">在 " **层次结构** " 面板中，展开 " **CursorWithFeedback**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="56fbb-226">在 **全息影像** 文件夹中，找到 " **ScrollFeedback** 资产"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="56fbb-227">将 **ScrollFeedback** prefab 拖放到 **层次结构** 中的 **CursorWithFeedback** GameObject。</span><span class="sxs-lookup"><span data-stu-id="56fbb-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="56fbb-228">单击 **CursorWithFeedback**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="56fbb-229">在 **检查器** 面板中，单击 " **添加组件** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="56fbb-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="56fbb-230">在菜单中，在 "搜索" 框中键入 **CursorFeedback**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="56fbb-231">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="56fbb-231">Select the search result.</span></span>
7. <span data-ttu-id="56fbb-232">将 **ScrollFeedback** 对象从 **层次结构** 中拖放到 **检查器** 的 **光标反馈** 组件中的 "**滚动检测到的游戏对象**" 属性上。</span><span class="sxs-lookup"><span data-stu-id="56fbb-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="56fbb-233">在 " **层次结构** " 面板中，选择 " **AstroMan** " 对象。</span><span class="sxs-lookup"><span data-stu-id="56fbb-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="56fbb-234">在 **检查器** 面板中，单击 " **添加组件** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="56fbb-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="56fbb-235">在菜单中，键入 "搜索框 **手势" 操作**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="56fbb-236">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="56fbb-236">Select the search result.</span></span>

<span data-ttu-id="56fbb-237">接下来，在 Visual Studio 中打开 **GestureAction** 。</span><span class="sxs-lookup"><span data-stu-id="56fbb-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="56fbb-238">在编码练习 2. c 中，编辑脚本以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="56fbb-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="56fbb-239">只要执行导航手势，就会 **旋转 AstroMan** 对象。</span><span class="sxs-lookup"><span data-stu-id="56fbb-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="56fbb-240">计算 **rotationFactor** 以控制应用于对象的旋转量。</span><span class="sxs-lookup"><span data-stu-id="56fbb-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="56fbb-241">当用户向左或向右移动对象时，绕 y 轴 **旋转对象**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="56fbb-242">在脚本中完成编码演练 2. c，或将代码替换为以下已完成的解决方案：</span><span class="sxs-lookup"><span data-stu-id="56fbb-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="56fbb-243">你会注意到，其他导航事件已经填充了某些信息。</span><span class="sxs-lookup"><span data-stu-id="56fbb-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="56fbb-244">我们将 GameObject 推送到工具包的 InputSystem's 模式堆栈上，这样用户就无需在旋转开始后在 Astronaut 上保持焦点。</span><span class="sxs-lookup"><span data-stu-id="56fbb-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="56fbb-245">同样，在完成该笔势后，将从堆栈中弹出 GameObject。</span><span class="sxs-lookup"><span data-stu-id="56fbb-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="56fbb-246">生成和部署</span><span class="sxs-lookup"><span data-stu-id="56fbb-246">Build and Deploy</span></span>

1. <span data-ttu-id="56fbb-247">重新生成 Unity 中的应用程序，然后从 Visual Studio 生成并部署，以便在 HoloLens 中运行。</span><span class="sxs-lookup"><span data-stu-id="56fbb-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="56fbb-248">注视 astronaut，光标两侧应会出现两个箭头。</span><span class="sxs-lookup"><span data-stu-id="56fbb-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="56fbb-249">此新视觉对象指示 astronaut 可以旋转。</span><span class="sxs-lookup"><span data-stu-id="56fbb-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="56fbb-250">将手放在 (食指指向天空) ，以便将开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="56fbb-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="56fbb-251">若要旋转 astronaut，请将食指降低到挤压位置，然后向左或向右移动以触发 NavigationX 手势。</span><span class="sxs-lookup"><span data-stu-id="56fbb-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="56fbb-252">第三章-手写指南</span><span class="sxs-lookup"><span data-stu-id="56fbb-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="56fbb-253">目标</span><span class="sxs-lookup"><span data-stu-id="56fbb-253">Objectives</span></span>

* <span data-ttu-id="56fbb-254">使用 " **手动指南分数** " 有助于预测何时会丢失手动跟踪。</span><span class="sxs-lookup"><span data-stu-id="56fbb-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="56fbb-255">提供 **有关光标的反馈** ，以便在用户尝试观看相机边缘时显示。</span><span class="sxs-lookup"><span data-stu-id="56fbb-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="56fbb-256">说明</span><span class="sxs-lookup"><span data-stu-id="56fbb-256">Instructions</span></span>

1. <span data-ttu-id="56fbb-257">在 " **层次结构** " 面板中，选择 " **CursorWithFeedback** " 对象。</span><span class="sxs-lookup"><span data-stu-id="56fbb-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="56fbb-258">在 **检查器** 面板中，单击 " **添加组件** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="56fbb-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="56fbb-259">在菜单中，键入搜索框的 **指导**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="56fbb-260">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="56fbb-260">Select the search result.</span></span>
4. <span data-ttu-id="56fbb-261">在 " **项目** " **面板中** ，找到 " **HandGuidanceFeedback** 资产"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="56fbb-262">将 **HandGuidanceFeedback** 资产拖放到 "**检查器**" 面板中的 "**手写指南" 指示符** 属性上。</span><span class="sxs-lookup"><span data-stu-id="56fbb-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="56fbb-263">生成和部署</span><span class="sxs-lookup"><span data-stu-id="56fbb-263">Build and Deploy</span></span>

* <span data-ttu-id="56fbb-264">重新生成 Unity 中的应用程序，然后从 Visual Studio 生成并部署，以在 HoloLens 上体验应用。</span><span class="sxs-lookup"><span data-stu-id="56fbb-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="56fbb-265">将你的手转到视图中，并抬起你的索引手指进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="56fbb-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="56fbb-266">开始通过导航手势旋转 astronaut， (将您的索引手指和) 一起。</span><span class="sxs-lookup"><span data-stu-id="56fbb-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="56fbb-267">向左、向右、向上、向下移动。</span><span class="sxs-lookup"><span data-stu-id="56fbb-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="56fbb-268">当手接近该笔势帧的边缘时，光标旁边应会出现一个箭头，警告您将丢失手动跟踪。</span><span class="sxs-lookup"><span data-stu-id="56fbb-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="56fbb-269">箭头指示移动哪一方向，以防丢失跟踪。</span><span class="sxs-lookup"><span data-stu-id="56fbb-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="56fbb-270">第4章-操作</span><span class="sxs-lookup"><span data-stu-id="56fbb-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="56fbb-271">目标</span><span class="sxs-lookup"><span data-stu-id="56fbb-271">Objectives</span></span>

* <span data-ttu-id="56fbb-272">使用操作事件将 astronaut 移动到手中。</span><span class="sxs-lookup"><span data-stu-id="56fbb-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="56fbb-273">提供有关游标的反馈，以让用户知道何时可以使用操作。</span><span class="sxs-lookup"><span data-stu-id="56fbb-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="56fbb-274">说明</span><span class="sxs-lookup"><span data-stu-id="56fbb-274">Instructions</span></span>

<span data-ttu-id="56fbb-275">GestureManager 和 AstronautManager 将允许我们执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="56fbb-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="56fbb-276">使用 speech 关键字 "**Move Astronaut**" 启用 **操作** 手势，并使用 "**旋转 Astronaut**" 来禁用它们。</span><span class="sxs-lookup"><span data-stu-id="56fbb-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="56fbb-277">切换到响应 **操作笔势识别器**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="56fbb-278">现在就开始吧。</span><span class="sxs-lookup"><span data-stu-id="56fbb-278">Let's get started.</span></span>

1. <span data-ttu-id="56fbb-279">在 " **层次结构** " 面板中，创建一个新的空 GameObject。</span><span class="sxs-lookup"><span data-stu-id="56fbb-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="56fbb-280">将其命名为 "**AstronautManager**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="56fbb-281">在 **检查器** 面板中，单击 " **添加组件** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="56fbb-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="56fbb-282">在菜单中，在 "搜索" 框中键入 " **Astronaut Manager**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="56fbb-283">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="56fbb-283">Select the search result.</span></span>
4. <span data-ttu-id="56fbb-284">在 **检查器** 面板中，单击 " **添加组件** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="56fbb-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="56fbb-285">在菜单中，在 "搜索" 框中键入 " **语音输入源**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="56fbb-286">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="56fbb-286">Select the search result.</span></span>

<span data-ttu-id="56fbb-287">现在，我们将添加控制 astronaut 交互状态所需的语音命令。</span><span class="sxs-lookup"><span data-stu-id="56fbb-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="56fbb-288">展开 **检查器** 中的 "**关键字**" 部分。</span><span class="sxs-lookup"><span data-stu-id="56fbb-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="56fbb-289">单击右侧的， **+** 添加一个新关键字。</span><span class="sxs-lookup"><span data-stu-id="56fbb-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="56fbb-290">将关键字键入为 **Move Astronaut**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="56fbb-291">如果需要，可以随意添加密钥快捷方式。</span><span class="sxs-lookup"><span data-stu-id="56fbb-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="56fbb-292">单击右侧的， **+** 添加一个新关键字。</span><span class="sxs-lookup"><span data-stu-id="56fbb-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="56fbb-293">将关键字键入为 **轮换 Astronaut**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="56fbb-294">如果需要，可以随意添加密钥快捷方式。</span><span class="sxs-lookup"><span data-stu-id="56fbb-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="56fbb-295">可在 **GestureAction** 中的 **ISpeechHandler. OnSpeechKeywordRecognized** 处理程序中找到相应的处理程序代码。</span><span class="sxs-lookup"><span data-stu-id="56fbb-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![如何设置第4章的语音输入源](images/holograms211-speech.png)

<span data-ttu-id="56fbb-297">接下来，我们将在游标上设置操作反馈。</span><span class="sxs-lookup"><span data-stu-id="56fbb-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="56fbb-298">在 " **项目** " **面板中** ，找到 " **PathingFeedback** 资产"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="56fbb-299">将 **PathingFeedback** prefab 拖放到 **层次结构** 中的 **CursorWithFeedback** 对象上。</span><span class="sxs-lookup"><span data-stu-id="56fbb-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="56fbb-300">在 " **层次结构** " 面板中，单击 " **CursorWithFeedback**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="56fbb-301">将 **PathingFeedback** 对象从 **层次结构** 中拖放到 **检查器** 的 "**游标反馈**" 组件中的 "**检测到路径" 游戏对象** 属性上。</span><span class="sxs-lookup"><span data-stu-id="56fbb-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="56fbb-302">现在，我们需要将代码添加到 **GestureAction** ，以启用以下内容：</span><span class="sxs-lookup"><span data-stu-id="56fbb-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="56fbb-303">将代码添加到 **IManipulationHandler. OnManipulationUpdated** 函数，该函数将在检测到 **操作** 笔势时移动 astronaut。</span><span class="sxs-lookup"><span data-stu-id="56fbb-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="56fbb-304">计算 **移动向量** ，以根据手头位置确定应将 astronaut 移动到的位置。</span><span class="sxs-lookup"><span data-stu-id="56fbb-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="56fbb-305">**将 Astronaut 移动** 到新位置。</span><span class="sxs-lookup"><span data-stu-id="56fbb-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="56fbb-306">完成编码练习 4. 在 **GestureAction** 中，或使用下面的已完成解决方案：</span><span class="sxs-lookup"><span data-stu-id="56fbb-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="56fbb-307">生成和部署</span><span class="sxs-lookup"><span data-stu-id="56fbb-307">Build and Deploy</span></span>

* <span data-ttu-id="56fbb-308">在 Unity 中重新生成，然后在 Visual Studio 中生成并部署，以在 HoloLens 中运行该应用。</span><span class="sxs-lookup"><span data-stu-id="56fbb-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="56fbb-309">将你的手移到 HoloLens 前面，并抬起你的食指，以便能够进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="56fbb-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="56fbb-310">将光标放在 astronaut 上。</span><span class="sxs-lookup"><span data-stu-id="56fbb-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="56fbb-311">说 "Move Astronaut" 将 Astronaut 与操作手势一起移动。</span><span class="sxs-lookup"><span data-stu-id="56fbb-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="56fbb-312">光标两侧应出现四个箭头，指示程序将立即响应操作事件。</span><span class="sxs-lookup"><span data-stu-id="56fbb-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="56fbb-313">将索引向下减小到拇指，并使其 pinched 在一起。</span><span class="sxs-lookup"><span data-stu-id="56fbb-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="56fbb-314">四处移动手时，astronaut 会 () 操作。</span><span class="sxs-lookup"><span data-stu-id="56fbb-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="56fbb-315">抬起索引手指，停止操作 astronaut。</span><span class="sxs-lookup"><span data-stu-id="56fbb-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="56fbb-316">注意：如果在移动手前未说 "移动 Astronaut"，则将改用导航手势。</span><span class="sxs-lookup"><span data-stu-id="56fbb-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="56fbb-317">说 "旋转 Astronaut" 返回到 rotatable 状态。</span><span class="sxs-lookup"><span data-stu-id="56fbb-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="56fbb-318">第5章-模型扩展</span><span class="sxs-lookup"><span data-stu-id="56fbb-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="56fbb-319">目标</span><span class="sxs-lookup"><span data-stu-id="56fbb-319">Objectives</span></span>

* <span data-ttu-id="56fbb-320">将 Astronaut 模型扩展为用户可与之交互的多个较小的部分。</span><span class="sxs-lookup"><span data-stu-id="56fbb-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="56fbb-321">使用导航和操作笔势分别移动各个部分。</span><span class="sxs-lookup"><span data-stu-id="56fbb-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="56fbb-322">说明</span><span class="sxs-lookup"><span data-stu-id="56fbb-322">Instructions</span></span>

<span data-ttu-id="56fbb-323">在本部分中，我们将完成下列任务：</span><span class="sxs-lookup"><span data-stu-id="56fbb-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="56fbb-324">添加新的关键字 "**展开模型**"，展开 astronaut 模型。</span><span class="sxs-lookup"><span data-stu-id="56fbb-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="56fbb-325">添加新的关键字 "**重置模型**"，以将模型返回到其原始形式。</span><span class="sxs-lookup"><span data-stu-id="56fbb-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="56fbb-326">为此，我们将向上一章的语音输入源添加另外两个关键字。</span><span class="sxs-lookup"><span data-stu-id="56fbb-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="56fbb-327">我们还将演示另一种处理识别事件的方法。</span><span class="sxs-lookup"><span data-stu-id="56fbb-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="56fbb-328">在 **检查器** 中单击 " **AstronautManager** "，然后展开 **检查器** 中的 "**关键字**" 部分。</span><span class="sxs-lookup"><span data-stu-id="56fbb-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="56fbb-329">单击右侧的， **+** 添加一个新关键字。</span><span class="sxs-lookup"><span data-stu-id="56fbb-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="56fbb-330">将关键字键入为 **展开 "模型**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="56fbb-331">如果需要，可以随意添加密钥快捷方式。</span><span class="sxs-lookup"><span data-stu-id="56fbb-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="56fbb-332">单击右侧的， **+** 添加一个新关键字。</span><span class="sxs-lookup"><span data-stu-id="56fbb-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="56fbb-333">将关键字键入为 " **重置模型**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="56fbb-334">如果需要，可以随意添加密钥快捷方式。</span><span class="sxs-lookup"><span data-stu-id="56fbb-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="56fbb-335">在 **检查器** 面板中，单击 " **添加组件** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="56fbb-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="56fbb-336">在菜单中，在 "搜索" 框中键入 **语音输入处理程序**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="56fbb-337">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="56fbb-337">Select the search result.</span></span>
8. <span data-ttu-id="56fbb-338">勾选 **是全局侦听器**，因为我们希望这些命令可以正常运行，而不考虑我们的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="56fbb-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="56fbb-339">单击 "" **+** 按钮，然后从 "关键字" 下拉列表中选择 " **展开模型** "。</span><span class="sxs-lookup"><span data-stu-id="56fbb-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="56fbb-340">单击 " **+** 响应" 下的 "AstronautManager"，并将 "  " 从 **层次结构** 拖到 "**无 (" 对象)** "字段。</span><span class="sxs-lookup"><span data-stu-id="56fbb-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="56fbb-341">现在，单击 " **无函数** " 下拉列表，选择 " **AstronautManager**"，然后选择 " **ExpandModelCommand**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="56fbb-342">单击 "语音输入处理程序" **+** 按钮，然后从 "关键字" 下拉列表中选择 " **重置模型** "。</span><span class="sxs-lookup"><span data-stu-id="56fbb-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="56fbb-343">单击 " **+** 响应" 下的 "AstronautManager"，并将 "  " 从 **层次结构** 拖到 "**无 (" 对象)** "字段。</span><span class="sxs-lookup"><span data-stu-id="56fbb-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="56fbb-344">现在，单击 " **无函数** " 下拉列表，选择 " **AstronautManager**"，然后选择 " **ResetModelCommand**"。</span><span class="sxs-lookup"><span data-stu-id="56fbb-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![如何设置第5章的语音输入源和处理程序](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="56fbb-346">生成和部署</span><span class="sxs-lookup"><span data-stu-id="56fbb-346">Build and Deploy</span></span>

* <span data-ttu-id="56fbb-347">试试看！</span><span class="sxs-lookup"><span data-stu-id="56fbb-347">Try it!</span></span> <span data-ttu-id="56fbb-348">生成应用并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="56fbb-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="56fbb-349">说 **展开 "模型** " 以查看扩展的 astronaut 模型。</span><span class="sxs-lookup"><span data-stu-id="56fbb-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="56fbb-350">使用 **导航** 旋转 astronaut 花色的各个部分。</span><span class="sxs-lookup"><span data-stu-id="56fbb-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="56fbb-351">假设 **移动 Astronaut** ，然后使用 **操作** 来移动 Astronaut 花色的各个部分。</span><span class="sxs-lookup"><span data-stu-id="56fbb-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="56fbb-352">说 **旋转 Astronaut** 再次旋转棋子。</span><span class="sxs-lookup"><span data-stu-id="56fbb-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="56fbb-353">假设 **Reset Model** 将 astronaut 返回到其原始形式。</span><span class="sxs-lookup"><span data-stu-id="56fbb-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="56fbb-354">结束</span><span class="sxs-lookup"><span data-stu-id="56fbb-354">The End</span></span>

<span data-ttu-id="56fbb-355">恭喜！</span><span class="sxs-lookup"><span data-stu-id="56fbb-355">Congratulations!</span></span> <span data-ttu-id="56fbb-356">你现在已经完成了 **MR 输入211：手势**。</span><span class="sxs-lookup"><span data-stu-id="56fbb-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="56fbb-357">你知道如何检测和响应手动跟踪、导航和操作事件。</span><span class="sxs-lookup"><span data-stu-id="56fbb-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="56fbb-358">了解导航和操作笔势之间的差异。</span><span class="sxs-lookup"><span data-stu-id="56fbb-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="56fbb-359">你知道如何更改光标以提供有关何时检测到手、即将丢失以及何时对象支持 (导航与操作) 的不同交互的视觉反馈。</span><span class="sxs-lookup"><span data-stu-id="56fbb-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>