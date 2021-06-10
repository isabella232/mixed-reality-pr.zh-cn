---
title: BoundsControl
description: MRTK 中的边界控制概述
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，边界控制，
ms.openlocfilehash: 65558861955f782cf9d81a8bb4ec3a31dee03fde
ms.sourcegitcommit: 95ea5f3cf873acc93c4614fbccaa093e0f5186f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2021
ms.locfileid: "110487724"
---
# <a name="bounds-control"></a><span data-ttu-id="a1aec-104">边界控件</span><span class="sxs-lookup"><span data-stu-id="a1aec-104">Bounds control</span></span>

![边界控件](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="a1aec-106">*BoundsControl* 是先前在 *BoundingBox* 中找到的操作行为的新组件。</span><span class="sxs-lookup"><span data-stu-id="a1aec-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="a1aec-107">界限控制在安装中做出了大量改进和简化，并添加了新功能。</span><span class="sxs-lookup"><span data-stu-id="a1aec-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="a1aec-108">此组件替换为不推荐使用的边界框。</span><span class="sxs-lookup"><span data-stu-id="a1aec-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="a1aec-109">该 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 脚本提供了用于在混合现实中转换对象的基本功能。</span><span class="sxs-lookup"><span data-stu-id="a1aec-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="a1aec-110">边界控件将在全息图周围显示一个框，以指示可以与交互。</span><span class="sxs-lookup"><span data-stu-id="a1aec-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="a1aec-111">框的角部和边缘上的控点允许缩放、旋转或平移对象。</span><span class="sxs-lookup"><span data-stu-id="a1aec-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="a1aec-112">边界控件也会对用户输入做出反应。</span><span class="sxs-lookup"><span data-stu-id="a1aec-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="a1aec-113">例如，在 HoloLens 2 上，边界控制响应手指邻近，提供可视反馈以帮助感觉与对象的距离。</span><span class="sxs-lookup"><span data-stu-id="a1aec-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="a1aec-114">可以轻松地自定义所有交互和视觉对象。</span><span class="sxs-lookup"><span data-stu-id="a1aec-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="a1aec-115">示例场景</span><span class="sxs-lookup"><span data-stu-id="a1aec-115">Example scene</span></span>

<span data-ttu-id="a1aec-116">可以在场景中找到界限控制配置的示例 `BoundsControlExamples` 。</span><span class="sxs-lookup"><span data-stu-id="a1aec-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="a1aec-117">检查器属性</span><span class="sxs-lookup"><span data-stu-id="a1aec-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="a1aec-118">“目标对象”</span><span class="sxs-lookup"><span data-stu-id="a1aec-118">Target object</span></span>

<span data-ttu-id="a1aec-119">此属性指定将由边界控制操作转换的对象。</span><span class="sxs-lookup"><span data-stu-id="a1aec-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="a1aec-120">如果未设置对象，则默认为 owner 对象。</span><span class="sxs-lookup"><span data-stu-id="a1aec-120">If no object is set, it defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="a1aec-121">激活行为</span><span class="sxs-lookup"><span data-stu-id="a1aec-121">Activation behavior</span></span>

<span data-ttu-id="a1aec-122">有几个选项可用于激活边界控制接口。</span><span class="sxs-lookup"><span data-stu-id="a1aec-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="a1aec-123">*启动时激活*：启动场景后，边界控制就变得可见。</span><span class="sxs-lookup"><span data-stu-id="a1aec-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="a1aec-124">"*按邻近范围激活*"：当有向右指的可表述的手势接近对象时，边界控件变为可见。</span><span class="sxs-lookup"><span data-stu-id="a1aec-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="a1aec-125">*按指针激活*：边界控件在面向手形指针时变为可见。</span><span class="sxs-lookup"><span data-stu-id="a1aec-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="a1aec-126">*通过邻近感应和指针激活*：边界控件在处于手形指针的目标时变为可见，或在靠近对象的右侧显示。</span><span class="sxs-lookup"><span data-stu-id="a1aec-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="a1aec-127">*手动激活*：边界控件不会自动变得可见。</span><span class="sxs-lookup"><span data-stu-id="a1aec-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="a1aec-128">可以通过在脚本中访问 boundsControl 属性来手动激活它。</span><span class="sxs-lookup"><span data-stu-id="a1aec-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="a1aec-129">界限重写</span><span class="sxs-lookup"><span data-stu-id="a1aec-129">Bounds override</span></span>

<span data-ttu-id="a1aec-130">设置从对象进行边界计算的框碰撞器。</span><span class="sxs-lookup"><span data-stu-id="a1aec-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="a1aec-131">框填充</span><span class="sxs-lookup"><span data-stu-id="a1aec-131">Box padding</span></span>

<span data-ttu-id="a1aec-132">向用于计算控件范围的碰撞器边界添加填充。</span><span class="sxs-lookup"><span data-stu-id="a1aec-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="a1aec-133">这不仅会影响交互，还会影响视觉对象。</span><span class="sxs-lookup"><span data-stu-id="a1aec-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="a1aec-134">平展轴</span><span class="sxs-lookup"><span data-stu-id="a1aec-134">Flatten axis</span></span>

<span data-ttu-id="a1aec-135">指示控件是否在一个轴中平展，使其成为二维，并在该轴上禁用操作。</span><span class="sxs-lookup"><span data-stu-id="a1aec-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="a1aec-136">此功能可用于清单等精简对象。</span><span class="sxs-lookup"><span data-stu-id="a1aec-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="a1aec-137">如果将 "平展轴" 设置为 " *平整自动* "，脚本会自动选取最小范围的轴作为拼合轴。</span><span class="sxs-lookup"><span data-stu-id="a1aec-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="a1aec-138">平滑处理</span><span class="sxs-lookup"><span data-stu-id="a1aec-138">Smoothing</span></span>

<span data-ttu-id="a1aec-139">"平滑" 部分允许配置控件缩放和旋转的平滑行为。</span><span class="sxs-lookup"><span data-stu-id="a1aec-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="a1aec-140">视觉对象</span><span class="sxs-lookup"><span data-stu-id="a1aec-140">Visuals</span></span>

<span data-ttu-id="a1aec-141">可以通过修改相应的视觉对象配置之一来配置边界控件的外观。</span><span class="sxs-lookup"><span data-stu-id="a1aec-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="a1aec-142">视觉对象配置可以是链接或内联的可编写脚本的对象，并在 " [配置对象" 部分](#configuration-objects)更详细地介绍。</span><span class="sxs-lookup"><span data-stu-id="a1aec-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="a1aec-143">配置对象</span><span class="sxs-lookup"><span data-stu-id="a1aec-143">Configuration Objects</span></span>

<span data-ttu-id="a1aec-144">控件附带一组配置对象，这些对象可存储为可编脚本的对象，并在不同的实例或 prototyping 之间共享。</span><span class="sxs-lookup"><span data-stu-id="a1aec-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="a1aec-145">配置可以作为单个可编脚本的资产文件或 prototyping 中嵌套的可编脚本的资产来共享和链接。</span><span class="sxs-lookup"><span data-stu-id="a1aec-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="a1aec-146">还可以直接在实例上定义进一步的配置，而无需链接到外部或嵌套的可编写脚本的资产。</span><span class="sxs-lookup"><span data-stu-id="a1aec-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="a1aec-147">边界控制检查器将通过在属性检查器中显示一条消息，指示配置是共享还是内联为当前实例的一部分。</span><span class="sxs-lookup"><span data-stu-id="a1aec-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="a1aec-148">此外，共享实例不会直接在 "边界控制" 属性窗口中进行编辑，而是将其链接到的资产直接修改，以避免对共享配置的任何意外更改。</span><span class="sxs-lookup"><span data-stu-id="a1aec-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="a1aec-149">当前界限控制提供以下功能的配置对象选项：</span><span class="sxs-lookup"><span data-stu-id="a1aec-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="a1aec-150">句柄数</span><span class="sxs-lookup"><span data-stu-id="a1aec-150">Handles</span></span>
  * [<span data-ttu-id="a1aec-151">缩放句柄</span><span class="sxs-lookup"><span data-stu-id="a1aec-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="a1aec-152">旋转控点</span><span class="sxs-lookup"><span data-stu-id="a1aec-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="a1aec-153">翻译句柄</span><span class="sxs-lookup"><span data-stu-id="a1aec-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="a1aec-154">链接/线框</span><span class="sxs-lookup"><span data-stu-id="a1aec-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="a1aec-155">框显示</span><span class="sxs-lookup"><span data-stu-id="a1aec-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="a1aec-156">邻近效果</span><span class="sxs-lookup"><span data-stu-id="a1aec-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="a1aec-157">Box 配置</span><span class="sxs-lookup"><span data-stu-id="a1aec-157">Box configuration</span></span>

<span data-ttu-id="a1aec-158">Box 配置负责呈现具有通过碰撞器大小和框填充定义的边界的实心框。</span><span class="sxs-lookup"><span data-stu-id="a1aec-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="a1aec-159">可以设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="a1aec-159">The following properties can be set up:</span></span>

* <span data-ttu-id="a1aec-160">**Box 材质**：定义在不发生交互时应用于呈现的框的材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="a1aec-161">只有在设置了此材料的情况下，才会呈现框。</span><span class="sxs-lookup"><span data-stu-id="a1aec-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="a1aec-162">**框获取材料**：用户通过通过近距离或远距离交互进行获取与控件进行交互时，框的材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="a1aec-163">**平展轴显示比例**：如果其中一个轴为 [平展](#flatten-axis)，则应用于框显示的刻度。</span><span class="sxs-lookup"><span data-stu-id="a1aec-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="a1aec-164">缩放句柄配置</span><span class="sxs-lookup"><span data-stu-id="a1aec-164">Scale handles configuration</span></span>

<span data-ttu-id="a1aec-165">此属性抽屉允许修改界限控制的缩放控点的行为和可视化效果。</span><span class="sxs-lookup"><span data-stu-id="a1aec-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="a1aec-166">**处理材料**：应用于图柄的材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="a1aec-167">**处理可处理的材料**：应用到该抓取句柄的材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="a1aec-168">**处理 prefab**：可选 prefab 作为刻度控点。</span><span class="sxs-lookup"><span data-stu-id="a1aec-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="a1aec-169">如果未设置 MRTK，则会将多维数据集用作默认多维数据集。</span><span class="sxs-lookup"><span data-stu-id="a1aec-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="a1aec-170">**控点大小**：缩放句柄的大小。</span><span class="sxs-lookup"><span data-stu-id="a1aec-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="a1aec-171">**碰撞器填充**：要添加到控点碰撞器的填充。</span><span class="sxs-lookup"><span data-stu-id="a1aec-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="a1aec-172">**操作时绘制接入**：活动时，将从交互点开始到当前手或指针位置绘制接入线。</span><span class="sxs-lookup"><span data-stu-id="a1aec-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="a1aec-173">**处理忽略碰撞** 器：如果碰撞器在此处链接，则处理将忽略与此碰撞器的任何冲突。</span><span class="sxs-lookup"><span data-stu-id="a1aec-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="a1aec-174">**处理石板 prefab**：在控件展开后用于该句柄的 prefab。</span><span class="sxs-lookup"><span data-stu-id="a1aec-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="a1aec-175">**显示刻度控点**：控件句柄的可见性。</span><span class="sxs-lookup"><span data-stu-id="a1aec-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="a1aec-176">**缩放行为**：可以设置为统一或非均匀缩放。</span><span class="sxs-lookup"><span data-stu-id="a1aec-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="a1aec-177">旋转控点配置</span><span class="sxs-lookup"><span data-stu-id="a1aec-177">Rotation handles configuration</span></span>

<span data-ttu-id="a1aec-178">此配置定义旋转控点的行为。</span><span class="sxs-lookup"><span data-stu-id="a1aec-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="a1aec-179">**处理材料**：应用于图柄的材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="a1aec-180">**处理可处理的材料**：应用到该抓取句柄的材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="a1aec-181">**处理 prefab**：句柄的可选 prefab。</span><span class="sxs-lookup"><span data-stu-id="a1aec-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="a1aec-182">如果设置为 "无"，MRTK 将使用一个球体作为默认值。</span><span class="sxs-lookup"><span data-stu-id="a1aec-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="a1aec-183">**句柄大小**：句柄的大小。</span><span class="sxs-lookup"><span data-stu-id="a1aec-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="a1aec-184">**碰撞器填充**：要添加到控点碰撞器的填充。</span><span class="sxs-lookup"><span data-stu-id="a1aec-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="a1aec-185">**操作时绘制接入**：活动时，将从交互点开始到当前手或指针位置绘制接入线。</span><span class="sxs-lookup"><span data-stu-id="a1aec-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="a1aec-186">**处理忽略碰撞** 器：如果碰撞器在此处链接，则处理将忽略与此碰撞器的任何冲突。</span><span class="sxs-lookup"><span data-stu-id="a1aec-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="a1aec-187">**处理 prefab 碰撞器类型**：要与创建的句柄一起使用的碰撞器类型。</span><span class="sxs-lookup"><span data-stu-id="a1aec-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="a1aec-188">显示 x 轴的句柄的 X：控件可见性的 **图柄**。</span><span class="sxs-lookup"><span data-stu-id="a1aec-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="a1aec-189">**显示 y** 轴控点的句柄。</span><span class="sxs-lookup"><span data-stu-id="a1aec-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="a1aec-190">**显示 z** 轴控点的显示手柄（z）：控件的可见性。</span><span class="sxs-lookup"><span data-stu-id="a1aec-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="a1aec-191">翻译句柄配置</span><span class="sxs-lookup"><span data-stu-id="a1aec-191">Translation handles configuration</span></span>

<span data-ttu-id="a1aec-192">允许为边界控件启用和配置转换句柄。</span><span class="sxs-lookup"><span data-stu-id="a1aec-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="a1aec-193">请注意，每个默认禁用翻译句柄。</span><span class="sxs-lookup"><span data-stu-id="a1aec-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="a1aec-194">**处理材料**：应用于图柄的材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="a1aec-195">**处理可处理的材料**：应用到该抓取句柄的材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="a1aec-196">**处理 prefab**：句柄的可选 prefab。</span><span class="sxs-lookup"><span data-stu-id="a1aec-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="a1aec-197">如果设置为 "无"，MRTK 将使用一个球体作为默认值。</span><span class="sxs-lookup"><span data-stu-id="a1aec-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="a1aec-198">**句柄大小**：句柄的大小。</span><span class="sxs-lookup"><span data-stu-id="a1aec-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="a1aec-199">**碰撞器填充**：要添加到控点碰撞器的填充。</span><span class="sxs-lookup"><span data-stu-id="a1aec-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="a1aec-200">**操作时绘制接入**：活动时，将从交互点开始到当前手或指针位置绘制接入线。</span><span class="sxs-lookup"><span data-stu-id="a1aec-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="a1aec-201">**处理忽略碰撞** 器：如果碰撞器在此处链接，则处理将忽略与此碰撞器的任何冲突。</span><span class="sxs-lookup"><span data-stu-id="a1aec-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="a1aec-202">**处理 prefab 碰撞器类型**：要与创建的句柄一起使用的碰撞器类型。</span><span class="sxs-lookup"><span data-stu-id="a1aec-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="a1aec-203">显示 x 轴的句柄的 X：控件可见性的 **图柄**。</span><span class="sxs-lookup"><span data-stu-id="a1aec-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="a1aec-204">**显示 y** 轴控点的句柄。</span><span class="sxs-lookup"><span data-stu-id="a1aec-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="a1aec-205">**显示 z** 轴控点的显示手柄（z）：控件的可见性。</span><span class="sxs-lookup"><span data-stu-id="a1aec-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="a1aec-206">链接配置 (线框) </span><span class="sxs-lookup"><span data-stu-id="a1aec-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="a1aec-207">链接配置启用了边界控件的线框功能。</span><span class="sxs-lookup"><span data-stu-id="a1aec-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="a1aec-208">可以配置以下属性：</span><span class="sxs-lookup"><span data-stu-id="a1aec-208">The following properties can be configured:</span></span>

* <span data-ttu-id="a1aec-209">**线框材料**：应用到线框网格的材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="a1aec-210">**线框边缘半径**：线框的粗细。</span><span class="sxs-lookup"><span data-stu-id="a1aec-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="a1aec-211">**线框形状**：线框或圆柱形可以是线框的形状。</span><span class="sxs-lookup"><span data-stu-id="a1aec-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="a1aec-212">**显示线框**：控件线框的可见性。</span><span class="sxs-lookup"><span data-stu-id="a1aec-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="a1aec-213">邻近效果配置</span><span class="sxs-lookup"><span data-stu-id="a1aec-213">Proximity effect configuration</span></span>

<span data-ttu-id="a1aec-214">显示和隐藏带有动画的带动画的图柄。</span><span class="sxs-lookup"><span data-stu-id="a1aec-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="a1aec-215">它具有两步缩放动画。</span><span class="sxs-lookup"><span data-stu-id="a1aec-215">It has two-step scaling animation.</span></span> <span data-ttu-id="a1aec-216">默认值设置为 "HoloLens 2 样式行为"。</span><span class="sxs-lookup"><span data-stu-id="a1aec-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="a1aec-217">**邻近效果活动**：启用基于近程的句柄激活</span><span class="sxs-lookup"><span data-stu-id="a1aec-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="a1aec-218">**对象中等** 距离：第一步缩放的距离</span><span class="sxs-lookup"><span data-stu-id="a1aec-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="a1aec-219">**对象近** 近：第二步缩放的距离</span><span class="sxs-lookup"><span data-stu-id="a1aec-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="a1aec-220">**远规模**：当手超出边界控制交互的范围时，句柄资产的默认缩放值 (按 "句柄中等距离" 定义的距离。</span><span class="sxs-lookup"><span data-stu-id="a1aec-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="a1aec-221">默认情况下，使用0隐藏句柄) </span><span class="sxs-lookup"><span data-stu-id="a1aec-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="a1aec-222">**中** 度：当手位于边界控件交互范围内时，该手柄资产的缩放值 (按 "句柄接近接近" 定义的距离。</span><span class="sxs-lookup"><span data-stu-id="a1aec-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="a1aec-223">使用1显示正常大小) </span><span class="sxs-lookup"><span data-stu-id="a1aec-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="a1aec-224">**关闭规模**：当手处于抓取交互范围内时，句柄资产的缩放值 (按 "句柄接近接近度" 定义的距离。</span><span class="sxs-lookup"><span data-stu-id="a1aec-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="a1aec-225">使用1.x 显示更大的) </span><span class="sxs-lookup"><span data-stu-id="a1aec-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="a1aec-226">**远比特率**：向邻近缩放的对象在从中到远的邻近度移动时缩放。</span><span class="sxs-lookup"><span data-stu-id="a1aec-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="a1aec-227">**中度增长率**：向邻近缩放的对象在手中移动时可缩放。</span><span class="sxs-lookup"><span data-stu-id="a1aec-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="a1aec-228">**关闭增长速率**：当手从近到对象中心移动时，可缩放邻近缩放对象。</span><span class="sxs-lookup"><span data-stu-id="a1aec-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="a1aec-229">约束系统</span><span class="sxs-lookup"><span data-stu-id="a1aec-229">Constraint System</span></span>

<span data-ttu-id="a1aec-230">使用界限控制句柄时，界限控制支持使用 [约束管理器](constraint-manager.md) 来限制或修改翻译、旋转或缩放行为。</span><span class="sxs-lookup"><span data-stu-id="a1aec-230">Bounds control supports using the [constraint manager](constraint-manager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="a1aec-231">属性检查器将在下拉列表中显示附加到同一游戏对象的所有可用约束管理器以及用于滚动和突出显示所选约束管理器的选项。</span><span class="sxs-lookup"><span data-stu-id="a1aec-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="a1aec-232">事件</span><span class="sxs-lookup"><span data-stu-id="a1aec-232">Events</span></span>

<span data-ttu-id="a1aec-233">界限控制提供以下事件。</span><span class="sxs-lookup"><span data-stu-id="a1aec-233">Bounds control provides the following events.</span></span> <span data-ttu-id="a1aec-234">此示例使用这些事件来播放音频反馈。</span><span class="sxs-lookup"><span data-stu-id="a1aec-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="a1aec-235">**旋转已开始**：旋转开始时激发。</span><span class="sxs-lookup"><span data-stu-id="a1aec-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="a1aec-236">**旋转停止**：旋转停止时激发。</span><span class="sxs-lookup"><span data-stu-id="a1aec-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="a1aec-237">**已开始缩放**：缩放开始时激发。</span><span class="sxs-lookup"><span data-stu-id="a1aec-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="a1aec-238">**缩放已停止**：缩放停止时激发。</span><span class="sxs-lookup"><span data-stu-id="a1aec-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="a1aec-239">**已开始翻译**：转换开始时激发。</span><span class="sxs-lookup"><span data-stu-id="a1aec-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="a1aec-240">**转换已停止**：转换停止时激发。</span><span class="sxs-lookup"><span data-stu-id="a1aec-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="a1aec-241">池中弹性 (试验性) </span><span class="sxs-lookup"><span data-stu-id="a1aec-241">Elastics (Experimental)</span></span>

<span data-ttu-id="a1aec-242">在通过边界控件操作对象时，可以使用池中弹性。</span><span class="sxs-lookup"><span data-stu-id="a1aec-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="a1aec-243">请注意， [池中弹性系统](../elastics/elastic-system.md) 仍处于试验状态。</span><span class="sxs-lookup"><span data-stu-id="a1aec-243">Note that the [elastics system](../elastics/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="a1aec-244">若要启用池中弹性，请链接现有的池中弹性 manager 组件或通过按钮创建和链接新的池中弹性管理器 `Add Elastics Manager` 。</span><span class="sxs-lookup"><span data-stu-id="a1aec-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="a1aec-245">句柄样式</span><span class="sxs-lookup"><span data-stu-id="a1aec-245">Handle styles</span></span>

<span data-ttu-id="a1aec-246">默认情况下，当你只分配 [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 脚本时，它将显示 HoloLens 1 代样式的句柄。</span><span class="sxs-lookup"><span data-stu-id="a1aec-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="a1aec-247">若要使用 HoloLens 2 样式句柄，需要分配正确的句柄 prototyping 和材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![边界控件句柄样式2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="a1aec-249">下面是 HoloLens 2 样式边界控件句柄的 prototyping、材料和缩放值。</span><span class="sxs-lookup"><span data-stu-id="a1aec-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="a1aec-250">您可以在场景中找到此示例 `BoundsControlExamples` 。</span><span class="sxs-lookup"><span data-stu-id="a1aec-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="a1aec-251">为 HoloLens 2 样式处理 (设置) </span><span class="sxs-lookup"><span data-stu-id="a1aec-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="a1aec-252">**处理材料**： BoundingBoxHandleWhite</span><span class="sxs-lookup"><span data-stu-id="a1aec-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="a1aec-253">**处理抓取材料**： BoundingBoxHandleBlueGrabbed</span><span class="sxs-lookup"><span data-stu-id="a1aec-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="a1aec-254">**缩放句柄 Prefab**： MRTK_BoundingBox_ScaleHandle。 Prefab</span><span class="sxs-lookup"><span data-stu-id="a1aec-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="a1aec-255">**缩放句柄石板 Prefab**： MRTK_BoundingBox_ScaleHandle_Slate。 Prefab</span><span class="sxs-lookup"><span data-stu-id="a1aec-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="a1aec-256">**缩放句柄大小**： 0.016 (1.6 厘米) </span><span class="sxs-lookup"><span data-stu-id="a1aec-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="a1aec-257">**刻度控点碰撞器填充**： 0.016 (使 grabbable 碰撞器略微大于处理视觉对象) </span><span class="sxs-lookup"><span data-stu-id="a1aec-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="a1aec-258">**旋转控点 Prefab**： MRTK_BoundingBox_RotateHandle。 Prefab</span><span class="sxs-lookup"><span data-stu-id="a1aec-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="a1aec-259">**旋转控点大小**：0.016</span><span class="sxs-lookup"><span data-stu-id="a1aec-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="a1aec-260">**旋转控点碰撞边距**： 0.016 (使 grabbable 碰撞器略微大于处理视觉对象) </span><span class="sxs-lookup"><span data-stu-id="a1aec-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="a1aec-261">对象操控器的转换更改</span><span class="sxs-lookup"><span data-stu-id="a1aec-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="a1aec-262">边界控件可以与结合使用 [`ObjectManipulator.cs`](object-manipulator.md) ，以允许某些类型的操作 (例如。</span><span class="sxs-lookup"><span data-stu-id="a1aec-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](object-manipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="a1aec-263">在不使用句柄的情况下移动对象) 。</span><span class="sxs-lookup"><span data-stu-id="a1aec-263">moving the object) without using handles.</span></span> <span data-ttu-id="a1aec-264">操作处理程序支持一种和两方交互。</span><span class="sxs-lookup"><span data-stu-id="a1aec-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="a1aec-265">可以使用[手动跟踪](../input/hand-tracking.md)来与对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="a1aec-265">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="a1aec-266">为了使边界控件边缘在使用远距离交互进行移动时以相同的方式运行 [`ObjectManipulator`](object-manipulator.md) ，建议在操作结束时连接其事件以进行操作  /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` ，如以上屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="a1aec-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](object-manipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="a1aec-267">如何使用 Unity 检查器添加和配置绑定控件</span><span class="sxs-lookup"><span data-stu-id="a1aec-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="a1aec-268">向对象添加框碰撞器</span><span class="sxs-lookup"><span data-stu-id="a1aec-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="a1aec-269">将 `BoundsControl` 脚本分配给对象</span><span class="sxs-lookup"><span data-stu-id="a1aec-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="a1aec-270">配置选项，如 "激活" 方法 (参阅下面的 [检查器属性](#inspector-properties) 部分) </span><span class="sxs-lookup"><span data-stu-id="a1aec-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="a1aec-271"> (可选) 为 HoloLens 2 样式边界控件分配 prototyping 和材料 (参见下面的 " [句柄样式](#handle-styles) " 部分) </span><span class="sxs-lookup"><span data-stu-id="a1aec-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="a1aec-272">使用 "检查器" 中的 " *目标对象* " 和 " *边界替代* " 字段，可以在具有多个子组件的对象中分配特定对象和碰撞器。</span><span class="sxs-lookup"><span data-stu-id="a1aec-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![边界控制](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="a1aec-274">如何在代码中添加和配置边界控件</span><span class="sxs-lookup"><span data-stu-id="a1aec-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="a1aec-275">实例化 cube GameObject</span><span class="sxs-lookup"><span data-stu-id="a1aec-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="a1aec-276">`BoundsControl`使用 AddComponent<>，将脚本分配给包含碰撞器的对象 () </span><span class="sxs-lookup"><span data-stu-id="a1aec-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="a1aec-277">直接在控件上或通过一个可脚本化的配置配置选项 (参阅下面的 [检查器属性](#inspector-properties) 和 [配置](#configuration-objects) 部分) </span><span class="sxs-lookup"><span data-stu-id="a1aec-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="a1aec-278"> (可选) 为 HoloLens 2 样式边界控件分配 prototyping 和材料。</span><span class="sxs-lookup"><span data-stu-id="a1aec-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="a1aec-279">这仍需要通过检查器进行的分配，因为应该动态加载材料和 prototyping。</span><span class="sxs-lookup"><span data-stu-id="a1aec-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="a1aec-280">使用 Unity 的 "资源" 文件夹或 [着色器。]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) 不建议查找动态加载着色器，因为在运行时可能会缺少着色器排列。</span><span class="sxs-lookup"><span data-stu-id="a1aec-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="a1aec-281">示例：使用 MinMaxScaleConstraint 设置最小值、最大边界控制比例</span><span class="sxs-lookup"><span data-stu-id="a1aec-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="a1aec-282">若要设置最小和最大刻度，请将添加 [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) 到控件。</span><span class="sxs-lookup"><span data-stu-id="a1aec-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="a1aec-283">当边界控制自动附加和激活约束管理器时，MinMaxScaleConstraint 将自动应用于附加和配置后的转换更改。</span><span class="sxs-lookup"><span data-stu-id="a1aec-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="a1aec-284">还可以使用 MinMaxScaleConstraint 设置的最小和最大刻度 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 。</span><span class="sxs-lookup"><span data-stu-id="a1aec-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="a1aec-285">示例：围绕游戏对象添加边界控件</span><span class="sxs-lookup"><span data-stu-id="a1aec-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="a1aec-286">若要在对象周围添加边界控件，只需向 `BoundsControl` 其添加一个组件：</span><span class="sxs-lookup"><span data-stu-id="a1aec-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="a1aec-287">从边界框迁移</span><span class="sxs-lookup"><span data-stu-id="a1aec-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="a1aec-288">使用 [范围框](bounding-box.md) 的现有 prototyping 和实例可以通过 [迁移窗口](../tools/migration-window.md) 升级到新的边界控件，该窗口是 MRTK 工具包的一部分。</span><span class="sxs-lookup"><span data-stu-id="a1aec-288">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="a1aec-289">对于升级边界框的单个实例，还会在组件的属性检查器中提供一个迁移选项。</span><span class="sxs-lookup"><span data-stu-id="a1aec-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a><span data-ttu-id="a1aec-290">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1aec-290">See also</span></span>

* [<span data-ttu-id="a1aec-291">对象操控器</span><span class="sxs-lookup"><span data-stu-id="a1aec-291">Object manipulator</span></span>](object-manipulator.md)
* [<span data-ttu-id="a1aec-292">约束管理器</span><span class="sxs-lookup"><span data-stu-id="a1aec-292">Constraint manager</span></span>](constraint-manager.md)
* [<span data-ttu-id="a1aec-293">迁移时限</span><span class="sxs-lookup"><span data-stu-id="a1aec-293">Migration window</span></span>](../tools/migration-window.md)
* [<span data-ttu-id="a1aec-294">池中弹性系统 (试验性) </span><span class="sxs-lookup"><span data-stu-id="a1aec-294">Elastics system (Experimental)</span></span>](../elastics/elastic-system.md)
