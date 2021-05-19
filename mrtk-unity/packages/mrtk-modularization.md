---
title: MRTK 模块化
description: 介绍 MRTK 中的组件化。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 04b2e6155e591a918b95aed20961a0450afe5f43
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144424"
---
# <a name="mixed-reality-toolkit-componentization"></a>混合现实工具包组件化

混合现实工具包 v2 的最新功能之一是组件化改进。 只要有可能，单个组件就会独立于基础的所有核心层。

## <a name="minimized-dependencies"></a>最小化依赖项

MRTK v2 特意开发为模块化，并最大程度地减少了系统服务之间的依赖关系 (例如：空间感知) 。

由于某些系统服务的性质 (例如： input 和 teleportation) ，因此存在少量依赖项。

尽管服务预计需要一个或多个数据提供程序组件，但它们之间没有直接链接。 这同样适用于 (ex：用户界面组件) 的 SDK 功能。

## <a name="component-communication"></a>组件通信

为了确保组件之间没有直接链接，MRTK v2 利用接口在服务、数据提供程序和应用程序代码之间进行通信。 这些接口在中定义，所有通信都通过混合现实工具包核心组件进行路由。

![通过接口使用空间感知系统](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>最大程度减少 MRTK 导入占用量

此时，MRTK 将导入为单个基础包， (忽略) 示例包，这是一个完全可选的包。 您可以通过手动对导入的文件进行处理来使此需求量更小，但这是一个高度手动的过程，该过程没有定义完善的指南。

在导入基础包的过程中，可以取消选中任意项。 但是，不建议在开发的早期阶段执行此操作，因为它可能会中断功能。 在确定应用的最终功能集后，可以在以下文件夹中执行删除不需要的提供程序和服务：

- MRTK/服务
- MRTK/提供程序
- MRTK/SDK/功能

> [!NOTE]
> MRTK v2.x **_需要_** Assets/MRTK/Core 文件夹的内容。

## <a name="upcoming-features"></a>即将推出的功能

### <a name="application-architecture"></a>应用程序体系结构

MRTK 将支持使用各种体系结构生成应用程序，包括：

- [MixedRealityToolkit 服务定位符](#mixedrealitytoolkit-service-locator)
- [单个服务](#individual-service-components)
- [自定义服务定位符](#custom-service-locator)
- [混合体系结构](#hybrid-architecture)

选择应用程序体系结构时，必须考虑设计灵活性和应用程序性能。 此处所述的体系结构不一定适合每个应用程序。

#### <a name="mixedrealitytoolkit-service-locator"></a>MixedRealityToolkit 服务定位符

MRTK 启用 (，并自动) 应用程序场景以使用默认 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 服务定位器组件。 此组件支持通过配置检查器配置 MRTK 系统和数据访问接口，并管理组件生命周期和核心行为 (例如：何时更新) 。

所有系统都表示在核心配置检查器中，无论它们是否在项目中存在或启用。 有关详细信息， [请参阅混合现实](../configuration/mixed-reality-configuration-guide.md) 配置指南。

#### <a name="individual-service-components"></a>单个服务组件

一些开发人员已表示希望将单个服务组件包括到应用程序场景层次结构中。 若要启用此用法，服务需要封装在自定义注册机构中，或者需要自行注册/自我管理。

自注册服务将实现 并 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 注册自身，以便应用程序代码可以通过注册表发现服务实例。

自我管理服务可以作为场景层次结构中的单一对象实现。 此对象将提供 和 实例属性，应用程序代码可以使用该属性直接访问服务功能。

#### <a name="custom-service-locator"></a>自定义服务定位符

某些开发人员已请求能够创建自定义服务定位器组件。 自定义服务定位器将实现 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 接口，并管理活动服务的生命周期和核心行为。

#### <a name="hybrid-architecture"></a>混合体系结构

MRTK 将支持混合体系结构，开发人员可在其中根据需要合并以前的方法。 例如，开发人员可以先从服务 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 定位符开始，然后添加自注册服务。

> [!NOTE]
> 选择混合体系结构时，必须注意任何重复的工作，例如 (多个组件获取控制器) 。
