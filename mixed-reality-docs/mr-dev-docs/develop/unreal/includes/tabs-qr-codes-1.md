---
ms.openlocfilehash: bcd9ae057f289d85d1f12d5cb79258bc3bb87ace
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443695"
---
# <a name="425"></a>[<span data-ttu-id="7ce08-101">4.25</span><span class="sxs-lookup"><span data-stu-id="7ce08-101">4.25</span></span>](#tab/425)

<span data-ttu-id="7ce08-102">没有特定于 UE 4.25 的其他启用步骤。</span><span class="sxs-lookup"><span data-stu-id="7ce08-102">There are no additional enabling steps specific to UE 4.25.</span></span>

# <a name="426"></a>[<span data-ttu-id="7ce08-103">4.26</span><span class="sxs-lookup"><span data-stu-id="7ce08-103">4.26</span></span>](#tab/426)

<span data-ttu-id="7ce08-104">如果你使用的是 UE 4.26，则建议使用以下蓝图设置来添加一个短暂延迟时间，因为必须在启动 AR 会话后初始化 QR 码跟踪：</span><span class="sxs-lookup"><span data-stu-id="7ce08-104">If you're using UE 4.26, we recommend using the following blueprint setup to add a small delay, because QR code tracking must be initialized AFTER starting an AR Session:</span></span>

![设有延迟时间的 Toggle ARCapture 函数的蓝图](../images/qr-codes-img-01.png)
