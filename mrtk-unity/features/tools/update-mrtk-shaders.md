---
title: 着色器更新工具
description: 有关如何更新 MRTK 标准着色器的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 1f943d8ac7050b8607ae3a85af0a377a7460eb3b
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647103"
---
# <a name="updating-shaders"></a>更新着色器

从版本 2.6.0 开始，MRTK 着色器通过 MRTK 进行版本控制。Shaders.sentinel 文件。 升级到新版本的 MRTK 时，可能会出现以下消息。

![更新着色器提示](../images/tools/UpdateShaderPrompt.png)

选择 **"** 是"会指示 MRTK 使用最新版本覆盖 **资产**  >  **MRTK**  >  着色器的内容。 选择 **"否** "将保留当前文件。 **忽略** 将在资产 MRTK 着色 () 创建文件，这将 `IgnoreUpdateCheck.sentinel`   >    >  禁止将来的着色器更新检查。

> [!IMPORTANT]
> 覆盖着色器文件时，任何自定义修改都将丢失。 在升级之前，请务必备份任何已修改的着色器文件。
>
> 如果项目已配置为使用通用呈现管道 (URP) - 以前是轻型呈现管道 (LWRP) ，请重新运行混合现实工具包实用工具升级轻型呈现管道 >  >  >
>  **的 MRTK** 标准着色器。

还可以在 Unity 编辑器的菜单栏上随时使用混合现实工具包实用工具检查着色器更新检查着色器  >    >    >  更新。

![检查着色器更新](../images/tools/ShaderUpdateMenu.png)

**检查着色器更新** 是否忽略 `IgnoreUpdateCheck.sentinel` 文件并允许按需着色器更新。

> [!NOTE]
> 导入 MRTK .unitypackage 文件时，无需检查着色器更新。
