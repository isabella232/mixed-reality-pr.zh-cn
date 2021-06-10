---
title: 对话框
description: 了解 MRTK 中的对话覆盖，以及如何在混合现实应用程序中使用它们。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合现实， HoloLens， UI 控件， 交互， ui， ux， UX 设计， 空间 UI， 空间交互， 3D UI， 3D UX， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包
ms.openlocfilehash: aa85402f765e8b02842054db0c2fb37ca4fa9d93
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600306"
---
# <a name="dialog"></a><span data-ttu-id="71968-104">对话框</span><span class="sxs-lookup"><span data-stu-id="71968-104">Dialog</span></span>

![显示"是"且 HoloLens 上未显示任何按钮的对话覆盖的屏幕截图](images/MRTK_UX_Dialog.jpg)

<span data-ttu-id="71968-106">对话框控件是 UI 覆盖，提供上下文应用信息，通常请求用户操作。</span><span class="sxs-lookup"><span data-stu-id="71968-106">Dialog controls are UI overlays that provide contextual app information, often requesting a user action.</span></span> <span data-ttu-id="71968-107">使用对话框为用户提供重要信息，并请求确认或额外信息，然后才能完成操作。</span><span class="sxs-lookup"><span data-stu-id="71968-107">Use dialogs to give users important information and request confirmation or extra information before an action can be completed.</span></span>

<br>

---

## <a name="dialog-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="71968-108">适用于 Unity 的混合现实工具包 (MRTK) 对话</span><span class="sxs-lookup"><span data-stu-id="71968-108">Dialog in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="71968-109">MRTK 提供三种大小的对话框控件，以及一个或两个按钮选项。</span><span class="sxs-lookup"><span data-stu-id="71968-109">MRTK provides dialog control in three sizes with one or two button options.</span></span> <span data-ttu-id="71968-110">还可以指定近距或远距交互范围的放置距离。</span><span class="sxs-lookup"><span data-stu-id="71968-110">You can also specify the placement distance for near or far interaction range.</span></span> 

- <span data-ttu-id="71968-111">DialogSmall_192x96.prefab：192x96mm</span><span class="sxs-lookup"><span data-stu-id="71968-111">DialogSmall_192x96.prefab: 192x96mm</span></span>
- <span data-ttu-id="71968-112">DialogMedium_192x128.prefab：192x128mm</span><span class="sxs-lookup"><span data-stu-id="71968-112">DialogMedium_192x128.prefab: 192x128mm</span></span>
- <span data-ttu-id="71968-113">DialogLarge_192x192.prefab：192x192mm</span><span class="sxs-lookup"><span data-stu-id="71968-113">DialogLarge_192x192.prefab: 192x192mm</span></span>

![HoloLens 上运行的不同大小的对话框覆盖的屏幕截图](images/MRTK_UX_Dialog_Types.jpg)


* <span data-ttu-id="71968-115">有关详细信息，请参阅 [MRTK - 对话框](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)。</span><span class="sxs-lookup"><span data-stu-id="71968-115">For more information, see [MRTK - Dialog](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="71968-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71968-116">See also</span></span>

* [<span data-ttu-id="71968-117">光标</span><span class="sxs-lookup"><span data-stu-id="71968-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="71968-118">手部射线</span><span class="sxs-lookup"><span data-stu-id="71968-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="71968-119">Button</span><span class="sxs-lookup"><span data-stu-id="71968-119">Button</span></span>](button.md)
* [<span data-ttu-id="71968-120">可交互对象</span><span class="sxs-lookup"><span data-stu-id="71968-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="71968-121">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="71968-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="71968-122">操作</span><span class="sxs-lookup"><span data-stu-id="71968-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="71968-123">手动菜单</span><span class="sxs-lookup"><span data-stu-id="71968-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="71968-124">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="71968-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="71968-125">对象集合</span><span class="sxs-lookup"><span data-stu-id="71968-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="71968-126">语音命令</span><span class="sxs-lookup"><span data-stu-id="71968-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="71968-127">键盘</span><span class="sxs-lookup"><span data-stu-id="71968-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="71968-128">工具提示</span><span class="sxs-lookup"><span data-stu-id="71968-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="71968-129">平板</span><span class="sxs-lookup"><span data-stu-id="71968-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="71968-130">滑块</span><span class="sxs-lookup"><span data-stu-id="71968-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="71968-131">着色器</span><span class="sxs-lookup"><span data-stu-id="71968-131">Shader</span></span>](shader.md)
* [<span data-ttu-id="71968-132">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="71968-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="71968-133">显示进度</span><span class="sxs-lookup"><span data-stu-id="71968-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="71968-134">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="71968-134">Surface magnetism</span></span>](surface-magnetism.md)