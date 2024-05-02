---
title: 'ACSD-51666： 「工作階段已過期，請重新登入」錯誤。 在您登入後'
description: 套用ACSD-51666修補程式以修正錯誤*工作階段已過期的Adobe Commerce問題，請重新登入。*會在您嘗試登入後發生。
feature: Customers
role: Admin, Developer
exl-id: c3913f1c-f401-440b-b6b3-10702f13fff5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-51666：錯誤 *工作階段已過期，請重新登入。* 在您登入後

ACSD-51666修補程式修正了錯誤的問題 *工作階段已過期，請重新登入。* 在您嘗試登入後發生。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.36。 修補程式ID為ACSD-51666。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

您收到錯誤 *工作階段已過期，請重新登入。* 當在不同裝置上重設密碼後，嘗試從一部裝置使用新密碼登入時。 只有在自訂模組新增的頁面上有其他Ajax要求時，才會發生這種情況。

<u>要再現的步驟</u>：

1. 安裝自訂模組，在店面的每個頁面上新增Ajax請求。
1. 建立新帳戶。
1. 登出並返回登入頁面。
1. 開啟 *忘記密碼* 連結至不同的瀏覽器，然後傳送 *重設密碼* 電子郵件。
1. 在第一個瀏覽器中開啟重設密碼電子郵件，並設定新密碼。
1. 請嘗試使用第二個瀏覽器登入。

<u>預期結果</u>：

第一次嘗試時，您就能成功登入。

<u>實際結果</u>：

* 您會看到 *工作階段已過期，請重新登入。* 錯誤。
* 您並未登入，且已重新導向至首頁。
* 您的第二次登入嘗試成功。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
