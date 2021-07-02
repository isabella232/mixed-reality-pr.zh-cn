---
title: 手动交互示例
description: MRTK 中的手动交互示例
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，手型交互，边界控制，Pressable 按钮，
ms.openlocfilehash: 7926c8bdd525af24a26e2f4c87257dca7628956a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177439"
---
# <a name="hand-interaction-examples"></a><span data-ttu-id="7f12b-104">手动交互示例</span><span class="sxs-lookup"><span data-stu-id="7f12b-104">Hand interaction examples</span></span>

![手动交互示例1](../images/hand-interaction-examples/MRTK_HandInteractionExamples.png)

<span data-ttu-id="7f12b-106">**HandInteractionExamples** 示例场景包含各种类型的交互和 UI 控件，它们突出显示了可表述的手动输入。</span><span class="sxs-lookup"><span data-stu-id="7f12b-106">The **HandInteractionExamples** example scene contains various types of interactions and UI controls that highlight articulated hand input.</span></span> <span data-ttu-id="7f12b-107">借助 MRTK 的输入模拟，你可以在 Unity 编辑器中体验手动跟踪交互。</span><span class="sxs-lookup"><span data-stu-id="7f12b-107">With MRTK's input simulation, you can experience hand-tracking interactions in Unity editor.</span></span> 

<span data-ttu-id="7f12b-108">**HandInteractionExamples** 场景包含在 MRTK 的示例包中。</span><span class="sxs-lookup"><span data-stu-id="7f12b-108">**HandInteractionExamples** scene is included in the MRTK's Examples package.</span></span> <span data-ttu-id="7f12b-109">可以通过 [混合现实功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)来下载和导入 **混合现实 Toolkit 示例** 包</span><span class="sxs-lookup"><span data-stu-id="7f12b-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="7f12b-110">在 Unity 中，使用菜单窗口 > Project > 自定义程序包管理器 >，并选择 **混合现实 Toolkit 示例**。</span><span class="sxs-lookup"><span data-stu-id="7f12b-110">In Unity, use the menu Window > Package Manager > In Project > Custom and select **Mixed Reality Toolkit Examples**.</span></span> <span data-ttu-id="7f12b-111">单击 **HandTracking 旁边的**"**导入到 Project** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="7f12b-111">Click **Import into Project** button next to **Demos - HandTracking**.</span></span> <span data-ttu-id="7f12b-112">你将能够在资产 > Samples 文件夹下找到 **HandInteractionExamples** 场景。</span><span class="sxs-lookup"><span data-stu-id="7f12b-112">You will be able to find **HandInteractionExamples** scene under Assets > Samples folder.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

* <span data-ttu-id="7f12b-113">如果不使用混合现实功能工具，则可以直接下载并导入 **Toolkit MixedReality。unitypackage** 从 [MRTK GitHub 的发布页](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="7f12b-113">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

> [!NOTE]
> <span data-ttu-id="7f12b-114">此示例场景使用 *TextMesh Pro*。</span><span class="sxs-lookup"><span data-stu-id="7f12b-114">This example scene uses *TextMesh Pro*.</span></span> <span data-ttu-id="7f12b-115">若要打开场景，请在导入场景时，单击 *"导入 TMP Essentials"* 。</span><span class="sxs-lookup"><span data-stu-id="7f12b-115">To open the scene, click *'Import TMP Essentials'* when the respective prompt is shown during the import of the scene.</span></span> <span data-ttu-id="7f12b-116">然后，Unity 将 Pro 包中导入 TextMesh。</span><span class="sxs-lookup"><span data-stu-id="7f12b-116">Unity will then import TextMesh Pro packages.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_TMP2.png" width="450" alt="Example TMP2">



<span data-ttu-id="7f12b-117">可以在 **HandInteractionExamples** 场景中体验这些组件</span><span class="sxs-lookup"><span data-stu-id="7f12b-117">You can experience these components in **HandInteractionExamples** scene</span></span>

- [<span data-ttu-id="7f12b-118">可按按钮</span><span class="sxs-lookup"><span data-stu-id="7f12b-118">Pressable button</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="7f12b-119">边界控件</span><span class="sxs-lookup"><span data-stu-id="7f12b-119">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="7f12b-120">对象操控器</span><span class="sxs-lookup"><span data-stu-id="7f12b-120">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)
- [<span data-ttu-id="7f12b-121">平板</span><span class="sxs-lookup"><span data-stu-id="7f12b-121">Slate</span></span>](../ux-building-blocks/slate.md)
- [<span data-ttu-id="7f12b-122">滑块</span><span class="sxs-lookup"><span data-stu-id="7f12b-122">Slider</span></span>](../ux-building-blocks/sliders.md)
- [<span data-ttu-id="7f12b-123">系统键盘</span><span class="sxs-lookup"><span data-stu-id="7f12b-123">System keyboard</span></span>](../ux-building-blocks/system-keyboard.md)
