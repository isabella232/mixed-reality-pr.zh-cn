---
title: Unity 中的失跟
description: 了解如何在 Unity 混合现实应用中处理手动和默认跟踪丢失。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，跟踪丢失，跟踪丢失图像，轮询，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 39ce4e079886b27ed35c419a3b3913c6700e0d32
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009847"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="c0c2a-104">Unity 中的失跟</span><span class="sxs-lookup"><span data-stu-id="c0c2a-104">Tracking loss in Unity</span></span>

<span data-ttu-id="c0c2a-105">当设备在世界各地找不到自己时，应用程序会遇到 "跟踪丢失" 的情况。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-105">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="c0c2a-106">默认情况下，Unity 将暂停更新循环，并在跟踪丢失时向用户显示一个初始映像。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-106">By default, Unity will pause the update loop and display a splash image to the user anytime tracking is lost.</span></span> <span data-ttu-id="c0c2a-107">重新获得跟踪后，初始映像将消失，更新循环将继续。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-107">Once tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="c0c2a-108">作为替代方法，用户可以通过选择退出设置来手动处理此转换。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="c0c2a-109">如果未执行任何处理操作，则所有内容似乎会在跟踪丢失时变为正文锁定状态。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="c0c2a-110">默认处理</span><span class="sxs-lookup"><span data-stu-id="c0c2a-110">Default Handling</span></span>

<span data-ttu-id="c0c2a-111">默认情况下，更新循环和所有消息和事件将在跟踪丢失期间停止。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-111">The update loop and all messages and events will stop for the duration of tracking loss by default.</span></span> <span data-ttu-id="c0c2a-112">同时，系统会向用户显示一个映像。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="c0c2a-113">可以通过以下方式自定义此映像：转到 "编辑"->"设置->播放器"，单击 "闪屏"，然后设置 "全息跟踪丢失" 图像。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="c0c2a-114">手动处理</span><span class="sxs-lookup"><span data-stu-id="c0c2a-114">Manual Handling</span></span>

<span data-ttu-id="c0c2a-115">若要手动处理跟踪丢失情况，需要执行 "**编辑**  >  **项目设置**  >  **播放器**  >  "**通用 Windows 平台 "设置" 选项卡**，  >    >  然后选择 "跟踪丢失时暂停和显示图像"。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="c0c2a-116">此后，需要处理跟踪更改和下面指定的 Api。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="c0c2a-117">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="c0c2a-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="c0c2a-118">**类型：** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="c0c2a-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="c0c2a-119">全局管理器公开一个事件，以检测 (*OnPositionalLocatorStateChanged*) 的跟踪丢失/获得的情况，并使用属性来查询当前状态 (*WorldManager*) </span><span class="sxs-lookup"><span data-stu-id="c0c2a-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="c0c2a-120">当跟踪状态处于不活动状态时，即使用户翻译，照相机也不会在虚拟世界中进行转换。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-120">When the tracking state isn't active, the camera won't appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="c0c2a-121">对象将不再与任何物理位置相对应，并且所有对象都将显示为 "已锁定"。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-121">Objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="c0c2a-122">处理自己的跟踪更改时，需要轮询每个帧的状态属性，或处理 *OnPositionalLocatorStateChanged* 事件。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-122">When handling tracking changes on your own, you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="c0c2a-123">轮询</span><span class="sxs-lookup"><span data-stu-id="c0c2a-123">Polling</span></span>

<span data-ttu-id="c0c2a-124">最重要的状态为 *PositionalLocatorState*，这意味着跟踪功能完全正常。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-124">The most important state is *PositionalLocatorState.Active*, which means tracking is fully functional.</span></span> <span data-ttu-id="c0c2a-125">任何其他状态将仅导致对主相机的循环增量。</span><span class="sxs-lookup"><span data-stu-id="c0c2a-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="c0c2a-126">例如：</span><span class="sxs-lookup"><span data-stu-id="c0c2a-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="c0c2a-127">处理 OnPositionalLocatorStateChanged 事件</span><span class="sxs-lookup"><span data-stu-id="c0c2a-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="c0c2a-128">更方便的是，还可以订阅 *OnPositionalLocatorStateChanged* 来处理转换：</span><span class="sxs-lookup"><span data-stu-id="c0c2a-128">More conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="c0c2a-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0c2a-129">See also</span></span>

* [<span data-ttu-id="c0c2a-130">在 DirectX 中处理跟踪丢失</span><span class="sxs-lookup"><span data-stu-id="c0c2a-130">Handling tracking loss in DirectX</span></span>](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
