---
title: 「ACSD-54264：客戶嘗試以可轉讓報價結帳時發生錯誤」
description: 套用ACSD-54264修補程式以修正Adobe Commerce問題，其中錯誤訊息「您無法更新要求的屬性。 當客戶嘗試從其他商店檢視中取出可轉讓的報價時，就會出現資料列ID：store_id。
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264：客戶嘗試以可轉讓報價結帳時出現錯誤

ACSD-54264修補程式修正錯誤訊息的問題 *您無法更新要求的屬性。 列ID：store_id* 當客戶嘗試從其他商店檢視中取出可協商的報價時出現。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.42。 修補程式ID為ACSD-54264。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤訊息 *您無法更新要求的屬性。 列ID：store_id* 當客戶嘗試從其他商店檢視中取出可協商的報價時出現。

<u>必要條件</u>：

Adobe Commerce B2B模組已安裝並啟用。

<u>要再現的步驟</u>：

1. 為預設網站建立其他商店檢視。
1. 啟用 *[!UICONTROL B2B Quote]* 在設定中。
1. 在其中一個商店檢視中，以公司客戶身分登入。
1. 將產品新增至 *[!UICONTROL Shopping Cart]*.
1. 提交報價以供檢閱。
1. 以管理員使用者身分，前往 **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** 並提交核准的報價。
1. 作為公司客戶，將商店檢視變更為不同的商店檢視。
1. 嘗試簽出。

<u>預期結果</u>：

客戶使用此報價單下訂單。

<u>實際結果</u>：

* 儲存送貨資訊時發生錯誤：

  `You cannot update the request attribute. Row ID: store_id =#`

* 會記錄下列錯誤：

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
