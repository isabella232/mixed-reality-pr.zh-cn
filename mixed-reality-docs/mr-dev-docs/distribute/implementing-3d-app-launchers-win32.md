---
title: 实现 3D 应用启动器（Win32 应用）
description: 了解如何为 "开始" 菜单和 home 环境创建 "Win32 VR 应用和游戏" 的3D 应用启动器和徽标。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D，徽标，图标，建模，启动器，3D 启动器，磁贴，动态立方体，win32，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，清单
ms.openlocfilehash: 63b07664cb09f51e6d0588fdc50d141ad8985093
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009666"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="a17ea-104">实现 3D 应用启动器（Win32 应用）</span><span class="sxs-lookup"><span data-stu-id="a17ea-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="a17ea-105">此功能仅适用于运行最新 [Windows 有问必答](https://insider.windows.com) 航班 (RS5) ，版本17704和更高版本的电脑。</span><span class="sxs-lookup"><span data-stu-id="a17ea-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="a17ea-106">[Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)是用户在启动应用程序之前居住的起点。</span><span class="sxs-lookup"><span data-stu-id="a17ea-106">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="a17ea-107">默认情况下，你需要从耳机外启动沉浸式 Win32 VR 应用和游戏，而不会出现在 Windows Mixed Reality 开始菜单上的 "所有应用" 列表中。</span><span class="sxs-lookup"><span data-stu-id="a17ea-107">By default, you need to launch immersive Win32 VR apps and games from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="a17ea-108">如果按照本文中的说明来实现3D 应用启动器，则可以从 Windows Mixed Reality 开始菜单和 home 环境中启动沉浸式 Win32 VR 体验。</span><span class="sxs-lookup"><span data-stu-id="a17ea-108">If you follow the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="a17ea-109">这仅适用于分散在流之外的沉浸式 Win32 VR 体验。</span><span class="sxs-lookup"><span data-stu-id="a17ea-109">This is only true for immersive Win32 VR experiences distributed outside of Steam.</span></span> <span data-ttu-id="a17ea-110">对于 [通过流发布](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)的 VR 体验，我们已 [更新了适用于 SteamVR Beta 的 windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 以及最新的 windows 有问必答 RS5 航班，以便 SteamVR 标题可使用默认启动器自动显示在 "所有应用" 列表中的 "windows mixed reality 开始" 菜单。</span><span class="sxs-lookup"><span data-stu-id="a17ea-110">For VR experiences [distributed through Steam](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="a17ea-111">换句话说，本文中所述的方法对于 SteamVR 标题是不必要的，将被 Windows Mixed Reality 替换为 SteamVR Beta 功能。</span><span class="sxs-lookup"><span data-stu-id="a17ea-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="a17ea-112">3D 应用程序启动器创建过程</span><span class="sxs-lookup"><span data-stu-id="a17ea-112">3D app launcher creation process</span></span>

<span data-ttu-id="a17ea-113">创建三维应用启动器有三个步骤：</span><span class="sxs-lookup"><span data-stu-id="a17ea-113">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="a17ea-114">设计和 concepting</span><span class="sxs-lookup"><span data-stu-id="a17ea-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="a17ea-115">建模和导出</span><span class="sxs-lookup"><span data-stu-id="a17ea-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="a17ea-116">将其集成到你的应用程序中 (本文) </span><span class="sxs-lookup"><span data-stu-id="a17ea-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="a17ea-117">要用作应用程序启动器的3D 资产应使用 [Windows Mixed Reality 创作指南](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 进行创作，以确保兼容性。</span><span class="sxs-lookup"><span data-stu-id="a17ea-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="a17ea-118">未能满足此创作规范的资产将不会在 Windows Mixed Reality 主页中呈现。</span><span class="sxs-lookup"><span data-stu-id="a17ea-118">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="a17ea-119">配置3D 启动器</span><span class="sxs-lookup"><span data-stu-id="a17ea-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="a17ea-120">如果为 Windows Mixed Reality 开始菜单创建了一个3D 应用启动器，Win32 应用程序将显示在 "所有应用程序" 列表中。</span><span class="sxs-lookup"><span data-stu-id="a17ea-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="a17ea-121">为此，请按照以下步骤创建一个引用3D 应用程序启动器的 [视觉元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML 文件：</span><span class="sxs-lookup"><span data-stu-id="a17ea-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="a17ea-122">创建 **三维应用启动器资产 GLB 文件** (参阅 [建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)) 。</span><span class="sxs-lookup"><span data-stu-id="a17ea-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="a17ea-123">为应用程序创建一个 **[可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 。</span><span class="sxs-lookup"><span data-stu-id="a17ea-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="a17ea-124">您可以从下面的 [示例](#sample-visual-elements-manifest)开始。</span><span class="sxs-lookup"><span data-stu-id="a17ea-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="a17ea-125">有关更多详细信息，请参阅完整的 [可视元素清单](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) 文档。</span><span class="sxs-lookup"><span data-stu-id="a17ea-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="a17ea-126">使用适用于应用的 PNG/JPG/GIF 更新 **Square150x150Logo** 和 **Square70x70Logo** 。</span><span class="sxs-lookup"><span data-stu-id="a17ea-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="a17ea-127">这些项将用于 Windows Mixed Reality 的 "所有应用" 列表中的应用的2D 徽标和桌面上的 "开始" 菜单。</span><span class="sxs-lookup"><span data-stu-id="a17ea-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="a17ea-128">文件路径基于包含视觉元素清单的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a17ea-128">The file path is based on the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="a17ea-129">仍需通过标准机制为应用提供桌面开始菜单图标。</span><span class="sxs-lookup"><span data-stu-id="a17ea-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="a17ea-130">这可以直接在可执行文件中，也可以在创建的快捷方式中。</span><span class="sxs-lookup"><span data-stu-id="a17ea-130">This can either be directly in the executable or in the shortcut you create.</span></span> <span data-ttu-id="a17ea-131">例如，通过 IShellLink：： SetIconLocation。</span><span class="sxs-lookup"><span data-stu-id="a17ea-131">For example, via IShellLink::SetIconLocation.</span></span>
        * <span data-ttu-id="a17ea-132">*可选：* 如果希望使用 MRT.LOG 为不同分辨率缩放和高对比度主题提供多种资产大小，则可以使用资源 pri 文件。</span><span class="sxs-lookup"><span data-stu-id="a17ea-132">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="a17ea-133">更新 **MixedRealityModel 路径** ，使其指向3D 应用程序启动器的 GLB</span><span class="sxs-lookup"><span data-stu-id="a17ea-133">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="a17ea-134">使用与可执行文件相同的名称保存文件，扩展名为 ".VisualElementsManifest.xml"，并将其保存在同一目录中。</span><span class="sxs-lookup"><span data-stu-id="a17ea-134">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="a17ea-135">例如，对于可执行文件 "contoso.exe"，附带的 XML 文件名为 "contoso.visualelementsmanifest.xml"。</span><span class="sxs-lookup"><span data-stu-id="a17ea-135">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="a17ea-136">将应用程序的 **快捷方式添加** 到桌面 Windows "开始" 菜单。</span><span class="sxs-lookup"><span data-stu-id="a17ea-136">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="a17ea-137">有关 c + + 实现的示例，请参阅 [下面的示例](#sample-app-launcher-shortcut-creation) 。</span><span class="sxs-lookup"><span data-stu-id="a17ea-137">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="a17ea-138">在%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) 或%APPDATA%\Microsoft\Windows\Start Menu\Programs (用户中创建它) </span><span class="sxs-lookup"><span data-stu-id="a17ea-138">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="a17ea-139">如果更新更改了你的可视元素清单或它所引用的资产，则更新程序或安装程序应更新该快捷方式，以使清单被重新分析并更新缓存资产。</span><span class="sxs-lookup"><span data-stu-id="a17ea-139">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="a17ea-140">*可选：* 如果桌面快捷方式不会直接指向应用程序的 EXE (例如，如果它调用自定义协议处理程序，如 "myapp://" ) ，则 "开始" 菜单将不会自动查找应用的 VisualElementsManifest.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="a17ea-140">*Optional:* If your desktop shortcut doesn't point directly to your application’s EXE (for example, if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="a17ea-141">若要解决此问题，快捷方式应使用 AppUserModel. VisualElementsManifestHintPath ( # A1 指定视觉元素清单的文件路径。</span><span class="sxs-lookup"><span data-stu-id="a17ea-141">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="a17ea-142">这可以使用与 System.AppUserModel.ID 相同的技术在快捷方式中进行设置。</span><span class="sxs-lookup"><span data-stu-id="a17ea-142">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="a17ea-143">不需要使用 System.AppUserModel.ID，但如果想要将快捷方式与应用程序的显式应用程序用户模型 ID 相匹配（如果使用），则可以执行此操作。</span><span class="sxs-lookup"><span data-stu-id="a17ea-143">You aren't required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="a17ea-144">有关 c + + 示例，请参阅下面的 [示例应用程序启动器快捷方式创建](#sample-app-launcher-shortcut-creation) 部分。</span><span class="sxs-lookup"><span data-stu-id="a17ea-144">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="a17ea-145">示例视觉元素清单</span><span class="sxs-lookup"><span data-stu-id="a17ea-145">Sample Visual Elements Manifest</span></span>

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="a17ea-146">示例应用启动器快捷方式创建</span><span class="sxs-lookup"><span data-stu-id="a17ea-146">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="a17ea-147">下面的示例代码演示如何在 c + + 中创建快捷方式，包括重写可视元素清单 XML 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="a17ea-147">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="a17ea-148">请注意，仅当快捷方式不直接指向与清单关联的 EXE 时才需要替代 (例如，快捷方式使用自定义协议处理程序，如 "myapp://" ) 。</span><span class="sxs-lookup"><span data-stu-id="a17ea-148">Note the override is only required in cases where your shortcut doesn't point directly to the EXE associated with the manifest (for example, your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="a17ea-149">范例. (c + +) 的 .LNK 快捷方式创建</span><span class="sxs-lookup"><span data-stu-id="a17ea-149">Sample .LNK shortcut creation (C++)</span></span>

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="a17ea-150">范例.URL 启动器快捷方式</span><span class="sxs-lookup"><span data-stu-id="a17ea-150">Sample .URL launcher shortcut</span></span> 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a><span data-ttu-id="a17ea-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a17ea-151">See also</span></span>

* <span data-ttu-id="a17ea-152">包含三维应用程序启动器的[混合现实模型示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。</span><span class="sxs-lookup"><span data-stu-id="a17ea-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="a17ea-153">3D 应用启动器设计指南</span><span class="sxs-lookup"><span data-stu-id="a17ea-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="a17ea-154">创建用于 Windows Mixed Reality 主页的3D 模型</span><span class="sxs-lookup"><span data-stu-id="a17ea-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="a17ea-155"> (UWP 应用实现3D 应用启动器) </span><span class="sxs-lookup"><span data-stu-id="a17ea-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="a17ea-156">导航 Windows Mixed Reality 主页</span><span class="sxs-lookup"><span data-stu-id="a17ea-156">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
