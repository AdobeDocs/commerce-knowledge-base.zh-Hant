---
title: 「ACSD-50345：結帳期間出現reCAPTCHA問題」
description: 套用ACSD-50345修補程式以修正Adobe Commerce問題，其中在下訂單時和結帳期間，reCAPTCHA v2和v3驗證失敗。
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345：結帳期間出現reCAPTCHA問題

ACSD-50345修補程式修正了下訂單時和結帳期間reCAPTCHA v2和v3驗證失敗的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.31。 修補程式ID為ACSD-50345。 請注意，Adobe Commerce 2.4.6已部分修正此問題，Adobe Commerce 2.4.7已排程完全修正此問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

**案例#1**

Google reCAPTCHA v2在提交失敗的付款後未重新載入。

<u>要再現的步驟</u>

1. 設定 **[!UICONTROL Google reCAPTCHA v2]** (*我不是機器人*)。
1. 啟用 **[!UICONTROL reCAPTCHA]** 以結帳。
1. 嘗試下單而不按一下 **[!UICONTROL reCAPTCHA]**.
1. 使用者收到遺失reCAPTCHA的錯誤訊息後(*reCAPTCHA驗證失敗，請重試*)，按一下 **[!UICONTROL reCAPTCHA]** 然後嘗試下訂單。

<u>預期結果</u>

使用不正確的reCAPTCHA將不會下訂單。

<u>實際結果</u>

擲回錯誤 —  *reCAPTCHA驗證失敗，請重試* 和 *沒有ID = 4的此類購物車*

**案例#2**

Google reCAPTCHA v3 Visible無法用於結帳，因此無法下訂單。 `PlaceOrder` 事件未觸發。

<u>要再現的步驟</u>

1. 設定 **[!UICONTROL reCAPTCHA v3 Invisible]** 從 **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. 啟用 **[!UICONTROL reCAPTCHA v3 Invisible]** ，以結帳/下訂單 **[!UICONTROL Storefront]** 標籤。
1. 嘗試透過以下方式下訂單： [!UICONTROL Check/Money order] 付款方式。

<u>預期結果</u>

訂單應與 **[!UICONTROL reCAPTCHA]** 已開啟。

<u>實際結果</u>

按一下 **[!UICONTROL Place Order]** 按鈕時，系統就會停用該功能，系統不會再顯示任何專案。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
