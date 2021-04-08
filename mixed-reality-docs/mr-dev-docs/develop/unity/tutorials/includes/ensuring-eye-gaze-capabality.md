---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097168"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 插件](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>确保凝视输入功能并添加凝视数据提供程序

在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用眼睛凝视输入功能”是否灰显   ：

![Unity“MRTK 项目配置器”窗口](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> 当你在本系列教程开头配置 Unity 项目时，[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#configuring-the-unity-project)指令期间应该已经启用了眼睛凝视输入功能。 但如果未启用此功能，请确保立即启用。

在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡：

* 展开“输入数据提供程序”，单击“+ 添加数据提供程序”按钮并添加新的数据提供程序 

![添加凝视数据提供程序 1](../images/mr-learning-base/base-08-section1-step1-2.png)

将 Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input >  WindowsMixedRealityEyeGazeProvider 分配给新数据提供程序的 Type 字段。

![添加凝视数据提供程序 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>确保凝视输入功能并添加凝视数据提供程序

在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡：

* 展开“输入数据提供程序”，单击“+ 添加数据提供程序”按钮并添加新的数据提供程序 

![添加凝视数据提供程序 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

将 Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input >  WindowsMixedRealityEyeGazeProvider 分配给新数据提供程序的 Type 字段。

![添加凝视数据提供程序 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>确保启用了“眼睛凝视输入”功能

在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用眼睛凝视输入功能”是否灰显   ：

![Unity“MRTK 项目配置器”窗口](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> 当你在本系列教程开头配置 Unity 项目时，[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指令期间应该已经启用了眼睛凝视输入功能。 但如果未启用此功能，请确保立即启用。
