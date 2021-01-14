---
title: 在 Unreal 中升级项目
description: 跟进了解适用于你的 Unreal 项目的版本升级步骤、API 更改和弃用内容。
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 移植, 升级
ms.openlocfilehash: 27fb726bc0ca9c51b4e7b68ad28b76f89312262e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010047"
---
# <a name="upgrading-projects-in-unreal"></a><span data-ttu-id="70069-104">在 Unreal 中升级项目</span><span class="sxs-lookup"><span data-stu-id="70069-104">Upgrading projects in Unreal</span></span>

<span data-ttu-id="70069-105">更新到新版本的 Unreal 后，在编译蓝图或打包项目时，已弃用的函数会显示为“警告”。</span><span class="sxs-lookup"><span data-stu-id="70069-105">When updating to a new version of Unreal, deprecated functions show up as warnings when compiling blueprints or packaging the project.</span></span>  <span data-ttu-id="70069-106">如果已添加新函数，且应改为使用此函数，那么这些函数会被弃用。</span><span class="sxs-lookup"><span data-stu-id="70069-106">Functions are deprecated when a new function has been added that should be used instead.</span></span> 

## <a name="426-upgrades"></a><span data-ttu-id="70069-107">4.26 版升级</span><span class="sxs-lookup"><span data-stu-id="70069-107">4.26 upgrades</span></span>
 
<span data-ttu-id="70069-108">在 4.26 版本中，所有 AR 和 VR 平台都已经过重构，添加了常见接口，且仍然与应用程序代码平台无关，因此可能会出现比平常更多的警告。</span><span class="sxs-lookup"><span data-stu-id="70069-108">In 4.26, all AR and VR platforms have been refactored to add common interfaces and keep application code platform agnostic, so you may see more warnings than usual.</span></span>  <span data-ttu-id="70069-109">建议更新到新的 API，使项目能够更轻松地移植到其他平台。</span><span class="sxs-lookup"><span data-stu-id="70069-109">Updating to the new APIs is recommended so the project can be more easily ported to other platforms.</span></span>

<span data-ttu-id="70069-110">警报消息将显示哪个函数已被弃用，并指出该改用哪个函数。</span><span class="sxs-lookup"><span data-stu-id="70069-110">Warning messages will show which function has been deprecated and indicate what function to use instead.</span></span>  <span data-ttu-id="70069-111">所有已弃用的函数都将继续适用于此版本，但可能在未来版本中失效。</span><span class="sxs-lookup"><span data-stu-id="70069-111">All deprecated functions will continue to work for this release but may not work in future releases.</span></span>  <span data-ttu-id="70069-112">在蓝图中搜索函数时，也将不再列出已弃用的函数。</span><span class="sxs-lookup"><span data-stu-id="70069-112">Deprecated functions will also no longer be listed when searching for functions in a blueprint.</span></span>

![Create Named ARPin 函数的蓝图](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a><span data-ttu-id="70069-114">4.25 版弃用项</span><span class="sxs-lookup"><span data-stu-id="70069-114">4.25 deprecations</span></span>

| <span data-ttu-id="70069-115">弃用的函数</span><span class="sxs-lookup"><span data-stu-id="70069-115">Deprecated function</span></span> | <span data-ttu-id="70069-116">新建函数</span><span class="sxs-lookup"><span data-stu-id="70069-116">New function</span></span> |
| --- | --- |
| <span data-ttu-id="70069-117">CreateNamedARPin</span><span class="sxs-lookup"><span data-stu-id="70069-117">CreateNamedARPin</span></span> | ![Pin Component 函数的蓝图](images/unreal-porting-img-02.png) |
| <span data-ttu-id="70069-119">LoadWMRAnchorStoreARPins</span><span class="sxs-lookup"><span data-stu-id="70069-119">LoadWMRAnchorStoreARPins</span></span> | ![Load ARPins from Local Store 函数的蓝图](images/unreal-porting-img-03.png) |
| <span data-ttu-id="70069-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span><span class="sxs-lookup"><span data-stu-id="70069-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span></span> | ![Save ARPin to Local Store 函数的蓝图](images/unreal-porting-img-04.png) |
| <span data-ttu-id="70069-123">RemoveARPinFromWMRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="70069-123">RemoveARPinFromWMRAnchorStore</span></span> | ![Remove ARPin from Local Store 函数的蓝图](images/unreal-porting-img-05.png) |
| <span data-ttu-id="70069-125">SetEnabledMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="70069-125">SetEnabledMixedRealityCamera</span></span> | ![Set Enabled XRCamera 函数的蓝图](images/unreal-porting-img-06.png) |
| <span data-ttu-id="70069-127">ResizeMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="70069-127">ResizeMixedRealityCamera</span></span> | ![Resize XRCamera 函数的蓝图](images/unreal-porting-img-07.png) |
| <span data-ttu-id="70069-129">StartCameraCapture</span><span class="sxs-lookup"><span data-stu-id="70069-129">StartCameraCapture</span></span> | ![用于启动摄像头捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-08.png) |
| <span data-ttu-id="70069-131">StopCameraCapture</span><span class="sxs-lookup"><span data-stu-id="70069-131">StopCameraCapture</span></span> | ![用于停止摄像头捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-09.png) |
| <span data-ttu-id="70069-133">StartQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="70069-133">StartQRCodeCapture</span></span> | ![用于启动 QR 码捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-10.png) |
| <span data-ttu-id="70069-135">StopQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="70069-135">StopQRCodeCapture</span></span> | ![用于停止 QR 码捕获的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-11.png) |
| <span data-ttu-id="70069-137">空间映射之前自动在 4.25 版中启动，但现在 4.26 版中需要进行切换。</span><span class="sxs-lookup"><span data-stu-id="70069-137">Spatial mapping previously automatically started in 4.25, but now needs to be toggled in 4.26.</span></span> | ![用于启用空间映射的 Toggle ARCapture 函数的蓝图](images/unreal-porting-img-12.png) |
| <span data-ttu-id="70069-139">ShowKeyboard</span><span class="sxs-lookup"><span data-stu-id="70069-139">ShowKeyboard</span></span> | <span data-ttu-id="70069-140">已在 4.26 版中删除，这是因为当焦点在文本小组件上时，会自动显示键盘。</span><span class="sxs-lookup"><span data-stu-id="70069-140">Removed in 4.26 since the keyboard automatically shows when a text widget is focused on.</span></span> |
| <span data-ttu-id="70069-141">HideKeyboard</span><span class="sxs-lookup"><span data-stu-id="70069-141">HideKeyboard</span></span> | <span data-ttu-id="70069-142">已在 4.26 版中删除，这是因为当焦点不在文本小组件上时，将自动隐藏键盘。</span><span class="sxs-lookup"><span data-stu-id="70069-142">Removed in 4.26 since the keyboard will automatically hide when a text widget is unfocused.</span></span> |
| <span data-ttu-id="70069-143">SupportsHandTracking</span><span class="sxs-lookup"><span data-stu-id="70069-143">SupportsHandTracking</span></span> | ![“支持手部跟踪”属性的蓝图](images/unreal-porting-img-13.png) |
| <span data-ttu-id="70069-145">IsDisplayOpaque</span><span class="sxs-lookup"><span data-stu-id="70069-145">IsDisplayOpaque</span></span> | ![IsDisplayOpaque 属性的蓝图](images/unreal-porting-img-14.png) |
| <span data-ttu-id="70069-147">GetHandJointTransform、GetPointerPoseInfo、GetControllerTrackingStatus</span><span class="sxs-lookup"><span data-stu-id="70069-147">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span></span> | ![Get Motion Controller Data 函数的蓝图](images/unreal-porting-img-15.png) |
| <span data-ttu-id="70069-149">GetVersionString</span><span class="sxs-lookup"><span data-stu-id="70069-149">GetVersionString</span></span> | ![Get Version String 函数的蓝图](images/unreal-porting-img-16.png) |
| <span data-ttu-id="70069-151">IsTrackingAvailable</span><span class="sxs-lookup"><span data-stu-id="70069-151">IsTrackingAvailable</span></span> | ![IsTrackingAvailable 属性的蓝图](images/unreal-porting-img-17.png) |
| <span data-ttu-id="70069-153">IsButtonClicked、IsButtonDown、IsGrasped、IsSelectPressed</span><span class="sxs-lookup"><span data-stu-id="70069-153">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span></span> | <span data-ttu-id="70069-154">使用 Unreal 的输入操作系统。</span><span class="sxs-lookup"><span data-stu-id="70069-154">Use Unreal’s input action system.</span></span> |
| <span data-ttu-id="70069-155">SetFocusPointForFrame</span><span class="sxs-lookup"><span data-stu-id="70069-155">SetFocusPointForFrame</span></span> | <span data-ttu-id="70069-156">已在 4.26 版中删除。</span><span class="sxs-lookup"><span data-stu-id="70069-156">Removed in 4.26.</span></span>  <span data-ttu-id="70069-157">之前用于在远程处理时重新投影，而现在支持深度重新投影。</span><span class="sxs-lookup"><span data-stu-id="70069-157">Previously used for reprojection when remoting, which now supports depth reprojection.</span></span> |

## <a name="426-changes"></a><span data-ttu-id="70069-158">4.26 更改</span><span class="sxs-lookup"><span data-stu-id="70069-158">4.26 changes</span></span>

<span data-ttu-id="70069-159">重大更改在于，必须从“编辑”>“项目设置”>“项目”>“说明”>“设置”选择“在 VR 中启动”，才能启动 Windows Mixed Reality 插件 。</span><span class="sxs-lookup"><span data-stu-id="70069-159">The significant change is that **Start in VR** from **Edit > Project Settings > Project > Description > Settings** is mandatory for starting Windows Mixed Reality plugin.</span></span> <span data-ttu-id="70069-160">如果没有该参数，则你不会在设备上看到全息影像。</span><span class="sxs-lookup"><span data-stu-id="70069-160">Without that parameter, you will not see your holograms on the device.</span></span>
