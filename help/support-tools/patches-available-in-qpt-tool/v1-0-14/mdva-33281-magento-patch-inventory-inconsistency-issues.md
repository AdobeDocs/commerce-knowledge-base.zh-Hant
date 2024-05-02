---
title: 'MDVA-33281修補程式：詳細目錄不一致問題'
description: MDVA-33281修補程式修正了三個詳細目錄不一致問題。 按一下問題區段下的連結問題，檢視重現這些錯誤的步驟。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14時，即可使用此修補程式。
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-33281修補程式：清查不一致性問題

MDVA-33281修補程式修正了三個詳細目錄不一致問題。 按一下問題區段下的連結問題，檢視重現這些錯誤的步驟。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.14。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.3.5-p1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此修補程式修正了以下庫存不一致問題：

* **PHP嚴重錯誤** 執行時 `bin/magento inventory:reservation:list-inconsistencies` 在CLI中，因為錯誤的SKU引數型別。
* **重複資料** 在不一致清單中。
* **新預訂** 會在下訂單前建立（先前實現是根據下訂單後的預訂）。 如果訂購時發生錯誤，系統會新增額外訂位以補償。

>[!NOTE]
>
>此外，也有修補程式MDVA-30112可解決數量意外過大的問題。 [預訂不一致](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) 在我們的開發人員檔案中，將位於 `inventory_reservation` 表格。 如需解決方案，請參閱 [MDVA-30112Magento修補程式：大量保留不一致](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) 在我們的支援知識庫中。

## PHP嚴重錯誤

<u>要再現的步驟</u>：

PHP執行時發生嚴重錯誤 `bin/magento inventory:reservation:list-inconsistencies`.

若要取得保留區不一致的清單，請登入生產伺服器，並在CLI中執行以下命令（ — r交換器 — 原始輸出）：

<pre>bin/magento詳細目錄:reservation:list-inconsistency -r</pre>

<u>預期結果</u>：

已建立預訂不一致的清單。 這些會以下列格式傳回

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>實際結果</u>：

PHP嚴重錯誤已輸出。

## 重複資料

重複資料位於 `inventory_reservation table`.

<u>要再現的步驟</u>：

若要疑難排解預留不一致，請執行以下命令：

<pre>選取*，COUNT(*) FROM inventory_reservation GROUP BY中繼資料，SKU，COUNT(*) &gt; 1的數量</pre>

<u>預期結果</u>：

無重複專案。

<u>實際結果</u>：

有重複專案。

## 新預訂

<u>要再現的步驟</u>：

下訂單前已建立新預訂：

1. 匯入資料庫。
1. 執行 `bin/magento setup:upgrade` 在終端機中。
1. 透過執行列出不一致專案 `bin/magento inventory:reservation:list-inconsistencies        -i -r` 在終端機中。

<u>預期結果</u>：

沒有回圈，而且結果快得多。

<u>實際結果</u>：

相同的結果會顯示在無限回圈中，否則命令會失敗 `memory_limit`，視系統設定而定。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
