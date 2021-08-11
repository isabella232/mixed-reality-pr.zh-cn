---
title: 资产交换实用工具
description: 有关使用 MRTK for Unity 中的资产交换实用工具的文档。
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK
ms.openlocfilehash: 3322087f9027f46b39be07f5368cd8ae4ca875f206984fb823f9b1c8590f86f6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196259"
---
# <a name="asset-swap-utility"></a>资产交换实用工具

"查找和替换" 在使用文本和内容创建工具时无处不在。 当你需要在 Unity 场景中交换多个资产时， [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 和 editor 可以获得一个手型。 此实用程序包含在 `Microsoft.MixedReality.Toolkit.Unity.Tools` 包中。

将 `AssetSwapUtility` 所有查找和替换操作保存为 ScriptableObject，以便 trival 来回交换或保存交换的 "主题" 以供将来使用。

## <a name="swapping-assets"></a>交换资产

一旦创建，就可以轻松交换资产 `AssetSwapCollection` 。 让我们通过交换场景中两个蓝色球的两个红色立方体来演示使用。 首先将两个红多维数据集添加到使用默认 Unity 多维数据集和材料的场景中 `MRTK_Standard_Red` 。

若要创建 `AssetSwapCollection` ，请导航到 **混合现实 Toolkit > 实用工具 > 创建资产交换集合**。 `AssetSwapCollection`按下图所示填充属性：

![Unity 编辑器中的资产交换集合](images/asset-swap-img-01.png)

接下来，从 "所选主题" 下拉列表中选择 "蓝球"，并单击 "应用"。 场景中的所有红色立方体都应该替换为蓝色球。

![在 Unity 编辑器中突出显示选定主题的资产交换集合](images/asset-swap-img-02.png)

在此示例中，我们执行了完整的场景替换，但你可以通过更改 "选择模式" 来替换场景的某些部分。 还可以通过从 "选择的主题" 下拉列表中选择 "红色多维数据集"，并再次按 "应用" 来交换到红色多维数据集。

> [!NOTE]
> 可以交换任何资产类型，如音频文件、字体、prototyping 等。 `AssetSwapUtility` 将执行几个检查以确保你要交换到类似类型。
