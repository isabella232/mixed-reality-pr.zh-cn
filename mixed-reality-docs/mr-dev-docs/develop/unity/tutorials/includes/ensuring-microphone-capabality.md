---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098034"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 插件](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>确保麦克风功能并添加语音输入数据提供程序

在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：

![启用麦克风功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> 在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#configuring-the-unity-project)指令期间，应该已经启用了麦克风功能。 但如果未启用此功能，请确保立即启用。

在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡：

* 展开“输入数据提供程序”，单击“+ 添加数据提供程序”按钮并添加新的数据提供程序 

![用于添加新语音命令的数据提供程序](../images/mr-learning-base/base-09-section1-step1-2.png)

将 Microsoft.MixedReality.ToolKit.Windows.Input >  WindowsSpeechInputProvider 分配给新数据提供程序的 Type 字段。

![添加新语音命令设置](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>确保麦克风功能并添加语音输入数据提供程序

在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：

![为 OpenXR 启用麦克风功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> 在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#configuring-the-unity-project)指令期间，应该已经启用了麦克风功能。 但如果未启用此功能，请确保立即启用。

在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡：

* 展开“输入数据提供程序”，单击“+ 添加数据提供程序”按钮并添加新的数据提供程序 

![为 OpenXR 添加新语音命令](../images/mr-learning-base/base-09-section1-step1-2.png)

将 Microsoft.MixedReality.ToolKit.Windows.Input >  WindowsSpeechInputProvider 分配给新数据提供程序的 Type 字段。

![为 OpenXR 添加新语音命令设置](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a>确保启用麦克风功能

在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：

![启用麦克风功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> 在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指令期间，应该已经启用了麦克风功能。 但如果未启用此功能，请确保立即启用。
