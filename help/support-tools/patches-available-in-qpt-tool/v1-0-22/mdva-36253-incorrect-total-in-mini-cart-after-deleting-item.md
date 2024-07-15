---
title: 'MDVA-36253：刪除專案後，迷你購物車中的總計不正確'
description: MDVA-36253修補程式可解決使用多重出貨結帳步驟時，當您刪除產品後返回迷你購物車頁面時，產品價格未更新的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22時，即可使用此修補程式。 修補程式ID為MDVA-36253。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: cbd436d7-7fbd-46dd-97cf-30f709da1ce5
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-36253：刪除專案後，迷你購物車中的總計不正確

MDVA-36253修補程式可解決使用多重出貨結帳步驟時，當您刪除產品後返回迷你購物車頁面時，產品價格未更新的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22時，即可使用此修補程式。 修補程式ID為MDVA-36253。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.0-2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

刪除專案後，迷你購物車中的總計不正確。

<u>要再現的步驟</u>：

1. 以至少有一個位址的客戶身分登入。
1. 新增四種產品至購物車（價格=每件$10）。
1. 前往購物車並按一下&#x200B;**使用多個地址結帳**。
1. 移除一個專案。
1. 導覽回首頁。
1. 開啟購物車並檢查總價。

<u>預期結果</u>：

總計為$30。

<u>實際結果</u>：

總計為$40。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
