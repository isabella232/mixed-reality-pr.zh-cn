---
title: 手部物理服务
description: 在 MRTK 中使用手型物理扩展服务的文档
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f54f8dabddba03bc279a090bf1c62b25656e64109b3b5671a4ed50d070445f14
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221723"
---
# <a name="hand-physics-service"></a>手部物理服务

![手型物理扩展服务](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

手型物理学服务实现了严格的正文冲突事件和与明确的操作的交互。

## <a name="enabling-the-extension"></a>启用扩展

若要启用此扩展，请打开 RegisteredServiceProvider 配置文件。 单击 `Register a new Service Provider` 以添加新配置。 在 "组件类型" 字段中，选择 "HandPhysicsService"。 在 "配置文件" 字段中，选择包含在扩展中的 "默认手型" 物理配置文件。

## <a name="profile-options"></a>配置文件选项

### <a name="hand-physics-layer"></a>手型物理层

控制实例化手形联接将跳到的层。

尽管服务默认为 "默认" 层 (0) ，但建议对现有物理对象使用单独的层。 否则，可能会出现不需要的冲突和/或不准确的 raycasts。

### <a name="finger-tip-kinematic-body-prefab"></a>Finger tip 运动学 prefab

控制可轻松实例化的 prefab。 为了使服务按预期方式工作，prefab 要求：

- 启用了 isKinematic 的刚体组件
- 碰撞器
- `JointKinematicBody` 组件

### <a name="use-palm-kinematic-body"></a>使用掌运动主体

控制服务是否将尝试实例化 palm 接点上的 prefab。

### <a name="palm-kinematic-body-prefab"></a>掌运动正文 prefab

`UsePalmKinematicBody`启用后，这就是它将实例化的 prefab。 就像 `FingerTipKinematicBodyPrefab` 这样，此 prefab 需要：

- 启用了 isKinematic 的刚体组件
- 碰撞器
- `JointKinematicBody` 组件

## <a name="how-to-use-the-service"></a>如何使用服务

启用后，如果启用了) ，请使用任何碰撞器的 `IsTrigger` 属性接收来自所有10位数的冲突事件 (和不要。
