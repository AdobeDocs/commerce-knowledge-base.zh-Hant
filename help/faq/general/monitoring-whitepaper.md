---
title: 正在監視 [!DNL Adobe Commerce on cloud pro infrastructure]的資料工作表
description: 本檔案提供Adobe Commerce基礎架構監控和通知的相關資訊。
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 27fed162416c619a08d757279a3405f1fa72e976
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# 正在監視[!DNL Adobe Commerce on cloud pro infrastructure]的資料工作表

本檔案提供Adobe Commerce基礎架構監控和通知的相關資訊。

監控可讓商家、系統整合經銷商和Adobe的內部團隊疑難排解網站可用性和磁碟空間不足的問題。

## 問題疑難排解與解決

Adobe Commerce例項通常包含自訂程式碼和設定。 Adobe不支援或解決自訂程式碼和設定的問題。 Adobe確實協助商家疑難排解並找出我們知識庫中的問題，並提供預防和解決這些問題的建議解決方案和最佳實務。 我們鼓勵商家和合作夥伴使用下表來瞭解受監控的專案及負責解決問題的人員。

觸發通知時，Adobe Commerce支援團隊會分類問題。 作為分類的一部分，會分析錯誤記錄和其他資源。 根據分類結果，系統會建立其他[!DNL Zendesk]個支援票證給商家或合作夥伴（若是自訂更新）或Adobe的內部團隊以解決問題。

## Adobe Commerce：預設監視

以下事件會受到監控，Adobe Commerce團隊會採取必要步驟來解決和溝通發現的問題。

## 網站可用性監視

| 網站可用性 | 說明 |
|------------|------------|
| **監視目標** | 追蹤網站可用性。 |
| **檢測於** | 已為高[!DNL SLA]選取單一[!DNL URL]。 |
| **描述** | 網站可用性是根據測量結果周圍的設定臨界值來決定。 如果檢查在10分鐘內失敗，並且沒有正在進行的部署，則會觸發網站中斷通知。 |
| **通知收件者** | 商家/合作夥伴和Adobe。 |
| 由Adobe執行的&#x200B;**動作** | 如果問題發生在Adobe Commerce基礎架構上，則負責分類及修正。 |
| 商戶的&#x200B;**動作** | 負責修正因商家/合作夥伴引進的變更或自訂程式碼所造成的問題。 如需疑難排解，請參閱： [Site Down Troubleshooter](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=zh-Hant)。 |

## 磁碟空間監視

| 磁碟空間監視 | 說明 |
|------------|------------|
| **監視目標** | 追蹤磁碟空間使用狀況。 |
| **檢測於** | [!DNL MySQL]磁碟和媒體磁碟分割。 |
| **量度** | 每分鐘都會在主機上監視可用磁碟空間。 如果僅剩下5%或2GB可用空間，則會引發警告。 在剩餘可用空間設定的嚴重臨界值為2%或1GB。 |
| **描述** | 系統會根據設定在主機可用磁碟空間周圍的臨界值來傳送通知。 額外的磁碟空間會自動新增一次，以利相關掛載（[!DNL MySQL]或媒體）避免網站中斷，並讓商家有時間清除磁碟空間，及/或識別並解決造成磁碟使用量快速增加的任何程式碼或記錄檔。 |
| **通知收件者** | 商家/合作夥伴和Adobe。 |
| 由Adobe執行的&#x200B;**動作** | 自動提高支援票證，並將額外的磁碟空間自動新增至相關的掛載（[!DNL MySQL]或媒體），以防止網站中斷。 |
| 商戶的&#x200B;**動作** | 若要接收持續警告層級的磁碟空間警示，請參閱： <ul><li>[[!DNL Managed alerts for Adobe Commerce]：磁碟警告警示](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert)</li><li>[[!DNL Managed alerts for Adobe Commerce]：磁碟嚴重警示](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert) </li></ul> |
