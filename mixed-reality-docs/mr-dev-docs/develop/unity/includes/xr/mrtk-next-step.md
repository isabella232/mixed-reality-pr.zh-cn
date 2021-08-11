---
ms.openlocfilehash: 695db2d7e6765d3584c9e9a6459071ab537c1f003d13461ce5736481b98b7495
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202752"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

若要开始使用 MRTK 的 **新 Unity 项目** ，请从 MRTK 教程中的步骤2开始：

> [!div class="nextstepaction"]
> [使用 MRTK 设置新的 OpenXR 项目](../../tutorials/mr-learning-base-02.md?tabs=openxr)

如果要将现有的 **MRTK 项目升级到 OpenXR**，则需要将 MRTK-Unity 升级到最新版本 (版本2.7.2 或更高版本，) 获取与混合现实 OpenXR 插件兼容的密钥修补程序。  使用 [混合现实功能工具](../../welcome-to-mr-feature-tool.md) 升级到最新版本的 MRTK，然后按照 [以下手动 OpenXR 设置步骤](#manual-setup-without-mrtk)操作。 有关 [将现有的 MRTK 项目迁移到 OpenXR 的更深入信息](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，请参阅 MRTK 文档。

> [!NOTE]
> 从早于 **2.5.3** 的 MRTK 的早期版本进行升级时，请确保 **资产/MixedRealityToolkit 和 link.xml** 文件中有以下行：
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 如果开始使用 MRTK 2.5.4 或更高版本，则默认情况下会添加此行。

# <a name="windows-xr"></a>[WindowsXR](#tab/windowsxr)

若要开始使用 MRTK 的 **新 Unity 项目** ，请从 MRTK 教程中的步骤2开始：

> [!div class="nextstepaction"]
> [使用 MRTK 设置新的 Windows XR 项目](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[旧版 XR](#tab/legacy)

若要开始使用 MRTK 的 **新 Unity 项目** ，请从 MRTK 教程中的步骤2开始：

> [!div class="nextstepaction"]
> [使用 MRTK 设置新的旧式 XR 项目](../../tutorials/mr-learning-base-02.md?tabs=wsa)