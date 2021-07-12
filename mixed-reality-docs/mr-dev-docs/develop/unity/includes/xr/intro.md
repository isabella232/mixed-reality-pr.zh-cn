---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603701"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

混合现实 OpenXR 插件 **是 Microsoft** 针对 **Unity 2020 LTS 或** 更高版本的建议。 随着将来开发新功能，它们只会包含在混合现实 OpenXR 插件中。

混合现实 OpenXR 插件完全支持 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 实现。 这样，你可以编写一次光线广播代码，该代码HoloLens 2 ARCore/ARKit 手机和平板电脑。

### <a name="prerequisites"></a>先决条件 

* 用于[开发HoloLens 2工具](../../../install-the-tools.md?tabs=unity#installation-checklist)
* 最新 Unity 2020.3 LTS：版本 2020.3.8f1 或更高版本

### <a name="recommended-package-versions"></a>建议的包版本

本页中的说明将设置核心 Unity OpenXR 包，这些包HoloLens 2或Windows Mixed Reality应用：

* Unity OpenXR 插件：版本 1.2 或更高版本
* 混合现实 OpenXR 插件：版本 1.0.0 或更高版本

如果在项目中使用以下包，则需要确保至少使用下面列出的最低版本：

* MRTK：版本 2.7.2 或更高版本
* AR Foundation：版本 4.1.1 或更高版本
* URP (通用) 管道：版本 10.5.1 或更高版本
* Azure 空间定位点：版本 2.10 或更高版本
* Azure 远程渲染：版本 1.0.15 或更高版本

> [!NOTE]
> 如果要在电脑上生成 VR Windows，则不严格要求使用混合现实 OpenXR 插件。 但是，如果要为 HP Reverb G2 控制器设置输入绑定，或构建在 HOLOLENS 2 和 VR 头戴显示设备上运行的应用，需要安装插件。

# <a name="windows-xr"></a>[WindowsXR](#tab/windowsxr)

Microsoft 不建议将 Windows XR 插件用于 Unity 2020 中的任何新项目。  应改为使用混合现实 OpenXR 插件。

但是，如果使用的是 Unity 2019，并且需要 AR Foundation 2.0 来与 ARCore/ARKit 设备兼容，则此插件会启用该支持。

> [!IMPORTANT]
> 在 Unity 2019 中使用此插件与 Azure 空间定位点不兼容。

# <a name="legacy-xr"></a>[旧版 XR](#tab/legacy)

如果你仍在使用 Unity **2019** 或更早版本，Microsoft 建议使用旧版 **内置 XR 支持**。

虽然 Windows XR 插件在 Unity 2019 上正常运行，但不建议这样做，因为此插件与 Unity 2019 上的 Azure 空间定位点不兼容。

如果要启动新项目，建议改为安装 [Unity 2020，](../../choosing-unity-version.md) 然后使用混合现实 OpenXR 插件。