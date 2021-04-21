---
ms.openlocfilehash: 2b0dc328a1a47d9a0bd385cac6a88563dcc3938d
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107327196"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="b0e9d-101">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="b0e9d-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="b0e9d-102">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="b0e9d-102">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity“项目设置...”菜单路径](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="b0e9d-104">在“项目设置”窗口中，选择“XR 插件管理” > “安装 XR 插件管理”，安装 XR 插件管理 ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-104">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="b0e9d-106">Unity 安装完 XR 插件管理后。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-106">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="b0e9d-107">确保转到“通用 Windows 平台”设置，然后选中“在启动时初始化 XR”和“Windows Mixed Reality”复选框。 </span><span class="sxs-lookup"><span data-stu-id="b0e9d-107">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup** and **Windows Mixed Reality** checkbox.</span></span>

![包含“添加 Windows Mixed Reality SDK”的 Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2-1.png)

<span data-ttu-id="b0e9d-109">Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-109">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="b0e9d-110">如果未显示，请使用 Unity 菜单打开它。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-110">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="b0e9d-111">在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-111">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![选中了 Windows Mixed Reality SDK 的 Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="b0e9d-113">可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-113">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="b0e9d-114">如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-114">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="b0e9d-115">若要了解有关本主题的详细信息，请参阅<a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-115">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="b0e9d-116">在“项目设置”窗口中，选择“XR 插件管理” > “Windows Mixed Reality” >   “运行时设置”，然后使用“深度缓冲格式”下拉列表选择“16 位深度”：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-116">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth:**</span></span>

![突出显示包名称的 Unity 发布设置](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> <span data-ttu-id="b0e9d-118">可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-118">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="b0e9d-119">若要了解有关此主题的更多信息，可以参考 MRTK 的<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">性能</a>文档的<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-119">To learn more about this topic, you can refer to the   <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="b0e9d-120">在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-120">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![显示了包名称的 Unity 发布设置](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="b0e9d-122">“包名称”是应用的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-122">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="b0e9d-123">在部署应用之前应更改此标识符，以免覆盖以前安装的应用。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-123">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="b0e9d-124">“产品名称”是在 HoloLens“开始”菜单中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-124">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="b0e9d-125">要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-125">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="b0e9d-126">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="b0e9d-126">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="b0e9d-127">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="b0e9d-127">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity“项目设置...”菜单路径](../images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="b0e9d-129">在“项目设置”窗口中，选择“XR 插件管理” > “安装 XR 插件管理”，安装 XR 插件管理 ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-129">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![选择了“安装 XR 插件管理”的 Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="b0e9d-131">Unity 安装完 XR 插件管理后。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-131">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="b0e9d-132">确保转到“通用 Windows 平台”设置，然后选中“在启动时初始化 XR”、“OpenXR”和“Microsoft HoloLens 功能集”复选框。  </span><span class="sxs-lookup"><span data-stu-id="b0e9d-132">Ensure that you are in Universal Windows Platform settings and Check the **Initialize XR on Startup**, **OpenXR** and **Microsoft HoloLens feature set** checkboxes.</span></span>

![选择了“添加 OpenXR 和 Microsoft HoloLens 功能”的 Unity XR 设置](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

<span data-ttu-id="b0e9d-134">在屏幕顶部的菜单栏中，导航到“Mixed Reality”>“OpenXR”>“应用适用于 HoloLens 2 的推荐项目设置”，以获得更好的应用性能。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-134">In the menu bar at the top of the screen, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Mixed Reality 菜单，其中选择了“OpenXR”和“应用适用于 HoloLens 2 的推荐项目设置”](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

>[!Important]
><span data-ttu-id="b0e9d-136">如果在 OpenXR 插件（预览版）旁边看到红色的警告图标，请单击该图标，选择“全部修复”并继续。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-136">If you see a red warning icon next to OpenXR Plugin (Preview), click the icon and select Fix all before continuing.</span></span> <span data-ttu-id="b0e9d-137">Unity 编辑器可能需要自动重启以使更改生效。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-137">The Unity Editor may need to restart itself for the changes to take effect.</span></span>
><span data-ttu-id="b0e9d-138">![OpenXR 项目验证菜单，其中选中了所有问题以待修复。](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span><span class="sxs-lookup"><span data-stu-id="b0e9d-138">![OpenXR project validation menu with all issues selected to be fixed.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)</span></span>

<span data-ttu-id="b0e9d-139">Unity 导入必要的文件后，应再次显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-139">After Unity has finished importing necessary files, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="b0e9d-140">如果未显示，请使用 Unity 菜单打开它。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-140">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="b0e9d-141">在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-141">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![选中默认选项的 MRTK 配置窗口](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
><span data-ttu-id="b0e9d-143">可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-143">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="b0e9d-144">如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-144">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="b0e9d-145">若要了解有关本主题的详细信息，请参阅<a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-145">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>


<span data-ttu-id="b0e9d-146">在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 的“发布设置”](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="b0e9d-148">“包名称”是应用的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-148">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="b0e9d-149">在部署应用之前应更改此标识符，以免覆盖以前安装的应用。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-149">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="b0e9d-150">“产品名称”是在 HoloLens“开始”菜单中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-150">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="b0e9d-151">要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-151">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="b0e9d-152">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="b0e9d-152">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="b0e9d-153">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="b0e9d-153">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="b0e9d-154">在“项目设置”窗口中，选择“播放器” > “XR 设置”，勾选“支持虚拟现实”复选框，然后单击 + 图标，选择“Windows Mixed Reality”以添加 Windows Mixed Reality SDK   ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-154">In the Project Settings window, select **Player** > **XR Settings** and check the **Virual Reality Supported** checkbox then click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Unity XR 设置，选中了“添加 Windows Mixed Reality SDK”](../images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="b0e9d-156">Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-156">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="b0e9d-157">如果未显示该窗口，可从 Unity 菜单手动将其打开，方法是转到“混合现实工具包” > “实用程序” > “配置 Unity 项目”</span><span class="sxs-lookup"><span data-stu-id="b0e9d-157">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="b0e9d-158">在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-158">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 配置窗口](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="b0e9d-160">可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-160">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="b0e9d-161">如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-161">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="b0e9d-162">若要了解有关本主题的详细信息，请参阅<a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-162">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="b0e9d-163">在“项目设置”窗口中，选择“播放器” > “XR 设置”，然后使用“深度格式”下拉列表选“16 位深度”   ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-163">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 启用 16 深度](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="b0e9d-165">可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-165">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="b0e9d-166">若要详细了解此主题，可参考 MRTK 的性能文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-166">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="b0e9d-167">在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：</span><span class="sxs-lookup"><span data-stu-id="b0e9d-167">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 发布设置。](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="b0e9d-170">“包名称”是应用的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-170">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="b0e9d-171">在部署应用之前应更改此标识符，以免覆盖以前安装的应用。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-171">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="b0e9d-172">“产品名称”是在 HoloLens“开始”菜单中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-172">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="b0e9d-173">要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。</span><span class="sxs-lookup"><span data-stu-id="b0e9d-173">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
