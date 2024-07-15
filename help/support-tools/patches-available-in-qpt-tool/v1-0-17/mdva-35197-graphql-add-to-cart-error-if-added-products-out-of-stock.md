---
title: 「MDVA-35197：如果新增的產品無庫存，GraphQL會新增到購物車錯誤」
description: MDVA-35197修補程式修正了使用GraphQL新增到購物車時，如果先前新增的產品無庫存，則會發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17時，即可使用此修補程式。
exl-id: 189312f7-a505-4ba4-b12d-662987e69374
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-35197：如果新增的產品無庫存，則GraphQL新增到購物車錯誤

MDVA-35197修補程式修正了使用GraphQL新增到購物車時，如果先前新增的產品無庫存，則會發生錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.6

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

嘗試透過GraphQL將產品新增到購物車時，如果購物車中已有其他產品(也透過GraphQL新增)無庫存，便發生錯誤。

<u>要再現的步驟</u>：

1. 使用GraphQL新增任何產品至購物車。
1. 登入Commerce管理面板，並將此產品設定為無庫存。
1. 嘗試透過GraphQL將其他產品新增到購物車。

<u>預期結果</u>：

庫存產品可新增至購物車。

<u>實際結果</u>：

GraphQL錯誤訊息： *部分產品缺貨*。 無法新增新的「庫存」產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
