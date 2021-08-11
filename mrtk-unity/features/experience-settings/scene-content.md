---
title: 混合现实场景内容
description: 有关混合现实场景内容组件的文档
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 9980c01b47c3d7d451fda886b4645664f06f204da9967c186382878be947d64f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193220"
---
# <a name="mixed-reality-scene-content"></a>混合现实场景内容

将 MRTK 添加到场景时， `MixedRealitySceneContent` 会创建 gameobject。 此对象用作放置和实例化混合现实内容的专用位置，以确保它可以在多个不同的体验中进行适当缩放。 Gameobject 具有等效的 **MixedRealitySceneContent** monobehavior，可通过 **对齐类型** 参数进行配置。 此参数可以采用以下值。

* *AlignWithExperienceScale* -根据配置文件的体验中设置的 **目标体验规模** 和 **内容偏移量** 来对齐内容 [设置](experience-settings.md)
* *AlignWithHeadHeight* -将内容与用户头的 y 位置对齐，这是主摄像机的位置。


  ![在编辑器中创建了混合现实场景内容对象](../images/experience-settings/MixedRealitySceneContent.png)
