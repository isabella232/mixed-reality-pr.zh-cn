---
title: 使用 Unity 进行托管调试
description: 本文介绍如何在 Unity IL2CPP UWP 项目上运行托管调试器。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity， Visual Studio， 调试， il2cpp， HoloLens， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， UWP
ms.openlocfilehash: 92b730768b6402b356e550d8f01d85e654832aef1ac382d8f992df615a9ce1b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196527"
---
# <a name="managed-debugging-with-unity"></a>使用 Unity 进行托管调试

按照以下步骤将托管调试器附加到 Unity IL2CPP UWP 内部版本，HoloLens HoloLens 2。

1. 你需要位于支持多播 [的网络上](https://en.wikipedia.org/wiki/Multicast)。
2. 转到 **"UWP 发布设置功能"，并** 选中 **"InternetClientServer"** 和 **"PrivateNetworkClientServer"：**

    ![UWP 发布设置功能](images/il2cpp-debugging-capabilities.png)

3. 配置 Unity UWP 生成设置：
    - 开发生成
    - 脚本调试
    - 等待托管调试器 (可选) 

    ![UWP 生成设置](images/il2cpp-debugging-build.png)

4. 在 Unity 中生成。
5. 从解决方案生成Visual Studio部署到设备。 应该使用"调试" **或** "发布" **配置进行** 生成。 主 **配置** 禁用 Unity 探查器，并可能阻止最佳调试。 （可选）在解决方案中 Package.appxmanifest 的功能列表中，验证 Internet (客户端 & **Server)** 和专用网络 (客户端 & 服务器 **) 。**
6. 确保设备已连接到与电脑相同的网络，并启动设备上的应用。
7. 确保设备 **未通过** USB 连接到电脑。
8. 在 Unity 中双击其中一个脚本，并转到打开Visual Studio并编辑的脚本解决方案。
9. 调试 ->附加 Unity 调试器。

    ![附加 Unity 调试器](images/il2cpp-debugging-attach.png)

10. 在列表中选择设备，然后单击"确定"进行附加。

    ![设备列表](images/il2cpp-debugging-machines.png)

## <a name="see-also"></a>另请参阅 

* [C# 调试](/visualstudio/get-started/csharp/tutorial-debugger)
