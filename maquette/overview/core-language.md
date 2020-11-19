---
title: 核心语言
description: 了解 Maquette 的核心语言详细信息。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality，Maquette，原型设计，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
ms.openlocfilehash: e0c0b2f204aa32245cc13aff4c64fa641313de51
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935418"
---
# <a name="maquettescript-core-language-details"></a>MaquetteScript 核心语言详细信息

<!-- TODO(Harrison): Need consolidated logo with text -->
![Maquette 徽标 ](../images/MaquetteIcon.png) MaquetteScript 核心语言详细信息

## <a name="accessing-maquette-object-and-namespace"></a>访问 `Maquette` 对象和命名空间

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
Maquette 通过 `Maquette` 对象及其子对象公开 JavaScript 中的内部对象和接口。 此功能在 [Maquette 对象和命名空间](https://www.maquette.ms/doc_staging/objects/Maquette.html) 文档中进行了介绍。 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
`Maquette`对象具有顶级函数，使你可以更轻松地与 Maquette 本身交互，并使重复性问题更易于解决。 这在 [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)的文档中进行了介绍。

## <a name="maquette-startup-and-loading"></a>Maquette 启动和加载

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
Maquette 将加载并评估特定 JavaScript 文件，以便在以下时间启用配置、设置和初始化：

在 Maquette 启动过程中：
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

每次加载项目时：
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

项目加载各自的项目脚本：
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a>JavaScript 实现

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
Maquette 中使用的 JavaScript 解释器基于 [Jint](https://github.com/sebastienros/jint)。 Jint 是 ECMAScript 5.1 兼容的，并支持 [来自 ecmascript 6 的其他扩展](https://github.com/sebastienros/jint/issues/343)。 

此扩展 `.mqjs` 用于将 Maquette javascript 文件与普通 javascript 区分开来。

## <a name="see-also"></a>请参阅 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->