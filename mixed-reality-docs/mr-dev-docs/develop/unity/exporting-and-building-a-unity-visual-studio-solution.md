---
title: 导出和构建 Unity Visual Studio 解决方案
description: 本文概述如何从 Unity 导出混合现实项目，以便可以在 Visual Studio 中生成和部署。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity，visual studio，导出，生成，部署，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，UWP，部署
ms.openlocfilehash: 4da20a30375c7204c532a19c129c9265c0fa27d9
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010408"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a><span data-ttu-id="7544b-104">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="7544b-104">Exporting and building a Unity Visual Studio solution</span></span>

<span data-ttu-id="7544b-105">如果你的应用程序不需要系统键盘，我们建议使用 *D3D* ，使你的应用程序使用略微少的内存和更快的启动时间。</span><span class="sxs-lookup"><span data-stu-id="7544b-105">If your app doesn't need the system keyboard, our recommendation is to use *D3D* so that your app uses slightly less memory and a faster launch time.</span></span> <span data-ttu-id="7544b-106">但是，如果通过 TouchScreenKeyboard API 使用系统键盘，则需要将项目导出为 *XAML*。</span><span class="sxs-lookup"><span data-stu-id="7544b-106">However, if you're using the system keyboard through the TouchScreenKeyboard API, you need to export the project as *XAML*.</span></span>

## <a name="how-to-export-from-unity"></a><span data-ttu-id="7544b-107">如何从 Unity 导出</span><span class="sxs-lookup"><span data-stu-id="7544b-107">How to export from Unity</span></span>

<span data-ttu-id="7544b-108">![Unity 生成设置](images/unitybuildsettings-300px.png)</span><span class="sxs-lookup"><span data-stu-id="7544b-108">![Unity build settings](images/unitybuildsettings-300px.png)</span></span><br>
<span data-ttu-id="7544b-109">*Unity 编辑器中的生成设置*</span><span class="sxs-lookup"><span data-stu-id="7544b-109">*Build settings in Unity editor*</span></span>

1. <span data-ttu-id="7544b-110">如果已准备好从 Unity 导出项目，请打开 "**文件**" 菜单，然后选择 "**生成设置 ...** "</span><span class="sxs-lookup"><span data-stu-id="7544b-110">When you're ready to export your project from Unity, open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="7544b-111">选择 " **添加打开的场景** "，将场景添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="7544b-111">Select **Add Open Scenes** to add your scene to the build.</span></span>
3. <span data-ttu-id="7544b-112">在 " **生成设置** " 对话框中，选择以下要为 HoloLens 导出的选项：</span><span class="sxs-lookup"><span data-stu-id="7544b-112">In the **Build Settings** dialog, choose the following options to export for HoloLens:</span></span>
   * <span data-ttu-id="7544b-113">**平台：** *通用 Windows 平台* ，并确保选择 " **切换平台** " 以使选择生效。</span><span class="sxs-lookup"><span data-stu-id="7544b-113">**Platform:** *Universal Windows Platform* and be sure to select **Switch Platform** for your selection to take effect.</span></span>
   * <span data-ttu-id="7544b-114">**SDK：** *通用 10*。</span><span class="sxs-lookup"><span data-stu-id="7544b-114">**SDK:** *Universal 10*.</span></span>
   * <span data-ttu-id="7544b-115">**UWP 生成类型：** *D3D*。</span><span class="sxs-lookup"><span data-stu-id="7544b-115">**UWP Build Type:** *D3D*.</span></span>
4. <span data-ttu-id="7544b-116">**可选**： **Unity c # 项目：** 已选中。</span><span class="sxs-lookup"><span data-stu-id="7544b-116">**Optional**: **Unity C# Projects:** Checked.</span></span>

>[!NOTE]
><span data-ttu-id="7544b-117">选中此框后，您可以：</span><span class="sxs-lookup"><span data-stu-id="7544b-117">Checking this box allows you to:</span></span>
>* <span data-ttu-id="7544b-118">在 Visual Studio 远程调试器中调试你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="7544b-118">Debug your app in the Visual Studio remote debugger.</span></span>
>* <span data-ttu-id="7544b-119">使用 IntelliSense for WinRT Api 时在 Unity c # 项目中编辑脚本。</span><span class="sxs-lookup"><span data-stu-id="7544b-119">Edit scripts in the Unity C# project while using IntelliSense for WinRT APIs.</span></span>

5. <span data-ttu-id="7544b-120">从 "**生成设置 ...** " 窗口中，打开 "**播放机设置 ...** "</span><span class="sxs-lookup"><span data-stu-id="7544b-120">From the **Build Settings...** window, open **Player Settings...**</span></span>
6. <span data-ttu-id="7544b-121">选择通用 Windows 平台 "选项卡的" **设置** "。</span><span class="sxs-lookup"><span data-stu-id="7544b-121">Select the **Settings for Universal Windows Platform** tab.</span></span>
7. <span data-ttu-id="7544b-122">展开“XR 设置”组。</span><span class="sxs-lookup"><span data-stu-id="7544b-122">Expand the **XR Settings** group.</span></span>
8. <span data-ttu-id="7544b-123">在 " **XR 设置** " 部分中，选中 " **受支持的虚拟现实** " 复选框，以添加新的 **虚拟现实设备** 列表，并确认 **"Windows Mixed Reality"** 列为受支持的设备。</span><span class="sxs-lookup"><span data-stu-id="7544b-123">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list and confirm **"Windows Mixed Reality"** is listed as a supported device.</span></span>
9. <span data-ttu-id="7544b-124">返回到 " **生成设置** " 对话框。</span><span class="sxs-lookup"><span data-stu-id="7544b-124">Return to the **Build Settings** dialog.</span></span>
10. <span data-ttu-id="7544b-125">选择“生成”  。</span><span class="sxs-lookup"><span data-stu-id="7544b-125">Select **Build**.</span></span>
11. <span data-ttu-id="7544b-126">在出现的 "Windows 资源管理器" 对话框中，创建一个新文件夹来保存 Unity 的生成输出。</span><span class="sxs-lookup"><span data-stu-id="7544b-126">In the Windows Explorer dialog that appears, create a new folder to hold Unity's build output.</span></span> <span data-ttu-id="7544b-127">通常，将文件夹命名为 "App"。</span><span class="sxs-lookup"><span data-stu-id="7544b-127">Generally, we name the folder "App".</span></span>
12. <span data-ttu-id="7544b-128">选择新创建的文件夹，然后选择 " **选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="7544b-128">Select the newly created folder and select **Select Folder**.</span></span>
13. <span data-ttu-id="7544b-129">Unity 完成生成后，将打开项目根目录的 Windows 资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="7544b-129">Once Unity has finished building, a Windows Explorer window will open to the project root directory.</span></span> <span data-ttu-id="7544b-130">导航到新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7544b-130">Navigate into the newly created folder.</span></span>
14. <span data-ttu-id="7544b-131">打开位于此文件夹中的生成的 Visual Studio 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="7544b-131">Open the generated Visual Studio solution file located inside this folder.</span></span>

## <a name="when-to-re-export-from-unity"></a><span data-ttu-id="7544b-132">何时从 Unity 重新导出</span><span class="sxs-lookup"><span data-stu-id="7544b-132">When to re-export from Unity</span></span>

<span data-ttu-id="7544b-133">在从 Unity 导出应用程序时，选中 " **c # 项目** " 复选框会创建一个包含所有 Unity 脚本文件的 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="7544b-133">Checking the **C# Projects** checkbox when exporting your app from Unity creates a Visual Studio solution that includes all your Unity script files.</span></span> <span data-ttu-id="7544b-134">让所有脚本都位于同一位置，无需从 Unity 重新导出即可进行迭代。</span><span class="sxs-lookup"><span data-stu-id="7544b-134">Having all your scripts in one place lets you iterate without re-exporting from Unity.</span></span> <span data-ttu-id="7544b-135">但是，如果对不只是更改脚本内容的项目进行更改，则需要从 Unity 重新导出。</span><span class="sxs-lookup"><span data-stu-id="7544b-135">However, if you make changes to your project that aren't just changing the contents of scripts, you'll need to re-export from Unity.</span></span> <span data-ttu-id="7544b-136">需要从 Unity 重新导出的一些时间示例如下：</span><span class="sxs-lookup"><span data-stu-id="7544b-136">Some examples of times you need to re-export from Unity are:</span></span>
* <span data-ttu-id="7544b-137">您可以在 "项目" 选项卡中添加或删除资产。</span><span class="sxs-lookup"><span data-stu-id="7544b-137">You add or remove assets in the Project tab.</span></span>
* <span data-ttu-id="7544b-138">您可以在 "检查器" 选项卡中更改任何值。</span><span class="sxs-lookup"><span data-stu-id="7544b-138">You change any value in the Inspector tab.</span></span>
* <span data-ttu-id="7544b-139">您可以在 "层次结构" 选项卡中添加或删除对象。</span><span class="sxs-lookup"><span data-stu-id="7544b-139">You add or remove objects from the Hierarchy tab.</span></span>
* <span data-ttu-id="7544b-140">更改任何 Unity 项目设置</span><span class="sxs-lookup"><span data-stu-id="7544b-140">You change any Unity project settings</span></span>

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a><span data-ttu-id="7544b-141">生成和部署 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="7544b-141">Building and deploying a Unity Visual Studio solution</span></span>

<span data-ttu-id="7544b-142">在 [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md)中生成和部署应用程序的其余部分。</span><span class="sxs-lookup"><span data-stu-id="7544b-142">The remainder of building and deploying apps happens in [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md).</span></span> <span data-ttu-id="7544b-143">你将需要指定 Unity 生成配置。</span><span class="sxs-lookup"><span data-stu-id="7544b-143">You will need to specify a Unity build configuration.</span></span> <span data-ttu-id="7544b-144">Unity 的命名约定可能不同于你在 Visual Studio 中所用的内容：</span><span class="sxs-lookup"><span data-stu-id="7544b-144">Unity's naming conventions may differ from what you're used to in Visual Studio:</span></span>

|  <span data-ttu-id="7544b-145">配置</span><span class="sxs-lookup"><span data-stu-id="7544b-145">Configuration</span></span>  |  <span data-ttu-id="7544b-146">说明</span><span class="sxs-lookup"><span data-stu-id="7544b-146">Explanation</span></span> | 
|----------|----------|
|  <span data-ttu-id="7544b-147">调试</span><span class="sxs-lookup"><span data-stu-id="7544b-147">Debug</span></span>  |  <span data-ttu-id="7544b-148">禁用所有优化，并启用探查器。</span><span class="sxs-lookup"><span data-stu-id="7544b-148">All optimizations off and the profiler is enabled.</span></span> <span data-ttu-id="7544b-149">用于调试脚本。</span><span class="sxs-lookup"><span data-stu-id="7544b-149">Used to debug scripts.</span></span> | 
|  <span data-ttu-id="7544b-150">Master</span><span class="sxs-lookup"><span data-stu-id="7544b-150">Master</span></span>  |  <span data-ttu-id="7544b-151">启用所有优化并禁用探查器。</span><span class="sxs-lookup"><span data-stu-id="7544b-151">All optimizations are turned on and the profiler is disabled.</span></span> <span data-ttu-id="7544b-152">用于将应用提交到应用商店。</span><span class="sxs-lookup"><span data-stu-id="7544b-152">Used to submit apps to the Store.</span></span> | 
|  <span data-ttu-id="7544b-153">发布</span><span class="sxs-lookup"><span data-stu-id="7544b-153">Release</span></span>  |  <span data-ttu-id="7544b-154">启用所有优化，并启用探查器。</span><span class="sxs-lookup"><span data-stu-id="7544b-154">All optimizations are turned on and the profiler is enabled.</span></span> <span data-ttu-id="7544b-155">用于评估应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="7544b-155">Used to evaluate app performance.</span></span> | 

<span data-ttu-id="7544b-156">请注意，上面的列表是常见触发器的一个子集，将导致需要生成 Visual Studio 项目。</span><span class="sxs-lookup"><span data-stu-id="7544b-156">Note, the above list is a subset of the common triggers that will cause the Visual Studio project to need to be generated.</span></span> <span data-ttu-id="7544b-157">通常，在 Visual Studio 中编辑 .cs 文件不需要从 Unity 内重新生成项目。</span><span class="sxs-lookup"><span data-stu-id="7544b-157">In general, editing .cs files from within Visual Studio won't require the project to be regenerated from within Unity.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="7544b-158">疑难解答</span><span class="sxs-lookup"><span data-stu-id="7544b-158">Troubleshooting</span></span>

<span data-ttu-id="7544b-159">如果你发现在你的 Visual Studio 项目中无法识别对 .cs 文件的编辑，请确保在从 Unity 的 "生成" 菜单生成 VS 项目时检查 **Unity c # 项目** 。</span><span class="sxs-lookup"><span data-stu-id="7544b-159">If you find that edits to your .cs files aren't being recognized in your Visual Studio project, ensure that **Unity C# Projects** is checked when you generate the VS project from Unity's Build menu.</span></span>
