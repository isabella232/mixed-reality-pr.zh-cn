---
title: 允许在主页中放置 3D 模型
description: 如何在 Windows Mixed Reality 主页中放置网站或应用程序中的3D 模型
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D，模型，在家中放置，地方，世界，建模，混合现实主页，web，应用，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: ad35e1d010e32c4729b0d0dd58943dabdee86e09
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757805"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>允许在混合现实主页中放置 3D 模型

> [!NOTE]
> 此功能已作为 [Windows 10 2018 年4月更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)的一部分添加。 Windows 的较早版本与此功能不兼容。

[Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)是用户在启动应用程序之前居住的起点。 在某些情况下，二维应用 (如全息影像应用) 会将3D 模型直接置于混合现实主页中作为装饰，或以完整的3D 形式进行进一步检查。 使用 " *添加模型" 协议* ，可以将三维模型从你的网站或应用程序直接发送到 Windows Mixed Reality 主页，它将在其中持久保存，如 [3d 应用程序启动器](3d-app-launcher-design-guidance.md)、二维应用和全息影像。 

例如，如果您正在开发一个应用程序，该应用程序显示了用于设计空间的3D 家具目录，则使用 " *添加模型" 协议* 允许用户将这些3d 家具模型从目录中放置。 一旦进入世界，用户就可以移动、调整大小和删除这些3D 模型，就像在家中的其他全息影像一样。 本文概述了如何实现 *添加模型协议* ，使用户能够使用应用或 web 中的3d 对象装饰其世界。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>添加模型协议</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>概述

可以通过两个步骤在 Windows Mixed Reality 主页中启用3D 模型的放置：
1. [确保3d 模型与 Windows Mixed Reality 主页兼容](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。
2. 在应用程序或网页中实现 *添加模型协议* ， (本文) 。

## <a name="implementing-the-add-model-protocol"></a>实现 *添加模型协议*

获得 [兼容的3d 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)后，可以通过从任何网页或应用程序激活以下 URI 来实现 *添加模型协议* ：

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

如果 URI 指向远程资源，则它将自动下载并放置在主文件夹中。 本地资源将被复制到混合现实主页的应用数据文件夹中，然后放入 home。 建议在以下情况下设计你的体验：用户可能正在运行不支持此功能的较早版本的 Windows （如有可能）。 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>从通用 Windows 平台应用调用 *添加模型协议* ：

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>从网页调用 *添加模型协议* ：

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>沉浸式 (VR) 耳机注意事项

* 对于沉浸式 (VR) 耳机，在调用 *添加模型协议* 之前，混合现实门户无需运行。 在这种情况下，" *添加模型" 协议* 将启动混合现实门户，并将对象直接放置在头戴显示在混合现实中的位置。 
* 当在已运行混合现实门户的情况下从桌面调用 " *添加模型" 协议* 时，请确保头戴式耳机处于 "唤醒" 状态。 否则，放置不会成功。 

## <a name="see-also"></a>另请参阅

* [创建用于 Windows Mixed Reality 主页的3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [导航 Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)
