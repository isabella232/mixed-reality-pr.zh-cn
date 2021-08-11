---
title: 创建在主页中使用的 3D 模型
description: 在 HoloLens 和沉浸式 (VR) 耳机上，要在 Windows Mixed Reality 主页中使用的三维模型的资产要求和创作指南。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D，建模，建模指南，资产需求，创作准则，启动器，3D 启动器，纹理，材料，复杂性，三角形，网格，多边形，polycount，限制，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 9fdd485c67a757d40b049c08f114ce9982aafc27e9103c4b31c21fd8af08d186
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207677"
---
# <a name="create-3d-models-for-use-in-the-home"></a>创建在主页中使用的 3D 模型

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md)是用户在启动应用程序之前居住的起点。 为 Windows Mixed Reality 耳机设计应用程序时，使用[3d 模型作为应用启动器](implementing-3d-app-launchers.md)，并将[3d 深层链接放入 Windows Mixed Reality home](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)。 本文概述了用于创建与 Windows Mixed Reality home 兼容的3d 模型的准则。

## <a name="asset-requirements-overview"></a>资产要求概述

为 Windows Mixed Reality 创建3d 模型时，所有资产都必须满足以下要求： 
1. [导出](#exporting-models) -资产必须以 glb 文件格式提供， (二进制 glTF) 
2. [建模](#modeling-guidelines) -资产必须小于10000个三角形，每个 LOD 不超过64个节点和 32 submeshes
3. [材料](#material-guidelines) -纹理不能大于 4096 x 4096，并且最小 mip 映射在任一维度上都不应大于4
4. [动画](#animation-guidelines) -动画的长度不能超过20分钟 (36000 个关键帧) 并且必须包含 <= 8192 变形目标顶点
5. [优化](#optimizations) -资产应使用 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)进行优化。 *Windows 操作系统版本上需要 <= 1709** 并建议在 Windows os 版本 >= 1803

本文的其余部分详细介绍了这些要求和额外指导原则，以确保你的模型与 Windows Mixed Reality home 良好合作。 

## <a name="detailed-guidance"></a>详细指南

### <a name="exporting-models"></a>导出模型

Windows Mixed Reality home 需要使用带有嵌入图像和二进制数据的 glb 文件格式传递3d 资产。 Glb 是 glTF 格式的二进制版本，它是 Khronos 组维护的用于3D 资产交付的版税免费开放标准。 随着 glTF 发展为可互操作的3d 内容行业标准，Microsoft 将在 Windows 应用和体验中提供格式支持。 如果尚未创建 glTF 资产，你可以在 glTF 工作组 github 页上找到 [受支持的导出程序和转换器的列表](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) 。  

### <a name="modeling-guidelines"></a>建模准则

Windows 要求使用以下建模准则生成资产，以确保与混合现实主体验兼容。 当你选择的程序中的建模时，请记住以下建议和限制：
1. 向上轴应设置为 "Y"。
2. 资产应正面朝正 Z 轴 "前进"。
3. 所有资产都应在场景原点 (0，0，0) 上构建。
4. 应将工作单元设置为计量和资产，以便能够在全球范围内创作资产
5. 所有网格都不需要组合，但如果目标是资源受限的设备，则建议使用此方法
6. 所有网格应共享一个材料，并且对于整个资产只使用一个纹理集
7. 在0-1 空间中，Uv-11 的布局必须按正方形排列。 如果允许，请避免平铺纹理。
8. 不支持多 Uv-11
9. 不支持双面材料

### <a name="triangle-counts-and-levels-of-detail-lods"></a>三角形计数和详细级别 (LODs) 

Windows Mixed Reality home 不支持超过10000个三角形的模型。 建议在导出前三角化网格，以确保它们不会超过此计数。 WindowsMR 还支持 (LODs) 的可选几何级别详细信息，以确保实现高性能和高质量的体验。 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) 将帮助你将模型的3个版本合并为 glb 模型。 Windows 根据模型占用的屏幕实际空间量来确定要显示的 LOD。 仅支持3个 LOD 级别，并提供以下建议的三角形计数：
<br>

|  LOD 级别  |  推荐的三角形计数  |  最大三角形计数 | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>节点计数和子网格限制

Windows Mixed Reality home 不支持每个 LOD 超过64个节点或 32 submeshes 的模型。 节点是 [glTF 规范](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) 中定义场景中对象的概念。 Submeshes 是在对象的网格上的 [基元](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) 数组中定义的。 

|  功能 |  说明  |  支持的最大值 | 文档 |
|------|------|------|------|
|  Nodes |  GlTF 场景中的对象 |  每 LOD 64 | [这儿](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  所有网格上的基元的总和 |  每 LOD 32 | [这儿](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>材料指导原则

应使用 .PBR 金属粗糙度工作流准备纹理。 首先创建一组完整的纹理，其中包括 Albedo、Normal、封闭、金属和粗糙度。 Windows Mixed Reality 支持分辨率最高为4096x4096 的纹理，但建议你在512x512 中创作。 纹理应以4的倍数以分辨率编写。 这是在下面概述的导出步骤中应用于纹理的压缩格式的要求。 生成 mip maps 或纹理时，最小 mip 必须最大为4x4。
<br>

|  建议的纹理大小  |  最大纹理大小 | 最小 Mip
|----|----|----|
|  512x512  |  4096x4096 | 最大4x4|

### <a name="albedo-base-color-map"></a>Albedo (基准颜色) 地图

没有照明信息的原始颜色。 此地图还包含金属地图中金属 (白色的 reflectance 和漫射信息) 并分别在金属) 地图中 insulator (黑色黑色。

### <a name="normal"></a>普通

相切空间正常映射

### <a name="roughness-map"></a>粗糙度图

描述对象的 microsurface。 白色1.0 的黑色0.0 为平滑。 此地图为资产提供了最多的字符，因为它真正描述了图面。 例如，刮擦、指纹、涂抹、grime 等。

### <a name="ambient-occlusion-map"></a>环境封闭映射

显示封闭像素光线区域的值比例图，用于阻止反射

### <a name="metallic-map"></a>金属图

指示着色器（如果有）。 Raw 金属 = 1.0 白色非金属 = 0.0 黑色。 可能有一些过渡灰度值，这些值指示了诸如灰尘等原材料的内容，但通常情况下，此地图只应为黑色和白色。

## <a name="optimizations"></a>优化

Windows Mixed Reality主页基于使用自定义扩展定义的核心 glTF 规范提供一系列优化。 这些优化要求在 Windows 版本 <= 1709，建议在较新版本的 Windows。 可以使用 GitHub 上提供的 Windows Mixed Reality Asset Converter 轻松优化任何 glTF 2.0 [GitHub。](https://github.com/Microsoft/glTF-Toolkit/releases) 此工具将执行正确的纹理打包和优化，如下所示。 对于常规用法，我们建议使用 WindowsMRAssetConverter，但是，如果需要对体验进行更多控制，并且要生成自己的优化管道，可以参考下面的详细规范。  

> [!NOTE]
> 有关精确模型限制的可能性的最终列表，请参阅 [3D 模型](/dynamics365/mixed-reality/guides/3d-content-guidelines/optimize-models) 优化一文，以在 Dynamics 365 应用程序中使用。

### <a name="materials"></a>材料

为了改善混合现实环境中的资产加载时间Windows MR 支持根据本部分中定义的纹理打包方案呈现压缩的 DDS 纹理。 使用扩展名 引用 DDS [MSFT_texture_dds纹理](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)。 强烈建议压缩纹理。 

#### <a name="hololens"></a>HoloLens

HoloLens混合现实体验要求使用 2 纹理设置通过以下封装规范来打包纹理：
<br>

|  glTF 属性  |  纹理  |  封装方案 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  红色 (R) 、绿色 (G) 、蓝色 (B)  | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  普通 (RG) 、 (B) 、 (A)  | 


压缩 DDS 纹理时，应在每个映射上进行以下压缩：
<br>

|  纹理  |  预期压缩 | 
|------|------|
|  baseColorTexture、normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>沉浸 (VR) 头戴显示设备

基于电脑Windows Mixed Reality沉浸式 VR (头戴显示设备) 希望使用 3 纹理设置通过以下封装规范来打包纹理：

##### <a name="windows-os--1803"></a>WindowsOS >= 1803

<br>

|  glTF 属性  |  纹理  |  封装方案 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  红色 (R) 、绿色 (G) 、蓝色 (B)  | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  遮挡 (R) 、粗糙度 (G) 、 (B)  | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  常规 (RG)  | 

压缩 DDS 纹理时，应在每个映射上进行以下压缩：
<br>

|  纹理  |  预期压缩 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture、occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>WindowsOS <= 1709
<br>

|  glTF 属性  |  纹理  |  封装方案 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  红色 (R) 、绿色 (G) 、蓝色 (B)  | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  粗糙 (R) 、 (G) 、遮挡 (B)  | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  常规 (RG)  | 

压缩 DDS 纹理时，应在每个映射上进行以下压缩：
<br>

|  纹理  |  预期压缩 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture，粗糙度MetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>添加网格 LOD

WindowsMR 使用几何节点 LOD 以不同详细级别呈现 3D 模型，具体取决于屏幕覆盖率。 虽然此功能在技术上不是必需的，但建议用于所有资产。 目前Windows支持 3 个详细级别。 默认 LOD 为 0，表示最高质量。 其他 LOD 按顺序编号，例如 1、2，质量逐渐降低。 资产[Windows Mixed Reality](https://github.com/Microsoft/glTF-Toolkit/releases)通过接受多个 glTF 模型并合并到具有有效 LOD 级别的单个资产，支持生成满足此 LOD 规范的资产。 下表概述了预期的 LOD 排序和三角形目标：
<br>

|  LOD 级别  |  建议的三角形计数  |  最大三角形计数 | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

使用 LOD 时，始终指定 3 个 LOD 级别。 缺少 LOD 会导致模型在 LOD 系统切换到缺少的 LOD 级别时意外呈现。 glTF 2.0 目前不支持将 LOD 作为核心规范的一部分。应该使用扩展 MSFT_LOD [LOD。](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)

### <a name="screen-coverage"></a>屏幕覆盖率

LOD 基于Windows Mixed Reality LOD 上设置的屏幕覆盖率值驱动的系统，在数据中显示。 当前使用较大屏幕空间的对象显示在更高的 LOD 级别。 屏幕覆盖率不是核心 glTF 2.0 规范的一部分，必须使用 MSFT_ScreenCoverage 扩展的"额外"部分中的 [MSFT_lod 指定](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)。
<br>

|  LOD 级别  |  建议的范围  |  默认范围 | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  0.5 | 
|  LOD 1 |  在 50% - 20% 以下  |  0.2 | 
|  LOD 2 |  在 20% - 1% 以下  |  0.01 | 
|  LOD 4  |  在 1% 以下  |  - | 

## <a name="animation-guidelines"></a>动画指南

> [!NOTE]
> 此功能已作为[2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)年 4 Windows 10 更新 的一部分添加。 在较旧版本Windows这些动画不会播放，但如果根据本文中的指导创作，它们仍将加载。  

该混合现实主页在 VR HoloLens头戴显示设备上支持动态 glTF () 对象。 如果要在模型上触发动画，则需要使用 glTF 格式的动画映射扩展。 此扩展使你能够基于用户的存在在 glTF 模型中触发动画，例如，当用户靠近对象或正在查看对象时触发动画。 如果 glTF 对象具有动画，但不定义触发器，则动画不会播放。 以下部分介绍一个工作流，用于将这些触发器添加到任何动画 glTF 对象。

### <a name="tools"></a>工具

首先，下载以下工具（如果尚未安装）。 使用这些工具可以轻松打开任何 glTF 模型、预览模型、进行更改并保存为 glTF 或 .glb：
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [glTF Tools for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>打开和预览模型

首先，将 .glTF 文件拖动到编辑器窗口中，在 VSCode 中打开 glTF 模型。 如果有 .glb 而不是 .glTF 文件，可以使用下载的 glTF 工具加载项将其导入 VSCode。 转到"查看 -> 命令面板"，然后开始在命令面板中键入"glTF"并选择"glTF： Import from glb"，这将弹出一个文件选取器供你导入 .glb。 

打开 glTF 模型后，应在编辑器窗口中看到 JSON。 还可使用 在实时 3D 查看器中预览模型，方法是右键单击文件名，然后从右键单击菜单中选择"glTF：预览 3D 模型"命令快捷方式。 

### <a name="adding-the-triggers"></a>添加触发器

使用动画映射扩展将动画触发器添加到 glTF 模型 JSON。 动画映射扩展在此处公开记录[，GitHub (](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md)注意：这是草稿扩展) 。 若要将扩展添加到模型，只需滚动到编辑器中 glTF 文件的末尾，然后向文件添加"extensionsUsed"和"extensions"块（如果它们不存在）。 在"extensionsUsed"部分中，将添加对"EXT_animation_map"扩展的引用，在"扩展"块中，将映射添加到模型中的动画。

如 [规范中说明，](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) 在"动画"列表（动画索引数组）上定义使用"语义"字符串触发动画的触发内容。 在下面的示例中，我们指定了在用户正在对象上时要播放的动画：

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
主场支持以下动画触发器Windows Mixed Reality语义。  
* "ALWAYS"：不断循环动画
* "HELD"：在抓取对象的整个持续时间内循环。
* "GAZE"：在查看对象时循环
* "PROXIMITY"：在查看器靠近对象时循环
* "POINTING"：用户指向对象时循环

### <a name="saving-and-exporting"></a>保存和导出

对 glTF 模型进行更改后，可以直接将其另存为 glTF。 还可以在编辑器中右键单击文件的名称，然后选择"glTF：导出到 GLB (二进制文件) "以导出 .glb。 

### <a name="restrictions"></a>限制

动画不能超过 20 分钟，在 30 FPS 时不能包含超过 36，000 个关键帧 (20 分钟) 。 此外，使用基于 morph 目标的动画时，不会超过 8192 个变态目标顶点或更少。 超过这些计数将导致动态资产在主Windows Mixed Reality不受支持。 

|功能|最大值|
|-----|-----|
|持续时间|20 分钟|
|关键帧|36,000| 
|Morph Target 顶点|8192|

## <a name="gltf-implementation-notes"></a>glTF 实现说明

WindowsMR 不支持使用负刻度翻转几何图形。 具有负刻度的几何图形可能会导致可视化项目。

glTF 资产必须使用由 MR 呈现的场景属性指向Windows场景。 此外，Windows [2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)年 4 月更新Windows 10 MR glTF 加载程序 **需要** 访问器：
* 必须具有最小值和最大值。
* 类型 SCALAR 必须是 componentType UNSIGNED_SHORT (5123) 或 UNSIGNED_INT (5125) 。
* 类型 VEC2 和 VEC3 必须是 componentType FLOAT (5126) 。

以下材料属性用于核心 glTF 2.0 规范，但不是必需的：
* baseColorFactor、roughFactor、roughnessFactor
* baseColorTexture：必须指向存储在 dds 中的纹理。
* missiveTexture：必须指向存储在 dds 中的纹理。
* emissiveFactor
* alphaMode

核心规范中将忽略以下材料属性：
* 所有多 UV
* metalRoughnessTexture：必须改为使用下面定义的 Microsoft 优化纹理打包
* normalTexture：必须改为使用下面定义的 Microsoft 优化纹理打包
* normalScale
* occlusionTexture：必须改为使用下面定义的 Microsoft 优化纹理打包
* occlusionStrength

WindowsMR 不支持基元模式线和点。 

仅支持单个 UV 顶点属性。

## <a name="more-resources"></a>更多资源

* [glTF 导出器和转换器](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 规范](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD 扩展规范](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC Mixed Reality 纹理打包扩展规范](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens混合现实纹理打包扩展规范](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS 纹理 glTF 扩展规范](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>另请参阅

* [实现 3D 应用启动器（UWP 应用）](implementing-3d-app-launchers.md)
* [实现 3D 应用启动器（Win32 应用）](implementing-3d-app-launchers-win32.md)
* [导航 Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)