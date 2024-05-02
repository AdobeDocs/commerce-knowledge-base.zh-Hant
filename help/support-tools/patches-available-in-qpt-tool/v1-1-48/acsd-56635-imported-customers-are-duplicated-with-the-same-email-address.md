---
title: '''ACSD-56635：帳戶共用設為時，匯入的客戶會重複 [!DNL Global]『'
description: 套用ACSD-56635修補程式，修正在帳戶共用設為的情況下使用匯入時，匯入的客戶會以相同的電子郵件地址重複的Adobe Commerce問題 [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
source-git-commit: 86d752c9c2791ef19960876afafe24fefe5d29ed
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635：帳戶共用設為，匯入的客戶會以相同的電子郵件地址重複 [!DNL Global]

ACSD-56635修補程式修正使用匯入作業，且帳戶共用設為「 」時，匯入的客戶會以相同的電子郵件地址重複的問題 [!DNL Global]. 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.48。 修補程式ID為ACSD-56635。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當帳戶共用設定為時，匯入的客戶會以相同的電子郵件地址重複 [!DNL Global].

<u>要再現的步驟</u>：

1. 在Adobe Commerce （2.4 — 開發b2b）底下 **[!UICONTROL Admin]**，存取 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. 設定 *[!UICONTROL Share Customer Accounts]* 將設為 *[!DNL Global]*.
1. 建立多個網站和商店：

   * ws1 > s11， s12 > sw111， sw122
   * ws2 > s21， s22 > sw211， sw212

1. 在下建立新客戶 *主要網站* 來自管理員，電子郵件地址為 <adb@yormail.com>.
1. 在 **[!UICONTROL Admin]**，導覽至 **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. 選取 **[!UICONTROL Customer Entity Type]** 作為 *[!UICONTROL Customers Main File]*.
1. 使用與相同的電子郵件地址 <adb@yormail.com> 位於不同的網站，例如ws1。 請參閱下方提供的範例CSV檔案customer.csv 。
1. 完成匯入，檢視下建立的新使用者 *ws1* 具有相同電子郵件地址的網站。

customer.csv內容：

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>預期結果</u>：

會更新具有相同電子郵件地址的匯入客戶，而非進行複製。

<u>實際結果</u>：

使用客戶匯入時，系統會使用相同的電子郵件地址建立重複客戶。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
