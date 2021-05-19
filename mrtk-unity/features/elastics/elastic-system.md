---
title: 弹性系统
description: 与 MRTK 中池中弹性模拟相关的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，ElasticsSystem，
ms.openlocfilehash: 01a4c4a337593252e0955c03e883e35e1329fc45
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145187"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="2b15d-104">弹性系统 (试验性) </span><span class="sxs-lookup"><span data-stu-id="2b15d-104">Elastic system (experimental)</span></span>

![弹性系统](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="2b15d-106">MRTK 附带了一个弹性模拟系统，其中包含各种可扩展和灵活的子类，为四维四元数弹簧、三维量弹簧和简单线性弹簧系统提供绑定。</span><span class="sxs-lookup"><span data-stu-id="2b15d-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="2b15d-107">目前，支持 [池中弹性 manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 的以下 MRTK 组件可以利用池中弹性功能：</span><span class="sxs-lookup"><span data-stu-id="2b15d-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="2b15d-108">边界控件</span><span class="sxs-lookup"><span data-stu-id="2b15d-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="2b15d-109">对象操控器</span><span class="sxs-lookup"><span data-stu-id="2b15d-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="2b15d-110">池中弹性管理器</span><span class="sxs-lookup"><span data-stu-id="2b15d-110">Elastics manager</span></span>

![弹性 System2](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="2b15d-112">池中弹性 manager 处理传递的转换，并将其馈送到池中弹性系统。</span><span class="sxs-lookup"><span data-stu-id="2b15d-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="2b15d-113">为自定义组件启用池中弹性可以通过两个步骤来实现：</span><span class="sxs-lookup"><span data-stu-id="2b15d-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="2b15d-114">在操作开始时调用 Initialize 方法，并更新具有当前主机转换的系统。</span><span class="sxs-lookup"><span data-stu-id="2b15d-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="2b15d-115">每次对更新的目标转换执行池中弹性计算时，都要查询 ApplyHostTransform。</span><span class="sxs-lookup"><span data-stu-id="2b15d-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="2b15d-116">请注意，池中弹性将在操作结束后通过池中弹性 manager 更新循环) 继续模拟 (。</span><span class="sxs-lookup"><span data-stu-id="2b15d-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="2b15d-117">若要阻止此行为，可以将池中弹性 auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) 设置为 false。</span><span class="sxs-lookup"><span data-stu-id="2b15d-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="2b15d-118">默认情况下，池中弹性 manager 组件添加到游戏对象时，不会为任何转换类型启用池中弹性。</span><span class="sxs-lookup"><span data-stu-id="2b15d-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="2b15d-119">需要为 `Manipulation types using elastic feedback` 特定的转换类型启用此字段，以创建所选类型的池中弹性配置和区。</span><span class="sxs-lookup"><span data-stu-id="2b15d-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="2b15d-120">池中弹性配置</span><span class="sxs-lookup"><span data-stu-id="2b15d-120">Elastics configurations</span></span>

<span data-ttu-id="2b15d-121">与 [边界控制配置](../ux-building-blocks/bounds-control.md#configuration-objects)类似，弹性管理器附带一组配置对象，这些对象可存储为可编脚本的对象，并在不同的实例或 prototyping 之间共享。</span><span class="sxs-lookup"><span data-stu-id="2b15d-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="2b15d-122">配置可以作为单个可编脚本的资产文件或 prototyping 中嵌套的可编脚本的资产来共享和链接。</span><span class="sxs-lookup"><span data-stu-id="2b15d-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="2b15d-123">还可以直接在实例上定义其他配置，而无需链接到外部或嵌套的可脚本化资产。</span><span class="sxs-lookup"><span data-stu-id="2b15d-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="2b15d-124">弹性管理器检查器将在属性检查器中显示消息，指示配置是作为当前实例的一部分进行共享还是内内。</span><span class="sxs-lookup"><span data-stu-id="2b15d-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="2b15d-125">此外，共享实例不能直接在弹性管理器属性窗口本身中编辑，但必须直接修改它链接到的资产，以避免对共享配置发生任何意外更改。</span><span class="sxs-lookup"><span data-stu-id="2b15d-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="2b15d-126">弹性管理器为以下转换类型提供配置对象选项，其中每种类型都由弹性配置 [对象表示](#elastic-configuration-object)：</span><span class="sxs-lookup"><span data-stu-id="2b15d-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="2b15d-127">翻译弹性</span><span class="sxs-lookup"><span data-stu-id="2b15d-127">Translation Elastic</span></span>
- <span data-ttu-id="2b15d-128">旋转弹性</span><span class="sxs-lookup"><span data-stu-id="2b15d-128">Rotation Elastic</span></span>
- <span data-ttu-id="2b15d-129">缩放弹性</span><span class="sxs-lookup"><span data-stu-id="2b15d-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="2b15d-130">弹性配置对象</span><span class="sxs-lookup"><span data-stu-id="2b15d-130">Elastic configuration object</span></span>

<span data-ttu-id="2b15d-131">弹性配置定义已设置好效果的微分系统的属性。</span><span class="sxs-lookup"><span data-stu-id="2b15d-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="2b15d-132">可以调整以下属性，但 MRTK 中已具有一组默认值：</span><span class="sxs-lookup"><span data-stu-id="2b15d-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="2b15d-133">**质量**：模拟的中子元素的质量。</span><span class="sxs-lookup"><span data-stu-id="2b15d-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="2b15d-134">**HandK：** 手部 spring 常量。</span><span class="sxs-lookup"><span data-stu-id="2b15d-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="2b15d-135">**EndK：** 端帽 spring 常量。</span><span class="sxs-lookup"><span data-stu-id="2b15d-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="2b15d-136">**SnapK：** 对齐点 spring 常量。</span><span class="sxs-lookup"><span data-stu-id="2b15d-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="2b15d-137">**拖动**：拖动/拖动系数，与速度成正比。</span><span class="sxs-lookup"><span data-stu-id="2b15d-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="2b15d-138">弹性区</span><span class="sxs-lookup"><span data-stu-id="2b15d-138">Elastics extents</span></span>

<span data-ttu-id="2b15d-139">弹性区设置因操作类型而异。</span><span class="sxs-lookup"><span data-stu-id="2b15d-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="2b15d-140">平移和缩放由卷 [弹性区表示](#volume-elastic-extent) ，旋转由四元弹性 [区 表示](#quaternion-elastic-extent)。</span><span class="sxs-lookup"><span data-stu-id="2b15d-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="2b15d-141">卷弹性区</span><span class="sxs-lookup"><span data-stu-id="2b15d-141">Volume elastic extent</span></span>

<span data-ttu-id="2b15d-142">卷区定义一个三维空间，其中，可随意移动三维空间。</span><span class="sxs-lookup"><span data-stu-id="2b15d-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![弹性卷拉伸边界](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="2b15d-144">**StretchBounds**：表示弹性空间的下限。</span><span class="sxs-lookup"><span data-stu-id="2b15d-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="2b15d-145">**UseBounds**：系统是否应遵循 stretch 边界。</span><span class="sxs-lookup"><span data-stu-id="2b15d-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="2b15d-146">如果为 true，则当目标位置的当前迭代超出延伸边界时，将应用最终强制。</span><span class="sxs-lookup"><span data-stu-id="2b15d-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="2b15d-147">**吸附点**：指向系统将对齐到的空间内的点。</span><span class="sxs-lookup"><span data-stu-id="2b15d-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="2b15d-148">**RepeatSnapPoints**：将对齐点重复为无限大。</span><span class="sxs-lookup"><span data-stu-id="2b15d-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="2b15d-149">现有的 snap 点将充当一个模数，其中实际的对齐点映射到每个对齐点的最接近整数倍数。</span><span class="sxs-lookup"><span data-stu-id="2b15d-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="2b15d-150">**SnapRadius**： snap 点开始强制弹簧的距离。</span><span class="sxs-lookup"><span data-stu-id="2b15d-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![弹性卷对齐网格](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="2b15d-152">四元数弹性区</span><span class="sxs-lookup"><span data-stu-id="2b15d-152">Quaternion elastic extent</span></span>

<span data-ttu-id="2b15d-153">四元数区定义了一种可自由旋转的阻止调和震荡的四维旋转空间。</span><span class="sxs-lookup"><span data-stu-id="2b15d-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![弹性旋转示例](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="2b15d-155">**吸附点**：系统将对齐到的欧拉角。</span><span class="sxs-lookup"><span data-stu-id="2b15d-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="2b15d-156">**RepeatSnapPoints**：重复对齐点。</span><span class="sxs-lookup"><span data-stu-id="2b15d-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="2b15d-157">现有的 snap 点将充当一个模数，其中实际的对齐点映射到每个对齐点的最接近整数倍数。</span><span class="sxs-lookup"><span data-stu-id="2b15d-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="2b15d-158">**SnapRadius**：弧线-角度，其中的对齐点以欧拉度开始强制弹簧。</span><span class="sxs-lookup"><span data-stu-id="2b15d-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="2b15d-159">池中弹性示例场景</span><span class="sxs-lookup"><span data-stu-id="2b15d-159">Elastics example scene</span></span>

<span data-ttu-id="2b15d-160">你可以在场景中查找池中弹性配置的示例 `ElasticSystemExample` 。</span><span class="sxs-lookup"><span data-stu-id="2b15d-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![池中弹性示例场景](../images/elastics/Elastics_Example_Scene.png)
