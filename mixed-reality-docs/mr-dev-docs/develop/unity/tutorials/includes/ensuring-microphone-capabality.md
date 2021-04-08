---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098034"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="95cda-101">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="95cda-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="95cda-102">确保麦克风功能并添加语音输入数据提供程序</span><span class="sxs-lookup"><span data-stu-id="95cda-102">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="95cda-103">在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：</span><span class="sxs-lookup"><span data-stu-id="95cda-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![启用麦克风功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="95cda-105">在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#configuring-the-unity-project)指令期间，应该已经启用了麦克风功能。</span><span class="sxs-lookup"><span data-stu-id="95cda-105">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="95cda-106">但如果未启用此功能，请确保立即启用。</span><span class="sxs-lookup"><span data-stu-id="95cda-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="95cda-107">在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡：</span><span class="sxs-lookup"><span data-stu-id="95cda-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="95cda-108">展开“输入数据提供程序”，单击“+ 添加数据提供程序”按钮并添加新的数据提供程序 </span><span class="sxs-lookup"><span data-stu-id="95cda-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![用于添加新语音命令的数据提供程序](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="95cda-110">将 Microsoft.MixedReality.ToolKit.Windows.Input >  WindowsSpeechInputProvider 分配给新数据提供程序的 Type 字段。</span><span class="sxs-lookup"><span data-stu-id="95cda-110">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![添加新语音命令设置](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="95cda-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="95cda-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="95cda-113">确保麦克风功能并添加语音输入数据提供程序</span><span class="sxs-lookup"><span data-stu-id="95cda-113">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="95cda-114">在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：</span><span class="sxs-lookup"><span data-stu-id="95cda-114">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![为 OpenXR 启用麦克风功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="95cda-116">在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#configuring-the-unity-project)指令期间，应该已经启用了麦克风功能。</span><span class="sxs-lookup"><span data-stu-id="95cda-116">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="95cda-117">但如果未启用此功能，请确保立即启用。</span><span class="sxs-lookup"><span data-stu-id="95cda-117">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="95cda-118">在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡：</span><span class="sxs-lookup"><span data-stu-id="95cda-118">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="95cda-119">展开“输入数据提供程序”，单击“+ 添加数据提供程序”按钮并添加新的数据提供程序 </span><span class="sxs-lookup"><span data-stu-id="95cda-119">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![为 OpenXR 添加新语音命令](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="95cda-121">将 Microsoft.MixedReality.ToolKit.Windows.Input >  WindowsSpeechInputProvider 分配给新数据提供程序的 Type 字段。</span><span class="sxs-lookup"><span data-stu-id="95cda-121">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![为 OpenXR 添加新语音命令设置](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="95cda-123">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="95cda-123">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="95cda-124">确保启用麦克风功能</span><span class="sxs-lookup"><span data-stu-id="95cda-124">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="95cda-125">在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：</span><span class="sxs-lookup"><span data-stu-id="95cda-125">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![启用麦克风功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="95cda-127">在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指令期间，应该已经启用了麦克风功能。</span><span class="sxs-lookup"><span data-stu-id="95cda-127">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="95cda-128">但如果未启用此功能，请确保立即启用。</span><span class="sxs-lookup"><span data-stu-id="95cda-128">However, if it is not enabled, make sure you enable it now.</span></span>
