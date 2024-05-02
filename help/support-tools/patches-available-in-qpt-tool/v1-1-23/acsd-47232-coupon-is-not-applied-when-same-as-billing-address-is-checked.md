---
title: 'ACSD-47232：優惠券未套用時機 [!UICONTROL Same as Billing Address] 已勾選'
description: 套用ACSD-47232修補程式，修正Adobe Commerce發生以下情況時未套用優惠券的問題： [!UICONTROL Same as Billing Address] 已勾選。
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232：優惠券未套用時機 [!UICONTROL Same as Billing Address] 已勾選

ACSD-47232修補程式修正以下情況下未套用抵用券的問題： **[!UICONTROL Same as Billing Address]** 已勾選。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.23。 修補程式ID為ACSD-47232。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

優惠券未套用時機 **[!UICONTROL Same as Billing Address]** 已勾選。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce。
1. 建立簡單的產品，其重量為= *8*.
1. 建立具有預設帳單和送貨地址的新客戶。
1. 使用優惠券建立購物車價格規則。
   * 在 **[!UICONTROL Conditions]** 部分，新增 *總權重等於或大於5*
1. 嘗試在中建立新訂單 [!UICONTROL Commerce] 管理員。
   * 使用剛才建立的客戶
   * 新增產品
   * 嘗試套用抵用券

<u>預期結果</u>：

已套用抵用券。

<u>實際結果</u>：

您會收到類似下列的錯誤： *123優惠券代碼無效。 請驗證代碼，然後再試一次。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
