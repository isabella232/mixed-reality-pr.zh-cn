---
title: 用于 HoloLens 的适用于 Unity 的 WinRT Api
description: Leanr 如何在适用于 HoloLens 的 Unity 混合现实项目中使用 WinRT Api 和 Windows 命名空间。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，WinRT，windows mixed reality，API，演练，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，混合现实 Api
ms.openlocfilehash: 2c57af72a10867b5ef4fc87ff96679e576d203f4
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007317"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="b477c-104">用于 HoloLens 的适用于 Unity 的 WinRT Api</span><span class="sxs-lookup"><span data-stu-id="b477c-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="b477c-105">本页介绍如何在适用于 HoloLens 的 Unity 项目中使用 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="b477c-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="b477c-106">混合现实 Api</span><span class="sxs-lookup"><span data-stu-id="b477c-106">Mixed Reality APIs</span></span>

<span data-ttu-id="b477c-107">已在 .NET Standard 2.0 兼容的投影中提供 Windows SDK 的混合现实重点，你可以在不带预处理器指令的项目中使用。</span><span class="sxs-lookup"><span data-stu-id="b477c-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="b477c-108">Windows 中的大多数 Api。</span><span class="sxs-lookup"><span data-stu-id="b477c-108">Most APIs in the Windows.</span></span> <span data-ttu-id="b477c-109">感知和 Windows UI. Input 命名空间包括在内，并且可能会在将来扩展以包含其他 Api。</span><span class="sxs-lookup"><span data-stu-id="b477c-109">Perception and Windows.UI.Input.Spatial namespaces are included and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="b477c-110">在编辑器中运行时，可以使用投影的 Api，这允许使用 [播放模式](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)。</span><span class="sxs-lookup"><span data-stu-id="b477c-110">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="b477c-111">若要使用此投影，请对项目进行以下修改：</span><span class="sxs-lookup"><span data-stu-id="b477c-111">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="b477c-112">使用[NuGet For Unity](https://github.com/GlitchEnzo/NuGetForUnity)添加对[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) nuget 包的引用。</span><span class="sxs-lookup"><span data-stu-id="b477c-112">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="b477c-113">命名空间的前缀引用 `Windows` 包含 `Microsoft.` ：</span><span class="sxs-lookup"><span data-stu-id="b477c-113">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="b477c-114">将本机指针转换替换为 `FromNativePtr` ：</span><span class="sxs-lookup"><span data-stu-id="b477c-114">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="b477c-115">有条件地包含 WinRT API 调用</span><span class="sxs-lookup"><span data-stu-id="b477c-115">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="b477c-116">还可以通过使用预处理器指令，在为通用 Windows 平台和 Xbox one 平台构建的 Unity 项目中使用 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="b477c-116">You can also use the WinRT APIs in Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives.</span></span> <span data-ttu-id="b477c-117">在 Unity 脚本中编写的面向 WinRT Api 的任何代码必须仅有条件地包含在这些内部版本中。</span><span class="sxs-lookup"><span data-stu-id="b477c-117">Any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="b477c-118">这可以通过 Unity 中的两个步骤完成：</span><span class="sxs-lookup"><span data-stu-id="b477c-118">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="b477c-119">API 兼容级别必须设置为 " **.net 4.6** " 或 "播放机设置" 中 **.NET Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="b477c-119">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="b477c-120">**编辑**  > **项目设置**  > **播放器**  > **配置**  > **Api 兼容级别** 到 **.net 4.6** 或 **.NET Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="b477c-120">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="b477c-121">必须围绕任何 WinRT 利用代码包装预处理器指令 **ENABLE_WINMD_SUPPORT**</span><span class="sxs-lookup"><span data-stu-id="b477c-121">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="b477c-122">以下代码片段来自 Unity 手动页，适用于 [c # 脚本中通用 Windows 平台： WINRT API](https://docs.unity3d.com/Manual/windowsstore-scripts.html)。</span><span class="sxs-lookup"><span data-stu-id="b477c-122">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="b477c-123">在此示例中，将返回一个广告 ID，但只能在 UWP 和 Xbox one build 上生成：</span><span class="sxs-lookup"><span data-stu-id="b477c-123">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="b477c-124">在 Unity c # 项目中编辑脚本</span><span class="sxs-lookup"><span data-stu-id="b477c-124">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="b477c-125">双击 Unity 编辑器中的脚本时，默认情况下，该脚本将在编辑器项目中启动。</span><span class="sxs-lookup"><span data-stu-id="b477c-125">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="b477c-126">WinRT Api 将显示为 "未知"，因为 Visual Studio 项目不引用 Windows 运行时。</span><span class="sxs-lookup"><span data-stu-id="b477c-126">The WinRT APIs will appear to be unknown because the Visual Studio project doesn't reference the Windows Runtime.</span></span> <span data-ttu-id="b477c-127">在将项目生成到 UWP Visual Studio 解决方案之前，将忽略 **ENABLE_WINMD_SUPPORT** 指令，并忽略任何 *#if* 包装的代码。</span><span class="sxs-lookup"><span data-stu-id="b477c-127">The **ENABLE_WINMD_SUPPORT** directive is undefined and any *#if* wrapped code is ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="b477c-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b477c-128">See also</span></span>
* [<span data-ttu-id="b477c-129">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="b477c-129">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="b477c-130">Windows 运行时支持 Unity</span><span class="sxs-lookup"><span data-stu-id="b477c-130">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
