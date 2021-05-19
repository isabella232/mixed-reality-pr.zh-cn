---
title: MRTK 标准着色器
description: MRTKStandardShader 的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 材料着色器
ms.openlocfilehash: 8b570ebb023305cecbeca16b32832417a3f57cce
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145109"
---
# <a name="mrtk-standard-shader"></a>MRTK 标准着色器

![标准着色器示例](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

MRTK 标准着色系统利用单个灵活的着色器，该着色器可以实现类似于 Unity 标准着色器、实现 [Fluent Design System](https://www.microsoft.com/design/fluent/) 原则的视觉对象，并可在混合现实设备上保持性能。

## <a name="example-scenes"></a>示例场景

可以在 下的 **MaterialGallery** 场景中找到着色器材料示例 `MRTK/Examples/Demos/StandardShader/Scenes/` 。 此场景中的所有材料都使用 MRTK/标准着色器。

![材料库](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

可以在 下的 **StandardMaterialComparison** 场景中找到比较场景，以针对 Unity/标准着色器示例比较和测试 MRTK/Standard 着色器 `MRTK/Examples/Demos/StandardShader/Scenes/` 。

![材料比较](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>体系结构

MRTK/标准着色系统是一种"uber 着色器"，它使用 Unity 的着色器程序 [变体](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) 功能基于材料属性自动生成最佳着色器代码。 当用户在材料检查器中选择材料属性时，他们只会对已启用的功能产生性能成本。

## <a name="material-inspector"></a>材料检查器

对于名为 的 MRTK/标准着色器，存在自定义材料检查器 [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) 。 检查器根据用户选择自动启用/禁用着色器功能，并有助于设置呈现状态。 有关每项功能的信息，请将鼠标悬停在 Unity 编辑器中每个属性 **上，获取工具提示。**

![材料检查器](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

检查器的第一部分控制材料的呈现状态。 *呈现模式* 确定何时以及如何呈现材料。 MRTK/标准着色器的目标是镜像 [Unity/标准](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)着色器 中的呈现模式。 MRTK/标准着色器还包括加法呈现模式和 *自定义呈现模式*，用于完成用户控制。

| 呈现模式 |         说明                                                       |
|----------------|---------------------------------------------------------------------------|
| 半透明         |  (默认) 适用于没有透明区域的普通实体对象。    |
| 剪影         | 允许创建在不透明和透明区域之间具有硬边缘的透明效果。 在此模式下，没有半透明区域，纹理为100% 不透明或不可见。 当使用透明度创建材料形状（如 vegetation）时，这非常有用。 |
| 淡化           | 允许透明度值完全淡化对象，包括任何镜面高光或反射。 如果要使对象的动画淡入或淡出，此模式非常有用。它不适合呈现清晰的透明材料（如清晰的塑料或玻璃），因为反射和高光还会淡出。 |
| 透明    | 适用于渲染真实的透明材料，如清晰的塑料或玻璃。 在此模式下，材料本身将根据纹理的 alpha 通道和颜色颜色) 的 alpha (来使用透明度值。 但是，反射和照明突出显示内容将在完全清晰的情况下保持可见，就像实际透明材料一样。 |
| 加法       | 启用一种加法混合模式，该模式将以前的像素颜色与当前像素颜色进行求和。 这是用于避免透明度排序问题的首选透明模式。     |
| 自定义         | 允许手动控制呈现模式的每个方面。 仅适用于高级用途。   |

![呈现模式](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| 精选模式 |             说明                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 关       | 禁用面部剔除。 如果需要双面网格，则只能将剔除设置为 Off。                                                                                        |
| Front     | 启用正面剔除。                                                                                                                                                        |
| 返回      |  (默认) 启用 [后退人脸剔除](https://en.wikipedia.org/wiki/Back-face_culling)。 应尽可能经常启用背面剔除以提高呈现性能。 |

## <a name="performance"></a>性能

在 Unity 标准着色器上使用 MRTK 标准着色器的主要优势之一是性能。 MRTK 标准着色器可扩展，仅利用启用的功能。 但是，还编写 MRTK 标准着色器，以提供与 Unity 标准着色器相当的美观效果，但成本要低得多。 比较着色器性能的一种简单方法是通过需要在 GPU 上执行的操作数。 当然，计算量可能会因启用的功能和其他呈现配置而波动。 但一般情况下，MRTK 标准着色器执行的计算比 Unity 标准着色器要少得多。

Unity 标准着色器统计信息示例

![Unity 标准着色器统计信息](../images/performance/UnityStandardShader-Stats.PNG)

MRTK 标准着色器统计信息示例

![MRTK 标准着色器统计信息](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> 可以通过在 Unity 检查器中选择和查看 [](https://docs.unity3d.com/Manual/class-Shader.html)着色器资产，然后单击"编译和显示代码"按钮来 *生成* 这些结果。

## <a name="lighting"></a>照明

MRTK/Standard 对照明使用简单的近似值。 由于此着色器不会计算物理正确性和能量消耗，因此它可以快速高效地呈现。 Blinn-Phong是主要照明技术，与 Fresnel 和基于图像的照明混合，以近似基于物理的照明。 着色器支持以下照明技术：

### <a name="directional-light"></a>定向光

如果启用，着色器将遵守场景中第一个 Unity 方向光的方向、颜色和 (强度) 。 动态点光、点光或其他任何 Unity 光不会在实时照明中考虑。

### <a name="spherical-harmonics"></a>球状球状

着色器使用 [球状谐波](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html)（如果已启用），将使用光源探测来估算场景中的灯。 球形谐波计算按顶点执行以降低计算成本。

### <a name="lightmapping"></a>Lightmapping

对于静态照明，着色器将遵循由 Unity 的 [Lightmapping 系统](https://docs.unity3d.com/Manual/Lightmapping.html)生成的 lightmaps。 只需将呈现器标记为 static (或 lightmap static) 才能使用 lightmaps。

### <a name="hover-light"></a>悬停灯光

* 请参阅 [悬停灯光](hover-light.md)

### <a name="proximity-light"></a>邻近感应

* 查看 [邻近感应](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>轻型可编写脚本呈现管道支持

MRTK 包含一个升级路径，使开发人员能够使用 MRTK 着色器 (LWRP) 使用 Unity 的轻型可编写脚本呈现管道。 在 Unity 2019.1.1 f1 和轻型 RP 5.7.2 包中进行了测试。 有关 LWRP 入门的说明，请参阅 [此页](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)。

若要执行 MRTK 升级，请选择： **混合现实工具包-> 实用程序-> UPGRADE MRTK Standard 着色器**

![lwrp 升级](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

升级完成后，MRTK/Standard 着色器将被更改，并且任何洋红色 (着色器错误) 材料应修复。 若要验证升级是否成功，请查看：**升级资产/MixedRealityToolkit/StandardAssets/着色器/MixedRealityStandard 用于轻量渲染管道** 的控制台。

## <a name="ugui-support"></a>UGUI 支持

MRTK 标准着色系统与 Unity 内置的 [UI 系统](https://docs.unity3d.com/Manual/UISystem.html)一起工作。 在 Unity UI 组件上，unity_ObjectToWorld 矩阵不是图形组件所在的本地转换的转换矩阵，而是它的父画布的转换矩阵。 许多 MRTK/标准着色器效果都需要了解对象规模。 若要解决此问题， 将在 UI 网格构造期间将缩放信息存储 [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) 到 UV 通道属性中。

请注意，使用 Unity 图像组件时，建议为源图像指定"无 (子画面) "，以防止 Unity UI 生成额外的顶点。

当需要时，MRTK 中的画布将提示添加 [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) ：

![缩放网格效果](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>纹理合并器

若要提高与 Unity Standard 着色器每像素金属的奇偶校验，可通过通道封装 控制平滑度、半透明性和遮 [挡性值](http://wiki.polycount.com/wiki/ChannelPacking)。 例如：

![通道映射示例](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

使用通道打包时，只需对一个纹理采样并加载到内存中，而不是四个单独的纹理。 在 Program 或 Photoshop 等程序中编写纹理贴图时，可以手动打包它们，如下所示：

| 通道 | 属性             |
|---------|----------------------|
| Red     | 金属             |
| 绿色   | 封闭            |
| 蓝色    | 灰 (辐射)  |
| Alpha   | 平滑           |

或者，可以使用 MRTK 纹理合并器工具。 若要打开该工具，请选择：混合现实工具包 **-> 实用工具 ->纹理** 合并器，这将打开以下窗口：

![纹理合并器示例](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

可以通过选择 Unity 标准着色器并单击"从标准材料自动填充"来自动填充此窗口。 或者，可以为每个红色、 (、蓝色) alpha 通道手动指定纹理值或常数值。 纹理组合是 GPU 加速的，不需要输入纹理可供 CPU 访问。

## <a name="additional-feature-documentation"></a>其他功能文档

下面是 MRTK/Standard 着色器提供的一些功能详细信息的额外详细信息。

### <a name="primitive-clipping"></a>基元剪辑

![基元剪辑](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* 请参阅 [剪辑基元](clipping-primitive.md)

### <a name="mesh-outlines"></a>网格轮廓

许多网格大纲技术均使用 [post 处理](https://docs.unity3d.com/Manual/PostProcessingOverview.html) 技术完成。 Post 处理提供了很好的大纲，但在许多混合现实设备上可能会占用大量资源。 可以在下的  **OutlineExamples** 场景中找到演示网格轮廓用法的场景 `MRTK/Examples/Demos/StandardShader/Scenes/` 。

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) 和 [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) 可用于呈现围绕网格呈现器的轮廓。 启用此组件会引入所述对象的其他呈现处理过程，但设计用于在移动混合现实设备上运行之前，而不使用任何 post 过程。 这种效果的限制包括它不能很好地处理不是 (watertight 的对象，也不需要是两面) 并且在重叠对象上可能会出现深度排序问题。

大纲行为设计为与 MRTK/Standard 着色器结合使用。 大纲材料通常是一种可靠的 unlit 颜色，但可以配置为实现范围很大的效果。 大纲材料的默认配置如下所示：

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. 深度写入-应禁用轮廓材料，以确保轮廓不会阻止其他对象呈现。
2. 顶点延伸-需要启用才能呈现轮廓。
3. 使用平滑法线-对于某些网格，此设置是可选的。 在沿顶点法线移动顶点时进行延伸，某些网格沿默认的法线凸出会导致中断。 若要修复这些中断，可以选中此框，以使用由生成的另一组平滑法 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 是一个组件，可用于在网格上自动生成平滑的法线。 此方法对共享空间中相同位置的网格中的顶点进行分组，然后计算这些顶点的法线平均值。 此过程会创建基础网格的副本，应仅在需要时使用。

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. 通过 生成的平滑法线 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 。
2. 使用的默认法线，请注意围绕立方体角的项目。

### <a name="stencil-testing"></a>模具测试

内置可配置模具测试支持，以实现各种效果。 例如门户：

![模具测试](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>实例颜色支持

实例颜色支持，为数千个 GPU 实例网格提供唯一的材料属性：

![实例属性](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>行程映射

三边形映射是一种以编程方式对网格进行纹理处理的技术。 通常用于地形、没有 UV 的网格或难以解包形状。 此实现支持世界或本地空间投影、混合平滑度规范以及普通地图支持。 请注意，使用的每个纹理都需要 3 个纹理样本，因此在性能关键的情况下请谨慎使用。

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>顶点外泄

世界空间中的顶点外泄。 用于可视化外向边界卷或内/出网格的转换。

![普通地图比例1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>杂项

用于控制 albedo 优化的复选框。 当未指定 albedo 纹理时，将禁用优化 albedo 操作。 这对于控制 [远程纹理加载](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)很有用。

只需选中此框：

![albedo 分配](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

每个像素剪辑纹理、基于本地边缘的抗锯齿和普通地图缩放都受支持。

![普通地图比例2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>另请参阅

* [可交互](../ux-building-blocks/interactable.md)
* [悬停灯光](hover-light.md)
* [邻近感应灯](proximity-light.md)
* [剪辑基元](clipping-primitive.md)
