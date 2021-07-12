---
ms.openlocfilehash: 0a89ef77bee7eff83d4599c46ffd2681c99b2165
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175564"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

在 Unity 菜单中，选择“窗口” > “包管理器”以打开“包管理器”窗口，然后验证安装了“AR Foundation” > “4.1.7”版本。

![选中 AR Foundation 的 Unity 包管理器](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

## <a name="importing-the-tutorial-assets"></a>导入教程资产

将 AzurespatialAnchors SDK V2.10 添加到您的项目，若要添加包，请遵循此[教程](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

下载以下 Unity 自定义包，并 **按其列出顺序** 将其 **导入**：

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

导入教程资产后，“项目”窗口应如下所示：

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](../images/mr-learning-asa/asa-02-section3-step1-2-OpenXR.png)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅 [导入教程资产](../mr-learning-base-04.md#importing-the-tutorial-assets) 说明。

# <a name="unity-2020--windows-xr-plugin"></a>[Unity 2020 + Windows XR 插件](#tab/winxr)

在 Unity 菜单中，选择“窗口” > “包管理器”打开“包管理器”窗口，然后选择“AR Foundation”>“4.0.12”版本并单击“安装”按钮以安装包   ：

![选中 AR Foundation 的 Unity 包管理器](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

## <a name="importing-the-tutorial-assets"></a>导入教程资产

将 AzurespatialAnchors SDK V2.10 添加到您的项目，若要添加包，请遵循此[教程](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

下载以下 Unity 自定义包，并 **按其列出顺序** 将其 **导入**：

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

导入教程资产后，“项目”窗口应如下所示：

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](../images/mr-learning-asa/asa-02-section3-step1-2-XRSDK.PNG)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅 [导入教程资产](../mr-learning-base-04.md#importing-the-tutorial-assets) 说明。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

在 Unity 菜单中，选择“窗口” > “包管理器”打开“包管理器”窗口，然后选择“AR Foundation”>“3.1.3”版本并单击“安装”按钮以安装包   ：

![选中 AR Foundation 的 Unity 包管理器](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

## <a name="importing-the-tutorial-assets"></a>导入教程资产

将 AzurespatialAnchors SDK V2.7.2 添加到您的项目，若要添加包，请遵循此[教程](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

下载以下 Unity 自定义包，并 **按其列出顺序** 将其 **导入**：

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage)

导入教程资产后，“项目”窗口应如下所示：

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](../images/mr-learning-asa/asa-02-section3-step1-2-Legacy.png)

> [!NOTE]
> 如果看到任何有关“WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) 已过时”的 CS0618 警告，则可以忽略这些警告。

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅 [导入教程资产](../mr-learning-base-04.md#importing-the-tutorial-assets) 说明。
