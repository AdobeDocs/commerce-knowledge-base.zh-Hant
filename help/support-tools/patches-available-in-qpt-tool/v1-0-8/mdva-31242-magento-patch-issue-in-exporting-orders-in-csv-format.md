---
title: 'MDVA-31242：以CSV格式匯出訂單時出現問題'
description: MDVA-31242修補程式可解決以CSV檔案格式匯出訂單時發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 1e343f23-5b10-492b-885f-8113ace4777f
feature: B2B, Data Import/Export, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# MDVA-31242：以CSV格式匯出訂單時出現問題

MDVA-31242修補程式可解決以CSV檔案格式匯出訂單時發生錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

* Adobe Commerce （部署方法） 2.3.0 - 2.4.0-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 登入管理員後端。
1. 在&#x200B;**商店** > **組態** > **B2B功能**&#x200B;啟用&#x200B;**公司**。
1. 移至&#x200B;**銷售** > **訂單**。
1. 按一下「**欄** > **公司名稱**」核取方塊。
1. 在&#x200B;**篩選器** > **公司名稱**&#x200B;文字欄位中輸入任何值。
1. 按一下&#x200B;**套用篩選器**&#x200B;按鈕。
1. 按一下「**匯出** > **CSV** > **匯出**」按鈕。

<u>預期結果</u>：

選取的檔案快顯視窗會如預期般開啟。

<u>實際結果</u>：

白色熒幕發生錯誤&#x200B;*處理您的請求時發生錯誤*&#x200B;例外狀況已顯示。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
