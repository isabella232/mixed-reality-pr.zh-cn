---
ms.openlocfilehash: c9ce068adc3b4b550ecaf1b1c106d9b12f363ac0
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443516"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

如果有一个 HoloLens 应用程序，请从下表中选择首选的 [分发选项](../distribute-overview.md#distribution-options) 。 如果要发布到 Microsoft Store，可以选择添加 [应用内购买](../in-app-purchases.md) ，以盈利内容。

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

如果使用面向 Windows Mixed Reality 耳机的沉浸式应用程序，请创建一个三维应用启动器，然后从下表中选择首选的 [分发选项](../distribute-overview.md#distribution-options) 。 如果要发布到 Microsoft Store，可以选择添加 [应用内购买](../in-app-purchases.md) ，以盈利内容。

### <a name="designing-3d-app-launchers-for-vr"></a>设计用于 VR 的3D 应用启动器 

3D 应用启动器在 Windows Mixed Reality 主环境中显示为对象，只要用户进入沉浸式耳机就会出现。 您可以使用这些对象来创建和自定义，但建议您从 [设计指南](../3d-app-launcher-design-guidance.md) 文章开始，以获取良好的设计实践（包括缩放、类型、颜色选择、纹理等），并使其在虚拟环境中突出显示。

### <a name="modeling-and-exporting-3d-app-launchers"></a>建模和导出3D 应用启动器

针对3D 应用启动器设置好后，需确保它满足 Microsoft Store 要求，包括资产文件格式、三角形计数、纹理大小、动画长度和资产优化。 此过程可能是高度技术性的，因此我们建议使用 [三维模型创建](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 文章来检查所有的框。 不符合此创作规范的资产不会呈现在 Windows Mixed Reality 主页中。

### <a name="adding-3d-app-launchers-in-your-apps"></a>在应用程序中添加3D 应用启动器

确保3D 应用启动器满足 Windows Mixed Reality 创作准则后，可用于在 Windows Mixed Reality home 环境中覆盖应用程序的默认2D 启动器。 将三维应用程序启动器集成到应用程序的过程取决于要开发的应用程序类型：

* [UWP 应用](../implementing-3d-app-launchers.md)
* [Win32 应用](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>可有可无在 Windows Mixed Reality 主页中放置3D 模型

作为额外的优点，某些2D 应用程序允许您将3D 模型直接置于 Windows Mixed Reality 主主页中作为装饰或进行进一步检查。 使用 "添加模型" 协议，可以将三维模型从网站或应用程序发送到 Windows Mixed Reality 主页，在该模型中，它将持久保存，如3D 应用程序启动器、二维应用和全息影像。 请查看 [如何在 Windows Mixed Reality 主页中放置3d 模型](../enable-placement-of-3d-models-in-the-home.md) ，以了解更多详细信息和有关如何使自己的应用实现生动的说明。