---
title: 「ACSD-54472：被拒絕公司的客戶仍然可以驗證」
description: 套用ACSD-54472修補程式以修正遭拒絕公司的客戶仍可驗證，以及遭封鎖和遭拒絕公司的客戶仍可下訂單的Adobe Commerce問題。
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472：被拒絕公司的客戶仍可驗證

ACSD-54472修補程式修正被拒絕公司的客戶仍可驗證，以及被封鎖和拒絕公司的客戶仍可下訂單的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.40。 修補程式ID為ACSD-54472。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

被拒絕公司的客戶仍然可以驗證，被封鎖和被拒絕公司的客戶仍然可以下訂單。

<u>要再現的步驟</u>：

1. 建立公司。
1. 透過將產品新增到購物車 [!DNL GraphQL].
1. 將公司狀態變更為 *已封鎖*.
1. 傳送 [!DNL GraphQL] 請求下單並建立可轉讓的報價。
1. 將公司狀態變更為 *已拒絕*.
1. 傳送 [!DNL GraphQL] 要求取得公司的使用者授權權杖。
1. 將客戶狀態設為 *非使用中*.
1. 傳送 [!DNL GraphQL] 要求取得公司的使用者授權權杖。

<u>預期結果</u>：

* 訂單與可轉讓報價單不是由以下使用者下單： *已封鎖* 公司。
* 未為的使用者取得授權權杖 *已拒絕* 公司。
* 未取得授權權杖給 *非使用中* 客戶。

<u>實際結果</u>：

* 訂單與可轉讓報價由以下使用者下單： *已封鎖* 公司。
* 已為的使用者取得授權權杖 *已拒絕* 公司。
* 已為取得授權權杖 *非使用中* 客戶。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
