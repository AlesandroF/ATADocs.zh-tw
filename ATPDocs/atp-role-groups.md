---
title: "適用於存取管理的 Azure 進階威脅防護角色群組 | Microsoft Docs"
description: "逐步引導您使用 Azure ATP 角色群組。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: effca0f2-fcae-4fca-92c1-c37306decf84
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 86cb55fd2b5ce81460dead4b8b753c88f79edd7b
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2018
---
適用於：Azure 進階威脅防護




# <a name="azure-atp-role-groups"></a>Azure ATP 角色群組

角色群組可針對 Azure ATP 啟用存取管理。 使用角色群組可以隔離安全性小組內的責任，並授與使用者執行工作所需的存取權。 本文說明存取管理和 Azure ATP 角色授權，並可協助您在 ATP 中開始使用角色群組。

> [!NOTE]
> 租用戶 Azure Active Directory 上的任何全域管理員或安全性系統管理員，都會自動是 Azure ATP 系統管理員。

## <a name="accessing-the-workspace-management-portal"></a>存取工作區管理入口網站

只有具備全域管理員或安全性系統管理員目錄角色的 Azure AD 使用者，才能存取工作區管理入口網站。 進入入口網站之後，您可以建立不同的工作區。 針對每個工作區，Azure ATP 服務會在 Azure Active Directory 租用戶中建立三個安全性群組：系統管理員、使用者、檢視者。 

> [!NOTE]
> Azure ATP 工作區入口網站的存取權只會授與工作區 Azure AD 安全性群組內的使用者，以及全域系統管理員和安全性系統管理員。


## <a name="types-of-azure-atp-security-groups"></a>Azure ATP 安全性群組的類型 

Azure ATP 導入三種類型的安全性群組：Azure ATP「工作區名稱」系統管理員，Azure ATP「工作區名稱」使用者和 Azure ATP「工作區名稱」檢視者。 下表描述每個角色在 Azure ATP 工作區入口網站中可用的存取類型。 根據您所指派的角色而定，Azure ATP 工作區入口網站中的某些畫面與功能表選項將會無法使用，如下所示︰

|活動 |Azure ATP「工作區名稱」系統管理員|Azure ATP「工作區名稱」使用者|Azure ATP「工作區名稱」檢視者|
|----|----|----|----|
|登入|可用|可用|可用|
|提供可疑活動的輸入|可用|可用|無法使用|
|變更可疑活動的狀態|可用|可用|無法使用|
|透過電子郵件/取得連結共用/匯出可疑的活動|可用|可用|無法使用|
|變更監視警示的狀態|可用|可用|無法使用|
|更新 Azure ATP 設定|可用|無法使用|無法使用|
|感應器 - 新增|可用|無法使用|無法使用|
|感應器 - 刪除 |可用|無法使用|無法使用|
|監視的 DC - 新增 |可用|無法使用|無法使用|
|監視的 DC - 刪除|可用|無法使用|無法使用|
|檢視警示及可疑的活動|可用|可用|可用|


當使用者嘗試存取不適用於其角色群組的頁面時，便會被重新導向至 Azure ATP 未授權頁面。 

## <a name="add-and-remove-users"></a>新增及移除使用者 

Azure ATP 使用 Azure AD 安全性群組作為角色群組的基礎。 可以從 [https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UserManagementMenuBlade/All groups](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UserManagementMenuBlade/All groups) 來管理角色群組。  只可以將 AAD 使用者加入或移除自安全性群組。 


## <a name="see-also"></a>另請參閱
- [ATA 調整大小工具](http://aka.ms/aatpsizingtool)
- [ATA 架構](atp-architecture.md)
- [安裝 ATA](install-atp-step1.md)
- [查看 ATP 論壇！](https://aka.ms/azureatpcommunity)\(英文\)
