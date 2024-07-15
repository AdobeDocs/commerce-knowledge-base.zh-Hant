---
title: '''MDVA-34850：色票未點進清查達到「0」'
description: MDVA-34850修補程式修正了當詳細目錄達到「0」時，色票未通過，以及未顯示在任何其他庫存色票產品詳細資料頁面(PDP)連結中的問題。 在管理員設定中，**顯示缺貨產品**也設為*是*。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850：未刪除的色票清查達到「0」

MDVA-34850修補程式修正了當詳細目錄達到「0」時，色票未通過，以及未顯示在任何其他庫存色票產品詳細資料頁面(PDP)連結中的問題。 在管理員設定中，**顯示缺貨的產品**&#x200B;也設為&#x200B;*是*。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.1 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當預設庫存未使用且已啟用&#x200B;**顯示無庫存產品**&#x200B;設定時，無庫存產品選項不會顯示在PDP頁面上。

<u>必要條件</u>：

* 安裝多Source詳細目錄(MSI)。
* 啟用在[存貨選項](https://docs.magento.com/user-guide/configuration/catalog/inventory.html)中顯示無存貨產品。

<u>要再現的步驟</u>：

1. 建立新庫存量\[新庫存\]，並將所有網站指派給該庫存量和上述來源。 現在，不應使用「預設庫存」。
1. 新增三個大小選項\[S，M，L\]，以建立[可設定的產品](https://docs.magento.com/user-guide/catalog/product-create-configurable.html)。
1. 開啟每個選項，並只指定建立的自訂來源\[new\_source\]來新增數量。 此外，將\[Source狀態\]設為\[庫存中\]。
1. 從前端重新索引並檢查可配置產品。 這三個選項應該都會顯示。
1. 開啟從後端指派給\[size：S\]的簡單產品，並將\[Source Status\]設定為\[無庫存\]，同時將數量更新為0。 從前端重新索引並檢查可配置產品。

<u>預期結果</u>：

由於已啟用「顯示無庫存產品」選項，因此應會顯示全部三個選項。 無庫存選項\[S\]應停用並清除。 前端和後端應該會顯示2x / 1選項產品，且價格= 12x2，以取得訂單詳細資料。

<u>實際結果</u>：

「無庫存」選項會隱藏。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
