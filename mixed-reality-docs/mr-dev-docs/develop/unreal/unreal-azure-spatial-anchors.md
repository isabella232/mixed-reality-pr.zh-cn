---
title: Unreal 中的 Azure 空间定位点
description: 了解如何在 Unreal 混合现实应用程序中创建、管理和定位现有的 Azure 空间定位点。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, azure 开发, 空间定位点, 混合现实, 开发, 功能, 新项目, 仿真器, 文档, 指南, 全息影像, 游戏开发, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 5797cd48198b163b55f3724685126b1d4d85c69c
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583025"
---
# <a name="azure-spatial-anchors-in-unreal"></a>Unreal 中的 Azure 空间定位点

Azure 空间定位点是一项 Microsoft Mixed Reality 服务，增强现实设备可用它来发现、共享和保存现实世界中的定位点。 下列文档介绍了如何将 Azure 空间定位点服务集成到 Unreal 项目中。 若要了解详细信息，请查看 [Azure 空间定位点服务](https://azure.microsoft.com/services/spatial-anchors/)。

> [!NOTE]
> Unreal Engine 4.26 现具有适合 ARKit 和 ARCore 支持的插件，供你在面向 iOS 或 Android 时使用。

> [!IMPORTANT]
> 本地定位点存储在设备上，而 Azure 空间定位点存储在云中。 如果你想要在设备上本地存储定位点，我们有一个[本地空间定位点](unreal-spatial-anchors.md)文档可指导你完成整个过程。 请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。

## <a name="prerequisites"></a>必备条件

要完成本指南，请确保：

- 已安装 [Unreal 4.25](https://www.unrealengine.com/get-now) 或更高版本
- 已在 Unreal 中设置 [HoloLens 2 项目](tutorials/unreal-uxt-ch1.md) 
- 已仔细阅读 [Azure 空间定位点概述](/azure/spatial-anchors/overview)
- 具备 C++ 和 Unreal 的基础知识

## <a name="getting-azure-spatial-anchors-account-info"></a>获取 Azure 空间定位点帐户信息

在项目中使用 Azure 空间定位点之前，你需要：
* [创建空间定位点资源](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)并复制下面列出的帐户字段。 这些值用于向你的应用程序的帐户验证用户的身份：
    * **帐户 ID**
    * **帐户密钥**

有关详细信息，请查看 [Azure 空间定位点身份验证](/azure/spatial-anchors/concepts/authentication?tabs=csharp)文档。

> [!NOTE]
> Unreal 4.25 中的 Azure 空间定位点不支持 Azure AD 身份验证令牌，但今后的版本中将提供对该功能的支持。

## <a name="adding-azure-spatial-anchors-plugins"></a>添加 Azure 空间定位点插件

通过以下方法在 Unreal 编辑器中启用 Azure 空间定位点插件：
1. 单击“编辑”>“插件”，然后搜索“AzureSpatialAnchors”和“AzureSpatialAnchorsForWMR”  。
2. 选中这两个插件中的“启用”复选框，允许访问你的应用程序中的 Azure 空间定位点蓝图库。

![Unreal 编辑器中空间定位点插件的屏幕截图](images/asa-unreal/unreal-spatial-anchors-img-01.png)

完成后，重启 Unreal 编辑器，使插件更改生效。 该项目现就可使用 Azure 空间定位点了。

## <a name="starting-a-spatial-anchors-session"></a>启动空间定位点会话

通过 Azure 空间定位点会话，客户端应用程序可与 Azure 空间定位点服务通信。 你需要创建并启动 Azure 空间定位点会话才能创建、保存和共享 Azure 空间定位点：

1. 打开你在应用程序中使用的 Pawn 的蓝图。
2. 添加两个字符串变量分别用于帐户 ID 和帐户密钥，然后从 Azure 空间定位点帐户分配相应的值，对会话进行身份验证 。

![详细信息面板的屏幕截图，其中突出显示了 Azure 空间定位点帐户 ID、密钥和变量类型](images/asa-unreal/unreal-spatial-anchors-img-02.png)

通过以下方式启动 Azure 空间定位点会话：
1. 检查 AR 会话是否正在 HoloLens 应用程序中运行，因为在 AR 会话运行之后，才能启动 Azure 空间定位点会话。 如果未设置，请[创建 AR 会话资产](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)。
2. 添加名为“启动 Azure 空间定位点会话”的自定义事件并对其进行配置，如下面的屏幕截图所示。
    * 默认情况下，创建会话不会启动会话，这使得你可配置会话来向 Azure 空间定位点服务进行身份验证。

![启动 Azure 空间定位点会话自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. 配置 Azure 空间定位点会话，以提供帐户 ID 和帐户密钥 。

![添加了帐户 ID 和密钥的 config session 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. 启动 Azure 空间定位点会话，让应用程序能够创建和查找 Azure 空间定位点。

![Azure 空间定位点 session start 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-05.png)

不再使用该服务时，最好清理 Event Graph 蓝图中的 Azure 空间定位点资源：

1. 停止 Azure 空间定位点会话。 该会话将不再运行，但它关联的资源仍将保留在 Azure 空间定位点插件中。

![stop azure spatial anchors sessions custom event and stop session 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. 销毁 Azure 空间定位点会话，来清理 Azure 空间定位点插件仍然知晓的所有 Azure 空间定位点会话资源。

![destroy session 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-07.png)

你的 Event Graph 蓝图应该会与以下屏幕截图类似：

![Azure 空间定位点会话设置的完整事件图的蓝图](images/asa-unreal/unreal-spatial-anchors-img-08.png)

## <a name="creating-an-anchor"></a>创建定位点

Azure 空间定位点是现实世界中的姿势在增强现实应用空间中的表示形式，它将增强现实内容与物理位置挂钩。 Azure 空间定位点也可在不同的用户之间共享。 通过这种共享，在不同设备上绘制的增强现实内容可放置到现实世界中的同一个位置。 

若要创建新的 Azure 空间定位点：
1. 检查 Azure 空间定位点会话是否正在运行。 如果 Azure 空间定位点会话都未运行，则应用程序无法创建或保留 Azure 空间定位点。

![创建 Azure 空间定位点自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. 创建或获取 Unreal [场景组件](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)（该组件应保留其所在位置）。 
    * 在下图中，“场景组件需要定位点”组件用作变量。 要为 [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) 和 Azure 空间定位点建立应用世界坐标变换，需要使用 Unreal 场景组件。

![使用场景组件创建 Azure 空间定位点自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-10.png)

若要为 Unreal 场景组件构造并保存 Azure 空间定位点：
1. 为 Unreal 场景组件调用 [Pin 组件](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html)，并将场景组件的世界坐标变换指定为用于 AR Pin 的世界坐标变换。
    * Unreal 使用 AR Pin 来跟踪应用空间中的 AR 点，AR Pin 用于创建 Azure 空间定位点。 在 Unreal 中，AR Pin 与 HoloLens 上的 SpatialAnchor 类似。

![连接到 pin component 函数的场景组件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. 使用新创建的 AR Pin 调用“创建云定位点”。
    * “创建云定位点”会在本地创建 Azure 空间定位点，但不在 Azure 空间定位点服务中进行创建。 在使用服务创建 Azure 空间定位点之前，可设置 Azure 空间定位点的参数（例如到期日期）。

![连接到返回 ARPin 的 create cloud anchor 函数的 pin component 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. 设置 Azure 空间定位点的到期日期。 通过此函数的生存期参数，开发人员可以秒为单位指定服务应维护定位点多长时间。
    * 例如，一周有效期的值的计算方式为：60 秒 x 60 分钟 x 24 小时 x 7 天 = 604,800 秒。

![连接到 set expiration 函数（其生存期值设置为 604,800 秒）的云定位点的蓝图](images/asa-unreal/unreal-spatial-anchors-img-13.png)

设置定位点参数后，将定位点声明为已可供保存。 在下例中，新创建的 Azure 空间定位点会被添加到一组需要保存的 Azure 空间定位点中。 这组定位点被声明为 Pawn 蓝图的变量。

![准备保存在 set 变量中的定位点蓝图](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a>保存定位点

在用参数配置 Azure 空间定位点之后，调用“保存云定位点”。 “保存云定位点”会将定位点声明指向 Azure 空间定位点服务。 “保存云定位点”调用成功后，Azure 空间定位点可供 Azure 空间定位点服务的其他用户使用。  

![正在调用的 save cloud anchor 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> “保存云定位点”是一个异步函数，只能在游戏线程事件（例如 EventTick）上调用。 在自定义蓝图函数中，“保存云定位点”可能不会显示为可用的蓝图函数。 但是，应该能在 Pawn Event Graph 蓝图编辑器中使用它。

在下例中，Azure 空间定位点在输入事件回调期间存储在一个集合中。 随后，在出现 EventTick 时保存定位点。 保存 Azure 空间定位点可能需要多次尝试，具体取决于 Azure 空间定位点会话创建的空间数据量。 这就是检查保存调用是否成功的原因。

如果定位点没有保存，请重新将它添加到仍然需要保存的定位点集中。 之后的 EventTick 将继续尝试保存定位点，直到它成功存储。

![在 set 变量中再次保存未保存定位点的蓝图](images/asa-unreal/unreal-spatial-anchors-img-16.png)

保存定位点后，AR Pin 的变换用作将内容置于应用中的引用坐标变换。 其他用户可检测此定位点，请针对现实世界中的不同设备将 AR 内容对齐。

## <a name="deleting-an-anchor"></a>删除定位点

可通过调用“删除云定位点”，从 Azure 空间定位点服务中删除定位点。

![正在调用的 delete cloud anchor 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> “删除云定位点”是一个潜在函数，只能在游戏线程事件（例如 EventTick）上调用。 在自定义蓝图函数中，“删除云定位点”可能不会显示为可用的蓝图函数。 但是，应该能够在 Pawn Event Graph 蓝图编辑器中使用它。

在下例中，定位点被标记为要在发生自定义输入事件时删除。 系统随后在发生 EventTick 时尝试删除。 如果定位点删除失败，请将 Azure 空间定位点添加到已标记为要删除且将在发生后续 EventTick 时重试的定位点集中。

你的 Event Graph 蓝图现在应该会与以下屏幕截图类似：

![用于处理云定位点的完整事件图的蓝图](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a>查找预先存在的定位点

对等方可以使用 Azure 空间定位点服务创建现有定位点：

1. 获取要检测的定位点的 Azure 空间定位点标识符。
    * 可为在之前的 Azure 空间定位点会话中由同一设备创建的定位点获取定位点标识符。 它还可由与 Azure 空间定位点服务交互的对等设备进行创建和共享。

![使用 get azure cloud identifier 函数的存储 Azure 空间定位点标识符自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. 将 AzureSpatialAnchorsEvent 组件添加到 Pawn 蓝图中。
    * 通过此组件可订阅各种 Azure 空间定位点事件，例如在查找 Azure 空间定位点时调用的事件。

![屏幕截图显示了蓝图编辑器中打开的 BP_Pawn，其中打开了组件和详细信息面板](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. 订阅 AzureSpatialAnchorsEvent 组件的“ASAAnchor 已找到委托” 。
    * 通过委托，应用程序可知道已找到与 Azure 空间定位点帐户关联的新的定位点。
    * 默认情况下，通过事件回调，由使用 Azure 空间定位点会话的对等方创建的 Azure 空间定位点不会创建 AR Pin。 要为检测到的 Azure 空间定位点创建 AR Pin，开发人员可调用“围绕 Azure 云空间定位点创建 ARPin”。

![连接到 ASAAnchor 所找到委托的开始播放事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-20.png)

若要查找由使用 Azure 空间定位点服务的 Peer 创建的 Azure 空间定位点，应用程序必须创建“Azure 空间定位点观察程序”：
1. 检查 Azure 空间定位点会话是否正在运行。
2. 创建 AzureSpatialAnchorsLocateCriteria。
    * 可指定不同的位置参数，例如与用户的距离或与另一定位点的距离。
3. 在 AzureSpatialAnchorsLocateCritieria 中声明所需的 Azure 空间定位点标识符。
4. 调用“创建观察程序”。

![启动 Azure 空间定位点观察程序自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-21.png)

应用程序现开始查找 Azure 空间定位点服务已知的 Azure 空间定位点，这意味着用户可找到由其对等方创建的 Azure 空间定位点。

找到 Azure 空间定位点后，调用“停止观察程序”来停止 Azure 空间定位点观察程序，并清理观察程序资源。

![正在调用的 stop watcher 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-22.png)

最终的 Event Graph 蓝图现在应该会与以下屏幕截图类似：

![用于处理定位点委托事件的完整事件图的蓝图](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unreal 开发历程，则你处于探索 MRTK 核心基础知识的过程之中。 从这里，你可以继续了解下一部分基础知识： 

> [!div class="nextstepaction"]
> [空间映射](unreal-spatial-mapping.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [HoloLens 摄像头](unreal-hololens-camera.md)

你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。


## <a name="next-steps"></a>后续步骤
* [本地空间定位点](unreal-spatial-anchors.md)
* [空间定位点文档](/azure/spatial-anchors/)
* [空间定位点功能](https://azure.microsoft.com/services/spatial-anchors/#features)
* [有效定位点体验准则](/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)