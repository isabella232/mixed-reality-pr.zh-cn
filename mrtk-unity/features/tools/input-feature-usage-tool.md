---
title: 输入功能使用情况工具
description: MRTK 中的文档 InputFeatureUsage 工具
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 413d2a3105294411f9c08f4a2add9365389ea783
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176122"
---
# <a name="input-feature-usage-tool"></a><span data-ttu-id="aaf78-104">输入功能使用情况工具</span><span class="sxs-lookup"><span data-stu-id="aaf78-104">Input feature usage tool</span></span>

<span data-ttu-id="aaf78-105">InputFeatureUsage 工具是设备上的运行时 (，或在编辑器) 工具中，它使开发人员能够快速确定检测到的输入源的可用 Unity InputFeatureUsages， (例如，运动控制器或有向清楚表述的) 手写内容。</span><span class="sxs-lookup"><span data-stu-id="aaf78-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="aaf78-106">此场景仅适用于 Unity 2019.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="aaf78-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="aaf78-107">当开发对新硬件控制器的支持时，此工具非常有用。</span><span class="sxs-lookup"><span data-stu-id="aaf78-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="aaf78-108">它还可以帮助确认现有控制器的支持类中存在可疑的控件映射问题。</span><span class="sxs-lookup"><span data-stu-id="aaf78-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![InputFeatureUsage 工具](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="aaf78-110">使用 InputFeatureUsage 工具</span><span class="sxs-lookup"><span data-stu-id="aaf78-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="aaf78-111">若要开始学习 InputFeatureUsage 工具，请导航到 **MRTK/tools/RuntimeTools/tools/InputFeatureUsageTool** 并打开 **InputFeatureUsageTool** 场景。</span><span class="sxs-lookup"><span data-stu-id="aaf78-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="aaf78-112">加载场景后，可以使用播放模式在编辑器中运行项目，也可以在设备上生成并运行该项目。</span><span class="sxs-lookup"><span data-stu-id="aaf78-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="aaf78-113">检查控制器的 Unity 映射：</span><span class="sxs-lookup"><span data-stu-id="aaf78-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="aaf78-114">连接控制器</span><span class="sxs-lookup"><span data-stu-id="aaf78-114">Connect the controller</span></span>
- <span data-ttu-id="aaf78-115">按每个按钮并移动每个轴</span><span class="sxs-lookup"><span data-stu-id="aaf78-115">Press each button and move each axis</span></span>
- <span data-ttu-id="aaf78-116">请注意，显示的功能用法</span><span class="sxs-lookup"><span data-stu-id="aaf78-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="aaf78-117">更新控制器的输入系统数据提供程序中的控件映射</span><span class="sxs-lookup"><span data-stu-id="aaf78-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="aaf78-118">InputFeatureUsage 工具不会将 Microsoft Mixed Reality Toolkit 组件使用。</span><span class="sxs-lookup"><span data-stu-id="aaf78-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="aaf78-119">它直接与 Unity 通信，以确定和显示功能使用情况。</span><span class="sxs-lookup"><span data-stu-id="aaf78-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="aaf78-120">面板</span><span class="sxs-lookup"><span data-stu-id="aaf78-120">Panels</span></span>

<span data-ttu-id="aaf78-121">面板显示所有检测到的 Unity 输入源上所有报告的 InputFeatureUsages 的当前状态。</span><span class="sxs-lookup"><span data-stu-id="aaf78-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="aaf78-122">顶部的小面板会列出所有检测到的源的名称。</span><span class="sxs-lookup"><span data-stu-id="aaf78-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="aaf78-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aaf78-123">See also</span></span>

- [<span data-ttu-id="aaf78-124">创建输入系统数据提供程序</span><span class="sxs-lookup"><span data-stu-id="aaf78-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="aaf78-125">控制器映射工具</span><span class="sxs-lookup"><span data-stu-id="aaf78-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
