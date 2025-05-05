---
title: Adobe Commerce [!DNL Site-Wide Analysis Tool] 報告常見問題集
description: 瞭解 [!DNL Site-Wide Analysis Tool]，主動式自助服務工具和中央存放庫，其中包含詳細的系統分析和建議，以確保您的Adobe Commerce安裝的安全性和可操作性。
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 580ad148cd4346868cd9892a1ae9a4d85f73edce
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Adobe Commerce [!DNL Site-Wide Analysis Tool]報告常見問題集

>[!IMPORTANT]
>
>自2024年4月23日起，所有Adobe Commerce內部部署客戶將停止使用[!DNL Site-Wide Analysis Tool]。

本文提供[!DNL Site-Wide Analysis Tool]報告的說明，該報告會每月或每季自動為雲端基礎結構上的Adobe Commerce客戶產生。

>[!NOTE]
>
>在Adobe Commerce雲端基礎結構v2.4.1和更新版本中，[!DNL Site-Wide Analysis Tool]可透過Commerce管理面板使用。 因此，客戶可以直接執行[!DNL Site-Wide Analysis Tool]報告。 如需存取詳細資訊，請參閱[[!DNL Site-Wide Analysis Tool] 指南](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html?lang=zh-Hant)。

## 什麼是[!DNL Site-Wide Analysis Tool]？

[!DNL Site-Wide Analysis Tool]是執行端對端「時間點」客戶網站分析的SaaS應用程式（在[!DNL Site-Wide Analysis Tool]環境中，而不是在客戶網站上）。 所有與[!DNL Site-Wide Analysis Tool]相關的客戶網站資訊會以預定排程收集，從每3小時收集到每天一次。 這表示[!DNL Site-Wide Analysis Tool]正在持續分析客戶網站資料以尋找發現。

## 什麼是[!DNL Site-Wide Analysis Tool]報告？

[!DNL Site-Wide Analysis Tool]報告是具有自助服務、最佳實務建議的發現（問題）清單，可透過Adobe Commerce支援票證系統以PDF表單傳送給客戶。

## [!DNL Site-Wide Analysis Tool]報告包含哪些資訊？

[!DNL Site-Wide Analysis Tool]報表中提供的網站資訊包括：

* 發現
   * 概述，包括實作修正順序的「優先順序」
   * 結果說明
   * 先決條件（如有）
   * 網站影響
   * 根本原因
   * 建議
* 例外狀況記錄檔
   * 記錄例外狀況資訊
   * 上次發生的日期
   * 例外發生的次數

## 誰會收到每月自動傳送的[!DNL Site-Wide Analysis Tool]報表？

目前，那些健全狀況指數低[!DNL Site-Wide Analysis Tool]的客戶（達到或低於目前設定的效能臨界值），將透過支援票證系統收到其生產環境的每月[!DNL Site-Wide Analysis Tool]報告。

## 誰會收到自動化每季[!DNL Site-Wide Analysis Tool]報告？

所有客戶（不論[!DNL Site-Wide Analysis Tool]健康情況指數為何）將透過支援票證系統收到其生產環境的每季[!DNL Site-Wide Analysis Tool]報告。

## 如何傳送報表？

每月或每季透過Adobe Commerce支援票證系統自動傳送[!DNL Site-Wide Analysis Tool]個報告。 [!DNL Site-Wide Analysis Tool]報告也可以從[!DNL Site-Wide Analysis Tool]儀表板手動產生，並儲存到您的案頭。 然後可將這[!DNL Site-Wide Analysis Tool]份報告以電子郵件的形式寄送為附件。

>[!NOTE]
>
>套用建議後，手動產生報告不會更新建議 — 可能需要幾天的時間才能從[!DNL Site-Wide Analysis Tool Dashboard]中將其移除。
