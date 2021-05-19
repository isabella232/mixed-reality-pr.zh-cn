---
title: 迁移窗口
description: 有关如何在 MRTK 中迁移到更新的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 8e03848097c313a518f638de591f692ab71f0985
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143877"
---
# <a name="migration-window"></a><span data-ttu-id="e0b88-104">迁移时限</span><span class="sxs-lookup"><span data-stu-id="e0b88-104">Migration window</span></span>

<span data-ttu-id="e0b88-105">当 MRTK 发生变化时，某些组件可能会被弃用，并且会引入替换内容。</span><span class="sxs-lookup"><span data-stu-id="e0b88-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="e0b88-106">"迁移" 窗口是一种工具，可帮助用户自动将这些不推荐使用的部分的子集迁移到新的替换项。</span><span class="sxs-lookup"><span data-stu-id="e0b88-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![迁移时限](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="e0b88-108">使用情况</span><span class="sxs-lookup"><span data-stu-id="e0b88-108">Usage</span></span>

<span data-ttu-id="e0b88-109">若要打开该窗口，请选择 "*混合现实工具包*  >  *实用工具*  >  *迁移" 窗口*。</span><span class="sxs-lookup"><span data-stu-id="e0b88-109">To open the window, select *Mixed Reality Toolkit* > *Utilities* > *Migration Window*.</span></span> <span data-ttu-id="e0b88-110">在迁移窗口打开后，可以通过选择迁移处理程序的特定于组件的实现来启用选择模式导航选项卡。</span><span class="sxs-lookup"><span data-stu-id="e0b88-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![迁移选择模式](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="e0b88-112">对象模式</span><span class="sxs-lookup"><span data-stu-id="e0b88-112">Object mode</span></span>

<span data-ttu-id="e0b88-113">选择 "对象" 选项卡后，用户可以在其中将 "对象" 字段拖放到要迁移的项目文件夹中当前打开的场景或 prototyping 中的任何游戏对象。</span><span class="sxs-lookup"><span data-stu-id="e0b88-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="e0b88-114">按所列对象右侧显示的 "删除 *( )* " 按钮将从选择列表中删除该对象。</span><span class="sxs-lookup"><span data-stu-id="e0b88-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="e0b88-115">所有所需的对象都在列表中后，按 " *迁移* " 按钮会将所选迁移处理程序实现所需的更改应用于所选内容中与实现匹配的所有组件。</span><span class="sxs-lookup"><span data-stu-id="e0b88-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![选择迁移](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="e0b88-117">场景模式</span><span class="sxs-lookup"><span data-stu-id="e0b88-117">Scene mode</span></span>

<span data-ttu-id="e0b88-118">允许用户拖放包含要迁移的对象的场景资产。</span><span class="sxs-lookup"><span data-stu-id="e0b88-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![选择用于迁移的场景](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="e0b88-120">项目模式</span><span class="sxs-lookup"><span data-stu-id="e0b88-120">Project mode</span></span>

<span data-ttu-id="e0b88-121">按 " *迁移* " 按钮将为项目中的所有 prototyping 和场景更新迁移处理程序实现的目标组件。</span><span class="sxs-lookup"><span data-stu-id="e0b88-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![迁移完整项目](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="e0b88-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0b88-123">See also</span></span>

- [<span data-ttu-id="e0b88-124">从早期版本更新</span><span class="sxs-lookup"><span data-stu-id="e0b88-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="e0b88-125">Microsoft 混合现实工具包版本</span><span class="sxs-lookup"><span data-stu-id="e0b88-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="e0b88-126">MRTK 路线图</span><span class="sxs-lookup"><span data-stu-id="e0b88-126">MRTK roadmap</span></span>](../../roadmap.md)
