---
ms.openlocfilehash: eaa7ee56cdaf8b003990571d85f0c2a3bd61ba74fcc0a1112b498fef08032759
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226987"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

在 Unity 菜单中，选择“窗口” > “包管理器”以打开“包管理器”窗口，然后验证安装了“AR Foundation” > “4.1.7”版本。

![选中 AR Foundation 的 Unity 包管理器](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

> [!NOTE]
> 你要安装 AR Foundation 包，因为在下一部分中导入 Azure 空间定位点 SDK 时必须使用它。

## <a name="importing-the-tutorial-assets"></a>导入教程资产

将 AzurespatialAnchors SDK V2.10 添加到您的项目，若要添加包，请遵循此[教程](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

下载以下 Unity 自定义包，并 **按其列出顺序** 将其 **导入**：

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

导入教程资产后，“项目”窗口应如下所示：

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](../images/mr-learning-azure/tutorial1-section4-step1-1-OpenXR.png)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅 [导入混合现实工具包](../mr-learning-base-04.md#importing-the-tutorial-assets) 说明。

# <a name="unity-2020--windows-xr-plugin"></a>[Unity 2020 + Windows XR 插件](#tab/winxr)

在 Unity 菜单中，选择“窗口” > “包管理器”打开“包管理器”窗口，然后选择“AR Foundation”>“4.0.12”版本并单击“安装”按钮以安装包   ：

![选中 AR Foundation 的 Unity 包管理器](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

> [!NOTE]
> 你要安装 AR Foundation 包，因为在下一部分中导入 Azure 空间定位点 SDK 时必须使用它。

## <a name="importing-the-tutorial-assets"></a>导入教程资产

将 AzurespatialAnchors SDK V2.10 添加到您的项目，若要添加包，请遵循此[教程](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

下载以下 Unity 自定义包，并 **按其列出顺序** 将其 **导入**：

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

导入教程资产后，“项目”窗口应如下所示：

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](../images/mr-learning-azure/tutorial1-section4-step1-1-XRSDK.png)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅 [导入混合现实工具包](../mr-learning-base-04.md#importing-the-tutorial-assets) 说明。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

在 Unity 菜单中，选择“窗口” > “包管理器”打开“包管理器”窗口，然后选择“AR Foundation”>“3.1.3”版本并单击“安装”按钮以安装包   ：

![选中 AR Foundation 的 Unity 包管理器](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

> [!NOTE]
> 你要安装 AR Foundation 包，因为在下一部分中导入 Azure 空间定位点 SDK 时必须使用它。

## <a name="importing-the-tutorial-assets"></a>导入教程资产

将 AzurespatialAnchors SDK V2.7.2 添加到您的项目，若要添加包，请遵循此[教程](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)

下载以下 Unity 自定义包，并 **按其列出顺序** 将其 **导入**：

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage)

导入教程资产后，“项目”窗口应如下所示：

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](../images/mr-learning-azure/tutorial1-section4-step1-1-Legacy.png)

> [!NOTE]
> 如果看到任何有关“WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)”和“WorldAnchor.GetNativeSpatialAnchorPtr()”即将过时的 CS0618 警告，可忽略这些警告。

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅 [导入混合现实工具包](../mr-learning-base-04.md#importing-the-tutorial-assets) 说明。
