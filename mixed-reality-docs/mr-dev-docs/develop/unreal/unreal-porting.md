---
title: 在 Unreal 中升级项目
description: 简要介绍 Unreal 项目中的版本升级步骤和已弃用的 API。
author: hferrone
ms.author: v-hferrone
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 移植, 升级
ms.openlocfilehash: efad783ee199ed42c7355917a180855b3ec4f11b
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355638"
---
# <a name="upgrading-projects-in-unreal"></a><span data-ttu-id="43afb-104">在 Unreal 中升级项目</span><span class="sxs-lookup"><span data-stu-id="43afb-104">Upgrading projects in Unreal</span></span>

<span data-ttu-id="43afb-105">更新到新版本的 Unreal 后，在编译蓝图或打包项目时，已弃用的函数将显示为“警告”。</span><span class="sxs-lookup"><span data-stu-id="43afb-105">When updating to a new version of Unreal, deprecated functions will show up as warnings when compiling the blueprint or packaging the project.</span></span>  <span data-ttu-id="43afb-106">如果已添加新函数，且应改为使用此函数，那么这些函数会被弃用。</span><span class="sxs-lookup"><span data-stu-id="43afb-106">Functions are deprecated when a new function has been added that should be used instead.</span></span> 

## <a name="426-upgrades"></a><span data-ttu-id="43afb-107">4.26 版升级</span><span class="sxs-lookup"><span data-stu-id="43afb-107">4.26 upgrades</span></span>
 
<span data-ttu-id="43afb-108">在 4.26 版本中，所有 AR 和 VR 平台都已经过重构，添加了常见接口，且仍然与应用程序代码平台无关。</span><span class="sxs-lookup"><span data-stu-id="43afb-108">In 4.26, all AR and VR platforms have been refactored to add common interfaces and keep application code platform agnostic.</span></span>  <span data-ttu-id="43afb-109">由于此重构，更新到 4.26 版的 HoloLens 项目看到的警告可能比平时的多。</span><span class="sxs-lookup"><span data-stu-id="43afb-109">Because of this refactor, HoloLens projects updating to 4.26 may see more warnings than usual.</span></span>  <span data-ttu-id="43afb-110">建议更新到新的 API，使项目能够更轻松地移植到其他平台。</span><span class="sxs-lookup"><span data-stu-id="43afb-110">Updating to the new APIs is recommended so the project can be more easily ported to other platforms.</span></span>

<span data-ttu-id="43afb-111">警报消息将显示哪个函数已被弃用，并指出该改用哪个函数。</span><span class="sxs-lookup"><span data-stu-id="43afb-111">Warning messages will show which function has been deprecated and indicate what function to use instead.</span></span>  <span data-ttu-id="43afb-112">所有已弃用的函数都将继续适用于此版本，但可能在未来版本中失效。</span><span class="sxs-lookup"><span data-stu-id="43afb-112">All deprecated functions will continue to work for this release but may not work in future releases.</span></span>  <span data-ttu-id="43afb-113">在蓝图中搜索函数时，也将不再列出已弃用的函数。</span><span class="sxs-lookup"><span data-stu-id="43afb-113">Deprecated functions will also no longer be listed when searching for functions in a blueprint.</span></span>

![Create Named ARPin 函数的蓝图](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a><span data-ttu-id="43afb-115">4.25 版弃用项</span><span class="sxs-lookup"><span data-stu-id="43afb-115">4.25 deprecations</span></span>

| <span data-ttu-id="43afb-116">弃用的函数</span><span class="sxs-lookup"><span data-stu-id="43afb-116">Deprecated function</span></span> | <span data-ttu-id="43afb-117">新建函数</span><span class="sxs-lookup"><span data-stu-id="43afb-117">New function</span></span> |
| --- | --- |
| <span data-ttu-id="43afb-118">CreateNamedARPin</span><span class="sxs-lookup"><span data-stu-id="43afb-118">CreateNamedARPin</span></span> | ![Pin Component 函数的蓝图](images/unreal-porting-img-02.png) |
| <span data-ttu-id="43afb-120">LoadWMRAnchorStoreARPins</span><span class="sxs-lookup"><span data-stu-id="43afb-120">LoadWMRAnchorStoreARPins</span></span> | ![Load ARPins from Local Store 函数的蓝图](images/unreal-porting-img-03.png) |
| <span data-ttu-id="43afb-122">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span><span class="sxs-lookup"><span data-stu-id="43afb-122">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span></span> | ![Save ARPin to Local Store 函数的蓝图](images/unreal-porting-img-04.png) |
| <span data-ttu-id="43afb-124">RemoveARPinFromWMRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="43afb-124">RemoveARPinFromWMRAnchorStore</span></span> | ![Remove ARPin from Local Store 函数的蓝图](images/unreal-porting-img-05.png) |
| <span data-ttu-id="43afb-126">SetEnabledMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="43afb-126">SetEnabledMixedRealityCamera</span></span> | ![Set Enabled XRCamera 函数的蓝图](images/unreal-porting-img-06.png) |
| <span data-ttu-id="43afb-128">ResizeMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="43afb-128">ResizeMixedRealityCamera</span></span> | ![Resize XRCamera 函数的蓝图](images/unreal-porting-img-07.png) |
| <span data-ttu-id="43afb-130">StartCameraCapture</span><span class="sxs-lookup"><span data-stu-id="43afb-130">StartCameraCapture</span></span> | ![用于启动摄像头捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-08.png) |
| <span data-ttu-id="43afb-132">StopCameraCapture</span><span class="sxs-lookup"><span data-stu-id="43afb-132">StopCameraCapture</span></span> | ![用于停止摄像头捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-09.png) |
| <span data-ttu-id="43afb-134">StartQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="43afb-134">StartQRCodeCapture</span></span> | ![用于启动 QR 码捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-10.png) |
| <span data-ttu-id="43afb-136">StopQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="43afb-136">StopQRCodeCapture</span></span> | ![用于停止 QR 码捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-11.png) |
| <span data-ttu-id="43afb-138">空间映射之前自动在 4.25 版中启动，但现在 4.26 版中需要进行切换。</span><span class="sxs-lookup"><span data-stu-id="43afb-138">Spatial mapping previously automatically started in 4.25, but now needs to be toggled in 4.26.</span></span> | ![用于启用空间映射的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-12.png) |
| <span data-ttu-id="43afb-140">ShowKeyboard</span><span class="sxs-lookup"><span data-stu-id="43afb-140">ShowKeyboard</span></span> | <span data-ttu-id="43afb-141">已在 4.26 版中删除，这是因为当焦点在文本小组件上时，会自动显示键盘。</span><span class="sxs-lookup"><span data-stu-id="43afb-141">Removed in 4.26 since the keyboard automatically shows when a text widget is focused on.</span></span> |
| <span data-ttu-id="43afb-142">HideKeyboard</span><span class="sxs-lookup"><span data-stu-id="43afb-142">HideKeyboard</span></span> | <span data-ttu-id="43afb-143">已在 4.26 版中删除，这是因为当焦点不在文本小组件上时，将自动隐藏键盘。</span><span class="sxs-lookup"><span data-stu-id="43afb-143">Removed in 4.26 since the keyboard will automatically hide when a text widget is unfocused.</span></span> |
| <span data-ttu-id="43afb-144">SupportsHandTracking</span><span class="sxs-lookup"><span data-stu-id="43afb-144">SupportsHandTracking</span></span> | ![“支持手部跟踪”属性的蓝图](images/unreal-porting-img-13.png) |
| <span data-ttu-id="43afb-146">IsDisplayOpaque</span><span class="sxs-lookup"><span data-stu-id="43afb-146">IsDisplayOpaque</span></span> | ![IsDisplayOpaque 属性的蓝图](images/unreal-porting-img-14.png) |
| <span data-ttu-id="43afb-148">GetHandJointTransform、GetPointerPoseInfo、GetControllerTrackingStatus</span><span class="sxs-lookup"><span data-stu-id="43afb-148">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span></span> | ![Get Motion Controller Data 函数的蓝图](images/unreal-porting-img-15.png) |
| <span data-ttu-id="43afb-150">GetVersionString</span><span class="sxs-lookup"><span data-stu-id="43afb-150">GetVersionString</span></span> | ![Get Version String 函数的蓝图](images/unreal-porting-img-16.png) |
| <span data-ttu-id="43afb-152">IsTrackingAvailable</span><span class="sxs-lookup"><span data-stu-id="43afb-152">IsTrackingAvailable</span></span> | ![IsTrackingAvailable 属性的蓝图](images/unreal-porting-img-17.png) |
| <span data-ttu-id="43afb-154">IsButtonClicked、IsButtonDown、IsGrasped、IsSelectPressed</span><span class="sxs-lookup"><span data-stu-id="43afb-154">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span></span> | <span data-ttu-id="43afb-155">使用 Unreal 的输入操作系统。</span><span class="sxs-lookup"><span data-stu-id="43afb-155">Use Unreal’s input action system.</span></span> |
| <span data-ttu-id="43afb-156">SetFocusPointForFrame</span><span class="sxs-lookup"><span data-stu-id="43afb-156">SetFocusPointForFrame</span></span> | <span data-ttu-id="43afb-157">已在 4.26 版中删除。</span><span class="sxs-lookup"><span data-stu-id="43afb-157">Removed in 4.26.</span></span>  <span data-ttu-id="43afb-158">之前，它用于在远程时重新投影，而现在支持深度重新投影。</span><span class="sxs-lookup"><span data-stu-id="43afb-158">Previously this was used for reprojection when remoting, which now supports depth reprojection.</span></span> |