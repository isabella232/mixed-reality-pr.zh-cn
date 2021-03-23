---
title: 创建全息远程处理电脑应用程序
description: 完成本课程可以了解如何创建电脑应用程序来远程处理从电脑到 HoloLens 2 的混合现实体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 电脑全息远程处理, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: 916a9396c0b29637d5619bac203718e05112b598
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590299"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="7e82d-104">2.创建全息远程处理电脑应用程序</span><span class="sxs-lookup"><span data-stu-id="7e82d-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="7e82d-105">本教程将介绍如何创建用于全息远程处理的电脑应用并随时连接到 HoloLens 2，从而提供一种在混合现实中直观显示 3D 内容的方式。</span><span class="sxs-lookup"><span data-stu-id="7e82d-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="7e82d-106">目标</span><span class="sxs-lookup"><span data-stu-id="7e82d-106">Objectives</span></span>

* <span data-ttu-id="7e82d-107">为全息远程处理配置 Unity</span><span class="sxs-lookup"><span data-stu-id="7e82d-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="7e82d-108">了解如何通过 Visual Studio 生成和部署应用程序</span><span class="sxs-lookup"><span data-stu-id="7e82d-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="7e82d-109">开发全息远程处理应用程序并连接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="7e82d-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="7e82d-110">为全息远程处理配置场景</span><span class="sxs-lookup"><span data-stu-id="7e82d-110">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="7e82d-111">在本部分，你将配置项目，以通过 Wi-Fi 连接将电脑上的混合现实体验实时流式传输到 HoloLens 2 设备。</span><span class="sxs-lookup"><span data-stu-id="7e82d-111">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="7e82d-112">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.PCHolograhicRemoting” > “预制件”文件夹，然后单击“HolographicRemoting”预制件并将其拖放到场景中   。</span><span class="sxs-lookup"><span data-stu-id="7e82d-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![新增的 HolographicRemoting 预制件仍处于选中状态的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="7e82d-114">在电脑上构建应用程序</span><span class="sxs-lookup"><span data-stu-id="7e82d-114">Build your application to PC</span></span>

<span data-ttu-id="7e82d-115">全息远程处理应用现可在你的电脑上生成内容。</span><span class="sxs-lookup"><span data-stu-id="7e82d-115">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="7e82d-116">请按照以下步骤进行这些更改，以在电脑上构建该应用程序。</span><span class="sxs-lookup"><span data-stu-id="7e82d-116">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="7e82d-117">1.设置播放器设置</span><span class="sxs-lookup"><span data-stu-id="7e82d-117">1. Set the player settings</span></span>

<span data-ttu-id="7e82d-118">在 Unity 菜单中选择“编辑”>“项目设置”，打开“播放器设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="7e82d-118">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="7e82d-119">在“项目设置”窗口中，展开“发布设置”，向下滚动到“功能”部分，然后选择下面除现有功能外显示的功能复选框 。</span><span class="sxs-lookup"><span data-stu-id="7e82d-119">In the Project Settings window, expand the **Publishing Settings**, scroll down to the **Capabilities** section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="7e82d-120">Internet 客户端服务器</span><span class="sxs-lookup"><span data-stu-id="7e82d-120">Internet Clint server</span></span>
* <span data-ttu-id="7e82d-121">专用网络客户端服务器</span><span class="sxs-lookup"><span data-stu-id="7e82d-121">Private Network Client Server</span></span>

<span data-ttu-id="7e82d-122">在“XR 设置”部分，选中“支持的 WSA 全息远程处理”复选框，启用全息远程处理 。</span><span class="sxs-lookup"><span data-stu-id="7e82d-122">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![启用了“支持 WSA 全息远程处理”的 Unity XR 设置窗口](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="7e82d-124">2.生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="7e82d-124">2. Build the Unity Project</span></span>

<span data-ttu-id="7e82d-125">在 Unity 菜单中选择“文件”>“生成设置”，打开“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="7e82d-125">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="7e82d-126">在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“场景”中。</span><span class="sxs-lookup"><span data-stu-id="7e82d-126">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="7e82d-127">在“生成”列表中，单击“生成”按钮以打开“生成通用 Windows 平台”窗口：</span><span class="sxs-lookup"><span data-stu-id="7e82d-127">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![添加了场景的 Unity“生成设置”窗口](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="7e82d-129">在“生成通用 Windows 平台”窗口中，选择一个合适的位置来存储生成结果，例如 Documents\MixedRealityLearning。</span><span class="sxs-lookup"><span data-stu-id="7e82d-129">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="7e82d-130">创建一个新文件夹并为其指定合适的名称，例如 PCHolographicRemoting。</span><span class="sxs-lookup"><span data-stu-id="7e82d-130">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="7e82d-131">然后单击“选择文件夹”按钮，开始生成过程：</span><span class="sxs-lookup"><span data-stu-id="7e82d-131">Then click the ***Select Folder*** button to start the build process:</span></span>

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="7e82d-133">等待 Unity 完成生成过程。</span><span class="sxs-lookup"><span data-stu-id="7e82d-133">Wait for Unity to finish the build process.</span></span>

![Unity 正在生成进程](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="7e82d-135">3.生成并部署应用程序</span><span class="sxs-lookup"><span data-stu-id="7e82d-135">3. Build and deploy the application</span></span>

<span data-ttu-id="7e82d-136">生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。</span><span class="sxs-lookup"><span data-stu-id="7e82d-136">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="7e82d-137">在文件夹内导航，然后双击 .sln 文件，在 Visual Studio 中其打开：</span><span class="sxs-lookup"><span data-stu-id="7e82d-137">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![选中了新建的“Visual Studio 解决方案”的 Windows 资源管理器](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="7e82d-139">如果 Visual Studio 要求安装新组件，请花一点时间确保按照安装工具文档中的说明安装所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="7e82d-139">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="7e82d-140">通过选择“发布配置”、“x64 体系结构”和“本地计算机”作为目标，配置 PC 版 Visual Studio：</span><span class="sxs-lookup"><span data-stu-id="7e82d-140">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![配置了“本地计算机”的 Visual Studio](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="7e82d-142">单击“本地计算机”按钮。</span><span class="sxs-lookup"><span data-stu-id="7e82d-142">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="7e82d-143">它会开始生成应用程序并将其部署到你的电脑。</span><span class="sxs-lookup"><span data-stu-id="7e82d-143">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="7e82d-144">该应用程序将默认安装在你的电脑中。</span><span class="sxs-lookup"><span data-stu-id="7e82d-144">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="7e82d-145">测试“全息远程处理”远程应用程序</span><span class="sxs-lookup"><span data-stu-id="7e82d-145">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="7e82d-146">若要将电脑应用程序连接到 HoloLens 2，请执行以下过程：</span><span class="sxs-lookup"><span data-stu-id="7e82d-146">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="7e82d-147">1.在 HoloLens 2 设备上安装“远程播放器”应用程序</span><span class="sxs-lookup"><span data-stu-id="7e82d-147">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="7e82d-148">在 HoloLens 2 上，访问 Store 应用并搜索“远程播放器”。</span><span class="sxs-lookup"><span data-stu-id="7e82d-148">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="7e82d-149">选择“远程播放器”应用。</span><span class="sxs-lookup"><span data-stu-id="7e82d-149">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="7e82d-150">点击“安装”，下载并安装该应用。</span><span class="sxs-lookup"><span data-stu-id="7e82d-150">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="7e82d-151">2.将全息远程处理电脑应用连接到远程播放器</span><span class="sxs-lookup"><span data-stu-id="7e82d-151">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="7e82d-152">在 HoloLens 上启动“远程播放器”。</span><span class="sxs-lookup"><span data-stu-id="7e82d-152">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="7e82d-153">记下 HoloLens IP 地址。</span><span class="sxs-lookup"><span data-stu-id="7e82d-153">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="7e82d-154">远程播放器启动后，会立即将其显示为全息图。</span><span class="sxs-lookup"><span data-stu-id="7e82d-154">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="7e82d-155">在电脑上打开全息远程处理电脑应用程序。</span><span class="sxs-lookup"><span data-stu-id="7e82d-155">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="7e82d-156">启动该应用程序后，输入 IP 地址，然后单击“连接”按钮进行连接 。</span><span class="sxs-lookup"><span data-stu-id="7e82d-156">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7e82d-157">祝贺</span><span class="sxs-lookup"><span data-stu-id="7e82d-157">Congratulations</span></span>

<span data-ttu-id="7e82d-158">本教程介绍了如何创建全息远程处理远程应用并随时连接到 HoloLens 2，从而提供一种在混合现实中直观显示 3D 内容的方式。</span><span class="sxs-lookup"><span data-stu-id="7e82d-158">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="7e82d-159">将 HoloLens 连接到全息远程处理电脑应用程序后，你应该会看到混合现实体验流式传输到 HoloLens 2 设备。</span><span class="sxs-lookup"><span data-stu-id="7e82d-159">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
