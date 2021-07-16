---
title: 按钮
description: MRTK 中的按钮概述
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、混合现实、开发、MRTK、MRTK 按钮
ms.openlocfilehash: 16baeede2c63437e933eb1367f01af7f372cd62f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281856"
---
# <a name="buttons"></a><span data-ttu-id="d8f55-104">按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-104">Buttons</span></span>

![按钮主按钮](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="d8f55-106">按钮为用户提供了触发即时操作的方法。</span><span class="sxs-lookup"><span data-stu-id="d8f55-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="d8f55-107">它是混合现实中最基础的组件之一。</span><span class="sxs-lookup"><span data-stu-id="d8f55-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="d8f55-108">MRTK 提供各种类型的按钮预制。</span><span class="sxs-lookup"><span data-stu-id="d8f55-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="d8f55-109">MRTK 中的按钮预制</span><span class="sxs-lookup"><span data-stu-id="d8f55-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="d8f55-110">文件夹下的 ``MRTK/SDK/Features/UX/Interactable/Prefabs`` 按钮预制示例</span><span class="sxs-lookup"><span data-stu-id="d8f55-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="d8f55-111">基于 Unity UI 图像/图形的按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="d8f55-112">基于碰撞体按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="d8f55-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="d8f55-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="d8f55-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="d8f55-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="d8f55-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="d8f55-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="d8f55-119">HoloLens 2外壳样式按钮，带底板，支持各种视觉反馈，例如边框光、邻近感应光和压缩的前板</span><span class="sxs-lookup"><span data-stu-id="d8f55-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-120">HoloLens 2不带反板的 shell 样式按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-121">HoloLens 2圆形的 shell 样式按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="d8f55-122">![](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96 PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="d8f55-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="d8f55-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="d8f55-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="d8f55-125">宽HoloLens 2 shell 样式按钮 32x96mm</span><span class="sxs-lookup"><span data-stu-id="d8f55-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-126">水平HoloLens 2带共享底板的按钮栏</span><span class="sxs-lookup"><span data-stu-id="d8f55-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-127">具有HoloLens 2底板的垂直按钮栏</span><span class="sxs-lookup"><span data-stu-id="d8f55-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="d8f55-128">![](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32 PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="d8f55-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-129">![](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32 PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="d8f55-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-130">![](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32 PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="d8f55-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="d8f55-131">HoloLens 2 shell 样式复选框 32x32mm</span><span class="sxs-lookup"><span data-stu-id="d8f55-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-132">HoloLens 2 shell 样式开关 32x32mm</span><span class="sxs-lookup"><span data-stu-id="d8f55-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-133">HoloLens 2 shell 样式的无线电 32x32mm</span><span class="sxs-lookup"><span data-stu-id="d8f55-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="d8f55-134">![](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96 PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="d8f55-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-135">![](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96 PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="d8f55-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-136">![](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96 PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="d8f55-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="d8f55-137">HoloLens 2 shell 样式复选框 32x96mm</span><span class="sxs-lookup"><span data-stu-id="d8f55-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-138">HoloLens 2 shell 样式开关 32x96mm</span><span class="sxs-lookup"><span data-stu-id="d8f55-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-139">HoloLens 2 shell 样式的无线电 32x96mm</span><span class="sxs-lookup"><span data-stu-id="d8f55-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="d8f55-140">![径 ](../images/button/MRTK_Button_Radial.png) **向径向**</span><span class="sxs-lookup"><span data-stu-id="d8f55-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-141">![复选框 ](../images/button/MRTK_Button_Checkbox.png) **复选框**</span><span class="sxs-lookup"><span data-stu-id="d8f55-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="d8f55-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="d8f55-143">径向按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-144">复选框</span><span class="sxs-lookup"><span data-stu-id="d8f55-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-145">切换开关</span><span class="sxs-lookup"><span data-stu-id="d8f55-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="d8f55-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="d8f55-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="d8f55-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-148">![按钮基本 ](../images/button/MRTK_Button_Base.png) **按钮**</span><span class="sxs-lookup"><span data-stu-id="d8f55-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="d8f55-149">HoloLens第一代的 shell 样式按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-150">圆形按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="d8f55-151">“基本”按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="d8f55-152"> (`Button` Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) 基于可交互概念，为[](interactable.md)按钮或其他类型的交互式图面提供简单的 UI 控件。</span><span class="sxs-lookup"><span data-stu-id="d8f55-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="d8f55-153">基线按钮支持所有可用的输入方法，包括近部交互的表达手部输入，以及远端交互的凝视 + 空敲击。</span><span class="sxs-lookup"><span data-stu-id="d8f55-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="d8f55-154">还可使用语音命令触发按钮。</span><span class="sxs-lookup"><span data-stu-id="d8f55-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="d8f55-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) 是 HoloLens 2 的 shell 样式按钮，支持直接手部跟踪输入的按钮的精确移动。</span><span class="sxs-lookup"><span data-stu-id="d8f55-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="d8f55-156">它将脚本 `Interactable` 与脚本 `PressableButton` 组合在一起。</span><span class="sxs-lookup"><span data-stu-id="d8f55-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="d8f55-157">对于HoloLens 2，建议使用具有不透明底板的按钮。</span><span class="sxs-lookup"><span data-stu-id="d8f55-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="d8f55-158">由于以下可用性和稳定性问题，不建议使用透明按钮：</span><span class="sxs-lookup"><span data-stu-id="d8f55-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="d8f55-159">物理环境难以读取图标和文本</span><span class="sxs-lookup"><span data-stu-id="d8f55-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="d8f55-160">很难理解何时触发事件</span><span class="sxs-lookup"><span data-stu-id="d8f55-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="d8f55-161">全息影像深度 LSR 稳定时，通过透明平面显示HoloLens 2不稳定</span><span class="sxs-lookup"><span data-stu-id="d8f55-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![按钮已设置色块](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="d8f55-163">如何使用可按下按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="d8f55-164">基于 Unity UI 的按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-164">Unity UI based buttons</span></span>

<span data-ttu-id="d8f55-165">使用 (GameObject -> UI -> Canvas) 在场景中创建画布。</span><span class="sxs-lookup"><span data-stu-id="d8f55-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="d8f55-166">在画布的"检查器"面板中：</span><span class="sxs-lookup"><span data-stu-id="d8f55-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="d8f55-167">单击"转换为 MRTK 画布"</span><span class="sxs-lookup"><span data-stu-id="d8f55-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="d8f55-168">单击"添加 NearInteractionTouchableUnityUI"</span><span class="sxs-lookup"><span data-stu-id="d8f55-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="d8f55-169">将矩形转换组件的 X、Y 和 Z 刻度设置为 0.001</span><span class="sxs-lookup"><span data-stu-id="d8f55-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="d8f55-170">然后，拖动 `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab) ， `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab) ，或画布上的 `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="d8f55-171">基于碰撞体按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-171">Collider based buttons</span></span>

<span data-ttu-id="d8f55-172">只需将 `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) 或 `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) 拖动到场景中。</span><span class="sxs-lookup"><span data-stu-id="d8f55-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="d8f55-173">这些按钮预制项已配置为提供各种类型的输入（包括明确手部输入和凝视）的音频视觉对象反馈。</span><span class="sxs-lookup"><span data-stu-id="d8f55-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="d8f55-174">预制件本身以及可交互组件中公开的事件可用于触发其他操作[](interactable.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f55-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="d8f55-175">[HandInteractionExample](../example-scenes/hand-interaction-examples.md)场景中的可按下按钮使用 Interactable 的 *OnClick* 事件触发多维数据集颜色的变化。</span><span class="sxs-lookup"><span data-stu-id="d8f55-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="d8f55-176">对于不同类型的输入方法（如凝视、敲击、手部射线，以及通过可按下按钮脚本的物理按钮按下）触发此事件。</span><span class="sxs-lookup"><span data-stu-id="d8f55-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="d8f55-177">可以通过按钮上的 来配置可按下按钮何时触发 *OnClick* `PhysicalPressEventRouter` 事件。</span><span class="sxs-lookup"><span data-stu-id="d8f55-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="d8f55-178">例如，可以将 *OnClick* 设置为在首次按下按钮时启动，而不是按下和释放，只需将"可交互"设置为"单击时事件"*即可。*</span><span class="sxs-lookup"><span data-stu-id="d8f55-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="d8f55-179">若要利用特定的手部输入状态信息，可以使用可按下按钮事件 - Touch *Begin、Touch* *End、Button* *Pressed、Button* *Released。*</span><span class="sxs-lookup"><span data-stu-id="d8f55-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="d8f55-180">但是，这些事件不会在响应敲击、手部射线或眼睛输入时发生。</span><span class="sxs-lookup"><span data-stu-id="d8f55-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="d8f55-181">**若要同时支持近近交互，建议使用 Interactable 的 *OnClick* 事件。**</span><span class="sxs-lookup"><span data-stu-id="d8f55-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="d8f55-182">交互状态</span><span class="sxs-lookup"><span data-stu-id="d8f55-182">Interaction states</span></span>

<span data-ttu-id="d8f55-183">处于空闲状态时，按钮的前盘不可见。</span><span class="sxs-lookup"><span data-stu-id="d8f55-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="d8f55-184">当手指接近或光标从凝视输入指向表面时，前盘的闪烁边框将变为可见。</span><span class="sxs-lookup"><span data-stu-id="d8f55-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="d8f55-185">前板图面上的指指位置有额外的突出显示。</span><span class="sxs-lookup"><span data-stu-id="d8f55-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="d8f55-186">当用手指推入时，前盘会随手移动。</span><span class="sxs-lookup"><span data-stu-id="d8f55-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="d8f55-187">当手指触摸前盘表面时，它会显示一种细微的脉冲效果，提供触摸点的视觉反馈。</span><span class="sxs-lookup"><span data-stu-id="d8f55-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="d8f55-188">在HoloLens 2 shell 样式按钮中，有许多视觉提示和视觉元素，可增强用户对交互的置信度。</span><span class="sxs-lookup"><span data-stu-id="d8f55-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![邻近感应灯](../images/button/ux_button_affordance_proximitylight.jpg) | ![焦点突出显示](../images/button/ux_button_affordance_focushighlight.jpg)  | ![压缩机](../images/button/ux_button_affordance_compression.jpg) | ![触发时脉冲](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="d8f55-193">邻近感应灯</span><span class="sxs-lookup"><span data-stu-id="d8f55-193">Proximity light</span></span> | <span data-ttu-id="d8f55-194">焦点突出显示</span><span class="sxs-lookup"><span data-stu-id="d8f55-194">Focus highlight</span></span> | <span data-ttu-id="d8f55-195">压缩机</span><span class="sxs-lookup"><span data-stu-id="d8f55-195">Compressing cage</span></span> | <span data-ttu-id="d8f55-196">触发时脉冲</span><span class="sxs-lookup"><span data-stu-id="d8f55-196">Pulse on trigger</span></span> |

<span data-ttu-id="d8f55-197">可按下按钮触发细微脉冲效果，该按钮查找 (指针上) 的 *ProximityLight* 对象。</span><span class="sxs-lookup"><span data-stu-id="d8f55-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="d8f55-198">如果找到任何邻近光，则调用 方法，该方法会自动对着色器参数进行动画处理以显示 `ProximityLight.Pulse` 脉冲。</span><span class="sxs-lookup"><span data-stu-id="d8f55-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="d8f55-199">检查器属性</span><span class="sxs-lookup"><span data-stu-id="d8f55-199">Inspector properties</span></span>

![按钮结构](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="d8f55-201">**盒碰撞体** 
 `Box Collider`按钮前板的 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="d8f55-202">**可按下按钮** 按钮移动与手动按下交互的逻辑。</span><span class="sxs-lookup"><span data-stu-id="d8f55-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="d8f55-203">**物理按下事件路由器** 此脚本将事件从手动按下交互发送到 [可交互](interactable.md)的 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="d8f55-204">**可交互** 
[可交互](interactable.md)处理各种类型的交互状态和事件。</span><span class="sxs-lookup"><span data-stu-id="d8f55-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="d8f55-205">HoloLens脚本直接处理凝视、手势和语音输入以及沉浸式头戴显示设备运动控制器输入。</span><span class="sxs-lookup"><span data-stu-id="d8f55-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="d8f55-206">**音频源** 音频反馈剪辑的 Unity 音频源。</span><span class="sxs-lookup"><span data-stu-id="d8f55-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="d8f55-207">*NearInteractionTouchable.cs* 需要使任何对象都能够触摸到已表达的手动输入。</span><span class="sxs-lookup"><span data-stu-id="d8f55-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="d8f55-208">预制布局</span><span class="sxs-lookup"><span data-stu-id="d8f55-208">Prefab layout</span></span>

<span data-ttu-id="d8f55-209">*ButtonContent* 对象包含前板、文本标签和图标。</span><span class="sxs-lookup"><span data-stu-id="d8f55-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="d8f55-210">*FrontPlate* 使用着色器响应索引 *Button_Box邻近性*。</span><span class="sxs-lookup"><span data-stu-id="d8f55-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="d8f55-211">它显示闪烁边框、邻近光和触控脉冲效果。</span><span class="sxs-lookup"><span data-stu-id="d8f55-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="d8f55-212">文本标签是使用 TextMesh Pro。</span><span class="sxs-lookup"><span data-stu-id="d8f55-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="d8f55-213">*SeeItSayItLabel* 的可见性由 [可交互](interactable.md)的主题控制。</span><span class="sxs-lookup"><span data-stu-id="d8f55-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![按钮布局](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="d8f55-215">如何更改图标和文本</span><span class="sxs-lookup"><span data-stu-id="d8f55-215">How to change the icon and text</span></span>

<span data-ttu-id="d8f55-216">MRTK 按钮使用 组件来帮助你更改按钮的 `ButtonConfigHelper` 图标、文本和标签。</span><span class="sxs-lookup"><span data-stu-id="d8f55-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="d8f55-217"> (请注意，如果所选按钮上不存在元素，则某些字段可能不存在。) </span><span class="sxs-lookup"><span data-stu-id="d8f55-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![按钮配置帮助程序](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="d8f55-219">创建和修改图标集</span><span class="sxs-lookup"><span data-stu-id="d8f55-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="d8f55-220">图标 **集** 是组件使用的一组共享图标 `ButtonConfigHelper` 资产。</span><span class="sxs-lookup"><span data-stu-id="d8f55-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="d8f55-221">支持 *三种* 图标样式。</span><span class="sxs-lookup"><span data-stu-id="d8f55-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="d8f55-222">**四** 边形图标使用 在四边形上呈现 `MeshRenderer` 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="d8f55-223">这是默认图标样式。</span><span class="sxs-lookup"><span data-stu-id="d8f55-223">This is the default icon style.</span></span>
* <span data-ttu-id="d8f55-224">**子画面** 图标是使用 呈现的 `SpriteRenderer` 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="d8f55-225">如果希望将图标导入为子画面表，或者希望与 Unity UI 组件共享图标资产，则此功能很有用。</span><span class="sxs-lookup"><span data-stu-id="d8f55-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="d8f55-226">若要使用此样式，需要安装 Sprite 编辑器包 (Windows **-> 程序包管理器 -> 2D 子画面)**</span><span class="sxs-lookup"><span data-stu-id="d8f55-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="d8f55-227">**字符** 图标是使用 组件 `TextMeshPro` 呈现的。</span><span class="sxs-lookup"><span data-stu-id="d8f55-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="d8f55-228">如果希望使用图标字体，这很有用。</span><span class="sxs-lookup"><span data-stu-id="d8f55-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="d8f55-229">若要使用HoloLens图标字体，需要创建字体 `TextMeshPro` 资产。</span><span class="sxs-lookup"><span data-stu-id="d8f55-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="d8f55-230">若要更改按钮使用的样式，请展开 ButtonConfigHelper 中的"图标"下拉列表，然后从"图标样式 *"* 下拉列表中选择 。 </span><span class="sxs-lookup"><span data-stu-id="d8f55-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="d8f55-231">可以使用资产菜单创建新的按钮图标集："创建混合现实 **>"图标Toolkit >设置" 。**</span><span class="sxs-lookup"><span data-stu-id="d8f55-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="d8f55-232">若要添加四边形图标和子画面图标，只需将它们拖动到各自的数组中。</span><span class="sxs-lookup"><span data-stu-id="d8f55-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="d8f55-233">若要添加 Char 图标，必须先创建并分配字体资产。</span><span class="sxs-lookup"><span data-stu-id="d8f55-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="d8f55-234">在 MRTK 2.4 及更中，建议将自定义图标纹理移动到 IconSet 中。</span><span class="sxs-lookup"><span data-stu-id="d8f55-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="d8f55-235">若要将项目中所有按钮上的资产升级到新的推荐格式，请使用 ButtonConfigHelperMigrationHandler。</span><span class="sxs-lookup"><span data-stu-id="d8f55-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="d8f55-236"> (混合现实Toolkit -> 实用工具 -> 迁移窗口 -> 迁移处理程序选择 -> Microsoft.MixedReality。Toolkit。Utilities.ButtonConfigHelperMigrationHandler) </span><span class="sxs-lookup"><span data-stu-id="d8f55-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="d8f55-237">导入升级按钮所需的 Microsoft.MixedRealityToolkit.Unity.Tools 包。</span><span class="sxs-lookup"><span data-stu-id="d8f55-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![升级窗口对话](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="d8f55-239">如果在迁移过程中的默认图标集内找不到图标，将在 MixedRealityToolkit.Generated/CustomIconSets 中创建自定义图标集。</span><span class="sxs-lookup"><span data-stu-id="d8f55-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="d8f55-240">此时会显示一个对话框，指示已发生此状态。</span><span class="sxs-lookup"><span data-stu-id="d8f55-240">A dialog will indicate that this has taken place.</span></span>

![自定义图标通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="d8f55-242">创建HoloLens图标字体资产</span><span class="sxs-lookup"><span data-stu-id="d8f55-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="d8f55-243">首先，将图标字体导入 Unity。</span><span class="sxs-lookup"><span data-stu-id="d8f55-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="d8f55-244">在Windows计算机上，可以在 *HoloLens/Fonts/holomdl2.ttf Windows默认字体。*</span><span class="sxs-lookup"><span data-stu-id="d8f55-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="d8f55-245">将此文件复制并粘贴到"资产"文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d8f55-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="d8f55-246">接下来，通过"窗口"打开 TextMeshPro 字体资产创建者 **> TextMeshPro >"字体资产创建者"。**</span><span class="sxs-lookup"><span data-stu-id="d8f55-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="d8f55-247">下面是用于生成字体图集HoloLens设置。</span><span class="sxs-lookup"><span data-stu-id="d8f55-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="d8f55-248">若要包括所有图标，将以下 Unicode 范围粘贴到 *"字符序列"* 字段中：</span><span class="sxs-lookup"><span data-stu-id="d8f55-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![按钮创建 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="d8f55-250">生成字体资产后，将其保存到项目中，并将其分配给图标集的 *"字符图标字体"* 字段。</span><span class="sxs-lookup"><span data-stu-id="d8f55-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="d8f55-251">现在 *将填充* "可用图标"下拉列表。</span><span class="sxs-lookup"><span data-stu-id="d8f55-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="d8f55-252">若要使图标可供按钮使用，请单击它。</span><span class="sxs-lookup"><span data-stu-id="d8f55-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="d8f55-253">它将被添加到" *所选图标* "下拉列表中，现在会显示在"可以选择为图标 `ButtonConfigHelper.` 提供标记"中。</span><span class="sxs-lookup"><span data-stu-id="d8f55-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="d8f55-254">这允许在运行时设置图标。</span><span class="sxs-lookup"><span data-stu-id="d8f55-254">This enables setting the icon at runtime.</span></span>

![按钮创建 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![按钮创建 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="d8f55-257">若要使用图标集选择按钮，请展开 中的"图标"下拉列表 `ButtonConfigHelper` ，并将其分配给"图标集 *"* 字段。</span><span class="sxs-lookup"><span data-stu-id="d8f55-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![按钮图标集](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="d8f55-259">如何更改按钮的大小</span><span class="sxs-lookup"><span data-stu-id="d8f55-259">How to change the size of a button</span></span>

<span data-ttu-id="d8f55-260">HoloLens 2 shell 样式按钮的大小为 32x32mm。</span><span class="sxs-lookup"><span data-stu-id="d8f55-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="d8f55-261">若要自定义维度，请更改按钮预制件中这些对象的大小：</span><span class="sxs-lookup"><span data-stu-id="d8f55-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="d8f55-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="d8f55-262">**FrontPlate**</span></span>
2. <span data-ttu-id="d8f55-263">**BackPlate** 下的四边形</span><span class="sxs-lookup"><span data-stu-id="d8f55-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="d8f55-264">**根上的** 盒碰撞体</span><span class="sxs-lookup"><span data-stu-id="d8f55-264">**Box Collider** on the root</span></span>

<span data-ttu-id="d8f55-265">然后，单击位于按钮 **根** 目录的 NearInteractionTouchable 脚本中的"修复边界"按钮。</span><span class="sxs-lookup"><span data-stu-id="d8f55-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="d8f55-266">更新 FrontPlate 按钮 ![ 大小自定义项的大小 1](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="d8f55-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="d8f55-267">更新四边形 ![ 按钮大小自定义项的大小 2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="d8f55-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="d8f55-268">更新"盒碰撞体按钮大小 ![ "自定义项的大小 3](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="d8f55-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="d8f55-269">单击"修复边界" ![ 按钮大小自定义项 4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="d8f55-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it"></a><span data-ttu-id="d8f55-270">语音 ("see-it，假设) </span><span class="sxs-lookup"><span data-stu-id="d8f55-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="d8f55-271">**语音输入处理程序** 可 [按下按钮](interactable.md) 中的可交互脚本已实现 `IMixedRealitySpeechHandler` 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="d8f55-272">可以在此处设置语音命令关键字。</span><span class="sxs-lookup"><span data-stu-id="d8f55-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="d8f55-273">**语音输入配置文件** 此外，需要在全局语音命令配置文件 中注册 voice *命令关键字*。</span><span class="sxs-lookup"><span data-stu-id="d8f55-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="d8f55-274">**查看，Say-it 标签** 可按下按钮预制项在 *SeeItSayItLabel* Pro下具有占位符 TextMesh 标签。</span><span class="sxs-lookup"><span data-stu-id="d8f55-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="d8f55-275">可以使用此标签将按钮的语音命令关键字传达给用户。</span><span class="sxs-lookup"><span data-stu-id="d8f55-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="d8f55-276">如何从头开始创建按钮</span><span class="sxs-lookup"><span data-stu-id="d8f55-276">How to make a button from scratch</span></span>

<span data-ttu-id="d8f55-277">可以在 **PressableButtonExample** 场景中找到这些按钮的示例。</span><span class="sxs-lookup"><span data-stu-id="d8f55-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="d8f55-278">1.创建具有多维数据集的可按下按钮 (交互仅) </span><span class="sxs-lookup"><span data-stu-id="d8f55-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="d8f55-279">创建 Unity 多维数据集 (GameObject > 3D 对象>多维数据集) </span><span class="sxs-lookup"><span data-stu-id="d8f55-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="d8f55-280">添加 `PressableButton.cs` 脚本</span><span class="sxs-lookup"><span data-stu-id="d8f55-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="d8f55-281">添加 `NearInteractionTouchable.cs` 脚本</span><span class="sxs-lookup"><span data-stu-id="d8f55-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="d8f55-282">在 `PressableButton` 的"检查器"面板中，将多维数据集对象分配给"**移动按钮视觉对象"。**</span><span class="sxs-lookup"><span data-stu-id="d8f55-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="d8f55-283">选择多维数据集时，对象上将看到多个彩色层。</span><span class="sxs-lookup"><span data-stu-id="d8f55-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="d8f55-284">这会将"按"下的距离值可视化 **设置。**</span><span class="sxs-lookup"><span data-stu-id="d8f55-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="d8f55-285">使用句柄，可以配置何时开始按 (对象) 触发事件。</span><span class="sxs-lookup"><span data-stu-id="d8f55-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="d8f55-286">按下按钮时，它将移动并生成脚本中公开的正确事件，例如 `PressableButton.cs` TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="d8f55-287">故障排除</span><span class="sxs-lookup"><span data-stu-id="d8f55-287">Troubleshooting</span></span>

<span data-ttu-id="d8f55-288">如果按钮正在执行双击，请确保"强制前推"属性处于活动状态，并且"开始推送距离"平面放置在近距 **交互可触摸** 平面的前面。</span><span class="sxs-lookup"><span data-stu-id="d8f55-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="d8f55-289">近 **交互可触摸** 平面由下面 gif 中白色箭头原点前面的蓝色平面指示：</span><span class="sxs-lookup"><span data-stu-id="d8f55-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![突出显示了"强制执行 Front Push"属性的可按下按钮脚本组件](../images/button/MRTK_Button_Enforce_Push.png)

![在近距交互可触摸平面前面移动起始推送距离的动画示例](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="d8f55-292">2.向基本多维数据集按钮添加视觉反馈</span><span class="sxs-lookup"><span data-stu-id="d8f55-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="d8f55-293">MRTK 标准着色器提供各种功能，便于添加视觉反馈。</span><span class="sxs-lookup"><span data-stu-id="d8f55-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="d8f55-294">创建材料并选择着色器 `Mixed Reality Toolkit/Standard` 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="d8f55-295">或者，可以使用或复制下使用 `/SDK/StandardAssets/Materials/` MRTK 标准着色器的现有材料之一。</span><span class="sxs-lookup"><span data-stu-id="d8f55-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="d8f55-296">选中 `Hover Light` " `Proximity Light` 选项 **"下的 Fluent 和**。</span><span class="sxs-lookup"><span data-stu-id="d8f55-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="d8f55-297">这样，鼠标悬停光交互 (近距) 和远距指针 () 视觉反馈。</span><span class="sxs-lookup"><span data-stu-id="d8f55-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="d8f55-298">3.向基本多维数据集按钮添加音频反馈</span><span class="sxs-lookup"><span data-stu-id="d8f55-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="d8f55-299">由于脚本公开 `PressableButton.cs` 了 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 等事件，因此可以轻松分配音频反馈。</span><span class="sxs-lookup"><span data-stu-id="d8f55-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="d8f55-300">只需将 Unity 添加到多维数据集 `Audio Source` 对象，然后选择 AudioSource.PlayOneShot () 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="d8f55-301">可以使用 "文件夹" 下的 MRTK_Select_Main 和 MRTK_Select_Secondary 音频剪辑 `/SDK/StandardAssets/Audio/` 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="d8f55-302">4. 添加可视状态并处理远距离交互事件</span><span class="sxs-lookup"><span data-stu-id="d8f55-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="d8f55-303">[种不可交互](interactable.md) 是一个脚本，可轻松地为各种类型的输入交互创建可视状态。</span><span class="sxs-lookup"><span data-stu-id="d8f55-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="d8f55-304">它还处理远距离交互事件。</span><span class="sxs-lookup"><span data-stu-id="d8f55-304">It also handles far interaction events.</span></span> <span data-ttu-id="d8f55-305">添加 `Interactable.cs` 多维数据集对象并将其拖放到 "**配置文件**" 下的 **目标** 字段。</span><span class="sxs-lookup"><span data-stu-id="d8f55-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="d8f55-306">然后，使用类型 **ScaleOffsetColorTheme** 创建一个新主题。</span><span class="sxs-lookup"><span data-stu-id="d8f55-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="d8f55-307">在此主题下，可以指定特定交互状态的对象的颜色，如 **焦点** 和 **按下** 状态。</span><span class="sxs-lookup"><span data-stu-id="d8f55-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="d8f55-308">还可以控制缩放和偏移量。</span><span class="sxs-lookup"><span data-stu-id="d8f55-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="d8f55-309">检查 **缓动** 并设置持续时间，以使视觉对象过渡平滑。</span><span class="sxs-lookup"><span data-stu-id="d8f55-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![选择配置文件主题](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="d8f55-311">你将看到对象同时响应 (的手 ray 或注视光标) ，并接近 (手型) 交互。</span><span class="sxs-lookup"><span data-stu-id="d8f55-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="d8f55-312">自定义按钮示例</span><span class="sxs-lookup"><span data-stu-id="d8f55-312">Custom button examples</span></span>

<span data-ttu-id="d8f55-313">在 [HandInteractionExample 场景](../example-scenes/hand-interaction-examples.md)中，请参阅使用的钢琴和轮按钮示例 `PressableButton` 。</span><span class="sxs-lookup"><span data-stu-id="d8f55-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="d8f55-314">每个钢琴键均已 `PressableButton` 分配一个和一个 `NearInteractionTouchable` 脚本。</span><span class="sxs-lookup"><span data-stu-id="d8f55-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="d8f55-315">务必验证的 *本地前向* 方向是 `NearInteractionTouchable` 正确的。</span><span class="sxs-lookup"><span data-stu-id="d8f55-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="d8f55-316">它在编辑器中用白色箭头表示。</span><span class="sxs-lookup"><span data-stu-id="d8f55-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="d8f55-317">请确保箭头指向按钮的正面：</span><span class="sxs-lookup"><span data-stu-id="d8f55-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="d8f55-318">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8f55-318">See also</span></span>

* [<span data-ttu-id="d8f55-319">可交互</span><span class="sxs-lookup"><span data-stu-id="d8f55-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="d8f55-320">视觉主题</span><span class="sxs-lookup"><span data-stu-id="d8f55-320">Visual Themes</span></span>](visual-themes.md)
