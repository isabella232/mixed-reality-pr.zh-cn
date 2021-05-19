---
title: 扩展服务
description: MRTK 中扩展功能的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: a39616a091a3f6800c429dc797ec2f3130e96f40
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144548"
---
# <a name="extension-services"></a><span data-ttu-id="e6d3c-104">扩展服务</span><span class="sxs-lookup"><span data-stu-id="e6d3c-104">Extension services</span></span>

<span data-ttu-id="e6d3c-105">扩展服务是扩展混合现实工具包功能的组件。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="e6d3c-106">这些服务可能由 MRTK 或其他方提供。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="e6d3c-107">创建扩展服务</span><span class="sxs-lookup"><span data-stu-id="e6d3c-107">Creating an extension service</span></span>

<span data-ttu-id="e6d3c-108">创建扩展服务的最高效方法就是使用扩展 [服务创建向导](../tools/extension-service-creation-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="e6d3c-109">若要启动扩展服务创建向导，请选择"创建扩展服务 **>实用工具>混合现实工具包"。**</span><span class="sxs-lookup"><span data-stu-id="e6d3c-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![扩展服务创建向导](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="e6d3c-111">向导自动创建服务组件，并确保正确的接口继承。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![扩展服务创建向导创建的组件](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="e6d3c-113">在 MRTK 版本 2.0.0 中，扩展服务向导中存在需要生成服务检查器和服务配置文件的问题。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="e6d3c-114">有关详细信息，请参阅问题[5654。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654)</span><span class="sxs-lookup"><span data-stu-id="e6d3c-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="e6d3c-115">向导完成后，可以实现服务功能。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="e6d3c-116">注册扩展服务</span><span class="sxs-lookup"><span data-stu-id="e6d3c-116">Registering an extension service</span></span>

<span data-ttu-id="e6d3c-117">若要由应用程序访问，需要向混合现实工具包注册新的扩展服务。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="e6d3c-118">扩展服务创建向导可用于注册服务。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-118">The extension service creation wizard can be used to register the service.</span></span>

![扩展服务创建向导注册](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="e6d3c-120">也可使用混合现实工具包配置检查器手动注册该服务。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![手动扩展服务注册](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="e6d3c-122">如果扩展服务使用配置文件，请确保在检查器中指定该配置文件。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![已配置扩展服务](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="e6d3c-124">还可以调整组件名称和优先级。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="e6d3c-125">访问扩展服务</span><span class="sxs-lookup"><span data-stu-id="e6d3c-125">Accessing an extension service</span></span>

<span data-ttu-id="e6d3c-126">扩展服务是使用代码中的来访问的， [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="e6d3c-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="e6d3c-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6d3c-127">See also</span></span>

- [<span data-ttu-id="e6d3c-128">系统、扩展服务和数据访问接口</span><span class="sxs-lookup"><span data-stu-id="e6d3c-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="e6d3c-129">扩展服务创建向导</span><span class="sxs-lookup"><span data-stu-id="e6d3c-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="e6d3c-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="e6d3c-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="e6d3c-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="e6d3c-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
