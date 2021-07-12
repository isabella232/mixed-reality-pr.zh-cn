---
title: babylon.js 简介和 WebXR 教程
description: 完成本课程，了解如何使用 babylon.js和创建基本的混合现实应用程序。
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: 混合现实, javascript, 教程, BabylonJS, hololens, 混合现实, UWP, Windows 10, WebXR, 沉浸式 web
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600116"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="2e12d-104">教程：使用 babylon.js 创建您的第一个 WebXR 应用程序</span><span class="sxs-lookup"><span data-stu-id="2e12d-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="2e12d-105">本教程将介绍如何使用 babylon.js 和 Visual Studio Code 创建基本混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="2e12d-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="2e12d-106">要生成的应用将呈现一个立方体，使您可以旋转它以将其他面呈现在视野中，并添加交互。</span><span class="sxs-lookup"><span data-stu-id="2e12d-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="2e12d-107">在本教程中，你将了解如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2e12d-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="2e12d-108">设置开发环境</span><span class="sxs-lookup"><span data-stu-id="2e12d-108">Set up a development environment</span></span>
> * <span data-ttu-id="2e12d-109">用于创建基本 3D 元素的 babylon.js API</span><span class="sxs-lookup"><span data-stu-id="2e12d-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="2e12d-110">创建新的网页</span><span class="sxs-lookup"><span data-stu-id="2e12d-110">Create a new web page</span></span>
> * <span data-ttu-id="2e12d-111">与 3D 元素交互</span><span class="sxs-lookup"><span data-stu-id="2e12d-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="2e12d-112">在 Windows Mixed Reality 模拟器中运行应用程序</span><span class="sxs-lookup"><span data-stu-id="2e12d-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2e12d-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="2e12d-113">Prerequisites</span></span>

* <span data-ttu-id="2e12d-114">支持 WebXR 的浏览器，例如 [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span><span class="sxs-lookup"><span data-stu-id="2e12d-114">WebXR-supported browser, for example [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span></span>
* <span data-ttu-id="2e12d-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="2e12d-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="2e12d-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="2e12d-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="2e12d-117">可选：[Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10)（如果您想要使用 Windows Mixed Reality 模拟器）</span><span class="sxs-lookup"><span data-stu-id="2e12d-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="2e12d-118">可选：[Windows Mixed Reality 模拟器](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="2e12d-118">Optional: [Windows Mixed Reality simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="getting-started"></a><span data-ttu-id="2e12d-119">入门</span><span class="sxs-lookup"><span data-stu-id="2e12d-119">Getting started</span></span>

<span data-ttu-id="2e12d-120">若要从头开始创建此项目，请首先创建一个 Visual Studio Code (VSCode) 项目。</span><span class="sxs-lookup"><span data-stu-id="2e12d-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="2e12d-121">使用 VSCode 不是强制要求，但为了方便起见，我们将在本教程中使用它。</span><span class="sxs-lookup"><span data-stu-id="2e12d-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="2e12d-122">更有经验的 JavaScript 开发人员可以使用他们选择的其他编辑器，即使是最简单的记事本也可以。</span><span class="sxs-lookup"><span data-stu-id="2e12d-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="2e12d-123">下载 [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 单个文件，或使用 [babylon.js 官方网站](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers)上提供的联机版本。</span><span class="sxs-lookup"><span data-stu-id="2e12d-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="2e12d-124">还可以从 [GitHub](https://github.com/BabylonJS/Babylon.js) 克隆整个 babylon.js 项目</span><span class="sxs-lookup"><span data-stu-id="2e12d-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="2e12d-125">创建一个空文件并将其另存为 html 页面，例如index.html</span><span class="sxs-lookup"><span data-stu-id="2e12d-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="2e12d-126">创建基本 html 标记并引用 babylon.js javascript 文件。</span><span class="sxs-lookup"><span data-stu-id="2e12d-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="2e12d-127">最终代码如下所示：</span><span class="sxs-lookup"><span data-stu-id="2e12d-127">The final code is as shown below:</span></span>

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

1. <span data-ttu-id="2e12d-128">在 body 中添加 canvas HTML 元素，以呈现 babylon.js 内容。</span><span class="sxs-lookup"><span data-stu-id="2e12d-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="2e12d-129">请注意，canvas 具有 id 属性，可让您稍后通过 JavaScript 访问此 HTML 元素。</span><span class="sxs-lookup"><span data-stu-id="2e12d-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

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

1. <span data-ttu-id="2e12d-130">canvas 占据整个网页。</span><span class="sxs-lookup"><span data-stu-id="2e12d-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="2e12d-131">网页到此就完成了。</span><span class="sxs-lookup"><span data-stu-id="2e12d-131">That completes our web page.</span></span> <span data-ttu-id="2e12d-132">现在，网页已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="2e12d-132">At this point, the web page is ready.</span></span> <span data-ttu-id="2e12d-133">您可以在任何浏览器中打开它，并确保没有显示任何错误，但目前还没有沉浸式体验。</span><span class="sxs-lookup"><span data-stu-id="2e12d-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2e12d-134">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2e12d-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e12d-135">下一教程：2. 准备场景</span><span class="sxs-lookup"><span data-stu-id="2e12d-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)