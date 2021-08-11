---
title: 应用内购买
description: 了解如何在混合现实应用中使用 2d XAML 视图和股票 Windows 操作系统弹出窗口中进行应用内购买。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 应用内购买，hololens，XAML，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: fbb957d1044a5c76c19691b875de8f9513bfc4b49bc4cb0dbb98d045d615f1a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196145"
---
# <a name="in-app-purchases"></a>应用内购买

HoloLens 中支持应用内购买，但有一些工作需要进行设置。

若要在应用购买功能中使用，你必须：
* 创建 XAML [2d 视图](../design/app-views.md) 以显示为一个石板
* 切换到它以激活放置，这会使沉浸式视图
* 调用 API： await [CurrentApp. RequestProductPurchaseAsync ( "DurableItemIAPName" ) ;](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

此 API 将显示库存 Windows 操作系统弹出窗口，其中显示了应用内购买名称、说明和价格。 然后，用户可以选择 "购买选项"。 操作完成后，应用将需要显示 UI，这允许用户切换回其 [沉浸式视图](../design/app-views.md)。

对于面向基于桌面的 Windows Mixed Reality 沉浸式耳机的应用程序，无需在调用 RequestProductPurchaseAsync API 之前手动切换到 XAML 视图。