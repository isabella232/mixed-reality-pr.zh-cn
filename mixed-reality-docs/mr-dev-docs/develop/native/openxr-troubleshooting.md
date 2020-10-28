---
title: OpenXR 故障排除
description: 解决 OpenXR 应用程序中的问题。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件，故障排除
ms.openlocfilehash: 174c115b86e62d5c52051a7363a59e383e503a95
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903092"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="dc4e1-104">OpenXR 故障排除</span><span class="sxs-lookup"><span data-stu-id="dc4e1-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="dc4e1-105">下面是使用 Windows Mixed Reality OpenXR 运行时开发 OpenXR 应用时的一些故障排除提示。</span><span class="sxs-lookup"><span data-stu-id="dc4e1-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="dc4e1-106">如果你有关于 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>的任何其他问题，请访问 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 论坛</a> 或 <a href="https://khr.io/slack" target="_blank">时差 #openxr 频道</a>。</span><span class="sxs-lookup"><span data-stu-id="dc4e1-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="dc4e1-107">当前 Windows Mixed Reality OpenXR 运行时中有一些已知问题。</span><span class="sxs-lookup"><span data-stu-id="dc4e1-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="dc4e1-108">此时，你应该为 x64 生成桌面 OpenXR 应用。</span><span class="sxs-lookup"><span data-stu-id="dc4e1-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="dc4e1-109">OpenXR 应用未启动 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="dc4e1-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="dc4e1-110">如果 OpenXR 应用在运行时未启动 Windows Mixed Reality，则 Windows Mixed Reality OpenXR 运行时可能不会设置为活动运行时。</span><span class="sxs-lookup"><span data-stu-id="dc4e1-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="dc4e1-111">请务必按照 [OpenXR For Windows Mixed Reality 耳机](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 入门中的说明操作，使运行时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="dc4e1-111">Be sure to follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="dc4e1-112">还可以运行 [Windows Mixed reality 的 OpenXR 开发人员工具](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) ，以便在系统上绕过 Windows Mixed Reality OpenXR 运行时的状态的其他故障排除帮助。</span><span class="sxs-lookup"><span data-stu-id="dc4e1-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>