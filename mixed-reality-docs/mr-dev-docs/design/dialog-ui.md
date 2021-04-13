---
title: 对话框
description: 了解 MRTK 中的对话覆盖，以及如何在混合现实应用程序中使用它们。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合现实，HoloLens，UI 控制，交互，UI，ux，UX 设计，空间 UI，空间交互，三维 UI，三维 UX，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: 18e446f6b35e8073f939d065de3572204e2967a1
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299992"
---
# <a name="dialog"></a><span data-ttu-id="622b6-104">对话框</span><span class="sxs-lookup"><span data-stu-id="622b6-104">Dialog</span></span>

![HoloLens 上显示 "是" 和 "否" 按钮的对话框覆盖屏幕截图](images/MRTK_UX_Dialog.jpg)

<span data-ttu-id="622b6-106">对话框控件是提供上下文应用信息的 UI 覆盖，通常请求用户操作。</span><span class="sxs-lookup"><span data-stu-id="622b6-106">Dialog controls are UI overlays that provide contextual app information, often requesting a user action.</span></span> <span data-ttu-id="622b6-107">在完成操作之前，请使用对话向用户授予重要信息并请求确认或附加信息。</span><span class="sxs-lookup"><span data-stu-id="622b6-107">Use dialogs to give users important information and request confirmation or extra information before an action can be completed.</span></span>

<br>

---

## <a name="dialog-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="622b6-108">MRTK 中的对话框 (适用于 Unity 的混合现实工具包) </span><span class="sxs-lookup"><span data-stu-id="622b6-108">Dialog in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="622b6-109">MRTK 提供了三种大小的对话框控件，其中包含一个或两个按钮选项。</span><span class="sxs-lookup"><span data-stu-id="622b6-109">MRTK provides dialog control in three sizes with one or two button options.</span></span> <span data-ttu-id="622b6-110">您还可以为近或远交互范围指定放置距离。</span><span class="sxs-lookup"><span data-stu-id="622b6-110">You can also specify the placement distance for near or far interaction range.</span></span> 

- <span data-ttu-id="622b6-111">DialogSmall_192x96： prefab：192x96mm</span><span class="sxs-lookup"><span data-stu-id="622b6-111">DialogSmall_192x96.prefab: 192x96mm</span></span>
- <span data-ttu-id="622b6-112">DialogMedium_192x128： prefab：192x128mm</span><span class="sxs-lookup"><span data-stu-id="622b6-112">DialogMedium_192x128.prefab: 192x128mm</span></span>
- <span data-ttu-id="622b6-113">DialogLarge_192x192： prefab：192x192mm</span><span class="sxs-lookup"><span data-stu-id="622b6-113">DialogLarge_192x192.prefab: 192x192mm</span></span>

![在 HoloLens 上运行的不同大小对话框覆盖的屏幕截图](images/MRTK_UX_Dialog_Types.jpg)


* <span data-ttu-id="622b6-115">有关详细信息，请参阅 [MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)。</span><span class="sxs-lookup"><span data-stu-id="622b6-115">For more information, see [MRTK - Dialog](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="622b6-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="622b6-116">See also</span></span>

* [<span data-ttu-id="622b6-117">光标</span><span class="sxs-lookup"><span data-stu-id="622b6-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="622b6-118">手部射线</span><span class="sxs-lookup"><span data-stu-id="622b6-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="622b6-119">Button</span><span class="sxs-lookup"><span data-stu-id="622b6-119">Button</span></span>](button.md)
* [<span data-ttu-id="622b6-120">可交互对象</span><span class="sxs-lookup"><span data-stu-id="622b6-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="622b6-121">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="622b6-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="622b6-122">操作</span><span class="sxs-lookup"><span data-stu-id="622b6-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="622b6-123">手动菜单</span><span class="sxs-lookup"><span data-stu-id="622b6-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="622b6-124">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="622b6-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="622b6-125">对象集合</span><span class="sxs-lookup"><span data-stu-id="622b6-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="622b6-126">语音命令</span><span class="sxs-lookup"><span data-stu-id="622b6-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="622b6-127">键盘</span><span class="sxs-lookup"><span data-stu-id="622b6-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="622b6-128">工具提示</span><span class="sxs-lookup"><span data-stu-id="622b6-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="622b6-129">平板</span><span class="sxs-lookup"><span data-stu-id="622b6-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="622b6-130">滑块</span><span class="sxs-lookup"><span data-stu-id="622b6-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="622b6-131">着色器</span><span class="sxs-lookup"><span data-stu-id="622b6-131">Shader</span></span>](shader.md)
* [<span data-ttu-id="622b6-132">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="622b6-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="622b6-133">显示进度</span><span class="sxs-lookup"><span data-stu-id="622b6-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="622b6-134">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="622b6-134">Surface magnetism</span></span>](surface-magnetism.md)
