---
title: 扩展服务创建向导
description: 有关从单一文件转换到服务 MRTK 的向导的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 83797a9d6d465a150406b27162a5e84c157567f1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143545"
---
# <a name="extension-service-creation-wizard"></a>扩展服务创建向导

从单一状态转换到服务可能很困难。 此向导可以通过使开发人员能够使用 (创建新服务来补充其他文档和示例代码) 与创建新的 MonoBehaviour 脚本大致相同。 若要了解如何从头开始创建服务， [请参阅构建已](../../configuration/mixed-reality-configuration-guide.md) 注册服务服务指南 (即将推出) 。

## <a name="launching-the-wizard"></a>启动向导

从主菜单启动向导 **：MixedRealityToolkit/Utilities/Create Extension Service** - 然后，向导将介绍生成服务脚本、接口和配置文件类的过程。

## <a name="editing-your-service-script"></a>编辑服务脚本

默认情况下，将在 文件夹中生成新的脚本 `MixedRealityToolkit.Generated/Extensions` 资产。 完成向导后，导航到此处并打开新的服务脚本。

生成的服务脚本包括一些类似于新 MonoBehaviour 脚本的提示。 它们可让你了解在何处初始化和更新服务。

```csharp
namespace Microsoft.MixedReality.Toolkit.Extensions
{
    [MixedRealityExtensionService(SupportedPlatforms.WindowsStandalone|SupportedPlatforms.MacStandalone|SupportedPlatforms.LinuxStandalone|SupportedPlatforms.WindowsUniversal)]
    public class NewService : BaseExtensionService, INewService, IMixedRealityExtensionService
    {
        private NewServiceProfile newServiceProfile;

        public NewService(IMixedRealityServiceRegistrar registrar,  string name,  uint priority,  BaseMixedRealityProfile profile) : base(registrar, name, priority, profile) 
        {
            newServiceProfile = (NewServiceProfile)profile;
        }

        public override void Initialize()
        {
            // Do service initialization here.
        }

        public override void Update()
        {
            // Do service updates here.
        }
    }
}
```

如果选择在向导中注册服务，则你只要编辑此脚本，服务就会自动更新。 否则，可以在此处[阅读有关注册新服务。](../../configuration/mixed-reality-configuration-guide.md)
