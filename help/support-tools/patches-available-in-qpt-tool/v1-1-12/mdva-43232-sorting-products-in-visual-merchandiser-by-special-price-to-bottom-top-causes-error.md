---
title: 'MDVA-43232：依特殊價格排序視覺化銷售器中的產品至頂端（或底部）會導致錯誤'
description: MDVA-43232修補程式修正依特殊價格排序視覺化銷售器中的產品至頂端（或底部）時，導致儲存類別時發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-43232。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232：依特殊價格排序視覺化銷售器中的產品至頂端（或底部）會導致錯誤

MDVA-43232修補程式修正依特殊價格排序視覺化銷售器中的產品至頂端（或底部）時，導致儲存類別時發生錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-43232。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

依特殊價格排序視覺化銷售器中的產品至頂端（或底部）會在儲存類別時造成錯誤。

<u>要再現的步驟</u>：

1. 確定有兩個網站。
1. 導覽至&#x200B;**商店** > **設定** > **目錄** > **價格**，並設定目錄價格範圍=網站。
1. 再次導覽至&#x200B;**商店** > **設定** > **目錄** > **視覺化銷售工具** > **類別規則的可見屬性** >並新增特殊價格。
1. 建立簡單產品並將產品指派給兩個網站。
1. 新增特殊價格至產品的預設範圍。
1. 切換到其他商店的範圍並覆寫該產品的「價格」和「特殊價格」。
1. 執行`catalog_product_price`重新索引。
1. 移至&#x200B;**目錄** > **類別**&#x200B;並建立新類別。
1. 新增類別規則，以篩選具有特殊價格的產品。
1. 儲存類別。
1. 在「分類中的產品」區段下，將「排序順序=特殊價格」設定為「頂端（或底部）」。
1. 再次儲存類別。

<u>預期結果</u>：

類別儲存時不會發生錯誤。

<u>實際結果</u>：

系統擲回例外狀況：

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
