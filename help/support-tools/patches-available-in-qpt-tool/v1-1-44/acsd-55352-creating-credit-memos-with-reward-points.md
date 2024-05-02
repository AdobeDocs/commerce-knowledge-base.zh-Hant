---
title: 'ACSD-55352：建立含獎勵積分的銷退折讓單'
description: 套用ACSD-55352修補程式以修正Adobe Commerce問題，其中在建立包含客戶獎勵點數的部分銷退折讓單後，訂單狀態會變更為*closed*，而銷退折讓單選項會從管理訂單頁面消失。
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352：以獎勵點數建立銷退折讓單

ACSD-55352修補程式修正了以下問題：使用客戶獎勵點數建立部分銷退折讓單後，訂單狀態會變更為 *已關閉* 和銷退折讓單選項從管理訂單頁面消失。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.44。 修補程式ID為ACSD-55352。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

建立含客戶獎勵點數的部份銷退折讓單後，訂單狀態會變更為 *已關閉* 和銷退折讓單選項從管理訂單頁面消失。

<u>要再現的步驟</u>：

1. 登入Adobe Commerce管理員。
2. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. 新增兩個費率：
   * *[!UICONTROL First]*：
      * *[!UICONTROL Direction]* = *貨幣點數*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*：
      * *[!UICONTROL Direction]* = *貨幣到點*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. 建立簡單的產品，其價格為 *$100* 和 *數量* ： *100*.
5. 從店面建立客戶。
6. 再次前往後端： **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** >新增 *100* 並儲存客戶。
7. 前往店面，並以客戶先前建立的身分登入。
8. 新增產品至購物車，使用 *數量* ： *10*.
9. 前往 **[!UICONTROL Checkout]** 並使用可用的 *100* 提示時獎勵積分並下訂單。
10. 前往 **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** 並送出該訂單。
11. 前往 [!UICONTROL Credit Memo] 並更新 *要退款的數量* 至 *8*.
12. 勾選 **[!UICONTROL Refund Reward Points]** 核取方塊並按一下 **[!UICONTROL Refund offline]**.
13. 嘗試使用退還訂單中其他兩個剩餘的產品 [!UICONTROL Credit Memo].

<u>預期結果</u>：

* 管理員會建立 [!UICONTROL Credit Memo] 以傳回剩餘的兩個產品。
* 訂單狀態為 *已完成*.

<u>實際結果</u>：

* 無法建立更多專案 [!UICONTROL Credit Memo].
* 訂單狀態為 *已關閉*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
