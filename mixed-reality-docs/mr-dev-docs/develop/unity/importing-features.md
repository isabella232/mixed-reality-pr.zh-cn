---
title: 导入功能
description: 了解如何从面向 HoloLens 和 VR 开发的混合现实功能工具导入并安装功能。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: a82eea93a07b662314f3a718eef0c1bd18a4ca4e
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243878"
---
# <a name="importing-features"></a><span data-ttu-id="2fb72-104">导入功能</span><span class="sxs-lookup"><span data-stu-id="2fb72-104">Importing features</span></span>

<span data-ttu-id="2fb72-105">下载功能后，可以查看这些功能并将其导入到 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="2fb72-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="2fb72-106">在此步骤中，你的应用程序窗口应如下图所示：</span><span class="sxs-lookup"><span data-stu-id="2fb72-106">At this step, your application window should look like the following image:</span></span>

![导入功能](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="2fb72-108">特征列表</span><span class="sxs-lookup"><span data-stu-id="2fb72-108">Features list</span></span>

<span data-ttu-id="2fb72-109">“功能”列表包含在发现过程中选择的包的集合。</span><span class="sxs-lookup"><span data-stu-id="2fb72-109">The **Features** list contains the collection of packages selected during discovery.</span></span> 
* <span data-ttu-id="2fb72-110">在导入之前，可以选择或取消选择每个功能。</span><span class="sxs-lookup"><span data-stu-id="2fb72-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="2fb72-111">可使用下面所示的“详细信息”链接查看包详细信息</span><span class="sxs-lookup"><span data-stu-id="2fb72-111">Package details can be viewed using the **Details** link shown below</span></span>

![特征列表](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="2fb72-113">必需的依赖项列表</span><span class="sxs-lookup"><span data-stu-id="2fb72-113">Required dependencies list</span></span>

<span data-ttu-id="2fb72-114">“必需的依赖项”列表包含运行一个或多个所选功能所需的包。</span><span class="sxs-lookup"><span data-stu-id="2fb72-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="2fb72-115">此列表还将包含依赖项的依赖项。</span><span class="sxs-lookup"><span data-stu-id="2fb72-115">This list will also contain dependencies of dependencies.</span></span>
* <span data-ttu-id="2fb72-116">在导入之前，可以选择或取消选择每个依赖项。</span><span class="sxs-lookup"><span data-stu-id="2fb72-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="2fb72-117">可使用下面所示的“详细信息”链接查看包详细信息</span><span class="sxs-lookup"><span data-stu-id="2fb72-117">Package details can be viewed using the **Details** link shown below</span></span>

![依赖项列表](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="2fb72-119">如果取消选择所需的依赖项，则会导致在 Unity 中加载项目时出现一个或多个依赖项缺失的错误。</span><span class="sxs-lookup"><span data-stu-id="2fb72-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="2fb72-120">这些功能在项目中不可用。</span><span class="sxs-lookup"><span data-stu-id="2fb72-120">These features won't be usable in the project.</span></span>

## <a name="specifying-the-unity-project-path"></a><span data-ttu-id="2fb72-121">指定 Unity 项目路径</span><span class="sxs-lookup"><span data-stu-id="2fb72-121">Specifying the Unity project path</span></span>

<span data-ttu-id="2fb72-122">必须先向混合现实功能工具注册路径，然后才能将功能导入到项目中。</span><span class="sxs-lookup"><span data-stu-id="2fb72-122">Before features can be imported into the project, you need to register the path with the Mixed Reality Feature Tool.</span></span>

![设置项目路径](images/ProjectPath.png)

## <a name="validating-selections"></a><span data-ttu-id="2fb72-124">验证选定内容</span><span class="sxs-lookup"><span data-stu-id="2fb72-124">Validating selections</span></span>

<span data-ttu-id="2fb72-125">强烈建议在导入前验证所选功能。</span><span class="sxs-lookup"><span data-stu-id="2fb72-125">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="2fb72-126">此步骤引发的任何问题都可能会妨碍项目成功开发。</span><span class="sxs-lookup"><span data-stu-id="2fb72-126">This step will raise any issues that are likely to impede successful project development.</span></span>

![验证问题](images/ValidationIssues.png)

<span data-ttu-id="2fb72-128">混合现实功能工具提供了两个自行解决问题的方法（如后面部分所述）以及手动取消和解决问题的选项。</span><span class="sxs-lookup"><span data-stu-id="2fb72-128">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2fb72-129">混合现实功能工具无法自行解决与所需版本的 Unity 相关的问题。</span><span class="sxs-lookup"><span data-stu-id="2fb72-129">The Mixed Reality Feature Tool cannot automatically resolve issues related to required versions of Unity.</span></span> <span data-ttu-id="2fb72-130">必须通过升级项目所使用的 Unity 版本或禁用需要更新版本的功能，手动处理这些问题。</span><span class="sxs-lookup"><span data-stu-id="2fb72-130">These issues must be handled manually by upgrading the version of Unity used by the project or disabling the feature(s) requiring a newer version.</span></span>
>
> <span data-ttu-id="2fb72-131">未来版本的混合现实功能工具将根据项目所使用的 Unity 版本提供更好的功能筛选。</span><span class="sxs-lookup"><span data-stu-id="2fb72-131">A future release of the Mixed Reality Feature Tool will provide better filtering of features based upon the version of Unity being used by the project.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="2fb72-132">启用依赖项</span><span class="sxs-lookup"><span data-stu-id="2fb72-132">Enable dependencies</span></span>

<span data-ttu-id="2fb72-133">“启用依赖项”按钮将自动重新选择缺少的依赖项。</span><span class="sxs-lookup"><span data-stu-id="2fb72-133">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="2fb72-134">此选项适用于显式选择的依赖项（显示在“功能”列表中）和根据所选功能的要求隐式选择的依赖项。</span><span class="sxs-lookup"><span data-stu-id="2fb72-134">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="2fb72-135">禁用功能</span><span class="sxs-lookup"><span data-stu-id="2fb72-135">Disable features</span></span>

<span data-ttu-id="2fb72-136">选择“禁用功能”会自动取消选择依赖于一个或多个未选中的依赖项的功能。</span><span class="sxs-lookup"><span data-stu-id="2fb72-136">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="2fb72-137">此选项适用于隐式选择的依赖项包和显式选择的功能。</span><span class="sxs-lookup"><span data-stu-id="2fb72-137">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="2fb72-138">导入</span><span class="sxs-lookup"><span data-stu-id="2fb72-138">Importing</span></span>

<span data-ttu-id="2fb72-139">选择“导入”添加所选功能，并在更新目标项目之前提供[最终审批](reviewing-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="2fb72-139">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2fb72-140">如果导入时仍然存在验证问题，则将显示一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="2fb72-140">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="2fb72-141">建议选择“否”，单击“验证”并解决所显示的任何问题。</span><span class="sxs-lookup"><span data-stu-id="2fb72-141">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![继续验证问题](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="2fb72-143">返回到上一步骤</span><span class="sxs-lookup"><span data-stu-id="2fb72-143">Going back to the previous step</span></span>

<span data-ttu-id="2fb72-144">在“导入功能”中，混合现实功能工具允许返回到[发现](discovering-features.md)。</span><span class="sxs-lookup"><span data-stu-id="2fb72-144">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="2fb72-145">选择“返回”下载其他功能包。</span><span class="sxs-lookup"><span data-stu-id="2fb72-145">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fb72-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fb72-146">See also</span></span>

- [<span data-ttu-id="2fb72-147">欢迎使用混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="2fb72-147">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="2fb72-148">发现和获取</span><span class="sxs-lookup"><span data-stu-id="2fb72-148">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="2fb72-149">查看功能包详细信息</span><span class="sxs-lookup"><span data-stu-id="2fb72-149">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="2fb72-150">查看和批准项目修改</span><span class="sxs-lookup"><span data-stu-id="2fb72-150">Reviewing and approving project modifications</span></span>](reviewing-changes.md)