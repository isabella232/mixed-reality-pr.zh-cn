---
title: 资产交换实用工具
description: 有关在 MRTK for Unity 中使用资产交换实用工具的文档。
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK
ms.openlocfilehash: c277cadffb356b93ffc359233b0b8307f43e8d57
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144130"
---
# <a name="asset-swap-utility"></a>资产交换实用工具

使用文本和内容创建工具时，查找和替换是普遍现象。 当需要在 Unity 场景中交换多个资产时 [，AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 和编辑器可以在此方面提供帮助。 该实用工具包含在包 `Microsoft.MixedReality.Toolkit.Unity.Tools` 中。

将 `AssetSwapUtility` 所有查找和替换操作保存为 ScriptableObject，以便来回交换或保存交换"主题"供将来使用。

## <a name="swapping-assets"></a>交换资产

创建 后，可以轻松交换资产 `AssetSwapCollection` 。 让我们通过交换场景中的两个红色立方体和两个蓝色球体来演示如何使用。 首先，将两个红色立方体添加到使用默认 Unity 立方体和材料的 `MRTK_Standard_Red` 场景中。

若要创建 ， `AssetSwapCollection` 请导航到"**混合现实工具包>实用工具>创建资产交换集合"。** 选中 `AssetSwapCollection` 后，填写属性，如下图所示：

![Unity 编辑器中的资产交换集合](images/asset-swap-img-01.png)

接下来，从"所选主题"下拉列表中选择"蓝色球体"，然后点击"应用"。 场景中的所有红色立方体都应替换为蓝色球体。

![Unity 编辑器中的资产交换集合，突出显示了所选主题](images/asset-swap-img-02.png)

此示例中，我们执行了完整的场景替换，但你可以更改"选择模式"来替换场景的一部分。 还可以从"所选主题"下拉列表中选择"红色多维数据集"，然后再次点击"应用"，交换回红色立方体。

> [!NOTE]
> 可以交换任何资产类型，如音频文件、字体、prototyping 等。 `AssetSwapUtility` 将执行几个检查以确保你要交换到类似类型。