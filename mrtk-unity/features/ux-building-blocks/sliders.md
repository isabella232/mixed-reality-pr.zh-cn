---
title: 滑块
description: 滑杆 MRTK 概述
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，滑杆，
ms.openlocfilehash: be19806e0202f6cb3ddcea1a80c2c40811aff4f2
ms.sourcegitcommit: e9661d3bab061f9499134226ef3b87751ec56277
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2021
ms.locfileid: "112426873"
---
# <a name="sliders"></a><span data-ttu-id="16020-104">滑块</span><span class="sxs-lookup"><span data-stu-id="16020-104">Sliders</span></span>

![滑块示例](../images/slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="16020-106">滑块是用户界面组件，使您可以通过将滑块移动到轨道上来持续更改值。目前，可以通过直接或距离方向直接抓取滑块来移动挤压滑块。</span><span class="sxs-lookup"><span data-stu-id="16020-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="16020-107">滑块在 AR 和 VR 上工作，使用运动控制器、手或手势 + 语音。</span><span class="sxs-lookup"><span data-stu-id="16020-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="16020-108">示例场景</span><span class="sxs-lookup"><span data-stu-id="16020-108">Example scene</span></span>

<span data-ttu-id="16020-109">可以在中的 **SliderExample** 场景中找到示例 `MRTK/Examples/Demos/UX/Slider/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="16020-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="16020-110">如何使用滑块</span><span class="sxs-lookup"><span data-stu-id="16020-110">How to use sliders</span></span>

<span data-ttu-id="16020-111">将 **PinchSlider** prefab 拖放到场景层次结构中。</span><span class="sxs-lookup"><span data-stu-id="16020-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="16020-112">如果要修改或创建自己的滑块，请记住执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="16020-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="16020-113">请确保拇指对象上有一个碰撞器。</span><span class="sxs-lookup"><span data-stu-id="16020-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="16020-114">在 PinchSlider prefab 中，碰撞器位于 `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="16020-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="16020-115">如果你希望能够抓住附近的滑块，请确保包含碰撞器的对象在其上还有近乎交互的 Grabbable 组件。</span><span class="sxs-lookup"><span data-stu-id="16020-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="16020-116">我们还建议使用以下层次结构</span><span class="sxs-lookup"><span data-stu-id="16020-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="16020-117">PinchSlider-包含 sliderComponent</span><span class="sxs-lookup"><span data-stu-id="16020-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="16020-118">TouchCollider-包含滑块的整个可选择区域的碰撞器。</span><span class="sxs-lookup"><span data-stu-id="16020-118">TouchCollider - Collider containing the entire selectable area of the slider.</span></span> <span data-ttu-id="16020-119">启用 "对齐位置" 行为。</span><span class="sxs-lookup"><span data-stu-id="16020-119">Enables the Snap To Position behavior.</span></span>
  - <span data-ttu-id="16020-120">SliderThumb-包含可移动的拇指</span><span class="sxs-lookup"><span data-stu-id="16020-120">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="16020-121">TrackVisuals-包含轨迹和任何其他视觉对象</span><span class="sxs-lookup"><span data-stu-id="16020-121">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="16020-122">OtherVisuals-包含任何其他视觉对象</span><span class="sxs-lookup"><span data-stu-id="16020-122">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="16020-123">滑块事件</span><span class="sxs-lookup"><span data-stu-id="16020-123">Slider events</span></span>

<span data-ttu-id="16020-124">滑块公开了以下事件：</span><span class="sxs-lookup"><span data-stu-id="16020-124">Sliders expose the following events:</span></span>

- <span data-ttu-id="16020-125">OnValueUpdated-每当滑块值改变时调用</span><span class="sxs-lookup"><span data-stu-id="16020-125">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="16020-126">OnInteractionStarted-用户获取滑块时调用</span><span class="sxs-lookup"><span data-stu-id="16020-126">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="16020-127">OnInteractionEnded-用户释放滑块时调用</span><span class="sxs-lookup"><span data-stu-id="16020-127">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="16020-128">OnHoverEntered-当用户的手动/控制器使用近距离或远交互方式悬停在滑块上时调用。</span><span class="sxs-lookup"><span data-stu-id="16020-128">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="16020-129">OnHoverExited-当用户的手/控制器不再位于滑块附近时调用。</span><span class="sxs-lookup"><span data-stu-id="16020-129">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="16020-130">配置滑块绑定和轴</span><span class="sxs-lookup"><span data-stu-id="16020-130">Configuring slider bound and axis</span></span>

<span data-ttu-id="16020-131">您可以通过移动场景中的句柄直接移动滑块的起点和终点：</span><span class="sxs-lookup"><span data-stu-id="16020-131">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![滑杆配置](../images/sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="16020-133">还可以通过 " _滑块轴_ " 字段在滑块的本地空间) 指定轴 (</span><span class="sxs-lookup"><span data-stu-id="16020-133">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="16020-134">如果您无法使用该句柄，则可以改为通过 " _滑块起始距离_ " 和 " _滑块结束距离_ " 字段指定滑块的起点和终点。</span><span class="sxs-lookup"><span data-stu-id="16020-134">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="16020-135">它们将滑块的开始/结束位置指定为以局部坐标形式从滑块中心的距离。</span><span class="sxs-lookup"><span data-stu-id="16020-135">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="16020-136">这意味着，一旦您所需的滑块开始和结束距离，您可以将滑块缩放到更小或更大，而无需更新开始和结束距离。</span><span class="sxs-lookup"><span data-stu-id="16020-136">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="16020-137">检查器属性</span><span class="sxs-lookup"><span data-stu-id="16020-137">Inspector properties</span></span>

<span data-ttu-id="16020-138">**拇指根** 包含滑块的 gameobject。</span><span class="sxs-lookup"><span data-stu-id="16020-138">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="16020-139">**对齐位置** 此滑块是否与滑块上指定的位置对齐</span><span class="sxs-lookup"><span data-stu-id="16020-139">**Snap To Position** Whether or not this slider snaps to the designated position on the slider</span></span>

<span data-ttu-id="16020-140">**为可触摸** 此滑块是否可通过触摸事件控制</span><span class="sxs-lookup"><span data-stu-id="16020-140">**Is Touchable** Whether or not this slider is controllable via touch events</span></span>

<span data-ttu-id="16020-141">**拇指碰撞** 器控制滑块的碰撞器</span><span class="sxs-lookup"><span data-stu-id="16020-141">**Thumb Collider** The collider that controls the slider thumb</span></span>

<span data-ttu-id="16020-142">**可触摸碰撞** 器对齐位置为 true 时，可接触或选中的滑块区域。</span><span class="sxs-lookup"><span data-stu-id="16020-142">**Touchable Collider** The area of the slider that can be touched or selected when Snap To Position is true.</span></span>

<span data-ttu-id="16020-143">**滑块值** 滑块的值。</span><span class="sxs-lookup"><span data-stu-id="16020-143">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="16020-144">**使用滑块步骤划分** 控制是在步骤中还是连续递增此滑块。</span><span class="sxs-lookup"><span data-stu-id="16020-144">**Use Slider Step Divisions** Controls whether this slider is increments in steps or continuously.</span></span>

<span data-ttu-id="16020-145">**滑块步骤划分** 启用滑块步骤划分后，滑块拆分到的细分数。</span><span class="sxs-lookup"><span data-stu-id="16020-145">**Slider Step Divisions** Number of subdivisions the slider is split into when Use Slider Step Divisions is enabled.</span></span>

<span data-ttu-id="16020-146">**跟踪视觉对象** 包含沿滑块方向的所需跟踪视觉对象的 gameobject。</span><span class="sxs-lookup"><span data-stu-id="16020-146">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="16020-147">**刻度线** Gameobject，其中包含沿滑块方向的所需刻度线。</span><span class="sxs-lookup"><span data-stu-id="16020-147">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="16020-148">**Thumb 视觉对象** 包含沿滑块方向的所需 thumb 视觉对象的 gameobject。</span><span class="sxs-lookup"><span data-stu-id="16020-148">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="16020-149">**滑块轴** 滑块沿其移动的轴。</span><span class="sxs-lookup"><span data-stu-id="16020-149">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="16020-150">**滑块开始距离** 滑块轨道的起始位置，与中心沿滑块轴的距离（以本地空间单位为单位）。</span><span class="sxs-lookup"><span data-stu-id="16020-150">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="16020-151">**滑块结束距离** 滑块轨迹结束的位置，与中心沿滑块轴的距离（以本地空间单位为单位）。</span><span class="sxs-lookup"><span data-stu-id="16020-151">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="16020-152">当用户在编辑器中更新滑块轴值时，如果指定了 "跟踪视觉对象" 或 "滴答视觉对象"，则会更新其转换。</span><span class="sxs-lookup"><span data-stu-id="16020-152">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="16020-153">具体而言，将重置其本地位置，并将其本地旋转设置为与滑块轴方向匹配。</span><span class="sxs-lookup"><span data-stu-id="16020-153">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="16020-154">未修改其缩放比例。</span><span class="sxs-lookup"><span data-stu-id="16020-154">Their scale isn't modified.</span></span>
<span data-ttu-id="16020-155">如果刻度线具有网格对象集合组件，则会相应地更新 Layout 和 CellWidth 或 CellHeight 以匹配滑块轴。</span><span class="sxs-lookup"><span data-stu-id="16020-155">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>

## <a name="example-slider-configurations"></a><span data-ttu-id="16020-156">示例滑块配置</span><span class="sxs-lookup"><span data-stu-id="16020-156">Example Slider Configurations</span></span>

<span data-ttu-id="16020-157">靠齐到位置连续滑块的连续滑块 ![](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span><span class="sxs-lookup"><span data-stu-id="16020-157">Continuous Sliders with Snap To Position ![Continuous Sliders](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span></span>

<span data-ttu-id="16020-158">带有对齐位置的步骤滑块</span><span class="sxs-lookup"><span data-stu-id="16020-158">Step Sliders with Snap To Position</span></span>

![步骤滑块](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

<span data-ttu-id="16020-160">触摸滑块</span><span class="sxs-lookup"><span data-stu-id="16020-160">Touch Sliders</span></span>

![触摸滑块](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)