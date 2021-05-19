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
# <a name="asset-swap-utility"></a><span data-ttu-id="05d02-104">资产交换实用工具</span><span class="sxs-lookup"><span data-stu-id="05d02-104">Asset swap utility</span></span>

<span data-ttu-id="05d02-105">使用文本和内容创建工具时，查找和替换是普遍现象。</span><span class="sxs-lookup"><span data-stu-id="05d02-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="05d02-106">当需要在 Unity 场景中交换多个资产时 [，AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 和编辑器可以在此方面提供帮助。</span><span class="sxs-lookup"><span data-stu-id="05d02-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="05d02-107">该实用工具包含在包 `Microsoft.MixedReality.Toolkit.Unity.Tools` 中。</span><span class="sxs-lookup"><span data-stu-id="05d02-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="05d02-108">将 `AssetSwapUtility` 所有查找和替换操作保存为 ScriptableObject，以便来回交换或保存交换"主题"供将来使用。</span><span class="sxs-lookup"><span data-stu-id="05d02-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="05d02-109">交换资产</span><span class="sxs-lookup"><span data-stu-id="05d02-109">Swapping assets</span></span>

<span data-ttu-id="05d02-110">创建 后，可以轻松交换资产 `AssetSwapCollection` 。</span><span class="sxs-lookup"><span data-stu-id="05d02-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="05d02-111">让我们通过交换场景中的两个红色立方体和两个蓝色球体来演示如何使用。</span><span class="sxs-lookup"><span data-stu-id="05d02-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="05d02-112">首先，将两个红色立方体添加到使用默认 Unity 立方体和材料的 `MRTK_Standard_Red` 场景中。</span><span class="sxs-lookup"><span data-stu-id="05d02-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="05d02-113">若要创建 ， `AssetSwapCollection` 请导航到"**混合现实工具包>实用工具>创建资产交换集合"。**</span><span class="sxs-lookup"><span data-stu-id="05d02-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="05d02-114">选中 `AssetSwapCollection` 后，填写属性，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="05d02-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Unity 编辑器中的资产交换集合](images/asset-swap-img-01.png)

<span data-ttu-id="05d02-116">接下来，从"所选主题"下拉列表中选择"蓝色球体"，然后点击"应用"。</span><span class="sxs-lookup"><span data-stu-id="05d02-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="05d02-117">场景中的所有红色立方体都应替换为蓝色球体。</span><span class="sxs-lookup"><span data-stu-id="05d02-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Unity 编辑器中的资产交换集合，突出显示了所选主题](images/asset-swap-img-02.png)

<span data-ttu-id="05d02-119">此示例中，我们执行了完整的场景替换，但你可以更改"选择模式"来替换场景的一部分。</span><span class="sxs-lookup"><span data-stu-id="05d02-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="05d02-120">还可以从"所选主题"下拉列表中选择"红色多维数据集"，然后再次点击"应用"，交换回红色立方体。</span><span class="sxs-lookup"><span data-stu-id="05d02-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="05d02-121">可以交换任何资产类型，如音频文件、字体、prototyping 等。 `AssetSwapUtility` 将执行几个检查以确保你要交换到类似类型。</span><span class="sxs-lookup"><span data-stu-id="05d02-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>