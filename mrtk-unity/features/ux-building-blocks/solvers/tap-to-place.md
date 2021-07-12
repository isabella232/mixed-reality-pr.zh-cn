---
title: 点击以放置
description: TapToPlace MRTK 文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity,HoloLens, HoloLens 2, 混合现实, 开发, MRTK, 点击以放置,
ms.openlocfilehash: 1664509a08c2d589d22b71df580328f3f3655c61
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176401"
---
# <a name="tap-to-place"></a><span data-ttu-id="a2b7b-104">点击以放置</span><span class="sxs-lookup"><span data-stu-id="a2b7b-104">Tap to place</span></span>

![TapToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

<span data-ttu-id="a2b7b-106">“点击以放置”是一个远距离交互组件，用于将游戏对象放置在表面上。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-106">Tap to Place is a far interaction component that is used to place a game object on surface.</span></span> <span data-ttu-id="a2b7b-107">此组件适用于将对象放置在空间网格上。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-107">This component is useful for placing objects on a spatial mesh.</span></span> <span data-ttu-id="a2b7b-108">“点击以放置”使用两个单击和头部运动的组合来放置对象。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-108">Tap to Place uses a combination of two clicks and head movement to place an object.</span></span> <span data-ttu-id="a2b7b-109">一个单击用于开始放置，头部运动用于控制对象的位置，另一个单击用于将对象放置在场景中。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-109">A click to start the placement, head movement to control the position of the object and a click to place the object in the scene.</span></span>

## <a name="using-tap-to-place"></a><span data-ttu-id="a2b7b-110">使用点击以放置</span><span class="sxs-lookup"><span data-stu-id="a2b7b-110">Using Tap to Place</span></span>

1. <span data-ttu-id="a2b7b-111">设置场景</span><span class="sxs-lookup"><span data-stu-id="a2b7b-111">Set up the scene</span></span>
    - <span data-ttu-id="a2b7b-112">新建全新的 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="a2b7b-112">Create a new unity scene</span></span>
    - <span data-ttu-id="a2b7b-113">通过导航到“混合现实工具包” > “添加到场景并配置”，将 MRTK 添加到场景中</span><span class="sxs-lookup"><span data-stu-id="a2b7b-113">Add MRTK to the scene by navigating to the **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    > [!NOTE]
    > <span data-ttu-id="a2b7b-114">点击以放置使用 MRTK 输入系统驱动的单击，但也可以不使用单击进行控制，请参见下文的“点击以放置代码可配置性”部分。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-114">Tap to Place uses clicks driven by the MRTK Input System but it can also be controlled without clicks, see the Tap To Place Code Configurability section below.</span></span>
    - <span data-ttu-id="a2b7b-115">将立方体添加到场景中，将刻度更改为 0.2，并将位置更改为 (0, 0, 0.7)。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-115">Add a cube to the scene and change the scale to 0.2 and change the position to (0, 0, 0.7).</span></span>
1. <span data-ttu-id="a2b7b-116">将[点击以放置](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace)附加到具有碰撞器的游戏对象</span><span class="sxs-lookup"><span data-stu-id="a2b7b-116">Attach [Tap to Place](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) to a game object with a collider</span></span>

    ![TapToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - <span data-ttu-id="a2b7b-118">添加“点击以放置”组件时，还会附加“求解器处理程序”。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-118">When the Tap to Place component is added, a Solver Handler will also be attached.</span></span> <span data-ttu-id="a2b7b-119">“点击以放置”将派生自需要求解器处理程序的[求解器](solver.md)类。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-119">Tap to Place derives from the [Solver](solver.md) class which requires a Solver Handler.</span></span> <span data-ttu-id="a2b7b-120">“点击以放置”对象的位置是相对于求解器处理程序中的 `TrackedTargetType` 计算出来的。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-120">The position of a Tap to Place object is calculated relative to the `TrackedTargetType` within the Solver Handler.</span></span> <span data-ttu-id="a2b7b-121">默认情况下，头部为 `TrackedTargetType`，即当头部移动时，选择的对象也会跟随移动。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-121">By default the Head is the `TrackedTargetType`, i.e. when the head moves, the object follows if it is selected.</span></span>  <span data-ttu-id="a2b7b-122">`TrackedTargetType` 还可以设置为控制器射线，该射线会让对象跟随控制器。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-122">The `TrackedTargetType` can also be set to Controller Ray which has the object follow the controller.</span></span> <span data-ttu-id="a2b7b-123">点击以放置检查器中的第一组属性是[常见的求解器属性](solver.md#common-solver-properties)。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-123">The first group of properties in the Tap to Place inspector are the [Common Solver Properties](solver.md#common-solver-properties).</span></span>  
    > [!IMPORTANT]
    > <span data-ttu-id="a2b7b-124">点击以放置独立的求解器，不能与其他求解器链接在一起。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-124">Tap to Place is a stand alone Solver and cannot be chained with other Solvers.</span></span> <span data-ttu-id="a2b7b-125">它无法链接的原因是，在放置对象时，会使用 SolverHandler.UpdateSolvers 更新对象位置。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-125">It cannot be chained because SolverHandler.UpdateSolvers is used to update the object's position while it is being placed.</span></span>
    - <span data-ttu-id="a2b7b-126">点击以放置属性：</span><span class="sxs-lookup"><span data-stu-id="a2b7b-126">Tap to Place Properties:</span></span>
        - <span data-ttu-id="a2b7b-127">`Auto Start`：如果为 true，则点击以放置求解器将开始控制要放置的游戏对象的位置。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-127">`Auto Start`: If true, the Tap to Place solver will start out controlling the position of the game object to be placed.</span></span> <span data-ttu-id="a2b7b-128">对象将立即开始跟随 TrackedTargetType（头部或控制器射线）。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-128">The object will immediately start following the TrackedTargetType (Head or Controller Ray).</span></span> <span data-ttu-id="a2b7b-129">该值必须在调用 Start() 之前修改才能生效。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-129">This value must be modified before Start() is invoked in order to have any effect.</span></span>
        - <span data-ttu-id="a2b7b-130">`Default Placement Distance`：对象相对于 SolverHandler 中的 TrackedTargetType 放置的默认距离（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-130">`Default Placement Distance`: The default distance (in meters) an object will be placed relative to the TrackedTargetType forward in the SolverHandler.</span></span> <span data-ttu-id="a2b7b-131">如果表面没有被光线投射击中，则游戏对象放置在默认放置距离。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-131">The game object will be placed at the default placement distance if a surface is not hit by the raycast.</span></span>
        - <span data-ttu-id="a2b7b-132">`Max Raycast Distance`：基于“TrackedTargetType”原点的光线投射的最大距离（米）。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-132">`Max Raycast Distance`: The max distance (meters) for the raycast based on the 'TrackedTargetType' origin.</span></span> <span data-ttu-id="a2b7b-133">此光线投射查找要放置选定对象的表面。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-133">This raycast looks for a surface to place a selected object.</span></span>
        - <span data-ttu-id="a2b7b-134">`UseDefaultSurfaceNormalOffset`：默认情况下，此属性为 true，它确保所放置的对象在表面上对齐。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-134">`UseDefaultSurfaceNormalOffset`: This property is true by default, it ensures the object being placed is aligned on a surface.</span></span> <span data-ttu-id="a2b7b-135">如果此属性为 true，则将应用默认的表面法线偏移，而不是为 `SurfaceNormalOffset` 属性指定的任何值。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-135">If this property is true, the default surface normal offset will be applied instead of any value specified for the `SurfaceNormalOffset` property.</span></span> <span data-ttu-id="a2b7b-136">如果为 false，则将应用 `SurfaceNormalOffset` 的值。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-136">If false, the value for `SurfaceNormalOffset` will be applied.</span></span> <span data-ttu-id="a2b7b-137">默认的表面法线偏移是沿 z 轴的碰撞区范围。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-137">The default surface normal offset is the collider's extents along the z axis.</span></span>
        - <span data-ttu-id="a2b7b-138">`Surface Normal Offset`：当光线投射击中表面时，要放置的游戏对象的中心与表面法线之间的距离。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-138">`Surface Normal Offset`: The distance between the center of the game object to place and a surface along the surface normal, if the raycast hits a surface.</span></span> <span data-ttu-id="a2b7b-139">仅当 `UseDefaultSurfaceNormalOffset` 为 false 时，此属性才会应用于对象。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-139">This property is only applied to an object if `UseDefaultSurfaceNormalOffset` is false.</span></span>
        - <span data-ttu-id="a2b7b-140">`Keep Orientation Vertical`：如果为 true，则要放置的游戏对象将保持直立，并与 Vector3.up 平齐。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-140">`Keep Orientation Vertical`: If true, the game object to place will remain upright and in line with Vector3.up.</span></span>
        - <span data-ttu-id="a2b7b-141">`Rotate According to Surface`：如果为 false，则要放置的游戏对象将不会根据表面击中更改其旋转。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-141">`Rotate According to Surface`: If false, the game object to place will not change its rotation according to the surface hit.</span></span>  <span data-ttu-id="a2b7b-142">当 IsBeingPlaced 为 true 时，对象将始终面向相机。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-142">The object will remain facing the camera while IsBeingPlaced is true.</span></span>
        - <span data-ttu-id="a2b7b-143">`Magnetic Surfaces`：要按最高到最低优先级的顺序执行的 LayerMasks 数组。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-143">`Magnetic Surfaces`: An array of LayerMasks to execute from highest to lowest priority.</span></span> <span data-ttu-id="a2b7b-144">用于提供光线投射击中的第一层掩码用于位置计算。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-144">First layer mask to provide a raycast hit will be used for position calculations.</span></span>
        - <span data-ttu-id="a2b7b-145">`Debug Enabled`：如果为 true，并且在 Unity 编辑器中，则将以黄色绘制光线投射的法线。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-145">`Debug Enabled`: If true and in the Unity Editor, the normal of the raycast hit will be drawn in yellow.</span></span> <span data-ttu-id="a2b7b-146">如果 `RotateAccordingToSurface` 为 true，则启用调试非常有用，因为它会绘制表面击中的法线，这会直观地说明对象处于当前方向的原因。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-146">Debug enabled is useful when `RotateAccordingToSurface` is true because it draws the normal of the surface hit which visually explains why the object is set at its current orientation.</span></span>
        - <span data-ttu-id="a2b7b-147">`On Placing Started`：选择了要放置的游戏对象时，触发此事件一次。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-147">`On Placing Started`: This event is triggered once when the game object to place is selected.</span></span>
        - <span data-ttu-id="a2b7b-148">`On Placing Stopped`：未选择要放置的游戏对象时，触发此事件一次。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-148">`On Placing Stopped`: This event is triggered once when the game object to place is unselected, placed.</span></span>

1. <span data-ttu-id="a2b7b-149">在编辑器中测试“点击以放置”行为</span><span class="sxs-lookup"><span data-stu-id="a2b7b-149">Testing Tap to Place behavior in editor</span></span>
    - <span data-ttu-id="a2b7b-150">按“播放”并按住空格键以显示输入模拟手。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-150">Press play and hold the space bar to show an input simulation hand.</span></span>
    - <span data-ttu-id="a2b7b-151">移动手直到立方体获得焦点，并通过单击鼠标左键，模拟使用输入模拟手进行单击。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-151">Move the hand until the cube is in focus and simulate a click with the input simulation hand by clicking with the left mouse.</span></span>
        - <span data-ttu-id="a2b7b-152">如果场景中不存在碰撞器，则对象将按照定义的 `Default Placement Distance` 跟随 `TrackedTargetType`。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-152">If colliders are not present in the scene, the object will follow the `TrackedTargetType` at the defined `Default Placement Distance`.</span></span>
    - <span data-ttu-id="a2b7b-153">对象在被选中后跟随 `TrackedTargetType` 的运动。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-153">The object will follow the movement of the `TrackedTargetType` after selection.</span></span> <span data-ttu-id="a2b7b-154">若要在编辑器中模拟头部运动，请按 WASD 键。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-154">To simulate head movement in editor, press the WASD keys.</span></span> <span data-ttu-id="a2b7b-155">单击并按住鼠标右键，改变头部旋转。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-155">Change head rotation by clicking and holding the right mouse.</span></span>
    - <span data-ttu-id="a2b7b-156">若要停止放置对象，请再次单击。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-156">To stop placing the object, click again.</span></span>  <span data-ttu-id="a2b7b-157">对于停止放置单击，对象无需获得焦点。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-157">The object does not need to be in focus for the stop placement click.</span></span> <span data-ttu-id="a2b7b-158">只有在初次单击来启动放置过程时，才需要获得焦点。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-158">Focus is only required for the initial click that starts the placement process.</span></span>

    <span data-ttu-id="a2b7b-159">`TrackedTargetType`：头部（默认值）</span><span class="sxs-lookup"><span data-stu-id="a2b7b-159">`TrackedTargetType`: Head (Default)</span></span> |  <span data-ttu-id="a2b7b-160">`TrackedTargetType`：控制器射线</span><span class="sxs-lookup"><span data-stu-id="a2b7b-160">`TrackedTargetType`: Controller Ray</span></span>
    :-------------------------:|:-------------------------:
    ![点击以放置输入模拟头部控制射线](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![点击以放置输入模拟控制器射线 2](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a><span data-ttu-id="a2b7b-163">点击以放置代码可配置性</span><span class="sxs-lookup"><span data-stu-id="a2b7b-163">Tap to Place Code Configurability</span></span>

<span data-ttu-id="a2b7b-164">点击以放置对象选择时间还可以通过 `StartPlacement()` 和 `StopPlacement()` 来控制，而不需要单击事件。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-164">Tap to Place object selection timing can also be controlled via `StartPlacement()` and `StopPlacement()` instead of requiring a click event.</span></span> <span data-ttu-id="a2b7b-165">此功能可用于编写测试，并提供一种替代方法，用于在编辑器中放置对象，而无需使用 MRTK 输入系统。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-165">This capability is useful for writing tests and provides an alternative method to place an object in editor without using the MRTK Input System.</span></span>

1. <span data-ttu-id="a2b7b-166">创建空游戏对象</span><span class="sxs-lookup"><span data-stu-id="a2b7b-166">Create an empty game object</span></span>
1. <span data-ttu-id="a2b7b-167">创建以下示例脚本并将其附加到空游戏对象</span><span class="sxs-lookup"><span data-stu-id="a2b7b-167">Create and attach the following example script to the empty game object</span></span>

    ```c#
    using UnityEngine;
    using Microsoft.MixedReality.Toolkit.Utilities.Solvers;

    public class TapToPlaceInputExample : MonoBehaviour
    {
        private GameObject cube;
        private TapToPlace tapToPlace;

        void Start()
        {
            cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
            cube.transform.localScale = Vector3.one * 0.2f;
            cube.transform.position = Vector3.forward * 0.7f;

            tapToPlace = cube.AddComponent<TapToPlace>();
        }

        void Update()
        {
            if (Input.GetKeyDown(KeyCode.U))
            {
                tapToPlace.StartPlacement();
            }
            if (Input.GetKeyDown(KeyCode.I))
            {
                tapToPlace.StopPlacement();
            }
        }
    }
    ```

1. <span data-ttu-id="a2b7b-168">在播放模式下，按 U 键开始放置立方体</span><span class="sxs-lookup"><span data-stu-id="a2b7b-168">In play mode, press the *U key* to start placing the cube</span></span>
1. <span data-ttu-id="a2b7b-169">按 I 键停止放置</span><span class="sxs-lookup"><span data-stu-id="a2b7b-169">Press the *I key* to stop the placement</span></span>

## <a name="tap-to-place-example-scene"></a><span data-ttu-id="a2b7b-170">点击以放置示例场景</span><span class="sxs-lookup"><span data-stu-id="a2b7b-170">Tap to Place Example Scene</span></span>

<span data-ttu-id="a2b7b-171">点击以放置示例场景包含 4 个可放置对象，每个对象具有不同的配置。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-171">The Tap to Place example scene consists of 4 placeable objects, each with a different configuration.</span></span> <span data-ttu-id="a2b7b-172">该示例场景包含墙壁，用于显示在层次结构中默认禁用的表面放置行为。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-172">The example scene contains walls to show the surface placement behavior that are disabled by default in the hierarchy.</span></span> <span data-ttu-id="a2b7b-173">该示例场景可以在[发布页面](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)上的 Microsoft.MixedReality.Toolkit.Unity.Examples Unity 包中找到。</span><span class="sxs-lookup"><span data-stu-id="a2b7b-173">The example scene can be found in the Microsoft.MixedReality.Toolkit.Unity.Examples unity package found on the [Release Page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="a2b7b-174">场景位置是：*MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*</span><span class="sxs-lookup"><span data-stu-id="a2b7b-174">The scene location is: *MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*</span></span>

![点击以放置示例](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a><span data-ttu-id="a2b7b-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2b7b-176">See also</span></span>

- [<span data-ttu-id="a2b7b-177">求解器</span><span class="sxs-lookup"><span data-stu-id="a2b7b-177">Solvers</span></span>](solver.md)
- [<span data-ttu-id="a2b7b-178">空间感知</span><span class="sxs-lookup"><span data-stu-id="a2b7b-178">Spatial Awareness</span></span>](../../spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="a2b7b-179">输入模拟</span><span class="sxs-lookup"><span data-stu-id="a2b7b-179">Input Simulation</span></span>](../../input-simulation/input-simulation-service.md)
- [<span data-ttu-id="a2b7b-180">手部跟踪</span><span class="sxs-lookup"><span data-stu-id="a2b7b-180">Hand Tracking</span></span>](../../input/hand-tracking.md)
- [<span data-ttu-id="a2b7b-181">凝视</span><span class="sxs-lookup"><span data-stu-id="a2b7b-181">Gaze</span></span>](../../input/gaze.md)
