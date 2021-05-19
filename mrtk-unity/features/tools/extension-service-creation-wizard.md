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
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="cdd68-104">扩展服务创建向导</span><span class="sxs-lookup"><span data-stu-id="cdd68-104">Extension service creation wizard</span></span>

<span data-ttu-id="cdd68-105">从单一状态转换到服务可能很困难。</span><span class="sxs-lookup"><span data-stu-id="cdd68-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="cdd68-106">此向导可以通过使开发人员能够使用 (创建新服务来补充其他文档和示例代码) 与创建新的 MonoBehaviour 脚本大致相同。</span><span class="sxs-lookup"><span data-stu-id="cdd68-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="cdd68-107">若要了解如何从头开始创建服务， [请参阅构建已](../../configuration/mixed-reality-configuration-guide.md) 注册服务服务指南 (即将推出) 。</span><span class="sxs-lookup"><span data-stu-id="cdd68-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="cdd68-108">启动向导</span><span class="sxs-lookup"><span data-stu-id="cdd68-108">Launching the wizard</span></span>

<span data-ttu-id="cdd68-109">从主菜单启动向导 **：MixedRealityToolkit/Utilities/Create Extension Service** - 然后，向导将介绍生成服务脚本、接口和配置文件类的过程。</span><span class="sxs-lookup"><span data-stu-id="cdd68-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="cdd68-110">编辑服务脚本</span><span class="sxs-lookup"><span data-stu-id="cdd68-110">Editing your service script</span></span>

<span data-ttu-id="cdd68-111">默认情况下，将在 文件夹中生成新的脚本 `MixedRealityToolkit.Generated/Extensions` 资产。</span><span class="sxs-lookup"><span data-stu-id="cdd68-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="cdd68-112">完成向导后，导航到此处并打开新的服务脚本。</span><span class="sxs-lookup"><span data-stu-id="cdd68-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="cdd68-113">生成的服务脚本包括一些类似于新 MonoBehaviour 脚本的提示。</span><span class="sxs-lookup"><span data-stu-id="cdd68-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="cdd68-114">它们可让你了解在何处初始化和更新服务。</span><span class="sxs-lookup"><span data-stu-id="cdd68-114">They will let you know where to initialize and update your service.</span></span>

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

<span data-ttu-id="cdd68-115">如果选择在向导中注册服务，则你只要编辑此脚本，服务就会自动更新。</span><span class="sxs-lookup"><span data-stu-id="cdd68-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="cdd68-116">否则，可以在此处[阅读有关注册新服务。](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="cdd68-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
