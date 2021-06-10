---
ms.openlocfilehash: 17719d2547aa10981e7b8cdf0d2c7d56823e6da5
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345102"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="77095-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="77095-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

1. <span data-ttu-id="77095-102">在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="77095-102">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="77095-103">在 HoloLens 上，启动 **全息远程处理播放器** 应用。</span><span class="sxs-lookup"><span data-stu-id="77095-103">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="77095-104">在 Unity 中，转到"编辑 **"菜单**，然后选择"**项目设置"。**</span><span class="sxs-lookup"><span data-stu-id="77095-104">In Unity, go to the **Edit** menu and select **Project Settings**.</span></span>
1. <span data-ttu-id="77095-105">选择 **"XR 插件管理"。**</span><span class="sxs-lookup"><span data-stu-id="77095-105">Select **XR Plug-in Management**.</span></span>
1. <span data-ttu-id="77095-106">确保选中 **"Windows** 独立"选项卡，在列表中找到 **"OpenXR"Windows Mixed Reality"** 功能集，并选中其复选框。 </span><span class="sxs-lookup"><span data-stu-id="77095-106">Ensure the **Windows Standalone** tab is selected, find **OpenXR** and **Windows Mixed Reality feature set** in the list, and check their checkboxes.</span></span>
1. <span data-ttu-id="77095-107">接下来，转到"**窗口"** 菜单，展开 **XR** 子菜单，然后选择 **"OpenXR 编辑器远程处理"。**</span><span class="sxs-lookup"><span data-stu-id="77095-107">Next, go to the **Window** menu, expand the **XR** submenu, and select **OpenXR Editor Remoting**.</span></span>
1. <span data-ttu-id="77095-108">单击 **"启用编辑器远程处理"。**</span><span class="sxs-lookup"><span data-stu-id="77095-108">Click **Enable Editor Remoting**.</span></span>
1. <span data-ttu-id="77095-109">如果显示 **"启用缺少依赖项"** 按钮，则也单击该按钮。</span><span class="sxs-lookup"><span data-stu-id="77095-109">If the **Enable Missing Dependencies** button appears, click that as well.</span></span> <span data-ttu-id="77095-110">按钮上方的错误框描述了它启用的功能以及原因。</span><span class="sxs-lookup"><span data-stu-id="77095-110">The error box above the button describes the features it's enabling and why.</span></span>
1. <span data-ttu-id="77095-111">对于 **"远程主机名**"，请输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="77095-111">For **Remote Host Name**, enter the IP address of your HoloLens.</span></span>
   1. <span data-ttu-id="77095-112">根据需要更改其他设置。</span><span class="sxs-lookup"><span data-stu-id="77095-112">Change other settings as needed.</span></span>
   1. <span data-ttu-id="77095-113">启动播放模式后，编辑器将尝试连接。</span><span class="sxs-lookup"><span data-stu-id="77095-113">The editor will attempt to connect once Play Mode is started.</span></span>
1. <span data-ttu-id="77095-114">选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。</span><span class="sxs-lookup"><span data-stu-id="77095-114">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="77095-115">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="77095-115">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

1. <span data-ttu-id="77095-116">在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="77095-116">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="77095-117">在 HoloLens 上，启动 **全息远程处理播放器** 应用。</span><span class="sxs-lookup"><span data-stu-id="77095-117">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="77095-118">在 Unity 中，转到"编辑 **"菜单**，然后选择"**项目设置"。**</span><span class="sxs-lookup"><span data-stu-id="77095-118">In Unity, go to the **Edit** menu and select **Project Settings**.</span></span>
1. <span data-ttu-id="77095-119">选择 **"XR 插件管理"。**</span><span class="sxs-lookup"><span data-stu-id="77095-119">Select **XR Plug-in Management**.</span></span>
1. <span data-ttu-id="77095-120">确保选中 **"Windows** 独立"选项卡 **，Windows Mixed Reality列表中** 找到该选项卡，并选中其复选框。</span><span class="sxs-lookup"><span data-stu-id="77095-120">Ensure the **Windows Standalone** tab is selected, find **Windows Mixed Reality** in the list, and check its checkbox.</span></span>
1. <span data-ttu-id="77095-121">接下来，转到"**窗口"** 菜单，展开 **XR** 子菜单，然后选择 **"Windows XR 插件远程处理"。**</span><span class="sxs-lookup"><span data-stu-id="77095-121">Next, go to the **Window** menu, expand the **XR** submenu, and select **Windows XR Plugin Remoting**.</span></span>
1. <span data-ttu-id="77095-122">将 **仿真模式设置为\*\*\*\*"远程"到"设备"。**</span><span class="sxs-lookup"><span data-stu-id="77095-122">Set **Emulation Mode** to **Remote to Device**.</span></span>
1. <span data-ttu-id="77095-123">对于 **"远程计算机**"，请输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="77095-123">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
1. <span data-ttu-id="77095-124">若要连接，请进行连接：</span><span class="sxs-lookup"><span data-stu-id="77095-124">To connect, either:</span></span>
   1. <span data-ttu-id="77095-125">若要手动连接，请取消选中"**播放时连接"，** 然后选择"连接 **"。**</span><span class="sxs-lookup"><span data-stu-id="77095-125">To manually connect, uncheck **Connect on Play**, and select **Connect**.</span></span> <span data-ttu-id="77095-126">应会看到" **连接状态"** 更改为"已 **连接"，** 并且看到屏幕在 HoloLens 中为空白。</span><span class="sxs-lookup"><span data-stu-id="77095-126">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
   1. <span data-ttu-id="77095-127">若要自动连接，请选中"**播放时连接"。**</span><span class="sxs-lookup"><span data-stu-id="77095-127">To automatically connect, check **Connect on Play**.</span></span> <span data-ttu-id="77095-128">启动播放模式后，编辑器将尝试连接。</span><span class="sxs-lookup"><span data-stu-id="77095-128">The editor will attempt to connect once Play Mode is started.</span></span>
1. <span data-ttu-id="77095-129">选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。</span><span class="sxs-lookup"><span data-stu-id="77095-129">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="77095-130">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="77095-130">Legacy WSA</span></span>](#tab/wsa)

1. <span data-ttu-id="77095-131">在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="77095-131">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="77095-132">在 HoloLens 上，启动 **全息远程处理播放器** 应用。</span><span class="sxs-lookup"><span data-stu-id="77095-132">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="77095-133">在 Unity 中，转到"**窗口**"菜单，展开 **XR** 子菜单，然后选择"全息仿真" (在 Unity 2019) 中标记为已弃用。</span><span class="sxs-lookup"><span data-stu-id="77095-133">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation** (marked as deprecated in Unity 2019).</span></span>
1. <span data-ttu-id="77095-134">将 **仿真模式设置为\*\*\*\*"远程"到"设备"。**</span><span class="sxs-lookup"><span data-stu-id="77095-134">Set **Emulation Mode** to **Remote to Device**.</span></span>
1. <span data-ttu-id="77095-135">如果 **使用的是第一** 代 HoloLens 或设备，根据设备版本HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="77095-135">Set **Device Version** according to if you're using a first generation HoloLens or a HoloLens 2.</span></span>
1. <span data-ttu-id="77095-136">对于 **"远程计算机**"，请输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="77095-136">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
1. <span data-ttu-id="77095-137">选择“连接”  。</span><span class="sxs-lookup"><span data-stu-id="77095-137">Select **Connect**.</span></span> <span data-ttu-id="77095-138">应会看到" **连接状态"** 更改为"已 **连接"，** 并且看到屏幕在 HoloLens 中为空白。</span><span class="sxs-lookup"><span data-stu-id="77095-138">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
1. <span data-ttu-id="77095-139">选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。</span><span class="sxs-lookup"><span data-stu-id="77095-139">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>
