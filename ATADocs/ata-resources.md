---
title: Advanced Threat Analytics 資源及整備藍圖 |Microsoft Docs
description: 提供 ATA 資源、影片、使用者入門、部署和整備藍圖連結的清單。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/15/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 42a1a34f-ed6b-4538-befb-452168a30e8c
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 48756cbde8b288116975c05567beeac76e83a717
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133764"
---
*適用於：Advanced Threat Analytics 1.9 版*

# <a name="ata-readiness-roadmap"></a>ATA 整備藍圖 
本文件提供整備藍圖，協助您開始使用 Advanced Threat Analytics。

## <a name="understanding-ata"></a>了解 ATA

Advanced Threat Analytics (ATA) 是內部部署平台，可協助保護您的企業免於受到多種進階鎖定目標類型的網路攻擊和內部威脅。 您可以利用下列資源深入了解 ATA：

- [ATA 概觀](what-is-ata.md)

- [ATA 簡介影片 - 簡短版](https://aka.ms/ATAShort)

- [ATA 簡介影片 - 完整版](https://aka.ms/ATAVideo) 


## <a name="deployment-decisions"></a>部署決定

ATA 由 ATA 中心和 ATA 閘道構成，您可將前者安裝在伺服器上，並將後者安裝於其他電腦上，也可直接在您的網域控制站上使用輕量型閘道。 在啟動並執行前，請務必先決定下列部署項目：

|設定|決定|
|----|----|
|硬體類型|實體、虛擬、Azure VM|
|工作群組或網域|工作群組、網域|
|閘道大小|完整閘道、輕量型閘道|
|憑證|PKI、自我簽署|

如果目前使用實體伺服器，則應規劃容量。 為 ATA 配置空間時，可從調整大小工具取得協助：

[ATA 調整大小工具](ata-capacity-planning.md) - 調整大小的工具會自動收集 ATA 所需的流量多寡。 其會自動為 ATA 中心和 ATA 輕量型閘道提供支援能力以及資源建議。

[ATA 容量規劃](ata-capacity-planning.md)

## <a name="deploy-ata"></a>部署 ATA

這些資源可協助您下載並安裝 ATA 中心、連線至 Active Directory、下載 ATA 閘道套件、設定事件收集，也可與您的 VPN 整合，及設定 honeytoken 帳戶和排除項目。

[下載 ATA](http://aka.ms/ataeval) - 在部署 ATA 前，若尚未決定是否要購買 ATA，可下載評估版。 

[ATA POC 實戰手冊](http://aka.ms/atapoc) - 成功進行 ATA POC 部署的指南，內含所需的所有步驟。

[ATA 部署影片](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes) - 這段影片簡介 ATA 部署步驟，總長在 10 分鐘內。

## <a name="ata-settings"></a>ATA 設定

ATA 中的基本必要設定，會一併於安裝精靈作業中進行。 但您仍可進行一些其他設定來微調 ATA，更正確地偵測環境，例如 SIEM 整合和稽核設定。

[稽核設定](https://aka.ms/ataauditingblog) – 在ATA 部署前後，稽核網域控制站的健全狀況。

[ATA 一般文件](https://docs.microsoft.com/advanced-threat-analytics/)

## <a name="work-with-ata"></a>使用 ATA

ATA 開始運作之後，您即可檢視在攻擊時間表中偵測到的可疑活動。 這是您登入 ATA 主控台時會前往的預設登陸頁面。 根據預設，所有開啟的可疑活動都會顯示在攻擊時間表上。 您也可以查看指派給每個活動的嚴重性。 透過向下切入實體 (電腦、裝置、使用者) 來開啟其提供詳細資訊的設定檔頁面，以調查每項可疑活動。 以下資源有助於您處理 ATA 的可疑活動：

[ATA 可疑活動實戰手冊](http://aka.ms/ataplaybook) - 本文會運用網際網路上現成的研究工具，逐步說明認證竊取攻擊技巧。 您可了解 ATA 如何協助您掌握每個攻擊面所帶來的威脅。

[ATA 可疑活動指南](suspicious-activity-guide.md)



## <a name="security-best-practices"></a>安全性最佳做法

[ATA 最佳做法](https://aka.ms/atasecbestpractices) - 保護 ATA 安全的最佳做法。

[ATA 常見問題集](ata-technical-faq.md) - 本文提供有關 ATA 的常見問題清單，並提供深入分析和解答。

## <a name="additional-resources"></a>其他資源

[Microsoft 安全性 Channel 9 頁面](https://channel9.msdn.com/Shows/Microsoft-Security/)

## <a name="community-resources"></a>社群資源

[ATA 部落格](https://aka.ms/ATABlog)
[ATA 社群](https://aka.ms/ATACommunity)
[提供有關 ATA 的意見反應](https://aka.ms/ATAUserVoice)
