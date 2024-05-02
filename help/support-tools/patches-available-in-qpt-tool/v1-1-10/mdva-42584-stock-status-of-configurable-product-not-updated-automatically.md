---
title: 「MDVA-42584：可設定產品的庫存狀態未自動更新」
description: MDVA-42584修補程式可解決在簡單產品更新時，可設定產品的庫存狀態未自動更新的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-42584。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584：可設定產品的庫存狀態未自動更新

MDVA-42584修補程式可解決在簡單產品更新時，可設定產品的庫存狀態未自動更新的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.10。 修補程式ID為MDVA-42584。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當簡單產品設定為時，後端中可設定產品的庫存狀態不會自動更新 **有貨** 透過API或匯入。

<u>必要條件</u>：

已安裝MSI。

<u>要再現的步驟</u>：

1. 建立可設定的產品， **InvCheck001**，提供兩個選項： **InvCheck001-M** 和 **InvCheck001-L**.
1. 簡單產品都應該有數量，而且它們應該是 **有貨** 因此可設定的產品也 **有貨** 在後端中。
1. 現在，請更新簡單產品，並將「數量」設定為 **0** 和庫存狀態至 **無庫存**.
1. 重新整理可設定產品並確認庫存狀態已更新至 **無庫存**.
1. 使用以下API端點並設定簡單產品 **InvCheck001-M** 至 **有貨** 數量大於0時。

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. 前往後端，驗證簡單產品的數量與庫存狀態 **InvCheck001-M**. 更新為 **有貨**.
1. 重新整理可設定產品並檢查庫存狀態。

<u>預期結果</u>：

可設定產品的庫存狀態 **InvCheck001** 後端的自動更新為 **有貨**.

<u>實際結果</u>：

可設定產品的庫存狀態仍為 **無庫存**.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
