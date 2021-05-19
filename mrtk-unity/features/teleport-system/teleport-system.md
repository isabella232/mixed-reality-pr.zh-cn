---
title: Teleport 系统概述
description: 在 MRTK 中启用和禁用 Teleport 系统的概述
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Teleport 系统，
ms.openlocfilehash: a44ad1827597dd0b27bc88a9420a3b251f934afd
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144147"
---
# <a name="teleport-system"></a><span data-ttu-id="c79af-104">传送系统</span><span class="sxs-lookup"><span data-stu-id="c79af-104">Teleport System</span></span>

<span data-ttu-id="c79af-105">远程端口系统是 MRTK 的一个子系统，在应用程序使用不透明显示器时处理用户远程传送。</span><span class="sxs-lookup"><span data-stu-id="c79af-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="c79af-106">对于 HOLoLens (等 AR 体验) ，远程传送系统不处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="c79af-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="c79af-107">对于使用 OpenVR 的沉 (HMD 体验，) 启用 WMR 和远程端口系统。</span><span class="sxs-lookup"><span data-stu-id="c79af-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="c79af-108">启用和禁用</span><span class="sxs-lookup"><span data-stu-id="c79af-108">Enabling and disabling</span></span>

<span data-ttu-id="c79af-109">可以通过切换其配置文件中的复选框来启用或禁用远程端口系统。</span><span class="sxs-lookup"><span data-stu-id="c79af-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="c79af-110">为此，可以在场景中选择 MixedRealityToolkit 对象，单击"Teleport"，然后切换"启用 Teleport 系统"复选框。</span><span class="sxs-lookup"><span data-stu-id="c79af-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="c79af-111">还可以在运行时完成此操作：</span><span class="sxs-lookup"><span data-stu-id="c79af-111">This can also be done at runtime:</span></span>

```c#
void DisableTeleportSystem()
{
    CoreServices.TeleportSystem.Disable();
}

void EnableTeleportSystem()
{
    CoreServices.TeleportSystem.Enable();
}
```

## <a name="events"></a><span data-ttu-id="c79af-112">事件</span><span class="sxs-lookup"><span data-stu-id="c79af-112">Events</span></span>

<span data-ttu-id="c79af-113">远程端口系统通过 接口公开事件，以在远程端口操作开始、结束或取消时 [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) 提供信号。</span><span class="sxs-lookup"><span data-stu-id="c79af-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="c79af-114">有关事件的机制及其关联的有效负载的详细信息，请参阅链接的 API 文档。</span><span class="sxs-lookup"><span data-stu-id="c79af-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="c79af-115">使用情况</span><span class="sxs-lookup"><span data-stu-id="c79af-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="c79af-116">如何注册远程传送事件</span><span class="sxs-lookup"><span data-stu-id="c79af-116">How to register for teleportation events</span></span>

<span data-ttu-id="c79af-117">下面的代码演示如何创建用于侦听远程传送事件的 MonoBehaviour。</span><span class="sxs-lookup"><span data-stu-id="c79af-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="c79af-118">此代码假定已启用远程端口系统。</span><span class="sxs-lookup"><span data-stu-id="c79af-118">This code assumes that the teleport system is enabled.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Teleport;
using UnityEngine;

public class TeleportHandlerExample : MonoBehaviour, IMixedRealityTeleportHandler
{
    public void OnTeleportCanceled(TeleportEventData eventData)
    {
        Debug.Log("Teleport Cancelled");
    }

    public void OnTeleportCompleted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Completed");
    }

    public void OnTeleportRequest(TeleportEventData eventData)
    {
        Debug.Log("Teleport Request");
    }

    public void OnTeleportStarted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Started");
    }

    void OnEnable()
    {
        // This is the critical call that registers this class for events. Without this
        // class's IMixedRealityTeleportHandler interface will not be called.
        CoreServices.TeleportSystem.RegisterHandler<IMixedRealityTeleportHandler>(this);
    }

    void OnDisable()
    {
        // Unregistering when disabled is important, otherwise this class will continue
        // to receive teleportation events.
        CoreServices.TeleportSystem.UnregisterHandler<IMixedRealityTeleportHandler>(this);
    }
}
```

## <a name="teleporting-on-mrtk"></a><span data-ttu-id="c79af-119">MRTK 上的远程传送</span><span class="sxs-lookup"><span data-stu-id="c79af-119">Teleporting on MRTK</span></span>

<span data-ttu-id="c79af-120">若要在具有默认配置的 MR 设备上通过控制器进行远程传送，请使用指纹。</span><span class="sxs-lookup"><span data-stu-id="c79af-120">To teleport with a controller on MR devices with default configurations, use the thumbstick.</span></span> <span data-ttu-id="c79af-121">若要使用可表达的手进行远程传送，请用手指朝上手势，同时将索引和滚动块朝外，通过卷起手指完成视区。</span><span class="sxs-lookup"><span data-stu-id="c79af-121">To teleport with articulated hands, make a gesture with your palm facing up with the index and thumb sticking outwards, completing the teleport by curling the index finger.</span></span> <span data-ttu-id="c79af-122">若要使用输入模拟进行远程传送，请参阅更新 [后的输入模拟服务文档](../input-simulation/input-simulation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="c79af-122">To teleport with input simulation, please see our updated [Input Simulation Service documentation](../input-simulation/input-simulation-service.md).</span></span>

  ![远程端口手势](../images/teleport/handteleport.gif)