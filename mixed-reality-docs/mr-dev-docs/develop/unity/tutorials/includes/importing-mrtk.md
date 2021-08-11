---
ms.openlocfilehash: 7fd590713322c296cbbb14e133b1085aa27bb0197b70d1feca1ecb59ed61a3c7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201244"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

打开“MixedRealityFeatureTool”后，单击“开始”以开始使用混合现实功能工具。

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

第一步是使用省略号按钮将混合现实功能工具指向您的项目路径，单击项目路径旁边的三个点省略号按钮，然后在资源管理器中浏览到项目文件夹，例如 D:\MixedRealityLearning\MRTK Tutorials。

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

找到项目的文件夹后，单击“打开”按钮返回到混合现实功能工具。 然后单击“发现功能”。

> [!NOTE]
> 浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。 文件名必须有一个值才能使文件夹被选中。

> [!Important]
> 混合现实功能工具执行验证以确保它已定向到 Unity 项目文件夹。 文件夹必须包含资产、包和项目设置文件夹。

功能按类别分组以便于查找，单击“混合现实工具包”下拉列表，查找与混合现实工具包相关的包，然后单击“平台支持”下拉列表查找与各种支持平台相关的包。

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

选中“混合现实工具包基础”，单击其旁边的下拉列表以选择“MRTK 2.7.2”，同时选中“混合现实 OpenXR 插件 1.0.0”，并单击其旁边的下拉列表，选择最新可用版本，然后单击“获取功能”按钮下载所选的包。

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

接下来，单击“验证”按钮以验证所选包，随即显示一个弹出窗口，其中显示消息“未检测到任何验证问题”，单击“确定”以关闭弹出窗口，然后单击“导入”按钮。

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


单击“批准”按钮，将“混合现实工具包”添加到项目中。

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>配置 Unity 项目

当 Unity 完成导入上一节的包后，系统将显示一条警告消息，提示重新启动 Unity 编辑器来为新插件系统启用后端，单击“是”

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

Unity 重新启动后，应显示“MRTK 项目配置器”窗口。 如果未显示该窗口，请转到“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”：

![打开“MRTK 项目配置器”窗口](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

单击“Unity OpenXR 插件”以启用 XR 插件管理，并将其所需的包添加到项目中。

![添加 Unity OpenXR 插件 ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

这会为 XR 插件管理导入所需的 Unity 包，完成后，请单击 MRTK 项目配置器中的“显示 XR 插件管理设置”。

![显示 XR 插件管理设置 ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

这将打开“项目设置”窗口。 在“项目设置”窗口的“XR 插件管理”下，确保处于”通用 Windows 平台”设置（Windows 徽标选项卡）中。 还需确保选中“启动时初始化 XR”，然后单击“OpenXR”复选框和“Microsoft HoloLens 功能集”复选框以启用这些功能。  

![启用 OpenXR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

选中“OpenXR”复选框后，MRTK 项目配置器窗口将显示更新的消息和“应用设置”按钮。 单击“应用设置”按钮。 

![项目设置窗口 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

单击“应用设置”时，可能会在控制台中看到此错误消息。 如果这是唯一错误或没有错误，您可以继续。

![OpenXR 远程处理错误消息](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

若要验证 OpenXR 配置，请在“XR 插件管理”下单击“OpenXR”，并检查以下各项：
* 深度提交模式：深度 16 位
* 交互配置文件：Microsoft 手部交互配置文件

![项目设置窗口 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> 可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。 若要详细了解此主题，可参考 MRTK 的性能文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。


在“MRTK 项目配置器”窗口中，单击“下一步”，然后单击“应用”按钮以应用设置。   （如果已关闭该窗口，请转到“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”）

![项目设置窗口 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![项目设置窗口 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

单击“应用”后，Unity 将尝试重新启动以使输入系统生效，单击“应用”以重新启动 Unity 编辑器

### <a name="configure-additional-project-settings"></a>配置其他项目设置

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口 。

在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：

![Unity 发布设置。 已配置包名称](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> “包名称”是应用的唯一标识符。 在部署应用之前应更改此标识符，以免覆盖以前安装的应用。

> [!TIP]
> “产品名称”是在 HoloLens“开始”菜单中显示的名称。 要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 插件](#tab/winxr)

打开“MixedRealityFeatureTool”后，单击“开始”以开始使用混合现实功能工具。

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

第一步是使用省略号按钮将混合现实功能工具指向您的项目路径，单击项目路径旁边的三个点省略号按钮，然后在资源管理器中浏览到项目文件夹，例如 D:\MixedRealityLearning\MRTK Tutorials。

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


找到项目的文件夹后，单击“打开”按钮返回到混合现实功能工具。 然后单击“发现功能”。

> [!NOTE]
> 浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。 文件名必须有一个值才能使文件夹被选中。

> [!Important]
> 混合现实功能工具执行验证以确保它已定向到 Unity 项目文件夹。 文件夹必须包含资产、包和项目设置文件夹。

功能按类别进行了分组，以便于查找，单击“混合现实工具包”下拉列表，查找与混合现实工具包相关的包。

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

选中“混合现实工具包基础”框，并单击其旁边的下拉列表以选择“MRTK 2.7.0”，然后单击“获取功能”按钮以下载所选的包。  

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

接下来，单击“验证”按钮以验证所选包，随即显示一个弹出窗口，其中显示消息“未检测到任何验证问题”，单击“确定”以关闭弹出窗口，然后单击“导入”按钮。

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


单击“批准”按钮，将“混合现实工具包”添加到项目中。

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>配置 Unity 项目

Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。 如果未显示该窗口，请转到“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”：

![打开 MRTK 配置器工具](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

单击“内置 Unity 插件（非 OpenXR）”以启用 XR 插件管理，并将其所需的包添加到项目中。

![ MRTK 配置器工具](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> 上面的屏幕截图来自 Unity 2020，如果您使用的是 Unity 2019，请选择“XR SDK/XR 管理”

这会为 XR 插件管理导入所需的 Unity 包，完成后，请单击 MRTK 项目配置器中的“显示设置”。

![播放器设置窗口](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

这会打开“项目设置”窗口，在“项目设置”窗口的“XR 插件管理”下方，确保您位于“通用 Windows 平台”设置中，还要确保选中“启动时初始化 XR”和“Windows Mixed Reality”复选框。   

![播放器设置窗口“启用混合现实-xrsdk”](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。 如果未显示，请使用 Unity 菜单打开它。

在“MRTK 项目配置器”窗口中，单击“下一步”，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：

![MRTK 项目配置器-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> 可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：

> * 设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。 若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文档的[单通道实例化渲染](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)部分。
> * 设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。 若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。

> [!TIP]
> 可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。 如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。 若要了解有关本主题的详细信息，请参阅<a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。

单击“下一步”，然后在“MRTK 项目配置器”窗口中单击“完成”，完成 XRSDK 的 Unity 项目配置。

### <a name="configure-additional-project-settings"></a>配置其他项目设置

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： 

在“项目设置”窗口中，选择“XR 插件管理” > “Windows Mixed Reality” > “运行时设置”，然后使用“深度缓冲格式”下拉列表选择“16 位深度” ：

![Unity 启用 16 深度](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> 可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。 若要详细了解此主题，可参考 MRTK 的性能文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。

在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：

![Unity 发布设置。 已配置包名称](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> “包名称”是应用的唯一标识符。 在部署应用之前应更改此标识符，以免覆盖以前安装的应用。

> [!TIP]
> “产品名称”是在 HoloLens“开始”菜单中显示的名称。 要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

打开“MixedRealityFeatureTool”后，单击“开始”以开始使用混合现实功能工具。

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

第一步是使用省略号按钮将混合现实功能工具指向您的项目路径，单击项目路径旁边的三个点省略号按钮，然后在资源管理器中浏览到项目文件夹，例如 D:\MixedRealityLearning\MRTK Tutorials。

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

找到项目的文件夹后，单击“打开”按钮返回到混合现实功能工具。 然后单击“发现功能”。

> [!NOTE]
> 浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。 文件名必须有一个值才能使文件夹被选中。

> [!Important]
> 混合现实功能工具执行验证以确保它已定向到 Unity 项目文件夹。 文件夹必须包含资产、包和项目设置文件夹。

功能按类别进行了分组，以便于查找，单击“混合现实工具包”下拉列表，查找与混合现实工具包相关的包。

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

选中“混合现实工具包基础”，并单击其旁边的下拉列表以选择“MRTK 2.7.0”，然后单击“获取功能”按钮以下载所选的包。  

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

接下来，单击“验证”按钮以验证所选包，随即显示一个弹出窗口，其中显示消息“未检测到任何验证问题”，单击“确定”以关闭弹出窗口，然后单击“导入”按钮。

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

单击“批准”按钮，将“混合现实工具包”添加到项目中。

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>配置 Unity 项目

Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。 如果未显示该窗口，请转到“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”：

![Unity“配置 Unity 项目”菜单路径](../images/mr-learning-base/base-02-section5-step1-1.png)

单击“旧版 XR”以启用旧版 XR，并将其所需的包添加到项目中。

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

单击“下一步”按钮，为旧版 XR 启用 XR 管道设置。

![Unity MRTK 配置窗口](../images/mr-learning-base/base-02-section5-step1-3.PNG)

在“MRTK 项目配置器”窗口中，确保选中所有选项，同时使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：

![MRTK 配置窗口](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> 可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：

> * 设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。 若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文档的[单通道实例化渲染](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)部分。
> * 设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。 若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。

> [!TIP]
> 可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。 如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。 若要了解有关本主题的详细信息，请参阅<a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。

单击“下一步”，然后在“MRTK 项目配置器”窗口中单击“完成”按钮，完成旧版 XR 的 Unity 项目配置。

### <a name="configure-additional-project-settings"></a>配置其他项目设置

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： 

在“项目设置”窗口中，选择“播放器” > “XR 设置”，然后使用“深度格式”下拉列表选“16 位深度”   ：

![Unity 启用 16 深度](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> 可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。 若要详细了解此主题，可参考 MRTK 的性能文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。

在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：

![Unity 发布设置。 已配置包名称](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> “包名称”是应用的唯一标识符。 在部署应用之前应更改此标识符，以免覆盖以前安装的应用。

> [!TIP]
> “产品名称”是在 HoloLens“开始”菜单中显示的名称。 要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。
