---
title: Unreal 中的 HP 回音 G2 控制器
description: 在 OpenXR 和 SteamVR 中使用 HP 回音 G2 控制器的说明
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal，Unreal Engine 4，UE4，回音，回音 G2，HP 回音 G2，mixed reality，开发，运动控制器，用户输入，功能，新项目，模拟器，文档，指南，功能，全息影像，游戏开发，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 6a56b11e6738dd6359508d0cdfc1560bddfaff2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678926"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="d491c-104">Unreal 中的 HP 回音 G2 控制器</span><span class="sxs-lookup"><span data-stu-id="d491c-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="d491c-105">入门</span><span class="sxs-lookup"><span data-stu-id="d491c-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d491c-106">需要使用 Unreal 引擎4.26 和 OpenXR 或 SteamVR 来访问 HP 运动控制器插件，你需要使用 HP 回音 G2 控制器。</span><span class="sxs-lookup"><span data-stu-id="d491c-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="d491c-107">移植现有的 OpenXR 应用</span><span class="sxs-lookup"><span data-stu-id="d491c-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="d491c-108">如果 HP 混合现实控制器的游戏中不存在控制器绑定，OpenXR 运行时将尝试将现有绑定重新映射到活动控制器。</span><span class="sxs-lookup"><span data-stu-id="d491c-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will attempt to remap the existing bindings to the active controller.</span></span>  <span data-ttu-id="d491c-109">在这种情况下，游戏具有 Oculus Touch 绑定，没有 HP 混合现实控制器绑定。</span><span class="sxs-lookup"><span data-stu-id="d491c-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![在不存在控制器绑定时重新映射现有绑定](images/reverb-g2-img-04.png)

<span data-ttu-id="d491c-111">事件仍将触发，但是如果游戏需要使用控制器特定的绑定（如右菜单按钮），则必须使用 HP 混合现实交互配置文件。</span><span class="sxs-lookup"><span data-stu-id="d491c-111">The events will still fire, but if the game needs to make use of controller specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="d491c-112">可以为每个操作指定多个控制器绑定，以便更好地支持不同的设备。</span><span class="sxs-lookup"><span data-stu-id="d491c-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![使用多控制器绑定](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="d491c-114">添加输入操作映射</span><span class="sxs-lookup"><span data-stu-id="d491c-114">Adding input action mappings</span></span> 

<span data-ttu-id="d491c-115">定义新操作并映射到 "HP Mixed Reality 控制器" 部分中的某个按键。</span><span class="sxs-lookup"><span data-stu-id="d491c-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![定义新操作和映射](images/reverb-g2-img-02.png)

<span data-ttu-id="d491c-117">HP 回音 G2 控制器还具有模拟手柄，可在使用 "挤压轴" 绑定的轴映射中使用。</span><span class="sxs-lookup"><span data-stu-id="d491c-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="d491c-118">有一个单独的压缩绑定，该绑定应在完全按下手柄按钮时用于操作映射。</span><span class="sxs-lookup"><span data-stu-id="d491c-118">There is a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![使用挤轴绑定](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="d491c-120">添加输入事件</span><span class="sxs-lookup"><span data-stu-id="d491c-120">Adding input events</span></span>

<span data-ttu-id="d491c-121">右键单击蓝图，并搜索输入系统中的新操作名称，为这些操作添加事件。</span><span class="sxs-lookup"><span data-stu-id="d491c-121">Right click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="d491c-122">这里，蓝图使用输出当前按钮和轴状态的打印字符串来响应事件。</span><span class="sxs-lookup"><span data-stu-id="d491c-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![蓝图响应事件并输出当前按钮和轴状态](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="d491c-124">使用输入</span><span class="sxs-lookup"><span data-stu-id="d491c-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="d491c-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="d491c-125">See also</span></span>
* [<span data-ttu-id="d491c-126">SteamVR 输入</span><span class="sxs-lookup"><span data-stu-id="d491c-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="d491c-127">将 SteamVR 与 Windows Mixed Reality 一起使用</span><span class="sxs-lookup"><span data-stu-id="d491c-127">Using SteamVR with Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="d491c-128">Unreal Player 相机</span><span class="sxs-lookup"><span data-stu-id="d491c-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)