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
# <a name="maquettescript-core-language-details"></a><span data-ttu-id="7a6f2-104">MaquetteScript 核心语言详细信息</span><span class="sxs-lookup"><span data-stu-id="7a6f2-104">MaquetteScript core language details</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="7a6f2-105">![Maquette 徽标 ](../images/MaquetteIcon.png) MaquetteScript 核心语言详细信息</span><span class="sxs-lookup"><span data-stu-id="7a6f2-105">![Maquette logo](../images/MaquetteIcon.png) MaquetteScript Core Language Details</span></span>

## <a name="accessing-maquette-object-and-namespace"></a><span data-ttu-id="7a6f2-106">访问 `Maquette` 对象和命名空间</span><span class="sxs-lookup"><span data-stu-id="7a6f2-106">Accessing `Maquette` Object and Namespace</span></span>

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="7a6f2-107">Maquette 通过 `Maquette` 对象及其子对象公开 JavaScript 中的内部对象和接口。</span><span class="sxs-lookup"><span data-stu-id="7a6f2-107">Maquette exposes internal objects and interfaces in JavaScript through the `Maquette` object and its children.</span></span> <span data-ttu-id="7a6f2-108">此功能在 [Maquette 对象和命名空间](https://www.maquette.ms/doc_staging/objects/Maquette.html) 文档中进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="7a6f2-108">This functionality is described in the [Maquette Object and Namespace](https://www.maquette.ms/doc_staging/objects/Maquette.html) documentation.</span></span> 

<!-- TODO(Stefan): Need high-level summary of this functionality before we send people to an outside docs link. -->
<span data-ttu-id="7a6f2-109">`Maquette`对象具有顶级函数，使你可以更轻松地与 Maquette 本身交互，并使重复性问题更易于解决。</span><span class="sxs-lookup"><span data-stu-id="7a6f2-109">The `Maquette` object has top-level functions to make it easier to interact with Maquette itself and make repetitive problems easier to solve.</span></span> <span data-ttu-id="7a6f2-110">这在 [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html)的文档中进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="7a6f2-110">This is described in the documentation of [MaquetteScriptObject](https://www.maquette.ms/doc_staging/objects/Maquette.MaquetteScriptObject.html).</span></span>

## <a name="maquette-startup-and-loading"></a><span data-ttu-id="7a6f2-111">Maquette 启动和加载</span><span class="sxs-lookup"><span data-stu-id="7a6f2-111">Maquette Startup and Loading</span></span>

<!-- TODO(Stefan): Need context on why this is important for users and how they will take advantage of this in production? -->
<span data-ttu-id="7a6f2-112">Maquette 将加载并评估特定 JavaScript 文件，以便在以下时间启用配置、设置和初始化：</span><span class="sxs-lookup"><span data-stu-id="7a6f2-112">Maquette will load and evaluate specific JavaScript files to enable config, setup and initialization at the following times:</span></span>

<span data-ttu-id="7a6f2-113">在 Maquette 启动过程中：</span><span class="sxs-lookup"><span data-stu-id="7a6f2-113">During Maquette startup:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteStartup.mqjs
</pre>

<span data-ttu-id="7a6f2-114">每次加载项目时：</span><span class="sxs-lookup"><span data-stu-id="7a6f2-114">Whenever any project is loaded:</span></span>
<pre>
~/Documents/Maquette/Scripts/OnMaquetteProjectLoad.mqjs
</pre>

<span data-ttu-id="7a6f2-115">项目加载各自的项目脚本：</span><span class="sxs-lookup"><span data-stu-id="7a6f2-115">Projects load their respective project scripts:</span></span>
<pre>
~/Documents/Maquette/Project/&lt;Your Project&gt;/Scripts/OnLoad.mqjs
</pre>

## <a name="javascript-implementation"></a><span data-ttu-id="7a6f2-116">JavaScript 实现</span><span class="sxs-lookup"><span data-stu-id="7a6f2-116">JavaScript Implementation</span></span>

<!-- TODO(Stefan): Is there anything else we can tell users about the JS interpreter as applied to Maquette? -->
<span data-ttu-id="7a6f2-117">Maquette 中使用的 JavaScript 解释器基于 [Jint](https://github.com/sebastienros/jint)。</span><span class="sxs-lookup"><span data-stu-id="7a6f2-117">The JavaScript interpreter used in Maquette is based on [Jint](https://github.com/sebastienros/jint).</span></span> <span data-ttu-id="7a6f2-118">Jint 是 ECMAScript 5.1 兼容的，并支持 [来自 ecmascript 6 的其他扩展](https://github.com/sebastienros/jint/issues/343)。</span><span class="sxs-lookup"><span data-stu-id="7a6f2-118">Jint is ECMAScript 5.1 compatible and supports additional [extensions from ECMAScript 6](https://github.com/sebastienros/jint/issues/343).</span></span> 

<span data-ttu-id="7a6f2-119">此扩展 `.mqjs` 用于将 Maquette javascript 文件与普通 javascript 区分开来。</span><span class="sxs-lookup"><span data-stu-id="7a6f2-119">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a6f2-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="7a6f2-120">See also</span></span> 
<!-- TODO(Stefan): Add any additional JS related links that may help with troubleshooting or issues? -->