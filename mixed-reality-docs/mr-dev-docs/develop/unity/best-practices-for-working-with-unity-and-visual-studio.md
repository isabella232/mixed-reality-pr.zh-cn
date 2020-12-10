---
title: 使用 Unity 和 Visual Studio 的最佳做法
description: 用于简化使用 Unity 和 Visual Studio 创建混合现实应用程序的工作流的提示和技巧。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 部署，unity，visual studio，HoloLens，HoloLens 2，沉浸式耳机，最佳实践，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，UWP，Visual Studio Tools，Windows SDK
ms.openlocfilehash: 9e80cad3e7154ae5548514297343db8efcdcb49e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010258"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="11905-104">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="11905-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="11905-105">使用 Unity 创建混合现实应用程序时，需要在 Unity 和 Visual Studio 之间切换，以生成应用包并将其部署到 HoloLens 或沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="11905-105">When you're creating a mixed reality application with Unity, you need to switch between Unity and Visual Studio to build and deploy the app package to HoloLens or an immersive headset.</span></span> <span data-ttu-id="11905-106">默认情况下，需要 Visual Studio 的两个实例-一个实例用于修改 Unity 脚本，另一个实例用于部署到设备并进行调试。</span><span class="sxs-lookup"><span data-stu-id="11905-106">By default, two instances of Visual Studio are required - one instance to modify Unity scripts and another to deploy to the device and debug.</span></span> <span data-ttu-id="11905-107">以下说明允许使用单个 Visual Studio 实例进行开发，从而降低导出 Unity 项目的频率并改善调试体验。</span><span class="sxs-lookup"><span data-stu-id="11905-107">The following instructions let you develop using a single Visual Studio instance, reducing the frequency of exporting Unity projects and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="11905-108">提高迭代时间</span><span class="sxs-lookup"><span data-stu-id="11905-108">Improving iteration time</span></span>

<span data-ttu-id="11905-109">Unity 中的 .NET 脚本编写后端支持在 Unity 2018 中被弃用，并且在 Unity 2019 + 中被删除。</span><span class="sxs-lookup"><span data-stu-id="11905-109">Support for .NET scripting back-end in Unity is being deprecated in Unity 2018 and removed in Unity 2019+.</span></span> <span data-ttu-id="11905-110">因此，建议切换到 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。</span><span class="sxs-lookup"><span data-stu-id="11905-110">so we recommend you switch to [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html).</span></span> <span data-ttu-id="11905-111">但是，从 Unity 到 Visual Studio 的生成时间可能会更长。</span><span class="sxs-lookup"><span data-stu-id="11905-111">However, you may experience longer build times from Unity to Visual Studio.</span></span> <span data-ttu-id="11905-112">若要提高迭代速度，请设置你的环境以获得最佳的编译结果：</span><span class="sxs-lookup"><span data-stu-id="11905-112">To improve for faster iteration, set up your environment for best compilation results:</span></span>

1) <span data-ttu-id="11905-113">使用增量生成，每次将项目生成到同一个目录，并在此处重复使用预先生成的文件</span><span class="sxs-lookup"><span data-stu-id="11905-113">Use incremental building by building your project to the same directory every time, reusing the pre-built files there</span></span>
2) <span data-ttu-id="11905-114">禁用项目 & 生成文件夹的反恶意软件扫描</span><span class="sxs-lookup"><span data-stu-id="11905-114">Disable anti-malware software scans for your project & build folders</span></span>
   - <span data-ttu-id="11905-115">在 Windows 10 设置应用下打开 **病毒 & 威胁防护**</span><span class="sxs-lookup"><span data-stu-id="11905-115">Open **Virus & threat protection** under your Windows 10 settings app</span></span>
   - <span data-ttu-id="11905-116">选择 "安全 **& 威胁防护设置**" 下的 "**管理设置**"</span><span class="sxs-lookup"><span data-stu-id="11905-116">Select **Manage Settings** under **Virus & threat protection settings**</span></span>
   - <span data-ttu-id="11905-117">选择 "**排除**" 部分下的 "**添加或删除排除** 项"</span><span class="sxs-lookup"><span data-stu-id="11905-117">Select **Add or remove exclusions** under the **Exclusions** section</span></span>
   - <span data-ttu-id="11905-118">选择 " **添加排除** "，然后选择包含 Unity 项目代码和生成输出的文件夹</span><span class="sxs-lookup"><span data-stu-id="11905-118">Select **Add an exclusion** and select the folder containing your Unity project code and build outputs</span></span>
3) <span data-ttu-id="11905-119">使用 SSD 进行生成</span><span class="sxs-lookup"><span data-stu-id="11905-119">Use an SSD for building</span></span>

<span data-ttu-id="11905-120">有关详细信息，请参阅 [优化 IL2CPP 的生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 。</span><span class="sxs-lookup"><span data-stu-id="11905-120">Review [Optimizing Build Times for IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) for more info.</span></span> <span data-ttu-id="11905-121">此外，请查看 [IL2CPP 脚本编写后端的调试](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)。</span><span class="sxs-lookup"><span data-stu-id="11905-121">Also, review [Debugging on IL2CPP Scripting Back-end](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).</span></span>

<span data-ttu-id="11905-122">请考虑安装 [ *UnityScriptAnalyzer* Visual Studio 扩展](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)。</span><span class="sxs-lookup"><span data-stu-id="11905-122">Consider installing the [*UnityScriptAnalyzer* Visual Studio extension](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer).</span></span> <span data-ttu-id="11905-123">此工具分析你的 Unity c # 脚本，以了解可以通过更优化的方式编写的代码。</span><span class="sxs-lookup"><span data-stu-id="11905-123">This tool analyzes your Unity C# scripts for code that can be written in a more optimized manner.</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="11905-124">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="11905-124">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="11905-125">下载 [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span><span class="sxs-lookup"><span data-stu-id="11905-125">Download [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity)</span></span>

<span data-ttu-id="11905-126">**Visual Studio Tools for Unity 的优点**</span><span class="sxs-lookup"><span data-stu-id="11905-126">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="11905-127">通过放置断点、计算变量和复杂表达式，从 Visual Studio 调试 Unity 编辑器播放模式。</span><span class="sxs-lookup"><span data-stu-id="11905-127">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="11905-128">使用 Unity 项目资源管理器查找脚本，该脚本具有 Unity 显示的完全相同的层次结构。</span><span class="sxs-lookup"><span data-stu-id="11905-128">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="11905-129">直接在 Visual Studio 中获取 Unity 控制台。</span><span class="sxs-lookup"><span data-stu-id="11905-129">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="11905-130">使用向导快速创建或导航到脚本。</span><span class="sxs-lookup"><span data-stu-id="11905-130">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="11905-131">公开 c # 类变量以便轻松优化</span><span class="sxs-lookup"><span data-stu-id="11905-131">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="11905-132">可以通过两种方式公开类变量。</span><span class="sxs-lookup"><span data-stu-id="11905-132">There are two ways to expose class variables.</span></span> <span data-ttu-id="11905-133">建议将 [SerializeField] 特性添加到专用变量。</span><span class="sxs-lookup"><span data-stu-id="11905-133">The recommended way is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="11905-134">序列化的字段可以从编辑器访问，但不能以编程方式公开。</span><span class="sxs-lookup"><span data-stu-id="11905-134">Serialized fields can be accessed from the editor but not programmatically exposed.</span></span>  <span data-ttu-id="11905-135">另一种方法是将 c # 类变量公开为在编辑器 UI 中公开它们。</span><span class="sxs-lookup"><span data-stu-id="11905-135">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="11905-136">利用这两种方法，可以在编辑器中播放时轻松地调整变量，这对于优化交互 mechanic 属性特别有用。</span><span class="sxs-lookup"><span data-stu-id="11905-136">Both approaches make it possible to easily tweak variables while playing in-editor, which is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="11905-137">Windows SDK 或 Unity 升级后重新生成 UWP Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="11905-137">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="11905-138">签入到源代码管理中的 UWP Visual Studio 解决方案可以在升级到新的 Windows SDK 或 Unity 引擎之后过期。</span><span class="sxs-lookup"><span data-stu-id="11905-138">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="11905-139">通过从 Unity 生成新的 UWP 解决方案并将差异合并到签入的解决方案中，可以在以后解决过时的解决方案。</span><span class="sxs-lookup"><span data-stu-id="11905-139">You can resolve out-of-date solutions after by building a new UWP solution from Unity and merging differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="11905-140">使用文本格式资产以便于比较内容更改</span><span class="sxs-lookup"><span data-stu-id="11905-140">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="11905-141">以文本格式存储资产使你可以更轻松地在 Visual Studio 中查看内容更改差异。</span><span class="sxs-lookup"><span data-stu-id="11905-141">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="11905-142">可以通过选择 " **编辑 > 项目设置" > 编辑器** ，并更改 **资产序列化** 模式来 **强制文本**，以文本格式存储资产。</span><span class="sxs-lookup"><span data-stu-id="11905-142">You can store assets in text format by selecting **Edit > Project Settings > Editor** and change **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="11905-143">但是，合并文本资产文件更改很容易出错，不建议这样做，因此请考虑在源代码管理中启用独占二进制文件签出。</span><span class="sxs-lookup"><span data-stu-id="11905-143">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control.</span></span>

## <a name="see-also"></a><span data-ttu-id="11905-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11905-144">See also</span></span>
- [<span data-ttu-id="11905-145">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="11905-145">Visual Studio Tools for Unity</span></span>](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [<span data-ttu-id="11905-146">优化 IL2CPP 的生成时间</span><span class="sxs-lookup"><span data-stu-id="11905-146">Optimizing Build Times for IL2CPP</span></span>](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [<span data-ttu-id="11905-147">*UnityScriptAnalyzer* Visual Studio 扩展</span><span class="sxs-lookup"><span data-stu-id="11905-147">*UnityScriptAnalyzer* Visual Studio extension</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
