---
title: 应用模型
description: Windows Mixed Reality 使用通用 Windows 平台所提供的应用模型，该模型和环境适用于新式 Windows 应用。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP，应用模型，生命周期，暂停，恢复，磁贴，视图，合同，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: 941c0f3f81596e8465157121462b4150cefd8ac2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583210"
---
# <a name="app-model"></a>应用模型

Windows Mixed Reality 使用 [通用 Windows 平台](/windows/uwp/get-started/) 提供的应用模型 (UWP) ，这是新式 Windows 应用的模型和环境。 UWP 应用模型定义如何安全地安装、更新、版本化和删除应用。 它还控制应用程序的生命周期，即应用程序的执行、睡眠和停止，以及它们如何保持状态。 最后，应用程序模型涵盖与操作系统、文件和其他应用程序的集成和交互。

![在早餐区域中，在 Windows Mixed Reality 主页中安排的2D 应用](images/20160112-055908-hololens-500px.jpg)<br>
*在 Windows Mixed Reality 主页中显示2D 视图的应用*

## <a name="app-lifecycle"></a>应用生命周期

混合现实应用程序的生命周期涉及标准应用概念，如放置、启动、终止和删除。

### <a name="placement-is-launch"></a>启动位置

每个应用程序都通过将应用磁贴置于 windows [Mixed reality 主](../discover/navigating-the-windows-mixed-reality-home.md))  (仅[windows 辅助磁贴](/uwp/api/Windows.UI.StartScreen.SecondaryTile)，以混合现实的方式启动。 在放置时，这些应用磁贴会开始运行应用。 这些应用磁贴保留并停留在其放置位置，在任何时候想要返回到应用程序时都是如此。

![放置将辅助磁贴置于世界中](images/slide1-600px.png)<br>
*放置将辅助磁贴置于世界中*

定位完成后 (除非将应用启动 [到应用](app-model.md#protocols) 启动) ，否则应用将开始启动。 Windows Mixed Reality 一次可以运行有限数量的应用。 一旦你开始应用并启动应用，其他活动的应用可能会挂起。 挂起的应用程序会在放置应用程序的任何位置上将应用程序的最后一条状态的屏幕截图保留在其中。 有关处理恢复和其他生命周期事件的详细信息，请参阅 [Windows 10 UWP 应用生命周期](/windows/uwp/launch-resume/app-lifecycle)。

![放置磁贴后，应用将开始运行 ](images/slide2-500px.png) ![ 状态图，以使应用程序运行、挂起或未运行](images/ic576232-500px.png)<br>
*Left：放置磁贴后，应用将开始运行。Right：应用正在运行、已挂起或未运行的状态图。*

### <a name="remove-is-closeterminate-process"></a>删除为关闭/终止进程

在从世界中删除放置的应用磁贴时，基础进程将关闭。 这对于确保应用程序停止或重新启动有问题的应用程序很有用。

### <a name="app-suspensiontermination"></a>应用挂起/终止

在 [Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)中，用户可以通过从 "开始" 菜单启动应用程序并将应用磁贴置于世界中，为应用程序创建多个入口点。 每个应用磁贴表现为不同的入口点，并且在系统中有一个单独的磁贴实例。 针对每个应用实例的 [SecondaryTile](/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) 的查询将导致 **SecondaryTile** 。

当 UWP 应用暂停时，将获取当前状态的屏幕截图。

![显示已挂起应用程序的屏幕截图](images/slide9-800px.png)<br>
*显示已挂起应用程序的屏幕截图*

与其他 Windows 10 shell 的一个关键区别在于，如何通过 [CoreApplication](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) 和 [CoreWindow](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) 事件通知应用程序实例激活。

|  方案 |  正在恢复  |  已激活 | 
|----------|----------|----------|
|  从 "开始" 菜单启动应用程序的新实例  |   |  使用新的 [TileId](/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) **激活** | 
|  从 "开始" 菜单启动应用的第二个实例  |   |  使用新的 **TileId** **激活** | 
|  选择当前不处于活动状态的应用的实例  |   |  已通过与实例关联的 **TileId** **激活** | 
|  选择其他应用，然后选择以前的活动实例  |  **继续** 引发  |  | 
|  选择一个不同的应用，然后选择先前处于非活动状态的实例  |  **继续** 引发  |  然后通过与实例关联的 **TileId** **激活** | 

### <a name="extended-execution"></a>扩展执行

有时，您的应用程序需要在后台继续工作或播放音频。 HoloLens 上提供了[后台任务](/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest)。

![应用可在后台运行](images/slide10-800px.png)<br>
*应用可在后台运行*

## <a name="app-views"></a>应用视图

当应用程序激活时，可以选择想要显示的视图类型。 对于应用的 **CoreApplication**，始终有一个主要 [应用视图](/uwp/api/Windows.UI.ViewManagement.ApplicationView) 以及要创建的任意数量的其他应用视图。 在桌面上，可以将应用视图视为窗口。 混合现实应用模板会创建一个 Unity 项目，其中主要应用视图是 [沉浸式](app-views.md)的。 

你的应用可以使用类似于 XAML 的技术创建额外的2D 应用视图，以使用 Windows 10 功能，如应用内购买。 如果你的应用程序是作为其他 Windows 10 设备的 UWP 应用启动的，则主视图为2D。 不过，您可以通过添加另一个可沉浸显示体验 volumetrically 的应用程序视图，在混合现实中 "亮起"。 想象一下，在 XAML 中生成照片查看器应用程序，其中的 "幻灯片" 按钮切换到了一个沉浸式应用视图，可在世界各地的应用程序中星城照片。

![正在运行的应用程序可以有2D 视图或沉浸式视图](images/slide3-800px.png)<br>
*正在运行的应用程序可以有2D 视图或沉浸式视图*

### <a name="creating-an-immersive-view"></a>创建沉浸式视图

混合现实应用创建可使用 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace) 类型实现的沉浸式视图。

即使是从桌面启动，纯粹沉浸式应用程序也应始终在启动时创建一个沉浸式视图。 沉浸式视图始终显示在耳机中，而不考虑它们的创建位置。 激活沉浸式视图将显示混合现实门户，并指导用户将其放在耳机上。

以2D 视图在桌面监视器上启动的应用程序可能会创建辅助沉浸式视图，以显示耳机中的内容。 这种情况的一个示例是监视器上的2D 边缘窗口，该窗口在耳机中显示360度视频。

![在沉浸式视图中运行的应用程序是唯一可见的](images/slide4-800px.png)<br>
*在沉浸式视图中运行的应用程序是唯一可见的*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 主页中的2D 视图

沉浸式视图以外的任何内容都将呈现为世界上的2D 视图。

应用可能在桌面监视器和耳机上都有2D 视图。 新的2D 视图将放在与创建它的视图相同的 shell 中，无论是在监视器上还是在头戴式耳机中。 目前，应用或用户无法在混合现实主页与监视器之间移动2D 视图。

![在2D 视图中运行的应用与其他应用共享混合世界的空间](images/slide5-800px.png)<br>
*在二维视图中运行的应用与其他应用共享空间*

### <a name="placement-of-additional-app-tiles"></a>其他应用磁贴的位置

您可以根据需要将任意数量的应用程序与 [辅助磁贴 api](/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)放在世界。 这些 "固定" 磁贴将显示为初始屏幕，用户必须在该屏幕中放置，然后可以使用该屏幕来启动应用。 Windows Mixed Reality 目前不支持将任何2D 磁贴内容呈现为动态磁贴。

![应用可以有多个使用辅助磁贴的放置](images/slide6-800px.png)<br>
*应用可以有多个使用辅助磁贴的放置*

### <a name="switching-views"></a>切换视图

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>从 2D XAML 视图切换到沉浸式视图

如果应用使用 XAML，则 XAML [IFrameworkViewSource](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) 将控制应用的第一个视图。 在激活 **CoreWindow** 之前，应用需要切换到沉浸式视图，以确保应用直接启动到沉浸式体验。

使用 [CreateNewView](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) 和 [ApplicationViewSwitcher](/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) 将其设为活动视图（CoreApplication）。

> [!NOTE]
>* 在从 XAML 视图切换到沉浸式视图时，请勿指定 **SwitchAsync** 的 [ApplicationViewSwitchingOptions ConsolidateViews](/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions)标志，否则将从世界中删除启动该应用程序的盖板。
>* 应使用与要切换到的视图关联的 [调度](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher)程序来调用 **SwitchAsync** 。
>* 如果需要启动虚拟键盘或要激活其他应用程序，则需要 **SwitchAsync** 到 XAML 视图。

![](images/slide7-600px.png)当应用进入沉浸式视图时，应用可以在2d 视图和沉浸式视图之间切换 ![ ，而混合世界和其他应用会消失](images/slide8-600px.png)<br>
*Left：应用可以在2D 视图和沉浸式视图之间切换。Right：当应用进入沉浸式视图时，Windows Mixed Reality home 和其他应用会消失。*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>从沉浸式视图切换回键盘 XAML 视图

在两个视图之间来回切换的一个常见原因是在混合现实应用中显示一个键盘。 如果应用显示的是2D 视图，shell 只能显示系统键盘。 如果应用需要获取文本输入，它可能会提供一个带有文本输入字段的自定义 XAML 视图，切换到该视图，然后在输入完成后切换回。

与上一节一样，可以使用 SwitchAsync 从沉浸式视图过渡回 XAML 视图。 **ApplicationViewSwitcher**

## <a name="app-size"></a>应用大小

2D 应用视图始终显示在固定的虚拟石板中。 这会使所有2D 视图显示完全相同的内容量。 下面是有关应用程序的2D 视图大小的更多详细信息：
* 调整大小时，会保留应用的长宽比。
* 调整大小不会更改应用 [分辨率和缩放比例](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) 。
* 应用无法查询世界上的实际大小。

![2D 应用显示为固定的窗口大小](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*具有2D 视图的应用以固定窗口大小显示*

## <a name="app-tiles"></a>应用磁贴

"开始" 菜单将标准的小型磁贴和中型磁贴用于混合现实中的 "pin" 和 " **所有应用** " 列表。 

![Windows Mixed Reality 的 "开始" 菜单](images/start-500px.png)<br>
*Windows Mixed Reality 的 "开始" 菜单*

## <a name="app-to-app-interactions"></a>应用到应用交互

当你生成应用时，你可以访问 Windows 10 上提供的应用程序通信机制的丰富应用程序。 许多新的协议 Api 和文件注册在 HoloLens 上完美地工作，以实现应用程序的启动和通信。 

对于桌面耳机，与给定文件扩展名或协议相关联的应用程序可能是一个 Win32 应用程序，只能在桌面监视器或桌面石板中出现。

### <a name="protocols"></a>协议

HoloLens 支持通过Windows.System 启动应用程序 [ 。启动器 Api](/uwp/api/Windows.System.Launcher)。

启动其他应用程序时需要考虑以下事项：

* 执行非模式启动（如 [LaunchUriAsync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)）时，用户必须先放置应用，然后再与它交互。

* 当执行模式启动（例如通过 [LaunchUriForResultsAsync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)）时，将在窗口顶部放置模式应用。

* Windows Mixed Reality 无法在排他视图之上覆盖应用程序。 为了显示已启动的应用程序，Windows 会使用户回到世界以显示应用程序。

### <a name="file-pickers"></a>文件选取器

HoloLens 同时支持 [FileOpenPicker](/uwp/api/Windows.Storage.Pickers.FileOpenPicker) 和 [FileSavePicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 约定。 但是，没有预安装的应用可满足文件选取器协定。 例如，可以从 Microsoft Store 中安装这些应用-OneDrive。

如果安装了多个文件选取器应用，则不会看到任何消除歧义 UI，因此无法选择要启动的应用。 相反，将选择第一个安装的文件选取器。 保存文件时，会生成包含时间戳的文件名。 用户无法对其进行更改。

默认情况下，本地支持以下扩展插件：

|  应用  |  扩展 | 
|----------|----------|
|  照片  |  bmp、gif、jpg、png、avi、mov、.wmv、wmv | 
|  Microsoft Edge  |  htm，html，pdf，svg，xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>应用协定和 Windows Mixed Reality 扩展

应用协定和扩展点允许注册应用，以利用更深入的操作系统功能，例如处理文件扩展名或使用后台任务。 此列表列出了支持的和不支持的合同以及在 HoloLens 上的扩展点。

|  协定或扩展  |  是否支持？ | 
|----------|----------|
| [帐户图片提供程序 (扩展) ](/previous-versions/windows/apps/hh464906(v=win.10)#account_picture_provider) | 不支持 | 
| [警报](/previous-versions/windows/apps/hh464906(v=win.10)#alarm) | 不支持 | 
| [应用服务](/previous-versions/windows/apps/hh464906(v=win.10)#app_service) | 支持但无法完全正常运行 | 
| [约会提供程序](/previous-versions/windows/apps/hh464906(v=win.10)#appointmnets_provider) | 不支持 | 
| [自动播放 (扩展) ](/previous-versions/windows/apps/hh464906(v=win.10)#autoplay) | 不支持 | 
| [后台任务 (扩展) ](/previous-versions/windows/apps/hh464906(v=win.10)#background_tasts) | 部分支持的 (并非所有触发器都适用)  | 
| [更新任务 (扩展) ](/previous-versions/windows/apps/hh464906(v=win.10)#update_task) | 支持 | 
| [缓存的文件更新程序协定](/previous-versions/windows/apps/hh464906(v=win.10)#cached_file_updater) | 支持 | 
| [照相机设置 (扩展) ](/previous-versions/windows/apps/hh464906(v=win.10)#camera_settings) | 不支持 | 
| [拨号协议](/previous-versions/windows/apps/hh464906(v=win.10)#dial_protocol) | 不支持 | 
| [文件激活 (扩展) ](/previous-versions/windows/apps/hh464906(v=win.10)#file_activation) | 支持 | 
| [文件打开选取器协定](/previous-versions/windows/apps/hh464906(v=win.10)#file_open_picker_contract) | 支持 | 
| [文件保存选取器协定](/previous-versions/windows/apps/hh464906(v=win.10)#file_save_picker_contract) | 支持 | 
| [锁定屏幕调用](/previous-versions/windows/apps/hh464906(v=win.10)#lock_screen_call) | 不支持 | 
| [媒体播放](/previous-versions/windows/apps/hh464906(v=win.10)#media_playback) | 不支持 | 
| [扮演合同](/previous-versions/windows/apps/hh464906(v=win.10)#playto_contract) | 不支持 | 
| [预安装的配置任务](/previous-versions/windows/apps/hh464906(v=win.10)#preinstalled_config_task) | 不支持 | 
| [打印三维工作流](/previous-versions/windows/apps/hh464906(v=win.10)#print_3d_workflow) | 支持 | 
| [ (扩展) 打印任务设置 ](/previous-versions/windows/apps/hh464906(v=win.10)#print_task_settings) | 不支持 | 
| [URI 激活 (扩展) ](/previous-versions/windows/apps/hh464906(v=win.10)#protocol_activation) | 支持 | 
| [受限启动](/previous-versions/windows/apps/hh464906(v=win.10)#restricted_launch) | 不支持 | 
| [搜索协定](/previous-versions/windows/apps/hh464906(v=win.10)#search_contract) | 不支持 | 
| [设置约定](/previous-versions/windows/apps/hh464906(v=win.10)#settings_contract) | 不支持 | 
| [共享协定](/previous-versions/windows/apps/hh464906(v=win.10)#share_contract) | 不支持 | 
| [SSL/证书 (扩展) ](/previous-versions/windows/apps/hh464906(v=win.10)#ssl_certificates) | 支持 | 
| [Web 帐户提供程序](/previous-versions/windows/apps/hh464906(v=win.10)#web_account_provider) | 支持 | 

## <a name="app-file-storage"></a>应用文件存储

所有存储都通过 [Windows. 存储命名空间](/uwp/api/Windows.Storage)。 HoloLens 不支持应用存储同步/漫游。 有关详细信息，请查看以下文档：

* [文件、文件夹和库](/windows/uwp/files/index)
* [存储和检索设置以及其他应用数据](/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>已知文件夹

有关 UWP 应用的完整详细信息，请参阅 [knownfolders.h](/uwp/api/Windows.Storage.KnownFolders) 。

<table>
<tr>
<th> properties</th><th> 在 HoloLens 上受支持</th><th> 沉浸式耳机支持</th><th> 说明</th>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取应用捕获文件夹。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取照相机滚动文件夹。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取文档库。 文档库不用于常规用途。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取音乐库。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取对象的三维文件夹。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取图片库。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">播放列表</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取播放列表文件夹。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取已保存的图片文件夹。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>获取视频库。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">家庭组</a></td><td></td><td style="text-align: center;">✔️</td><td>获取家庭组文件夹。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>获取媒体服务器的文件夹， (数字生活网络联盟 (DLNA) # A3 设备。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>获取记录的调用文件夹。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>获取 "可移动设备" 文件夹。</td>
</tr>
</table>

## <a name="app-package"></a>应用包

对于 Windows 10，您不再以操作系统为目标，而是将您的 [应用程序定位到一个或多个设备系列](/windows/uwp/get-started/universal-application-platform-guide#device-families)。 设备系列可标识在其中的设备上所需的 API、系统特性和行为。 它还决定了可通过 [Microsoft Store](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)安装应用的设备集。

* 若要以台式机耳机和 HoloLens 为目标，请将应用定位到 **Windows。通用** 设备系列。
* 若要仅面向台式机耳机，请将应用定向到 **Windows desktop** 设备系列。
* 若要仅面向 HoloLens，请将应用定位到 **Windows 全息** 设备系列。

## <a name="see-also"></a>另请参阅

* [应用视图](app-views.md)
* [更新混合现实的 2D UWP 应用](../develop/porting-apps/building-2d-apps.md)
* [3D 应用启动器设计指南](../distribute/3d-app-launcher-design-guidance.md)
* [实现 3D 应用启动器](../distribute/implementing-3d-app-launchers.md)