---
title: 'MDVA-40488：含有無庫存子產品的可設定產品未顯示在正確價格範圍內'
description: MDVA-40488修補程式解決具有無庫存子產品的可設定產品無法顯示在其正確價格範圍的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-40488。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488：含有無庫存子產品的可設定產品未顯示在正確價格範圍內

MDVA-40488修補程式解決具有無庫存子產品的可設定產品無法顯示在其正確價格範圍的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9時，即可使用此修補程式。 修補程式ID為MDVA-40488。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

含有無庫存子產品的可設定產品無法顯示在其正確的價格範圍內。

<u>必要條件</u>：

前往Commerce管理> **商店** > **設定** > **目錄** > **詳細目錄** > **庫存選項**，並將&#x200B;**顯示缺貨產品**&#x200B;設定設為&#x200B;*是*。

<u>要再現的步驟</u>：

1. 使用兩個相關聯的產品建立可設定的產品。 例如：簡單產品Red和Brown。
1. 將簡單產品的庫存設定為[紅色]，並將[庫存狀態]設定為&#x200B;*庫存*，然後將[啟用產品]狀態設定為&#x200B;*否*。
1. 設定簡單產品Brown的詳細目錄，然後將[啟用產品]狀態設定為&#x200B;*是*。
1. 確定可設定的產品庫存狀態為&#x200B;*庫存*。
1. 將簡單產品Brown的庫存變更為0，並將庫存狀態設定為&#x200B;*缺貨*。
1. 此時，可設定的產品庫存狀態仍為&#x200B;*庫存*。
1. 執行重新索引。
1. 檢查`catalog_product_index_price` DB資料表中可設定產品的`min_price`和`max_price` — 這兩個值設定為0。
1. 但是，如果我們將可設定產品的Stock狀態設定為&#x200B;*缺貨*&#x200B;並且重新索引，那麼我們可以看到可設定產品的`min_price`和`max_price`非零值。

<u>預期結果</u>：

如果所有子產品都是&#x200B;*無庫存*，而可設定的產品本身也是&#x200B;*無庫存*，則使用所有子產品來計算價格。

<u>實際結果</u>：

當可設定的庫存狀態為&#x200B;*庫存*&#x200B;時，`catalog_product_index_price`資料庫資料表中可設定產品的`min_price`與`max_price`值會設為0，但如果狀態為&#x200B;*庫存不足*，則會變成非零值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
