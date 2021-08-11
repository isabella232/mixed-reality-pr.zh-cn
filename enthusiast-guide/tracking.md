---
title: 跟踪常见问题解答
description: 跟踪Windows Mixed Reality超出标准使用者支持文档的故障排除。
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 故障排除， 错误， 帮助， 支持， 跟踪
ms.openlocfilehash: fe5462a53de7b196db37edbbf0e56199a17c4c99b54ea1e7d9edf72e0845c9e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199473"
---
# <a name="tracking-faqs"></a>跟踪常见问题解答

## <a name="my-headset-has-stopped-tracking"></a>我的头戴显示设备已停止跟踪

确保灯亮起，并且头戴显示设备正面没有任何遮挡外侧跟踪相机。 如果跟踪丢失，可能需要几秒钟才能恢复。 重启Windows Mixed Reality门户跟踪不会重启。

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>我可以四处查看，但无法 (我停滞在 3DOF) 

这意味着跟踪系统无法生成姿势，或者应用程序已停止使用新的姿势数据进行呈现。 若要解决这一问题，请执行以下操作：

* 确保房间有足够的光线。
* 确保房间有足够的详细信息进行跟踪。
* 拔下设备，Windows Mixed Reality，然后再次插入设备。
* 如果消息仍然存在，请联系 [客户支持](https://support.microsoft.com/)

## <a name="the-view-in-the-hmd-is-frozen"></a>HMD 中的视图被冻结

这通常意味着应用程序或系统级别组件已失败。 尝试：

1. 按"主页"按钮离开应用程序。
2. 拔下设备，关闭 MRP，然后重新插入设备。
3. 重启电脑。

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>世界在恢复正常之前短暂冻结、倾斜或翻转

这可能是由应用程序或系统级别组件出现严重错误或内存或 CPU 资源暂时不足导致的。 检查：

1. 打开任务管理器，并确保至少有 20% 的 CPU 可用，400 MB 内存可用，磁盘 IO 应低于 80%。
2. 转到 **事件查看器 > Windows日志>"** 应用程序"，查找冻结时间左右的任何错误。 查找任何引用HoloLens传感器、混合现实或你大约在当时运行的应用程序。 这些日志可能会解释导致失败的原因。
3. 如果问题仍然存在，请重启电脑。

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>世界暂时翻转并恢复正常

这通常是由于从头戴显示设备获取传感器数据以通知跟踪算法时出错导致的。 如果这种情况频繁发生：

1. 将头戴显示设备插入不同的 USB 3.0 端口。
2. 将头戴显示设备直接插入电脑，而不是插入 USB 3.0 集线器。
3. 如果问题仍然存在，请联系 [客户支持](https://support.microsoft.com/)。

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>世界是倾斜的，但我可以在Windows Mixed Reality

如果传感器数据错误记录到电脑上的环境数据中，则可能会导致Windows Mixed Reality看起来倾斜，有时是永久性的。 解决方法：

1. 拔下头戴显示设备，Windows Mixed Reality头戴显示设备，然后重新插入头戴显示设备。
2. 重启电脑。
3. 清除环境数据。