---
title: MRTK 中的控制器
description: 有关将各种控制器与 MRTK 一起使用的文档
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，控制器，HP 回音，Oculus，HTC Naopak，动手
ms.openlocfilehash: 111ebf2b1eb26bbef8cde16832f780acfa758595
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743584"
---
# <a name="controllers-in-mrtk"></a><span data-ttu-id="d5d4d-104">MRTK 中的控制器</span><span class="sxs-lookup"><span data-stu-id="d5d4d-104">Controllers in MRTK</span></span>

<span data-ttu-id="d5d4d-105">MRTK 支持许多不同的控制器。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-105">MRTK has support for many different controllers.</span></span> <span data-ttu-id="d5d4d-106">当使用 MRTK 构建的应用程序在兼容的设备上启动时，许多控制器（例如 HTC Naopak Knuckles 和 HTC Naopak Wands）都将在本机工作。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-106">Many controllers, such as HTC Vive Knuckles and HTC Vive Wands, will work natively once an application built with MRTK is launched on the compatible device.</span></span> <span data-ttu-id="d5d4d-107">其他控制器（如 Oculus 请求和 HP 回音 G2 控制器上的明确说明）在 MRTK 识别它们之前需要额外的包。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-107">Other controllers, such as articulated hands on the Oculus Quest and the HP Reverb G2 Controllers, require additional packages before they are recognized by MRTK.</span></span>

<span data-ttu-id="d5d4d-108">本文档将介绍需要安装额外包的常见方案。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-108">This document will describe the common scenarios where extra packages need to be installed.</span></span> <span data-ttu-id="d5d4d-109">有关如何部署到设备的说明，请参阅 [**Hololens/WMR**](./wmr-mrtk.md) 或 [**Oculus 寻找**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) 部署页。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-109">For instructions on how to deploy to your device, see the [**Hololens/WMR**](./wmr-mrtk.md) or [**Oculus Quest**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) deployment pages.</span></span> <span data-ttu-id="d5d4d-110">有关控制器的其他信息，请访问 [**功能页**](../features/input/controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-110">For additional information about controllers, visit the [**features page**](../features/input/controllers.md).</span></span> <span data-ttu-id="d5d4d-111">若要调试控制器的问题，请参阅 [**控制器映射工具**](../features/tools/controller-mapping-tool.md)</span><span class="sxs-lookup"><span data-stu-id="d5d4d-111">To debug issues with controllers, see the [**Controller mapping tool**](../features/tools/controller-mapping-tool.md)</span></span>

## <a name="hp-reverb-g2-controllers"></a><span data-ttu-id="d5d4d-112">HP 回音 G2 控制器</span><span class="sxs-lookup"><span data-stu-id="d5d4d-112">HP Reverb G2 Controllers</span></span>

<span data-ttu-id="d5d4d-113">若要在使用 MRTK 时检测并显示 HP 回音 G2 控制器，请按照以下步骤安装 [**MixedReality**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 包。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-113">To detect and show the HP Reverb G2 controllers when using MRTK, follow these steps to install the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package.</span></span> <span data-ttu-id="d5d4d-114">安装此包后，需要对默认配置文件进行其他更改，使控制器显示在 HP 回音上。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-114">Once this package is installed, no other changes to the default profiles need to be made to have the controllers show up on the HP Reverb.</span></span> 

<span data-ttu-id="d5d4d-115">若要在编辑器中显示控制器，需要确保使用的是 [**OpenXR 插件**](/windows/mixed-reality/develop/unity/openxr-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-115">In order to display the controllers in editor, you need to ensure that you are using the using the [**OpenXR Plugin**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span></span>

## <a name="oculus-controllers"></a><span data-ttu-id="d5d4d-116">Oculus 控制器</span><span class="sxs-lookup"><span data-stu-id="d5d4d-116">Oculus Controllers</span></span> 

<span data-ttu-id="d5d4d-117">若要可视化 Oculus 控制器模型，请按照 Oculus 寻找部署说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-117">To visualize Oculus controller models, follow the Oculus Quest deployment instructions.</span></span> <span data-ttu-id="d5d4d-118">如果要在使用控制器时显示虚拟指针，请确保在 XR SDK Oculus Device Manager 下选中 " **呈现头像" 而非 "控制器** "。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-118">If you wish to show virtual hands when using the controllers, make sure that **Render Avatar Hands Instead Of Controllers** is checked under the XR SDK Oculus Device Manager.</span></span> <span data-ttu-id="d5d4d-119">否则，请取消选中此选项。</span><span class="sxs-lookup"><span data-stu-id="d5d4d-119">Otherwise, uncheck this option.</span></span>

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)