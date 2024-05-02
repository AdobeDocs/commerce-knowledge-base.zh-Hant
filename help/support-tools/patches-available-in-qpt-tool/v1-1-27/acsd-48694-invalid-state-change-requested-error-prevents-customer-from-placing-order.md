---
title: 「ACSD-48694：要求的狀態變更無效」錯誤導致客戶無法下訂單」
description: 套用ACSD-48694修補程式以修正Adobe Commerce問題，其中錯誤*請求的無效狀態變更*會阻止客戶下訂單。
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694： *要求的狀態變更無效* 錯誤導致客戶無法下訂單

ACSD-48694修補程式修正了錯誤的問題 *要求的狀態變更無效* 防止客戶下訂單。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.27。 修補程式ID為ACSD-48694。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.37-p4， 2.4.1 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤 *要求的狀態變更無效* 防止客戶下訂單。

<u>要再現的步驟</u>：

1. 在此期間新增輕微延遲 `/estimate-shipping-methods` 透過包含 `sleep()` 在 `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` 函式，因此 `/estimate-shipping-methods` 要求於以下日期後完成： `/shipping-information` 結帳期間，從運送步驟移至付款步驟時。
1. 設定要使用的工作階段 [!DNL Redis] 使用 *disable_locking： 1* 設定。
1. 開啟 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** 並啟用 *[!UICONTROL Persistent Shopping Cart]*.
1. 以客戶身分登入，並將產品新增至購物車。
1. 讓客戶工作階段過期。 永久性Cookie和購物車仍持續存在。
1. 現在前往結帳，新增運送地址並導覽至付款區段。
1. 返回首頁或任何其他頁面，並使用客戶帳戶登入。
1. 讓工作階段再次過期。
1. 現在直接前往結帳頁面，並導覽至付款步驟。
1. 嘗試下訂單。

<u>預期結果</u>：

* 沒有錯誤。
* 已成功下訂單，且 *感謝您* 頁面隨即顯示。

<u>實際結果</u>：

錯誤 *要求的狀態變更無效* 會顯示，但會下訂單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
