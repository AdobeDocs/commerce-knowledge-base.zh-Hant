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

MDVA-30837修補程式新增免費送貨計算的設定選項，讓使用者可以設定最低訂購金額，以根據小計（或總計）取得免費送貨。 這允許針對稅捐和送貨方法自訂本機。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.3.4-p2

**與Adobe Commerce版本相容：**

* 雲端基礎結構上的Adobe Commerce 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修補程式MDVA-30837新增組態設定，以設定&#x200B;**最低訂購金額**&#x200B;設定，以根據小計（或總量）取得免費送貨：

* 在免運費方式組態中&#x200B;**包含金額**： *是/否*。
   * 當&#x200B;**包含稅捐至金額**&#x200B;設定為&#x200B;*是*&#x200B;時，最小訂單金額會計算為「小計+稅捐 — 折扣」。
   * 當&#x200B;**含稅金額**&#x200B;設定為&#x200B;*否*&#x200B;時，最小訂購金額會計算為「小計 — 折扣」。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** >設定> **組態** > **銷售** > **稅捐**，並設定下列專案：

   * 根據&#x200B;*送貨地址*&#x200B;計算稅捐
   * 啟用跨境貿易： *否*
   * 在目錄中顯示產品價格： *排除稅捐*
   * 顯示運費： *不含稅金*
   * 顯示價格： *不包括稅捐*
   * 顯示小計： *排除稅捐*
   * 顯示送貨金額： *不包括稅捐*
   * 顯示贈品包裝價格： *不含稅*
   * 顯示列印的卡片價格： *不含稅*
   * 含稅訂單總計： *是*
   * 顯示完整稅捐彙總： *是*

1. 移至&#x200B;**銷售** > **送貨設定** > **免運費**，並設定&#x200B;**最低訂單金額** = *30*。
1. 前往&#x200B;**行銷** >促銷活動> **購物車價格規則**&#x200B;並建立新的價格規則（如需詳細步驟，請參閱使用手冊中的[建立購物車價格規則](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html)）。

   * 優惠券代碼= *特定優惠券*。
   * 條件：小計等於或大於$25。
   * 動作：免運費= *針對具有相符料號的出貨*。

1. 建立價格$23.10的產品。
1. 將CA稅捐新增至預設稅捐規則。
1. 將此產品新增到購物車。
1. 取得送貨報價 — 稅後總計= $25.01並套用免運費。
1. 套用抵用券代碼 — 該代碼將無效，因為小計（不含稅）為$23.10。

<u>預期結果</u>：

有額外的組態設定 — 包含稅捐至金額： *是*/*否* （在免運費方式組態中）：

* 當「包含稅捐至金額」設定為&#x200B;*是*&#x200B;時，最小訂單金額會計算為「小計+稅捐 — 折扣」。
* 當「含稅金額」設定為&#x200B;*否*&#x200B;時，最小訂購金額會計算為「小計 — 折扣」。

<u>實際結果</u>：

「免運費」價格規則條件只能以「小計」為基礎，而「免運費」方法只能以「總計」為基礎。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
