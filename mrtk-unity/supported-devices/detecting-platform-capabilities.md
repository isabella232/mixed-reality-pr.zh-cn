---
title: 检测PlatformCapabilities
description: MRTK 支持的不同功能的详细信息
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 功能，
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852337"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="868a1-104">检测平台功能</span><span class="sxs-lookup"><span data-stu-id="868a1-104">Detecting platform capabilities</span></span>

<span data-ttu-id="868a1-105">MRTK 的一个常见问题涉及了解 (特定设备，例如Microsoft HoloLens 2) 运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="868a1-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="868a1-106">确定确切的硬件在不同平台上可能很有挑战性。</span><span class="sxs-lookup"><span data-stu-id="868a1-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="868a1-107">相反，MRTK 提供了在运行时识别特定功能的方法， (例如，当前设备终结点是否支持手部) 。</span><span class="sxs-lookup"><span data-stu-id="868a1-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="868a1-108">功能</span><span class="sxs-lookup"><span data-stu-id="868a1-108">Capabilities</span></span>

<span data-ttu-id="868a1-109">混合现实工具包提供 枚举，该枚举定义应用程序可在运行时查询的一组 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 功能。</span><span class="sxs-lookup"><span data-stu-id="868a1-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="868a1-110">输入系统功能</span><span class="sxs-lookup"><span data-stu-id="868a1-110">Input system capabilities</span></span>

<span data-ttu-id="868a1-111">默认 MRTK 输入系统支持查询以下功能：</span><span class="sxs-lookup"><span data-stu-id="868a1-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="868a1-112">功能</span><span class="sxs-lookup"><span data-stu-id="868a1-112">Capability</span></span> | <span data-ttu-id="868a1-113">说明</span><span class="sxs-lookup"><span data-stu-id="868a1-113">Description</span></span> |
|---|---|
| <span data-ttu-id="868a1-114">HandHand</span><span class="sxs-lookup"><span data-stu-id="868a1-114">ArticulatedHand</span></span> | <span data-ttu-id="868a1-115">表达手部输入</span><span class="sxs-lookup"><span data-stu-id="868a1-115">Articulated hand input</span></span> |
| <span data-ttu-id="868a1-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="868a1-116">EyeTracking</span></span> | <span data-ttu-id="868a1-117">眼睛凝视目标</span><span class="sxs-lookup"><span data-stu-id="868a1-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="868a1-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="868a1-118">GGVHand</span></span> | <span data-ttu-id="868a1-119">凝视手势-语音手部输入</span><span class="sxs-lookup"><span data-stu-id="868a1-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="868a1-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="868a1-120">MotionController</span></span> | <span data-ttu-id="868a1-121">运动控制器输入</span><span class="sxs-lookup"><span data-stu-id="868a1-121">Motion controller input</span></span> |
| <span data-ttu-id="868a1-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="868a1-122">VoiceCommand</span></span> | <span data-ttu-id="868a1-123">使用应用定义的关键字的语音命令</span><span class="sxs-lookup"><span data-stu-id="868a1-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="868a1-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="868a1-124">VoiceDictation</span></span> | <span data-ttu-id="868a1-125">语音到文本听写</span><span class="sxs-lookup"><span data-stu-id="868a1-125">Voice to text dictation</span></span> |

<span data-ttu-id="868a1-126">下面的示例代码检查输入系统是否已加载数据提供程序，并支持有表述的指针。</span><span class="sxs-lookup"><span data-stu-id="868a1-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="868a1-127">空间感知功能</span><span class="sxs-lookup"><span data-stu-id="868a1-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="868a1-128">默认的 MRTK 空间感知系统支持查询以下功能：</span><span class="sxs-lookup"><span data-stu-id="868a1-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="868a1-129">功能</span><span class="sxs-lookup"><span data-stu-id="868a1-129">Capability</span></span> | <span data-ttu-id="868a1-130">说明</span><span class="sxs-lookup"><span data-stu-id="868a1-130">Description</span></span> |
|---|---|
| <span data-ttu-id="868a1-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="868a1-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="868a1-132">空间网格</span><span class="sxs-lookup"><span data-stu-id="868a1-132">Spatial meshes</span></span> |
| <span data-ttu-id="868a1-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="868a1-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="868a1-134">空间平面</span><span class="sxs-lookup"><span data-stu-id="868a1-134">Spatial planes</span></span> |
| <span data-ttu-id="868a1-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="868a1-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="868a1-136">空间点</span><span class="sxs-lookup"><span data-stu-id="868a1-136">Spatial points</span></span> |

<span data-ttu-id="868a1-137">此示例将检查空间感知系统是否已加载支持空间网格的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="868a1-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="868a1-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="868a1-138">See also</span></span>

- [<span data-ttu-id="868a1-139">IMixedRealityCapabilityCheck API 文档</span><span class="sxs-lookup"><span data-stu-id="868a1-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="868a1-140">MixedRealityCapability 枚举文档</span><span class="sxs-lookup"><span data-stu-id="868a1-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
