---
title: 安装 Maquette
description: 了解如何在 VSCode 中安装和配置 Maquette。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality，Maquette， 原型制作， 混合现实， 虚拟现实， VR， MR， 反馈， 反馈中心， bug
ms.openlocfilehash: c31f461adbe553a5c10e7acfff3037ea0c2b65caf2bbe63bfc234e067a6369e8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214751"
---
# <a name="installing-maquette"></a>安装 Maquette

<!-- TODO(Harrison): Need consolidated logo with text. -->
![徽标 ](../images/MaquetteIcon.png) Maquescript 安装

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
Maquescript 开发主要在 VSCode 中完成。 Maquescript 可以从文件中包含的脚本运行， `.mqjs` 也可通过特殊的 VSCode 扩展接口运行。 VSCode 与 Maquette 之间的集成以启用扩展接口是使用 Maquescript VSCode 扩展完成的。

## <a name="installing-the-vscode-extension"></a>安装 VSCode 扩展

* 下载并安装 [VSCode](https://code.visualstudio.com)。 

Maquette javascript 扩展位于 Visual Studio [Marketplace 中](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)。

* 运行 [扩展 的安装过程](vscode:extension/ms-maquette.vscode-maquette-javascript)。

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>启用脚本

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

若要在预发布期间访问脚本，请执行：

* 将名称为 的文件放在 `scripting.enabled` Maquette 的 Users Documents 目录中 `~/Documents/Maquette/Settings` ：。

安装后，出于安全原因，脚本默认处于禁用状态。

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* 若要启用脚本执行，请打开配套窗口的主选项卡或 json 设置文件。

![在 VS Code](images/IntroductionEnableScripting.png)


