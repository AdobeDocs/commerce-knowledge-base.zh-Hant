---
title: 'MDVA-43605：使用Rest API時，訂單資料傳回資料列總計的負值'
description: MDVA-43605修補程式修正了使用Rest API時，訂單資料傳回負值的列總計問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-43605。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605：使用Rest API時，訂單資料會傳回列總計的負值

MDVA-43605修補程式修正了使用Rest API時，訂單資料傳回負值的列總計問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.14。 修補程式ID為MDVA-43605。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.1 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用Rest API時，訂單資料會傳回列總計的負值。

<u>要再現的步驟</u>：

1. 啟用免費送貨。
1. 瀏覽至 **設定** > **目錄** > **價格** >並設定目錄價格範圍=網站。
1. 瀏覽至 **設定** > **銷售** > **稅金** 和更新：
   * 出貨的稅捐類別=應稅貨品
   * 計算設定：
      * 型錄價格=含稅
      * 送貨價格=包含價格
      * 套用價格折扣=含稅
   * 價格顯示設定：包含稅捐（所有欄位）
   * 購物車顯示設定：包含稅捐（所有欄位）
   * 訂單、商業發票、銷退折讓單：
      * 顯示出貨金額=含稅
1. 建立美國的稅率（州= &#39;*&#39;），稅率百分比= 24.00
1. 建立具有上述稅率的稅捐規則。
1. 建立具有特定優惠券的購物車價格規則，並且折扣= $50是整個購物車的固定金額。
1. 使用下列價格建立四種產品：$8.90、$5.90、$6.90和$5.95。
1. 使用上一步建立的優惠券代碼，建立包括其中四個產品的管理訂單。 使用免運費。
1. 由於優惠券代碼涵蓋購物車總計，因此不需要付款。
1. 擷取剛透過Rest API端點建立的訂單：

   ```json
   GET rest/V1/orders/1
   ```

<u>預期結果</u>：

下列專案的值 `base_row_total` 和 `base_row_total_incl_tax` 回應中為零。

<u>實際結果</u>：

此 `base_row_total` 和 `base_row_total_incl_tax` 回應中的欄位具有負值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
