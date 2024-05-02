---
title: 'ACSD-49464：未從封存移回的商業發票、出貨及銷退折讓單'
description: 套用ACSD-49464修補程式，以修正當訂單ID不同時，商業發票、出貨及銷退折讓單不會從封存移回的Adobe Commerce問題。
exl-id: 845f9878-5f7e-4e58-8f8a-b02af17b3f11
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-49464：未從封存移回的商業發票、出貨及銷退折讓單

當orderId不同時，ACSD-49464修補程式會修正商業發票、出貨及銷退折讓單不會從封存移回的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.29。 修補程式ID為ACSD-49464。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當orderId不同時，不會將商業發票、出貨及銷退折讓單從存檔移回。

<u>要再現的步驟</u>：

1. 啟用訂單、商業發票、出貨及銷退折讓單存檔。
1. 建立並完成訂單，包括出貨、商業發票及銷退折讓單。
1. 請確認出貨、商業發票及銷退折讓單ID與訂單編號不同。
1. 將訂單移至封存。
1. 將已封存的訂單還原至訂單管理。
1. 檢查發票、出貨及銷退折讓單明細（位於個別專案下） [!UICONTROL Invoice]， [!UICONTROL Shipping]、和 [!UICONTROL Credit Memo] 格線頁面。

<u>預期結果</u>：

將訂單從封存清單移至訂單管理時，會還原原始相關記錄。

<u>實際結果</u>：

* 如果所有識別碼不同，則沒有出貨、商業發票及銷退折讓單的記錄。
* 如果訂單與相關記錄具有相同的ID，則會傳回記錄。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
