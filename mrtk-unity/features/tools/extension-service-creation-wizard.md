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
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="2af68-104">扩展服务创建向导</span><span class="sxs-lookup"><span data-stu-id="2af68-104">Extension service creation wizard</span></span>

<span data-ttu-id="2af68-105">使从单一实例到服务的转换变得很困难。</span><span class="sxs-lookup"><span data-stu-id="2af68-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="2af68-106">此向导可以通过使开发人员创建新的服务并 () 大致与创建新的 MonoBehaviour 脚本相比，来补充我们的其他文档和示例代码。</span><span class="sxs-lookup"><span data-stu-id="2af68-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="2af68-107">若要了解有关从头开始创建服务的信息，请参阅 [如何构建注册服务](../../configuration/mixed-reality-configuration-guide.md) (即将) 。</span><span class="sxs-lookup"><span data-stu-id="2af68-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="2af68-108">启动向导</span><span class="sxs-lookup"><span data-stu-id="2af68-108">Launching the wizard</span></span>

<span data-ttu-id="2af68-109">从主菜单启动向导： **MixedRealityToolkit/公用事业/Create Extension Service** -该向导将引导您完成生成服务脚本、接口和配置文件类的过程。</span><span class="sxs-lookup"><span data-stu-id="2af68-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="2af68-110">编辑服务脚本</span><span class="sxs-lookup"><span data-stu-id="2af68-110">Editing your service script</span></span>

<span data-ttu-id="2af68-111">默认情况下，新的脚本资产将在文件夹中生成 `MixedRealityToolkit.Generated/Extensions` 。</span><span class="sxs-lookup"><span data-stu-id="2af68-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="2af68-112">完成向导后，请在此处导航并打开新的服务脚本。</span><span class="sxs-lookup"><span data-stu-id="2af68-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="2af68-113">生成的服务脚本包含类似于新 MonoBehaviour 脚本的一些提示。</span><span class="sxs-lookup"><span data-stu-id="2af68-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="2af68-114">他们会告诉你如何初始化和更新服务。</span><span class="sxs-lookup"><span data-stu-id="2af68-114">They will let you know where to initialize and update your service.</span></span>

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

<span data-ttu-id="2af68-115">如果在向导中选择了 "注册服务"，则只需编辑此脚本，你的服务就会自动更新。</span><span class="sxs-lookup"><span data-stu-id="2af68-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="2af68-116">否则，可以在此处阅读有关 [注册新服务](../../configuration/mixed-reality-configuration-guide.md)的信息。</span><span class="sxs-lookup"><span data-stu-id="2af68-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
