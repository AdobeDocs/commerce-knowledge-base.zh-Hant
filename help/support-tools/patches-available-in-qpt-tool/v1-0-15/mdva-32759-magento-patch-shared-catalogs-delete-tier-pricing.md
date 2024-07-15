---
title: 'MDVA-32759修補程式：共用目錄刪除層定價'
description: MDVA-32759修補程式可解決共用目錄刪除現有層級定價的問題。
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-32759修補程式：共用目錄刪除層定價

MDVA-32759修補程式可解決共用目錄刪除現有層級定價的問題。

安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.4-p2

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>必要條件</u>：

安裝Adobe Commerce並啟用&#x200B;**B2B功能**。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店>設定> B2B功能>啟用公司**&#x200B;和&#x200B;**共用目錄**。
1. 執行`bin/magento cron:run`。
1. 建立簡單的產品，按一下&#x200B;**進階價格**，然後新增&#x200B;**目錄與階層價格**，然後儲存。
1. 移至&#x200B;**目錄>共用目錄>設定價格與結構**，按一下&#x200B;**設定**，然後從下拉式功能表中取消選取所有選項並儲存。
1. 執行`bin/magento cron:run`。
1. 開啟上述建立的產品，然後檢查進階定價。

<u>預期結果</u>：

從公用共用目錄移除所有產品後，不應如預期從產品移除層級價格。

<u>實際結果</u>：

從公用共用目錄移除所有產品後，就會移除階層價格。


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
