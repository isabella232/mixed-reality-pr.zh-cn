---
title: 使用 BabylonJS 在 WebXR 中构建钢琴
description: 请完成本教程系列，了解如何使用 BabylonJS 在 WebXR 中构建功能正常的 88 键钢琴键盘
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: 混合现实, javascript, 教程, BabylonJS, hololens, 混合现实, UWP, Windows 10, WebXR, 沉浸式 web
ms.localizationpriority: high
ms.openlocfilehash: 93a3896b081e736bb62bceb6c8ae609685d7c5b5
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932486"
---
# <a name="tutorial-build-a-piano-in-webxr-using-babylonjs"></a>教程：使用 Babylon.js 在 WebXR 中构建钢琴

在真实世界中建造一架钢琴需要很多时间、技能和材料。 我们来在 VR/AR 世界中构建一架钢琴怎么样？

在本教程系列中，你将了解如何使用 Babylon.js 创建混合现实 Web 应用，该应用包含在虚拟世界中正常使用的 88 键立式钢琴。 在完成的应用中，你将能够传送到钢琴并使用混合现实控制器弹奏琴键。

在本教程系列中，你将了解如何执行以下操作：

> [!div class="checklist"]
> * 创建、定位和合并网格以构建钢琴键盘
> * 导入立式钢琴框架的 Babylon.js 模型
> * 为每个钢琴键添加指针交互
> * 在 WebXR 中启用传送和多指针支持

## <a name="prerequisites"></a>先决条件

* 一台连接到 Internet 的计算机
* 具备 Javascript 基础知识
* [WebXR Javascript Hello World 教程](../babylonjs-webxr-helloworld/introduction-01.md)
* 支持 WebXR 的浏览器，例如 [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 或更高版本
* 任何 [VR 头戴显示设备](../../../../discover/immersive-headset-hardware-details.md)或 [Windows Mixed Reality 模拟器](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)
* 可选：[Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10)（如果您想要使用 Windows Mixed Reality 模拟器）

## <a name="getting-started"></a>入门

我们首先开始设置包含 Babylon.js 场景的 HTML 网页。

1. 创建一个名为 babylonjs-piano-tutorial 的文件夹并在 Visual Studio Code 中打开该文件夹。

    > [!NOTE]
    > 虽然可以使用任何代码编辑器来完成此操作，但为了方便起见，我们将在本教程中使用 Visual Studio Code。

1. 在该文件夹中，创建一个名为 index.html 的文件并将以下模板插入到该文件中：

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas"); 
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
        
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

    如果需要有关此模板内容的更多说明，请参阅 [Hello World 教程](../babylonjs-webxr-helloworld/introduction-01.md)，这是本教程的先决条件。

1. 如果尝试在浏览器中打开此文件，控制台会显示一条错误消息，该消息表示找不到 `createScene()` 函数。 我们通过在下一部分中实现函数 `createScene()` 来解决此错误。

## <a name="setup-the-scene"></a>设置场景

1. 在与 index.html 相同的文件夹中，创建另一个名为 scene.js 的文件 。 我们将在此文件中存储与设置场景和创建钢琴相关的所有 JavaScript 代码。

1. 我们将 `createScene()` 函数添加到 scene.js 中：

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        return scene;
    }
    ```

    请注意，我们将 `createScene()` 设为异步函数。 请继续关注以了解原因。

1. 接下来，我们需要灯光和相机，以便我们能够看到场景。 更新 `createScene()` 函数：

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);

        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;

        return scene;
    }
    ```

    在这里，我们创建了一个 [ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera)，它几乎完全指向下方并以空间的原点为目标。 我们创建的灯光是指向天空的 [HemisphericLight](https://doc.babylonjs.com/divingDeeper/lights/lights_introduction#the-hemispheric-light)，可用于模拟环境空间。 我们还通过降低亮度来稍微调暗灯光。

    如果需要复习如何创建相机和灯光，请在继续下一步之前重新访问 [Hello World 教程系列的准备场景部分](../babylonjs-webxr-helloworld/prepare-scene-02.md#add-a-camera)。

1. 最后，由于我们正在为 WebXR 平台进行开发，因此我们需要在场景中[启用 XR 体验](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)，方法是在 `return scene;` 前插入以下行：

    ```javascript
    const xrHelper = await scene.createDefaultXRExperienceAsync();
    ```

    在 JavaScript 中，若要在函数内的 `async` 函数上使用 `await` 键盘，父函数也必须是 `async`，这就是我们之前将 `createScene` 函数定义为异步的原因。 稍后在本教程系列中，我们将使用此 `xrHelper` 来启用和配置 Babylon.js 支持的不同 WebXR 功能。

1. 完成后的 scene.js 应如下所示：

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        
        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. 现在我们有一个可用的 `createScene()` 函数，接下来让 index.html 将 scene.js 文件作为脚本加载，以便在 index.html 中识别 `createScene()` 函数  。 在 html 文件的 `<header>` 部分添加以下代码行：

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <script src="scene.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas");
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
                
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

1. 在浏览器中打开 index.html 后，你会发现之前看到的错误信息不复存在，页面中会出现一个空的 Babylon.js 场景。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [下一个教程：构建 3D 钢琴模型](keyboard-model-02.md)
