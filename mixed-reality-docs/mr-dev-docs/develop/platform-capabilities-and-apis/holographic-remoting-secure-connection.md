---
title: 为全息远程处理启用连接安全性
description: 本页介绍如何将全息远程处理配置为使用播放机与远程应用之间经过加密和经过身份验证的连接。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，安全性，身份验证，服务器到客户端
ms.openlocfilehash: ea00565580fdbc850a11d103520351be53cb37b5
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810116"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a><span data-ttu-id="cb7a4-104">为全息远程处理启用连接安全性</span><span class="sxs-lookup"><span data-stu-id="cb7a4-104">Enabling connection security for Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="cb7a4-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="cb7a4-106">此页概述了用于全息远程处理的网络安全。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-106">This page gives you an overview of network security for Holographic Remoting.</span></span> <span data-ttu-id="cb7a4-107">你将找到有关</span><span class="sxs-lookup"><span data-stu-id="cb7a4-107">You'll find information about</span></span>

* <span data-ttu-id="cb7a4-108">全息远程处理的上下文中的安全性以及可能需要它的原因</span><span class="sxs-lookup"><span data-stu-id="cb7a4-108">security in the context of Holographic Remoting and why you might need it</span></span>
* <span data-ttu-id="cb7a4-109">基于不同用例的建议度量值</span><span class="sxs-lookup"><span data-stu-id="cb7a4-109">recommended measures based on different use cases</span></span>
* <span data-ttu-id="cb7a4-110">实现全息远程处理解决方案中的安全性</span><span class="sxs-lookup"><span data-stu-id="cb7a4-110">implementing security in your Holographic Remoting solution</span></span>

## <a name="holographic-remoting-security"></a><span data-ttu-id="cb7a4-111">全息远程处理安全</span><span class="sxs-lookup"><span data-stu-id="cb7a4-111">Holographic Remoting security</span></span>

<span data-ttu-id="cb7a4-112">全息远程处理通过网络交换信息。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-112">Holographic Remoting exchanges information over a network.</span></span> <span data-ttu-id="cb7a4-113">如果没有合适的安全措施，则相同网络上的攻击者可能会危及通信的完整性或访问机密信息。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-113">If no security measures are in place, adversaries on the same network may compromise the integrity of the communication or access confidential information.</span></span>

<span data-ttu-id="cb7a4-114">Windows 应用商店中的示例应用程序和全息远程处理播放机处于禁用安全状态。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-114">The sample apps and the Holographic Remoting Player in the Windows Store come with security disabled.</span></span> <span data-ttu-id="cb7a4-115">这样做会使示例更易于理解。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-115">Doing so makes the samples easier to understand.</span></span> <span data-ttu-id="cb7a4-116">它还可帮助你更快地开始进行开发。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-116">It also helps you to get started more quickly with development.</span></span>

<span data-ttu-id="cb7a4-117">对于现场测试或生产环境，我们强烈建议在全息远程处理解决方案中启用安全性。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-117">For field testing or production, we strongly recommend enabling security in your Holographic Remoting solution.</span></span>

<span data-ttu-id="cb7a4-118">全息远程处理中的安全性在为用例设置正确时，可提供以下保证：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-118">Security in Holographic Remoting, when set up correctly for your use case, gives you the following guarantees:</span></span>

* <span data-ttu-id="cb7a4-119">**真品：** 播放机和远程应用可以确保另一方是他们宣称的身份</span><span class="sxs-lookup"><span data-stu-id="cb7a4-119">**Authenticity:** both player and remote app can be sure the other side is who they claim to be</span></span>
* <span data-ttu-id="cb7a4-120">**机密性：** 任何第三方都无法读取播放机与远程应用之间交换的信息</span><span class="sxs-lookup"><span data-stu-id="cb7a4-120">**Confidentiality:** no third party can read the information exchanged between player and remote app</span></span>
* <span data-ttu-id="cb7a4-121">**完整性：** 播放机和远程可检测任何正在传输的通信更改</span><span class="sxs-lookup"><span data-stu-id="cb7a4-121">**Integrity:** player and remote can detect any in-transit changes to their communication</span></span>

>[!IMPORTANT]
><span data-ttu-id="cb7a4-122">若要能够使用安全功能，需要使用[Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)或[OpenXR](holographic-remoting-create-remote-openxr.md) api 来实现[自定义播放器](holographic-remoting-create-player.md)和自定义远程应用。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-122">To be able to use security features, you will need to implement both a [custom player](holographic-remoting-create-player.md) and a custom remote app using either [Windows Mixed Reality](holographic-remoting-create-remote-wmr.md) or [OpenXR](holographic-remoting-create-remote-openxr.md) APIs.</span></span>

>[!NOTE]
> <span data-ttu-id="cb7a4-123">从版本 [2.4.0](holographic-remoting-version-history.md#v2.4.0) 开始，可以创建使用 [OpenXR API](../native/openxr.md) 的远程应用。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-123">Starting with version [2.4.0](holographic-remoting-version-history.md#v2.4.0) remote apps using the [OpenXR API](../native/openxr.md) can be created.</span></span> <span data-ttu-id="cb7a4-124">[下面](#secure-connection-using-the-openxr-api)是有关如何在 OpenXR 环境中建立安全连接的概述。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-124">An overview on how to establish a secure connection in an OpenXR environment can be found [below](#secure-connection-using-the-openxr-api).</span></span>

## <a name="planning-the-security-implementation"></a><span data-ttu-id="cb7a4-125">规划安全实现</span><span class="sxs-lookup"><span data-stu-id="cb7a4-125">Planning the security implementation</span></span>

<span data-ttu-id="cb7a4-126">当你在全息远程处理中启用安全性时，远程处理库将自动对通过网络交换的所有数据启用加密和完整性检查。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-126">When you enable security in Holographic Remoting, the remoting library will automatically enable encryption and integrity checks for all data exchanged over the network.</span></span>

<span data-ttu-id="cb7a4-127">不过，确保正确的身份验证需要额外的工作。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-127">Ensuring proper authentication requires some extra work though.</span></span> <span data-ttu-id="cb7a4-128">需要执行的具体操作取决于你的用例，本部分的其余部分介绍了如何查明必要的步骤。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-128">What exactly you need to do depends on your use case, and the rest of this section is about figuring out the necessary steps.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="cb7a4-129">本文仅提供一般指导。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-129">This article can only provide general guidance.</span></span> <span data-ttu-id="cb7a4-130">如果你不确定，请考虑咨询一个安全专家，它可以向你介绍特定于用例的指导。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-130">If you feel unsure, consider consulting a security expert that can give you guidance specific to your use case.</span></span>

<span data-ttu-id="cb7a4-131">首先是一些术语：描述网络连接时，将使用术语 " _客户端_ " 和 " _服务器_ "。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-131">First some terminology: when describing network connections, the terms _client_ and _server_ will be used.</span></span> <span data-ttu-id="cb7a4-132">服务器是在已知的终结点地址上侦听传入连接的端，而客户端是连接到服务器终结点的服务器。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-132">The server is the side listening for incoming connections on a known endpoint address, and the client is the one connecting to the server's endpoint.</span></span>

>[!NOTE]
> <span data-ttu-id="cb7a4-133">客户端和和服务器角色不与应用程序是充当播放机还是作为远程角色关联。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-133">The client and and server roles are not tied to whether an app is acting as a player or as a remote.</span></span> <span data-ttu-id="cb7a4-134">尽管示例在服务器角色中具有播放器，但如果角色更适合你的用例，则可以很容易地反转角色。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-134">While the samples have the player in the server role, it's easy to reverse the roles if it better fits your use case.</span></span>

### <a name="planning-the-server-to-client-authentication"></a><span data-ttu-id="cb7a4-135">规划服务器到客户端身份验证</span><span class="sxs-lookup"><span data-stu-id="cb7a4-135">Planning the server-to-client authentication</span></span>

<span data-ttu-id="cb7a4-136">服务器使用数字证书向客户端证明其身份。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-136">The server uses digital certificates to prove its identity to the client.</span></span> <span data-ttu-id="cb7a4-137">客户端在连接握手阶段验证服务器的证书。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-137">The client validates the server's certificate during the connection handshake phase.</span></span> <span data-ttu-id="cb7a4-138">如果客户端不信任服务器，此时它将结束连接。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-138">If the client doesn't trust the server, it will end the connection at this point.</span></span>

<span data-ttu-id="cb7a4-139">客户端如何验证服务器证书，以及可以使用的服务器证书种类取决于用例。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-139">How the client validates the server certificate, and what kinds of server certificates can be used, depends on your use case.</span></span>

<span data-ttu-id="cb7a4-140">**使用案例1：** 服务器主机名不是固定的，或者服务器没有按主机名进行寻址。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-140">**Use case 1:** The server hostname isn't fixed, or the server isn't addressed by host name at all.</span></span>

<span data-ttu-id="cb7a4-141">在此用例中， (或可能) 为服务器的主机名颁发证书是不切实际的。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-141">In this use case, it isn't practical (or even possible) to issue a certificate for the server's host name.</span></span> <span data-ttu-id="cb7a4-142">建议改为验证证书的指纹。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-142">We recommendation you validate the certificate's thumbprint instead.</span></span> <span data-ttu-id="cb7a4-143">与人为指纹一样，指纹会唯一标识证书。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-143">Like a human fingerprint, the thumbprint uniquely identifies a certificate.</span></span>

<span data-ttu-id="cb7a4-144">很重要的一点是，将指纹传达给客户端带外。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-144">It's important to communicate the thumbprint to the client out-of-band.</span></span> <span data-ttu-id="cb7a4-145">也就是说，不能通过用于远程处理的同一网络连接发送它。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-145">That means, you can't send it over the same network connection that's used for remoting.</span></span> <span data-ttu-id="cb7a4-146">相反，您可以手动将它输入到客户端的配置中，或让客户端扫描 QR 代码。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-146">Instead, you could manually enter it into the client's configuration, or to have the client scan a QR code.</span></span>

<span data-ttu-id="cb7a4-147">**用例2：** 可以通过稳定的主机名来访问服务器。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-147">**Use case 2:** The server can be reached over a stable host name.</span></span>

<span data-ttu-id="cb7a4-148">在此用例中，服务器具有特定的主机名，并且你知道此名称不太可能更改。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-148">In this use case, the server has a specific host name, and you know this name isn't likely to change.</span></span> <span data-ttu-id="cb7a4-149">然后，可以使用颁发给服务器的主机名的证书。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-149">You can then use a certificate issued to the server's host name.</span></span> <span data-ttu-id="cb7a4-150">将基于主机名和证书的信任链来建立信任。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-150">Trust will be established based on the host name and the certificate's chain of trust.</span></span>

<span data-ttu-id="cb7a4-151">如果选择此选项，则客户端需要事先知道服务器的主机名和根证书。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-151">If you choose this option, the client needs to know the server's host name and the root certificate in advance.</span></span>

### <a name="planning-the-client-to-server-authentication"></a><span data-ttu-id="cb7a4-152">规划客户端到服务器的身份验证</span><span class="sxs-lookup"><span data-stu-id="cb7a4-152">Planning the client-to-server authentication</span></span>

<span data-ttu-id="cb7a4-153">客户端使用自由格式的令牌对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-153">Clients authenticate against the server using a free-form token.</span></span> <span data-ttu-id="cb7a4-154">此标记应该包含的内容将再次依赖于你的使用情况：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-154">What this token should contain will again depend on your use case:</span></span>

<span data-ttu-id="cb7a4-155">**使用案例1：** 仅需验证客户端应用的标识。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-155">**Use case 1:** You only need to verify the client app's identity.</span></span>

<span data-ttu-id="cb7a4-156">在此用例中，共享机密就足够了。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-156">In this use case, a shared secret can be sufficient.</span></span> <span data-ttu-id="cb7a4-157">此机密必须足够复杂，才能被猜出。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-157">This secret must be complex enough that it can't be guessed.</span></span>

<span data-ttu-id="cb7a4-158">良好的共享机密是一个随机 GUID，它是在服务器和客户端的配置中手动输入的。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-158">A good shared secret is a random GUID, which is manually entered in both the server's and client's configuration.</span></span> <span data-ttu-id="cb7a4-159">例如，若要创建一个，可以 `New-Guid` 在 PowerShell 中使用命令。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-159">To create one you can, for example, use the `New-Guid` command in PowerShell.</span></span>

<span data-ttu-id="cb7a4-160">请确保此共享机密永远不会通过不安全的通道进行通信。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-160">Make sure this shared secret is never communicated over insecure channels.</span></span> <span data-ttu-id="cb7a4-161">远程处理库确保始终以加密的形式发送共享机密，并确保只发送到受信任的对等方。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-161">The remoting library ensures that the shared secret is always sent encrypted, and only to trusted peers.</span></span>

<span data-ttu-id="cb7a4-162">**用例2：** 还需要验证客户端应用程序的用户身份。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-162">**Use case 2:** You also need to verify the identity of the client app's user.</span></span>

<span data-ttu-id="cb7a4-163">共享密钥不足以涵盖此用例。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-163">A shared secret won't be enough to cover this use case.</span></span> <span data-ttu-id="cb7a4-164">相反，你可以使用标识提供程序创建的标记。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-164">Instead, you can use tokens created by an identity provider.</span></span> <span data-ttu-id="cb7a4-165">使用标识提供者的身份验证工作流如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-165">An authentication workflow using an identity provider would look like this:</span></span>

* <span data-ttu-id="cb7a4-166">客户端向标识提供程序授权，并请求令牌</span><span class="sxs-lookup"><span data-stu-id="cb7a4-166">The client authorizes against the identity provider and requests a token</span></span>
* <span data-ttu-id="cb7a4-167">标识提供程序生成一个令牌并将其发送到客户端</span><span class="sxs-lookup"><span data-stu-id="cb7a4-167">The identity provider generates a token and sends it to the client</span></span>
* <span data-ttu-id="cb7a4-168">客户端通过全息远程处理将此令牌发送到服务器</span><span class="sxs-lookup"><span data-stu-id="cb7a4-168">The client sends this token to the server through Holographic Remoting</span></span>
* <span data-ttu-id="cb7a4-169">服务器根据标识提供程序验证客户端的令牌</span><span class="sxs-lookup"><span data-stu-id="cb7a4-169">The server validates the client's token against the identity provider</span></span>

<span data-ttu-id="cb7a4-170">标识提供程序的一个示例是 [Microsoft 标识平台](/azure/active-directory/develop/)。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-170">One example of an identity provider is the [Microsoft identity platform](/azure/active-directory/develop/).</span></span>

<span data-ttu-id="cb7a4-171">与上一用例类似，请确保这些标记不通过不安全的通道发送或公开。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-171">Like in the previous use case, make sure these tokens aren't sent through insecure channels or otherwise exposed.</span></span>

## <a name="implementing-holographic-remoting-security"></a><span data-ttu-id="cb7a4-172">实现全息远程处理安全</span><span class="sxs-lookup"><span data-stu-id="cb7a4-172">Implementing holographic remoting security</span></span>

<span data-ttu-id="cb7a4-173">请记住，如果要启用连接安全性，则需要实现自定义远程和播放器应用。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-173">Remember that you need to implement custom remote and player apps if you want to enable connection security.</span></span> <span data-ttu-id="cb7a4-174">你可以使用提供的示例作为你自己的应用的起点。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-174">You can use the provided samples as starting points for your own apps.</span></span>

<span data-ttu-id="cb7a4-175">若要启用安全性，请调用 `ListenSecure()` 而不是 `Listen()` ，而 `ConnectSecure()` 不是 `Connect()` 建立远程处理连接。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-175">To enable security, call `ListenSecure()` instead of `Listen()`, and `ConnectSecure()` instead of `Connect()` to establish the remoting connection.</span></span>

<span data-ttu-id="cb7a4-176">这些调用需要提供某些接口的实现，以便提供和验证与安全相关的信息：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-176">These calls require you to provide implementations of certain interfaces for providing and validating security-related information:</span></span>

* <span data-ttu-id="cb7a4-177">服务器需要实现证书提供程序和身份验证验证程序</span><span class="sxs-lookup"><span data-stu-id="cb7a4-177">The server needs to implement a certificate provider and an authentication validator</span></span>
* <span data-ttu-id="cb7a4-178">客户端需要实现身份验证提供程序和证书验证程序。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-178">The client needs to implement an authentication provider and a certificate validator.</span></span>

<span data-ttu-id="cb7a4-179">所有接口都有一个请求执行操作的函数，该函数接收回调对象作为参数。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-179">All interfaces have a function requesting you to take action, which receives a callback object as parameter.</span></span> <span data-ttu-id="cb7a4-180">使用此对象，可以轻松实现请求的异步处理。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-180">Using this object, you can easily implement asynchronous handling of the request.</span></span> <span data-ttu-id="cb7a4-181">保留对此对象的引用，并在异步操作完成时调用完成函数。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-181">Keep a reference to this object, and call the completion function when the asynchronous action is complete.</span></span> <span data-ttu-id="cb7a4-182">可以从任何线程调用完成函数。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-182">The completion function may be called from any thread.</span></span>

>[!TIP]
><span data-ttu-id="cb7a4-183">可使用 c + +/WinRT. 轻松实现 WinRT 接口</span><span class="sxs-lookup"><span data-stu-id="cb7a4-183">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="cb7a4-184">[带有 c + +/WinRT 的作者 api](/windows/uwp/cpp-and-winrt-apis/author-apis)一章将对此进行详细介绍。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-184">The [Author APIs with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="cb7a4-185">`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet 包中的包含有关与安全连接相关的 API 的详细文档。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-185">The `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

### <a name="implementing-a-certificate-provider"></a><span data-ttu-id="cb7a4-186">实现证书提供程序</span><span class="sxs-lookup"><span data-stu-id="cb7a4-186">Implementing a certificate provider</span></span>

<span data-ttu-id="cb7a4-187">证书提供程序为服务器应用程序提供要使用的证书。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-187">Certificate providers supply the server application with the certificate to use.</span></span> <span data-ttu-id="cb7a4-188">实现由两部分组成：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-188">The implementation consists of two parts:</span></span>

1) <span data-ttu-id="cb7a4-189">用于实现接口的证书对象 `ICertificate` ：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-189">A certificate object, which implements the `ICertificate` interface:</span></span>

    * <span data-ttu-id="cb7a4-190">`GetCertificatePfx()` 应返回证书存储的二进制内容 `PKCS#12` 。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-190">`GetCertificatePfx()` should return the binary contents of a `PKCS#12` certificate store.</span></span> <span data-ttu-id="cb7a4-191">`.pfx`文件包含 `PKCS#12` 数据，因此可直接在此处使用其内容。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-191">A `.pfx` file contains `PKCS#12` data, so its contents can be used directly here.</span></span>
    * <span data-ttu-id="cb7a4-192">`GetSubjectName()` 应返回标识要使用的证书的友好名称。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-192">`GetSubjectName()` should return the friendly name that identifies the certificate to use.</span></span> <span data-ttu-id="cb7a4-193">如果没有为证书指定友好名称，则此函数应返回证书的使用者名称。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-193">If no friendly name is assigned to the certificate, this function should return the certificate's subject name.</span></span>
    * <span data-ttu-id="cb7a4-194">`GetPfxPassword()` 应返回 (打开证书存储区所需的密码，如果) 不需要密码，则返回空字符串。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-194">`GetPfxPassword()` should return the password required to open the certificate store (or an empty string if no password is required).</span></span>

2) <span data-ttu-id="cb7a4-195">用于实现接口的证书提供程序 `ICertificateProvider` ：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-195">A certificate provider implementing the `ICertificateProvider` interface:</span></span>
    * <span data-ttu-id="cb7a4-196">`GetCertificate()` 应构造一个证书对象并通过 `CertificateReceived()` 在回调对象上调用来返回该对象。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-196">`GetCertificate()` should construct a certificate object and return it by calling `CertificateReceived()` on the callback object.</span></span>

### <a name="implementing-an-authentication-validator"></a><span data-ttu-id="cb7a4-197">实现身份验证验证程序</span><span class="sxs-lookup"><span data-stu-id="cb7a4-197">Implementing an authentication validator</span></span>

<span data-ttu-id="cb7a4-198">身份验证验证程序接收客户端发送的身份验证令牌，并使用验证结果回复。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-198">Authentication validators receive the authentication token sent by the client, and answer back with the validation result.</span></span>

<span data-ttu-id="cb7a4-199">实现该 `IAuthenticationReceiver` 接口，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-199">Implement the `IAuthenticationReceiver` interface as follows:</span></span>

* <span data-ttu-id="cb7a4-200">`GetRealm()` 应返回 (在远程处理连接握手期间使用的 HTTP 领域的身份验证领域的名称) 。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-200">`GetRealm()` should return the name of the authentication realm (an HTTP realm  used during the remoting connection handshake).</span></span>
* <span data-ttu-id="cb7a4-201">`ValidateToken()` 应该验证客户端身份验证令牌，并 `ValidationCompleted()` 通过验证结果对回调对象调用。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-201">`ValidateToken()` should validate the client authentication token and call `ValidationCompleted()` on the callback object with the validation result.</span></span>

### <a name="implementing-an-authentication-provider"></a><span data-ttu-id="cb7a4-202">实现身份验证提供程序</span><span class="sxs-lookup"><span data-stu-id="cb7a4-202">Implementing an authentication provider</span></span>

<span data-ttu-id="cb7a4-203">身份验证提供程序生成或检索要发送到服务器的身份验证令牌。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-203">Authentication providers generate or retrieve the authentication token to be sent to the server.</span></span>

<span data-ttu-id="cb7a4-204">实现该 `IAuthenticationProvider` 接口，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-204">Implement the `IAuthenticationProvider` interface as follows:</span></span>

* <span data-ttu-id="cb7a4-205">`GetToken()` 应生成或检索要发送的身份验证令牌。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-205">`GetToken()` should generate or retrieve the authentication token to be sent.</span></span> <span data-ttu-id="cb7a4-206">标记准备就绪后，调用 `TokenReceived()` 回调对象的方法。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-206">Once the token is ready, call the `TokenReceived()` method on the callback object.</span></span>

### <a name="implementing-a-certificate-validator"></a><span data-ttu-id="cb7a4-207">实现证书验证程序</span><span class="sxs-lookup"><span data-stu-id="cb7a4-207">Implementing a certificate validator</span></span>

<span data-ttu-id="cb7a4-208">证书验证程序接收服务器发送的证书链，并确定服务器是否可信任。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-208">Certificate validators receive the certificate chain sent by the server and determine whether the server can be trusted.</span></span>

<span data-ttu-id="cb7a4-209">若要验证证书，可以使用基础系统的验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-209">To validate certificates, you can use the validation logic of the underlying system.</span></span> <span data-ttu-id="cb7a4-210">此系统验证可以支持您自己的验证逻辑，也可以全部替换。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-210">This system validation can either support your own validation logic, or replace it altogether.</span></span> <span data-ttu-id="cb7a4-211">如果在请求安全连接时未传递自己的证书验证程序，系统将自动使用系统验证。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-211">If you don't pass your own certificate validator when requesting a secure connection, system validation will be used automatically.</span></span>

<span data-ttu-id="cb7a4-212">在 Windows 上，系统验证将检查：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-212">On Windows, the system validation will check for:</span></span>

* <span data-ttu-id="cb7a4-213">证书链的完整性：证书构成以受信任的根证书结尾的一致链</span><span class="sxs-lookup"><span data-stu-id="cb7a4-213">Integrity of the certificate chain: the certificates form a consistent chain that ends at a trusted root certificate</span></span>
* <span data-ttu-id="cb7a4-214">证书有效期：服务器的证书在其有效期内，并为服务器身份验证颁发</span><span class="sxs-lookup"><span data-stu-id="cb7a4-214">Certificate validity: the server's certificate is within its validity timespan, and is issued for server authentication</span></span>
* <span data-ttu-id="cb7a4-215">吊销：证书未被吊销</span><span class="sxs-lookup"><span data-stu-id="cb7a4-215">Revocation: The certificate hasn't been revoked</span></span>
* <span data-ttu-id="cb7a4-216">名称匹配：服务器的主机名与颁发证书的主机名之一匹配</span><span class="sxs-lookup"><span data-stu-id="cb7a4-216">Name match: The host name of the server matches one of the host names the certificate was issued for</span></span>

<span data-ttu-id="cb7a4-217">实现该 `ICertificateValidator` 接口，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb7a4-217">Implement the `ICertificateValidator` interface as follows:</span></span>

 * <span data-ttu-id="cb7a4-218">`PerformSystemValidation()``true`如果应执行上述系统验证，应返回。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-218">`PerformSystemValidation()` should return `true` if a system validation as described above should be performed.</span></span> <span data-ttu-id="cb7a4-219">在这种情况下，系统验证结果将作为输入传递给 `ValidateCertificate()` 方法。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-219">In this case, the system validation result is passed as an input to the `ValidateCertificate()` method.</span></span>
* <span data-ttu-id="cb7a4-220">`ValidateCertificate()` 应该验证证书链，然后 `CertificateValidated()` 在传递的回调上调用最终验证结果。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-220">`ValidateCertificate()` should validate the certificate chain and then call `CertificateValidated()` on the passed callback with the final validation result.</span></span> <span data-ttu-id="cb7a4-221">此方法接受证书链、与之建立连接的服务器的名称，以及是否应强制执行吊销检查。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-221">This method accepts the certificate chain, the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="cb7a4-222">如果证书链包含多个证书，则第一个证书是使用者证书。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-222">If the certificate chain contains multiple certificates, the first one is the subject certificate.</span></span>

>[!NOTE]
><span data-ttu-id="cb7a4-223">如果用例需要不同形式的验证 (参阅) 上方的证书用例 #1，请完全绕过系统验证。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-223">If your use case requires a different form of validation (see certificate use case #1 above), bypass system validation entirely.</span></span> <span data-ttu-id="cb7a4-224">相反，请使用任何可处理 DER 编码的 x.509 证书的 API 或库来解码证书链，并执行用例所需的检查。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-224">Instead, use any API or library that can handle DER-encoded X.509 certificates to decode the certificate chain and perform the checks needed for your use case.</span></span>

## <a name="secure-connection-using-the-openxr-api"></a><span data-ttu-id="cb7a4-225">使用 OpenXR API 的安全连接</span><span class="sxs-lookup"><span data-stu-id="cb7a4-225">Secure connection using the OpenXR API</span></span>

<span data-ttu-id="cb7a4-226">使用 [OPENXR API](../native/openxr.md) 时，与连接相关的所有安全 api 都作为 OpenXR 扩展的一部分提供 `XR_MSFT_holographic_remoting` 。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-226">When using the [OpenXR API](../native/openxr.md) all secure connection-related API is available as part of the `XR_MSFT_holographic_remoting` OpenXR extension.</span></span>

>[!IMPORTANT]
><span data-ttu-id="cb7a4-227">若要了解全息远程处理 OpenXR 扩展 API，请查看可在[全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到的[规范](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-227">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="cb7a4-228">使用 OpenXR 扩展进行安全连接的关键元素 `XR_MSFT_holographic_remoting` 是以下回调。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-228">The key elements for secure connection using the `XR_MSFT_holographic_remoting` OpenXR extension are the following callbacks.</span></span>
- <span data-ttu-id="cb7a4-229">`xrRemotingRequestAuthenticationTokenCallbackMSFT`、生成或检索要发送的身份验证令牌。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-229">`xrRemotingRequestAuthenticationTokenCallbackMSFT`, generates, or retrieves the authentication token to be sent.</span></span>
- <span data-ttu-id="cb7a4-230">`xrRemotingValidateServerCertificateCallbackMSFT`，验证证书链。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-230">`xrRemotingValidateServerCertificateCallbackMSFT`, validates the certificate chain.</span></span>
- <span data-ttu-id="cb7a4-231">`xrRemotingValidateAuthenticationTokenCallbackMSFT`验证客户端身份验证令牌。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-231">`xrRemotingValidateAuthenticationTokenCallbackMSFT`, validates the client authentication token.</span></span>
- <span data-ttu-id="cb7a4-232">`xrRemotingRequestServerCertificateCallbackMSFT`，为服务器应用程序提供要使用的证书。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-232">`xrRemotingRequestServerCertificateCallbackMSFT`, supply the server application with the certificate to use.</span></span>

<span data-ttu-id="cb7a4-233">可以通过和向远程处理 OpenXR 运行时提供这些 `xrRemotingSetSecureConnectionClientCallbacksMSFT` 回调 `xrRemotingSetSecureConnectionServerCallbacksMSFT` 。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-233">These callbacks can be provided to the remoting OpenXR runtime via `xrRemotingSetSecureConnectionClientCallbacksMSFT` and `xrRemotingSetSecureConnectionServerCallbacksMSFT`.</span></span> <span data-ttu-id="cb7a4-234">此外，需要通过结构或结构上的 secureConnection 参数启用安全连接， `XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` 具体取决于你使用 `xrRemotingConnectMSFT` 的是还是 `xrRemotingListenMSFT` 。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-234">Additionally, the secure connection needs to be enabled via the secureConnection parameter on the `XrRemotingConnectInfoMSFT` structure or the `XrRemotingListenInfoMSFT` structure depending on whether you're using `xrRemotingConnectMSFT` or `xrRemotingListenMSFT`.</span></span>

<span data-ttu-id="cb7a4-235">此 API 类似于 [实现全息远程处理安全](#implementing-holographic-remoting-security)中所述的基于 IDL 的 api。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-235">This API is similar to the IDL-based API described in [Implementing holographic remoting security](#implementing-holographic-remoting-security).</span></span> <span data-ttu-id="cb7a4-236">但是，你应该提供回调实现，而不是实现接口。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-236">However, instead of implementing interfaces, you're supposed to provide callback implementations.</span></span> <span data-ttu-id="cb7a4-237">可在 [OpenXR 示例应用](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到详细的示例。</span><span class="sxs-lookup"><span data-stu-id="cb7a4-237">You can find a detailed example in the [OpenXR sample app](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb7a4-238">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb7a4-238">See Also</span></span>
* [<span data-ttu-id="cb7a4-239">使用 Windows Mixed Reality Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="cb7a4-239">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="cb7a4-240">使用 OpenXR Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="cb7a4-240">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="cb7a4-241">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="cb7a4-241">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="cb7a4-242">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="cb7a4-242">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="cb7a4-243">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="cb7a4-243">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="cb7a4-244">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="cb7a4-244">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)