---
title: Unity 中的 HP 回音 G2 控制器
description: 有关在 SteamVR 和 Windows Mixed Reality 中使用 HP 回音 G2 控制器的说明。
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity，回音，回音 G2，HP 回音 G2，mixed reality，开发，运动控制器，用户输入，功能，新项目，模拟器，文档，指南，功能，全息影像，游戏开发
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638384"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Unity 中的 HP 回音 G2 控制器

## <a name="getting-started"></a>入门

如果要针对 SteamVR 进行开发或使用 Windows Mixed Reality 输入 API (XR，则无需进行其他设置即可使用 HP 回音 G2 控制器。WSA.输入) 。 但是，当前无法通过输入管理器访问 A、B、X、Y 按钮和挤压触发器，除非使用的是 SteamVR。 在不久的将来会提供对额外回音 G2 输入的支持，因此请务必查看！

## <a name="porting-existing-applications"></a>移植现有应用程序

如果你已经有一个现有应用程序是为 Windows Mixed Reality 沉浸式耳机开发的，请查看我们的 [移植指南](../porting-apps/porting-guides.md) 和 [项目设置](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) 部分，以获取一般建议。

## <a name="mapping-input"></a>映射输入

准备好为新控制器启用输入映射后，请从沉浸式迁移指南的 [输入映射](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) 部分开始。 [笔势和运动控制器](gestures-and-motion-controllers-in-unity.md)中详细说明了如何配置 Unity 中的输入，以及用于引用的完整[按钮和轴映射表](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers)。

## <a name="see-also"></a>另请参阅
* [SteamVR 更新](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)