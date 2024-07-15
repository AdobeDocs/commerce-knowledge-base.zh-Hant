---
title: 'MDVA-34695：未顯示產品和類別'
description: MDVA-34695修補程式解決管理中類別格線未顯示產品和類別的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18後，即可使用此修補程式。 修補程式ID為MDVA-34695。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695：未顯示產品和類別

MDVA-34695修補程式解決管理中類別格線未顯示產品和類別的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18時，即可使用此修補程式。 修補程式ID為MDVA-34695。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.4

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.0-2.4.0-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

刪除類別後，`children_count`的負值會出現在資料庫中。

<u>要再現的步驟</u>：

1. 登入管理員後端。
1. 導覽至&#x200B;**目錄>類別**。
1. 按一下&#x200B;**新增子類別**。
1. 設定&#x200B;**類別名稱** = *父系1*，然後儲存。
1. 按一下&#x200B;**新增子類別**。
1. 設定&#x200B;**類別名稱** = *子項1*，然後儲存。
1. 按一下&#x200B;**新增子類別**。
1. 設定&#x200B;**類別名稱** = *子項2*，然後儲存。
1. 按一下&#x200B;**新增子類別**。
1. 設定&#x200B;**類別名稱** = *子項3*，然後儲存。 此時，此類別應該有層級= *5*。
1. 按一下&#x200B;**子項1**&#x200B;類別。
1. 刪除類別。

<u>預期結果</u>：

類別方格會如預期顯示產品和類別。

<u>實際結果</u>：

類別格線是空的。 檢查資料庫中的`catalog_category_entity`資料表。 請注意，`children_count`變成負數。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
