---
title: '''ACSD-51890： [!UICONTROL Submit review] 按鈕可按多次'
description: 套用ACSD-51890修補程式以修正Adobe Commerce問題，其中 [!UICONTROL Submit Review] 您可以按幾下按鈕，不需要 [!DNL Google reCAPTCHA v3] 驗證。
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890： **[!UICONTROL Submit Review]** 您可以按幾下按鈕，不需要 **[!DNL Google reCAPTCHA v3]** 驗證

>[!NOTE]
>
>此修補程式已取代為 [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

ACSD-51890修補程式修正了 **[!UICONTROL Submit Review]** 您可以按幾下按鈕，不需要 **[!DNL Google reCAPTCHA v3]** 驗證。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.35。 修補程式ID為ACSD-51890。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

此 **[!UICONTROL Submit Review]** 您可以按幾下按鈕，不使用 **[!DNL Google reCAPTCHA v3]** 驗證。

<u>要再現的步驟</u>：

1. 啟用 **[!DNL Google reCAPTCHA v3]** 以檢閱產品。
1. 開啟產品頁面並導覽至 **[!UICONTROL Review]** 區段並確定 [!DNL reCAPTCHA] 是可見的。
1. 填寫稽核表單，然後按一下 **[!UICONTROL Submit Review]** 按鈕多次。
1. 開啟 **[!UICONTROL Review]** 區段。

<u>預期結果</u>

不會建立重複的稽核。

<u>實際結果</u>

會建立重複的稽核。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
