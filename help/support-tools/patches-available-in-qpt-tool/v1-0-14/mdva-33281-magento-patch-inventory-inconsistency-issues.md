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

MDVA-33281修補程式修正了三個詳細目錄不一致問題。 按一下問題區段下的連結問題，檢視重現這些錯誤的步驟。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此修補程式修正了以下庫存不一致問題：

* 在CLI中執行`bin/magento inventory:reservation:list-inconsistencies`時發生&#x200B;**PHP嚴重錯誤**，因為SKU引數型別錯誤。
* **重複資料**&#x200B;在不一致清單中。
* **新預訂**&#x200B;將在下訂單前建立（先前實現方式是根據下訂單後的預訂）。 如果訂購時發生錯誤，系統會新增額外訂位以補償。

>[!NOTE]
>
>也有修補程式MDVA-30112可解決`inventory_reservation`表格中，我們的開發人員檔案中的[保留不一致](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies)數量異常大的問題。 如需解決方案，請參閱我們的支援知識庫中的[MDVA-30112Magento修補程式：大量保留不一致](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md)。

## PHP嚴重錯誤

<u>要再現的步驟</u>：

PHP執行`bin/magento inventory:reservation:list-inconsistencies`時發生嚴重錯誤。

若要取得保留區不一致的清單，請登入生產伺服器，並在CLI中執行以下命令（ — r交換器 — 原始輸出）：

<pre>bin/magento inventory:reservation:清單不一致 — r</pre>

<u>預期結果</u>：

已建立預訂不一致的清單。 這些會以下列格式傳回

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>實際結果</u>：

PHP嚴重錯誤已輸出。

## 重複資料

`inventory_reservation table`中有重複資料。

<u>要再現的步驟</u>：

若要疑難排解預留不一致，請執行以下命令：

<pre>選取*，COUNT(*)
從inventory_reservation
依中繼資料、SKU、數量分組
有COUNT(*) &gt; 1</pre>

<u>預期結果</u>：

無重複專案。

<u>實際結果</u>：

有重複專案。

## 新預訂

<u>要再現的步驟</u>：

下訂單前已建立新預訂：

1. 匯入資料庫。
1. 在終端機中執行`bin/magento setup:upgrade`。
1. 在終端機執行`bin/magento inventory:reservation:list-inconsistencies        -i -r`以列出不一致專案。

<u>預期結果</u>：

沒有回圈，而且結果快得多。

<u>實際結果</u>：

相同的結果會顯示在無限回圈中，或命令因`memory_limit`而失敗（視系統設定而定）。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
