---
title: 'MDVA-40609： cataloginventory_stock_status表格中缺少停用的產品資料'
description: MDVA-40609修補程式可解決「cataloginventory_stock_status」索引表中未顯示已停用產品資料，導致顯示錯誤產品數量的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-40609。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: 2424c3b3-8bc9-4dd4-908c-9d653f09a57a
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40609： cataloginventory_stock_status表格中缺少已停用的產品資料

MDVA-40609修補程式解決停用產品資料未顯示在`cataloginventory_stock_status`索引表中，導致顯示不正確產品數量的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-40609。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

停用的產品資料未顯示在`cataloginventory_stock_status`索引表中，導致顯示不正確的產品數量。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 設定兩個有商店和商店檢視的網站。
1. 建立其他來源和庫存。
1. 新增簡單產品：
   * 將[啟用產品]設定為&#x200B;*否*。
   * 指定兩個來源，Source料號狀態=安裝及數量大於零。
1. 儲存產品。
1. 檢查&#x200B;**產品可銷售數量**&#x200B;索引標籤。

<u>預期結果</u>：

兩個庫存都輸入了大於零的值。

<u>實際結果</u>：

一種股票具有零值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修補程式區段。
