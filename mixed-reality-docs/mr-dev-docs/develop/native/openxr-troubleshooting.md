---
title: OpenXR 故障排除
description: 解决 OpenXR 应用程序中的问题。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件，故障排除
ms.openlocfilehash: ddfe548d689d84576ad0ac06bda46d7c2757859c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612931"
---
# <a name="openxr-troubleshooting"></a>OpenXR 故障排除

下面是使用 Windows Mixed Reality OpenXR 运行时开发 OpenXR 应用时的一些故障排除提示。  如果你有关于 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>的任何其他问题，请访问 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 论坛</a> 或 <a href="https://khr.io/slack" target="_blank">时差 #openxr 频道</a>。

>[!NOTE]
>当前 Windows Mixed Reality OpenXR 运行时中有一些已知问题。  此时，你应该为 x64 生成桌面 OpenXR 应用。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 应用未启动 Windows Mixed Reality

如果 OpenXR 应用在运行时未启动 Windows Mixed Reality，则 Windows Mixed Reality OpenXR 运行时可能不会设置为活动运行时。 请按照 [OpenXR For Windows Mixed Reality 耳机](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 入门中的说明解决此问题。

你还可以运行 [Windows Mixed reality 的 OpenXR 开发人员工具](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) ，以获取有关系统 Windows Mixed Reality OpenXR 运行时状态的故障排除帮助。