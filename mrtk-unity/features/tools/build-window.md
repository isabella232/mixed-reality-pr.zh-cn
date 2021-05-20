---
title: MRTK 生成窗口
description: 有关在适用于 Unity 的 MRTK 中使用生成窗口的文档。
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 生成， 生成窗口， 工具
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196844"
---
# <a name="build-window"></a><span data-ttu-id="ed50a-104">“生成”窗口</span><span class="sxs-lookup"><span data-stu-id="ed50a-104">Build window</span></span>
![生成&部署流](images/MRTK_BuildWindow0.png)

<span data-ttu-id="ed50a-106">使用 MRTK 的生成窗口可以轻松生成&部署MRTK-Unity项目。</span><span class="sxs-lookup"><span data-stu-id="ed50a-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="ed50a-107">单击单个按钮即可生成 Unity 项目，并生成Visual Studio解决方案 (。SLN) ，UWP 应用包 (。APPX) ，在设备上安装应用包。</span><span class="sxs-lookup"><span data-stu-id="ed50a-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="ed50a-108">Unity 生成选项</span><span class="sxs-lookup"><span data-stu-id="ed50a-108">Unity Build Options</span></span>
![生成窗口 - Unity 生成选项 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="ed50a-110">这些场景来自 Unity 生成设置。</span><span class="sxs-lookup"><span data-stu-id="ed50a-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="ed50a-111">可以使用下拉菜单更改目标设备类型。</span><span class="sxs-lookup"><span data-stu-id="ed50a-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="ed50a-112">Appx 生成选项</span><span class="sxs-lookup"><span data-stu-id="ed50a-112">Appx Build Options</span></span>
![生成窗口 - Appx 生成选项 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="ed50a-114">此选项卡显示解决方案Visual Studio配置。</span><span class="sxs-lookup"><span data-stu-id="ed50a-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="ed50a-115">若要启用HoloLens 2眼动跟踪输入功能，请检查" **凝视输入功能"** 选项。</span><span class="sxs-lookup"><span data-stu-id="ed50a-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="ed50a-116">可以在自定义 3D 应用启动器图标的 **"3D 应用** 启动器模型"字段中分配 .glb 文件。</span><span class="sxs-lookup"><span data-stu-id="ed50a-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="ed50a-117">有关详细信息 [，请参阅 3D 应用启动器](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 设计准则。</span><span class="sxs-lookup"><span data-stu-id="ed50a-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="ed50a-118">默认情况下 **，"版本控制** 选项"中会选中"自动递增"。</span><span class="sxs-lookup"><span data-stu-id="ed50a-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="ed50a-119">AppX 版本将自动递增。</span><span class="sxs-lookup"><span data-stu-id="ed50a-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="ed50a-120">部署选项</span><span class="sxs-lookup"><span data-stu-id="ed50a-120">Deploy Options</span></span>
![生成窗口 - 部署选项 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="ed50a-122">在此选项卡中，可以通过输入设备门户的用户名和密码来连接到设备。</span><span class="sxs-lookup"><span data-stu-id="ed50a-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="ed50a-123">在页面的底部，可以找到已创建的应用包的列表。</span><span class="sxs-lookup"><span data-stu-id="ed50a-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

