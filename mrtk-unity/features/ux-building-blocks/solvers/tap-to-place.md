---
title: 点击以放置
description: TapToPlace MRTK 文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity,HoloLens, HoloLens 2, 混合现实, 开发, MRTK, 点击以放置,
ms.openlocfilehash: 98408312ec2637dc3fa137e7d51cce1f37e816f9a21b703ec9216bf90251661f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198304"
---
# <a name="tap-to-place"></a>点击以放置

![TapToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

“点击以放置”是一个远距离交互组件，用于将游戏对象放置在表面上。 此组件适用于将对象放置在空间网格上。 “点击以放置”使用两个单击和头部运动的组合来放置对象。 一个单击用于开始放置，头部运动用于控制对象的位置，另一个单击用于将对象放置在场景中。

## <a name="using-tap-to-place"></a>使用点击以放置

1. 设置场景
    - 新建全新的 Unity 场景
    - 通过导航到“混合现实工具包” > “添加到场景并配置”，将 MRTK 添加到场景中
    > [!NOTE]
    > 点击以放置使用 MRTK 输入系统驱动的单击，但也可以不使用单击进行控制，请参见下文的“点击以放置代码可配置性”部分。
    - 将立方体添加到场景中，将刻度更改为 0.2，并将位置更改为 (0, 0, 0.7)。
1. 将[点击以放置](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace)附加到具有碰撞器的游戏对象

    ![TapToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - 添加“点击以放置”组件时，还会附加“求解器处理程序”。 “点击以放置”将派生自需要求解器处理程序的[求解器](solver.md)类。 “点击以放置”对象的位置是相对于求解器处理程序中的 `TrackedTargetType` 计算出来的。 默认情况下，头部为 `TrackedTargetType`，即当头部移动时，选择的对象也会跟随移动。  `TrackedTargetType` 还可以设置为控制器射线，该射线会让对象跟随控制器。 点击以放置检查器中的第一组属性是[常见的求解器属性](solver.md#common-solver-properties)。  
    > [!IMPORTANT]
    > 点击以放置独立的求解器，不能与其他求解器链接在一起。 它无法链接的原因是，在放置对象时，会使用 SolverHandler.UpdateSolvers 更新对象位置。
    - 点击以放置属性：
        - `Auto Start`：如果为 true，则点击以放置求解器将开始控制要放置的游戏对象的位置。 对象将立即开始跟随 TrackedTargetType（头部或控制器射线）。 该值必须在调用 Start() 之前修改才能生效。
        - `Default Placement Distance`：对象相对于 SolverHandler 中的 TrackedTargetType 放置的默认距离（以米为单位）。 如果表面没有被光线投射击中，则游戏对象放置在默认放置距离。
        - `Max Raycast Distance`：基于“TrackedTargetType”原点的光线投射的最大距离（米）。 此光线投射查找要放置选定对象的表面。
        - `UseDefaultSurfaceNormalOffset`：默认情况下，此属性为 true，它确保所放置的对象在表面上对齐。 如果此属性为 true，则将应用默认的表面法线偏移，而不是为 `SurfaceNormalOffset` 属性指定的任何值。 如果为 false，则将应用 `SurfaceNormalOffset` 的值。 默认的表面法线偏移是沿 z 轴的碰撞区范围。
        - `Surface Normal Offset`：当光线投射击中表面时，要放置的游戏对象的中心与表面法线之间的距离。 仅当 `UseDefaultSurfaceNormalOffset` 为 false 时，此属性才会应用于对象。
        - `Keep Orientation Vertical`：如果为 true，则要放置的游戏对象将保持直立，并与 Vector3.up 平齐。
        - `Rotate According to Surface`：如果为 false，则要放置的游戏对象将不会根据表面击中更改其旋转。  当 IsBeingPlaced 为 true 时，对象将始终面向相机。
        - `Magnetic Surfaces`：要按最高到最低优先级的顺序执行的 LayerMasks 数组。 用于提供光线投射击中的第一层掩码用于位置计算。
        - `Debug Enabled`：如果为 true，并且在 Unity 编辑器中，则将以黄色绘制光线投射的法线。 如果 `RotateAccordingToSurface` 为 true，则启用调试非常有用，因为它会绘制表面击中的法线，这会直观地说明对象处于当前方向的原因。
        - `On Placing Started`：选择了要放置的游戏对象时，触发此事件一次。
        - `On Placing Stopped`：未选择要放置的游戏对象时，触发此事件一次。

1. 在编辑器中测试“点击以放置”行为
    - 按“播放”并按住空格键以显示输入模拟手。
    - 移动手直到立方体获得焦点，并通过单击鼠标左键，模拟使用输入模拟手进行单击。
        - 如果场景中不存在碰撞器，则对象将按照定义的 `Default Placement Distance` 跟随 `TrackedTargetType`。
    - 对象在被选中后跟随 `TrackedTargetType` 的运动。 若要在编辑器中模拟头部运动，请按 WASD 键。 单击并按住鼠标右键，改变头部旋转。
    - 若要停止放置对象，请再次单击。  对于停止放置单击，对象无需获得焦点。 只有在初次单击来启动放置过程时，才需要获得焦点。

    `TrackedTargetType`：头部（默认值） |  `TrackedTargetType`：控制器射线
    :-------------------------:|:-------------------------:
    ![点击以放置输入模拟头部控制射线](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![点击以放置输入模拟控制器射线 2](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>点击以放置代码可配置性

点击以放置对象选择时间还可以通过 `StartPlacement()` 和 `StopPlacement()` 来控制，而不需要单击事件。 此功能可用于编写测试，并提供一种替代方法，用于在编辑器中放置对象，而无需使用 MRTK 输入系统。

1. 创建空游戏对象
1. 创建以下示例脚本并将其附加到空游戏对象

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

1. 在播放模式下，按 U 键开始放置立方体
1. 按 I 键停止放置

## <a name="tap-to-place-example-scene"></a>点击以放置示例场景

点击以放置示例场景包含 4 个可放置对象，每个对象具有不同的配置。 该示例场景包含墙壁，用于显示在层次结构中默认禁用的表面放置行为。 该示例场景可以在[发布页面](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)上的 Microsoft.MixedReality.Toolkit.Unity.Examples Unity 包中找到。 场景位置是：*MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*

![点击以放置示例](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>另请参阅

- [求解器](solver.md)
- [空间感知](../../spatial-awareness/spatial-awareness-getting-started.md)
- [输入模拟](../../input-simulation/input-simulation-service.md)
- [手部跟踪](../../input/hand-tracking.md)
- [凝视](../../input/gaze.md)
