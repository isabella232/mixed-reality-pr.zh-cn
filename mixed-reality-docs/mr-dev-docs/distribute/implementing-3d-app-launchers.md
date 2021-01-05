---
title: 实现 3D 应用启动器（UWP 应用）
description: 如何创建适用于 Windows Mixed Reality UWP 应用和游戏的3D 应用启动器和徽标 (通过 Microsoft Store) ，同时在 HoloLens 和沉浸式 (VR) 耳机。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D，徽标，图标，建模，启动器，3D 启动器，磁贴，动态立方体，深层链接，secondarytile，辅助磁贴，UWP，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，XML，边界框，unity
ms.openlocfilehash: 38f0932f20e3660c91b87de7bcb9d66799d9a51a
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757490"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="d6ff3-104">实现 3D 应用启动器（UWP 应用）</span><span class="sxs-lookup"><span data-stu-id="d6ff3-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="d6ff3-105">此功能已作为2017秋季创意者更新的一部分添加 (了沉浸式头中的 RS3) ，并支持通过 Windows 10 4 月2018更新进行更新。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="d6ff3-106">请确保应用程序面向的是10.0.16299 的版本，Windows SDK 该版本大于或等于沉浸式耳机上的和10.0.17125 上的。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="d6ff3-107">可在 [此处](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="d6ff3-108">[Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)是用户在启动应用程序之前居住的起点。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-108">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="d6ff3-109">为 Windows Mixed Reality 创建 UWP 应用程序时，默认情况下，应用程序将以2D 清单启动，其应用的徽标。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="d6ff3-110">当开发 Windows Mixed Reality 体验时，可以根据需要定义3D 启动程序来覆盖应用程序的默认2D 启动器。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="d6ff3-111">一般情况下，建议使用三维启动器来启动使用户离开 Windows Mixed Reality 主页的沉浸式应用程序。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home.</span></span> <span data-ttu-id="d6ff3-112">就地激活应用时，首选的是默认的2D 启动器。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-112">The default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="d6ff3-113">你还可以创建一个 [3d 深层链接， (secondaryTile) ](#3d-deep-links-secondarytiles) 为 2d UWP 应用内的内容的三维启动器。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-113">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="d6ff3-114">3D 应用程序启动器创建过程</span><span class="sxs-lookup"><span data-stu-id="d6ff3-114">3D app launcher creation process</span></span>

<span data-ttu-id="d6ff3-115">创建三维应用启动器有三个步骤：</span><span class="sxs-lookup"><span data-stu-id="d6ff3-115">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="d6ff3-116">设计和 concepting</span><span class="sxs-lookup"><span data-stu-id="d6ff3-116">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="d6ff3-117">建模和导出</span><span class="sxs-lookup"><span data-stu-id="d6ff3-117">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="d6ff3-118">将其集成到你的应用程序中 (本文) </span><span class="sxs-lookup"><span data-stu-id="d6ff3-118">Integrating it into your application (this article)</span></span>

<span data-ttu-id="d6ff3-119">要用作应用程序启动器的3D 资产应使用 [Windows Mixed Reality 创作指南](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 进行创作，以确保兼容性。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-119">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="d6ff3-120">未能满足此创作规范的资产将不会在 Windows Mixed Reality 主页中呈现。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-120">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="d6ff3-121">配置3D 启动器</span><span class="sxs-lookup"><span data-stu-id="d6ff3-121">Configuring the 3D launcher</span></span>

<span data-ttu-id="d6ff3-122">当在 Visual Studio 中创建新项目时，它将创建显示应用名称和徽标的简单默认磁贴。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-122">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="d6ff3-123">若要将此2D 表示形式替换为自定义3D 模型，请编辑应用程序的应用程序清单，将 "MixedRealityModel" 元素作为默认磁贴定义的一部分包含在内。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-123">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="d6ff3-124">若要还原为2D 启动器，只需从清单中删除 MixedRealityModel 定义。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-124">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="d6ff3-125">XML</span><span class="sxs-lookup"><span data-stu-id="d6ff3-125">XML</span></span>

<span data-ttu-id="d6ff3-126">首先，在当前项目中找到应用程序包清单。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-126">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="d6ff3-127">默认情况下，该清单将命名为 appxmanifest.xml。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-127">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="d6ff3-128">如果使用的是 Visual Studio，请右键单击解决方案查看器中的清单，然后选择 " **查看源** " 以打开要编辑的 xml。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-128">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="d6ff3-129">在清单的顶部，添加 uap5 架构，并将其包含为可忽略的命名空间：</span><span class="sxs-lookup"><span data-stu-id="d6ff3-129">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="d6ff3-130">接下来，在应用程序的默认磁贴中指定 "MixedRealityModel"：</span><span class="sxs-lookup"><span data-stu-id="d6ff3-130">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="d6ff3-131">MixedRealityModel 元素接受指向存储在应用包中的3D 资产的文件路径。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-131">The MixedRealityModel element accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="d6ff3-132">目前仅支持使用 glb 文件格式交付并针对 [Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 创作的3d 模型。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-132">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="d6ff3-133">资产必须存储在应用包中，且当前不支持动画。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-133">Assets must be stored in the app package and animation isn't currently supported.</span></span> <span data-ttu-id="d6ff3-134">如果 "Path" 参数保留为空，则 Windows 将显示2D 盖板而不是3D 启动器。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-134">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="d6ff3-135">**注意：** 生成和运行应用之前，必须在生成设置中将 glb 资产标记为 "内容"。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-135">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="d6ff3-136">![在解决方案资源管理器中选择 glb，并使用 properties 节将其标记为生成设置中的 "Content"](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="d6ff3-136">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="d6ff3-137">*在解决方案资源管理器中选择 glb，并使用 properties 节将其标记为生成设置中的 "Content"*</span><span class="sxs-lookup"><span data-stu-id="d6ff3-137">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="d6ff3-138">边界框</span><span class="sxs-lookup"><span data-stu-id="d6ff3-138">Bounding box</span></span>

<span data-ttu-id="d6ff3-139">边界框可用于根据需要在对象周围添加额外的缓冲区区域。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-139">A bounding box can be used to optionally add an extra buffer region around the object.</span></span> <span data-ttu-id="d6ff3-140">边界框是使用中心点和范围指定的，它们表示从边界框的中心到沿每个轴的边缘之间的距离。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-140">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="d6ff3-141">边界框的单位可以映射到1个 unit = 1 个计量器。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-141">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="d6ff3-142">如果未提供边界框，则会自动将一个边界框拟合到对象的网格中。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-142">If a bounding box isn't provided, then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="d6ff3-143">如果提供的边界框小于模型，则将调整其大小以适合网格。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-143">If the provided bounding box is smaller than the model, then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="d6ff3-144">对范围框属性的支持将作为 MixedRealityModel 元素上的属性提供给 Windows RS4 更新。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-144">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="d6ff3-145">若要首先在应用程序清单顶部定义边界框，请添加 uap6 架构，并将其包含为可忽略的命名空间：</span><span class="sxs-lookup"><span data-stu-id="d6ff3-145">To define a bounding box first at the top of the app manifest add the uap6 schema and include it as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="d6ff3-146">接下来，在 MixedRealityModel 上，将 SpatialBoundingBox 属性设置为定义边界框：</span><span class="sxs-lookup"><span data-stu-id="d6ff3-146">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="d6ff3-147">使用 Unity</span><span class="sxs-lookup"><span data-stu-id="d6ff3-147">Using Unity</span></span>

<span data-ttu-id="d6ff3-148">使用 Unity 时，必须先在 Visual Studio 中生成和打开项目，然后才能编辑应用程序清单。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-148">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="d6ff3-149">在从 Unity 生成和部署新的 Visual Studio 解决方案时，必须在清单中重新定义3D 启动程序。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-149">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="d6ff3-150"> (secondaryTiles) 的3D 深层链接</span><span class="sxs-lookup"><span data-stu-id="d6ff3-150">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="d6ff3-151">此功能已作为2017秋季创意者更新的一部分添加 (用于沉浸式 (VR) 耳机的 RS3) 和年4月2018更新 (RS4) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-151">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="d6ff3-152">请确保应用程序面向的是 Windows SDK 大于或等于10.0.17125 上的)  (10.0.16299 的版本。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-152">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="d6ff3-153">可在 [此处](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-153">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="d6ff3-154"> (secondaryTiles 的3D 深层链接) 仅适用于 2D UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-154">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="d6ff3-155">不过，你可以创建一个 [3d 应用启动器](implementing-3d-app-launchers.md) ，从 Windows Mixed Reality 主页启动一个独占应用。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-155">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="d6ff3-156">您的2D 应用程序可以通过添加将3D 模型从应用置于 [Windows Mixed reality 主页](../discover/navigating-the-windows-mixed-reality-home.md) 中来增强 Windows mixed reality，就像 Windows "开始" 菜单上的 [2d 辅助磁贴](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) 一样。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-156">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="d6ff3-157">例如，你可以创建360° photospheres，它直接链接到360°照片查看器应用，或让用户从一组资产中放置3D 内容，以便打开有关作者的详细信息页。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-157">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="d6ff3-158">这只是使用三维内容展开2D 应用程序功能的几种方法。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-158">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="d6ff3-159">创建三维 "secondaryTile"</span><span class="sxs-lookup"><span data-stu-id="d6ff3-159">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="d6ff3-160">可以通过在创建时定义混合现实模型，使用 "secondaryTiles" 从应用程序中放置3D 内容。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-160">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="d6ff3-161">混合现实模型是通过引用应用包中的3D 资产创建的，还可以选择定义边界框。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-161">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="d6ff3-162">当前不支持在排他视图内创建 "secondaryTiles"。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-162">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="d6ff3-163">边界框</span><span class="sxs-lookup"><span data-stu-id="d6ff3-163">Bounding box</span></span>

<span data-ttu-id="d6ff3-164">边界框可用于在对象周围添加额外的缓冲区区域。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-164">A bounding box can be used to add an extra buffer region around the object.</span></span> <span data-ttu-id="d6ff3-165">边界框是使用中心点和范围指定的，它们表示从边界框的中心到沿每个轴的边缘之间的距离。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-165">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="d6ff3-166">边界框的单位可以映射到1个 unit = 1 个计量器。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-166">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="d6ff3-167">如果未提供边界框，则会自动将一个边界框拟合到对象的网格中。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-167">If a bounding box isn't provided, one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="d6ff3-168">如果提供的边界框小于模型，则将调整其大小以适应网格。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-168">If the provided bounding box is smaller than the model, it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="d6ff3-169">激活行为</span><span class="sxs-lookup"><span data-stu-id="d6ff3-169">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="d6ff3-170">Windows RS4 更新将支持此功能。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-170">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="d6ff3-171">如果计划使用此功能，请确保应用程序面向的 Windows SDK 版本大于或等于10.0.17125</span><span class="sxs-lookup"><span data-stu-id="d6ff3-171">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="d6ff3-172">您可以定义三维 secondaryTile 的激活行为，以控制用户选择它时其反应方式。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-172">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="d6ff3-173">这可用于将三维对象置于纯信息性或装饰性的混合现实主页中。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-173">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="d6ff3-174">支持以下激活行为类型：</span><span class="sxs-lookup"><span data-stu-id="d6ff3-174">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="d6ff3-175">默认值：用户选择 3D secondaryTile 时，会激活应用</span><span class="sxs-lookup"><span data-stu-id="d6ff3-175">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="d6ff3-176">无：当用户选择三维 secondaryTile 时，不会执行任何操作，并且不会激活应用程序。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-176">None: When the user selects the 3D secondaryTile nothing happens and the app isn't activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="d6ff3-177">获取和更新现有 "secondaryTile"</span><span class="sxs-lookup"><span data-stu-id="d6ff3-177">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="d6ff3-178">开发人员可以返回其现有辅助磁贴的列表，其中包括前面指定的属性。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-178">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="d6ff3-179">它们还可以通过更改值，然后调用 UpdateAsync ( # A1 来更新属性。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-179">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="d6ff3-180">正在检查用户是否处于 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d6ff3-180">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="d6ff3-181">只有在 Windows Mixed Reality 耳机中显示视图时，才能创建 (secondaryTiles) 的3D 深层链接。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-181">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="d6ff3-182">如果未在 Windows Mixed Reality 耳机中显示你的视图，我们建议通过隐藏输入点或显示错误消息来处理此问题。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-182">When your view isn't being presented in a Windows Mixed Reality headset, we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="d6ff3-183">可以通过查询 [IsCurrentViewPresentedOnHolographic ( # B1 ](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)来检查此情况。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-183">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="d6ff3-184">磁贴通知</span><span class="sxs-lookup"><span data-stu-id="d6ff3-184">Tile notifications</span></span>

<span data-ttu-id="d6ff3-185">磁贴通知当前不支持使用三维资产发送更新。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-185">Tile notifications don't currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="d6ff3-186">这意味着开发人员不能执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d6ff3-186">This means that developers can't do the following:</span></span>

* <span data-ttu-id="d6ff3-187">推送通知</span><span class="sxs-lookup"><span data-stu-id="d6ff3-187">Push Notifications</span></span>
* <span data-ttu-id="d6ff3-188">定期轮询</span><span class="sxs-lookup"><span data-stu-id="d6ff3-188">Periodic Polling</span></span>
* <span data-ttu-id="d6ff3-189">计划的通知</span><span class="sxs-lookup"><span data-stu-id="d6ff3-189">Scheduled Notifications</span></span>

<span data-ttu-id="d6ff3-190">有关其他磁贴功能和属性以及它们如何用于2D 磁贴的详细信息，请参阅 [UWP 应用的磁贴文档](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-190">For more information on the other tiles features and attributes and how they're used for 2D tiles, see the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6ff3-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6ff3-191">See also</span></span>

* <span data-ttu-id="d6ff3-192">包含三维应用程序启动器的[混合现实模型示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。</span><span class="sxs-lookup"><span data-stu-id="d6ff3-192">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="d6ff3-193">3D 应用启动器设计指南</span><span class="sxs-lookup"><span data-stu-id="d6ff3-193">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="d6ff3-194">创建用于 Windows Mixed Reality 主页的3D 模型</span><span class="sxs-lookup"><span data-stu-id="d6ff3-194">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="d6ff3-195"> (Win32 应用程序上实现3D 应用程序启动器) </span><span class="sxs-lookup"><span data-stu-id="d6ff3-195">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="d6ff3-196">导航 Windows Mixed Reality 主页</span><span class="sxs-lookup"><span data-stu-id="d6ff3-196">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
