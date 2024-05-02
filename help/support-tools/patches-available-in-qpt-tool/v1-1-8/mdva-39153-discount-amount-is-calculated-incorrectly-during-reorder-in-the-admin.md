---
title: 'MDVA-39153：在管理員中重新排序時計算的折扣金額不正確'
description: MDVA-39153修補程式修正了在管理員中重新排序時折扣金額計算錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-39153。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: d4d11bea-a528-4eb5-8a57-8a7330975e4a
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-39153：在管理員中重新排序時計算的折扣金額不正確

MDVA-39153修補程式修正了在管理員中重新排序時折扣金額計算錯誤的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.8。 修補程式ID為MDVA-39153。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在管理員中重新訂購時計算的折扣金額不正確。

<u>要再現的步驟</u>：

1. 前往 **管理員** > **商店** > **設定** > **銷售** > **稅金**.
1. 開啟在購物車中顯示稅捐之出貨稅捐。
1. 啟用並設定表格費率送貨方法($15)。
1. 為內建稅率(CA)建立稅捐規則。
1. 建立購物車價格規則，並將固定$5的折扣套用至整個購物車和運費金額。
1. 新增價格為$12的產品至購物車，然後前往購物車頁面。
1. 將折扣套用至購物車。
1. 將「預估」區段中的送貨方法設定為「統一費率」。
1. 繼續結帳，直到檢閱步驟（請勿下訂單）。
1. 前往首頁，然後返回購物車。
1. 將「預估」區段中的送貨方法變更為「表格費率」。

<u>預期結果</u>：

折扣保持不變 — $5。

<u>實際結果</u>：

折扣為$6.31。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
