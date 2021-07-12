---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175807"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="35174-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="35174-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="35174-102">打开“MixedRealityFeatureTool”后，单击“开始”以开始使用混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="35174-102">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="35174-103">第一步是使用省略号按钮将混合现实功能工具指向您的项目路径，单击项目路径旁边的三个点省略号按钮，然后在资源管理器中浏览到项目文件夹，例如 D:\MixedRealityLearning\MRTK Tutorials。</span><span class="sxs-lookup"><span data-stu-id="35174-103">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="35174-104">找到项目的文件夹后，单击“打开”按钮返回到混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="35174-104">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="35174-105">然后单击“发现功能”。</span><span class="sxs-lookup"><span data-stu-id="35174-105">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="35174-106">浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。</span><span class="sxs-lookup"><span data-stu-id="35174-106">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="35174-107">文件名必须有一个值才能使文件夹被选中。</span><span class="sxs-lookup"><span data-stu-id="35174-107">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="35174-108">混合现实功能工具执行验证以确保它已定向到 Unity 项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="35174-108">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="35174-109">文件夹必须包含资产、包和项目设置文件夹。</span><span class="sxs-lookup"><span data-stu-id="35174-109">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="35174-110">功能按类别分组以便于查找，单击“混合现实工具包”下拉列表，查找与混合现实工具包相关的包，然后单击“平台支持”下拉列表查找与各种支持平台相关的包。</span><span class="sxs-lookup"><span data-stu-id="35174-110">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="35174-111">选中“混合现实工具包基础”，单击其旁边的下拉列表以选择“MRTK 2.7.2”，同时选中“混合现实 OpenXR 插件 1.0.0”，并单击其旁边的下拉列表，选择最新可用版本，然后单击“获取功能”按钮下载所选的包。</span><span class="sxs-lookup"><span data-stu-id="35174-111">Check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.2**, also check the **Mixed Reality OpenXR Plugin 1.0.0** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

<span data-ttu-id="35174-112">接下来，单击“验证”按钮以验证所选包，随即显示一个弹出窗口，其中显示消息“未检测到任何验证问题”，单击“确定”以关闭弹出窗口，然后单击“导入”按钮。</span><span class="sxs-lookup"><span data-stu-id="35174-112">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="35174-113">单击“批准”按钮，将“混合现实工具包”添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="35174-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a><span data-ttu-id="35174-114">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="35174-114">Configuring the Unity project</span></span>

<span data-ttu-id="35174-115">当 Unity 完成导入上一节的包后，系统将显示一条警告消息，提示重新启动 Unity 编辑器来为新插件系统启用后端，单击“是”</span><span class="sxs-lookup"><span data-stu-id="35174-115">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

<span data-ttu-id="35174-116">Unity 重新启动后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="35174-116">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="35174-117">如果未显示该窗口，请转到“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”：</span><span class="sxs-lookup"><span data-stu-id="35174-117">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![打开“MRTK 项目配置器”窗口](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="35174-119">单击“Unity OpenXR 插件”以启用 XR 插件管理，并将其所需的包添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="35174-119">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="35174-120">添加 Unity OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="35174-120">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

<span data-ttu-id="35174-121">这会为 XR 插件管理导入所需的 Unity 包，完成后，请单击 MRTK 项目配置器中的“显示 XR 插件管理设置”。</span><span class="sxs-lookup"><span data-stu-id="35174-121">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="35174-122">显示 XR 插件管理设置</span><span class="sxs-lookup"><span data-stu-id="35174-122">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

<span data-ttu-id="35174-123">这将打开“项目设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="35174-123">This opens **Project Settings window**.</span></span> <span data-ttu-id="35174-124">在“项目设置”窗口的“XR 插件管理”下，确保处于”通用 Windows 平台”设置（Windows 徽标选项卡）中。</span><span class="sxs-lookup"><span data-stu-id="35174-124">In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings (Windows logo tab).</span></span> <span data-ttu-id="35174-125">还需确保选中“启动时初始化 XR”，然后单击“OpenXR”复选框和“Microsoft HoloLens 功能集”复选框以启用这些功能。  </span><span class="sxs-lookup"><span data-stu-id="35174-125">Also Ensure **Initialize XR on Startup** is checked, then click **OpenXR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![启用 OpenXR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

<span data-ttu-id="35174-127">选中“OpenXR”复选框后，MRTK 项目配置器窗口将显示更新的消息和“应用设置”按钮。</span><span class="sxs-lookup"><span data-stu-id="35174-127">Once you check OpenXR checkbox, MRTK Project Configurator window will show updated message with **Apply Settings** button.</span></span> <span data-ttu-id="35174-128">单击“应用设置”按钮。</span><span class="sxs-lookup"><span data-stu-id="35174-128">Click **Apply Settings** button.</span></span> 

![项目设置窗口 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

<span data-ttu-id="35174-130">单击“应用设置”时，可能会在控制台中看到此错误消息。</span><span class="sxs-lookup"><span data-stu-id="35174-130">When you click Apply Settings, you might see this error message in the Console.</span></span> <span data-ttu-id="35174-131">如果这是唯一错误或没有错误，您可以继续。</span><span class="sxs-lookup"><span data-stu-id="35174-131">You can proceed if this is the only error or there is no error.</span></span>

![OpenXR 远程处理错误消息](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

<span data-ttu-id="35174-133">若要验证 OpenXR 配置，请在“XR 插件管理”下单击“OpenXR”，并检查以下各项：</span><span class="sxs-lookup"><span data-stu-id="35174-133">To validate OpenXR configuration, click **OpenXR** under **XR Plug-in Management** and check these items:</span></span>
* <span data-ttu-id="35174-134">深度提交模式：深度 16 位</span><span class="sxs-lookup"><span data-stu-id="35174-134">Depth Submission Mode: **Depth 16 Bit**</span></span>
* <span data-ttu-id="35174-135">交互配置文件：Microsoft 手部交互配置文件</span><span class="sxs-lookup"><span data-stu-id="35174-135">Interaction Profiles: **Microsoft Hand Interaction Profile**</span></span>

![项目设置窗口 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> <span data-ttu-id="35174-137">可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。</span><span class="sxs-lookup"><span data-stu-id="35174-137">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="35174-138">若要详细了解此主题，可参考 MRTK 的性能文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。</span><span class="sxs-lookup"><span data-stu-id="35174-138">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>


<span data-ttu-id="35174-139">在“MRTK 项目配置器”窗口中，单击“下一步”，然后单击“应用”按钮以应用设置。  </span><span class="sxs-lookup"><span data-stu-id="35174-139">In the **MRTK Project Configurator** window, click on **Next**, then click the **Apply** button to apply the settings.</span></span> <span data-ttu-id="35174-140">（如果已关闭该窗口，请转到“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”）</span><span class="sxs-lookup"><span data-stu-id="35174-140">(If you closed it, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**)</span></span>

![项目设置窗口 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![项目设置窗口 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="35174-143">单击“应用”后，Unity 将尝试重新启动以使输入系统生效，单击“应用”以重新启动 Unity 编辑器</span><span class="sxs-lookup"><span data-stu-id="35174-143">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="35174-144">配置其他项目设置</span><span class="sxs-lookup"><span data-stu-id="35174-144">Configure additional project settings</span></span>

<span data-ttu-id="35174-145">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口 。</span><span class="sxs-lookup"><span data-stu-id="35174-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window.</span></span>

<span data-ttu-id="35174-146">在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：</span><span class="sxs-lookup"><span data-stu-id="35174-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 发布设置。](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="35174-149">“包名称”是应用的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="35174-149">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="35174-150">在部署应用之前应更改此标识符，以免覆盖以前安装的应用。</span><span class="sxs-lookup"><span data-stu-id="35174-150">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="35174-151">“产品名称”是在 HoloLens“开始”菜单中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="35174-151">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="35174-152">要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。</span><span class="sxs-lookup"><span data-stu-id="35174-152">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="35174-153">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="35174-153">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="35174-154">打开“MixedRealityFeatureTool”后，单击“开始”以开始使用混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="35174-154">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="35174-155">第一步是使用省略号按钮将混合现实功能工具指向您的项目路径，单击项目路径旁边的三个点省略号按钮，然后在资源管理器中浏览到项目文件夹，例如 D:\MixedRealityLearning\MRTK Tutorials。</span><span class="sxs-lookup"><span data-stu-id="35174-155">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


<span data-ttu-id="35174-156">找到项目的文件夹后，单击“打开”按钮返回到混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="35174-156">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="35174-157">然后单击“发现功能”。</span><span class="sxs-lookup"><span data-stu-id="35174-157">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="35174-158">浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。</span><span class="sxs-lookup"><span data-stu-id="35174-158">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="35174-159">文件名必须有一个值才能使文件夹被选中。</span><span class="sxs-lookup"><span data-stu-id="35174-159">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="35174-160">混合现实功能工具执行验证以确保它已定向到 Unity 项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="35174-160">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="35174-161">文件夹必须包含资产、包和项目设置文件夹。</span><span class="sxs-lookup"><span data-stu-id="35174-161">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="35174-162">功能按类别进行了分组，以便于查找，单击“混合现实工具包”下拉列表，查找与混合现实工具包相关的包。</span><span class="sxs-lookup"><span data-stu-id="35174-162">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="35174-163">选中“混合现实工具包基础”框，并单击其旁边的下拉列表以选择“MRTK 2.7.0”，然后单击“获取功能”按钮以下载所选的包。  </span><span class="sxs-lookup"><span data-stu-id="35174-163">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="35174-164">接下来，单击“验证”按钮以验证所选包，随即显示一个弹出窗口，其中显示消息“未检测到任何验证问题”，单击“确定”以关闭弹出窗口，然后单击“导入”按钮。</span><span class="sxs-lookup"><span data-stu-id="35174-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="35174-165">单击“批准”按钮，将“混合现实工具包”添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="35174-165">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="35174-166">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="35174-166">Configuring the Unity project</span></span>

<span data-ttu-id="35174-167">Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="35174-167">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="35174-168">如果未显示该窗口，请转到“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”：</span><span class="sxs-lookup"><span data-stu-id="35174-168">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![打开 MRTK 配置器工具](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="35174-170">单击“内置 Unity 插件（非 OpenXR）”以启用 XR 插件管理，并将其所需的包添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="35174-170">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="35174-171">MRTK 配置器工具</span><span class="sxs-lookup"><span data-stu-id="35174-171">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="35174-172">上面的屏幕截图来自 Unity 2020，如果您使用的是 Unity 2019，请选择“XR SDK/XR 管理”</span><span class="sxs-lookup"><span data-stu-id="35174-172">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="35174-173">这会为 XR 插件管理导入所需的 Unity 包，完成后，请单击 MRTK 项目配置器中的“显示设置”。</span><span class="sxs-lookup"><span data-stu-id="35174-173">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![播放器设置窗口](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="35174-175">这会打开“项目设置”窗口，在“项目设置”窗口的“XR 插件管理”下方，确保您位于“通用 Windows 平台”设置中，还要确保选中“启动时初始化 XR”和“Windows Mixed Reality”复选框。   </span><span class="sxs-lookup"><span data-stu-id="35174-175">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![播放器设置窗口“启用混合现实-xrsdk”](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="35174-177">Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="35174-177">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="35174-178">如果未显示，请使用 Unity 菜单打开它。</span><span class="sxs-lookup"><span data-stu-id="35174-178">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="35174-179">在“MRTK 项目配置器”窗口中，单击“下一步”，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：</span><span class="sxs-lookup"><span data-stu-id="35174-179">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 项目配置器-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="35174-181">可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：</span><span class="sxs-lookup"><span data-stu-id="35174-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="35174-182">设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。</span><span class="sxs-lookup"><span data-stu-id="35174-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="35174-183">若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文档的[单通道实例化渲染](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)部分。</span><span class="sxs-lookup"><span data-stu-id="35174-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="35174-184">设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。</span><span class="sxs-lookup"><span data-stu-id="35174-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="35174-185">若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。</span><span class="sxs-lookup"><span data-stu-id="35174-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="35174-186">可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。</span><span class="sxs-lookup"><span data-stu-id="35174-186">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="35174-187">如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。</span><span class="sxs-lookup"><span data-stu-id="35174-187">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="35174-188">若要了解有关本主题的详细信息，请参阅<a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。</span><span class="sxs-lookup"><span data-stu-id="35174-188">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="35174-189">单击“下一步”，然后在“MRTK 项目配置器”窗口中单击“完成”，完成 XRSDK 的 Unity 项目配置。</span><span class="sxs-lookup"><span data-stu-id="35174-189">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="35174-190">配置其他项目设置</span><span class="sxs-lookup"><span data-stu-id="35174-190">Configure additional project settings</span></span>

<span data-ttu-id="35174-191">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="35174-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="35174-192">在“项目设置”窗口中，选择“XR 插件管理” > “Windows Mixed Reality” > “运行时设置”，然后使用“深度缓冲格式”下拉列表选择“16 位深度” ：</span><span class="sxs-lookup"><span data-stu-id="35174-192">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Unity 启用 16 深度](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="35174-194">可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。</span><span class="sxs-lookup"><span data-stu-id="35174-194">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="35174-195">若要详细了解此主题，可参考 MRTK 的性能文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。</span><span class="sxs-lookup"><span data-stu-id="35174-195">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="35174-196">在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：</span><span class="sxs-lookup"><span data-stu-id="35174-196">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 发布设置。](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="35174-199">“包名称”是应用的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="35174-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="35174-200">在部署应用之前应更改此标识符，以免覆盖以前安装的应用。</span><span class="sxs-lookup"><span data-stu-id="35174-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="35174-201">“产品名称”是在 HoloLens“开始”菜单中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="35174-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="35174-202">要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。</span><span class="sxs-lookup"><span data-stu-id="35174-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="35174-203">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="35174-203">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="35174-204">打开“MixedRealityFeatureTool”后，单击“开始”以开始使用混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="35174-204">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="35174-205">第一步是使用省略号按钮将混合现实功能工具指向您的项目路径，单击项目路径旁边的三个点省略号按钮，然后在资源管理器中浏览到项目文件夹，例如 D:\MixedRealityLearning\MRTK Tutorials。</span><span class="sxs-lookup"><span data-stu-id="35174-205">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="35174-206">找到项目的文件夹后，单击“打开”按钮返回到混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="35174-206">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="35174-207">然后单击“发现功能”。</span><span class="sxs-lookup"><span data-stu-id="35174-207">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="35174-208">浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。</span><span class="sxs-lookup"><span data-stu-id="35174-208">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="35174-209">文件名必须有一个值才能使文件夹被选中。</span><span class="sxs-lookup"><span data-stu-id="35174-209">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="35174-210">混合现实功能工具执行验证以确保它已定向到 Unity 项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="35174-210">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="35174-211">文件夹必须包含资产、包和项目设置文件夹。</span><span class="sxs-lookup"><span data-stu-id="35174-211">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="35174-212">功能按类别进行了分组，以便于查找，单击“混合现实工具包”下拉列表，查找与混合现实工具包相关的包。</span><span class="sxs-lookup"><span data-stu-id="35174-212">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="35174-213">选中“混合现实工具包基础”，并单击其旁边的下拉列表以选择“MRTK 2.7.0”，然后单击“获取功能”按钮以下载所选的包。  </span><span class="sxs-lookup"><span data-stu-id="35174-213">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="35174-214">接下来，单击“验证”按钮以验证所选包，随即显示一个弹出窗口，其中显示消息“未检测到任何验证问题”，单击“确定”以关闭弹出窗口，然后单击“导入”按钮。</span><span class="sxs-lookup"><span data-stu-id="35174-214">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

<span data-ttu-id="35174-215">单击“批准”按钮，将“混合现实工具包”添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="35174-215">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="35174-216">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="35174-216">Configuring the Unity project</span></span>

<span data-ttu-id="35174-217">Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="35174-217">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="35174-218">如果未显示该窗口，请转到“混合现实” > “工具包” > “实用程序” > “为 MRTK 配置项目”：</span><span class="sxs-lookup"><span data-stu-id="35174-218">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Unity“配置 Unity 项目”菜单路径](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="35174-220">单击“旧版 XR”以启用旧版 XR，并将其所需的包添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="35174-220">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="35174-222">单击“下一步”按钮，为旧版 XR 启用 XR 管道设置。</span><span class="sxs-lookup"><span data-stu-id="35174-222">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Unity MRTK 配置窗口](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="35174-224">在“MRTK 项目配置器”窗口中，确保选中所有选项，同时使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：</span><span class="sxs-lookup"><span data-stu-id="35174-224">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 配置窗口](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="35174-226">可以根据需要决定是否应用 MRTK 默认设置，但强烈建议应用，因为它有助于配置以下推荐的 Unity 设置：</span><span class="sxs-lookup"><span data-stu-id="35174-226">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="35174-227">设置单通道实例化渲染路径：通过在同一绘制调用中执行双眼的渲染管道来提高图形性能。</span><span class="sxs-lookup"><span data-stu-id="35174-227">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="35174-228">若要了解有关此主题的更多信息，可以参考 MRTK 的[性能](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文档的[单通道实例化渲染](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)部分。</span><span class="sxs-lookup"><span data-stu-id="35174-228">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="35174-229">设置默认的空间感知层：创建名为空间感知的 Unity 层，并将 MRTK 配置为对空间感知网格使用该层。</span><span class="sxs-lookup"><span data-stu-id="35174-229">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="35174-230">若要详细了解 Unity 层，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自定义工作区</a>文档。</span><span class="sxs-lookup"><span data-stu-id="35174-230">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="35174-231">可以根据需要决定是否设置“音频空间定位器”属性，如果设置，可提高项目中的音频体验。</span><span class="sxs-lookup"><span data-stu-id="35174-231">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="35174-232">如果将其设置为“MS HRTF 空间定位器”，则启用 Unity 的 AudioSource.spatialize 属性时将使用此空间定位器插件。</span><span class="sxs-lookup"><span data-stu-id="35174-232">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="35174-233">若要了解有关本主题的详细信息，请参阅<a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">空间音频教程</a>。</span><span class="sxs-lookup"><span data-stu-id="35174-233">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="35174-234">单击“下一步”，然后在“MRTK 项目配置器”窗口中单击“完成”按钮，完成旧版 XR 的 Unity 项目配置。</span><span class="sxs-lookup"><span data-stu-id="35174-234">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="35174-235">配置其他项目设置</span><span class="sxs-lookup"><span data-stu-id="35174-235">Configure additional project settings</span></span>

<span data-ttu-id="35174-236">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="35174-236">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="35174-237">在“项目设置”窗口中，选择“播放器” > “XR 设置”，然后使用“深度格式”下拉列表选“16 位深度”   ：</span><span class="sxs-lookup"><span data-stu-id="35174-237">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 启用 16 深度](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="35174-239">可以根据需要决定是否将深度格式减小为 16 位，如果减小，可提高项目中的图形性能。</span><span class="sxs-lookup"><span data-stu-id="35174-239">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="35174-240">若要详细了解此主题，可参考 MRTK 的性能文档的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度缓冲区共享 (HoloLens)</a> 部分。</span><span class="sxs-lookup"><span data-stu-id="35174-240">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="35174-241">在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：</span><span class="sxs-lookup"><span data-stu-id="35174-241">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 发布设置。](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="35174-244">“包名称”是应用的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="35174-244">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="35174-245">在部署应用之前应更改此标识符，以免覆盖以前安装的应用。</span><span class="sxs-lookup"><span data-stu-id="35174-245">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="35174-246">“产品名称”是在 HoloLens“开始”菜单中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="35174-246">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="35174-247">要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。</span><span class="sxs-lookup"><span data-stu-id="35174-247">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
