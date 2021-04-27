---
ms.openlocfilehash: d8d46da1a1a095074f059b53ebd997e1b6f89961
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984397"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 插件](#tab/winxr)

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： 

![Unity“项目设置...”菜单路径](../images/mr-learning-base/base-02-section5-step2-1.png)

在“项目设置”窗口中，选择“XR 插件管理” > “安装 XR 插件管理”，安装 XR 插件管理 ：

![Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2.png)

Unity 安装完 XR 插件管理后。 确保转到“通用 Windows 平台”设置，然后选中“在启动时初始化 XR”和“Windows Mixed Reality”复选框。 

![包含“添加 Windows Mixed Reality SDK”的 Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。 如果未显示，请使用 Unity 菜单打开它。

在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：

![选中了 Windows Mixed Reality SDK 的 Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。 如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。 若要了解有关本主题的详细信息，请参阅<a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。

在“项目设置”窗口中，选择“XR 插件管理” > “Windows Mixed Reality” >   “运行时设置”，然后使用“深度缓冲格式”下拉列表选择“16 位深度”：

![突出显示包名称的 Unity 发布设置](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> 可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。 若要了解有关此主题的更多信息，可以参考 MRTK 的<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">性能</a>文档的<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。

在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：

![显示了包名称的 Unity 发布设置](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> “包名称”是应用的唯一标识符。 在部署应用之前应更改此标识符，以免覆盖以前安装的应用。

> [!TIP]
> “产品名称”是在 HoloLens“开始”菜单中显示的名称。 要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： 

![Unity“项目设置...”菜单路径](../images/mr-learning-base/base-02-section5-step2-1.png)

在“项目设置”窗口中，选择“XR 插件管理” > “安装 XR 插件管理”，安装 XR 插件管理 ：

![选择了“安装 XR 插件管理”的 Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2.png)

Unity 安装完 XR 插件管理后。 确保转到“通用 Windows 平台”设置，然后选中“在启动时初始化 XR”、“OpenXR”和“Microsoft HoloLens 功能集”复选框。  

![选择了“添加 OpenXR 和 Microsoft HoloLens 功能”的 Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

>[!Important]
>如果在 OpenXR 插件（预览版）旁边看到红色的警告图标，请单击该图标，选择“全部修复”并继续。 Unity 编辑器可能需要自动重启以使更改生效。
>![OpenXR 项目验证菜单，其中选中了所有问题以待修复。](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)

在屏幕顶部的菜单栏中，导航到“Mixed Reality”>“OpenXR”>“应用适用于 HoloLens 2 的推荐项目设置”，以获得更好的应用性能。

![Mixed Reality 菜单，其中选择了“OpenXR”和“应用适用于 HoloLens 2 的推荐项目设置”](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

Unity 导入必要的文件后，应再次显示“MRTK 项目配置器”窗口。 如果未显示，请使用 Unity 菜单打开它。

在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：

![选中默认选项的 MRTK 配置窗口](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。 如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。 若要了解有关本主题的详细信息，请参阅<a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。


在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：

![Unity 的“发布设置”](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> “包名称”是应用的唯一标识符。 在部署应用之前应更改此标识符，以免覆盖以前安装的应用。

> [!TIP]
> “产品名称”是在 HoloLens“开始”菜单中显示的名称。 要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： 

在“项目设置”窗口中，选择“播放器” > “XR 设置”，勾选“支持虚拟现实”复选框，然后单击 + 图标，选择“Windows Mixed Reality”以添加 Windows Mixed Reality SDK   ：

![Unity XR 设置，选中了“添加 Windows Mixed Reality SDK”](../images/mr-learning-base/base-02-section5-step2-4.png)

Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。 如果未显示该窗口，可从 Unity 菜单手动将其打开，方法是转到“混合现实工具包” > “实用程序” > “配置 Unity 项目”

在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：

![MRTK 配置窗口](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。 如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。 若要了解有关本主题的详细信息，请参阅<a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。

在“项目设置”窗口中，选择“播放器” > “XR 设置”，然后使用“深度格式”下拉列表选“16 位深度”   ：

![Unity 启用 16 深度](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> 可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。 若要详细了解此主题，可参考 MRTK 的性能文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。

在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：

![Unity 发布设置。 已配置包名称](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> “包名称”是应用的唯一标识符。 在部署应用之前应更改此标识符，以免覆盖以前安装的应用。

> [!TIP]
> “产品名称”是在 HoloLens“开始”菜单中显示的名称。 要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。
