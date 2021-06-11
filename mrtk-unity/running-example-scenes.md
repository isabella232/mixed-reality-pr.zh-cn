---
title: 运行示例场景
description: 了解如何获取和使用 MRTK 的示例场景。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: 混合现实工具包，MRTK，示例，HoloLens，HoloLens 2，着色器，工具提示，手动交互，剪辑，边界框，按钮，手形菜单，石板，滑块
ms.openlocfilehash: 8ba4df237189f0de3bd869bc05bdf7e3c5451490
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111911856"
---
# <a name="example-scenes"></a><span data-ttu-id="782b4-104">示例场景</span><span class="sxs-lookup"><span data-stu-id="782b4-104">Example scenes</span></span>

<span data-ttu-id="782b4-105">MRTK 提供各种类型的示例场景，这些场景演示 MRTK 的功能和构建基块以实现空间用户体验。</span><span class="sxs-lookup"><span data-stu-id="782b4-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="782b4-106">遇到和二级示例场景有助于理解这些功能并将其应用于项目。</span><span class="sxs-lookup"><span data-stu-id="782b4-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="782b4-107">如何获取示例场景</span><span class="sxs-lookup"><span data-stu-id="782b4-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="782b4-108">使用混合现实功能工具和 Unity 包管理器</span><span class="sxs-lookup"><span data-stu-id="782b4-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="782b4-109">可以通过 [混合现实功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)下载并导入 **混合现实工具包示例** 包</span><span class="sxs-lookup"><span data-stu-id="782b4-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="782b4-110">在 Unity 中，使用菜单 **窗口 > "包管理器" > 在 "项目 >" 自定义** "，然后选择 **混合现实工具包示例**。</span><span class="sxs-lookup"><span data-stu-id="782b4-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="782b4-111">在面板右侧的列表中，单击示例场景名称旁的 " **导入项目** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="782b4-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="782b4-112">例如，可以单击 "HandTracking" 旁边 **的**"**导入项目**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="782b4-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="782b4-113">导入后，可以在 " **资产 > 示例** " 文件夹下找到它们。</span><span class="sxs-lookup"><span data-stu-id="782b4-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="782b4-114">**HandInteractionExamples** 场景是开始体验 MRTK 的空间交互和 UI 构建基块的好地方。</span><span class="sxs-lookup"><span data-stu-id="782b4-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="782b4-115">直接从 GitHub 下载和导入包</span><span class="sxs-lookup"><span data-stu-id="782b4-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="782b4-116">如果不使用混合现实功能工具，则可以直接从 [MRTK GitHub 的发布页](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)中下载并导入 **MixedReality unitypackage**</span><span class="sxs-lookup"><span data-stu-id="782b4-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="782b4-117">使用 **资产 > 导入包 > 自定义包** 菜单导入 unitypackage。</span><span class="sxs-lookup"><span data-stu-id="782b4-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="782b4-118">导入后，你将能够在 **资产 > MRTK > 示例 > 演示** 中查找示例场景。</span><span class="sxs-lookup"><span data-stu-id="782b4-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>