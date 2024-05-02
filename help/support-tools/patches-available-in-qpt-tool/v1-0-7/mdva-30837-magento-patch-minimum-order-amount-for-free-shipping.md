---
title: 'MDVA-30837：免運費的最低訂單金額'
description: MDVA-30837修補程式新增免費送貨計算的設定選項，讓使用者可以設定最低訂購金額，以根據小計（或總計）取得免費送貨。 這允許針對稅捐和送貨方法自訂本機。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837：免運費的最低訂單金額

MDVA-30837修補程式新增免費送貨計算的設定選項，讓使用者可以設定最低訂購金額，以根據小計（或總計）取得免費送貨。 這允許針對稅捐和送貨方法自訂本機。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.7。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* 雲端基礎結構上的Adobe Commerce 2.3.4-p2

**與Adobe Commerce版本相容：**

* 雲端基礎結構上的Adobe Commerce 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修補程式MDVA-30837新增組態設定，以設定 **最小訂購金額** 設定為根據小計（或總計）取得免運費：

* **包含稅捐目標金額**： *是/否* 在「免運費」方法設定中。
   * 時間 **包含稅捐目標金額** 設為 *是*，最小訂購金額的計算方式為小計+稅捐 — 折扣。
   * 時間 **包含稅捐目標金額** 設為 *否*，最小訂購金額的計算方式為「小計 — 折扣」。

<u>要再現的步驟</u>：

1. 前往 **商店** >設定> **設定** > **銷售** > **稅金** 並設定下列專案：

   * 稅捐計算依據 *送貨地址*
   * 啟用跨境貿易： *否*
   * 在目錄中顯示產品價格： *排除稅金*
   * 顯示送貨價格： *排除稅金*
   * 顯示價格： *排除稅金*
   * 顯示小計： *排除稅金*
   * 顯示送貨金額： *排除稅金*
   * 顯示贈品包裝價格： *排除稅金*
   * 顯示列印的卡片價格： *排除稅金*
   * 依訂單總計包含稅捐： *是*
   * 顯示完整稅捐彙總： *是*

1. 前往 **銷售** > **送貨設定** > **免運費** 並設定 **最小訂購金額** = *30*.
1. 前往 **行銷** >促銷活動> **購物車價格規則** 並建立新的價格規則(如需詳細步驟，請參閱 [建立購物車價格規則](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html) （位於使用手冊中）。

   * 抵用券代碼= *特定抵用券*.
   * 條件：小計等於或大於$25。
   * 動作：免運費= *針對具有相符料號的出貨*.

1. 建立價格$23.10的產品。
1. 將CA稅捐新增至預設稅捐規則。
1. 將此產品新增到購物車。
1. 取得送貨報價 — 稅後總計= $25.01並套用免運費。
1. 套用抵用券代碼 — 該代碼將無效，因為小計（不含稅）為$23.10。

<u>預期結果</u>：

還有額外的組態設定 — 包含稅捐至金額： *是*/*否* 在「免運費」方法設定中：

* 當「含稅金額」設定為時 *是*，最小訂購金額的計算方式為小計+稅捐 — 折扣。
* 當「含稅金額」設定為時 *否*，最小訂購金額的計算方式為小計 — 折扣。

<u>實際結果</u>：

「免運費」價格規則條件只能以「小計」為基礎，而「免運費」方法只能以「總計」為基礎。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
