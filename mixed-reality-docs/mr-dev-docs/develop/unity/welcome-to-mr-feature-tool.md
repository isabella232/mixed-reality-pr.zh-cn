---
title: 欢迎使用混合现实功能工具
description: 了解面向 HoloLens 和 VR 开发的混合现实功能工具的基础知识。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: 4e822f2dda2a314ce06bc394a4d92b1aa6953af3
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772410"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="71c3c-104">欢迎使用混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="71c3c-104">Welcome to the Mixed Reality Feature Tool</span></span>

![混合现实功能工具横幅图像](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="71c3c-106">混合现实功能工具目前仅适用于 Unity。</span><span class="sxs-lookup"><span data-stu-id="71c3c-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="71c3c-107">如果是在 Unreal 中进行开发，请参阅[工具安装](../install-the-tools.md)文档。</span><span class="sxs-lookup"><span data-stu-id="71c3c-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="71c3c-108">混合现实功能工具是开发人员发现、更新混合现实功能包并将其添加到 Unity 项目中的一种新方式。</span><span class="sxs-lookup"><span data-stu-id="71c3c-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="71c3c-109">你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。</span><span class="sxs-lookup"><span data-stu-id="71c3c-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="71c3c-110">如果以前从未使用过清单文件，则它是包含所有项目包的 JSON 文件。</span><span class="sxs-lookup"><span data-stu-id="71c3c-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="71c3c-111">验证所需的包后，混合现实功能工具会将它们下载到所选的项目中。</span><span class="sxs-lookup"><span data-stu-id="71c3c-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="71c3c-112">系统要求</span><span class="sxs-lookup"><span data-stu-id="71c3c-112">System requirements</span></span>

<span data-ttu-id="71c3c-113">在运行混合现实功能工具之前，需要具备以下项：</span><span class="sxs-lookup"><span data-stu-id="71c3c-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="71c3c-114">.NET 5.0 运行时</span><span class="sxs-lookup"><span data-stu-id="71c3c-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="71c3c-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="71c3c-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="71c3c-116">混合现实功能工具目前仅可在 Windows 上运行，但即将推出 MacOS 支持！</span><span class="sxs-lookup"><span data-stu-id="71c3c-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="71c3c-117">下载</span><span class="sxs-lookup"><span data-stu-id="71c3c-117">Download</span></span>

<span data-ttu-id="71c3c-118">设置环境后：</span><span class="sxs-lookup"><span data-stu-id="71c3c-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="71c3c-119">请从 Microsoft 下载中心[下载混合现实功能工具的最新版本](https://aka.ms/MRFeatureTool)。</span><span class="sxs-lookup"><span data-stu-id="71c3c-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="71c3c-120">下载完成后，解压缩文件并将其保存到桌面</span><span class="sxs-lookup"><span data-stu-id="71c3c-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="71c3c-121">建议创建可执行文件的快捷方式，以便更快地进行访问</span><span class="sxs-lookup"><span data-stu-id="71c3c-121">We recommend creating a shortcut to the executable file for faster access</span></span>

> [!NOTE]
> <span data-ttu-id="71c3c-122">如果您是刚开始使用 Unity 包管理器，请遵循我们的 [UPM 说明](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager)。</span><span class="sxs-lookup"><span data-stu-id="71c3c-122">If you're new to using the Unity Package Manager, follow our [UPM instructions](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span></span>

## <a name="changes-in-this-release"></a><span data-ttu-id="71c3c-123">此版本中的更改</span><span class="sxs-lookup"><span data-stu-id="71c3c-123">Changes in this release</span></span>

<span data-ttu-id="71c3c-124">版本 1.0.2103 Beta 包含以下修补程序：</span><span class="sxs-lookup"><span data-stu-id="71c3c-124">Version 1.0.2103 Beta includes the following fixes:</span></span>

* <span data-ttu-id="71c3c-125">改进了下载错误检测。</span><span class="sxs-lookup"><span data-stu-id="71c3c-125">Improvements to download error detection.</span></span>
* <span data-ttu-id="71c3c-126">更新了如何编写清单以避免无法正确更新。</span><span class="sxs-lookup"><span data-stu-id="71c3c-126">Updates on how manifests are written to avoid failure to update correctly.</span></span>
* <span data-ttu-id="71c3c-127">已从项目清单中的文件路径中删除 Escpaing。</span><span class="sxs-lookup"><span data-stu-id="71c3c-127">Escpaing has been removed from file paths in the project manifest.</span></span>

<span data-ttu-id="71c3c-128">此版本中添加了以下功能：</span><span class="sxs-lookup"><span data-stu-id="71c3c-128">The following features have been added in this release:</span></span>

* <span data-ttu-id="71c3c-129">功能目录现在会缓存。</span><span class="sxs-lookup"><span data-stu-id="71c3c-129">The feature catalog is now cached.</span></span> <span data-ttu-id="71c3c-130">若要检查新功能和更新，请使用“发现”中的刷新按钮。</span><span class="sxs-lookup"><span data-stu-id="71c3c-130">To check for new features and updates, please use the refresh button in Discovery.</span></span>
* <span data-ttu-id="71c3c-131">将项目选择从“导入”步骤移动到“发现”之前。</span><span class="sxs-lookup"><span data-stu-id="71c3c-131">Move project selection from the Import step to before Discovery.</span></span>
* <span data-ttu-id="71c3c-132">可用包按项目的指定 Unity 版本进行筛选。</span><span class="sxs-lookup"><span data-stu-id="71c3c-132">Available packages are filtered by the project's specified Unity version.</span></span>
* <span data-ttu-id="71c3c-133">发现视图现在会显示当前安装的包。</span><span class="sxs-lookup"><span data-stu-id="71c3c-133">The discovery view now displays currently installed packages.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="71c3c-134">1.入门</span><span class="sxs-lookup"><span data-stu-id="71c3c-134">1. Getting started</span></span>

<span data-ttu-id="71c3c-135">从可执行文件启动混合现实功能工具，此操作将在首次启动时显示起始页：</span><span class="sxs-lookup"><span data-stu-id="71c3c-135">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![开始使用](images/FeatureToolStart.png)

<span data-ttu-id="71c3c-137">从起始页，你可以：</span><span class="sxs-lookup"><span data-stu-id="71c3c-137">From the start page, you can:</span></span>

* <span data-ttu-id="71c3c-138">[使用齿轮图标按钮配置](configuring-feature-tool.md)工具设置</span><span class="sxs-lookup"><span data-stu-id="71c3c-138">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="71c3c-139">使用问号按钮启动默认 web 浏览器并显示文档</span><span class="sxs-lookup"><span data-stu-id="71c3c-139">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="71c3c-140">选择“开始”，开始发现功能包</span><span class="sxs-lookup"><span data-stu-id="71c3c-140">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-selecting-your-unity-project"></a><span data-ttu-id="71c3c-141">2. 选择 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="71c3c-141">2. Selecting your Unity project</span></span>

<span data-ttu-id="71c3c-142">为了确保您项目的 Unity 版本支持所有发现的功能，第一步是使用省略号按钮（位于项目路径字段右侧）将混合现实功能工具指向您的项目。</span><span class="sxs-lookup"><span data-stu-id="71c3c-142">To ensure that all discovered features are supported on your project's version of Unity, the fist step is to point the Mixed Reality Feature Tool to your project using the **ellipsis** button (to the right of the project path field).</span></span>

![选择 Unity 项目](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> <span data-ttu-id="71c3c-144">浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。</span><span class="sxs-lookup"><span data-stu-id="71c3c-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="71c3c-145">文件名必须有一个值才能使文件夹被选中。</span><span class="sxs-lookup"><span data-stu-id="71c3c-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="71c3c-146">找到项目的文件夹后，单击“打开”按钮返回到混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="71c3c-146">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71c3c-147">混合现实功能工具执行验证以确保它已定向到 Unity 项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="71c3c-147">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="71c3c-148">该文件夹必须包含 `Assets`、`Packages` 和 `Project Settings` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="71c3c-148">The folder must contain `Assets`, `Packages` and `Project Settings` folders.</span></span>

## <a name="3-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="71c3c-149">3. 发现并获取功能包</span><span class="sxs-lookup"><span data-stu-id="71c3c-149">3. Discovering and acquiring feature packages</span></span>

> [!NOTE]
> <span data-ttu-id="71c3c-150">版本 1.0.2103 Beta 现在每次访问服务器时都会缓存功能目录内容。</span><span class="sxs-lookup"><span data-stu-id="71c3c-150">Version 1.0.2103 Beta now caches the feature catalog contents whenever the server is accessed.</span></span> <span data-ttu-id="71c3c-151">通过此更改，可以快速访问可用功能，但却只能显示绝对最新的数据。</span><span class="sxs-lookup"><span data-stu-id="71c3c-151">This change enables fast access to available features, at the expense of displaying the absolute latest data.</span></span> <span data-ttu-id="71c3c-152">若要更新目录，请使用“刷新”按钮。</span><span class="sxs-lookup"><span data-stu-id="71c3c-152">To update the catalog, please use the **Refresh** button.</span></span>

<span data-ttu-id="71c3c-153">功能按类别分组，方便查找。</span><span class="sxs-lookup"><span data-stu-id="71c3c-153">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="71c3c-154">例如，“混合现实工具包”类别具有几个可供选择的功能：</span><span class="sxs-lookup"><span data-stu-id="71c3c-154">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![发现和获取](images/FeatureToolDiscovery.png)

<span data-ttu-id="71c3c-156">当混合现实功能工具识别到以前导入的功能时，它针对每个功能显示一条通知消息。</span><span class="sxs-lookup"><span data-stu-id="71c3c-156">When the Mixed Reality Feature Tool recognizes previously imported feature(s), it displays a notification message by each.</span></span>

![已导入功能的通知](images/feature-tool-imported-note.png)


<span data-ttu-id="71c3c-158">做出选择后，选择“获取功能”，从目录中获取所有所需的包。</span><span class="sxs-lookup"><span data-stu-id="71c3c-158">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="71c3c-159">有关详细信息，请参阅[发现并获取功能](discovering-features.md)。</span><span class="sxs-lookup"><span data-stu-id="71c3c-159">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="4-importing-feature-packages"></a><span data-ttu-id="71c3c-160">4. 导入功能包</span><span class="sxs-lookup"><span data-stu-id="71c3c-160">4. Importing feature packages</span></span>

<span data-ttu-id="71c3c-161">获取完毕后，将显示完整的包集，以及所需依赖项的列表。</span><span class="sxs-lookup"><span data-stu-id="71c3c-161">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="71c3c-162">如果需要更改任何功能或包选择，则可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="71c3c-162">If you need to change any feature or package selections, this is the time:</span></span>

![导入程序包](images/FeatureToolImport.png)

<span data-ttu-id="71c3c-164">强烈建议使用“验证”按钮，确保 Unity 项目可以成功导入所选功能。</span><span class="sxs-lookup"><span data-stu-id="71c3c-164">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="71c3c-165">验证完成后，你将看到一个弹出对话框，其中包含一条成功消息或已识别出的问题的列表。</span><span class="sxs-lookup"><span data-stu-id="71c3c-165">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="71c3c-166">选择“导入”继续。</span><span class="sxs-lookup"><span data-stu-id="71c3c-166">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="71c3c-167">单击“导入”按钮后，如果有任何问题仍存在，则将显示一条简单消息。</span><span class="sxs-lookup"><span data-stu-id="71c3c-167">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="71c3c-168">建议单击“否”，并使用“验证”按钮来查看和解决问题。</span><span class="sxs-lookup"><span data-stu-id="71c3c-168">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="71c3c-169">有关详细信息，请参阅[导入功能](importing-features.md)。</span><span class="sxs-lookup"><span data-stu-id="71c3c-169">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="5-reviewing-and-approving-project-changes"></a><span data-ttu-id="71c3c-170">5. 查看和批准项目更改</span><span class="sxs-lookup"><span data-stu-id="71c3c-170">5. Reviewing and approving project changes</span></span>

<span data-ttu-id="71c3c-171">最后一步是检查并批准对清单和项目文件的建议更改：</span><span class="sxs-lookup"><span data-stu-id="71c3c-171">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="71c3c-172">建议的清单更改显示在左侧</span><span class="sxs-lookup"><span data-stu-id="71c3c-172">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="71c3c-173">要添加到项目中的文件显示在右侧</span><span class="sxs-lookup"><span data-stu-id="71c3c-173">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="71c3c-174">“比较”按钮允许并排查看当前清单和建议的更改</span><span class="sxs-lookup"><span data-stu-id="71c3c-174">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![授权](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="71c3c-176">有关详细信息，请参阅[查看和批准项目修改](reviewing-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="71c3c-176">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="6-project-updated"></a><span data-ttu-id="71c3c-177">6. 已更新项目</span><span class="sxs-lookup"><span data-stu-id="71c3c-177">6. Project updated</span></span>

<span data-ttu-id="71c3c-178">更改建议获得批准后，目标 Unity 项目会进行相应更新以引用所选的混合现实功能。</span><span class="sxs-lookup"><span data-stu-id="71c3c-178">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features.</span></span>

![已更新项目](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="71c3c-180">Unity 项目的 Packages 文件夹现在具有一个包含功能包文件的 MixedReality 子文件夹，并且清单将包含相应的引用 。</span><span class="sxs-lookup"><span data-stu-id="71c3c-180">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="71c3c-181">返回到 Unity，等待加载新的选定功能，并开始生成！</span><span class="sxs-lookup"><span data-stu-id="71c3c-181">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="71c3c-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71c3c-182">See also</span></span>

- [<span data-ttu-id="71c3c-183">配置功能工具</span><span class="sxs-lookup"><span data-stu-id="71c3c-183">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="71c3c-184">发现和获取</span><span class="sxs-lookup"><span data-stu-id="71c3c-184">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="71c3c-185">查看功能包详细信息</span><span class="sxs-lookup"><span data-stu-id="71c3c-185">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="71c3c-186">导入选定包</span><span class="sxs-lookup"><span data-stu-id="71c3c-186">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="71c3c-187">查看和批准项目修改</span><span class="sxs-lookup"><span data-stu-id="71c3c-187">Reviewing and approving project modifications</span></span>](reviewing-changes.md)