---
ms.openlocfilehash: d7232ca645c2a8cfb2508b090fdb7ae02c2ab010
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984415"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="a3c6f-101">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="a3c6f-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="a3c6f-102">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="a3c6f-102">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity“生成设置...”菜单路径](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="a3c6f-104">在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮： </span><span class="sxs-lookup"><span data-stu-id="a3c6f-104">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![选中了 UWP 要从 Standalone 切换平台的 Unity“生成设置”窗口](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="a3c6f-106">等待 Unity 完成平台切换操作：</span><span class="sxs-lookup"><span data-stu-id="a3c6f-106">Wait for Unity to finish switching the platform:</span></span>

![Unity 正在切换平台](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="a3c6f-108">当 Unity 完成平台切换后，单击红色 **x** 图标，关闭“生成设置”窗口：</span><span class="sxs-lookup"><span data-stu-id="a3c6f-108">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![突出显示了“关闭”图标的 Unity 生成窗口](../images/mr-learning-base/base-02-section2-step1-4.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="a3c6f-110">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="a3c6f-110">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="a3c6f-111">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="a3c6f-111">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity“生成设置...”菜单路径](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="a3c6f-113">在“生成设置”窗口中选择“通用 Windows 平台”，然后：</span><span class="sxs-lookup"><span data-stu-id="a3c6f-113">In the Build Settings window, select **Universal Windows Platform** and:</span></span>
1.  <span data-ttu-id="a3c6f-114">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="a3c6f-114">Set **Target device** to **HoloLens**</span></span>
2.  <span data-ttu-id="a3c6f-115">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="a3c6f-115">Set **Architecture** to **ARM 64**</span></span>
3.  <span data-ttu-id="a3c6f-116">将“生成类型”设置为“D3D 项目”</span><span class="sxs-lookup"><span data-stu-id="a3c6f-116">Set **Build Type** to **D3D Project**</span></span>
4.  <span data-ttu-id="a3c6f-117">将“目标 SDK 版本”设置为“最新安装项” </span><span class="sxs-lookup"><span data-stu-id="a3c6f-117">Set **Target SDK Version** to **Latest Installed**</span></span>
5.  <span data-ttu-id="a3c6f-118">将“最低平台版本”设置为 10.0.18362 </span><span class="sxs-lookup"><span data-stu-id="a3c6f-118">Set **Minimum Platform Version** to **10.0.18362**</span></span>
6.  <span data-ttu-id="a3c6f-119">将“Visual Studio 版本”设置为“最新安装项” </span><span class="sxs-lookup"><span data-stu-id="a3c6f-119">Set **Visual Studio Version** to **Latest installed**</span></span>
7.  <span data-ttu-id="a3c6f-120">将“生成和运行位置”设置为“USB 设备” </span><span class="sxs-lookup"><span data-stu-id="a3c6f-120">Set **Build and Run on** to **USB Device**</span></span>
8.  <span data-ttu-id="a3c6f-121">将“生成配置”设置为“发布”，因为调试存在已知的性能问题 </span><span class="sxs-lookup"><span data-stu-id="a3c6f-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9.  <span data-ttu-id="a3c6f-122">单击“切换平台”按钮</span><span class="sxs-lookup"><span data-stu-id="a3c6f-122">Click the Switch Platform button</span></span>


![设置了通用 Windows 平台设置的 Unity 生成设置](../images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="a3c6f-124">当 Unity 完成平台切换后，单击红色 x 图标，关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="a3c6f-124">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="a3c6f-125">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="a3c6f-125">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="a3c6f-126">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="a3c6f-126">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity“生成设置...”菜单路径](../images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="a3c6f-128">在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮： </span><span class="sxs-lookup"><span data-stu-id="a3c6f-128">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![选中了 UWP 要从 Standalone 切换平台的 Unity“生成设置”窗口](../images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="a3c6f-130">等待 Unity 完成平台切换操作：</span><span class="sxs-lookup"><span data-stu-id="a3c6f-130">Wait for Unity to finish switching the platform:</span></span>

![Unity 正在切换平台](../images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="a3c6f-132">当 Unity 完成平台切换后，单击红色 **x** 图标，关闭“生成设置”窗口：</span><span class="sxs-lookup"><span data-stu-id="a3c6f-132">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![突出显示了“关闭”图标的 Unity 生成窗口](../images/mr-learning-base/base-02-section2-step1-4.png)
