---
title: 扩展服务创建向导
description: 有关将单一实例转换为服务的向导的文档 MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 4be9a58c7d63ab3bc93bcc326a90260cf6a3366b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176616"
---
# <a name="extension-service-creation-wizard"></a>扩展服务创建向导

使从单一实例到服务的转换变得很困难。 此向导可以通过使开发人员创建新的服务并 () 大致与创建新的 MonoBehaviour 脚本相比，来补充我们的其他文档和示例代码。 若要了解有关从头开始创建服务的信息，请参阅 [如何构建注册服务](../../configuration/mixed-reality-configuration-guide.md) (即将) 。

## <a name="launching-the-wizard"></a>启动向导

从主菜单启动向导： **MixedRealityToolkit/公用事业/Create Extension Service** -该向导将引导您完成生成服务脚本、接口和配置文件类的过程。

## <a name="editing-your-service-script"></a>编辑服务脚本

默认情况下，新的脚本资产将在文件夹中生成 `MixedRealityToolkit.Generated/Extensions` 。 完成向导后，请在此处导航并打开新的服务脚本。

生成的服务脚本包含类似于新 MonoBehaviour 脚本的一些提示。 他们会告诉你如何初始化和更新服务。

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

如果在向导中选择了 "注册服务"，则只需编辑此脚本，你的服务就会自动更新。 否则，可以在此处阅读有关 [注册新服务](../../configuration/mixed-reality-configuration-guide.md)的信息。
