---
title: 疑難排解Adobe Commerce中的[!UICONTROL Product Recommendations]模組
description: 本文介紹Adobe Commerce中[!UICONTROL Product Recommendations]模組的疑難排解建議。
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# 疑難排解Adobe Commerce中的[!UICONTROL Product Recommendations]模組

本文會討論下列專案的疑難排解建議：

```php
magento/product-recommendations
```

模組及其相依性

```php
saas-export
```

模組，因為您需要兩個模組都運作，才能在Adobe Commerce中使用[!UICONTROL Product Recommendations]工具。

## 受影響的產品和版本

* Adobe Commerce 2.4.4 - 2.4.7

## 產品建議模組疑難排解

如果您已設定

```php
magento/product-recommendations
```

模組正確，（請檢視開發人員檔案中的[[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure)。）但您未看到任何建議，請嘗試下列步驟：

* 模組可能沒有足夠的時間來收集行為資料。 允許系統執行24小時，以便開始收集資料。 請考慮部署不需要任何行為資料的建議型別，例如&quot;*更多類似此*&quot;。

* 如果您未看到您設定的建議，表示可能還沒有足夠的資料可供使用者建置建議。

* 請確定[!DNL SaaS]資料空間或[!DNL API]金鑰有效。 如果在產品建議初始化期間指定您的[!DNL SaaS]資料空間或[!DNL API]金鑰之後發生錯誤，請檢查以確定您已正確輸入[[!DNL SaaS] 資料空間和 [!DNL API] 金鑰](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) （在我們的使用手冊中）。 若要確保[!DNL MageID]和[!DNL API]金鑰已連結，擁有[!DNL MageID]的使用者(通常是擁有Adobe Commerce授權的使用者)必須是產生[!DNL API]金鑰的相同使用者。 如果您必須變更已使用的[!DNL MageID]，[請提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

>[!NOTE]
>
>如果&#x200B;[**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law) （在我們的使用手冊中）為&#x200B;*已啟用*，Adobe Commerce會在購物者同意前不會收集行為資料。 如果&#x200B;**[!UICONTROL Cookie Restriction Mode]**&#x200B;已&#x200B;*停用*，Adobe Commerce會依預設收集行為資料。

## 目錄[!DNL SaaS]匯出模組

針對與目錄[!DNL SaaS]匯出相關的問題(

```php
saas-export
```

)模組：

1. 確認[[!DNL cron]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) （在開發人員檔案中）工作正在執行。
1. 確認[[!UICONTROL indexers]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) （在開發人員檔案中）執行中，並且    ```php    Product Feed    ```    [!UICONTROL indexer]已設定為    ```php    Update by Schedule    ```    .
1. 確認模組&#x200B;*已啟用*。 此    ```php    saas-export    ```    Metapackage會安裝下列模組，這些模組必須全部&#x200B;*啟用*：    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. 檢查[記錄檔](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging) （在開發人員檔案中）。 請確定沒有與上述模組相關聯的錯誤。
1. 重新整理[!UICONTROL Configuration cache]。 移至&#x200B;**系統** > **工具** > **快取管理**，然後清除[!UICONTROL Configuration cache]。
1. 確認`cde_products_products_feed`資料庫表格中有資料。

   >[!NOTE]
   >
   >如果找不到該資料表，請檢查`catalog_data_exporter_products`資料表。 資料表名稱已在[!DNL Data Export]版本103.3.0中變更。

## 活動

[在開發人員檔案中，驗證Event Collection](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/verify)說明傳送至Adobe Commerce的行為事件。

## 相關閱讀

* 在開發人員檔案中[產品Recommendations管理員開發](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
* 產品Recommendations指南中的[產品Recommendations簡介](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview)
* 在產品Recommendations指南中[建立產品Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/admin/create)
* 在[!DNL SaaS]資料匯出指南中[檢閱記錄檔及疑難排解](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging)
* Adobe Commerce Data Export Guide for [!DNL SaaS] Services中的[[!DNL SaaS] Data Export Extension發行說明](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

