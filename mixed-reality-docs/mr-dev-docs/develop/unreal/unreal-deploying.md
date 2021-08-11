---
title: 在 Unreal 中部署到设备
description: 了解使用编辑器或设备门户将混合现实 Unreal 应用部署到 HoloLens 2 所需了解的一切内容。
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal，Unreal Engine 4，UE4，HoloLens，HoloLens 2，混合现实，部署到设备，PC，文档，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
appliesto:
- HoloLens 2
ms.openlocfilehash: d6df3f9af21a0759c98306c28696d21eac7687b92d3cb74a9cd9948122cbcbcc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226631"
---
# <a name="deploy-to-device-in-unreal"></a>在 Unreal 中部署到设备

可通过两种方法将 Unreal 应用程序部署到 HoloLens 2：
* 直接从 Unreal 编辑器
* 作为通过设备门户上传的包

这两个选项都要求您将 HoloLens 设置为使用[设备门户](../platform-capabilities-and-apis/using-the-windows-device-portal.md)进行开发。

## <a name="deploying-to-device-from-the-unreal-editor"></a>从 Unreal 编辑器部署到设备

1. 选择 " **启动** " 按钮旁边的下拉箭头。 最初，HoloLens 设备选项将显示为灰色。

![启动下拉选项](images/unreal/launch-dropdown.png)

2. 打开 **Device Manager** ，请注意，HoloLens 不会自动显示在设备列表中。

3. 展开 " **添加未列出的设备** " 部分。

4. 选择 " **HoloLens** 作为 **平台**。

5. 输入设备的 IP 地址和端口信息，用冒号分隔作为设备标识符。 例如，当通过 USB) 连接时 ("127.0.0.1： 10080"。 使用设备门户的用户名和密码凭据。

6. 点击 " **添加** " 并关闭 "设备管理器"。
    * 如果出现错误，如地址或用户凭据错误，则会在输出日志中打印一条消息。

![添加未列出的设备](images/unreal/add-unlisted-device.png)

7. 再次选择 "**启动**" 按钮旁的下拉箭头，此时应会看到刚才添加的 HoloLens 设备。 选择要生成并部署到 HoloLens HoloLens 设备。

>[!NOTE]
>构建设备可能需要重新编译着色器 (尤其是在第一次运行) 上，这可能需要一些时间。 不要让设备进入睡眠状态，直到应用程序运行 (可能需要) 。 否则，着色器编译将失败！

## <a name="deploying-to-device-via-device-portal"></a>通过设备门户部署到设备

可在 [Unreal 教程系列](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)中找到有关打包和部署应用的详细说明。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们的 Unreal 开发旅程，就是在部署阶段。 在此处，你可以继续添加高级服务：

> [!div class="nextstepaction"]
> [高级服务](unreal-development-overview.md#5-adding-services)

你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#4-streaming-and-deploying-to-a-device)。
