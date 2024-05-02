---
title: 'ACSD-56621：更新後的名稱未顯示在公司管理員使用者的問候語標題中'
description: 套用ACSD-56621修補程式以修正Adobe Commerce問題，該問題導致更新後的公司管理員使用者名字和姓氏未反映在問候語標題區段中。
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 4ad9c878-b617-4e6a-939c-be15faf7124b
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621：更新後的名稱未顯示在公司管理員使用者的問候語標題中

ACSD-56621修補程式修正了Greetings標頭區段中未反映公司管理員使用者更新名字和姓氏的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.46。 修補程式ID為ACSD-56621。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

更新的名稱不會顯示在公司管理員使用者的問候語標題中。

<u>要再現的步驟</u>：

1. 導覽至 **[!UICONTROL Admin]** 面板。
1. 前往 **[!UICONTROL Stores]** 並選取 **[!UICONTROL Configuration]**.
1. 在 **[!UICONTROL General]** 區段，選取 **[!UICONTROL B2B]** 以啟用B2B公司功能。
1. 前往 **[!UICONTROL Storefront]** 並註冊新公司。
1. 以公司管理員使用者身分登入。
1. 前往 **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** 並視需要修改名字和姓氏欄位。

<u>預期結果</u>：

問候語標題區段中使用者的名字和姓氏會立即變更。

<u>實際結果</u>：

使用者的名字和姓氏只有在使用者登出並再次登入時才會變更。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
