---
ms.openlocfilehash: 283ef0bedc96a63d34a66fa0d88dee97420957c7744ad3702c6ac3bc34c14310
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218851"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| 选项 | 描述 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | 获取要连接到的 HoloLens 2 设备的 IP 地址（和可选端口）。 如果未提供任何端口，则默认值为 8265。 |
| `-RemotingBitrate=<bitrate>` | （可选）默认值 8000。 最大网络传输速率 (kb/s)。 |
| `-HoloLensRemotingListen` | （可选）启动侦听服务器 |
| `-HoloLensRemotingListenPort=<port>` | （可选）获取要在其上侦听的端口。 用于从 HoloLens 设备连接到电脑或 VM。 |
| `-HoloLens1Remoting=<IP address>` | （在 4.26 中弃用）获取要连接到的 HoloLens 1 设备的 IP 地址 |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| 选项 | 描述 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | 获取要连接到的 HoloLens 2 设备的 IP 地址（和可选端口，默认值为 8265），或应用应在其上侦听连接的端口。 |
| `-EnableAudio` | （可选）远程处理时使用来自电脑的音频  |
| `-Listen` | （可选）启动侦听服务器 |
| `-RemotingBitrate=<bitrate>` | （可选）默认值 8000。 最大网络传输速率 (kb/s)。 |
| `-RemotingCodec=<codec>` | （可选）连接编解码器  |