---
title: TeleportSystemOverview
description: 有关在 MRTK 中启用和禁用传送系统的概述
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity,HoloLens, HoloLens 2, 混合现实, 开发, MRTK, 传送系统,
ms.openlocfilehash: ee56f62d6e0206249db62d8e7e93cf97cdf8bcc40c35ec0284ebae319870f8ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197637"
---
# <a name="teleport-system"></a>传送系统

传送系统是 MRTK 的子系统，可在应用程序使用不透明显示器时处理用户传送操作。 对于 AR 体验（例如 HoloLens），传送系统处于非活动状态。 对于沉浸式 HMD 体验（OpenVR、WMR），可启用传送系统。

## <a name="enabling-and-disabling"></a>启用和禁用

可通过切换传送系统配置文件上的复选框来启用或禁用传送系统。
为此，可在场景中选择 MixedRealityToolkit 对象，单击“传送”，然后切换“启用传送系统”复选框。

也可在运行时执行此操作：

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

传送系统通过 [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) 界面公开事件，以在传送操作开始、结束或被取消时提供信号。
若要详细了解事件的机制及其关联的有效负载，请查看链接的 API 文档。

## <a name="usage"></a>使用情况

### <a name="how-to-register-for-teleportation-events"></a>如何注册传送事件

下面的代码显示如何创建将侦听传送事件的 MonoBehaviour。 此代码假定已启用传送系统。

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
