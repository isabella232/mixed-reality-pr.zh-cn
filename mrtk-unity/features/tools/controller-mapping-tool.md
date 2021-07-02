---
title: 控制器映射工具
description: 有关 MRTK 中的控制器映射工具的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 8c1da7ae6a46bd00599a77b1c4cbb0b2f7baa632
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176171"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="9161c-104">控制器映射工具</span><span class="sxs-lookup"><span data-stu-id="9161c-104">Controller mapping tool</span></span>

<span data-ttu-id="9161c-105">控制器映射工具是 (或编辑器) 工具中的运行时映射，使开发人员能够快速确定硬件控制器的 Unity 输入轴和按钮映射 (例如：运动控制器) 。</span><span class="sxs-lookup"><span data-stu-id="9161c-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="9161c-106">开发对新硬件控制器的支持时，此工具非常有用。</span><span class="sxs-lookup"><span data-stu-id="9161c-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="9161c-107">它还可以帮助确认现有控制器的支持类中存在可疑的控制映射问题。</span><span class="sxs-lookup"><span data-stu-id="9161c-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![控制器映射工具](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="9161c-109">使用控制器映射工具</span><span class="sxs-lookup"><span data-stu-id="9161c-109">Using the controller mapping tool</span></span>

<span data-ttu-id="9161c-110">若要开始使用控制器映射工具，请导航到 **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** 并打开 **ControllerMappingTool** 场景。</span><span class="sxs-lookup"><span data-stu-id="9161c-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="9161c-111">加载场景后，可以使用播放模式在编辑器中运行项目，或在设备上生成和运行项目。</span><span class="sxs-lookup"><span data-stu-id="9161c-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="9161c-112">检查 Unity 的控制器映射：</span><span class="sxs-lookup"><span data-stu-id="9161c-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="9161c-113">连接控制器</span><span class="sxs-lookup"><span data-stu-id="9161c-113">Connect the controller</span></span>
- <span data-ttu-id="9161c-114">按每个按钮并移动每个轴</span><span class="sxs-lookup"><span data-stu-id="9161c-114">Press each button and move each axis</span></span>
- <span data-ttu-id="9161c-115">请注意显示中的映射</span><span class="sxs-lookup"><span data-stu-id="9161c-115">Note the mappings in the display</span></span>
- <span data-ttu-id="9161c-116">更新控制器的输入系统数据提供程序中的控制映射</span><span class="sxs-lookup"><span data-stu-id="9161c-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="9161c-117">控制器映射工具不使用 Microsoft Mixed Reality Toolkit组件。</span><span class="sxs-lookup"><span data-stu-id="9161c-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="9161c-118">它直接与 Unity 通信以确定和显示控件映射。</span><span class="sxs-lookup"><span data-stu-id="9161c-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="9161c-119">显示所有控件</span><span class="sxs-lookup"><span data-stu-id="9161c-119">All controls display</span></span>

<span data-ttu-id="9161c-120">大型显示面板报告所有定义的 Unity 输入轴和按钮的状态，例如 (轴 10，按钮 3) 。</span><span class="sxs-lookup"><span data-stu-id="9161c-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="9161c-121">此面板提供控制器状态的完整视图。</span><span class="sxs-lookup"><span data-stu-id="9161c-121">This panel provides a complete view of the state of the controller.</span></span>

![显示所有控件](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="9161c-123">活动控件显示</span><span class="sxs-lookup"><span data-stu-id="9161c-123">Active controls display</span></span>

<span data-ttu-id="9161c-124">较小的窄显示面板显示 Unity 输入轴和处于活动状态的按钮 (例如：按下按钮) 。</span><span class="sxs-lookup"><span data-stu-id="9161c-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="9161c-125">活动控件显示提供易于阅读的控制器状态摘要视图。</span><span class="sxs-lookup"><span data-stu-id="9161c-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![活动控件显示](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="9161c-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9161c-127">See also</span></span>

- [<span data-ttu-id="9161c-128">创建输入系统数据提供程序</span><span class="sxs-lookup"><span data-stu-id="9161c-128">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="9161c-129">InputFeatureUsage 工具</span><span class="sxs-lookup"><span data-stu-id="9161c-129">InputFeatureUsage tool</span></span>](input-feature-usage-tool.md)
