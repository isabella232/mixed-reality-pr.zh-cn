---
title: Unity Visual Studio最佳做法
description: 使用 Unity 和 Visual Studio 简化创建混合现实应用程序的工作流的提示和Visual Studio。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: deploy， unity， visual Studio， HoloLens， HoloLens 2， 沉浸式头戴显示设备， 最佳做法， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， UWP， Visual Studio Tools， Windows SDK
ms.openlocfilehash: edd79b95d02cfeb1da4effc485fc57078e3d24a3
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042258"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="a50d3-104">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="a50d3-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="a50d3-105">使用 Unity 创建混合现实应用程序时，需要切换 Unity 和 Visual Studio，以生成应用包并部署到 HoloLens 或沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="a50d3-105">When you're creating a mixed reality application with Unity, you need to switch between Unity and Visual Studio to build and deploy the app package to HoloLens or an immersive headset.</span></span> <span data-ttu-id="a50d3-106">默认情况下，需要两个 Visual Studio实例 - 一个实例用于修改 Unity 脚本，另一个实例用于部署到设备和调试。</span><span class="sxs-lookup"><span data-stu-id="a50d3-106">By default, two instances of Visual Studio are required - one instance to modify Unity scripts and another to deploy to the device and debug.</span></span> <span data-ttu-id="a50d3-107">以下说明允许使用单个 Visual Studio 实例进行开发，从而减少导出 Unity 项目的频率并改进调试体验。</span><span class="sxs-lookup"><span data-stu-id="a50d3-107">The following instructions let you develop using a single Visual Studio instance, reducing the frequency of exporting Unity projects and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="a50d3-108">改善迭代时间</span><span class="sxs-lookup"><span data-stu-id="a50d3-108">Improving iteration time</span></span>

<span data-ttu-id="a50d3-109">Unity 中对 .NET 脚本后端的支持在 Unity 2018 中已弃用，从 Unity 2019+ 开始已删除，因此建议切换到 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。</span><span class="sxs-lookup"><span data-stu-id="a50d3-109">Support for .NET scripting back-end in Unity was deprecated in Unity 2018 and removed as of Unity 2019+, so we recommend you switch to [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html).</span></span> <span data-ttu-id="a50d3-110">但是，从 Unity 到 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a50d3-110">However, you may experience longer build times from Unity to Visual Studio.</span></span> <span data-ttu-id="a50d3-111">若要提高迭代速度，请设置环境以获得最佳编译结果：</span><span class="sxs-lookup"><span data-stu-id="a50d3-111">To improve for faster iteration, set up your environment for best compilation results:</span></span>

1) <span data-ttu-id="a50d3-112">使用增量生成，每次将项目生成到同一目录，并在那里重新使用预生成文件</span><span class="sxs-lookup"><span data-stu-id="a50d3-112">Use incremental building by building your project to the same directory every time, reusing the pre-built files there</span></span>
2) <span data-ttu-id="a50d3-113">在生成文件夹中禁用项目的反恶意软件&扫描</span><span class="sxs-lookup"><span data-stu-id="a50d3-113">Disable anti-malware software scans for your project & build folders</span></span>
   - <span data-ttu-id="a50d3-114">在 **& 设置应用下打开** "病毒Windows 10威胁防护"</span><span class="sxs-lookup"><span data-stu-id="a50d3-114">Open **Virus & threat protection** under your Windows 10 settings app</span></span>
   - <span data-ttu-id="a50d3-115">在 **"病毒和\*\*\*\*威胁&下选择"管理设置"**</span><span class="sxs-lookup"><span data-stu-id="a50d3-115">Select **Manage Settings** under **Virus & threat protection settings**</span></span>
   - <span data-ttu-id="a50d3-116">在 **"排除项"部分下选择** " **添加或删除排除** 项"</span><span class="sxs-lookup"><span data-stu-id="a50d3-116">Select **Add or remove exclusions** under the **Exclusions** section</span></span>
   - <span data-ttu-id="a50d3-117">选择 **"添加排除** 项"，然后选择包含 Unity 项目代码和生成输出的文件夹</span><span class="sxs-lookup"><span data-stu-id="a50d3-117">Select **Add an exclusion** and select the folder containing your Unity project code and build outputs</span></span>
3) <span data-ttu-id="a50d3-118">使用 SSD 进行生成</span><span class="sxs-lookup"><span data-stu-id="a50d3-118">Use an SSD for building</span></span>

<span data-ttu-id="a50d3-119">有关详细信息 [，请查看优化 IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 的生成时间。</span><span class="sxs-lookup"><span data-stu-id="a50d3-119">Review [Optimizing Build Times for IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) for more info.</span></span> <span data-ttu-id="a50d3-120">另请查看 [IL2CPP 脚本后端 上的调试](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)。</span><span class="sxs-lookup"><span data-stu-id="a50d3-120">Also, review [Debugging on IL2CPP Scripting Back-end](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).</span></span>

<span data-ttu-id="a50d3-121">请考虑安装 [*UnityScriptAnalyzer Visual Studio* 扩展](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)。</span><span class="sxs-lookup"><span data-stu-id="a50d3-121">Consider installing the [*UnityScriptAnalyzer* Visual Studio extension](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer).</span></span> <span data-ttu-id="a50d3-122">此工具分析 Unity C# 脚本，了解以更优化的方式编写的代码。</span><span class="sxs-lookup"><span data-stu-id="a50d3-122">This tool analyzes your Unity C# scripts for code that can be written in a more optimized manner.</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="a50d3-123">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="a50d3-123">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="a50d3-124">下载 [Visual Studio Tools for Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span><span class="sxs-lookup"><span data-stu-id="a50d3-124">Download [Visual Studio Tools for Unity](/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span></span>

<span data-ttu-id="a50d3-125">**服务Visual Studio Tools for Unity**</span><span class="sxs-lookup"><span data-stu-id="a50d3-125">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="a50d3-126">通过放置断点、计算变量和复杂表达式Visual Studio调试编辑器中 Unity 播放模式。</span><span class="sxs-lookup"><span data-stu-id="a50d3-126">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="a50d3-127">使用 Unity 项目资源管理器查找与 Unity 显示的层次结构完全相同的脚本。</span><span class="sxs-lookup"><span data-stu-id="a50d3-127">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="a50d3-128">直接在控制台内部获取 Unity Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a50d3-128">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="a50d3-129">使用向导快速创建或导航到脚本。</span><span class="sxs-lookup"><span data-stu-id="a50d3-129">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="a50d3-130">公开 C# 类变量以轻松优化</span><span class="sxs-lookup"><span data-stu-id="a50d3-130">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="a50d3-131">有两种方法可以公开类变量。</span><span class="sxs-lookup"><span data-stu-id="a50d3-131">There are two ways to expose class variables.</span></span> <span data-ttu-id="a50d3-132">建议的方式是向专用变量添加 [SerializeField] 属性。</span><span class="sxs-lookup"><span data-stu-id="a50d3-132">The recommended way is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="a50d3-133">序列化字段可以从编辑器访问，但不能以编程方式公开。</span><span class="sxs-lookup"><span data-stu-id="a50d3-133">Serialized fields can be accessed from the editor but not programmatically exposed.</span></span>  <span data-ttu-id="a50d3-134">另一个选项是使 C# 类变量成为公共变量，以在编辑器 UI 中公开它们。</span><span class="sxs-lookup"><span data-stu-id="a50d3-134">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="a50d3-135">这两种方法都使得在编辑器中播放时可以轻松调整变量，这一点对于优化交互选项属性特别有用。</span><span class="sxs-lookup"><span data-stu-id="a50d3-135">Both approaches make it possible to easily tweak variables while playing in-editor, which is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="a50d3-136">升级或 Unity Visual Studio后重新生成 UWP Windows SDK解决方案</span><span class="sxs-lookup"><span data-stu-id="a50d3-136">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="a50d3-137">升级到Visual Studio或 Unity 引擎后，签入到源代码管理中的 UWP Windows SDK可能过期。</span><span class="sxs-lookup"><span data-stu-id="a50d3-137">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="a50d3-138">可以通过从 Unity 生成新的 UWP 解决方案，将差异合并到签入解决方案中，解决过期的解决方案。</span><span class="sxs-lookup"><span data-stu-id="a50d3-138">You can resolve out-of-date solutions after by building a new UWP solution from Unity and merging differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="a50d3-139">使用文本格式资产轻松比较内容更改</span><span class="sxs-lookup"><span data-stu-id="a50d3-139">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="a50d3-140">通过以文本格式存储资产，可以更轻松地查看文本格式中的内容Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a50d3-140">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="a50d3-141">可以通过在"编辑器"中选择"编辑项目设置>，将资产>模式更改为"强制文本 **"，** 以文本格式 **存储资产**。</span><span class="sxs-lookup"><span data-stu-id="a50d3-141">You can store assets in text format by selecting **Edit > Project Settings > Editor** and change **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="a50d3-142">但是，合并文本资产文件更改容易出错，不建议这样做，因此请考虑在源代码管理中启用独占二进制签出。</span><span class="sxs-lookup"><span data-stu-id="a50d3-142">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control.</span></span>

## <a name="see-also"></a><span data-ttu-id="a50d3-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a50d3-143">See also</span></span>
- [<span data-ttu-id="a50d3-144">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="a50d3-144">Visual Studio Tools for Unity</span></span>](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [<span data-ttu-id="a50d3-145">优化 IL2CPP 的生成时间</span><span class="sxs-lookup"><span data-stu-id="a50d3-145">Optimizing Build Times for IL2CPP</span></span>](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [<span data-ttu-id="a50d3-146">*UnityScriptAnalyzer* Visual Studio扩展</span><span class="sxs-lookup"><span data-stu-id="a50d3-146">*UnityScriptAnalyzer* Visual Studio extension</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)