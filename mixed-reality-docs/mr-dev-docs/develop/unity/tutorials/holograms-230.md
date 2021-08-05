---
title: HoloLens（第一代）空间 230 - 空间映射
description: 按照此编码演练使用 Unity、Visual Studio和HoloLens了解空间映射概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit， mixedrealitytoolkit， mixedrealitytoolkit-unity， academy， 教程， 空间映射， 表面重建， 网格， HoloLens， 混合现实学院， unity， 混合现实头戴显示设备， windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， Windows 10
ms.openlocfilehash: 6806fd8c717d47ff4ea5340e6a2d70ba2c798960af8fe3103daa11d0a8e2bf74
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208707"
---
# <a name="hololens-1st-gen-spatial-230-spatial-mapping"></a>HoloLens (空间 230) 第一代：空间映射

>[!IMPORTANT]
>混合现实学院教程的设计HoloLens (第一代) Unity 2017 和混合现实沉浸式头戴显示设备。  因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。 这些教程 **_不会使用_** 最新工具集或交互进行更新HoloLens 2并且可能与较新版本的 Unity 不兼容。  我们将维护这些教程，使之持续适用于支持的设备。 已经为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。

[空间映射](../../../design/spatial-mapping.md) 通过教授有关环境的全息影像，将现实世界和虚拟世界结合在一起。 在 MR 空间 230 (Project地球) 中，我们将了解如何：

* 扫描环境，将数据从HoloLens计算机传输。
* 浏览着色器并了解如何使用它们来可视化空间。
* 使用网格处理将房间网格分解为简单的平面。
* 除了我们在 [MR 基础知识 101](../../../develop/unity/tutorials/holograms-101.md)中学到的放置技术之外，还可以提供有关全息影像可在环境中放置的位置的反馈。
* 探索遮挡效果，因此当全息影像位于真实对象后面时，仍可以使用 X 射线视觉来查看它！

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 空间 230：空间映射</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>准备工作

### <a name="prerequisites"></a>必备条件

* 配置Windows 10正确工具的[一台电脑](../../../develop/install-the-tools.md)。
* 一些基本的 C# 编程功能。
* 你应已完成[MR 基础知识 101。](../../../develop/unity/tutorials/holograms-101.md)
* 配置为HoloLens[的设备](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载 [项目](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) 所需的文件。 需要 Unity 2017.2 或更高版本。
  * 如果仍然需要 Unity 5.6 支持，请使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)。
  * 如果仍然需要 Unity 5.5 支持，请使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)。
  * 如果仍然需要 Unity 5.4 支持，请使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)。
* 将文件取消存档到桌面或其他易于访问的位置。

>[!NOTE]
>如果要在下载之前查看源代码，可在[GitHub。](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)

### <a name="notes"></a>备注

* Visual Studio中的"启用仅我的代码"需要在"工具">选项">调试"下 (未选中") "以命中代码中的断点。

## <a name="unity-setup"></a>Unity 设置

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* 启动 **Unity**。
* 选择 **"新建** "以创建新项目。
* 将项目名称 **为"Planetarium"。**
* 验证是否 **选择了 3D** 设置。
* 单击“创建项目”。
* Unity 启动后，转到"**编辑> Project 设置 >播放器"。**
* 在"**检查器**"面板中，找到并选择绿色 **"Windows"** 图标。
* 展开 **"其他设置"。**
* 在" **渲染"** 部分中，选中" **支持虚拟现实"** 选项。
* 验证 **Windows全息** 版显示在 **虚拟现实 SDK 列表中**。 如果没有，请选择列表底部的按钮，然后选择"Windows **+** **全息"。**
* 展开 **"发布设置"。**
* 在 **"功能"** 部分中，检查以下设置：
    * InternetClientServer
    * PrivateNetworkClientServer
    * 麦克风
    * SpatialPerception
* 转到"**编辑> Project 设置 >质量"**
* 在"**检查器**"面板的"Windows"图标下，选择"默认"行下的黑色下拉箭头，将默认设置更改为"**非常低"。**
* 转到"**资产>导入包>自定义包 "。**
* 导航到 **...\HolographicHoldemy-全息影像-230-SpatialMapping\Starting** 文件夹。
* 单击 **"Planetarium.unitypackage"。**
* 单击“打开”。
* " **导入 Unity 包"** 窗口应显示，单击"导入 **"** 按钮。
* 等待 Unity 导入完成此项目所需的所有资产。
* 在" **层次结构"面板** 中，删除 **主相机**。
* 在Project **面板****"HoloToolkit-SpatialMapping-230\Utilities\Prefabs"** 文件夹中，找到 **Main Camera** 对象。
* 将主相机 **预制块** 拖放到"层次结构 **"面板** 中。
* 在" **层次结构"面板** 中，删除 **"方向光"** 对象。
* 在 **"Project** 面板中 **，全息影像** 文件夹，找到 **Cursor** 对象。
* 将&将 **光标** 预制项拖放到 **"层次结构"中**。
* 在" **层次结构"面板** 中，选择 **"游标"** 对象。
* 在"**检查器**"面板中 **，单击"** 层"下拉列表，然后选择"**编辑层..."。**
* 将 **用户第 31 层** 名称为 **"SpatialMapping"。**
* 保存新场景： **文件>另存为...**
* 单击 **"新建文件夹**"，将文件夹命名"**场景"。**
* 将文件命名 **"Planetarium"，** 并将其保存在 **"场景"** 文件夹中。

## <a name="chapter-1---scanning"></a>第 1 章 - 扫描

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**目标**

* 了解 SurfaceObserver 及其设置如何影响体验和性能。
* 创建房间扫描体验以收集房间的网格。

**说明**

* 在 **"Project** **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs"** 文件夹中，找到 **SpatialMapping** 预制。
* 将& **将 SpatialMapping** 预制块拖放到 **"层次结构"面板** 中。

**生成和部署 (第 1 部分)**

* 在 Unity 中，选择"**文件>生成设置"。**
* 单击 **"添加打开** 的场景"， **将地球** 台场景添加到生成中。
* 在 **"平台Windows****选择"通用** 平台"，然后单击"**切换平台"。**
* 将 **SDK** 设置为 **通用 10，** 将 **UWP 生成类型设置为** **D3D**。
* 检查 **Unity C# 项目**。
* 单击“生成”。
* 创建名为 **"App"** 的新文件夹。
* 单击"应用 **"** 文件夹。
* 按" **选择文件夹"** 按钮。
* Unity 完成生成后，将显示文件资源管理器窗口。
* 双击"应用 **"** 文件夹以打开它。
* 双击 **"Planetarium.sln"，** 将项目加载到Visual Studio。
* 在Visual Studio，使用顶部工具栏将"配置"更改为"发布 **"。**
* 将"平台"更改为 **"x86"。**
* 单击"本地计算机"右边的下拉箭头，然后选择"**远程计算机"。**
* 在 ["地址"字段中输入设备的 IP](/hololens/hololens-network#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) 地址，将"身份验证模式"更改为"通用 (未 **加密协议) "**。
* 单击 " **调试-> 启动但不调试** " 或按 **Ctrl + F5**。
* 查看 "**输出**" 面板中的 "生成" 和 "部署" 状态 Visual Studio。
* 在应用程序部署完成后，请四处浏览聊天室。 你将看到由黑色和白色线框网格覆盖的周围面。
* 扫描您的环境。 务必查看墙壁、上限和楼层。

**生成并部署 (第2部分)**

现在，让我们了解空间映射如何影响性能。

* 在 Unity 中，选择 " **Window > Profiler**"。
* 单击 " **添加探查器 > GPU**"。
* 单击 "**活动探查 <Enter IP> 器 >**。
* 输入 HoloLens 的 **IP 地址**。
* 单击“连接”  。
* 观察 GPU 呈现帧所花的时间（以毫秒为单位）。
* 阻止应用程序在设备上运行。
* 返回到 Visual Studio 并打开 **SpatialMappingObserver**。 你将在 Assembly-CSharp (通用 Windows) 项目的 "HoloToolkit\SpatialMapping" 文件夹中找到它。
* 查找 **唤醒的 ()** 函数，并添加以下代码行： **TrianglesPerCubicMeter = 1200;**
* 将项目重新部署到你的设备，然后 **重新连接探查器**。 观察帧的呈现时间（毫秒）。
* 阻止应用程序在设备上运行。

**在 Unity 中保存和加载**

最后，让我们保存房间网格，并将其加载到 Unity。

* 返回 Visual Studio，并删除在上一节中在 **唤醒 ()** 函数中添加的 **TrianglesPerCubicMeter** 行。
* 将项目重新部署到你的设备。 现在，我们应该运行每个立方米的 **500** 三角形。
* 打开浏览器并输入 HoloLens IPAddress 以导航到 **Windows 设备门户**。
* 在左侧面板中选择 " **3D 视图** " 选项。
* 在 " **表面重建** " 下，选择 " **更新** " 按钮。
* 请注意，在 "显示" 窗口中显示 HoloLens 上所扫描的区域。
* 若要保存房间扫描，请按 " **保存** " 按钮。
* 打开 " **下载** " 文件夹，查找保存的会议室模型 **SRMesh**。
* 将 **SRMesh** 复制到 Unity 项目的 " **资产** " 文件夹。
* 在 Unity 中，在 "**层次结构**" 面板中选择 " **SpatialMapping** " 对象。
* **(脚本) 组件定位对象图面观察** 程序。
* 单击 " **房间模型** " 属性右侧的圆圈。
* 找到并选择 " **SRMesh** " 对象，然后关闭窗口。
* 验证 **检查器** 面板中的 "**房间模型**" 属性现在是否设置为 " **SRMesh**"。
* 按 " **播放** " 按钮进入 Unity 的预览模式。
* SpatialMapping 组件将从保存的房间模型加载网格，以便可以在 Unity 中使用它们。
* 切换到 **场景** 视图，查看以线框着色器显示的所有房间模型。
* 再次按 " **播放** " 按钮以退出预览模式。

**注意：** 下次在 Unity 中进入预览模式时，它会默认加载已保存的会议室网格。

## <a name="chapter-2---visualization"></a>第2章-可视化

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**目标**

* 了解着色器的基本知识。
* 可视化你的环境。

**说明**

* 在 Unity 的 " **层次结构** " 面板中，选择 " **SpatialMapping** " 对象。
* 在 " **检查器** " 面板中，找到 **(脚本) 组件的空间映射管理器** 。
* 单击 " **表面材料** " 属性右侧的圆圈。
* 找到并选择 **BlueLinesOnWalls** 材料并关闭窗口。
* 在 " **Project** 面板 **着色** 器" 文件夹中，双击 " **BlueLinesOnWalls** " 以打开 Visual Studio 中的着色器。
* 这是一个简单的像素 (顶点到片段) 着色器，用于完成以下任务：
    1. 将顶点的位置转换为世界空间。
    2. 检查顶点的法线，确定像素是否为垂直。
    3. 设置要呈现的像素的颜色。

**生成和部署**

* 返回到 Unity，按 " **播放** " 进入预览模式。
* 将在房间网格的所有垂直表面上呈现蓝线 (这会从已保存的扫描数据) 自动加载。
* 切换到 " **场景** " 选项卡以调整房间的视图，并查看整个房间网格在 Unity 中的显示方式。
* 在 **Project** 面板中，找到 "**材料**" 文件夹，并选择 **BlueLinesOnWalls** 材料。
* 修改某些属性，并查看更改在 Unity 编辑器中的显示方式。
    * 在 " **检查器** " 面板中，调整 **LineScale** 值，使线条显得更粗或更细。
    * 在 " **检查器** " 面板中，调整 **LinesPerMeter** 值以更改每个墙壁上显示的行数。
* 再次单击 " **播放** " 退出预览模式。
* 生成并部署到 HoloLens，并观察着色器呈现在真实表面上的显示方式。

Unity 非常适合用于预览材料，但在设备中签出渲染始终是一个好主意。

## <a name="chapter-3---processing"></a>第3章-处理

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**目标**

* 了解用于处理空间映射数据以在应用程序中使用的方法。
* 分析空间映射数据以查找平面并删除三角形。
* 使用平面放置全息图。

**说明**

* 在 Unity 的 **Project** 面板中，**全息影像**"文件夹中，找到" **SpatialProcessing** "对象。
* 拖动 & 将 **SpatialProcessing** 对象放入 **层次结构** 面板。

SpatialProcessing prefab 包含用于处理空间映射数据的组件。 **SurfaceMeshesToPlanes** 将根据空间映射数据查找并生成平面。 我们将在应用程序中使用平面来表示墙壁、地面和上限。 此 prefab 还包含 **RemoveSurfaceVertices** ，可从空间映射网格中删除顶点。 这可用于在网格中创建孔洞，或删除不再需要的多余三角形 (因为可以改为使用飞机) 。

* 在 Unity 的 **Project** 面板中，**全息影像**"文件夹中，找到" **SpaceCollection** "对象。
* 将 **SpaceCollection** 对象拖放到 **层次结构** 面板。
* 在 " **层次结构** " 面板中，选择 " **SpatialProcessing** " 对象。
* 在 " **检查器** " 面板中，找到 " **播放空间管理器" (脚本)** 组件。
* 双击 " **PlaySpaceManager** " 以 Visual Studio 中打开它。

PlaySpaceManager 包含应用程序特定的代码。 我们将向此脚本添加功能，以实现以下行为：

1. 超过扫描时间限制时停止收集空间映射数据 (10 秒) 。
2. 处理空间映射数据：
    1. 使用 SurfaceMeshesToPlanes 可以创建一个更简单的世界表示，作为 (墙壁、地面、上限等) 的平面。
    2. 使用 RemoveSurfaceVertices 可删除位于平面边界内的曲面三角形。
3. 在世界各地生成全息影像的集合，并将其放在靠近用户的墙壁和地面平面上。

完成标记为 PlaySpaceManager 的编码练习，或将脚本替换为下面的已完成解决方案：

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**生成和部署**

* 在部署到 HoloLens 之前，请按 Unity 中的 "**播放**" 按钮进入播放模式。
* 从文件加载房间网格后，请等待10秒，然后再开始处理空间映射网格。
* 处理完成后，平面将显示为表示地面、墙壁、天花板等。
* 找到所有平面后，应会看到一个阳历系统出现在摄像机附近的地面表上。
* 照相机附近的墙壁上还应显示两个海报。 如果在"游戏 **"** 模式下看不到它们，请切换到"场景 **"** 选项卡。
* 再次按 **"播放** "按钮退出播放模式。
* 像往常一样生成HoloLens部署到应用程序。
* 等待空间映射数据的扫描和处理完成。
* 看到飞机后，尝试在你的世界找到太阳能系统和海报。

## <a name="chapter-4---placement"></a>第 4 章 - 放置

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**目标**

* 确定全息影像是否适合表面。
* 当全息影像可以/无法适应表面时，为用户提供反馈。

**说明**

* 在 Unity 的" **层次结构"面板** 中，选择 **SpatialProcessing** 对象。
* 在" **检查器** "面板中，找到"平面的 **图面网格 (脚本)** 组件。
* 将" **绘制平面"** 属性更改为 **"无** "以清除选择。
* 将" **绘制平面"** 属性更改为 **"墙**"，以便只呈现墙面。
* 在 **Project"****脚本"** 文件夹中，双击 **Placeable.cs，** 在"脚本"Visual Studio。

可 **放置** 脚本已附加到在平面查找完成后创建的海报和投影框。 我们只需取消注释某些代码，此脚本将实现以下目的：

1. 通过从边界立方体的中心和四个角进行光线广播，确定全息影像是否适合表面。
2. 检查表面法线，确定全息影像是否足够平滑，
3. 在全息影像周围呈现边界立方体，以在放置时显示其实际大小。
4. 在全息影像下/后面投射阴影，以显示其放置于楼层/墙中的位置。
5. 如果无法将全息影像放置在图面上，则将阴影呈现为红色;如果可以，则呈现为绿色。
6. 重新定位全息影像，以与 (或水平) 图面类型对齐。
7. 将全息影像平滑地放在所选图面上，以避免跳转或对齐行为。

取消注释以下编码练习中的所有代码，或在 **Placeable.cs** 中使用此已完成的解决方案：

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The alignToVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**生成和部署**

* 与之前一样，生成项目并部署到HoloLens。
* 等待空间映射数据的扫描和处理完成。
* 看到太阳能系统时，凝视下面的投影框并执行选择手势来移动它。 选择投影框时，边界多维数据集将在投影框周围可见。
* 将头部移动到房间中的不同位置凝视。 投影框应跟随你的凝视。 当投影框下方的阴影变为红色时，无法将全息影像放在该图面上。 当投影框下方的阴影变为绿色时，可以通过执行另一个选择手势来放置全息影像。
* 在墙上查找并选择其中一个全息海报，以将其移动到新位置。 请注意，不能将海报放在楼层或上限上，并且当你四处移动时，它始终正确面向每面墙。

## <a name="chapter-5---occlusion"></a>第 5 章 - 遮挡

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**目标**

* 确定全息影像是否被空间映射网格遮挡。
* 应用不同的遮挡技术来实现有趣的效果。

**说明**

首先，我们将允许空间映射网格遮挡其他全息影像，而不遮挡现实世界：

* 在" **层次结构"面板** 中，选择 **"SpatialProcessing"** 对象。
* 在" **检查器** "面板中，找到" **播放空间管理器 (脚本)** 组件。
* 单击"辅助材料"属性 **右边的** 圆圈。
* 找到并选择 **遮挡材料** 并关闭窗口。

接下来，我们将向地球添加一种特殊行为，以便每当它被另一个全息影像（如 (如) 或空间映射网格遮挡时，它都有蓝色突出显示：

* 在Project **面板** 的 全息影像 **文件夹中，** 展开 **SolarSystem** 对象。
* 单击"**地球"。**
* 在 **"检查器** "面板中，找到地球材料 (底部) 。
* 在"**着色器"下拉列表中**，将着色器更改为"自定义>**遮挡Rim"。** 每当另一个对象遮挡地球时，这都会在地球周围呈现蓝色突出显示。

最后，我们将为太阳系中的行星启用 X 射线视觉效果。 我们需要编辑 Scripts\SolarSystem 文件夹中 (的 **PlanetOcclusion.cs**) 以实现以下目的：

1. 确定地球是否被空间网格和平面 (空间映射层) 。
2. 每当地球被 SpatialMapping 层遮挡时，显示它的线框表示形式。
3. 当地球未被 SpatialMapping 层阻止时，隐藏它的线框表示形式。

按照 PlanetOcclusion.cs 中的编码练习操作，或使用以下解决方案：

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**生成和部署**

* 像往常一样生成HoloLens应用程序。
* 等待空间映射数据的扫描和处理完成， (应看到蓝色线条显示在墙) 。
* 找到并选择太阳能系统的投影框，然后设置墙旁边或计数器后面的框。
* 可以通过隐藏图面隐藏在海报或投影框的对等方来查看基本遮挡。
* 查找地球，每当它在另一个全息影像或表面后面时，都应有蓝色突出显示效果。
* 观察行星在墙后面或房间的其他表面移动。 现在，你已拥有 X 射线视觉，并可以看到其线框框架！

## <a name="the-end"></a>结束

恭喜！ 现已完成 MR 空间 **230：空间映射**。

* 你知道如何扫描环境，以及如何将空间映射数据加载到 Unity。
* 你了解着色器的基本信息，以及如何使用材料来重新可视化世界。
* 你学习了用于查找平面和从网格中删除三角形的新处理技术。
* 你能够移动全息影像，将全息影像放在有意义的表面上。
* 你遇到了不同的遮挡技术，并充分利用了 X 射线视觉功能！