---
title: 'ACSD-52831：不得在下列情況下下可轉讓的報價單 [!DNL Google reCAPTCHA v3 Invisible] 已啟用'
description: 套用ACSD-52831修補程式，修正下列情況下您無法下可轉讓報價單的Adobe Commerce問題 [!DNL Google reCAPTCHA v3 Invisible] 已啟用。
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831：下列情況下無法下可轉讓的報價單 [!DNL Google reCAPTCHA v3 Invisible] 已啟用

ACSD-52831修補程式修正了以下問題：當發生下列情況時，您無法下可轉讓的報價單 [!DNL Google reCAPTCHA v3 Invisible] 已啟用。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.35。 修補程式ID為ACSD-52831。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法下可轉讓報價單，當 [!DNL Google reCAPTCHA v3 Invisible] 已啟用。

<u>要再現的步驟</u>：

1. 啟用B2B報價功能。
1. 啟用 [!DNL Google reCAPTCHA v3 Invisible] ，以啟用結帳/下訂單。
1. 提出報價，然後使用該報價進行結帳。
1. 發生驗證碼錯誤，您將無法下訂單。

<u>預期結果</u>：

報價會繼續進行結帳。

<u>實際結果</u>：

您收到錯誤 *reCAPTCHA驗證失敗，請重試*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
