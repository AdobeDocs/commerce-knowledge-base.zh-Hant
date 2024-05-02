---
title: 'ACSD-53643：下採購單時訂單總計不正確'
description: 套用ACSD-53643修補程式，修正訂購已停用或無存貨的產品時，訂單總計有誤的Adobe Commerce問題。
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643：下採購單時，訂單總計不正確

ACSD-53643修補程式修正訂購停用或無庫存產品時，訂單總計有誤的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.41。 修補程式ID為ACSD-53643。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

訂購停用或無庫存產品的訂單時，訂單總計不正確。

<u>要再現的步驟</u>：

1. 安裝 *[!UICONTROL B2B]* 和 *[!UICONTROL Inventory]*.
1. 前往 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** 並設定 **[!UICONTROL Company]** = *是* 和 **[!UICONTROL Purchase Order]** = *是*.
1. 清除設定快取。
1. 建立新公司、啟用其並啟用 *[!UICONTROL Purchase order]* 適用於公司。
1. 為公司建立新使用者。
1. 建立 *核准規則* 若要核准所有訂單超過 *1美元* 由公司管理員執行。
1. 建立其他來源。
1. 以新公司使用者的身分登入。
1. 新增兩個產品至購物車並下訂單。
1. 停用第二個產品。
1. 以公司管理員身分登入。
1. 開啟採購單，並檢視採購單是否同時包含產品，而且總金額是兩個產品的總和。
1. 核准採購單。
1. 下訂單。
1. 開啟訂單詳細資料。

<u>預期結果</u>：

* 即使訂單中的一個產品為，也無法下訂單 *已停用* 或 *無庫存*.
* *[!UICONTROL Place Order]* 按鈕已隱藏。

<u>實際結果</u>：

已下單的訂單僅包含第一個使用中產品，但會計算兩個產品的訂單總計。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
