---
title: 'MDVA-38728：變更產品可見度會建立主要網站的URL重新寫入'
description: MDVA-38728修補程式解決變更第二個網站的產品可見度時，會建立主要網站的URL重寫的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-38728。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: ad1d5f82-294d-485d-acd3-28c3cd0fbf56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-38728：變更產品可見性會建立主要網站的URL重新寫入

MDVA-38728修補程式解決變更第二個網站的產品可見度時，會建立主要網站的URL重寫的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-38728。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

變更第二個網站的產品可見度，會建立主要網站的URL重新寫入。

<u>要再現的步驟</u>：

1. 建立其他網站、商店和商店評論。
1. 建立簡單的產品。
1. 將可見度設定為&#x200B;**不個別可見**。
1. 僅將產品指派給第二個網站。
1. 填寫所有其他必填欄位。
1. 儲存產品。
1. 啟動MySQL佇列：

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. 前往產品清單。
1. 使用「型錄」與「搜尋」的整批更新來選取已建立的產品並更新可見性屬性。
1. 檢查URL重寫。

<u>預期結果</u>：

系統會針對指派產品的第二個網站建立重新寫入。

<u>實際結果</u>：

系統會針對主要網站建立重新寫入。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
