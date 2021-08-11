---
title: 编程概述
description: 了解如何使用脚本访问 Maquette 对象和接口。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality，Maquette，原型，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
ms.openlocfilehash: 969a4aedb60d947782acb41742b33f275e7c841c1989144b586b0329db3c3b57
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197871"
---
# <a name="programming-overview"></a>编程概述

<!-- TODO(Harrison): Need consolidated logo with text -->

![徽标](../images/MaquetteIcon.png) 编程概述

Microsoft Maquette 使用 JavaScript (ECMAScript 5.1，其中包含基于 [Jint](https://github.com/sebastienros/jint) 解释器的扩展) 。 此扩展 `.mqjs` 用于将 Maquette javascript 文件与普通 javascript 区分开来。

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Maquette 对象和接口可通过对象访问和编写脚本 `Maquette` 。 Maquette 的 API 参考中提供了有关 Maquette 对象和接口的文档。

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript 是新的添加项，在 flux 中，因此需要进行更改。 即将推出更详细的文档和更新。

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>关于脚本编写

* 待定-聚焦为示例/教程的脚本
  * 2x 图像/标题–链接到聚焦页

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>MaquetteScript 入门

* Mqjs 与 .JS
* 编程模型
  * 编辑与运行
* 指向编程工作流的链接
* 链接到共享结果

## <a name="programming-workflow"></a>编程工作流

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* 脚本操作
* 调试器操作
* 调试循环
* 复制/粘贴代码？

## <a name="running-mqjs-scripts"></a>正在运行 mqjs 脚本

<!-- TODO(Stefan): Need screenshot -->
若要运行 MaquetteScript 文件，请使用 Maquette 的随附窗口，并打开 "脚本" 选项卡来查找脚本。

> [!NOTE] 
> 某些选项将不起作用，因为我们尚未提供这些脚本。

## <a name="vscode-editor-workflow"></a>VSCode 编辑器工作流

若要从 VSCode 中评估 Maquette 中的脚本，用户需要知道两个命令：

   `CTRL-5` 计算光标所在的选定文本或整行。 

   `CTRL-SHIFT-5` 计算整个文件。

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
文本将发送到 Maquette，在 JavaScript 环境中计算，并将结果发送回 VSCode 的输出控制台。 这可用作复制 (读取-eval-) 。

## <a name="example-first-step"></a>示例第一步

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
将以下代码复制到 VSCode 中的文件：

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
选择代码或部分内容，然后单击 " `CTRL-5` 执行"。 这会创建一个多维数据集，将其放置在您的上方，并更改其颜色。

还可以通过扩展查找更多示例。

## <a name="sharing-results"></a>共享结果

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
如何在用户/团队之间共享
* 文档目录中的 Zip 项目
* 将项目复制到文件共享
* 将团队共享提交的文件位置添加到 Maquette 团队

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* 包括，在其他位置引用相对/绝对路径的代码，模块
* 库?
* 运行时支持
* 未解析的外部-当条目丢失/崩溃时的行为
* 能否添加/编辑/观察与特定对象关联的脚本？
  * 我们可以将此脚本复制/粘贴到其他位置吗？
  * 什么是对象属性？
  * 在我的场景中命名对象？ )  (重命名脚本
  * 与对象关联的脚本的此关键字或自关键字
  * 如果我右键单击某个对象，则可以查看与其关联的代码 (及其所有层次结构) 
  * 能否在 UI 中进行选择，并在 VSCode 中将其置于代码中？
  * 正在脚本源文件中将与对象 "一起" 关联的代码保留在一起？
  * 在单击对象时将其置于对象上？ 在 VR 和主选项卡中？
* 安全问题
* 测试–可能是待定，但我们可以通过脚本推荐视频或帧捕获
* 如果有 bug 报告机制，我们可能会通过脚本为其他 (？ ) .。。然后
* 部署-如何 "共享" 结果，包为 EXE
* 运行/控制演示或 spectating/监视
* 播放机模式
* 我们可能会提供有关如何使 "组件" 共享的段？  (可能是 tbd) 
  * #Include 吗？ 这将处理纯 JS I 假设，但可能存在命名空间冲突。
  * 对于 maquette 要合并某个其他 maquette 和命名对象以匹配 JS 代码，是否可以执行任何操作？
