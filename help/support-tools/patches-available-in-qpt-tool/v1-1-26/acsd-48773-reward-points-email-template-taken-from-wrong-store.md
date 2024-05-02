---
title: 'ACSD-48773：從錯誤的商店取得的獎勵點數電子郵件範本'
description: 套用ACSD-48773修補程式，修正從錯誤商店取得獎勵點數電子郵件範本的Adobe Commerce問題。
exl-id: 96dda97c-5177-4883-ad2b-709928cb5f4d
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-48773：從錯誤的商店取得的獎勵點數電子郵件範本

ACSD-48773修補程式修正了從錯誤商店取得獎勵點電子郵件範本的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.26。 修補程式ID為ACSD-48773。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果套件組合產品未指派給任何網站，則產品價格重新指數無法運作。

<u>要再現的步驟</u>：

1. 建立2個網站、2個商店和2個商店檢視。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** 並啟用 **[!UICONTROL Reviews]**.
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
切換至 **[!DNL default website scope]**，並設定 **[!UICONTROL Customer Support Sender Email]** 位址(例如： *support_base@example.com*)。
切換至 **[!DNL second website scope]**，並設定 **[!UICONTROL Customer Support Sender Email]** 位址至另一個值(例如： *support_second@example.com*)。
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**，並設定 **[!UICONTROL Share Customer Accounts]** = *每個網站*.
1. 在 **[!UICONTROL Reward Points]**，設定下列專案：
   **[!UICONTROL Enable Reward Points Functionality]** = *是*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *是*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** 並設定 **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** 並設定 **[!UICONTROL Email Sender]** = *客戶支援*
1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** 並為兩個網站設定第二個網站的匯率 **[!UICONTROL Points/Currency]** 和 **[!UICONTROL Currency/Points]**.
1. 在第二個網站上建立客戶帳戶。
1. 以客戶身分登入第二個網站。
1. 請務必啟用 **[!UICONTROL Subscribe]** 的 **[!UICONTROL Balance Updates]**.
1. 提交產品評論。
1. 前往 **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. 將新稽核的狀態變更為 ***[!UICONTROL Approved]*** 和 **[!UICONTROL Save]**.
1. 等候電子郵件送達。

<u>預期結果</u>：

第二個網站範圍上設定的電子郵件寄件者應該已傳送獎勵點數更新電子郵件。

<u>實際結果</u>：

預設網站範圍上設定的電子郵件寄件者已傳送獎勵點數更新電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
