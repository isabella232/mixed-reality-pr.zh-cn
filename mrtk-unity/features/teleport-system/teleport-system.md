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
# <a name="teleport-system"></a>传送系统

远程端口系统是 MRTK 的一个子系统，在应用程序使用不透明显示器时处理用户远程传送。 对于 HOLoLens (等 AR 体验) ，远程传送系统不处于活动状态。 对于使用 OpenVR 的沉 (HMD 体验，) 启用 WMR 和远程端口系统。

## <a name="enabling-and-disabling"></a>启用和禁用

可以通过切换其配置文件中的复选框来启用或禁用远程端口系统。
为此，可以在场景中选择 MixedRealityToolkit 对象，单击"Teleport"，然后切换"启用 Teleport 系统"复选框。

还可以在运行时完成此操作：

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

## <a name="events"></a>事件

远程端口系统通过 接口公开事件，以在远程端口操作开始、结束或取消时 [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) 提供信号。
有关事件的机制及其关联的有效负载的详细信息，请参阅链接的 API 文档。

## <a name="usage"></a>使用情况

### <a name="how-to-register-for-teleportation-events"></a>如何注册远程传送事件

下面的代码演示如何创建用于侦听远程传送事件的 MonoBehaviour。 此代码假定已启用远程端口系统。

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

## <a name="teleporting-on-mrtk"></a>MRTK 上的远程传送

若要在具有默认配置的 MR 设备上通过控制器进行远程传送，请使用指纹。 若要使用可表达的手进行远程传送，请用手指朝上手势，同时将索引和滚动块朝外，通过卷起手指完成视区。 若要使用输入模拟进行远程传送，请参阅更新 [后的输入模拟服务文档](../input-simulation/input-simulation-service.md)。

  ![远程端口手势](../images/teleport/handteleport.gif)