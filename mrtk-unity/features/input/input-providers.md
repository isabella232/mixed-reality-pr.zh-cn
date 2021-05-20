---
title: 输入提供者
description: 有关 MRTK 中不同类型的输入提供程序的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145263"
---
# <a name="input-providers"></a><span data-ttu-id="365c7-104">输入提供程序</span><span class="sxs-lookup"><span data-stu-id="365c7-104">Input providers</span></span>

<span data-ttu-id="365c7-105">输入提供程序在"已注册的 **服务提供商配置文件"中注册**，该配置文件位于混合现实工具包组件中：</span><span class="sxs-lookup"><span data-stu-id="365c7-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="365c7-106">这些是开箱可用的输入提供程序及其相应的控制器：</span><span class="sxs-lookup"><span data-stu-id="365c7-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="365c7-107">输入提供程序</span><span class="sxs-lookup"><span data-stu-id="365c7-107">Input Provider</span></span> | <span data-ttu-id="365c7-108">控制器</span><span class="sxs-lookup"><span data-stu-id="365c7-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="365c7-109">模拟手部</span><span class="sxs-lookup"><span data-stu-id="365c7-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="365c7-110">鼠标</span><span class="sxs-lookup"><span data-stu-id="365c7-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="365c7-111">通用 OpenVR、Vive Wand、Vive Knuckles、Oculus Touch、Oculus Remote、Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="365c7-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="365c7-112">一般时</span><span class="sxs-lookup"><span data-stu-id="365c7-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="365c7-113">Unity 触控控制器</span><span class="sxs-lookup"><span data-stu-id="365c7-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="365c7-114">*无*</span><span class="sxs-lookup"><span data-stu-id="365c7-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="365c7-115">WMR 手部、WMR 控制器、WMR GGV (凝视、手势和语音) 手</span><span class="sxs-lookup"><span data-stu-id="365c7-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="365c7-116">*无*</span><span class="sxs-lookup"><span data-stu-id="365c7-116">*None*</span></span> |

<span data-ttu-id="365c7-117">听写和语音提供程序不会创建任何控制器，它们直接引发自己的专用输入事件。</span><span class="sxs-lookup"><span data-stu-id="365c7-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="365c7-118">可以通过实现 接口创建自定义输入 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 提供程序。</span><span class="sxs-lookup"><span data-stu-id="365c7-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="365c7-119">有关详细信息，请参阅创建 [输入系统数据提供程序](create-data-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="365c7-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
