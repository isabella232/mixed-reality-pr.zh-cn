---
ms.openlocfilehash: d811df7f0dbd7c44a5135ed82c9061e19c1335e3e23dda6398562317f7ee8861
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198776"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

如果有一个HoloLens，[请从下表](../distribute-overview.md#distribution-options)中选择首选的分发选项。 如果要发布到应用Microsoft Store，可以选择添加应用内[购买，使](../in-app-purchases.md)内容盈利。

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

如果正在处理面向设备头戴显示设备Windows Mixed Reality沉浸式应用程序，请创建一个 3D 应用启动器，然后从下表[中选择首选的](../distribute-overview.md#distribution-options)分发选项。 如果要发布到应用Microsoft Store，可以选择添加应用内[购买，使](../in-app-purchases.md)内容盈利。

### <a name="designing-3d-app-launchers-for-vr"></a>为 VR 设计 3D 应用启动器 

3D 应用启动器在 Windows Mixed Reality环境中显示为对象，每当用户放在沉浸式头戴显示设备时，都会显示这些对象。 这些对象是根据需要创建和自定义的对象，但建议你从我们的设计指南一文开始，获取良好的设计[](../3d-app-launcher-design-guidance.md)做法的挂起，包括缩放、类型、颜色选择、文本，最重要的是使其在虚拟环境中突出。

### <a name="modeling-and-exporting-3d-app-launchers"></a>建模和导出 3D 应用启动器

确定 3D 应用启动器的想法后，需要确保它满足 Microsoft Store 要求，包括资产文件格式、三角形计数、纹理大小、动画长度和资产优化。 此过程可能是高度技术的过程，因此我们建议使用 [三维模型](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 创建一文来选中所有框。 不符合此创作规范的资产不会在主Windows Mixed Reality呈现。

### <a name="adding-3d-app-launchers-in-your-apps"></a>在应用中添加 3D 应用启动器

确保 3D 应用启动器符合 Windows Mixed Reality 创作准则后，可以使用它替代 Windows Mixed Reality 家庭环境中应用程序的默认 2D 启动器。 将 3D 应用启动器集成到应用程序的过程取决于正在开发的应用程序类型：

* [UWP 应用](../implementing-3d-app-launchers.md)
* [Win32 应用](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>[可选]将 3D 模型放置在Windows Mixed Reality中

作为额外的好处，某些 2D 应用程序允许将 3D 模型直接放在Windows Mixed Reality作为修饰或进一步检查整个 3D 中。 通过添加模型协议，可以将 3D 模型从网站或应用程序发送到 Windows Mixed Reality 主页，该模型将持久保存，例如 3D 应用启动器、2D 应用和全息影像。 了解如何[将 3D](../enable-placement-of-3d-models-in-the-home.md)模型Windows Mixed Reality主页中，以查找有关如何运行自己的应用的更多详细信息和说明。