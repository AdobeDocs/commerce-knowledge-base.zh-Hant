---
title: 'MDVA-30862：列印的PDF發票上的訂單日期不正確'
description: MDVA-30862修補程式修正了PDF發票上列印錯誤訂單日期的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-30862。 請注意，問題已在Adobe Commerce 2.4.0中修正。
exl-id: 695f530e-6abf-4883-972d-5d9c379493a2
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# MDVA-30862：列印的PDF商業發票上的訂單日期不正確

MDVA-30862修補程式修正了PDF發票上列印錯誤訂單日期的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-30862。 請注意，問題已在Adobe Commerce 2.4.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.3.4

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.4 - 2.3.7-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在PDF商業發票上列印的訂單日期不正確。

<u>要再現的步驟</u>：

1. 移至&#x200B;**銷售** > **訂單**。
1. 選取訂單並列印商業發票。

<u>預期結果</u>：

日期與購買日期相符。

<u>實際結果</u>：

日期（包括月/年）與購買日期不符。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
