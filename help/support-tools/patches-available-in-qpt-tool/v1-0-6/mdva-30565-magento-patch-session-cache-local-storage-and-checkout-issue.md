---
title: 'MDVA-30565：工作階段快取本機儲存和簽出問題'
description: MDVA-30565修補程式可解決工作階段快取本機儲存和結帳的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6後，即可使用此修補程式。
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565：工作階段快取本機儲存和簽出問題

MDVA-30565修補程式可解決工作階段快取本機儲存和結帳的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.3.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當客戶工作階段逾時，購物車頁面上仍可看到購物車專案。 這會造成預估送貨方法錯誤，導致沒有送貨方法可供來賓結帳。

<u>要再現的步驟</u>：

1. 在Commerce管理員中啟用永續性購物車。 （**啟用持續性** = &quot;*是*&quot;）
1. 以客戶身分登入前端。 這會建立`persistent_shopping_cart` Cookie並起始持續工作階段。
1. 將產品加入購物車。
1. 等候前端工作階段逾時，或刪除`PHPSESSID` Cookie。
1. 現在您是訪客使用者，但如果您移至購物車，仍可看到已新增為登入客戶的產品。
1. 將產品從購物車移除，現在購物車是空的。 您可以在此事件中看到Adobe Commerce刪除`persistent_shopping_cart` Cookie。
1. 將新產品加入購物車，然後前往購物車頁面。
1. 現在，在瀏覽器主控台中，它顯示`V1/guest-carts/4/estimate-shipping-methods`要求現在傳回404回應，訊息為`{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>預期結果</u>：

預估送貨方法要求傳回正確結果。

<u>實際結果</u>：

預估送貨方法要求失敗，錯誤如下： &quot;*很抱歉，目前沒有此訂單的報價單。*&quot;

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
