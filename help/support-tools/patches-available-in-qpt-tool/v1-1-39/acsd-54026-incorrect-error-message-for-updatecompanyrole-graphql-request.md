---
title: 'ACSD-54026：updateCompanyRole GraphQL請求出現不正確的錯誤訊息'
description: 套用ACSD-54026修補程式以修正Adobe Commerce問題，其中針對非授權使用者的updateCompanyRole GraphQL請求存在不正確的錯誤訊息。
feature: Roles/Permissions
role: Admin, Developer
exl-id: c18a8815-975a-499d-a372-8635d89aa673
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-54026：不正確的錯誤訊息 `updateCompanyRole` GraphQL要求

ACSD-54026修補程式修正 `updateCompanyRole` 非授權使用者的GraphQL請求。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.39。 修補程式ID為ACSD-54026。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

取得不正確的錯誤訊息 `updateCompanyRole` 非授權使用者的GraphQL請求。

<u>要再現的步驟</u>：

1. 在設定中啟用B2B公司。
1. 建立公司。
1. 傳送 `updateCompanyRole` GraphQL要求未傳遞持有人權杖或持有人權杖無效。
1. 觀察GraphQL回應中的錯誤訊息。

<u>預期結果</u>：

您會收到下列錯誤訊息： *目前客戶未獲授權。*

<u>實際結果</u>：

您會收到下列錯誤訊息： *客戶不是公司使用者。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
