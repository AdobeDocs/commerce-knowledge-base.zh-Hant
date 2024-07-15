---
title: 「MDVA-30593修補程式：過期引號未清除」
description: MDVA-30593修補程式可解決根據**Quote Lifetime**設定過期的報價未清除的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5後，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.3.4中修正。
exl-id: 5ee91546-a5cb-4282-bdfc-c9bb3438af50
feature: Cache, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# MDVA-30593修補程式：過期引號未清除

MDVA-30593修補程式可解決根據&#x200B;**報價存留期**&#x200B;設定到期的報價未清除的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.3.4中修正。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.3.0 - 2.3.3.x

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

根據&#x200B;**報價存留期**&#x200B;設定過期的報價未清除。

<u>要再現的步驟：</u>

1. 在Commerce Admin中，移至&#x200B;**商店** > **設定** > **銷售** > **結帳** > **購物車**。
1. 設定&#x200B;**報價存留期（天）** = *1*
1. 儲存設定並清除快取。
1. 以客戶身分登入。
1. 新增產品至購物車。
1. 一天後，返回購物車。

<u>預期結果：</u>

報價單已清除，產品也將從購物車中移除，因為舊的價格已不再有效。

<u>實際結果：</u>

產品仍在購物車中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
