---
title: 扩展服务
description: MRTK 中扩展功能的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 0f9f30bb7d2d44cef828b79bc916d933a6355dbb1068b09e73317d1c977ef45a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186982"
---
# <a name="extension-services"></a>扩展服务

扩展服务是扩展混合现实服务功能的组件Toolkit。 这些服务可能由 MRTK 或其他方提供。

## <a name="creating-an-extension-service"></a>创建扩展服务

创建扩展服务的最高效方法就是使用扩展 [服务创建向导](../tools/extension-service-creation-wizard.md)。
若要启动扩展服务创建向导，请选择"创建扩展服务 **Toolkit >实用工具>混合现实"**。

![扩展服务创建向导](../images/extension-wizard/ExtensionServiceCreationWizard.png)

向导自动创建服务组件，并确保正确的接口继承。

![扩展服务创建向导创建的组件](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> 在 MRTK 版本 2.0.0 中，扩展服务向导中存在需要生成服务检查器和服务配置文件的问题。 有关详细信息，请参阅问题[5654。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654)

向导完成后，可以实现服务功能。

## <a name="registering-an-extension-service"></a>注册扩展服务

若要由应用程序访问，需要将新的扩展服务注册到混合现实Toolkit。

扩展服务创建向导可用于注册服务。

![扩展服务创建向导注册](../images/extension-wizard/ExtensionServiceWizardRegister.png)

也可使用混合现实配置检查器手动注册Toolkit服务。

![手动扩展服务注册](../images/profiles/RegisterExtensionService.png)

如果扩展服务使用配置文件，请确保在检查器中指定该配置文件。

![配置的扩展服务](../images/profiles/ConfiguredExtensionService.png)

还可以调整组件名称和优先级。

## <a name="accessing-an-extension-service"></a>访问扩展服务

在代码中，使用 访问扩展服务， [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 如以下示例所示。

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>另请参阅

- [系统、扩展服务和数据访问者](../../architecture/systems-extensions-providers.md)
- [扩展服务创建向导](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
