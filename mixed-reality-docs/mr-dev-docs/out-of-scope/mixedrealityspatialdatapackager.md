---
title: 混合现实空间数据打包器文档
description: 混合现实空间数据打包器工具现已弃用，不再在任何平台上运行。 建议改为使用 Map Manager 工具。
author: hferrone
ms.author: v-hferrone
ms.date: 08/03/2020
ms.topic: article
keywords: lbe、MixedRealitySpatialDataPackager.exe、MixedRealitySpatialDataPackager
ms.openlocfilehash: 914e22c4e80385c93696ebd978000978e1e03f57706d466bdbb3cfcd5843f69e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213161"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>混合现实空间数据打包器文档

>[!NOTE]
> 已弃用 
> 
> 从 2020/8/1 开始，此工具现已弃用，不再在任何平台上运行。 建议改为在映射 [管理器](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) 设备门户。 
> 
> 此工具及其操作是像现在一样提供的。 它可能会更改，无需任何通知，并且可能与将来的 HMD Windows版本Windows Mixed Reality兼容。 


## <a name="download"></a>下载
 在此处 [下载 MixedRealitySpatialDataPackager](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>混合现实空间数据打包器</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>快速入门

混合现实空间数据打包器工具通过两步导出和导入过程，将目标应用的空间数据从一台电脑复制到另一台电脑。 该工具必须使用管理员权限运行，并删除导入时的现有空间数据。 导出使现有空间数据保持不变。

关键要求和限制：

1. 必须使用管理员权限运行工具 
2. 如果在运行该工具后混合现实门户不稳定，可能需要重启电脑
3. 遇到空间数据版本不匹配或不兼容时，工具不会运行
4. 工具将在导入时擦除现有空间数据
5. 如果导入过程失败，将无法还原以前的数据，除非之前通过导出进行了备份
6. 导入功能的质量取决于空间地图数据的"只读"模式
***

## <a name="mapping-best-practices"></a>映射最佳做法

1. 从混合现实 -控制面板 (设置 -> 混合现实 -> 环境 ->清除环境数据映射) 
2. 确保有足够的照明进行良好的跟踪，如果运行锁定的地图模式，请尝试保持相同的照明
3. 如果可能，请避免深色阴影区域旁边的高照明区域，使照明动态范围保持较低
4. 最小化空白无纹理表面，例如，将一系列不同的海报放在白色墙上
5. 映射场景中没有动态对象的空间，例如移动人员
6. 锁定通过 Insider Preview (提供的导入映射) 
7. 解锁地图，在跟踪质量下降和/或环境中存在更改 (或对象布局更改时重新扫描) 
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>使用助理脚本运行混合现实空间数据打包器

我们提供了MRSpatialPackagerHelperScript.ps1工具的映射打包程序。 


脚本参数定义如下：

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

### <a name="powershell-script-example-usage-and-output"></a>Powershell 脚本示例用法和输出

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D：\temp\ -LockMap 0
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

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a>如何使用 MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

从设备导出地图会生成两个 mapx 文件：het.mapx 和 sa.mapx。 在导出过程中，将删除除指定的应用和用户创建的边界之外的所有空间定位点 (（如果存在) ）。 源包系列名称必须与现有的已安装应用匹配，否则 exe 将失败。

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a>如何使用 MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
导入会删除现有空间数据，并将其替换为指定目录中的数据。 应用名称输入指定应导入的空间定位点等目标应用的包名称，目标用户 SID 指定应有权访问导入的空间定位点的用户。 目标包系列名称和用户 ID 必须与电脑上的现有值匹配，否则 exe 将失败。


***
## <a name="error-messages"></a>错误消息
此外，以下故障的错误消息还将附带 HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>如果出现错误，参数无效
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>如果可执行文件未在管理员模式下运行
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>如果启用或禁用驱动程序时出错
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>如果验证空间数据库版本时出错
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>如果验证为目标导入/导出应用提供的包系列名称时出错
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>如果验证用户 SID 时出错
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>如果发生与目标或源空间数据文件相关的错误
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>如果发生与启动和停止 Spectrum/SharedRealitySvc 相关的错误
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```