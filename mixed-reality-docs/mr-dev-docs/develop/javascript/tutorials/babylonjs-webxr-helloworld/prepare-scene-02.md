---
title: 用基本 3D 对象准备场景的 Babylon.js 教程
description: 了解如何使用 babylon.js，以及如何将基本 3D 对象添加到场景中。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: 混合现实, javascript, 教程, BabylonJS, hololens, 混合现实, UWP, Windows 10, WebXR, 沉浸式 web
ms.localizationpriority: high
ms.openlocfilehash: 8213c445da9c1bbf0eeb591b7995fb61bc6d5b5f
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584498"
---
# <a name="tutorial-prepare-a-scene"></a>教程：准备场景

了解如何准备场景，并向场景添加一些基本的3D 元素。

本教程介绍如何执行下列操作：

> [!div class="checklist"]
> * 创建场景文件
> * 添加照相机
> * 添加光线
> * 添加基本 3D 元素

## <a name="before-you-begin"></a>准备阶段

在教程的上一步中，创建了一个基本网页。 打开网页进行编辑。

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

## <a name="create-a-scene"></a>创建场景文件

场景是将显示所有内容的位置。 可以有多个场景，并且可以在场景之间切换。 阅读有关 [babylon.js 场景](https://doc.babylonjs.com/divingDeeper/scene)的详细信息。

1. 在画布 html 元素后面添加脚本标记，并添加以下代码以创建填充了黑色的场景：

    ```html
    <script type="text/javascript">
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        const sceneToRender = createScene();
    </script>
    ```

    在上面的代码中，我们必须创建 babylon.js web 呈现引擎的实例，以在画布上呈现场景和挂钩事件。 有关该引擎的详细信息，请参阅文档页面 [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)

1. 默认情况下不呈现场景。 请记住，可能有多个场景，并且由您控制显示哪个场景。 若要在每一帧反复呈现场景，请在调用 createScene 函数之后执行以下代码：

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>添加基本 3D 元素

1. 让我们添加第一个 3D 形状。 在 3D 虚拟世界中，图形是通过“网格”生成的，许多三角小平面联接在一起，每个面由三个顶点构成。 您可以使用预定义的网格，也可以创建您自己的自定义网格。 在本教程中，我们将使用预定义的箱体网格，即立方体。 若要创建箱体，请使用 [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box)。 参数代表名称和选项（选项根据网格类型的不同而有所不同）。 将以下代码追加到函数 createScene：

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. 在 Microsoft Edge 浏览器中打开网页并查看输出。 浏览器窗口将显示一个空白页。 使用键盘打开 DevTools，并选择 F12 或 Control+Shift+I（Windows 和 Linux）或 Command+Option+I (macOS)。 打开“控制台”选项卡后，可以开始查找错误。 将显示错误：“未捕获的错误：未定义照相机”。 现在，我们必须将照相机添加到场景中。

## <a name="add-a-camera"></a>添加照相机

1. 若要看到虚拟世界并与之交互，必须将照相机连接到画布。 我们来添加 [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) 类型的照相机，它可以围绕着一个目标旋转。 创建照相机实例所需的参数如下：
    1. name：照相机的名称
    1. alpha：沿纵轴的角位置（以弧度表示）
    1. beta：沿横轴的角位置（以弧度表示）
    1. radius：与目标的距离
    1. target：照相机将始终面朝的点（通过 x-y-z 坐标定义）
    1. scene：照相机所在的场景

    alpha、beta、radius 和 target 共同定义照在空间中的位置，如下图所示：

    ![照相机的 Alpha Beta Radius](../images/camera-alpha-beta-radius.jpg)

    将以下代码追加到 createScene 函数：

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. 如果在浏览器中查看输出，将看到一个黑色画布。 我们还缺少光线。

## <a name="add-light"></a>添加光线

1. 一共有四种类型的光线，它们拥有一系列照明属性：点光源、定向光源、聚光灯和半球形光源。 接下来，添加环境光 [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight)，如下所示：

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. 网页的最终代码如下所示：

    ```html
    <html>
    <head>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    <body>
        <canvas id="renderCanvas"></canvas>
        <script>
            const canvas = document.getElementById("renderCanvas");
            const engine = new BABYLON.Engine(canvas, true);
            
            const createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            const sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. 在浏览器中查看输出。 您应看到立方体，并且使用鼠标可以围绕立方体旋转照相机，从而看到立方体的不同面：

![包含立方体的基本场景](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [下一教程：3. 与 3D 对象交互](interact-03.md)
