---
title: 'MDVA-36615：目錄產品格線篩選不正確的結果'
description: MDVA-36615修補程式修正管理產品格線中的產品計數不正確的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21後，即可使用此修補程式。 修補程式ID為MDVA-36615。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。
exl-id: 7ed70753-c637-4c13-8290-aa5e8a4d1b65
feature: Catalog Management, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-36615：目錄產品格線篩選不正確的結果

MDVA-36615修補程式修正管理產品格線中的產品計數不正確的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21時，即可使用此修補程式。 修補程式ID為MDVA-36615。 請注意，此問題已排程在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理產品格線中的產品計數不正確。

<u>要再現的步驟：</u>

1. 建立名稱中具有相同片語的簡單可設定產品（例如「red shirt」/「red shirt xs」）。
1. 在&#x200B;*管理員*&#x200B;側邊欄上，前往&#x200B;**目錄** > **產品** >搜尋此片語。
1. 按一下&#x200B;**篩選器**。 設定型別為&#x200B;*可設定的產品*。
1. 按一下&#x200B;**套用篩選器**。

<u>實際結果：</u>

相符產品計數器中的正確數字。

<u>預期結果：</u>

相符產品計數器中的數字不正確。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
