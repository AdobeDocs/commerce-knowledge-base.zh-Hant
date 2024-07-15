---
title: 'MDVA-29042：全域類別許可權未變更'
description: MDVA-29042修補程式修正在Commerce管理員中將新產品新增至共用目錄後，目錄許可權自動變更為"*Allow*"的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5後，即可使用此修補程式。 請注意，Adobe Commerce 2.3.6已透過B2B擴充功能修正問題。
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# mdva-29042：全域類別許可權未變更

MDVA-29042修補程式修正了將新產品新增至Commerce管理員的共用目錄後，目錄許可權自動變更為&quot;*允許*&quot;的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5時，即可使用此修補程式。 請注意，Adobe Commerce 2.3.6已透過B2B擴充功能修正問題。

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.3.3到2.3.4-p2 （含B2B擴充功能）

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從Commerce管理員中的全域類別許可權中取消選取客戶群組，不會在類別許可權內自動將該客戶群組設為&quot;*拒絕*&quot;。

<u>必要條件</u>：

* 在&#x200B;**商店** > **設定** > **目錄** > **目錄** > **類別許可權**&#x200B;下定義並選取具有客戶群組的B2B執行個體：
   * **允許瀏覽類別**
   * **顯示產品價格**
   * **允許加入購物車**
* 在每個&#x200B;**類別**&#x200B;下，客戶群組被定義為&quot;*允許*&quot;：
   * **瀏覽類別**
   * **顯示產品價格**
   * **加入購物車**

<u>要再現的步驟</u>：

1. 在Commerce Admin中，移至&#x200B;**商店** > **設定** > **目錄** > **目錄** > **類別許可權**，並從下列位置取消選取客戶群組：
   * **允許瀏覽類別**
   * **顯示產品價格**
   * **允許加入購物車**
1. 按一下&#x200B;**儲存設定**&#x200B;按鈕。
1. 等候索引子執行。
1. 檢視&#x200B;**目錄** > **類別** > **類別許可權**。

<u>預期結果</u>：

針對客戶群組的所有類別，**類別許可權**&#x200B;將設為&#x200B;*拒絕*。

<u>實際結果</u>：

客戶群組的任何類別許可權沒有變更。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。

若要深入瞭解B2B公司功能，請參閱開發人員檔案中的下列文章：

* [B2B開發人員指南](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [管理公司角色](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Adobe Commerce Enterprise B2B擴充功能組態路徑參考](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
