---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097706"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="c82a9-101">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="c82a9-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="c82a9-102">1.克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="c82a9-102">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="c82a9-103">配置配置文件是顶级配置文件。</span><span class="sxs-lookup"><span data-stu-id="c82a9-103">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="c82a9-104">因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。</span><span class="sxs-lookup"><span data-stu-id="c82a9-104">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="c82a9-105">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，然后在“检查器”窗口中，验证 MixedRealityToolkit 配置文件是否已设置为 DefaultXRSDKConfigurationProfile  ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-105">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![选中 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

<span data-ttu-id="c82a9-107">在仍选中了“MixedRealityToolkit”对象的情况下，在检查器窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="c82a9-107">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Unity MixedRealityToolkit 组件的“复制和自定义”按钮](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

<span data-ttu-id="c82a9-109">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_XRSDKConfigurationProfile），然后单击“克隆”按钮，创建“DefaultXRSDKConfigurationProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-109">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

<span data-ttu-id="c82a9-111">新建的配置配置文件现已分配为场景中的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="c82a9-111">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![应用了新创建的自定义 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

<span data-ttu-id="c82a9-113">在 Unity 菜单中，选择“文件” > “保存”以保存场景。 </span><span class="sxs-lookup"><span data-stu-id="c82a9-113">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="c82a9-114">在学习整篇教程的过程中，请记得保存自己的工作。</span><span class="sxs-lookup"><span data-stu-id="c82a9-114">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="c82a9-115">2.启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="c82a9-115">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="c82a9-116">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，接下来在检查器窗口中，选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：  </span><span class="sxs-lookup"><span data-stu-id="c82a9-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![启用了空间感知系统的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="c82a9-118">在未来的项目中，如果你的应用无需响应环境或与环境交互，则建议关闭空间感知来减少性能成本。</span><span class="sxs-lookup"><span data-stu-id="c82a9-118">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="c82a9-119">3.克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="c82a9-119">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="c82a9-120">在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="c82a9-120">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![选中“空间感知”选项卡的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="c82a9-122">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_XRSDKSpatialAwarenessSystemProfile），然后单击“克隆”按钮，创建“DefaultXRSDKSpatialAwarenessSystemProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-122">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆空间感知系统配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="c82a9-124">新建的空间感知系统配置文件现已自动分配到你的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="c82a9-124">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![应用了新创建的自定义 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="c82a9-126">4.克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="c82a9-126">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="c82a9-127">在仍然选中了“空间感知”选项卡的情况下，展开“XR SDK Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口  ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-127">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![已展开“Windows Mixed Reality 空间网格观察程序”部分的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="c82a9-129">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessMeshObserverProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-129">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆空间网格观察程序配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="c82a9-131">新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：</span><span class="sxs-lookup"><span data-stu-id="c82a9-131">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![应用了新创建的自定义 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="c82a9-133">5.更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="c82a9-133">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="c82a9-134">在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下正常运行：  </span><span class="sxs-lookup"><span data-stu-id="c82a9-134">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![空间网格观察程序显示选项设置为“遮挡”的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="c82a9-136">尽管空间映射网格不可见，但它依然存在且可正常运行。</span><span class="sxs-lookup"><span data-stu-id="c82a9-136">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="c82a9-137">例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。</span><span class="sxs-lookup"><span data-stu-id="c82a9-137">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="c82a9-138">你已了解如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="c82a9-138">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="c82a9-139">可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="c82a9-139">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="c82a9-140">由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。</span><span class="sxs-lookup"><span data-stu-id="c82a9-140">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="c82a9-141">若要详细了解 MRTK 配置文件及其体系结构，可参阅 [MRTK 文档门户](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的 [MRTK 配置文件配置指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)。</span><span class="sxs-lookup"><span data-stu-id="c82a9-141">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="c82a9-142">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="c82a9-142">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="c82a9-143">1.克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="c82a9-143">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="c82a9-144">配置配置文件是顶级配置文件。</span><span class="sxs-lookup"><span data-stu-id="c82a9-144">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="c82a9-145">因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。</span><span class="sxs-lookup"><span data-stu-id="c82a9-145">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="c82a9-146">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，然后在“检查器”窗口中，验证 MixedRealityToolkit 配置文件是否已设置为 DefaultOpenXRConfigurationProfile：  </span><span class="sxs-lookup"><span data-stu-id="c82a9-146">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultOpenXRConfigurationProfile**:</span></span>

![选择了默认 openXR 配置文件的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

<span data-ttu-id="c82a9-148">在仍选中了“MixedRealityToolkit”对象的情况下，在检查器窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="c82a9-148">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![适用于 openxr 配置文件的 Unity MixedRealityToolkit 组件“复制和自定义”按钮](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

<span data-ttu-id="c82a9-150">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_OpenXRConfigurationProfile），然后单击“克隆”按钮，创建“DefaultOpenXRConfigurationProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_OpenXRConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultOpenXRConfigurationProfile**:</span></span>

![适用于 openxr 配置文件的 Unity MixedRealityToolkit 的“克隆配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

<span data-ttu-id="c82a9-152">新建的配置配置文件现已分配为场景中的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="c82a9-152">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![应用了新创建的自定义 OpenXR 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

<span data-ttu-id="c82a9-154">在 Unity 菜单中，选择“文件” > “保存”以保存场景。 </span><span class="sxs-lookup"><span data-stu-id="c82a9-154">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="c82a9-155">在学习整篇教程的过程中，请记得保存自己的工作。</span><span class="sxs-lookup"><span data-stu-id="c82a9-155">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="c82a9-156">2.启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="c82a9-156">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="c82a9-157">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，接下来在检查器窗口中，选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：  </span><span class="sxs-lookup"><span data-stu-id="c82a9-157">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![启用了空间感知系统的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="c82a9-159">在未来的项目中，如果你的应用无需响应环境或与环境交互，则建议关闭空间感知来减少性能成本。</span><span class="sxs-lookup"><span data-stu-id="c82a9-159">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="c82a9-160">3.克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="c82a9-160">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="c82a9-161">在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="c82a9-161">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![选中“空间感知”选项卡的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="c82a9-163">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_OpenXRSpatialAwarenessSystemProfile），然后单击“克隆”按钮，创建“DefaultXRSDKSpatialAwarenessSystemProfile”的可编辑副本：  </span><span class="sxs-lookup"><span data-stu-id="c82a9-163">In the Clone Profile window, enter a suitable **Profile Name**, for example, GettingStarted_OpenXRSpatialAwarenessSystemProfile, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆空间感知系统配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="c82a9-165">新建的空间感知系统配置文件现已自动分配到你的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="c82a9-165">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![应用了新创建的自定义 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="c82a9-167">4.克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="c82a9-167">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="c82a9-168">在仍然选中了“空间感知”选项卡的情况下，展开“XR SDK Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口  ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-168">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![已展开“Windows Mixed Reality 空间网格观察程序”部分的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="c82a9-170">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessMeshObserverProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-170">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆空间网格观察程序配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="c82a9-172">新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：</span><span class="sxs-lookup"><span data-stu-id="c82a9-172">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![应用了新创建的自定义 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="c82a9-174">5.更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="c82a9-174">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="c82a9-175">在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下正常运行：  </span><span class="sxs-lookup"><span data-stu-id="c82a9-175">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![空间网格观察程序显示选项设置为“遮挡”的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="c82a9-177">尽管空间映射网格不可见，但它依然存在且可正常运行。</span><span class="sxs-lookup"><span data-stu-id="c82a9-177">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="c82a9-178">例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。</span><span class="sxs-lookup"><span data-stu-id="c82a9-178">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="c82a9-179">你已了解如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="c82a9-179">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="c82a9-180">可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="c82a9-180">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="c82a9-181">由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。</span><span class="sxs-lookup"><span data-stu-id="c82a9-181">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="c82a9-182">若要详细了解 MRTK 配置文件及其体系结构，可参阅 [MRTK 文档门户](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的 [MRTK 配置文件配置指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)。</span><span class="sxs-lookup"><span data-stu-id="c82a9-182">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="c82a9-183">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="c82a9-183">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="c82a9-184">1.克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="c82a9-184">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="c82a9-185">配置配置文件是顶级配置文件。</span><span class="sxs-lookup"><span data-stu-id="c82a9-185">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="c82a9-186">因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。</span><span class="sxs-lookup"><span data-stu-id="c82a9-186">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="c82a9-187">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，然后在检查器窗口中将“MixedRealityToolkit”配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”：</span><span class="sxs-lookup"><span data-stu-id="c82a9-187">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![选中 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="c82a9-189">在仍选中了“MixedRealityToolkit”对象的情况下，在检查器窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="c82a9-189">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Unity MixedRealityToolkit 组件的“复制和自定义”按钮](../images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="c82a9-191">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_HoloLens2ConfigurationProfile），然后单击“克隆”按钮，创建“DefaultHololens2ConfigurationProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-191">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="c82a9-193">新建的配置配置文件现已分配为场景中的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="c82a9-193">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![应用了新创建的自定义 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="c82a9-195">在 Unity 菜单中，选择“文件” > “保存”以保存场景。 </span><span class="sxs-lookup"><span data-stu-id="c82a9-195">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="c82a9-196">在学习整篇教程的过程中，请记得保存自己的工作。</span><span class="sxs-lookup"><span data-stu-id="c82a9-196">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="c82a9-197">2.启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="c82a9-197">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="c82a9-198">在“层次结构”窗口中，选择 MixedRealityToolkit 对象，接下来在检查器窗口中，选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：  </span><span class="sxs-lookup"><span data-stu-id="c82a9-198">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![启用了空间感知系统的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="c82a9-200">在未来的项目中，如果你的应用无需响应环境或与环境交互，则建议关闭空间感知来减少性能成本。</span><span class="sxs-lookup"><span data-stu-id="c82a9-200">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="c82a9-201">3.克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="c82a9-201">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="c82a9-202">在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口： </span><span class="sxs-lookup"><span data-stu-id="c82a9-202">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![选中“空间感知”选项卡的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="c82a9-204">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessSystemProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessSystemProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-204">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆空间感知系统配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="c82a9-206">新建的空间感知系统配置文件现已自动分配到你的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="c82a9-206">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![应用了新创建的自定义 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="c82a9-208">4.克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="c82a9-208">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="c82a9-209">在仍然选中了“空间感知”选项卡的情况下，展开“Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口：  </span><span class="sxs-lookup"><span data-stu-id="c82a9-209">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![已展开“Windows Mixed Reality 空间网格观察程序”部分的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="c82a9-211">在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessMeshObserverProfile”的可编辑副本 ：</span><span class="sxs-lookup"><span data-stu-id="c82a9-211">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 的“克隆空间网格观察程序配置文件”弹出窗口](../images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="c82a9-213">新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：</span><span class="sxs-lookup"><span data-stu-id="c82a9-213">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![应用了新创建的自定义 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="c82a9-215">5.更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="c82a9-215">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="c82a9-216">在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下正常运行：  </span><span class="sxs-lookup"><span data-stu-id="c82a9-216">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![空间网格观察程序显示选项设置为“遮挡”的 Unity MixedRealityToolkit 组件](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="c82a9-218">尽管空间映射网格不可见，但它依然存在且可正常运行。</span><span class="sxs-lookup"><span data-stu-id="c82a9-218">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="c82a9-219">例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。</span><span class="sxs-lookup"><span data-stu-id="c82a9-219">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="c82a9-220">你已了解如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="c82a9-220">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="c82a9-221">可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="c82a9-221">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="c82a9-222">由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。</span><span class="sxs-lookup"><span data-stu-id="c82a9-222">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="c82a9-223">若要详细了解 MRTK 配置文件及其体系结构，可参阅 [MRTK 文档门户](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的 [MRTK 配置文件配置指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)。</span><span class="sxs-lookup"><span data-stu-id="c82a9-223">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>
