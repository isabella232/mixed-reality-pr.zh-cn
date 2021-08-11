---
title: 与 3D 对象交互的 Babylon.js 教程
description: 了解如何使用 babylon.js 并与 3D 对象交互。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: 混合现实, javascript, 教程, BabylonJS, hololens, 混合现实, UWP, Windows 10, WebXR, 沉浸式 web
ms.localizationpriority: high
ms.openlocfilehash: 9aa044789c5d9d331677206dbc7ef7170bfa592075819ae73bd46aa14116122a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196874"
---
# <a name="tutorial-interact-with-3d-object"></a>教程：与 3D 对象交互

了解如何使用 babylon.js 为混合现实体验创建 3D 对象和交互。 在本部分中，您将从一些简单内容开始，例如，在选择对象时为立方体面涂色。

本教程涵盖以下主题：

> [!div class="checklist"]
> * 如何添加交互
> * 启用 WebXR 沉浸式模式
> * 在 Windows Mixed Reality 模拟器上运行应用
> * 在 Android Chrome 上运行和调试应用

## <a name="before-you-begin"></a>准备阶段

在教程的上一步中，创建了一个包含场景的基本网页。 打开主页进行编辑。

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

## <a name="add-interaction"></a>添加交互

1. 首先，让我们更新创建立方体的代码，以便使用随机颜色为立方体涂色。 为此，我们将向立方体添加[材料](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction)。 材料允许我们指定颜色和纹理，并可用于覆盖其他对象。 材料显示方式取决于场景中使用的光线以及材料对光线的响应方式。 例如，diffuseColor 将颜色分布到它所附加到的网格上。 添加以下代码：

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. 现在，立方体已经涂上了随机颜色，接下来让我们添加如下交互：

    * 单击立方体时更改颜色
    * 更改颜色后移动立方体

    若要添加交互，应使用[操作](https://doc.babylonjs.com/divingDeeper/events/actions)。 系统会启动操作以响应事件触发器。 例如，当用户单击立方体时。 我们只需实例化 BABYLON.ActionManager 并为特定触发器注册操作。 当有人单击立方体时，[BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) 将运行 JavaScript 函数：

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            const sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a>启用 WebXR 沉浸式体验

现在，立方体正在更改颜色，我们已准备好尝试沉浸式体验。

1. 在此步骤中，我们将介绍一个[地面](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground)。 立方体将悬吊于空中，我们将在底部看到地板。 按如下所示添加地面：

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    这会创建一个简单的 4x4 米的地板。

1. 为了添加 WebXR 支持，我们需要调用 createDefaultXRExperienceAsync，它会产生 Promise 结果。 在 createScene 函数（而不是 return scene;）的末尾添加此代码：

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. 由于 createScene 函数现在会返回 promise 而不是场景，因此我们需要修改 createScene 和 engine.runRenderLoop 的调用方式。 将这些函数的当前调用（位于 *\</script>* 标记之前）替换为以下代码：

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                const xrPromise = scene.createDefaultXRExperienceAsync({
                    floorMeshes: [ground]
                });
                
                return xrPromise.then((xrExperience) => {
                    console.log("Done, WebXR is enabled.");
                    return scene;
                });
            };
            
            createScene().then(sceneToRender => {
                engine.runRenderLoop(() => sceneToRender.render());
            });
        </script>
    </body>
    </html>
    ```

1. 上述代码在浏览器窗口中生成以下输出：![WebXR 场景](../images/hello-world-webxr-scene.png)

## <a name="run-on-a-windows-mixed-reality-simulator"></a>在 Windows Mixed Reality 模拟器上运行

1. [启用 Windows Mixed Reality 模拟器](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)（如果之前没有启用）。

1. 选择右下角的沉浸式 VR 按钮：![沉浸式 VR 按钮](../images/immersive-vr-button.png)

1. 此操作将启动 Windows Mixed Reality 模拟器窗口，如下所示：![混合现实门户](../images/mixed-reality-portal.png)

1. 使用键盘上的 W、A、S 和 D 键相应地向前、向后、向左和向右移动。 使用模拟的手对准立方体，然后按键盘上的 Enter 键执行单击操作。 立方体将更改其颜色并移动到新位置。

> [!NOTE]
> 对准立方体时，请确保手部射线末端（白色圆圈）与立方体相交，如上图所示。 详细了解[用手指向和提交](../../../../design/point-and-commit.md)。

## <a name="run-and-debug-on-android-device"></a>在 Android 设备上运行和调试

执行以下步骤，在 Android 设备上启用调试：

### <a name="prerequisites"></a>先决条件

* 在开发计算机上的安全上下文中提供静态 html 页面的 Web 服务器（ https:// 或通过 localhost 上的端口转发）。 例如，利用 serve npm 包作为简单的轻量级 Web 服务器来提供静态 html 文件，进一步了解 [npm serve](https://github.com/vercel/serve#readme)
* 设备最初附带 Google Play Store，并且必须运行 Android 7.0 或更新版本
* 开发工作站和设备上均装有最新版 [Google Chrome](https://support.google.com/chrome/answer/95346)
* 若要验证设备是否正确配置为运行 WebXR，请在设备上浏览到[示例 WebXR 页面](https://immersive-web.github.io/webxr-samples/)。 应看到如下消息：

    > 您的浏览器支持 WebXR，如果具有适当的硬件，可以运行虚拟现实和增强现实体验。

1. 在 Android 设备上启用开发人员模式和 USB 调试。 请参阅官方文档页面[配置设备上的开发人员选项](https://developer.android.com/studio/debug/dev-options)，了解如何为您使用的 Android 版本执行此操作
1. 接下来，通过 USB 线将 Android 设备连接到开发计算机或笔记本电脑
1. 确保开发计算机上的 Web 服务器正在运行。 例如，导航到包含 Web 主页 (index.html) 的 root 文件夹，并执行以下代码（假设您使用 serve npm 包）：

    ```bash
    serve
    ```

1. 在开发计算机上打开 Google Chrome，并在地址栏中输入以下文本：
    > chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)
1. 确保已启用“发现 USB 设备”复选框
1. 单击“端口转发”按钮，确保“端口转发”已启用并包含条目 localhost:5000，如下所示：![Chrome 端口转发窗口](../images/chrome-port-forwarding.png)
1. 在连接的 Android 设备中，打开 Google Chrome 窗口并浏览到 *http://localhost:5000* ，您应该会看到立方体
1. 在开发计算机上的 Chrome 中，您将看到您的设备和设备中当前打开的网页列表：![Chrome 检查窗口](../images/chrome-inspect.png)
1. 单击条目 *http://localhost:5000* 旁边的“检查”：![ Chrome DevTools 调试窗口](../images/chrome-debug.png)
1. 使用 [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) 调试页面

## <a name="takeaways"></a>要点

以下是本教程的内容要点：
* Babylon.js 有助于轻松地使用 JavaScript 打造沉浸式体验
* 若要创建虚拟场景，无需编写低级别代码或学习新技术
* 可以使用支持 WebXR 浏览器生成混合现实应用程序，而无需购买头戴显示设备

## <a name="next-steps"></a>后续步骤

祝贺！ 您已完成 babylon.js 系列教程并学习了如何：
> [!div class="checklist"]
> * 设置开发环境
> * 创建新的网页来显示结果
> * 用于创建基本 3D 元素并与之交互的 babylon.js API
> * 在 Windows Mixed Reality 模拟器中运行和测试应用程序

有关混合现实 JavaScript 开发的更多信息，请参阅 [JavaScript 开发概述](/javascript-development-overview.md)。
