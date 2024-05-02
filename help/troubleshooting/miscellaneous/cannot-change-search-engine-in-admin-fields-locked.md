---
title: 無法變更'app/etc/env.php'中的搜尋引擎
description: 本文提供當您嘗試在Commerce管理員中變更搜尋引擎，但欄位鎖定的問題的解決方案。
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# 無法變更中的搜尋引擎 `app/etc/env.php`

本文提供您嘗試從移除搜尋引擎設定的問題解決方案。 `app/etc/env.php` 檔案，但在重新部署後，設定將恢復為先前的設定或將變更為 [!DNL OpenSearch] 依預設。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce， [所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

您嘗試在「Commerce管理員」中變更搜尋引擎，但欄位已鎖定。

## 原因

搜尋引擎設定已鎖定於 `app/etc/env.php` 或搜尋引擎明確定義於 `.magento.env.yaml` 檔案。

## 解決方案

1. 檢查 `.magento.env.yaml` 在部署階段下的檔案，並檢視 `SEARCH_CONFIGURATION` 變數已設定。 範例：

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. 是  `SEARCH_CONFIGURATION` 出現變數嗎？ 如果不存在，則會將搜尋引擎設定鎖定到 [!DNL OpenSearch] 依預設。 若要變更設定，您必須將變數新增至 `.magento.env.yaml` 具有適當搜尋引擎值的檔案。 如果 `SEARCH_CONFIGURATION` 變數存在，而您想要修改引擎，請在中取代引擎的現有值 `.magento.env.yaml`. 可能/已知值： [!DNL opensearch]， [!DNL livesearch]， [!DNL elasticsuite]， [!DNL amasty_elastic]、和 [!DNL amasty_elastic_opensearch].
1. 重新部署執行個體。
1. 管理員中的搜尋引擎欄位將維持鎖定狀態，但應該會以您指定的值更新。

## 相關閱讀

* [Commerce管理員中的鎖定欄位](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) 雲端基礎結構指南中的Commerce 。
