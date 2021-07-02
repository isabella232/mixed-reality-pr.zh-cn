---
title: 应用栏
description: MRTK 中的应用栏概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 应用栏，
ms.openlocfilehash: 3c8633d91b2c26f8bdc774a98b2cb48ffb276720
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175693"
---
# <a name="app-bar"></a><span data-ttu-id="f5bb4-104">应用栏</span><span class="sxs-lookup"><span data-stu-id="f5bb4-104">App bar</span></span>

![应用栏](../images/app-bar/MRTK_AppBar_Main.png)

<span data-ttu-id="f5bb4-106">应用栏是一个 UI 组件，与 [边界控件脚本一起](bounds-control.md) 使用。</span><span class="sxs-lookup"><span data-stu-id="f5bb4-106">App bar is a UI component that is used together with the [bounds control](bounds-control.md) script.</span></span> <span data-ttu-id="f5bb4-107">它将按钮控件添加到对象，并意图对其进行操作。</span><span class="sxs-lookup"><span data-stu-id="f5bb4-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="f5bb4-108">使用"调整"按钮，可以取消/激活对象的边界控制接口。</span><span class="sxs-lookup"><span data-stu-id="f5bb4-108">Using the 'Adjust' button, the bounds control interface for an object can be de- / activated.</span></span> <span data-ttu-id="f5bb4-109">"删除"按钮应从场景中删除对象。</span><span class="sxs-lookup"><span data-stu-id="f5bb4-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="f5bb4-110">如何使用应用栏</span><span class="sxs-lookup"><span data-stu-id="f5bb4-110">How to use app bar</span></span>

<span data-ttu-id="f5bb4-111">将 `AppBar` " (assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) 拖放到场景层次结构中。</span><span class="sxs-lookup"><span data-stu-id="f5bb4-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="f5bb4-112">在组件的检查器面板中，分配具有边界控件的任何对象作为目标 *边界框* ，以将应用栏添加到其中。</span><span class="sxs-lookup"><span data-stu-id="f5bb4-112">In the inspector panel of the component, assign any object with a bounds control as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="f5bb4-113">**重要提示：** 目标对象的边界控制激活选项应为"手动激活"。</span><span class="sxs-lookup"><span data-stu-id="f5bb4-113">**Important:** The bounds control activation option for the target object should be 'Activate Manually'.</span></span>

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
