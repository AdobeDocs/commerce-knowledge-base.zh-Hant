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

MDVA-30594修補程式可解決客戶在多個地址下訂單後未看到訂單成功頁面的問題。 檢查Commerce管理員上的訂單時，會顯示兩個包含相同產品（而非正確產品）的訂單。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.7。 Adobe Commerce 2.4.2已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* 雲端基礎結構上的Adobe Commerce 2.3.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

多個地址訂單未與訂單成功頁面同時完成，並顯示兩個訂單包含相同產品，而非正確產品。

<u>必要條件</u>：

使用商店和商店檢視建立兩個網站。

<u>要再現的步驟</u>：

1. 設定 **目錄價格範圍** 針對網站目錄(**商店** > **設定** > **設定** > **目錄** > **目錄** > **價格** > **範圍**)。
1. 設定 **固定產品稅金(FPT)** (**商店** > **設定** > **銷售** > **稅金** > **固定產品稅金**)：

   * **啟用FPT** = *是*
   * **在產品清單中顯示價格** = *排除FPT*
   * **在產品檢視頁面上顯示價格** = *排除FPT*
   * **在銷售模組中顯示價格** = *排除FPT* (包括 **FPT** 說明與最終價格)。
   * **在電子郵件中顯示價格** = *排除FPT* (包括 **FPT** 說明與最終價格)。
   * **將稅捐套用至財務申報單** = *是*
   * **在小計中包含FPT** = *否*

1. 建立 **FPT屬性**，並將其指派給預設屬性集。 (請參閱 [設定FPT：建立FPT屬性](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) （位於使用手冊中）。

1. 建立四個簡單的產品，並將 **FPT** **屬性值** (範例：設定 **FPT**   **屬性值** = *澳洲*)。

1. 使用下列設定建立兩個套件式產品：

   * 定義 **FPT**.
   * 設定 **動態價格** = *否*.
   * 設定 **價格** = *100*.
   * 捆綁選項一起出貨，全部標示為預設，附有 **價格型別** = *固定*.
   * 新增在步驟四中建立的兩個簡單產品。

1. 在前端建立使用者帳戶。 以澳洲地址更新地址（將國家/地區設定為澳洲或中使用的任何國家/地區） **FPT** 設定)。

1. 將兩個隨附產品加入購物車。

1. 前往購物車頁面，並檢查 **FPT** 顯示正確。

1. 按一下 **使用多個地址簽出**.

1. 新增第二個地址。

1. 將每個產品指派至不同的地址。

1. 繼續結帳程式，直到 **下單**.

1. 按一下 **下單** 按鈕。

<u>預期結果</u>：

已成功下訂單多個地址。

<u>實際結果</u>：

類似以下的訊息： 」*發生錯誤。*「」將會出現。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
