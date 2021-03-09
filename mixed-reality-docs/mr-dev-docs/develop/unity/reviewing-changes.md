---
title: 授权项目更改
description: 了解如何授权对面向 HoloLens 和 VR 开发的混合现实功能工具进行项目更改。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230753"
---
# <a name="authorizing-project-changes"></a>授权项目更改

在修改 Unity 项目之前，需要查看和批准对清单和项目文件所做的更改：

![请求授权](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>file:///

可以在左侧的“清单”列中查看建议的清单更改。 该内容与将写入项目清单 (Packages/manifest.json) 的内容完全相同：

![清单预览](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>要复制到项目中的文件

右侧的“要复制到项目中的文件”部分列出了将复制到 Unity 项目中的特定功能包文件：

![包含要复制的文件的清单预览](images/FilesToCopy.png)

## <a name="compare-manifests"></a>比较清单

可通过选择“比较”来查看所有建议更改的详细并排比较：

![比较清单](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>批准更改

建议的更改获得批准后，所列文件将被复制到 Unity 项目中，并将更新清单，使其包含对这些文件的引用。

> [!NOTE]
> 应将功能包 (*.tgz) 文件添加到源代码管理。 它们使用相对路径进行引用，使开发团队能够轻松共享功能和清单更改。

 在修改过程中，将对当前 manifest.json 文件进行备份。

> [!IMPORTANT]
> 查看清单备份时，最早的备份将称为 manifest.json.backup。 后续的新备份将使用从零 (0) 开始的数字值进行批注。

## <a name="going-back-to-the-previous-step"></a>返回到上一步骤

如需对功能选择进行更改，请单击“返回”，返回到[导入](importing-features.md)步骤。

## <a name="see-also"></a>另请参阅

- [欢迎使用混合现实功能工具](welcome-to-mr-feature-tool.md)
- [导入选定包](importing-features.md)
