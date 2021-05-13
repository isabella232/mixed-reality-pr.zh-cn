---
title: Controllers
description: 如何在 MRTK 中使用控制器
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 控制器，
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850333"
---
# <a name="controllers"></a><span data-ttu-id="5bce0-104">控制器</span><span class="sxs-lookup"><span data-stu-id="5bce0-104">Controllers</span></span>

<span data-ttu-id="5bce0-105">控制器由输入提供程序 自动创建 [**和销毁**](input-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="5bce0-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="5bce0-106">每个控制器类型都有一些由轴类型定义的物理输入，告诉我们输入值 (（数字、单轴、双轴、六 Dof、...) ）的数据类型，以及描述输入来源的输入类型 *(* Button Press、Trigger、Thumb Stick、Spatial Pointer...) 。</span><span class="sxs-lookup"><span data-stu-id="5bce0-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="5bce0-107">物理输入通过"控制器输入映射配置文件"（位于混合现实工具包组件中的"输入 *系统* 配置文件"下）映射到输入操作。</span><span class="sxs-lookup"><span data-stu-id="5bce0-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

<span data-ttu-id="5bce0-108">安装 [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 包时，MRTK 将自动检测 WMR 控制器并显示它们。</span><span class="sxs-lookup"><span data-stu-id="5bce0-108">MRTK will automatically detect WMR controllers and display them when the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package is installed.</span></span> <span data-ttu-id="5bce0-109">控制器模型仅在使用 OpenXR 管道时显示在编辑器中。</span><span class="sxs-lookup"><span data-stu-id="5bce0-109">Controllers models will only show up in the editor when using the OpenXR pipeline.</span></span> <span data-ttu-id="5bce0-110">若要可视化 Oculus 控制器模型，请按照 [Oculus Quest 部署说明进行操作](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="5bce0-110">To visualize Oculus controller models, follow the [Oculus Quest deployment instructions](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span></span>

![控制器输入映射](../images/input/ControllerInputMapping.png)