---
ms.openlocfilehash: 481a063cac3cb4d7e5ef7521ad19af43cb68e2cf
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110630744"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[MRTK 的配置对话框](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) 将尝试设置 XR SDK 和旧 WSA 的深度缓冲区设置，但最好检查这些选项卡并验证 Unity 中的设置。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

设置 Unity 应用是否将向 Windows 提供深度缓冲区：

1. 请参阅 **编辑**  >  **项目设置**  >  **XR 插件管理**，并确保展开菜单项。
2. 单击与所选 XR 运行时对应的菜单项，即 "Windows Mixed Reality" 或 "OpenXR"。 此外，请确保选择了正确的生成平台，作为 Windows 独立版和通用 Windows 平台的选项卡可用。
3. 若要启用和配置：
    1. 对于 OpenXR，请在 " **深度提交模式** " 下拉列表中选择 "深度格式" 或 "无"。
    2. 对于 Windows Mixed Reality，选中或取消选中 " **共享深度缓冲区** " 复选框。 然后，从 " **深度缓冲区格式** " 下拉列表中选择一种格式。

![Windows XR 插件深度设置 ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR 深度设置](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> 通常建议使用16位深度缓冲区来提高性能。 但是，如果使用16位深度格式，模具缓冲区所需效果 (如某些 Unity UI 滚动面板) 将不起作用，因为 Unity 不会在此设置中 [创建模具缓冲区](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。 相反，选择 *24 位深度格式* 通常会在端点图形平台上创建 [8 位模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html) 。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

设置 Unity 应用是否将向 Windows 提供深度缓冲区：

1. 请参阅 **编辑**  >  **项目设置**  >  **播放器**  >  **通用 Windows 平台选项卡**  >  **XR 设置**。
2. 展开 " **Windows Mixed REALITY SDK** " 项。
3. 选中或取消选中 " **启用深度缓冲共享** " 复选框。 默认情况下，在新项目中选中 "启用深度缓冲区共享"，但默认情况下，在较旧的项目中可能未选中。

![旧 XR 深度设置](../../images/wmr-depth.png)

深度缓冲区可以提高视觉质量，只要 Windows 可以使用在主摄像机上的 Unity 中设置的近和远的平面，将深度缓冲区中的规范化每像素深度值准确地映射回以米为单位的距离。 如果您的呈现器通过使用典型的方式来处理深度值，则通常情况下，您应该非常好，但是，在显示到现有颜色像素时，写入深度缓冲区的半透明渲染传递可能会混淆 reprojection。  如果你知道，你的 render pass 会使很多最终深度像素具有不准确的深度值，则你可能会通过取消选中 "启用深度缓冲区共享" 获得更好的视觉质量。

> [!NOTE]
> 通常建议使用16位深度缓冲区来提高性能。 但是，如果使用16位深度格式，模具缓冲区所需效果 (如某些 Unity UI 滚动面板) 将不起作用，因为 Unity 不会在此设置中 [创建模具缓冲区](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。 相反，选择 *24 位深度格式* 通常会在端点图形平台上创建 [8 位模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html) 。