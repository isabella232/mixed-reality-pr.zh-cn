---
title: 扩展服务
description: MRTK 中扩展功能的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f8f7b8dbac0355c226e4bbfae39246e5c1c58f69
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176276"
---
# <a name="extension-services"></a><span data-ttu-id="09ada-104">扩展服务</span><span class="sxs-lookup"><span data-stu-id="09ada-104">Extension services</span></span>

<span data-ttu-id="09ada-105">扩展服务是扩展混合现实服务功能的组件Toolkit。</span><span class="sxs-lookup"><span data-stu-id="09ada-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="09ada-106">这些服务可能由 MRTK 或其他方提供。</span><span class="sxs-lookup"><span data-stu-id="09ada-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="09ada-107">创建扩展服务</span><span class="sxs-lookup"><span data-stu-id="09ada-107">Creating an extension service</span></span>

<span data-ttu-id="09ada-108">创建扩展服务的最高效方法就是使用扩展 [服务创建向导](../tools/extension-service-creation-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="09ada-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="09ada-109">若要启动扩展服务创建向导，请选择"创建扩展服务 **Toolkit >实用工具>混合现实"**。</span><span class="sxs-lookup"><span data-stu-id="09ada-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![扩展服务创建向导](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="09ada-111">向导自动创建服务组件，并确保正确的接口继承。</span><span class="sxs-lookup"><span data-stu-id="09ada-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![扩展服务创建向导创建的组件](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="09ada-113">在 MRTK 版本 2.0.0 中，扩展服务向导中存在需要生成服务检查器和服务配置文件的问题。</span><span class="sxs-lookup"><span data-stu-id="09ada-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="09ada-114">有关详细信息，请参阅问题[5654。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654)</span><span class="sxs-lookup"><span data-stu-id="09ada-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="09ada-115">向导完成后，可以实现服务功能。</span><span class="sxs-lookup"><span data-stu-id="09ada-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="09ada-116">注册扩展服务</span><span class="sxs-lookup"><span data-stu-id="09ada-116">Registering an extension service</span></span>

<span data-ttu-id="09ada-117">若要由应用程序访问，需要将新的扩展服务注册到混合现实Toolkit。</span><span class="sxs-lookup"><span data-stu-id="09ada-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="09ada-118">扩展服务创建向导可用于注册服务。</span><span class="sxs-lookup"><span data-stu-id="09ada-118">The extension service creation wizard can be used to register the service.</span></span>

![扩展服务创建向导注册](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="09ada-120">也可使用混合现实配置检查器手动注册Toolkit服务。</span><span class="sxs-lookup"><span data-stu-id="09ada-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![手动扩展服务注册](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="09ada-122">如果扩展服务使用配置文件，请确保在检查器中指定该配置文件。</span><span class="sxs-lookup"><span data-stu-id="09ada-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![配置的扩展服务](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="09ada-124">还可以调整组件名称和优先级。</span><span class="sxs-lookup"><span data-stu-id="09ada-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="09ada-125">访问扩展服务</span><span class="sxs-lookup"><span data-stu-id="09ada-125">Accessing an extension service</span></span>

<span data-ttu-id="09ada-126">在代码中，使用 访问扩展服务， [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="09ada-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="09ada-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09ada-127">See also</span></span>

- [<span data-ttu-id="09ada-128">系统、扩展服务和数据访问者</span><span class="sxs-lookup"><span data-stu-id="09ada-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="09ada-129">扩展服务创建向导</span><span class="sxs-lookup"><span data-stu-id="09ada-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="09ada-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="09ada-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="09ada-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="09ada-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
