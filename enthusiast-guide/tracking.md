---
title: 跟踪常见问题解答
description: 跟踪 Windows Mixed Reality 故障排除，这超出了标准使用者支持文档的范围。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，跟踪
ms.openlocfilehash: 2634b95cf876a5b540710f80d3dd7f9d48b3bad9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725828"
---
# <a name="tracking-faqs"></a>跟踪常见问题解答

## <a name="my-headset-has-stopped-tracking"></a>我的耳机已停止跟踪

请确保指示灯亮起，并且没有任何内容阻碍耳机前面的内部跟踪相机。 如果跟踪丢失，可能需要几秒钟才能恢复。 重新启动 Windows Mixed Reality 门户将不会重新启动。

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>我可以找出，但无法转换 (我在3DOF 中停滞) 

这意味着跟踪系统无法生成姿势，或应用程序已停止使用新的姿势数据来呈现。 若要解决这一问题，请执行以下操作：

* 请确保空间充足。
* 请确保会议室有足够的详细信息可供跟踪。
* 拔出设备，关闭 Windows Mixed Reality，并再次插入设备。
* 如果消息仍然存在，请联系 [客户支持部门](https://support.microsoft.com/)

## <a name="the-view-in-the-hmd-is-frozen"></a>HMD 中的视图已冻结

这通常意味着应用程序或系统级组件发生了故障。 尝试执行以下操作：

1. 按 "home" 按钮退出应用程序。
2. 拔出设备，关闭 MRP，并重新插入设备。
3. 重启电脑。

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>在返回到正常状态之前，世界短暂冻结、倾斜或翻转

这可能是由于应用程序或系统级别组件遇到致命错误或暂时缺少内存或 CPU 资源而导致的。 若要检查：

1. 打开任务管理器，确保至少20% 的 CPU 空闲，400 MB 可用内存，磁盘 IO 应该低于80%。
2. 请参阅 **事件查看器 > Windows 日志 > 应用程序** ，以查看冻结时间周围的任何错误。 查找所有引用 HoloLens 传感器、混合现实或在此时间段内运行的应用程序的内容。 这些日志可能解释导致失败的原因。
3. 如果问题仍然存在，请重启电脑。

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>世界翻转并返回到正常

这通常是由于从耳机获取传感器数据以通知跟踪算法时出错引起的。 如果经常发生这种情况：

1. 将耳机插入到其他 USB 3.0 端口。
2. 将耳机直接插入 PC 而不是 USB 3.0 集线器。
3. 如果问题仍然存在，请与 [客户支持](https://support.microsoft.com/)联系。

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>世界是倾斜的，但我可以在 Windows Mixed Reality 中导航和四处浏览

如果传感器数据错误记录到电脑上的环境数据中，则可能会导致 Windows Mixed Reality 显示为倾斜，有时会永久显示。 解决方法：

1. 拔出耳机，关闭 Windows Mixed Reality 并插上耳机。
2. 重启电脑。
3. 清除你的环境数据。