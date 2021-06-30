---
title: 框架和运行时
description: 与 MRTK 中的框架和运行时有关的信息。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121605"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="9f63a-104">框架和运行时</span><span class="sxs-lookup"><span data-stu-id="9f63a-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="9f63a-105">对场景的更改</span><span class="sxs-lookup"><span data-stu-id="9f63a-105">Changes to the scene</span></span>

<span data-ttu-id="9f63a-106">若要使用工具包，MixedRealityToolkit 脚本的实例必须在你的场景中。</span><span class="sxs-lookup"><span data-stu-id="9f63a-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="9f63a-107">若要添加一个，请使用菜单选项：混合现实工具包 ->添加到场景和配置。</span><span class="sxs-lookup"><span data-stu-id="9f63a-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="9f63a-108">此实例负责注册、更新和拆收服务。</span><span class="sxs-lookup"><span data-stu-id="9f63a-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="9f63a-109">这也是选择配置文件的地方。</span><span class="sxs-lookup"><span data-stu-id="9f63a-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="9f63a-110">除了将 MRTK GameObject 添加到场景中外，菜单选项还将：</span><span class="sxs-lookup"><span data-stu-id="9f63a-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="9f63a-111">添加 MixedRealityPlayspace，许多其他 MRTK 组件都使用该空间进行全球和本地空间转换。</span><span class="sxs-lookup"><span data-stu-id="9f63a-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="9f63a-112">将主相机作为 MixedRealityPlayspace (的子级移动，还将一些与输入和凝视相关的脚本添加到主相机，这有助于为 UnityUI 和凝视相关的输入功能) 。</span><span class="sxs-lookup"><span data-stu-id="9f63a-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="9f63a-113">MixedRealityToolkit 对象和运行时</span><span class="sxs-lookup"><span data-stu-id="9f63a-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="9f63a-114">MRTK 具有多个核心服务。</span><span class="sxs-lookup"><span data-stu-id="9f63a-114">The MRTK has several core services.</span></span> <span data-ttu-id="9f63a-115">相互协调;其他是独立的。</span><span class="sxs-lookup"><span data-stu-id="9f63a-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="9f63a-116">全部共享相同的生命周期（启动、注册、更新和拆解）并且此生命周期与 Unity 的 MonoBehaviour 生命周期不同。</span><span class="sxs-lookup"><span data-stu-id="9f63a-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="9f63a-117">此 [中等帖子](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) 解释了此方法背后的一些背景和动机。</span><span class="sxs-lookup"><span data-stu-id="9f63a-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="9f63a-118">MRTK 有一个对象，用于管理其服务生命周期和运行时。</span><span class="sxs-lookup"><span data-stu-id="9f63a-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="9f63a-119">此实体可确保：</span><span class="sxs-lookup"><span data-stu-id="9f63a-119">This entity ensures that:</span></span>

- <span data-ttu-id="9f63a-120">游戏开始时，服务的发现和初始化按预定义的顺序进行。</span><span class="sxs-lookup"><span data-stu-id="9f63a-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="9f63a-121">它提供了一种机制，使服务能够自行注册 (，即"我支持此服务！") 其他调用方使用 和 来保存这些服务。</span><span class="sxs-lookup"><span data-stu-id="9f63a-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="9f63a-122">它提供 Update () /LateUpdate () 调用，并转发到各种服务 (即通过 UpdateAllServices/LateUpdateAllServices) 。</span><span class="sxs-lookup"><span data-stu-id="9f63a-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
