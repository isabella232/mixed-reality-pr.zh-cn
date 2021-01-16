---
title: Unreal 中的 WinRT
description: 了解如何在适用于 HoloLens 设备的 Unreal mixed reality 应用中编写和管理自定义 WinRT 功能。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，流式处理，远程处理，混合现实，开发，入门，功能，新项目，模拟器，文档，指南，功能，全息影像，游戏开发，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，WinRT，DLL
ms.openlocfilehash: 0d181d1eff644de0512c40a140474612a1540b40
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2021
ms.locfileid: "98247750"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="ef790-104">Unreal 中的 WinRT</span><span class="sxs-lookup"><span data-stu-id="ef790-104">WinRT in Unreal</span></span>

<span data-ttu-id="ef790-105">在 HoloLens 开发过程中，可能需要使用 WinRT 编写功能。</span><span class="sxs-lookup"><span data-stu-id="ef790-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="ef790-106">例如，在 HoloLens 应用程序中打开文件对话时，需要 winrt/FileSavePicker 头文件中的。</span><span class="sxs-lookup"><span data-stu-id="ef790-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="ef790-107">从版本4.26 开始，Unreal 的生成系统支持 WinRT。</span><span class="sxs-lookup"><span data-stu-id="ef790-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="ef790-108">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="ef790-108">Next Development Checkpoint</span></span>

<span data-ttu-id="ef790-109">如果你遵循我们规划的 Unreal 开发历程，则你处于探索混合现实平台功能和 API 的过程之中。</span><span class="sxs-lookup"><span data-stu-id="ef790-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="ef790-110">在这里，你可以继续阅读任何 [主题](unreal-development-overview.md#3-advanced-features) ，也可以直接跳转到在设备或模拟器上部署你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ef790-110">From here, you can continue to any [topic](unreal-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ef790-111">部署到设备</span><span class="sxs-lookup"><span data-stu-id="ef790-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="ef790-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef790-112">See also</span></span>

* [<span data-ttu-id="ef790-113">C + +/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="ef790-113">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="ef790-114">FileSavePicker 类</span><span class="sxs-lookup"><span data-stu-id="ef790-114">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="ef790-115">Unreal 第三方库</span><span class="sxs-lookup"><span data-stu-id="ef790-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
