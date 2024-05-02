---
title: 疑難排解Adobe Commerce中的產品Recommendations模組
description: 本文會討論下列專案的疑難排解建議：
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 疑難排解Adobe Commerce中的產品Recommendations模組

本文會討論下列專案的疑難排解建議：

```php
magento/product-recommendations
```

模組及其相依性

```php
saas-export
```

模組，因為您需要兩個模組都運作，才能在Adobe Commerce中使用產品Recommendations工具。

## 受影響的產品和版本

* Adobe Commerce 2.4.4 - 2.4.7

## 產品建議模組疑難排解

如果您已設定

```php
magento/product-recommendations
```

模組正確(檢查 [產品Recommendations — 安裝和設定Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) （位於我們的開發人員檔案中），但是您沒有看到任何建議，請嘗試下列步驟：

* 模組可能沒有足夠的時間來收集行為資料。 允許系統執行24小時，以便開始收集資料。 請考慮部署不需要任何行為資料的建議型別，例如「更多與此類似的專案」。

* 如果您沒有看到您設定的建議，可能沒有足夠的資料可為使用者建置建議。

* 請確定SaaS資料空間或API金鑰有效。 如果在產品建議初始化期間指定SaaS資料空間或API金鑰時發生錯誤，請檢查以確保您已輸入 [SaaS資料空間和API金鑰](https://docs.magento.com/user-guide/configuration/services/saas.html) （位於使用手冊中）正確無誤。 若要確保MageID和API金鑰已連結，擁有MageID的使用者(通常是擁有Adobe Commerce授權的使用者)必須是產生API金鑰的相同使用者。 如果您必須變更已使用的MageID， [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>如果 [Cookie限制模式](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html) （位於我們的使用手冊中）已啟用後，Adobe Commerce會收集行為資料，直到購物者同意為止。 如果「Cookie限制模式」已停用，Adobe Commerce會依預設收集行為資料。

## 目錄SaaS匯出模組

關於目錄SaaS匯出的相關問題(

```php
saas-export
```

)模組：

1. 確認 [cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html) （在開發人員檔案中）工作正在執行中。
1. 確認 [索引子](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html) （在開發人員檔案中）執行中，而    ```php    Product Feed    ```    索引子設定為    ```php    Update by Schedule    ```    .
1. 確認模組已啟用。 此    ```php    saas-export    ```    Metapackage會安裝下列模組，且必須啟用所有模組：    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. 檢查 [記錄檔](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html) （在開發人員檔案中）。 請確定沒有與上述模組相關聯的錯誤。
1. 重新整理設定快取。 前往 **系統** > **工具** > **快取管理** ，並清除設定快取。
1. 確認    ```php    catalog_data_exporter_products    ```    資料庫表格。

## 活動

[建議事件](https://devdocs.magento.com/recommendations/verify.html)，在我們的開發人員檔案中，說明傳送至Adobe Commerce的行為事件。

## 相關閱讀

* [產品Recommendations — 概觀](https://devdocs.magento.com/recommendations/product-recs.html) 在我們的開發人員檔案中
* [產品Recommendations — 安裝和設定Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) 在我們的開發人員檔案中
* [行銷 — 產品Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html) 在我們的使用手冊中
* [建立產品Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html) 在我們的使用手冊中
