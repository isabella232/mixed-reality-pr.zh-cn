---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "96855875"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="076e6-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="076e6-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="076e6-102">选项</span><span class="sxs-lookup"><span data-stu-id="076e6-102">Option</span></span> | <span data-ttu-id="076e6-103">描述</span><span class="sxs-lookup"><span data-stu-id="076e6-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="076e6-104">获取要连接到的 HoloLens 2 设备的 IP 地址（和可选端口）。</span><span class="sxs-lookup"><span data-stu-id="076e6-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="076e6-105">如果未提供任何端口，则默认值为 8265。</span><span class="sxs-lookup"><span data-stu-id="076e6-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="076e6-106">（可选）默认值 8000。</span><span class="sxs-lookup"><span data-stu-id="076e6-106">(optional) Default 8000.</span></span> <span data-ttu-id="076e6-107">最大网络传输速率 (kb/s)。</span><span class="sxs-lookup"><span data-stu-id="076e6-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="076e6-108">（可选）启动侦听服务器</span><span class="sxs-lookup"><span data-stu-id="076e6-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="076e6-109">（可选）获取要在其上侦听的端口。</span><span class="sxs-lookup"><span data-stu-id="076e6-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="076e6-110">用于从 HoloLens 设备连接到电脑或 VM。</span><span class="sxs-lookup"><span data-stu-id="076e6-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="076e6-111">（在 4.26 中弃用）获取要连接到的 HoloLens 1 设备的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="076e6-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="076e6-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="076e6-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="076e6-113">选项</span><span class="sxs-lookup"><span data-stu-id="076e6-113">Option</span></span> | <span data-ttu-id="076e6-114">描述</span><span class="sxs-lookup"><span data-stu-id="076e6-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="076e6-115">获取要连接到的 HoloLens 2 设备的 IP 地址（和可选端口，默认值为 8265），或应用应在其上侦听连接的端口。</span><span class="sxs-lookup"><span data-stu-id="076e6-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="076e6-116">（可选）远程处理时使用来自电脑的音频</span><span class="sxs-lookup"><span data-stu-id="076e6-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="076e6-117">（可选）启动侦听服务器</span><span class="sxs-lookup"><span data-stu-id="076e6-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="076e6-118">（可选）默认值 8000。</span><span class="sxs-lookup"><span data-stu-id="076e6-118">(optional) Default 8000.</span></span> <span data-ttu-id="076e6-119">最大网络传输速率 (kb/s)。</span><span class="sxs-lookup"><span data-stu-id="076e6-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="076e6-120">（可选）连接编解码器</span><span class="sxs-lookup"><span data-stu-id="076e6-120">(optional) Connection codec</span></span>  |