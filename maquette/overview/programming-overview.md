---
title: 编程概述
description: 了解如何使用脚本访问 Maquette 对象和接口。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality，Maquette，原型设计，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935351"
---
# <a name="programming-overview"></a><span data-ttu-id="bd1a4-104">编程概述</span><span class="sxs-lookup"><span data-stu-id="bd1a4-104">Programming overview</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->

![徽标](../images/MaquetteIcon.png) <span data-ttu-id="bd1a4-106">编程概述</span><span class="sxs-lookup"><span data-stu-id="bd1a4-106">Programming Overview</span></span>

<span data-ttu-id="bd1a4-107">Microsoft Maquette 使用 JavaScript (ECMAScript 5.1，其中包含基于 [Jint](https://github.com/sebastienros/jint) 解释器的扩展) 。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-107">Microsoft Maquette uses JavaScript (ECMAScript 5.1 with extensions) based on the [Jint](https://github.com/sebastienros/jint) interpreter.</span></span> <span data-ttu-id="bd1a4-108">此扩展 `.mqjs` 用于将 Maquette javascript 文件与普通 javascript 区分开来。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-108">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
<span data-ttu-id="bd1a4-109">Maquette 对象和接口可通过对象访问和编写脚本 `Maquette` 。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-109">Maquette objects and interfaces are accessible and scriptable via the `Maquette` Object.</span></span> <span data-ttu-id="bd1a4-110">Maquette 的 API 参考中提供了有关 Maquette 对象和接口的文档。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-110">Documentation on Maquette Objects and interfaces are provided in Maquette's API Reference.</span></span>

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
<span data-ttu-id="bd1a4-111">MaquetteScript 是新的添加项，在 flux 中，因此需要进行更改。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-111">MaquetteScript is a new addition and in flux so changes should be expected.</span></span> <span data-ttu-id="bd1a4-112">即将推出更详细的文档和更新。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-112">More detailed documentation and updates available soon.</span></span>

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a><span data-ttu-id="bd1a4-113">关于脚本编写</span><span class="sxs-lookup"><span data-stu-id="bd1a4-113">Spotlights on Scripting</span></span>

* <span data-ttu-id="bd1a4-114">待定-聚焦为示例/教程的脚本</span><span class="sxs-lookup"><span data-stu-id="bd1a4-114">TBD - Scripting Spotlights focused as Samples/Tutorials</span></span>
  * <span data-ttu-id="bd1a4-115">2x 图像/标题–链接到聚焦页</span><span class="sxs-lookup"><span data-stu-id="bd1a4-115">2x Images/Caption – link to spotlight page</span></span>

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a><span data-ttu-id="bd1a4-116">MaquetteScript 入门</span><span class="sxs-lookup"><span data-stu-id="bd1a4-116">Getting started with MaquetteScript</span></span>

* <span data-ttu-id="bd1a4-117">Mqjs 与 .JS</span><span class="sxs-lookup"><span data-stu-id="bd1a4-117">Mqjs vs. JS</span></span>
* <span data-ttu-id="bd1a4-118">编程模型</span><span class="sxs-lookup"><span data-stu-id="bd1a4-118">Programming Model</span></span>
  * <span data-ttu-id="bd1a4-119">编辑与运行</span><span class="sxs-lookup"><span data-stu-id="bd1a4-119">Editing vs. Running</span></span>
* <span data-ttu-id="bd1a4-120">指向编程工作流的链接</span><span class="sxs-lookup"><span data-stu-id="bd1a4-120">Link to Programming Workflow</span></span>
* <span data-ttu-id="bd1a4-121">链接到共享结果</span><span class="sxs-lookup"><span data-stu-id="bd1a4-121">Link to Sharing Results</span></span>

## <a name="programming-workflow"></a><span data-ttu-id="bd1a4-122">编程工作流</span><span class="sxs-lookup"><span data-stu-id="bd1a4-122">Programming workflow</span></span>

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
<span data-ttu-id="bd1a4-123">TBD</span><span class="sxs-lookup"><span data-stu-id="bd1a4-123">TBD</span></span>
* <span data-ttu-id="bd1a4-124">REPL</span><span class="sxs-lookup"><span data-stu-id="bd1a4-124">REPL</span></span>
* <span data-ttu-id="bd1a4-125">脚本操作</span><span class="sxs-lookup"><span data-stu-id="bd1a4-125">Scripting operation</span></span>
* <span data-ttu-id="bd1a4-126">调试器操作</span><span class="sxs-lookup"><span data-stu-id="bd1a4-126">Debugger operation</span></span>
* <span data-ttu-id="bd1a4-127">调试循环</span><span class="sxs-lookup"><span data-stu-id="bd1a4-127">Debugging loop</span></span>
* <span data-ttu-id="bd1a4-128">复制/粘贴代码？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-128">Copy/Paste of code?</span></span>

## <a name="running-mqjs-scripts"></a><span data-ttu-id="bd1a4-129">正在运行 mqjs 脚本</span><span class="sxs-lookup"><span data-stu-id="bd1a4-129">Running .mqjs scripts</span></span>

<!-- TODO(Stefan): Need screenshot -->
<span data-ttu-id="bd1a4-130">若要运行 MaquetteScript 文件，请使用 Maquette 的随附窗口，并打开 "脚本" 选项卡来查找脚本。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-130">To run a MaquetteScript .mqjs file, go to the companion windows of Maquette and open the scripting tab to locate scripts.</span></span>

> [!NOTE] 
> <span data-ttu-id="bd1a4-131">某些选项将不起作用，因为我们尚未提供这些脚本。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-131">Some options will not work yet because we have not ship the scripts.</span></span>

## <a name="vscode-editor-workflow"></a><span data-ttu-id="bd1a4-132">VSCode 编辑器工作流</span><span class="sxs-lookup"><span data-stu-id="bd1a4-132">VSCode Editor Workflow</span></span>

<span data-ttu-id="bd1a4-133">若要从 VSCode 中评估 Maquette 中的脚本，用户需要知道两个命令：</span><span class="sxs-lookup"><span data-stu-id="bd1a4-133">To evaluate script in Maquette from within VSCode, the user needs to know two commands:</span></span>

   <span data-ttu-id="bd1a4-134">`CTRL-5` 计算光标所在的选定文本或整行。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-134">`CTRL-5` evaluates the selected text or the entire line where the cursor is located.</span></span> 

   <span data-ttu-id="bd1a4-135">`CTRL-SHIFT-5` 计算整个文件。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-135">`CTRL-SHIFT-5` evaluates the entire file.</span></span>

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
<span data-ttu-id="bd1a4-136">文本将发送到 Maquette，在 JavaScript 环境中计算，并将结果发送回 VSCode 的输出控制台。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-136">Text is sent to Maquette, evaluated in the JavaScript environment, and the result is sent back to the output console of VSCode.</span></span> <span data-ttu-id="bd1a4-137">这可用作复制 (读取-eval-) 。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-137">This can be used as a REPL (read-eval-print-loop).</span></span>

## <a name="example-first-step"></a><span data-ttu-id="bd1a4-138">示例第一步</span><span class="sxs-lookup"><span data-stu-id="bd1a4-138">Example First Step</span></span>

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
<span data-ttu-id="bd1a4-139">将以下代码复制到 VSCode 中的文件：</span><span class="sxs-lookup"><span data-stu-id="bd1a4-139">Copy the following code into a file in VSCode:</span></span>

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
<span data-ttu-id="bd1a4-140">选择代码或部分内容，然后单击 " `CTRL-5` 执行"。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-140">Select the code or just sections and hit `CTRL-5` to execute.</span></span> <span data-ttu-id="bd1a4-141">这会创建一个多维数据集，将其放置在您的上方，并更改其颜色。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-141">This should create a cube, place it in front of you and change its color.</span></span>

<span data-ttu-id="bd1a4-142">还可以通过扩展查找更多示例。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-142">There are more examples to find through the extension.</span></span>

## <a name="sharing-results"></a><span data-ttu-id="bd1a4-143">共享结果</span><span class="sxs-lookup"><span data-stu-id="bd1a4-143">Sharing Results</span></span>

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
<span data-ttu-id="bd1a4-144">如何在用户/团队之间共享</span><span class="sxs-lookup"><span data-stu-id="bd1a4-144">How to share between users/teams</span></span>
* <span data-ttu-id="bd1a4-145">文档目录中的 Zip 项目</span><span class="sxs-lookup"><span data-stu-id="bd1a4-145">Zip project in documents directory</span></span>
* <span data-ttu-id="bd1a4-146">将项目复制到文件共享</span><span class="sxs-lookup"><span data-stu-id="bd1a4-146">Copy project to file share</span></span>
* <span data-ttu-id="bd1a4-147">将团队共享提交的文件位置添加到 Maquette 团队</span><span class="sxs-lookup"><span data-stu-id="bd1a4-147">Adding file location of team share Submissions to Maquette Team</span></span>

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
<span data-ttu-id="bd1a4-148">TBD</span><span class="sxs-lookup"><span data-stu-id="bd1a4-148">TBD</span></span>
* <span data-ttu-id="bd1a4-149">包括，在其他位置引用相对/绝对路径的代码，模块</span><span class="sxs-lookup"><span data-stu-id="bd1a4-149">Includes, reference to code elsewhere with relative/absolute paths, modules</span></span>
* <span data-ttu-id="bd1a4-150">库?</span><span class="sxs-lookup"><span data-stu-id="bd1a4-150">Libraries?</span></span>
* <span data-ttu-id="bd1a4-151">运行时支持</span><span class="sxs-lookup"><span data-stu-id="bd1a4-151">Runtime support</span></span>
* <span data-ttu-id="bd1a4-152">未解析的外部-当条目丢失/崩溃时的行为</span><span class="sxs-lookup"><span data-stu-id="bd1a4-152">Unresolved Externals - Behavior when entries missing/crashing</span></span>
* <span data-ttu-id="bd1a4-153">能否添加/编辑/观察与特定对象关联的脚本？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-153">Can we add/edit/observe script associated with specific objects?</span></span>
  * <span data-ttu-id="bd1a4-154">我们可以将此脚本复制/粘贴到其他位置吗？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-154">Can we copy/paste this script elsewhere?</span></span>
  * <span data-ttu-id="bd1a4-155">什么是对象属性？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-155">What about object properties?</span></span>
  * <span data-ttu-id="bd1a4-156">在我的场景中命名对象？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-156">Naming objects in my scene?</span></span> <span data-ttu-id="bd1a4-157">)  (重命名脚本</span><span class="sxs-lookup"><span data-stu-id="bd1a4-157">(renaming script with it)</span></span>
  * <span data-ttu-id="bd1a4-158">与对象关联的脚本的此关键字或自关键字</span><span class="sxs-lookup"><span data-stu-id="bd1a4-158">THIS or SELF keyword for script associated with an object</span></span>
  * <span data-ttu-id="bd1a4-159">如果我右键单击某个对象，则可以查看与其关联的代码 (及其所有层次结构) </span><span class="sxs-lookup"><span data-stu-id="bd1a4-159">If I right click on an object, can I see code associated with it (and all it's hierarchy)</span></span>
  * <span data-ttu-id="bd1a4-160">能否在 UI 中进行选择，并在 VSCode 中将其置于代码中？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-160">Can I select in UI and be brought up at the code in VSCode?</span></span>
  * <span data-ttu-id="bd1a4-161">正在脚本源文件中将与对象 "一起" 关联的代码保留在一起？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-161">Keeping code associated with an object "together" in the script source file?</span></span>
  * <span data-ttu-id="bd1a4-162">在单击对象时将其置于对象上？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-162">Bring property window up of an object when I click on it?</span></span> <span data-ttu-id="bd1a4-163">在 VR 和主选项卡中？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-163">In VR and in main tab?</span></span>
* <span data-ttu-id="bd1a4-164">安全问题</span><span class="sxs-lookup"><span data-stu-id="bd1a4-164">Security Issues</span></span>
* <span data-ttu-id="bd1a4-165">测试–可能是待定，但我们可以通过脚本推荐视频或帧捕获</span><span class="sxs-lookup"><span data-stu-id="bd1a4-165">Testing – might be TBD but we could suggest video or frame grab by script</span></span>
* <span data-ttu-id="bd1a4-166">如果有 bug 报告机制，我们可能会通过脚本为其他 (？ ) .。。然后</span><span class="sxs-lookup"><span data-stu-id="bd1a4-166">If we have a bug reporting mechanism, we might make that accessible via script for others (?) …later</span></span>
* <span data-ttu-id="bd1a4-167">部署-如何 "共享" 结果，包为 EXE</span><span class="sxs-lookup"><span data-stu-id="bd1a4-167">Deployment – how to “share” the result, package as EXE</span></span>
* <span data-ttu-id="bd1a4-168">运行/控制演示或 spectating/监视</span><span class="sxs-lookup"><span data-stu-id="bd1a4-168">Running/controlling a demo or spectating/monitoring</span></span>
* <span data-ttu-id="bd1a4-169">播放机模式</span><span class="sxs-lookup"><span data-stu-id="bd1a4-169">Player mode</span></span>
* <span data-ttu-id="bd1a4-170">我们可能会提供有关如何使 "组件" 共享的段？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-170">We might have a segment on how to make “components” for sharing?</span></span> <span data-ttu-id="bd1a4-171"> (可能是 tbd) </span><span class="sxs-lookup"><span data-stu-id="bd1a4-171">(might  be tbd)</span></span>
  * <span data-ttu-id="bd1a4-172">#Include 吗？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-172">Is there #include?</span></span> <span data-ttu-id="bd1a4-173">这将处理纯 JS I 假设，但可能存在命名空间冲突。</span><span class="sxs-lookup"><span data-stu-id="bd1a4-173">This handles pure JS I suppose but may have namespace conflicts.</span></span>
  * <span data-ttu-id="bd1a4-174">对于 maquette 要合并某个其他 maquette 和命名对象以匹配 JS 代码，是否可以执行任何操作？</span><span class="sxs-lookup"><span data-stu-id="bd1a4-174">Is there anything we could do for a maquette to incorporate some other maquette with named objects to match JS code?</span></span>
