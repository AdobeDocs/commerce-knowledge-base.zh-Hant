---
title: '''ACSD 49843：使用自動開立發票後無法使用產品下載連結 [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]『'
description: 套用ACSD-49843修補程式以修正Adobe Commerce問題，此問題導致訂購專案在下列情況下自動開立商業發票後無法使用產品下載連結： [!UICONTROL Payment Action] 設為 [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843：使用自動開立發票後無法使用產品下載連結 [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

ACSD-49843修補程式修正了以下問題：當訂購專案由線上付款方式自動開立商業發票後，將無法使用產品下載連結： [!UICONTROL Payment Action] 設為 [!UICONTROL Intent Sale]. 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.37。 修補程式ID為ACSD-49843。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當訂購料號已透過線上付款方式自動開立商業發票之後，便無法使用產品下載連結。 [!UICONTROL Payment Action] 設為 [!UICONTROL Intent Sale].

<u>要再現的步驟</u>：

1. 登入Adobe Commerce管理員並導覽至 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * 在 [!UICONTROL Payment Action] 下拉式清單，選取 **[!UICONTROL Intent Sale]**，並設定 *[!UICONTROL Enable Card Payments]* 至 *是*.

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**，並確保其設為 *&quot;已開發票&quot;*.
1. 在店面，以客戶身分登入。

   * 新增任何可下載的產品和簡單產品至購物車。
   * 使用 [!DNL Braintree Pay] 以使用卡片選項下訂單。

1. 前往 **[!UICONTROL My Orders]** 並檢視會自動建立訂單的商業發票，且料號狀態皆為 *&quot;已開發票&quot;*.
1. 前往 **[!UICONTROL My Downloadable Products]** 並觀察下載連結目前無法使用。
1. 在Admin中，移至該訂單並建立其出貨。
1. 在店面，前往 **[!UICONTROL My Downloadable Products]** 並觀察下載連結現在是否可供使用。

<u>預期結果</u>：

當可下載的產品狀態為「 」時，便可使用下載連結 *&quot;已開發票&quot;*.

<u>實際結果</u>：

即使可下載的產品狀態顯示「下載」連結，仍無法使用 *&quot;已開發票&quot;*. 只有在為實體產品建立出貨後，才能使用此功能。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
