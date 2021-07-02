---
title: 滚动对象集合
description: 概述菜单类型 MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，滚动对象
ms.openlocfilehash: a724b9fb4a0f72910e16353a6c76b9e31005a76e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176602"
---
# <a name="scrolling-object-collection"></a><span data-ttu-id="1d640-104">滚动对象集合</span><span class="sxs-lookup"><span data-stu-id="1d640-104">Scrolling object collection</span></span>

![滚动对象集合](../images/scrolling-collection/ScrollingCollection_Main.jpg)

<span data-ttu-id="1d640-106">MRTK 滚动对象集合是一个 UX 组件，通过包含的可查看区域启用3D 内容滚动。</span><span class="sxs-lookup"><span data-stu-id="1d640-106">The MRTK scrolling object collection is an UX component that enables scrolling of 3D content through a contained viewable area.</span></span> <span data-ttu-id="1d640-107">滚动移动可由近或远的输入交互以及离散分页触发。</span><span class="sxs-lookup"><span data-stu-id="1d640-107">The scrolling movement can be triggered by near or far input interaction and by discrete pagination.</span></span> <span data-ttu-id="1d640-108">它支持交互式和非交互式对象。</span><span class="sxs-lookup"><span data-stu-id="1d640-108">It supports both interactive and non-interactive objects.</span></span>

## <a name="getting-started-with-the-scrolling-object-collection"></a><span data-ttu-id="1d640-109">滚动对象集合入门</span><span class="sxs-lookup"><span data-stu-id="1d640-109">Getting started with the scrolling object collection</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="1d640-110">设置场景</span><span class="sxs-lookup"><span data-stu-id="1d640-110">Setting up the scene</span></span>

1. <span data-ttu-id="1d640-111">创建新的 unity 场景。</span><span class="sxs-lookup"><span data-stu-id="1d640-111">Create a new unity scene.</span></span>
1. <span data-ttu-id="1d640-112">通过导航到 **混合现实 Toolkit**  >  **添加到场景并进行配置**，将 MRTK 添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="1d640-112">Add MRTK to the scene by navigating to the **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

### <a name="setting-up-the-scrolling-object"></a><span data-ttu-id="1d640-113">设置滚动对象</span><span class="sxs-lookup"><span data-stu-id="1d640-113">Setting up the scrolling object</span></span>

1. <span data-ttu-id="1d640-114">在场景中创建一个空游戏对象，并将其位置更改为 (0，0，1) 。</span><span class="sxs-lookup"><span data-stu-id="1d640-114">Create an empty game object in the scene and change its position to (0, 0, 1).</span></span>
1. <span data-ttu-id="1d640-115">向游戏对象添加 [滚动对象集合](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) 组件。</span><span class="sxs-lookup"><span data-stu-id="1d640-115">Add a [scrolling object collection](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) component to the game object.</span></span>

    <span data-ttu-id="1d640-116">添加滚动对象集合时，会自动将一个框碰撞器和 [近交互可触摸](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 组件连接到根游戏对象。</span><span class="sxs-lookup"><span data-stu-id="1d640-116">When the scrolling object collection is added, a box collider and a [near interaction touchable](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component will be automatically attached to the root game object.</span></span> <span data-ttu-id="1d640-117">这些组件允许 scroll 对象侦听近和远交互输入事件，如指针触摸或单击。</span><span class="sxs-lookup"><span data-stu-id="1d640-117">These components allow the scroll object to listen to near and far interaction input events, like a pointer touch or click.</span></span>  

    <span data-ttu-id="1d640-118">MRTK 滚动对象集合具有两个在根滚动对象层次结构下作为子游戏对象创建的重要元素：</span><span class="sxs-lookup"><span data-stu-id="1d640-118">The MRTK scrolling object collection has two important elements that are created as child game objects under the root scrolling object hierarchy:</span></span>
    * <span data-ttu-id="1d640-119">`Container` -所有滚动内容对象都必须是容器游戏对象的子项。</span><span class="sxs-lookup"><span data-stu-id="1d640-119">`Container` - All scrolling content objects must be children of the container game object.</span></span>
    * <span data-ttu-id="1d640-120">`Clipping bounds` -如果启用了滚动内容屏蔽，则剪辑边界元素可确保仅显示其边界内的可滚动内容。</span><span class="sxs-lookup"><span data-stu-id="1d640-120">`Clipping bounds` - If scrolling content masking is enabled, the clipping bounds element ensures that only the scrollable content inside its boundaries is visible.</span></span> <span data-ttu-id="1d640-121">剪切边界游戏对象包含两个组件：禁用的框碰撞器和 [剪切框](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)。</span><span class="sxs-lookup"><span data-stu-id="1d640-121">The clipping bounds game object has two components: a disabled box collider and a [clipping box](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).</span></span>

![滚动对象集合元素](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a><span data-ttu-id="1d640-123">向滚动对象添加内容</span><span class="sxs-lookup"><span data-stu-id="1d640-123">Adding content to the scrolling object</span></span>

<span data-ttu-id="1d640-124">滚动对象集合可以与 [网格对象集合](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 结合使用，以便在大小和间距相同的对齐元素网格中布局内容。</span><span class="sxs-lookup"><span data-stu-id="1d640-124">The scrolling object collection can be combined with a [grid object collection](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) to layout content in a grid of aligned elements that have uniform size and spacing.</span></span>

1. <span data-ttu-id="1d640-125">创建一个空游戏对象作为滚动容器的子级。</span><span class="sxs-lookup"><span data-stu-id="1d640-125">Create an empty game object as a child of the scroll container.</span></span>
1. <span data-ttu-id="1d640-126">向游戏对象添加网格对象集合组件。</span><span class="sxs-lookup"><span data-stu-id="1d640-126">Add a grid object collection component to the game object.</span></span>
1. <span data-ttu-id="1d640-127">对于垂直单列滚动，在 "检查器" 选项卡中，按如下所示配置网格对象集合：</span><span class="sxs-lookup"><span data-stu-id="1d640-127">For a vertical single column scroll, in the inspector tab, configure the grid object collection as follow:</span></span>
    * <span data-ttu-id="1d640-128">**列** 数：1</span><span class="sxs-lookup"><span data-stu-id="1d640-128">**Num columns**: 1</span></span>
    * <span data-ttu-id="1d640-129">**布局**：列 then 行</span><span class="sxs-lookup"><span data-stu-id="1d640-129">**Layout**: column then row</span></span>
    * <span data-ttu-id="1d640-130">**定位点**：左上</span><span class="sxs-lookup"><span data-stu-id="1d640-130">**Anchor**: upper left</span></span>
1. <span data-ttu-id="1d640-131">根据内容对象的尺寸更改 **单元格的宽度** 和 **高度** 。</span><span class="sxs-lookup"><span data-stu-id="1d640-131">Change the **cell width** and **height** according to the dimensions of the content objects.</span></span>
1. <span data-ttu-id="1d640-132">添加内容对象作为网格对象的子级。</span><span class="sxs-lookup"><span data-stu-id="1d640-132">Add the content objects as children of the grid object.</span></span>
1. <span data-ttu-id="1d640-133">按 " **更新集合**"。</span><span class="sxs-lookup"><span data-stu-id="1d640-133">Press **update collection**.</span></span>

![网格布局](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> <span data-ttu-id="1d640-135">任何滚动内容对象材料必须使用 [MRTK 标准着色器](../rendering/MRTK-standard-shader.md) ，才能使可视区域上的剪辑效果正常工作。</span><span class="sxs-lookup"><span data-stu-id="1d640-135">Any scrolling content object material must use the [MRTK standard shader](../rendering/MRTK-standard-shader.md) in order for the clipping effect on the viewable area to work properly.</span></span>

> [!NOTE]
> <span data-ttu-id="1d640-136">如果启用了滚动内容屏蔽，则滚动对象集合将向附加了呈现器的任何内容对象添加 [材料实例](../rendering/material-instance.md) 组件。</span><span class="sxs-lookup"><span data-stu-id="1d640-136">If scrolling content masking is enabled, the scrolling object collection will add a [material instance](../rendering/material-instance.md) component to any content objects that have a renderer attached.</span></span> <span data-ttu-id="1d640-137">此组件用于管理实例材料生存期并提高内存性能。</span><span class="sxs-lookup"><span data-stu-id="1d640-137">This component is used to manage instanced materials lifetime and improve memory performance.</span></span>

### <a name="configuring-the-scrolling-viewable-area"></a><span data-ttu-id="1d640-138">配置滚动可查看区域</span><span class="sxs-lookup"><span data-stu-id="1d640-138">Configuring the scrolling viewable area</span></span>

1. <span data-ttu-id="1d640-139">对于垂直滚动浏览对象的单个列，请在 "检查器" 选项卡中，按如下所示配置滚动对象集合：</span><span class="sxs-lookup"><span data-stu-id="1d640-139">For vertical scrolling through a single column of objects, in the inspector tab, configure the scrolling object collection as follow:</span></span>
    * <span data-ttu-id="1d640-140">**单元格/层**：1</span><span class="sxs-lookup"><span data-stu-id="1d640-140">**Cells per tier**: 1</span></span>
    * <span data-ttu-id="1d640-141">根据所需的可见行数选择 **每页的层** 数</span><span class="sxs-lookup"><span data-stu-id="1d640-141">Choose the number of **tiers per page** according to the desired number of visible rows</span></span>
1. <span data-ttu-id="1d640-142">根据内容对象的尺寸更改 **页面单元宽度**、 **高度** 和 **深度** 。</span><span class="sxs-lookup"><span data-stu-id="1d640-142">Change the **page cell width**, **height** and **depth** according to the dimensions of the content objects.</span></span>

<span data-ttu-id="1d640-143">请注意，当前已禁用滚动可见区域外的内容对象，而与滚动线框相交的对象可能会被剪辑基元部分屏蔽。</span><span class="sxs-lookup"><span data-stu-id="1d640-143">Notice how the content objects lying outside the scrolling viewable area are now disabled, while objects intersecting the scroll wireframe might be partially masked by the clipping primitive.</span></span>

![可视区域](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a><span data-ttu-id="1d640-145">在编辑器中测试滚动对象集合</span><span class="sxs-lookup"><span data-stu-id="1d640-145">Testing the scrolling object collection in the editor</span></span>

1. <span data-ttu-id="1d640-146">按下 "播放" 并按住空格键以显示输入模拟手。</span><span class="sxs-lookup"><span data-stu-id="1d640-146">Press play and hold the space bar to show an input simulation hand.</span></span>
1. <span data-ttu-id="1d640-147">移动手直到滚动碰撞器或任何滚动交互内容处于焦点状态，并通过单击并上下拖动鼠标并触发滚动移动。</span><span class="sxs-lookup"><span data-stu-id="1d640-147">Move the hand until the scrolling collider or any scrolling interactive content is in focus and trigger the scrolling movement by clicking and dragging up and down with the left mouse.</span></span>

## <a name="controlling-the-scrolling-object-from-code"></a><span data-ttu-id="1d640-148">从代码控制滚动对象</span><span class="sxs-lookup"><span data-stu-id="1d640-148">Controlling the scrolling object from code</span></span>

<span data-ttu-id="1d640-149">MRTK 滚动对象集合公开了一些公共方法，这些公共方法允许移动滚动容器，方法是根据属性配置对齐滚动容器的位置 `pagination` 。</span><span class="sxs-lookup"><span data-stu-id="1d640-149">The MRTK scrolling object collection exposes a few public methods that allow moving the scrolling container by snapping its position according to the `pagination` properties configuration.</span></span>

<span data-ttu-id="1d640-150">有关如何访问滚动对象集合分页接口的示例，可在文件夹下使用 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` 。</span><span class="sxs-lookup"><span data-stu-id="1d640-150">An example of how to access the scrolling object collection pagination interface is available to use under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` folder.</span></span> <span data-ttu-id="1d640-151">可 [滚动分页](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) 示例脚本可以链接到场景中的任何现有的滚动对象集合。</span><span class="sxs-lookup"><span data-stu-id="1d640-151">The [scrollable pagination](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) example script can be linked to any existing scrolling object collection in the scene.</span></span> <span data-ttu-id="1d640-152">然后，该脚本可以由显示 Unity 事件的场景组件引用 (例如， [MRTK 按钮](button.md)) 。</span><span class="sxs-lookup"><span data-stu-id="1d640-152">The script can then be referenced by scene components exposing Unity events (e.g, [MRTK button](button.md)).</span></span>

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }
}
```

## <a name="scrolling-object-collection-properties"></a><span data-ttu-id="1d640-153">滚动对象集合属性</span><span class="sxs-lookup"><span data-stu-id="1d640-153">Scrolling object collection properties</span></span>

| <span data-ttu-id="1d640-154">常规</span><span class="sxs-lookup"><span data-stu-id="1d640-154">General</span></span>          | <span data-ttu-id="1d640-155">说明</span><span class="sxs-lookup"><span data-stu-id="1d640-155">Description</span></span>                                   |
| :--------------- | :-------------------------------------------- |
| <span data-ttu-id="1d640-156">滚动方向</span><span class="sxs-lookup"><span data-stu-id="1d640-156">Scroll direction</span></span> | <span data-ttu-id="1d640-157">内容应滚动的方向。</span><span class="sxs-lookup"><span data-stu-id="1d640-157">The direction in which content should scroll.</span></span> |

| <span data-ttu-id="1d640-158">分页</span><span class="sxs-lookup"><span data-stu-id="1d640-158">Pagination</span></span>     | <span data-ttu-id="1d640-159">说明</span><span class="sxs-lookup"><span data-stu-id="1d640-159">Description</span></span>                                                                                               |
| :------------- | :-------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1d640-160">单元格数</span><span class="sxs-lookup"><span data-stu-id="1d640-160">Cells per tier</span></span> | <span data-ttu-id="1d640-161">向上滚动视图中的行中的单元格数或左侧滚动视图中列的单元格数。</span><span class="sxs-lookup"><span data-stu-id="1d640-161">Number of cells in a row on up-down scroll view or number of cells in a column on left-right scroll view.</span></span> |
| <span data-ttu-id="1d640-162">每页层数</span><span class="sxs-lookup"><span data-stu-id="1d640-162">Tiers per page</span></span> | <span data-ttu-id="1d640-163">滚动区域中可见层的数目。</span><span class="sxs-lookup"><span data-stu-id="1d640-163">Number of visible tiers in the scrolling area.</span></span>                                                            |
| <span data-ttu-id="1d640-164">页面单元</span><span class="sxs-lookup"><span data-stu-id="1d640-164">Page cell</span></span>      | <span data-ttu-id="1d640-165">分页单元格的尺寸。</span><span class="sxs-lookup"><span data-stu-id="1d640-165">Dimensions of the pagination cell.</span></span>                                                                        |

| <span data-ttu-id="1d640-166">高级设置</span><span class="sxs-lookup"><span data-stu-id="1d640-166">Advanced settings</span></span>           | <span data-ttu-id="1d640-167">说明</span><span class="sxs-lookup"><span data-stu-id="1d640-167">Description</span></span>                                                                                                                                                                |
| :-------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1d640-168">掩码编辑模式</span><span class="sxs-lookup"><span data-stu-id="1d640-168">Mask edit mode</span></span>              | <span data-ttu-id="1d640-169">用于定义剪辑框掩码边界的编辑模式。</span><span class="sxs-lookup"><span data-stu-id="1d640-169">Edit modes for defining the clipping box masking boundaries.</span></span> <span data-ttu-id="1d640-170">"Auto" 自动使用分页值。</span><span class="sxs-lookup"><span data-stu-id="1d640-170">'Auto' automatically uses pagination values.</span></span> <span data-ttu-id="1d640-171">"手动" 启用剪切框对象的直接操作。</span><span class="sxs-lookup"><span data-stu-id="1d640-171">'Manual' enables direct manipulation of the clipping box object.</span></span> |
| <span data-ttu-id="1d640-172">碰撞器编辑模式</span><span class="sxs-lookup"><span data-stu-id="1d640-172">Collider edit mode</span></span>          | <span data-ttu-id="1d640-173">用于定义滚动交互碰撞器边界的编辑模式。</span><span class="sxs-lookup"><span data-stu-id="1d640-173">Edit modes for defining the scroll interaction collider boundaries.</span></span> <span data-ttu-id="1d640-174">"Auto" 自动使用分页值。</span><span class="sxs-lookup"><span data-stu-id="1d640-174">'Auto' automatically uses pagination values.</span></span> <span data-ttu-id="1d640-175">"手动" 启用碰撞器的直接操作。</span><span class="sxs-lookup"><span data-stu-id="1d640-175">'Manual' enables direct manipulation of the collider.</span></span>     |
| <span data-ttu-id="1d640-176">可以滚动</span><span class="sxs-lookup"><span data-stu-id="1d640-176">Can scroll</span></span>                  | <span data-ttu-id="1d640-177">启用/禁用对近/远交互的滚动。</span><span class="sxs-lookup"><span data-stu-id="1d640-177">Enables/disables scrolling with near/far interaction.</span></span>                                                                                                                      |
| <span data-ttu-id="1d640-178">在预呈现时使用</span><span class="sxs-lookup"><span data-stu-id="1d640-178">Use on pre render</span></span>           | <span data-ttu-id="1d640-179">切换 scrollingObjectCollection 是否将使用摄像 OnPreRender 事件来管理内容可见性。</span><span class="sxs-lookup"><span data-stu-id="1d640-179">Toggles whether the scrollingObjectCollection will use the Camera OnPreRender event to manage content visibility.</span></span>                                                          |
| <span data-ttu-id="1d640-180">分页曲线</span><span class="sxs-lookup"><span data-stu-id="1d640-180">Pagination curve</span></span>            | <span data-ttu-id="1d640-181">用于分页的动画曲线。</span><span class="sxs-lookup"><span data-stu-id="1d640-181">Animation curve for pagination.</span></span>                                                                                                                                            |
| <span data-ttu-id="1d640-182">动画长度</span><span class="sxs-lookup"><span data-stu-id="1d640-182">Animation length</span></span>            | <span data-ttu-id="1d640-183">PaginationCurve 计算所需的时间量，以秒为单位)  (。</span><span class="sxs-lookup"><span data-stu-id="1d640-183">The amount of time (in seconds) the PaginationCurve will take to evaluate.</span></span>                                                                                                 |
| <span data-ttu-id="1d640-184">手动增量滚动阈值</span><span class="sxs-lookup"><span data-stu-id="1d640-184">Hand delta scroll threshold</span></span> | <span data-ttu-id="1d640-185">在触发滚动拖动之前，当前指针可以沿滚动方向行进的距离（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="1d640-185">The distance, in meters, the current pointer can travel along the scroll direction before triggering a scroll drag.</span></span>                                                        |
| <span data-ttu-id="1d640-186">正面触摸距离</span><span class="sxs-lookup"><span data-stu-id="1d640-186">Front touch distance</span></span>        | <span data-ttu-id="1d640-187">定位用于验证在滚动视图前面是否启动了触摸屏交互的本地 xy 平面的距离（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="1d640-187">Distance, in meters, to position a local xy plane used to verify if a touch interaction started in the front of the scroll view.</span></span>                                           |
| <span data-ttu-id="1d640-188">发布阈值</span><span class="sxs-lookup"><span data-stu-id="1d640-188">Release threshold</span></span>           | <span data-ttu-id="1d640-189">从与已释放的触摸开始转换所需的滚动边界，收回量（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="1d640-189">Withdraw amount, in meters, from the scroll boundaries needed to transition from touch engaged to released.</span></span>                                                                |

| <span data-ttu-id="1d640-190">速度</span><span class="sxs-lookup"><span data-stu-id="1d640-190">Velocity</span></span>            | <span data-ttu-id="1d640-191">说明</span><span class="sxs-lookup"><span data-stu-id="1d640-191">Description</span></span>                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1d640-192">速度类型</span><span class="sxs-lookup"><span data-stu-id="1d640-192">Type of velocity</span></span>    | <span data-ttu-id="1d640-193">滚动条的所需速度过渡类型。</span><span class="sxs-lookup"><span data-stu-id="1d640-193">The desired type of velocity falloff for the scroller.</span></span>                                                      |
| <span data-ttu-id="1d640-194">速度乘数</span><span class="sxs-lookup"><span data-stu-id="1d640-194">Velocity multiplier</span></span> | <span data-ttu-id="1d640-195">要应用到滚动条的 (额外) 速度量。</span><span class="sxs-lookup"><span data-stu-id="1d640-195">Amount of (extra) velocity to be applied to scroller.</span></span>                                                       |
| <span data-ttu-id="1d640-196">速度 dampen</span><span class="sxs-lookup"><span data-stu-id="1d640-196">Velocity dampen</span></span>     | <span data-ttu-id="1d640-197">应用到速度的衰减量。</span><span class="sxs-lookup"><span data-stu-id="1d640-197">Amount of falloff applied to the velocity.</span></span>                                                                  |
| <span data-ttu-id="1d640-198">弹跳乘数</span><span class="sxs-lookup"><span data-stu-id="1d640-198">Bounce multiplier</span></span>   | <span data-ttu-id="1d640-199">当使用每个帧的衰减或每个项的衰减时，将更多弹跳添加到列表的 overscroll。</span><span class="sxs-lookup"><span data-stu-id="1d640-199">Multiplier to add more bounce to the overscroll of a list when using falloff per frame or falloff per item.</span></span> |

| <span data-ttu-id="1d640-200">调试选项</span><span class="sxs-lookup"><span data-stu-id="1d640-200">Debug options</span></span>         | <span data-ttu-id="1d640-201">说明</span><span class="sxs-lookup"><span data-stu-id="1d640-201">Description</span></span>                                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1d640-202">已启用掩码</span><span class="sxs-lookup"><span data-stu-id="1d640-202">Mask enabled</span></span>          | <span data-ttu-id="1d640-203">滚动内容的可见性模式。</span><span class="sxs-lookup"><span data-stu-id="1d640-203">Visibility mode of scroll content.</span></span> <span data-ttu-id="1d640-204">默认值将屏蔽滚动可查看区域之外的所有对象。</span><span class="sxs-lookup"><span data-stu-id="1d640-204">Default value will mask all objects outside of the scroll viewable area.</span></span> |
| <span data-ttu-id="1d640-205">显示阈值平面</span><span class="sxs-lookup"><span data-stu-id="1d640-205">Show threshold planes</span></span> | <span data-ttu-id="1d640-206">如果为 true，编辑器将在滚动边界周围呈现触摸释放阈值平面。</span><span class="sxs-lookup"><span data-stu-id="1d640-206">If true, the editor will render the touch release threshold planes around the scroll boundaries.</span></span>            |
| <span data-ttu-id="1d640-207">调试分页</span><span class="sxs-lookup"><span data-stu-id="1d640-207">Debug pagination</span></span>      | <span data-ttu-id="1d640-208">使用本部分可在运行时调试滚动分页。</span><span class="sxs-lookup"><span data-stu-id="1d640-208">Use this section to debug the scroll pagination during runtime.</span></span>                                             |

| <span data-ttu-id="1d640-209">事件</span><span class="sxs-lookup"><span data-stu-id="1d640-209">Events</span></span>              | <span data-ttu-id="1d640-210">说明</span><span class="sxs-lookup"><span data-stu-id="1d640-210">Description</span></span>                                                                                                                   |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1d640-211">单击</span><span class="sxs-lookup"><span data-stu-id="1d640-211">On click</span></span>            | <span data-ttu-id="1d640-212">当滚动背景碰撞体或任何其交互式内容收到单击时触发。</span><span class="sxs-lookup"><span data-stu-id="1d640-212">Triggered when the scroll background collider or any of its interactive content receives a click.</span></span>                             |
| <span data-ttu-id="1d640-213">触控启动</span><span class="sxs-lookup"><span data-stu-id="1d640-213">On touch started</span></span>    | <span data-ttu-id="1d640-214">当滚动背景碰撞体或任何其交互内容收到近交互触摸时触发。</span><span class="sxs-lookup"><span data-stu-id="1d640-214">Triggered when the scroll background collider or any of its interactive content receives a near interaction touch.</span></span>            |
| <span data-ttu-id="1d640-215">触控结束时</span><span class="sxs-lookup"><span data-stu-id="1d640-215">On touch ended</span></span>      | <span data-ttu-id="1d640-216">当近交互指针跨越发布阈值平面时，当活动触摸交互终止时触发。</span><span class="sxs-lookup"><span data-stu-id="1d640-216">Triggered when an active touch interaction is terminated when the near interaction pointer crosses a release threshold plane.</span></span> |
| <span data-ttu-id="1d640-217">启动时</span><span class="sxs-lookup"><span data-stu-id="1d640-217">On momentum started</span></span> | <span data-ttu-id="1d640-218">当滚动容器开始通过交互、速度回退或分页移动时触发。</span><span class="sxs-lookup"><span data-stu-id="1d640-218">Triggered when the scroll container starts moving by interaction, velocity falloff, or pagination.</span></span>                            |
| <span data-ttu-id="1d640-219">在动量结束时</span><span class="sxs-lookup"><span data-stu-id="1d640-219">On momentum ended</span></span>   | <span data-ttu-id="1d640-220">滚动容器通过交互、速度回退或分页停止移动时触发。</span><span class="sxs-lookup"><span data-stu-id="1d640-220">Triggered when the scroll container stops moving by interaction, velocity falloff, or pagination.</span></span>                             |

## <a name="scrolling-example-scene"></a><span data-ttu-id="1d640-221">滚动示例场景</span><span class="sxs-lookup"><span data-stu-id="1d640-221">Scrolling example scene</span></span>

<span data-ttu-id="1d640-222">**ScrollingObjectCollection.unity** 示例场景包含 3 个可滚动的示例，每个示例具有不同的速度回退配置。</span><span class="sxs-lookup"><span data-stu-id="1d640-222">**ScrollingObjectCollection.unity** example scene consists of 3 scrollable examples, each one with a different velocity falloff configuration.</span></span> <span data-ttu-id="1d640-223">示例场景包含用于显示默认情况下在层次结构中禁用的图面放置行为的墙。</span><span class="sxs-lookup"><span data-stu-id="1d640-223">The example scene contains walls to show the surface placement behavior that are disabled by default in the hierarchy.</span></span> <span data-ttu-id="1d640-224">可以在 文件夹下找到示例 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` 场景。</span><span class="sxs-lookup"><span data-stu-id="1d640-224">The example scene can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` folder.</span></span>

![滚动对象集合示例场景](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a><span data-ttu-id="1d640-226">滚动示例预制</span><span class="sxs-lookup"><span data-stu-id="1d640-226">Scrolling example prefabs</span></span>

<span data-ttu-id="1d640-227">为方便起见，可以使用两个滚动对象集合预制件。</span><span class="sxs-lookup"><span data-stu-id="1d640-227">For convenience, two scrolling object collection prefabs are available to use.</span></span> <span data-ttu-id="1d640-228">可以在 文件夹下找到示例 ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` 预制项。</span><span class="sxs-lookup"><span data-stu-id="1d640-228">The example prefabs can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` folder.</span></span>

![滚动对象集合预制件](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a><span data-ttu-id="1d640-230">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d640-230">See also</span></span>

* [<span data-ttu-id="1d640-231">剪辑基元</span><span class="sxs-lookup"><span data-stu-id="1d640-231">Clipping Primitive</span></span>](../rendering/clipping-primitive.md)
* [<span data-ttu-id="1d640-232">材料实例</span><span class="sxs-lookup"><span data-stu-id="1d640-232">Material Instance</span></span>](../rendering/material-instance.md)
* [<span data-ttu-id="1d640-233">标准着色器</span><span class="sxs-lookup"><span data-stu-id="1d640-233">Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
* [<span data-ttu-id="1d640-234">对象集合</span><span class="sxs-lookup"><span data-stu-id="1d640-234">Object collection</span></span>](object-collection.md)
