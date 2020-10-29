---
title: 用于 HoloLens 的适用于 Unity 的 WinRT Api
description: 说明如何在适用于你的 Unity 项目中的 Windows 命名空间)  (使用 WinRT Api。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，WinRT，windows mixed reality，API，演练
ms.openlocfilehash: 80f950d7571a936e93eb08490ad83dbb34a50b3a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677944"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="8e205-104">用于 HoloLens 的适用于 Unity 的 WinRT Api</span><span class="sxs-lookup"><span data-stu-id="8e205-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="8e205-105">本页介绍如何在适用于 HoloLens 的 Unity 项目中使用 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="8e205-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="8e205-106">混合现实 Api</span><span class="sxs-lookup"><span data-stu-id="8e205-106">Mixed Reality APIs</span></span>

<span data-ttu-id="8e205-107">已在 .NET Standard 2.0 兼容的投影中提供 Windows SDK 的混合现实重点，你可以在不带预处理器指令的项目中使用。</span><span class="sxs-lookup"><span data-stu-id="8e205-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="8e205-108">这包括 Windows 中的大多数 Api 和 Windows UI 命名空间，并且可能会在将来扩展以包含其他 Api。</span><span class="sxs-lookup"><span data-stu-id="8e205-108">This includes most APIs in the Windows.Perception and Windows.UI.Input.Spatial namespaces, and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="8e205-109">在编辑器中运行时，可以使用投影的 Api，这允许使用 [播放模式](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)。</span><span class="sxs-lookup"><span data-stu-id="8e205-109">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="8e205-110">若要使用此投影，请对项目进行以下修改：</span><span class="sxs-lookup"><span data-stu-id="8e205-110">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="8e205-111">使用[NuGet For Unity](https://github.com/GlitchEnzo/NuGetForUnity)添加对[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) nuget 包的引用。</span><span class="sxs-lookup"><span data-stu-id="8e205-111">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="8e205-112">命名空间的前缀引用 `Windows` 包含 `Microsoft.` ：</span><span class="sxs-lookup"><span data-stu-id="8e205-112">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="8e205-113">将本机指针转换替换为 `FromNativePtr` ：</span><span class="sxs-lookup"><span data-stu-id="8e205-113">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="8e205-114">有条件地包含 WinRT API 调用</span><span class="sxs-lookup"><span data-stu-id="8e205-114">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="8e205-115">或者，通过使用预处理器指令，可将 WinRT Api 用于通用 Windows 平台和 Xbox One 平台构建的 Unity 项目;在 Unity 脚本中编写的面向 WinRT Api 的任何代码必须仅有条件地包含在这些内部版本中。</span><span class="sxs-lookup"><span data-stu-id="8e205-115">Alternatively, WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="8e205-116">这可以通过 Unity 中的两个步骤完成：</span><span class="sxs-lookup"><span data-stu-id="8e205-116">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="8e205-117">API 兼容级别必须设置为 " **.net 4.6** " 或 "播放机设置" 中 **.NET Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="8e205-117">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="8e205-118">**编辑**  > **项目设置**  > **播放器**  > **配置**  > **Api 兼容级别** 到 **.net 4.6** 或 **.NET Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="8e205-118">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="8e205-119">必须围绕任何 WinRT 利用代码包装预处理器指令 **ENABLE_WINMD_SUPPORT**</span><span class="sxs-lookup"><span data-stu-id="8e205-119">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="8e205-120">以下代码片段来自 Unity 手动页，适用于 [c # 脚本中通用 Windows 平台： WINRT API](https://docs.unity3d.com/Manual/windowsstore-scripts.html)。</span><span class="sxs-lookup"><span data-stu-id="8e205-120">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="8e205-121">在此示例中，将返回一个广告 ID，但只能在 UWP 和 Xbox one build 上生成：</span><span class="sxs-lookup"><span data-stu-id="8e205-121">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="8e205-122">在 Unity c # 项目中编辑脚本</span><span class="sxs-lookup"><span data-stu-id="8e205-122">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="8e205-123">双击 Unity 编辑器中的脚本时，默认情况下，该脚本将在编辑器项目中启动。</span><span class="sxs-lookup"><span data-stu-id="8e205-123">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="8e205-124">WinRT Api 将显示为 "未知"，因为 Visual Studio 项目未引用 Windows 运行时。</span><span class="sxs-lookup"><span data-stu-id="8e205-124">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="8e205-125">此外， **ENABLE_WINMD_SUPPORT** 指令将是未定义的，并且在你将项目生成到 UWP Visual Studio 解决方案之前，将忽略任何 *#if* 包装的代码。</span><span class="sxs-lookup"><span data-stu-id="8e205-125">Further, the **ENABLE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e205-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e205-126">See also</span></span>
* [<span data-ttu-id="8e205-127">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="8e205-127">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="8e205-128">Windows 运行时支持 Unity</span><span class="sxs-lookup"><span data-stu-id="8e205-128">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
