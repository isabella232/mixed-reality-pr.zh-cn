---
title: 为全息远程处理启用连接安全性
description: 本页介绍如何将全息远程处理配置为使用播放机与远程应用之间经过加密和经过身份验证的连接。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，安全性，身份验证，服务器到客户端
ms.openlocfilehash: 64eb54d9401f3fbc8b73ebb97b19de5a68cdc5c4
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530411"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>为全息远程处理启用连接安全性

>[!IMPORTANT]
>本指南特定于 HoloLens 2 上的全息远程处理。

此页概述了用于全息远程处理的网络安全。 你将找到有关

* 全息远程处理的上下文中的安全性以及可能需要它的原因
* 基于不同用例的建议度量值
* 实现全息远程处理解决方案中的安全性

## <a name="overview"></a>概述

全息远程处理通过网络交换信息。 如果没有合适的安全措施，则相同网络上的攻击者可能会危及通信的完整性或访问机密信息。

Windows 应用商店中的示例应用程序和全息远程处理播放机处于禁用安全状态。 这样做会使示例更易于理解。 它还可帮助你更快地开始进行开发。

对于现场测试或生产环境，我们强烈建议在全息远程处理解决方案中启用安全性。

全息远程处理中的安全性在为用例设置正确时，可提供以下保证：

* **真品：** 播放机和远程应用可以确保另一方是他们宣称的身份
* **机密性：** 任何第三方都无法读取播放机与远程应用之间交换的信息
* **完整性：** 播放机和远程可检测任何正在传输的通信更改

>[!IMPORTANT]
>若要能够使用安全功能，需要使用[Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)或[OpenXR](holographic-remoting-create-remote-openxr.md) api 来实现[自定义播放器](holographic-remoting-create-player.md)和自定义远程应用。

>[!NOTE]
> 从版本 [2.4.0](holographic-remoting-version-history.md#v2.4.0) 开始，可以创建使用 [OpenXR API](../native/openxr.md) 的远程应用。 [下面](#secure-connection-using-the-openxr-api)是有关如何在 OpenXR 环境中建立安全连接的概述。

## <a name="planning-the-security-implementation"></a>规划安全实现

当你在全息远程处理中启用安全性时，远程处理库将自动对通过网络交换的所有数据启用加密和完整性检查。

不过，确保正确的身份验证需要额外的工作。 需要执行的具体操作取决于你的用例，本部分的其余部分介绍了如何查明必要的步骤。

>[!IMPORTANT]
> 本文仅提供一般指导。 如果你不确定，请考虑咨询一个安全专家，它可以向你介绍特定于用例的指导。

首先是一些术语：描述网络连接时，将使用术语 " _客户端_ " 和 " _服务器_ "。 服务器是在已知的终结点地址上侦听传入连接的端，而客户端是连接到服务器终结点的服务器。

>[!NOTE]
> 客户端和和服务器角色不与应用程序是充当播放机还是作为远程角色关联。 尽管示例在服务器角色中具有播放器，但如果角色更适合你的用例，则可以很容易地反转角色。

### <a name="planning-the-server-to-client-authentication"></a>规划服务器到客户端身份验证

服务器使用数字证书向客户端证明其身份。 客户端在连接握手阶段验证服务器的证书。 如果客户端不信任服务器，此时它将结束连接。

客户端如何验证服务器证书，以及可以使用的服务器证书种类取决于用例。

**使用案例1：** 服务器主机名不是固定的，或者服务器没有按主机名进行寻址。

在此用例中， (或可能) 为服务器的主机名颁发证书是不切实际的。 建议改为验证证书的指纹。 与人为指纹一样，指纹会唯一标识证书。

很重要的一点是，将指纹传达给客户端带外。 也就是说，不能通过用于远程处理的同一网络连接发送它。 相反，您可以手动将它输入到客户端的配置中，或让客户端扫描 QR 代码。

**用例2：** 可以通过稳定的主机名来访问服务器。

在此用例中，服务器具有特定的主机名，并且你知道此名称不太可能更改。 然后，可以使用颁发给服务器的主机名的证书。 将基于主机名和证书的信任链来建立信任。

如果选择此选项，则客户端需要事先知道服务器的主机名和根证书。

### <a name="planning-the-client-to-server-authentication"></a>规划客户端到服务器的身份验证

客户端使用自由格式的令牌对服务器进行身份验证。 此标记应该包含的内容将再次依赖于你的使用情况：

**使用案例1：** 仅需验证客户端应用的标识。

在此用例中，共享机密就足够了。 此机密必须足够复杂，才能被猜出。

良好的共享机密是一个随机 GUID，它是在服务器和客户端的配置中手动输入的。 例如，若要创建一个，可以 `New-Guid` 在 PowerShell 中使用命令。

请确保此共享机密永远不会通过不安全的通道进行通信。 远程处理库确保始终以加密的形式发送共享机密，并确保只发送到受信任的对等方。

**用例2：** 还需要验证客户端应用程序的用户身份。

共享密钥不足以涵盖此用例。 相反，你可以使用标识提供程序创建的标记。 使用标识提供者的身份验证工作流如下所示：

* 客户端向标识提供程序授权，并请求令牌
* 标识提供程序生成一个令牌并将其发送到客户端
* 客户端通过全息远程处理将此令牌发送到服务器
* 服务器根据标识提供程序验证客户端的令牌

标识提供程序的一个示例是 [Microsoft 标识平台](https://docs.microsoft.com/azure/active-directory/develop/)。

与上一用例类似，请确保这些标记不通过不安全的通道发送或公开。

## <a name="implementing-holographic-remoting-security"></a>实现全息远程处理安全

请记住，如果要启用连接安全性，则需要实现自定义远程和播放器应用。 你可以使用提供的示例作为你自己的应用的起点。

若要启用安全性，请调用 `ListenSecure()` 而不是 `Listen()` ，而 `ConnectSecure()` 不是 `Connect()` 建立远程处理连接。

这些调用需要提供某些接口的实现，以便提供和验证与安全相关的信息：

* 服务器需要实现证书提供程序和身份验证验证程序
* 客户端需要实现身份验证提供程序和证书验证程序。

所有接口都有一个请求执行操作的函数，该函数接收回调对象作为参数。 使用此对象，可以轻松实现请求的异步处理。 保留对此对象的引用，并在异步操作完成时调用完成函数。 可以从任何线程调用完成函数。

>[!TIP]
>可使用 c + +/WinRT. 轻松实现 WinRT 接口 [带有 c + +/WinRT 的作者 api](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis)一章将对此进行详细介绍。

>[!IMPORTANT]
>`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet 包中的包含有关与安全连接相关的 API 的详细文档。

### <a name="implementing-a-certificate-provider"></a>实现证书提供程序

证书提供程序为服务器应用程序提供要使用的证书。 实现由两部分组成：

1) 用于实现接口的证书对象 `ICertificate` ：

    * `GetCertificatePfx()` 应返回证书存储的二进制内容 `PKCS#12` 。 `.pfx`文件包含 `PKCS#12` 数据，因此可直接在此处使用其内容。
    * `GetSubjectName()` 应返回标识要使用的证书的友好名称。 如果没有为证书指定友好名称，则此函数应返回证书的使用者名称。
    * `GetPfxPassword()` 应返回 (打开证书存储区所需的密码，如果) 不需要密码，则返回空字符串。

2) 用于实现接口的证书提供程序 `ICertificateProvider` ：
    * `GetCertificate()` 应构造一个证书对象并通过 `CertificateReceived()` 在回调对象上调用来返回该对象。

### <a name="implementing-an-authentication-validator"></a>实现身份验证验证程序

身份验证验证程序接收客户端发送的身份验证令牌，并使用验证结果回复。

实现该 `IAuthenticationReceiver` 接口，如下所示：

* `GetRealm()` 应返回 (在远程处理连接握手期间使用的 HTTP 领域的身份验证领域的名称) 。
* `ValidateToken()` 应该验证客户端身份验证令牌，并 `ValidationCompleted()` 通过验证结果对回调对象调用。

### <a name="implementing-an-authentication-provider"></a>实现身份验证提供程序

身份验证提供程序生成或检索要发送到服务器的身份验证令牌。

实现该 `IAuthenticationProvider` 接口，如下所示：

* `GetToken()` 应生成或检索要发送的身份验证令牌。 标记准备就绪后，调用 `TokenReceived()` 回调对象的方法。

### <a name="implementing-a-certificate-validator"></a>实现证书验证程序

证书验证程序接收服务器发送的证书链，并确定服务器是否可信任。

若要验证证书，可以使用基础系统的验证逻辑。 此系统验证可以支持您自己的验证逻辑，也可以全部替换。 如果在请求安全连接时未传递自己的证书验证程序，系统将自动使用系统验证。

在 Windows 上，系统验证将检查：

* 证书链的完整性：证书构成以受信任的根证书结尾的一致链
* 证书有效期：服务器的证书在其有效期内，并为服务器身份验证颁发
* 吊销：证书未被吊销
* 名称匹配：服务器的主机名与颁发证书的主机名之一匹配

实现该 `ICertificateValidator` 接口，如下所示：

 * `PerformSystemValidation()``true`如果应执行上述系统验证，应返回。 在这种情况下，系统验证结果将作为输入传递给 `ValidateCertificate()` 方法。
* `ValidateCertificate()` 应该验证证书链，然后 `CertificateValidated()` 在传递的回调上调用最终验证结果。 此方法接受证书链、与之建立连接的服务器的名称，以及是否应强制执行吊销检查。 如果证书链包含多个证书，则第一个证书是使用者证书。

>[!NOTE]
>如果用例需要不同形式的验证 (参阅) 上方的证书用例 #1，请完全绕过系统验证。 相反，请使用任何可处理 DER 编码的 x.509 证书的 API 或库来解码证书链，并执行用例所需的检查。

## <a name="secure-connection-using-the-openxr-api"></a>使用 OpenXR API 的安全连接

使用 [OPENXR API](../native/openxr.md) 时，与连接相关的所有安全 api 都作为 OpenXR 扩展的一部分提供 `XR_MSFT_holographic_remoting` 。

>[!IMPORTANT]
>若要了解全息远程处理 OpenXR 扩展 API，请查看可在[全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到的[规范](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)。

使用 OpenXR 扩展进行安全连接的关键元素 `XR_MSFT_holographic_remoting` 是以下回调。
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`、生成或检索要发送的身份验证令牌。
- `xrRemotingValidateServerCertificateCallbackMSFT`，验证证书链。
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`验证客户端身份验证令牌。
- `xrRemotingRequestServerCertificateCallbackMSFT`，为服务器应用程序提供要使用的证书。

可以通过和向远程处理 OpenXR 运行时提供这些 `xrRemotingSetSecureConnectionClientCallbacksMSFT` 回调 `xrRemotingSetSecureConnectionServerCallbacksMSFT` 。 此外，需要通过结构或结构上的 secureConnection 参数启用安全连接， `XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` 具体取决于你使用 `xrRemotingConnectMSFT` 的是还是 `xrRemotingListenMSFT` 。

此 API 类似于 [实现全息远程处理安全](#implementing-holographic-remoting-security)中所述的基于 IDL 的 api。 但是，你应该提供回调实现，而不是实现接口。 可在 [OpenXR 示例应用](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到详细的示例。

## <a name="see-also"></a>另请参阅
* [使用 Windows Mixed Reality Api 编写全息远程处理远程应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)
