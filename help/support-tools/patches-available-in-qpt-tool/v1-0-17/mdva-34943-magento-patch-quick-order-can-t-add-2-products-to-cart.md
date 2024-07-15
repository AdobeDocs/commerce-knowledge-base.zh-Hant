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

MDVA-34943修補程式解決快速訂單無法將兩個或更多產品新增到購物車的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.2版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.0-p1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法快速新增兩個或更多產品至購物車。

<u>必要條件</u>：

Adobe Commerce與簡單產品。

<u>要再現的步驟</u>：

1. 前往店面上的&#x200B;**快速訂購** （未登入時）。
1. 輸入有效的SKU，按一下自動完成欄位中顯示的產品，然後設定&#x200B;**數量** = *1*。
1. 輸入相同的有效SKU，但變更第一個字元的大小寫（將大寫變更為小寫，或將小寫變更為大寫），然後按一下自動完成欄位中顯示的產品，並設定&#x200B;**數量** = *1*。
1. 輸入&#x200B;**SKU**&#x200B;的`random_sting_value`，並設定&#x200B;**數量** = *1*。
1. 設定&#x200B;**SKU** = *123123123*，並設定&#x200B;**數量** = *1*。
1. 刪除您新增至&#x200B;**快速訂購**&#x200B;頁面的第一個專案以外的所有專案。
1. 在&#x200B;**輸入多個SKU**&#x200B;欄位中輸入第一個SKU （類似上述步驟2），然後按一下&#x200B;**新增至清單**。
1. 這會導致第一個SKU的數量為2，而`random_sting_value`的行為。
1. 若要進行更多測試，請重新整理頁面。
1. 如此可如預期產生無快速訂購SKU。
1. 在&#x200B;**輸入多個SKU**&#x200B;欄位中輸入`random_sting_value2`，然後按一下&#x200B;**新增至清單**。
1. 這會產生兩個來自之前的有效SKU和`random_sting_value2`。

<u>預期結果</u>：

如預期，兩個或多個產品可新增至購物車。

<u>實際結果</u>：

當進入&#x200B;**購物車**&#x200B;頁面時，第一個新增的產品會正常顯示，但對於第二個產品及任何新增至購物車的後續產品，會顯示「*1產品需要注意*」錯誤訊息。 第二個或任何其他產品將列在&#x200B;**購物車**&#x200B;頁面的&#x200B;**產品需要注意**&#x200B;區段。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
