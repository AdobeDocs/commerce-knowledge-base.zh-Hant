---
title: '[!DNL Advanced Reporting] Adobe Commerce發生404錯誤'
description: 本文針對當商家嘗試存取[[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html)時發生404錯誤時的Adobe Commerce問題提供修補程式。 安裝此修補程式後，使用者將能夠存取 [!DNL Advanced Reporting]。
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Adobe Commerce上的[!DNL Advanced Reporting] 404錯誤

本文提供當商家嘗試存取[[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html)時發生404錯誤時，Adobe Commerce問題的修補程式。 安裝此修補程式後，使用者將能存取[!DNL Advanced Reporting]。

若要檢查此修補程式是否能解決此問題，請先使用以下命令檢閱記錄檔：

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

如果您看到`Not valid cipher`錯誤，請套用附加的修補程式。

## 受影響的產品和版本

Adobe Commerce 2.2.6

## 問題

商家嘗試存取[!DNL Advanced Reporting]時發生404錯誤。

## 解決方案

若要修正此問題，請套用本文附加的修補程式。 若要下載，請向下捲動至文章結尾並按一下檔案名稱，或按一下下列連結： [下載MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## 如何套用修補程式

如需指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
