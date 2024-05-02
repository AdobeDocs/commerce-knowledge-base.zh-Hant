---
title: 'MC-41359商務修補程式：遺失設定SameSite Cookie引數'
description: MC-41359商務修補程式修正遺失SameSite Cookie引數設定的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MC-41359。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# MC-41359商務修補程式：遺失設定SameSite Cookie引數

MC-41359商務修補程式修正遺失SameSite Cookie引數設定的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.20。 修補程式ID為MC-41359。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.4.2

**與Adobe Commerce版本相容：** 雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.6-p1、2.4.2、2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

缺少SameSite Cookie引數的設定。

<u>要再現的步驟：</u>

先決條件：

* 開啟Chrome並前往chrome://flags/
* 啟用 **預設SameSite Cookie** 和 **不含SameSite的Cookie必須是安全的**.
* 開啟Chrome檢視窗。

<u>案例1：</u>

1. 啟用PayPal。
1. 前往商店前面。
1. 新增產品至購物車。
1. 前往結帳。

<u>案例2：</u>

如果您有New Relic [已啟用](https://docs.magento.com/user-guide/reports/new-relic-reporting.html) 警告會出現在任何前端頁面上。

<u>實際結果：</u>

瀏覽器主控台中的警告訊息： *與跨網站資源相關聯的Cookie已設定為不含SameSite屬性。*

<u>預期結果：</u>

&quot;lax&quot;不應新增至cookie網域；samesite屬性應以預設值存在。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

如需QPT工具中其他可用修補程式的詳細資訊，請參閱 [QPT工具中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
