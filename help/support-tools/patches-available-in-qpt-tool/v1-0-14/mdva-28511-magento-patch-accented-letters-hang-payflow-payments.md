---
title: 'MDVA-28511：重音字母暫停付款流程付款'
description: MDVA-28511修補程式可解決透過**Payflow Pro**付款時，客戶名稱含重音字母的付款無法完成的問題。
exl-id: ecc827e3-2a1c-4f32-a0e2-9c5792483e7d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-28511：帶重音符號的字母掛起Payflow付款

MDVA-28511修補程式可解決透過付款時的問題 **Payflow Pro** 對於有重音字母的客戶名稱，請勿完成。

此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝1.0.14。 請注意，Adobe Commerce 2.3.6版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** 雲端基礎結構上的Adobe Commerce 2.3.5-p1

**與Adobe Commerce版本相容：** 雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.5 - 2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>先決條件</u>：

啟用 **Payflow Pro** 信用卡付款方式。

<u>要再現的步驟</u>：

1. 新增產品至購物車並繼續前往結帳頁面。
1. 使用重音字母設定客戶名稱。 (範例： **奧蒂安·奧伊林**)
1. 繼續付款步驟。
1. 選取 **Payflow Pro** 作為 **信用卡** 並填寫信用卡詳細資料。
1. 按一下 **下單** 按鈕。

<u>預期結果</u>：

訂單如預期般順利完成。

<u>實際結果</u>：

順序未完成，記錄將顯示與此範例類似的錯誤：

```php
[2020-06-12 07:50:23] report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted: �?tienne �?illini [] []
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
