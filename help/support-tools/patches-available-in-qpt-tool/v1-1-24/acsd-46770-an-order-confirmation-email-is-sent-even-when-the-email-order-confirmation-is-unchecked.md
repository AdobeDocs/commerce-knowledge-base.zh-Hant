---
title: 'ACSD-46770：訂單確認電子郵件即使在 [!UICONTROL Email Order Confirmation] 已取消勾選'
description: 套用ACSD-46770修補程式以修正傳送訂單確認電子郵件的Adobe Commerce問題，即使 [!UICONTROL Email Order Confirmation] 未選取。
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770：訂單確認電子郵件即使在 **[!UICONTROL Email Order Confirmation]** 已取消勾選

ACSD-46770修補程式修正了透過REST API以訪客使用者身分下訂單的問題，即使在 **[!UICONTROL Email Order Confirmation]** 已取消選取。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.24。 修補程式ID為ACSD-46770。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使發生下列情況，也會傳送訂單確認電子郵件 **[!UICONTROL Email Order Confirmation]** 未選取。

<u>要再現的步驟</u>：

1. 建立客戶帳戶。
1. 前往 **[!UICONTROL Sales]** > **[!UICONTROL Order]** 並按一下  **[!UICONTROL Create New Order]**.
1. 選取客戶、將產品新增至訂單、填寫地址，然後選取「送貨」與「付款」方式。
1. 在提交訂單之前，取消選取 **[!UICONTROL Email Order confirmation]** 核取方塊。
1. 按一下 **[!UICONTROL Submit Order]** 以建立訂單。

<u>預期結果</u>：

若發生下列情況，則不應傳送訂單確認電子郵件： **[!UICONTROL Email Order Confirmation]** 已取消選取。

<u>實際結果</u>：

無論是否取消選取，都會傳送訂單確認電子郵件 **[!UICONTROL Email Order Confirmation]** 核取方塊。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
