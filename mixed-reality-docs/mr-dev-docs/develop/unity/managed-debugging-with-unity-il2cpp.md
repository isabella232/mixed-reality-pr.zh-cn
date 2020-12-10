---
title: 使用 Unity IL2CPP 进行托管调试
description: 本文介绍如何在 Unity IL2CPP UWP 项目上运行托管调试器。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity，visual studio，调试，il2cpp，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，UWP
ms.openlocfilehash: 4b21e4888e467e6bd5f1938024a1b8312d8ecbcb
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010238"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>使用 Unity IL2CPP 进行托管调试

按照以下步骤将托管调试器附加到适用于 HoloLens 和 HoloLens 2 的 Unity IL2CPP UWP 生成。

1. 你需要位于支持 [多播](https://en.wikipedia.org/wiki/Multicast)的网络上。
2. 请参阅 **UWP 发布设置功能** 并查看 **InternetClientServer** 和 **PrivateNetworkClientServer**：

    ![UWP 发布设置功能](images/il2cpp-debugging-capabilities.png)

3. 配置 Unity UWP 生成设置：
    - 开发生成
    - 脚本调试
    - 等待托管调试器 (可选) 

    ![UWP 生成设置](images/il2cpp-debugging-build.png)

4. 在 Unity 中构建。
5. 生成 Visual Studio 解决方案并将其部署到设备。 你应以 " **调试** " 或 " **发布** " 配置进行构建。 **主** 配置将禁用 Unity 探查器，并可防止优化调试。 （可选）在解决方案的 appxmanifest.xml 中的功能列表中验证 **Internet (客户端 & 服务器)** 和 **专用网络 (客户端 & 服务器)** 。
6. 确保你的设备已连接到与你的电脑相同的网络，并在设备上启动该应用。
7. 请确保设备 **未** 通过 USB 连接到你的电脑。
8. 双击 Unity 中的一个脚本，并中转到 Visual Studio 解决方案，打开它以查看和编辑。
9. 调试-> 附加 Unity 调试器。

    ![附加 Unity 调试器](images/il2cpp-debugging-attach.png)

10. 在列表中选择你的设备，然后单击 "确定" 以附加。

    ![设备列表](images/il2cpp-debugging-machines.png)
