---
title: 为全息远程处理启用连接安全性
description: 本页介绍如何将全息远程处理配置为在播放器和远程应用之间使用加密和经过身份验证的连接。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、安全性、身份验证、服务器到客户端
ms.openlocfilehash: fa23994ff4ab49d313fe24a67974bf4d90454e511658e0663c61d7b129b10f9e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223577"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>为全息远程处理启用连接安全性

>[!IMPORTANT]
>本指南特定于全息远程处理HoloLens 2。

本页概述了全息远程处理的网络安全性。 你将找到有关

* 全息远程处理上下文中的安全性以及可能需要它的原因
* 基于不同用例的建议度量值
* 在全息远程处理解决方案中实现安全性

## <a name="holographic-remoting-security"></a>全息远程处理安全性

全息远程处理通过网络交换信息。 如果没有安全措施，则同一网络上攻击者可能会破坏通信的完整性或访问机密信息。

示例应用和 Windows Store 中的全息远程处理播放器已禁用安全性。 这样做可使示例更易于理解。 它还可帮助你更快速地开始开发。

对于现场测试或生产，强烈建议在全息远程处理解决方案中启用安全性。

如果为用例正确设置了全息远程处理中的安全性，则提供以下保证：

* **真实性** ：播放器和远程应用都可以确保另一端是他们声称是谁
* **保密性：** 没有任何第三方可以读取播放器和远程应用之间交换的信息
* **完整性：** 播放器和远程设备可以检测其通信的任何传输中更改

>[!IMPORTANT]
>若要使用安全功能，需要同时使用自定义[播放器](holographic-remoting-create-player.md)和自定义远程应用，Windows Mixed Reality [OpenXR](holographic-remoting-create-remote-openxr.md) API。 [](holographic-remoting-create-remote-wmr.md)

>[!NOTE]
> 从版本 [2.4.0](holographic-remoting-version-history.md#v2.4.0) 开始，可以使用 [OpenXR API](../native/openxr.md) 创建远程应用。 下面概述了如何在 OpenXR 环境中建立安全 [连接](#secure-connection-using-the-openxr-api)。

## <a name="planning-the-security-implementation"></a>规划安全实现

在全息远程处理中启用安全性时，远程处理库将自动为通过网络交换的所有数据启用加密和完整性检查。

但是，确保适当的身份验证需要一些额外的工作。 具体需要执行哪些操作取决于用例，本部分的余下内容是确定必要的步骤。

>[!IMPORTANT]
> 本文只能提供一般指导。 如果不确定，请考虑咨询安全专家，该专家可针对用例提供相关指导。

首先使用一些术语：描述网络连接时，将使用术语 _"客户端__"和_"服务器"。 服务器是侦听已知终结点地址上的传入连接的端，客户端是连接到服务器终结点的端。

>[!NOTE]
> 客户端和服务器角色不与应用是充当播放器还是远程角色有关。 虽然示例具有服务器角色中的播放器，但如果它们更适合你的用例，则很容易反转角色。

### <a name="planning-the-server-to-client-authentication"></a>规划服务器到客户端身份验证

服务器使用数字证书向客户端证明其身份。 客户端在连接握手阶段验证服务器的证书。 如果客户端不信任服务器，则此时将结束连接。

客户端如何验证服务器证书以及可以使用哪些类型的服务器证书取决于用例。

**用例 1：** 服务器主机名未固定，或者服务器不按主机名寻址。

在此用例中，不可行 (甚至) 服务器主机名颁发证书。 建议改为验证证书的指纹。 与人类指纹一样，指纹唯一标识证书。

将指纹与带外客户端通信非常重要。 这意味着，无法通过用于远程处理的同一网络连接发送它。 相反，你可以手动在客户端的配置中输入它，或让客户端扫描 QR 码。

**用例 2：** 可以通过稳定的主机名访问服务器。

在此用例中，服务器具有特定的主机名，并且你知道此名称不太可能更改。 然后，可以使用颁发给服务器的主机名的证书。 将基于主机名和证书的信任链建立信任关系。

如果选择此选项，客户端需要提前知道服务器的主机名和根证书。

### <a name="planning-the-client-to-server-authentication"></a>规划客户端到服务器身份验证

客户端使用自由格式令牌对服务器进行身份验证。 此令牌应包含哪些内容将再次取决于用例：

**用例 1：** 只需验证客户端应用的标识。

在此用例中，共享机密就足够了。 此机密必须足够复杂，无法猜出。

良好的共享机密是随机 GUID，在服务器的 和客户端的配置中手动输入。 例如，若要创建一个，可以在 `New-Guid` PowerShell 中使用 命令。

确保永远不会通过不安全的通道传达此共享机密。 远程处理库可确保共享机密始终以加密方式发送到受信任的对等方。

**用例 2：** 还需要验证客户端应用用户的标识。

共享机密不足以涵盖此用例。 相反，可以使用标识提供者创建的令牌。 使用标识提供者的身份验证工作流将如下所示：

* 客户端对标识提供者授权并请求令牌
* 标识提供者生成令牌并将其发送到客户端
* 客户端通过全息远程处理将此令牌发送到服务器
* 服务器针对标识提供者验证客户端的令牌

标识提供者的一个示例[是Microsoft 标识平台。](/azure/active-directory/develop/)

与前面的用例一样，请确保这些令牌不会通过不安全的通道发送，或者不会以其他方式公开。

## <a name="implementing-holographic-remoting-security"></a>实现全息远程处理安全性

请记住，如果要启用连接安全性，则需要实现自定义远程和播放器应用。 可以使用提供的示例作为你自己的应用的起点。

若要启用安全性，请调用 而不是 `ListenSecure()` `Listen()` 和 `ConnectSecure()` 来 `Connect()` 建立远程处理连接。

这些调用要求你提供某些接口的实现，以提供和验证安全相关信息：

* 服务器需要实现证书提供程序和身份验证验证程序
* 客户端需要实现身份验证提供程序和证书验证程序。

所有接口都有一个函数，该函数请求你采取措施，该函数接收回调对象作为参数。 使用此对象可以轻松实现请求的异步处理。 保留对此 对象的引用，在异步操作完成时调用完成函数。 完成函数可能从任何线程调用。

>[!TIP]
>使用 C++/WinRT 可以轻松实现 WinRT 接口。 使用 [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis) 创作 API 一章对此进行详细介绍。

>[!IMPORTANT]
>包 `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` 内的 NuGet包含有关安全连接的相关 API 的详细文档。

### <a name="implementing-a-certificate-provider"></a>实现证书提供程序

证书提供程序为服务器应用程序提供使用的证书。 实现包括两个部分：

1) 实现 接口的证书 `ICertificate` 对象：

    * `GetCertificatePfx()` 应返回证书存储的二 `PKCS#12` 进制内容。 `.pfx`文件包含 `PKCS#12` 数据，因此可以直接在此处使用其内容。
    * `GetSubjectName()` 应返回标识要使用的证书的友好名称。 如果未为证书分配友好名称，则此函数应返回证书的主题名称。
    * `GetPfxPassword()` 如果不需要密码，则 应返回打开证书存储 () 或空字符串。

2) 实现 接口的证书 `ICertificateProvider` 提供程序：
    * `GetCertificate()` 应构造证书对象，然后通过调用回调对象 `CertificateReceived()` 来返回它。

### <a name="implementing-an-authentication-validator"></a>实现身份验证验证程序

身份验证验证程序接收客户端发送的身份验证令牌，并返回验证结果。

按 `IAuthenticationReceiver` 如下所示实现 接口：

* `GetRealm()` 应返回在远程处理连接握手期间 (HTTP 领域的身份验证领域) 。
* `ValidateToken()` 应验证客户端身份验证令牌，并 `ValidationCompleted()` 调用具有验证结果的回调对象。

### <a name="implementing-an-authentication-provider"></a>实现身份验证提供程序

身份验证提供程序生成或检索要发送到服务器的身份验证令牌。

按 `IAuthenticationProvider` 如下所示实现 接口：

* `GetToken()` 应生成或检索要发送的身份验证令牌。 令牌准备就绪后，对 `TokenReceived()` 回调对象调用 方法。

### <a name="implementing-a-certificate-validator"></a>实现证书验证程序

证书验证程序接收服务器发送的证书链，并确定服务器是否可以受信任。

若要验证证书，可以使用基础系统的验证逻辑。 此系统验证可以支持自己的验证逻辑，也可以完全替换它。 如果在请求安全连接时没有传递自己的证书验证程序，系统验证将自动使用。

在Windows，系统验证将检查：

* 证书链的完整性：证书形成以受信任的根证书结尾的一致链
* 证书有效性：服务器的证书在其有效期范围内，颁发用于服务器身份验证
* 吊销：证书尚未吊销
* 名称匹配：服务器的主机名与颁发证书的主机名之一匹配

按 `ICertificateValidator` 如下所示实现 接口：

 * `PerformSystemValidation()` 如果应 `true` 执行上述系统验证，则 应返回 。 在这种情况下，系统验证结果作为输入传递给 `ValidateCertificate()` 方法。
* `ValidateCertificate()` 应验证证书链，然后使用最终验证结果 `CertificateValidated()` 对传递的回调调用 。 此方法接受证书链、建立连接的服务器的名称，以及是否应该强制吊销检查。 如果证书链包含多个证书，则第一个证书是主题证书。

>[!NOTE]
>如果用例需要另一种形式的验证 (请参阅上述证书用例#1，) 完全绕过系统验证。 请改为使用可以处理 DER 编码的 X.509 证书的任何 API 或库来解码证书链并执行用例所需的检查。

## <a name="secure-connection-using-the-openxr-api"></a>使用 OpenXR API 保护连接

使用 [OpenXR API 时](../native/openxr.md) ，所有安全连接相关 API 都作为 `XR_MSFT_holographic_remoting` OpenXR 扩展的一部分提供。

>[!IMPORTANT]
>若要了解全息远程处理 OpenXR 扩展 API，请查看可在全息远程[](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)处理示例 github 存储库 找到[的规范](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)。

使用 OpenXR 扩展进行安全 `XR_MSFT_holographic_remoting` 连接的关键元素是以下回调。
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`、生成或检索要发送的身份验证令牌。
- `xrRemotingValidateServerCertificateCallbackMSFT`验证证书链。
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`验证客户端身份验证令牌。
- `xrRemotingRequestServerCertificateCallbackMSFT`，为服务器应用程序提供使用的证书。

可以通过 和 向远程处理 OpenXR 运行时提供这些 `xrRemotingSetSecureConnectionClientCallbacksMSFT` 回调 `xrRemotingSetSecureConnectionServerCallbacksMSFT` 。 此外，需要在 结构或 结构上通过 secureConnection 参数启用安全连接，具体取决于 `XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` 使用的是 还是 `xrRemotingConnectMSFT` `xrRemotingListenMSFT` 。

此 API 类似于实现全息远程处理安全性中所述的基于 IDL[的 API。](#implementing-holographic-remoting-security) 但是，应该提供回调实现，而不是实现接口。 可以在 OpenXR 示例应用中 [找到详细示例](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)。

## <a name="see-also"></a>另请参阅
* [使用远程 API 编写全息远程Windows Mixed Reality应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR API 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)