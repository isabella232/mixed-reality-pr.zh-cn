---
title: 脉冲着色器
description: MRTK 中的脉冲着色器的说明。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 0b26242d71bbe080e440f9c52a009e29000ab00b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224205"
---
# <a name="pulse-shader"></a><span data-ttu-id="9b072-104">脉冲着色器</span><span class="sxs-lookup"><span data-stu-id="9b072-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="9b072-106">使用脉冲着色器对表面重建、有向右网格或任何其他网格的视觉脉冲效果进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="9b072-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="9b072-107">着色器和材料</span><span class="sxs-lookup"><span data-stu-id="9b072-107">Shader and material</span></span>

<span data-ttu-id="9b072-108">以下材料使用 **SR_Triangles** 着色器。</span><span class="sxs-lookup"><span data-stu-id="9b072-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="9b072-109">可以配置各种选项，如填充颜色、线条颜色和脉冲颜色。</span><span class="sxs-lookup"><span data-stu-id="9b072-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="9b072-110">**MRTK_Pulse_SpatialMeshBlue**</span><span class="sxs-lookup"><span data-stu-id="9b072-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="9b072-111">**MRTK_Pulse_SpatialMeshPurple**</span><span class="sxs-lookup"><span data-stu-id="9b072-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="9b072-112">**MRTK_Pulse_ArticulatedHandMeshBlue**</span><span class="sxs-lookup"><span data-stu-id="9b072-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="9b072-113">**MRTK_Pulse_ArticulatedHandMeshPurple**</span><span class="sxs-lookup"><span data-stu-id="9b072-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="9b072-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="9b072-114">Prerequisites</span></span>

<span data-ttu-id="9b072-115">对于空间网格示例，请确保在 MixedRealityToolkit 对象（> 空间感知配置文件设置 >）下分配 MRTK_Pulse_SpatialMeshBlue 的 MRTK_Pulse_SpatialMeshPurple。</span><span class="sxs-lookup"><span data-stu-id="9b072-115">For the spatial mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned under MixedRealityToolkit object -> Spatial Awareness Profile -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="9b072-116">对于手写网格示例，请确保在 ArticulatedHandMesh 中分配 MRTK_Pulse_ArticulatedHandMeshBlue MRTK_Pulse_ArticulatedHandMeshPurple。 prefab，这本身应在 MRTK 设置-> 输入-> 手动跟踪-> 手写网格 Prefab 中分配。</span><span class="sxs-lookup"><span data-stu-id="9b072-116">For the hand mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="9b072-117">工作原理</span><span class="sxs-lookup"><span data-stu-id="9b072-117">How it works</span></span>

<span data-ttu-id="9b072-118">手写着色器使用 Uv-11 来沿手写网格地图脉冲，并使手腕淡出。</span><span class="sxs-lookup"><span data-stu-id="9b072-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="9b072-119">Surface 重构着色器使用顶点位置来映射脉冲。</span><span class="sxs-lookup"><span data-stu-id="9b072-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="9b072-120">空间网格示例-PulseShaderSpatialMeshExample</span><span class="sxs-lookup"><span data-stu-id="9b072-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="9b072-121">与 HoloLens 2 shell 体验类似，你可以通过使用手型来指向并使用手型来在空间网格上生成影响效果。</span><span class="sxs-lookup"><span data-stu-id="9b072-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="9b072-122">示例场景包含 ExampleSpatialMesh 对象，该对象是适用于 Unity 游戏模式的测试空间网格数据。</span><span class="sxs-lookup"><span data-stu-id="9b072-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="9b072-123">此对象将在设备上被禁用和隐藏。</span><span class="sxs-lookup"><span data-stu-id="9b072-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="9b072-124">如果为 true，则 **PulseShaderSpatialMeshHandler** 脚本将在点位置对空间网格生成脉冲效果 `PulseOnSelect` 。</span><span class="sxs-lookup"><span data-stu-id="9b072-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="9b072-125">`Auto Pulse`对于重复动画，属性也可在材料本身中设置为 true。</span><span class="sxs-lookup"><span data-stu-id="9b072-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="9b072-126">在示例场景中，此脚本附加到 PulseShaderSpatialMeshParent prefab。</span><span class="sxs-lookup"><span data-stu-id="9b072-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="9b072-127">通过运行时空间网格 Prefab 属性在空间感知配置文件下引用此 prefab。</span><span class="sxs-lookup"><span data-stu-id="9b072-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="9b072-128">在运行时，PulseShaderSpatialMeshParent prefab 和将实例化并添加到空间网格层次结构中 (仅在设备上，不能在编辑器) 中观察到此行为。</span><span class="sxs-lookup"><span data-stu-id="9b072-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="9b072-129">手写网格示例-PulseShaderHandMeshExample</span><span class="sxs-lookup"><span data-stu-id="9b072-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="9b072-130">此示例场景演示了使用脉冲着色器的手写网格可视化。</span><span class="sxs-lookup"><span data-stu-id="9b072-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="9b072-131">HoloLens 设备检测到手时，将触发一次脉冲动画。</span><span class="sxs-lookup"><span data-stu-id="9b072-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="9b072-132">此视觉反馈可提高用户的交互置信度。</span><span class="sxs-lookup"><span data-stu-id="9b072-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="9b072-133">**PulseShaderHandMeshHandler** 脚本会对分配的材料生成脉冲效果。</span><span class="sxs-lookup"><span data-stu-id="9b072-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="9b072-134">默认情况下，选中 "检测到手动脉冲"。</span><span class="sxs-lookup"><span data-stu-id="9b072-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
