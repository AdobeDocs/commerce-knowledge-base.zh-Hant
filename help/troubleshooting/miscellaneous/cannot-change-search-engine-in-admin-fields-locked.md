---
title: 無法變更'app/etc/env.php'中的搜尋引擎
description: 本文提供當您嘗試在Commerce管理員中變更搜尋引擎，但欄位鎖定的問題的解決方案。
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# 無法變更`app/etc/env.php`中的搜尋引擎

本文提供您嘗試從`app/etc/env.php`檔案移除搜尋引擎組態，但在重新部署後，組態會回覆成先前的設定，或是依預設變更為[!DNL OpenSearch]的問題的解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

您嘗試在「Commerce管理員」中變更搜尋引擎，但欄位已鎖定。

## 原因

搜尋引擎組態已鎖定在`app/etc/env.php`檔案中，或搜尋引擎已明確定義在`.magento.env.yaml`檔案中。

## 解決方案

1. 檢查部署階段下的`.magento.env.yaml`檔案，並檢視`SEARCH_CONFIGURATION`變數是否已設定。 範例：

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. `SEARCH_CONFIGURATION`變數是否存在？ 如果不存在，搜尋引擎設定預設會鎖定為[!DNL OpenSearch]。 若要變更組態，您必須使用搜尋引擎的適當值，將變數新增至`.magento.env.yaml`檔案。 如果`SEARCH_CONFIGURATION`變數存在，而且您想要修改引擎，請在`.magento.env.yaml`中取代引擎的現有值。 可能/已知的值： [!DNL opensearch]、[!DNL livesearch]、[!DNL elasticsuite]、[!DNL amasty_elastic]和[!DNL amasty_elastic_opensearch]。
1. 重新部署執行個體。
1. 管理員中的搜尋引擎欄位將維持鎖定狀態，但應該會以您指定的值更新。

## 相關閱讀

* 雲端基礎結構指南上的Commerce管理員中的[鎖定欄位](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) Commerce。
