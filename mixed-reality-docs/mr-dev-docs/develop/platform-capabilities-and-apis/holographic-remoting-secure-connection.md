---
title: 使用全息远程处理建立安全连接
description: 本页说明如何在使用全息远程处理时建立安全的加密连接。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677042"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>使用全息远程处理建立安全连接

>[!IMPORTANT]
>本指南特定于 HoloLens 2 上的全息远程处理。

本页说明如何在使用全息远程处理时建立安全的加密连接。

当通过不安全的网络（如开放 WiFi 或 internet）将内容流式传输到 HoloLens 2 时，强烈建议使用加密连接。

>[!IMPORTANT]
>即使使用受信任的本地 WiFi，也应考虑使用加密连接。

若要使用加密的连接，则需要同时实现 [自定义播放器](holographic-remoting-create-player.md) 和 [自定义远程应用](holographic-remoting-create-host.md)。

加密是通过使用基础平台 TLS 实现实现的。

## <a name="basics-of-an-encrypted-connection"></a>加密连接的基本信息

需要实现以下对象才能允许证书交换。

>[!TIP]
>可使用 c + +/WinRT. 轻松实现 WinRT 接口 [带有 c + +/WinRT 的作者 api](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis)一章将对此进行详细介绍。

>[!IMPORTANT]
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 包中的包含有关与安全连接相关的 API 的详细文档。

1) 需要实现接口的证书对象 ```ICertificate``` 。

    * 通过方法返回 pfx 证书的二进制内容 ```GetCertificatePfx``` 。 与 .pfx 文件的二进制内容相同。
    * 通过返回证书使用者名称 ```GetSubjectName``` 。
    * 通过返回 pfx 密码 ```GetPfxPassword``` 。 为未受保护的 pfx 返回空字符串。

2) 一个证书提供程序，该提供程序 ```ICertificateProvider``` 在系统通过方法时提供证书来实现接口 ```GetCertificate``` 。

3) 用于实现接口的证书验证程序 ```ICertificateValidator``` 。 它的任务是验证传入的证书。
    * ```PerformSystemValidation``` ```true``` 如果基础平台应验证传入的证书链，则该方法应返回， ```false``` 否则返回。
    * ```ValidateCertificate``` 由客户端上下文调用来请求验证证书。 此方法接受证书链 (第一个证书为 "使用者证书) "、与之建立连接的服务器的名称，以及是否应强制执行吊销检查。 如果已请求基础系统验证，则将提供系统验证结果。 若要继续处理 ```CertificateValidated``` 适当的结果，或者 ```Cancel``` 需要对传递的调用取消验证，则为 ```ICertificateValidationCallback``` 。

而且，若要允许交换安全令牌，需要实现以下对象。

1) 实现接口的身份验证提供程序 ```IAuthenticationProvider``` 。 ```GetToken```客户端上下文调用其方法来请求客户端身份验证的令牌。 若要继续 ```TokenReceived``` 提供身份验证令牌并继续连接过程或取消， ```Cancel``` 需要在传递的上调用该过程 ```IAuthenticationProviderCallback``` 。
2) 实现接口的身份验证接收器 ```IAuthenticationReceiver``` 。 它的任务是验证传入令牌。
    * ```GetRealm```方法应返回身份验证领域的名称。
    * ```ValidateToken```服务器网络上下文调用方法来请求验证客户端身份验证令牌。 若要继续调用 ```ValidationCompleted``` 验证的信号完成，则为; 否则 ```Cancel``` 为拒绝客户端连接。 根据传递给的验证结果，将会对客户端连接进行许可或拒绝 ```ValidationCompleted``` 。 

实现这些对象后， ```ListenSecure``` 需要 ```Listen``` ```ConnectSecure``` ```Connect``` 分别在远程上下文和播放机上下文上调用而不是和而不是。 ```ListenSecure``` 需要额外的证书提供程序和身份验证接收器 ```Listen``` 。 ```ConnectSecure``` 需要额外的身份验证提供程序和证书验证程序 ```Connect``` 。

## <a name="see-also"></a>另请参阅
* [编写全息远程处理远程应用](holographic-remoting-create-host.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)
