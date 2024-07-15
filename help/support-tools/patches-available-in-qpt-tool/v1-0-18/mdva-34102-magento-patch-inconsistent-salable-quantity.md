---
title: 'MDVA-34102：可銷售數量不一致'
description: MDVA-34102修補程式可解決「產品網格」和「管理」中「編輯產品」頁面上已停用產品的預設庫存量為零的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18後，即可使用此修補程式。 修補程式ID為MDVA-34102。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102：可銷售數量不一致

MDVA-34102修補程式可解決「產品網格」和「管理」中「編輯產品」頁面上已停用產品的預設庫存量為零的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18時，即可使用此修補程式。 修補程式ID為MDVA-34102。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p2

**與Adobe Commerce版本相容：**

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.0-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 設定兩個有商店和商店檢視的網站。
1. 建立其他來源和庫存。
1. 新增簡單產品：
   * 設定&#x200B;**啟用產品** = *否*。
   * 指派數量大於零的兩個來源為&#x200B;**Source專案狀態** = *庫存中* （範例： **預設庫存** = *123*&#x200B;和&#x200B;**英國庫存** = *123*）。
1. 儲存產品。
1. 檢查&#x200B;**產品可銷售數量**&#x200B;索引標籤。

<u>預期結果</u>：

預設庫存和英國庫存= *123.*

在Admin的「產品網格」和「編輯產品」頁面上，已停用的產品可正確顯示預設庫存數量。

<u>實際結果</u>：

預設存量= *0*&#x200B;而英國存量= *123.*

在Admin的「產品網格」和「編輯產品」頁面上，已停用產品的預設庫存數量為零。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)區段中的[修補程式。
