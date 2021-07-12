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
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="87394-104">教程：准备场景</span><span class="sxs-lookup"><span data-stu-id="87394-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="87394-105">了解如何准备场景，并向场景添加一些基本的3D 元素。</span><span class="sxs-lookup"><span data-stu-id="87394-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="87394-106">本教程介绍如何执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="87394-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="87394-107">创建场景文件</span><span class="sxs-lookup"><span data-stu-id="87394-107">Create a scene</span></span>
> * <span data-ttu-id="87394-108">添加照相机</span><span class="sxs-lookup"><span data-stu-id="87394-108">Add a camera</span></span>
> * <span data-ttu-id="87394-109">添加光线</span><span class="sxs-lookup"><span data-stu-id="87394-109">Add light</span></span>
> * <span data-ttu-id="87394-110">添加基本 3D 元素</span><span class="sxs-lookup"><span data-stu-id="87394-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="87394-111">准备阶段</span><span class="sxs-lookup"><span data-stu-id="87394-111">Before you begin</span></span>

<span data-ttu-id="87394-112">在教程的上一步中，创建了一个基本网页。</span><span class="sxs-lookup"><span data-stu-id="87394-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="87394-113">打开网页进行编辑。</span><span class="sxs-lookup"><span data-stu-id="87394-113">Have the web page open for editing.</span></span>

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

## <a name="create-a-scene"></a><span data-ttu-id="87394-114">创建场景文件</span><span class="sxs-lookup"><span data-stu-id="87394-114">Create a scene</span></span>

<span data-ttu-id="87394-115">场景是将显示所有内容的位置。</span><span class="sxs-lookup"><span data-stu-id="87394-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="87394-116">可以有多个场景，并且可以在场景之间切换。</span><span class="sxs-lookup"><span data-stu-id="87394-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="87394-117">阅读有关 [babylon.js 场景](https://doc.babylonjs.com/divingDeeper/scene)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="87394-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="87394-118">在画布 html 元素后面添加脚本标记，并添加以下代码以创建填充了黑色的场景：</span><span class="sxs-lookup"><span data-stu-id="87394-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

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

    <span data-ttu-id="87394-119">在上面的代码中，我们必须创建 babylon.js web 呈现引擎的实例，以在画布上呈现场景和挂钩事件。</span><span class="sxs-lookup"><span data-stu-id="87394-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="87394-120">有关该引擎的详细信息，请参阅文档页面 [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span><span class="sxs-lookup"><span data-stu-id="87394-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="87394-121">默认情况下不呈现场景。</span><span class="sxs-lookup"><span data-stu-id="87394-121">The scene is not rendered by default.</span></span> <span data-ttu-id="87394-122">请记住，可能有多个场景，并且由您控制显示哪个场景。</span><span class="sxs-lookup"><span data-stu-id="87394-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="87394-123">若要在每一帧反复呈现场景，请在调用 createScene 函数之后执行以下代码：</span><span class="sxs-lookup"><span data-stu-id="87394-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="87394-124">添加基本 3D 元素</span><span class="sxs-lookup"><span data-stu-id="87394-124">Add basic 3D element</span></span>

1. <span data-ttu-id="87394-125">让我们添加第一个 3D 形状。</span><span class="sxs-lookup"><span data-stu-id="87394-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="87394-126">在 3D 虚拟世界中，图形是通过“网格”生成的，许多三角小平面联接在一起，每个面由三个顶点构成。</span><span class="sxs-lookup"><span data-stu-id="87394-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="87394-127">您可以使用预定义的网格，也可以创建您自己的自定义网格。</span><span class="sxs-lookup"><span data-stu-id="87394-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="87394-128">在本教程中，我们将使用预定义的箱体网格，即立方体。</span><span class="sxs-lookup"><span data-stu-id="87394-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="87394-129">若要创建箱体，请使用 [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box)。</span><span class="sxs-lookup"><span data-stu-id="87394-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="87394-130">参数代表名称和选项（选项根据网格类型的不同而有所不同）。</span><span class="sxs-lookup"><span data-stu-id="87394-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="87394-131">将以下代码追加到函数 createScene：</span><span class="sxs-lookup"><span data-stu-id="87394-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="87394-132">在 Microsoft Edge 浏览器中打开网页并查看输出。</span><span class="sxs-lookup"><span data-stu-id="87394-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="87394-133">浏览器窗口将显示一个空白页。</span><span class="sxs-lookup"><span data-stu-id="87394-133">The browser window shows a blank page.</span></span> <span data-ttu-id="87394-134">使用键盘打开 DevTools，并选择 F12 或 Control+Shift+I（Windows 和 Linux）或 Command+Option+I (macOS)。</span><span class="sxs-lookup"><span data-stu-id="87394-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="87394-135">打开“控制台”选项卡后，可以开始查找错误。</span><span class="sxs-lookup"><span data-stu-id="87394-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="87394-136">将显示错误：“未捕获的错误：未定义照相机”。</span><span class="sxs-lookup"><span data-stu-id="87394-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="87394-137">现在，我们必须将照相机添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="87394-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="87394-138">添加照相机</span><span class="sxs-lookup"><span data-stu-id="87394-138">Add a camera</span></span>

1. <span data-ttu-id="87394-139">若要看到虚拟世界并与之交互，必须将照相机连接到画布。</span><span class="sxs-lookup"><span data-stu-id="87394-139">In order to view the virtual world and interact with it, a camera must be attached to the canvas.</span></span> <span data-ttu-id="87394-140">我们来添加 [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) 类型的照相机，它可以围绕着一个目标旋转。</span><span class="sxs-lookup"><span data-stu-id="87394-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), which can be rotated around a target.</span></span> <span data-ttu-id="87394-141">创建照相机实例所需的参数如下：</span><span class="sxs-lookup"><span data-stu-id="87394-141">The parameters required to create an instance of the camera are:</span></span>
    1. <span data-ttu-id="87394-142">name：照相机的名称</span><span class="sxs-lookup"><span data-stu-id="87394-142">**name**: name of the camera</span></span>
    1. <span data-ttu-id="87394-143">alpha：沿纵轴的角位置（以弧度表示）</span><span class="sxs-lookup"><span data-stu-id="87394-143">**alpha**: angular position along the longitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="87394-144">beta：沿横轴的角位置（以弧度表示）</span><span class="sxs-lookup"><span data-stu-id="87394-144">**beta**: angular position along the latitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="87394-145">radius：与目标的距离</span><span class="sxs-lookup"><span data-stu-id="87394-145">**radius**: distance from the target</span></span>
    1. <span data-ttu-id="87394-146">target：照相机将始终面朝的点（通过 x-y-z 坐标定义）</span><span class="sxs-lookup"><span data-stu-id="87394-146">**target**: the point that the camera would always face towards (defined by x-y-z coordinates)</span></span>
    1. <span data-ttu-id="87394-147">scene：照相机所在的场景</span><span class="sxs-lookup"><span data-stu-id="87394-147">**scene**: the scene that the camera is in</span></span>

    <span data-ttu-id="87394-148">alpha、beta、radius 和 target 共同定义照在空间中的位置，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="87394-148">Alpha, beta, radius, and target together define the camera's position in the space, as shown in the diagram below:</span></span>

    ![照相机的 Alpha Beta Radius](../images/camera-alpha-beta-radius.jpg)

    <span data-ttu-id="87394-150">将以下代码追加到 createScene 函数：</span><span class="sxs-lookup"><span data-stu-id="87394-150">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="87394-151">如果在浏览器中查看输出，将看到一个黑色画布。</span><span class="sxs-lookup"><span data-stu-id="87394-151">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="87394-152">我们还缺少光线。</span><span class="sxs-lookup"><span data-stu-id="87394-152">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="87394-153">添加光线</span><span class="sxs-lookup"><span data-stu-id="87394-153">Add light</span></span>

1. <span data-ttu-id="87394-154">一共有四种类型的光线，它们拥有一系列照明属性：点光源、定向光源、聚光灯和半球形光源。</span><span class="sxs-lookup"><span data-stu-id="87394-154">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="87394-155">接下来，添加环境光 [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="87394-155">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="87394-156">网页的最终代码如下所示：</span><span class="sxs-lookup"><span data-stu-id="87394-156">The final code of the web page will look as follows:</span></span>

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

1. <span data-ttu-id="87394-157">在浏览器中查看输出。</span><span class="sxs-lookup"><span data-stu-id="87394-157">Check the output in the browser.</span></span> <span data-ttu-id="87394-158">您应看到立方体，并且使用鼠标可以围绕立方体旋转照相机，从而看到立方体的不同面：</span><span class="sxs-lookup"><span data-stu-id="87394-158">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![包含立方体的基本场景](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="87394-160">后续步骤</span><span class="sxs-lookup"><span data-stu-id="87394-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="87394-161">下一教程：3. 与 3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="87394-161">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)
