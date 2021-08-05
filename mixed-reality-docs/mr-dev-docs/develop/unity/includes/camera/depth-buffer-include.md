---
ms.openlocfilehash: 924190e10de100fc84795344a6cf676f318d04cec26793af96d03a3cb7cb5f78
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212220"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[MRTK 的配置](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) 对话框将尝试为 XR SDK 和旧版 WSA 设置深度缓冲区设置，但检查这些选项卡并验证 Unity 中的设置是个不错的选择。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

若要设置 Unity 应用是否将提供深度缓冲区来Windows：

1. 转到  >  **"Project 设置**  >  **XR 插件管理**"，并确保菜单项已展开。
2. 单击与所选 XR 运行时对应的菜单项，Windows Mixed Reality OpenXR。 此外，请确保选择正确的生成平台，因为"独立"和"通用Windows平台Windows选项卡都可用。
3. 启用和配置：
    1. 对于 OpenXR，请在"深度提交模式"下拉列表中选择深度格式或" **无** "。
    2. 对于Windows Mixed Reality，请选中或取消选中"**共享深度缓冲区"** 复选框。 然后，从"深度缓冲区格式 **"下拉列表中选择** 一种格式。

![WindowsXR 插件深度设置 ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR 深度设置](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> 通常建议使用 16 位深度缓冲区来提高性能。 但是，如果使用 16 位深度格式，模具缓冲区需要效果 (例如某些 Unity UI 滚动面板) 将不起作用，因为 [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 不会在此设置中创建模具缓冲区。 相反 *，如果选择 24* 位深度格式，通常会在终结点图形平台上创建一个 [8](https://docs.unity3d.com/Manual/SL-Stencil.html) 位模具缓冲区（如果适用）。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

若要设置 Unity 应用是否将提供深度缓冲区来Windows：

1. 转到"**编辑**  >  **Project 设置**  >  **Player**  >  **Universal Windows 平台"选项卡**  >  **XR 设置。**
2. 展开 **"Windows Mixed Reality SDK"** 项。
3. 选中或取消选中" **启用深度缓冲区共享"** 复选框。 默认情况下，在新项目中选中"启用深度缓冲区共享"，但在较旧的项目中可能默认未选中。

![旧版 XR 深度设置](../../images/wmr-depth.png)

深度缓冲区可以提高视觉质量，只要 Windows 可以使用在主相机的 Unity 中设置的近距平面和远距平面，将深度缓冲区中规范化的按像素深度值准确映射回以米为单位的距离。 如果呈现器以典型方式传递句柄深度值，则通常应该可以在此处正常使用，尽管半透明渲染传递会写入深度缓冲区，同时向现有颜色像素显示 ，但可能会混淆重新重现。  如果知道呈现通道会保留许多最终深度像素，但深度值不准确，则取消选中"启用深度缓冲区共享"可能会获得更好的视觉质量。

> [!NOTE]
> 通常建议使用 16 位深度缓冲区来提高性能。 但是，如果使用 16 位深度格式，模具缓冲区需要效果 (例如某些 Unity UI 滚动面板) 将不起作用，因为 [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 不会在此设置中创建模具缓冲区。 相反 *，如果选择 24* 位深度格式，通常会在终结点图形平台上创建一个 [8](https://docs.unity3d.com/Manual/SL-Stencil.html) 位模具缓冲区（如果适用）。