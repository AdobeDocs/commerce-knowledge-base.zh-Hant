---
title: 'MDVA-31021：如果有多個產品選項，匯入和匯出會很慢'
description: MDVA-31021修補程式可解決匯入/匯出大量產品選項所需時間比預期更長的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021：如果有許多產品選項，匯入和匯出會很慢

MDVA-31021修補程式可解決匯入/匯出大量產品選項所需時間比預期更長的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果`catalog_product_option`表格中有100,000筆或以上的記錄，則匯入/匯出函式檔案驗證所花的時間會比預期長。 在匯入/匯出之前，為了檢查選項驗證，Adobe Commerce會載入所有現有產品的產品選項。

<u>必要條件</u>：

Adobe Commerce商店提供5000種產品搭配自訂選項。 每個產品應至少有四個自訂選項，且有兩個或多個選項可供選擇，以便`catalog_product_option`表格中有100,000筆記錄。

<u>要再現的步驟</u>：

1. 在&#x200B;**匯入**&#x200B;範例中：使用Commerce管理員的其中一個SKU建立CSV匯入檔案。
1. 新增四個自訂選項至CSV匯入檔案。
1. 嘗試從Commerce管理員匯入CSV檔案。

<u>預期結果</u>：

匯入或匯出功能會如預期般完成。 使用一種產品完成驗證只需要不到10秒。

<u>實際結果</u>：

匯入或匯出函式所需的時間比預期長。 僅需一個產品即可完成驗證，需時超過10秒。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
