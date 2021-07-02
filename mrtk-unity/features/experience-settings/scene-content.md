---
title: 混合现实场景内容
description: 有关混合现实场景内容组件的文档
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7ed81352537bec799721b49c4e2d3d55066c5316
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177343"
---
# <a name="mixed-reality-scene-content"></a>混合现实场景内容

将 MRTK 添加到场景时， `MixedRealitySceneContent` 会创建 gameobject。 此对象充当放置和实例化混合现实内容的专用位置，以确保它在许多不同的体验中适当缩放。 gameobject 具有等效的 **MixedRealitySceneContent** monobehavior，可通过对齐 **类型参数进行** 配置。 此参数可以取以下值。

* *AlignWithExperienceScale* - 根据配置文件的 Experience设置 中设置的目标体验缩放和内容偏移量 [来对齐设置](experience-settings.md)
* *AlignWithHeadHeight* - 将内容与用户头部的 y 位置对齐，即主相机的位置。


  ![在编辑器中创建的混合现实场景内容对象](../images/experience-settings/MixedRealitySceneContent.png)
