---
title: 安装 Maquette
description: 了解如何在 VSCode 中安装和配置 Maquette。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality，Maquette，原型设计，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935329"
---
# <a name="installing-maquette"></a>安装 Maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![徽标 ](../images/MaquetteIcon.png) MaquetteScript 安装

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
MaquetteScript 开发主要在 VSCode 内完成。 MaquetteScript 可以从文件中包含的脚本运行 `.mqjs` ，也可以通过特殊的 VSCode 扩展接口运行。 VSCode 和 Maquette 之间的集成可通过 MaquetteScript VSCode 扩展来实现扩展接口。

## <a name="installing-the-vscode-extension"></a>安装 VSCode 扩展

* 下载并安装 [VSCode](https://code.visualstudio.com)。 

Maquette javascript 扩展位于 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)中。

* [为扩展运行安装过程](vscode:extension/ms-maquette.vscode-maquette-javascript)。

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>启用脚本

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

若要在预发布期间使脚本可访问：

* 将名为的文件放 `scripting.enabled` 在 Maquette 的用户文档目录中： `~/Documents/Maquette/Settings` 。

安装之后，出于安全考虑，默认情况下将禁用脚本。

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* 若要启用脚本的执行，请在助理窗口的主选项卡或 json 设置文件中打开它。

![在 VS Code 中启用脚本](images/IntroductionEnableScripting.png)


