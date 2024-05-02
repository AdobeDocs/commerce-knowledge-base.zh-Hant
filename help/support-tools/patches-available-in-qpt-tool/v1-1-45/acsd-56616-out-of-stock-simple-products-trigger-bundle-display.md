---
title: 'ACSD-56616：簡單存貨短缺期間套件式產品的店面展示'
description: 套用ACSD-56616修補程式，修正Adobe Commerce發生的問題，亦即當所有相關的簡單產品無存貨時，店面會意外出現套裝產品。
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616：在簡單存貨短缺期間，店面會顯示套件式產品。

ACSD-56616修補程式修正所有相關簡單產品無庫存時，店面意外出現套件產品的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.45。 修補程式ID為ACSD-56616。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在簡單存貨短缺期間，捆綁產品的店面顯示不正確。

<u>要再現的步驟</u>：

1. 建立新網站/商店/店面。
1. 建立新的來源。
1. 建立新庫存並將其指派給新建立的網站。
1. 設定索引子以依排程更新。
1. 產生兩個簡單產品，S1 （數量= 1）和S2 （數量= 1），並將它們指派給新庫存和新網站。
1. 建立 *套件式1* 產品並將其與新網站建立關聯，然後放入類別 *類別*.
1. 定義兩個必要的下拉式清單選項並連結簡單產品 *S1* to option1和 *S2* 至option2。
1. 儲存產品。
1. 瀏覽至 **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** 並啟用 *將商店代碼新增至URL* = *是*.
1. 開啟店面並購買隨附產品。
1. 執行cron兩次。
1. 返回 *類別* 類別。

<u>預期結果</u>：

此 *組合1* 產品無庫存。

<u>實際結果</u>：

此 *組合1* 以價格顯示產品= *$0*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
