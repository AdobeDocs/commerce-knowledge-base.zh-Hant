---
title: 「ACSD-58446：透過GraphQL刪除具有子使用者或團隊的團隊會出現無法提供資訊的錯誤訊息」
description: 套用ACSD-58446修補程式以修正Adobe Commerce的問題，也就是透過GraphQL刪除具有子使用者或團隊的團隊時，會傳回與UI不一致的無法提供資訊的錯誤訊息。
feature: Product, GraphQL, Company
role: Admin, Developer
source-git-commit: ab290f7c5b052aa220b3ef003febd9afc1cfdf00
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-58446：透過GraphQL刪除具有子使用者或團隊的團隊會產生無法提供資訊的錯誤訊息

ACSD-58446修補程式修正Adobe Commerce透過GraphQL刪除具有子使用者或團隊的團隊時傳回與UI不一致的無法提供資訊的錯誤訊息的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49時，即可使用此修補程式。 修補程式ID為ACSD-58446。 請注意，此問題已排程在Adobe Commerce B2B 1.5.1中修正

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce和Magento Open Source版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過GraphQL刪除具有子使用者或團隊的團隊會傳回與UI不一致的無法提供資訊的錯誤訊息。

## 先決條件：

已安裝的B2B模組。

<u>要再現的步驟</u>：

1. 啟用&#x200B;*[!UICONTROL Company]*&#x200B;功能。
1. 建立新的公司帳戶。
1. 登入&#x200B;**[!UICONTROL Admin]**&#x200B;並讓公司帳戶生效。
1. 檢查電子郵件並設定新公司帳戶的密碼。
1. 為公司建立新團隊。
1. 從前端以&#x200B;**[!UICONTROL company user]**&#x200B;登入，並為建立的團隊新增&#x200B;**[!UICONTROL new user]**。
1. 登入&#x200B;**[!UICONTROL Admin]**，停用公司使用者，並設定&#x200B;*[!UICONTROL Customer Active]* = *否*
1. 請務必透過GraphQL刪除建立的團隊。

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>預期結果</u>：

系統傳回與UI一致的資訊性錯誤訊息。

<u>實際結果</u>：

傳回一般內部伺服器錯誤訊息。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。