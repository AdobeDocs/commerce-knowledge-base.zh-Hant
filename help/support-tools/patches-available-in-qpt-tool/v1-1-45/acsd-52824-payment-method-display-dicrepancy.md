---
title: 「ACSD-52824：為公司客戶顯示的停用付款方法」
description: 套用ACSD-52824修補程式以修正Adobe Commerce問題，其中 [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] 公司客戶即使已在公司設定中停用，仍可看到付款方法。
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824：為公司客戶顯示的停用付款方法

ACSD-52824修補程式修正以下問題： [!DNL PayPal Express]， [!DNL Google Pay]、和 [!DNL Apple Pay] 公司客戶即使已在公司設定中停用，仍可看到付款方法。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.45。 修補程式ID為ACSD-52824。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

系統會為公司客戶顯示停用的付款方法。

<u>要再現的步驟</u>：

1. 設定並啟用 [!DNL PayPal Express Checkout]. 瀏覽至 **[!UICONTROL Basic Settings]** >選取 **[!DNL PayPal Express Checkout]** 並設定選項 **[!UICONTROL Display on Shopping Cart]** 至 *是*.
1. 設定 [!DNL Braintree] 並啟用 [!DNL Apple Pay] 和 [!DNL Google Pay] 到 [!DNL Braintree].
1. 瀏覽至 **[!UICONTROL Customers]** > **[!UICONTROL Companies]** 並建立新公司。
1. 按一下 **[!UICONTROL Advanced Settings]**，找到 **[!UICONTROL Applicable Payment Methods]** 並選擇 **[!UICONTROL Selected Payment Methods]**.
1. 在 **[!UICONTROL Selected Payment Methods]**，選擇已啟用且沒有關聯的付款方法 *[!DNL PayPal Express Checkout]*， *[!DNL Apple Pay]*，或 *[!DNL Google Pay]*. 例如，選取 **[!UICONTROL Check/Money Order]**.
1. 選取適當的付款方式後，建立新客戶，並將其與先前建立的公司建立關聯。
1. 使用與公司相關聯的客戶帳戶登入，並繼續將專案新增到購物車。
1. 在結帳過程中，請注意迷你購物車、購物車和付款步驟。

<u>預期結果</u>：

付款選項來源 [!DNL PayPal] 和 [!DNL Braintree] 在迷你購物車和購物車中不可見。

<u>實際結果</u>：

付款選項來源 [!DNL PayPal] 和 [!DNL Braintree] 在迷你購物車和購物車中仍可見。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
