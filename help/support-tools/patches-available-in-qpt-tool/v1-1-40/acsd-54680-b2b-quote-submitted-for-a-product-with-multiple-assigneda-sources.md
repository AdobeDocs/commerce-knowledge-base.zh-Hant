---
title: 「ACSD-54680：無法處理具有多個指定來源之產品的B2B報價」
description: 套用ACSD-54680修補程式，修正Adobe Commerce無法處理具有多指定來源之產品的B2B報價的問題。
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680：無法處理具有多個指定來源之產品的B2B報價。

ACSD-54680修補程式修正了無法處理具有多個指派來源之產品的B2B報價的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.40。 修補程式ID為ACSD-54680。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法處理具有多個指定來源之產品的B2B報價。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** 並建立兩個新來源： **來源1** 和 **來源2**.
1. 前往 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** 並建立新庫存： **Stock A**，將其指派至主要網站，然後指派 **來源1** 和 **來源2** 轉換至此。
1. 建立簡單產品，指派 **來源1** 和 **來源2**，並設定數量= *2* 用於每個來源。 (產品的可銷售數量應為 *4* 因此)。
1. 建立公司帳戶。
1. 前往 **[!UICONTROL Storefront]** 並登入公司帳戶。
1. 使用數量將簡單產品新增到購物車= *4*.
1. 開啟 *[!UICONTROL Shopping cart]* 並按一下 **[!UICONTROL Request a quote]** 按鈕。
1. 新增評論和報價名稱，然後按一下 **[!UICONTROL Send a Request]** 按鈕。
1. 前往 **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. 開啟最近提交的報價。

<u>預期結果</u>：

報價專案包含訂購的產品。

<u>實際結果</u>：

引用頁面中的專案區段是空的，因此無法處理報價。
`var/log/system.log` 包含

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
