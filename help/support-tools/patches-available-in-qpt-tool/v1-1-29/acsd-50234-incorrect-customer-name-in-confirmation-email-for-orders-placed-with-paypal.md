---
title: '''ACSD-50234：使用下訂單的確認電子郵件中的客戶名稱不正確 [!DNL PayPal]『'
description: 套用ACSD-50234修補程式，修正Adobe Commerce使用下訂單的確認電子郵件中客戶名稱顯示不正確的問題 [!DNL PayPal].
exl-id: b2e9c25a-5dd5-4b37-81e3-ca960078da77
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50234：使用下訂單的確認電子郵件中的客戶名稱不正確 [!DNL PayPal]

ACSD-50234修補程式修正了使用下訂單的確認電子郵件中，客戶名稱顯示不正確的問題 [!DNL PayPal]. 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.29。 修補程式ID為ACSD-50234。 請注意，問題已在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

訂單的確認電子郵件，使用 [!DNL PayPal] 顯示錯誤的客戶名稱。

<u>要再現的步驟</u>

1. 啟用 **[!UICONTROL PayPal Express Checkout]**.
1. 以訪客身分導覽至前端。
1. 將產品新增至購物車。
1. 結帳，使用 **[!UICONTROL PayPal Express Checkout]** 作為付款方式。
1. 檢查訂單確認電子郵件。

<u>預期結果</u>

訂單確認電子郵件、商業發票電子郵件及所有與出貨相關的電子郵件都會寄送給客戶的名稱。

<u>實際結果</u>

訂單確認電子郵件、發票電子郵件及所有與出貨相關的電子郵件皆寄送至 *來賓*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
