---
title: 创建全息远程处理电脑应用程序
description: 完成本课程可以了解如何创建电脑应用程序来远程处理从电脑到 HoloLens 2 的混合现实体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 电脑全息远程处理, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: 916a9396c0b29637d5619bac203718e05112b598
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590299"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2.创建全息远程处理电脑应用程序

本教程将介绍如何创建用于全息远程处理的电脑应用并随时连接到 HoloLens 2，从而提供一种在混合现实中直观显示 3D 内容的方式。

## <a name="objectives"></a>目标

* 为全息远程处理配置 Unity
* 了解如何通过 Visual Studio 生成和部署应用程序
* 开发全息远程处理应用程序并连接到 HoloLens

## <a name="configuring-your-scene-for-holographic-remoting"></a>为全息远程处理配置场景

在本部分，你将配置项目，以通过 Wi-Fi 连接将电脑上的混合现实体验实时流式传输到 HoloLens 2 设备。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.PCHolograhicRemoting” > “预制件”文件夹，然后单击“HolographicRemoting”预制件并将其拖放到场景中   。

![新增的 HolographicRemoting 预制件仍处于选中状态的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>在电脑上构建应用程序

全息远程处理应用现可在你的电脑上生成内容。 请按照以下步骤进行这些更改，以在电脑上构建该应用程序。

### <a name="1-set-the-player-settings"></a>1.设置播放器设置

在 Unity 菜单中选择“编辑”>“项目设置”，打开“播放器设置”窗口。

在“项目设置”窗口中，展开“发布设置”，向下滚动到“功能”部分，然后选择下面除现有功能外显示的功能复选框 。

* Internet 客户端服务器
* 专用网络客户端服务器

在“XR 设置”部分，选中“支持的 WSA 全息远程处理”复选框，启用全息远程处理 。

![启用了“支持 WSA 全息远程处理”的 Unity XR 设置窗口](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2.生成 Unity 项目

在 Unity 菜单中选择“文件”>“生成设置”，打开“生成设置”窗口。

在“生成设置”窗口中，单击“添加打开的场景”按钮，将当前场景添加到“场景”中。 在“生成”列表中，单击“生成”按钮以打开“生成通用 Windows 平台”窗口：

![添加了场景的 Unity“生成设置”窗口](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

在“生成通用 Windows 平台”窗口中，选择一个合适的位置来存储生成结果，例如 Documents\MixedRealityLearning。 创建一个新文件夹并为其指定合适的名称，例如 PCHolographicRemoting。 然后单击“选择文件夹”按钮，开始生成过程：

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

等待 Unity 完成生成过程。

![Unity 正在生成进程](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3.生成并部署应用程序

生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。 在文件夹内导航，然后双击 .sln 文件，在 Visual Studio 中其打开：

![选中了新建的“Visual Studio 解决方案”的 Windows 资源管理器](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> 如果 Visual Studio 要求安装新组件，请花一点时间确保按照安装工具文档中的说明安装所有必备组件。

通过选择“发布配置”、“x64 体系结构”和“本地计算机”作为目标，配置 PC 版 Visual Studio：

![配置了“本地计算机”的 Visual Studio](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

单击“本地计算机”按钮。 它会开始生成应用程序并将其部署到你的电脑。 该应用程序将默认安装在你的电脑中。

## <a name="testing-holographic-remoting-remote-application"></a>测试“全息远程处理”远程应用程序

若要将电脑应用程序连接到 HoloLens 2，请执行以下过程：

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1.在 HoloLens 2 设备上安装“远程播放器”应用程序

* 在 HoloLens 2 上，访问 Store 应用并搜索“远程播放器”。
* 选择“远程播放器”应用。
* 点击“安装”，下载并安装该应用。

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2.将全息远程处理电脑应用连接到远程播放器

* 在 HoloLens 上启动“远程播放器”。
* 记下 HoloLens IP 地址。 远程播放器启动后，会立即将其显示为全息图。
* 在电脑上打开全息远程处理电脑应用程序。
* 启动该应用程序后，输入 IP 地址，然后单击“连接”按钮进行连接 。

## <a name="congratulations"></a>祝贺

本教程介绍了如何创建全息远程处理远程应用并随时连接到 HoloLens 2，从而提供一种在混合现实中直观显示 3D 内容的方式。 将 HoloLens 连接到全息远程处理电脑应用程序后，你应该会看到混合现实体验流式传输到 HoloLens 2 设备。
