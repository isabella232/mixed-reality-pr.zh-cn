---
title: 为全息远程处理启用连接安全性
description: 本页介绍如何将全息远程处理配置为使用播放机与远程应用之间经过加密和经过身份验证的连接。
author: markkeinz
ms.author: makei
ms.date: 10/29/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，安全性，身份验证，服务器到客户端
ms.openlocfilehash: 4004c7534092c73fe478130b9d957461bb34bcfa
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679586"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a><span data-ttu-id="1f0ad-104">为全息远程处理启用连接安全性</span><span class="sxs-lookup"><span data-stu-id="1f0ad-104">Enabling connection security for Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="1f0ad-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="1f0ad-106">此页概述了用于全息远程处理的网络安全。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-106">This page gives you an overview of network security for Holographic Remoting.</span></span> <span data-ttu-id="1f0ad-107">你将找到有关</span><span class="sxs-lookup"><span data-stu-id="1f0ad-107">You'll find information about</span></span>

* <span data-ttu-id="1f0ad-108">全息远程处理的上下文中的安全性以及可能需要它的原因</span><span class="sxs-lookup"><span data-stu-id="1f0ad-108">security in the context of Holographic Remoting and why you might need it</span></span>
* <span data-ttu-id="1f0ad-109">基于不同用例的建议度量值</span><span class="sxs-lookup"><span data-stu-id="1f0ad-109">recommended measures based on different use cases</span></span>
* <span data-ttu-id="1f0ad-110">实现全息远程处理解决方案中的安全性</span><span class="sxs-lookup"><span data-stu-id="1f0ad-110">implementing security in your Holographic Remoting solution</span></span>

## <a name="overview"></a><span data-ttu-id="1f0ad-111">概述</span><span class="sxs-lookup"><span data-stu-id="1f0ad-111">Overview</span></span>

<span data-ttu-id="1f0ad-112">全息远程处理通过网络交换信息。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-112">Holographic Remoting exchanges information over a network.</span></span> <span data-ttu-id="1f0ad-113">如果没有合适的安全措施，则相同网络上的攻击者可能会危及通信的完整性或访问机密信息。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-113">If no security measures are in place, adversaries on the same network may compromise the integrity of the communication or access confidential information.</span></span>

<span data-ttu-id="1f0ad-114">Windows 应用商店中的示例应用程序和全息远程处理播放机处于禁用安全状态。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-114">The sample apps and the Holographic Remoting Player in the Windows Store come with security disabled.</span></span> <span data-ttu-id="1f0ad-115">这样做会使示例更易于理解。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-115">Doing so makes the samples easier to understand.</span></span> <span data-ttu-id="1f0ad-116">它还可帮助你更快地开始进行开发。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-116">It also helps you to get started more quickly with development.</span></span>

<span data-ttu-id="1f0ad-117">但对于现场测试或生产用途，我们强烈建议在全息远程处理解决方案中启用安全性。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-117">For field testing or production use however, we strongly recommend enabling security in your Holographic Remoting solution.</span></span>

<span data-ttu-id="1f0ad-118">全息远程处理中的安全性在为用例设置正确时，可提供以下保证：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-118">Security in Holographic Remoting, when set up correctly for your use case, gives you the following guarantees:</span></span>

* <span data-ttu-id="1f0ad-119">**真品：** 播放机和远程应用可以确保另一方是他们宣称的身份</span><span class="sxs-lookup"><span data-stu-id="1f0ad-119">**Authenticity:** both player and remote app can be sure the other side is who they claim to be</span></span>
* <span data-ttu-id="1f0ad-120">**机密性：** 任何第三方都无法读取播放机与远程应用之间交换的信息</span><span class="sxs-lookup"><span data-stu-id="1f0ad-120">**Confidentiality:** no third party can read the information exchanged between player and remote app</span></span>
* <span data-ttu-id="1f0ad-121">**完整性：** 播放机和远程可检测任何正在传输的通信更改</span><span class="sxs-lookup"><span data-stu-id="1f0ad-121">**Integrity:** player and remote can detect any in-transit changes to their communication</span></span>

>[!TIP]
><span data-ttu-id="1f0ad-122">若要能够使用安全功能，你将需要实现 [自定义播放器](holographic-remoting-create-player.md) 和 [自定义远程应用](holographic-remoting-create-host.md)。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-122">To be able to use security features, you will need to implement both a [custom player](holographic-remoting-create-player.md) and a [custom remote app](holographic-remoting-create-host.md).</span></span>

## <a name="planning-the-security-implementation"></a><span data-ttu-id="1f0ad-123">规划安全实现</span><span class="sxs-lookup"><span data-stu-id="1f0ad-123">Planning the security implementation</span></span>

<span data-ttu-id="1f0ad-124">当你在全息远程处理中启用安全性时，远程处理库将自动对通过网络交换的所有数据启用加密和完整性检查。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-124">When you enable security in Holographic Remoting, the remoting library will automatically enable encryption and integrity checks for all data exchanged over the network.</span></span>

<span data-ttu-id="1f0ad-125">不过，确保正确的身份验证需要额外的工作。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-125">Ensuring proper authentication requires some extra work though.</span></span> <span data-ttu-id="1f0ad-126">需要执行的具体操作取决于你的用例，本部分的其余部分介绍了如何查明必要的步骤。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-126">What exactly you need to do depends on your use case, and the rest of this section is about figuring out the necessary steps.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="1f0ad-127">本文仅提供一般指导。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-127">This article can only provide general guidance.</span></span> <span data-ttu-id="1f0ad-128">如果你不确定，请考虑咨询一个安全专家，它可以向你介绍特定于用例的指导。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-128">If you feel unsure, consider consulting a security expert that can give you guidance specific to your use case.</span></span>

<span data-ttu-id="1f0ad-129">首先是一些术语：描述网络连接时，将使用术语 " _客户端_ " 和 " _服务器_ "。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-129">First some terminology: when describing network connections, the terms _client_ and _server_ will be used.</span></span> <span data-ttu-id="1f0ad-130">服务器是在已知的终结点地址上侦听传入连接的端，而客户端是连接到服务器终结点的服务器。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-130">The server is the side listening for incoming connections on a known endpoint address, and the client is the one connecting to the server's endpoint.</span></span>

>[!NOTE]
> <span data-ttu-id="1f0ad-131">客户端和和服务器角色不与应用程序是充当播放机还是作为远程角色关联。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-131">The client and and server roles are not tied to whether an app is acting as a player or as a remote.</span></span> <span data-ttu-id="1f0ad-132">尽管示例在服务器角色中具有播放器，但如果角色更适合你的用例，则可以很容易地反转角色。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-132">While the samples have the player in the server role, it's easy to reverse the roles if it better fits your use case.</span></span>

### <a name="planning-the-server-to-client-authentication"></a><span data-ttu-id="1f0ad-133">规划服务器到客户端身份验证</span><span class="sxs-lookup"><span data-stu-id="1f0ad-133">Planning the server-to-client authentication</span></span>

<span data-ttu-id="1f0ad-134">服务器使用数字证书向客户端证明其身份。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-134">The server uses digital certificates to prove its identity to the client.</span></span> <span data-ttu-id="1f0ad-135">客户端在连接握手阶段验证服务器的证书。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-135">The client validates the server's certificate during the connection handshake phase.</span></span> <span data-ttu-id="1f0ad-136">如果客户端不信任服务器，此时它将结束连接。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-136">If the client doesn't trust the server, it will end the connection at this point.</span></span>

<span data-ttu-id="1f0ad-137">客户端如何验证服务器证书，以及可以使用的服务器证书种类取决于用例。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-137">How the client validates the server certificate, and what kinds of server certificates can be used, depends on your use case.</span></span>

<span data-ttu-id="1f0ad-138">**使用案例1：** 服务器主机名不是固定的，或者服务器没有按主机名进行寻址。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-138">**Use case 1:** The server hostname isn't fixed, or the server isn't addressed by host name at all.</span></span>

<span data-ttu-id="1f0ad-139">在此用例中， (或可能) 为服务器的主机名颁发证书是不切实际的。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-139">In this use case, it isn't practical (or even possible) to issue a certificate for the server's host name.</span></span> <span data-ttu-id="1f0ad-140">此处的建议是改为验证证书的指纹。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-140">The recommendation here is to validate the certificate's thumbprint instead.</span></span> <span data-ttu-id="1f0ad-141">与人为指纹一样，指纹会唯一标识证书。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-141">Like a human fingerprint, the thumbprint uniquely identifies a certificate.</span></span>

<span data-ttu-id="1f0ad-142">很重要的一点是，将指纹传达给客户端带外。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-142">It's important to communicate the thumbprint to the client out-of-band.</span></span> <span data-ttu-id="1f0ad-143">也就是说，不能通过用于远程处理的同一网络连接发送它。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-143">That means, you can't send it over the same network connection that's used for remoting.</span></span> <span data-ttu-id="1f0ad-144">相反，您可以手动将它输入到客户端的配置中，或让客户端扫描 QR 代码。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-144">Instead, you could manually enter it into the client's configuration, or to have the client scan a QR code.</span></span>

<span data-ttu-id="1f0ad-145">**用例2：** 可以通过稳定的主机名来访问服务器。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-145">**Use case 2:** The server can be reached over a stable host name.</span></span>

<span data-ttu-id="1f0ad-146">在此用例中，服务器具有特定的主机名，并且你知道此名称不太可能更改。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-146">In this use case, the server has a specific host name, and you know this name isn't likely to change.</span></span> <span data-ttu-id="1f0ad-147">然后，可以使用颁发给服务器的主机名的证书。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-147">You can then use a certificate issued to the server's host name.</span></span> <span data-ttu-id="1f0ad-148">将基于主机名和证书的信任链来建立信任。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-148">Trust will be established based on the host name and the certificate's chain of trust.</span></span>

<span data-ttu-id="1f0ad-149">如果选择此选项，则客户端需要事先知道服务器的主机名和根证书。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-149">If you choose this option, the client needs to know the server's host name and the root certificate in advance.</span></span>

### <a name="planning-the-client-to-server-authentication"></a><span data-ttu-id="1f0ad-150">规划客户端到服务器的身份验证</span><span class="sxs-lookup"><span data-stu-id="1f0ad-150">Planning the client-to-server authentication</span></span>

<span data-ttu-id="1f0ad-151">客户端使用自由格式的令牌对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-151">Clients authenticate against the server using a free-form token.</span></span> <span data-ttu-id="1f0ad-152">此标记应该包含的内容将再次依赖于你的使用情况：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-152">What this token should contain will again depend on your use case:</span></span>

<span data-ttu-id="1f0ad-153">**使用案例1：** 仅需验证客户端应用的标识。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-153">**Use case 1:** You only need to verify the client app's identity.</span></span>

<span data-ttu-id="1f0ad-154">在此用例中，共享机密就足够了。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-154">In this use case, a shared secret can be sufficient.</span></span> <span data-ttu-id="1f0ad-155">此机密必须足够复杂，才能被猜出。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-155">This secret must be complex enough that it can't be guessed.</span></span>

<span data-ttu-id="1f0ad-156">良好的共享机密是一个随机 GUID，它是在服务器和客户端的配置中手动输入的。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-156">A good shared secret is a random GUID, which is manually entered in both the server's and client's configuration.</span></span> <span data-ttu-id="1f0ad-157">例如，若要创建一个，可以 `New-Guid` 在 PowerShell 中使用命令。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-157">To create one you can, for example, use the `New-Guid` command in PowerShell.</span></span>

<span data-ttu-id="1f0ad-158">请确保此共享机密永远不会通过不安全的通道进行通信。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-158">Make sure this shared secret is never communicated over insecure channels.</span></span> <span data-ttu-id="1f0ad-159">远程处理库确保始终以加密的形式发送共享机密，并确保只发送到受信任的对等方。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-159">The remoting library ensures that the shared secret is always sent encrypted, and only to trusted peers.</span></span>

<span data-ttu-id="1f0ad-160">**用例2：** 还需要验证客户端应用程序的用户身份。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-160">**Use case 2:** You also need to verify the identity of the client app's user.</span></span>

<span data-ttu-id="1f0ad-161">共享密钥不足以涵盖此用例。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-161">A shared secret won't be enough to cover this use case.</span></span> <span data-ttu-id="1f0ad-162">相反，你可以使用标识提供程序创建的标记。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-162">Instead, you can use tokens created by an identity provider.</span></span> <span data-ttu-id="1f0ad-163">使用标识提供者的身份验证工作流如下所示：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-163">An authentication workflow using an identity provider would look like this:</span></span>

* <span data-ttu-id="1f0ad-164">客户端向标识提供程序授权，并请求令牌</span><span class="sxs-lookup"><span data-stu-id="1f0ad-164">The client authorizes against the identity provider and requests a token</span></span>
* <span data-ttu-id="1f0ad-165">标识提供程序生成一个令牌并将其发送到客户端</span><span class="sxs-lookup"><span data-stu-id="1f0ad-165">The identity provider generates a token and sends it to the client</span></span>
* <span data-ttu-id="1f0ad-166">客户端通过全息远程处理将此令牌发送到服务器</span><span class="sxs-lookup"><span data-stu-id="1f0ad-166">The client sends this token to the server through Holographic Remoting</span></span>
* <span data-ttu-id="1f0ad-167">服务器根据标识提供程序验证客户端的令牌</span><span class="sxs-lookup"><span data-stu-id="1f0ad-167">The server validates the client's token against the identity provider</span></span>

<span data-ttu-id="1f0ad-168">标识提供程序的一个示例是 [Microsoft 标识平台](https://docs.microsoft.com/azure/active-directory/develop/)。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-168">One example of an identity provider is the [Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/).</span></span>

<span data-ttu-id="1f0ad-169">与上一用例类似，请确保这些标记不通过不安全的通道发送或公开。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-169">Like in the previous use case, make sure these tokens aren't sent through insecure channels or otherwise exposed.</span></span>

## <a name="implementing-holographic-remoting-security"></a><span data-ttu-id="1f0ad-170">实现全息远程处理安全</span><span class="sxs-lookup"><span data-stu-id="1f0ad-170">Implementing holographic remoting security</span></span>

<span data-ttu-id="1f0ad-171">请记住，如果要启用连接安全性，则需要实现自定义远程和播放器应用。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-171">Remember that you need to implement custom remote and player apps if you want to enable connection security.</span></span> <span data-ttu-id="1f0ad-172">你可以使用提供的示例作为你自己的应用的起点。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-172">You can use the provided samples as starting points for your own apps.</span></span>

<span data-ttu-id="1f0ad-173">若要启用安全性，请调用 `ListenSecure()` 而不是 `Listen()` ，而 `ConnectSecure()` 不是 `Connect()` 建立远程处理连接。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-173">To enable security, call `ListenSecure()` instead of `Listen()`, and `ConnectSecure()` instead of `Connect()` to establish the remoting connection.</span></span>

<span data-ttu-id="1f0ad-174">这些调用需要提供某些接口的实现，以便提供和验证与安全相关的信息：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-174">These calls require you to provide implementations of certain interfaces for providing and validating security-related information:</span></span>

* <span data-ttu-id="1f0ad-175">服务器需要实现证书提供程序和身份验证验证程序</span><span class="sxs-lookup"><span data-stu-id="1f0ad-175">The server needs to implement a certificate provider and an authentication validator</span></span>
* <span data-ttu-id="1f0ad-176">客户端需要实现身份验证提供程序和证书验证程序。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-176">The client needs to implement an authentication provider and a certificate validator.</span></span>

<span data-ttu-id="1f0ad-177">所有接口都有一个请求执行操作的函数，该函数接收回调对象作为参数。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-177">All interfaces have a function requesting you to take action, which receives a callback object as parameter.</span></span> <span data-ttu-id="1f0ad-178">使用此对象，可以轻松实现请求的异步处理。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-178">Using this object, you can easily implement asynchronous handling of the request.</span></span> <span data-ttu-id="1f0ad-179">保留对此对象的引用，并在异步操作完成时调用完成函数。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-179">Keep a reference to this object, and call the completion function when the asynchronous action is complete.</span></span> <span data-ttu-id="1f0ad-180">可以从任何线程调用完成函数。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-180">The completion function may be called from any thread.</span></span>

>[!TIP]
><span data-ttu-id="1f0ad-181">可使用 c + +/WinRT. 轻松实现 WinRT 接口</span><span class="sxs-lookup"><span data-stu-id="1f0ad-181">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="1f0ad-182">[带有 c + +/WinRT 的作者 api](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis)一章将对此进行详细介绍。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-182">The [Author APIs with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1f0ad-183">`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet 包中的包含有关与安全连接相关的 API 的详细文档。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-183">The `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

### <a name="implementing-a-certificate-provider"></a><span data-ttu-id="1f0ad-184">实现证书提供程序</span><span class="sxs-lookup"><span data-stu-id="1f0ad-184">Implementing a certificate provider</span></span>

<span data-ttu-id="1f0ad-185">证书提供程序为服务器应用程序提供要使用的证书。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-185">Certificate providers supply the server application with the certificate to use.</span></span> <span data-ttu-id="1f0ad-186">实现由两部分组成：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-186">The implementation consists of two parts:</span></span>

1) <span data-ttu-id="1f0ad-187">用于实现接口的证书对象 `ICertificate` ：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-187">A certificate object, which implements the `ICertificate` interface:</span></span>

    * <span data-ttu-id="1f0ad-188">`GetCertificatePfx()` 应返回证书存储的二进制内容 `PKCS#12` 。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-188">`GetCertificatePfx()` should return the binary contents of a `PKCS#12` certificate store.</span></span> <span data-ttu-id="1f0ad-189">`.pfx`文件包含 `PKCS#12` 数据，因此可直接在此处使用其内容。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-189">A `.pfx` file contains `PKCS#12` data, so its contents can be used directly here.</span></span>
    * <span data-ttu-id="1f0ad-190">`GetSubjectName()` 应返回标识要使用的证书的友好名称。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-190">`GetSubjectName()` should return the friendly name that identifies the certificate to use.</span></span> <span data-ttu-id="1f0ad-191">如果没有为证书指定友好名称，则此函数应返回证书的使用者名称。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-191">If no friendly name is assigned to the certificate, this function should return the certificate's subject name.</span></span>
    * <span data-ttu-id="1f0ad-192">`GetPfxPassword()` 应返回 (打开证书存储区所需的密码，如果) 不需要密码，则返回空字符串。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-192">`GetPfxPassword()` should return the password required to open the certificate store (or an empty string if no password is required).</span></span>

2) <span data-ttu-id="1f0ad-193">用于实现接口的证书提供程序 `ICertificateProvider` ：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-193">A certificate provider implementing the `ICertificateProvider` interface:</span></span>
    * <span data-ttu-id="1f0ad-194">`GetCertificate()` 应构造一个证书对象并通过 `CertificateReceived()` 在回调对象上调用来返回该对象。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-194">`GetCertificate()` should construct a certificate object and return it by calling `CertificateReceived()` on the callback object.</span></span>

### <a name="implementing-an-authentication-validator"></a><span data-ttu-id="1f0ad-195">实现身份验证验证程序</span><span class="sxs-lookup"><span data-stu-id="1f0ad-195">Implementing an authentication validator</span></span>

<span data-ttu-id="1f0ad-196">身份验证验证程序接收客户端发送的身份验证令牌，并使用验证结果回复。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-196">Authentication validators receive the authentication token sent by the client, and answer back with the validation result.</span></span>

<span data-ttu-id="1f0ad-197">实现该 `IAuthenticationReceiver` 接口，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-197">Implement the `IAuthenticationReceiver` interface as follows:</span></span>

* <span data-ttu-id="1f0ad-198">`GetRealm()` 应返回 (在远程处理连接握手期间使用的 HTTP 领域的身份验证领域的名称) 。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-198">`GetRealm()` should return the name of the authentication realm (an HTTP realm  used during the remoting connection handshake).</span></span>
* <span data-ttu-id="1f0ad-199">`ValidateToken()` 应该验证客户端身份验证令牌，并 `ValidationCompleted()` 通过验证结果对回调对象调用。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-199">`ValidateToken()` should validate the client authentication token and call `ValidationCompleted()` on the callback object with the validation result.</span></span>

### <a name="implementing-an-authentication-provider"></a><span data-ttu-id="1f0ad-200">实现身份验证提供程序</span><span class="sxs-lookup"><span data-stu-id="1f0ad-200">Implementing an authentication provider</span></span>

<span data-ttu-id="1f0ad-201">身份验证提供程序生成或检索要发送到服务器的身份验证令牌。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-201">Authentication providers generate or retrieve the authentication token to be sent to the server.</span></span>

<span data-ttu-id="1f0ad-202">实现该 `IAuthenticationProvider` 接口，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-202">Implement the `IAuthenticationProvider` interface as follows:</span></span>

* <span data-ttu-id="1f0ad-203">`GetToken()` 应生成或检索要发送的身份验证令牌。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-203">`GetToken()` should generate or retrieve the authentication token to be sent.</span></span> <span data-ttu-id="1f0ad-204">标记准备就绪后，调用 `TokenReceived()` 回调对象的方法。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-204">Once the token is ready, call the `TokenReceived()` method on the callback object.</span></span>

### <a name="implementing-a-certificate-validator"></a><span data-ttu-id="1f0ad-205">实现证书验证程序</span><span class="sxs-lookup"><span data-stu-id="1f0ad-205">Implementing a certificate validator</span></span>

<span data-ttu-id="1f0ad-206">证书验证程序接收服务器发送的证书链，并确定服务器是否可信任。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-206">Certificate validators receive the certificate chain sent by the server and determine whether the server can be trusted.</span></span>

<span data-ttu-id="1f0ad-207">若要验证证书，可以使用基础系统的验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-207">To validate certificates, you can use the validation logic of the underlying system.</span></span> <span data-ttu-id="1f0ad-208">此系统验证可以支持您自己的验证逻辑，也可以全部替换。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-208">This system validation can either support your own validation logic, or replace it altogether.</span></span> <span data-ttu-id="1f0ad-209">如果在请求安全连接时未传递自己的证书验证程序，系统将自动使用系统验证。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-209">If you don't pass your own certificate validator when requesting a secure connection, system validation will be used automatically.</span></span>

<span data-ttu-id="1f0ad-210">在 Windows 上，系统验证将检查：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-210">On Windows, the system validation will check for:</span></span>

* <span data-ttu-id="1f0ad-211">证书链的完整性：证书构成以受信任的根证书结尾的一致链</span><span class="sxs-lookup"><span data-stu-id="1f0ad-211">Integrity of the certificate chain: the certificates form a consistent chain that ends at a trusted root certificate</span></span>
* <span data-ttu-id="1f0ad-212">证书有效期：服务器的证书在其有效期内，并且出于服务器身份验证目的而颁发</span><span class="sxs-lookup"><span data-stu-id="1f0ad-212">Certificate validity: the server's certificate is within its validity timespan, and is issued for the purpose of server authentication</span></span>
* <span data-ttu-id="1f0ad-213">吊销：证书未被吊销</span><span class="sxs-lookup"><span data-stu-id="1f0ad-213">Revocation: The certificate hasn't been revoked</span></span>
* <span data-ttu-id="1f0ad-214">名称匹配：服务器的主机名与颁发证书的主机名之一匹配</span><span class="sxs-lookup"><span data-stu-id="1f0ad-214">Name match: The host name of the server matches one of the host names the certificate was issued for</span></span>

<span data-ttu-id="1f0ad-215">实现该 `ICertificateValidator` 接口，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1f0ad-215">Implement the `ICertificateValidator` interface as follows:</span></span>

 * <span data-ttu-id="1f0ad-216">`PerformSystemValidation()``true`如果应执行上述系统验证，应返回。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-216">`PerformSystemValidation()` should return `true` if a system validation as described above should be performed.</span></span> <span data-ttu-id="1f0ad-217">在这种情况下，系统验证结果将作为输入传递给 `ValidateCertificate()` 方法。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-217">In this case, the system validation result is passed as an input to the `ValidateCertificate()` method.</span></span>
* <span data-ttu-id="1f0ad-218">`ValidateCertificate()` 应该验证证书链，然后 `CertificateValidated()` 在传递的回调上调用最终验证结果。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-218">`ValidateCertificate()` should validate the certificate chain and then call `CertificateValidated()` on the passed callback with the final validation result.</span></span> <span data-ttu-id="1f0ad-219">此方法接受证书链、与之建立连接的服务器的名称，以及是否应强制执行吊销检查。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-219">This method accepts the certificate chain, the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="1f0ad-220">如果证书链包含多个证书，则第一个证书是使用者证书。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-220">If the certificate chain contains multiple certificates, the first one is the subject certificate.</span></span>

>[!NOTE]
><span data-ttu-id="1f0ad-221">如果用例需要不同形式的验证 (参阅) 上方的证书用例 #1，请完全绕过系统验证。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-221">If your use case requires a different form of validation (see certificate use case #1 above), bypass system validation entirely.</span></span> <span data-ttu-id="1f0ad-222">相反，请使用任何可处理 DER 编码的 x.509 证书的 API 或库来解码证书链，并执行用例所需的检查。</span><span class="sxs-lookup"><span data-stu-id="1f0ad-222">Instead, use any API or library that can handle DER-encoded X.509 certificates to decode the certificate chain and perform the checks needed for your use case.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f0ad-223">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f0ad-223">See Also</span></span>
* [<span data-ttu-id="1f0ad-224">编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="1f0ad-224">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="1f0ad-225">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="1f0ad-225">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="1f0ad-226">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="1f0ad-226">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="1f0ad-227">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="1f0ad-227">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="1f0ad-228">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="1f0ad-228">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
