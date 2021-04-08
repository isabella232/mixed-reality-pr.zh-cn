---
title: 按钮
description: MRTK 中的按钮概述
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、混合现实、开发、MRTK、MRTK 按钮
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003100"
---
# <a name="button"></a><span data-ttu-id="b7574-104">Button</span><span class="sxs-lookup"><span data-stu-id="b7574-104">Button</span></span>

![主要按钮](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="b7574-106">按钮为用户提供了触发即时操作的方法。</span><span class="sxs-lookup"><span data-stu-id="b7574-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="b7574-107">这是混合现实中最基本的组件之一。</span><span class="sxs-lookup"><span data-stu-id="b7574-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="b7574-108">MRTK 提供各种类型的按钮 prototyping。</span><span class="sxs-lookup"><span data-stu-id="b7574-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="b7574-109">MRTK 中的按钮 prototyping</span><span class="sxs-lookup"><span data-stu-id="b7574-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="b7574-110">文件夹下的按钮 prototyping 示例 ``MRTK/SDK/Features/UX/Interactable/Prefabs``</span><span class="sxs-lookup"><span data-stu-id="b7574-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="b7574-111">Unity UI 图像/基于图形的按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="b7574-112">基于碰撞器的按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="b7574-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="b7574-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="b7574-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="b7574-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="b7574-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="b7574-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="b7574-119">HoloLens 2 的带有 backplate 的 shell 样式按钮，它支持各种可视反馈，如边框细、邻近浅色和压缩前板</span><span class="sxs-lookup"><span data-stu-id="b7574-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-120">HoloLens 2 的 shell 样式按钮，无 backplate</span><span class="sxs-lookup"><span data-stu-id="b7574-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-121">HoloLens 2 的带有圆形形状的 shell 样式按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="b7574-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="b7574-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="b7574-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="b7574-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="b7574-125">宽 HoloLens 2 的 shell 样式按钮32x96mm</span><span class="sxs-lookup"><span data-stu-id="b7574-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-126">具有共享 backplate 的水平 HoloLens 2 按钮栏</span><span class="sxs-lookup"><span data-stu-id="b7574-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-127">带有共享 backplate 的纵向 HoloLens 2 按钮栏</span><span class="sxs-lookup"><span data-stu-id="b7574-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="b7574-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="b7574-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="b7574-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="b7574-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="b7574-131">HoloLens 2 的 shell 样式复选框32x32mm</span><span class="sxs-lookup"><span data-stu-id="b7574-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-132">HoloLens 2 的 shell 样式开关32x32mm</span><span class="sxs-lookup"><span data-stu-id="b7574-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-133">HoloLens 2 的 shell 样式收音机32x32mm</span><span class="sxs-lookup"><span data-stu-id="b7574-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="b7574-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="b7574-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="b7574-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="b7574-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b7574-137">HoloLens 2 的 shell 样式复选框32x96mm</span><span class="sxs-lookup"><span data-stu-id="b7574-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-138">HoloLens 2 的 shell 样式开关32x96mm</span><span class="sxs-lookup"><span data-stu-id="b7574-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-139">HoloLens 2 的 shell 样式收音机32x96mm</span><span class="sxs-lookup"><span data-stu-id="b7574-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b7574-140">![放射 ](../images/button/MRTK_Button_Radial.png) 辐射</span><span class="sxs-lookup"><span data-stu-id="b7574-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-141">![复选框](../images/button/MRTK_Button_Checkbox.png) **复选框**</span><span class="sxs-lookup"><span data-stu-id="b7574-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="b7574-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b7574-143">径向按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-144">复选框</span><span class="sxs-lookup"><span data-stu-id="b7574-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-145">切换开关</span><span class="sxs-lookup"><span data-stu-id="b7574-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b7574-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="b7574-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="b7574-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-148">![按钮基 ](../images/button/MRTK_Button_Base.png) **按钮**</span><span class="sxs-lookup"><span data-stu-id="b7574-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="b7574-149">HoloLens 第一代 shell 样式按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-150">圆形形状推送按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="b7574-151">“基本”按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="b7574-152">`Button` (资产/MRTK/SDK/功能/UX/种不可交互/prototyping/prefab) 基于[种不可交互](interactable.md)概念，以便为按钮或其他类型的交互表面提供简单的 UI 控件。</span><span class="sxs-lookup"><span data-stu-id="b7574-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="b7574-153">"基线" 按钮支持所有可用的输入方法，包括接近交互的有向右输入，还支持 "注视" 和 "空中点击" 进行远距离交互。</span><span class="sxs-lookup"><span data-stu-id="b7574-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="b7574-154">你还可以使用语音命令触发该按钮。</span><span class="sxs-lookup"><span data-stu-id="b7574-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="b7574-155">`PressableButtonHoloLens2` (资产/MRTK/SDK/Features/UX/种不可交互/Prototyping/PressableButtonHoloLens2) 为 HoloLens 2 的 shell 样式按钮，该按钮支持直接手动跟踪输入的按钮的精确移动。</span><span class="sxs-lookup"><span data-stu-id="b7574-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="b7574-156">它将 `Interactable` 脚本与 `PressableButton` 脚本结合起来。</span><span class="sxs-lookup"><span data-stu-id="b7574-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="b7574-157">对于 HoloLens 2，建议使用不透明 backplate 的按钮。</span><span class="sxs-lookup"><span data-stu-id="b7574-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="b7574-158">不建议使用透明按钮，因为存在以下可用性和稳定性问题：</span><span class="sxs-lookup"><span data-stu-id="b7574-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="b7574-159">在物理环境中，无法读取图标和文本</span><span class="sxs-lookup"><span data-stu-id="b7574-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="b7574-160">事件触发时很难理解</span><span class="sxs-lookup"><span data-stu-id="b7574-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="b7574-161">使用 HoloLens 2 的深度 LSR 稳定性时，通过透明平面显示的全息影像可能会变得不稳定</span><span class="sxs-lookup"><span data-stu-id="b7574-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![按钮 plated](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="b7574-163">如何使用 pressable 按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="b7574-164">基于 Unity UI 的按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-164">Unity UI based buttons</span></span>

<span data-ttu-id="b7574-165"> (GameObject-> UI > 画布) 中创建画布。</span><span class="sxs-lookup"><span data-stu-id="b7574-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="b7574-166">在画布的 "检查器" 面板中：</span><span class="sxs-lookup"><span data-stu-id="b7574-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="b7574-167">单击 "转换为 MRTK 画布"</span><span class="sxs-lookup"><span data-stu-id="b7574-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="b7574-168">单击 "添加 NearInteractionTouchableUnityUI"</span><span class="sxs-lookup"><span data-stu-id="b7574-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="b7574-169">将矩形转换组件的 X、Y 和 Z 刻度设置为0.001</span><span class="sxs-lookup"><span data-stu-id="b7574-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="b7574-170">然后，将 `PressableButtonUnityUI` (资产/MRTK/SDK/Features/ux/种不可交互/prototyping/PressableButtonUnityUI. prefab) ， `PressableButtonUnityUICircular` (资产/MRTK/Sdk/FEATURES/Ux/种不可交互/prototyping/PressableButtonUnityUICircular) ，或 `PressableButtonHoloLens2UnityUI` (资产/prefab/sdk/features//MRTK/种不可交互/prototyping) 拖到画布上。</span><span class="sxs-lookup"><span data-stu-id="b7574-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="b7574-171">基于碰撞器的按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-171">Collider based buttons</span></span>

<span data-ttu-id="b7574-172">只需将 `PressableButtonHoloLens2` (资产/MRTK/SDK/功能/ux/种不可交互/prototyping/PressableButtonHoloLens2. prefab) 或 `PressableButtonHoloLens2Unplated` (资产/MRTK/Sdk/FEATURES/ux/种不可交互/prototyping/PressableButtonHoloLens2Unplated) 到场景中。</span><span class="sxs-lookup"><span data-stu-id="b7574-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="b7574-173">这些按钮 prototyping 已配置为对各种类型的输入具有音频视觉对象反馈，其中包括有表述的手写输入和注视。</span><span class="sxs-lookup"><span data-stu-id="b7574-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="b7574-174">Prefab 本身以及 [种不可交互](interactable.md) 组件中公开的事件可用于触发其他操作。</span><span class="sxs-lookup"><span data-stu-id="b7574-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="b7574-175">[HandInteractionExample 场景](../example-scenes/hand-interaction-examples.md)中的 pressable 按钮使用种不可交互的 *OnClick* 事件来触发多维数据集颜色的更改。</span><span class="sxs-lookup"><span data-stu-id="b7574-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="b7574-176">此事件是针对不同类型的输入法（如注视、分流、手型）以及通过 pressable 按钮脚本的物理按钮按下触发的。</span><span class="sxs-lookup"><span data-stu-id="b7574-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="b7574-177">可以通过按钮上的打开 "pressable" *按钮的配置* 时间 `PhysicalPressEventRouter` 。</span><span class="sxs-lookup"><span data-stu-id="b7574-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="b7574-178">例如，可以将 *OnClick* 设置为第一次按下按钮时激发，而不是按下并释放，方法是 *在\*\*按下* 时，将种不可交互设置为单击事件。</span><span class="sxs-lookup"><span data-stu-id="b7574-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="b7574-179">若要利用特定的可表述的手写输入状态信息，你可以使用 pressable 按钮事件- *Touch 开始*、 *触摸端*、 *按下按钮*、 *按钮已释放*。</span><span class="sxs-lookup"><span data-stu-id="b7574-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="b7574-180">不过，这些事件不会因出现空中点击、触碰或眼睛输入而激发。</span><span class="sxs-lookup"><span data-stu-id="b7574-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="b7574-181">**为了同时支持近交互和远交互，建议使用种不可交互的 *OnClick* 事件。**</span><span class="sxs-lookup"><span data-stu-id="b7574-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="b7574-182">交互状态</span><span class="sxs-lookup"><span data-stu-id="b7574-182">Interaction states</span></span>

<span data-ttu-id="b7574-183">处于空闲状态时，按钮的顶层印不见。</span><span class="sxs-lookup"><span data-stu-id="b7574-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="b7574-184">作为手指方法，或从注视输入定位到表面的光标，前面板的光亮边框变为可见。</span><span class="sxs-lookup"><span data-stu-id="b7574-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="b7574-185">前板面上的手指位置还有其他突出突出。</span><span class="sxs-lookup"><span data-stu-id="b7574-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="b7574-186">用手指推送时，前板会随手指移动。</span><span class="sxs-lookup"><span data-stu-id="b7574-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="b7574-187">当手指接触到前板面时，它会显示一种细小的脉冲效果，以提供触摸点的可视反馈。</span><span class="sxs-lookup"><span data-stu-id="b7574-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="b7574-188">在 HoloLens 2 shell 样式的按钮中，有很多视觉提示和实用可提高用户交互的置信度。</span><span class="sxs-lookup"><span data-stu-id="b7574-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![邻近感应](../images/button/ux_button_affordance_proximitylight.jpg) | ![焦点突出显示](../images/button/ux_button_affordance_focushighlight.jpg)  | ![压缩箱](../images/button/ux_button_affordance_compression.jpg) | ![触发暂停](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="b7574-193">邻近感应</span><span class="sxs-lookup"><span data-stu-id="b7574-193">Proximity light</span></span> | <span data-ttu-id="b7574-194">焦点突出显示</span><span class="sxs-lookup"><span data-stu-id="b7574-194">Focus highlight</span></span> | <span data-ttu-id="b7574-195">压缩箱</span><span class="sxs-lookup"><span data-stu-id="b7574-195">Compressing cage</span></span> | <span data-ttu-id="b7574-196">触发暂停</span><span class="sxs-lookup"><span data-stu-id="b7574-196">Pulse on trigger</span></span> |

<span data-ttu-id="b7574-197">精细的脉冲效果由 pressable 按钮触发，该按钮查找当前正在交互的指针上的 *ProximityLight (s)* 。</span><span class="sxs-lookup"><span data-stu-id="b7574-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="b7574-198">如果找到任何邻近光源，则会 `ProximityLight.Pulse` 调用方法，这会自动对着色器参数进行动画处理以显示脉冲。</span><span class="sxs-lookup"><span data-stu-id="b7574-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="b7574-199">检查器属性</span><span class="sxs-lookup"><span data-stu-id="b7574-199">Inspector properties</span></span>

![按钮结构](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="b7574-201">**框碰撞器** 
 `Box Collider`按钮的前面板。</span><span class="sxs-lookup"><span data-stu-id="b7574-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="b7574-202">**Pressable 按钮** 用手按下交互的按钮移动的逻辑。</span><span class="sxs-lookup"><span data-stu-id="b7574-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="b7574-203">**物理按下事件路由器** 此脚本将事件从一开始按下交互发送到 [种不可交互](interactable.md)。</span><span class="sxs-lookup"><span data-stu-id="b7574-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="b7574-204">**种不可交互** 
[种不可交互](interactable.md)处理各种类型的交互状态和事件。</span><span class="sxs-lookup"><span data-stu-id="b7574-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="b7574-205">HoloLens 注视、手势和语音输入以及沉浸式耳机动作控制器输入由此脚本直接处理。</span><span class="sxs-lookup"><span data-stu-id="b7574-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="b7574-206">**音频源** 音频反馈剪辑的 Unity 音频源。</span><span class="sxs-lookup"><span data-stu-id="b7574-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="b7574-207">*NearInteractionTouchable* 是使任何对象可触摸带有明确表述的手写输入所需的。</span><span class="sxs-lookup"><span data-stu-id="b7574-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="b7574-208">Prefab 布局</span><span class="sxs-lookup"><span data-stu-id="b7574-208">Prefab layout</span></span>

<span data-ttu-id="b7574-209">*ButtonContent* 对象包含前板、文本标签和图标。</span><span class="sxs-lookup"><span data-stu-id="b7574-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="b7574-210">*FrontPlate* 使用 *Button_Box* 着色器响应索引手指的邻近性。</span><span class="sxs-lookup"><span data-stu-id="b7574-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="b7574-211">它显示光亮边界、邻近浅色和对触控的脉冲效果。</span><span class="sxs-lookup"><span data-stu-id="b7574-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="b7574-212">文本标签通过 TextMesh Pro 进行。</span><span class="sxs-lookup"><span data-stu-id="b7574-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="b7574-213">*SeeItSayItLabel* 的可见性由 [种不可交互](interactable.md)的主题控制。</span><span class="sxs-lookup"><span data-stu-id="b7574-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![按钮布局](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="b7574-215">如何更改图标和文本</span><span class="sxs-lookup"><span data-stu-id="b7574-215">How to change the icon and text</span></span>

<span data-ttu-id="b7574-216">MRTK 按钮使用 `ButtonConfigHelper` 组件来帮助您更改按钮图标、文本和标签。</span><span class="sxs-lookup"><span data-stu-id="b7574-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="b7574-217"> (请注意，如果所选按钮上没有元素，则某些字段可能不存在。 ) </span><span class="sxs-lookup"><span data-stu-id="b7574-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![按钮配置帮助器](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="b7574-219">创建和修改图标集</span><span class="sxs-lookup"><span data-stu-id="b7574-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="b7574-220">**图标集** 是组件使用的一组共享图标资产 `ButtonConfigHelper` 。</span><span class="sxs-lookup"><span data-stu-id="b7574-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="b7574-221">支持三种图标 *样式* 。</span><span class="sxs-lookup"><span data-stu-id="b7574-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="b7574-222">使用在四个图标上呈现 **四** 个图标 `MeshRenderer` 。</span><span class="sxs-lookup"><span data-stu-id="b7574-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="b7574-223">这是默认图标样式。</span><span class="sxs-lookup"><span data-stu-id="b7574-223">This is the default icon style.</span></span>
* <span data-ttu-id="b7574-224">使用呈现子 **画面** 图标 `SpriteRenderer` 。</span><span class="sxs-lookup"><span data-stu-id="b7574-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="b7574-225">如果希望将图标作为 sprite 表导入，或者需要将图标资产与 Unity UI 组件共享，这会很有用。</span><span class="sxs-lookup"><span data-stu-id="b7574-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="b7574-226">若要使用此样式，将需要 **(Windows > 程序包管理器 > 2D sprite** 安装动画编辑器包) </span><span class="sxs-lookup"><span data-stu-id="b7574-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="b7574-227">使用组件呈现 **字符** 图标 `TextMeshPro` 。</span><span class="sxs-lookup"><span data-stu-id="b7574-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="b7574-228">如果希望使用图标字体，这会很有用。</span><span class="sxs-lookup"><span data-stu-id="b7574-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="b7574-229">若要使用 HoloLens 图标字体，需要创建 `TextMeshPro` 字体资产。</span><span class="sxs-lookup"><span data-stu-id="b7574-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="b7574-230">若要更改按钮使用的样式，请展开 ButtonConfigHelper 中的 *图标* 下拉列表，并从 *图标样式* 下拉列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="b7574-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="b7574-231">你可以使用 "资产" 菜单创建一个新的按钮图标集： " **创建 > 混合现实工具包" > 图标集。**</span><span class="sxs-lookup"><span data-stu-id="b7574-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="b7574-232">若要添加四个和动画图标，只需将其拖到各自的数组中。</span><span class="sxs-lookup"><span data-stu-id="b7574-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="b7574-233">若要添加字符图标，必须首先创建和分配字体资产。</span><span class="sxs-lookup"><span data-stu-id="b7574-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="b7574-234">在 MRTK 2.4 和更高版本中，我们建议将自定义图标纹理移到 IconSet 中。</span><span class="sxs-lookup"><span data-stu-id="b7574-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="b7574-235">若要将项目中所有按钮上的资产升级为新建议的格式，请使用 ButtonConfigHelperMigrationHandler。</span><span class="sxs-lookup"><span data-stu-id="b7574-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="b7574-236"> (混合现实工具包-> 实用工具-> 迁移窗口-> 迁移处理程序选择-> ButtonConfigHelperMigrationHandler) </span><span class="sxs-lookup"><span data-stu-id="b7574-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="b7574-237">导入升级按钮所需的 MixedRealityToolkit 包。</span><span class="sxs-lookup"><span data-stu-id="b7574-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![升级窗口对话框](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="b7574-239">如果在迁移过程中在默认图标集中找不到图标，将在 MixedRealityToolkit/CustomIconSets 中创建自定义图标集。</span><span class="sxs-lookup"><span data-stu-id="b7574-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="b7574-240">此时将显示一个对话框，指示已发生此情况。</span><span class="sxs-lookup"><span data-stu-id="b7574-240">A dialog will indicate that this has taken place.</span></span>

![自定义图标通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="b7574-242">创建 HoloLens 图标字体资产</span><span class="sxs-lookup"><span data-stu-id="b7574-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="b7574-243">首先，将图标字体导入 Unity。</span><span class="sxs-lookup"><span data-stu-id="b7574-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="b7574-244">在 Windows 计算机上，可以在 *windows/Fonts/holomdl2. .ttf* 中找到默认的 HoloLens 字体。</span><span class="sxs-lookup"><span data-stu-id="b7574-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="b7574-245">将此文件复制并粘贴到 "资产" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="b7574-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="b7574-246">接下来，通过 **> TextMeshPro > 字体资产创建者的窗口** 打开 TextMeshPro 字体资产创建者。</span><span class="sxs-lookup"><span data-stu-id="b7574-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="b7574-247">下面是用于生成 HoloLens 字体阿特拉斯的推荐设置。</span><span class="sxs-lookup"><span data-stu-id="b7574-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="b7574-248">若要包含所有图标，请将以下 Unicode 范围粘贴到 *字符序列* 字段中：</span><span class="sxs-lookup"><span data-stu-id="b7574-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![按钮创建1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="b7574-250">生成字体资产后，将其保存到你的项目，并将其分配给图标集的 *字符图标字体* 字段。</span><span class="sxs-lookup"><span data-stu-id="b7574-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="b7574-251">此时将填充 *可用图标* 下拉列表。</span><span class="sxs-lookup"><span data-stu-id="b7574-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="b7574-252">若要使图标可用于按钮，请单击该图标。</span><span class="sxs-lookup"><span data-stu-id="b7574-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="b7574-253">它将被添加到 " *选定的图标* " 下拉列表中，此时将显示在中， `ButtonConfigHelper.` 可以选择为图标指定标记。</span><span class="sxs-lookup"><span data-stu-id="b7574-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="b7574-254">这样就可以在运行时设置图标。</span><span class="sxs-lookup"><span data-stu-id="b7574-254">This enables setting the icon at runtime.</span></span>

![按钮创建3](../images/button/MRTK_Font_Asset_Creation_3.png)

![按钮创建2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="b7574-257">若要使用图标集，请选择一个按钮，展开中的图标下拉列表， `ButtonConfigHelper` 并将其分配给 *图标集* 字段。</span><span class="sxs-lookup"><span data-stu-id="b7574-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![按钮图标集](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="b7574-259">如何更改按钮大小</span><span class="sxs-lookup"><span data-stu-id="b7574-259">How to change the size of a button</span></span>

<span data-ttu-id="b7574-260">HoloLens 2 的 shell 样式按钮的大小为32x32mm。</span><span class="sxs-lookup"><span data-stu-id="b7574-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="b7574-261">若要自定义维度，请在 prefab 按钮中更改这些对象的大小：</span><span class="sxs-lookup"><span data-stu-id="b7574-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="b7574-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="b7574-262">**FrontPlate**</span></span>
2. <span data-ttu-id="b7574-263">BackPlate 下的 **四核**</span><span class="sxs-lookup"><span data-stu-id="b7574-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="b7574-264">根上的 **Box 碰撞** 器</span><span class="sxs-lookup"><span data-stu-id="b7574-264">**Box Collider** on the root</span></span>

<span data-ttu-id="b7574-265">然后，在 NearInteractionTouchable 脚本中单击 " **修复边界** " 按钮，该脚本位于按钮的根目录中。</span><span class="sxs-lookup"><span data-stu-id="b7574-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="b7574-266">更新 "FrontPlate" ![ 按钮大小自定义项的大小1](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="b7574-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="b7574-267">更新四 ![ 按钮大小自定义项的大小2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="b7574-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="b7574-268">更新框碰撞器 ![ 按钮大小自定义3的大小](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="b7574-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="b7574-269">单击 "修复边界" ![ 按钮大小自定义4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="b7574-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it&quot;></a><span data-ttu-id=&quot;b7574-270&quot;>语音命令 ( &quot;见 ..." ) </span><span class="sxs-lookup"><span data-stu-id="b7574-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="b7574-271">**语音输入处理程序** Pressable 按钮中的 [种不可交互](interactable.md) 脚本已实现 `IMixedRealitySpeechHandler` 。</span><span class="sxs-lookup"><span data-stu-id="b7574-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="b7574-272">可以在此处设置语音命令关键字。</span><span class="sxs-lookup"><span data-stu-id="b7574-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="b7574-273">**语音输入配置文件** 此外，还需要在全局 *语音命令配置文件* 中注册语音命令关键字。</span><span class="sxs-lookup"><span data-stu-id="b7574-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="b7574-274">**请参阅-it 标签** Pressable 按钮 prefab 在 *SeeItSayItLabel* 对象下有一个占位符 TextMesh Pro 标签。</span><span class="sxs-lookup"><span data-stu-id="b7574-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="b7574-275">您可以使用此标签来向用户传达按钮的语音命令关键字。</span><span class="sxs-lookup"><span data-stu-id="b7574-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="b7574-276">如何从头开始按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-276">How to make a button from scratch</span></span>

<span data-ttu-id="b7574-277">可以在 **PressableButtonExample** 场景中找到这些按钮的示例。</span><span class="sxs-lookup"><span data-stu-id="b7574-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="b7574-278">1. 创建一个 pressable 按钮，其中包含多维数据集 (接近交互) </span><span class="sxs-lookup"><span data-stu-id="b7574-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="b7574-279"> (GameObject > 3D Object > 多维数据集创建 Unity 多维数据集) </span><span class="sxs-lookup"><span data-stu-id="b7574-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="b7574-280">添加 `PressableButton.cs` 脚本</span><span class="sxs-lookup"><span data-stu-id="b7574-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="b7574-281">添加 `NearInteractionTouchable.cs` 脚本</span><span class="sxs-lookup"><span data-stu-id="b7574-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="b7574-282">在 `PressableButton` 的 "检查器" 面板中，将 cube 对象分配给 **移动按钮视觉** 对象。</span><span class="sxs-lookup"><span data-stu-id="b7574-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="b7574-283">选择多维数据集时，会在对象上看到多个彩色层。</span><span class="sxs-lookup"><span data-stu-id="b7574-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="b7574-284">这会直观显示 " **按下设置**" 下的距离值。</span><span class="sxs-lookup"><span data-stu-id="b7574-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="b7574-285">使用句柄，可以配置何时开始按下 (将对象移动) 以及何时触发事件。</span><span class="sxs-lookup"><span data-stu-id="b7574-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="b7574-286">按下该按钮时，它将移动并生成正确的事件， `PressableButton.cs` 如 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 。</span><span class="sxs-lookup"><span data-stu-id="b7574-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="b7574-287">故障排除</span><span class="sxs-lookup"><span data-stu-id="b7574-287">Troubleshooting</span></span>

<span data-ttu-id="b7574-288">如果按钮正在执行双击，请确保 " **强制前台推送** " 属性处于活动状态，" **开始推送距离** " 平面置于 **Near 交互可触摸** 平面的前方。</span><span class="sxs-lookup"><span data-stu-id="b7574-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="b7574-289">**近交互可触摸** 平面由下方 gif 中白色箭头原点前面的蓝色平面表示：</span><span class="sxs-lookup"><span data-stu-id="b7574-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![突出显示了 "强制前台推送" 属性的 Pressable 按钮脚本组件](../images/button/MRTK_Button_Enforce_Push.png)

![在接近交互可触摸平面前面移动起始推送距离的动画示例](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="b7574-292">2. 将视觉反馈添加到 "基本多维数据集" 按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="b7574-293">MRTK 标准着色器提供各种功能，可轻松添加视觉反馈。</span><span class="sxs-lookup"><span data-stu-id="b7574-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="b7574-294">创建材料并选择着色器 `Mixed Reality Toolkit/Standard` 。</span><span class="sxs-lookup"><span data-stu-id="b7574-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="b7574-295">或者，您可以使用或复制 `/SDK/StandardAssets/Materials/` 使用 MRTK 标准着色器的现有材料中的一个。</span><span class="sxs-lookup"><span data-stu-id="b7574-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="b7574-296">勾选 `Hover Light` 和 `Proximity Light` " **流畅选项**"。</span><span class="sxs-lookup"><span data-stu-id="b7574-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="b7574-297">这将为近手 (邻近感应) 和远端指针， (悬停光) 交互提供视觉反馈。</span><span class="sxs-lookup"><span data-stu-id="b7574-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="b7574-298">3. 将音频反馈添加到 "基本" 多维数据集按钮</span><span class="sxs-lookup"><span data-stu-id="b7574-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="b7574-299">由于 `PressableButton.cs` 脚本公开了 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 等事件，因此我们可以轻松地分配音频反馈。</span><span class="sxs-lookup"><span data-stu-id="b7574-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="b7574-300">只需将 Unity 添加 `Audio Source` 到多维数据集对象，然后通过选择 AudioSource PlayOneShot () 来分配音频剪辑。</span><span class="sxs-lookup"><span data-stu-id="b7574-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="b7574-301">可以使用 "文件夹" 下的 MRTK_Select_Main 和 MRTK_Select_Secondary 音频剪辑 `/SDK/StandardAssets/Audio/` 。</span><span class="sxs-lookup"><span data-stu-id="b7574-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="b7574-302">4. 添加可视状态并处理远距离交互事件</span><span class="sxs-lookup"><span data-stu-id="b7574-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="b7574-303">[种不可交互](interactable.md) 是一个脚本，可轻松地为各种类型的输入交互创建可视状态。</span><span class="sxs-lookup"><span data-stu-id="b7574-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="b7574-304">它还处理远距离交互事件。</span><span class="sxs-lookup"><span data-stu-id="b7574-304">It also handles far interaction events.</span></span> <span data-ttu-id="b7574-305">添加 `Interactable.cs` 多维数据集对象并将其拖放到 "**配置文件**" 下的 **目标** 字段。</span><span class="sxs-lookup"><span data-stu-id="b7574-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="b7574-306">然后，使用类型 **ScaleOffsetColorTheme** 创建一个新主题。</span><span class="sxs-lookup"><span data-stu-id="b7574-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="b7574-307">在此主题下，可以指定特定交互状态的对象的颜色，如 **焦点** 和 **按下** 状态。</span><span class="sxs-lookup"><span data-stu-id="b7574-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="b7574-308">还可以控制缩放和偏移量。</span><span class="sxs-lookup"><span data-stu-id="b7574-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="b7574-309">检查 **缓动** 并设置持续时间，以使视觉对象过渡平滑。</span><span class="sxs-lookup"><span data-stu-id="b7574-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![选择配置文件主题](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="b7574-311">你将看到对象同时响应 (的手 ray 或注视光标) ，并接近 (手型) 交互。</span><span class="sxs-lookup"><span data-stu-id="b7574-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="b7574-312">自定义按钮示例</span><span class="sxs-lookup"><span data-stu-id="b7574-312">Custom button examples</span></span>

<span data-ttu-id="b7574-313">在 [HandInteractionExample 场景](../example-scenes/hand-interaction-examples.md)中，请参阅使用的钢琴和轮按钮示例 `PressableButton` 。</span><span class="sxs-lookup"><span data-stu-id="b7574-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="b7574-314">每个钢琴键均已 `PressableButton` 分配一个和一个 `NearInteractionTouchable` 脚本。</span><span class="sxs-lookup"><span data-stu-id="b7574-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="b7574-315">务必验证的 *本地前向* 方向是 `NearInteractionTouchable` 正确的。</span><span class="sxs-lookup"><span data-stu-id="b7574-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="b7574-316">它在编辑器中用白色箭头表示。</span><span class="sxs-lookup"><span data-stu-id="b7574-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="b7574-317">请确保箭头指向按钮的正面：</span><span class="sxs-lookup"><span data-stu-id="b7574-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="b7574-318">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7574-318">See also</span></span>

* [<span data-ttu-id="b7574-319">可交互</span><span class="sxs-lookup"><span data-stu-id="b7574-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="b7574-320">视觉主题</span><span class="sxs-lookup"><span data-stu-id="b7574-320">Visual Themes</span></span>](visual-themes.md)
