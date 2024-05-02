---
title: '''ACSD-54989：以下情況時公司管理員無法訂購 [!UICONTROL Enable Purchase Orders] 設為「是」且 [!UICONTROL Purchase Order] 設為「否」'
description: 套用ACSD-54989修補程式以修正Adobe Commerce在下列情況下公司管理員無法下單的問題 [!UICONTROL Enable Purchase Orders] 設為「是」且 [!UICONTROL Purchase Order] 設為「否」。
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989：以下情況時公司管理員無法訂購 *[!UICONTROL Enable Purchase Orders]* 設為 *是* 和 *[!UICONTROL Purchase Order]* 設為 *否*

ACSD-54989修補程式修正下列情況下無法下訂單的問題 **[!UICONTROL Enable Purchase Orders]** 設為 *是* 和 **[!UICONTROL Purchase Order]** 設為 *否*. 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.40。 修補程式ID為ACSD-54989。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

公司管理員無法在下列情況下下訂單： **[!UICONTROL Enable Purchase Orders]** 設為 *是* 和 **採購單** 設為 *否*.

<u>必要條件</u>：

安裝 [!DNL B2B] 模組。

<u>要再現的步驟</u>：

1. 啟用公司並離開 [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *否*.
1. 建立價格100的簡單產品。
1. 透過「管理員」建立新公司。
1. 設定 [!UICONTROL **啟用採購單**] 至 *是*.
1. 以公司管理員身分登入店面。
1. 將建立的簡單產品新增到購物車。
1. 前往結帳頁面，然後按一下 **[!UICONTROL Place Order]** 以完成購買。

<u>預期結果</u>：

您可以成功下訂單。

<u>實際結果</u>：

此 **[!UICONTROL My Account]** 頁面隨即開啟，且未下訂單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
