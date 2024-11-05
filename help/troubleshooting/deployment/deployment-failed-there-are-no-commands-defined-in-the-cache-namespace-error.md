---
title: 「快取排清時部署失敗：『快取』名稱空間中未定義命令』錯誤」
description: 本文提供部署失敗並出現以下錯誤**快取名稱空間中未定義命令**時問題的解決方案。
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# 快取排清時部署失敗：「在&#39;cache&#39;名稱空間中未定義命令」錯誤

>[!WARNING]
>
>在執行這些步驟之前，請先在即時生產網站中備份資料庫（如果這樣做）。

本文提供部署失敗且記錄中其中一個錯誤看起來像這樣時，問題的解決方案：

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.4.x

## 問題

<u>要再現的步驟</u>：

嘗試部署。

<u>預期結果</u>：

您已成功部署。

<u>實際結果</u>：

您未成功部署。 在記錄檔中，您看到部署錯誤，訊息類似於下列&#x200B;*快取名稱空間*&#x200B;中沒有命令。

### 原因

**`core_config_data`**&#x200B;資料表包含資料庫中已不存在的商店ID或網站ID的設定。 當您從另一個執行個體/環境匯入資料庫備份，而且這些範圍的設定仍保留在資料庫中，儘管關聯的存放區/網站已被刪除時，就會發生這種情況。

### 解決方案

如果您只有一個網站，則網站的第二個測試不適用，您只需要測試商店。

若要解決此問題，請識別這些設定中剩餘的無效列。

1. SSH連線至伺服器並執行此命令：

   `bin/magento`

1. 錯誤訊息可能會指出哪些資料列和資料表從刪除的網站保留在資料庫中。 例如，下列錯誤指出找不到要求的存放區：

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. 執行此[!DNL MySQL]查詢以確認找不到存放區（由步驟2中的錯誤訊息所指示）。

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 執行下列[!DNL MySQL]陳述式以刪除無效的資料列：

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 再次執行此命令：

   `bin/magento`

   如果您收到類似以下的錯誤，指出找不到所要求的ID為X的網站，表示您還有設定        以及已刪除之商店的資料庫中。

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   執行此[!DNL MySQL]查詢並確認找不到網站：

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 執行此[!DNL MySQL]陳述式，從網站組態中刪除無效的資料列：

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

若要確認解決方案是否有效，請再次執行`bin/magento`命令。 您應該不會再看到錯誤，可以成功部署。

## 相關閱讀

* [Adobe Commerce部署疑難排解員](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter)
* [如果雲端UI有「記錄片段」錯誤，則檢查部署記錄](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
