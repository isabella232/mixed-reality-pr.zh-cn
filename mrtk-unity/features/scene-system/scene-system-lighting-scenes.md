---
title: 场景系统照明场景
description: 有关场景中的照明的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 407813f52044d3405e5045f64817d87c4f3e4b59ddfd87308586ac2d81924674
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202565"
---
# <a name="lighting-scene-operations"></a>光照场景操作

在启动时加载配置文件中定义的默认照明场景。 在调用之前，该照明场景将保持加载状态 `SetLightingScene` 。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>照明设置转换

`transitionType` 控制过渡到新光源场景的样式。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

可用样式包括：

类型 | 说明 | 持续时间
--- | --- | ---
无 | 上一个光照场景已卸载，将加载新的照明场景。 无转换。 | 忽略
FadeToBlack | 上一个光照场景淡出为黑色。 加载新的照明场景，然后从黑色上褪色。 适用于位置间的平滑转换。 | 已使用
CrossFade | 当新的照明场景淡入时，上一个光照场景将淡出。 对于同一位置的照明设置之间的平滑转换很有用。 | 已使用

请注意，在转换过程中不能插值某些照明设置。 如果希望平滑视觉对象的转换，这些设置必须保持一致。

设置 | 平滑 FadeToBlack 转换 | 平滑 CrossFade 转换
--- | --- | ---
Skybox | 否 | 否
自定义反射 | 否 | 否
Sun 轻型实时阴影 | 是 | 否
