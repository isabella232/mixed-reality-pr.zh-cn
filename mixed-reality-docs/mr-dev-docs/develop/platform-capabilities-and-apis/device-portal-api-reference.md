---
title: 设备门户 API 参考
description: HoloLens 上 Windows 设备门户的 API 参考
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens，Windows 设备门户，API，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 1085f6c948ab7fe0ff8cb3801ebb0b883570acbc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677966"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="514a2-104">设备门户 API 参考</span><span class="sxs-lookup"><span data-stu-id="514a2-104">Device portal API reference</span></span>

<span data-ttu-id="514a2-105">[Windows 设备门户](using-the-windows-device-portal.md)中的所有内容都是在 REST API 的基础之上构建的，你可以使用它以编程方式访问数据和控制设备。</span><span class="sxs-lookup"><span data-stu-id="514a2-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="514a2-106">应用常见问题</span><span class="sxs-lookup"><span data-stu-id="514a2-106">App deloyment</span></span>

<span data-ttu-id="514a2-107">**/api/app/packagemanager/package (删除)**</span><span class="sxs-lookup"><span data-stu-id="514a2-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="514a2-108">卸载应用</span><span class="sxs-lookup"><span data-stu-id="514a2-108">Uninstalls an app</span></span>

<span data-ttu-id="514a2-109">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-109">Parameters</span></span>
* <span data-ttu-id="514a2-110">package：要卸载的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="514a2-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="514a2-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="514a2-112">安装应用程序</span><span class="sxs-lookup"><span data-stu-id="514a2-112">Installs an App</span></span>

<span data-ttu-id="514a2-113">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-113">Parameters</span></span>
* <span data-ttu-id="514a2-114">package：要安装的包的文件名。</span><span class="sxs-lookup"><span data-stu-id="514a2-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="514a2-115">有效负载</span><span class="sxs-lookup"><span data-stu-id="514a2-115">Payload</span></span>
* <span data-ttu-id="514a2-116">多部分相容的 http 正文</span><span class="sxs-lookup"><span data-stu-id="514a2-116">multi-part conforming http body</span></span>

<span data-ttu-id="514a2-117">**/api/app/packagemanager/packages (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="514a2-118">检索系统上已安装应用的列表，详细信息</span><span class="sxs-lookup"><span data-stu-id="514a2-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="514a2-119">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-119">Return data</span></span>
* <span data-ttu-id="514a2-120">包含详细信息的已安装包列表</span><span class="sxs-lookup"><span data-stu-id="514a2-120">List of installed packages with details</span></span>

<span data-ttu-id="514a2-121">**/api/app/packagemanager/state (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="514a2-122">获取正在进行的应用安装的状态</span><span class="sxs-lookup"><span data-stu-id="514a2-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="514a2-123">转储集合</span><span class="sxs-lookup"><span data-stu-id="514a2-123">Dump collection</span></span>

<span data-ttu-id="514a2-124">**/api/debug/dump/usermode/crashcontrol (删除)**</span><span class="sxs-lookup"><span data-stu-id="514a2-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="514a2-125">为旁加载应用禁用故障转储收集</span><span class="sxs-lookup"><span data-stu-id="514a2-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="514a2-126">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-126">Parameters</span></span>
* <span data-ttu-id="514a2-127">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="514a2-127">packageFullname : package name</span></span>

<span data-ttu-id="514a2-128">**/api/debug/dump/usermode/crashcontrol (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="514a2-129">获取旁加载应用故障转储收集的设置</span><span class="sxs-lookup"><span data-stu-id="514a2-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="514a2-130">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-130">Parameters</span></span>
* <span data-ttu-id="514a2-131">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="514a2-131">packageFullname : package name</span></span>

<span data-ttu-id="514a2-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="514a2-133">启用和设置旁加载应用的转储控件设置</span><span class="sxs-lookup"><span data-stu-id="514a2-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="514a2-134">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-134">Parameters</span></span>
* <span data-ttu-id="514a2-135">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="514a2-135">packageFullname : package name</span></span>

<span data-ttu-id="514a2-136">**/api/debug/dump/usermode/crashdump (删除)**</span><span class="sxs-lookup"><span data-stu-id="514a2-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="514a2-137">删除旁加载应用程序的故障转储</span><span class="sxs-lookup"><span data-stu-id="514a2-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="514a2-138">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-138">Parameters</span></span>
* <span data-ttu-id="514a2-139">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="514a2-139">packageFullname : package name</span></span>
* <span data-ttu-id="514a2-140">文件名：转储文件名</span><span class="sxs-lookup"><span data-stu-id="514a2-140">fileName : dump file name</span></span>

<span data-ttu-id="514a2-141">**/api/debug/dump/usermode/crashdump (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="514a2-142">检索旁加载应用的故障转储</span><span class="sxs-lookup"><span data-stu-id="514a2-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="514a2-143">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-143">Parameters</span></span>
* <span data-ttu-id="514a2-144">packageFullname：包名称</span><span class="sxs-lookup"><span data-stu-id="514a2-144">packageFullname : package name</span></span>
* <span data-ttu-id="514a2-145">文件名：转储文件名</span><span class="sxs-lookup"><span data-stu-id="514a2-145">fileName : dump file name</span></span>

<span data-ttu-id="514a2-146">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-146">Return data</span></span>
* <span data-ttu-id="514a2-147">转储文件。</span><span class="sxs-lookup"><span data-stu-id="514a2-147">Dump file.</span></span> <span data-ttu-id="514a2-148">与 WinDbg 或 Visual Studio 一起检查</span><span class="sxs-lookup"><span data-stu-id="514a2-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="514a2-149">**/api/debug/dump/usermode/dumps (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="514a2-150">返回旁加载应用的所有崩溃转储的列表</span><span class="sxs-lookup"><span data-stu-id="514a2-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="514a2-151">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-151">Return data</span></span>
* <span data-ttu-id="514a2-152">每端加载的应用的故障转储列表</span><span class="sxs-lookup"><span data-stu-id="514a2-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="514a2-153">ETW</span><span class="sxs-lookup"><span data-stu-id="514a2-153">ETW</span></span>

<span data-ttu-id="514a2-154">**/api/etw/providers (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="514a2-155">枚举注册的提供程序</span><span class="sxs-lookup"><span data-stu-id="514a2-155">Enumerates registered providers</span></span>

<span data-ttu-id="514a2-156">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-156">Return data</span></span>
* <span data-ttu-id="514a2-157">提供程序列表、友好名称和 GUID</span><span class="sxs-lookup"><span data-stu-id="514a2-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="514a2-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="514a2-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="514a2-159">创建实时 ETW 会话;通过 websocket 进行管理。</span><span class="sxs-lookup"><span data-stu-id="514a2-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="514a2-160">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-160">Return data</span></span>
* <span data-ttu-id="514a2-161">已启用的提供程序中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="514a2-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="514a2-162">全息操作系统</span><span class="sxs-lookup"><span data-stu-id="514a2-162">Holographic OS</span></span>

<span data-ttu-id="514a2-163">**/api/holographic/os/etw/customproviders (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="514a2-164">返回未向系统注册的 HoloLens 特定 ETW 提供程序的列表</span><span class="sxs-lookup"><span data-stu-id="514a2-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="514a2-165">**/api/holographic/os/services (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="514a2-166">返回所有正在运行的服务的状态。</span><span class="sxs-lookup"><span data-stu-id="514a2-166">Returns the states of all services running.</span></span>

<span data-ttu-id="514a2-167">**/api/holographic/os/settings/ipd (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="514a2-168">获取存储的 IPD (Interpupillary 距离) （以毫米为单位）</span><span class="sxs-lookup"><span data-stu-id="514a2-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="514a2-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="514a2-170">设置 IPD</span><span class="sxs-lookup"><span data-stu-id="514a2-170">Sets the IPD</span></span>

<span data-ttu-id="514a2-171">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-171">Parameters</span></span>
* <span data-ttu-id="514a2-172">ipd：要设置的新 IPD 值（以毫米为单位）</span><span class="sxs-lookup"><span data-stu-id="514a2-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="514a2-173">**/api/holographic/os/webmanagement/settings/https (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="514a2-174">获取设备门户的 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="514a2-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="514a2-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="514a2-176">为设备门户设置 HTTPS 要求</span><span class="sxs-lookup"><span data-stu-id="514a2-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="514a2-177">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-177">Parameters</span></span>
* <span data-ttu-id="514a2-178">必需：是、否或默认值</span><span class="sxs-lookup"><span data-stu-id="514a2-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="514a2-179">全息认知</span><span class="sxs-lookup"><span data-stu-id="514a2-179">Holographic Perception</span></span>

<span data-ttu-id="514a2-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="514a2-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="514a2-181">接受 websocket 升级，并运行以 30 fps 发送更新的感知客户端。</span><span class="sxs-lookup"><span data-stu-id="514a2-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="514a2-182">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-182">Parameters</span></span>
* <span data-ttu-id="514a2-183">clientmode： "active" 强制在无法被动建立时强制视觉跟踪模式</span><span class="sxs-lookup"><span data-stu-id="514a2-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="514a2-184">全息热量</span><span class="sxs-lookup"><span data-stu-id="514a2-184">Holographic Thermal</span></span>

<span data-ttu-id="514a2-185">**/api/holographic/thermal/stage (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="514a2-186">获取设备的热阶段 (0 正常，1温，2严重) </span><span class="sxs-lookup"><span data-stu-id="514a2-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="514a2-187">地图管理器</span><span class="sxs-lookup"><span data-stu-id="514a2-187">Map Manager</span></span>

<span data-ttu-id="514a2-188">**/api/holographic/mapmanager/mapFiles (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="514a2-189">获取可用映射文件 () 的列表。</span><span class="sxs-lookup"><span data-stu-id="514a2-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="514a2-190">**/api/holographic/mapmanager/anchorFiles (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="514a2-191">获取 () 的可用定位点文件的列表。</span><span class="sxs-lookup"><span data-stu-id="514a2-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="514a2-192">**/api/holographic/mapmanager/srdbFiles (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="514a2-193">获取可用空间重构数据库文件 () 的列表。</span><span class="sxs-lookup"><span data-stu-id="514a2-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="514a2-194">**/api/holographic/mapmanager/getanchors (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="514a2-195">获取当前用户的持久定位点的列表。</span><span class="sxs-lookup"><span data-stu-id="514a2-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="514a2-196">下载/上传/删除文件</span><span class="sxs-lookup"><span data-stu-id="514a2-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="514a2-197">**/api/holographic/mapmanager/download (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="514a2-198">下载映射、定位点或空间重构数据库文件。</span><span class="sxs-lookup"><span data-stu-id="514a2-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="514a2-199">文件之前必须已上载或导出。</span><span class="sxs-lookup"><span data-stu-id="514a2-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="514a2-200">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-200">Parameters</span></span>
* <span data-ttu-id="514a2-201">FileName：要下载的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="514a2-202">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="514a2-203">**/api/holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="514a2-204">上载映射、定位点或空间重构数据库文件。</span><span class="sxs-lookup"><span data-stu-id="514a2-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="514a2-205">文件上传后，以后可以导入该文件以供系统使用。</span><span class="sxs-lookup"><span data-stu-id="514a2-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="514a2-206">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-206">Parameters</span></span>
* <span data-ttu-id="514a2-207">file：要上传的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="514a2-208">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-208">Example:</span></span>
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

<span data-ttu-id="514a2-209">**/api/holographic/mapmanager/delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="514a2-210">删除映射、定位点或空间重构数据库文件。</span><span class="sxs-lookup"><span data-stu-id="514a2-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="514a2-211">文件之前必须已上载或导出。</span><span class="sxs-lookup"><span data-stu-id="514a2-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="514a2-212">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-212">Parameters</span></span>
* <span data-ttu-id="514a2-213">FileName：要删除的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="514a2-214">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="514a2-215">导出</span><span class="sxs-lookup"><span data-stu-id="514a2-215">Export</span></span>

<span data-ttu-id="514a2-216">**/api/holographic/mapmanager/export (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="514a2-217">导出系统当前使用的映射。</span><span class="sxs-lookup"><span data-stu-id="514a2-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="514a2-218">导出后，可以下载它。</span><span class="sxs-lookup"><span data-stu-id="514a2-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="514a2-219">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="514a2-220">**/api/holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="514a2-221">导出系统当前使用的映射。</span><span class="sxs-lookup"><span data-stu-id="514a2-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="514a2-222">导出后，可以下载它。</span><span class="sxs-lookup"><span data-stu-id="514a2-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="514a2-223">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="514a2-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="514a2-225">导出系统当前使用的映射和定位点。</span><span class="sxs-lookup"><span data-stu-id="514a2-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="514a2-226">导出后，可以下载。</span><span class="sxs-lookup"><span data-stu-id="514a2-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="514a2-227">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="514a2-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="514a2-229">导出系统当前使用的映射和空间重建数据库。</span><span class="sxs-lookup"><span data-stu-id="514a2-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="514a2-230">导出后，可以下载它们。</span><span class="sxs-lookup"><span data-stu-id="514a2-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="514a2-231">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="514a2-232">导入</span><span class="sxs-lookup"><span data-stu-id="514a2-232">Import</span></span>

<span data-ttu-id="514a2-233">**/api/holographic/mapmanager/import (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="514a2-234">向系统指示当前使用应使用的映射。</span><span class="sxs-lookup"><span data-stu-id="514a2-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="514a2-235">可对已导出或上载的文件调用。</span><span class="sxs-lookup"><span data-stu-id="514a2-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="514a2-236">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-236">Parameters</span></span>
* <span data-ttu-id="514a2-237">FileName：要使用的映射的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="514a2-238">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="514a2-239">**/api/holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="514a2-240">向系统指示当前使用的定位点。</span><span class="sxs-lookup"><span data-stu-id="514a2-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="514a2-241">可对已导出或上载的文件调用。</span><span class="sxs-lookup"><span data-stu-id="514a2-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="514a2-242">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-242">Parameters</span></span>
* <span data-ttu-id="514a2-243">FileName：要使用的定位点的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="514a2-244">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="514a2-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="514a2-246">向系统指示当前使用的空间重建数据库。</span><span class="sxs-lookup"><span data-stu-id="514a2-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="514a2-247">可对已导出或上载的文件调用。</span><span class="sxs-lookup"><span data-stu-id="514a2-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="514a2-248">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-248">Parameters</span></span>
* <span data-ttu-id="514a2-249">FileName：要使用的空间映射 db 的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="514a2-250">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="514a2-251">其他</span><span class="sxs-lookup"><span data-stu-id="514a2-251">Other</span></span>

<span data-ttu-id="514a2-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="514a2-253">重置系统地图、锚定和空间重建数据库。</span><span class="sxs-lookup"><span data-stu-id="514a2-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="514a2-254">例如：</span><span class="sxs-lookup"><span data-stu-id="514a2-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="514a2-255">**/api/holographic/mapmanager/status (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="514a2-256">获取系统的状态，包括上次导入的映射、定位点和空间重构数据库文件。</span><span class="sxs-lookup"><span data-stu-id="514a2-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="514a2-257">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="514a2-257">Mixed Reality Capture</span></span>

<span data-ttu-id="514a2-258">**/api/holographic/mrc/file (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="514a2-259">从设备下载混合现实文件。</span><span class="sxs-lookup"><span data-stu-id="514a2-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="514a2-260">使用 op = stream query 参数进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="514a2-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="514a2-261">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-261">Parameters</span></span>
* <span data-ttu-id="514a2-262">filename：要获取的视频文件的名称、hex64 编码</span><span class="sxs-lookup"><span data-stu-id="514a2-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="514a2-263">op： stream</span><span class="sxs-lookup"><span data-stu-id="514a2-263">op : stream</span></span>

<span data-ttu-id="514a2-264">**/api/holographic/mrc/file (删除)**</span><span class="sxs-lookup"><span data-stu-id="514a2-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="514a2-265">从设备中删除混合现实记录。</span><span class="sxs-lookup"><span data-stu-id="514a2-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="514a2-266">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-266">Parameters</span></span>
* <span data-ttu-id="514a2-267">filename：要删除的文件的名称，hex64 已编码</span><span class="sxs-lookup"><span data-stu-id="514a2-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="514a2-268">**/api/holographic/mrc/files (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="514a2-269">返回存储在设备上的混合现实文件的列表</span><span class="sxs-lookup"><span data-stu-id="514a2-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="514a2-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="514a2-271">采用混合现实照片，并在设备上创建文件</span><span class="sxs-lookup"><span data-stu-id="514a2-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="514a2-272">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-272">Parameters</span></span>
* <span data-ttu-id="514a2-273">holo：捕获全息影像： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="514a2-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="514a2-274">pv：捕获 PV 摄像机： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="514a2-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="514a2-275">RenderFromCamera： (HoloLens 2 仅) 照片/视频相机的透视中呈现： true 或 false (默认为 true) </span><span class="sxs-lookup"><span data-stu-id="514a2-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="514a2-276">**/api/holographic/mrc/settings (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="514a2-277">获取默认的混合现实捕获设置</span><span class="sxs-lookup"><span data-stu-id="514a2-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="514a2-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="514a2-279">设置默认的混合现实捕获设置。</span><span class="sxs-lookup"><span data-stu-id="514a2-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="514a2-280">其中一些设置适用于系统的 MRC 照片和视频捕获。</span><span class="sxs-lookup"><span data-stu-id="514a2-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="514a2-281">**/api/holographic/mrc/status (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="514a2-282">获取 Windows 设备门户内混合现实捕获的状态。</span><span class="sxs-lookup"><span data-stu-id="514a2-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="514a2-283">\**_响应_* _</span><span class="sxs-lookup"><span data-stu-id="514a2-283">\**_Response_* _</span></span>

<span data-ttu-id="514a2-284">响应包含一个 JSON 属性，用于指示 Windows 设备门户是否正在录制视频。</span><span class="sxs-lookup"><span data-stu-id="514a2-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="514a2-285">_ */api/holographic/mrc/thumbnail (获取)*\*</span><span class="sxs-lookup"><span data-stu-id="514a2-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="514a2-286">获取指定文件的缩略图图像。</span><span class="sxs-lookup"><span data-stu-id="514a2-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="514a2-287">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-287">Parameters</span></span>
* <span data-ttu-id="514a2-288">文件名：要为其请求缩略图的文件的名称，hex64 已编码</span><span class="sxs-lookup"><span data-stu-id="514a2-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="514a2-289">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="514a2-290">启动混合现实记录</span><span class="sxs-lookup"><span data-stu-id="514a2-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="514a2-291">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-291">Parameters</span></span>
* <span data-ttu-id="514a2-292">holo：捕获全息影像： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="514a2-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="514a2-293">pv：捕获 PV 摄像机： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="514a2-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="514a2-294">mic：捕获麦克风： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="514a2-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="514a2-295">环回：捕获应用音频： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="514a2-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="514a2-296">RenderFromCamera： (HoloLens 2 仅) 照片/视频相机的透视中呈现： true 或 false (默认为 true) </span><span class="sxs-lookup"><span data-stu-id="514a2-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="514a2-297">vstab： (HoloLens 2 仅) 启用视频抖动： true 或 false (默认为 true) </span><span class="sxs-lookup"><span data-stu-id="514a2-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="514a2-298">vstabbuffer： (HoloLens 2 仅) 视频稳定性缓冲区延迟：0到30帧 (默认为15帧) </span><span class="sxs-lookup"><span data-stu-id="514a2-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="514a2-299">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="514a2-300">停止当前混合现实记录</span><span class="sxs-lookup"><span data-stu-id="514a2-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="514a2-301">混合现实流式处理</span><span class="sxs-lookup"><span data-stu-id="514a2-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="514a2-302">HoloLens 支持混合现实的实时预览，通过块区下载零碎的工作方式。</span><span class="sxs-lookup"><span data-stu-id="514a2-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="514a2-303">混合现实流共享相同的参数集来控制捕获的内容：</span><span class="sxs-lookup"><span data-stu-id="514a2-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="514a2-304">holo：捕获全息影像： true 或 false</span><span class="sxs-lookup"><span data-stu-id="514a2-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="514a2-305">pv：捕获 PV 摄像机： true 或 false</span><span class="sxs-lookup"><span data-stu-id="514a2-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="514a2-306">mic：捕获麦克风： true 或 false</span><span class="sxs-lookup"><span data-stu-id="514a2-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="514a2-307">环回：捕获应用音频： true 或 false</span><span class="sxs-lookup"><span data-stu-id="514a2-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="514a2-308">如果未指定任何内容：将捕获全息影像、照片/视频相机和应用音频</span><span class="sxs-lookup"><span data-stu-id="514a2-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="514a2-309">如果已指定任何参数：未指定的参数将默认为 false</span><span class="sxs-lookup"><span data-stu-id="514a2-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="514a2-310">可选参数 (仅限 HoloLens 2) </span><span class="sxs-lookup"><span data-stu-id="514a2-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="514a2-311">RenderFromCamera：从照片/视频相机的角度呈现： true 或 false (默认为 true) </span><span class="sxs-lookup"><span data-stu-id="514a2-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="514a2-312">vstab：启用视频抖动： true 或 false (默认为 false) </span><span class="sxs-lookup"><span data-stu-id="514a2-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="514a2-313">vstabbuffer：视频稳定缓冲区延迟：0到30帧 (默认为15帧) </span><span class="sxs-lookup"><span data-stu-id="514a2-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="514a2-314">**/api/holographic/stream/live.mp4 (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="514a2-315">1280x720p 30fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="514a2-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="514a2-316">**/api/holographic/stream/live_high.mp4 (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="514a2-317">1280x720p 30fps 5Mbit 流。</span><span class="sxs-lookup"><span data-stu-id="514a2-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="514a2-318">**/api/holographic/stream/live_med.mp4 (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="514a2-319">854x480p 30fps 2.5 Mbit stream。</span><span class="sxs-lookup"><span data-stu-id="514a2-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="514a2-320">**/api/holographic/stream/live_low.mp4 (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="514a2-321">428x240p 15fps 0.6 Mbit stream。</span><span class="sxs-lookup"><span data-stu-id="514a2-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="514a2-322">网络</span><span class="sxs-lookup"><span data-stu-id="514a2-322">Networking</span></span>

<span data-ttu-id="514a2-323">**/api/networking/ipconfig (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="514a2-324">获取当前 ip 配置</span><span class="sxs-lookup"><span data-stu-id="514a2-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="514a2-325">操作系统信息</span><span class="sxs-lookup"><span data-stu-id="514a2-325">OS Information</span></span>

<span data-ttu-id="514a2-326">**/api/os/info (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="514a2-327">获取操作系统信息</span><span class="sxs-lookup"><span data-stu-id="514a2-327">Gets operating system information</span></span>

<span data-ttu-id="514a2-328">**/api/os/machinename (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="514a2-329">获取计算机名称</span><span class="sxs-lookup"><span data-stu-id="514a2-329">Gets the machine name</span></span>

<span data-ttu-id="514a2-330">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="514a2-331">设置计算机名称</span><span class="sxs-lookup"><span data-stu-id="514a2-331">Sets the machine name</span></span>

<span data-ttu-id="514a2-332">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-332">Parameters</span></span>
* <span data-ttu-id="514a2-333">名称：要设置为的新计算机名称，hex64 编码为</span><span class="sxs-lookup"><span data-stu-id="514a2-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="514a2-334">感知模拟控制</span><span class="sxs-lookup"><span data-stu-id="514a2-334">Perception Simulation Control</span></span>

<span data-ttu-id="514a2-335">**/api/holographic/simulation/control/mode (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="514a2-336">获取模拟模式</span><span class="sxs-lookup"><span data-stu-id="514a2-336">Get the simulation mode</span></span>

<span data-ttu-id="514a2-337">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="514a2-338">设置模拟模式</span><span class="sxs-lookup"><span data-stu-id="514a2-338">Set the simulation mode</span></span>

<span data-ttu-id="514a2-339">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-339">Parameters</span></span>
* <span data-ttu-id="514a2-340">模式：模拟模式：默认、模拟、远程、旧</span><span class="sxs-lookup"><span data-stu-id="514a2-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="514a2-341">**/api/holographic/simulation/control/stream (删除)**</span><span class="sxs-lookup"><span data-stu-id="514a2-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="514a2-342">删除控件流。</span><span class="sxs-lookup"><span data-stu-id="514a2-342">Delete a control stream.</span></span>

<span data-ttu-id="514a2-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="514a2-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="514a2-344">为控制流打开 web 套接字连接。</span><span class="sxs-lookup"><span data-stu-id="514a2-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="514a2-345">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="514a2-346">需要创建控制流 (优先级) 或将数据发送到创建的流 (streamId 必需的) 。</span><span class="sxs-lookup"><span data-stu-id="514a2-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="514a2-347">已发布的数据的类型应为 "application/八进制流"。</span><span class="sxs-lookup"><span data-stu-id="514a2-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="514a2-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="514a2-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="514a2-349">请求模拟视频流，其中包含在处于 "模拟" 模式时呈现给系统的内容。</span><span class="sxs-lookup"><span data-stu-id="514a2-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="514a2-350">首先发送一个简单的格式说明符标头，然后再发送一个-264 编码的纹理，每个纹理前面都有一个标头，指示眼睛索引和纹理大小。</span><span class="sxs-lookup"><span data-stu-id="514a2-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="514a2-351">感知播放</span><span class="sxs-lookup"><span data-stu-id="514a2-351">Perception Simulation Playback</span></span>

<span data-ttu-id="514a2-352">**/api/holographic/simulation/playback/file (删除)**</span><span class="sxs-lookup"><span data-stu-id="514a2-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="514a2-353">删除记录。</span><span class="sxs-lookup"><span data-stu-id="514a2-353">Delete a recording.</span></span>

<span data-ttu-id="514a2-354">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-354">Parameters</span></span>
* <span data-ttu-id="514a2-355">录制：要删除的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="514a2-356">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="514a2-357">上传记录。</span><span class="sxs-lookup"><span data-stu-id="514a2-357">Upload a recording.</span></span>

<span data-ttu-id="514a2-358">**/api/holographic/simulation/playback/files (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="514a2-359">获取所有记录。</span><span class="sxs-lookup"><span data-stu-id="514a2-359">Get all recordings.</span></span>

<span data-ttu-id="514a2-360">**/api/holographic/simulation/playback/session (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="514a2-361">获取记录的当前播放状态。</span><span class="sxs-lookup"><span data-stu-id="514a2-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="514a2-362">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-362">Parameters</span></span>
* <span data-ttu-id="514a2-363">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-363">recording : Name of recording.</span></span>

<span data-ttu-id="514a2-364">**/api/holographic/simulation/playback/session/file (删除)**</span><span class="sxs-lookup"><span data-stu-id="514a2-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="514a2-365">卸载记录。</span><span class="sxs-lookup"><span data-stu-id="514a2-365">Unload a recording.</span></span>

<span data-ttu-id="514a2-366">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-366">Parameters</span></span>
* <span data-ttu-id="514a2-367">录制：要卸载的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="514a2-368">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="514a2-369">加载记录。</span><span class="sxs-lookup"><span data-stu-id="514a2-369">Load a recording.</span></span>

<span data-ttu-id="514a2-370">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-370">Parameters</span></span>
* <span data-ttu-id="514a2-371">录制：要加载的记录的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="514a2-372">**/api/holographic/simulation/playback/session/files (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="514a2-373">获取所有加载的记录。</span><span class="sxs-lookup"><span data-stu-id="514a2-373">Get all loaded recordings.</span></span>

<span data-ttu-id="514a2-374">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="514a2-375">暂停录制。</span><span class="sxs-lookup"><span data-stu-id="514a2-375">Pause a recording.</span></span>

<span data-ttu-id="514a2-376">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-376">Parameters</span></span>
* <span data-ttu-id="514a2-377">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-377">recording : Name of recording.</span></span>

<span data-ttu-id="514a2-378">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="514a2-379">播放录制。</span><span class="sxs-lookup"><span data-stu-id="514a2-379">Play a recording.</span></span>

<span data-ttu-id="514a2-380">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-380">Parameters</span></span>
* <span data-ttu-id="514a2-381">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-381">recording : Name of recording.</span></span>

<span data-ttu-id="514a2-382">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="514a2-383">停止录制。</span><span class="sxs-lookup"><span data-stu-id="514a2-383">Stop a recording.</span></span>

<span data-ttu-id="514a2-384">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-384">Parameters</span></span>
* <span data-ttu-id="514a2-385">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-385">recording : Name of recording.</span></span>

<span data-ttu-id="514a2-386">**/api/holographic/simulation/playback/session/types (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="514a2-387">获取已加载记录中数据的类型。</span><span class="sxs-lookup"><span data-stu-id="514a2-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="514a2-388">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-388">Parameters</span></span>
* <span data-ttu-id="514a2-389">记录：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="514a2-390">感知模拟记录</span><span class="sxs-lookup"><span data-stu-id="514a2-390">Perception Simulation Recording</span></span>

<span data-ttu-id="514a2-391">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="514a2-392">开始记录。</span><span class="sxs-lookup"><span data-stu-id="514a2-392">Start a recording.</span></span> <span data-ttu-id="514a2-393">一次只能有一个记录处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="514a2-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="514a2-394">必须设置 head、双手、spatialMapping 或环境之一。</span><span class="sxs-lookup"><span data-stu-id="514a2-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="514a2-395">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-395">Parameters</span></span>
* <span data-ttu-id="514a2-396">head：设置为1以记录头数据。</span><span class="sxs-lookup"><span data-stu-id="514a2-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="514a2-397">动手：设置为1以记录手型数据。</span><span class="sxs-lookup"><span data-stu-id="514a2-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="514a2-398">spatialMapping：设置为1以记录空间映射。</span><span class="sxs-lookup"><span data-stu-id="514a2-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="514a2-399">环境：设置为1以记录环境数据。</span><span class="sxs-lookup"><span data-stu-id="514a2-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="514a2-400">name：记录的名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-400">name : Name of the recording.</span></span>
* <span data-ttu-id="514a2-401">singleSpatialMappingFrame：设置为1将仅记录单个空间映射框架。</span><span class="sxs-lookup"><span data-stu-id="514a2-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="514a2-402">**/api/holographic/simulation/recording/status (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="514a2-403">获取记录状态。</span><span class="sxs-lookup"><span data-stu-id="514a2-403">Get recording state.</span></span>

<span data-ttu-id="514a2-404">**/api/holographic/simulation/recording/stop (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="514a2-405">停止当前记录。</span><span class="sxs-lookup"><span data-stu-id="514a2-405">Stop the current recording.</span></span> <span data-ttu-id="514a2-406">记录将以文件的形式返回。</span><span class="sxs-lookup"><span data-stu-id="514a2-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="514a2-407">性能数据</span><span class="sxs-lookup"><span data-stu-id="514a2-407">Performance data</span></span>

<span data-ttu-id="514a2-408">**/api/resourcemanager/processes (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="514a2-409">返回正在运行的进程的列表以及详细信息</span><span class="sxs-lookup"><span data-stu-id="514a2-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="514a2-410">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-410">Return data</span></span>
* <span data-ttu-id="514a2-411">JSON，包含进程列表和每个进程的详细信息</span><span class="sxs-lookup"><span data-stu-id="514a2-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="514a2-412">**/api/resourcemanager/systemperf (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="514a2-413">返回系统性能统计信息 (i/o 读/写、内存统计信息等。</span><span class="sxs-lookup"><span data-stu-id="514a2-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="514a2-414">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-414">Return data</span></span>
* <span data-ttu-id="514a2-415">包含系统信息的 JSON： CPU、GPU、内存、网络、IO</span><span class="sxs-lookup"><span data-stu-id="514a2-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="514a2-416">强力</span><span class="sxs-lookup"><span data-stu-id="514a2-416">Power</span></span>

<span data-ttu-id="514a2-417">**/api/power/battery (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="514a2-418">获取当前电池状态</span><span class="sxs-lookup"><span data-stu-id="514a2-418">Gets the current battery state</span></span>

<span data-ttu-id="514a2-419">**/api/power/state (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="514a2-420">检查系统是否处于低功耗状态</span><span class="sxs-lookup"><span data-stu-id="514a2-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="514a2-421">远程控制</span><span class="sxs-lookup"><span data-stu-id="514a2-421">Remote Control</span></span>

<span data-ttu-id="514a2-422">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="514a2-423">重新启动目标设备</span><span class="sxs-lookup"><span data-stu-id="514a2-423">Restarts the target device</span></span>

<span data-ttu-id="514a2-424">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="514a2-425">关闭目标设备</span><span class="sxs-lookup"><span data-stu-id="514a2-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="514a2-426">任务管理器</span><span class="sxs-lookup"><span data-stu-id="514a2-426">Task Manager</span></span>

<span data-ttu-id="514a2-427">**/api/taskmanager/app (删除)**</span><span class="sxs-lookup"><span data-stu-id="514a2-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="514a2-428">停止现代应用</span><span class="sxs-lookup"><span data-stu-id="514a2-428">Stops a modern app</span></span>

<span data-ttu-id="514a2-429">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-429">Parameters</span></span>
* <span data-ttu-id="514a2-430">包：应用包的完整名称，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="514a2-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="514a2-431">forcestop：强制停止所有进程 (= yes) </span><span class="sxs-lookup"><span data-stu-id="514a2-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="514a2-432">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="514a2-433">启动新式应用</span><span class="sxs-lookup"><span data-stu-id="514a2-433">Starts a modern app</span></span>

<span data-ttu-id="514a2-434">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-434">Parameters</span></span>
* <span data-ttu-id="514a2-435">appid：要启动的应用的 PRAID，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="514a2-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="514a2-436">包：应用包的完整名称，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="514a2-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="514a2-437">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="514a2-437">WiFi Management</span></span>

<span data-ttu-id="514a2-438">**/api/wifi/interfaces (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="514a2-439">枚举无线网络接口</span><span class="sxs-lookup"><span data-stu-id="514a2-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="514a2-440">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-440">Return data</span></span>
* <span data-ttu-id="514a2-441">包含详细信息 (GUID、说明等 ) 的无线接口列表</span><span class="sxs-lookup"><span data-stu-id="514a2-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="514a2-442">**/api/wifi/network (删除)**</span><span class="sxs-lookup"><span data-stu-id="514a2-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="514a2-443">删除与指定接口上的网络相关联的配置文件</span><span class="sxs-lookup"><span data-stu-id="514a2-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="514a2-444">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-444">Parameters</span></span>
* <span data-ttu-id="514a2-445">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="514a2-445">interface : network interface guid</span></span>
* <span data-ttu-id="514a2-446">配置文件：配置文件名称</span><span class="sxs-lookup"><span data-stu-id="514a2-446">profile : profile name</span></span>

<span data-ttu-id="514a2-447">**/api/wifi/networks (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="514a2-448">枚举指定网络接口上的无线网络</span><span class="sxs-lookup"><span data-stu-id="514a2-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="514a2-449">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-449">Parameters</span></span>
* <span data-ttu-id="514a2-450">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="514a2-450">interface : network interface guid</span></span>

<span data-ttu-id="514a2-451">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-451">Return data</span></span>
* <span data-ttu-id="514a2-452">网络接口上发现的无线网络的列表，详细信息</span><span class="sxs-lookup"><span data-stu-id="514a2-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="514a2-453">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="514a2-454">连接或断开指定接口上的网络连接</span><span class="sxs-lookup"><span data-stu-id="514a2-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="514a2-455">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-455">Parameters</span></span>
* <span data-ttu-id="514a2-456">接口：网络接口 guid</span><span class="sxs-lookup"><span data-stu-id="514a2-456">interface : network interface guid</span></span>
* <span data-ttu-id="514a2-457">ssid： ssid，hex64 编码，用于连接到</span><span class="sxs-lookup"><span data-stu-id="514a2-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="514a2-458">op：连接或断开连接</span><span class="sxs-lookup"><span data-stu-id="514a2-458">op : connect or disconnect</span></span>
* <span data-ttu-id="514a2-459">createprofile： yes 或 no</span><span class="sxs-lookup"><span data-stu-id="514a2-459">createprofile : yes or no</span></span>
* <span data-ttu-id="514a2-460">key：共享密钥，hex64 编码</span><span class="sxs-lookup"><span data-stu-id="514a2-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="514a2-461">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="514a2-461">Windows Performance Recorder</span></span>

<span data-ttu-id="514a2-462">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="514a2-463">上传 "配置文件，并使用上传的配置文件开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="514a2-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="514a2-464">有效负载</span><span class="sxs-lookup"><span data-stu-id="514a2-464">Payload</span></span>
* <span data-ttu-id="514a2-465">多部分相容的 http 正文</span><span class="sxs-lookup"><span data-stu-id="514a2-465">multi-part conforming http body</span></span>

<span data-ttu-id="514a2-466">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-466">Return data</span></span>
* <span data-ttu-id="514a2-467">返回 "会话状态。</span><span class="sxs-lookup"><span data-stu-id="514a2-467">Returns the WPR session status.</span></span>

<span data-ttu-id="514a2-468">**/api/wpr/status (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="514a2-469">检索 "会话的状态</span><span class="sxs-lookup"><span data-stu-id="514a2-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="514a2-470">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-470">Return data</span></span>
* <span data-ttu-id="514a2-471">"会话状态。</span><span class="sxs-lookup"><span data-stu-id="514a2-471">WPR session status.</span></span>

<span data-ttu-id="514a2-472">**/api/wpr/trace (获取)**</span><span class="sxs-lookup"><span data-stu-id="514a2-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="514a2-473">停止 " (性能) 跟踪会话</span><span class="sxs-lookup"><span data-stu-id="514a2-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="514a2-474">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-474">Return data</span></span>
* <span data-ttu-id="514a2-475">返回跟踪 ETL 文件</span><span class="sxs-lookup"><span data-stu-id="514a2-475">Returns the trace ETL file</span></span>

<span data-ttu-id="514a2-476">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="514a2-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="514a2-477">启动 " (性能) 跟踪会话</span><span class="sxs-lookup"><span data-stu-id="514a2-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="514a2-478">参数</span><span class="sxs-lookup"><span data-stu-id="514a2-478">Parameters</span></span>
* <span data-ttu-id="514a2-479">配置文件：配置文件名称。</span><span class="sxs-lookup"><span data-stu-id="514a2-479">profile : Profile name.</span></span> <span data-ttu-id="514a2-480">可用的配置文件存储在 perfprofiles/profiles.js</span><span class="sxs-lookup"><span data-stu-id="514a2-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="514a2-481">返回数据</span><span class="sxs-lookup"><span data-stu-id="514a2-481">Return data</span></span>
* <span data-ttu-id="514a2-482">在 "开始" 中，返回 "会话状态。</span><span class="sxs-lookup"><span data-stu-id="514a2-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="514a2-483">请参阅</span><span class="sxs-lookup"><span data-stu-id="514a2-483">See also</span></span>
* [<span data-ttu-id="514a2-484">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="514a2-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="514a2-485"> (UWP) 的设备门户核心 API 参考 </span><span class="sxs-lookup"><span data-stu-id="514a2-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
