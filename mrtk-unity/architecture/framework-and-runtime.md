---
title: 框架和运行时
description: 与 MRTK 中的框架和运行时有关的信息。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f2391ab0c67880c8902092be6fcecefcf30f008c7f31ea76879d399e35e1491b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212668"
---
# <a name="framework-and-runtime"></a>框架和运行时

## <a name="changes-to-the-scene"></a>对场景的更改

若要使用工具包，MixedRealityToolkit 脚本的实例必须在你的场景中。
若要添加一个，请使用菜单选项：混合现实Toolkit ->添加到场景和配置。 此实例负责注册、更新和拆收服务。 这也是选择配置文件的地方。

除了将 MRTK GameObject 添加到场景中外，菜单选项还将：

- 添加 MixedRealityPlayspace，许多其他 MRTK 组件都使用该空间进行全球和本地空间转换。
- 将主相机作为 MixedRealityPlayspace (的子级移动，还将一些与输入和凝视相关的脚本添加到主相机，这有助于为 UnityUI 和凝视相关的输入功能) 。

## <a name="mixedrealitytoolkit-object-and-runtime"></a>MixedRealityToolkit 对象和运行时

MRTK 具有多个核心服务。 相互协调;其他是独立的。
全部共享相同的生命周期（启动、注册、更新和拆解）并且此生命周期与 Unity 的 MonoBehaviour 生命周期不同。 此 [中等帖子](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) 解释了此方法背后的一些背景和动机。 MRTK 有一个对象，用于管理其服务生命周期和运行时。

此实体可确保：

- 游戏开始时，服务的发现和初始化按预定义的顺序进行。
- 它提供了一种机制，使服务能够自行注册 (，即"我支持此服务！") 其他调用方使用 和 来保存这些服务。
- 它提供 Update () /LateUpdate () 调用，并转发到各种服务 (即通过 UpdateAllServices/LateUpdateAllServices) 。
