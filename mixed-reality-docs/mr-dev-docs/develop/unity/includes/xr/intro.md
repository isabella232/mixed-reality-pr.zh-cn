---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906935"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Mixed Reality OpenXR 插件是 Microsoft 针对 Unity 2020 LTS 或更高版本的 **建议** 。 随着将来开发新功能，这些新功能将仅包括在混合现实 OpenXR 插件中。

Mixed Reality OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。 这样一来，你就可以编写 raycasting 代码一次，然后跨 HoloLens 2 和 ARCore/ARKit 手机和平板电脑。

### <a name="prerequisites"></a>先决条件 

* [适用于 HoloLens 2 开发的](../../../install-the-tools.md?tabs=unity#installation-checklist)最新工具
* 最新 Unity 2020.3 LTS， (建议 2020.3.8 f1 或更高版本) 

### <a name="minimum-versions"></a>最低版本

此页中的说明将设置以下列出的最新和最大 Unity 和 OpenXR 要求：

* 最新 Unity OpenXR 插件 (建议1.2 或更高版本) 
* 最新混合现实 OpenXR 插件， (建议1.0.0 版或更高版本) 
* **(可选)** 最新 MRTK， (建议2.7 版或更高版本) 
* **(可选)** 最新的通用呈现管道包， (建议10.5.1 或更高版本) 

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> 如果要在 Windows 电脑上构建 VR 应用程序，则不一定需要混合现实 OpenXR 插件。 但是，如果要自定义 HP 回音 G2 控制器的控制器映射，或生成在 HoloLens 2 和 VR 耳机上都适用的应用，则需要安装该插件。

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft 不建议对 Unity 2020 中的任何新项目使用 Windows XR 插件。

但是，如果你使用的是 Unity 2019，并且需要 AR Foundation 2.0 才能兼容 ARCore/ARKit 设备，此插件会启用该支持。

> [!IMPORTANT]
> 在 Unity 2019 中使用此插件不支持 Azure 空间锚。 

# <a name="legacy-xr"></a>[旧版 XR](#tab/legacy)

如果你仍在 Unity 2019 或更早版本，Microsoft 建议使用旧的内置 XR 支持。 尽管 Windows XR 插件在 Unity 2019 上正常运行，但不建议这样做，因为不支持 Azure 空间锚。