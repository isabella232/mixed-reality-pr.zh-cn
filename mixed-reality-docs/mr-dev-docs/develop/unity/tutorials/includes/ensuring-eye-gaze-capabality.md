---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097168"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="571d2-101">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="571d2-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="571d2-102">确保凝视输入功能并添加凝视数据提供程序</span><span class="sxs-lookup"><span data-stu-id="571d2-102">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="571d2-103">在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用眼睛凝视输入功能”是否灰显   ：</span><span class="sxs-lookup"><span data-stu-id="571d2-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity“MRTK 项目配置器”窗口](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="571d2-105">当你在本系列教程开头配置 Unity 项目时，[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#configuring-the-unity-project)指令期间应该已经启用了眼睛凝视输入功能。</span><span class="sxs-lookup"><span data-stu-id="571d2-105">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="571d2-106">但如果未启用此功能，请确保立即启用。</span><span class="sxs-lookup"><span data-stu-id="571d2-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="571d2-107">在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡：</span><span class="sxs-lookup"><span data-stu-id="571d2-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="571d2-108">展开“输入数据提供程序”，单击“+ 添加数据提供程序”按钮并添加新的数据提供程序 </span><span class="sxs-lookup"><span data-stu-id="571d2-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![添加凝视数据提供程序 1](../images/mr-learning-base/base-08-section1-step1-2.png)

<span data-ttu-id="571d2-110">将 Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input >  WindowsMixedRealityEyeGazeProvider 分配给新数据提供程序的 Type 字段。</span><span class="sxs-lookup"><span data-stu-id="571d2-110">Assign **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![添加凝视数据提供程序 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="571d2-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="571d2-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="571d2-113">确保凝视输入功能并添加凝视数据提供程序</span><span class="sxs-lookup"><span data-stu-id="571d2-113">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="571d2-114">在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡：</span><span class="sxs-lookup"><span data-stu-id="571d2-114">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="571d2-115">展开“输入数据提供程序”，单击“+ 添加数据提供程序”按钮并添加新的数据提供程序 </span><span class="sxs-lookup"><span data-stu-id="571d2-115">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![添加凝视数据提供程序 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

<span data-ttu-id="571d2-117">将 Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input >  WindowsMixedRealityEyeGazeProvider 分配给新数据提供程序的 Type 字段。</span><span class="sxs-lookup"><span data-stu-id="571d2-117">Assign **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![添加凝视数据提供程序 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="571d2-119">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="571d2-119">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="571d2-120">确保启用了“眼睛凝视输入”功能</span><span class="sxs-lookup"><span data-stu-id="571d2-120">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="571d2-121">在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用眼睛凝视输入功能”是否灰显   ：</span><span class="sxs-lookup"><span data-stu-id="571d2-121">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity“MRTK 项目配置器”窗口](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="571d2-123">当你在本系列教程开头配置 Unity 项目时，[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指令期间应该已经启用了眼睛凝视输入功能。</span><span class="sxs-lookup"><span data-stu-id="571d2-123">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="571d2-124">但如果未启用此功能，请确保立即启用。</span><span class="sxs-lookup"><span data-stu-id="571d2-124">However, if it is not enabled, make sure you enable it now.</span></span>
