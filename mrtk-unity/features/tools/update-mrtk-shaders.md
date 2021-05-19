---
title: 着色器更新工具
description: 有关如何更新 MRTK 标准着色器的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: ed9f9fa5e6337850f31ecce9d07bc82a8ea12060
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145136"
---
# <a name="updating-shaders"></a>正在更新着色器

从版本2.6.0 开始，MRTK 着色器通过 MRTK 进行版本控制。着色器 sentinel 文件。 升级到新版本的 MRTK 时，可能会出现以下消息。

![更新着色器提示](../images/tools/UpdateShaderPrompt.png)

选择 **"是"** 将指示 MRTK   >    >  用最新版本覆盖资产 MRTK **着色** 器的内容。 选择 " **否** " 将保留当前文件。 "**忽略** `IgnoreUpdateCheck.sentinel` " 将在 **资产** MRTK 着色器中创建一个文件 ()  >    >  ，这将取消将来的着色器更新检查。

> [!IMPORTANT]
> 当覆盖着色器文件时，任何自定义修改都将丢失。 请确保在升级之前备份任何已修改的着色器文件。
>
> 如果已将项目配置为使用 (URP) 的通用呈现管道 (LWRP) ，请重新运行 **混合现实工具包** > **实用工具** >
>  **升级 MRTK 标准着色器来实现轻型呈现管道**。

还可以使用 **混合现实工具包**  >  **实用工具** 在  >  Unity 编辑器的菜单栏上 **检查着色器更新**，同时检查着色器更新。

![检查着色器更新](../images/tools/ShaderUpdateMenu.png)

**检查着色器更新是否** 忽略 `IgnoreUpdateCheck.sentinel` 文件并允许按需着色器更新。

> [!NOTE]
> 导入 MRTK unitypackage 文件时，不需要检查着色器更新。
