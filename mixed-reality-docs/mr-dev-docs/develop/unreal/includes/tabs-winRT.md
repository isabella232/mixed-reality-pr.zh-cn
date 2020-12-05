---
ms.openlocfilehash: be267da576e020e88f08d475395b144d42285383
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609399"
---
# <a name="425"></a>[4.25](#tab/425)

Unreal 不在版本4.25 中对 WinRT 代码进行本机编译，因此，你可以创建一个可供 Unreal 的生成系统使用的单独的二进制文件。 

## <a name="objectives"></a>目标

- 创建用于打开 FileSaveDialogue 的通用 Windows DLL
- 将该 DLL 链接到 Unreal 游戏项目
- 使用新 DLL 从 Unreal 蓝图将文件保存在 HoloLens 上

## <a name="getting-started"></a>入门

1. 检查是否已安装所有[必需的工具](../tutorials/unreal-uxt-ch1.md)
2. [创建新的 Unreal 项目](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) 并将其命名为 **Consumewinrt**
3. 为 HoloLens 开发启用[所需插件](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins)
4. 部署到设备或仿真程序[的设置](../tutorials/unreal-uxt-ch6.md)

## <a name="creating-a-winrt-dll"></a>创建 WinRT DLL 

1. 打开新的 Visual Studio 项目，并在 Unreal 游戏的 **uproject** 文件所在的目录中创建一个 **DLL (通用 Windows)** 项目。 

![创建 DLL](../images/unreal-winrt-img-01.png)

2. 将该项目命名为 **HoloLensWinrtDLL** ，并将该位置设置为 Unreal 游戏 uproject 文件的 **ThirdParty** 子目录。 
    * 选择 **"将解决方案和项目放置在相同的目录中"** ，以简化以后查找路径的情况。 

![配置 DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> 新项目编译完成后，请特别注意名称为 **HoloLensWinrtDLL** 和 **HoloLensWinrtDLL** 的空白 cpp 和头文件。 标头是在 Unreal 中使用 DLL 的包含文件，而 cpp 包含所导出的任何函数的主体，并且包含 Unreal 不能编译的任何 WinRT 代码。 

3. 添加任何代码之前，需要更新项目属性，以确保所需的 WinRT 代码可以编译： 
    * 右键单击 "HoloLensWinrtDLL" 项目，然后选择 "**属性**"  
    * 将 " **配置** " 下拉列表中的 " **所有配置** " 和 " **平台** " 下拉列表更改为 **所有平台**  
    * 在 " **配置属性" 下> C/c + +> 所有选项**：
        * 将 **await** 添加到 **其他选项** ，以确保我们可以等待异步任务  
        * 将 **c + + 语言标准** 更改为 **ISO c + + 17 standard (/std： c + + 17)** 以包括任何 WinRT 代码

![升级项目属性](../images/unreal-winrt-img-03.png)

你的项目已准备好使用 WinRT 代码更新 DLL 的源，该代码打开文件对话框，并将文件保存到 HoloLens 磁盘。  

## <a name="adding-the-dll-code"></a>添加 DLL 代码

1. 打开 **HoloLensWinrtDLL** ，并添加要使用的 Unreal 的 dll 导出函数： 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. 打开 **HoloLensWinrtDLL** 并添加类将使用的所有标头：  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> 所有 WinRT 代码都存储在 **HoloLensWinrtDLL** 中，因此 Unreal 不会在引用标头时尝试包含任何 WinRT 代码。 

3. 仍在 **HoloLensWinrtDLL** 中，为 OpenFileDialogue ( # A1 和所有支持的代码添加函数体： 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. 将 SaveGameManager 类添加到 **HoloLensWinrtDLL** 以处理文件对话框并保存文件： 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. 生成用于 **Release > ARM64** 的解决方案，以便将 DLL 从 dll 解决方案生成到子目录 ARM64/Release/HoloLensWinrtDLL。 

## <a name="adding-the-winrt-binary-to-unreal"></a>向 Unreal 添加 WinRT 二进制文件 
在 Unreal 中链接和使用 DLL 需要一个 c + + 项目。 如果使用的是蓝图项目，可以通过添加 c + + 类轻松地将其转换为 c + + 项目：  

1. 在 Unreal 编辑器中，打开 " **> 新建 c + + 类的文件 ...** " 并在 DLL 中 **创建名为** **WinrtActor** 的新执行组件： 

![创建新的执行组件](../images/unreal-winrt-img-04.png)

> [!NOTE]
> 现在，已在与 uproject 文件相同的目录中创建了一个解决方案，同时还创建了一个名为 Source/ConsumeWinRT/ConsumeWinRT 的新生成脚本。

2. 打开解决方案，浏览到 **游戏/ConsumeWinRT/源/ConsumeWinRT** 文件夹，然后打开 **ConsumeWinRT.build.cs**：

![打开 ConsumeWinRT.build.cs 文件](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>链接 DLL
1. 在 **ConsumeWinRT.build.cs** 中，添加一个属性来查找 DLL (包含 HoloLensWinrtDLL) 的目录的包含路径。 DLL 位于包含路径的子目录中，因此此属性将用作二进制根目录：

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. 在类构造函数中，添加以下代码以更新包含路径、链接新的 lib 并延迟加载，并将 DLL 复制到打包的 appx 位置：

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. 打开 **WinrtActor** 并添加一个由蓝图调用的函数定义： 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. 打开 **WinrtActor** 并更新 BeginPlay 以加载 DLL： 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> 必须先加载 DLL，然后才能调用它的任何函数。

### <a name="building-the-game"></a>构建游戏
1. 构建游戏解决方案，启动为游戏项目打开的 Unreal 编辑器： 
    * 在 " **设置参与者** " 选项卡中，搜索新 **WinrtActor** 并将其拖动到场景中 
    * 打开级别蓝图，以在 **WinrtActor** 中执行蓝图可调用函数 

![将 WinrtActor 放在场景中](../images/unreal-winrt-img-06.png)

2. 在 **World Outliner** 中，找到以前拖放到场景中的 **WindrtActor** ，并将其拖动到级别蓝图： 

![将 WinrtActor 拖动到级别蓝图](../images/unreal-winrt-img-07.png)

3. 在级别蓝图中，从 WinrtActor 中拖动输出节点，搜索 " **打开文件" 对话框**，然后从任何用户输入路由节点。  在这种情况下，从语音事件调用 "打开文件" 对话框： 

![在级别蓝图中配置节点](../images/unreal-winrt-img-08.png)

4. [为 HoloLens 打包这一游戏](../tutorials/unreal-uxt-ch6.md)，部署它，然后运行。  

当 Unreal 调用 OpenFileDialogue 时，将在 HoloLens 提示符下打开一个文件对话框，提示输入 .txt 文件名。  保存该文件后，请在设备门户中转到 " **文件资源管理器** " 选项卡，查看内容 "Hello WinRT"。 

## <a name="summary"></a>总结 

如果需要使用 Windows 的相同文件对话框将文件保存到 HoloLens 磁盘，则建议使用本教程作为在 Unreal 中使用 WinRT 代码的起点。  同一过程适用于从 HoloLensWinrtDLL 标头导出其他函数并在 Unreal 中使用。  请特别注意在后台 MTA 线程中等待异步 WinRT 代码的 DLL 代码，这可避免死锁 Unreal 游戏线程。 

# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>标准 WinRT Api

使用 WinRT 最常见和最简单的方法是从 WinSDK 调用方法。 为此，请打开 YourModule.Build.cs 文件并添加以下行：

```cpp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

接下来，需要添加以下 WinRT 标头： 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

WinRT 代码只能在 Win64 和 HoloLens 平台中进行编译，因此，if 语句阻止在其他平台上包含 WinRT 库。 添加了 unknwn 以实现 IUnknown 接口。 

编写任何代码之前，需要使用以下内容禁用 WinRT 标头中的常见警告：

```cpp
#pragma warning(disable : 5205 4265)
```

## <a name="winrt-from-a-nuget-package"></a>从 NuGet 包 WinRT

如果需要使用 WinRT 支持添加 NuGet 包，则会稍微复杂一些。 在这种情况下，Visual Studio 可以为您执行几乎所有的工作，但 Unreal 的生成系统不能。 幸运的是，这并不是很困难。 下面是有关如何下载 MixedReality 包的一个示例。 你可以将其替换为另一个，只需确保你不会丢失 winmd 文件并复制正确的 dll。 

之前部分中 Windows SDK dll 由 OS 处理。 NuGet 的 dll 必须由模块中的代码进行管理。 建议添加代码以下载这些代码、将其复制到二进制文件夹，以及在模块启动时加载到进程内存。

第一步，应将 packages.config (添加 https://docs.microsoft.com/nuget/reference/packages-config) 到模块的根文件夹中。 应添加要下载的所有包，包括所有包的依赖项。 此处我添加了 MixedReality 作为主负载，另外两个作为依赖项。 该文件的格式与 Visual Studio 中的格式相同：

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

现在，你可以下载 NuGet、所需的包，或者参阅 NuGet [文档](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)。

打开 YourModule.Build.cs 并添加以下代码：

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

            PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
                                myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);

    }
    else
    {
        // fall to default WinSDK headers
                        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
            }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }
```

需要定义 SafeCopy 方法，如下所示：

```cpp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

NuGet Dll 需要手动加载到 Win32 进程内存中;建议将手动加载添加到模块的 startup 方法中：

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

最后，可以将 WinRT 标头包含在代码中，如前一部分中所述。