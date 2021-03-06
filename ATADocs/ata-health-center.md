---
title: 監視 Advanced Threat Analytics 系統健康狀態和事件 | Microsoft Docs
description: 使用 ATA 健康狀態中心來查看 ATA 服務的運作情況、收看潛在問題的警示，以及在事件檢視器中檢視系統事件。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: d6c783b2-46c5-4211-b21a-d6b17f08d03d
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 12d1a3f10cc3b9d99a20a2562ae4f81425ec9578
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133489"
---
*適用於：Advanced Threat Analytics 1.9 版*


# <a name="working-with-ata-system-health-and-events"></a>使用 ATA 系統健康狀態和事件

## <a name="ata-health-center"></a>ATA 健全狀況中心
ATA 健全狀況中心可讓您知道 ATA 服務的運作情況，並向您警示問題。

## <a name="working-with-the-ata-health-center"></a>使用 ATA 健全狀況中心
當功能表列中的健全狀況中心圖示上方出現警示 (一個紅點)，就是 ATA 健全狀況中心在告訴您有問題發生。

![ATA 健全狀況中心紅點工具列](media/ATA-Health-Center-Alert-red-dot.png)

### <a name="managing-ata-health"></a>管理 ATA 健全狀況
若要檢查系統的整體健全狀況，按一下功能表列中的健全狀況中心圖示 ![ATA 健全狀況中心圖示](media/ATA-red-dot.png)

-   將開啟的警示設定為 [關閉]、[隱藏] 或 [刪除]，或是按一下警示角落的三個點並選擇所要的選項，便能管理所有開啟的警示。

-   **開啟**：所有新的可疑活動都出現在此清單中。

-   **關閉**：用於追蹤您已識別、研究與修正以緩解的可疑活動。

    > [!NOTE]
    > 如果在短時間內偵測到相同的活動，ATA 可能會重新開啟已經關閉的活動。

-   **隱藏**：隱藏活動表示您想要暫時將它忽略，只有出現新的執行個體時才會再次收到警示。 如果有類似的警示，ATA 不會將它重新開啟。 但如果此警示在停止七天後再次出現，您便會再次收到警示。

- **刪除**：如果您刪除警示，則會將它從系統和資料庫中刪除，而且您將「無法」予以還原。 按一下 [刪除] 之後，您將可以刪除相同類型的所有可疑活動。



![ATA 健全狀況中心問題的圖片](media/ATA-Health-Issue.JPG)






## <a name="see-also"></a>另請參閱

- [處理可疑活動](working-with-suspicious-activities.md)
- [查看 ATA 論壇！](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
