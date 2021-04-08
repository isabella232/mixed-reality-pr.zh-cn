---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097706"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 插件](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a>1.克隆默认的配置配置文件

> [!NOTE]
> 配置配置文件是顶级配置文件。 因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。

在“层次结构”窗口中，选择 MixedRealityToolkit 对象，然后在“检查器”窗口中，验证 MixedRealityToolkit 配置文件是否已设置为 DefaultXRSDKConfigurationProfile  ：

![选中 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

在仍选中了“MixedRealityToolkit”对象的情况下，在检查器窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口： 

![Unity MixedRealityToolkit 组件的“复制和自定义”按钮](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_XRSDKConfigurationProfile），然后单击“克隆”按钮，创建“DefaultXRSDKConfigurationProfile”的可编辑副本 ：

![Unity MixedRealityToolkit 的“克隆配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

新建的配置配置文件现已分配为场景中的配置配置文件：

![应用了新创建的自定义 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

在 Unity 菜单中，选择“文件” > “保存”以保存场景。 

> [!TIP]
> 在学习整篇教程的过程中，请记得保存自己的工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.启用空间感知系统

在“层次结构”窗口中，选择 MixedRealityToolkit 对象，接下来在检查器窗口中，选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：  

![启用了空间感知系统的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> 在未来的项目中，如果你的应用无需响应环境或与环境交互，则建议关闭空间感知来减少性能成本。

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.克隆默认的空间感知系统配置文件

在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口： 

![选中“空间感知”选项卡的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_XRSDKSpatialAwarenessSystemProfile），然后单击“克隆”按钮，创建“DefaultXRSDKSpatialAwarenessSystemProfile”的可编辑副本 ：

![Unity MixedRealityToolkit 的“克隆空间感知系统配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

新建的空间感知系统配置文件现已自动分配到你的配置配置文件：

![应用了新创建的自定义 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.克隆默认的空间感知网格观察程序配置文件

在仍然选中了“空间感知”选项卡的情况下，展开“XR SDK Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口  ：

![已展开“Windows Mixed Reality 空间网格观察程序”部分的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessMeshObserverProfile”的可编辑副本 ：

![Unity MixedRealityToolkit 的“克隆空间网格观察程序配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：

![应用了新创建的自定义 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.更改空间感知网格的可见性

在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下正常运行：  

![空间网格观察程序显示选项设置为“遮挡”的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> 尽管空间映射网格不可见，但它依然存在且可正常运行。 例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。

你已了解如何修改 MRTK 配置文件中的设置。 可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。 由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。 若要详细了解 MRTK 配置文件及其体系结构，可参阅 [MRTK 文档门户](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的 [MRTK 配置文件配置指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)。

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a>1.克隆默认的配置配置文件

> [!NOTE]
> 配置配置文件是顶级配置文件。 因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。

在“层次结构”窗口中，选择 MixedRealityToolkit 对象，然后在“检查器”窗口中，验证 MixedRealityToolkit 配置文件是否已设置为 DefaultOpenXRConfigurationProfile：  

![选择了默认 openXR 配置文件的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

在仍选中了“MixedRealityToolkit”对象的情况下，在检查器窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口： 

![适用于 openxr 配置文件的 Unity MixedRealityToolkit 组件“复制和自定义”按钮](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_OpenXRConfigurationProfile），然后单击“克隆”按钮，创建“DefaultOpenXRConfigurationProfile”的可编辑副本 ：

![适用于 openxr 配置文件的 Unity MixedRealityToolkit 的“克隆配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

新建的配置配置文件现已分配为场景中的配置配置文件：

![应用了新创建的自定义 OpenXR 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

在 Unity 菜单中，选择“文件” > “保存”以保存场景。 

> [!TIP]
> 在学习整篇教程的过程中，请记得保存自己的工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.启用空间感知系统

在“层次结构”窗口中，选择 MixedRealityToolkit 对象，接下来在检查器窗口中，选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：  

![启用了空间感知系统的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> 在未来的项目中，如果你的应用无需响应环境或与环境交互，则建议关闭空间感知来减少性能成本。

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.克隆默认的空间感知系统配置文件

在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口： 

![选中“空间感知”选项卡的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_OpenXRSpatialAwarenessSystemProfile），然后单击“克隆”按钮，创建“DefaultXRSDKSpatialAwarenessSystemProfile”的可编辑副本：  

![Unity MixedRealityToolkit 的“克隆空间感知系统配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

新建的空间感知系统配置文件现已自动分配到你的配置配置文件：

![应用了新创建的自定义 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.克隆默认的空间感知网格观察程序配置文件

在仍然选中了“空间感知”选项卡的情况下，展开“XR SDK Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口  ：

![已展开“Windows Mixed Reality 空间网格观察程序”部分的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessMeshObserverProfile”的可编辑副本 ：

![Unity MixedRealityToolkit 的“克隆空间网格观察程序配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：

![应用了新创建的自定义 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.更改空间感知网格的可见性

在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下正常运行：  

![空间网格观察程序显示选项设置为“遮挡”的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> 尽管空间映射网格不可见，但它依然存在且可正常运行。 例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。

你已了解如何修改 MRTK 配置文件中的设置。 可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。 由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。 若要详细了解 MRTK 配置文件及其体系结构，可参阅 [MRTK 文档门户](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的 [MRTK 配置文件配置指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)。


# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a>1.克隆默认的配置配置文件

> [!NOTE]
> 配置配置文件是顶级配置文件。 因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。

在“层次结构”窗口中，选择 MixedRealityToolkit 对象，然后在检查器窗口中将“MixedRealityToolkit”配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”：

![选中 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-1.png)

在仍选中了“MixedRealityToolkit”对象的情况下，在检查器窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口： 

![Unity MixedRealityToolkit 组件的“复制和自定义”按钮](../images/mr-learning-base/base-03-section1-step1-2.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_HoloLens2ConfigurationProfile），然后单击“克隆”按钮，创建“DefaultHololens2ConfigurationProfile”的可编辑副本 ：

![Unity MixedRealityToolkit 的“克隆配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step1-3.png)

新建的配置配置文件现已分配为场景中的配置配置文件：

![应用了新创建的自定义 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-4.png)

在 Unity 菜单中，选择“文件” > “保存”以保存场景。 

> [!TIP]
> 在学习整篇教程的过程中，请记得保存自己的工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.启用空间感知系统

在“层次结构”窗口中，选择 MixedRealityToolkit 对象，接下来在检查器窗口中，选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：  

![启用了空间感知系统的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> 在未来的项目中，如果你的应用无需响应环境或与环境交互，则建议关闭空间感知来减少性能成本。

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.克隆默认的空间感知系统配置文件

在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口： 

![选中“空间感知”选项卡的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-1.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessSystemProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessSystemProfile”的可编辑副本 ：

![Unity MixedRealityToolkit 的“克隆空间感知系统配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step3-2.png)

新建的空间感知系统配置文件现已自动分配到你的配置配置文件：

![应用了新创建的自定义 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.克隆默认的空间感知网格观察程序配置文件

在仍然选中了“空间感知”选项卡的情况下，展开“Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口：  

![已展开“Windows Mixed Reality 空间网格观察程序”部分的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-1.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessMeshObserverProfile”的可编辑副本 ：

![Unity MixedRealityToolkit 的“克隆空间网格观察程序配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step4-2.png)

新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：

![应用了新创建的自定义 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.更改空间感知网格的可见性

在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下正常运行：  

![空间网格观察程序显示选项设置为“遮挡”的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> 尽管空间映射网格不可见，但它依然存在且可正常运行。 例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。

你已了解如何修改 MRTK 配置文件中的设置。 可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。 由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。 若要详细了解 MRTK 配置文件及其体系结构，可参阅 [MRTK 文档门户](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的 [MRTK 配置文件配置指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)。
