---
title: Unity 中的失跟
description: 了解如何在 Unity 混合现实应用中处理手动和默认跟踪丢失。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，跟踪丢失，跟踪丢失图像，轮询，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: fe11c88bec60042901bd7ebb5c55116da97b6e28f0e44e889ef517a03d67245a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211349"
---
# <a name="tracking-loss-in-unity"></a>Unity 中的失跟

当设备在世界各地找不到自己时，应用程序会遇到 "跟踪丢失" 的情况。 默认情况下，Unity 将暂停更新循环，并在跟踪丢失时向用户显示一个初始映像。 重新获得跟踪后，初始映像将消失，更新循环将继续。

作为替代方法，用户可以通过选择退出设置来手动处理此转换。 如果未执行任何处理操作，则所有内容似乎会在跟踪丢失时变为正文锁定状态。

## <a name="default-handling"></a>默认处理

默认情况下，更新循环和所有消息和事件将在跟踪丢失期间停止。 同时，系统会向用户显示一个映像。 可以通过以下方式自定义此映像：转到 "编辑"-">设置->播放机，单击" 闪屏 "，并设置" 全息跟踪丢失 "图像。

## <a name="manual-handling"></a>手动处理

若要手动处理跟踪丢失情况，需要执行 "**编辑**  >  **Project 设置**  >  **Player**  >  "**通用 Windows 平台设置 "选项卡**  >  上的" 设置 "选项卡 **启动图像**  >  **Windows 全息**，并取消选中" 跟踪丢失时暂停和显示图像 "。 此后，需要处理跟踪更改和下面指定的 Api。

**命名空间：** *UnityEngine. XR*<br>
**类型：** *WorldManager*

* 全局管理器公开一个事件，以检测 (*OnPositionalLocatorStateChanged*) 的跟踪丢失/获得的情况，并使用属性来查询当前状态 (*WorldManager*) 
* 当跟踪状态处于不活动状态时，即使用户翻译，照相机也不会在虚拟世界中进行转换。 对象将不再与任何物理位置相对应，并且所有对象都将显示为 "已锁定"。

处理自己的跟踪更改时，需要轮询每个帧的状态属性，或处理 *OnPositionalLocatorStateChanged* 事件。

### <a name="polling"></a>轮询

最重要的状态为 *PositionalLocatorState*，这意味着跟踪功能完全正常。 任何其他状态将仅导致对主相机的循环增量。 例如：

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>处理 OnPositionalLocatorStateChanged 事件

更方便的是，还可以订阅 *OnPositionalLocatorStateChanged* 来处理转换：

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>另请参阅

* [在 DirectX 中处理跟踪丢失](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
