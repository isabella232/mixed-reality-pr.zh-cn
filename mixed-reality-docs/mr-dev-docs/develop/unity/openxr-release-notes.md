---
title: 混合现实 OpenXR 插件发行说明
description: 及时了解最新的发行说明，并升级到混合现实 OpenXR 插件。
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394627"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a><span data-ttu-id="9b803-104">混合现实 OpenXR 插件发行说明</span><span class="sxs-lookup"><span data-stu-id="9b803-104">Mixed Reality OpenXR plugin release notes</span></span>

## <a name="100---current-release"></a><span data-ttu-id="9b803-105">1.0.0 - 最新版本</span><span class="sxs-lookup"><span data-stu-id="9b803-105">1.0.0 - Current release</span></span>

* <span data-ttu-id="9b803-106">修复了一个错误：无论是不是 ARAnchorManager，应用启动时 XRAnchorSubsystem 总是启动。</span><span class="sxs-lookup"><span data-stu-id="9b803-106">Fixed a bug where a the XRAnchorSubsystem was always started on app start regardless ARAnchorManager’s present.</span></span>
* <span data-ttu-id="9b803-107">修复了重新投射模式不能正常工作的错误。</span><span class="sxs-lookup"><span data-stu-id="9b803-107">Fixed a bug where the reprojection mode didn’t work properly.</span></span>

## <a name="100-preview2---2021-06-14"></a><span data-ttu-id="9b803-108">1.0.0-preview.2 - 2021-06-14</span><span class="sxs-lookup"><span data-stu-id="9b803-108">1.0.0-preview.2 - 2021-06-14</span></span>

* <span data-ttu-id="9b803-109">依赖于 Unity 的 1.2.2 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="9b803-109">Depends on Unity’s 1.2.2 OpenXR plugin.</span></span>
* <span data-ttu-id="9b803-110">将全息远程处理功能更改到各个功能组中。</span><span class="sxs-lookup"><span data-stu-id="9b803-110">Changed Holographic Remoting features in to individual feature groups.</span></span>
* <span data-ttu-id="9b803-111">修复了“应用 HoloLens 2 项目设置”会更改项目颜色空间的错误。</span><span class="sxs-lookup"><span data-stu-id="9b803-111">Fixed a bug where “Apply HoloLens 2 project settings” changes project color space.</span></span> <span data-ttu-id="9b803-112">Unity OpenXR 1.2.0 插件后不再需要此功能。</span><span class="sxs-lookup"><span data-stu-id="9b803-112">This is no longer needed after Unity OpenXR 1.2.0 plugin.</span></span>
* <span data-ttu-id="9b803-113">修复了错误：输入设备连接后，在应用程序挂起和恢复后，设备输入不会断开连接。</span><span class="sxs-lookup"><span data-stu-id="9b803-113">Fixed a bug where a input device get connected without disconnect after application suspended and resumed.</span></span>
* <span data-ttu-id="9b803-114">添加了支持：通过 ARSession 检测插件和当前跟踪状态。</span><span class="sxs-lookup"><span data-stu-id="9b803-114">Added support for detecting plugin and current tracking states via ARSession.</span></span>
* <span data-ttu-id="9b803-115">修复了“AR 默认平面”ARFoundation 预设不可见的错误。</span><span class="sxs-lookup"><span data-stu-id="9b803-115">Fixed a bug where the “AR Default Plane” ARFoundation prefab wouldn’t be visible.</span></span>

## <a name="100-preview1---2021-06-02"></a><span data-ttu-id="9b803-116">1.0.0-preview.1 - 2021-06-02</span><span class="sxs-lookup"><span data-stu-id="9b803-116">1.0.0-preview.1 - 2021-06-02</span></span>

* <span data-ttu-id="9b803-117">支持 OpenXR 场景了解 MSFT 扩展，而不是预览扩展。</span><span class="sxs-lookup"><span data-stu-id="9b803-117">Supports OpenXR scene understanding MSFT extensions instead of preview extensions.</span></span>
* <span data-ttu-id="9b803-118">HoloLens 2 上的平面检测不再需要混合现实 OpenXR 运行时的预览版本。</span><span class="sxs-lookup"><span data-stu-id="9b803-118">Plane detection on HoloLens 2 no longer requires preview versions of the Mixed Reality OpenXR runtimes.</span></span>

## <a name="095---2021-05-21"></a><span data-ttu-id="9b803-119">0.9.5 - 2021-05-21</span><span class="sxs-lookup"><span data-stu-id="9b803-119">0.9.5 - 2021-05-21</span></span>

* <span data-ttu-id="9b803-120">依赖于 Unity 的 1.2.0 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="9b803-120">Depends on Unity’s 1.2.0 OpenXR Plugin</span></span>
* <span data-ttu-id="9b803-121">适应新的功能 UI（在 OpenXR 插件 1.2.0 中）进行配置。</span><span class="sxs-lookup"><span data-stu-id="9b803-121">Adapted to the new feature UI (in OpenXR Plugin 1.2.0) for configuration.</span></span>
* <span data-ttu-id="9b803-122">修复了可定位相机提供程序未正确取消注册的错误。</span><span class="sxs-lookup"><span data-stu-id="9b803-122">Fixed a bug where the locatable camera provider wasn’t properly unregistering.</span></span>
* <span data-ttu-id="9b803-123">清理了一些额外使用的 [Preserve]。</span><span class="sxs-lookup"><span data-stu-id="9b803-123">Cleaned up some extra usages of [Preserve].</span></span>
* <span data-ttu-id="9b803-124">更新输入系统 UI 中的“HP Reverb G2 控制器 (OpenXR)”名称。</span><span class="sxs-lookup"><span data-stu-id="9b803-124">Update “HP Reverb G2 Controller (OpenXR)” name in the input system UI.</span></span>

## <a name="094---2021-05-20"></a><span data-ttu-id="9b803-125">0.9.4 - 2021-05-20</span><span class="sxs-lookup"><span data-stu-id="9b803-125">0.9.4 - 2021-05-20</span></span>

* <span data-ttu-id="9b803-126">依赖于 Unity 的 1.2.0 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="9b803-126">Depends on Unity’s 1.2.0 OpenXR Plugin.</span></span>
* <span data-ttu-id="9b803-127">添加了新的 C# API，用于获取运动控制器 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="9b803-127">Added new C# API to get motion controller glTF model.</span></span>
* <span data-ttu-id="9b803-128">添加了新的 C# API，用于获取启用的视图配置并设置重新投射设置。</span><span class="sxs-lookup"><span data-stu-id="9b803-128">Added new C# API to get enabled view configurations and set reprojection settings.</span></span>
* <span data-ttu-id="9b803-129">添加了新的 C# API，用于通过 XRMeshSubsystem 为计算网格设置其他设置。</span><span class="sxs-lookup"><span data-stu-id="9b803-129">Added new C# API to set additional settings for computing meshes with XRMeshSubsystem.</span></span>
* <span data-ttu-id="9b803-130">添加了新的 C# API 来配置和订阅手势识别事件。</span><span class="sxs-lookup"><span data-stu-id="9b803-130">Added new C# API to configure and subscribe to gesture recognition events.</span></span>
* <span data-ttu-id="9b803-131">添加了“Windows->XR->编辑器远程处理”设置对话框。</span><span class="sxs-lookup"><span data-stu-id="9b803-131">Added Windows->XR->Editor Remoting settings dialog.</span></span>
* <span data-ttu-id="9b803-132">添加了对 HoloLens UWP 应用程序的 ARM 支持。</span><span class="sxs-lookup"><span data-stu-id="9b803-132">Added ARM support for HoloLens UWP applications.</span></span>

## <a name="093---2021-04-29"></a><span data-ttu-id="9b803-133">0.9.3 - 2021-04-29</span><span class="sxs-lookup"><span data-stu-id="9b803-133">0.9.3 - 2021-04-29</span></span>

* <span data-ttu-id="9b803-134">修复了全息远程处理连接不可靠的错误</span><span class="sxs-lookup"><span data-stu-id="9b803-134">Fixed a bug where Holographic remoting connection is not reliable</span></span>
* <span data-ttu-id="9b803-135">修复了错误：在升级到 Unity 的 1.1.1 OpenXR 插件后，VR 渲染性能为不理想。</span><span class="sxs-lookup"><span data-stu-id="9b803-135">Fixed a bug where the VR rendering performance is sub-optimum after upgrade to Unity’s 1.1.1 OpenXR plugin.</span></span>

## <a name="092---2021-04-21"></a><span data-ttu-id="9b803-136">0.9.2 - 2021-04-21</span><span class="sxs-lookup"><span data-stu-id="9b803-136">0.9.2 - 2021-04-21</span></span>

* <span data-ttu-id="9b803-137">插件版本 0.9.1 中 HoloLens 2 平面检测将适用于 105 版本的混合现实 OpenXR 预览版运行时。</span><span class="sxs-lookup"><span data-stu-id="9b803-137">Plane detection on HoloLens 2 in plugin version 0.9.1 will work with version 105 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="9b803-138">插件版本 0.9.2 中 HoloLens 2 平面检测将适用于 106 版本的混合现实 OpenXR 预览版运行时。</span><span class="sxs-lookup"><span data-stu-id="9b803-138">Plane detection on HoloLens 2 in plugin version 0.9.2 will work with version 106 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="9b803-139">从 InputProvider 中删除了一些未使用的回调，以防止 XRInputSubsystem.\* GetTrackingOriginMode 等调用（不是由我们的输入系统管理）返回具有误导性值的成功。</span><span class="sxs-lookup"><span data-stu-id="9b803-139">Removed some unused callbacks from InputProvider to prevent calls like XRInputSubsystem.\* GetTrackingOriginMode (which aren’t managed by our input system) from returning success with misleading values.</span></span>
* <span data-ttu-id="9b803-140">将 XRAnchorStore 的弃用版本拆分到其专有文件，以防止 Unity 控制台发出警告。</span><span class="sxs-lookup"><span data-stu-id="9b803-140">Split out deprecated version of XRAnchorStore into its own file to prevent Unity console warning.</span></span>

## <a name="091---2021-04-20"></a><span data-ttu-id="9b803-141">0.9.1 - 2021-04-20</span><span class="sxs-lookup"><span data-stu-id="9b803-141">0.9.1 - 2021-04-20</span></span>

* <span data-ttu-id="9b803-142">依赖于 Unity 的 1.1.1 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="9b803-142">Depends on Unity’s 1.1.1 OpenXR Plugin.</span></span>
* <span data-ttu-id="9b803-143">添加了对 UWP 平台的全息远程处理应用程序的支持。</span><span class="sxs-lookup"><span data-stu-id="9b803-143">Added support for Holographic Remoting application for UWP platform.</span></span>
* <span data-ttu-id="9b803-144">修复了 XRAnchorStore 尝试在主线程之外获取设置实例的 UnityException。</span><span class="sxs-lookup"><span data-stu-id="9b803-144">Fix UnityException where XRAnchorStore was trying to get a settings instance outside the main thread.</span></span>

## <a name="090---2021-03-29"></a><span data-ttu-id="9b803-145">0.9.0 - 2021-03-29</span><span class="sxs-lookup"><span data-stu-id="9b803-145">0.9.0 - 2021-03-29</span></span>

* <span data-ttu-id="9b803-146">添加了支持：通过 XRMeshSubsystem 和 ARMeshManager 进行空间映射。</span><span class="sxs-lookup"><span data-stu-id="9b803-146">Added support for spatial mapping via XRMeshSubsystem and ARMeshManager.</span></span>
* <span data-ttu-id="9b803-147">添加了新的 C# API，用于获取 OpenXR 句柄，以支持其他 Unity 包使用 OpenXR 扩展。</span><span class="sxs-lookup"><span data-stu-id="9b803-147">Added new C# API to get OpenXR handles to support other Unity packages consumes OpenXR extensions.</span></span>
* <span data-ttu-id="9b803-148">添加了新的 C# API，用于与 Windows.Perception API 互操作，以支持其他 Unity 包使用 Perception WinRT API。</span><span class="sxs-lookup"><span data-stu-id="9b803-148">Added new C# API to interop with Windows.Perception APIs to support other Unity packages consuming Perception WinRT APIs.</span></span>
* <span data-ttu-id="9b803-149">从 Windows Mixed Reality 功能集的所需功能中删除了交互配置文件，以便开发人员可以选择他们测试用的运动控制器。</span><span class="sxs-lookup"><span data-stu-id="9b803-149">Removed interaction profiles from required features in Windows Mixed Reality feature set, so developers can choose the motion controllers they tested with.</span></span>
* <span data-ttu-id="9b803-150">添加了全息编辑器远程处理功能验证程序，以帮助用户正确设置编辑器远程处理。</span><span class="sxs-lookup"><span data-stu-id="9b803-150">Added Holographic editor remoting feature validator to help users to setup editor remoting properly.</span></span>
* <span data-ttu-id="9b803-151">修复了在连接失败后退出全息编辑器远程处理模式时，Unity 编辑器崩溃的错误。</span><span class="sxs-lookup"><span data-stu-id="9b803-151">Fixed a bug where Unity editor crashes when exiting Holographic editor remoting mode after connection failure.</span></span>
* <span data-ttu-id="9b803-152">修复了 unpremultipled alpha 纹理导致 HoloLens 2 性能欠佳的错误。</span><span class="sxs-lookup"><span data-stu-id="9b803-152">Fixed a bug where unpremultipled alpha textures leads to sub-optimum performance on HoloLens 2.</span></span>
* <span data-ttu-id="9b803-153">修复了场景原点处于地面级别时未正确找到手部跟踪的错误。</span><span class="sxs-lookup"><span data-stu-id="9b803-153">Fixed a bug where hand tracking was not located correctly when the scene origin was at floor level.</span></span>
* <span data-ttu-id="9b803-154">修复了在离开并加载新场景后手部网格跟踪消失的错误。</span><span class="sxs-lookup"><span data-stu-id="9b803-154">Fixed a bug where hand mesh tracking disappear after leaving and loading a new scene.</span></span>
* <span data-ttu-id="9b803-155">修复了可定位相机提供程序未正确清理的错误。</span><span class="sxs-lookup"><span data-stu-id="9b803-155">Fixed a bug where locatable camera provider didn’t properly clean up.</span></span>
* <span data-ttu-id="9b803-156">将 XRAnchorStore API 的命名空间修改为 Microsoft.MixedReality.OpenXR。</span><span class="sxs-lookup"><span data-stu-id="9b803-156">Revised the namespace of XRAnchorStore API into Microsoft.MixedReality.OpenXR.</span></span>