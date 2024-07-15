---
title: 「MDVA-35982：無法送出部分訂單」
description: MDVA-35982修補程式修正了僅限特定網站的管理員使用者無法為同一網站上的訂單建立出貨的錯誤。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19後，即可使用此修補程式。 修補程式ID為MDVA-35982。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982：無法出貨部分訂單

MDVA-35982修補程式修正了僅限特定網站的管理員使用者無法為同一網站上的訂單建立出貨的錯誤。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19時，即可使用此修補程式。 修補程式ID為MDVA-35982。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.5-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.0 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

商家無法運送某些訂單。

<u>要再現的步驟</u>：

1. 選擇產品的任何產品網站，預設商店除外。 請參閱使用手冊中的[網站產品](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html)，瞭解詳細步驟。
1. 為具有自訂角色範圍的管理員建立使用者角色，其中未選取預設網站/商店。 請參閱使用手冊中的[定義角色](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role)以取得詳細步驟。
1. 以編輯模式開啟產品，並設定此產品的群組價格（在&#x200B;**進階價格**&#x200B;中）。 請參閱使用手冊中的[群組價格](https://docs.magento.com/user-guide/catalog/product-price-group.html)以取得詳細步驟。
1. 建立此產品的訂單。
1. 以此使用者角色登入「管理員」底下，並建立出貨。 請參閱使用手冊中的[建立出貨](https://docs.magento.com/user-guide/sales/shipments-create.html)，以取得詳細步驟。

<u>預期結果</u>：

出貨已建立。

<u>實際結果</u>：

會顯示下列錯誤：

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
