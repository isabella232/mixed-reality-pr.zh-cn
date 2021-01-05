---
title: 设备门户 API 参考
description: HoloLens 上 Windows 设备门户的 API 参考
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens，Windows 设备门户，API，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: c705ce65971042ab41befed9c6813dc797b61fc0
ms.sourcegitcommit: 084b1da9d7b435394b38d6152a2f9aee7a74aa2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/29/2020
ms.locfileid: "97804425"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="d24f5-104">设备门户 API 参考</span><span class="sxs-lookup"><span data-stu-id="d24f5-104">Device portal API reference</span></span>

<span data-ttu-id="d24f5-105">[Windows 设备门户](using-the-windows-device-portal.md)中的所有内容都是在 REST API 的基础之上构建的，你可以使用它以编程方式访问数据和控制设备。</span><span class="sxs-lookup"><span data-stu-id="d24f5-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="d24f5-106">应用常见问题</span><span class="sxs-lookup"><span data-stu-id="d24f5-106">App deloyment</span></span>

<span data-ttu-id="d24f5-107">**/api/app/packagemanager/package (删除)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="d24f5-108">卸载应用</span><span class="sxs-lookup"><span data-stu-id="d24f5-108">Uninstalls an app</span></span>

<span data-ttu-id="d24f5-109">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-109">Parameters</span></span>
* <span data-ttu-id="d24f5-110">package：要卸载的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="d24f5-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="d24f5-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="d24f5-112">安装应用程序</span><span class="sxs-lookup"><span data-stu-id="d24f5-112">Installs an App</span></span>

<span data-ttu-id="d24f5-113">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-113">Parameters</span></span>
* <span data-ttu-id="d24f5-114">package：要安装的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="d24f5-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="d24f5-115">有效负载</span><span class="sxs-lookup"><span data-stu-id="d24f5-115">Payload</span></span>
* <span data-ttu-id="d24f5-116">多部分相容的 http 正文</span><span class="sxs-lookup"><span data-stu-id="d24f5-116">multi-part conforming http body</span></span>

<span data-ttu-id="d24f5-117">**/api/app/packagemanager/packages (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="d24f5-118">检索系统上已安装应用的列表，详细信息</span><span class="sxs-lookup"><span data-stu-id="d24f5-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="d24f5-119">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-119">Return data</span></span>
* <span data-ttu-id="d24f5-120">包含详细信息的已安装包列表</span><span class="sxs-lookup"><span data-stu-id="d24f5-120">List of installed packages with details</span></span>

<span data-ttu-id="d24f5-121">**/api/app/packagemanager/state (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="d24f5-122">获取正在进行的应用安装的状态</span><span class="sxs-lookup"><span data-stu-id="d24f5-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="d24f5-123">转储集合</span><span class="sxs-lookup"><span data-stu-id="d24f5-123">Dump collection</span></span>

<span data-ttu-id="d24f5-124">**/api/debug/dump/usermode/crashcontrol (删除)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="d24f5-125">为旁加载应用禁用故障转储收集</span><span class="sxs-lookup"><span data-stu-id="d24f5-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="d24f5-126">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-126">Parameters</span></span>
* <span data-ttu-id="d24f5-127">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="d24f5-127">packageFullname : package name</span></span>

<span data-ttu-id="d24f5-128">**/api/debug/dump/usermode/crashcontrol (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="d24f5-129">获取旁加载应用故障转储收集的设置</span><span class="sxs-lookup"><span data-stu-id="d24f5-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="d24f5-130">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-130">Parameters</span></span>
* <span data-ttu-id="d24f5-131">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="d24f5-131">packageFullname : package name</span></span>

<span data-ttu-id="d24f5-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="d24f5-133">启用和设置旁加载应用的转储控件设置</span><span class="sxs-lookup"><span data-stu-id="d24f5-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="d24f5-134">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-134">Parameters</span></span>
* <span data-ttu-id="d24f5-135">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="d24f5-135">packageFullname : package name</span></span>

<span data-ttu-id="d24f5-136">**/api/debug/dump/usermode/crashdump (删除)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="d24f5-137">删除旁加载应用程序的故障转储</span><span class="sxs-lookup"><span data-stu-id="d24f5-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="d24f5-138">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-138">Parameters</span></span>
* <span data-ttu-id="d24f5-139">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="d24f5-139">packageFullname : package name</span></span>
* <span data-ttu-id="d24f5-140">文件名：转储文件名</span><span class="sxs-lookup"><span data-stu-id="d24f5-140">fileName : dump file name</span></span>

<span data-ttu-id="d24f5-141">**/api/debug/dump/usermode/crashdump (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="d24f5-142">检索旁加载应用的故障转储</span><span class="sxs-lookup"><span data-stu-id="d24f5-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="d24f5-143">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-143">Parameters</span></span>
* <span data-ttu-id="d24f5-144">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="d24f5-144">packageFullname : package name</span></span>
* <span data-ttu-id="d24f5-145">文件名：转储文件名</span><span class="sxs-lookup"><span data-stu-id="d24f5-145">fileName : dump file name</span></span>

<span data-ttu-id="d24f5-146">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-146">Return data</span></span>
* <span data-ttu-id="d24f5-147">转储文件。</span><span class="sxs-lookup"><span data-stu-id="d24f5-147">Dump file.</span></span> <span data-ttu-id="d24f5-148">与 WinDbg 或 Visual Studio 一起检查</span><span class="sxs-lookup"><span data-stu-id="d24f5-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="d24f5-149">**/api/debug/dump/usermode/dumps (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="d24f5-150">返回旁加载应用的所有崩溃转储的列表</span><span class="sxs-lookup"><span data-stu-id="d24f5-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="d24f5-151">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-151">Return data</span></span>
* <span data-ttu-id="d24f5-152">每端加载的应用的故障转储列表</span><span class="sxs-lookup"><span data-stu-id="d24f5-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="d24f5-153">ETW</span><span class="sxs-lookup"><span data-stu-id="d24f5-153">ETW</span></span>

<span data-ttu-id="d24f5-154">**/api/etw/providers (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="d24f5-155">枚举注册的提供程序</span><span class="sxs-lookup"><span data-stu-id="d24f5-155">Enumerates registered providers</span></span>

<span data-ttu-id="d24f5-156">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-156">Return data</span></span>
* <span data-ttu-id="d24f5-157">提供程序列表、友好名称和 GUID</span><span class="sxs-lookup"><span data-stu-id="d24f5-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="d24f5-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="d24f5-159">创建实时 ETW 会话;通过 websocket 进行管理。</span><span class="sxs-lookup"><span data-stu-id="d24f5-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="d24f5-160">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-160">Return data</span></span>
* <span data-ttu-id="d24f5-161">已启用的提供程序中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="d24f5-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="d24f5-162">全息操作系统</span><span class="sxs-lookup"><span data-stu-id="d24f5-162">Holographic OS</span></span>

<span data-ttu-id="d24f5-163">**/api/holographic/os/etw/customproviders (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="d24f5-164">返回未向系统注册的 HoloLens 特定 ETW 提供程序的列表</span><span class="sxs-lookup"><span data-stu-id="d24f5-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="d24f5-165">**/api/holographic/os/services (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="d24f5-166">返回所有正在运行的服务的状态。</span><span class="sxs-lookup"><span data-stu-id="d24f5-166">Returns the states of all services running.</span></span>

<span data-ttu-id="d24f5-167">**/api/holographic/os/settings/ipd (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="d24f5-168">获取存储的 IPD (Interpupillary 距离) （以毫米为单位）</span><span class="sxs-lookup"><span data-stu-id="d24f5-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="d24f5-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="d24f5-170">设置 IPD</span><span class="sxs-lookup"><span data-stu-id="d24f5-170">Sets the IPD</span></span>

<span data-ttu-id="d24f5-171">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-171">Parameters</span></span>
* <span data-ttu-id="d24f5-172">ipd：要设置的新 IPD 值（以毫米为单位）</span><span class="sxs-lookup"><span data-stu-id="d24f5-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="d24f5-173">**/api/holographic/os/webmanagement/settings/https (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="d24f5-174">获取设备门户的 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="d24f5-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="d24f5-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="d24f5-176">为设备门户设置 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="d24f5-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="d24f5-177">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-177">Parameters</span></span>
* <span data-ttu-id="d24f5-178">必需：是、否或默认值</span><span class="sxs-lookup"><span data-stu-id="d24f5-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="d24f5-179">全息认知</span><span class="sxs-lookup"><span data-stu-id="d24f5-179">Holographic Perception</span></span>

<span data-ttu-id="d24f5-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="d24f5-181">接受 websocket 升级，并运行以 30 fps 发送更新的感知客户端。</span><span class="sxs-lookup"><span data-stu-id="d24f5-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="d24f5-182">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-182">Parameters</span></span>
* <span data-ttu-id="d24f5-183">clientmode： "active" 强制在无法被动建立时强制视觉跟踪模式</span><span class="sxs-lookup"><span data-stu-id="d24f5-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="d24f5-184">全息热量</span><span class="sxs-lookup"><span data-stu-id="d24f5-184">Holographic Thermal</span></span>

<span data-ttu-id="d24f5-185">**/api/holographic/thermal/stage (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="d24f5-186">获取设备的热阶段 (0 正常，1温，2严重) </span><span class="sxs-lookup"><span data-stu-id="d24f5-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="d24f5-187">地图管理器</span><span class="sxs-lookup"><span data-stu-id="d24f5-187">Map Manager</span></span>

<span data-ttu-id="d24f5-188">**/api/holographic/mapmanager/mapFiles (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="d24f5-189">获取可用映射文件 () 的列表。</span><span class="sxs-lookup"><span data-stu-id="d24f5-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="d24f5-190">**/api/holographic/mapmanager/anchorFiles (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="d24f5-191">获取 () 的可用定位点文件的列表。</span><span class="sxs-lookup"><span data-stu-id="d24f5-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="d24f5-192">**/api/holographic/mapmanager/srdbFiles (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="d24f5-193">获取可用空间重构数据库文件 () 的列表。</span><span class="sxs-lookup"><span data-stu-id="d24f5-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="d24f5-194">**/api/holographic/mapmanager/getanchors (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="d24f5-195">获取当前用户的持久定位点的列表。</span><span class="sxs-lookup"><span data-stu-id="d24f5-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="d24f5-196">下载/上传/删除文件</span><span class="sxs-lookup"><span data-stu-id="d24f5-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="d24f5-197">**/api/holographic/mapmanager/download (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="d24f5-198">下载映射、定位点或空间重构数据库文件。</span><span class="sxs-lookup"><span data-stu-id="d24f5-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="d24f5-199">文件之前必须已上载或导出。</span><span class="sxs-lookup"><span data-stu-id="d24f5-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="d24f5-200">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-200">Parameters</span></span>
* <span data-ttu-id="d24f5-201">FileName：要下载的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="d24f5-202">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="d24f5-203">**/api/holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="d24f5-204">上载映射、定位点或空间重构数据库文件。</span><span class="sxs-lookup"><span data-stu-id="d24f5-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="d24f5-205">文件上传后，以后可以导入该文件以供系统使用。</span><span class="sxs-lookup"><span data-stu-id="d24f5-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="d24f5-206">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-206">Parameters</span></span>
* <span data-ttu-id="d24f5-207">file：要上传的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="d24f5-208">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="d24f5-209">**/api/holographic/mapmanager/delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="d24f5-210">删除映射、定位点或空间重构数据库文件。</span><span class="sxs-lookup"><span data-stu-id="d24f5-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="d24f5-211">文件之前必须已上载或导出。</span><span class="sxs-lookup"><span data-stu-id="d24f5-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="d24f5-212">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-212">Parameters</span></span>
* <span data-ttu-id="d24f5-213">FileName：要删除的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="d24f5-214">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="d24f5-215">导出</span><span class="sxs-lookup"><span data-stu-id="d24f5-215">Export</span></span>

<span data-ttu-id="d24f5-216">**/api/holographic/mapmanager/export (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="d24f5-217">导出系统当前使用的映射。</span><span class="sxs-lookup"><span data-stu-id="d24f5-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="d24f5-218">导出后，可以下载它。</span><span class="sxs-lookup"><span data-stu-id="d24f5-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="d24f5-219">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="d24f5-220">**/api/holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="d24f5-221">导出系统当前使用的映射。</span><span class="sxs-lookup"><span data-stu-id="d24f5-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="d24f5-222">导出后，可以下载它。</span><span class="sxs-lookup"><span data-stu-id="d24f5-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="d24f5-223">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="d24f5-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="d24f5-225">导出系统当前使用的映射和定位点。</span><span class="sxs-lookup"><span data-stu-id="d24f5-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="d24f5-226">导出后，可以下载。</span><span class="sxs-lookup"><span data-stu-id="d24f5-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="d24f5-227">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="d24f5-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="d24f5-229">导出系统当前使用的映射和空间重建数据库。</span><span class="sxs-lookup"><span data-stu-id="d24f5-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="d24f5-230">导出后，可以下载它们。</span><span class="sxs-lookup"><span data-stu-id="d24f5-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="d24f5-231">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="d24f5-232">导入</span><span class="sxs-lookup"><span data-stu-id="d24f5-232">Import</span></span>

<span data-ttu-id="d24f5-233">**/api/holographic/mapmanager/import (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="d24f5-234">向系统指示当前使用应使用的映射。</span><span class="sxs-lookup"><span data-stu-id="d24f5-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="d24f5-235">可对已导出或上载的文件调用。</span><span class="sxs-lookup"><span data-stu-id="d24f5-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="d24f5-236">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-236">Parameters</span></span>
* <span data-ttu-id="d24f5-237">FileName：要使用的映射的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="d24f5-238">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="d24f5-239">**/api/holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="d24f5-240">向系统指示当前使用的定位点。</span><span class="sxs-lookup"><span data-stu-id="d24f5-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="d24f5-241">可对已导出或上载的文件调用。</span><span class="sxs-lookup"><span data-stu-id="d24f5-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="d24f5-242">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-242">Parameters</span></span>
* <span data-ttu-id="d24f5-243">FileName：要使用的定位点的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="d24f5-244">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="d24f5-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="d24f5-246">向系统指示当前使用的空间重建数据库。</span><span class="sxs-lookup"><span data-stu-id="d24f5-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="d24f5-247">可对已导出或上载的文件调用。</span><span class="sxs-lookup"><span data-stu-id="d24f5-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="d24f5-248">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-248">Parameters</span></span>
* <span data-ttu-id="d24f5-249">FileName：要使用的空间映射 db 的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="d24f5-250">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="d24f5-251">其他</span><span class="sxs-lookup"><span data-stu-id="d24f5-251">Other</span></span>

<span data-ttu-id="d24f5-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="d24f5-253">重置系统地图、锚定和空间重建数据库。</span><span class="sxs-lookup"><span data-stu-id="d24f5-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="d24f5-254">示例：</span><span class="sxs-lookup"><span data-stu-id="d24f5-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="d24f5-255">**/api/holographic/mapmanager/status (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="d24f5-256">获取系统的状态，包括上次导入的映射、定位点和空间重构数据库文件。</span><span class="sxs-lookup"><span data-stu-id="d24f5-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="d24f5-257">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="d24f5-257">Mixed Reality Capture</span></span>

<span data-ttu-id="d24f5-258">**/api/holographic/mrc/file (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="d24f5-259">从设备下载混合现实文件。</span><span class="sxs-lookup"><span data-stu-id="d24f5-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="d24f5-260">使用 op = stream query 参数进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="d24f5-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="d24f5-261">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-261">Parameters</span></span>
* <span data-ttu-id="d24f5-262">filename：要获取的视频文件的名称、hex64 编码</span><span class="sxs-lookup"><span data-stu-id="d24f5-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="d24f5-263">op： stream</span><span class="sxs-lookup"><span data-stu-id="d24f5-263">op : stream</span></span>

<span data-ttu-id="d24f5-264">**/api/holographic/mrc/file (删除)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="d24f5-265">从设备中删除混合现实记录。</span><span class="sxs-lookup"><span data-stu-id="d24f5-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="d24f5-266">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-266">Parameters</span></span>
* <span data-ttu-id="d24f5-267">filename：要删除的文件的名称，hex64 已编码</span><span class="sxs-lookup"><span data-stu-id="d24f5-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="d24f5-268">**/api/holographic/mrc/files (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="d24f5-269">返回存储在设备上的混合现实文件的列表</span><span class="sxs-lookup"><span data-stu-id="d24f5-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="d24f5-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="d24f5-271">采用混合现实照片，并在设备上创建文件</span><span class="sxs-lookup"><span data-stu-id="d24f5-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="d24f5-272">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-272">Parameters</span></span>
* <span data-ttu-id="d24f5-273">holo：捕获全息影像： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="d24f5-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="d24f5-274">pv：捕获 PV 摄像机： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="d24f5-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="d24f5-275">RenderFromCamera： (HoloLens 2 仅) 照片/视频相机的透视中呈现： true 或 false (默认为 true) </span><span class="sxs-lookup"><span data-stu-id="d24f5-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="d24f5-276">**/api/holographic/mrc/settings (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="d24f5-277">获取默认的混合现实捕获设置</span><span class="sxs-lookup"><span data-stu-id="d24f5-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="d24f5-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="d24f5-279">设置默认的混合现实捕获设置。</span><span class="sxs-lookup"><span data-stu-id="d24f5-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="d24f5-280">其中一些设置适用于系统的 MRC 照片和视频捕获。</span><span class="sxs-lookup"><span data-stu-id="d24f5-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="d24f5-281">**/api/holographic/mrc/status (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="d24f5-282">获取 Windows 设备门户内混合现实捕获的状态。</span><span class="sxs-lookup"><span data-stu-id="d24f5-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="d24f5-283">\**_响应_* _</span><span class="sxs-lookup"><span data-stu-id="d24f5-283">\**_Response_* _</span></span>

<span data-ttu-id="d24f5-284">响应包含一个 JSON 属性，用于指示 Windows 设备门户是否正在录制视频。</span><span class="sxs-lookup"><span data-stu-id="d24f5-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="d24f5-285">_ */api/holographic/mrc/thumbnail (获取)*\*</span><span class="sxs-lookup"><span data-stu-id="d24f5-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="d24f5-286">获取指定文件的缩略图图像。</span><span class="sxs-lookup"><span data-stu-id="d24f5-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="d24f5-287">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-287">Parameters</span></span>
* <span data-ttu-id="d24f5-288">文件名：要为其请求缩略图的文件的名称，hex64 已编码</span><span class="sxs-lookup"><span data-stu-id="d24f5-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="d24f5-289">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="d24f5-290">启动混合现实记录</span><span class="sxs-lookup"><span data-stu-id="d24f5-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="d24f5-291">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-291">Parameters</span></span>
* <span data-ttu-id="d24f5-292">holo：捕获全息影像： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="d24f5-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="d24f5-293">pv：捕获 PV 摄像机： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="d24f5-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="d24f5-294">mic：捕获麦克风： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="d24f5-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="d24f5-295">环回：捕获应用音频： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="d24f5-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="d24f5-296">RenderFromCamera： (HoloLens 2 仅) 照片/视频相机的透视中呈现： true 或 false (默认为 true) </span><span class="sxs-lookup"><span data-stu-id="d24f5-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="d24f5-297">vstab： (HoloLens 2 仅) 启用视频抖动： true 或 false (默认为 true) </span><span class="sxs-lookup"><span data-stu-id="d24f5-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="d24f5-298">vstabbuffer： (HoloLens 2 仅) 视频稳定性缓冲区延迟：0到30帧 (默认为15帧) </span><span class="sxs-lookup"><span data-stu-id="d24f5-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="d24f5-299">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="d24f5-300">停止当前混合现实记录</span><span class="sxs-lookup"><span data-stu-id="d24f5-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="d24f5-301">混合现实流式处理</span><span class="sxs-lookup"><span data-stu-id="d24f5-301">Mixed Reality Streaming</span></span>

> [!CAUTION]
> <span data-ttu-id="d24f5-302">由于环回隔离，无法从设备上的应用内部连接到混合现实流式处理。</span><span class="sxs-lookup"><span data-stu-id="d24f5-302">Because of loopback isolation, you can't connect to Mixed Reality Streaming from inside an app on a device.</span></span>

<span data-ttu-id="d24f5-303">HoloLens 支持混合现实的实时预览，通过块区下载零碎的工作方式。</span><span class="sxs-lookup"><span data-stu-id="d24f5-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="d24f5-304">混合现实流共享相同的参数集来控制捕获的内容：</span><span class="sxs-lookup"><span data-stu-id="d24f5-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="d24f5-305">holo：捕获全息影像： true 或 false</span><span class="sxs-lookup"><span data-stu-id="d24f5-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="d24f5-306">pv：捕获 PV 摄像机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="d24f5-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="d24f5-307">mic：捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="d24f5-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="d24f5-308">环回：捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="d24f5-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="d24f5-309">如果未指定任何内容：将捕获全息影像、照片/视频相机和应用音频</span><span class="sxs-lookup"><span data-stu-id="d24f5-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="d24f5-310">如果已指定任何参数：未指定的参数将默认为 false</span><span class="sxs-lookup"><span data-stu-id="d24f5-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="d24f5-311">可选参数 (仅限 HoloLens 2) </span><span class="sxs-lookup"><span data-stu-id="d24f5-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="d24f5-312">RenderFromCamera：从照片/视频相机的角度呈现： true 或 false (默认为 true) </span><span class="sxs-lookup"><span data-stu-id="d24f5-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="d24f5-313">vstab：启用视频抖动： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="d24f5-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="d24f5-314">vstabbuffer：视频稳定缓冲区延迟：0到30帧 (默认为15帧) </span><span class="sxs-lookup"><span data-stu-id="d24f5-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="d24f5-315">**/api/holographic/stream/live.mp4 (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="d24f5-316">1280x720p 30fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="d24f5-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="d24f5-317">**/api/holographic/stream/live_high.mp4 (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="d24f5-318">1280x720p 30fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="d24f5-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="d24f5-319">**/api/holographic/stream/live_med.mp4 (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="d24f5-320">854x480p 30fps 2.5 Mbit stream。</span><span class="sxs-lookup"><span data-stu-id="d24f5-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="d24f5-321">**/api/holographic/stream/live_low.mp4 (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="d24f5-322">428x240p 15fps 0.6 Mbit stream。</span><span class="sxs-lookup"><span data-stu-id="d24f5-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="d24f5-323">网络</span><span class="sxs-lookup"><span data-stu-id="d24f5-323">Networking</span></span>

<span data-ttu-id="d24f5-324">**/api/networking/ipconfig (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="d24f5-325">获取当前 ip 配置</span><span class="sxs-lookup"><span data-stu-id="d24f5-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="d24f5-326">操作系统信息</span><span class="sxs-lookup"><span data-stu-id="d24f5-326">OS Information</span></span>

<span data-ttu-id="d24f5-327">**/api/os/info (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="d24f5-328">获取操作系统信息</span><span class="sxs-lookup"><span data-stu-id="d24f5-328">Gets operating system information</span></span>

<span data-ttu-id="d24f5-329">**/api/os/machinename (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="d24f5-330">获取计算机名称</span><span class="sxs-lookup"><span data-stu-id="d24f5-330">Gets the machine name</span></span>

<span data-ttu-id="d24f5-331">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="d24f5-332">设置计算机名称</span><span class="sxs-lookup"><span data-stu-id="d24f5-332">Sets the machine name</span></span>

<span data-ttu-id="d24f5-333">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-333">Parameters</span></span>
* <span data-ttu-id="d24f5-334">名称：要设置为的新计算机名称，hex64 编码为</span><span class="sxs-lookup"><span data-stu-id="d24f5-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="d24f5-335">感知模拟控制</span><span class="sxs-lookup"><span data-stu-id="d24f5-335">Perception Simulation Control</span></span>

<span data-ttu-id="d24f5-336">**/api/holographic/simulation/control/mode (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-336">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="d24f5-337">获取模拟模式</span><span class="sxs-lookup"><span data-stu-id="d24f5-337">Get the simulation mode</span></span>

<span data-ttu-id="d24f5-338">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-338">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="d24f5-339">设置模拟模式</span><span class="sxs-lookup"><span data-stu-id="d24f5-339">Set the simulation mode</span></span>

<span data-ttu-id="d24f5-340">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-340">Parameters</span></span>
* <span data-ttu-id="d24f5-341">模式：模拟模式：默认、模拟、远程、旧</span><span class="sxs-lookup"><span data-stu-id="d24f5-341">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="d24f5-342">**/api/holographic/simulation/control/stream (删除)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-342">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="d24f5-343">删除控件流。</span><span class="sxs-lookup"><span data-stu-id="d24f5-343">Delete a control stream.</span></span>

<span data-ttu-id="d24f5-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="d24f5-345">为控制流打开 web 套接字连接。</span><span class="sxs-lookup"><span data-stu-id="d24f5-345">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="d24f5-346">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-346">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="d24f5-347">需要创建控制流 (优先级) 或将数据发送到创建的流 (streamId 必需的) 。</span><span class="sxs-lookup"><span data-stu-id="d24f5-347">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="d24f5-348">已发布的数据的类型应为 "application/八进制流"。</span><span class="sxs-lookup"><span data-stu-id="d24f5-348">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="d24f5-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="d24f5-350">请求模拟视频流，其中包含在处于 "模拟" 模式时呈现给系统的内容。</span><span class="sxs-lookup"><span data-stu-id="d24f5-350">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="d24f5-351">首先发送一个简单的格式说明符标头，然后再发送一个-264 编码的纹理，每个纹理前面都有一个标头，指示眼睛索引和纹理大小。</span><span class="sxs-lookup"><span data-stu-id="d24f5-351">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="d24f5-352">感知播放</span><span class="sxs-lookup"><span data-stu-id="d24f5-352">Perception Simulation Playback</span></span>

<span data-ttu-id="d24f5-353">**/api/holographic/simulation/playback/file (删除)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-353">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="d24f5-354">删除记录。</span><span class="sxs-lookup"><span data-stu-id="d24f5-354">Delete a recording.</span></span>

<span data-ttu-id="d24f5-355">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-355">Parameters</span></span>
* <span data-ttu-id="d24f5-356">录制：要删除的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-356">recording : Name of recording to delete.</span></span>

<span data-ttu-id="d24f5-357">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-357">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="d24f5-358">上传记录。</span><span class="sxs-lookup"><span data-stu-id="d24f5-358">Upload a recording.</span></span>

<span data-ttu-id="d24f5-359">**/api/holographic/simulation/playback/files (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-359">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="d24f5-360">获取所有记录。</span><span class="sxs-lookup"><span data-stu-id="d24f5-360">Get all recordings.</span></span>

<span data-ttu-id="d24f5-361">**/api/holographic/simulation/playback/session (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-361">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="d24f5-362">获取记录的当前播放状态。</span><span class="sxs-lookup"><span data-stu-id="d24f5-362">Get the current playback state of a recording.</span></span>

<span data-ttu-id="d24f5-363">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-363">Parameters</span></span>
* <span data-ttu-id="d24f5-364">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-364">recording : Name of recording.</span></span>

<span data-ttu-id="d24f5-365">**/api/holographic/simulation/playback/session/file (删除)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-365">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="d24f5-366">卸载记录。</span><span class="sxs-lookup"><span data-stu-id="d24f5-366">Unload a recording.</span></span>

<span data-ttu-id="d24f5-367">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-367">Parameters</span></span>
* <span data-ttu-id="d24f5-368">录制：要卸载的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-368">recording : Name of recording to unload.</span></span>

<span data-ttu-id="d24f5-369">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-369">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="d24f5-370">加载记录。</span><span class="sxs-lookup"><span data-stu-id="d24f5-370">Load a recording.</span></span>

<span data-ttu-id="d24f5-371">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-371">Parameters</span></span>
* <span data-ttu-id="d24f5-372">录制：要加载的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-372">recording : Name of recording to load.</span></span>

<span data-ttu-id="d24f5-373">**/api/holographic/simulation/playback/session/files (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-373">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="d24f5-374">获取所有加载的记录。</span><span class="sxs-lookup"><span data-stu-id="d24f5-374">Get all loaded recordings.</span></span>

<span data-ttu-id="d24f5-375">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-375">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="d24f5-376">暂停录制。</span><span class="sxs-lookup"><span data-stu-id="d24f5-376">Pause a recording.</span></span>

<span data-ttu-id="d24f5-377">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-377">Parameters</span></span>
* <span data-ttu-id="d24f5-378">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-378">recording : Name of recording.</span></span>

<span data-ttu-id="d24f5-379">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-379">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="d24f5-380">播放录制。</span><span class="sxs-lookup"><span data-stu-id="d24f5-380">Play a recording.</span></span>

<span data-ttu-id="d24f5-381">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-381">Parameters</span></span>
* <span data-ttu-id="d24f5-382">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-382">recording : Name of recording.</span></span>

<span data-ttu-id="d24f5-383">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-383">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="d24f5-384">停止录制。</span><span class="sxs-lookup"><span data-stu-id="d24f5-384">Stop a recording.</span></span>

<span data-ttu-id="d24f5-385">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-385">Parameters</span></span>
* <span data-ttu-id="d24f5-386">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-386">recording : Name of recording.</span></span>

<span data-ttu-id="d24f5-387">**/api/holographic/simulation/playback/session/types (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-387">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="d24f5-388">获取已加载记录中数据的类型。</span><span class="sxs-lookup"><span data-stu-id="d24f5-388">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="d24f5-389">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-389">Parameters</span></span>
* <span data-ttu-id="d24f5-390">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-390">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="d24f5-391">感知模拟记录</span><span class="sxs-lookup"><span data-stu-id="d24f5-391">Perception Simulation Recording</span></span>

<span data-ttu-id="d24f5-392">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-392">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="d24f5-393">开始记录。</span><span class="sxs-lookup"><span data-stu-id="d24f5-393">Start a recording.</span></span> <span data-ttu-id="d24f5-394">一次只能有一个记录处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="d24f5-394">Only a single recording can be active at once.</span></span> <span data-ttu-id="d24f5-395">必须设置 head、双手、spatialMapping 或环境之一。</span><span class="sxs-lookup"><span data-stu-id="d24f5-395">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="d24f5-396">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-396">Parameters</span></span>
* <span data-ttu-id="d24f5-397">head：设置为1以记录头数据。</span><span class="sxs-lookup"><span data-stu-id="d24f5-397">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="d24f5-398">动手：设置为1以记录手型数据。</span><span class="sxs-lookup"><span data-stu-id="d24f5-398">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="d24f5-399">spatialMapping：设置为1以记录空间映射。</span><span class="sxs-lookup"><span data-stu-id="d24f5-399">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="d24f5-400">环境：设置为1以记录环境数据。</span><span class="sxs-lookup"><span data-stu-id="d24f5-400">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="d24f5-401">name：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-401">name : Name of the recording.</span></span>
* <span data-ttu-id="d24f5-402">singleSpatialMappingFrame：设置为1将仅记录单个空间映射框架。</span><span class="sxs-lookup"><span data-stu-id="d24f5-402">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="d24f5-403">**/api/holographic/simulation/recording/status (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-403">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="d24f5-404">获取记录状态。</span><span class="sxs-lookup"><span data-stu-id="d24f5-404">Get recording state.</span></span>

<span data-ttu-id="d24f5-405">**/api/holographic/simulation/recording/stop (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-405">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="d24f5-406">停止当前记录。</span><span class="sxs-lookup"><span data-stu-id="d24f5-406">Stop the current recording.</span></span> <span data-ttu-id="d24f5-407">记录将以文件的形式返回。</span><span class="sxs-lookup"><span data-stu-id="d24f5-407">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="d24f5-408">性能数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-408">Performance data</span></span>

<span data-ttu-id="d24f5-409">**/api/resourcemanager/processes (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-409">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="d24f5-410">返回正在运行的进程的列表以及详细信息</span><span class="sxs-lookup"><span data-stu-id="d24f5-410">Returns the list of running processes with details</span></span>

<span data-ttu-id="d24f5-411">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-411">Return data</span></span>
* <span data-ttu-id="d24f5-412">JSON，包含进程列表和每个进程的详细信息</span><span class="sxs-lookup"><span data-stu-id="d24f5-412">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="d24f5-413">**/api/resourcemanager/systemperf (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-413">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="d24f5-414">返回系统性能统计信息 (i/o 读/写、内存统计信息等。</span><span class="sxs-lookup"><span data-stu-id="d24f5-414">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="d24f5-415">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-415">Return data</span></span>
* <span data-ttu-id="d24f5-416">包含系统信息的 JSON： CPU、GPU、内存、网络、IO</span><span class="sxs-lookup"><span data-stu-id="d24f5-416">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="d24f5-417">强力</span><span class="sxs-lookup"><span data-stu-id="d24f5-417">Power</span></span>

<span data-ttu-id="d24f5-418">**/api/power/battery (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-418">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="d24f5-419">获取当前电池状态</span><span class="sxs-lookup"><span data-stu-id="d24f5-419">Gets the current battery state</span></span>

<span data-ttu-id="d24f5-420">**/api/power/state (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-420">**/api/power/state (GET)**</span></span>

<span data-ttu-id="d24f5-421">检查系统是否处于低功耗状态</span><span class="sxs-lookup"><span data-stu-id="d24f5-421">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="d24f5-422">远程控制</span><span class="sxs-lookup"><span data-stu-id="d24f5-422">Remote Control</span></span>

<span data-ttu-id="d24f5-423">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-423">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="d24f5-424">重新启动目标设备</span><span class="sxs-lookup"><span data-stu-id="d24f5-424">Restarts the target device</span></span>

<span data-ttu-id="d24f5-425">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-425">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="d24f5-426">关闭目标设备</span><span class="sxs-lookup"><span data-stu-id="d24f5-426">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="d24f5-427">任务管理器</span><span class="sxs-lookup"><span data-stu-id="d24f5-427">Task Manager</span></span>

<span data-ttu-id="d24f5-428">**/api/taskmanager/app (删除)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-428">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="d24f5-429">停止现代应用</span><span class="sxs-lookup"><span data-stu-id="d24f5-429">Stops a modern app</span></span>

<span data-ttu-id="d24f5-430">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-430">Parameters</span></span>
* <span data-ttu-id="d24f5-431">包：应用包的完整名称，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="d24f5-431">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="d24f5-432">forcestop：强制停止所有进程 (= yes) </span><span class="sxs-lookup"><span data-stu-id="d24f5-432">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="d24f5-433">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-433">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="d24f5-434">启动新式应用</span><span class="sxs-lookup"><span data-stu-id="d24f5-434">Starts a modern app</span></span>

<span data-ttu-id="d24f5-435">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-435">Parameters</span></span>
* <span data-ttu-id="d24f5-436">appid：要启动的应用的 PRAID，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="d24f5-436">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="d24f5-437">包：应用包的完整名称，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="d24f5-437">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="d24f5-438">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="d24f5-438">WiFi Management</span></span>

<span data-ttu-id="d24f5-439">**/api/wifi/interfaces (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-439">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="d24f5-440">枚举无线网络接口</span><span class="sxs-lookup"><span data-stu-id="d24f5-440">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="d24f5-441">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-441">Return data</span></span>
* <span data-ttu-id="d24f5-442">包含详细信息 (GUID、说明等 ) 的无线接口列表</span><span class="sxs-lookup"><span data-stu-id="d24f5-442">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="d24f5-443">**/api/wifi/network (删除)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-443">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="d24f5-444">删除与指定接口上的网络相关联的配置文件</span><span class="sxs-lookup"><span data-stu-id="d24f5-444">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="d24f5-445">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-445">Parameters</span></span>
* <span data-ttu-id="d24f5-446">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="d24f5-446">interface : network interface guid</span></span>
* <span data-ttu-id="d24f5-447">配置文件：配置文件名称</span><span class="sxs-lookup"><span data-stu-id="d24f5-447">profile : profile name</span></span>

<span data-ttu-id="d24f5-448">**/api/wifi/networks (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-448">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="d24f5-449">枚举指定网络接口上的无线网络</span><span class="sxs-lookup"><span data-stu-id="d24f5-449">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="d24f5-450">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-450">Parameters</span></span>
* <span data-ttu-id="d24f5-451">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="d24f5-451">interface : network interface guid</span></span>

<span data-ttu-id="d24f5-452">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-452">Return data</span></span>
* <span data-ttu-id="d24f5-453">网络接口上发现的无线网络的列表，详细信息</span><span class="sxs-lookup"><span data-stu-id="d24f5-453">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="d24f5-454">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-454">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="d24f5-455">连接或断开指定接口上的网络连接</span><span class="sxs-lookup"><span data-stu-id="d24f5-455">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="d24f5-456">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-456">Parameters</span></span>
* <span data-ttu-id="d24f5-457">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="d24f5-457">interface : network interface guid</span></span>
* <span data-ttu-id="d24f5-458">ssid： ssid，hex64 编码，用于连接到</span><span class="sxs-lookup"><span data-stu-id="d24f5-458">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="d24f5-459">op：连接或断开连接</span><span class="sxs-lookup"><span data-stu-id="d24f5-459">op : connect or disconnect</span></span>
* <span data-ttu-id="d24f5-460">createprofile： yes 或 no</span><span class="sxs-lookup"><span data-stu-id="d24f5-460">createprofile : yes or no</span></span>
* <span data-ttu-id="d24f5-461">key：共享密钥，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="d24f5-461">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="d24f5-462">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="d24f5-462">Windows Performance Recorder</span></span>

<span data-ttu-id="d24f5-463">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-463">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="d24f5-464">上传 "配置文件，并使用上传的配置文件开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="d24f5-464">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="d24f5-465">有效负载</span><span class="sxs-lookup"><span data-stu-id="d24f5-465">Payload</span></span>
* <span data-ttu-id="d24f5-466">多部分相容的 http 正文</span><span class="sxs-lookup"><span data-stu-id="d24f5-466">multi-part conforming http body</span></span>

<span data-ttu-id="d24f5-467">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-467">Return data</span></span>
* <span data-ttu-id="d24f5-468">返回 "会话状态。</span><span class="sxs-lookup"><span data-stu-id="d24f5-468">Returns the WPR session status.</span></span>

<span data-ttu-id="d24f5-469">**/api/wpr/status (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-469">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="d24f5-470">检索 "会话的状态</span><span class="sxs-lookup"><span data-stu-id="d24f5-470">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="d24f5-471">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-471">Return data</span></span>
* <span data-ttu-id="d24f5-472">"会话状态。</span><span class="sxs-lookup"><span data-stu-id="d24f5-472">WPR session status.</span></span>

<span data-ttu-id="d24f5-473">**/api/wpr/trace (获取)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-473">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="d24f5-474">停止 " (性能) 跟踪会话</span><span class="sxs-lookup"><span data-stu-id="d24f5-474">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="d24f5-475">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-475">Return data</span></span>
* <span data-ttu-id="d24f5-476">返回跟踪 ETL 文件</span><span class="sxs-lookup"><span data-stu-id="d24f5-476">Returns the trace ETL file</span></span>

<span data-ttu-id="d24f5-477">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="d24f5-477">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="d24f5-478">启动 " (性能) 跟踪会话</span><span class="sxs-lookup"><span data-stu-id="d24f5-478">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="d24f5-479">参数</span><span class="sxs-lookup"><span data-stu-id="d24f5-479">Parameters</span></span>
* <span data-ttu-id="d24f5-480">配置文件：配置文件名称。</span><span class="sxs-lookup"><span data-stu-id="d24f5-480">profile : Profile name.</span></span> <span data-ttu-id="d24f5-481">可用的配置文件存储在 perfprofiles/profiles.js</span><span class="sxs-lookup"><span data-stu-id="d24f5-481">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="d24f5-482">返回数据</span><span class="sxs-lookup"><span data-stu-id="d24f5-482">Return data</span></span>
* <span data-ttu-id="d24f5-483">在 "开始" 中，返回 "会话状态。</span><span class="sxs-lookup"><span data-stu-id="d24f5-483">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="d24f5-484">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d24f5-484">See also</span></span>
* [<span data-ttu-id="d24f5-485">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="d24f5-485">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="d24f5-486"> (UWP) 的设备门户核心 API 参考 </span><span class="sxs-lookup"><span data-stu-id="d24f5-486">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
