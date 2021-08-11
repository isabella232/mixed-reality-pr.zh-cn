---
title: OpenXR 故障排除
description: 查找有关 Windows Mixed Reality OpenXR 应用程序中常见的故障排除问题的资源和解答。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件，故障排除
ms.openlocfilehash: 456dcf927c70aaaebc8dda1338d24acc910a1e801cf29e8880048d44f9432718
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219201"
---
# <a name="openxr-troubleshooting"></a>OpenXR 故障排除

下面是使用 Windows Mixed Reality OpenXR 运行时开发 OpenXR 应用时的一些故障排除提示。  如果你有关于 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>的任何其他问题，请访问 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 论坛</a> 或 <a href="https://khr.io/slack" target="_blank">时差 #openxr 频道</a>。

>[!NOTE]
>对于 x86 应用，当前 Windows Mixed Reality OpenXR 运行时中存在一些已知问题。  此时，你应该为 x64 生成桌面 OpenXR 应用。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 应用未启动 Windows Mixed Reality

如果在运行 OpenXR 应用时没有开始 Windows Mixed Reality，则 Windows Mixed Reality OpenXR 运行时可能不会设置为活动运行时。 按照[Windows Mixed Reality 耳机](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets)入门中的说明解决此问题。

你还可以运行[用于 Windows Mixed Reality 的 OpenXR 开发人员工具](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality)，以获取有关系统 Windows Mixed Reality OpenXR 运行时的状态的故障排除帮助。