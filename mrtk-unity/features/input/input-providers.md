---
title: 输入提供程序
description: MRTK 中的不同类型提供程序的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f53932b5e12e60b3638c1d6c31e569016de983ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176751"
---
# <a name="input-providers"></a><span data-ttu-id="7401f-104">输入提供程序</span><span class="sxs-lookup"><span data-stu-id="7401f-104">Input providers</span></span>

<span data-ttu-id="7401f-105">输入提供程序在 **已注册的服务提供程序配置文件** 中注册，该配置文件位于混合现实 Toolkit 组件中：</span><span class="sxs-lookup"><span data-stu-id="7401f-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="7401f-106">这些是现成提供的输入提供程序及其相应的控制器：</span><span class="sxs-lookup"><span data-stu-id="7401f-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="7401f-107">输入提供程序</span><span class="sxs-lookup"><span data-stu-id="7401f-107">Input Provider</span></span> | <span data-ttu-id="7401f-108">Controllers</span><span class="sxs-lookup"><span data-stu-id="7401f-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="7401f-109">模拟手势</span><span class="sxs-lookup"><span data-stu-id="7401f-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="7401f-110">鼠标</span><span class="sxs-lookup"><span data-stu-id="7401f-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="7401f-111">通用 OpenVR、naopak、naopak Knuckles、Oculus Touch、Oculus Remote、Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="7401f-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="7401f-112">通用操纵杆</span><span class="sxs-lookup"><span data-stu-id="7401f-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="7401f-113">Unity 触控控制器</span><span class="sxs-lookup"><span data-stu-id="7401f-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="7401f-114">*无*</span><span class="sxs-lookup"><span data-stu-id="7401f-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="7401f-115">WMR，WMR 控制器，WMR GGV (注视、手势和语音) 手</span><span class="sxs-lookup"><span data-stu-id="7401f-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="7401f-116">*无*</span><span class="sxs-lookup"><span data-stu-id="7401f-116">*None*</span></span> |

<span data-ttu-id="7401f-117">听写和语音提供程序不创建任何控制器，它们直接引发自己的专用输入事件。</span><span class="sxs-lookup"><span data-stu-id="7401f-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="7401f-118">自定义输入提供程序可以通过实现接口来创建 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 。</span><span class="sxs-lookup"><span data-stu-id="7401f-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="7401f-119">有关详细信息，请参阅 [创建输入系统数据提供程序](create-data-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="7401f-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
