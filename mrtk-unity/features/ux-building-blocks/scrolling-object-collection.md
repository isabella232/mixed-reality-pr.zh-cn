---
title: 滚动对象集合
description: 概述菜单类型 MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，滚动对象
ms.openlocfilehash: 0ed1d61aed203a5daa45c5d89990e66115cc3abb
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300112"
---
# <a name="scrolling-object-collection"></a><span data-ttu-id="4e754-104">滚动对象集合</span><span class="sxs-lookup"><span data-stu-id="4e754-104">Scrolling object collection</span></span>

![滚动对象集合](../images/scrolling-collection/ScrollingCollection_Main.jpg)

<span data-ttu-id="4e754-106">MRTK 滚动对象集合是一个 UX 组件，通过包含的可查看区域启用3D 内容滚动。</span><span class="sxs-lookup"><span data-stu-id="4e754-106">The MRTK scrolling object collection is an UX component that enables scrolling of 3D content through a contained viewable area.</span></span> <span data-ttu-id="4e754-107">滚动移动可由近或远的输入交互以及离散分页触发。</span><span class="sxs-lookup"><span data-stu-id="4e754-107">The scrolling movement can be triggered by near or far input interaction and by discrete pagination.</span></span> <span data-ttu-id="4e754-108">它支持交互式和非交互式对象。</span><span class="sxs-lookup"><span data-stu-id="4e754-108">It supports both interactive and non-interactive objects.</span></span>

## <a name="getting-started-with-the-scrolling-object-collection"></a><span data-ttu-id="4e754-109">滚动对象集合入门</span><span class="sxs-lookup"><span data-stu-id="4e754-109">Getting started with the scrolling object collection</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="4e754-110">设置场景</span><span class="sxs-lookup"><span data-stu-id="4e754-110">Setting up the scene</span></span>

1. <span data-ttu-id="4e754-111">创建新的 unity 场景。</span><span class="sxs-lookup"><span data-stu-id="4e754-111">Create a new unity scene.</span></span>
1. <span data-ttu-id="4e754-112">通过导航到 **混合现实工具包**"  >  **添加到场景" 并配置，** 将 MRTK 添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="4e754-112">Add MRTK to the scene by navigating to the **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

### <a name="setting-up-the-scrolling-object"></a><span data-ttu-id="4e754-113">设置滚动对象</span><span class="sxs-lookup"><span data-stu-id="4e754-113">Setting up the scrolling object</span></span>

1. <span data-ttu-id="4e754-114">在场景中创建一个空游戏对象，并将其位置更改为 (0，0，1) 。</span><span class="sxs-lookup"><span data-stu-id="4e754-114">Create an empty game object in the scene and change its position to (0, 0, 1).</span></span>
1. <span data-ttu-id="4e754-115">向游戏对象添加 [滚动对象集合](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) 组件。</span><span class="sxs-lookup"><span data-stu-id="4e754-115">Add a [scrolling object collection](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) component to the game object.</span></span>

    <span data-ttu-id="4e754-116">添加滚动对象集合时，会自动将一个框碰撞器和 [近交互可触摸](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 组件连接到根游戏对象。</span><span class="sxs-lookup"><span data-stu-id="4e754-116">When the scrolling object collection is added, a box collider and a [near interaction touchable](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component will be automatically attached to the root game object.</span></span> <span data-ttu-id="4e754-117">这些组件允许 scroll 对象侦听近和远交互输入事件，如指针触摸或单击。</span><span class="sxs-lookup"><span data-stu-id="4e754-117">These components allow the scroll object to listen to near and far interaction input events, like a pointer touch or click.</span></span>  

    <span data-ttu-id="4e754-118">MRTK 滚动对象集合具有两个在根滚动对象层次结构下作为子游戏对象创建的重要元素：</span><span class="sxs-lookup"><span data-stu-id="4e754-118">The MRTK scrolling object collection has two important elements that are created as child game objects under the root scrolling object hierarchy:</span></span>
    * <span data-ttu-id="4e754-119">`Container` -所有滚动内容对象都必须是容器游戏对象的子项。</span><span class="sxs-lookup"><span data-stu-id="4e754-119">`Container` - All scrolling content objects must be children of the container game object.</span></span>
    * <span data-ttu-id="4e754-120">`Clipping bounds` -如果启用了滚动内容屏蔽，则剪辑边界元素可确保仅显示其边界内的可滚动内容。</span><span class="sxs-lookup"><span data-stu-id="4e754-120">`Clipping bounds` - If scrolling content masking is enabled, the clipping bounds element ensures that only the scrollable content inside its boundaries is visible.</span></span> <span data-ttu-id="4e754-121">剪切边界游戏对象包含两个组件：禁用的框碰撞器和 [剪切框](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)。</span><span class="sxs-lookup"><span data-stu-id="4e754-121">The clipping bounds game object has two components: a disabled box collider and a [clipping box](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).</span></span>

![滚动对象集合元素](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a><span data-ttu-id="4e754-123">向滚动对象添加内容</span><span class="sxs-lookup"><span data-stu-id="4e754-123">Adding content to the scrolling object</span></span>

<span data-ttu-id="4e754-124">滚动对象集合可以与 [网格对象集合](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 结合使用，以便在大小和间距相同的对齐元素网格中布局内容。</span><span class="sxs-lookup"><span data-stu-id="4e754-124">The scrolling object collection can be combined with a [grid object collection](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) to layout content in a grid of aligned elements that have uniform size and spacing.</span></span>

1. <span data-ttu-id="4e754-125">创建一个空游戏对象作为滚动容器的子级。</span><span class="sxs-lookup"><span data-stu-id="4e754-125">Create an empty game object as a child of the scroll container.</span></span>
1. <span data-ttu-id="4e754-126">向游戏对象添加网格对象集合组件。</span><span class="sxs-lookup"><span data-stu-id="4e754-126">Add a grid object collection component to the game object.</span></span>
1. <span data-ttu-id="4e754-127">对于垂直单列滚动，在 "检查器" 选项卡中，按如下所示配置网格对象集合：</span><span class="sxs-lookup"><span data-stu-id="4e754-127">For a vertical single column scroll, in the inspector tab, configure the grid object collection as follow:</span></span>
    * <span data-ttu-id="4e754-128">**列** 数：1</span><span class="sxs-lookup"><span data-stu-id="4e754-128">**Num columns**: 1</span></span>
    * <span data-ttu-id="4e754-129">**布局**：列 then 行</span><span class="sxs-lookup"><span data-stu-id="4e754-129">**Layout**: column then row</span></span>
    * <span data-ttu-id="4e754-130">**定位点**：左上</span><span class="sxs-lookup"><span data-stu-id="4e754-130">**Anchor**: upper left</span></span>
1. <span data-ttu-id="4e754-131">根据内容对象的尺寸更改 **单元格的宽度** 和 **高度** 。</span><span class="sxs-lookup"><span data-stu-id="4e754-131">Change the **cell width** and **height** according to the dimensions of the content objects.</span></span>
1. <span data-ttu-id="4e754-132">添加内容对象作为网格对象的子级。</span><span class="sxs-lookup"><span data-stu-id="4e754-132">Add the content objects as children of the grid object.</span></span>
1. <span data-ttu-id="4e754-133">按 " **更新集合**"。</span><span class="sxs-lookup"><span data-stu-id="4e754-133">Press **update collection**.</span></span>

![网格布局](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> <span data-ttu-id="4e754-135">任何滚动内容对象材料必须使用 [MRTK 标准着色器](../rendering/MRTK-standard-shader.md) ，才能使可视区域上的剪辑效果正常工作。</span><span class="sxs-lookup"><span data-stu-id="4e754-135">Any scrolling content object material must use the [MRTK standard shader](../rendering/MRTK-standard-shader.md) in order for the clipping effect on the viewable area to work properly.</span></span>

> [!NOTE]
> <span data-ttu-id="4e754-136">如果启用了滚动内容屏蔽，则滚动对象集合将向附加了呈现器的任何内容对象添加 [材料实例](../rendering/material-instance.md) 组件。</span><span class="sxs-lookup"><span data-stu-id="4e754-136">If scrolling content masking is enabled, the scrolling object collection will add a [material instance](../rendering/material-instance.md) component to any content objects that have a renderer attached.</span></span> <span data-ttu-id="4e754-137">此组件用于管理实例材料生存期并提高内存性能。</span><span class="sxs-lookup"><span data-stu-id="4e754-137">This component is used to manage instanced materials lifetime and improve memory performance.</span></span>

### <a name="configuring-the-scrolling-viewable-area"></a><span data-ttu-id="4e754-138">配置滚动可查看区域</span><span class="sxs-lookup"><span data-stu-id="4e754-138">Configuring the scrolling viewable area</span></span>

1. <span data-ttu-id="4e754-139">对于垂直滚动浏览对象的单个列，请在 "检查器" 选项卡中，按如下所示配置滚动对象集合：</span><span class="sxs-lookup"><span data-stu-id="4e754-139">For vertical scrolling through a single column of objects, in the inspector tab, configure the scrolling object collection as follow:</span></span>
    * <span data-ttu-id="4e754-140">**单元格/层**：1</span><span class="sxs-lookup"><span data-stu-id="4e754-140">**Cells per tier**: 1</span></span>
    * <span data-ttu-id="4e754-141">根据所需的可见行数选择 **每页的层** 数</span><span class="sxs-lookup"><span data-stu-id="4e754-141">Choose the number of **tiers per page** according to the desired number of visible rows</span></span>
1. <span data-ttu-id="4e754-142">根据内容对象的尺寸更改 **页面单元宽度**、 **高度** 和 **深度** 。</span><span class="sxs-lookup"><span data-stu-id="4e754-142">Change the **page cell width**, **height** and **depth** according to the dimensions of the content objects.</span></span>

<span data-ttu-id="4e754-143">请注意，当前已禁用滚动可见区域外的内容对象，而与滚动线框相交的对象可能会被剪辑基元部分屏蔽。</span><span class="sxs-lookup"><span data-stu-id="4e754-143">Notice how the content objects lying outside the scrolling viewable area are now disabled, while objects intersecting the scroll wireframe might be partially masked by the clipping primitive.</span></span>

![可视区域](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a><span data-ttu-id="4e754-145">在编辑器中测试滚动对象集合</span><span class="sxs-lookup"><span data-stu-id="4e754-145">Testing the scrolling object collection in the editor</span></span>

1. <span data-ttu-id="4e754-146">按下 "播放" 并按住空格键以显示输入模拟手。</span><span class="sxs-lookup"><span data-stu-id="4e754-146">Press play and hold the space bar to show an input simulation hand.</span></span>
1. <span data-ttu-id="4e754-147">移动手直到滚动碰撞器或任何滚动交互内容处于焦点状态，并通过单击并上下拖动鼠标并触发滚动移动。</span><span class="sxs-lookup"><span data-stu-id="4e754-147">Move the hand until the scrolling collider or any scrolling interactive content is in focus and trigger the scrolling movement by clicking and dragging up and down with the left mouse.</span></span>

## <a name="controlling-the-scrolling-object-from-code"></a><span data-ttu-id="4e754-148">从代码控制滚动对象</span><span class="sxs-lookup"><span data-stu-id="4e754-148">Controlling the scrolling object from code</span></span>

<span data-ttu-id="4e754-149">MRTK 滚动对象集合公开了一些公共方法，这些公共方法允许移动滚动容器，方法是根据属性配置对齐滚动容器的位置 `pagination` 。</span><span class="sxs-lookup"><span data-stu-id="4e754-149">The MRTK scrolling object collection exposes a few public methods that allow moving the scrolling container by snapping its position according to the `pagination` properties configuration.</span></span>

<span data-ttu-id="4e754-150">有关如何访问滚动对象集合分页接口的示例，可在文件夹下使用 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` 。</span><span class="sxs-lookup"><span data-stu-id="4e754-150">An example of how to access the scrolling object collection pagination interface is available to use under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` folder.</span></span> <span data-ttu-id="4e754-151">可 [滚动分页](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) 示例脚本可以链接到场景中的任何现有的滚动对象集合。</span><span class="sxs-lookup"><span data-stu-id="4e754-151">The [scrollable pagination](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) example script can be linked to any existing scrolling object collection in the scene.</span></span> <span data-ttu-id="4e754-152">然后，该脚本可以由显示 Unity 事件的场景组件引用 (例如， [MRTK 按钮](button.md)) 。</span><span class="sxs-lookup"><span data-stu-id="4e754-152">The script can then be referenced by scene components exposing Unity events (e.g, [MRTK button](button.md)).</span></span>

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

## <a name="scrolling-object-collection-properties"></a><span data-ttu-id="4e754-153">滚动对象集合属性</span><span class="sxs-lookup"><span data-stu-id="4e754-153">Scrolling object collection properties</span></span>

| <span data-ttu-id="4e754-154">常规</span><span class="sxs-lookup"><span data-stu-id="4e754-154">General</span></span>                                                                                                                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4e754-155">滚动方向</span><span class="sxs-lookup"><span data-stu-id="4e754-155">Scroll direction</span></span>             | <span data-ttu-id="4e754-156">内容应滚动的方向。</span><span class="sxs-lookup"><span data-stu-id="4e754-156">The direction in which content should scroll.</span></span>|

| <span data-ttu-id="4e754-157">分页</span><span class="sxs-lookup"><span data-stu-id="4e754-157">Pagination</span></span>                   |               <span data-ttu-id="4e754-158">说明</span><span class="sxs-lookup"><span data-stu-id="4e754-158">Description</span></span>                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4e754-159">单元格数</span><span class="sxs-lookup"><span data-stu-id="4e754-159">Cells per tier</span></span>               | <span data-ttu-id="4e754-160">向上滚动视图中的行中的单元格数或左侧滚动视图中列的单元格数。</span><span class="sxs-lookup"><span data-stu-id="4e754-160">Number of cells in a row on up-down scroll view or number of cells in a column on left-right scroll view.</span></span>                                                                                                         |
| <span data-ttu-id="4e754-161">每页层数</span><span class="sxs-lookup"><span data-stu-id="4e754-161">Tiers per page</span></span>               | <span data-ttu-id="4e754-162">滚动区域中可见层的数目。</span><span class="sxs-lookup"><span data-stu-id="4e754-162">Number of visible tiers in the scrolling area.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="4e754-163">页面单元</span><span class="sxs-lookup"><span data-stu-id="4e754-163">Page cell</span></span>                    | <span data-ttu-id="4e754-164">分页单元格的尺寸。</span><span class="sxs-lookup"><span data-stu-id="4e754-164">Dimensions of the pagination cell.</span></span>                  |

| <span data-ttu-id="4e754-165">高级设置</span><span class="sxs-lookup"><span data-stu-id="4e754-165">Advanced settings</span></span>            |                  <span data-ttu-id="4e754-166">说明</span><span class="sxs-lookup"><span data-stu-id="4e754-166">Description</span></span>                                                                                                                                                                                    |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4e754-167">掩码编辑模式</span><span class="sxs-lookup"><span data-stu-id="4e754-167">Mask edit mode</span></span>               | <span data-ttu-id="4e754-168">用于定义剪辑框掩码边界的编辑模式。</span><span class="sxs-lookup"><span data-stu-id="4e754-168">Edit modes for defining the clipping box masking boundaries.</span></span> <span data-ttu-id="4e754-169">选择 "自动" 可自动使用分页值。</span><span class="sxs-lookup"><span data-stu-id="4e754-169">Choose 'Auto' to automatically use pagination values.</span></span> <span data-ttu-id="4e754-170">选择 "手动" 以启用对剪切框对象的直接操作。</span><span class="sxs-lookup"><span data-stu-id="4e754-170">Choose 'Manual' for enabling direct manipulation of the clipping box object.</span></span>|
| <span data-ttu-id="4e754-171">碰撞器编辑模式</span><span class="sxs-lookup"><span data-stu-id="4e754-171">Collider edit mode</span></span>           | <span data-ttu-id="4e754-172">用于定义滚动交互碰撞器边界的编辑模式。</span><span class="sxs-lookup"><span data-stu-id="4e754-172">Edit modes for defining the scroll interaction collider boundaries.</span></span> <span data-ttu-id="4e754-173">选择 "自动" 可自动使用分页值。</span><span class="sxs-lookup"><span data-stu-id="4e754-173">Choose 'Auto' to automatically use pagination values.</span></span> <span data-ttu-id="4e754-174">选择 "手动" 以启用碰撞器的直接操作。</span><span class="sxs-lookup"><span data-stu-id="4e754-174">Choose 'Manual' for enabling direct manipulation of the collider.</span></span>|
| <span data-ttu-id="4e754-175">可以滚动</span><span class="sxs-lookup"><span data-stu-id="4e754-175">Can scroll</span></span>                   | <span data-ttu-id="4e754-176">启用/禁用对近/远交互的滚动。</span><span class="sxs-lookup"><span data-stu-id="4e754-176">Enables/disables scrolling with near/far interaction.</span></span>                  |
| <span data-ttu-id="4e754-177">在预呈现时使用</span><span class="sxs-lookup"><span data-stu-id="4e754-177">Use on pre render</span></span>            | <span data-ttu-id="4e754-178">切换 scrollingObjectCollection 是否将使用摄像 OnPreRender 事件来管理内容可见性。</span><span class="sxs-lookup"><span data-stu-id="4e754-178">Toggles whether the scrollingObjectCollection will use the Camera OnPreRender event to manage content visibility.</span></span>                  |
| <span data-ttu-id="4e754-179">分页曲线</span><span class="sxs-lookup"><span data-stu-id="4e754-179">Pagination curve</span></span>             | <span data-ttu-id="4e754-180">用于分页的动画曲线。</span><span class="sxs-lookup"><span data-stu-id="4e754-180">Animation curve for pagination.</span></span>                  |
| <span data-ttu-id="4e754-181">动画长度</span><span class="sxs-lookup"><span data-stu-id="4e754-181">Animation length</span></span>             | <span data-ttu-id="4e754-182">PaginationCurve 计算所需的时间量，以秒为单位)  (。</span><span class="sxs-lookup"><span data-stu-id="4e754-182">The amount of time (in seconds) the PaginationCurve will take to evaluate.</span></span>                  |
| <span data-ttu-id="4e754-183">手动增量滚动阈值</span><span class="sxs-lookup"><span data-stu-id="4e754-183">Hand delta scroll threshold</span></span>  | <span data-ttu-id="4e754-184">在触发滚动拖动之前，当前指针可以沿滚动方向行进的距离（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="4e754-184">The distance, in meters, the current pointer can travel along the scroll direction before triggering a scroll drag.</span></span>                  |
| <span data-ttu-id="4e754-185">正面触摸距离</span><span class="sxs-lookup"><span data-stu-id="4e754-185">Front touch distance</span></span>         | <span data-ttu-id="4e754-186">定位用于验证在滚动视图前面是否启动了触摸屏交互的本地 xy 平面的距离（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="4e754-186">Distance, in meters, to position a local xy plane used to verify if a touch interaction started in the front of the scroll view.</span></span>                  |
| <span data-ttu-id="4e754-187">发布阈值</span><span class="sxs-lookup"><span data-stu-id="4e754-187">Release threshold</span></span>            | <span data-ttu-id="4e754-188">从与已释放的触摸开始转换所需的滚动边界，收回量（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="4e754-188">Withdraw amount, in meters, from the scroll boundaries needed to transition from touch engaged to released.</span></span>                  |

| <span data-ttu-id="4e754-189">速度</span><span class="sxs-lookup"><span data-stu-id="4e754-189">Velocity</span></span> |               <span data-ttu-id="4e754-190">说明</span><span class="sxs-lookup"><span data-stu-id="4e754-190">Description</span></span>                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4e754-191">速度类型</span><span class="sxs-lookup"><span data-stu-id="4e754-191">Type of velocity</span></span>       | <span data-ttu-id="4e754-192">滚动条的所需速度过渡类型。</span><span class="sxs-lookup"><span data-stu-id="4e754-192">The desired type of velocity falloff for the scroller.</span></span>                                                                                        |
| <span data-ttu-id="4e754-193">速度乘数</span><span class="sxs-lookup"><span data-stu-id="4e754-193">Velocity multiplier</span></span>     | <span data-ttu-id="4e754-194">要应用到滚动条的 (额外) 速度量。</span><span class="sxs-lookup"><span data-stu-id="4e754-194">Amount of (extra) velocity to be applied to scroller.</span></span>                                                                                                                                                        |
| <span data-ttu-id="4e754-195">速度 dampen</span><span class="sxs-lookup"><span data-stu-id="4e754-195">Velocity dampen</span></span>     | <span data-ttu-id="4e754-196">应用到速度的衰减量。</span><span class="sxs-lookup"><span data-stu-id="4e754-196">Amount of falloff applied to the velocity.</span></span> |
| <span data-ttu-id="4e754-197">弹跳乘数</span><span class="sxs-lookup"><span data-stu-id="4e754-197">Bounce multiplier</span></span>     | <span data-ttu-id="4e754-198">当使用每个帧的衰减或每个项的衰减时，将更多弹跳添加到列表的 overscroll。</span><span class="sxs-lookup"><span data-stu-id="4e754-198">Multiplier to add more bounce to the overscroll of a list when using falloff per frame or falloff per item.</span></span> |

| <span data-ttu-id="4e754-199">调试选项</span><span class="sxs-lookup"><span data-stu-id="4e754-199">Debug options</span></span> |            <span data-ttu-id="4e754-200">说明</span><span class="sxs-lookup"><span data-stu-id="4e754-200">Description</span></span>                                                                                                                                                                         |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4e754-201">掩码已启用</span><span class="sxs-lookup"><span data-stu-id="4e754-201">Mask enabled</span></span>       | <span data-ttu-id="4e754-202">滚动内容的可见性模式。</span><span class="sxs-lookup"><span data-stu-id="4e754-202">Visibility mode of scroll content.</span></span> <span data-ttu-id="4e754-203">默认值将屏蔽滚动可查看区域之外的所有对象。</span><span class="sxs-lookup"><span data-stu-id="4e754-203">Default value will mask all objects outside of the scroll viewable area.</span></span>                                                                                        |
| <span data-ttu-id="4e754-204">显示阈值平面</span><span class="sxs-lookup"><span data-stu-id="4e754-204">Show threshold planes</span></span>     | <span data-ttu-id="4e754-205">如果为 true，则编辑器将呈现围绕滚动边界的触摸释放阈值平面。</span><span class="sxs-lookup"><span data-stu-id="4e754-205">If true, the editor will render the touch release threshold planes around the scroll boundaries.</span></span>                                                                                                                                                        |
| <span data-ttu-id="4e754-206">调试分页</span><span class="sxs-lookup"><span data-stu-id="4e754-206">Debug pagination</span></span>     | <span data-ttu-id="4e754-207">使用此部分可在运行时调试滚动分页。</span><span class="sxs-lookup"><span data-stu-id="4e754-207">Use this section to debug the scroll pagination during runtime.</span></span> |

| <span data-ttu-id="4e754-208">事件</span><span class="sxs-lookup"><span data-stu-id="4e754-208">Events</span></span>|    <span data-ttu-id="4e754-209">说明</span><span class="sxs-lookup"><span data-stu-id="4e754-209">Description</span></span>                                                                                                                                                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4e754-210">单击时</span><span class="sxs-lookup"><span data-stu-id="4e754-210">On click</span></span>       | <span data-ttu-id="4e754-211">当滚动背景碰撞器或其任何交互式内容收到单击时触发的事件。</span><span class="sxs-lookup"><span data-stu-id="4e754-211">Event triggered when the scroll background collider or any of its interactive content receives a click.</span></span>                                                                                        |
| <span data-ttu-id="4e754-212">开始触控</span><span class="sxs-lookup"><span data-stu-id="4e754-212">On touch started</span></span>     | <span data-ttu-id="4e754-213">当滚动背景碰撞器或其任何交互式内容收到近交互触摸时触发的事件。</span><span class="sxs-lookup"><span data-stu-id="4e754-213">Event triggered when the scroll background collider or any of its interactive content receives a near interaction touch.</span></span>                                                                                                                                                        |
| <span data-ttu-id="4e754-214">On touch 结束</span><span class="sxs-lookup"><span data-stu-id="4e754-214">On touch ended</span></span>     | <span data-ttu-id="4e754-215">通过使近交互指针跨越某个版本阈值平面终止活动触摸交互时触发的事件。</span><span class="sxs-lookup"><span data-stu-id="4e754-215">Event triggered when an active touch interaction is terminated by having the near interaction pointer crossing one of the release threshold planes.</span></span> |
| <span data-ttu-id="4e754-216">起步后</span><span class="sxs-lookup"><span data-stu-id="4e754-216">On momentum started</span></span>     | <span data-ttu-id="4e754-217">滚动容器由交互、速度 fallofff 或分页开始移动时触发的事件。</span><span class="sxs-lookup"><span data-stu-id="4e754-217">Event triggered when the scroll container starts moving by interaction, velocity fallofff or pagination.</span></span> |
| <span data-ttu-id="4e754-218">在动力结束时</span><span class="sxs-lookup"><span data-stu-id="4e754-218">On momentum ended</span></span>     | <span data-ttu-id="4e754-219">滚动容器停止交互、速度 fallofff 或分页时触发的事件。</span><span class="sxs-lookup"><span data-stu-id="4e754-219">Event triggered when the scroll container stops moving by interaction, velocity fallofff or pagination.</span></span> |

## <a name="scrolling-example-scene"></a><span data-ttu-id="4e754-220">滚动示例场景</span><span class="sxs-lookup"><span data-stu-id="4e754-220">Scrolling example scene</span></span>

<span data-ttu-id="4e754-221">**ScrollingObjectCollection** 示例场景包含3个可滚动的示例，每个示例都有不同的速度衰减配置。</span><span class="sxs-lookup"><span data-stu-id="4e754-221">**ScrollingObjectCollection.unity** example scene consists of 3 scrollable examples, each one with a different velocity falloff configuration.</span></span> <span data-ttu-id="4e754-222">示例场景包含用于显示在层次结构中默认禁用的表面布局行为的墙壁。</span><span class="sxs-lookup"><span data-stu-id="4e754-222">The example scene contains walls to show the surface placement behavior that are disabled by default in the hierarchy.</span></span> <span data-ttu-id="4e754-223">示例场景可以在文件夹下找到 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` 。</span><span class="sxs-lookup"><span data-stu-id="4e754-223">The example scene can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` folder.</span></span>

![滚动对象集合示例场景](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a><span data-ttu-id="4e754-225">滚动示例 prototyping</span><span class="sxs-lookup"><span data-stu-id="4e754-225">Scrolling example prefabs</span></span>

<span data-ttu-id="4e754-226">为方便起见，可以使用两个滚动对象集合 prototyping。</span><span class="sxs-lookup"><span data-stu-id="4e754-226">For convenience, two scrolling object collection prefabs are available to use.</span></span> <span data-ttu-id="4e754-227">示例 prototyping 可以在文件夹下找到 ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` 。</span><span class="sxs-lookup"><span data-stu-id="4e754-227">The example prefabs can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` folder.</span></span>

![滚动对象集合 prototyping](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a><span data-ttu-id="4e754-229">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e754-229">See also</span></span>

* [<span data-ttu-id="4e754-230">剪辑基元</span><span class="sxs-lookup"><span data-stu-id="4e754-230">Clipping Primitive</span></span>](../rendering/clipping-primitive.md)
* [<span data-ttu-id="4e754-231">材料实例</span><span class="sxs-lookup"><span data-stu-id="4e754-231">Material Instance</span></span>](../rendering/material-instance.md)
* [<span data-ttu-id="4e754-232">标准着色器</span><span class="sxs-lookup"><span data-stu-id="4e754-232">Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
* [<span data-ttu-id="4e754-233">对象集合</span><span class="sxs-lookup"><span data-stu-id="4e754-233">Object collection</span></span>](object-collection.md)
