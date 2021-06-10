---
ms.openlocfilehash: 481a063cac3cb4d7e5ef7521ad19af43cb68e2cf
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110630744"
---
# <a name="mrtk"></a>[<span data-ttu-id="ee6a4-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="ee6a4-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ee6a4-102">[MRTK 的配置对话框](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) 将尝试设置 XR SDK 和旧 WSA 的深度缓冲区设置，但最好检查这些选项卡并验证 Unity 中的设置。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-102">[MRTK's configuration dialog](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) will attempt to set depth buffer settings for both XR SDK and legacy WSA, but it's good to check those tabs and verify the settings in Unity.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="ee6a4-103">XR SDK</span><span class="sxs-lookup"><span data-stu-id="ee6a4-103">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ee6a4-104">设置 Unity 应用是否将向 Windows 提供深度缓冲区：</span><span class="sxs-lookup"><span data-stu-id="ee6a4-104">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="ee6a4-105">请参阅 **编辑**  >  **项目设置**  >  **XR 插件管理**，并确保展开菜单项。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-105">Go to **Edit** > **Project Settings** > **XR Plug-in Management** and ensure the menu item is expanded.</span></span>
2. <span data-ttu-id="ee6a4-106">单击与所选 XR 运行时对应的菜单项，即 "Windows Mixed Reality" 或 "OpenXR"。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-106">Click on the menu item corresponding to the XR runtime you've chosen, either Windows Mixed Reality or OpenXR.</span></span> <span data-ttu-id="ee6a4-107">此外，请确保选择了正确的生成平台，作为 Windows 独立版和通用 Windows 平台的选项卡可用。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-107">Additionally, ensure the correct build platform is selected, as tabs for both Windows Standalone and Universal Windows Platform are available.</span></span>
3. <span data-ttu-id="ee6a4-108">若要启用和配置：</span><span class="sxs-lookup"><span data-stu-id="ee6a4-108">To enable and configure:</span></span>
    1. <span data-ttu-id="ee6a4-109">对于 OpenXR，请在 " **深度提交模式** " 下拉列表中选择 "深度格式" 或 "无"。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-109">For OpenXR, select either a depth format or "None" in the **Depth Submission Mode** dropdown.</span></span>
    2. <span data-ttu-id="ee6a4-110">对于 Windows Mixed Reality，选中或取消选中 " **共享深度缓冲区** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-110">For Windows Mixed Reality, check or uncheck the **Shared Depth Buffer** check box.</span></span> <span data-ttu-id="ee6a4-111">然后，从 " **深度缓冲区格式** " 下拉列表中选择一种格式。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-111">Then, select a format from the **Depth Buffer Format** dropdown.</span></span>

<span data-ttu-id="ee6a4-112">![Windows XR 插件深度设置 ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR 深度设置](../../images/xrsdk-openxr-depth.png)</span><span class="sxs-lookup"><span data-stu-id="ee6a4-112">![Windows XR Plugin depth settings](../../images/xrsdk-winxr-depth.png)
![OpenXR depth settings](../../images/xrsdk-openxr-depth.png)</span></span>

> [!NOTE]
> <span data-ttu-id="ee6a4-113">通常建议使用16位深度缓冲区来提高性能。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-113">It is generally recommended to use 16 bit depth buffers for improved performance.</span></span> <span data-ttu-id="ee6a4-114">但是，如果使用16位深度格式，模具缓冲区所需效果 (如某些 Unity UI 滚动面板) 将不起作用，因为 Unity 不会在此设置中 [创建模具缓冲区](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-114">However, if using 16-bit depth format, stencil buffer required effects (like some Unity UI scroll panels) will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="ee6a4-115">相反，选择 *24 位深度格式* 通常会在端点图形平台上创建 [8 位模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html) 。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-115">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html) if applicable on the endpoint graphics platform.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="ee6a4-116">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="ee6a4-116">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ee6a4-117">设置 Unity 应用是否将向 Windows 提供深度缓冲区：</span><span class="sxs-lookup"><span data-stu-id="ee6a4-117">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="ee6a4-118">请参阅 **编辑**  >  **项目设置**  >  **播放器**  >  **通用 Windows 平台选项卡**  >  **XR 设置**。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-118">Go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform tab** > **XR Settings**.</span></span>
2. <span data-ttu-id="ee6a4-119">展开 " **Windows Mixed REALITY SDK** " 项。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-119">Expand the **Windows Mixed Reality SDK** item.</span></span>
3. <span data-ttu-id="ee6a4-120">选中或取消选中 " **启用深度缓冲共享** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-120">Check or uncheck the **Enable Depth Buffer Sharing** check box.</span></span> <span data-ttu-id="ee6a4-121">默认情况下，在新项目中选中 "启用深度缓冲区共享"，但默认情况下，在较旧的项目中可能未选中。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-121">Enable Depth Buffer Sharing is checked by default in new projects, but may have been unchecked by default in older projects.</span></span>

![旧 XR 深度设置](../../images/wmr-depth.png)

<span data-ttu-id="ee6a4-123">深度缓冲区可以提高视觉质量，只要 Windows 可以使用在主摄像机上的 Unity 中设置的近和远的平面，将深度缓冲区中的规范化每像素深度值准确地映射回以米为单位的距离。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-123">A depth buffer can improve visual quality so long as Windows can accurately map the normalized per-pixel depth values in your depth buffer back to distances in meters, using the near and far planes you've set in Unity on the main camera.</span></span> <span data-ttu-id="ee6a4-124">如果您的呈现器通过使用典型的方式来处理深度值，则通常情况下，您应该非常好，但是，在显示到现有颜色像素时，写入深度缓冲区的半透明渲染传递可能会混淆 reprojection。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-124">If your render passes handle depth values in typical ways, you should generally be fine here, though translucent render passes that write to the depth buffer while showing through to existing color pixels can confuse the reprojection.</span></span>  <span data-ttu-id="ee6a4-125">如果你知道，你的 render pass 会使很多最终深度像素具有不准确的深度值，则你可能会通过取消选中 "启用深度缓冲区共享" 获得更好的视觉质量。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-125">If you know that your render passes will leave many of your final depth pixels with inaccurate depth values, you are likely to get better visual quality by unchecking "Enable Depth Buffer Sharing".</span></span>

> [!NOTE]
> <span data-ttu-id="ee6a4-126">通常建议使用16位深度缓冲区来提高性能。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-126">It is generally recommended to use 16 bit depth buffers for improved performance.</span></span> <span data-ttu-id="ee6a4-127">但是，如果使用16位深度格式，模具缓冲区所需效果 (如某些 Unity UI 滚动面板) 将不起作用，因为 Unity 不会在此设置中 [创建模具缓冲区](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-127">However, if using 16-bit depth format, stencil buffer required effects (like some Unity UI scroll panels) will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="ee6a4-128">相反，选择 *24 位深度格式* 通常会在端点图形平台上创建 [8 位模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html) 。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-128">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html) if applicable on the endpoint graphics platform.</span></span>