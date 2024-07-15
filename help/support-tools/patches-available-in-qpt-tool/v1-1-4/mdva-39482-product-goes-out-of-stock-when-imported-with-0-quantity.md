---
title: 「MDVA-39482：如果以'0'數量匯入並啟用延期交貨，則產品無庫存」
description: MDVA-39482修正啟用MSI和延期交貨且缺貨臨界值設定為負值時，以「0」數量匯入產品缺貨的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-39482。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482：如果以「0」數量匯入並啟用延期交貨，則產品無庫存

MDVA-39482修正啟用MSI和延期交貨且缺貨臨界值設定為負值時，以「0」數量匯入產品缺貨的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-39482。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用MSI和延期交貨且缺貨臨界值設定為負值時，如果以「0」數量匯入產品，則產品缺貨。

<u>必要條件</u>：

1. 必須安裝MSI和範例資料。
1. 移至&#x200B;**商店** > **組態** > **目錄** > **詳細目錄**：
   * 將延期交貨設為「允許數量低於0」
   * 將無庫存臨界值設為「–10」

<u>要再現的步驟</u>：

1. 確定SKU為&#x200B;**庫存**，且數量為&#x200B;**24-MB01**。
1. 匯入「庫存來源」的CSV。 請務必在「實體型別」中選取「庫存來源」：

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. 在匯入庫存來源後，檢查產品的庫存狀態。

<u>預期結果</u>：

24-MB01在店面有&#x200B;**庫存**。

<u>實際結果</u>：

24-MB01在店面有&#x200B;**無庫存**。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
