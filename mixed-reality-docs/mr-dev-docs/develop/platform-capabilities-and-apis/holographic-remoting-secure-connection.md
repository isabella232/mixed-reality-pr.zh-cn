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
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a><span data-ttu-id="e2164-104">使用全息远程处理建立安全连接</span><span class="sxs-lookup"><span data-stu-id="e2164-104">Establishing a secure connection with Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="e2164-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="e2164-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="e2164-106">本页说明如何在使用全息远程处理时建立安全的加密连接。</span><span class="sxs-lookup"><span data-stu-id="e2164-106">This page explains how to establish a secure encrypted connection when using Holographic Remoting.</span></span>

<span data-ttu-id="e2164-107">当通过不安全的网络（如开放 WiFi 或 internet）将内容流式传输到 HoloLens 2 时，强烈建议使用加密连接。</span><span class="sxs-lookup"><span data-stu-id="e2164-107">When streaming content to HoloLens 2 over a insecure Network such as an open WiFi or the internet it is highly recommended to use an encrypted connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e2164-108">即使使用受信任的本地 WiFi，也应考虑使用加密连接。</span><span class="sxs-lookup"><span data-stu-id="e2164-108">Even when using a trusted local WiFi using an encrypted connection should be considered.</span></span>

<span data-ttu-id="e2164-109">若要使用加密的连接，则需要同时实现 [自定义播放器](holographic-remoting-create-player.md) 和 [自定义远程应用](holographic-remoting-create-host.md)。</span><span class="sxs-lookup"><span data-stu-id="e2164-109">To be able to use a encrypted connection you will need to implement both a [custom player](holographic-remoting-create-player.md) and a [custom remote app](holographic-remoting-create-host.md).</span></span>

<span data-ttu-id="e2164-110">加密是通过使用基础平台 TLS 实现实现的。</span><span class="sxs-lookup"><span data-stu-id="e2164-110">The encryption is achieved by using the underlying platforms TLS implementation.</span></span>

## <a name="basics-of-an-encrypted-connection"></a><span data-ttu-id="e2164-111">加密连接的基本信息</span><span class="sxs-lookup"><span data-stu-id="e2164-111">Basics of an encrypted connection</span></span>

<span data-ttu-id="e2164-112">需要实现以下对象才能允许证书交换。</span><span class="sxs-lookup"><span data-stu-id="e2164-112">The following objects need to be implemented to allow for a certificate exchange.</span></span>

>[!TIP]
><span data-ttu-id="e2164-113">可使用 c + +/WinRT. 轻松实现 WinRT 接口</span><span class="sxs-lookup"><span data-stu-id="e2164-113">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="e2164-114">[带有 c + +/WinRT 的作者 api](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis)一章将对此进行详细介绍。</span><span class="sxs-lookup"><span data-stu-id="e2164-114">The [Author APIs with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e2164-115">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 包中的包含有关与安全连接相关的 API 的详细文档。</span><span class="sxs-lookup"><span data-stu-id="e2164-115">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

1) <span data-ttu-id="e2164-116">需要实现接口的证书对象 ```ICertificate``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-116">A certificate object, which needs to implement the ```ICertificate``` interface.</span></span>

    * <span data-ttu-id="e2164-117">通过方法返回 pfx 证书的二进制内容 ```GetCertificatePfx``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-117">Return the binary contents of the pfx certificate through the ```GetCertificatePfx``` method.</span></span> <span data-ttu-id="e2164-118">与 .pfx 文件的二进制内容相同。</span><span class="sxs-lookup"><span data-stu-id="e2164-118">Same as the binary contents of a .pfx file.</span></span>
    * <span data-ttu-id="e2164-119">通过返回证书使用者名称 ```GetSubjectName``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-119">Return the certificate subject name through ```GetSubjectName```.</span></span>
    * <span data-ttu-id="e2164-120">通过返回 pfx 密码 ```GetPfxPassword``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-120">Return the pfx password through ```GetPfxPassword```.</span></span> <span data-ttu-id="e2164-121">为未受保护的 pfx 返回空字符串。</span><span class="sxs-lookup"><span data-stu-id="e2164-121">Return an empty string for an unprotected pfx.</span></span>

2) <span data-ttu-id="e2164-122">一个证书提供程序，该提供程序 ```ICertificateProvider``` 在系统通过方法时提供证书来实现接口 ```GetCertificate``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-122">A certificate provider implementing the ```ICertificateProvider``` interface which provides a certificate when asked through the ```GetCertificate``` method.</span></span>

3) <span data-ttu-id="e2164-123">用于实现接口的证书验证程序 ```ICertificateValidator``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-123">A certificate validator implementing the ```ICertificateValidator``` interface.</span></span> <span data-ttu-id="e2164-124">它的任务是验证传入的证书。</span><span class="sxs-lookup"><span data-stu-id="e2164-124">Its task is to verify incoming certificates.</span></span>
    * <span data-ttu-id="e2164-125">```PerformSystemValidation``` ```true``` 如果基础平台应验证传入的证书链，则该方法应返回， ```false``` 否则返回。</span><span class="sxs-lookup"><span data-stu-id="e2164-125">The ```PerformSystemValidation``` method should return ```true``` when the underlying platform should validate the incoming certificate chain, ```false``` otherwise.</span></span>
    * <span data-ttu-id="e2164-126">```ValidateCertificate``` 由客户端上下文调用来请求验证证书。</span><span class="sxs-lookup"><span data-stu-id="e2164-126">```ValidateCertificate``` is called by the client context to request validation of a certificate.</span></span> <span data-ttu-id="e2164-127">此方法接受证书链 (第一个证书为 "使用者证书) "、与之建立连接的服务器的名称，以及是否应强制执行吊销检查。</span><span class="sxs-lookup"><span data-stu-id="e2164-127">This method accepts the certificate chain (with the first certificate being the subject certificate), the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="e2164-128">如果已请求基础系统验证，则将提供系统验证结果。</span><span class="sxs-lookup"><span data-stu-id="e2164-128">The system validation result will be provided if validation by the underlying system has been requested.</span></span> <span data-ttu-id="e2164-129">若要继续处理 ```CertificateValidated``` 适当的结果，或者 ```Cancel``` 需要对传递的调用取消验证，则为 ```ICertificateValidationCallback``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-129">To continue processing either ```CertificateValidated``` with the appropriate result or ```Cancel``` to cancel validation needs to be called on the passed ```ICertificateValidationCallback```.</span></span>

<span data-ttu-id="e2164-130">而且，若要允许交换安全令牌，需要实现以下对象。</span><span class="sxs-lookup"><span data-stu-id="e2164-130">Furthermore, to allow for the exchange of a secure token the following objects need to be implemented.</span></span>

1) <span data-ttu-id="e2164-131">实现接口的身份验证提供程序 ```IAuthenticationProvider``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-131">An authentication provider implementing the ```IAuthenticationProvider``` interface.</span></span> <span data-ttu-id="e2164-132">```GetToken```客户端上下文调用其方法来请求客户端身份验证的令牌。</span><span class="sxs-lookup"><span data-stu-id="e2164-132">Its ```GetToken``` method is called by the client context to request a token for client authentication.</span></span> <span data-ttu-id="e2164-133">若要继续 ```TokenReceived``` 提供身份验证令牌并继续连接过程或取消， ```Cancel``` 需要在传递的上调用该过程 ```IAuthenticationProviderCallback``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-133">To continue either ```TokenReceived``` to provide the authentication token and continue the connection process or ```Cancel``` to cancel the process needs to be called on the passed ```IAuthenticationProviderCallback```.</span></span>
2) <span data-ttu-id="e2164-134">实现接口的身份验证接收器 ```IAuthenticationReceiver``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-134">An authentication receiver implementing the ```IAuthenticationReceiver``` interface.</span></span> <span data-ttu-id="e2164-135">它的任务是验证传入令牌。</span><span class="sxs-lookup"><span data-stu-id="e2164-135">Its task is to validate incoming tokens.</span></span>
    * <span data-ttu-id="e2164-136">```GetRealm```方法应返回身份验证领域的名称。</span><span class="sxs-lookup"><span data-stu-id="e2164-136">The ```GetRealm``` method should return the name of the authentication realm.</span></span>
    * <span data-ttu-id="e2164-137">```ValidateToken```服务器网络上下文调用方法来请求验证客户端身份验证令牌。</span><span class="sxs-lookup"><span data-stu-id="e2164-137">The ```ValidateToken``` method is called by the server network context to request validation of a client authentication token.</span></span> <span data-ttu-id="e2164-138">若要继续调用 ```ValidationCompleted``` 验证的信号完成，则为; 否则 ```Cancel``` 为拒绝客户端连接。</span><span class="sxs-lookup"><span data-stu-id="e2164-138">To continue either call ```ValidationCompleted``` to signal completion of the validation or ```Cancel``` to reject the client connection..</span></span> <span data-ttu-id="e2164-139">根据传递给的验证结果，将会对客户端连接进行许可或拒绝 ```ValidationCompleted``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-139">The client connection will be admitted or rejected based on the validation result passed to ```ValidationCompleted```.</span></span> 

<span data-ttu-id="e2164-140">实现这些对象后， ```ListenSecure``` 需要 ```Listen``` ```ConnectSecure``` ```Connect``` 分别在远程上下文和播放机上下文上调用而不是和而不是。</span><span class="sxs-lookup"><span data-stu-id="e2164-140">Once these objects are implemented ```ListenSecure``` needs to be called instead of ```Listen``` and ```ConnectSecure``` instead of ```Connect``` on the remote context and player context respectively.</span></span> <span data-ttu-id="e2164-141">```ListenSecure``` 需要额外的证书提供程序和身份验证接收器 ```Listen``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-141">```ListenSecure``` requires an additional certificate provider and authentication receiver over ```Listen```.</span></span> <span data-ttu-id="e2164-142">```ConnectSecure``` 需要额外的身份验证提供程序和证书验证程序 ```Connect``` 。</span><span class="sxs-lookup"><span data-stu-id="e2164-142">```ConnectSecure``` requires an additional authentication provider and certificate validator over ```Connect```.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2164-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2164-143">See Also</span></span>
* [<span data-ttu-id="e2164-144">编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="e2164-144">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="e2164-145">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="e2164-145">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="e2164-146">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="e2164-146">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="e2164-147">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="e2164-147">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="e2164-148">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="e2164-148">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
