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

MDVA-29042修補程式修正目錄許可權變更為&#39;&#39;的問題&#x200B;*允許*「在Commerce管理員中將新產品新增至共用目錄後自動進行。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.5。 請注意，Adobe Commerce 2.3.6已透過B2B擴充功能修正問題。

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.3.3到2.3.4-p2 （含B2B擴充功能）

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在Commerce管理員中，從全域類別許可權中取消選取客戶群組時，不會自動將該客戶群組設為&quot;*拒絕*&#x200B;類別許可權內的「」。

<u>必要條件</u>：

* 在下定義並選取客戶群組的B2B執行個體 **商店** > **設定** > **目錄** > **目錄** > **類別許可權** 針對：
   * **允許瀏覽類別**
   * **顯示產品價格**
   * **允許加入購物車**
* 在每個底下 **類別**，客戶群組會定義為「*允許*「，代表：
   * **瀏覽類別**
   * **顯示產品價格**
   * **加入購物車**

<u>要再現的步驟</u>：

1. 在Commerce Admin中，前往 **商店** > **設定** > **目錄** > **目錄** > **類別許可權** 並從下列位置取消選取客戶群組：
   * **允許瀏覽類別**
   * **顯示產品價格**
   * **允許加入購物車**
1. 按一下 **儲存設定** 按鈕。
1. 等候索引子執行。
1. 檢視 **目錄** > **類別** > **類別許可權**.

<u>預期結果</u>：

**類別許可權** 將設為&quot;*拒絕*」代表客戶群組的所有類別。

<u>實際結果</u>：

客戶群組的任何類別許可權沒有變更。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。

若要深入瞭解B2B公司功能，請參閱開發人員檔案中的下列文章：

* [B2B開發人員指南](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [管理公司角色](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Adobe Commerce Enterprise B2B擴充功能設定路徑參考](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
