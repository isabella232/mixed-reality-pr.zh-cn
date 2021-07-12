---
title: 与 3D 对象交互的 Babylon.js 教程
description: 了解如何使用 babylon.js 并与 3D 对象交互。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: 混合现实, javascript, 教程, BabylonJS, hololens, 混合现实, UWP, Windows 10, WebXR, 沉浸式 web
ms.localizationpriority: high
ms.openlocfilehash: a3dbab0572cd50105dac3d877a0d72c5cbc504b6
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584516"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="3e512-104">教程：与 3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="3e512-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="3e512-105">了解如何使用 babylon.js 为混合现实体验创建 3D 对象和交互。</span><span class="sxs-lookup"><span data-stu-id="3e512-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="3e512-106">在本部分中，您将从一些简单内容开始，例如，在选择对象时为立方体面涂色。</span><span class="sxs-lookup"><span data-stu-id="3e512-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="3e512-107">本教程涵盖以下主题：</span><span class="sxs-lookup"><span data-stu-id="3e512-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3e512-108">如何添加交互</span><span class="sxs-lookup"><span data-stu-id="3e512-108">How to add interactions</span></span>
> * <span data-ttu-id="3e512-109">启用 WebXR 沉浸式模式</span><span class="sxs-lookup"><span data-stu-id="3e512-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="3e512-110">在 Windows Mixed Reality 模拟器上运行应用</span><span class="sxs-lookup"><span data-stu-id="3e512-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="3e512-111">在 Android Chrome 上运行和调试应用</span><span class="sxs-lookup"><span data-stu-id="3e512-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="3e512-112">准备阶段</span><span class="sxs-lookup"><span data-stu-id="3e512-112">Before you begin</span></span>

<span data-ttu-id="3e512-113">在教程的上一步中，创建了一个包含场景的基本网页。</span><span class="sxs-lookup"><span data-stu-id="3e512-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="3e512-114">打开主页进行编辑。</span><span class="sxs-lookup"><span data-stu-id="3e512-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="3e512-115">添加交互</span><span class="sxs-lookup"><span data-stu-id="3e512-115">Add interaction</span></span>

1. <span data-ttu-id="3e512-116">首先，让我们更新创建立方体的代码，以便使用随机颜色为立方体涂色。</span><span class="sxs-lookup"><span data-stu-id="3e512-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="3e512-117">为此，我们将向立方体添加[材料](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction)。</span><span class="sxs-lookup"><span data-stu-id="3e512-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="3e512-118">材料允许我们指定颜色和纹理，并可用于覆盖其他对象。</span><span class="sxs-lookup"><span data-stu-id="3e512-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="3e512-119">材料显示方式取决于场景中使用的光线以及材料对光线的响应方式。</span><span class="sxs-lookup"><span data-stu-id="3e512-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="3e512-120">例如，diffuseColor 将颜色分布到它所附加到的网格上。</span><span class="sxs-lookup"><span data-stu-id="3e512-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="3e512-121">添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="3e512-121">Add the following code:</span></span>

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="3e512-122">现在，立方体已经涂上了随机颜色，接下来让我们添加如下交互：</span><span class="sxs-lookup"><span data-stu-id="3e512-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="3e512-123">单击立方体时更改颜色</span><span class="sxs-lookup"><span data-stu-id="3e512-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="3e512-124">更改颜色后移动立方体</span><span class="sxs-lookup"><span data-stu-id="3e512-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="3e512-125">若要添加交互，应使用[操作](https://doc.babylonjs.com/divingDeeper/events/actions)。</span><span class="sxs-lookup"><span data-stu-id="3e512-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="3e512-126">系统会启动操作以响应事件触发器。</span><span class="sxs-lookup"><span data-stu-id="3e512-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="3e512-127">例如，当用户单击立方体时。</span><span class="sxs-lookup"><span data-stu-id="3e512-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="3e512-128">我们只需实例化 BABYLON.ActionManager 并为特定触发器注册操作。</span><span class="sxs-lookup"><span data-stu-id="3e512-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="3e512-129">当有人单击立方体时，[BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) 将运行 JavaScript 函数：</span><span class="sxs-lookup"><span data-stu-id="3e512-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

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

1. <span data-ttu-id="3e512-130">网页的最终代码如下所示：</span><span class="sxs-lookup"><span data-stu-id="3e512-130">The final code of the web page will look as follows:</span></span>

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="3e512-131">启用 WebXR 沉浸式体验</span><span class="sxs-lookup"><span data-stu-id="3e512-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="3e512-132">现在，立方体正在更改颜色，我们已准备好尝试沉浸式体验。</span><span class="sxs-lookup"><span data-stu-id="3e512-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="3e512-133">在此步骤中，我们将介绍一个[地面](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground)。</span><span class="sxs-lookup"><span data-stu-id="3e512-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="3e512-134">立方体将悬吊于空中，我们将在底部看到地板。</span><span class="sxs-lookup"><span data-stu-id="3e512-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="3e512-135">按如下所示添加地面：</span><span class="sxs-lookup"><span data-stu-id="3e512-135">Add the ground as follows:</span></span>

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="3e512-136">这会创建一个简单的 4x4 米的地板。</span><span class="sxs-lookup"><span data-stu-id="3e512-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="3e512-137">为了添加 WebXR 支持，我们需要调用 createDefaultXRExperienceAsync，它会产生 Promise 结果。</span><span class="sxs-lookup"><span data-stu-id="3e512-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="3e512-138">在 createScene 函数（而不是 return scene;）的末尾添加此代码：</span><span class="sxs-lookup"><span data-stu-id="3e512-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="3e512-139">由于 createScene 函数现在会返回 promise 而不是场景，因此我们需要修改 createScene 和 engine.runRenderLoop 的调用方式。</span><span class="sxs-lookup"><span data-stu-id="3e512-139">Since the *createScene* function is now returning a promise instead of a scene, we need to modify how *createScene* and *engine.runRenderLoop* are called.</span></span> <span data-ttu-id="3e512-140">将这些函数的当前调用（位于 *\</script>* 标记之前）替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="3e512-140">Replace the current calls of these functions, which are located right before the *\</script>* tag, with the code below:</span></span>

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. <span data-ttu-id="3e512-141">网页的最终代码如下所示：</span><span class="sxs-lookup"><span data-stu-id="3e512-141">The final code of the web page will look as follows:</span></span>

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

1. <span data-ttu-id="3e512-142">上述代码在浏览器窗口中生成以下输出：![WebXR 场景](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="3e512-142">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="3e512-143">在 Windows Mixed Reality 模拟器上运行</span><span class="sxs-lookup"><span data-stu-id="3e512-143">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="3e512-144">[启用 Windows Mixed Reality 模拟器](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)（如果之前没有启用）。</span><span class="sxs-lookup"><span data-stu-id="3e512-144">[Enable the Windows Mixed Reality Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) if you have not done so in the past.</span></span>

1. <span data-ttu-id="3e512-145">选择右下角的沉浸式 VR 按钮：![沉浸式 VR 按钮](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="3e512-145">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="3e512-146">此操作将启动 Windows Mixed Reality 模拟器窗口，如下所示：![混合现实门户](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="3e512-146">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="3e512-147">使用键盘上的 W、A、S 和 D 键相应地向前、向后、向左和向右移动。</span><span class="sxs-lookup"><span data-stu-id="3e512-147">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="3e512-148">使用模拟的手对准立方体，然后按键盘上的 Enter 键执行单击操作。</span><span class="sxs-lookup"><span data-stu-id="3e512-148">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="3e512-149">立方体将更改其颜色并移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="3e512-149">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="3e512-150">对准立方体时，请确保手部射线末端（白色圆圈）与立方体相交，如上图所示。</span><span class="sxs-lookup"><span data-stu-id="3e512-150">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="3e512-151">详细了解[用手指向和提交](../../../../design/point-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="3e512-151">Learn more about [Point and commit with hands](../../../../design/point-and-commit.md).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="3e512-152">在 Android 设备上运行和调试</span><span class="sxs-lookup"><span data-stu-id="3e512-152">Run and debug on Android device</span></span>

<span data-ttu-id="3e512-153">执行以下步骤，在 Android 设备上启用调试：</span><span class="sxs-lookup"><span data-stu-id="3e512-153">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3e512-154">先决条件</span><span class="sxs-lookup"><span data-stu-id="3e512-154">Prerequisites</span></span>

* <span data-ttu-id="3e512-155">在开发计算机上的安全上下文中提供静态 html 页面的 Web 服务器（ https:// 或通过 localhost 上的端口转发）。</span><span class="sxs-lookup"><span data-stu-id="3e512-155">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="3e512-156">例如，利用 serve npm 包作为简单的轻量级 Web 服务器来提供静态 html 文件，进一步了解 [npm serve](https://github.com/vercel/serve#readme)</span><span class="sxs-lookup"><span data-stu-id="3e512-156">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="3e512-157">设备最初附带 Google Play Store，并且必须运行 Android 7.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="3e512-157">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="3e512-158">开发工作站和设备上均装有最新版 [Google Chrome](https://support.google.com/chrome/answer/95346)</span><span class="sxs-lookup"><span data-stu-id="3e512-158">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="3e512-159">若要验证设备是否正确配置为运行 WebXR，请在设备上浏览到[示例 WebXR 页面](https://immersive-web.github.io/webxr-samples/)。</span><span class="sxs-lookup"><span data-stu-id="3e512-159">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="3e512-160">应看到如下消息：</span><span class="sxs-lookup"><span data-stu-id="3e512-160">You should see the message, such as:</span></span>

    > <span data-ttu-id="3e512-161">您的浏览器支持 WebXR，如果具有适当的硬件，可以运行虚拟现实和增强现实体验。</span><span class="sxs-lookup"><span data-stu-id="3e512-161">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="3e512-162">在 Android 设备上启用开发人员模式和 USB 调试。</span><span class="sxs-lookup"><span data-stu-id="3e512-162">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="3e512-163">请参阅官方文档页面[配置设备上的开发人员选项](https://developer.android.com/studio/debug/dev-options)，了解如何为您使用的 Android 版本执行此操作</span><span class="sxs-lookup"><span data-stu-id="3e512-163">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="3e512-164">接下来，通过 USB 线将 Android 设备连接到开发计算机或笔记本电脑</span><span class="sxs-lookup"><span data-stu-id="3e512-164">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="3e512-165">确保开发计算机上的 Web 服务器正在运行。</span><span class="sxs-lookup"><span data-stu-id="3e512-165">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="3e512-166">例如，导航到包含 Web 主页 (index.html) 的 root 文件夹，并执行以下代码（假设您使用 serve npm 包）：</span><span class="sxs-lookup"><span data-stu-id="3e512-166">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="3e512-167">在开发计算机上打开 Google Chrome，并在地址栏中输入以下文本：</span><span class="sxs-lookup"><span data-stu-id="3e512-167">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="3e512-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="3e512-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="3e512-169">确保已启用“发现 USB 设备”复选框</span><span class="sxs-lookup"><span data-stu-id="3e512-169">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="3e512-170">单击“端口转发”按钮，确保“端口转发”已启用并包含条目 localhost:5000，如下所示：![Chrome 端口转发窗口](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="3e512-170">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="3e512-171">在连接的 Android 设备中，打开 Google Chrome 窗口并浏览到 *http://localhost:5000* ，您应该会看到立方体</span><span class="sxs-lookup"><span data-stu-id="3e512-171">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="3e512-172">在开发计算机上的 Chrome 中，您将看到您的设备和设备中当前打开的网页列表：![Chrome 检查窗口](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="3e512-172">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="3e512-173">单击条目 *http://localhost:5000* 旁边的“检查”：![ Chrome DevTools 调试窗口](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="3e512-173">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="3e512-174">使用 [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) 调试页面</span><span class="sxs-lookup"><span data-stu-id="3e512-174">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="3e512-175">要点</span><span class="sxs-lookup"><span data-stu-id="3e512-175">Takeaways</span></span>

<span data-ttu-id="3e512-176">以下是本教程的内容要点：</span><span class="sxs-lookup"><span data-stu-id="3e512-176">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="3e512-177">Babylon.js 有助于轻松地使用 JavaScript 打造沉浸式体验</span><span class="sxs-lookup"><span data-stu-id="3e512-177">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="3e512-178">若要创建虚拟场景，无需编写低级别代码或学习新技术</span><span class="sxs-lookup"><span data-stu-id="3e512-178">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="3e512-179">可以使用支持 WebXR 浏览器生成混合现实应用程序，而无需购买头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="3e512-179">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="3e512-180">后续步骤</span><span class="sxs-lookup"><span data-stu-id="3e512-180">Next steps</span></span>

<span data-ttu-id="3e512-181">祝贺！</span><span class="sxs-lookup"><span data-stu-id="3e512-181">Congratulations!</span></span> <span data-ttu-id="3e512-182">您已完成 babylon.js 系列教程并学习了如何：</span><span class="sxs-lookup"><span data-stu-id="3e512-182">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="3e512-183">设置开发环境</span><span class="sxs-lookup"><span data-stu-id="3e512-183">Set up a development environment</span></span>
> * <span data-ttu-id="3e512-184">创建新的网页来显示结果</span><span class="sxs-lookup"><span data-stu-id="3e512-184">Create a new web page to display results</span></span>
> * <span data-ttu-id="3e512-185">用于创建基本 3D 元素并与之交互的 babylon.js API</span><span class="sxs-lookup"><span data-stu-id="3e512-185">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="3e512-186">在 Windows Mixed Reality 模拟器中运行和测试应用程序</span><span class="sxs-lookup"><span data-stu-id="3e512-186">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="3e512-187">有关混合现实 JavaScript 开发的更多信息，请参阅 [JavaScript 开发概述](/javascript-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3e512-187">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>
