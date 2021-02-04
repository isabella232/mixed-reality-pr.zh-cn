---
title: 欢迎使用混合现实功能工具
description: 了解面向 HoloLens 和 VR 开发的混合现实功能工具的基础知识。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: b9d54edb251cfe22d4f5fbea6fa8c923f6ff2d69
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243899"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="382a1-104">欢迎使用混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="382a1-104">Welcome to the Mixed Reality Feature Tool</span></span>

![混合现实功能工具横幅图像](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="382a1-106">混合现实功能工具目前仅适用于 Unity。</span><span class="sxs-lookup"><span data-stu-id="382a1-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="382a1-107">如果是在 Unreal 中进行开发，请参阅[工具安装](../install-the-tools.md)文档。</span><span class="sxs-lookup"><span data-stu-id="382a1-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="382a1-108">混合现实功能工具是开发人员发现、更新混合现实功能包并将其添加到 Unity 项目中的一种新方式。</span><span class="sxs-lookup"><span data-stu-id="382a1-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="382a1-109">你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。</span><span class="sxs-lookup"><span data-stu-id="382a1-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="382a1-110">如果以前从未使用过清单文件，则它是包含所有项目包的 JSON 文件。</span><span class="sxs-lookup"><span data-stu-id="382a1-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="382a1-111">验证所需的包后，混合现实功能工具会将它们下载到所选的项目中。</span><span class="sxs-lookup"><span data-stu-id="382a1-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="382a1-112">系统要求</span><span class="sxs-lookup"><span data-stu-id="382a1-112">System requirements</span></span>

<span data-ttu-id="382a1-113">在运行混合现实功能工具之前，需要具备以下项：</span><span class="sxs-lookup"><span data-stu-id="382a1-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="382a1-114">.NET 5.0 运行时</span><span class="sxs-lookup"><span data-stu-id="382a1-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="382a1-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="382a1-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="382a1-116">混合现实功能工具目前仅可在 Windows 上运行，但即将推出 MacOS 支持！</span><span class="sxs-lookup"><span data-stu-id="382a1-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

<span data-ttu-id="382a1-117">设置环境后：</span><span class="sxs-lookup"><span data-stu-id="382a1-117">Once you have your environment set up:</span></span>

* <span data-ttu-id="382a1-118">请从 [Microsoft 下载中心](https://aka.ms/MRFeatureTool)下载混合现实功能工具的最新版本。</span><span class="sxs-lookup"><span data-stu-id="382a1-118">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool).</span></span>
* <span data-ttu-id="382a1-119">下载完成后，解压缩文件并将其保存到桌面</span><span class="sxs-lookup"><span data-stu-id="382a1-119">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="382a1-120">建议创建可执行文件的快捷方式，以便更快地进行访问</span><span class="sxs-lookup"><span data-stu-id="382a1-120">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="382a1-121">1.入门</span><span class="sxs-lookup"><span data-stu-id="382a1-121">1. Getting started</span></span>

<span data-ttu-id="382a1-122">从可执行文件启动混合现实功能工具，此操作将在首次启动时显示起始页：</span><span class="sxs-lookup"><span data-stu-id="382a1-122">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![开始使用](images/FeatureToolStart.png)

<span data-ttu-id="382a1-124">从起始页，你可以：</span><span class="sxs-lookup"><span data-stu-id="382a1-124">From the start page, you can:</span></span>

* <span data-ttu-id="382a1-125">[使用齿轮图标按钮配置](configuring-feature-tool.md)工具设置</span><span class="sxs-lookup"><span data-stu-id="382a1-125">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="382a1-126">使用问号按钮启动默认 web 浏览器并显示文档</span><span class="sxs-lookup"><span data-stu-id="382a1-126">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="382a1-127">选择“开始”，开始发现功能包</span><span class="sxs-lookup"><span data-stu-id="382a1-127">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="382a1-128">2.发现并获取功能包</span><span class="sxs-lookup"><span data-stu-id="382a1-128">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="382a1-129">按下“开始”之后，即会检索功能包目录。</span><span class="sxs-lookup"><span data-stu-id="382a1-129">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="382a1-130">功能按类别分组，方便查找。</span><span class="sxs-lookup"><span data-stu-id="382a1-130">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="382a1-131">例如，“混合现实工具包”类别具有几个可供选择的功能：</span><span class="sxs-lookup"><span data-stu-id="382a1-131">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![发现和获取](images/FeatureToolDiscovery.png)

<span data-ttu-id="382a1-133">做出选择后，选择“获取功能”，从目录中获取所有所需的包。</span><span class="sxs-lookup"><span data-stu-id="382a1-133">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="382a1-134">有关详细信息，请参阅[发现并获取功能](discovering-features.md)。</span><span class="sxs-lookup"><span data-stu-id="382a1-134">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="382a1-135">3.导入功能包</span><span class="sxs-lookup"><span data-stu-id="382a1-135">3. Importing feature packages</span></span>

<span data-ttu-id="382a1-136">获取完毕后，将显示完整的包集，以及所需依赖项的列表。</span><span class="sxs-lookup"><span data-stu-id="382a1-136">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="382a1-137">如果需要更改任何功能或包选择，则可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="382a1-137">If you need to change any feature or package selections, this is the time:</span></span>

![导入程序包](images/FeatureToolImport.png)

<span data-ttu-id="382a1-139">强烈建议使用“验证”按钮，确保 Unity 项目可以成功导入所选功能。</span><span class="sxs-lookup"><span data-stu-id="382a1-139">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="382a1-140">验证完成后，你将看到一个弹出对话框，其中包含一条成功消息或已识别出的问题的列表。</span><span class="sxs-lookup"><span data-stu-id="382a1-140">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="382a1-141">还需要在导入之前设置目标 Unity 项目的位置。</span><span class="sxs-lookup"><span data-stu-id="382a1-141">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="382a1-142">使用项目路径左侧的省略号按钮进行浏览。</span><span class="sxs-lookup"><span data-stu-id="382a1-142">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="382a1-143">完成文件系统导航后，打开包含目标 Unity 项目的文件夹。</span><span class="sxs-lookup"><span data-stu-id="382a1-143">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="382a1-144">浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。</span><span class="sxs-lookup"><span data-stu-id="382a1-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="382a1-145">文件名必须有一个值才能使文件夹被选中。</span><span class="sxs-lookup"><span data-stu-id="382a1-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="382a1-146">选择“导入”继续。</span><span class="sxs-lookup"><span data-stu-id="382a1-146">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="382a1-147">单击“导入”按钮后，如果有任何问题仍存在，则将显示一条简单消息。</span><span class="sxs-lookup"><span data-stu-id="382a1-147">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="382a1-148">建议单击“否”，并使用“验证”按钮来查看和解决问题。</span><span class="sxs-lookup"><span data-stu-id="382a1-148">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="382a1-149">有关详细信息，请参阅[导入功能](importing-features.md)。</span><span class="sxs-lookup"><span data-stu-id="382a1-149">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="382a1-150">4.查看和批准项目更改</span><span class="sxs-lookup"><span data-stu-id="382a1-150">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="382a1-151">最后一步是检查并批准对清单和项目文件的建议更改：</span><span class="sxs-lookup"><span data-stu-id="382a1-151">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="382a1-152">建议的清单更改显示在左侧</span><span class="sxs-lookup"><span data-stu-id="382a1-152">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="382a1-153">要添加到项目中的文件显示在右侧</span><span class="sxs-lookup"><span data-stu-id="382a1-153">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="382a1-154">“比较”按钮允许并排查看当前清单和建议的更改</span><span class="sxs-lookup"><span data-stu-id="382a1-154">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![授权](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="382a1-156">有关详细信息，请参阅[查看和批准项目修改](reviewing-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="382a1-156">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="382a1-157">5.已更新项目</span><span class="sxs-lookup"><span data-stu-id="382a1-157">5. Project updated</span></span>

<span data-ttu-id="382a1-158">更改建议获得批准后，会更新目标 Unity 项目以引用所选的混合现实功能：</span><span class="sxs-lookup"><span data-stu-id="382a1-158">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![已更新项目](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="382a1-160">Unity 项目的 Packages 文件夹现在具有一个包含功能包文件的 MixedReality 子文件夹，并且清单将包含相应的引用 。</span><span class="sxs-lookup"><span data-stu-id="382a1-160">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="382a1-161">返回到 Unity，等待加载新的选定功能，并开始生成！</span><span class="sxs-lookup"><span data-stu-id="382a1-161">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="382a1-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="382a1-162">See also</span></span>

- [<span data-ttu-id="382a1-163">配置功能工具</span><span class="sxs-lookup"><span data-stu-id="382a1-163">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="382a1-164">发现和获取</span><span class="sxs-lookup"><span data-stu-id="382a1-164">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="382a1-165">查看功能包详细信息</span><span class="sxs-lookup"><span data-stu-id="382a1-165">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="382a1-166">导入选定包</span><span class="sxs-lookup"><span data-stu-id="382a1-166">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="382a1-167">查看和批准项目修改</span><span class="sxs-lookup"><span data-stu-id="382a1-167">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
