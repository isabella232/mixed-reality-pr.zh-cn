---
title: babylon.js 简介和 WebXR 教程
description: 完成本课程，了解如何使用 babylon.js和创建基本的混合现实应用程序。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: 混合现实, javascript, 教程, BabylonJS, hololens, 混合现实, UWP, Windows 10, WebXR, 沉浸式 web
ms.localizationpriority: high
ms.openlocfilehash: e2006e911ad9dae00252c929c7739ff2209f4bf7796f1c49e713cfaf53267cd2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196821"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>教程：使用 babylon.js 创建您的第一个 WebXR 应用程序

本教程将介绍如何使用 babylon.js 和 Visual Studio Code 创建基本混合现实应用。 要生成的应用将呈现一个立方体，使您可以旋转它以将其他面呈现在视野中，并添加交互。 在本教程中，你将了解如何执行以下操作：

> [!div class="checklist"]
> * 设置开发环境
> * 用于创建基本 3D 元素的 babylon.js API  
> * 创建新的网页
> * 与 3D 元素交互
> * 在 Windows Mixed Reality 模拟器中运行应用程序

## <a name="prerequisites"></a>先决条件

* 支持 WebXR 的浏览器，例如 [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 或更高版本
* [NodeJS](https://nodejs.org/)
* 可选：[Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10)（如果您想要使用 Windows Mixed Reality 模拟器）
* 可选：[Windows Mixed Reality 模拟器](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="getting-started"></a>入门

若要从头开始创建此项目，请首先创建一个 Visual Studio Code (VSCode) 项目。

> [!NOTE]
> 使用 VSCode 不是强制要求，但为了方便起见，我们将在本教程中使用它。 更有经验的 JavaScript 开发人员可以使用他们选择的其他编辑器，即使是最简单的记事本也可以。

1. 下载 [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 单个文件，或使用 [babylon.js 官方网站](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers)上提供的联机版本。 还可以从 [GitHub](https://github.com/BabylonJS/Babylon.js) 克隆整个 babylon.js 项目
1. 创建一个空文件并将其另存为 html 页面，例如index.html
1. 创建基本 html 标记并引用 babylon.js javascript 文件。 最终代码如下所示：

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. 在 body 中添加 canvas HTML 元素，以呈现 babylon.js 内容。 请注意，canvas 具有 id 属性，可让您稍后通过 JavaScript 访问此 HTML 元素。

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
    <body>
        <canvas id="renderCanvas"></canvas>
    </body>
    </html>
    ```

1. canvas 占据整个网页。 网页到此就完成了。 现在，网页已准备就绪。 您可以在任何浏览器中打开它，并确保没有显示任何错误，但目前还没有沉浸式体验。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [下一教程：2. 准备场景](prepare-scene-02.md)