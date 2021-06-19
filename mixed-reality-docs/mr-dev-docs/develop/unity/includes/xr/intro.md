---
ms.openlocfilehash: ca3589364fb27c3f8087572113f09e48d30e087e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394571"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

混合现实 OpenXR 插件 **是 Microsoft** 针对 Unity 2020 LTS 或更高版本的建议。 随着将来开发新功能，它们只会包含在混合现实 OpenXR 插件中。

混合现实 OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。 这样，你可以编写一次光线广播代码，该代码HoloLens 2 ARCore/ARKit 手机和平板电脑。

### <a name="prerequisites"></a>先决条件 

* 用于 [开发HoloLens 2工具](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* 最新的 Unity 2020.3 LTS， (2020.3.8f1 或) 

### <a name="minimum-versions"></a>最低版本

本页中的说明将设置下面列出的最新、最大的 Unity 和 OpenXR 要求：

* 最新的 Unity OpenXR 插件， (1.2 或更高版本) 
* 最新的混合现实 OpenXR 插件， (版本 1.0.0 或更高版本) 
* **(可选)** 建议使用最新的 MRTK (2.7 或更高版本) 
* **(可选)** 最新的通用呈现管道包， (版本 10.5.1 或更高版本) 

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> 如果要在 Windows 电脑上生成 VR 应用程序，则混合现实 OpenXR 插件不一定是必需的。 但是，如果要为 HP Reverb G2 控制器自定义控制器映射，或构建适用于 HOLOLENS 2 和 VR 头戴显示设备的应用，需要安装插件。

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft 不建议将 Windows XR 插件用于 Unity 2020 中任何新项目。

但是，如果使用的是 Unity 2019，并且需要 AR Foundation 2.0 来与 ARCore/ARKit 设备兼容，则此插件会启用该支持。

> [!IMPORTANT]
> 在 Unity 2019 中使用此插件不支持 Azure 空间定位点。 

# <a name="legacy-xr"></a>[旧版 XR](#tab/legacy)

如果你仍在使用 Unity 2019 或更早版本，Microsoft 建议使用旧版内置 XR 支持。 虽然 Windows XR 插件在 Unity 2019 上正常运行，但不建议这样做，因为不支持 Azure 空间定位点。