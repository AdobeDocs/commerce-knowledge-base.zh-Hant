---
title: 'MDVA-28300：GraphQL中目錄價格規則的價格計算問題'
description: MDVA-28300修補程式修正GraphQL要求無法反映目錄價格規則之價格變更的問題。 安裝Quality Patches Tool (QPT) v.1.0.6後，即可使用此修補程式。 請注意，Adobe Commerce 2.3.6版已修正問題。
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300：GraphQL中目錄價格規則的價格計算問題

>[!WARNING]
>
>名為MDVA-33975的新修補程式修正了GraphQL價格計算問題。 MDVA-28300已過時，建議您套用修補程式MDVA-33975。 若要存取此修補程式，請參閱 [MDVA-33975：GraphQL價格計算](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html).

MDVA-28300修補程式修正GraphQL要求無法反映目錄價格規則之價格變更的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝v.1.0.6。 請注意，Adobe Commerce 2.3.6版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：** Adobe Commerce內部部署2.3.5-p1

**與Adobe Commerce版本相容：** 雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將目錄價格規則套用至特定客戶群組時，在GraphQL中無法正確計算購物車和訂單總計中的專案價格。

<u>要再現的步驟：</u>

1. 建立新的客戶帳戶，並將其客戶群組變更為批發。
1. 在中建立新的目錄規則 **行銷** > **促銷活動** > **目錄價格規則** ，並使用下列引數：
   * 客戶群組：WriteralActions：
   * 套用： *套用為原始內容的百分比*
   * 折扣： *50*


1. 建立價格=100的新產品。
1. 使用先前建立的客戶帳戶登入前端（如果您已經登入，請先登出然後再登入）。
1. 將產品新增至購物車。 產品價格為50 （一般價格100），訂單總計：55 （50 + 5出貨成本）。
1. 執行中所述的GraphQL API呼叫 [customerCart查詢](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html) （位於我們的開發人員檔案中）。

<u>預期結果：</u>

API和前端都有相同的訂單總計，加上套用的目錄規則所提供的折扣。

<u>實際結果：</u>

訂單總計未套用型錄規則折扣。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [使用品質修補程式工具套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html).
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html).

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱QPT中可用的修補程式區段。
