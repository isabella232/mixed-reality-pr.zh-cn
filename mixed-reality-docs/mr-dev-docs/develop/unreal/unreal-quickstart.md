---
title: 创建 HoloLens 项目
description: 了解如何为 HoloLens 混合现实开发正确配置具有场景对象和输入交互的 Unreal 项目。
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal 编辑器, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 移植, 升级
ms.openlocfilehash: 3b2b88ac897a8791fec1ca2942d0db34efcee598
ms.sourcegitcommit: be33fcda10d1cb98df90b428a923289933d42c77
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2021
ms.locfileid: "98672734"
---
# <a name="creating-a-hololens-project"></a>创建 HoloLens 项目

首先需要一个待处理的项目。 如果你是刚接触的 Unreal 开发人员，则需要从 Epic Launcher [下载支持文件](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。

1. 启动 Unreal Engine
2. 在“新建项目类别”中，选择“游戏”，然后单击“下一步”  ：

![“最近使用的项目”窗口打开，并突出显示了“游戏”](images/unreal-quickstart-img-01.png)

3. 选择“空白”模板，然后单击“下一步” ：

![Unreal 项目浏览器窗口，突出显示了“空白”模板](images/unreal-quickstart-img-02.png)

4. 在“项目设置”中，设置“C++、可缩放的 3D 或 2D、移动/平板电脑”和“非初学者内容”，然后选择保存位置并单击“创建项目”   

> [!NOTE] 使用 C++ 而不是 Blueprint 项目，以便后续可以使用 OpenXR 插件。 本快速入门使用 Unreal Engine 随附的默认 OpenXR 插件。 但建议下载和使用官方的 Microsoft OpenXR 插件。 这要求项目是 C++ 项目。

![“项目设置”窗口，突出显示了项目、性能、目标平台和初学者内容选项](images/unreal-quickstart-img-03.png)

新项目应在 Unreal 编辑器中自动打开，这意味着你已准备好进入下一部分。

## <a name="enabling-required-plugins"></a>启用所需插件

你需要启用两个插件，然后才能开始向场景添加对象。

1. 打开“编辑”>“插件”，并从内置选项列表中选择“增强现实”。
* 向下滚动到“HoloLens”并选中“已启用” 

![“插件”窗口，打开了“增强现实”部分并突出显示了 HoloLens](images/unreal-quickstart-img-04.png)

2. 在右上角的搜索框中键入 OpenXR，然后启用 OpenXR 和 OpenXRMsftHandInteraction 插件  ：

![“插件”窗口，其中启用了 OpenXR](images/unreal-quickstart-img-05.jpg)

![“插件”窗口，其中启用了 OpenXR Msft Hand Interaction](images/unreal-quickstart-img-06.jpg)

3. 重启编辑器

> [!NOTE]
> 本教程使用 OpenXR，但上文中安装的两个插件目前尚不提供适用于 HoloLens 开发的完整功能集。 HandInteraction 插件可满足后续将使用的“收缩”手势的要求，但如果还想实现基础要求以外的要求，则需要[下载 OpenXR 插件](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。

启用插件后，可专注于为其填充内容。

## <a name="creating-a-level"></a>创建关卡

下一个任务是创建具有可供参考和缩放的起点和立方体的玩家设置。

1. 选择“文件”>“新关卡”>“空关卡”。 视口中的默认场景现在应为空
2. 从“模式”选项卡中选择“基本”，并将“PlayerStart”拖到场景中  
* 在“详细信息”选项卡中，将“位置”设置为“X = 0, Y = 0”和“Z = 0”，以便在应用启动时将用户放置到场景的中心   

![Unreal 编辑器场景，其中添加了位置和 PlayerStart](images/unreal-quickstart-img-07.png)

3. 在“基本”选项卡中，将“立方体”拖到场景中 
* 将立方体的“位置”设置为“X = 50, Y = 0”和“Z = 0”，以便在启动时将立方体放置于距播放器 50 厘米处的位置  
* 将立方体的“缩放”更改为“X = 0.2, Y = 0.2”和“Z = 0.2”   

除非向场景添加光源（这是测试场景前的最后一个任务），否则看不到立方体。

4. 在“模式”面板上，切换到“光”选项卡，然后将“定向光”拖到场景中  
* 将光置于“PlayerStart”上方，以便可以看到它

![Unreal 编辑器场景，其中添加了立方体和定向光](images/unreal-quickstart-img-08.png)

5. 转到“文件”>“保存当前”，将关卡命名为“主”，然后选择“保存”  

设置场景后，按工具栏中的“开始”，以查看正在运行的立方体！ 完成工作后，按 Esc 停止应用程序。

![播放模式下的场景，其中立方体位于屏幕中间](images/unreal-quickstart-img-09.png)

设置好场景后，准备在 AR 中进行一些基本交互。 首先，需创建 AR 会话，然后可以添加蓝图以启用手动交互。

## <a name="adding-a-session-asset"></a>添加会话资产

Unreal 中的 AR 会话无法自行发生。 要使用会话，需要借助 ARSessionConfig 数据资产，这就是接下来的任务：

1. 在“内容浏览器”中，选择“添加新项”>“其他”>“数据资产”，并确保位于根“内容”文件夹级别 
2. 选择“ARSessionConfig”，单击“选择”，然后将资产命名为“ARSessionConfig”  ：

![“选择数据资产类”窗口打开，其中突出显示了 AR 会话配置资产](images/unreal-quickstart-img-10.png)

2. 双击“ARSessionConfig”将其打开，保存所有默认设置，然后返回到主窗口 ：

![“AR 会话配置资产详细信息”窗口](images/unreal-quickstart-img-11.png)

完成此操作后，下一步是确保在关卡加载时 AR 会话会启动，而在关卡结束时 AR 会话会停止。 幸运的是，Unreal 具有叫做“关卡蓝图”的特殊蓝图，它用作关卡范围的全局事件图。 在关卡蓝图中连接 ARSessionConfig 资产，可确保游戏开始时 AR 会话将立即触发。

3. 从编辑器工具栏中，选择“蓝图”>“打开关卡蓝图”：

![“蓝图”菜单打开，其中突出显示了“打开关卡蓝图”选项](images/unreal-quickstart-img-12.png)

4. 将执行节点（左指箭头图标）拖离 Event BeginPlay 并释放
* 搜索“启动 AR 会话”节点，然后按 Enter 键
* 单击“会话配置”下的“选择资产”下拉列表，然后选择“ARSessionConfig”资产  

![“蓝图”图，其中“event begin play”连接到了“start ar session”函数](images/unreal-quickstart-img-13.png)

5. 右键单击 EventGraph 中的任意位置，然后创建一个新的 Event EndPlay 节点。 
* 拖动执行脚本，随后放开，然后搜索“停止 AR 会话”节点并按 Enter 
* 点击“编译”和保存”，然后返回到主窗口 

> [!IMPORTANT]
> 如果在关卡结束时 AR 会话仍在运行，那么在流式传输到头戴显示设备时，如果你重启应用，某些功能可能会停止工作。

![附加到“stop ar session”函数的“event end play”节点](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>设置输入

1. 选择“编辑”>“项目设置”，然后转到“引擎”>“输入” 
2. 选择“操作映射”旁的 + 图标，然后创建 RightPinch 和 LeftPinch 操作   ：

![“绑定输入”设置，其中突出显示了右收缩和左收缩操作映射](images/unreal-quickstart-img-15.jpg)

3. 将 RightPinch 和 LeftPinch 操作映射到相应的 OpenXR Msft Hand Interaction 操作  ：

![操作映射，其中突出显示了 Open XR Msft Hand Interaction 选项](images/unreal-quickstart-img-16.jpg)

4. 打开“关卡蓝图”，然后添加 InputAction RightPinch 和 InputAction LeftPinch  
* 将右收缩事件连接到 AddActorLocalRotation，并将立方体作为目标，将“Delta 旋转”设置为“X = 0, Y = 0”和“Z = 20”    。 现在每次收缩时，立方体将旋转 20 度
* 将左收缩事件连接到“退出游戏”

![关卡蓝图打开，其中有针对右收缩和左收缩事件的输入操作](images/unreal-quickstart-img-17.jpg)

5. 在立方体的“转换”设置中，将“移动性”设置为“可移动”，使其可动态移动  ：

![“转换”设置，其中突出显示了“移动性”属性](images/unreal-quickstart-img-18.jpg)

现在即可部署和测试应用程序！