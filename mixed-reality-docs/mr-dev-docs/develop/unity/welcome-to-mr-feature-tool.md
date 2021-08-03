---
title: 欢迎使用混合现实功能工具
description: 了解面向 HoloLens 和 VR 开发的混合现实功能工具的基础知识。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, unity, visual studio, 工具包, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 安装, Windows, HoloLens, 仿真器, unreal, openxr
ms.openlocfilehash: 1244f9cd4da0d6ae0b5c6f92698f87f0edd812e2
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757086"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>欢迎使用混合现实功能工具

![混合现实功能工具横幅图像](images/feature-tool-banner.jpg)

> [!IMPORTANT]
> 混合现实功能工具目前仅适用于 Unity。 如果是在 Unreal 中进行开发，请参阅[工具安装](../install-the-tools.md)文档。

混合现实功能工具是开发人员发现、更新混合现实功能包并将其添加到 Unity 项目中的一种新方式。 你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。 如果以前从未使用过清单文件，则它是包含所有项目包的 JSON 文件。 验证所需的包后，混合现实功能工具会将它们下载到所选的项目中。

## <a name="system-requirements"></a>系统要求

在运行混合现实功能工具之前，需要具备以下项：

* [.NET 5.0 运行时](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> 混合现实功能工具目前仅可在 Windows 上运行，但即将推出 MacOS 支持！

## <a name="download"></a>下载

设置环境后：

* 请从 Microsoft 下载中心[下载混合现实功能工具的最新版本](https://aka.ms/MRFeatureTool)。
* 下载完成后，解压缩文件并将其保存到桌面
    * 建议创建可执行文件的快捷方式，以便更快地进行访问

> [!NOTE]
> 如果您是刚开始使用 Unity 包管理器，请遵循我们的 [UPM 说明](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager)。

## <a name="changes-in-this-release"></a>此版本中的更改

版本 1.0.2103 Beta 包含以下修补程序：

* 改进了下载错误检测。
* 更新了如何编写清单以避免无法正确更新。
* 已从项目清单中的文件路径中删除 Escpaing。

此版本中添加了以下功能：

* 功能目录现在会缓存。 若要检查新功能和更新，请使用“发现”中的刷新按钮。
* 将项目选择从“导入”步骤移动到“发现”之前。
* 可用包按项目的指定 Unity 版本进行筛选。
* 发现视图现在会显示当前安装的包。

## <a name="1-getting-started"></a>1.入门

从可执行文件启动混合现实功能工具，此操作将在首次启动时显示起始页：

![开始使用](images/FeatureToolStart.png)

从起始页，你可以：

* [使用齿轮图标按钮配置](configuring-feature-tool.md)工具设置
* 使用问号按钮启动默认 web 浏览器并显示文档
* 选择“开始”，开始发现功能包

## <a name="2-selecting-your-unity-project"></a>2. 选择 Unity 项目

为了确保您项目的 Unity 版本支持所有发现的功能，第一步是使用省略号按钮（位于项目路径字段右侧）将混合现实功能工具指向您的项目。

![选择 Unity 项目](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> 浏览 Unity 项目文件夹时显示的对话框包含“_”作为文件名。 文件名必须有一个值才能使文件夹被选中。

找到项目的文件夹后，单击“打开”按钮返回到混合现实功能工具。

> [!IMPORTANT]
> 混合现实功能工具执行验证以确保它已定向到 Unity 项目文件夹。 该文件夹必须包含 `Assets`、`Packages` 和 `Project Settings` 文件夹。

## <a name="3-discovering-and-acquiring-feature-packages"></a>3. 发现并获取功能包

> [!NOTE]
> 版本 1.0.2103 Beta 现在每次访问服务器时都会缓存功能目录内容。 通过此更改，可以快速访问可用功能，但却只能显示绝对最新的数据。 若要更新目录，请使用“刷新”按钮。

功能按类别分组，方便查找。 例如，“混合现实工具包”类别具有几个可供选择的功能：

![发现和获取](images/FeatureToolDiscovery.png)

当混合现实功能工具识别到以前导入的功能时，它针对每个功能显示一条通知消息。

![已导入功能的通知](images/feature-tool-imported-note.png)


做出选择后，选择“获取功能”，从目录中获取所有所需的包。 有关详细信息，请参阅[发现并获取功能](discovering-features.md)。

## <a name="4-importing-feature-packages"></a>4. 导入功能包

获取完毕后，将显示完整的包集，以及所需依赖项的列表。 如果需要更改任何功能或包选择，则可以执行以下操作：

![导入程序包](images/FeatureToolImport.png)

强烈建议使用“验证”按钮，确保 Unity 项目可以成功导入所选功能。 验证完成后，你将看到一个弹出对话框，其中包含一条成功消息或已识别出的问题的列表。

选择“导入”继续。

> [!NOTE]
> 单击“导入”按钮后，如果有任何问题仍存在，则将显示一条简单消息。 建议单击“否”，并使用“验证”按钮来查看和解决问题。

有关详细信息，请参阅[导入功能](importing-features.md)。

## <a name="5-reviewing-and-approving-project-changes"></a>5. 查看和批准项目更改

最后一步是检查并批准对清单和项目文件的建议更改：

* 建议的清单更改显示在左侧
* 要添加到项目中的文件显示在右侧
* “比较”按钮允许并排查看当前清单和建议的更改

![授权](images/FeatureToolApprovalRequest.png)

有关详细信息，请参阅[查看和批准项目修改](reviewing-changes.md)。

## <a name="6-project-updated"></a>6. 已更新项目

更改建议获得批准后，目标 Unity 项目会进行相应更新以引用所选的混合现实功能。

![已更新项目](images/FeatureToolProjectUpdated.png)

Unity 项目的 Packages 文件夹现在具有一个包含功能包文件的 MixedReality 子文件夹，并且清单将包含相应的引用 。

返回到 Unity，等待加载新的选定功能，并开始生成！

## <a name="see-also"></a>另请参阅

- [配置功能工具](configuring-feature-tool.md)
- [发现和获取](discovering-features.md)
- [查看功能包详细信息](viewing-package-details.md)
- [导入选定包](importing-features.md)
- [查看和批准项目修改](reviewing-changes.md)