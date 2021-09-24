---
title: 生成 3D 钢琴模型
description: 了解如何通过使用 Babylon.js 进行编码来创建 3D 钢琴模型
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: 混合现实, javascript, 教程, BabylonJS, hololens, 混合现实, UWP, Windows 10, WebXR, 沉浸式 web
ms.localizationpriority: high
ms.openlocfilehash: e5c3dd6206566f781ceb52e5d13a49a0c9ab1018
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932503"
---
# <a name="tutorial-build-a-3d-piano-model"></a>教程：构建 3D 钢琴模型

在本教程系列的上一个教程中，我们设置了一个网页，其中包含带有相机和灯光的 Babylon.js 场景。 在本教程中，我们将构建钢琴模型并将其添加到该场景中。

![立式钢琴网格](./images/standup-piano-mesh.png)

在本教程中，您将学习如何执行以下操作：

> [!div class="checklist"]
> * 创建、定位和合并网格
> * 从长方体网格构建钢琴键盘
> * 导入钢琴框架的 3D 模型

## <a name="before-you-begin"></a>准备阶段

确保已完成[本教程系列的上一个教程](introduction-01.md)，并准备好继续添加代码。

index.html 

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

scene.js

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

## <a name="getting-started"></a>入门

首先，让我们构建一个具有以下结构的简单钢琴键盘：

![钢琴音域说明](./images/piano-register.jpg)

此图像中有 7 个白键和 5 个黑键，其中每个键都标有音符的名称。 一个完整的 88 键钢琴键盘包含 7 组完全重复的黑白键选择（也称为音域）和 4 个额外的键。 每个音域的频率均为其前一个音域的两倍。 例如，C5（即第五个音域中的 C 音符）的音高频率是 C4 的两倍，D5 的音高频率是 D4 的两倍，依此类推。

从视觉上看，每个音域看起来都与另一个音域完全相同，因此我们可以开始研究如何使用黑白键选择创建一个简单的钢琴键盘。 稍后，我们可以找到一种方法将范围扩展到 88 键全钢琴键盘。

## <a name="build-a-simple-piano-keyboard"></a>构建一个简单的钢琴键盘

> [!NOTE]
> 虽然可以从在线资源中找到预先构建的钢琴键盘 3D 模型并将其导入网页，但在本教程中，我们将从头开始构建键盘，以实现最大的可自定义性并展示如何通过 Babylon.js 创建 3D 模型。

1. 在开始创建用于构建键盘的任何网格之前，请注意，每个黑键并没有完全与旁边两个白键的中间对齐，而且并非每个琴键的宽度都相同。 这意味着必须分别为每个琴键创建和定位网格。

    ![黑键对齐](./images/black-key-position.png)

1. 对于白键，可以观察到每个白键由两部分组成：(1) 下半部分是黑键下方的部分；(2) 上半部分是黑键旁边的部分。 这两个部分的尺寸不同，但堆叠在一起构成一个完整的白键。

    ![白键形状](./images/white-key-shape-label.png)

1. 下面是用于为音符 C 创建单个白键的代码（尚不用担心如何将其添加到 scene.js 中）：

    ```javascript
    const whiteKeyBottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: 2.3, height: 1.5, depth: 4.5}, scene);
    const whiteKeyTop = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: 1.4, height: 1.5, depth: 5}, scene);
    whiteKeyTop.position.z += 4.75;
    whiteKeyTop.position.x -= 0.45;

    // Parameters of BABYLON.Mesh.MergeMeshes:
    // (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
    const whiteKeyV1 = BABYLON.Mesh.MergeMeshes([whiteKeyBottom, whiteKeyTop], true, false, null, false, false);
    whiteKeyV1.material = whiteMat;
    whiteKeyV1.name = "C4";
    ```

    在这里，我们创建了两个[长方体](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box#box-mesh)网格，分别用于白键的下半部分和上半部分。 然后修改上半部分的位置，将其堆叠在下半部分的上方，并将其向左移动，为相邻的黑键 (C#) 留出空间。

    最后，使用 [MergeMeshes](https://doc.babylonjs.com/divingDeeper/mesh/mergeMeshes) 函数将这两部分合并在一起，构成一个完整的白键。 下面是此代码将生成的结果网格：

    ![白键 C](./images/white-key-c.png)

1. 创建黑键更加简单。 由于所有黑键的形状均为长方体，因此只需使用黑色 [StandardMaterial](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction#color) 创建长方体网格，便可创建黑键。

    > [!NOTE]
    > 由于默认的网格颜色是浅灰色，该颜色类似于白色，因此本教程不包含用于向白键添加白色材料的步骤。 但是，如果想要在白键上使用真实、明亮的白色，请随意自行添加材料。

    下面是用于创建黑键 C# 的代码（也不用担心如何将其添加到 scene.js）：

    ```javascript
    const blackMat = new BABYLON.StandardMaterial("black");
    blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

    const blackKey = BABYLON.MeshBuilder.CreateBox("C#4", {width: 1.4, height: 2, depth: 5}, scene);
    blackKey.position.z += 4.75;
    blackKey.position.y += 0.25;
    blackKey.position.x += 0.95;
    blackKey.material = blackMat;
    ```

    这段代码生成的黑键（以及之前的白键）如下所示：

    ![黑键 C#](./images/black-key-csharp.png)

1. 如你所见，创建每个琴键可能会产生很多类似的代码，因为我们必须指定其中每个琴键的尺寸和位置。 我们在下一部分中尝试更高效地进行创建。

## <a name="build-a-simple-piano-keyboard-efficiently"></a>高效构建简单的钢琴键盘

1. 虽然每个白键的形状略有不同，但它们均可通过组合上半部分和下半部分来创建。 我们接下来实现用于创建和定位任何白键的泛型函数。

    将以下函数添加到 scene.js 中，位于 `createScene()` 函数之外：

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    在此代码块中，我们创建了一个名为 `buildKey()` 的函数，如果 `props.type` 为 `"white"`，该函数将构建并返回白键。 通过在参数 `props` 中识别键的类型，可以通过使用 if 语句扩大范围，在同一个函数中创建黑键和白键。

    `buildKey()` 的参数是：
    * **场景**：琴键所在的场景
    * **父级**：网格的父级（这允许我们将所有琴键组合到一个父级）
    * **props**：将要构建的琴键的属性

    白键的 `props` 将包含以下项：
    * **类型**：“白色”
    * **名称**：琴键表示的音符名称
    * **topWidth**：上半部分的宽度
    * **bottomWidth**：下半部分的宽度
    * **topPositionX**：上半部分相对于下半部分的 x 位置
    * **wholePositionX**：整个琴键相对于音域终点（琴键 B 的右边缘）的 x 位置。
    * **音域**：琴键所属的音域（介于 0 到 8 之间的数字）
    * **referencePositionX**：音域终点的 x 坐标（用作参考点）。

    通过分离 `wholePositionX` 和 `referencePositionX`，我们能够初始化在任何音域中创建特定类型的琴键（例如 C）所需的 `props` 参数，然后在特定音域（例如 C4、C5）中创建该琴键时将 `register` 和 `referencePositionX` 添加到 `props`。

1. 同样，也可编写一个泛型函数来创建黑键。 扩展 `buildKey()` 函数以包含该逻辑：

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    黑键的 `props` 包含以下项：

    * **类型**：“黑色”
    * **名称**：琴键表示的音符名称
    * **wholePositionX**：整个键相对于音域终点（键 B 的右边缘）的 x 位置
    * **音域**：琴键所属的音域（介于 0 到 8 之间的数字）
    * **referencePositionX**：音域终点的 x 坐标（用作参考点）。

    用于创建黑键的 `props` 要简单得多，因为创建黑键只涉及创建一个长方体，并且每个黑键的宽度和 z 位置都相同。

1. 现在我们通过一种更有效的方法来创建琴键，让我们初始化一个数组，该数组存储与音域中的音符对应的每个琴键的 `props`，然后对每个琴键调用 `buildKey()` 函数，以在第 4 个音域中创建一个简单的键盘。

    我们还将创建一个名为 `keyboard` 的 [TransformNode](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/transform_node#a-transformnode)，作为所有钢琴键的[父级](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/parent#overview-of-a-parent)。 由于应用于父级的任何位置或缩放更改也将应用于子级，因此通过这种方式对琴键进行分组，我们可以将其作为一个整体进行缩放或移动。

    在 `createScene()` 函数中追加以下代码行：

    ```javascript
    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    keyParams.forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
    })
    ```

    你可能已经注意到，在此代码块中，我们将所有琴键都放置在相对于空间原点的位置。

1. 下面是 scene.js 到目前为止包含的代码：

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]

        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
        })

        const xrHelper = await scene.createDefaultXRExperienceAsync();

        return scene;
    }
    ```

1. 生成的键盘如下所示：

    ![包含一个音域的钢琴键盘](./images/piano-one-register.png)

## <a name="expanding-to-an-88-key-piano"></a>扩展到 88 键钢琴

在本部分中，我们将 key-creation 函数的用法扩展到生成完整的 88 键钢琴键盘。

1. 如前所述，完整的 88 键钢琴键盘包含 7 个重复音域和 4 个其他音符。 这些额外音符中有 3 个位于音域 0（键盘的左侧）中，1 个位于音域 8（键盘的右侧）中。

    ![88 键钢琴布局](./images/88-key-piano-keyboard-layout.jpg)

1. 我们将首先通过围绕之前编写的音乐循环添加一个额外的音乐循环来构建 7 个完整的重复。 将 `buildKey()` 函数的上一个循环替换为以下代码：

    ```javascript
    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }
    ```

    在此音乐循环中，我们为音域 1 到 7 构建琴键，并在每次移动到下一个音域时增加参考位置。

1. 接下来，让我们创建其余的琴键。 将以下代码片段添加到 `createScene()` 函数：

    ```javascript
    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    ```

    请注意，钢琴键盘最左边的琴键和最右边的琴键不适合 `keyParams` 中定义的 props 尺寸（因为它们不在边缘的黑键旁边），因此需要为每个琴键定义一个新的 `props` 对象以指定其特殊形状。

1. 更改后生成的键盘应如下所示：

    ![完整的钢琴键盘网格](./images/full-keyboard-mesh.png)

## <a name="adding-a-piano-frame"></a>添加钢琴框架

1. 这个场景看起来有点奇怪，只有一个键盘漂浮在空间中。 让我们在键盘周围添加一个钢琴框架，以创建立式钢琴的外观。

1. 与创建琴键的方式类似，也可通过定位和组合一组长方体网格来创建框架。

    但是，我们会将这个挑战留给你，你可以自己尝试并使用 [BABYLON.SceneLoader.ImportMesh](https://doc.babylonjs.com/divingDeeper/importers/loadingFileTypes#sceneloaderimportmesh) 导入立式钢琴框架的预构建网格。 将这段代码追加到 `createScene()`：

    ```javascript
    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });
    ```

    请注意，我们需要再次创建一个名为 `piano` 的父级 `TransformNode`，以将键盘和框架组合为一个整体。 如果需要这样做，这样可以更加轻松地移动或缩放整个钢琴。

1. 导入框架后，请注意，键盘位于框架的下半部分（因为琴键的 y 坐标默认值为 0）。 抬起键盘，使其与立式钢琴框架一致：

    ```javascript
    // Lift piano keys
    keyboard.position.y += 80;
    ```

    由于 `keyboard` 是所有钢琴键的父级，因此只需更改 `keyboard` 的 y 位置，即可抬起所有钢琴键。

1. scene.js 的最终代码应如下所示：

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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

        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        // Register 1 through 7
        var referencePositionX = -2.4*14;
        for (let register = 1; register <= 7; register++) {
            keyParams.forEach(key => {
                buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
            })
            referencePositionX += 2.4*7;
        }
    
        // Register 0
        buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
        keyParams.slice(10, 12).forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
        })
    
        // Register 8
        buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    
        // Transform node that acts as the parent of all piano components
        const piano = new BABYLON.TransformNode("piano");
        keyboard.parent = piano;
    
        // Import and scale piano frame
        BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
            const frame = meshes[0];
            frame.parent = piano;
        });
    
        // Lift the piano keyboard
        keyboard.position.y += 80;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. 现在应有一个如下所示的立式钢琴：![立式钢琴网格](./images/standup-piano-mesh.png)

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [下一个教程：弹奏 3D 钢琴](keyboard-interaction-03.md)
