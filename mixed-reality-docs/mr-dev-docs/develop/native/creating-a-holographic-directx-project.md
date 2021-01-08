---
title: 创建全息 DirectX 项目
description: 了解如何创建新的基于 Windows Mixed Reality 应用模板的全息版 DirectX 应用。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality，全息应用，新应用，UWP 应用，模板应用，全息影像，新建项目，演练，下载，示例代码，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 9259a85512555342877de0a5a8bae697fdd03b8d
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006867"
---
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="4dc90-104">创建全息 DirectX 项目</span><span class="sxs-lookup"><span data-stu-id="4dc90-104">Creating a holographic DirectX project</span></span>

> [!NOTE]
> <span data-ttu-id="4dc90-105">本文与旧版 WinRT 本机 Api 相关。</span><span class="sxs-lookup"><span data-stu-id="4dc90-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="4dc90-106">对于新的本机应用项目，建议使用 **[OPENXR API](openxr-getting-started.md)**。</span><span class="sxs-lookup"><span data-stu-id="4dc90-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="4dc90-107">为 HoloLens 创建的全息版应用将是 <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平台 (UWP) 应用</a>。</span><span class="sxs-lookup"><span data-stu-id="4dc90-107">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="4dc90-108">如果面向桌面 Windows Mixed Reality 耳机，则可以创建 UWP 应用或 Win32 应用。</span><span class="sxs-lookup"><span data-stu-id="4dc90-108">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="4dc90-109">DirectX 11 全息 UWP 应用模板非常类似于 DirectX 11 UWP 应用模板。</span><span class="sxs-lookup"><span data-stu-id="4dc90-109">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template.</span></span> <span data-ttu-id="4dc90-110">该模板包括一个程序循环、一个用于管理 Direct3D 设备和上下文的 **DeviceResources** 类和一个简化的内容呈现器类。</span><span class="sxs-lookup"><span data-stu-id="4dc90-110">The template includes a program loop, a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="4dc90-111">它还有 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>，就像其他任何 UWP 应用一样。</span><span class="sxs-lookup"><span data-stu-id="4dc90-111">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="4dc90-112">然而，混合现实应用有一些其他功能，这些功能在典型的 Direct3D UWP 应用中不存在。</span><span class="sxs-lookup"><span data-stu-id="4dc90-112">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D UWP app.</span></span> <span data-ttu-id="4dc90-113">Windows Mixed Reality 应用模板可以：</span><span class="sxs-lookup"><span data-stu-id="4dc90-113">The Windows Mixed Reality app template can:</span></span>
* <span data-ttu-id="4dc90-114">处理与全息相机关联的 Direct3D 设备资源。</span><span class="sxs-lookup"><span data-stu-id="4dc90-114">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="4dc90-115">从系统检索相机后台缓冲区。</span><span class="sxs-lookup"><span data-stu-id="4dc90-115">Retrieve camera back buffers from the system.</span></span> <span data-ttu-id="4dc90-116">对于 Direct3D12，创建全息后台缓冲区资源并管理资源生存期。</span><span class="sxs-lookup"><span data-stu-id="4dc90-116">In the case of Direct3D12, create holographic back buffer resources and manage resource lifetimes.</span></span>
* <span data-ttu-id="4dc90-117">处理 [注视](../../design/gaze-and-commit.md) 的输入，并识别 [手势](../../design/gaze-and-commit.md#composite-gestures)。</span><span class="sxs-lookup"><span data-stu-id="4dc90-117">Handle [gaze](../../design/gaze-and-commit.md) input, and recognize a [gesture](../../design/gaze-and-commit.md#composite-gestures).</span></span>
* <span data-ttu-id="4dc90-118">进入全屏立体声呈现模式。</span><span class="sxs-lookup"><span data-stu-id="4dc90-118">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="4dc90-119">如何入门？</span><span class="sxs-lookup"><span data-stu-id="4dc90-119">How do I get started?</span></span>

<span data-ttu-id="4dc90-120">按照下载 Visual Studio 2019 和 Windows Mixed Reality 应用模板中的说明，首先 [安装这些工具](../install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc90-120">First [install the tools](../install-the-tools.md), following the instructions on downloading Visual Studio 2019 and the Windows Mixed Reality app templates.</span></span> <span data-ttu-id="4dc90-121">混合现实应用模板在 Visual Studio marketplace 上可作为 [web 下载](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)，或通过 VISUAL studio UI 安装为扩展。</span><span class="sxs-lookup"><span data-stu-id="4dc90-121">The mixed reality app templates are available on the Visual Studio marketplace as a [web download](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX), or by installing them as an extension through the Visual Studio UI.</span></span>

<span data-ttu-id="4dc90-122">现在，你已准备好创建 DirectX 11 Windows Mixed Reality 应用！</span><span class="sxs-lookup"><span data-stu-id="4dc90-122">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="4dc90-123">请注意，若要删除示例内容，请在 *pch* 中注释掉 **DRAW_SAMPLE_CONTENT** 预处理器指令。</span><span class="sxs-lookup"><span data-stu-id="4dc90-123">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="4dc90-124">创建 UWP 项目</span><span class="sxs-lookup"><span data-stu-id="4dc90-124">Creating a UWP project</span></span>

<span data-ttu-id="4dc90-125">安装工具后，] (。/install-the-tools.md) 你可以创建一个全息的 DirectX UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="4dc90-125">Once the tools are installed,](../install-the-tools.md) you can then create a holographic DirectX UWP project.</span></span>

<span data-ttu-id="4dc90-126">在 Visual Studio 2019 中创建新项目：</span><span class="sxs-lookup"><span data-stu-id="4dc90-126">To create a new project in Visual Studio 2019:</span></span>
1. <span data-ttu-id="4dc90-127">启动 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="4dc90-127">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="4dc90-128">在右侧的 " **入门** " 部分中，选择 " **创建新项目**"。</span><span class="sxs-lookup"><span data-stu-id="4dc90-128">In the **Get Started** section on the right, select **Create a new project**.</span></span>
3. <span data-ttu-id="4dc90-129">在 " **创建新项目** " 对话框的下拉菜单中，选择 " **c + +**"、" **Windows Mixed Reality**" 和 " **UWP**"。</span><span class="sxs-lookup"><span data-stu-id="4dc90-129">In the drop-down menus in the **Create a new project** dialog, select **C++**, **Windows Mixed Reality**, and **UWP**.</span></span>
4. <span data-ttu-id="4dc90-130">**(通用 Windows)  (c + +/WinRT) 中选择 "全息 DirectX 11 应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="4dc90-130">Select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="4dc90-131">![Visual Studio 2019 中全息版 DirectX 11 c + +/WinRT UWP 应用项目模板的屏幕截图](images/holographic-directx-app-cpp-new-project-2019.png)</span><span class="sxs-lookup"><span data-stu-id="4dc90-131">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)</span></span><br>
   <span data-ttu-id="4dc90-132">*Visual Studio 2019 中的全息 DirectX 11 c + +/WinRT UWP 应用项目模板*</span><span class="sxs-lookup"><span data-stu-id="4dc90-132">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio 2019*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="4dc90-133">请确保项目模板的名称包含 " (c + +/WinRT) "。</span><span class="sxs-lookup"><span data-stu-id="4dc90-133">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="4dc90-134">如果没有，则已安装全息版项目模板。</span><span class="sxs-lookup"><span data-stu-id="4dc90-134">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="4dc90-135">若要获取最新的项目模板，请将 [其安装](../install-the-tools.md) 为 Visual Studio 2019 的扩展。</span><span class="sxs-lookup"><span data-stu-id="4dc90-135">To get the latest project templates, [install them](../install-the-tools.md) as an extension to Visual Studio 2019.</span></span>
5. <span data-ttu-id="4dc90-136">选择“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="4dc90-136">Select **Next**.</span></span>
5. <span data-ttu-id="4dc90-137">填写 " **项目名称** " 和 " **位置** " 文本框，然后选择或点击 " **创建**"。</span><span class="sxs-lookup"><span data-stu-id="4dc90-137">Fill in the **Project name** and **Location** text boxes, and select or tap **Create**.</span></span> <span data-ttu-id="4dc90-138">创建全息应用项目。</span><span class="sxs-lookup"><span data-stu-id="4dc90-138">The holographic app project is created.</span></span>
6. <span data-ttu-id="4dc90-139">对于仅面向 HoloLens 2 的开发，请确保将 **目标版本** 和 **最低版本** 设置为 **Windows 10，版本 1903**。</span><span class="sxs-lookup"><span data-stu-id="4dc90-139">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="4dc90-140">如果你还面向 HoloLens (第一代) 或桌面 Windows Mixed Reality 耳机，则可以将 **最低版本** 设置为 **Windows 10，版本 1809**。</span><span class="sxs-lookup"><span data-stu-id="4dc90-140">If you're also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809**.</span></span> <span data-ttu-id="4dc90-141">使用 HoloLens 2 的新功能时，这将要求在代码中进行某种 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本自适应检查</a> 。</span><span class="sxs-lookup"><span data-stu-id="4dc90-141">This will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="4dc90-142">![将 Windows 10 （版本1903）设置为目标和最小版本的屏幕截图](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="4dc90-142">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="4dc90-143">*将 **Windows 10 （版本1903）** 设置为目标和最低版本*</span><span class="sxs-lookup"><span data-stu-id="4dc90-143">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="4dc90-144">如果看不到 **windows 10 （版本 1903** ）作为选项，则不会安装最新的 WINDOWS 10 SDK。</span><span class="sxs-lookup"><span data-stu-id="4dc90-144">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="4dc90-145">若要使此选项显示，请 <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安装10.0.18362.0 或更高版本的 Windows 10 SDK</a>。</span><span class="sxs-lookup"><span data-stu-id="4dc90-145">To get this option to appear, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="4dc90-146">在 Visual Studio 2017 中创建新项目：</span><span class="sxs-lookup"><span data-stu-id="4dc90-146">To create a new project in Visual Studio 2017:</span></span>
1. <span data-ttu-id="4dc90-147">启动 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="4dc90-147">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="4dc90-148">在 " **文件** " 菜单上，指向 " **新建** "，然后从上下文菜单中选择 " **项目** "。</span><span class="sxs-lookup"><span data-stu-id="4dc90-148">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="4dc90-149">此时会打开“新建项目”对话框。 </span><span class="sxs-lookup"><span data-stu-id="4dc90-149">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="4dc90-150">展开左侧的 " **已安装** "，然后展开 " **Visual C++** 语言" 节点。</span><span class="sxs-lookup"><span data-stu-id="4dc90-150">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="4dc90-151">导航到 " **Windows 通用 > 全息** 节点"，然后选择 " **)  (c + +/WinRT)  (通用 Windows 的全息 DirectX 11 应用**。</span><span class="sxs-lookup"><span data-stu-id="4dc90-151">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="4dc90-152">![Visual Studio 2017 中全息版 DirectX 11 c + +/WinRT UWP 应用项目模板的屏幕截图](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="4dc90-152">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
   <span data-ttu-id="4dc90-153">*Visual Studio 2017 中的全息 DirectX 11 c + +/WinRT UWP 应用项目模板*</span><span class="sxs-lookup"><span data-stu-id="4dc90-153">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio 2017*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="4dc90-154">请确保项目模板的名称包含 " (c + +/WinRT) "。</span><span class="sxs-lookup"><span data-stu-id="4dc90-154">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="4dc90-155">如果没有，则已安装全息版项目模板。</span><span class="sxs-lookup"><span data-stu-id="4dc90-155">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="4dc90-156">若要获取最新的项目模板，请将 [其安装](../install-the-tools.md) 为 Visual Studio 2017 的扩展。</span><span class="sxs-lookup"><span data-stu-id="4dc90-156">To get the latest project templates, [install them](../install-the-tools.md) as an extension to Visual Studio 2017.</span></span>
5. <span data-ttu-id="4dc90-157">填写 " **名称** " 和 " **位置** " 文本框，然后选择或点击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="4dc90-157">Fill in the **Name** and **Location** text boxes, and select or tap **OK**.</span></span> <span data-ttu-id="4dc90-158">创建全息应用项目。</span><span class="sxs-lookup"><span data-stu-id="4dc90-158">The holographic app project is created.</span></span>
6. <span data-ttu-id="4dc90-159">对于仅面向 HoloLens 2 的开发，请确保将 **目标版本** 和 **最低版本** 设置为 **Windows 10，版本 1903**。</span><span class="sxs-lookup"><span data-stu-id="4dc90-159">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="4dc90-160">如果你还面向 HoloLens (第一代) 或桌面 Windows Mixed Reality 耳机，则可以将 **最低版本** 设置为 **Windows 10，版本 1809**。</span><span class="sxs-lookup"><span data-stu-id="4dc90-160">If you're also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809**.</span></span> <span data-ttu-id="4dc90-161">使用 HoloLens 2 的新功能时，这将要求在代码中进行某种 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本自适应检查</a> 。</span><span class="sxs-lookup"><span data-stu-id="4dc90-161">This will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="4dc90-162">![将 Windows 10 （版本1903）设置为目标和最小版本的屏幕截图](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="4dc90-162">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="4dc90-163">*将 **Windows 10 （版本1903）** 设置为目标和最低版本*</span><span class="sxs-lookup"><span data-stu-id="4dc90-163">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="4dc90-164">如果看不到 **windows 10 （版本 1903** ）作为选项，则不会安装最新的 WINDOWS 10 SDK。</span><span class="sxs-lookup"><span data-stu-id="4dc90-164">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="4dc90-165">若要使此选项显示，请 <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安装10.0.18362.0 或更高版本的 Windows 10 SDK</a>。</span><span class="sxs-lookup"><span data-stu-id="4dc90-165">To get this option to appear, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="4dc90-166">该模板将使用 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">c + +/WinRT</a>（一种 c + + 17 语言 Windows 运行时 api）生成项目，该项目支持任何符合标准的 c + + 17 编译器。</span><span class="sxs-lookup"><span data-stu-id="4dc90-166">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="4dc90-167">该项目演示了如何创建一个世界上锁定的多维数据集，该多维数据集是用户的2米。</span><span class="sxs-lookup"><span data-stu-id="4dc90-167">The project shows how to create a world-locked cube that's placed 2 meters from the user.</span></span> <span data-ttu-id="4dc90-168">用户 [可以按](../../design/gaze-and-commit.md#composite-gestures) 下或按下控制器上的按钮，将多维数据集置于用户 [注视](../../design/gaze-and-commit.md)指定的不同位置。</span><span class="sxs-lookup"><span data-stu-id="4dc90-168">The user can [air-tap](../../design/gaze-and-commit.md#composite-gestures) or press a button on the controller to place the cube in a different position specified by the user's [gaze](../../design/gaze-and-commit.md).</span></span> <span data-ttu-id="4dc90-169">可以修改此项目来创建任何混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="4dc90-169">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="4dc90-170">你还可以使用 **Visual c #** 全息项目模板创建一个新项目，该模板基于 SharpDX。</span><span class="sxs-lookup"><span data-stu-id="4dc90-170">You can also create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="4dc90-171">如果你的全息 c # 项目不是从 Windows 全息应用程序模板开始，则需要从 Windows Mixed Reality c # 模板项目复制 fxcompile 文件并将其导入到 .csproj 文件中，以便编译添加到项目中的 HLSL 文件。</span><span class="sxs-lookup"><span data-stu-id="4dc90-171">If your holographic C# project didn't start from the Windows Holographic app template, you'll need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your.csproj file to compile HLSL files that you add to your project.</span></span> <span data-ttu-id="4dc90-172">在 Visual Studio 的 Windows Mixed Reality 应用程序模板扩展中还提供了 Direct3D 12 模板。</span><span class="sxs-lookup"><span data-stu-id="4dc90-172">A Direct3D 12 template is also provided in the Windows Mixed Reality app templates extension to Visual Studio.</span></span>

<span data-ttu-id="4dc90-173">请参阅 [使用 Visual Studio 进行部署和调试](../platform-capabilities-and-apis/using-visual-studio.md) ，获取有关如何生成和部署该示例并将其部署到 HoloLens、附加了沉浸式设备的 PC 或仿真程序的信息。</span><span class="sxs-lookup"><span data-stu-id="4dc90-173">Review [Using Visual Studio to deploy and debug](../platform-capabilities-and-apis/using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="4dc90-174">下面的说明将假设你使用 c + + 生成应用。</span><span class="sxs-lookup"><span data-stu-id="4dc90-174">The rest of the instructions below will assume that you're using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="4dc90-175">UWP 应用入口点</span><span class="sxs-lookup"><span data-stu-id="4dc90-175">UWP app entry point</span></span>

<span data-ttu-id="4dc90-176">全息 UWP 应用在 AppView 的 **wWinMain** 函数中启动。</span><span class="sxs-lookup"><span data-stu-id="4dc90-176">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="4dc90-177">**WWinMain** 函数创建应用的 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> ，并通过它启动 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 。</span><span class="sxs-lookup"><span data-stu-id="4dc90-177">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="4dc90-178">从 **AppView**：</span><span class="sxs-lookup"><span data-stu-id="4dc90-178">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="4dc90-179">从现在开始，AppView 类处理与 Windows 基本输入事件、CoreWindow 事件和消息等的交互。</span><span class="sxs-lookup"><span data-stu-id="4dc90-179">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="4dc90-180">它还将创建应用使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="4dc90-180">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="4dc90-181">创建 Win32 项目</span><span class="sxs-lookup"><span data-stu-id="4dc90-181">Creating a Win32 project</span></span>

<span data-ttu-id="4dc90-182">开始构建 Win32 全息项目的最简单方法是修改 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 示例</a>。</span><span class="sxs-lookup"><span data-stu-id="4dc90-182">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="4dc90-183">此 Win32 示例使用 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">c + +/WinRT</a>，它是支持任何符合标准的 c + + 17 编译器的 Windows 运行时 Api 的 c + + 17 语言投影。</span><span class="sxs-lookup"><span data-stu-id="4dc90-183">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="4dc90-184">该项目演示了如何创建一个世界上锁定的多维数据集，该多维数据集是用户的2米。</span><span class="sxs-lookup"><span data-stu-id="4dc90-184">The project shows how to create a world-locked cube that's placed 2 meters from the user.</span></span> <span data-ttu-id="4dc90-185">用户可以按控制器上的按钮，将多维数据集置于用户 [注视](../../design/gaze-and-commit.md)指定的不同位置。</span><span class="sxs-lookup"><span data-stu-id="4dc90-185">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](../../design/gaze-and-commit.md).</span></span> <span data-ttu-id="4dc90-186">可以修改此项目来创建任何混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="4dc90-186">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="4dc90-187">Win32 应用程序入口点</span><span class="sxs-lookup"><span data-stu-id="4dc90-187">Win32 app entry point</span></span>

<span data-ttu-id="4dc90-188">全息 Win32 应用程序在 AppMain 的 **wWinMain** 函数中启动。</span><span class="sxs-lookup"><span data-stu-id="4dc90-188">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="4dc90-189">**WWinMain** 函数创建应用的 HWND 并启动其消息循环。</span><span class="sxs-lookup"><span data-stu-id="4dc90-189">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="4dc90-190">从 **AppMain**：</span><span class="sxs-lookup"><span data-stu-id="4dc90-190">From **AppMain.cpp**:</span></span>

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

<span data-ttu-id="4dc90-191">从现在开始，AppMain 类处理与基本窗口消息的交互，等等。</span><span class="sxs-lookup"><span data-stu-id="4dc90-191">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="4dc90-192">它还将创建应用使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="4dc90-192">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="4dc90-193">呈现全息内容</span><span class="sxs-lookup"><span data-stu-id="4dc90-193">Render holographic content</span></span>

<span data-ttu-id="4dc90-194">项目的 " **内容** " 文件夹包含用于渲染 [全息空间](getting-a-holographicspace.md)中全息影像的类。</span><span class="sxs-lookup"><span data-stu-id="4dc90-194">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="4dc90-195">模板中的默认全息图是远离用户的旋转多维数据集。</span><span class="sxs-lookup"><span data-stu-id="4dc90-195">The default hologram in the template is a spinning cube that's placed 2 meters away from the user.</span></span> <span data-ttu-id="4dc90-196">绘制此多维数据集是在 **SpinningCubeRenderer** 中实现的，该方法具有以下关键方法：</span><span class="sxs-lookup"><span data-stu-id="4dc90-196">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="4dc90-197">方法</span><span class="sxs-lookup"><span data-stu-id="4dc90-197">Method</span></span>  |  <span data-ttu-id="4dc90-198">说明</span><span class="sxs-lookup"><span data-stu-id="4dc90-198">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="4dc90-199">加载着色器并创建多维数据集网格。</span><span class="sxs-lookup"><span data-stu-id="4dc90-199">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="4dc90-200">将全息图置于所提供的 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>指定的位置。</span><span class="sxs-lookup"><span data-stu-id="4dc90-200">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="4dc90-201">旋转多维数据集，并设置模型矩阵。</span><span class="sxs-lookup"><span data-stu-id="4dc90-201">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="4dc90-202">使用顶点和像素着色器呈现一个帧。</span><span class="sxs-lookup"><span data-stu-id="4dc90-202">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="4dc90-203">**着色** 子文件夹包含四个默认着色器实现：</span><span class="sxs-lookup"><span data-stu-id="4dc90-203">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="4dc90-204">着色器</span><span class="sxs-lookup"><span data-stu-id="4dc90-204">Shader</span></span>  |  <span data-ttu-id="4dc90-205">说明</span><span class="sxs-lookup"><span data-stu-id="4dc90-205">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="4dc90-206">不修改几何图形的传递。</span><span class="sxs-lookup"><span data-stu-id="4dc90-206">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="4dc90-207">通过颜色数据。</span><span class="sxs-lookup"><span data-stu-id="4dc90-207">Passes through the color data.</span></span> <span data-ttu-id="4dc90-208">在光栅化步骤中，将颜色数据插值并分配给一个像素。</span><span class="sxs-lookup"><span data-stu-id="4dc90-208">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="4dc90-209">用于在 GPU 上执行顶点处理的简单着色器。</span><span class="sxs-lookup"><span data-stu-id="4dc90-209">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="4dc90-210">用于在 GPU 上执行顶点处理的简单着色器，针对 Windows Mixed Reality 立体声渲染进行了优化。</span><span class="sxs-lookup"><span data-stu-id="4dc90-210">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="4dc90-211">`VertexShaderShared.hlsl` 包含在和之间共享的通用代码 `VertexShader.hlsl` `VPRTVertexShader.hlsl` 。</span><span class="sxs-lookup"><span data-stu-id="4dc90-211">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="4dc90-212">注意： Direct3D 12 应用模板还包括 `ViewInstancingVertexShader.hlsl` 。</span><span class="sxs-lookup"><span data-stu-id="4dc90-212">Note: The Direct3D 12 app template also includes `ViewInstancingVertexShader.hlsl`.</span></span> <span data-ttu-id="4dc90-213">此变体使用 D3D12 可选功能来更有效地呈现立体声图像。</span><span class="sxs-lookup"><span data-stu-id="4dc90-213">This variant uses D3D12 optional features to render stereo images more efficiently.</span></span>

<span data-ttu-id="4dc90-214">着色器将在项目生成时编译，并在 **SpinningCubeRenderer：： CreateDeviceDependentResources** 方法中加载。</span><span class="sxs-lookup"><span data-stu-id="4dc90-214">The shaders compile when the project is built, and loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="4dc90-215">与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="4dc90-215">Interact with your holograms</span></span>

<span data-ttu-id="4dc90-216">用户输入在 **SpatialInputHandler** 类中处理，该类获取 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> 实例并订阅 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> 事件。</span><span class="sxs-lookup"><span data-stu-id="4dc90-216">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="4dc90-217">这将允许检测分流手势和其他空间输入事件。</span><span class="sxs-lookup"><span data-stu-id="4dc90-217">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="4dc90-218">更新全息内容</span><span class="sxs-lookup"><span data-stu-id="4dc90-218">Update holographic content</span></span>

<span data-ttu-id="4dc90-219">混合现实应用在游戏循环中更新，默认情况下，该循环在的 **Update** 方法中实现 `AppMain.cpp` 。</span><span class="sxs-lookup"><span data-stu-id="4dc90-219">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="4dc90-220">**Update** 方法更新场景对象，如旋转立方体，并返回一个 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>对象，该对象用于获取最新的视图和投影矩阵并显示交换链。</span><span class="sxs-lookup"><span data-stu-id="4dc90-220">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="4dc90-221">中的 **Render** 方法 `AppMain.cpp` 采用 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> ，并根据当前应用和空间定位状态将当前帧呈现到每个全息相机。</span><span class="sxs-lookup"><span data-stu-id="4dc90-221">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="notes"></a><span data-ttu-id="4dc90-222">备注</span><span class="sxs-lookup"><span data-stu-id="4dc90-222">Notes</span></span>

<span data-ttu-id="4dc90-223">现在，Windows Mixed Reality 应用模板支持 (/Qspectre) 启用了 Spectre 缓解标志的编译。</span><span class="sxs-lookup"><span data-stu-id="4dc90-223">The Windows Mixed Reality app template now supports compilation with the Spectre mitigation flag enabled (/Qspectre).</span></span> <span data-ttu-id="4dc90-224">在编译使用 Spectre 缓解功能的配置之前，请确保安装 Spectre (MSVC) 运行时库的 Microsoft Visual C++ 版本。</span><span class="sxs-lookup"><span data-stu-id="4dc90-224">Make sure to install the Spectre-mitigated version of the Microsoft Visual C++ (MSVC) runtime libraries before compiling a configuration with Spectre mitigation enabled.</span></span> <span data-ttu-id="4dc90-225">若要安装 Spectre 缓解的 c + + 库，请启动 Visual Studio 安装程序并选择 " **修改**"。</span><span class="sxs-lookup"><span data-stu-id="4dc90-225">To install the Spectre-mitigated C++ libraries, launch the Visual Studio Installer and select **Modify**.</span></span> <span data-ttu-id="4dc90-226">导航到 **各个组件** 并搜索 "spectre"。</span><span class="sxs-lookup"><span data-stu-id="4dc90-226">Navigate to **Individual components** and search for "spectre".</span></span> <span data-ttu-id="4dc90-227">选择与要为其编译 Spectre 的代码所需的目标平台和 MSVC 版本对应的框，然后单击 " **修改** " 开始安装。</span><span class="sxs-lookup"><span data-stu-id="4dc90-227">Select the boxes corresponding to the target platforms and MSVC version that you need to compile Spectre-mitigated code for, and click **Modify** to begin the install.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dc90-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4dc90-228">See also</span></span>
* [<span data-ttu-id="4dc90-229">获取 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="4dc90-229">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="4dc90-230"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="4dc90-230"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="4dc90-231">在 DirectX 中渲染</span><span class="sxs-lookup"><span data-stu-id="4dc90-231">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="4dc90-232">使用 Visual Studio 进行部署和调试</span><span class="sxs-lookup"><span data-stu-id="4dc90-232">Using Visual Studio to deploy and debug</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="4dc90-233">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="4dc90-233">Using the HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [<span data-ttu-id="4dc90-234">将 XAML 与全息 DirectX 应用配合使用</span><span class="sxs-lookup"><span data-stu-id="4dc90-234">Using XAML with holographic DirectX apps</span></span>](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)
