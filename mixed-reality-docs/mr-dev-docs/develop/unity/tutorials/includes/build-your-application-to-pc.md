---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392533"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="aabde-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="aabde-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-switching-build-platform"></a><span data-ttu-id="aabde-102">1. 切换生成平台</span><span class="sxs-lookup"><span data-stu-id="aabde-102">1. Switching Build Platform</span></span>

<span data-ttu-id="aabde-103">在 Unity 菜单中选择“文件”>“生成设置”，打开“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="aabde-103">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="aabde-104">在“生成设置”窗口中，选择“PC、Mac 和 Linux 单机”，然后单击“切换平台”按钮以更改生成平台： </span><span class="sxs-lookup"><span data-stu-id="aabde-104">In the Build Settings window, select **PC, Mac & Linux Standalone** Platform and click the **Switch Platform** button to change the Build Platform:</span></span>

![切换生成平台](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

<span data-ttu-id="aabde-106">当 Unity 完成平台切换后，单击 x 图标，关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="aabde-106">When Unity has finished switching the platform, click the x icon to close the Build Settings window.</span></span>

### <a name="2-set-the-project-settings"></a><span data-ttu-id="aabde-107">2. 设置项目设置</span><span class="sxs-lookup"><span data-stu-id="aabde-107">2. Set the project settings</span></span>

<span data-ttu-id="aabde-108">在 Unity 菜单中，选择“编辑” > “项目设置” > “XR 插件管理”，以确保您位于“Windows 单机”选项卡中，然后选中“OpenXR”和“Windows Mixed Reality 功能集”复选框。    </span><span class="sxs-lookup"><span data-stu-id="aabde-108">In the Unity menu, select **Edit** > **Project Settings** > **XR Plug-in Management** ensure that you are in Windows Standalone tab and check the **OpenXR** and **Windows Mixed Reality feature set** checkbox.</span></span>

![启用 OpenXR 和 Windows Mixed Reality 功能集](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

<span data-ttu-id="aabde-110">在“项目设置”窗口中，选择“OpenXR”，并确保您位于“Windows 单机”选项卡中，将“深度提交模式”从“无”更改为“深度 16 位”。  </span><span class="sxs-lookup"><span data-stu-id="aabde-110">In Project Settings window, select **OpenXR** and ensure that you are in Windows Standalone tab and change the **Depth submission mode** from None to **Depth 16 Bit**.</span></span>

<span data-ttu-id="aabde-111">在交互配置文件选项卡中，单击 + 符号添加“目视交互配置文件”和“Microsoft 手部交互配置文件”。</span><span class="sxs-lookup"><span data-stu-id="aabde-111">In interaction profiles tab add **Eye Gaze Interaction Profile** and **Microsoft Hand Interaction Profile** by clicking on the + symbol.</span></span>

![添加目视交互配置文件和 Microsoft 手部交互配置文件](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

<span data-ttu-id="aabde-113">在“打开 XR 功能组” > “所有功能”下面，选中“全息应用远程处理”复选框。</span><span class="sxs-lookup"><span data-stu-id="aabde-113">Under **Open XR feature groups** > **All features** > check the **Holographic App Remoting** checkbox.</span></span>

![启用全息应用远程处理](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

<span data-ttu-id="aabde-115">接下来选中“Windows Mixed Reality”复选框，并在 Windows Mixed Reality 组下选择“全息应用远程处理”复选框。</span><span class="sxs-lookup"><span data-stu-id="aabde-115">next select the **Windows Mixed Reality**  check box and under Windows Mixed Reality group select the  **Holographic App Remoting** checkbox.</span></span>

![启用 Windows Mixed Reality 全息应用远程处理](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a><span data-ttu-id="aabde-117">3. 生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="aabde-117">3. Build the Unity Project</span></span>

<span data-ttu-id="aabde-118">在 Unity 菜单中选择“文件”>“生成设置”，打开“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="aabde-118">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="aabde-119">在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“场景”中。</span><span class="sxs-lookup"><span data-stu-id="aabde-119">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="aabde-120">在“生成”列表中，单击“生成”按钮：</span><span class="sxs-lookup"><span data-stu-id="aabde-120">In the Build list, then click the _ *Build*\* button:</span></span>

![添加了场景的 Unity“生成设置”窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

<span data-ttu-id="aabde-122">选择合适的位置来存储您生成的项目，例如 Documents\MixedRealityLearning。</span><span class="sxs-lookup"><span data-stu-id="aabde-122">choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="aabde-123">创建一个新文件夹并为其指定合适的名称，例如 PCHolographicRemoting。</span><span class="sxs-lookup"><span data-stu-id="aabde-123">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="aabde-124">然后单击“选择文件夹”按钮，开始生成过程：</span><span class="sxs-lookup"><span data-stu-id="aabde-124">Then click the ***Select Folder*** button to start the build process:</span></span>

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

<span data-ttu-id="aabde-126">等待 Unity 完成生成过程。</span><span class="sxs-lookup"><span data-stu-id="aabde-126">Wait for Unity to finish the build process.</span></span>

![Unity 正在生成进程](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

<span data-ttu-id="aabde-128">双击可执行文件，在 PC 中打开 PC 全息远程处理应用程序。</span><span class="sxs-lookup"><span data-stu-id="aabde-128">double click on the Executable file to open the PC Holographic Remoting Application in your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="aabde-129">由于作为 UWP 生成的 PC 全息远程处理应用存在一些已知问题，我们正在将 PC 应用生成为 OpenXR Windows 单机。</span><span class="sxs-lookup"><span data-stu-id="aabde-129">Due to some known issues in Holographic Remoting for PC app Built as UWP we are Building the PC App as Windows Standalone for OpenXR.</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="aabde-130">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="aabde-130">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-set-the-player-settings"></a><span data-ttu-id="aabde-131">1.设置播放器设置</span><span class="sxs-lookup"><span data-stu-id="aabde-131">1. Set the player settings</span></span>

<span data-ttu-id="aabde-132">在“XR 设置”部分，选中“支持的 WSA 全息远程处理”复选框，启用全息远程处理 。</span><span class="sxs-lookup"><span data-stu-id="aabde-132">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![启用了“支持 WSA 全息远程处理”的 Unity XR 设置窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="aabde-134">2.生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="aabde-134">2. Build the Unity Project</span></span>

<span data-ttu-id="aabde-135">在 Unity 菜单中选择“文件”>“生成设置”，打开“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="aabde-135">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="aabde-136">在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“场景”中。</span><span class="sxs-lookup"><span data-stu-id="aabde-136">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="aabde-137">在“生成”列表中，单击“生成”按钮以打开“生成通用 Windows 平台”窗口：</span><span class="sxs-lookup"><span data-stu-id="aabde-137">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![添加了场景的 Unity“生成设置”窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="aabde-139">在“生成通用 Windows 平台”窗口中，选择一个合适的位置来存储生成结果，例如 Documents\MixedRealityLearning。</span><span class="sxs-lookup"><span data-stu-id="aabde-139">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="aabde-140">创建一个新文件夹并为其指定合适的名称，例如 PCHolographicRemoting。</span><span class="sxs-lookup"><span data-stu-id="aabde-140">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="aabde-141">然后单击“选择文件夹”按钮，开始生成过程：</span><span class="sxs-lookup"><span data-stu-id="aabde-141">Then click the ***Select Folder*** button to start the build process:</span></span>

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="aabde-143">等待 Unity 完成生成过程。</span><span class="sxs-lookup"><span data-stu-id="aabde-143">Wait for Unity to finish the build process.</span></span>

![Unity 正在生成进程](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="aabde-145">3.生成并部署应用程序</span><span class="sxs-lookup"><span data-stu-id="aabde-145">3. Build and deploy the application</span></span>

<span data-ttu-id="aabde-146">生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。</span><span class="sxs-lookup"><span data-stu-id="aabde-146">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="aabde-147">在文件夹内导航，然后双击 .sln 文件，在 Visual Studio 中其打开：</span><span class="sxs-lookup"><span data-stu-id="aabde-147">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![选中了新建的“Visual Studio 解决方案”的 Windows 资源管理器](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="aabde-149">如果 Visual Studio 要求安装新组件，请花一点时间确保按照安装工具文档中的说明安装所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="aabde-149">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="aabde-150">通过选择“发布配置”、“x64 体系结构”和“本地计算机”作为目标，配置 PC 版 Visual Studio：</span><span class="sxs-lookup"><span data-stu-id="aabde-150">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![配置了“本地计算机”的 Visual Studio](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="aabde-152">单击“本地计算机”按钮。</span><span class="sxs-lookup"><span data-stu-id="aabde-152">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="aabde-153">它会开始生成应用程序并将其部署到你的电脑。</span><span class="sxs-lookup"><span data-stu-id="aabde-153">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="aabde-154">该应用程序将默认安装在你的电脑中。</span><span class="sxs-lookup"><span data-stu-id="aabde-154">The application will be installed in your PC by default.</span></span>
