---
title: 'MDVA-30594：多個地址簽出錯誤'
description: MDVA-30594修補程式可解決客戶在多個地址下訂單後未看到訂單成功頁面的問題。 檢查Commerce管理員上的訂單時，會顯示兩個包含相同產品（而非正確產品）的訂單。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 Adobe Commerce 2.4.2已修正問題。
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594：多個地址簽出錯誤

MDVA-30594修補程式可解決客戶在多個地址下訂單後未看到訂單成功頁面的問題。 檢查Commerce管理員上的訂單時，會顯示兩個包含相同產品（而非正確產品）的訂單。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 Adobe Commerce 2.4.2已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.3.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

多個地址訂單未與訂單成功頁面同時完成，並顯示兩個訂單包含相同產品，而非正確產品。

<u>必要條件</u>：

使用商店和商店檢視建立兩個網站。

<u>要再現的步驟</u>：

1. 設定網站目錄的&#x200B;**目錄價格範圍** （**商店** > **設定** > **組態** > **目錄** > **目錄** > **價格** > **範圍**）。
1. 設定&#x200B;**固定產品稅(FPT)** （**商店** > **組態** > **銷售** > **稅** > **固定產品稅**）：

   * **啟用FPT** = *是*
   * **產品清單中的顯示價格** = *不包括FPT*
   * **產品檢視頁面上的顯示價格** = *不包括FPT*
   * **銷售模組中的顯示價格** = *不包括FPT* （包括&#x200B;**FPT**&#x200B;說明和最終價格）。
   * **電子郵件中的顯示價格** = *不包括FPT* （包括&#x200B;**FPT**&#x200B;說明和最終價格）。
   * **套用稅捐至FPT** = *是*
   * **小計中包含FPT** = *否*

1. 建立&#x200B;**FPT屬性**，並將其指派給預設屬性集。 （請參閱使用手冊中的[設定FPT：建立FPT屬性](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute)）。

1. 建立四個簡單產品，並設定&#x200B;**FPT** **屬性值** （範例：設定&#x200B;**FPT**）   **屬性值** = *澳洲*)。

1. 使用下列設定建立兩個套件式產品：

   * 定義&#x200B;**FPT**。
   * 設定&#x200B;**動態價格** = *否*。
   * 設定&#x200B;**價格** = *100*。
   * 組合選項已一起寄出，全部標示為預設，並附有&#x200B;**價格型別** = *固定*。
   * 新增在步驟四中建立的兩個簡單產品。

1. 在前端建立使用者帳戶。 以澳洲地址更新地址（將國家/地區設定為澳洲或在&#x200B;**FPT**&#x200B;設定中使用的任何國家/地區）。

1. 將兩個隨附產品加入購物車。

1. 前往購物車頁面，並檢查&#x200B;**FPT**&#x200B;是否正確顯示。

1. 按一下&#x200B;**使用多個地址簽出**。

1. 新增第二個地址。

1. 將每個產品指派至不同的地址。

1. 繼續結帳程式，最多可達&#x200B;**下訂單**。

1. 按一下&#x200B;**下訂單**&#x200B;按鈕。

<u>預期結果</u>：

已成功下訂單多個地址。

<u>實際結果</u>：

類似於&#39;&#39;*&#39;的訊息已經發生錯誤。「*」將會出現。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
