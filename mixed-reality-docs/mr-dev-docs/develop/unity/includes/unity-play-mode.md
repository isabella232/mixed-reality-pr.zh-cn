---
ms.openlocfilehash: 40d24083ec83b9d6faebc00cf801d1f6f55fddd7
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392286"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8cdaa-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8cdaa-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

1. <span data-ttu-id="8cdaa-102">在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-102">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="8cdaa-103">在 HoloLens 上，启动 **全息远程处理播放器** 应用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-103">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="8cdaa-104">在 Unity 中，转到"编辑 **"菜单**，然后选择"**项目设置"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-104">In Unity, go to the **Edit** menu and select **Project Settings**.</span></span>
1. <span data-ttu-id="8cdaa-105">选择 **"XR 插件管理"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-105">Select **XR Plug-in Management**.</span></span>
1. <span data-ttu-id="8cdaa-106">确保选中 **"Windows** 独立"选项卡，在列表中找到 **"OpenXR"Windows Mixed Reality"** 功能集，并选中其复选框。 </span><span class="sxs-lookup"><span data-stu-id="8cdaa-106">Ensure the **Windows Standalone** tab is selected, find **OpenXR** and **Windows Mixed Reality feature set** in the list, and check their checkboxes.</span></span>
1. <span data-ttu-id="8cdaa-107">接下来，转到"**窗口"** 菜单，展开 **XR** 子菜单，然后选择 **"OpenXR 编辑器远程处理"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-107">Next, go to the **Window** menu, expand the **XR** submenu, and select **OpenXR Editor Remoting**.</span></span>

    ![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](../images/openxr-features-img-02.png)

1. <span data-ttu-id="8cdaa-109">单击 **"启用编辑器远程处理"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-109">Click **Enable Editor Remoting**.</span></span>

    ![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了"功能"](../images/openxr-features-img-03.png)

1. <span data-ttu-id="8cdaa-111">如果显示 **"启用缺少依赖项"** 按钮，则也单击该按钮。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-111">If the **Enable Missing Dependencies** button appears, click that as well.</span></span> <span data-ttu-id="8cdaa-112">按钮上方的错误框描述了它启用的功能以及原因。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-112">The error box above the button describes the features it's enabling and why.</span></span>
1. <span data-ttu-id="8cdaa-113">对于 **"远程主机名**"，请输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-113">For **Remote Host Name**, enter the IP address of your HoloLens.</span></span>
   1. <span data-ttu-id="8cdaa-114">根据需要更改其他设置。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-114">Change other settings as needed.</span></span>
   1. <span data-ttu-id="8cdaa-115">启动播放模式后，编辑器将尝试连接。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-115">The editor will attempt to connect once Play Mode is started.</span></span>
1. <span data-ttu-id="8cdaa-116">选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-116">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span> <span data-ttu-id="8cdaa-117">若要在播放模式下调试 C# 脚本，[请将Visual Studio附加到 Unity。](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)</span><span class="sxs-lookup"><span data-stu-id="8cdaa-117">To debug C# scripts in play mode, [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).</span></span>

> [!NOTE]
> <span data-ttu-id="8cdaa-118">从版本 0.1.0 起，全息远程处理运行时不支持定位点，ARAnchorManager 功能将不能通过远程处理工作。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-118">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="8cdaa-119">此功能将在未来版本中推出。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-119">This feature is coming in future releases.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="8cdaa-120">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="8cdaa-120">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

1. <span data-ttu-id="8cdaa-121">在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-121">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="8cdaa-122">在 HoloLens 上，启动 **全息远程处理播放器** 应用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-122">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="8cdaa-123">在 Unity 中，转到"编辑 **"菜单**，然后选择"**项目设置"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-123">In Unity, go to the **Edit** menu and select **Project Settings**.</span></span>
1. <span data-ttu-id="8cdaa-124">选择 **"XR 插件管理"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-124">Select **XR Plug-in Management**.</span></span>
1. <span data-ttu-id="8cdaa-125">确保选中 **"Windows** 独立"选项卡 **，Windows Mixed Reality列表中** 找到该选项卡，并选中其复选框。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-125">Ensure the **Windows Standalone** tab is selected, find **Windows Mixed Reality** in the list, and check its checkbox.</span></span>
1. <span data-ttu-id="8cdaa-126">接下来，转到"**窗口"** 菜单，展开 **XR** 子菜单，然后选择 **"Windows XR 插件远程处理"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-126">Next, go to the **Window** menu, expand the **XR** submenu, and select **Windows XR Plugin Remoting**.</span></span>
1. <span data-ttu-id="8cdaa-127">将 **仿真模式设置为\*\*\*\*"远程"到"设备"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-127">Set **Emulation Mode** to **Remote to Device**.</span></span>
1. <span data-ttu-id="8cdaa-128">对于 **"远程计算机**"，请输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-128">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
1. <span data-ttu-id="8cdaa-129">若要连接，请进行连接：</span><span class="sxs-lookup"><span data-stu-id="8cdaa-129">To connect, either:</span></span>
   1. <span data-ttu-id="8cdaa-130">若要手动连接，请取消选中"**播放时连接"，** 然后选择"连接 **"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-130">To manually connect, uncheck **Connect on Play**, and select **Connect**.</span></span> <span data-ttu-id="8cdaa-131">应会看到" **连接状态"** 更改为"已 **连接"，** 并且看到屏幕在 HoloLens 中为空白。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-131">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
   1. <span data-ttu-id="8cdaa-132">若要自动连接，请选中"**播放时连接"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-132">To automatically connect, check **Connect on Play**.</span></span> <span data-ttu-id="8cdaa-133">启动播放模式后，编辑器将尝试连接。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-133">The editor will attempt to connect once Play Mode is started.</span></span>
1. <span data-ttu-id="8cdaa-134">选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-134">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span> <span data-ttu-id="8cdaa-135">若要在播放模式下调试 C# 脚本，[请将Visual Studio附加到 Unity。](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)</span><span class="sxs-lookup"><span data-stu-id="8cdaa-135">To debug C# scripts in play mode, [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="8cdaa-136">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="8cdaa-136">Legacy WSA</span></span>](#tab/wsa)

1. <span data-ttu-id="8cdaa-137">在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-137">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="8cdaa-138">在 HoloLens 上，启动 **全息远程处理播放器** 应用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-138">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="8cdaa-139">在 Unity 中，转到"**窗口**"菜单，展开 **XR** 子菜单，然后选择"全息仿真" (在 Unity 2019) 中标记为已弃用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-139">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation** (marked as deprecated in Unity 2019).</span></span>
1. <span data-ttu-id="8cdaa-140">将 **仿真模式设置为\*\*\*\*"远程"到"设备"。**</span><span class="sxs-lookup"><span data-stu-id="8cdaa-140">Set **Emulation Mode** to **Remote to Device**.</span></span>
1. <span data-ttu-id="8cdaa-141">如果 **使用的是第一** 代 HoloLens 或设备，根据设备版本HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-141">Set **Device Version** according to if you're using a first generation HoloLens or a HoloLens 2.</span></span>
1. <span data-ttu-id="8cdaa-142">对于 **"远程计算机**"，请输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-142">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
1. <span data-ttu-id="8cdaa-143">选择“连接”  。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-143">Select **Connect**.</span></span> <span data-ttu-id="8cdaa-144">应会看到" **连接状态"** 更改为"已 **连接"，** 并且看到屏幕在 HoloLens 中为空白。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-144">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
1. <span data-ttu-id="8cdaa-145">选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。</span><span class="sxs-lookup"><span data-stu-id="8cdaa-145">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span> <span data-ttu-id="8cdaa-146">若要在播放模式下调试 C# 脚本，[请将Visual Studio附加到 Unity。](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)</span><span class="sxs-lookup"><span data-stu-id="8cdaa-146">To debug C# scripts in play mode, [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).</span></span>
