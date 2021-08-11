---
title: 实现 3D 应用启动器（UWP 应用）
description: 了解如何在显示器和 VR 头戴显示设备上为 Windows Mixed Reality UWP 应用和游戏创建 3D HoloLens和徽标。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D， 徽标， 图标， 建模， 启动器， 3D 启动器， 磁贴， 实时多维数据集， 深层链接， 辅助磁贴， 辅助磁贴， UWP， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， XML， 边界框， unity
ms.openlocfilehash: b0ccff2aaba9c4693f58b134cdb3af9190b59befec0b31851273ed6a3bc1fc04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196414"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>实现 3D 应用启动器（UWP 应用）

> [!NOTE]
> 此功能已作为沉浸式头戴显示设备 2017 Fall Creators Update (RS3) 的一部分添加，并且由 HoloLens 通过 Windows 10 2018 年 4 月更新获得支持。 确保应用程序面向的 Windows SDK 版本大于或等于沉浸式头戴显示设备上的 10.0.16299 和 HoloLens 上的 10.0.17125。 可在此处找到最新的 Windows [SDK。](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

Windows Mixed Reality[主页](../discover/navigating-the-windows-mixed-reality-home.md)是用户启动应用程序之前登录的起点。 为应用创建 UWP Windows Mixed Reality，默认情况下，应用会以 2D 板和其应用徽标启动。 开发用于Windows Mixed Reality体验时，可以选择定义 3D 启动器来替代应用程序的默认 2D 启动器。 通常，建议使用 3D 启动器来启动将用户从Windows Mixed Reality应用程序。 当应用就地激活时，首选默认的 2D 启动器。 还可以在 [secondaryTile ](#3d-deep-links-secondarytiles) (创建 3D 深层链接) 作为 2D UWP 应用中内容的 3D 启动器。

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D 应用启动器创建过程

创建 3D 应用启动器有三个步骤：
1. [设计和概念](3d-app-launcher-design-guidance.md)
2. [建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 本文 (将其集成到) 

要用作应用程序的启动器的 3D 资产应该使用 Windows Mixed Reality[创作](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)指南进行创作，以确保兼容性。 不符合此创作规范的资产不会在主Windows Mixed Reality呈现。

## <a name="configuring-the-3d-launcher"></a>配置 3D 启动器

当在 Visual Studio 中创建新项目时，它将创建显示应用名称和徽标的简单默认磁贴。 若要将此 2D 表示形式替换为自定义 3D 模型，请编辑应用程序的应用清单，以在默认磁贴定义中包括"MixedRealityModel"元素。 若要还原到 2D 启动器，只需从清单中删除 MixedRealityModel 定义。

### <a name="xml"></a>XML

首先，在当前项目中找到应用包清单。 默认情况下，清单将命名为 Package.appxmanifest。 如果使用的是Visual Studio，请右键单击解决方案查看器中的清单，然后选择"查看源"以打开 xml进行编辑。 

在清单顶部，添加 uap5 架构，并包含为可忽略的命名空间：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

接下来，在应用程序的默认磁贴中指定"MixedRealityModel"：

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

MixedRealityModel 元素接受指向应用包中存储的 3D 资产的文件路径。 目前仅支持使用 .glb 文件格式交付的 3D 模型，Windows Mixed Reality [3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)资产创作说明进行创作。 资产必须存储在应用包中，当前不支持动画。 如果"Path"参数留空Windows将显示 2D 板，而不是 3D 启动器。 **注意：** 生成和运行应用之前，必须在生成设置中将 .glb 资产标记为"内容"。


![在解决方案资源管理器中选择 .glb，并使用"属性"部分在生成设置中将其标记为"内容"](images/buildsetting-content-300px.png)<br>
*在解决方案资源管理器中选择 .glb，并使用"属性"部分在生成设置中将其标记为"内容"*

### <a name="bounding-box"></a>边界框

边界框可用于选择性地在 对象周围添加额外的缓冲区区域。 边界框是使用中心点和区指定的，该点和范围指示从边界框的中心到沿每个轴的边缘的距离。 边界框的单位可以映射到 1 个单位 = 1 米。 如果未提供边界框，则会自动将边界框拟合到对象的网格。 如果提供的边界框小于模型，则它将调整大小以适应网格。

对边界框属性的支持将随 RS4 Windows作为 MixedRealityModel 元素上的属性提供。 若要首先在应用清单顶部定义边界框，请添加 uap6 架构，并包含为可忽略的命名空间：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
接下来，在 MixedRealityModel 上设置 SpatialBoundingBox 属性以定义边界框： 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>使用 Unity

使用 Unity 时，必须先在 Visual Studio中生成和打开项目，然后才能编辑应用清单。 

>[!NOTE]
>从 Unity 生成和部署新的 Visual Studio解决方案时，必须在清单中重新定义 3D 启动器。

## <a name="3d-deep-links-secondarytiles"></a>辅助数据库的 3D (链接) 

> [!NOTE]
> 此功能已作为沉浸式 (VR) 头戴显示设备 2017 Fall Creators Update (RS3) 的一部分添加，并作为 HoloLens 的 2018 年 4 月更新 (RS4) 的一部分添加。 确保应用程序面向沉浸式 (VR) 头戴显示设备上大于或等于 10.0.16299 的 Windows SDK 版本，以及 HoloLens 上的 10.0.17125。 可在此处找到最新的 Windows [SDK。](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

>[!IMPORTANT]
>辅助数据库的 3D (链接) 仅适用于 2D UWP 应用。 但是，可以创建一个[3D 应用启动器](implementing-3d-app-launchers.md)，从用户主页启动Windows Mixed Reality应用。

通过添加将 Windows Mixed Reality 3D 模型从应用放置到[Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)主页的能力，可以增强 2D 应用程序的 2D 应用程序，作为指向 2D 应用中内容的深层链接，就像在 Windows "开始"菜单 上放置[2D](/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles)辅助磁贴一样。 例如，可以创建直接链接到 360° 照片查看器应用的 360° 照片圈，或允许用户放置资产集合中的 3D 内容，以打开有关作者的详细信息页。 这些只是使用 3D 内容扩展 2D 应用程序功能的几种方法。

### <a name="creating-a-3d-secondarytile"></a>创建 3D"secondaryTile"

可以在创建时定义混合现实模型，使用"secondaryTiles"从应用程序放置 3D 内容。 混合现实模型通过引用应用包中的 3D 资产并选择性地定义边界框创建。 

> [!NOTE]
> 目前不支持从独占视图内创建"secondaryTiles"。

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

### <a name="bounding-box"></a>边界框

边界框可用于在 对象周围添加额外的缓冲区区域。 边界框是使用中心点和区指定的，该点和范围指示从边界框的中心到沿每个轴的边缘的距离。 边界框的单位可以映射到 1 个单位 = 1 米。 如果未提供边界框，则会自动将边界框拟合到对象的网格中。 如果提供的边界框小于模型，将调整其大小以适应网格。

### <a name="activation-behavior"></a>激活行为

> [!NOTE]
> 自 RS4 更新发布起，Windows此功能。 如果计划使用此功能，请确保应用程序面向的 Windows SDK 版本大于或等于 10.0.17125

可以定义 3D 辅助数据库的激活行为，以控制用户选择它时其响应方式。 这可用于将 3D 对象放在混合现实主页中，这些对象只是信息性或装饰性。 支持以下激活行为类型：
1. 默认值：当用户选择 3D 辅助数据库时激活应用
2. 无：当用户选择 3D 辅助数据库时，不会执行任何操作，并且应用未激活。

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>获取和更新现有"secondaryTile"

开发人员可以返回其现有辅助磁贴的列表，其中包括他们之前指定的属性。 它们还可以通过更改值，然后调用 UpdateAsync () 。

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>检查用户是否位于Windows Mixed Reality

辅助设备 (3D 深层链接) 仅在视图显示在设备头戴显示设备中时Windows Mixed Reality链接。 如果视图未显示在头戴显示设备Windows Mixed Reality，建议通过隐藏入口点或显示错误消息来正常处理这种情况。 可以通过查询[IsCurrentViewPresentedOnHolographic () 。 ](/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)

## <a name="tile-notifications"></a>磁贴通知

磁贴通知当前不支持使用 3D 资产发送更新。 这意味着开发人员无法执行以下操作：

* 推送通知
* 定期轮询
* 计划通知

有关其他磁贴功能和属性及其如何用于 2D 磁贴的信息，请参阅 [适用于 UWP 应用的磁贴文档](/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。

## <a name="see-also"></a>另请参阅

* [包含 3D](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) 应用启动器的混合现实模型示例。
* [3D 应用启动器设计指南](3d-app-launcher-design-guidance.md)
* [创建 3D 模型以在Windows Mixed Reality使用](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [在 Win32 应用中 (3D 应用启动) ](implementing-3d-app-launchers-win32.md)
* [导航 Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)