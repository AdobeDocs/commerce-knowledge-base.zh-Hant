---
title: 'MDVA-36833：搜尋結果頁面上的分頁中斷'
description: MDVA-36833修補程式修正了在啟用共用目錄且將部分產品從共用目錄排除時，分頁中斷的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22時，即可使用此修補程式。 修補程式ID為MDVA-36833。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833：搜尋結果頁面上的分頁中斷

MDVA-36833修補程式修正了在啟用共用目錄且將部分產品從共用目錄排除時，分頁中斷的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22時，即可使用此修補程式。 修補程式ID為MDVA-36833。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** Adobe Commerce （所有部署方法） 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從共用目錄排除某些產品會導致搜尋結果的分頁中斷。

<u>要再現的步驟：</u>

1. 啟用共用目錄。
1. 移至&#x200B;**目錄** > **共用目錄**，並透過指派所有產品來設定預設的共用目錄。
1. 載入店面並搜尋「jacket」。
1. 記下第一頁上列出的產品。 應該有12種產品。
1. 從第一頁開始記下11個SKU。 移至後端並載入預設共用目錄。
1. 從預設共用目錄中取消指派先前記錄的SKU。
1. 前往店面搜尋「夾克」。
1. 檢查搜尋結果的第一頁。

<u>實際結果：</u>

第一頁有一個產品，其餘產品可在第二頁取得。

<u>預期結果：</u>

第一頁應該有12種產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。


## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
