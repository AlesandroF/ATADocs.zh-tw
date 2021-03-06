---
title: 以無訊息模式安裝 Azure 進階威脅防護 | Microsoft Docs
description: 說明如何以無訊息模式安裝 Azure ATP。
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/09/2017
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 24eca4c6-c949-42ea-97b9-41ef0fb611f1
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 23d92b207c9bcfeb38afa67bdd5e4911b1a16aa4
ms.sourcegitcommit: 02a4d7a0d44817da8e40580c5fe97f8839a7941f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48876574"
---
適用於：Azure 進階威脅防護


# <a name="azure-atp-switches-and-silent-installation"></a>Azure ATP 切換參數與無訊息安裝
此文章提供 Azure ATP 切換參數與無訊息安裝的指導方針與指示。

## <a name="prerequisites"></a>必要條件

Azure ATP 要求您必須安裝 Microsoft .NET Framework 4.7。 

當您安裝 Azure ATP 時，也會在部署 Azure ATP 之際自動安裝 .Net Framework 4.7。

> [!IMPORTANT] 
> 確定您已安裝最新版的 .Net Framework。 如已安裝舊版的 .Net，您的 Azure ATP 無訊息安裝會卡在迴圈中，無法安裝。 

> [!NOTE] 
> .Net Framework 4.7 的安裝可能需要重新啟動伺服器。 在網域控制站上安裝 Azure ATP 感應器時，請考慮為網域控制站排定維護時段。
使用 Azure ATP 無訊息安裝時，安裝程式是設定為在安裝結束時自動重新啟動伺服器 (如有必要)。 請務必只在維護時段執行無訊息安裝。 因為 Windows Installer 的某個錯誤 (Bug)，*norestart* 旗標無法可靠地用來確定伺服器不會重新啟動。

若要追蹤您的部署進度，請監視位於 **%AppData%\Local\Temp** 中的 Azure ATP 安裝程式記錄檔。



## <a name="azure-atp-sensor-silent-installation"></a>Azure ATP 感應器無訊息安裝

> [!NOTE]
> 使用 System Center Configuration Manager 或其他軟體部署系統，以無訊息模式部署 Azure ATP 感應器時，建議建立兩個部署套件：</br>- Net Framework 4.7，包括重新啟動網域控制站</br>- Azure ATP 感應器。 </br>讓 Azure ATP 感應器套件相依於 .Net Framework 套件的部署。 </br>取得 [.Net Framework 4.7 離線部署套件](https://support.microsoft.com/help/3186497/the-net-framework-4-7-offline-installer-for-windows)。 


使用下列命令執行 Azure ATP 感應器的完整無訊息解除安裝：


**語法**：

    Azure ATP sensor Setup.exe /AccessKey=<Access Key> /quiet NetFrameworkCommandLineArguments ="/q" 
   

> [!NOTE]
> 從 Azure ATP 入口網站的 [設定]、[感應器] 下，複製存取金鑰。


**安裝選項**：

> [!div class="mx-tableFixed"]
|名稱|語法|對無訊息安裝而言是否為必要？|說明|
|-------------|----------|---------|---------|
|Quiet|/quiet|是|執行安裝程式，但不顯示任何 UI 和提示。|
|[說明]|/help|否|提供說明和快速參考。 顯示安裝程式命令的正確用法，包括所有選項和行為清單。|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|是|指定 .Net Framework 安裝的參數。 必須設定，才能強制執行 .Net Framework 的無訊息安裝。|

**安裝參數**：

> [!div class="mx-tableFixed"]
|名稱|語法|對無訊息安裝而言是否為必要？|說明|
|-------------|----------|---------|---------|
|AccessKey|AccessKey="\*\*"|是|設定用來向 Azure ATP 工作區註冊 Azure ATP 感應器的存取金鑰。|

**範例**：若要以無訊息模式安裝 Azure ATP 感應器，請使用您的 Azure ATP 系統管理員認證登入已加入網域的電腦，以便不需要在安裝期間指定認證。 否則，請使用指定的認證向 Azure ATP 雲端服務註冊：

    "Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" 
    AccessKey="3WlO0uKW7lY6Lk0+dfkfkJQ0qZV6aSq5WxLf71+fuBhggCl/BMs9JxfAwi7oy9vYGviazUS1EPpzte7z8s4grw==" 
    

## <a name="update-the-azure-atp-sensor"></a>更新 Azure ATP 感應器

使用下列命令以無訊息模式更新 Azure ATP 感應器：

**語法**：

    Azure ATP sensor Setup.exe [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]


**安裝選項**：

> [!div class="mx-tableFixed"]
|名稱|語法|對無訊息安裝而言是否為必要？|說明|
|-------------|----------|---------|---------|
|Quiet|/quiet|是|執行安裝程式，但不顯示任何 UI 和提示。|
|[說明]|/help|否|提供說明和快速參考。 顯示安裝程式命令的正確用法，包括所有選項和行為清單。|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|是|指定 .Net Framework 安裝的參數。 必須設定，才能強制執行 .Net Framework 的無訊息安裝。|


**範例**：以無訊息模式更新 Azure ATP 感應器：

    Azure ATP sensor Setup.exe /quiet NetFrameworkCommandLineArguments="/q"

## <a name="uninstall-the-azure-atp-sensor-silently"></a>以無訊息模式將 Azure ATP 感應器解除安裝

使用下列命令執行 Azure ATP 感應器的無訊息解除安裝：**語法**：

    Azure ATP sensor Setup.exe [/quiet] [/Uninstall] [/Help]
    
**安裝選項**：

> [!div class="mx-tableFixed"]
|名稱|語法|對無訊息解除安裝而言是否為必要？|說明|
|-------------|----------|---------|---------|
|Quiet|/quiet|是|執行解除安裝程式，但不顯示任何 UI 和提示。|
|解除安裝|/uninstall|是|從伺服器中執行 Azure ATP 感應器的無訊息解除安裝。|
|[說明]|/help|否|提供說明和快速參考。 顯示安裝程式命令的正確用法，包括所有選項和行為清單。|

**範例**：以無訊息模式將 Azure ATP 感應器從伺服器解除安裝：


    Azure ATP sensor Setup.exe /quiet /uninstall
    



## <a name="see-also"></a>另請參閱

- [Azure ATP 必要條件](atp-prerequisites.md)
- [安裝 Azure ATP 感應器](install-atp-step4.md)
- [設定 Azure ATP 感應器](install-atp-step5.md)
- [查看 Azure ATP 論壇！](https://aka.ms/azureatpcommunity)
