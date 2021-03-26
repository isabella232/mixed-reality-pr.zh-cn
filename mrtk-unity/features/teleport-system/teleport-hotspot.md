---
title: TeleportHotspot
description: 有关 MRTK 中传送热点组件的文档
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，传送系统，传送热点
ms.openlocfilehash: 986105dd771c38b1e26fd9f86df90224110591a4
ms.sourcegitcommit: 4be6f36df9063ccfdce2662e299accc7406b6779
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105582950"
---
# <a name="teleport-hotspot-experimental"></a><span data-ttu-id="26113-104">传送热点 [实验]</span><span class="sxs-lookup"><span data-stu-id="26113-104">Teleport Hotspot [Experimental]</span></span>

<span data-ttu-id="26113-105">传送热点是可以添加到 gameobject 的组件，用于确保用户在传送到该位置时处于特定位置和方向。</span><span class="sxs-lookup"><span data-stu-id="26113-105">The teleport hotspot is a component you can add to your gameobject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

## <a name="usage"></a><span data-ttu-id="26113-106">使用情况</span><span class="sxs-lookup"><span data-stu-id="26113-106">Usage</span></span>

### <a name="how-to-create-a-teleport-hotspot"></a><span data-ttu-id="26113-107">如何创建传送热点</span><span class="sxs-lookup"><span data-stu-id="26113-107">How to create a teleport hotspot</span></span>

<span data-ttu-id="26113-108">若要创建传送热点，请将 TeleportHotspot 组件添加到对象，该对象也有一个碰撞器组件。</span><span class="sxs-lookup"><span data-stu-id="26113-108">To create a teleport hotspot, add the TeleportHotspot component to an object which also has a collider component.</span></span> 

![传送热点组件](../images/teleport/TeleportHotspotComponent.png)

<span data-ttu-id="26113-110">现在，在通过 TeleportHotspot 时，传送指针的指示器会改变颜色。</span><span class="sxs-lookup"><span data-stu-id="26113-110">Now, the teleport pointer's indicator will change color when it's directed over a TeleportHotspot.</span></span> <span data-ttu-id="26113-111">当传送操作在热点上完成时，用户将传送到 TeleportHotspot 的中心。</span><span class="sxs-lookup"><span data-stu-id="26113-111">When the teleport action is completed over the hotspot, the user will teleport to the center of the TeleportHotspot.</span></span>

<span data-ttu-id="26113-112">如果勾选了覆盖方向标志，则用户的方向将与传送热点的方向匹配。</span><span class="sxs-lookup"><span data-stu-id="26113-112">If the override orientation flag is checked off, the user's orientation will match that of the teleport hotspot.</span></span>

![传送热点示例](../images/teleport/TeleportHotspotExample.gif)
