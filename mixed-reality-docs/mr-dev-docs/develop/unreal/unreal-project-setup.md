---
title: 设置 Unreal 项目
description: 了解如何使用最新版 Unreal Engine 和混合现实功能工具设置项目。
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, 混合现实, 开发, 功能, 新项目, 仿真器, 文档, 指南, 全息影像, 游戏开发, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394611"
---
# <a name="setting-up-your-unreal-project"></a><span data-ttu-id="8e938-104">设置 Unreal 项目</span><span class="sxs-lookup"><span data-stu-id="8e938-104">Setting up your Unreal project</span></span>

<span data-ttu-id="8e938-105">建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。</span><span class="sxs-lookup"><span data-stu-id="8e938-105">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="8e938-106">转到 Epic Games Launcher 的“库”选项卡，选择“启动”旁的下拉箭头，然后单击“选项”。  </span><span class="sxs-lookup"><span data-stu-id="8e938-106">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="8e938-107">在“目标平台”下，选择“HoloLens 2”，然后单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="8e938-107">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="8e938-108">![Unreal 安装选项 HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="8e938-108">![Unreal Install Option HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span></span>

## <a name="import-mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="8e938-109">导入 Unreal 的混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="8e938-109">Import Mixed Reality Toolkit for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="8e938-111">混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="8e938-111">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="8e938-112">MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="8e938-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="8e938-113">该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="8e938-113">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="8e938-114">对于安装，我们建议完成策划的 [Unreal 开发历程](unreal-development-overview.md)的[入门部分](unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="8e938-114">For installation, we recommend completing the [Getting Started section](unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](unreal-development-overview.md).</span></span> <span data-ttu-id="8e938-115">如果你已遵循 Unreal 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="8e938-115">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8e938-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 徽标图像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="8e938-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="8e938-117">**混合现实工具包 - Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="8e938-117">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="8e938-118">如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。</span><span class="sxs-lookup"><span data-stu-id="8e938-118">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>