---
title: 案例研究 - 生成 HoloSketch，一种空间布局和 UX 草图应用，HoloLens
description: HoloSketch 是一种设备空间布局和 UX 草图工具，HoloLens构建全息体验。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch， HoloLens， Windows Mixed Reality， 草图， 应用
ms.openlocfilehash: 24929d38f97a3c02946a28184d7702c151dc22b2
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757319"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>案例研究 - 生成 HoloSketch，一种空间布局和 UX 草图应用，HoloLens

HoloSketch 是一种设备空间布局和 UX 草图工具，HoloLens构建全息体验。 HoloSketch 适用于配对蓝牙键盘和鼠标，以及手势和语音命令。 HoloSketch 的用途是提供一个简单的 UX 布局工具，用于快速可视化和迭代。

![HoloSketch：适用于 HoloLens 的空间布局和 UX HoloLens。](images/holosketch-image-01-640px.png)<br>
*HoloSketch：适用于 HoloLens 的空间布局和 UX HoloLens*

![用于快速可视化和迭代的简单 UX 布局工具。](images/holosketch-image-02.png)<br>
*用于快速可视化和迭代的简单 UX 布局工具*

## <a name="features"></a>功能

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>用于快速研究与规模原型制作的基元

![使用基元形状](images/holosketch-primitives-giphy.gif)

使用基元形状进行快速批量研究和规模原型制作。

### <a name="import-objects-through-onedrive"></a>通过导入对象OneDrive

![导入对象](images/holosketch-importobjects-giphy.gif)

导入 PNG/JPG 图像或 3D FBX 对象 (Unity) 打包到混合现实空间中通过 OneDrive。

### <a name="manipulate-objects"></a>操作对象

![操作对象](images/manipulate-objects-640px.jpg)

使用 (3D 对象接口) 移动/旋转/缩放对象。

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>蓝牙、鼠标/键盘、手势和语音命令

![支持蓝牙](images/supports-bluetooth-640px.jpg)

HoloSketch 支持蓝牙/键盘、手势和语音命令。

## <a name="background"></a>背景

### <a name="importance-of-experiencing-your-design-in-the-device"></a>在设备中体验设计的重要性

为设备设计HoloLens时，在设备中体验设计非常重要。 混合现实应用设计的最大挑战之一是难以获得缩放性、位置和深度感，尤其是通过传统的 2D 草图。

### <a name="cost-of-2d-based-communication"></a>基于 2D 的通信成本

为了有效地将 UX 流和方案传达给其他人，设计人员可能会花费大量时间使用传统的 2D 工具（如 Illustrator、Photoshop 和 PowerPoint）。 这些 2D 设计通常需要额外努力将其转换为 3D。 此从 2D 到 3D 的翻译中丢失了一些想法。

### <a name="complex-deployment-process"></a>复杂的部署过程

由于混合现实是一个新的画布，因此它涉及大量的设计迭代和试错， 对于不熟悉 Unity 和 Visual Studio 等工具的设计人员，将某些内容放在一起并不HoloLens。 通常，必须完成以下过程，在设备中查看 2D/3D 图稿。 对于设计人员来说，这是快速进行想法和方案的一大障碍。

![复杂的部署过程](images/holosketch-image-03-1000px.png)<br>
*部署过程*

### <a name="simplified-process-with-holosketch"></a>使用 HoloSketch 简化过程

使用 HoloSketch 时，我们希望在不涉及开发工具和设备门户配对的情况下简化此过程。 使用 OneDrive，用户可以轻松地将 2D/3D 资产放入HoloLens。

![使用 HoloSketch 简化过程](images/holosketch-image-04-1000px.png)<br>
*使用 HoloSketch 简化过程*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>鼓励三维设计思维和解决方案

我们认为此工具会为设计人员提供在真正的三维空间中探索解决方案的机会，并且不会停滞在 2D 中。 他们不必考虑为 UI 创建 3D 背景，因为背景是真实情况，HoloLens。 HoloSketch 为设计人员打开了一种在 3D 设计上轻松浏览HoloLens。

## <a name="get-started"></a>开始使用

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>如何将 JPG/PNG (2D) 导入 HoloSketch

* UploadJPG/PNG 图像，OneDrive文件夹"Documents/HoloSketch"。
* 在 HoloSketch OneDrive菜单中，可以选择图像，将其放在环境中。

![导入 2D 图像](images/import-2d-images-1000px.jpg)<br>
*通过图像导入图像和 3D OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>如何将 3D 对象导入 HoloSketch

在上传到 OneDrive 文件夹之前，请按照以下步骤将 3D 对象打包到 Unity 资产捆绑包中。 使用此过程，可以从 3D 软件（如 Maya、则使用 4D 和 4D）导入 FBX/OBJ Microsoft 画图 3D。

>[!IMPORTANT]
>目前，Unity 版本 5.4.5f1 支持创建资产捆绑包。

1. 下载并打开 Unity 项目["AssetBunlder_Unity"。](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity) 此 Unity 项目包括用于捆绑资产生成脚本。
2. 创建新的 GameObject。
3. 根据内容命名 GameObject。
4. 在"检查器"面板中，单击"添加组件"并添加"Box Collider"。 

   ![在检查器面板中，单击"添加组件"并添加"Box Collider"](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在"检查器"面板中，单击"添加组件"，然后添加"盒碰撞体"#2](images/holosketch-10b-assetbundles-1000px.png)

5. 将 3D FBX 文件拖动到项目面板中，以将其导入。
6. 将对象拖到新 **GameObject 下的"层次结构"面板中**。

   ![将对象拖到新 GameObject 下的"层次结构"面板中](images/holosketch-12-assetbundles-1000px.png)

7. 如果碰撞体尺寸与对象不匹配，请调整该尺寸。 将 对象旋转为面向 **Z 轴**。

   ![如果碰撞体尺寸与对象不匹配，请调整该尺寸。](images/holosketch-13-assetbundles-1000px.png)

8. 将对象从"层次结构"面板拖到Project面板 **，使其预制**。
9. 在检查器面板的底部，单击下拉列表，创建并分配新的唯一名称。 以下示例演示如何为 AssetBundle 名称添加和分配"brownchair"。 

   ![在检查器面板的底部，单击下拉列表并分配新的唯一名称。](images/holosketch-14-assetbundles-1000px.png)

10. 为模型对象准备缩略图。 
   ![将图像拖动到项目面板中，并分配用于对象的名称。](images/holosketch-15-assetbundles-1000px.png)

11. 在 Unity 项目的"Asset"文件夹下创建名为"Assetbundles"的文件夹。

12. 从"资产"菜单中，选择"生成 AssetBundles"以生成文件。 
   ![从"资产"菜单中，选择"生成 AssetBundles"以生成文件。](images/holosketch-15a-assetbundles.png)


13. **Upload生成的文件提交到 OneDrive 上的 /Files/Documents/HoloSketch OneDrive。** Upload asset_unique_name文件。 无需上传清单文件或 AssetBundles 文件。 <br>
![将文件添加到 Files/Documents/HoloSketch/ 文件夹 你将 ](images/holosketch-onedriveupload-1000px.png)
 ![ 在 HoloSketch 的"OneDrive"菜单中看到添加的 3D 对象](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>如何操作对象

HoloSketch 支持在 3D 软件中广泛使用的传统接口。 可以使用手势和鼠标移动、旋转和缩放对象。 可以使用语音或键盘在不同的模式之间快速切换。

### <a name="object-manipulation-modes"></a>对象操作模式

![如何操作对象](images/holosketch-image-06-1000px.png)<br>
*如何操作对象*

### <a name="contextual-and-tool-belt-menus"></a>上下文和工具带菜单

**使用上下文菜单**

双击以打开上下文菜单。 

菜单项：
* **布局图面：** 这是一个 3D 网格系统，可在其中布局多个对象，并作为一个组进行管理。 双击布局图面以向其添加对象。
* **基元：** 使用立方体、球体、柱面和圆锥进行批量研究。
* **OneDrive：** 打开"OneDrive"菜单以导入对象。
* **帮助：** 显示帮助屏幕。

![上下文菜单](images/holosketch-image-07.png)<br>
*上下文菜单*

**使用"工具带"菜单**

"工具带"菜单中提供了移动、旋转、缩放、保存和加载场景。 

## <a name="using-keyboard-gestures-and-voice-commands"></a>使用键盘、手势和语音命令

![键盘、手势和语音命令](images/holosketch-image-08-1000px.png)<br>
*键盘、手势和语音命令*

## <a name="download-the-app"></a>下载应用

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">从客户端免费下载并安装 HoloSketch Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>已知问题
* Unity 版本 **5.4.5f1 目前支持创建资产捆绑包。**
* 根据应用中数据量OneDrive，应用在加载内容时可能OneDrive停止
* 目前，"保存和加载"功能仅支持基元对象
* 上下文菜单上禁用了"文本"、"声音"菜单、"视频和照片"菜单
* "工具带"菜单上的"播放"按钮可清除操作 gizmos

## <a name="sharing-your-sketches"></a>共享草图

可以通过说"你好，HoloLens，开始/停止录制Cortana视频录制功能。 将音量向上/向下键一起按下，拍摄草图的图片。

## <a name="about-the-authors"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon Park</b></a><br>用户体验设计师 @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>开发 人员 @Microsoft</td>
</tr>
</table> 