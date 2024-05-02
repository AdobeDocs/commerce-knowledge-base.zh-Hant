---
title: 'ACSD-55566： [!UICONTROL mergeCart] 變異失敗，發生內部伺服器錯誤 [!DNL GraphQL] 回應'
description: 套用ACSD-55566修補程式，修正Adobe Commerce問題，該問題導致「mergeCart」突變失敗，並出現內部伺服器錯誤。 [!DNL GraphQL] 在合併具有相同組合專案的來源和目的地購物車時回應。
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84a9b861-351e-4fcc-bb91-3e31c7ae24e6
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-55566： `mergeCart` 變異失敗，發生內部伺服器錯誤 [!DNL GraphQL] 回應

ACSD-55566修補程式修正了 `mergeCart` 變異失敗，且發生內部伺服器錯誤 [!DNL GraphQL] 回應。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.48。 修補程式ID為ACSD-55566。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`mergeCart` 變異失敗，且發生內部伺服器錯誤 [!DNL GraphQL] 在合併具有相同組合專案的來源和目的地購物車時回應。

<u>要再現的步驟</u>：

1. 建立自訂來源與自訂庫存。
1. 將建立的庫存指派給主要網站。
1. 建立簡單產品並將建立的來源指派給它（數量=2）。
1. 建立一個包含一個選項和一個子產品的套件產品（在步驟3中建立的產品）。
1. 建立訪客購物車，透過 [!DNL GraphQL].
1. 新增已選取兩個選項的套件組合產品。
1. 儲存 *cartID*.
1. 建立客戶並產生客戶代號。
1. 建立客戶購物車。
1. 將具有相同設定的相同套件產品新增至購物車。
1. 嘗試將訪客購物車與客戶購物車合併。

<u>預期結果</u>：

客戶購物車包含來自兩個購物車的產品。

<u>實際結果</u>：

您收到內部錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
