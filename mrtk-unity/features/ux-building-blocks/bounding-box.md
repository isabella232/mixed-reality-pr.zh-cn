---
title: 边界框
description: MRTK 中的边界框概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 边界框
ms.openlocfilehash: e8e3587ba871e127590a975b688a70db337daa19
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177542"
---
# <a name="bounding-box"></a><span data-ttu-id="1905a-104">边界框</span><span class="sxs-lookup"><span data-stu-id="1905a-104">Bounding box</span></span>

![边界框](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="1905a-106">边界框已弃用，并替换为其后续 [边界控件](bounds-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1905a-106">Bounding box is deprecated and replaced by its successor [bounds control](bounds-control.md).</span></span> <span data-ttu-id="1905a-107">使用 [迁移选项之一](#migrating-to-bounds-control) 升级现有游戏对象。</span><span class="sxs-lookup"><span data-stu-id="1905a-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="1905a-108">该 [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) 脚本提供在混合现实中转换对象的基本功能。</span><span class="sxs-lookup"><span data-stu-id="1905a-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="1905a-109">边界框将在全息影像周围显示一个立方体，以指示它可以进行交互。</span><span class="sxs-lookup"><span data-stu-id="1905a-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="1905a-110">多维数据集的角和边缘上的句柄允许缩放或旋转对象。</span><span class="sxs-lookup"><span data-stu-id="1905a-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="1905a-111">边界框还会响应用户输入。</span><span class="sxs-lookup"><span data-stu-id="1905a-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="1905a-112">例如HoloLens 2，边界框响应手指邻近性，提供视觉反馈以帮助感知与对象的距离。</span><span class="sxs-lookup"><span data-stu-id="1905a-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="1905a-113">可以轻松自定义所有交互和视觉对象。</span><span class="sxs-lookup"><span data-stu-id="1905a-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="1905a-114">有关详细信息，请参阅应用程序[设置中的边界框](/windows/mixed-reality/app-bar-and-bounding-box)Windows 开发人员中心。</span><span class="sxs-lookup"><span data-stu-id="1905a-114">For more information, see [Bounding box and App bar](/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="1905a-115">示例场景</span><span class="sxs-lookup"><span data-stu-id="1905a-115">Example scene</span></span>

<span data-ttu-id="1905a-116">可以在场景中找到边界框配置 `BoundingBoxExamples` 的示例。</span><span class="sxs-lookup"><span data-stu-id="1905a-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="1905a-117">如何使用 Unity Inspector 添加和配置边界框</span><span class="sxs-lookup"><span data-stu-id="1905a-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="1905a-118">将 Box 碰撞体添加到对象</span><span class="sxs-lookup"><span data-stu-id="1905a-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="1905a-119">将 `BoundingBox` 脚本分配给对象</span><span class="sxs-lookup"><span data-stu-id="1905a-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="1905a-120">配置选项，例如"激活"方法 ("检查器 [属性](#inspector-properties) "部分) </span><span class="sxs-lookup"><span data-stu-id="1905a-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="1905a-121"> (可选) 为样式边界框分配预制件HoloLens 2材料[ (请参阅下面的](#handle-styles)处理样式) </span><span class="sxs-lookup"><span data-stu-id="1905a-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="1905a-122">使用 *检查器* 中的 *"* 目标对象"和"边界替代"字段，分配对象中具有多个子组件的特定对象和碰撞体。</span><span class="sxs-lookup"><span data-stu-id="1905a-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![边界框 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="1905a-124">如何在代码中添加和配置边界框</span><span class="sxs-lookup"><span data-stu-id="1905a-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="1905a-125">实例化多维数据集 GameObject</span><span class="sxs-lookup"><span data-stu-id="1905a-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="1905a-126">使用 `BoundingBox` AddComponent 参数将脚本分配给具有碰撞体<> () </span><span class="sxs-lookup"><span data-stu-id="1905a-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="1905a-127">配置选项 (请参阅下面的 [检查](#inspector-properties) 器属性) </span><span class="sxs-lookup"><span data-stu-id="1905a-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="1905a-128"> (可选) 为样式边界框HoloLens 2预制件和材料。</span><span class="sxs-lookup"><span data-stu-id="1905a-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="1905a-129">这仍然需要通过检查器进行分配，因为应该动态加载材料与预制材料。</span><span class="sxs-lookup"><span data-stu-id="1905a-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="1905a-130">不建议使用 Unity 的"资源"文件夹或 [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 动态加载着色器，因为在运行时可能缺少着色器排列。</span><span class="sxs-lookup"><span data-stu-id="1905a-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="1905a-131">示例：使用 MinMaxScaleConstraint 设置最小、最大边界框刻度</span><span class="sxs-lookup"><span data-stu-id="1905a-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="1905a-132">若要设置最小和最大缩放，请使用 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 。</span><span class="sxs-lookup"><span data-stu-id="1905a-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="1905a-133">还可使用 MinMaxScaleConstraint 为 设置最小和最大缩放 [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。</span><span class="sxs-lookup"><span data-stu-id="1905a-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="1905a-134">示例：在游戏对象周围添加边界框</span><span class="sxs-lookup"><span data-stu-id="1905a-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="1905a-135">若要在对象周围添加边界框，只需向该对象 `BoundingBox` 添加组件：</span><span class="sxs-lookup"><span data-stu-id="1905a-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="1905a-136">检查器属性</span><span class="sxs-lookup"><span data-stu-id="1905a-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="1905a-137">“目标对象”</span><span class="sxs-lookup"><span data-stu-id="1905a-137">Target object</span></span>

<span data-ttu-id="1905a-138">此属性指定边界框操作将转换的对象。</span><span class="sxs-lookup"><span data-stu-id="1905a-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="1905a-139">如果未设置对象，则边界框默认为所有者对象。</span><span class="sxs-lookup"><span data-stu-id="1905a-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="1905a-140">边界替代</span><span class="sxs-lookup"><span data-stu-id="1905a-140">Bounds override</span></span>

<span data-ttu-id="1905a-141">为边界计算设置 对象中的盒碰撞体。</span><span class="sxs-lookup"><span data-stu-id="1905a-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="1905a-142">激活行为</span><span class="sxs-lookup"><span data-stu-id="1905a-142">Activation behavior</span></span>

<span data-ttu-id="1905a-143">有几种选项可以激活边界框接口。</span><span class="sxs-lookup"><span data-stu-id="1905a-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="1905a-144">*开始激活*：场景启动后，边界框将变为可见。</span><span class="sxs-lookup"><span data-stu-id="1905a-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="1905a-145">*通过邻近感应激活*：当明确手靠近对象时，边界框将变为可见。</span><span class="sxs-lookup"><span data-stu-id="1905a-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="1905a-146">*通过指针激活*：当边界框以手部射线指针为目标时，该边界框将变为可见。</span><span class="sxs-lookup"><span data-stu-id="1905a-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="1905a-147">*手动激活*：边界框不会自动显示。</span><span class="sxs-lookup"><span data-stu-id="1905a-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="1905a-148">可以通过访问 boundingBox.Active 属性通过脚本手动激活它。</span><span class="sxs-lookup"><span data-stu-id="1905a-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="1905a-149">最小缩放</span><span class="sxs-lookup"><span data-stu-id="1905a-149">Scale minimum</span></span>

<span data-ttu-id="1905a-150">允许的最小小数位。</span><span class="sxs-lookup"><span data-stu-id="1905a-150">The minimum allowed scale.</span></span> <span data-ttu-id="1905a-151">此属性已弃用，最好添加 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 脚本。</span><span class="sxs-lookup"><span data-stu-id="1905a-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="1905a-152">如果添加此脚本，则从该脚本（而不是边界框）取最小小数位。</span><span class="sxs-lookup"><span data-stu-id="1905a-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="1905a-153">缩放最大值</span><span class="sxs-lookup"><span data-stu-id="1905a-153">Scale maximum</span></span>

<span data-ttu-id="1905a-154">允许的最大小数位。</span><span class="sxs-lookup"><span data-stu-id="1905a-154">The maximum allowed scale.</span></span> <span data-ttu-id="1905a-155">此属性已弃用，最好添加 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 脚本。</span><span class="sxs-lookup"><span data-stu-id="1905a-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="1905a-156">如果添加此脚本，则从该脚本（而不是边界框）获得最大规模。</span><span class="sxs-lookup"><span data-stu-id="1905a-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="1905a-157">框显示</span><span class="sxs-lookup"><span data-stu-id="1905a-157">Box display</span></span>

<span data-ttu-id="1905a-158">各种边界框可视化选项。</span><span class="sxs-lookup"><span data-stu-id="1905a-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="1905a-159">如果将"平展轴"设置为"平展自动"，则脚本将禁止沿具有最小范围轴的操作。</span><span class="sxs-lookup"><span data-stu-id="1905a-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="1905a-160">这导致一个 2D 边界框，通常用于精简对象。</span><span class="sxs-lookup"><span data-stu-id="1905a-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="1905a-161">句柄数</span><span class="sxs-lookup"><span data-stu-id="1905a-161">Handles</span></span>

<span data-ttu-id="1905a-162">可以分配材料与预制材料来替代句柄样式。</span><span class="sxs-lookup"><span data-stu-id="1905a-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="1905a-163">如果未分配任何句柄，这些句柄将显示为默认样式。</span><span class="sxs-lookup"><span data-stu-id="1905a-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="1905a-164">事件</span><span class="sxs-lookup"><span data-stu-id="1905a-164">Events</span></span>

<span data-ttu-id="1905a-165">边界框提供以下事件。</span><span class="sxs-lookup"><span data-stu-id="1905a-165">Bounding box provides the following events.</span></span> <span data-ttu-id="1905a-166">此示例使用这些事件播放音频反馈。</span><span class="sxs-lookup"><span data-stu-id="1905a-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="1905a-167">**旋转已启动**：旋转开始时触发。</span><span class="sxs-lookup"><span data-stu-id="1905a-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="1905a-168">**旋转结束**：旋转结束时触发。</span><span class="sxs-lookup"><span data-stu-id="1905a-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="1905a-169">**缩放已** 启动：缩放开始时触发。</span><span class="sxs-lookup"><span data-stu-id="1905a-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="1905a-170">**缩放结束**：缩放结束时触发。</span><span class="sxs-lookup"><span data-stu-id="1905a-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a><span data-ttu-id="1905a-171">句柄样式</span><span class="sxs-lookup"><span data-stu-id="1905a-171">Handle styles</span></span>

<span data-ttu-id="1905a-172">默认情况下，当你仅分配脚本时，它将显示第一代HoloLens [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) 句柄。</span><span class="sxs-lookup"><span data-stu-id="1905a-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="1905a-173">若要HoloLens 2样式句柄，需要分配适当的句柄预制和材料。</span><span class="sxs-lookup"><span data-stu-id="1905a-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![边界框句柄样式](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="1905a-175">下面是样式边界框句柄的预制HoloLens 2和缩放值。</span><span class="sxs-lookup"><span data-stu-id="1905a-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="1905a-176">可以在场景中找到 `BoundingBoxExamples` 此示例。</span><span class="sxs-lookup"><span data-stu-id="1905a-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="1905a-177">处理 (样式设置HoloLens 2设置) </span><span class="sxs-lookup"><span data-stu-id="1905a-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="1905a-178">**处理材料**：BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="1905a-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="1905a-179">**处理抓取材料**：BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="1905a-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="1905a-180">**缩放句柄预制**：MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="1905a-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="1905a-181">**缩放句柄 Slate 预制**：MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="1905a-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="1905a-182">**缩放句柄大小**：0.016 (1.6cm) </span><span class="sxs-lookup"><span data-stu-id="1905a-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="1905a-183">**缩放手柄碰撞体填充**：0.016 (使可抓取碰撞体略大于处理可视) </span><span class="sxs-lookup"><span data-stu-id="1905a-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="1905a-184">**旋转句柄预制**：MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="1905a-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="1905a-185">**旋转句柄大小**：0.016</span><span class="sxs-lookup"><span data-stu-id="1905a-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="1905a-186">**旋转手柄碰撞体填充**：0.016 (使可抓取碰撞体稍微大于处理可视) </span><span class="sxs-lookup"><span data-stu-id="1905a-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="1905a-187">样式 (的邻近HoloLens 2设置) </span><span class="sxs-lookup"><span data-stu-id="1905a-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="1905a-188">根据与手的距离，使用动画显示和隐藏句柄。</span><span class="sxs-lookup"><span data-stu-id="1905a-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="1905a-189">它具有两步缩放动画。</span><span class="sxs-lookup"><span data-stu-id="1905a-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="1905a-190">**邻近效果活动**：启用基于邻近的句柄激活</span><span class="sxs-lookup"><span data-stu-id="1905a-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="1905a-191">**处理中等邻近度**：第一步缩放的距离</span><span class="sxs-lookup"><span data-stu-id="1905a-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="1905a-192">**处理邻近感应**：第 2 步缩放的距离</span><span class="sxs-lookup"><span data-stu-id="1905a-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="1905a-193">**远距**：手超过边界框交互范围时句柄资产的默认缩放值 ("处理中等邻近度"定义的距离。</span><span class="sxs-lookup"><span data-stu-id="1905a-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="1905a-194">默认情况下，使用 0 隐藏句柄) </span><span class="sxs-lookup"><span data-stu-id="1905a-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="1905a-195">**中等比例**：当手位于边界框交互范围内时，句柄资产的缩放值 ("处理近距"定义的距离。</span><span class="sxs-lookup"><span data-stu-id="1905a-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="1905a-196">使用 1 显示正常大小) </span><span class="sxs-lookup"><span data-stu-id="1905a-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="1905a-197">**关闭刻度**：当手在抓取交互范围范围内时，句柄资产 ("句柄邻近度"定义的距离。</span><span class="sxs-lookup"><span data-stu-id="1905a-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="1905a-198">使用 1.x 显示更大的) </span><span class="sxs-lookup"><span data-stu-id="1905a-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="1905a-199">使用操作处理程序使对象可移动</span><span class="sxs-lookup"><span data-stu-id="1905a-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="1905a-200">边界框可以与 结合使用， [`ManipulationHandler.cs`](manipulation-handler.md) 以使用远交互使对象可移动。</span><span class="sxs-lookup"><span data-stu-id="1905a-200">A bounding box can be combined with [`ManipulationHandler.cs`](manipulation-handler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="1905a-201">操作处理程序支持一种和两方交互。</span><span class="sxs-lookup"><span data-stu-id="1905a-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="1905a-202">可以使用[手动跟踪](../input/hand-tracking.md)来与对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="1905a-202">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="1905a-203">为了使边界框边缘在使用远距离交互时以相同的方式运行 [`ManipulationHandler`](manipulation-handler.md) ，建议在操作结束时连接其事件以进行操作  /   `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` ，如以上屏幕截图中所示。</span><span class="sxs-lookup"><span data-stu-id="1905a-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](manipulation-handler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="1905a-204">迁移到边界控件</span><span class="sxs-lookup"><span data-stu-id="1905a-204">Migrating to bounds control</span></span>

<span data-ttu-id="1905a-205">使用 [范围框](bounding-box.md) 的现有 prototyping 和实例可以通过 [迁移窗口](../tools/migration-window.md) 升级到新的边界控件，该窗口是 MRTK 工具包的一部分。</span><span class="sxs-lookup"><span data-stu-id="1905a-205">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="1905a-206">对于升级边界框的单个实例，还会在组件的属性检查器中提供一个迁移选项。</span><span class="sxs-lookup"><span data-stu-id="1905a-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
