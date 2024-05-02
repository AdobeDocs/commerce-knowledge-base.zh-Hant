---
title: 'MDVA-30112：大量預訂不一致'
description: MDVA-30112修補程式可解決「inventory_reservation」表格中意外出現大量[預留不一致](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies)的問題。 預留不一致包括未註冊的未結訂單和未註冊的完成訂單。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.2版已修正問題。
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112：大量預訂不一致

MDVA-30112修補程式可解決您意外擁有大量客戶的問題， [預訂不一致](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) 在 `inventory_reservation` 表格。 預留不一致包括未註冊的未結訂單和未註冊的完成訂單。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.8。 請注意，Adobe Commerce 2.4.2版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* 雲端基礎結構上的Adobe Commerce 2.3.5

**與Adobe Commerce版本相容：**

* Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.4 - 2.3.5-p2， 2.4.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此 [bunch-size](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) value是要一次載入多少訂單的值。 當訂單數超過此值時，Adobe Commerce會將狀態為未決的訂單視為不一致。

>[!NOTE]
>
>有修正其他三個詳細目錄不一致問題的修補程式MDVA-33281。 這包括在執行時發生PHP嚴重錯誤 `bin/magento inventory:reservation:list-inconsistencies` 在CLI中。 另一個已修正的問題是不一致清單中的重複資料。 此外，在發出訂單之前建立預訂的問題（先前實現是根據發出訂單之後的預訂）。 如需解決方案，請參閱 [MDVA-33281：詳細目錄不一致問題](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) 在我們的支援知識庫中。

<u>必要條件</u>：

您在CLI中執行以下命令，以列出 `inventory_reservation` 表格：

```
magento inventory:reservation:list-inconsistencies
```

您會看到意外的大量預訂不一致和/或命令永遠未完成。

<u>要再現的步驟</u>：

1. 在CLI中執行以下命令以解決不一致問題：

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. 下三張訂單：
   * 為每個指派單一產品。
   * 使用「支票/匯票」付款方式，因此訂單狀態為「待處理」。
1. 您可在下列位置看到數量為–1的三個記錄 `inventory_reservation` 表格。 在CLI中執行以下命令，檢視任何不一致的情況：

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   這不會傳回任何結果，這是正確的。

1. 在CLI中執行以下命令：

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   您會看到「擱置」狀態訂單顯示為不一致。

1. 在CLI中執行以下命令：

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u>預期結果</u>：

Adobe Commerce不應解決「擱置」狀態訂單的不一致問題。 具有「完成」、「已關閉」及「已取消」狀態的訂單應解決存貨不一致問題。

<u>實際結果</u>：

當訂單超過指定的束團大小值時，Adobe Commerce會將狀態為「待定」的訂單視為不一致，並為相同訂單新增多個不一致問題解決記錄。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
