---
title: 允许在主页中放置 3D 模型
description: 了解如何将来自网站或应用程序的 3D 模型放在Windows Mixed Reality主页。
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D， 模型， 放在家庭， 位置， 世界， 建模， 混合现实主页， Web， 应用， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: 29761cb2a8725221a3be90187488cb13bf6643e4ff334a1edca73e633e7b1d4c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186793"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>允许在混合现实主页中放置 3D 模型

> [!NOTE]
> 此功能已作为[2018](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)年 4 月更新 Windows 10的一部分添加。 旧版本的 Windows与此功能不兼容。

Windows Mixed Reality[主页](../discover/navigating-the-windows-mixed-reality-home.md)是用户启动应用程序之前登录的起点。 在某些情况下，2D 应用 (例如 全息影像 应用) 将 3D 模型作为修饰直接放置到 混合现实主页 中，或者用于进一步检查整个 3D。 通过 *添加模型* 协议，你可以将 3D 模型从网站或应用程序直接发送到 Windows Mixed Reality 主页，它将像 [3D](3d-app-launcher-design-guidance.md)应用启动器、2D 应用和全息影像一样持久保存。 

例如，如果要开发一个应用程序来显示用于设计空间的 3D 装饰件目录，请使用 *添加* 模型协议允许用户从目录中放置这些 3D 装饰模型。 进入世界后，用户可以像在家庭的其他全息影像一样移动、调整和删除这些 3D 模型。 本文概述了如何实现添加 *模型* 协议，使用户能够使用应用或 Web 中的 3D 对象修饰他们的世界。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>添加模型协议</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>基础知识

在主Windows Mixed Reality三维模型的位置：
1. [确保 3D 模型与主](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)Windows Mixed Reality兼容。
2. 在 *应用程序或网页中* 实现添加模型协议 (本文) 。

## <a name="implementing-the-add-model-protocol"></a>实现 *添加模型协议*

拥有兼容的[3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)后，可以通过从任何网页或应用程序激活以下 URI 来实现添加模型协议：

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

如果 URI 指向远程资源，则会自动下载该资源并放置在主页中。 本地资源将复制到混合现实主页应用数据文件夹，然后再放置在主页中。 建议设计体验，以考虑用户可能运行不支持此功能的较旧版本 Windows（如果可能，请隐藏按钮或禁用此功能）。 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>从通用 *平台应用调用* Windows协议：

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>从网页 *调用添加* 模型协议：

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>沉浸式 VR (头戴显示) 注意事项

* 对于沉浸 (VR) 头戴显示设备，混合现实门户调用添加模型协议 之前，不必运行 *设备*。 在这种情况下，添加 *模型* 协议将启动 混合现实门户，在到达设备后直接将对象放在头戴显示设备混合现实主页。 
* 从桌面调用 *添加模型协议* 时，如果混合现实门户，请确保头戴显示设备处于"唤醒"状态。 如果没有，则放置不会成功。 

## <a name="see-also"></a>另请参阅

* [创建 3D 模型以在Windows Mixed Reality使用](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [导航 Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)