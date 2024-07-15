---
title: 'MDVA-28191：「管理員建立新訂單」中一個網站沒有付款方式'
description: MDVA-28191修補程式修正了某個網站的管理員**建立新訂單**中未載入付款方式的問題，不過其他網站可能會顯示付款方式。  安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)工具1.0.5版時，即可使用此修補程式。
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191：「管理員建立新訂單」中沒有網站的付款方式

MDVA-28191修補程式修正了在管理員&#x200B;**為某個網站建立新訂單**&#x200B;中並未載入付款方式的問題，不過其他網站可能會顯示付款方式。  安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)工具1.0.5版時，即可使用此修補程式。

## 受影響的產品和版本

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.3到2.4.1 （包括2.3.5-p1）。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從後端Adobe Commerce建立訂單時，會建立兩個報價單，一個為非使用中，另一個為使用中。 但工作階段會保留非使用中的報價識別碼。

<u>要再現的步驟</u>

1. 移至&#x200B;**管理面板** > **銷售** > **訂單**，然後按一下&#x200B;**建立新訂單**&#x200B;按鈕。
1. 選擇要建立訂單的客戶。
1. 如果您的商店有多個檢視，請在所選使用者的&#x200B;**建立新訂單**&#x200B;頁面上，選擇要下訂單的商店檢視。
1. 按一下&#x200B;**新增產品**，從&#x200B;**客戶的活動**&#x200B;區段或目錄新增產品。 向下捲動頁面，視需要完成訂單的下列區段：
   * 套用優惠券代碼
   * 付款方法
   * 送貨方法
   * 訂單註解

<u>預期結果：</u>

應在所有網站的Admin中載入付款方法。

<u>實際結果：</u>

雖然測試其他網站的訂單時可能會顯示付款方式，但此網站沒有可用的付款方式（亦未顯示&quot;*不需要付款資訊*&quot;訊息）。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
