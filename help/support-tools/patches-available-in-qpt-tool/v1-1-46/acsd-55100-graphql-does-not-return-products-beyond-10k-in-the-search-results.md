---
title: 「ACSD-55100： [!DNL GraphQL] 不會傳回搜尋結果中超過10,000的產品」
description: 套用ACSD-55100修補程式，修正GraphQL未在搜尋結果中傳回超過*10k*之產品的Adobe Commerce問題。
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100： [!DNL GraphQL] 不會傳回搜尋結果中超過10,000的產品

ACSD-55100修補程式修正以下問題： [!DNL GraphQL] 不會傳回超過以下範圍的產品 *1萬* 在搜尋結果中。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.46。 修補程式ID為ACSD-55100。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!DNL GraphQL] 不會傳回超過以下範圍的產品 *1萬* 在搜尋結果中。

<u>必要條件</u>：

若為 **[!DNL OpenSearch]**，請確定您使用的是最新可用版本。

為了解決回報的問題，我們引進了時間點功能，可在以下時段後使用 **[!DNL OpenSearch]** 2.5.0版，並需要2.2版的 `opensearch-project/opensearch-php` 封裝。

但是，與 `magento/magento-cloud-metapackage`，這會指定對的相依性 `opensearch-project/opensearch-php` 應小於2.0.1版的套件。


此相依性會防止更新 [opensearch-project/opensearch-php] 封裝至最新版本2.2。

因此，系統會遇到以下錯誤，並傳回超過產品數量的null結果 *10,000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

現有的相依性使得直接將版本新增到很困難 `composer.json` 檔案並更新 `opensearch-project/opensearch-php` 封裝至2.2版。

若要解決此問題，請在主索引標籤中包含下列行 `composer.json` 檔案。 之後，請重新部署，以將有問題的套件更新至最新版本。

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>要再現的步驟</u>：

1. 產生目錄，使用 *15k* 產品。
1. 傳送 [!DNL GraphQL]：

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>預期結果</u>：

總計= *15k*
您應該能夠顯示所有產品。

<u>實際結果</u>：

總計= *1萬*
之後您將無法再顯示任何產品 *1萬* 批次。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
