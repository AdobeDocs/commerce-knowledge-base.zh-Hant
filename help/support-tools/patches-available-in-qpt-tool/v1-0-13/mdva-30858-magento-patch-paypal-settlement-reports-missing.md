---
title: 'MDVA-30858：缺少PayPal結算報告'
description: 「MDVA-30858修補程式修正了擁有多個PayPal帳戶時遺失的PayPal結算報告。 這些報表應可在「管理員」側邊欄&amp；**報表**&amp；gt；銷售&amp；gt； **PayPal結算**下取得。 相反地，訊息為： *我們找不到任何記錄。*顯示。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13後，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。」
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858：缺少PayPal結算報表

MDVA-30858修補程式修正了擁有多個PayPal帳戶時遺失PayPal結算報表的問題。 這些報表應該可在「管理側欄> **報表** >銷售> **PayPal結算**」下取得。 而是訊息： *我們找不到任何記錄。顯示*。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.4

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正有多個PayPal帳戶時，**報表** >銷售> **PayPal結算**&#x200B;中找不到記錄的問題。

<u>要再現的步驟</u>：

1. 設定PayPal結算報表。
1. 移至[管理]，移至&#x200B;**報表** >銷售> **PayPal結算**。
1. 如需最新更新，請按一下右上角的&#x200B;**擷取更新**。

<u>預期結果</u>：

報表應該會出現。

<u>實際結果</u>：

格線中不會顯示任何專案，但報表仍可使用。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
