---
title: 在雲端基礎結構上移除Adobe Commerce的Blackfire存取權
description: 自2020年4月11日起，免費存取的Blackfire效能監控將不再包含在Adobe Commerce雲端基礎結構專業版計畫架構或Adobe Commerce雲端基礎結構入門計畫架構訂閱中。  您將無法再登入您的Blackfire帳戶。 在4月11日以後可以直接透過Blackfire.io購買授權，以繼續使用Blackfire。 Adobe Commerce商戶如果尚未在該日期前直接從Blackfire購買授權，將停用其免費的Adobe提供Blackfire授權。 除此之外，使用「效能評測器」工具建立新報告的功能將會停用。 使用雲端基礎結構上代管的Pro架構的客戶，仍可透過New Relic基礎結構免費監控基礎結構效能。
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# 在雲端基礎結構上移除Adobe Commerce的Blackfire存取權

自2020年4月11日起，免費存取的Blackfire效能監控將不再包含在Adobe Commerce雲端基礎結構專業版計畫架構或Adobe Commerce雲端基礎結構入門計畫架構訂閱中。  您將無法再登入您的Blackfire帳戶。 在4月11日以後可以直接透過Blackfire.io購買授權，以繼續使用Blackfire。 Adobe Commerce商戶如果尚未在該日期前直接從Blackfire購買授權，將停用其免費的Adobe提供Blackfire授權。 除此之外，使用「效能評測器」工具建立新報告的功能將會停用。 使用雲端基礎結構上代管的Pro架構的客戶，仍可透過New Relic基礎結構免費監控基礎結構效能。

**如果您要繼續使用Blackfire**：

1. 您必須直接以Blackfire購買授權。
1. 然後使用這些[步驟](https://blackfire.io/docs/integrations/paas/magentocloud)設定Blackfire。
1. 如果您在安裝時遇到任何困難，可以[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以要求協助。 如需Blackfire的特定問題，請直接在[support@blackfire.io](mailto:support@blackfire.io)聯絡Blackfire支援。

## 如果您在執行部署時發生錯誤：

如果執行部署時收到Blackfire相關錯誤，請執行下列動作：

1. 從設定中移除Blackfire。 編輯`.magento.app.yaml`檔案並從執行階段區段中移除Blackfire：

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. 在本機開發環境中完成此作業，並推送至雲端。

若您在執行部署後看到下列錯誤，則僅[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)：

*PHP警告： PHP啟動：無法載入動態程式庫&#39;blackfire.so&#39; (已嘗試： /usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so：無法開啟共用物件檔案：沒有這類檔案或目錄)、/usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so：無法開啟共用物件檔案：沒有這類檔案或目錄))，位於未知的線上0*

此錯誤表示Blackfire外掛程式必須更新並停止載入。

**如果您想使用New Relic基礎結構**：

若要瞭解如何存取New Relic基礎結構，請參閱我們的支援知識庫中的[存取New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html)。
