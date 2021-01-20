---
ms.openlocfilehash: 7d530b66596bb79a082b98e5417bd125a7c5687d
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580415"
---
# <a name="426"></a>[<span data-ttu-id="4ad0b-101">4.26</span><span class="sxs-lookup"><span data-stu-id="4ad0b-101">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="4ad0b-102">标准 WinRT Api</span><span class="sxs-lookup"><span data-stu-id="4ad0b-102">The standard WinRT APIs</span></span>

<span data-ttu-id="4ad0b-103">使用 WinRT 最常见和最简单的方法是从 WinSDK 调用方法。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-103">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="4ad0b-104">为此，请打开 YourModule.Build.cs 文件并添加以下行：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-104">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```csharp
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

<span data-ttu-id="4ad0b-105">接下来，需要添加以下 WinRT 标头：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-105">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
//Before writing any code, you need to disable common warnings in WinRT headers
#pragma warning(disable : 5205 4265 4268 4946)

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

<span data-ttu-id="4ad0b-106">WinRT 代码只能在 Win64 和 HoloLens 平台中进行编译，因此，if 语句阻止在其他平台上包含 WinRT 库。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-106">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="4ad0b-107">添加了 unknwn 以实现 IUnknown 接口。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-107">unknwn.h was added for having the IUnknown interface.</span></span> 


## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="4ad0b-108">从 NuGet 包 WinRT</span><span class="sxs-lookup"><span data-stu-id="4ad0b-108">WinRT from a NuGet package</span></span>

<span data-ttu-id="4ad0b-109">如果需要使用 WinRT 支持添加 NuGet 包，则会稍微复杂一些。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-109">It’s a little more complicated if you need to add a NuGet package with WinRT support.</span></span> <span data-ttu-id="4ad0b-110">在这种情况下，Visual Studio 可以为您执行几乎所有的工作，但 Unreal 的生成系统不能。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-110">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="4ad0b-111">幸运的是，这并不是很困难。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-111">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="4ad0b-112">下面是有关如何下载 MixedReality 包的一个示例。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-112">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="4ad0b-113">你可以将其替换为另一个，只需确保你不会丢失 winmd 文件并复制正确的 dll。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-113">You can replace it with another, just make sure you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="4ad0b-114">之前部分中 Windows SDK dll 由 OS 处理。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-114">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="4ad0b-115">NuGet 的 dll 必须由模块中的代码进行管理。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-115">NuGet’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="4ad0b-116">建议添加代码以下载这些代码、将其复制到二进制文件夹，以及在模块启动时加载到进程内存。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-116">We recommend adding code to download them, copying into binaries folder, and load into the process memory at the module startup.</span></span>

<span data-ttu-id="4ad0b-117">第一步，应将 packages.config (添加 https://docs.microsoft.com/nuget/reference/packages-config) 到模块的根文件夹中。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-117">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="4ad0b-118">应添加要下载的所有包，包括所有包的依赖项。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-118">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="4ad0b-119">此处我添加了 MixedReality 作为主负载，另外两个作为依赖项。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-119">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="4ad0b-120">该文件的格式与 Visual Studio 中的格式相同：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-120">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="4ad0b-121">现在，你可以下载 NuGet、所需的包，或者参阅 NuGet [文档](/nuget/consume-packages/install-use-packages-nuget-cli)。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-121">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="4ad0b-122">打开 YourModule.Build.cs 并添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-122">Open YourModule.Build.cs and add the following code:</span></span>

```csharp
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
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
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
        // fall back to default WinSDK headers
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
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
        string VCRTForwardersPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
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

<span data-ttu-id="4ad0b-123">需要定义 SafeCopy 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-123">You'll need to define the SafeCopy method as follows:</span></span>

```csharp
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

<span data-ttu-id="4ad0b-124">NuGet Dll 需要手动加载到 Win32 进程内存中;建议将手动加载添加到模块的 startup 方法中：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-124">NuGet DLLs needs to load into your Win32 process memory manually; we recommend adding manual loading into the startup method of your module:</span></span>

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

<span data-ttu-id="4ad0b-125">最后，可以将 WinRT 标头包含在代码中，如前一部分中所述。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-125">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>

# <a name="425"></a>[<span data-ttu-id="4ad0b-126">4.25</span><span class="sxs-lookup"><span data-stu-id="4ad0b-126">4.25</span></span>](#tab/425)

<span data-ttu-id="4ad0b-127">Unreal 不在版本4.25 中对 WinRT 代码进行本机编译，因此，你可以创建一个可供 Unreal 的生成系统使用的单独的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-127">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary that Unreal’s build system can consume.</span></span> 

## <a name="objectives"></a><span data-ttu-id="4ad0b-128">目标</span><span class="sxs-lookup"><span data-stu-id="4ad0b-128">Objectives</span></span>

- <span data-ttu-id="4ad0b-129">创建用于打开 FileSaveDialogue 的通用 Windows DLL</span><span class="sxs-lookup"><span data-stu-id="4ad0b-129">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="4ad0b-130">将该 DLL 链接到 Unreal 游戏项目</span><span class="sxs-lookup"><span data-stu-id="4ad0b-130">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="4ad0b-131">使用新 DLL 从 Unreal 蓝图将文件保存在 HoloLens 上</span><span class="sxs-lookup"><span data-stu-id="4ad0b-131">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="4ad0b-132">入门</span><span class="sxs-lookup"><span data-stu-id="4ad0b-132">Getting started</span></span>

1. <span data-ttu-id="4ad0b-133">检查是否已安装所有[必需的工具](../tutorials/unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="4ad0b-133">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="4ad0b-134">[创建新的 Unreal 项目](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) 并将其命名为 **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="4ad0b-134">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="4ad0b-135">为 HoloLens 开发启用[所需插件](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins)</span><span class="sxs-lookup"><span data-stu-id="4ad0b-135">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="4ad0b-136">部署到设备或仿真程序[的设置](../tutorials/unreal-uxt-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="4ad0b-136">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="4ad0b-137">创建 WinRT DLL</span><span class="sxs-lookup"><span data-stu-id="4ad0b-137">Creating a WinRT DLL</span></span> 

1. <span data-ttu-id="4ad0b-138">打开新的 Visual Studio 项目，并在 Unreal 游戏的 **uproject** 文件所在的目录中创建一个 **DLL (通用 Windows)** 项目。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-138">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory as the Unreal game’s **uproject** file.</span></span> 

![创建 DLL](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="4ad0b-140">将该项目命名为 **HoloLensWinrtDLL** ，并将该位置设置为 Unreal 游戏 uproject 文件的 **ThirdParty** 子目录。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-140">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="4ad0b-141">选择 **"将解决方案和项目放置在相同的目录中"** ，以简化以后查找路径的情况。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-141">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![配置 DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="4ad0b-143">新项目编译完成后，请特别注意名称为 **HoloLensWinrtDLL** 和 **HoloLensWinrtDLL** 的空白 cpp 和头文件。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-143">After the new project compiles, pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="4ad0b-144">标头是在 Unreal 中使用 DLL 的包含文件，而 cpp 包含所导出的任何函数的主体，并且包含 Unreal 不能编译的任何 WinRT 代码。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-144">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="4ad0b-145">添加任何代码之前，需要更新项目属性，以确保所需的 WinRT 代码可以编译：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-145">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="4ad0b-146">右键单击 "HoloLensWinrtDLL" 项目，然后选择 "**属性**"</span><span class="sxs-lookup"><span data-stu-id="4ad0b-146">Right-click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="4ad0b-147">将 " **配置** " 下拉列表中的 " **所有配置** " 和 " **平台** " 下拉列表更改为 **所有平台**</span><span class="sxs-lookup"><span data-stu-id="4ad0b-147">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="4ad0b-148">在 " **配置属性" 下> C/c + +> 所有选项**：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-148">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="4ad0b-149">将 **await** 添加到 **其他选项** ，以确保我们可以等待异步任务</span><span class="sxs-lookup"><span data-stu-id="4ad0b-149">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="4ad0b-150">将 **c + + 语言标准** 更改为 **ISO c + + 17 standard (/std： c + + 17)** 以包括任何 WinRT 代码</span><span class="sxs-lookup"><span data-stu-id="4ad0b-150">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![升级项目属性](../images/unreal-winrt-img-03.png)

<span data-ttu-id="4ad0b-152">你的项目已准备好使用 WinRT 代码更新 DLL 的源，该代码打开文件对话框，并将文件保存到 HoloLens 磁盘。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-152">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="4ad0b-153">添加 DLL 代码</span><span class="sxs-lookup"><span data-stu-id="4ad0b-153">Adding the DLL code</span></span>

1. <span data-ttu-id="4ad0b-154">打开 **HoloLensWinrtDLL** ，并添加要使用的 Unreal 的 dll 导出函数：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-154">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="4ad0b-155">打开 **HoloLensWinrtDLL** 并添加类将使用的所有标头：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-155">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="4ad0b-156">所有 WinRT 代码都存储在 **HoloLensWinrtDLL** 中，因此 Unreal 不会在引用标头时尝试包含任何 WinRT 代码。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-156">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="4ad0b-157">仍在 **HoloLensWinrtDLL** 中，为 OpenFileDialogue ( # A1 和所有支持的代码添加函数体：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-157">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="4ad0b-158">将 SaveGameManager 类添加到 **HoloLensWinrtDLL** 以处理文件对话框并保存文件：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-158">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="4ad0b-159">生成用于 **Release > ARM64** 的解决方案，以便将 DLL 从 dll 解决方案生成到子目录 ARM64/Release/HoloLensWinrtDLL。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-159">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="4ad0b-160">向 Unreal 添加 WinRT 二进制文件</span><span class="sxs-lookup"><span data-stu-id="4ad0b-160">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="4ad0b-161">在 Unreal 中链接和使用 DLL 需要一个 c + + 项目。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-161">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="4ad0b-162">如果使用的是蓝图项目，可以通过添加 c + + 类轻松地将其转换为 c + + 项目：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-162">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="4ad0b-163">在 Unreal 编辑器中，打开 " **> 新建 c + + 类的文件 ...** "</span><span class="sxs-lookup"><span data-stu-id="4ad0b-163">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="4ad0b-164">并在 DLL 中 **创建名为** **WinrtActor** 的新执行组件：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-164">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![创建新的执行组件](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="4ad0b-166">现在，已在与 uproject 文件相同的目录中创建了一个解决方案，同时还创建了一个名为 Source/ConsumeWinRT/ConsumeWinRT 的新生成脚本。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-166">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="4ad0b-167">打开解决方案，浏览到 **游戏/ConsumeWinRT/源/ConsumeWinRT** 文件夹，然后打开 **ConsumeWinRT.build.cs**：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-167">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![打开 ConsumeWinRT.build.cs 文件](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="4ad0b-169">链接 DLL</span><span class="sxs-lookup"><span data-stu-id="4ad0b-169">Linking the DLL</span></span>
1. <span data-ttu-id="4ad0b-170">在 **ConsumeWinRT.build.cs** 中，添加一个属性来查找 DLL (包含 HoloLensWinrtDLL) 的目录的包含路径。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-170">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="4ad0b-171">DLL 位于包含路径的子目录中，因此此属性将用作二进制根目录：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-171">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="4ad0b-172">在类构造函数中，添加以下代码以更新包含路径、链接新的 lib 并延迟加载，并将 DLL 复制到打包的 appx 位置：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-172">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="4ad0b-173">打开 **WinrtActor** 并添加一个由蓝图调用的函数定义：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-173">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="4ad0b-174">打开 **WinrtActor** 并更新 BeginPlay 以加载 DLL：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-174">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="4ad0b-175">必须先加载 DLL，然后才能调用它的任何函数。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-175">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="4ad0b-176">构建游戏</span><span class="sxs-lookup"><span data-stu-id="4ad0b-176">Building the game</span></span>
1. <span data-ttu-id="4ad0b-177">构建游戏解决方案，启动为游戏项目打开的 Unreal 编辑器：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-177">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="4ad0b-178">在 " **设置参与者** " 选项卡中，搜索新 **WinrtActor** 并将其拖动到场景中</span><span class="sxs-lookup"><span data-stu-id="4ad0b-178">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="4ad0b-179">打开级别蓝图，以在 **WinrtActor** 中执行蓝图可调用函数</span><span class="sxs-lookup"><span data-stu-id="4ad0b-179">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![将 WinrtActor 放在场景中](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="4ad0b-181">在 **World Outliner** 中，找到以前拖放到场景中的 **WindrtActor** ，并将其拖动到级别蓝图：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-181">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![将 WinrtActor 拖动到级别蓝图](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="4ad0b-183">在级别蓝图中，从 WinrtActor 中拖动输出节点，搜索 " **打开文件" 对话框**，然后从任何用户输入路由节点。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-183">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="4ad0b-184">在这种情况下，从语音事件调用 "打开文件" 对话框：</span><span class="sxs-lookup"><span data-stu-id="4ad0b-184">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![在级别蓝图中配置节点](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="4ad0b-186">[为 HoloLens 打包这一游戏](../tutorials/unreal-uxt-ch6.md)，部署它，然后运行。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-186">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="4ad0b-187">当 Unreal 调用 OpenFileDialogue 时，将在 HoloLens 提示符下打开一个文件对话框，提示输入 .txt 文件名。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-187">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="4ad0b-188">保存该文件后，请在设备门户中转到 " **文件资源管理器** " 选项卡，查看内容 "Hello WinRT"。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-188">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="4ad0b-189">总结</span><span class="sxs-lookup"><span data-stu-id="4ad0b-189">Summary</span></span> 

<span data-ttu-id="4ad0b-190">如果需要使用 Windows 的相同文件对话框将文件保存到 HoloLens 磁盘，则建议使用本教程作为在 Unreal 中使用 WinRT 代码的起点。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-190">We encourage you to use this tutorial as a starting point for consuming WinRT code in Unreal when you need to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="4ad0b-191">同一过程适用于从 HoloLensWinrtDLL 标头导出其他函数并在 Unreal 中使用。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-191">The same process applies to exporting additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="4ad0b-192">请特别注意在后台 MTA 线程中等待异步 WinRT 代码的 DLL 代码，这可避免死锁 Unreal 游戏线程。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-192">Pay special attention to the DLL code that waits on async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span>