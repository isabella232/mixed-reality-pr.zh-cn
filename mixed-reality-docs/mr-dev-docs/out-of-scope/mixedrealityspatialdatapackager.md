---
title: 混合现实空间数据包装程序文档
description: 现在已弃用混合现实空间数据包装器工具，在任何平台上都不再运行。 建议改为使用地图管理器工具。
author: hferrone
ms.author: v-hferrone
ms.date: 08/03/2020
ms.topic: article
keywords: lbe、MixedRealitySpatialDataPackager.exe、MixedRealitySpatialDataPackager
ms.openlocfilehash: 93d598a6add8350850faadab241b254e9cb341aa
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583647"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="b1a5f-105">混合现实空间数据包装程序文档</span><span class="sxs-lookup"><span data-stu-id="b1a5f-105">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="b1a5f-106">已弃用</span><span class="sxs-lookup"><span data-stu-id="b1a5f-106">DEPRECATED</span></span> 
> 
> <span data-ttu-id="b1a5f-107">从8/1/2020 开始，此工具现在已弃用，在任何平台上不再起作用。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-107">As of 8/1/2020 this tool is now deprecated and no longer functions on any platform.</span></span> <span data-ttu-id="b1a5f-108">建议改为在设备门户中使用 " [映射管理器](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) " 工具。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-108">We recommend using the [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) tool in the Device Portal instead.</span></span> 
> 
> <span data-ttu-id="b1a5f-109">此工具及其操作按原样提供。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-109">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="b1a5f-110">如果没有任何通知，它可能会更改，并且可能不会与未来的 Windows 或 Windows Mixed Reality HMD 版本兼容。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-110">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span> 


## <a name="download"></a><span data-ttu-id="b1a5f-111">下载</span><span class="sxs-lookup"><span data-stu-id="b1a5f-111">Download</span></span>
 <span data-ttu-id="b1a5f-112">[在此处下载 MixedRealitySpatialDataPackager](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="b1a5f-112">Download [MixedRealitySpatialDataPackager here](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="device-support"></a><span data-ttu-id="b1a5f-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="b1a5f-113">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b1a5f-114"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="b1a5f-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b1a5f-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="b1a5f-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b1a5f-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b1a5f-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b1a5f-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="b1a5f-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b1a5f-118">混合现实空间数据包装器</span><span class="sxs-lookup"><span data-stu-id="b1a5f-118">Mixed Reality Spatial Data Packager</span></span></td>
        <td>❌</td>
        <td>❌</td>
        <td><span data-ttu-id="b1a5f-119">✔️</span><span class="sxs-lookup"><span data-stu-id="b1a5f-119">✔️</span></span></td>
    </tr>
</table>

## <a name="quickstart"></a><span data-ttu-id="b1a5f-120">快速入门</span><span class="sxs-lookup"><span data-stu-id="b1a5f-120">Quickstart</span></span>

<span data-ttu-id="b1a5f-121">混合现实空间数据包装器工具通过两步导出和导入过程将目标应用的空间数据从一台 PC 复制到另一台 PC。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-121">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="b1a5f-122">此工具必须以管理员权限运行，并在导入时删除现有空间数据。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-122">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="b1a5f-123">导出会使现有的空间数据保持不变。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-123">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="b1a5f-124">关键要求和限制：</span><span class="sxs-lookup"><span data-stu-id="b1a5f-124">Key requirements and limitations:</span></span>

1. <span data-ttu-id="b1a5f-125">必须具有管理员权限才能运行工具</span><span class="sxs-lookup"><span data-stu-id="b1a5f-125">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="b1a5f-126">运行该工具后，如果混合现实门户不稳定，可能需要重启电脑</span><span class="sxs-lookup"><span data-stu-id="b1a5f-126">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="b1a5f-127">当遇到空间数据版本不匹配或不兼容时，工具不会运行</span><span class="sxs-lookup"><span data-stu-id="b1a5f-127">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="b1a5f-128">工具将在导入时删除现有空间数据</span><span class="sxs-lookup"><span data-stu-id="b1a5f-128">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="b1a5f-129">如果导入进程失败，则无法还原以前的数据，除非已通过导出以前的数据进行了备份</span><span class="sxs-lookup"><span data-stu-id="b1a5f-129">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="b1a5f-130">针对空间映射数据的 "只读" 模式的导入功能的质量</span><span class="sxs-lookup"><span data-stu-id="b1a5f-130">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="b1a5f-131">映射最佳实践</span><span class="sxs-lookup"><span data-stu-id="b1a5f-131">Mapping Best Practices</span></span>

1. <span data-ttu-id="b1a5f-132">清除控制面板中的现有映射 (设置-> 混合现实 > 环境-> 明文环境数据) </span><span class="sxs-lookup"><span data-stu-id="b1a5f-132">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="b1a5f-133">确保光线足以进行良好跟踪，如果正在运行锁定的映射模式，则尝试维持相同的照明</span><span class="sxs-lookup"><span data-stu-id="b1a5f-133">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="b1a5f-134">如果可能，请避免深色、阴影区域旁的高照明区域，使光照动态范围较低</span><span class="sxs-lookup"><span data-stu-id="b1a5f-134">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="b1a5f-135">最大程度地减少空白、textureless 的图面，例如，将一系列不同海报置于白名单上</span><span class="sxs-lookup"><span data-stu-id="b1a5f-135">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="b1a5f-136">在场景中映射不包含动态对象的空间，例如移动人员</span><span class="sxs-lookup"><span data-stu-id="b1a5f-136">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="b1a5f-137">在导入时锁定地图 (通过预览体验) </span><span class="sxs-lookup"><span data-stu-id="b1a5f-137">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="b1a5f-138">当跟踪质量下降并且/或环境中的更改 (光源或对象布局中的更改时，解锁地图并重新扫描环境) \* \* _</span><span class="sxs-lookup"><span data-stu-id="b1a5f-138">Unlock the map and rescan the environment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout) \*\*_</span></span>

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="b1a5f-139">运行带辅助脚本的混合现实空间数据包装器</span><span class="sxs-lookup"><span data-stu-id="b1a5f-139">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="b1a5f-140">我们提供了 MRSpatialPackagerHelperScript.ps1，它运行映射包装器工具。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-140">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="b1a5f-141">脚本参数定义如下：</span><span class="sxs-lookup"><span data-stu-id="b1a5f-141">The script parameters are defined below:</span></span>

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="b1a5f-142">Powershell 脚本示例用法和输出</span><span class="sxs-lookup"><span data-stu-id="b1a5f-142">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="b1a5f-143">.\MRSpatialPackagerHelperScript.ps1 AppName holoshell-UserName Administrator-Mode MapxPath D:\temp\-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="b1a5f-143">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="b1a5f-144">如何使用 MixedRealitySpatialDataPackager.exe 导出</span><span class="sxs-lookup"><span data-stu-id="b1a5f-144">How to Export using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="b1a5f-145">从设备导出映射会生成两个 mapx 文件：获取 mapx 和 mapx。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-145">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="b1a5f-146">在导出过程中，除了指定的应用和用户创建的边界 (，如果) 存在，则删除所有空间锚。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-146">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="b1a5f-147">源包系列名称必须与现有的已安装应用匹配，否则 exe 将会失败。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-147">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="b1a5f-148">如何使用 MixedRealitySpatialDataPackager.exe 导入</span><span class="sxs-lookup"><span data-stu-id="b1a5f-148">How to Import using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="b1a5f-149">导入删除现有空间数据，并将其替换为指定目录中的数据。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-149">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="b1a5f-150">应用名称输入指定要为其导入空间锚点的目标应用的包名称，而目标用户 SID 指定应该有权访问已导入的空间锚的用户。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-150">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="b1a5f-151">目标包系列名称和用户 Sid 必须与电脑上的现有值匹配，否则 exe 将会失败。</span><span class="sxs-lookup"><span data-stu-id="b1a5f-151">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


<span data-ttu-id="b1a5f-152">_\*\*</span><span class="sxs-lookup"><span data-stu-id="b1a5f-152">_\*\*</span></span>
## <a name="error-messages"></a><span data-ttu-id="b1a5f-153">错误消息</span><span class="sxs-lookup"><span data-stu-id="b1a5f-153">Error Messages</span></span>
<span data-ttu-id="b1a5f-154">此外，以下错误消息还将附带 HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1a5f-154">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="b1a5f-155">如果有错误的参数无效</span><span class="sxs-lookup"><span data-stu-id="b1a5f-155">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="b1a5f-156">如果可执行文件未在管理员模式下运行</span><span class="sxs-lookup"><span data-stu-id="b1a5f-156">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="b1a5f-157">如果启用或禁用驱动程序时出错</span><span class="sxs-lookup"><span data-stu-id="b1a5f-157">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="b1a5f-158">如果验证空间数据库版本时出错</span><span class="sxs-lookup"><span data-stu-id="b1a5f-158">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="b1a5f-159">验证为目标导入/导出应用提供的包系列名称时出错</span><span class="sxs-lookup"><span data-stu-id="b1a5f-159">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="b1a5f-160">验证用户 SID 时出错</span><span class="sxs-lookup"><span data-stu-id="b1a5f-160">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="b1a5f-161">如果存在与目标或源空间数据文件相关的错误</span><span class="sxs-lookup"><span data-stu-id="b1a5f-161">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a><span data-ttu-id="b1a5f-162">如果存在与启动和停止频谱/SharedRealitySvc 相关的错误</span><span class="sxs-lookup"><span data-stu-id="b1a5f-162">If there was an error related to starting and stopping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```