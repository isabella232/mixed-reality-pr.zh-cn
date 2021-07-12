---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603702"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

若要使用 MRTK **开始使用新的 Unity** 项目，请从 MRTK 教程的步骤 2 开始：

> [!div class="nextstepaction"]
> [使用 MRTK 设置新的 OpenXR 项目](../../tutorials/mr-learning-base-02.md?tabs=openxr)

如果要将现有 MRTK 项目升级到 **OpenXR，** 首先需要将 MRTK-Unity 升级到最新版本 (2.7.2 或更高版本) ，以获得与混合现实 OpenXR 插件兼容的关键修补程序。  使用 [混合现实功能工具](../../welcome-to-mr-feature-tool.md) 升级到最新版本的 MRTK，然后按照下面的 [手动 OpenXR 设置步骤操作](#manual-setup-without-mrtk)。 有关将现有 MRTK 项目迁移到 OpenXR 的更深入的信息，请参阅 [MRTK 文档](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)。

> [!NOTE]
> 从低于 **2.5.3** 的旧版 MRTK 升级时，请确保以下行位于 **Assets/MixedRealityToolkit.Generated/link.xml** 文件中：
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 如果从 MRTK 2.5.4 或更高版本开始，则默认情况下将添加此行。

# <a name="windows-xr"></a>[WindowsXR](#tab/windowsxr)

若要使用 MRTK **开始使用新的 Unity** 项目，请从 MRTK 教程的步骤 2 开始：

> [!div class="nextstepaction"]
> [使用 MRTK Windows XR 项目](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[旧版 XR](#tab/legacy)

若要使用 MRTK **开始使用新的 Unity** 项目，请从 MRTK 教程的步骤 2 开始：

> [!div class="nextstepaction"]
> [使用 MRTK 设置新的旧版 XR 项目](../../tutorials/mr-learning-base-02.md?tabs=wsa)