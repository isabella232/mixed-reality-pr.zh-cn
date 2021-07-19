---
title: Azure 语音服务教程 - 1. 集成并使用语音识别和听录
description: 请完成本课程来了解如何在混合现实应用程序中实施 Azure 语音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, Azure 空间定位点, 语音识别, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 39eaa8a17d4616dc9c044f9bff7522dde41cffb7
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656628"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="9286f-105">1.集成并使用语音识别和听录</span><span class="sxs-lookup"><span data-stu-id="9286f-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="9286f-106">概述</span><span class="sxs-lookup"><span data-stu-id="9286f-106">Overview</span></span>

<span data-ttu-id="9286f-107">在本教程系列中，你将创建一个混合现实应用程序用于探索如何将 Azure 语音服务与 HoloLens 2 配合使用。</span><span class="sxs-lookup"><span data-stu-id="9286f-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="9286f-108">完成本教程系列后，你便可以使用设备的麦克风实时进行语音转文本的听录，将语音翻译成其他语言，并利用意向识别功能通过人工智能来理解语音命令。</span><span class="sxs-lookup"><span data-stu-id="9286f-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="9286f-109">目标</span><span class="sxs-lookup"><span data-stu-id="9286f-109">Objectives</span></span>

* <span data-ttu-id="9286f-110">了解如何将 Azure 语音服务与 HoloLens 2 应用程序相集成</span><span class="sxs-lookup"><span data-stu-id="9286f-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="9286f-111">了解如何使用语音识别来听录文本</span><span class="sxs-lookup"><span data-stu-id="9286f-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9286f-112">必备条件</span><span class="sxs-lookup"><span data-stu-id="9286f-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="9286f-113">如果你尚未完成[入门教程](mr-learning-base-01.md)系列，建议先完成这些教程。</span><span class="sxs-lookup"><span data-stu-id="9286f-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="9286f-114">一台 Windows 10 电脑，其中已[安装](../../install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="9286f-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="9286f-115">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="9286f-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9286f-116">一些基本的 C# 编程功能</span><span class="sxs-lookup"><span data-stu-id="9286f-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="9286f-117">一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="9286f-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="9286f-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2020/2019 LTS 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="9286f-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!Important]
> <span data-ttu-id="9286f-119">本系列教程支持 Unity 2020 LTS（当前版本 2020.3.x）（如果您使用 Open XR 或 Windows XR 插件）以及 Unity 2019 LTS（当前版本 2019.4.x）（如果您使用旧版 WSA 或 Windows XR 插件）。</span><span class="sxs-lookup"><span data-stu-id="9286f-119">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="9286f-120">这将取代上述链接的先决条件中所述的任何 Unity 版本要求。</span><span class="sxs-lookup"><span data-stu-id="9286f-120">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="9286f-121">创建和准备 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="9286f-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="9286f-122">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="9286f-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="9286f-123">为此，请先执行[初始化项目和第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：</span><span class="sxs-lookup"><span data-stu-id="9286f-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="9286f-124">[创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="9286f-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="9286f-125">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="9286f-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="9286f-126">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="9286f-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="9286f-127">导入混合现实工具包和配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="9286f-127">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="9286f-128">[创建并配置场景](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)，并为场景指定适当的名称，例如 AzureSpeechServices</span><span class="sxs-lookup"><span data-stu-id="9286f-128">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="9286f-129">然后，根据[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)说明，确保场景的 MRTK 配置配置文件为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡” 。</span><span class="sxs-lookup"><span data-stu-id="9286f-129">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="9286f-130">配置语音命令的启动行为</span><span class="sxs-lookup"><span data-stu-id="9286f-130">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="9286f-131">由于你要使用语音 SDK 进行语音识别和听录，因此需要配置 MRTK 语音命令，使其不会干扰语音 SDK 的功能。</span><span class="sxs-lookup"><span data-stu-id="9286f-131">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="9286f-132">为此，可将语音命令的启动行为从“自动启动”更改为“手动启动”。</span><span class="sxs-lookup"><span data-stu-id="9286f-132">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="9286f-133">在“层次结构”窗口中选择“MixedRealityToolkit”对象后，在“检查器”窗口中选择“输入”选项卡，克隆“DefaultHoloLens2InputSystemProfile”和“DefaultMixedRealitySpeechCommandsProfile”，然后将语音命令的“启动行为”更改为“手动启动”：     </span><span class="sxs-lookup"><span data-stu-id="9286f-133">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a><span data-ttu-id="9286f-135">配置功能</span><span class="sxs-lookup"><span data-stu-id="9286f-135">Configuring the capabilities</span></span>

<span data-ttu-id="9286f-136">在 Unity 菜单中，选择“编辑” > “项目设置...”打开“播放器设置”窗口，然后找到“播放器” >  “发布设置”部分：   </span><span class="sxs-lookup"><span data-stu-id="9286f-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="9286f-138">在“发布设置”中，向下滚动到“功能”部分，仔细检查在教程中最初创建项目时启用的“InternetClient”、“Microphone”和“SpatialPerception”功能是否确实已启用。    </span><span class="sxs-lookup"><span data-stu-id="9286f-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which was enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="9286f-139">然后启用“InternetClientServer”和“PrivateNetworkClientServer”功能： </span><span class="sxs-lookup"><span data-stu-id="9286f-139">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9286f-141">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="9286f-141">Importing the tutorial assets</span></span>

<span data-ttu-id="9286f-142">下载以下 Unity 自定义包，并 **按其列出顺序** 将其 **导入**：</span><span class="sxs-lookup"><span data-stu-id="9286f-142">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="9286f-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage)（最新版本）</span><span class="sxs-lookup"><span data-stu-id="9286f-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="9286f-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9286f-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="9286f-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9286f-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage</span></span>](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> <span data-ttu-id="9286f-146">有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mr-learning-base-04.md#importing-the-tutorial-assets)说明。</span><span class="sxs-lookup"><span data-stu-id="9286f-146">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

<span data-ttu-id="9286f-147">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="9286f-147">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

<span data-ttu-id="9286f-149">您需要设置 Unity 项目以发布 ARM64 的 Azure Speech 插件，为此，请在“项目”窗口中，导航到“资产” > “SpeechSDK” > “插件” > “WSA” > “ARM64，并选择“Microsoft.CognitiveServices.Speech.core”插件。</span><span class="sxs-lookup"><span data-stu-id="9286f-149">You need to setup the Unity project to publish the Azure Speech plugins for ARM64,to do this in the Project window, navigate to **Assets** > **SpeechSDK** > **Plugins** > **WSA** > **ARM64** and select **Microsoft.CognitiveServices.Speech.core** plugin.</span></span>

![mrlearning-speech 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

<span data-ttu-id="9286f-151">在仍然选中“Microsoft.CognitiveServices.Speech.core”插件的情况下，在检查器窗口中，启用“WSA 播放器”，然后在“平台设置”下面的 SDK 中选择“UWP”，CPU 中选择“ARM64”，然后单击“应用”以将这些设置应用到插件。   </span><span class="sxs-lookup"><span data-stu-id="9286f-151">with **Microsoft.CognitiveServices.Speech.core** plugin still selected, in the inspector window Enable **WSA Player** then under **Platform settings** select **UWP** for SDK, **ARM64** for CPU and click on Apply to apply these settings to the plugin.</span></span>

![mrlearning-speech 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

<span data-ttu-id="9286f-153">对其余所有插件重复这些步骤：</span><span class="sxs-lookup"><span data-stu-id="9286f-153">Repeat this steps for each of the remaining plugins:</span></span>

* <span data-ttu-id="9286f-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span><span class="sxs-lookup"><span data-stu-id="9286f-154">**Microsoft.CognitiveServices.Speech.extension.audio.sys**</span></span>
* <span data-ttu-id="9286f-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span><span class="sxs-lookup"><span data-stu-id="9286f-155">**Microsoft.CognitiveServices.Speech.extension.kws**</span></span>
* <span data-ttu-id="9286f-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span><span class="sxs-lookup"><span data-stu-id="9286f-156">**Microsoft.CognitiveServices.Speech.extension.lu**</span></span>
* <span data-ttu-id="9286f-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span><span class="sxs-lookup"><span data-stu-id="9286f-157">**Microsoft.CognitiveServices.Speech.extension.silk_codec**</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="9286f-158">准备场景</span><span class="sxs-lookup"><span data-stu-id="9286f-158">Preparing the scene</span></span>

<span data-ttu-id="9286f-159">在本部分，你将通过添加教程预制件来准备场景，并配置“Lunarcom 控制器(脚本)”组件来控制场景。</span><span class="sxs-lookup"><span data-stu-id="9286f-159">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="9286f-160">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpeechServices” > “预制件”文件夹，并将“Lunarcom”预制件拖放到“层次结构”窗口中，以将其添加到场景中：   </span><span class="sxs-lookup"><span data-stu-id="9286f-160">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="9286f-162">仍在“层次结构”窗口中选中了“Lunarcom”对象的情况下，在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 控制器(脚本)”组件添加到 Lunarcom 对象中：  </span><span class="sxs-lookup"><span data-stu-id="9286f-162">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="9286f-164">MRTK 中未包含“Lunarcom 控制器(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="9286f-164">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="9286f-165">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="9286f-165">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="9286f-166">在仍选中了“Lunarcom”对象的情况下，将其展开以显示其子对象，然后将“Terminal”对象拖放到“Lunarcom 控制器(脚本)”组件的“终端”字段中：  </span><span class="sxs-lookup"><span data-stu-id="9286f-166">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="9286f-168">在仍选中了“Lunarcom”对象的情况下，展开 Terminal 对象以显示其子对象，然后将“ConnectionLight”对象拖放到“Lunarcom 控制器(脚本)”组件的“连接光线”字段中，并将“OutputText”对象拖放到“输出文本”字段中：    </span><span class="sxs-lookup"><span data-stu-id="9286f-168">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="9286f-170">在仍选中了“Lunarcom”对象的情况下，展开 Buttons 对象以显示其子对象，然后在“检查器”窗口中展开“按钮”列表，将其“大小”设置为 3，并将“MicButton”、“SatelliteButton”和“RocketButton”对象分别拖放到“元素 0”、“元素 1”和“元素 2”字段中：      </span><span class="sxs-lookup"><span data-stu-id="9286f-170">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="9286f-172">将 Unity 项目连接到 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="9286f-172">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="9286f-173">若要使用 Azure 语音服务，需要创建一个 Azure 资源并获取语音服务的 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="9286f-173">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="9286f-174">按照“[免费试用语音服务](/azure/cognitive-services/speech-service/get-started)”中的说明进行操作，并记下服务区域（也称为“位置”）和 API 密钥（也称为“密钥 1”或“密钥 2”）。</span><span class="sxs-lookup"><span data-stu-id="9286f-174">Follow the [Try the Speech service for free](/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="9286f-175">在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中找到“Lunarcom 控制器(脚本)”组件的“语音 SDK 凭据”部分，并按如下所述对其进行配置：  </span><span class="sxs-lookup"><span data-stu-id="9286f-175">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="9286f-176">在“语音服务 API 密钥”字段中，输入你的 API 密钥（“密钥 1”或“密钥 2”）</span><span class="sxs-lookup"><span data-stu-id="9286f-176">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="9286f-177">在“语音服务区域”字段中，使用小写字母输入不带空格的服务区域（位置）</span><span class="sxs-lookup"><span data-stu-id="9286f-177">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="9286f-179">使用语音识别听录语音</span><span class="sxs-lookup"><span data-stu-id="9286f-179">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="9286f-180">在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 语音识别器(脚本)”组件添加到 Lunarcom 对象中：  </span><span class="sxs-lookup"><span data-stu-id="9286f-180">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9286f-182">MRTK 中未包含“Lunarcom 语音识别器(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="9286f-182">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="9286f-183">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="9286f-183">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="9286f-184">如果现在进入“游戏”模式，可以先按麦克风按钮来测试语音识别：</span><span class="sxs-lookup"><span data-stu-id="9286f-184">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="9286f-186">假设计算机上配备了麦克风，当你讲话时，会在终端面板上听录你的语音：</span><span class="sxs-lookup"><span data-stu-id="9286f-186">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="9286f-188">应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="9286f-188">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9286f-189">祝贺</span><span class="sxs-lookup"><span data-stu-id="9286f-189">Congratulations</span></span>

<span data-ttu-id="9286f-190">现已实现了由 Azure 提供支持的语音识别。</span><span class="sxs-lookup"><span data-stu-id="9286f-190">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="9286f-191">请在设备上运行该应用程序，以确保功能正常。</span><span class="sxs-lookup"><span data-stu-id="9286f-191">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="9286f-192">下一篇教程将介绍如何使用 Azure 语音识别执行命令。</span><span class="sxs-lookup"><span data-stu-id="9286f-192">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9286f-193">教程：2. 使用 Azure 语音识别执行命令</span><span class="sxs-lookup"><span data-stu-id="9286f-193">Next tutorial: 2. Execute commands using Azure speech recognition</span></span>](mrlearning-speechSDK-ch2.md)
