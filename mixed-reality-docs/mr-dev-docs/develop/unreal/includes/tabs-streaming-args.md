---
ms.openlocfilehash: 12634c1fc18366e28a51688b19fc739ea69d37ec
ms.sourcegitcommit: 71c2a4884bd83599e35dd894771a5e43e951b574
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2021
ms.locfileid: "128184613"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| 选项 | 描述 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | 获取要连接到的 HoloLens 2 设备的 IP 地址（和可选端口）。 如果未提供任何端口，则默认值为 8265。 |
| `-RemotingBitrate=<bitrate>` | （可选）默认值 8000。 最大网络传输速率 (kb/s)。 |
| `-HoloLensRemotingListen` | （可选）启动侦听服务器 |
| `-HoloLensRemotingListenPort=<port>` | （可选）获取要在其上侦听的端口。 用于从 HoloLens 设备连接到电脑或 VM。 |
| `-HoloLens1Remoting=<IP address>` | （在 4.26 中弃用）获取要连接到的 HoloLens 1 设备的 IP 地址 |
| `-eyetracking=WindowsMixedRealityEyeTracker` | （可选）使用 Windows Mixed Reality 眼动追踪仪 |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| 选项 | 描述 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | 获取要连接到的 HoloLens 2 设备的 IP 地址（和可选端口，默认值为 8265），或应用应在其上侦听连接的端口。 |
| `-EnableAudio` | （可选）远程处理时使用来自电脑的音频  |
| `-Listen` | （可选）启动侦听服务器 |
| `-RemotingBitrate=<bitrate>` | （可选）默认值 8000。 最大网络传输速率 (kb/s)。 |
| `-RemotingCodec=<codec>` | （可选）连接编解码器  |
| `-eyetracking=OpenXREyeTracker` | （可选）使用 OpenXR 眼动追踪仪 |