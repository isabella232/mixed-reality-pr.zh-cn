---
title: 设备门户 API 参考
description: 随时了解 Windows 设备门户 API HoloLens 开发。
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens，Windows 设备门户，API，混合现实耳机，Windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 6b41c569917150c303da933a75d354f574fb579ba676dac281e9cde2bfc59818
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207835"
---
# <a name="device-portal-api-reference"></a>设备门户 API 参考

[Windows 设备门户](using-the-windows-device-portal.md)中的所有内容都是基于 REST API 的基础构建的，你可以使用它以编程方式访问数据和控制设备。

## <a name="app-deloyment"></a>应用常见问题

**/api/app/packagemanager/package (删除)**

卸载应用

参数
* package：要卸载的包的文件名。

**/api/app/packagemanager/package (POST)**

安装应用程序

参数
* package：要安装的包的文件名。

有效负载
* 多部分相容的 http 正文

**/api/app/packagemanager/packages (获取)**

检索系统上已安装应用的列表，详细信息

返回数据
* 包含详细信息的已安装包列表

**/api/app/packagemanager/state (获取)**

获取正在进行的应用安装的状态

## <a name="dump-collection"></a>转储集合

**/api/debug/dump/usermode/crashcontrol (删除)**

为旁加载应用禁用故障转储收集

参数
* packageFullname：包名称

**/api/debug/dump/usermode/crashcontrol (获取)**

获取旁加载应用故障转储收集的设置

参数
* packageFullname：包名称

**/api/debug/dump/usermode/crashcontrol (POST)**

启用和设置旁加载应用的转储控件设置

参数
* packageFullname：包名称

**/api/debug/dump/usermode/crashdump (删除)**

删除旁加载应用程序的故障转储

参数
* packageFullname：包名称
* 文件名：转储文件名

**/api/debug/dump/usermode/crashdump (获取)**

检索旁加载应用的故障转储

参数
* packageFullname：包名称
* 文件名：转储文件名

返回数据
* 转储文件。 用 WinDbg 或 Visual Studio 进行检查

**/api/debug/dump/usermode/dumps (获取)**

返回旁加载应用的所有崩溃转储的列表

返回数据
* 每端加载的应用的故障转储列表

## <a name="etw"></a>ETW

**/api/etw/providers (获取)**

枚举注册的提供程序

返回数据
* 提供程序列表、友好名称和 GUID

**/api/etw/session/realtime (GET/WebSocket)**

创建实时 ETW 会话;通过 websocket 进行管理。

返回数据
* 已启用的提供程序中的 ETW 事件

## <a name="holographic-os"></a>全息操作系统

**/api/holographic/os/etw/customproviders (获取)**

返回未向系统注册 HoloLens 特定 ETW 提供程序的列表

**/api/holographic/os/services (获取)**

返回所有正在运行的服务的状态。

**/api/holographic/os/settings/ipd (获取)**

获取存储的 IPD (Interpupillary 距离) （以毫米为单位）

**/api/holographic/os/settings/ipd (POST)**

设置 IPD

参数
* ipd：要设置的新 IPD 值（以毫米为单位）

**/api/holographic/os/webmanagement/settings/https (获取)**

获取设备门户的 HTTPS 要求

**/api/holographic/os/webmanagement/settings/https (POST)**

为设备门户设置 HTTPS 要求

参数
* 必需：是、否或默认值

## <a name="holographic-perception"></a>全息认知

**/api/holographic/perception/client (GET/WebSocket)**

接受 websocket 升级，并运行以 30 fps 发送更新的感知客户端。

参数
* clientmode： "active" 强制在无法被动建立时强制视觉跟踪模式

## <a name="holographic-thermal"></a>全息热量

**/api/holographic/thermal/stage (获取)**

获取设备的热阶段 (0 正常，1温，2严重) 

## <a name="map-manager"></a>地图管理器

**/api/holographic/mapmanager/mapFiles (获取)**

获取可用映射文件 () 的列表。

**/api/holographic/mapmanager/anchorFiles (获取)**

获取 () 的可用定位点文件的列表。

**/api/holographic/mapmanager/srdbFiles (获取)**

获取可用空间重构数据库文件 () 的列表。

**/api/holographic/mapmanager/getanchors (获取)**

获取当前用户的持久定位点的列表。 

### <a name="downloaduploaddelete-files"></a>下载/Upload/delete 文件
**/api/holographic/mapmanager/download (获取)**

下载映射、定位点或空间重构数据库文件。 文件之前必须已上载或导出。

参数
* FileName：要下载的文件的名称。

示例： 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

**/api/holographic/mapmanager/upload (POST)**

上传地图、定位点或空间重建数据库文件。 上传文件后，可以将其导入系统使用。

参数
* file：要上传的文件的名称。

示例：
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

**/api/holographic/mapmanager/delete (POST)**

删除地图、定位点或空间重建数据库文件。 文件必须以前已上传或导出。

参数
* FileName：要删除的文件的名称。

示例： 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a>导出

**/api/holographic/mapmanager/export (POST)**

导出系统当前使用的映射。 导出后，可以下载它。 

示例： 
```
$.post("/api/holographic/mapmanager/export")
```

**/api/holographic/mapmanager/exportanchors (POST)**

导出系统当前使用的映射。 导出后，可以下载它。 示例： 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

**/api/holographic/mapmanager/exportmapandanchors (POST)**

导出系统当前使用的地图和定位点。 导出后，可以下载它们。 示例： 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**

导出系统当前使用的地图和空间重建数据库。 导出后，可以下载它们。 

示例： 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a>导入

**/api/holographic/mapmanager/import (POST)**

向系统指示当前应该使用哪个映射。 可以在已导出或上传的文件上调用 。

参数
* FileName：要使用的映射的名称。 

示例： 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importanchors (POST)**

向系统指示当前应该使用哪些定位点。 可以在已导出或上传的文件上调用 。

参数
* FileName：要使用的定位点的名称。 

示例： 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importspatialmappingdb (POST)**

向系统指示当前应该使用的空间重建数据库。 可以在已导出或上传的文件上调用 。

参数
* FileName：要使用的空间映射数据库的名称。 

示例： 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a>其他

**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**

重置系统地图、定位点和空间重建数据库。

示例： 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

**/api/holographic/mapmanager/status (GET)**

获取系统的状态，包括上次导入的地图、定位点和空间重建数据库文件。 


## <a name="mixed-reality-capture"></a>混合现实捕获

**/api/holographic/mrc/file (GET)**

从设备下载混合现实文件。 使用 op=stream 查询参数进行流式处理。

参数
* filename：要获取的视频文件的名称，十六进制 64 编码
* op ： stream

**/api/holographic/mrc/file (DELETE)**

从设备中删除混合现实录制。

参数
* filename：要删除的文件的名称、十六进制 64 编码

**/api/holographic/mrc/files (GET)**

返回设备上存储的混合现实文件列表

**/api/holographic/mrc/photo (POST)**

拍摄混合现实照片，在设备上创建文件

参数
* holo：捕获全息影像：true 或 false (默认值为 false) 
* pv ：捕获 PV 相机：true 或 false (默认值为 false) 
* RenderFromCamera： (HoloLens 2) /视频相机的角度进行渲染：true 或 false (默认值为 true) 

**/api/holographic/mrc/settings (GET)**

获取默认的混合现实捕获设置

**/api/holographic/mrc/settings (POST)**

设置默认的混合现实捕获设置。  其中一些设置应用于系统的 MRC 照片和视频捕获。

**/api/holographic/mrc/status (GET)**

获取混合现实捕获在 Windows 设备门户。

***响应***

响应包含一个 JSON 属性，Windows 设备门户是否正在录制视频。

``` javascript
{"IsRecording" : boolean}
```

**/api/holographic/mrc/thumbnail (GET)**

获取指定文件的缩略图。

参数
* filename：要请求缩略图的文件的名称（十六进制 64 编码）

**/api/holographic/mrc/video/control/start (POST)**

启动混合现实录制

参数
* holo：捕获全息影像：true 或 false (默认值为 false) 
* pv ：捕获 PV 相机：true 或 false (默认值为 false) 
* 麦克风：捕获麦克风：true 或 false (默认值为 false) 
* loopback ：捕获应用音频：true 或 false (默认值为 false) 
* RenderFromCamera： (HoloLens 2) /视频相机的角度进行渲染：true 或 false (默认值为 true) 
* vstab： (HoloLens 2) 视频稳定：true 或 false (默认值为 true) 
* vst (HoloLens 2：) 视频稳定缓冲区延迟：0 到 30 帧 (默认为 15 帧) 

**/api/holographic/mrc/video/control/stop (POST)**

停止当前混合现实录制

## <a name="mixed-reality-streaming"></a>混合现实流式处理

> [!CAUTION]
> 由于环回隔离，无法从设备的应用内部连接到混合现实流式处理。

HoloLens分块下载分段 mp4，支持混合现实实时预览。

混合现实流共享一组相同的参数来控制捕获内容：
* holo：捕获全息影像：true 或 false
* pv ：捕获 PV 相机：true 或 false
* 麦克风：捕获麦克风：true 或 false
* loopback ：捕获应用音频：true 或 false

如果未指定其中任何一项：将捕获全息影像、照片/视频相机以及应用音频<br>
如果指定了任何参数：未指定的参数将默认为 false

可选参数 (HoloLens 2参数) 
* RenderFromCamera：从照片/视频相机的角度呈现：true 或 false (默认值为 true) 
* vstab：启用视频稳定：true 或 false (默认值为 false) 
* vst提示：视频稳定缓冲区延迟：0 到 30 帧 (默认为 15 帧) 

**/api/holographic/stream/live.mp4 (GET)**

1280x720p 30fps 5M 位流。

**/api/holographic/stream/live_high.mp4 (GET)**

1280x720p 30fps 5M 位流。

**/api/holographic/stream/live_med.mp4 (GET)**

854x480p 30fps 2.5M 位流。

**/api/holographic/stream/live_low.mp4 (GET)**

428x240p 15fps 0.6Mbit 流。

## <a name="networking"></a>网络

**/api/networking/ipconfig (GET)**

获取当前 IP 配置

## <a name="os-information"></a>OS 信息

**/api/os/info (GET)**

获取操作系统信息

**/api/os/machinename (GET)**

获取计算机名称

**/api/os/machinename (POST)**

设置计算机名称

参数
* 名称：新计算机名称，十六进制 64 编码，设置为

## <a name="perception-simulation-control"></a>感知模拟控制

**/api/holographic/simulation/control/mode (GET)**

获取模拟模式

**/api/holographic/simulation/control/mode (POST)**

设置模拟模式

参数
* mode ：模拟模式：default、simulation、remote、legacy

**/api/holographic/simulation/control/stream (DELETE)**

删除控件流。

**/api/holographic/simulation/control/stream (GET/WebSocket)**

打开控件流的 Web 套接字连接。

**/api/holographic/simulation/control/stream (POST)**

创建控制流 (需要优先级) 或将数据发布到创建的流 (streamId) 。 发布的数据应为"application/octet-stream"类型。

**/api/holographic/simulation/display/stream (GET/WebSocket)**

请求一个模拟视频流，其中包含在"模拟"模式下呈现给系统显示的内容。  最初将发送一个简单的格式描述符标头，后跟 H.264 编码的纹理，每个纹理前面都有一个指示眼睛索引和纹理大小的标头。

## <a name="perception-simulation-playback"></a>感知模拟播放

**/api/holographic/simulation/playback/file (DELETE)**

删除记录。

参数
* recording：要删除的录制的名称。

**/api/holographic/simulation/playback/file (POST)**

Upload录制内容。

**/api/holographic/simulation/playback/files (GET)**

获取所有录制内容。

**/api/holographic/simulation/playback/session (GET)**

获取录制的当前播放状态。

参数
* recording：记录的名称。

**/api/holographic/simulation/playback/session/file (DELETE)**

卸载记录。

参数
* recording：要卸载的录制的名称。

**/api/holographic/simulation/playback/session/file (POST)**

加载记录。

参数
* recording：要加载的录制的名称。

**/api/holographic/simulation/playback/session/files (GET)**

获取所有已加载的录制内容。

**/api/holographic/simulation/playback/session/pause (POST)**

暂停录制。

参数
* recording：记录的名称。

**/api/holographic/simulation/playback/session/play (POST)**

播放录制内容。

参数
* recording：记录的名称。

**/api/holographic/simulation/playback/session/stop (POST)**

停止录制。

参数
* recording：记录的名称。

**/api/holographic/simulation/playback/session/types (GET)**

获取加载的记录中的数据类型。

参数
* recording：记录的名称。

## <a name="perception-simulation-recording"></a>感知模拟记录

**/api/holographic/simulation/recording/start (POST)**

开始录制。 一次只能有一个记录处于活动状态。 必须设置头部、手部、spatialMapping 或环境之一。

参数
* head：设置为 1 以记录头数据。
* hand：设置为 1 以记录手部数据。
* spatialMapping：设置为 1 以记录空间映射。
* environment：设置为 1 以记录环境数据。
* name：记录的名称。
* singleSpatialMappingFrame：设置为1将仅记录单个空间映射框架。

**/api/holographic/simulation/recording/status (获取)**

获取记录状态。

**/api/holographic/simulation/recording/stop (获取)**

停止当前记录。 记录将以文件的形式返回。

## <a name="performance-data"></a>性能数据

**/api/resourcemanager/processes (获取)**

返回正在运行的进程的列表以及详细信息

返回数据
* JSON，包含进程列表和每个进程的详细信息

**/api/resourcemanager/systemperf (获取)**

返回系统性能统计信息 (i/o 读/写、内存统计信息等。

返回数据
* 包含系统信息的 JSON： CPU、GPU、内存、网络、IO

## <a name="power"></a>强力

**/api/power/battery (获取)**

获取当前电池状态

**/api/power/state (获取)**

检查系统是否处于低功耗状态

## <a name="remote-control"></a>远程控制

**/api/control/restart (POST)**

重新启动目标设备

**/api/control/shutdown (POST)**

关闭目标设备

## <a name="task-manager"></a>任务管理器

**/api/taskmanager/app (删除)**

停止现代应用

参数
* 包：应用包的完整名称，hex64 编码
* forcestop：强制停止所有进程 (= yes) 

**/api/taskmanager/app (POST)**

启动新式应用

参数
* appid：要启动的应用的 PRAID，hex64 编码
* 包：应用包的完整名称，hex64 编码

## <a name="wifi-management"></a>WiFi 管理

**/api/wifi/interfaces (获取)**

枚举无线网络接口

返回数据
* 包含详细信息 (GUID、说明等 ) 的无线接口列表

**/api/wifi/network (删除)**

删除与指定接口上的网络相关联的配置文件

参数
* 接口：网络接口 guid
* 配置文件：配置文件名称

**/api/wifi/networks (获取)**

枚举指定网络接口上的无线网络

参数
* 接口：网络接口 guid

返回数据
* 网络接口上发现的无线网络的列表，详细信息

**/api/wifi/network (POST)**

连接或断开指定接口上的网络连接

参数
* 接口：网络接口 guid
* ssid： ssid，hex64 编码，用于连接到
* op：连接或断开连接
* createprofile： yes 或 no
* key：共享密钥，hex64 编码

## <a name="windows-performance-recorder"></a>Windows Performance Recorder

**/api/wpr/customtrace (POST)**

上传 "配置文件，并使用上传的配置文件开始跟踪。

有效负载
* 多部分相容的 http 正文

返回数据
* 返回 "会话状态。

**/api/wpr/status (获取)**

检索 "会话的状态

返回数据
* "会话状态。

**/api/wpr/trace (获取)**

停止 " (性能) 跟踪会话

返回数据
* 返回跟踪 ETL 文件

**/api/wpr/trace (POST)**

启动 " (性能) 跟踪会话

参数
* 配置文件：配置文件名称。 可用的配置文件存储在 perfprofiles/profiles.js

返回数据
* 在 "开始" 中，返回 "会话状态。

## <a name="see-also"></a>另请参阅
* [使用 Windows 设备门户](using-the-windows-device-portal.md)
* [ (UWP) 的设备门户核心 API 参考 ](/windows/uwp/debug-test-perf/device-portal-api-core)