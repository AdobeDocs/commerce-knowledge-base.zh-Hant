---
title: 'MDVA-34591：購物車價格規則計算未如預期'
description: MDVA-34591修補程式修正了套用多個購物車價格規則時，具有**最大數量折扣套用至**的購物車價格規則無法正常運作的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19後，即可使用此修補程式。 修補程式ID為MDVA-34591。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591：購物車價格規則計算未如預期

MDVA-34591修補程式修正了隨附購物車價格規則的問題 **最大數量折扣套用至** 如果套用多個購物車價格規則，將無法正常運作。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.19。 修補程式ID為MDVA-34591。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.3.6

**與Adobe Commerce版本相容：**

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.0-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 前往「管理員」，建立下列兩個規則：

   * 規則1：購物車中最多三件物品優惠$10。 設定優先順序= *3*.
   * 規則2：購物車內所有產品八折優惠。 設定優先順序= *1*.

1. 前往店面。

1. 將產品集的八種數量加到價格= *$51* 每個都放入購物車。

1. 檢查購物車中的折扣金額。

<u>預期結果</u>：

正確計算的折扣為$234，與預期一致。

* 計算：

  比對購物車價格規則：規則2、規則1\
  套用規則2 （50%優惠），所以折扣= $204\
  套用規則1 （3個料號優惠10個），所以折扣= $30\
  總折扣=最小值( 408/2 + 10x3， 8 &#42; 51) =最小值(204 + 30， 8 &#42; 51) = $234

<u>實際結果</u>：

由於用於計算最大折扣值的數量錯誤，折扣被錯誤地計算為$153，因為無論購物車中的產品金額如何，都會套用固定折扣金額。

* 計算：

  比對購物車價格規則：規則2、規則1\
  套用規則2 （50%優惠），所以折扣= $204\
  套用規則1 （3個料號優惠10個），所以折扣= $30\
  總折扣=最小值(204 + 30， 3 &#42; 51) = $153

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
