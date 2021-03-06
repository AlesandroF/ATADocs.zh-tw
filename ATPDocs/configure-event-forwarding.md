---
title: 在 Azure 進階威脅防護中設定 Windows 事件轉寄 | Microsoft Docs
description: 描述使用 Azure ATP 設定 Windows 事件轉寄的選項
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 3547519f-8d9c-40a9-8f0e-c7ba21081203
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 90de9f0f02fa1b87fd2d741349a1d81e089b6fb1
ms.sourcegitcommit: bbbe808c08ce703a314c82b46aedaae79ab256a3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848519"
---
適用於：Azure 進階威脅防護



# <a name="configuring-windows-event-forwarding"></a>設定 Windows 事件轉送

> [!NOTE]
> Azure ATP 感應器會自動在本機讀取事件，而不需要設定事件轉寄。


為增強偵測功能，Azure ATP 需要下列 Windows 事件：4776、4732、4733、4728、4729、4756、4757 和 7045。 Azure ATP 感應器可以直接讀取這些事件。如果沒有部署 Azure ATP 感應器，則有兩種方法可以將之轉寄到 Azure ATP 獨立感應器：一種是將 Azure ATP 獨立感應器設定為接聽 SIEM 事件，另一種是設定 Windows 事件轉寄。

> [!NOTE]
> 檢查網域控制站是否已正確設定來擷取必要事件。

### <a name="wef-configuration-for-azure-atp-standalone-sensors-with-port-mirroring"></a>適用於具有連接埠鏡像之 Azure ATP 獨立感應器的 WEF 設定

設定從網域控制站到 Azure ATP 獨立感應器之間的連接埠鏡像之後，請依照下列指示以使用來源起始設定來設定 Windows 事件轉寄。 這是一個設定 Windows 事件轉送的方法。 

**步驟 1︰新增網路服務帳戶到網域 Event Log Readers 群組。** 

在此案例中，假設 Azure ATP 獨立感應器是網域的成員。

1.  開啟 [Active Directory 使用者和電腦]，瀏覽至 **BuiltIn** 資料夾，然後按兩下 [Event Log Readers]。 
2.  選取 [成員]。
3.  如果未列出 [Network Service]，請按一下 [新增]，在 [輸入要選取的物件名稱] 欄位中輸入 **Network Service**。 然後按一下 [檢查名稱]，再按兩次 [確定]。 

在將 [網路服務] 新增到 [Event Log Readers] 群組後，請重新啟動網域控制站，變更才會生效。

**步驟 2︰在網域控制站上建立原則以設定 [設定目標訂閱管理員] 設定。** 
> [!Note] 
> 您可以建立這些設定的群組原則，並將群組原則套用到 Azure ATP 獨立感應器監視的每個網域控制站。 下列步驟修改網域控制站的本機原則。     

1.  在每個網域控制站上執行下列命令︰*winrm quickconfig*
2.  在命令提示字元中輸入 *gpedit.msc*
3.  展開 [電腦設定] > [系統管理範本] > [Windows 元件] > [事件轉送]

 ![本機原則群組編輯器影像](media/wef%201%20local%20group%20policy%20editor.png)

4.  按兩下 [設定目標訂閱管理員]。
   
    1.  選取 [啟用]。
    2.  在 [選項] 下，按一下 [顯示]。
    3.  在 **SubscriptionManagers** 下方，輸入下列值，然後按一下 [確定]：*Server=`http://<fqdnATPSensor>:5985/wsman/SubscriptionManager/WEC,Refresh=10*` (例如：Server=`http://atpsensor9.contoso.com:5985/wsman/SubscriptionManager/WEC,Refresh=10`)
    
    ![設定目標訂閱影像](media/wef%202%20config%20target%20sub%20manager.png)
    
5.  按一下 [確定]。
6.  在提升權限的命令提示字元中，輸入 *gpupdate /force*。 

**步驟 3：在 Azure ATP 獨立感應器上執行下列步驟** 

1.  開啟提升權限的命令提示字元，輸入 *wecutil qc*
2.  開啟 [事件檢視器]。 
3.  以滑鼠右鍵按一下 [訂閱]，然後選取 [建立訂閱]。 

   1.   為訂閱輸入名稱和描述。 
   2.   針對 [目的地記錄檔]，請確認已選取 [轉送的事件]。 對於要讀取事件的 Azure ATP，目的地記錄檔必須是 [轉寄的事件]。 
   3.   選取 [來源電腦起始]，按一下 [選取電腦群組]。
        1.  按一下 [加入網域電腦]。
        2.  在 [輸入要選取的物件名稱] 欄位中輸入網域控制站的名稱。 然後按一下 [檢查名稱]，再按一下 [確定]。 
        3.  按一下 [確定]。
        ![事件檢視器影像](media/wef3%20event%20viewer.png)     
   4.   按一下 [選取事件]。
        1. 按一下 [依記錄]，然後選取 [安全性]。
        2. 在 [Includes/Excludes Event ID (包含/排除事件識別碼)] 欄位中鍵入事件編號，然後按一下 [確定]。 例如，鍵入 4776，如下列範例所示：![查詢篩選影像](media/wef-4-query-filter.png)
   5.   以滑鼠右鍵按一下建立的訂閱，然後選取 [執行階段狀態]，以查看該狀態是否有任何問題。 
   6.   幾分鐘後，請檢查您設定要轉寄的事件是否出現在 Azure ATP 上的 [轉送的事件] 中。


如需詳細資訊，請參閱[設定電腦以轉送和收集事件](https://technet.microsoft.com/library/cc748890)

## <a name="see-also"></a>另請參閱

- [安裝 Azure ATP](install-atp-step1.md)
- [查看 Azure ATP 論壇！](https://aka.ms/azureatpcommunity)
