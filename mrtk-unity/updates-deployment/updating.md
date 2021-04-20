---
title: 更新
description: 从较低版本的 MRTK 进行迁移的文档。
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742233"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a><span data-ttu-id="019a2-104">更新 Microsoft Mixed Reality 工具包</span><span class="sxs-lookup"><span data-stu-id="019a2-104">Updating the Microsoft Mixed Reality Toolkit</span></span>

- [<span data-ttu-id="019a2-105">升级到新版本的 MRTK</span><span class="sxs-lookup"><span data-stu-id="019a2-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="019a2-106">2.3.0 到2.4。0</span><span class="sxs-lookup"><span data-stu-id="019a2-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="019a2-107">2.2.0 到2.3。0</span><span class="sxs-lookup"><span data-stu-id="019a2-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="019a2-108">2.1.0 到2.2。0</span><span class="sxs-lookup"><span data-stu-id="019a2-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="019a2-109">2.0.0 到2.1。0</span><span class="sxs-lookup"><span data-stu-id="019a2-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="019a2-110">RC2 到2.0。0</span><span class="sxs-lookup"><span data-stu-id="019a2-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="019a2-111">查找当前版本</span><span class="sxs-lookup"><span data-stu-id="019a2-111">Finding the current version</span></span> 

<span data-ttu-id="019a2-112">按照以下说明来确定当前正在使用的 MRTK 版本：</span><span class="sxs-lookup"><span data-stu-id="019a2-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="019a2-113">在 Unity 中打开 MRTK 项目</span><span class="sxs-lookup"><span data-stu-id="019a2-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="019a2-114">在项目窗口中导航到 "MixedRealityToolkit" 文件夹</span><span class="sxs-lookup"><span data-stu-id="019a2-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="019a2-115">打开名为 "Version" 的文件</span><span class="sxs-lookup"><span data-stu-id="019a2-115">Open the file called "Version"</span></span>

<span data-ttu-id="019a2-116">如果上面的文件和文件夹不存在，则是 MRTK 的较新版本。</span><span class="sxs-lookup"><span data-stu-id="019a2-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="019a2-117">在这种情况下，请尝试以下操作：</span><span class="sxs-lookup"><span data-stu-id="019a2-117">In that case, try the following:</span></span>

1. <span data-ttu-id="019a2-118">导航到 "混合现实工具包 Foundation" 文件夹</span><span class="sxs-lookup"><span data-stu-id="019a2-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="019a2-119">单击 "package.js打开" 以查看 Unity 中的预览或使用文本编辑器打开该预览版</span><span class="sxs-lookup"><span data-stu-id="019a2-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="019a2-120">查找包含单词 "version：" 的行</span><span class="sxs-lookup"><span data-stu-id="019a2-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="019a2-121">升级到新版本的 MRTK</span><span class="sxs-lookup"><span data-stu-id="019a2-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="019a2-122">*强烈建议在获取 MRTK 更新后运行 [迁移工具](../features/tools/migration-window.md)* ，以自动修复并从弃用的组件升级，并调整为重大更改。</span><span class="sxs-lookup"><span data-stu-id="019a2-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="019a2-123">迁移工具是 **工具包** 的一部分。</span><span class="sxs-lookup"><span data-stu-id="019a2-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="019a2-124">以下说明介绍了 2.4.0 to 2.5.0 upgrade path。</span><span class="sxs-lookup"><span data-stu-id="019a2-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="019a2-125">如果项目在2.3.0 或更早版本上，请阅读 [版本间](#updating-230-to-240) 的更改以了解升级路径，或阅读以前 [版本的说明](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) ，以进行版本升级。</span><span class="sxs-lookup"><span data-stu-id="019a2-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="019a2-126">混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="019a2-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="019a2-127">将 MRTK 升级到较新版本 MRTK 的最简单方法是使用 [混合现实功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 下载最新的包并将它们直接加载到 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="019a2-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="019a2-128">如果项目以前使用了 Unity 资产)  (，请参阅 [这些说明](#switching-from-unity-asset-files-to-mixed-reality-feature-tool)。</span><span class="sxs-lookup"><span data-stu-id="019a2-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="019a2-129">Unity 资产 ( unitypackage) 文件</span><span class="sxs-lookup"><span data-stu-id="019a2-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="019a2-130">另一种升级途径是手动下载 MRTK Unity 包并将其应用于你的项目。</span><span class="sxs-lookup"><span data-stu-id="019a2-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="019a2-131">请参阅以下步骤，</span><span class="sxs-lookup"><span data-stu-id="019a2-131">See the steps below,</span></span>

1. <span data-ttu-id="019a2-132">保存当前项目的副本，以防在升级步骤中的任何点点击任何障碍。</span><span class="sxs-lookup"><span data-stu-id="019a2-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="019a2-133">关闭 Unity</span><span class="sxs-lookup"><span data-stu-id="019a2-133">Close Unity</span></span>
1. <span data-ttu-id="019a2-134">在 " *资产* " 文件夹中，删除以下 **MRTK** 文件夹及其元文件 (项目可能没有所有列出的文件夹) </span><span class="sxs-lookup"><span data-stu-id="019a2-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="019a2-135">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="019a2-135">MRTK/Core</span></span>
    - <span data-ttu-id="019a2-136">MRTK/示例</span><span class="sxs-lookup"><span data-stu-id="019a2-136">MRTK/Examples</span></span>
    - <span data-ttu-id="019a2-137">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="019a2-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="019a2-138">MRTK/提供程序</span><span class="sxs-lookup"><span data-stu-id="019a2-138">MRTK/Providers</span></span>
    - <span data-ttu-id="019a2-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="019a2-139">MRTK/SDK</span></span>
    - <span data-ttu-id="019a2-140">MRTK/服务</span><span class="sxs-lookup"><span data-stu-id="019a2-140">MRTK/Services</span></span>
    - <span data-ttu-id="019a2-141">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="019a2-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="019a2-142">如果对 MRTK 着色器进行了修改，请在删除 MRTK/StandardAssets 文件夹之前创建本地备份</span><span class="sxs-lookup"><span data-stu-id="019a2-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="019a2-143">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="019a2-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="019a2-144">请勿删除 **MixedRealityToolkit** 文件夹或其元文件。</span><span class="sxs-lookup"><span data-stu-id="019a2-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="019a2-145">删除 **库** 文件夹</span><span class="sxs-lookup"><span data-stu-id="019a2-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="019a2-146">某些 Unity 工具（如 Unity Collab）将配置信息保存到库文件夹。</span><span class="sxs-lookup"><span data-stu-id="019a2-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="019a2-147">如果使用这样的工具，请首先从库中复制该工具的数据文件夹，然后再删除，然后在库重新生成后将其还原。</span><span class="sxs-lookup"><span data-stu-id="019a2-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="019a2-148">重新打开 Unity 中的项目</span><span class="sxs-lookup"><span data-stu-id="019a2-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="019a2-149">导入新的 unity 包</span><span class="sxs-lookup"><span data-stu-id="019a2-149">Import the new unity packages</span></span>
    - <span data-ttu-id="019a2-150">Foundation- _首先导入此包_</span><span class="sxs-lookup"><span data-stu-id="019a2-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="019a2-151">工具</span><span class="sxs-lookup"><span data-stu-id="019a2-151">Tools</span></span>
    - <span data-ttu-id="019a2-152"> (可选) 扩展</span><span class="sxs-lookup"><span data-stu-id="019a2-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="019a2-153">如果已安装其他扩展，则可能需要重新导入它们。</span><span class="sxs-lookup"><span data-stu-id="019a2-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="019a2-154"> (可选) 示例</span><span class="sxs-lookup"><span data-stu-id="019a2-154">(Optional) Examples</span></span>
1. <span data-ttu-id="019a2-155">关闭 Unity 并删除 **库** 文件夹 (请先阅读下面的说明！ ) 。</span><span class="sxs-lookup"><span data-stu-id="019a2-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="019a2-156">此步骤是强制 Unity 刷新其资产数据库和协调现有自定义配置文件所必需的。</span><span class="sxs-lookup"><span data-stu-id="019a2-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="019a2-157">为项目中的每个场景启动 Unity 和</span><span class="sxs-lookup"><span data-stu-id="019a2-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="019a2-158">从层次结构中删除 **MixedRealityToolkit** 和 **MixedRealityPlayspace**（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="019a2-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="019a2-159">这将删除主摄像机，但会在下一步中重新创建它。</span><span class="sxs-lookup"><span data-stu-id="019a2-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="019a2-160">如果已手动更改了主相机的任何属性，则在创建新相机后，必须手动重新应用这些属性。</span><span class="sxs-lookup"><span data-stu-id="019a2-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="019a2-161">选择 **MixedRealityToolkit-> 添加到场景并配置**</span><span class="sxs-lookup"><span data-stu-id="019a2-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="019a2-162">选择 **MixedRealityToolkit-> 公用事业-> Update-> 控制器映射配置文件** (仅需执行一次) -这将用更新的轴和数据更新任何自定义控制器映射配置文件，同时使自定义分配的输入操作保持不变</span><span class="sxs-lookup"><span data-stu-id="019a2-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="019a2-163">运行 [迁移工具](../features/tools/migration-window.md) 并在 *整个项目* 上运行该工具，以确保将所有代码更新到最新版本。</span><span class="sxs-lookup"><span data-stu-id="019a2-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="019a2-164">迁移窗口包含多个不同的迁移处理程序，这些处理程序必须各自运行。</span><span class="sxs-lookup"><span data-stu-id="019a2-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="019a2-165">此步骤涉及：</span><span class="sxs-lookup"><span data-stu-id="019a2-165">This step involves:</span></span>
   - <span data-ttu-id="019a2-166">从 " **迁移处理程序选择** " 下拉列表中选择第一个迁移处理程序。</span><span class="sxs-lookup"><span data-stu-id="019a2-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="019a2-167">单击 "完全项目" 按钮。</span><span class="sxs-lookup"><span data-stu-id="019a2-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="019a2-168">单击 "添加用于迁移的完整项目" 按钮 (这将扫描要迁移的对象的整个项目) 。</span><span class="sxs-lookup"><span data-stu-id="019a2-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="019a2-169">单击 "迁移" 按钮，如果找到任何 migrateable 对象，应启用该按钮。</span><span class="sxs-lookup"><span data-stu-id="019a2-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="019a2-170">为下拉列表中的每个迁移处理程序重复前面三个步骤。</span><span class="sxs-lookup"><span data-stu-id="019a2-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="019a2-171"> (查看 [此问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) ，其中包含可在未来版本中用于简化此迁移过程的工作) </span><span class="sxs-lookup"><span data-stu-id="019a2-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="019a2-172">从 Unity 资产文件切换到混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="019a2-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="019a2-173">从 Unity 资产文件切换到混合现实功能包带来了很多好处：</span><span class="sxs-lookup"><span data-stu-id="019a2-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="019a2-174">更容易更新</span><span class="sxs-lookup"><span data-stu-id="019a2-174">Easier updating</span></span>
- <span data-ttu-id="019a2-175">更快的编译时间</span><span class="sxs-lookup"><span data-stu-id="019a2-175">Faster compile times</span></span>
- <span data-ttu-id="019a2-176">Visual Studio 解决方案中的项目较少</span><span class="sxs-lookup"><span data-stu-id="019a2-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="019a2-177">更改为使用混合现实功能工具需要一组一次性的手动步骤。</span><span class="sxs-lookup"><span data-stu-id="019a2-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="019a2-178">保存当前项目的副本。</span><span class="sxs-lookup"><span data-stu-id="019a2-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="019a2-179">关闭 Unity</span><span class="sxs-lookup"><span data-stu-id="019a2-179">Close Unity</span></span>
1. <span data-ttu-id="019a2-180">在 " *资产* " 文件夹中，删除以下 **MRTK** 文件夹及其元文件 (项目可能没有所有列出的文件夹) </span><span class="sxs-lookup"><span data-stu-id="019a2-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="019a2-181">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="019a2-181">MRTK/Core</span></span>
    - <span data-ttu-id="019a2-182">MRTK/示例</span><span class="sxs-lookup"><span data-stu-id="019a2-182">MRTK/Examples</span></span>
    - <span data-ttu-id="019a2-183">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="019a2-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="019a2-184">MRTK/提供程序</span><span class="sxs-lookup"><span data-stu-id="019a2-184">MRTK/Providers</span></span>
    - <span data-ttu-id="019a2-185">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="019a2-185">MRTK/SDK</span></span>
    - <span data-ttu-id="019a2-186">MRTK/服务</span><span class="sxs-lookup"><span data-stu-id="019a2-186">MRTK/Services</span></span>
    - <span data-ttu-id="019a2-187">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="019a2-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="019a2-188">如果对 MRTK 着色器进行了修改，请在删除 MRTK/StandardAssets 文件夹之前创建本地备份</span><span class="sxs-lookup"><span data-stu-id="019a2-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="019a2-189">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="019a2-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="019a2-190">请勿删除 **MixedRealityToolkit** 文件夹或其元文件。</span><span class="sxs-lookup"><span data-stu-id="019a2-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="019a2-191">删除 **库** 文件夹</span><span class="sxs-lookup"><span data-stu-id="019a2-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="019a2-192">某些 Unity 工具（如 Unity Collab）将配置信息保存到库文件夹。</span><span class="sxs-lookup"><span data-stu-id="019a2-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="019a2-193">如果使用这样的工具，请首先从库中复制该工具的数据文件夹，然后再删除，然后在库重新生成后将其还原。</span><span class="sxs-lookup"><span data-stu-id="019a2-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="019a2-194">重新打开 Unity 中的项目</span><span class="sxs-lookup"><span data-stu-id="019a2-194">Re-open the project in Unity</span></span>

<span data-ttu-id="019a2-195">执行前面的步骤后，请运行 [混合现实功能工具](#mixed-reality-feature-tool) ，并导入所需的混合现实工具包版本。</span><span class="sxs-lookup"><span data-stu-id="019a2-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="019a2-196">将2.3.0 更新为2.4。0</span><span class="sxs-lookup"><span data-stu-id="019a2-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="019a2-197">[文件夹重命名](#folder-renames-in-240) 
[API 更改](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="019a2-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="019a2-198">在2.4.0 中重命名文件夹</span><span class="sxs-lookup"><span data-stu-id="019a2-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="019a2-199">已重命名 MixedRealityToolkit 文件夹，并将其移入版本2.4 中的公共层次结构。</span><span class="sxs-lookup"><span data-stu-id="019a2-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="019a2-200">如果应用程序使用硬编码路径来 MRTK 资源，则需要按照下表对这些资源进行更新。</span><span class="sxs-lookup"><span data-stu-id="019a2-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="019a2-201">上一个文件夹</span><span class="sxs-lookup"><span data-stu-id="019a2-201">Previous Folder</span></span> | <span data-ttu-id="019a2-202">新建文件夹</span><span class="sxs-lookup"><span data-stu-id="019a2-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="019a2-203">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="019a2-203">MixedRealityToolkit</span></span> | <span data-ttu-id="019a2-204">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="019a2-204">MRTK/Core</span></span> |
| <span data-ttu-id="019a2-205">MixedRealityToolkit 示例</span><span class="sxs-lookup"><span data-stu-id="019a2-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="019a2-206">MRTK/示例</span><span class="sxs-lookup"><span data-stu-id="019a2-206">MRTK/Examples</span></span> |
| <span data-ttu-id="019a2-207">MixedRealityToolkit 扩展</span><span class="sxs-lookup"><span data-stu-id="019a2-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="019a2-208">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="019a2-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="019a2-209">MixedRealityToolkit 提供程序</span><span class="sxs-lookup"><span data-stu-id="019a2-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="019a2-210">MRTK/提供程序</span><span class="sxs-lookup"><span data-stu-id="019a2-210">MRTK/Providers</span></span> |
| <span data-ttu-id="019a2-211">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="019a2-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="019a2-212">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="019a2-212">MRTK/SDK</span></span> |
| <span data-ttu-id="019a2-213">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="019a2-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="019a2-214">MRTK/服务</span><span class="sxs-lookup"><span data-stu-id="019a2-214">MRTK/Services</span></span> |
| <span data-ttu-id="019a2-215">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="019a2-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="019a2-216">MRTK/测试</span><span class="sxs-lookup"><span data-stu-id="019a2-216">MRTK/Tests</span></span> |
| <span data-ttu-id="019a2-217">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="019a2-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="019a2-218">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="019a2-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="019a2-219">`MixedRealityToolkit.Generated`包含客户生成的文件，并且保持不变。</span><span class="sxs-lookup"><span data-stu-id="019a2-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="019a2-220">2.4.0 中的眼睛设置</span><span class="sxs-lookup"><span data-stu-id="019a2-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="019a2-221">此版本的 MRTK 修改目视注视设置所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="019a2-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="019a2-222">在输入指针配置文件的 "注视" 设置中可以找到 _"IsEyeTrackingEnabled"_ 复选框。</span><span class="sxs-lookup"><span data-stu-id="019a2-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="019a2-223">选中此框将启用基于眼睛的眼睛，而不是默认的基于头的注视。</span><span class="sxs-lookup"><span data-stu-id="019a2-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="019a2-224">有关这些更改和跟踪设置的完整说明的详细信息，请参阅 [目视跟踪](../features/input/eye-tracking/eye-tracking-basic-setup.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="019a2-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="019a2-225">2.4.0 中的眼睛指针行为</span><span class="sxs-lookup"><span data-stu-id="019a2-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="019a2-226">已对眼睛默认指针行为进行了修改，使其与头眼睛默认指针行为匹配。</span><span class="sxs-lookup"><span data-stu-id="019a2-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="019a2-227">检测到手后，会自动抑制眼睛指示器。</span><span class="sxs-lookup"><span data-stu-id="019a2-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="019a2-228">"选择" 后，眼睛眼睛指针将再次变为可见。</span><span class="sxs-lookup"><span data-stu-id="019a2-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="019a2-229">可在 [眼睛和实习](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) 文章中找到有关注视和手动设置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="019a2-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="019a2-230">2.4.0 中的 API 更改</span><span class="sxs-lookup"><span data-stu-id="019a2-230">API changes in 2.4.0</span></span>

<span data-ttu-id="019a2-231">**自定义控制器类**</span><span class="sxs-lookup"><span data-stu-id="019a2-231">**Custom controller classes**</span></span>

<span data-ttu-id="019a2-232">自定义控制器类之前必须定义 `SetupDefaultInteractions(Handedness)` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="019a2-233">此方法在2.4 中已过时，因为左右手使用习惯参数对于控制器类 "自有左右手使用习惯" 是冗余的。</span><span class="sxs-lookup"><span data-stu-id="019a2-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="019a2-234">新方法没有参数。</span><span class="sxs-lookup"><span data-stu-id="019a2-234">The new method has no parameters.</span></span> <span data-ttu-id="019a2-235">此外，许多控制器类定义了这种 () 的相同方式 `AssignControllerMappings(DefaultInteractions);` ，因此完全调用已重构为 `BaseController` ，并进行了可选替代，而不是必需的。</span><span class="sxs-lookup"><span data-stu-id="019a2-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="019a2-236">**眼睛属性**</span><span class="sxs-lookup"><span data-stu-id="019a2-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="019a2-237">的 `UseEyeTracking` 实现中的属性 `GazeProvider` `IMixedRealityEyeGazeProvider` 已重命名为 `IsEyeTrackingEnabled` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="019a2-238">如果你之前执行此操作 .。。</span><span class="sxs-lookup"><span data-stu-id="019a2-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="019a2-239">立即执行此操作 .。。</span><span class="sxs-lookup"><span data-stu-id="019a2-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="019a2-240">**WindowsApiChecker 属性**</span><span class="sxs-lookup"><span data-stu-id="019a2-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="019a2-241">以下 WindowsApiChecker 属性已标记为过时。</span><span class="sxs-lookup"><span data-stu-id="019a2-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="019a2-242">请使用 `IsMethodAvailable` 、 `IsPropertyAvailable` 或 `IsTypeAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="019a2-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="019a2-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="019a2-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="019a2-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="019a2-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="019a2-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="019a2-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="019a2-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="019a2-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="019a2-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="019a2-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="019a2-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="019a2-249">无计划为将来的 API 协定版本向 WindowsApiChecker 添加属性。</span><span class="sxs-lookup"><span data-stu-id="019a2-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="019a2-250">**GltfMeshPrimitiveAttributes 只读**</span><span class="sxs-lookup"><span data-stu-id="019a2-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="019a2-251">用于可设置的 gltf 网状基元属性现在为只读。</span><span class="sxs-lookup"><span data-stu-id="019a2-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="019a2-252">反序列化时，将设置一次其值。</span><span class="sxs-lookup"><span data-stu-id="019a2-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="019a2-253">自定义按钮图标迁移</span><span class="sxs-lookup"><span data-stu-id="019a2-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="019a2-254">以前的自定义按钮图标需要将新材料分配给按钮的四个呈现器。</span><span class="sxs-lookup"><span data-stu-id="019a2-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="019a2-255">这不再是必需的，我们建议将自定义图标纹理移到 IconSet。</span><span class="sxs-lookup"><span data-stu-id="019a2-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="019a2-256">保留现有的自定义材料和图标。</span><span class="sxs-lookup"><span data-stu-id="019a2-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="019a2-257">但在升级之前，它们将不太好。</span><span class="sxs-lookup"><span data-stu-id="019a2-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="019a2-258">若要将项目中所有按钮上的资产升级为新建议的格式，请使用 ButtonConfigHelperMigrationHandler。</span><span class="sxs-lookup"><span data-stu-id="019a2-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="019a2-259"> (混合现实工具包-> 实用工具-> 迁移窗口-> 迁移处理程序选择-> ButtonConfigHelperMigrationHandler) </span><span class="sxs-lookup"><span data-stu-id="019a2-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![升级窗口对话框](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="019a2-261">如果在迁移过程中在默认图标集中找不到图标，将在 MixedRealityToolkit/CustomIconSets 中创建自定义图标集。</span><span class="sxs-lookup"><span data-stu-id="019a2-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="019a2-262">此时将显示一个对话框，指示已发生此情况。</span><span class="sxs-lookup"><span data-stu-id="019a2-262">A dialog will indicate that this has taken place.</span></span>

![自定义图标通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="019a2-264">将2.2.0 更新为2.3。0</span><span class="sxs-lookup"><span data-stu-id="019a2-264">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="019a2-265">API 更改</span><span class="sxs-lookup"><span data-stu-id="019a2-265">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="019a2-266">2.3.0 中的 API 更改</span><span class="sxs-lookup"><span data-stu-id="019a2-266">API changes in 2.3.0</span></span>

<span data-ttu-id="019a2-267">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="019a2-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="019a2-268">Private ControllerPoseSynchronizer. 左右手使用习惯字段已标记为过时。</span><span class="sxs-lookup"><span data-stu-id="019a2-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="019a2-269">这对应用程序的影响最小，因为字段在其类的外部不可见。</span><span class="sxs-lookup"><span data-stu-id="019a2-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="019a2-270">已 ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)) 中删除 Public ControllerPoseSynchronizer 左右手使用习惯属性的 setter。</span><span class="sxs-lookup"><span data-stu-id="019a2-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="019a2-271">**用于 Unity 的 MSBuild**</span><span class="sxs-lookup"><span data-stu-id="019a2-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="019a2-272">此版本的 MRTK 对 Unity 使用比以前版本更高的 MSBuild 版本。</span><span class="sxs-lookup"><span data-stu-id="019a2-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="019a2-273">在项目加载期间，如果 "Unity 包管理器" 清单中列出了较旧的版本，则会出现 "配置" 对话框，并选中 "启用 MSBuild for Unity" 选项。</span><span class="sxs-lookup"><span data-stu-id="019a2-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="019a2-274">应用将执行升级。</span><span class="sxs-lookup"><span data-stu-id="019a2-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="019a2-275">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="019a2-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="019a2-276">ScriptingUtilities 类已标记为过时，并已替换为 ScriptUtilities 中的 MixedReality 程序集。</span><span class="sxs-lookup"><span data-stu-id="019a2-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="019a2-277">新类将改进以前的行为并添加对删除脚本定义的支持。</span><span class="sxs-lookup"><span data-stu-id="019a2-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="019a2-278">尽管现有代码将继续在版本2.3.0 中运行，但建议将更新为新类。</span><span class="sxs-lookup"><span data-stu-id="019a2-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="019a2-279">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="019a2-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="019a2-280">ShellHandRayPointer 类的 lineRendererSelected 和 lineRendererNoTarget 成员分别 ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)) 替换。</span><span class="sxs-lookup"><span data-stu-id="019a2-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="019a2-281">请将 lineRendererSelected 替换为 lineMaterialSelected 和/或 lineRendererNoTarget with lineMaterialNoTarget，以解决编译错误。</span><span class="sxs-lookup"><span data-stu-id="019a2-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="019a2-282">**空间观察程序 Microsoft.systemforcrossdomainidentitymanagement.iprovider.startupbehavior**</span><span class="sxs-lookup"><span data-stu-id="019a2-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="019a2-283">基于类构建的空间观察器 `BaseSpatialObserver` 现在可在重新启用 ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)) 时遵循 microsoft.systemforcrossdomainidentitymanagement.iprovider.startupbehavior 的值。</span><span class="sxs-lookup"><span data-stu-id="019a2-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="019a2-284">无需进行任何更改即可利用此修补程序。</span><span class="sxs-lookup"><span data-stu-id="019a2-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="019a2-285">**UX 控件 prototyping 已更新为使用 PressableButton**</span><span class="sxs-lookup"><span data-stu-id="019a2-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="019a2-286">以下 prototyping 现在正在使用 PressableButton 组件而不是 TouchHandler 进行近交互 ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070)) </span><span class="sxs-lookup"><span data-stu-id="019a2-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="019a2-287">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="019a2-287">AnimationButton</span></span>
- <span data-ttu-id="019a2-288">Button</span><span class="sxs-lookup"><span data-stu-id="019a2-288">Button</span></span>
- <span data-ttu-id="019a2-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="019a2-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="019a2-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="019a2-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="019a2-291">CheckBox</span><span class="sxs-lookup"><span data-stu-id="019a2-291">CheckBox</span></span>
- <span data-ttu-id="019a2-292">RadialSet</span><span class="sxs-lookup"><span data-stu-id="019a2-292">RadialSet</span></span>
- <span data-ttu-id="019a2-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="019a2-293">ToggleButton</span></span>
- <span data-ttu-id="019a2-294">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="019a2-294">ToggleSwitch</span></span>
- <span data-ttu-id="019a2-295">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="019a2-295">UnityUIButton</span></span>
- <span data-ttu-id="019a2-296">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="019a2-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="019a2-297">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="019a2-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="019a2-298">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="019a2-298">UnityUIToggleButton</span></span>

<span data-ttu-id="019a2-299">由于此更改，应用程序代码可能需要更新。</span><span class="sxs-lookup"><span data-stu-id="019a2-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="019a2-300">**WindowsMixedRealityUtilities 命名空间**</span><span class="sxs-lookup"><span data-stu-id="019a2-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="019a2-301">WindowsMixedRealityUtilities 的命名空间已从 WindowsMixedReality 更改为 MixedReality [#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)) 的。 WindowsMixedReality (。</span><span class="sxs-lookup"><span data-stu-id="019a2-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="019a2-302">请更新 #using 语句以解决编译错误。</span><span class="sxs-lookup"><span data-stu-id="019a2-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="019a2-303">将2.1.0 更新为2.2。0</span><span class="sxs-lookup"><span data-stu-id="019a2-303">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="019a2-304">API 更改</span><span class="sxs-lookup"><span data-stu-id="019a2-304">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="019a2-305">2.2.0 中的 API 更改</span><span class="sxs-lookup"><span data-stu-id="019a2-305">API changes in 2.2.0</span></span>

<span data-ttu-id="019a2-306">**IMixedRealityBoundarySystem。包含**</span><span class="sxs-lookup"><span data-stu-id="019a2-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="019a2-307">之前，此方法采用特定的 Unity 定义试验性枚举。</span><span class="sxs-lookup"><span data-stu-id="019a2-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="019a2-308">它现在采用与 Unity 枚举相同的 MRTK 定义枚举。</span><span class="sxs-lookup"><span data-stu-id="019a2-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="019a2-309">此更改有助于为 Unity 未来的边界 Api 准备 MRTK。</span><span class="sxs-lookup"><span data-stu-id="019a2-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="019a2-310">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="019a2-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="019a2-311">为了更好地描述支持配置文件的要求，MixedRealityServiceProfileAttribute 已更新为添加可选的排除类型集合。</span><span class="sxs-lookup"><span data-stu-id="019a2-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="019a2-312">作为此更改的一部分，ServiceType 属性已从类型更改为类型 []，并已重命名为 RequiredTypes。</span><span class="sxs-lookup"><span data-stu-id="019a2-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="019a2-313">还添加了另一个属性 ExcludedTypes。</span><span class="sxs-lookup"><span data-stu-id="019a2-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="019a2-314">将2.0.0 更新为2.1。0</span><span class="sxs-lookup"><span data-stu-id="019a2-314">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="019a2-315">API 更改</span><span class="sxs-lookup"><span data-stu-id="019a2-315">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="019a2-316">配置文件更改</span><span class="sxs-lookup"><span data-stu-id="019a2-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="019a2-317">2.1.0 中的 API 更改</span><span class="sxs-lookup"><span data-stu-id="019a2-317">API changes in 2.1.0</span></span>

<span data-ttu-id="019a2-318">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="019a2-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="019a2-319">已将 `BaseNearInteractionTouchable` 修改为将方法标记 `OnValidate` 为虚拟。</span><span class="sxs-lookup"><span data-stu-id="019a2-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="019a2-320">扩展 `BaseNearInteractionTouchable` (ex：) 的类已 `NearInteractionTouchableUnityUI` 更新，以反映此更改。</span><span class="sxs-lookup"><span data-stu-id="019a2-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="019a2-321">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="019a2-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="019a2-322">`ColliderNearInteractionTouchable` 类已弃用。</span><span class="sxs-lookup"><span data-stu-id="019a2-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="019a2-323">请更新要使用的代码引用 `BaseNearInteractionTouchable` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="019a2-324">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="019a2-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="019a2-325">**_已_**</span><span class="sxs-lookup"><span data-stu-id="019a2-325">**_Added_**</span></span>

<span data-ttu-id="019a2-326">`IMixedRealityMouseDeviceManager` 添加了 `CursorSpeed` 和 `WheelSpeed` 属性。</span><span class="sxs-lookup"><span data-stu-id="019a2-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="019a2-327">这些属性允许应用程序指定一个乘数值，通过该值，可分别缩放光标和滚轮的速度。</span><span class="sxs-lookup"><span data-stu-id="019a2-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="019a2-328">这是一项重大更改，需要修改现有的鼠标设备管理器实现。</span><span class="sxs-lookup"><span data-stu-id="019a2-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="019a2-329">此更改与版本2.0.0 不向后兼容。</span><span class="sxs-lookup"><span data-stu-id="019a2-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="019a2-330">**_弃用_**</span><span class="sxs-lookup"><span data-stu-id="019a2-330">**_Deprecated_**</span></span>

<span data-ttu-id="019a2-331">该 `MouseInputProfile` 属性已标记为过时，并将从 Microsoft 混合现实工具包的未来版本中删除。</span><span class="sxs-lookup"><span data-stu-id="019a2-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="019a2-332">建议应用程序代码不再使用此属性。</span><span class="sxs-lookup"><span data-stu-id="019a2-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="019a2-333">**可交互**</span><span class="sxs-lookup"><span data-stu-id="019a2-333">**Interactable**</span></span>

<span data-ttu-id="019a2-334">以下方法和属性已弃用，并将从 Microsoft 混合现实工具包的未来版本中删除。</span><span class="sxs-lookup"><span data-stu-id="019a2-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="019a2-335">建议按过时属性中包含的指南更新应用程序代码，并将其显示在控制台中。</span><span class="sxs-lookup"><span data-stu-id="019a2-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

<span data-ttu-id="019a2-336">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="019a2-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="019a2-337">`NearInteractionTouchableSurface`类已添加，现在用作和的基类 `NearInteractionTouchable` `NearInteractionTouchableUnityUI` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="019a2-338">2.1.0 中的配置文件更改</span><span class="sxs-lookup"><span data-stu-id="019a2-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="019a2-339">**手动跟踪配置文件**</span><span class="sxs-lookup"><span data-stu-id="019a2-339">**Hand tracking profile**</span></span>

<span data-ttu-id="019a2-340">手写网格和联合可视化效果现在具有单独的编辑器和播放机设置。</span><span class="sxs-lookup"><span data-stu-id="019a2-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="019a2-341">手动跟踪配置文件已更新为允许将这些可视化效果设置为;所有内容、编辑器或播放机。</span><span class="sxs-lookup"><span data-stu-id="019a2-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![手动可视化模式](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="019a2-343">自定义手动跟踪配置文件可能需要更新才能在版本2.1.0 中正常工作。</span><span class="sxs-lookup"><span data-stu-id="019a2-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="019a2-344">此更改与版本2.0.0 不向后兼容。</span><span class="sxs-lookup"><span data-stu-id="019a2-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="019a2-345">**输入模拟配置文件**</span><span class="sxs-lookup"><span data-stu-id="019a2-345">**Input simulation profile**</span></span>

<span data-ttu-id="019a2-346">已升级输入模拟系统，这将更改输入模拟配置文件中的几个设置。</span><span class="sxs-lookup"><span data-stu-id="019a2-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="019a2-347">某些更改不能自动迁移，用户可能会发现配置文件正在使用默认值。</span><span class="sxs-lookup"><span data-stu-id="019a2-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="019a2-348">配置文件中的所有 KeyCode 和鼠标按钮绑定都已替换为泛型 `KeyBinding` 结构，该结构存储 (键或鼠标) 的绑定类型，以及分别)  (KeyCode 或鼠标按钮号的实际绑定代码。</span><span class="sxs-lookup"><span data-stu-id="019a2-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="019a2-349">结构具有自己的检查器，它允许统一显示，并提供 "自动绑定" 工具，通过按相应的键来快速设置键绑定，而不是从大下拉列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="019a2-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="019a2-350">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="019a2-350">FastControlKey</span></span>
    - <span data-ttu-id="019a2-351">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="019a2-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="019a2-352">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="019a2-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="019a2-353">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="019a2-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="019a2-354">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="019a2-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="019a2-355">`MouseLookToggle` 先前作为枚举包含在中 `MouseLookButton` `InputSimulationMouseButton.Focused` ，它现在是一个单独的选项。</span><span class="sxs-lookup"><span data-stu-id="019a2-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="019a2-356">启用后，照相机会在松开按钮后一直旋转鼠标，直到按下 esc 键。</span><span class="sxs-lookup"><span data-stu-id="019a2-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="019a2-357">`HandDepthMultiplier` 从0.1 到0.03 的默认值已降低，可适应对输入模拟进行的某些更改。</span><span class="sxs-lookup"><span data-stu-id="019a2-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="019a2-358">如果在滚动时相机移动速度太快，请尝试降低此值。</span><span class="sxs-lookup"><span data-stu-id="019a2-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="019a2-359">旋转的键已被移除，手动旋转现在也由鼠标控制。</span><span class="sxs-lookup"><span data-stu-id="019a2-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="019a2-360">按住 `HandRotateButton` (Ctrl) ，同时 (LShift/Space) 将启用手写旋转。</span><span class="sxs-lookup"><span data-stu-id="019a2-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="019a2-361">已将新的 "UpDown" 轴引入到输入轴列表。</span><span class="sxs-lookup"><span data-stu-id="019a2-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="019a2-362">这会控制垂直方向的相机运动，默认值为 Q/E 键以及控制器触发器按钮。</span><span class="sxs-lookup"><span data-stu-id="019a2-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="019a2-363">有关这些更改的详细信息，请参阅 [输入模拟服务](../features/input-simulation/input-simulation-service.md) 一文。</span><span class="sxs-lookup"><span data-stu-id="019a2-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="019a2-364">**鼠标数据提供程序配置文件**</span><span class="sxs-lookup"><span data-stu-id="019a2-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="019a2-365">已更新鼠标数据提供程序配置文件，以公开新的 `CursorSpeed` 和 `WheelSpeed` 属性。</span><span class="sxs-lookup"><span data-stu-id="019a2-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="019a2-366">现有的自定义配置文件将自动提供默认值。</span><span class="sxs-lookup"><span data-stu-id="019a2-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="019a2-367">保存配置文件时，将保留这些新值。</span><span class="sxs-lookup"><span data-stu-id="019a2-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="019a2-368">**控制器映射配置文件**</span><span class="sxs-lookup"><span data-stu-id="019a2-368">**Controller mapping profile**</span></span>

<span data-ttu-id="019a2-369">某些轴和输入类型在2.1.0 中进行了更新，尤其是围绕 OpenVR 平台。</span><span class="sxs-lookup"><span data-stu-id="019a2-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="019a2-370">请确保在升级时选择 **MixedRealityToolkit-> 公用事业-> 更新 > 控制器映射配置文件** 。</span><span class="sxs-lookup"><span data-stu-id="019a2-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="019a2-371">这会更新包含更新的轴和数据的任何自定义控制器映射配置文件，同时使自定义分配的输入操作保持不变。</span><span class="sxs-lookup"><span data-stu-id="019a2-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="019a2-372">将 RC2 更新到2.0。0</span><span class="sxs-lookup"><span data-stu-id="019a2-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="019a2-373">Microsoft Mixed Reality 工具包的 RC2 版本和2.0.0 版本之间发生了更改，可能会影响现有项目。</span><span class="sxs-lookup"><span data-stu-id="019a2-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="019a2-374">本文档介绍这些更改，以及如何将项目更新到2.0.0 版本。</span><span class="sxs-lookup"><span data-stu-id="019a2-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="019a2-375">API 更改</span><span class="sxs-lookup"><span data-stu-id="019a2-375">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="019a2-376">程序集名称更改</span><span class="sxs-lookup"><span data-stu-id="019a2-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="019a2-377">2.0.0 中的 API 更改</span><span class="sxs-lookup"><span data-stu-id="019a2-377">API changes in 2.0.0</span></span>

<span data-ttu-id="019a2-378">从版本 RC2 开始，有许多 API 更改，其中一些可能会破坏现有项目。</span><span class="sxs-lookup"><span data-stu-id="019a2-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="019a2-379">以下各节介绍了 RC2 和2.0.0 版本之间发生的更改。</span><span class="sxs-lookup"><span data-stu-id="019a2-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="019a2-380">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="019a2-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="019a2-381">MixedRealityToolkit 对象上的以下公共属性已弃用。</span><span class="sxs-lookup"><span data-stu-id="019a2-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="019a2-382">`RegisteredMixedRealityServices` 不再包含注册的扩展服务和数据提供程序的集合。</span><span class="sxs-lookup"><span data-stu-id="019a2-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="019a2-383">若要访问扩展服务，请使用 `MixedRealityServiceRegistry.TryGetService<T>` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="019a2-384">若要访问数据访问接口，请将服务实例强制转换为 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 并使用 `GetDataProvider<T>` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="019a2-385">使用 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 或 [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) 而不是已弃用的以下属性</span><span class="sxs-lookup"><span data-stu-id="019a2-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="019a2-386">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="019a2-386">**CoreServices**</span></span>

<span data-ttu-id="019a2-387">[`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)类是在对象中找到的静态系统访问器 (例如： BoundarySystem) 的替换 `MixedRealityToolkit` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="019a2-388">`MixedRealityToolkit`版本2.0.0 中已弃用系统访问器，将在 MRTK 的未来版本中将其删除。</span><span class="sxs-lookup"><span data-stu-id="019a2-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="019a2-389">下面的代码示例演示了旧模式和新模式。</span><span class="sxs-lookup"><span data-stu-id="019a2-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="019a2-390">如果将应用程序更改为使用不同的服务注册机构 (例如：某个试验性服务经理) ，则使用 new CoreSystem 类将确保应用程序代码不需要更新。</span><span class="sxs-lookup"><span data-stu-id="019a2-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="019a2-391">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="019a2-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="019a2-392">如果添加了 IMixedRealityRaycastProvider，则会更改输入系统配置文件。</span><span class="sxs-lookup"><span data-stu-id="019a2-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="019a2-393">如果有自定义配置文件，则在运行应用程序时，可能会收到下图中的错误。</span><span class="sxs-lookup"><span data-stu-id="019a2-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![选择 Raycast 提供程序1](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="019a2-395">若要解决这些问题，请将 IMixedRealityRaycastProvider 实例添加到输入系统配置文件。</span><span class="sxs-lookup"><span data-stu-id="019a2-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![选择 Raycast provider 2](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="019a2-397">**事件系统**</span><span class="sxs-lookup"><span data-stu-id="019a2-397">**Event System**</span></span>

- <span data-ttu-id="019a2-398">`IMixedRealityEventSystem`旧的 API 方法 `Register` 和已 `Unregister` 标记为过时。</span><span class="sxs-lookup"><span data-stu-id="019a2-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="019a2-399">保留它们是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="019a2-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="019a2-400">`InputSystemGlobalListener` 已标记为过时。</span><span class="sxs-lookup"><span data-stu-id="019a2-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="019a2-401">其功能未发生更改。</span><span class="sxs-lookup"><span data-stu-id="019a2-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="019a2-402">`BaseInputHandler` 基类已从更改 `InputSystemGlobalListener` 为 `InputSystemGlobalHandlerListener` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="019a2-403">这是的任何后代的重大更改 `BaseInputHandler` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="019a2-404">**_变化背后的动机_**</span><span class="sxs-lookup"><span data-stu-id="019a2-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="019a2-405">旧的事件系统 API `Register` 可能 `Unregister` 会导致运行时出现多个问题，主要是：</span><span class="sxs-lookup"><span data-stu-id="019a2-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="019a2-406">如果组件注册全局事件，则它将接收 *所有* 类型的全局输入事件。</span><span class="sxs-lookup"><span data-stu-id="019a2-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="019a2-407">如果对象上的组件之一注册全局输入事件，则此对象上的所有组件都将接收 *所有* 类型的全局输入事件。</span><span class="sxs-lookup"><span data-stu-id="019a2-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="019a2-408">如果同一对象上的两个组件注册到全局事件，然后在运行时中有一个处于禁用状态，则第二个组件将停止接收全局事件。</span><span class="sxs-lookup"><span data-stu-id="019a2-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="019a2-409">新 `RegisterHandler` 的 API 和 `UnregisterHandler` ：</span><span class="sxs-lookup"><span data-stu-id="019a2-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="019a2-410">提供对应全局侦听哪些输入事件以及哪些应基于焦点的输入事件进行显式和精细的控制。</span><span class="sxs-lookup"><span data-stu-id="019a2-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="019a2-411">允许同一对象上的多个组件彼此独立地侦听全局事件。</span><span class="sxs-lookup"><span data-stu-id="019a2-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="019a2-412">**_如何迁移_**</span><span class="sxs-lookup"><span data-stu-id="019a2-412">**_How to migrate_**</span></span>

- <span data-ttu-id="019a2-413">如果你以前直接调用了 `Register` / `Unregister` API，请将这些调用替换为对的调用 `RegisterHandler` / `UnregisterHandler` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="019a2-414">使用实现为泛型参数的处理程序接口。</span><span class="sxs-lookup"><span data-stu-id="019a2-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="019a2-415">如果实现多个接口，并且其中几个接口侦听全局输入事件，则调用多次 `RegisterHandler` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="019a2-416">如果已从继承 `InputSystemGlobalListener` ，请将继承更改为 `InputSystemGlobalHandlerListener` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="019a2-417">实现 `RegisterHandlers` 和 `UnregisterHandlers` 抽象方法。</span><span class="sxs-lookup"><span data-stu-id="019a2-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="019a2-418">在实现调用中 `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) 在要侦听其全局事件的所有处理程序接口上进行注册。</span><span class="sxs-lookup"><span data-stu-id="019a2-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="019a2-419">如果已从继承，则 `BaseInputHandler` 实现 `RegisterHandlers` 和 `UnregisterHandlers` 抽象方法 (与 `InputSystemGlobalListener`) 相同。</span><span class="sxs-lookup"><span data-stu-id="019a2-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="019a2-420">**_迁移示例_**</span><span class="sxs-lookup"><span data-stu-id="019a2-420">**_Examples of migration_**</span></span>

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

<span data-ttu-id="019a2-421">**空间感知**</span><span class="sxs-lookup"><span data-stu-id="019a2-421">**Spatial Awareness**</span></span>

<span data-ttu-id="019a2-422">IMixedRealitySpatialAwarenessSystem 和 IMixedRealitySpatialAwarenessObserver 接口发生了多个重大更改，如下所述。</span><span class="sxs-lookup"><span data-stu-id="019a2-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="019a2-423">**_更改_**</span><span class="sxs-lookup"><span data-stu-id="019a2-423">**_Changes_**</span></span>

<span data-ttu-id="019a2-424">已重命名了以下方法 () ，以更好地描述其使用情况。</span><span class="sxs-lookup"><span data-stu-id="019a2-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="019a2-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` 已将重命名为， `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` 以明确其用法。</span><span class="sxs-lookup"><span data-stu-id="019a2-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="019a2-426">**_新增内容_**</span><span class="sxs-lookup"><span data-stu-id="019a2-426">**_Additions_**</span></span>

<span data-ttu-id="019a2-427">根据客户反馈，增加了对以前观察到的空间意识数据的轻松删除的支持。</span><span class="sxs-lookup"><span data-stu-id="019a2-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="019a2-428">**求解器**</span><span class="sxs-lookup"><span data-stu-id="019a2-428">**Solvers**</span></span>

<span data-ttu-id="019a2-429">某些规划求解组件和 SolverHandler manager 类已更改，可修复各种 bug，并获得更直观的用法。</span><span class="sxs-lookup"><span data-stu-id="019a2-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="019a2-430">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="019a2-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="019a2-431">类不再从扩展 `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="019a2-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="019a2-432">`TrackedObjectToReference` 公共属性已弃用，已重命名为 `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="019a2-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="019a2-433">`TrackedObjectType` 弃用左 & 右控制器值。</span><span class="sxs-lookup"><span data-stu-id="019a2-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="019a2-434">改为使用 `MotionController` 或 `HandJoint` 值，并更新新 `TrackedHandedness` 属性以将跟踪限制为左或右控制器</span><span class="sxs-lookup"><span data-stu-id="019a2-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="019a2-435">**_Receivebegindoc_**</span><span class="sxs-lookup"><span data-stu-id="019a2-435">**_InBetween_**</span></span>

- <span data-ttu-id="019a2-436">`TrackedObjectForSecondTransform` 公共属性已弃用，已重命名为 `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="019a2-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="019a2-437">`AttachSecondTransformToNewTrackedObject()` 已删除。</span><span class="sxs-lookup"><span data-stu-id="019a2-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="019a2-438">若要更新规划求解，请修改公共属性 (即</span><span class="sxs-lookup"><span data-stu-id="019a2-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="019a2-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="019a2-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="019a2-440">**_SurfaceMagnetism_**</span><span class="sxs-lookup"><span data-stu-id="019a2-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="019a2-441">`MaxDistance` 公共属性已弃用，已重命名为 `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="019a2-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="019a2-442">`CloseDistance` 公共属性已弃用，已重命名为 `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="019a2-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="019a2-443">的默认值 `RaycastDirectionMode` 现在 `TrackedTargetForward` raycasts 跟踪的目标转换的方向</span><span class="sxs-lookup"><span data-stu-id="019a2-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="019a2-444">`OrientationMode` 枚举值 `Vertical` 和 `Full` ，分别重命名为 `TrackedTarget` 和 `SurfaceNormal` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="019a2-445">`KeepOrientationVertical` 添加了公共属性，用于控制是否将相关 GameObject 的方向保持垂直</span><span class="sxs-lookup"><span data-stu-id="019a2-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="019a2-446">**按钮**</span><span class="sxs-lookup"><span data-stu-id="019a2-446">**Buttons**</span></span>

- <span data-ttu-id="019a2-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 现在已 `DistanceSpaceMode` 将属性设置为 `Local` 默认值。</span><span class="sxs-lookup"><span data-stu-id="019a2-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="019a2-448">这允许在仍 pressable 的情况下缩放按钮</span><span class="sxs-lookup"><span data-stu-id="019a2-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="019a2-449">**剪切球**</span><span class="sxs-lookup"><span data-stu-id="019a2-449">**Clipping Sphere**</span></span>

<span data-ttu-id="019a2-450">ClippingSphere 接口已更改为镜像在 ClippingBox 和 ClippingPlane 中找到的 Api。</span><span class="sxs-lookup"><span data-stu-id="019a2-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="019a2-451">现在，ClippingSphere 的 Radius 属性基于转换比例进行隐式计算。</span><span class="sxs-lookup"><span data-stu-id="019a2-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="019a2-452">开发人员必须在检查器中指定 ClippingSphere 的半径。</span><span class="sxs-lookup"><span data-stu-id="019a2-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="019a2-453">如果要更改 radius，只需像往常一样更新转换的转换比例。</span><span class="sxs-lookup"><span data-stu-id="019a2-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="019a2-454">**NearInteractionTouchable 和 PokePointer**</span><span class="sxs-lookup"><span data-stu-id="019a2-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="019a2-455">NearInteractionTouchable 不会再处理 Unity UI 画布。</span><span class="sxs-lookup"><span data-stu-id="019a2-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="019a2-456">NearInteractionTouchableUnityUI 类必须立即用于 Unity UI touchables。</span><span class="sxs-lookup"><span data-stu-id="019a2-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="019a2-457">ColliderNearInteractionTouchable 是基于 colliders 的 touchables （即每个可触摸除外）的新基类。</span><span class="sxs-lookup"><span data-stu-id="019a2-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="019a2-458">BaseNearInteractionTouchable 已移动，并已重命名为 PokePointer。 TouchableDistance 这是 PokePointer 可以与 touchables 交互的距离。</span><span class="sxs-lookup"><span data-stu-id="019a2-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="019a2-459">之前，每个可触摸都有其自己的最大交互距离，但现在这是在 PokePointer 中定义的，它可以更好地进行优化。</span><span class="sxs-lookup"><span data-stu-id="019a2-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="019a2-460">BaseNearInteractionTouchable 已将 DistBack 重命名为 PokeThreshold，这使得 PokeThreshold 是 DebounceThreshold 的对应项。</span><span class="sxs-lookup"><span data-stu-id="019a2-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="019a2-461">当超过 PokeThreshold 时，将激活可触摸，并在超过 DebounceThreshold 后释放。</span><span class="sxs-lookup"><span data-stu-id="019a2-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="019a2-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="019a2-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="019a2-463">`Microsoft.MixedReality.Toolkit`命名空间已添加到 `ReadOnlyAttribute` 、 `BeginReadOnlyGroupAttribute` 和 `EndReadOnlyGroupAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="019a2-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="019a2-464">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="019a2-464">**PointerClickHandler**</span></span>

<span data-ttu-id="019a2-465">`PointerClickHandler` 类已弃用。</span><span class="sxs-lookup"><span data-stu-id="019a2-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="019a2-466">`PointerHandler`应改用，它提供相同的功能。</span><span class="sxs-lookup"><span data-stu-id="019a2-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="019a2-467">**HoloLens clicker 支持**</span><span class="sxs-lookup"><span data-stu-id="019a2-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="019a2-468">HoloLens clicker 的控制器映射已从 unhanded 更改 [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) 为 unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) 。</span><span class="sxs-lookup"><span data-stu-id="019a2-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="019a2-469">为此，将在首次打开 ControllerMapping 配置文件时运行自动更新程序。</span><span class="sxs-lookup"><span data-stu-id="019a2-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="019a2-470">升级到2.0.0 后，请至少打开一次自定义配置文件，以便触发此一次性迁移步骤。</span><span class="sxs-lookup"><span data-stu-id="019a2-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="019a2-471">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="019a2-471">**InteractableHighlight**</span></span>

<span data-ttu-id="019a2-472">`InteractableHighlight` 类已弃用。</span><span class="sxs-lookup"><span data-stu-id="019a2-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="019a2-473">`InteractableOnFocus` `FocusInteractableStates` 应改用类和资产。</span><span class="sxs-lookup"><span data-stu-id="019a2-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="019a2-474">若要为创建新 `Theme` 资产 `InteractableOnFocus` ，请在项目窗口中右键单击，然后选择 "*创建*  >  *混合现实工具包*  >  *种不可交互*  >  *主题*"。</span><span class="sxs-lookup"><span data-stu-id="019a2-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="019a2-475">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="019a2-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="019a2-476">`HandInteractionPanZoom` 已移至 UI 命名空间，因为它不是输入组件。</span><span class="sxs-lookup"><span data-stu-id="019a2-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="019a2-477">`HandPanEventData` 已移动到此命名空间中，并进行了简化以与其他 UI 事件数据相对应。</span><span class="sxs-lookup"><span data-stu-id="019a2-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="019a2-478">2.0.0 中的程序集名称更改</span><span class="sxs-lookup"><span data-stu-id="019a2-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="019a2-479">在2.0.0 版本中，所有官方混合现实工具包程序集名称及其关联的程序集定义 (。 asmdef) 文件已更新为适合以下模式。</span><span class="sxs-lookup"><span data-stu-id="019a2-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="019a2-480">在某些情况下，已合并多个程序集，以创建更好的内容。</span><span class="sxs-lookup"><span data-stu-id="019a2-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="019a2-481">如果项目使用 asmdef 文件，可能需要更新。</span><span class="sxs-lookup"><span data-stu-id="019a2-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="019a2-482">下表描述了 RC2 asmdef 文件名如何映射到2.0.0 版本。</span><span class="sxs-lookup"><span data-stu-id="019a2-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="019a2-483">所有程序集名称均与 asmdef 文件名匹配。</span><span class="sxs-lookup"><span data-stu-id="019a2-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="019a2-484">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="019a2-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="019a2-485">RC2</span><span class="sxs-lookup"><span data-stu-id="019a2-485">RC2</span></span> | <span data-ttu-id="019a2-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="019a2-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="019a2-487">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="019a2-488">MixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="019a2-489">MixedRealityToolkit. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="019a2-490">MixedReality. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="019a2-491">MixedRealityToolkit. asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="019a2-492">删除，请使用 MixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="019a2-493">MixedRealityToolkit. EditorClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="019a2-494">MixedReality. ClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="019a2-495">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="019a2-496">MixedReality. 检查器 asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="019a2-497">MixedRealityToolkit. ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="019a2-498">MixedReality. ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="019a2-499">MixedRealityToolkit. UtilitiesAsync. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="019a2-500">MixedReality. asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="019a2-501">MixedRealityToolkit. asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="019a2-502">MixedReality. asmdef 中的</span><span class="sxs-lookup"><span data-stu-id="019a2-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="019a2-503">MixedRealityToolkit. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="019a2-504">MixedReality. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="019a2-505">MixedRealityToolkit. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="019a2-506">MixedReality. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="019a2-507">**MixedRealityToolkit 提供程序**</span><span class="sxs-lookup"><span data-stu-id="019a2-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="019a2-508">RC2</span><span class="sxs-lookup"><span data-stu-id="019a2-508">RC2</span></span> | <span data-ttu-id="019a2-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="019a2-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="019a2-510">MixedRealityToolkit. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="019a2-511">MixedReality. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="019a2-512">MixedRealityToolkit. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="019a2-513">MixedReality. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="019a2-514">MixedRealityToolkit. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="019a2-515">MixedReality. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="019a2-516">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="019a2-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="019a2-517">RC2</span><span class="sxs-lookup"><span data-stu-id="019a2-517">RC2</span></span> | <span data-ttu-id="019a2-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="019a2-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="019a2-519">MixedRealityToolkit. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="019a2-520">MixedReality. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="019a2-521">MixedRealityToolkit. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="019a2-522">MixedReality. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="019a2-523">MixedRealityToolkit. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="019a2-524">MixedReality. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="019a2-525">MixedRealityToolkit. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="019a2-526">MixedReality. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="019a2-527">MixedRealityToolkit. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="019a2-528">MixedReality. InputSimulation. asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="019a2-529">MixedRealityToolkit. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="019a2-530">MixedReality. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="019a2-531">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="019a2-532">MixedReality. InputSystem. asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="019a2-533">MixedRealityToolkit. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="019a2-534">MixedReality. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="019a2-535">MixedRealityToolkit. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="019a2-536">MixedReality. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="019a2-537">MixedRealityToolkit. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="019a2-538">MixedReality. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="019a2-539">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="019a2-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="019a2-540">RC2</span><span class="sxs-lookup"><span data-stu-id="019a2-540">RC2</span></span> | <span data-ttu-id="019a2-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="019a2-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="019a2-542">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="019a2-543">MixedReality. asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="019a2-544">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="019a2-545">MixedReality.. asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="019a2-546">**MixedRealityToolkit 示例**</span><span class="sxs-lookup"><span data-stu-id="019a2-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="019a2-547">RC2</span><span class="sxs-lookup"><span data-stu-id="019a2-547">RC2</span></span> | <span data-ttu-id="019a2-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="019a2-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="019a2-549">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="019a2-550">MixedReality. asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="019a2-551">MixedRealityToolkit. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="019a2-552">MixedReality. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="019a2-553">MixedRealityToolkit. StandardShader. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="019a2-554">MixedReality. StandardShader asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="019a2-555">MixedRealityToolkit. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="019a2-556">MixedReality. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="019a2-557">MixedRealityToolkit. InspectorFields. asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="019a2-558">MixedReality. InspectorFields asmdef。</span><span class="sxs-lookup"><span data-stu-id="019a2-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="019a2-559">MixedRealityToolkit. Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="019a2-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="019a2-560">MixedReality. asmdef. Interactables。</span><span class="sxs-lookup"><span data-stu-id="019a2-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |