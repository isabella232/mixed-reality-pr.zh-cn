---
title: 适用于 Unity 的 MRTK Figma Bridge
description: 使用 MRTK Figma Bridge for Unity，你可以将 Figma Toolkit布局引入 Unity
author: dongpark
ms.author: dongpark
ms.date: 03/29/2021
ms.topic: article
keywords: Figma、Sketch、Adobe XD、设计、设计器、设计文件、UX 设计、HoloLens、MRTK、混合现实Toolkit
ms.openlocfilehash: d21caa796907ebc7ea1fb46ce940cf210e9fc49d
ms.sourcegitcommit: 9431e9d6d7e959954ab3e18ecc0e420a3583d1a0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053778"
---
# <a name="mrtk-figma-bridge-for-unity-beta"></a>适用于 Unity 的 MRTK Figma Bridge (Beta) 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWKiO4]

使用 MRTK Figma Bridge for Unity，你可以将 Figma Toolkit到 Unity。 网桥可以导入使用 MRTK Figma Toolkit创建的 UI 布局，然后使用适当的位置和大小实例化相应的 MRTK 预制。 Figma Bridge 将帮助设计集成过程以及设计人员和开发人员之间的协作。


请参阅[MRTK Figma Toolkit](figma-toolkit.md)页，了解 Figma Toolkit这是具有设计HoloLens 2 UI 库的设计文件。

## <a name="prerequisites"></a>先决条件
- 请参阅 [安装用于](/windows/mixed-reality/develop/install-the-tools) 混合现实开发所需软件的工具
- Unity 2019 或更高版本
- [MRTK-Unity 2.7.0 或更高版本](/windows/mixed-reality/mrtk-unity/)

> [!IMPORTANT]
> **需要MRTK-Unity 2.7.0 或更高版本**
> 
> 由于 Figma Toolkit 和 Figma Bridge 基于 MRTK 2.7.0 预制项，因此需要 MRTK 2.7.0 或更高版本。 与较低版本的 MRTK 一起使用时，某些组件无法正确转换。

## <a name="how-to-use-mrtk-figma-bridge"></a>如何使用 MRTK Figma Bridge

### <a name="1-installation"></a>1.安装

Figma Unity Bridge 可以通过混合现实 [功能工具 进行安装](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)。 下载并运行混合现实功能工具。

在 **"发现功能"** 页的"**混合现实Toolkit** 部分，选择 **"MRTK Figma Unity Bridge"。** 按照步骤完成 MR 功能工具并返回到 Unity 项目。 Unity 将导入 MRTK Figma Bridge 的包。

### <a name="2-open-figma-bridge-window"></a>2.打开 Figma Bridge 窗口

完成导入过程后，可以在"Figma Bridge"的"混合现实"菜单下> Toolkit > **Figma Bridge**

<img src="images/FigmaToolkit/FigmaBridge_Menu.png" width="500px" alt="Figma Bridge - Menu"><br>

### <a name="3-generate-and-enter-your-figma-token"></a>3.生成并输入 Figma 令牌

在 Figma 网站上，单击左上角的 Figma 菜单，打开"帮助和帐户">帐户设置。 在"个人访问令牌"部分中生成新的个人访问令牌。

<img src="images/FigmaToolkit/FigmaToolkit_Token.png" width="500px" alt="Figma Bridge - Get Token"><br>

<img src="images/FigmaToolkit/FigmaBridge_Token.png" width="500px" alt="Figma Bridge - Enter Token"><br>


### <a name="4-enter-id-for-a-figma-document"></a>4.输入 Figma 文档的 ID
每个 Figma 文档在 URL 中都有唯一 ID。 将此 ID 复制并粘贴到 Figma Bridge 中。

<img src="images/FigmaToolkit/FigmaToolkit_DocID.png" alt="Figma Bridge - Doc ID"><br>

单击 **"获取文件** "以下载 Figma 文件。 可以通过输入新 ID 来下载其他 Figma 文件。

单击 **"加载文件** "打开 Figma 文件。

<img src="images/FigmaToolkit/FigmaBridge_Files.png" width="500px" alt="Figma Bridge - Files"><br>

### <a name="5-build-a-page"></a>5.生成页面

Figma Bridge 将显示 Figma 文件中的页面列表。 检查想要在 Unity 中生成的页面。 单击 **"生成页面"** 按钮。

<img src="images/FigmaToolkit/FigmaBridge_Pages.png" width="500px" alt="Figma Bridge - Pages"><br>

<img src="images/FigmaToolkit/FigmaBridge_Result.png" alt="Figma Bridge - Result"><br>

### <a name="6-refresh-a-document-for-changes"></a>6.刷新文档以进行更改

可以在 Web 应用上修改 Figma 文件 (桌面编辑器) 单击"刷新"以检索任何更改。 单击 **"生成页面** "以使用更新进行生成。 这样，你可以轻松地在 Figma 中访问设计，在 Unity 中查看它。



## <a name="see-also"></a>另请参阅
* [Figma 工具包](figma-toolkit.md)
* [光标](cursors.md)
* [手部射线](point-and-commit.md)
* [Button](button.md)
* [可交互对象](interactable-object.md)
* [边界框和应用栏](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手动菜单](hand-menu.md)
* [追踪菜单](near-menu.md)
* [对象集合](object-collection.md)
* [语音命令](voice-input.md)
* [键盘](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑块](slider.md)
* [着色器](shader.md)
* [公告和尾随](billboarding-and-tag-along.md)
* [显示进度](progress.md)
* [表面磁吸](surface-magnetism.md)
