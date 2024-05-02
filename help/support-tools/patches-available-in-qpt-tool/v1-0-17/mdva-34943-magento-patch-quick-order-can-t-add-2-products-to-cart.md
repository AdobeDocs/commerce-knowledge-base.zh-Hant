---
title: 「MDVA-34943：快速訂單無法新增2種以上的產品至購物車」
description: MDVA-34943修補程式解決快速訂單無法將兩個或更多產品新增到購物車的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.2版已修正問題。
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943：快速訂購無法新增2種以上的產品到購物車

MDVA-34943修補程式解決快速訂單無法將兩個或更多產品新增到購物車的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.17。 請注意，Adobe Commerce 2.4.2版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.4.0-p1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法快速新增兩個或更多產品至購物車。

<u>必要條件</u>：

Adobe Commerce與簡單產品。

<u>要再現的步驟</u>：

1. 前往 **快速訂購** 在店面（未登入時）。
1. 輸入有效的SKU，按一下自動完成欄位中顯示的產品，然後設定 **數量** = *1*.
1. 輸入相同的有效SKU，但變更第一個字元的大小寫（將大寫變更為小寫，或將小寫變更為大寫），然後按一下自動完成欄位中顯示的產品，並設定 **數量** = *1*.
1. 輸入 `random_sting_value` 的 **SKU**，並設定 **數量** = *1*.
1. 設定 **SKU** = *123123123*，並設定 **數量** = *1*.
1. 刪除您所新增至的第一個專案以外的所有專案 **快速訂購** 頁面。
1. 在「 」中輸入第一個SKU （類似上述步驟2） **輸入多個SKU** 欄位，然後按一下 **新增至清單**.
1. 這會導致第一個SKU的數量為2，而明細行數量為 `random_sting_value`.
1. 若要進行更多測試，請重新整理頁面。
1. 如此可如預期產生無快速訂購SKU。
1. 輸入 `random_sting_value2` 到 **輸入多個SKU** 欄位，然後按一下 **新增至清單**.
1. 這會產生兩個來自之前的有效SKU和 `random_sting_value2`.

<u>預期結果</u>：

如預期，兩個或多個產品可新增至購物車。

<u>實際結果</u>：

帶到以下位置時 **購物車** 頁面，第一個新增的產品會正常顯示，但第二個產品及任何新增至購物車的後續產品則會顯示「*1個產品需要注意*「錯誤訊息出現。 第二項或任何附加產品將列在 **產品需要注意** 的區段 **購物車** 頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 區段。
