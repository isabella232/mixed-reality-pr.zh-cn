---
title: 手部物理服务
description: 文档：在 MRTK 中使用手部物理扩展服务
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176257"
---
# <a name="hand-physics-service"></a>手部物理服务

![手部物理扩展服务](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

手部物理服务支持严格的人体碰撞事件，以及与手部表达的交互。

## <a name="enabling-the-extension"></a>启用扩展

若要启用扩展，请打开 RegisteredServiceProvider 配置文件。 单击 `Register a new Service Provider` 以添加新配置。 在组件类型字段中，选择"HandPhysicsService"。 在"配置文件"字段中，选择扩展中包含的默认手部物理配置文件。

## <a name="profile-options"></a>配置文件选项

### <a name="hand-physics-layer"></a>手部物理层

控制实例化手部将转到的层。

虽然服务默认为"默认"层 (0) ，但建议为手部物理对象使用单独的层。 否则，可能有不需要的碰撞和/或不准确的光线广播。

### <a name="finger-tip-kinematic-body-prefab"></a>手指尖运动性人体预制

控制在触手可及时实例化预制项。 为了使服务按预期工作，预制项需要：

- 已启用 isKinematic 的刚体组件
- 碰撞体
- `JointKinematicBody` 组件

### <a name="use-palm-kinematic-body"></a>使用手部运动体

控制服务是否尝试实例化手部上的预制。

### <a name="palm-kinematic-body-prefab"></a>手部运动人体预制

启用 `UsePalmKinematicBody` 后，这是它将实例化的预制。 与 `FingerTipKinematicBodyPrefab` 一样，此预制需要：

- 已启用 isKinematic 的刚体组件
- 碰撞体
- `JointKinematicBody` 组件

## <a name="how-to-use-the-service"></a>如何使用服务

启用后，使用碰撞体的任何 属性接收来自所有 10 位数字的碰撞事件 (（如果它们已启用 `IsTrigger`) ）。
